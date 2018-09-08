---
title: HOW TO：限定 XML 元素和 XML 屬性名稱
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- qualifying XML names
- qualifying XML elements
- XML namespaces, qualifying elements and names in
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
ms.openlocfilehash: 3c477923387e5a28dcc14b44b0f77bb6acb686e5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44192388"
---
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a><span data-ttu-id="0215a-102">HOW TO：限定 XML 元素和 XML 屬性名稱</span><span class="sxs-lookup"><span data-stu-id="0215a-102">How to: Qualify XML Element and XML Attribute Names</span></span>

<span data-ttu-id="0215a-103">執行個體所包含的 XML 命名空間<xref:System.Xml.Serialization.XmlSerializerNamespaces>類別必須符合全球資訊網協會 (W3C) 規格[Namespaces in XML](https://www.w3.org/TR/REC-xml-names/)。</span><span class="sxs-lookup"><span data-stu-id="0215a-103">XML namespaces contained by instances of the <xref:System.Xml.Serialization.XmlSerializerNamespaces> class must conform to the World Wide Web Consortium (W3C) specification called [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/).</span></span>

<span data-ttu-id="0215a-104">XML 命名空間提供限定 XML 文件中 XML 項目和 XML 屬性名稱的方法。</span><span class="sxs-lookup"><span data-stu-id="0215a-104">XML namespaces provide a method for qualifying the names of XML elements and XML attributes in XML documents.</span></span> <span data-ttu-id="0215a-105">限定名稱 (Qualified Name) 是由前置詞和本機名稱所組成，並以半形冒號 (:) 隔開。</span><span class="sxs-lookup"><span data-stu-id="0215a-105">A qualified name consists of a prefix and a local name, separated by a colon.</span></span> <span data-ttu-id="0215a-106">前置詞的作用只是個替代符號 (Placeholder)，它會對應到指定命名空間的 URI。</span><span class="sxs-lookup"><span data-stu-id="0215a-106">The prefix functions only as a placeholder; it is mapped to a URI that specifies a namespace.</span></span> <span data-ttu-id="0215a-107">通用管理的 URI 命名空間和本機名稱的組合會產生保證是通用唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="0215a-107">The combination of the universally managed URI namespace and the local name produces a name that is guaranteed to be universally unique.</span></span>

<span data-ttu-id="0215a-108">藉由建立 `XmlSerializerNamespaces` 執行個體以及將命名空間配對加入物件中，您可指定 XML 文件使用的前置詞。</span><span class="sxs-lookup"><span data-stu-id="0215a-108">By creating an instance of `XmlSerializerNamespaces` and adding the namespace pairs to the object, you can specify the prefixes used in an XML document.</span></span>

## <a name="to-create-qualified-names-in-an-xml-document"></a><span data-ttu-id="0215a-109">若要在 XML 文件中建立限定名稱</span><span class="sxs-lookup"><span data-stu-id="0215a-109">To create qualified names in an XML document</span></span>

1. <span data-ttu-id="0215a-110">建立 `XmlSerializerNamespaces` 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0215a-110">Create an instance of the `XmlSerializerNamespaces` class.</span></span>

2. <span data-ttu-id="0215a-111">加入所有前置詞與命名空間配對至 `XmlSerializerNamespaces`。</span><span class="sxs-lookup"><span data-stu-id="0215a-111">Add all prefixes and namespace pairs to the `XmlSerializerNamespaces`.</span></span>

3. <span data-ttu-id="0215a-112">套用適當的 `System.Xml.Serialization` 屬性至 <xref:System.Xml.Serialization.XmlSerializer> 將要序列化至 XML 文件的每個成員或類別。</span><span class="sxs-lookup"><span data-stu-id="0215a-112">Apply the appropriate `System.Xml.Serialization` attribute to each member or class that the <xref:System.Xml.Serialization.XmlSerializer> is to serialize into an XML document.</span></span>

  <span data-ttu-id="0215a-113">可用的屬性為：<xref:System.Xml.Serialization.XmlAnyElementAttribute>、<xref:System.Xml.Serialization.XmlArrayAttribute>、<xref:System.Xml.Serialization.XmlArrayItemAttribute>、<xref:System.Xml.Serialization.XmlAttributeAttribute>、<xref:System.Xml.Serialization.XmlElementAttribute>、<xref:System.Xml.Serialization.XmlRootAttribute> 與 <xref:System.Xml.Serialization.XmlTypeAttribute>。</span><span class="sxs-lookup"><span data-stu-id="0215a-113">The available attributes are: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span>

4. <span data-ttu-id="0215a-114">將每個屬性 (Attribute) 的 `Namespace` 屬性 (Property) 設定為 `XmlSerializerNamespaces` 的其中一個命名空間值。</span><span class="sxs-lookup"><span data-stu-id="0215a-114">Set the `Namespace` property of each attribute to one of the namespace values from the `XmlSerializerNamespaces`.</span></span>

5. <span data-ttu-id="0215a-115">傳遞 `XmlSerializerNamespaces` 至 `Serialize` 的 `XmlSerializer` 方法。</span><span class="sxs-lookup"><span data-stu-id="0215a-115">Pass the `XmlSerializerNamespaces` to the `Serialize` method of the `XmlSerializer`.</span></span>

## <a name="example"></a><span data-ttu-id="0215a-116">範例</span><span class="sxs-lookup"><span data-stu-id="0215a-116">Example</span></span>

<span data-ttu-id="0215a-117">下列範例建立 `XmlSerializerNamespaces`，並在物件加入兩個前置詞和命名空間配對。</span><span class="sxs-lookup"><span data-stu-id="0215a-117">The following example creates an `XmlSerializerNamespaces`, and adds two prefix and namespace pairs to the object.</span></span> <span data-ttu-id="0215a-118">程式碼建立用來系列化 `XmlSerializer` 類別執行個體的 `Books`。</span><span class="sxs-lookup"><span data-stu-id="0215a-118">The code creates an `XmlSerializer` that is used to serialize an instance of the `Books` class.</span></span> <span data-ttu-id="0215a-119">程式碼以 `Serialize``XmlSerializerNamespaces`呼叫  方法，讓 XML 能包含有前置詞的命名空間。</span><span class="sxs-lookup"><span data-stu-id="0215a-119">The code calls the `Serialize` method with the `XmlSerializerNamespaces`, allowing the XML to contain prefixed namespaces.</span></span>

```vb
Option Explicit
public class Price
{
    [XmlAttribute(Namespace = "http://www.cpandl.com")]
    public string currency;
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public decimal price;
}

Option Strict

Imports System
Imports System.IO
Imports System.Xml
Imports System.Xml.Serialization

Public Class Run

    Public Shared Sub Main()
        Dim test As New Run()
        test.SerializeObject("XmlNamespaces.xml")
    End Sub 'Main

    Public Sub SerializeObject(filename As String)
        Dim mySerializer As New XmlSerializer(GetType(Books))
        ' Writing a file requires a TextWriter.
        Dim myWriter As New StreamWriter(filename)

        ' Creates an XmlSerializerNamespaces and adds two
        ' prefix-namespace pairs.
        Dim myNamespaces As New XmlSerializerNamespaces()
        myNamespaces.Add("books", "http://www.cpandl.com")
        myNamespaces.Add("money", "http://www.cohowinery.com")

        ' Creates a Book.
        Dim myBook As New Book()
        myBook.TITLE = "A Book Title"
        Dim myPrice As New Price()
        myPrice.price = CDec(9.95)
        myPrice.currency = "US Dollar"
        myBook.PRICE = myPrice
        Dim myBooks As New Books()
        myBooks.Book = myBook
        mySerializer.Serialize(myWriter, myBooks, myNamespaces)
        myWriter.Close()
    End Sub
End Class

Public Class Books
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public Book As Book
End Class 'Books

<XmlType([Namespace] := "http://www.cpandl.com")> _
Public Class Book

    <XmlElement([Namespace] := "http://www.cpandl.com")> _
    Public TITLE As String
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public PRICE As Price
End Class

Public Class Price
    <XmlAttribute([Namespace] := "http://www.cpandl.com")> _
    Public currency As String
    Public <XmlElement([Namespace] := "http://www.cohowinery.com")> _
        price As Decimal
End Class
```

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Serialization;

public class Run
{
    public static void Main()
    {
        Run test = new Run();
        test.SerializeObject("XmlNamespaces.xml");
    }
    public void SerializeObject(string filename)
    {
        XmlSerializer mySerializer = new XmlSerializer(typeof(Books));
        // Writing a file requires a TextWriter.
        TextWriter myWriter = new StreamWriter(filename);

        // Creates an XmlSerializerNamespaces and adds two
        // prefix-namespace pairs.
        XmlSerializerNamespaces myNamespaces =
        new XmlSerializerNamespaces();
        myNamespaces.Add("books", "http://www.cpandl.com");
        myNamespaces.Add("money", "http://www.cohowinery.com");

        // Creates a Book.
        Book myBook = new Book();
        myBook.TITLE = "A Book Title";
        Price myPrice = new Price();
        myPrice.price = (decimal) 9.95;
        myPrice.currency = "US Dollar";
        myBook.PRICE = myPrice;
        Books myBooks = new Books();
        myBooks.Book = myBook;
        mySerializer.Serialize(myWriter,myBooks,myNamespaces);
        myWriter.Close();
    }
}

public class Books
{
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public Book Book;
}

[XmlType(Namespace ="http://www.cpandl.com")]
public class Book
{
    [XmlElement(Namespace = "http://www.cpandl.com")]
    public string TITLE;
    [XmlElement(Namespace ="http://www.cohowinery.com")]
    public Price PRICE;
}
```

## <a name="see-also"></a><span data-ttu-id="0215a-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0215a-120">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="0215a-121">XML 結構描述定義工具和 XML 序列化</span><span class="sxs-lookup"><span data-stu-id="0215a-121">The XML Schema Definition Tool and XML Serialization</span></span>](the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="0215a-122">XML 序列化簡介</span><span class="sxs-lookup"><span data-stu-id="0215a-122">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="0215a-123">XmlSerializer 類別</span><span class="sxs-lookup"><span data-stu-id="0215a-123">XmlSerializer Class</span></span>](xref:System.Xml.Serialization.XmlSerializer)
- [<span data-ttu-id="0215a-124">可控制 XML 序列化的屬性</span><span class="sxs-lookup"><span data-stu-id="0215a-124">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)
- [<span data-ttu-id="0215a-125">如何：指定 XML 資料流的替代元素名稱</span><span class="sxs-lookup"><span data-stu-id="0215a-125">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [<span data-ttu-id="0215a-126">如何：序列化物件</span><span class="sxs-lookup"><span data-stu-id="0215a-126">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="0215a-127">如何：還原序列化物件</span><span class="sxs-lookup"><span data-stu-id="0215a-127">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
