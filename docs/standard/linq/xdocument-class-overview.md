---
title: XDocument 類別總覽
description: LINQ to XML 的 XDocument 類別包含有效 XML 檔所需的資訊。 在許多情況下，您不需要 XDocument 物件的功能，也可以改用 System.xml.linq.xelement> 物件。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 63305603-ab54-49fc-84e4-f76eecc59549
ms.openlocfilehash: c26b7ac42733aad24d831f4a0a181e0fd8275eaf
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552107"
---
# <a name="xdocument-class-overview"></a><span data-ttu-id="d15c9-104">XDocument 類別總覽</span><span class="sxs-lookup"><span data-stu-id="d15c9-104">XDocument class overview</span></span>

<span data-ttu-id="d15c9-105"><xref:System.Xml.Linq.XDocument>類別包含有效 xml 檔所需的資訊，其中包括 XML 宣告、處理指示和批註。</span><span class="sxs-lookup"><span data-stu-id="d15c9-105">The <xref:System.Xml.Linq.XDocument> class contains the information necessary for a valid XML document, which includes an XML declaration, processing instructions, and comments.</span></span>

<span data-ttu-id="d15c9-106"><xref:System.Xml.Linq.XDocument>如果您需要類別所提供的特定功能，您只需要建立物件 <xref:System.Xml.Linq.XDocument> 。</span><span class="sxs-lookup"><span data-stu-id="d15c9-106">You only have to create <xref:System.Xml.Linq.XDocument> objects if you require the specific functionality provided by the <xref:System.Xml.Linq.XDocument> class.</span></span> <span data-ttu-id="d15c9-107">在許多情況下，您可以直接使用 <xref:System.Xml.Linq.XElement>。</span><span class="sxs-lookup"><span data-stu-id="d15c9-107">In many circumstances, you can work directly with <xref:System.Xml.Linq.XElement>.</span></span> <span data-ttu-id="d15c9-108">直接使用 <xref:System.Xml.Linq.XElement> 是較簡單的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="d15c9-108">Working directly with <xref:System.Xml.Linq.XElement> is a simpler programming model.</span></span>

<span data-ttu-id="d15c9-109"><xref:System.Xml.Linq.XDocument> 衍生自 <xref:System.Xml.Linq.XContainer> ，因此可以包含子節點。</span><span class="sxs-lookup"><span data-stu-id="d15c9-109"><xref:System.Xml.Linq.XDocument> derives from <xref:System.Xml.Linq.XContainer>, so it can contain child nodes.</span></span> <span data-ttu-id="d15c9-110">不過，<xref:System.Xml.Linq.XDocument> 物件可以有只有一個 <xref:System.Xml.Linq.XElement> 子節點。</span><span class="sxs-lookup"><span data-stu-id="d15c9-110">However, <xref:System.Xml.Linq.XDocument> objects can have only one child <xref:System.Xml.Linq.XElement> node.</span></span> <span data-ttu-id="d15c9-111">這會反映 XML 標準，也就是說 XML 文件中只能有一個根項目 (Root Element)。</span><span class="sxs-lookup"><span data-stu-id="d15c9-111">This reflects the XML standard that there can be only one root element in an XML document.</span></span>

## <a name="components-of-xdocument"></a><span data-ttu-id="d15c9-112">XDocument 的元件</span><span class="sxs-lookup"><span data-stu-id="d15c9-112">Components of XDocument</span></span>

<span data-ttu-id="d15c9-113"><xref:System.Xml.Linq.XDocument> 可以包含下列項目：</span><span class="sxs-lookup"><span data-stu-id="d15c9-113">An <xref:System.Xml.Linq.XDocument> can contain the following elements:</span></span>

- <span data-ttu-id="d15c9-114">一個 <xref:System.Xml.Linq.XDeclaration> 物件。</span><span class="sxs-lookup"><span data-stu-id="d15c9-114">One <xref:System.Xml.Linq.XDeclaration> object.</span></span> <span data-ttu-id="d15c9-115"><xref:System.Xml.Linq.XDeclaration> 可讓您指定 XML 宣告的相關部分： XML 版本、檔的編碼，以及 XML 檔是否是獨立的。</span><span class="sxs-lookup"><span data-stu-id="d15c9-115"><xref:System.Xml.Linq.XDeclaration> enables you to specify the pertinent parts of an XML declaration: the XML version, the encoding of the document, and whether the XML document is standalone.</span></span>
- <span data-ttu-id="d15c9-116">一個 <xref:System.Xml.Linq.XElement> 物件。</span><span class="sxs-lookup"><span data-stu-id="d15c9-116">One <xref:System.Xml.Linq.XElement> object.</span></span> <span data-ttu-id="d15c9-117">此物件是 XML 檔的根節點。</span><span class="sxs-lookup"><span data-stu-id="d15c9-117">This object is the root node of the XML document.</span></span>
- <span data-ttu-id="d15c9-118">任何數目的 <xref:System.Xml.Linq.XProcessingInstruction> 物件。</span><span class="sxs-lookup"><span data-stu-id="d15c9-118">Any number of <xref:System.Xml.Linq.XProcessingInstruction> objects.</span></span> <span data-ttu-id="d15c9-119">處理指示會將資訊傳達到處理 XML 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d15c9-119">A processing instruction communicates information to an application that processes the XML.</span></span>
- <span data-ttu-id="d15c9-120">任何數目的 <xref:System.Xml.Linq.XComment> 物件。</span><span class="sxs-lookup"><span data-stu-id="d15c9-120">Any number of <xref:System.Xml.Linq.XComment> objects.</span></span> <span data-ttu-id="d15c9-121">這些註解將是根項目的同層級。</span><span class="sxs-lookup"><span data-stu-id="d15c9-121">The comments will be siblings to the root element.</span></span> <span data-ttu-id="d15c9-122">物件不能 <xref:System.Xml.Linq.XComment> 是清單中的第一個引數，因為它對於 XML 檔的開頭不能是批註。</span><span class="sxs-lookup"><span data-stu-id="d15c9-122">The <xref:System.Xml.Linq.XComment> object can't be the first argument in the list, because it's not valid for an XML document to start with a comment.</span></span>
- <span data-ttu-id="d15c9-123">一個適用於 DTD 的 <xref:System.Xml.Linq.XDocumentType>。</span><span class="sxs-lookup"><span data-stu-id="d15c9-123">One <xref:System.Xml.Linq.XDocumentType> for the DTD.</span></span>

<span data-ttu-id="d15c9-124">當您序列化 <xref:System.Xml.Linq.XDocument> 時，即使 `XDocument.Declaration` 為 `null`，如果寫入器已將 `Writer.Settings.OmitXmlDeclaration` 設定為 `false` (預設值)，則輸出將會有 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="d15c9-124">When you serialize an <xref:System.Xml.Linq.XDocument>, even if `XDocument.Declaration` is `null`, the output will have an XML declaration if the writer has `Writer.Settings.OmitXmlDeclaration` set to `false` (the default).</span></span>

<span data-ttu-id="d15c9-125">根據預設，LINQ to XML 會將版本設定為 "1.0"，並將編碼設定為 "utf-8"。</span><span class="sxs-lookup"><span data-stu-id="d15c9-125">By default, LINQ to XML sets the version to "1.0", and sets the encoding to "utf-8".</span></span>

## <a name="use-xelement-without-xdocument"></a><span data-ttu-id="d15c9-126">使用 System.xml.linq.xelement> 而不 XDocument</span><span class="sxs-lookup"><span data-stu-id="d15c9-126">Use XElement without XDocument</span></span>

<span data-ttu-id="d15c9-127">如先前所述， <xref:System.Xml.Linq.XElement> 類別是 LINQ to XML 程式設計介面中的主要類別。</span><span class="sxs-lookup"><span data-stu-id="d15c9-127">As previously mentioned, the <xref:System.Xml.Linq.XElement> class is the main class in the LINQ to XML programming interface.</span></span> <span data-ttu-id="d15c9-128">在許多情況下，您的應用程式不需要建立檔。</span><span class="sxs-lookup"><span data-stu-id="d15c9-128">In many cases, your application won't require that you create a document.</span></span> <span data-ttu-id="d15c9-129">藉由使用 <xref:System.Xml.Linq.XElement> 類別，您可以：</span><span class="sxs-lookup"><span data-stu-id="d15c9-129">By using the <xref:System.Xml.Linq.XElement> class, you can:</span></span>

- <span data-ttu-id="d15c9-130">建立 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="d15c9-130">Create an XML tree.</span></span>
- <span data-ttu-id="d15c9-131">將其他 XML 樹狀結構新增至其中。</span><span class="sxs-lookup"><span data-stu-id="d15c9-131">Add other XML trees to it.</span></span>
- <span data-ttu-id="d15c9-132">修改 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="d15c9-132">Modify the XML tree.</span></span>
- <span data-ttu-id="d15c9-133">將其儲存。</span><span class="sxs-lookup"><span data-stu-id="d15c9-133">Save it.</span></span>

## <a name="use-xdocument"></a><span data-ttu-id="d15c9-134">使用 XDocument</span><span class="sxs-lookup"><span data-stu-id="d15c9-134">Use XDocument</span></span>

<span data-ttu-id="d15c9-135">若要建構 <xref:System.Xml.Linq.XDocument>，請使用功能結構，如同您建構 <xref:System.Xml.Linq.XElement> 物件時所執行的操作。</span><span class="sxs-lookup"><span data-stu-id="d15c9-135">To construct an <xref:System.Xml.Linq.XDocument>, use functional construction, just like you do to construct <xref:System.Xml.Linq.XElement> objects.</span></span>

<span data-ttu-id="d15c9-136">下列範例會建立 <xref:System.Xml.Linq.XDocument> 物件及其相關聯的包含物件。</span><span class="sxs-lookup"><span data-stu-id="d15c9-136">The following example creates an <xref:System.Xml.Linq.XDocument> object and its associated contained objects.</span></span>

```csharp
XDocument d = new XDocument(
    new XComment("This is a comment."),
    new XProcessingInstruction("xml-stylesheet",
        "href='mystyle.css' title='Compact' type='text/css'"),
    new XElement("Pubs",
        new XElement("Book",
            new XElement("Title", "Artifacts of Roman Civilization"),
            new XElement("Author", "Moreno, Jordao")
        ),
        new XElement("Book",
            new XElement("Title", "Midieval Tools and Implements"),
            new XElement("Author", "Gazit, Inbar")
        )
    ),
    new XComment("This is another comment.")
);
d.Declaration = new XDeclaration("1.0", "utf-8", "true");
Console.WriteLine(d);

d.Save("test.xml");
```

```vb
Dim doc As XDocument = <?xml version="1.0" encoding="utf-8"?>
                       <!--This is a comment.-->
                       <?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>
                       <Pubs>
                           <Book>
                               <Title>Artifacts of Roman Civilization</Title>
                               <Author>Moreno, Jordao</Author>
                           </Book>
                           <Book>
                               <Title>Midieval Tools and Implements</Title>
                               <Author>Gazit, Inbar</Author>
                           </Book>
                       </Pubs>
                       <!--This is another comment.-->
doc.Save("test.xml")
```

<span data-ttu-id="d15c9-137">此範例會在 test.xml 中產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="d15c9-137">The example produces this output in test.xml:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<!--This is a comment.-->
<?xml-stylesheet href='mystyle.css' title='Compact' type='text/css'?>
<Pubs>
  <Book>
    <Title>Artifacts of Roman Civilization</Title>
    <Author>Moreno, Jordao</Author>
  </Book>
  <Book>
    <Title>Midieval Tools and Implements</Title>
    <Author>Gazit, Inbar</Author>
  </Book>
</Pubs>
<!--This is another comment.-->
```

## <a name="see-also"></a><span data-ttu-id="d15c9-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d15c9-138">See also</span></span>

- [<span data-ttu-id="d15c9-139">LINQ to XML 總覽</span><span class="sxs-lookup"><span data-stu-id="d15c9-139">LINQ to XML overview</span></span>](linq-xml-overview.md)
