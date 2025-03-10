 2024-09-16 09:35

**XPath** (XML Path Language) — это язык для навигации по элементам и атрибутам в XML-документах. Его используют для выборки данных и определения путей к различным узлам в структуре XML. XPath является важной частью других технологий, таких как XSLT, XQuery и даже схем XML (например, XSD).

### Основные концепции XPath:

1. **Контекстный узел (Context Node)**:
    
    - XPath всегда работает в контексте определённого узла. Например, если вы применяете XPath в XSLT, контекстным узлом может быть корневой элемент, текущий элемент, элемент родитель и т.д.
2. **Выражения XPath**:
    
    - XPath выражения используются для выборки данных из XML-документа. Основная идея состоит в том, чтобы указать путь к элементам, используя синтаксис, подобный файловой системе.
    
    Пример: `/bankTransactions/transaction/amount`  
    Это выражение XPath выбирает элемент `<amount>` внутри элемента `<transaction>`, который находится внутри корневого элемента `<bankTransactions>`.
    
3. **Основа XPath (Axes)**:
    
    - В XPath существует концепция осей (axes), которые позволяют описать, как перемещаться между узлами. Например:
        - `child::` — выбирает дочерние элементы.
        - `parent::` — выбирает родительские элементы.
        - `ancestor::` — выбирает предков.
        - `following-sibling::` — выбирает последующие соседние элементы.
4. **Фильтрация узлов**:
    
    - XPath позволяет отфильтровывать элементы по условиям. Это делает XPath мощным инструментом для выборки только тех данных, которые удовлетворяют определённым критериям.
    
    Пример: `/bankTransactions/transaction[amount > 1000]` Это выражение выберет все транзакции, где сумма больше 1000.
    
5. **Отбор по атрибутам**:
    
    - XPath может использоваться для выборки элементов по значениям атрибутов.
    
    Пример: `/bankTransactions/transaction[@currency='USD']` Это выражение выберет все транзакции, где атрибут `currency` равен "USD".

### Пример использования XPath в XSLT:

XPath часто используется в XSLT для выбора данных из XML-документа. Например, чтобы выбрать и отобразить все транзакции, XPath выражение будет таким:

```xml
<xsl:for-each select="/bankTransactions/transaction">
  <tr>
    <td><xsl:value-of select="transactionId"/></td>
    <td><xsl:value-of select="amount"/></td>
  </tr>
</xsl:for-each>

```

### Операторы XPath:

1. **Операторы путей**:
    
    - `/` — выбирает элемент, начиная с корня.
    - `//` — выбирает все элементы в документе, которые соответствуют имени, независимо от их местоположения.
    
    Пример:  
    `/bankTransactions//amount`  
    Выбирает все элементы `<amount>` в документе, независимо от их уровня вложенности.
    
2. **Условия (Predicates)**:
    
    - `[ ]` — используется для фильтрации элементов на основе условий.
    
    Пример:  
    `/bankTransactions/transaction[amount > 1000]`  
    Выбирает все элементы `<transaction>`, где сумма транзакции больше 1000.
    
3. **Функции XPath**: XPath поддерживает различные функции для работы с данными:
    
    - `text()` — выбирает текстовое содержимое узла.
    - `position()` — возвращает позицию узла в наборе.
    
    Пример:  
    `/bankTransactions/transaction[position()=1]`  
    Выбирает первый элемент `<transaction>`.
    

### Пример XPath в XSD:

XPath может использоваться в XSD для ограничения допустимых значений элементов на основе значений других элементов. Например:

```xml
<xs:element name="transaction">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="transactionId" type="xs:string"/>
      <xs:element name="amount" type="xs:decimal"/>
      <xs:element name="currency" type="xs:string"/>
    </xs:sequence>
    <xs:assert test="currency = 'USD' or currency = 'EUR'"/>
  </xs:complexType>
</xs:element>

```

В этом примере используется XPath выражение в элементе `<xs:assert>` для проверки, что валюта транзакции должна быть либо "USD", либо "EUR".

### Заключение:

XPath — это гибкий и мощный язык, который применяется для выборки и фильтрации данных в XML-документах. Он играет важную роль в таких технологиях, как XSLT и XSD, позволяя эффективно извлекать и преобразовывать данные.

[[SOAP]]
[[XSD]]
[[XSLT]]
#Learn