2024-08-1513:42

## Что такое REST?

Какое же определение в понятие REST заложил его основатель Рой Филдинг?

**Representational State Transfer** — это архитектурный стиль взаимодействия компонентов распределённого приложения в сети. Архитектурный стиль – это набор согласованных ограничений и принципов проектирования, позволяющий добиться определённых свойств системы.

>«Передача репрезентативного состояния» или «передача „самоописываемого“ состояния»
>- Это сильно.

Но зачем нам REST? Зачем нам этот стиль? Что нам даст применение принципов REST?

Если мы обратимся опять же к первоисточнику — к работе Филдинга, то мы выясним, что назначение REST в том, чтобы придать проектируемой системе такие свойства как

1. Производительность
2. Масштабируемость
3. Гибкость к изменениям
4. Отказоустойчивость
5. Простота поддержки

Это наиболее ценные свойства, с которыми встречается, например, аналитик при проектировании систем. В действительности их намного больше. Если внимательно посмотреть на эти свойства, то мы увидим ни что иное, как нефункциональные требования к системе, которых мы на своих проектах стремимся достичь.

## Принципы REST

Каким образом REST может помочь нам достичь этих свойств и реализовать эти нефункциональные требования?

**6 принципов REST:**

1. [[Клиент-серверная архитектура]]
2. [[stateless]]
3. [[Кэширование]] 
4. [[Единообразие интерфейса HATEOAS]] 
5. [[Слоистая архитектура (layered system)]]
6. [[Код по требованию (code on demand)]] 


## Заблуждения о REST


**1. Ограничения REST опциональны (необязательны)**

С точки зрения создателя этой концепции существует ровно одно необязательное ограничение — код по требованию. Все остальные ограничения должны выполняться. Если одно из них не выполняется — это уже не REST-подход.  

>На практике принципы REST претерпевает изменения от реализации к реализации, происходит всякое.

**2. REST — протокол передачи данных**

REST — это не протокол передачи данных. Он не определяет правила о том, как мы должны передавать запросы, какая у них должна быть структура, что мы должны возвращать в ошибках. Единственное, что косвенно можно было бы приписать — это указание на то, что каждый ответ сервера должен содержать информацию о том, можно ли его кэшировать.

Но, в целом, REST — это концепция, парадигма, но не протокол. В отличие от [[HTTP]], который действительно является протоколом.

**3. REST — это всегда HTTP**

С одной стороны, ни один из архитектурных принципов REST не говорит нам о том, какой транспорт мы должны использовать — HTTP или другие протоколы.

Но при этом в жизни очень часто встречаются люди, для которых REST и HTTP — это аксиома.

Поэтому, если сказать человеку, что REST — это необязательно HTTP, то вас могут посчитать сумасшедшими.

Почему же все считают, что REST — это HTTP? Здесь нужно сделать ремарку, что одним из главных авторов протокола HTTP — это Рой Филдинг, автор концепции REST. Рой Филдинг стремился спроектировать HTTP так, чтобы с помощью него концепцию REST было максимально удобно реализовывать.

>На практике REST и HTTP практически неотделимы. Люди даже в плане "потеоретизировать" не хотят слушать про альтернативы HTTP.

**4. REST — это обязательно JSON**

Почему так сложилось? Главная причина в том, что какое-то время назад сервисы вида JSON over HTTP стали противопоставлять SOAP. JSON одновременно стал популярным и стал антагонистом XML, как SOAP подходу. JSON использовался, потому что это не SOAP.
( материал взят с (https://habr.com/ru/articles/590679/comments/))



[[Стили межсистемной интеграции по API]]
#Learn