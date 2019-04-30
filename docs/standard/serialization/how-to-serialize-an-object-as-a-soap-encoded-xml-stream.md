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
ms.openlocfilehash: bfbdda0861a6f2867a2e7003dd7054129fd343b8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018012"
---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="d691e-102">HOW TO：將物件序列化為 SOAP 編碼的 XML 資料流</span><span class="sxs-lookup"><span data-stu-id="d691e-102">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>
  
 <span data-ttu-id="d691e-103">因為 SOAP 訊息是使用 XML 建置的，所以 <xref:System.Xml.Serialization.XmlSerializer> 類別可用來序列化類別並產生編碼的 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="d691e-103">Because a SOAP message is built using XML, the <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize classes and generate encoded SOAP messages.</span></span> <span data-ttu-id="d691e-104">產生的 XML 會與[全球資訊網協會之＜Simple Object Access Protocol (SOAP) 1.1＞文件中的第 5 節](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512)相符。</span><span class="sxs-lookup"><span data-stu-id="d691e-104">The resulting XML conforms to [section 5 of the World Wide Web Consortium document "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span></span> <span data-ttu-id="d691e-105">當您建立透過 SOAP 訊息溝通的 XML Web 服務時，您可以將特殊 SOAP 屬性集套用至類別與類別成員以自訂 XML 資料流。</span><span class="sxs-lookup"><span data-stu-id="d691e-105">When you are creating an XML Web service that communicates through SOAP messages, you can customize the XML stream by applying a set of special SOAP attributes to classes and members of classes.</span></span> <span data-ttu-id="d691e-106">如需屬性的清單，請參閱[控制編碼 SOAP 序列化的屬性](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="d691e-106">For a list of attributes, see [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="d691e-107">將物件序列化為 SOAP 編碼的 XML 資料流</span><span class="sxs-lookup"><span data-stu-id="d691e-107">To serialize an object as a SOAP-encoded XML stream</span></span>  
  
1. <span data-ttu-id="d691e-108">使用 [XML 結構描述定義工具 (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md)建立類別。</span><span class="sxs-lookup"><span data-stu-id="d691e-108">Create the class using the [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
2. <span data-ttu-id="d691e-109">套用在 `System.Xml.Serialization`中發現的一個或多個特殊屬性。</span><span class="sxs-lookup"><span data-stu-id="d691e-109">Apply one or more of the special attributes found in `System.Xml.Serialization`.</span></span> <span data-ttu-id="d691e-110">請參閱＜控制編碼 SOAP 序列化的屬性＞中的清單。</span><span class="sxs-lookup"><span data-stu-id="d691e-110">See the list in "Attributes That Control Encoded SOAP Serialization."</span></span>  
  
3. <span data-ttu-id="d691e-111">藉由建立新的 `XmlTypeMapping` 及使用已序列化類別的型別叫用 `SoapReflectionImporter` 方法，來建立 `ImportTypeMapping`。</span><span class="sxs-lookup"><span data-stu-id="d691e-111">Create an `XmlTypeMapping` by creating a new `SoapReflectionImporter`, and invoking the `ImportTypeMapping` method with the type of the serialized class.</span></span>  
  
     <span data-ttu-id="d691e-112">下列程式碼範例會呼叫 `SoapReflectionImporter` 類別的 `ImportTypeMapping` 方法，以建立 `XmlTypeMapping`。</span><span class="sxs-lookup"><span data-stu-id="d691e-112">The following code example calls the `ImportTypeMapping` method of the `SoapReflectionImporter` class to create an `XmlTypeMapping`.</span></span>  
  
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
  
4. <span data-ttu-id="d691e-113">利用傳遞 `XmlSerializer` 給 `XmlTypeMapping` 建構函式的方式，來建立 <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="d691e-113">Create an instance of the `XmlSerializer` class by passing the `XmlTypeMapping` to the <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> constructor.</span></span>  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5. <span data-ttu-id="d691e-114">呼叫 `Serialize` 或 `Deserialize` 方法。</span><span class="sxs-lookup"><span data-stu-id="d691e-114">Call the `Serialize` or `Deserialize` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d691e-115">範例</span><span class="sxs-lookup"><span data-stu-id="d691e-115">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d691e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d691e-116">See also</span></span>

- [<span data-ttu-id="d691e-117">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="d691e-117">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
- [<span data-ttu-id="d691e-118">可控制編碼 SOAP 序列化的屬性</span><span class="sxs-lookup"><span data-stu-id="d691e-118">Attributes That Control Encoded SOAP Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)
- [<span data-ttu-id="d691e-119">以 XML Web 服務進行 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="d691e-119">XML Serialization with XML Web Services</span></span>](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md)
- [<span data-ttu-id="d691e-120">如何：將物件序列化</span><span class="sxs-lookup"><span data-stu-id="d691e-120">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="d691e-121">如何：還原序列化物件</span><span class="sxs-lookup"><span data-stu-id="d691e-121">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
- [<span data-ttu-id="d691e-122">如何：覆寫編碼的 SOAP XML 序列化</span><span class="sxs-lookup"><span data-stu-id="d691e-122">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)
