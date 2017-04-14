---
title: "HOW TO：將物件序列化為 SOAP 編碼的 XML 資料流 | Microsoft Docs"
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
  - "序列化, SOAP"
  - "SOAP, XML 序列化"
  - "XML 序列化, SOAP"
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# HOW TO：將物件序列化為 SOAP 編碼的 XML 資料流
[程式碼範例](#cpconxmlserializationusingsoapprotocolanchor1)  
  
 因為 SOAP 訊息是使用 XML 建立的，所以 [XmlSerializer](https://msdn.microsoft.com/en-us/library/system.xml.serialization.xmlserializer.aspx) 可用來序列化類別並產生編碼的 SOAP 訊息。產生的 XML 會與全球資訊網協會 \(www.w3.org\) 之＜Simple Object Access Protocol \(SOAP\) 1.1＞文件中的第 5 節相符。當您建立透過 SOAP 訊息溝通的 XML Web 服務時，您可以將特殊 SOAP 屬性集套用至類別與類別成員以自訂 XML 資料流。如需屬性的列表，請參閱[控制編碼 SOAP 序列化的屬性](../../../docs/framework/serialization/attributes-that-control-encoded-soap-serialization.md)。  
  
### 將物件序列化為 SOAP 編碼的 XML 資料流  
  
1.  使用 [XML 結構描述定義工具 \(Xsd.exe\)](../../../docs/framework/serialization/xml-schema-definition-tool-xsd-exe.md) 建立類別。  
  
2.  套用在 **System.Xml.Serialization** 中發現的一個或多個特殊屬性。請參閱＜控制編碼 SOAP 序列化的屬性＞中的清單。  
  
3.  藉由建立新的 **SoapReflectionImporter** 及使用已序列化類別的型別叫用 **ImportTypeMapping** 方法，來建立 **XmlTypeMapping**。  
  
     下列程式碼範例呼叫 **SoapReflectionImporter** 類型的 **ImportTypeMapping**方法，以建立 **XmlTypeMapping**。  
  
    ```vb  
    ' Serializes a class named Group as a SOAP message.  
    Dim myTypeMapping As XmlTypeMapping = (New SoapReflectionImporter(). _  
    ImportTypeMapping(GetType(Group))  
  
    ```  
  
    ```csharp  
    // Serializes a class named Group as a SOAP message.  
    XmlTypeMapping myTypeMapping = (new SoapReflectionImporter().  
    ImportTypeMapping(typeof(Group));  
    ```  
  
4.  利用傳遞 **XmlTypeMapping** 給 <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> 建構函式的方式，來建立 **XmlSerializer** 類別的執行個體。  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5.  呼叫 **Serialize** 或 **Deserialize** 方法。  
  
## 範例  
  
```vb  
' Serializes a class named Group as a SOAP message.  
Dim myTypeMapping As XmlTypeMapping = (New SoapReflectionImporter(). _  
ImportTypeMapping(GetType(Group))  
Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
  
```  
  
```csharp  
// Serializes a class named Group as a SOAP message.  
XmlTypeMapping myTypeMapping = (new SoapReflectionImporter().ImportTypeMapping(typeof(Group));  
XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
```  
  
## 請參閱  
 [XML 和 SOAP 序列化](../../../docs/framework/serialization/xml-and-soap-serialization.md)   
 [控制編碼 SOAP 序列化的屬性](../../../docs/framework/serialization/attributes-that-control-encoded-soap-serialization.md)   
 [以 XML Web 服務進行 XML 序列化](../../../docs/framework/serialization/xml-serialization-with-xml-web-services.md)   
 [HOW TO：序列化物件](../../../docs/framework/serialization/how-to-serialize-an-object.md)   
 [HOW TO：還原序列化物件](../../../docs/framework/serialization/how-to-deserialize-an-object.md)   
 [HOW TO：覆寫已編碼的 SOAP XML 序列化](../../../docs/framework/serialization/how-to-override-encoded-soap-xml-serialization.md)