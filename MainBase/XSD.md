**XSD (XML Schema Definition)**:

- **Описание структуры данных**. XSD используется для определения структуры XML-документов. В контексте SOAP XSD описывает, как должны выглядеть данные (например, типы элементов и их последовательность), чтобы SOAP-сообщение было корректно обработано.

```xml
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema"
           targetNamespace="http://www.examplebank.com/transactions"
           xmlns="http://www.examplebank.com/transactions"
           elementFormDefault="qualified">

  <!-- Определение корневого элемента -->
  <xs:element name="bankTransaction">
    <xs:complexType>
      <xs:sequence>
        <!-- Уникальный ID транзакции -->
        <xs:element name="transactionId" type="xs:string"/>
        <!-- Дата транзакции -->
        <xs:element name="transactionDate" type="xs:date"/>
        <!-- Выбор типа транзакции (кредит или дебет) -->
        <xs:element name="transactionDetails" type="TransactionDetailsType"/>
      </xs:sequence>
    </xs:complexType>
  </xs:element>

  <!-- Определение типа для деталей транзакции -->
  <xs:complexType name="TransactionDetailsType">
    <xs:sequence>
      <!-- Использование <xs:choice> для выбора между кредитом и дебетом -->
      <xs:choice>
        <xs:element name="credit">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="amount" type="xs:decimal"/>
              <xs:element name="currency" type="xs:string"/>
            </xs:sequence>
          </xs:complexType>
        </xs:element>
        <xs:element name="debit">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="amount" type="xs:decimal"/>
              <xs:element name="currency" type="xs:string"/>
            </xs:sequence>
          </xs:complexType>
        </xs:element>
      </xs:choice>
    </xs:sequence>
  </xs:complexType>

</xs:schema>

```

### Объяснение структуры:

1. **`<xs:schema>`**:
    
    - Определяет схему документа и пространство имён.
    - Атрибут `elementFormDefault="qualified"` требует, чтобы все элементы имели указание пространства имён.
2. **`<xs:element name="bankTransaction">`**:
    
    - Корневой элемент, который описывает банковскую транзакцию.
    - Содержит последовательность элементов: `transactionId`, `transactionDate` и `transactionDetails`.
3. **`<xs:element name="transactionDetails" type="TransactionDetailsType">`**:
    
    - Описывает детали транзакции, где используется сложный тип данных `TransactionDetailsType`.
4. **`<xs:choice>`**:
    
    - Ключевой элемент в этом XSD-документе. Он указывает, что в элементе `transactionDetails` может присутствовать либо элемент `<credit>`, либо элемент `<debit>`, но не оба сразу.
    - Если транзакция — это кредит (например, пополнение счёта), будет использован элемент `<credit>`.
    - Если это дебет (например, списание средств), используется элемент `<debit>`.
5. **`<xs:element name="credit">` и `<xs:element name="debit">`**:
    
    - Описывают альтернативные типы транзакции, которые могут быть выбраны с помощью `<xs:choice>`. Оба элемента содержат сумму транзакции (`amount`) и валюту (`currency`).


 2024-09-15 22:24



[[SOAP]]
#Learn