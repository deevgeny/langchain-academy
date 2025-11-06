![LangChain Academy](https://cdn.prod.website-files.com/65b8cd72835ceeacd4449a53/66e9eba1020525eea7873f96_LCA-big-green%20(2).svg)

## Введение

Добро пожаловать в LangChain Academy, курс «Введение в LangGraph»!
Это растущий набор модулей, сфокусированных на основных концепциях экосистемы LangChain.
Модуль 0 посвящен базовой настройке, а Модули с 1 по 5 ориентированы на разработку в LangGraph, постепенно добавляя более сложные темы. Модуль 6 посвящен развертыванию ваших агентов.
В папке каждого модуля вы найдете набор блокнотов. В верхней части каждого блокнота есть ссылка на урок в LangChain Academy, которая проведет вас через тему. Каждый модуль также имеет подкаталог `studio` с набором соответствующих графов, которые мы будем изучать с помощью LangGraph API и Studio.

## Настройка окружения

### Требования к Python

Для комфортной работы с курсом убедитесь, что у вас установлен Python версии 3.11 или выше. 
Именно эта версия обеспечивает полную совместимость с LangGraph. Если у вас стоит более старая версия,
рекомендуем обновиться - это избавит от возможных проблем.
```
python3 --version
```

### Клонирование репозитория
```
# Русскоязычный форк 
git clone https://github.com/deevgeny/langchain-academy.git
$ cd langchain-academy

# Оригинальный репозиторий на английском
git clone https://github.com/langchain-ai/langchain-academy.git
$ cd langchain-academy
```
Или скачайте [ZIP-архив](https://github.com/langchain-ai/langchain-academy/archive/refs/heads/main.zip), если предпочитаете этот способ.

### Создание виртуального окружения и установка пакетов
#### Mac/Linux/WSL
```
$ python3.11 -m venv venv
$ source venv/bin/activate
$ pip install -r requirements.txt
```
#### Windows Powershell
```
PS> python3.11 -m venv venv
PS> Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process
PS> venv\scripts\activate
PS> pip install -r requirements.txt
```

### Работа с блокнотами (Jupyter Notebook)
Если Jupyter не установлен, воспользуйтесь [официальной инструкцией](https://jupyter.org/install).
```
# Запускаем локальный сервер и выбираем нужный файл
$ jupyter notebook
```

### Настройка переменных окружения
Кратко о том, как задавать переменные окружения.
#### Mac/Linux/WSL
```
$ export API_ENV_VAR="your-api-key-here"
```
#### Windows Powershell
```
PS> $env:API_ENV_VAR = "your-api-key-here"
```

### Ключ Mistral API
* Получить ключ Mistral API можно [здесь](https://mistral.ai/).
* Задайте переменную окружения `MISTRAL_API_KEY`

### Регистрация в LangSmith
* Создайте аккаунт LangSmith [по этой ссылке](https://docs.langchain.com/langsmith/create-account-api-key#create-an-account-and-api-key). Подробнее о возможностях платформы читайте [в документации](https://www.langchain.com/langsmith).
* Задайте следующие переменные окружения: `LANGSMITH_API_KEY`, `LANGSMITH_TRACING_V2=true`, `LANGSMITH_PROJECT="langchain-academy"`
* Пользователям европейского сервера дополнительно укажите `LANGSMITH_ENDPOINT`="https://eu.api.smith.langchain.com".

### API-ключ Tavily для веб-поиска

* Tavily Search API - это поисковой движок, созданный специально для языковых моделей и RAG-систем. 
Он обеспечивает быстрый и стабильный поиск.
* Зарегистрируйтесь и получите ключ [на сайте](https://tavily.com/).
Регистрация занимает минуту, а бесплатный тариф весьма щедрый. Tavily понадобится в некоторых уроках Модуля 4.

* Задайте переменную окружения `TAVILY_API_KEY`.

### Работа со Studio

* Studio - это специальная среда разработки для создания и отладки агентов.
* Она работает локально и открывается в браузере на любой ОС.
* Подробности о локальном сервере разработки читайте [в документации](https://docs.langchain.com/langsmith/studio#local-development-server).
* Готовые графы для LangGraph Studio лежат в папках `module-x/studio/` (модули 1-5).
* Для запуска локального сервера перейдите в папку `/studio` нужного модуля и выполните:

```
langgraph dev
```

В ответ вы должны увидеть:
```
- 🚀 API: http://127.0.0.1:2024
- 🎨 Studio UI: https://smith.langchain.com/studio/?baseUrl=http://127.0.0.1:2024
- 📚 API Docs: http://127.0.0.1:2024/docs
```

Теперь откройте в браузере Studio UI: `https://smith.langchain.com/studio/?baseUrl=http://127.0.0.1:2024`.

* Для работы со Studio понадобятся API-ключи, которые хранятся в файле .env
* Чтобы создать эти файлы для модулей 1-5, выполните команду:
```
for i in {1..5}; do
  cp module-$i/studio/.env.example module-$i/studio/.env
  echo "OPENAI_API_KEY=\"$OPENAI_API_KEY\"" > module-$i/studio/.env
done
echo "TAVILY_API_KEY=\"$TAVILY_API_KEY\"" >> module-4/studio/.env
```

## Модули

### О курсе
1. [Коротко о курсе](https://github.com/deevgeny/langchain-academy/blob/main/module-0/basics.ipynb)

### Введение
1. [Граф (Graph)](https://github.com/deevgeny/langchain-academy/blob/main/module-1/simple-graph.ipynb)
2. [Цепочка (Chain)](https://github.com/deevgeny/langchain-academy/blob/main/module-1/chain.ipynb)
3. [Маршрутизатор (Router)](https://github.com/deevgeny/langchain-academy/blob/main/module-1/router.ipynb)
4. [Агент (Agent)](https://github.com/deevgeny/langchain-academy/blob/main/module-1/agent.ipynb)
5. [Агент с памятью (Agent with memory)](https://github.com/deevgeny/langchain-academy/blob/main/module-1/agent-memory.ipynb)
6. [Развертывание (Deployment)](https://github.com/deevgeny/langchain-academy/blob/main/module-1/deployment.ipynb)

### Состояние и память
1. [Схема состояния](https://github.com/deevgeny/langchain-academy/blob/main/module-2/state-schema.ipynb)
2. [Редьюсеры состояния](https://github.com/deevgeny/langchain-academy/blob/main/module-2/state-reducers.ipynb)
3. [Множественные схемы](https://github.com/deevgeny/langchain-academy/blob/main/module-2/multiple-schemas.ipynb)
4. [Фильтрация и очистка сообщений](https://github.com/deevgeny/langchain-academy/blob/main/module-2/trim-filter-messages.ipynb)
5. [Чат-бот с суммаризацией сообщений](https://github.com/deevgeny/langchain-academy/blob/main/module-2/chatbot-summarization.ipynb)
6. [Чат-бот с суммаризацией сообщений и внешней памятью БД](https://github.com/deevgeny/langchain-academy/blob/main/module-2/chatbot-external-memory.ipynb)

### UX и человеческое участие (Human-in-the-Loop)
1. [Стриминг (streaming)](https://github.com/deevgeny/langchain-academy/blob/main/module-3/streaming-interruptions.ipynb)
2. [Точки прерывания (breakpoints)](https://github.com/deevgeny/langchain-academy/blob/main/module-3/breakpoints.ipynb)
3. [Редактирование состояния графа (edit graph state)](https://github.com/deevgeny/langchain-academy/blob/main/module-3/edit-state-human-feedback.ipynb)
4. [Динамические точки прерывания (dynamic breakpoints)](https://github.com/deevgeny/langchain-academy/blob/main/module-3/dynamic-breakpoints.ipynb)
5. [Навигация по истории состояний (time travel)](https://github.com/deevgeny/langchain-academy/blob/main/module-3/time-travel.ipynb)

### Создание ассистента
1. [Параллелизация (parallelization)](https://github.com/deevgeny/langchain-academy/blob/main/module-4/parallelization.ipynb)
2. [Подграфы (sub-graphs)](https://github.com/deevgeny/langchain-academy/blob/main/module-4/sub-graphs.ipynb)
3. [Map-reduce](https://github.com/deevgeny/langchain-academy/blob/main/module-4/map-reduce.ipynb)
4. [Исследовательский ассистент](https://github.com/deevgeny/langchain-academy/blob/main/module-4/research-assistant.ipynb)