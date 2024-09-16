 2024-09-15 22:24

**WSDL (Web Services Description Language)**:

- **Описание веб-сервиса**. WSDL — это XML-документ, который описывает функции веб-сервиса, типы сообщений, которые он принимает и возвращает, и способ взаимодействия с ним. В контексте SOAP WSDL играет роль контракта между клиентом и сервером, который описывает доступные операции и форматы сообщений.

```wsdl
<definitions xmlns="http://schemas.xmlsoap.org/wsdl/"
             xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/"
             xmlns:xs="http://www.w3.org/2001/XMLSchema"
             xmlns:tns="http://www.examplebank.com/transactions"
             targetNamespace="http://www.examplebank.com/transactions"
             name="BankService">

  <!-- Определение типов данных -->
  <types>
    <xs:schema targetNamespace="http://www.examplebank.com/transactions">
      <xs:element name="TransferRequest">
        <xs:complexType>
          <xs:sequence>
            <xs:element name="fromAccount" type="xs:string"/>
            <xs:element name="toAccount" type="xs:string"/>
            <xs:element name="amount" type="xs:decimal"/>
            <xs:element name="currency" type="xs:string"/>
          </xs:sequence>
        </xs:complexType>
      </xs:element>
      <xs:element name="TransferResponse">
        <xs:complexType>
          <xs:sequence>
            <xs:element name="status" type="xs:string"/>
            <xs:element name="transactionId" type="xs:string"/>
          </xs:sequence>
        </xs:complexType>
      </xs:element>
    </xs:schema>
  </types>

  <!-- Определение интерфейса веб-сервиса -->
  <message name="TransferRequestMessage">
    <part name="parameters" element="tns:TransferRequest"/>
  </message>

  <message name="TransferResponseMessage">
    <part name="parameters" element="tns:TransferResponse"/>
  </message>

  <!-- Описание операций веб-сервиса -->
  <portType name="BankServicePortType">
    <operation name="TransferFunds">
      <input message="tns:TransferRequestMessage"/>
      <output message="tns:TransferResponseMessage"/>
    </operation>
  </portType>

  <!-- Привязка операций к протоколу SOAP -->
  <binding name="BankServiceSoapBinding" type="tns:BankServicePortType">
    <soap:binding style="document" transport="http://schemas.xmlsoap.org/soap/http"/>
    <operation name="TransferFunds">
      <soap:operation soapAction="http://www.examplebank.com/TransferFunds"/>
      <input>
        <soap:body use="literal"/>
      </input>
      <output>
        <soap:body use="literal"/>
      </output>
    </operation>
  </binding>

  <!-- Описание сервиса и его доступного адреса -->
  <service name="BankService">
    <port name="BankServiceSoapPort" binding="tns:BankServiceSoapBinding">
      <soap:address location="http://www.examplebank.com/BankService"/>
    </port>
  </service>

</definitions>

```

### Объяснение назначения тегов:

1. **`<definitions>`**:
    
    - Корневой элемент WSDL-документа, который содержит описание веб-сервиса.
    - Внутри этого элемента описываются типы данных, сообщения, операции и адреса сервиса.
    - Атрибуты `xmlns` задают пространства имён для WSDL, SOAP и XML Schema.
2. **`<types>`**:
    
    - Определяет типы данных, которые будут использоваться в веб-сервисе. В данном примере, используется схема XSD для описания структуры запросов и ответов.
    - Внутри этого тега находится `<xs:schema>`, который описывает два элемента:
        - **`TransferRequest`**: содержит информацию о переводе, включая номера счетов, сумму и валюту.
        - **`TransferResponse`**: возвращает результат операции, включая статус и ID транзакции.
3. **`<message>`**:
    
    - Описывает сообщения, которые будут использоваться для обмена данными между клиентом и сервером.
    - В данном примере, два сообщения:
        - **`TransferRequestMessage`**: используется для отправки запроса на перевод средств.
        - **`TransferResponseMessage`**: используется для получения ответа с результатом операции.
    - Каждый `<message>` содержит элемент `<part>`, который указывает на соответствующий элемент данных (например, `tns:TransferRequest`).
4. **`<portType>`**:
    
    - Определяет интерфейс веб-сервиса. В нём перечисляются операции, которые доступны через сервис.
    - В данном примере описана одна операция:
        - **`TransferFunds`**: операция перевода средств, которая принимает запрос (входной параметр `TransferRequestMessage`) и возвращает ответ (выходной параметр `TransferResponseMessage`).
5. **`<binding>`**:
    
    - Описывает, как операции веб-сервиса связаны с конкретным транспортным протоколом (в данном случае, с протоколом SOAP).
    - Важные атрибуты:
        - **`soap:binding`**: указывает, что используется протокол SOAP с передачей данных в формате документа (`style="document"`).
        - **`soap:operation`**: задаёт действие SOAP (например, `soapAction`), которое будет вызвано для данной операции.
6. **`<service>`**:
    
    - Описывает сам веб-сервис и предоставляет информацию о том, как и где он доступен.
    - В данном примере:
        - **`<port>`**: описывает порт, который связывает сервис с определённым протоколом (в данном случае, с SOAP).
        - **`soap:address`**: указывает URL-адрес веб-сервиса, по которому клиенты могут отправлять SOAP-запросы (например, `http://www.examplebank.com/BankService`).

### Как работает WSDL-документ:

Этот WSDL-документ описывает веб-сервис для перевода средств в банковской системе. Клиент может отправить SOAP-запрос на указанный адрес с параметрами, такими как номера счетов, сумма перевода и валюта, а веб-сервис вернёт ответ, который включает статус транзакции и уникальный идентификатор операции.

 Пример SOAP-запроса, соответствующего этому WSDL:

```xml
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/"
                  xmlns:tns="http://www.examplebank.com/transactions">
   <soapenv:Header/>
   <soapenv:Body>
      <tns:TransferRequest>
         <fromAccount>987654321</fromAccount>
         <toAccount>123456789</toAccount>
         <amount>1000.00</amount>
         <currency>USD</currency>
      </tns:TransferRequest>
   </soapenv:Body>
</soapenv:Envelope>

```

Этот запрос отправляет запрос на перевод средств от одного счета к другому, и веб-сервис, описанный в WSDL, обработает этот запрос и вернёт ответ с результатом.

[[SOAP]]
#Learn