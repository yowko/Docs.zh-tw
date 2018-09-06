---
title: HOW TO：將物件序列化為 SOAP 編碼的 XML 資料流
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
ms.openlocfilehash: cdfa2c8c7a27806873217495ac09f7f20e82b6bc
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891391"
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>HOW TO：將物件序列化為 SOAP 編碼的 XML 資料流
  
 因為 SOAP 訊息是使用 XML 建置的，所以 <xref:System.Xml.Serialization.XmlSerializer> 類別可用來序列化類別並產生編碼的 SOAP 訊息。 產生的 XML 會與[全球資訊網協會之＜Simple Object Access Protocol (SOAP) 1.1＞文件中的第 5 節](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512)相符。 當您建立透過 SOAP 訊息溝通的 XML Web 服務時，您可以將特殊 SOAP 屬性集套用至類別與類別成員以自訂 XML 資料流。 如需屬性的清單，請參閱[控制編碼 SOAP 序列化的屬性](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)。  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a>將物件序列化為 SOAP 編碼的 XML 資料流  
  
1.  使用 [XML 結構描述定義工具 (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)建立類別。  
  
2.  套用在 `System.Xml.Serialization`中發現的一個或多個特殊屬性。 請參閱＜控制編碼 SOAP 序列化的屬性＞中的清單。  
  
3.  藉由建立新的 `XmlTypeMapping` 及使用已序列化類別的型別叫用 `SoapReflectionImporter` 方法，來建立 `ImportTypeMapping`。  
  
     下列程式碼範例會呼叫 `SoapReflectionImporter` 類別的 `ImportTypeMapping` 方法，以建立 `XmlTypeMapping`。  
  
    ```vb  
    ' Serializes a class named Group as a SOAP message.  
    Dim myTypeMapping As XmlTypeMapping =
        New SoapReflectionImporter().ImportTypeMapping(GetType(Group))  
    ```  
  
    ```csharp  
    // Serializes a class named Group as a SOAP message.  
    XmlTypeMapping myTypeMapping =
        new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
    ```  
  
4.  利用傳遞 `XmlSerializer` 給 `XmlTypeMapping` 建構函式的方式，來建立 <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> 類別的執行個體。  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5.  呼叫 `Serialize` 或 `Deserialize` 方法。  
  
## <a name="example"></a>範例  
  
```vb  
' Serializes a class named Group as a SOAP message.  
Dim myTypeMapping As XmlTypeMapping =
    New SoapReflectionImporter().ImportTypeMapping(GetType(Group))
Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
```  
  
```csharp  
// Serializes a class named Group as a SOAP message.  
XmlTypeMapping myTypeMapping =
    new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
```  
  
## <a name="see-also"></a>另請參閱

- [XML 和 SOAP 序列化](../../../docs/standard/serialization/xml-and-soap-serialization.md)  
- [可控制編碼 SOAP 序列化的屬性](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
- [以 XML Web 服務進行 XML 序列化](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)  
- [如何：序列化物件](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
- [如何：還原序列化物件](../../../docs/standard/serialization/how-to-deserialize-an-object.md)  
- [如何：覆寫已編碼的 SOAP XML 序列化](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)
