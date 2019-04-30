---
title: HOW TO：指定 XML 資料流的替代項目名稱
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- XML serialization, overriding
- serialization, overriding
- XML stream, specifying alternate element name for
- overriding XML serialization
- classes, overriding
- overriding classes
ms.assetid: 5cc1c0b0-f94b-4525-9a41-88a582cd6668
ms.openlocfilehash: 577b96517632ca1ae06891540f22c2c3c3886cd1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62018004"
---
# <a name="how-to-specify-an-alternate-element-name-for-an-xml-stream"></a><span data-ttu-id="e53b4-102">HOW TO：指定 XML 資料流的替代項目名稱</span><span class="sxs-lookup"><span data-stu-id="e53b4-102">How to: Specify an Alternate Element Name for an XML Stream</span></span>
  
<span data-ttu-id="e53b4-103">使用 <xref:System.Xml.Serialization.XmlSerializer>，以相同類別集，可產生一個以上的 XML 資料流。</span><span class="sxs-lookup"><span data-stu-id="e53b4-103">Using the <xref:System.Xml.Serialization.XmlSerializer>, you can generate more than one XML stream with the same set of classes.</span></span> <span data-ttu-id="e53b4-104">當兩個不同的 XML Web 服務要求相同的基本資訊以及些微差異時，您也許會想這麼做。</span><span class="sxs-lookup"><span data-stu-id="e53b4-104">You might want to do this because two different XML Web services require the same basic information, with only slight differences.</span></span> <span data-ttu-id="e53b4-105">例如，試想有兩家處理書本訂單的 XML Web 服務，而且都需要 ISBN 號碼。</span><span class="sxs-lookup"><span data-stu-id="e53b4-105">For example, imagine two XML Web services that process orders for books, and thus both require ISBN numbers.</span></span> <span data-ttu-id="e53b4-106">一個服務使用標記 \<ISBN>，另一個則使用標記 \<BookID>。</span><span class="sxs-lookup"><span data-stu-id="e53b4-106">One service uses the tag \<ISBN> while the second uses the tag \<BookID>.</span></span> <span data-ttu-id="e53b4-107">您有名為 `Book` 的類別，其中包含名為 `ISBN`的欄位。</span><span class="sxs-lookup"><span data-stu-id="e53b4-107">You have a class named `Book` that contains a field named `ISBN`.</span></span> <span data-ttu-id="e53b4-108">當 `Book` 類別的執行個體序列化時，它會根據預設使用成員名稱 (ISBN) 做為標記項目名稱。</span><span class="sxs-lookup"><span data-stu-id="e53b4-108">When an instance of the `Book` class is serialized, it will, by default, use the member name (ISBN) as the tag element name.</span></span> <span data-ttu-id="e53b4-109">對於第一個 XML Web 服務，這正如預期。</span><span class="sxs-lookup"><span data-stu-id="e53b4-109">For the first XML Web service, this is as expected.</span></span> <span data-ttu-id="e53b4-110">不過要想要傳送 XML 資料流至第二個 XML Web 服務，您必須覆寫序列化，讓標記的項目名稱為 `BookID`。</span><span class="sxs-lookup"><span data-stu-id="e53b4-110">But to send the XML stream to the second XML Web service, you must override the serialization so that the tag's element name is `BookID`.</span></span>  
  
## <a name="to-create-an-xml-stream-with-an-alternate-element-name"></a><span data-ttu-id="e53b4-111">以其他項目名稱建立 XML 資料流</span><span class="sxs-lookup"><span data-stu-id="e53b4-111">To create an XML stream with an alternate element name</span></span>  
  
1. <span data-ttu-id="e53b4-112">建立 <xref:System.Xml.Serialization.XmlElementAttribute> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e53b4-112">Create an instance of the <xref:System.Xml.Serialization.XmlElementAttribute> class.</span></span>  
  
2. <span data-ttu-id="e53b4-113">將 <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> 的 <xref:System.Xml.Serialization.XmlElementAttribute> 設為 "BookID"。</span><span class="sxs-lookup"><span data-stu-id="e53b4-113">Set the <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> of the <xref:System.Xml.Serialization.XmlElementAttribute> to "BookID".</span></span>  
  
3. <span data-ttu-id="e53b4-114">建立 <xref:System.Xml.Serialization.XmlAttributes> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e53b4-114">Create an instance of the <xref:System.Xml.Serialization.XmlAttributes> class.</span></span>  
  
4. <span data-ttu-id="e53b4-115">將 `XmlElementAttribute` 物件加入至透過 <xref:System.Xml.Serialization.XmlAttributes.XmlElements%2A> 之 <xref:System.Xml.Serialization.XmlAttributes> 屬性存取的集合。</span><span class="sxs-lookup"><span data-stu-id="e53b4-115">Add the `XmlElementAttribute` object to the collection accessed through the <xref:System.Xml.Serialization.XmlAttributes.XmlElements%2A> property of <xref:System.Xml.Serialization.XmlAttributes> .</span></span>  
  
5. <span data-ttu-id="e53b4-116">建立 <xref:System.Xml.Serialization.XmlAttributeOverrides> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e53b4-116">Create an instance of the <xref:System.Xml.Serialization.XmlAttributeOverrides> class.</span></span>  
  
6. <span data-ttu-id="e53b4-117">將 `XmlAttributes` 加入至 <xref:System.Xml.Serialization.XmlAttributeOverrides>，傳遞要覆寫的物件型別及遭覆寫的成員名稱。</span><span class="sxs-lookup"><span data-stu-id="e53b4-117">Add the `XmlAttributes` to the <xref:System.Xml.Serialization.XmlAttributeOverrides>, passing the type of the object to override and the name of the member being overridden.</span></span>  
  
7. <span data-ttu-id="e53b4-118">使用 `XmlSerializer``XmlAttributeOverrides`建立  類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="e53b4-118">Create an instance of the `XmlSerializer` class with `XmlAttributeOverrides`.</span></span>  
  
8. <span data-ttu-id="e53b4-119">建立 `Book` 類別的執行個體，將它序列化或還原序列化。</span><span class="sxs-lookup"><span data-stu-id="e53b4-119">Create an instance of the `Book` class, and serialize or deserialize it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e53b4-120">範例</span><span class="sxs-lookup"><span data-stu-id="e53b4-120">Example</span></span>  
  
```vb  
Public Class SerializeOverride()  
    ' Creates an XmlElementAttribute with the alternate name.  
    Dim myElementAttribute As XmlElementAttribute = _  
    New XmlElementAttribute()  
    myElementAttribute.ElementName = "BookID"  
    Dim myAttributes As XmlAttributes = New XmlAttributes()  
    myAttributes.XmlElements.Add(myElementAttribute)  
    Dim myOverrides As XmlAttributeOverrides = New XmlAttributeOverrides()  
    myOverrides.Add(typeof(Book), "ISBN", myAttributes)  
    Dim mySerializer As XmlSerializer = _  
    New XmlSerializer(GetType(Book), myOverrides)  
    Dim b As Book = New Book()  
    b.ISBN = "123456789"  
    ' Creates a StreamWriter to write the XML stream to.  
    Dim writer As StreamWriter = New StreamWriter("Book.xml")  
    mySerializer.Serialize(writer, b);  
End Class  
```  
  
```csharp  
public class SerializeOverride()  
{  
    // Creates an XmlElementAttribute with the alternate name.  
    XmlElementAttribute myElementAttribute = new XmlElementAttribute();  
    myElementAttribute.ElementName = "BookID";  
    XmlAttributes myAttributes = new XmlAttributes();  
    myAttributes.XmlElements.Add(myElementAttribute);  
    XmlAttributeOverrides myOverrides = new XmlAttributeOverrides();  
    myOverrides.Add(typeof(Book), "ISBN", myAttributes);  
    XmlSerializer mySerializer =   
    new XmlSerializer(typeof(Book), myOverrides)  
    Book b = new Book();  
    b.ISBN = "123456789"  
    // Creates a StreamWriter to write the XML stream to.  
    StreamWriter writer = new StreamWriter("Book.xml");  
    mySerializer.Serialize(writer, b);  
}  
```  
  
 <span data-ttu-id="e53b4-121">XML 資料流可能類似下列所示。</span><span class="sxs-lookup"><span data-stu-id="e53b4-121">The XML stream might resemble the following.</span></span>  
  
```xml  
<Book>  
    <BookID>123456789</BookID>  
</Book>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e53b4-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e53b4-122">See also</span></span>

- <xref:System.Xml.Serialization.XmlElementAttribute>
- <xref:System.Xml.Serialization.XmlAttributes>
- <xref:System.Xml.Serialization.XmlAttributeOverrides>
- [<span data-ttu-id="e53b4-123">XML 和 SOAP 序列化</span><span class="sxs-lookup"><span data-stu-id="e53b4-123">XML and SOAP Serialization</span></span>](../../../docs/standard/serialization/xml-and-soap-serialization.md)
- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="e53b4-124">如何：將物件序列化</span><span class="sxs-lookup"><span data-stu-id="e53b4-124">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)
- [<span data-ttu-id="e53b4-125">如何：還原序列化物件</span><span class="sxs-lookup"><span data-stu-id="e53b4-125">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
