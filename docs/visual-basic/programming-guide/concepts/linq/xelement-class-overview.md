---
title: XElement 類別概觀 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 52331fcd-6023-4d19-b423-7b24f2d86ded
ms.openlocfilehash: 7fbe1cc484ea3482bc455c161783bd7a4513d0bd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783613"
---
# <a name="xelement-class-overview-visual-basic"></a><span data-ttu-id="8db0c-102">XElement 類別概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8db0c-102">XElement Class Overview (Visual Basic)</span></span>
<span data-ttu-id="8db0c-103"><xref:System.Xml.Linq.XElement> 類別是 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 中的其中一個基本類別。</span><span class="sxs-lookup"><span data-stu-id="8db0c-103">The <xref:System.Xml.Linq.XElement> class is one of the fundamental classes in [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span></span> <span data-ttu-id="8db0c-104">它代表 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="8db0c-104">It represents an XML element.</span></span> <span data-ttu-id="8db0c-105">您可以使用這個類別來建立項目；變更項目的內容；加入、變更或刪除子項目；將屬性加入到項目中；或以文字格式序列化項目的內容。</span><span class="sxs-lookup"><span data-stu-id="8db0c-105">You can use this class to create elements; change the content of the element; add, change, or delete child elements; add attributes to an element; or serialize the contents of an element in text form.</span></span> <span data-ttu-id="8db0c-106">您也可以與 <xref:System.Xml?displayProperty=nameWithType> 中的其他類別相互溝通，例如，<xref:System.Xml.XmlReader>、<xref:System.Xml.XmlWriter> 和 <xref:System.Xml.Xsl.XslCompiledTransform>。</span><span class="sxs-lookup"><span data-stu-id="8db0c-106">You can also interoperate with other classes in <xref:System.Xml?displayProperty=nameWithType>, such as <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, and <xref:System.Xml.Xsl.XslCompiledTransform>.</span></span>  
  
## <a name="xelement-functionality"></a><span data-ttu-id="8db0c-107">XElement 功能</span><span class="sxs-lookup"><span data-stu-id="8db0c-107">XElement Functionality</span></span>  
 <span data-ttu-id="8db0c-108">本主題描述 <xref:System.Xml.Linq.XElement> 類別提供的功能。</span><span class="sxs-lookup"><span data-stu-id="8db0c-108">This topic describes the functionality provided by the <xref:System.Xml.Linq.XElement> class.</span></span>  
  
### <a name="constructing-xml-trees"></a><span data-ttu-id="8db0c-109">建構 XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="8db0c-109">Constructing XML Trees</span></span>  
 <span data-ttu-id="8db0c-110">您可以用各種方式建構 XML 樹狀結構，包括：</span><span class="sxs-lookup"><span data-stu-id="8db0c-110">You can construct XML trees in a variety of ways, including the following:</span></span>  
  
- <span data-ttu-id="8db0c-111">您可以在程式碼中建構 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="8db0c-111">You can construct an XML tree in code.</span></span> <span data-ttu-id="8db0c-112">如需詳細資訊，請參閱 <<c0> [ 建立 XML 樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md)。</span><span class="sxs-lookup"><span data-stu-id="8db0c-112">For more information, see [Creating XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/creating-xml-trees.md).</span></span>  
  
- <span data-ttu-id="8db0c-113">您可以剖析來自各種來源的 XML，包括 <xref:System.IO.TextReader>、文字檔或網路位址 (URL)。</span><span class="sxs-lookup"><span data-stu-id="8db0c-113">You can parse XML from various sources, including a <xref:System.IO.TextReader>, text files, or a Web address (URL).</span></span> <span data-ttu-id="8db0c-114">如需詳細資訊，請參閱 <<c0> [ 剖析 XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="8db0c-114">For more information, see [Parsing XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md).</span></span>  
  
- <span data-ttu-id="8db0c-115">您可以使用 <xref:System.Xml.XmlReader> 來填入樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="8db0c-115">You can use an <xref:System.Xml.XmlReader> to populate the tree.</span></span> <span data-ttu-id="8db0c-116">如需詳細資訊，請參閱<xref:System.Xml.Linq.XNode.ReadFrom%2A>。</span><span class="sxs-lookup"><span data-stu-id="8db0c-116">For more information, see <xref:System.Xml.Linq.XNode.ReadFrom%2A>.</span></span>  
  
- <span data-ttu-id="8db0c-117">如果您擁有的模組可以將內容寫入到 <xref:System.Xml.XmlWriter>，您可以使用 <xref:System.Xml.Linq.XContainer.CreateWriter%2A> 方法來建立寫入器、將寫入器傳遞到模組，然後使用寫入到 <xref:System.Xml.XmlWriter> 的內容填入 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="8db0c-117">If you have a module that can write content to an <xref:System.Xml.XmlWriter>, you can use the <xref:System.Xml.Linq.XContainer.CreateWriter%2A> method to create a writer, pass the writer to the module, and then use the content that is written to the <xref:System.Xml.XmlWriter> to populate the XML tree.</span></span>  
  
 <span data-ttu-id="8db0c-118">不過，建立 XML 樹狀結構最常見的方式為下：</span><span class="sxs-lookup"><span data-stu-id="8db0c-118">However, the most common way to create an XML tree is as follows:</span></span>  
  
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
  
 <span data-ttu-id="8db0c-119">建立 XML 樹狀結構的另一個非常常見的技術包含使用 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢的結果填入 XML 樹狀結構，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="8db0c-119">Another very common technique for creating an XML tree involves using the results of a [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] query to populate an XML tree, as shown in the following example:</span></span>  
  
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
  
 <span data-ttu-id="8db0c-120">這個範例會產生下列輸出：</span><span class="sxs-lookup"><span data-stu-id="8db0c-120">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Child>1</Child>  
  <Child>2</Child>  
  <Element>3</Element>  
  <Element>4</Element>  
  <Element>5</Element>  
</Root>  
```  
  
### <a name="serializing-xml-trees"></a><span data-ttu-id="8db0c-121">序列化 XML 樹狀結構</span><span class="sxs-lookup"><span data-stu-id="8db0c-121">Serializing XML Trees</span></span>  
 <span data-ttu-id="8db0c-122">您可以將 XML 樹狀結構序列化至 <xref:System.IO.File>、<xref:System.IO.TextWriter> 或 <xref:System.Xml.XmlWriter>。</span><span class="sxs-lookup"><span data-stu-id="8db0c-122">You can serialize the XML tree to a <xref:System.IO.File>, a <xref:System.IO.TextWriter>, or an <xref:System.Xml.XmlWriter>.</span></span>  
  
 <span data-ttu-id="8db0c-123">如需詳細資訊，請參閱 <<c0> [ 序列化 XML 樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)。</span><span class="sxs-lookup"><span data-stu-id="8db0c-123">For more information, see [Serializing XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md).</span></span>  
  
### <a name="retrieving-xml-data-via-axis-methods"></a><span data-ttu-id="8db0c-124">透過座標軸方法擷取 XML 資料</span><span class="sxs-lookup"><span data-stu-id="8db0c-124">Retrieving XML Data via Axis Methods</span></span>  
 <span data-ttu-id="8db0c-125">您可以使用座標軸方法來擷取屬性、子項目、子系項目以及祖系項目。</span><span class="sxs-lookup"><span data-stu-id="8db0c-125">You can use axis methods to retrieve attributes, child elements, descendant elements, and ancestor elements.</span></span> [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] <span data-ttu-id="8db0c-126">查詢會在座標軸方法上操作，而且會提供數種具彈性而且功能強大的方式，導覽並處理 XML 樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="8db0c-126">queries operate on axis methods, and provide several flexible and powerful ways to navigate through and process an XML tree.</span></span>  
  
 <span data-ttu-id="8db0c-127">如需詳細資訊，請參閱 < [LINQ to XML 座標軸 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)。</span><span class="sxs-lookup"><span data-stu-id="8db0c-127">For more information, see [LINQ to XML Axes (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md).</span></span>  
  
### <a name="querying-xml-trees"></a><span data-ttu-id="8db0c-128">查詢 XML 樹狀</span><span class="sxs-lookup"><span data-stu-id="8db0c-128">Querying XML Trees</span></span>  
 <span data-ttu-id="8db0c-129">您可以撰寫從 XML 樹狀結構擷取資料的 [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] 查詢。</span><span class="sxs-lookup"><span data-stu-id="8db0c-129">You can write [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] queries that extract data from an XML tree.</span></span>  
  
 <span data-ttu-id="8db0c-130">如需詳細資訊，請參閱 <<c0> [ 查詢 XML 樹狀結構 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md)。</span><span class="sxs-lookup"><span data-stu-id="8db0c-130">For more information, see [Querying XML Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/querying-xml-trees.md).</span></span>  
  
### <a name="modifying-xml-trees"></a><span data-ttu-id="8db0c-131">修改 XML 樹狀</span><span class="sxs-lookup"><span data-stu-id="8db0c-131">Modifying XML Trees</span></span>  
 <span data-ttu-id="8db0c-132">您可以用各種方式修改項目，包括變更其內容或屬性。</span><span class="sxs-lookup"><span data-stu-id="8db0c-132">You can modify an element in a variety of ways, including changing its content or attributes.</span></span> <span data-ttu-id="8db0c-133">您也可以從其父代移除項目。</span><span class="sxs-lookup"><span data-stu-id="8db0c-133">You can also remove an element from its parent.</span></span>  
  
 <span data-ttu-id="8db0c-134">如需詳細資訊，請參閱 <<c0> [ 修改 XML 樹狀結構 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)。</span><span class="sxs-lookup"><span data-stu-id="8db0c-134">For more information, see [Modifying XML Trees (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8db0c-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8db0c-135">See also</span></span>

- [<span data-ttu-id="8db0c-136">LINQ to XML 程式設計概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8db0c-136">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
