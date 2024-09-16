 2024-09-15 20:30

**XML (Extensible Markup Language)**:

- **Формат данных**. SOAP-сообщения представлены в виде XML-документов. XML предоставляет структуру для передачи данных между сервисами, которая читаема как людьми, так и машинами.

```xml
<bankTransaction xmlns="http://www.examplebank.com/transactions">
  <transactionId>123456</transactionId>
  <transactionDate>2024-09-15</transactionDate>
  <account>
    <accountNumber>987654321</accountNumber>
    <accountHolder>John Doe</accountHolder>
  </account>
  <transactionDetails>
    <amount currency="USD">1500.00</amount>
    <type>Transfer</type>
    <status>Completed</status>
  </transactionDetails>
  <recipient>
    <recipientName>Jane Smith</recipientName>
    <recipientAccount>123456789</recipientAccount>
    <bankName>ExampleBank</bankName>
  </recipient>
</bankTransaction>
```
### Объяснение назначения тегов:

1. **`<bankTransaction>`**:
    
    - **Корневой элемент**. Этот тег является основным элементом XML-документа и обозначает, что документ описывает банковскую транзакцию.
    - Атрибут `xmlns="http://www.examplebank.com/transactions"` указывает на пространство имён XML (XML namespace), которое используется для уникальной идентификации элементов.
2. **`<transactionId>`**:
    
    - Уникальный идентификатор транзакции. Этот тег содержит ID, по которому можно идентифицировать конкретную банковскую операцию.
3. **`<transactionDate>`**:
    
    - Дата проведения транзакции. Этот элемент указывает на дату и время, когда была проведена операция.
4. **`<account>`**:
    
    - **Информация о счёте отправителя**. Этот тег группирует данные о банковском счёте, с которого была выполнена транзакция.
        - **`<accountNumber>`**: Номер банковского счёта отправителя.
        - **`<accountHolder>`**: Имя владельца банковского счёта.
5. **`<transactionDetails>`**:
    
    - **Детали транзакции**. Этот тег содержит информацию о сумме, типе и статусе транзакции.
        - **`<amount>`**: Сумма транзакции. В атрибуте `currency` указана валюта, в которой была проведена операция (например, USD).
        - **`<type>`**: Тип транзакции (например, "Transfer" — перевод средств).
        - **`<status>`**: Текущий статус транзакции (например, "Completed" — завершено).
6. **`<recipient>`**:
    
    - **Информация о получателе**. Этот тег содержит данные о получателе средств.
        - **`<recipientName>`**: Имя получателя.
        - **`<recipientAccount>`**: Номер счёта получателя.
        - **`<bankName>`**: Название банка получателя.

[[SOAP]]
#Learn