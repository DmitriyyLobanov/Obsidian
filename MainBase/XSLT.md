 2024-09-15 22:25

**XSLT (Extensible Stylesheet Language Transformations)**:

- **Преобразование данных**. XSLT используется для преобразования XML-документов в другие форматы (например, HTML или другой XML). В контексте SOAP XSLT может применяться для преобразования данных, извлечённых из SOAP-сообщения, в удобочитаемый формат или для других операций с XML.

Ниже представлен пример XSLT-документа, который используется для трансформации XML-документа в HTML-таблицу.

Пример XML-документа с банковскими данными:
```xml
<bankTransactions>
  <transaction>
    <transactionId>123456</transactionId>
    <accountNumber>987654321</accountNumber>
    <transactionDate>2024-09-01</transactionDate>
    <amount>1000.00</amount>
    <currency>USD</currency>
    <transactionType>credit</transactionType>
  </transaction>
  <transaction>
    <transactionId>123457</transactionId>
    <accountNumber>123456789</accountNumber>
    <transactionDate>2024-09-02</transactionDate>
    <amount>500.00</amount>
    <currency>EUR</currency>
    <transactionType>debit</transactionType>
  </transaction>
</bankTransactions>

```

Пример XSLT-документа для преобразования данных:
```xml
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

  <!-- Описание преобразования: корневой элемент -->
  <xsl:template match="/">
    <html>
      <head>
        <title>Bank Transactions</title>
        <style>
          table { border-collapse: collapse; width: 100%; }
          th, td { border: 1px solid black; padding: 8px; text-align: left; }
          th { background-color: #f2f2f2; }
        </style>
      </head>
      <body>
        <h2>Bank Transactions</h2>
        <table>
          <tr>
            <th>Transaction ID</th>
            <th>Account Number</th>
            <th>Date</th>
            <th>Amount</th>
            <th>Currency</th>
            <th>Type</th>
          </tr>
          <!-- Применение шаблона для каждой транзакции -->
          <xsl:for-each select="bankTransactions/transaction">
            <tr>
              <td><xsl:value-of select="transactionId"/></td>
              <td><xsl:value-of select="accountNumber"/></td>
              <td><xsl:value-of select="transactionDate"/></td>
              <td><xsl:value-of select="amount"/></td>
              <td><xsl:value-of select="currency"/></td>
              <td><xsl:value-of select="transactionType"/></td>
            </tr>
          </xsl:for-each>
        </table>
      </body>
    </html>
  </xsl:template>

</xsl:stylesheet>

```

### Объяснение назначения тегов:

1. **`<xsl:stylesheet>`**:
    
    - Корневой элемент XSLT-документа, который указывает, что это XSLT-преобразование. Атрибут `version="1.0"` задает версию XSLT, а пространство имён `xmlns:xsl="http://www.w3.org/1999/XSL/Transform"` указывает на стандарт XSLT.
2. **`<xsl:template>`**:
    
    - Шаблон, который применяется к узлам в исходном XML-документе. Атрибут `match="/"` означает, что этот шаблон будет применяться ко всему документу (начиная с корневого элемента).
    - Внутри шаблона определяется HTML-код, который будет сгенерирован на основе данных из XML.
3. **`<xsl:for-each>`**:
    
    - Цикл, который применяется для каждого элемента `<transaction>` внутри элемента `<bankTransactions>`. Этот цикл проходит по всем транзакциям в XML-документе и создает строку таблицы `<tr>` для каждой транзакции.
4. **`<xsl:value-of>`**:
    
    - Используется для извлечения значений из XML-документа. Например, `<xsl:value-of select="transactionId"/>` извлекает значение элемента `<transactionId>` для каждой транзакции и вставляет его в соответствующую ячейку таблицы.
5. **HTML-код**:
    
    - Внутри XSLT-документа создается HTML-таблица с заголовками и стилями для отображения данных. Теги `<th>` создают заголовки таблицы, а теги `<td>` заполняются данными из XML с помощью конструкции `<xsl:value-of>`.
6. **`<style>`**:
    
    - Определяет стили для таблицы в сгенерированном HTML-документе. В примере задаются границы таблицы, отступы и выравнивание текста.

### Как работает XSLT-документ:

Этот XSLT-документ преобразует данные из XML в HTML-таблицу. Для каждой транзакции в исходном XML-документе создается строка таблицы, в которой отображаются такие данные, как идентификатор транзакции, номер счета, дата, сумма, валюта и тип транзакции (кредит или дебет).

Пример результата после трансформации:
```html
<html>
  <head>
    <title>Bank Transactions</title>
    <style>
      table { border-collapse: collapse; width: 100%; }
      th, td { border: 1px solid black; padding: 8px; text-align: left; }
      th { background-color: #f2f2f2; }
    </style>
  </head>
  <body>
    <h2>Bank Transactions</h2>
    <table>
      <tr>
        <th>Transaction ID</th>
        <th>Account Number</th>
        <th>Date</th>
        <th>Amount</th>
        <th>Currency</th>
        <th>Type</th>
      </tr>
      <tr>
        <td>123456</td>
        <td>987654321</td>
        <td>2024-09-01</td>
        <td>1000.00</td>
        <td>USD</td>
        <td>credit</td>
      </tr>
      <tr>
        <td>123457</td>
        <td>123456789</td>
        <td>2024-09-02</td>
        <td>500.00</td>
        <td>EUR</td>
        <td>debit</td>
      </tr>
    </table>
  </body>
</html>

```
Этот HTML-документ содержит таблицу с данными о банковских транзакциях, которые были взяты из XML-документа и преобразованы с помощью XSLT.

[[SOAP]]
#Learn