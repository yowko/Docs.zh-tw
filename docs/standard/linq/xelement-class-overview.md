---
title: System.xml.linq.xelement> 類別總覽
description: System.xml.linq.xelement> 類別表示 XML 元素。 您可以使用它來建立和變更元素、新增屬性和子系，以及進行序列化。
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 325afd09661532fe44aecf89fe9784520274638e
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552175"
---
# <a name="xelement-class-overview"></a><span data-ttu-id="4ec58-104">System.xml.linq.xelement> 類別總覽</span><span class="sxs-lookup"><span data-stu-id="4ec58-104">XElement class overview</span></span>

<span data-ttu-id="4ec58-105"><xref:System.Xml.Linq.XElement>類別是 LINQ to XML 中的其中一個基礎類別。</span><span class="sxs-lookup"><span data-stu-id="4ec58-105">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in LINQ to XML.</span></span> <span data-ttu-id="4ec58-106">它代表 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="4ec58-106">It represents an XML element.</span></span> <span data-ttu-id="4ec58-107">下列清單顯示您可以使用此類別的內容：</span><span class="sxs-lookup"><span data-stu-id="4ec58-107">The following list shows what you can use this class for:</span></span>

- <span data-ttu-id="4ec58-108">建立元素。</span><span class="sxs-lookup"><span data-stu-id="4ec58-108">Create elements.</span></span>
- <span data-ttu-id="4ec58-109">變更元素的內容。</span><span class="sxs-lookup"><span data-stu-id="4ec58-109">Change the content of the element.</span></span>
- <span data-ttu-id="4ec58-110">加入、變更或刪除子項目。</span><span class="sxs-lookup"><span data-stu-id="4ec58-110">Add, change, or delete child elements.</span></span>
- <span data-ttu-id="4ec58-111">將屬性加入至元素。</span><span class="sxs-lookup"><span data-stu-id="4ec58-111">Add attributes to an element.</span></span>
- <span data-ttu-id="4ec58-112">以文字格式序列化元素的內容。</span><span class="sxs-lookup"><span data-stu-id="4ec58-112">Serialize the contents of an element in text form.</span></span>

<span data-ttu-id="4ec58-113">您也可以與 <xref:System.Xml?displayProperty=nameWithType> 中的其他類別相互溝通，例如，<xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter> 和 <xref:System.Xml.Xsl.XslCompiledTransform>。</span><span class="sxs-lookup"><span data-stu-id="4ec58-113">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>

<span data-ttu-id="4ec58-114">本文描述類別所提供的功能 <xref:System.Xml.Linq.XElement> 。</span><span class="sxs-lookup"><span data-stu-id="4ec58-114">This article describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>

## <a name="construct-xml-trees"></a><span data-ttu-id="4ec58-115">結構 XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="4ec58-115">Construct XML trees</span></span>

<span data-ttu-id="4ec58-116">您可以用不同的方式來建立 XML 樹狀結構，包括下列各項：</span><span class="sxs-lookup"><span data-stu-id="4ec58-116">You can construct XML trees in different ways, including the following:</span></span>

- <span data-ttu-id="4ec58-117">您可以在程式碼中建構 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="4ec58-117">You can construct an XML tree in code.</span></span> <span data-ttu-id="4ec58-118">如需詳細資訊，請參閱 [XML 樹狀](functional-construction.md)結構。</span><span class="sxs-lookup"><span data-stu-id="4ec58-118">For more information, see [XML trees](functional-construction.md).</span></span>
- <span data-ttu-id="4ec58-119">您可以剖析來自各種來源的 XML，包括 <xref:System.IO.TextReader>、文字檔或網路位址 (URL)。</span><span class="sxs-lookup"><span data-stu-id="4ec58-119">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="4ec58-120">如需詳細資訊，請參閱 [剖析 XML](parse-string.md)。</span><span class="sxs-lookup"><span data-stu-id="4ec58-120">For more information, see [Parse XML](parse-string.md).</span></span>
- <span data-ttu-id="4ec58-121">您可以使用 <xref:System.Xml.XmlReader> 來填入樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="4ec58-121">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="4ec58-122">如需詳細資訊，請參閱<xref:System.Xml.Linq.XNode.ReadFrom%2A>。</span><span class="sxs-lookup"><span data-stu-id="4ec58-122">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>
- <span data-ttu-id="4ec58-123">如果您有可將內容寫入至的模組， <xref:System.Xml.XmlWriter> 您可以使用 <xref:System.Xml.Linq.XContainer.CreateWriter%2A> 方法來建立寫入器、將寫入器傳遞至模組，然後使用寫入的內容 <xref:System.Xml.XmlWriter> 來填入 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="4ec58-123">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that's written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>

<span data-ttu-id="4ec58-124">下列範例會建立一個樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="4ec58-124">The following example creates a tree.</span></span> <span data-ttu-id="4ec58-125">C # 版本會使用 nested 元素建立。</span><span class="sxs-lookup"><span data-stu-id="4ec58-125">The C# version uses nested element creations.</span></span> <span data-ttu-id="4ec58-126">您可以在 Visual Basic 中使用相同的技術，但此範例會使用 XML 常值。</span><span class="sxs-lookup"><span data-stu-id="4ec58-126">You can use the same technique in Visual Basic, but this example uses XML literals.</span></span>

```csharp
XElement contacts =
    new XElement("Contacts",
        new XElement("Contact",
            new XElement("Name", "Patrick Hines"),
            new XElement("Phone", "206-555-0144"),
            new XElement("Address",
                new XElement("Street1", "123 Main St"),
                new XElement("City", "Mercer Island"),
                new XElement("State", "WA"),
                new XElement("Postal", "68042")
            )
        )
    );
```

```vb
Dim contacts As XElement = _
    <Contacts>
        <Contact>
            <Name>Patrick Hines</Name>
            <Phone>206-555-0144</Phone>
            <Address>
                <Street1>123 Main St</Street1>
                <City>Mercer Island</City>
                <State>WA</State>
                <Postal>68042</Postal>
            </Address>
        </Contact>
    </Contacts>
```

<span data-ttu-id="4ec58-127">您也可以使用 LINQ to XML 查詢來填入 XML 樹狀結構，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="4ec58-127">You can also use a LINQ to XML query to populate an XML tree, as shown in the following example:</span></span>

```csharp
XElement srcTree = new XElement("Root",
    new XElement("Element", 1),
    new XElement("Element", 2),
    new XElement("Element", 3),
    new XElement("Element", 4),
    new XElement("Element", 5)
);
XElement xmlTree = new XElement("Root",
    new XElement("Child", 1),
    new XElement("Child", 2),
    from el in srcTree.Elements()
    where (int)el > 2
    select el
);
Console.WriteLine(xmlTree);
```

```vb
Dim srcTree As XElement = _
    <Root>
        <Element>1</Element>
        <Element>2</Element>
        <Element>3</Element>
        <Element>4</Element>
        <Element>5</Element>
    </Root>
Dim xmlTree As XElement = _
    <Root>
        <Child>1</Child>
        <Child>2</Child>
        <%= From el In srcTree.Elements() _
            Where el.Value > 2 _
            Select el %>
    </Root>
Console.WriteLine(xmlTree)
```

<span data-ttu-id="4ec58-128">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="4ec58-128">This example produces the following output:</span></span>

```xml
<Root>
  <Child>1</Child>
  <Child>2</Child>
  <Element>3</Element>
  <Element>4</Element>
  <Element>5</Element>
</Root>
```

## <a name="serialize-xml-trees"></a><span data-ttu-id="4ec58-129">序列化 XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="4ec58-129">Serialize XML trees</span></span>

<span data-ttu-id="4ec58-130">您可以將 XML 樹狀結構序列化至 <xref:System.IO.File>、<xref:System.IO.TextWriter> 或 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="4ec58-130">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>

<span data-ttu-id="4ec58-131">如需詳細資訊，請參閱 [序列化 XML 樹狀](preserve-white-space-serializing.md)結構。</span><span class="sxs-lookup"><span data-stu-id="4ec58-131">For more information, see [Serialize XML trees](preserve-white-space-serializing.md).</span></span>

## <a name="retrieve-xml-data-via-axis-methods"></a><span data-ttu-id="4ec58-132">透過軸方法取得 XML 資料</span><span class="sxs-lookup"><span data-stu-id="4ec58-132">Retrieve XML data via axis methods</span></span>

<span data-ttu-id="4ec58-133">您可以使用座標軸方法來擷取屬性、子項目、子系項目以及祖系項目。</span><span class="sxs-lookup"><span data-stu-id="4ec58-133">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> <span data-ttu-id="4ec58-134">LINQ to XML 的查詢會在座標軸方法上操作，並提供數個具彈性且功能強大的方式來流覽和處理 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="4ec58-134">LINQ to XML queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>

<span data-ttu-id="4ec58-135">如需詳細資訊，請參閱 [LINQ to XML 軸總覽](linq-xml-axes-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4ec58-135">For more information, see [LINQ to XML axes overview](linq-xml-axes-overview.md).</span></span>

## <a name="query-xml-trees"></a><span data-ttu-id="4ec58-136">查詢 XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="4ec58-136">Query XML trees</span></span>

<span data-ttu-id="4ec58-137">您可以撰寫從 XML 樹狀結構中解壓縮資料的 LINQ to XML 查詢。</span><span class="sxs-lookup"><span data-stu-id="4ec58-137">You can write LINQ to XML queries that extract data from an XML tree.</span></span>

<span data-ttu-id="4ec58-138">如需詳細資訊，請參閱 [查詢 XML 樹狀結構總覽](query-xml-trees-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4ec58-138">For more information, see [Query XML trees overview](query-xml-trees-overview.md).</span></span>

## <a name="modify-xml-trees"></a><span data-ttu-id="4ec58-139">修改 XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="4ec58-139">Modify XML trees</span></span>

<span data-ttu-id="4ec58-140">您可以用不同的方式修改元素，包括變更其內容或屬性。</span><span class="sxs-lookup"><span data-stu-id="4ec58-140">You can modify an element in different ways, including changing its content or attributes.</span></span> <span data-ttu-id="4ec58-141">您也可以從其父代移除項目。</span><span class="sxs-lookup"><span data-stu-id="4ec58-141">You can also remove an element from its parent.</span></span>

<span data-ttu-id="4ec58-142">如需詳細資訊，請參閱 [修改 XML 樹狀](in-memory-xml-tree-modification-vs-functional-construction.md)結構。</span><span class="sxs-lookup"><span data-stu-id="4ec58-142">For more information, see [Modify XML trees](in-memory-xml-tree-modification-vs-functional-construction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4ec58-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ec58-143">See also</span></span>

- [<span data-ttu-id="4ec58-144">LINQ to XML 程式設計總覽</span><span class="sxs-lookup"><span data-stu-id="4ec58-144">LINQ to XML programming overview</span></span>](functional-vs-procedural-programming.md)
