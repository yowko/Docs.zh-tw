---
title: "以 XML Web 服務進行 XML 序列化 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - ".asmx 檔案"
  - "asmx 檔案"
  - "屬性 [.NET Framework], XML 序列化"
  - "已編碼的 XML 序列化"
  - "常值 XML 序列化"
  - "序列化, 屬性"
  - "序列化, SOAP"
  - "SOAP, XML 序列化"
  - "XML 序列化, 屬性"
  - "XML 序列化, XML Web Service"
  - "XML Web Service, XML 序列化"
ms.assetid: a416192f-8102-458e-bc0a-0b8f3f784da9
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 以 XML Web 服務進行 XML 序列化
XML 序列化為 XML Web 服務架構中使用的基礎傳輸機制，由 [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx) 類別執行。若要控制 XML Web 服務產生的 XML，可將列在[控制 XML 序列化的屬性](../../../docs/framework/serialization/attributes-that-control-xml-serialization.md)和[控制編碼 SOAP 序列化的屬性](../../../docs/framework/serialization/attributes-that-control-encoded-soap-serialization.md)的屬性，套用至用來建立 XML Web 服務 \(.asmx\) 之檔案的類別、傳回值、參數以及欄位。如需建立 XML Web 服務的詳細資訊，請參閱[Building XML Web Services Using ASP.NET](http://msdn.microsoft.com/zh-tw/01dfc27c-c68e-4910-a0aa-5e4c2a766b0c)。  
  
## 常值與編碼樣式  
 XML Web 服務產生的 XML 可使用常值或編碼的其中一種方式格式化，如[Customizing SOAP Messages](http://msdn.microsoft.com/zh-tw/1d777288-c0d9-4e6a-b638-f010da031952)中所述。因此有兩組屬性控制 XML 序列化。[控制 XML 序列化的屬性](../../../docs/framework/serialization/attributes-that-control-xml-serialization.md)列出的屬性，是為控制常值樣式 XML 而設計。[控制編碼 SOAP 序列化的屬性](../../../docs/framework/serialization/attributes-that-control-encoded-soap-serialization.md)中所列的屬性會控制編碼樣式。您可選擇性地套用這些屬性，自訂應用程式傳回其中一種或同時兩種樣式。除此之外，可將這些屬性套用至傳回值和參數 \(如果適合的話\)。  
  
### 同時使用兩種樣式的範例  
 當您建立 XML Web 服務，可同時使用方法上的兩組屬性。在下列程式碼範例中，名為 `MyService` 的類別包含兩個 XML Web 服務方法：`MyLiteralMethod` 及 `MyEncodedMethod`。兩種方法都執行相同功能：傳回 `Order` 類別的執行個體。在 `Order` 類別中，[XmlTypeAttribute](frlrfSystemXmlSerializationXmlTypeAttributeClassTopic) 以及 [SoapTypeAttribute](frlrfSystemXmlSerializationSoapTypeAttributeClassTopic) 屬性 \(Attribute\) 都套用至 `OrderID` 欄位，而且兩個屬性 \(Attribute\) 的 `ElementName` 屬性 \(Property\) 都設為不同值。  
  
 若要執行這個範例，請將程式碼貼至副檔名為 .asmx 的檔案中，並將該檔置於 Internet Information Services \(IIS\) 管理的虛擬目錄中。從 Internet Explorer 這類 HTML 瀏覽器中，輸入電腦、虛擬目錄及檔案的名稱。  
  
```vb  
<%@ WebService Language="VB" Class="MyService" %>  
Imports System  
Imports System.Web.Services  
Imports System.Web.Services.Protocols  
Imports System.Xml.Serialization  
Public Class Order  
    ' Both types of attributes can be applied. Depending on which type  
    ' the method used, either one will affect the call.  
    <SoapElement(ElementName:= "EncodedOrderID"), _  
    XmlElement(ElementName:= "LiteralOrderID")> _  
    public OrderID As String  
End Class  
  
Public Class MyService  
    <WebMethod, SoapDocumentMethod> _  
    public Function MyLiteralMethod() As Order   
        Dim myOrder As Order = New Order()  
        return myOrder  
    End Function  
    <WebMethod, SoapRpcMethod> _  
    public Function MyEncodedMethod() As Order   
        Dim myOrder As Order = New Order()  
        return myOrder  
    End Function  
End Class  
  
```  
  
```csharp  
<%@ WebService Language="C#" Class="MyService" %>  
using System;  
using System.Web.Services;  
using System.Web.Services.Protocols;  
using System.Xml.Serialization;  
public class Order{  
    // Both types of attributes can be applied. Depending on which type  
    // the method used, either one will affect the call.  
    [SoapElement(ElementName = "EncodedOrderID")]  
    [XmlElement(ElementName = "LiteralOrderID")]  
    public String OrderID;  
}  
public class MyService{  
    [WebMethod][SoapDocumentMethod]  
    public Order MyLiteralMethod(){  
        Order myOrder = new Order();  
        return myOrder;  
    }  
    [WebMethod][SoapRpcMethod]  
    public Order MyEncodedMethod(){  
        Order myOrder = new Order();  
        return myOrder;  
    }  
}  
```  
  
 下列程式碼範例會呼叫 `MyLiteralMethod`。項目名稱變更為 "LiteralOrderID"。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body>  
        <MyLiteralMethodResponse xmlns="http://tempuri.org/">  
            <MyLiteralMethodResult>  
                <LiteralOrderID>string</LiteralOrderID>  
            </MyLiteralMethodResult>  
        </MyLiteralMethodResponse>  
    </soap:Body>  
</soap:Envelope>  
```  
  
 下列程式碼範例會呼叫 `MyEncodedMethod`。項目名稱為 "EncodedOrderID"。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/" xmlns:tns="http://tempuri.org/" xmlns:types="http://tempuri.org/encodedTypes" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body soap:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
        <tns:MyEncodedMethodResponse>  
            <MyEncodedMethodResult href="#id1" />  
        </tns:MyEncodedMethodResponse>  
        <types:Order id="id1" xsi:type="types:Order">  
            <EncodedOrderID xsi:type="xsd:string">string</EncodedOrderID>  
        </types:Order>  
    </soap:Body>  
</soap:Envelope>  
```  
  
### 套用屬性至傳回值  
 您也可以套用屬性至傳回值以控制命名空間、項目名稱等等。下列程式碼範例套用 `XmlElementAttribute` 屬性至 `MyLiteralMethod` 方法的傳回值。這樣做可以讓您控制命名空間與項目名稱。  
  
```vb  
<WebMethod, SoapDocumentMethod> _  
public Function MyLiteralMethod() As _  
<XmlElement(Namespace:="http://www.cohowinery.com", _  
ElementName:= "BookOrder")> _  
Order   
    Dim myOrder As Order = New Order()  
    return myOrder  
End Function  
  
```  
  
```csharp  
[return: XmlElement(Namespace = "http://www.cohowinery.com",  
ElementName = "BookOrder")]  
[WebMethod][SoapDocumentMethod]  
public Order MyLiteralMethod(){  
    Order myOrder = new Order();  
    return myOrder;  
}  
```  
  
 叫用時，程式碼會傳回類似以下所示的 XML。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body>  
        <MyLiteralMethodResponse xmlns="http://tempuri.org/">  
            <BookOrder xmlns="http://www.cohowinery.com">  
                <LiteralOrderID>string</LiteralOrderID>  
            </BookOrder>  
        </MyLiteralMethodResponse>  
    </soap:Body>  
</soap:Envelope>  
```  
  
### 套用至參數的屬性  
 您也可以套用屬性至參數以指定命名空間、項目名稱等等。下列程式碼範例加入參數至 `MyLiteralMethodResponse` 方法，並套用 `XmlAttributeAttribute` 屬性至參數。項目名稱與命名空間都針對參數設定。  
  
```vb  
<WebMethod, SoapDocumentMethod> _  
public Function MyLiteralMethod(<XmlElement _  
("MyOrderID", Namespace:="http://www.microsoft.com")>ID As String) As _  
<XmlElement(Namespace:="http://www.cohowinery.com", _  
ElementName:= "BookOrder")> _  
Order   
    Dim myOrder As Order = New Order()  
    myOrder.OrderID = ID  
    return myOrder  
End Function  
  
```  
  
```csharp  
[return: XmlElement(Namespace = "http://www.cohowinery.com",  
ElementName = "BookOrder")]  
[WebMethod][SoapDocumentMethod]  
public Order MyLiteralMethod([XmlElement("MyOrderID",   
Namespace="http://www.microsoft.com")] string ID){  
    Order myOrder = new Order();  
    myOrder.OrderID = ID;  
    return myOrder;  
}   
```  
  
 SOAP 要求可能類似下列所示。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">  
    <soap:Body>  
        <MyLiteralMethod xmlns="http://tempuri.org/">  
            <MyOrderID xmlns="http://www.microsoft.com">string</MyOrderID>  
        </MyLiteralMethod>  
    </soap:Body>  
</soap:Envelope>  
```  
  
### 套用屬性至類別  
 若您需要控制類別相互關聯之項目的命名空間，可在適當的情況下套用 `XmlTypeAttribute`、`XmlRootAttribute` 及 `SoapTypeAttribute`。下列程式碼範例將三者全套用至 `Order` 類別。  
  
```vb  
<XmlType("BigBookService"), _  
SoapType("SoapBookService"), _  
XmlRoot("BookOrderForm")> _  
Public Class Order  
    ' Both types of attributes can be applied. Depending on which  
    ' the method used, either one will affect the call.  
    <SoapElement(ElementName:= "EncodedOrderID"), _  
    XmlElement(ElementName:= "LiteralOrderID")> _  
    public OrderID As String  
End Class  
  
```  
  
```csharp  
[XmlType("BigBooksService", Namespace = "http://www.cpandl.com")]  
[SoapType("SoapBookService")]  
[XmlRoot("BookOrderForm")]  
public class Order{  
    // Both types of attributes can be applied. Depending on which  
    // the method used, either one will affect the call.  
    [SoapElement(ElementName = "EncodedOrderID")]  
    [XmlElement(ElementName = "LiteralOrderID")]  
    public String OrderID;  
}  
```  
  
 套用 `XmlTypeAttribute` 及 `SoapTypeAttribute` 的結果可在檢查服務說明時看到，如下列程式碼範例所示。  
  
```  
    <s:element name="BookOrderForm" type="s0:BigBookService" />   
- <s:complexType name="BigBookService">  
- <s:sequence>  
    <s:element minOccurs="0" maxOccurs="1" name="LiteralOrderID" type="s:string" />   
    </s:sequence>  
  
- <s:schema targetNamespace="http://tempuri.org/encodedTypes">  
- <s:complexType name="SoapBookService">  
- <s:sequence>  
    <s:element minOccurs="1" maxOccurs="1" name="EncodedOrderID" type="s:string" />   
    </s:sequence>  
    </s:complexType>  
    </s:schema>  
```  
  
 `XmlRootAttribute` 的效果也可以在 HTTP GET 與 HTTP POST 結果中看到，如下所示。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<BookOrderForm xmlns="http://tempuri.org/">  
    <LiteralOrderID>string</LiteralOrderID>  
</BookOrderForm>  
```  
  
## 請參閱  
 [XML 和 SOAP 序列化](../../../docs/framework/serialization/xml-and-soap-serialization.md)   
 [控制編碼 SOAP 序列化的屬性](../../../docs/framework/serialization/attributes-that-control-encoded-soap-serialization.md)   
 [HOW TO：將物件序列化為 SOAP 編碼的 XML 資料流](../../../docs/framework/serialization/how-to-serialize-an-object-as-a-soap-encoded-xml-stream.md)   
 [HOW TO：覆寫已編碼的 SOAP XML 序列化](../../../docs/framework/serialization/how-to-override-encoded-soap-xml-serialization.md)   
 [XML 序列化簡介](../../../docs/framework/serialization/introducing-xml-serialization.md)   
 [HOW TO：序列化物件](../../../docs/framework/serialization/how-to-serialize-an-object.md)   
 [HOW TO：還原序列化物件](../../../docs/framework/serialization/how-to-deserialize-an-object.md)