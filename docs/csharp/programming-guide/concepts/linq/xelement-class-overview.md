---
title: XElement 類別概觀 (C#)
ms.date: 07/20/2015
ms.assetid: 2b9f0cd8-a1d1-4037-accf-0f38a410fa11
ms.openlocfilehash: 6a93dd4bdaf16fddff800b08b0f3146ecb63f9b7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79167890"
---
# <a name="xelement-class-overview-c"></a><span data-ttu-id="b7241-102">XElement 類別概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="b7241-102">XElement Class Overview (C#)</span></span>
<span data-ttu-id="b7241-103"><xref:System.Xml.Linq.XElement> 類別是 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中的其中一個基本類別。</span><span class="sxs-lookup"><span data-stu-id="b7241-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="b7241-104">它代表 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="b7241-104">It represents an XML element.</span></span> <span data-ttu-id="b7241-105">您可以使用這個類別來建立項目；變更項目的內容；加入、變更或刪除子項目；將屬性加入到項目中；或以文字格式序列化項目的內容。</span><span class="sxs-lookup"><span data-stu-id="b7241-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="b7241-106">您也可以與 <xref:System.Xml?displayProperty=nameWithType> 中的其他類別相互溝通，例如，<xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter> 和 <xref:System.Xml.Xsl.XslCompiledTransform>。</span><span class="sxs-lookup"><span data-stu-id="b7241-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
<span data-ttu-id="b7241-107">本主題描述 <xref:System.Xml.Linq.XElement> 類別提供的功能。</span><span class="sxs-lookup"><span data-stu-id="b7241-107">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
## <a name="constructing-xml-trees"></a><span data-ttu-id="b7241-108">建構 XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="b7241-108">Constructing XML Trees</span></span>  
 <span data-ttu-id="b7241-109">您可以用各種方式建構 XML 樹狀結構，包括：</span><span class="sxs-lookup"><span data-stu-id="b7241-109">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
- <span data-ttu-id="b7241-110">您可以在程式碼中建構 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="b7241-110">You can construct an XML tree in code.</span></span> <span data-ttu-id="b7241-111">如需詳細資訊，請參閱[建立 XML 樹狀結構 (C#)](./linq-to-xml-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b7241-111">For more information, see [Creating XML Trees (C#)](./linq-to-xml-overview.md).</span></span>  
  
- <span data-ttu-id="b7241-112">您可以剖析來自各種來源的 XML，包括 <xref:System.IO.TextReader>、文字檔或網路位址 (URL)。</span><span class="sxs-lookup"><span data-stu-id="b7241-112">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="b7241-113">如需詳細資訊，請參閱[剖析 XML (C#)](./how-to-parse-a-string.md)。</span><span class="sxs-lookup"><span data-stu-id="b7241-113">For more information, see [Parsing XML (C#)](./how-to-parse-a-string.md).</span></span>  
  
- <span data-ttu-id="b7241-114">您可以使用 <xref:System.Xml.XmlReader> 來填入樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="b7241-114">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="b7241-115">如需詳細資訊，請參閱 <xref:System.Xml.Linq.XNode.ReadFrom%2A>。</span><span class="sxs-lookup"><span data-stu-id="b7241-115">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
- <span data-ttu-id="b7241-116">如果您擁有的模組可以將內容寫入到 <xref:System.Xml.XmlWriter>，您可以使用 <xref:System.Xml.Linq.XContainer.CreateWriter%2A> 方法來建立寫入器、將寫入器傳遞到模組，然後使用寫入到 <xref:System.Xml.XmlWriter> 的內容填入 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="b7241-116">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="b7241-117">不過，建立 XML 樹狀結構最常見的方式為下：</span><span class="sxs-lookup"><span data-stu-id="b7241-117">However, the most common way to create an XML tree is as follows:</span></span>  
  
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
  
 <span data-ttu-id="b7241-118">創建 XML 樹的另一種非常常見的技術涉及使用 LINQ 查詢的結果來填充 XML 樹，如以下示例所示：</span><span class="sxs-lookup"><span data-stu-id="b7241-118">Another very common technique for creating an XML tree involves using the results of a LINQ query to populate an XML tree, as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="b7241-119">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="b7241-119">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
## <a name="serializing-xml-trees"></a><span data-ttu-id="b7241-120">序列化 XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="b7241-120">Serializing XML Trees</span></span>  
 <span data-ttu-id="b7241-121">您可以將 XML 樹狀結構序列化至 <xref:System.IO.File>、<xref:System.IO.TextWriter> 或 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="b7241-121">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="b7241-122">如需詳細資訊，請參閱[序列化 XML 樹狀結構 (C#)](./preserving-white-space-while-serializing.md)。</span><span class="sxs-lookup"><span data-stu-id="b7241-122">For more information, see [Serializing XML Trees (C#)](./preserving-white-space-while-serializing.md).</span></span>  
  
## <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="b7241-123">透過座標軸方法擷取 XML 資料</span><span class="sxs-lookup"><span data-stu-id="b7241-123">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="b7241-124">您可以使用座標軸方法來擷取屬性、子項目、子系項目以及祖系項目。</span><span class="sxs-lookup"><span data-stu-id="b7241-124">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> <span data-ttu-id="b7241-125">LINQ 查詢使用軸方法操作，並提供幾種靈活而強大的方法來流覽和處理 XML 樹。</span><span class="sxs-lookup"><span data-stu-id="b7241-125">LINQ queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="b7241-126">如需詳細資訊，請參閱 [LINQ to XML 座標軸 (C#)](./linq-to-xml-axes-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="b7241-126">For more information, see [LINQ to XML Axes (C#)](./linq-to-xml-axes-overview.md).</span></span>  
  
## <a name="querying-xml-trees"></a><span data-ttu-id="b7241-127">查詢 XML 樹狀</span><span class="sxs-lookup"><span data-stu-id="b7241-127">Querying XML Trees</span></span>  
 <span data-ttu-id="b7241-128">您可以編寫 LINQ 查詢，從 XML 樹中提取資料。</span><span class="sxs-lookup"><span data-stu-id="b7241-128">You can write LINQ queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="b7241-129">如需詳細資訊，請參閱[查詢 XML 樹狀結構 (C#)](./how-to-find-an-element-with-a-specific-attribute.md)。</span><span class="sxs-lookup"><span data-stu-id="b7241-129">For more information, see [Querying XML Trees (C#)](./how-to-find-an-element-with-a-specific-attribute.md).</span></span>  
  
## <a name="modifying-xml-trees"></a><span data-ttu-id="b7241-130">修改 XML 樹狀</span><span class="sxs-lookup"><span data-stu-id="b7241-130">Modifying XML Trees</span></span>  
 <span data-ttu-id="b7241-131">您可以用各種方式修改項目，包括變更其內容或屬性。</span><span class="sxs-lookup"><span data-stu-id="b7241-131">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="b7241-132">您也可以從其父代移除項目。</span><span class="sxs-lookup"><span data-stu-id="b7241-132">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="b7241-133">如需詳細資訊，請參閱[修改 XML 樹狀結構 (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="b7241-133">For more information, see [Modifying XML Trees (LINQ to XML) (C#)](./in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7241-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7241-134">See also</span></span>

- [<span data-ttu-id="b7241-135">LINQ to XML 程式設計概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="b7241-135">LINQ to XML Programming Overview (C#)</span></span>](serializing-to-files-textwriters-and-xmlwriters.md)
