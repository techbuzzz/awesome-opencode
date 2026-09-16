# HH Job Agent Pack — Viktor Buzin

Полный пакет агента для поиска работы на hh.ru. Готов к подключению в Claude, OpenAI, OpenRouter, Abacus.AI и любую платформу с поддержкой tool use / function calling / OpenAPI plugins.

---

## Содержимое пакета

```
hh_agent_pack/
├── system_prompt.md        ← Системная инструкция агента (вставить в System Instructions)
├── openapi.json            ← OpenAPI 3.0 schema (GPT Actions, OpenRouter, MCP-совместимые платформы)
├── plugin_manifest.json    ← Plugin manifest (OpenAI-стиль, Claude Extensions)
├── claude_tools.json       ← Tool definitions для Claude API (tools блок)
├── openai_functions.json   ← Function definitions для OpenAI API (functions блок)
└── README.md               ← Этот файл
```

Abacus.AI Skills (зарегистрированы отдельно, активны в текущем проекте):
```
skills/
├── hh-vacancy-analyzer/    ← Анализ вакансий
├── hh-cover-letter/        ← Сопроводительные письма
└── hh-resume-adapter/      ← ATS-адаптация резюме
```

---

## Подключение по платформам

### Claude (claude.ai Projects / Claude for Teams)

1. Открыть проект → **Project Instructions**
2. Вставить содержимое `system_prompt.md`
3. Для tool use через API — передать массив из `claude_tools.json` в поле `tools` запроса

```python
import anthropic, json

client = anthropic.Anthropic()
tools = json.load(open("claude_tools.json"))["tools"]

response = client.messages.create(
    model="claude-opus-4-5",
    max_tokens=2048,
    system=open("system_prompt.md").read(),
    tools=tools,
    messages=[{"role": "user", "content": "Проанализируй эту вакансию: ..."}]
)
```

---

### OpenAI (ChatGPT Custom GPT / GPT Actions)

**Вариант A — Custom GPT:**
1. ChatGPT → Explore GPTs → Create
2. Instructions: вставить содержимое `system_prompt.md`
3. Actions → Add action → вставить содержимое `openapi.json`
4. В `plugin_manifest.json` обновить `api.url` на URL вашего деплоя

**Вариант B — API (function calling):**

```python
from openai import OpenAI
import json

client = OpenAI()
functions = json.load(open("openai_functions.json"))["functions"]

response = client.chat.completions.create(
    model="gpt-4o",
    messages=[
        {"role": "system", "content": open("system_prompt.md").read()},
        {"role": "user", "content": "Напиши сопроводительное письмо к этой вакансии: ..."}
    ],
    functions=functions,
    function_call="auto"
)
```

---

### OpenRouter

OpenRouter поддерживает OpenAI-совместимый API. Используй `openai_functions.json` как tools:

```python
from openai import OpenAI
import json

client = OpenAI(
    base_url="https://openrouter.ai/api/v1",
    api_key="YOUR_OPENROUTER_KEY"
)

functions = json.load(open("openai_functions.json"))["functions"]

response = client.chat.completions.create(
    model="anthropic/claude-opus-4-5",  # или любая другая модель
    messages=[
        {"role": "system", "content": open("system_prompt.md").read()},
        {"role": "user", "content": "Проанализируй вакансию..."}
    ],
    tools=[{"type": "function", "function": f} for f in functions]
)
```

---

### Abacus.AI (текущий проект)

Skills уже зарегистрированы. Просто работай в этом проекте — агент автоматически применяет нужный skill в зависимости от задачи:

| Что сказать | Какой skill активируется |
|---|---|
| «Проанализируй эту вакансию» | hh-vacancy-analyzer |
| «Напиши сопроводительное письмо» | hh-cover-letter |
| «Адаптируй резюме под вакансию» | hh-resume-adapter |

---

### n8n / Make / Zapier (через REST API)

Используй `openapi.json` как спецификацию для HTTP-узлов. Каждый endpoint — отдельный шаг автоматизации:

- `POST /analyze_vacancy` → анализ при новой вакансии в базе
- `POST /write_cover_letter` → автогенерация письма
- `POST /adapt_resume` → адаптация резюме

---

## Описание инструментов агента

| Tool | Когда использовать | Обязательный параметр |
|---|---|---|
| `analyze_vacancy` | Прислана любая вакансия | `vacancy_text` |
| `write_cover_letter` | Нужно написать письмо | `vacancy_text` |
| `adapt_resume` | Нужно адаптировать резюме | `vacancy_text` |
| `generate_followup` | Нет ответа 5+ дней | `position_title`, `days_since_application` |
| `prepare_interview` | Получено приглашение | `vacancy_text` |

---

## Ключевые правила агента

- Отвечать на русском, если вакансия на русском; на английском, если вакансия на английском
- Никогда не добавлять компетенции, которых нет в реальном опыте Виктора
- Числа и даты в резюме не менять — только формулировки
- ATS-ключевые слова интегрировать дословно, не синонимами
- Письма: без «горю желанием», «идеально подхожу», «рад возможности» и прочего AI-слопа

---

## Обновление пакета

При изменении профиля кандидата (новая должность, новые достижения, смена целевых ролей) обновить:
1. `system_prompt.md` — блок «Профиль кандидата»
2. `skills/hh-resume-adapter/SKILL.md` — блок «Профиль кандидата (базовые данные)»
3. `skills/hh-cover-letter/SKILL.md` — блок «Профиль кандидата»
