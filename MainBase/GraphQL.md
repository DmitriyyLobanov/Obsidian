2024-08-15 15:18

**GraphQL** — это язык запросов к данным, представленный в 2012 году, чтобы нивелировать недостатки REST API, связанные с передачей избыточных или недостаточных данных от множества конечных точек. Он позволяет через вход в ресурс получать доступ к другим связанным ресурсам, если взаимосвязь между ними заранее определена в схеме данных. Будучи декларативным языком запросов для API со встроенной проверкой типов данных и серверной средой выполнения, GraphQL возвращает сложный граф данных (отсюда и слово Graph в названии), уменьшая количество запросов по сети до одного показа. CRUD-операции над данными в GraphQL реализуются через разные виды POST-запросов:

- простые запросы (**_query_**) на чтение данных аналогичны GET в REST API;
- создание новых и изменение существующих данных реализуются через запросы-мутации (**_mutation_**), которые позволяют клиенту создавать, обновлять и удалять данные на сервере;
- подписки (**_subscriptions_**), которые позволяют клиенту оперативно получать обновления в базе данных, прослушивая изменения в режиме реального времени. Подписки используют вебсокеты, создающие интерактивное соединение между клиентом (браузером) и сервером для обмена сообщениями в реальном времени. Данные передаются в обе стороны (от клиента к серверу и, наоборот, от сервера к клиенту), что актуально для сценариев длительного соединения в реальном времени, например, онлайн-биржа, онлайн-игры и пр.

GraphQL предоставляет следующие преимущества:

- очень гибкий и обеспечивает именно то, что нужно клиенту, избегая передачи излишних данных;
- исключает излишние запросы из-за недостатка данных;
- поддерживается многими языками программирования (JavaScript, Java, Python, Ruby и PHP);
- позволяет настраивать структуру данных;
- один запрос может содержать поля из нескольких ресурсов.

Обратной стороной этих достоинств GraphQL являются сложность реализации, статичная схема данных, отсутствие встроенной поддержки кэширования и трудности в управлении версиями. Запросы могут быть излишне сложными, а также по умолчанию не поддерживается загрузка файлов. Наконец, GraphQL работает только с JSON-структурами данных, тогда как REST воспринимает любые форматы (JSON, XML, HTML, TXT и пр.)

Однако, GraphQL API хорошо подходит для приложений с большим количеством клиентов и/или источников данных, когда нужно реализовать единообразие в средствах выполнения запросов, уменьшить число конечных точек и снизить нагрузку на сеть. Например, всем известные Github и Youtube используют GraphQL. Также благодаря своей гибкой структуре запросов GraphQL отлично подходит для баз с большим количеством записей, позволяя устранить избыточную выборку результатов и получать только нужные данные, чтобы повысить производительность приложения. Кроме того, можно использовать GraphQL, когда нет четкого понимания, как клиент использует API, без необходимости заранее определять строгий контракт: можно постепенно создавать API на основе отзывов клиентов.



[[Стили межсистемной интеграции по API]] 
#Learn