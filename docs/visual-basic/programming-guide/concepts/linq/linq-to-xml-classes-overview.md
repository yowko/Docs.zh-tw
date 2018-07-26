---
title: LINQ to XML 類別概觀 (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f11b62b5-d522-4c23-92ae-23186dc16447
ms.openlocfilehash: dd9e392c1fec86bfb1fe0e0f8bee0cd0c7919fe4
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244084"
---
# <a name="linq-to-xml-classes-overview-visual-basic"></a><span data-ttu-id="522bf-102">LINQ to XML 類別概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="522bf-102">LINQ to XML Classes Overview (Visual Basic)</span></span>
<span data-ttu-id="522bf-103">本主題提供 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] 命名空間 (Namespace) 中的 <xref:System.Xml.Linq> 類別 (Class) 清單，以及每個類別的簡短說明。</span><span class="sxs-lookup"><span data-stu-id="522bf-103">This topic provides a list of the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] classes in the <xref:System.Xml.Linq> namespace, and a short description of each.</span></span>  
  
## <a name="linq-to-xml-classes"></a><span data-ttu-id="522bf-104">LINQ to XML 類別</span><span class="sxs-lookup"><span data-stu-id="522bf-104">LINQ to XML Classes</span></span>  
  
### <a name="xattribute-class"></a><span data-ttu-id="522bf-105">XAttribute 類別</span><span class="sxs-lookup"><span data-stu-id="522bf-105">XAttribute Class</span></span>  
 <span data-ttu-id="522bf-106"><xref:System.Xml.Linq.XAttribute> 代表 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="522bf-106"><xref:System.Xml.Linq.XAttribute> represents an XML attribute.</span></span> <span data-ttu-id="522bf-107">如需詳細的資訊和範例，請參閱 < [XAttribute 類別概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="522bf-107">For detailed information and examples, see [XAttribute Class Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md).</span></span>  
  
### <a name="xcdata-class"></a><span data-ttu-id="522bf-108">XCData 類別</span><span class="sxs-lookup"><span data-stu-id="522bf-108">XCData Class</span></span>  
 <span data-ttu-id="522bf-109"><xref:System.Xml.Linq.XCData> 代表 CDATA 文字節點。</span><span class="sxs-lookup"><span data-stu-id="522bf-109"><xref:System.Xml.Linq.XCData> represents a CDATA text node.</span></span>  
  
### <a name="xcomment-class"></a><span data-ttu-id="522bf-110">XComment 類別</span><span class="sxs-lookup"><span data-stu-id="522bf-110">XComment Class</span></span>  
 <span data-ttu-id="522bf-111"><xref:System.Xml.Linq.XComment> 代表 XML 註解。</span><span class="sxs-lookup"><span data-stu-id="522bf-111"><xref:System.Xml.Linq.XComment> represents an XML comment.</span></span>  
  
### <a name="xcontainer-class"></a><span data-ttu-id="522bf-112">XContainer 類別</span><span class="sxs-lookup"><span data-stu-id="522bf-112">XContainer Class</span></span>  
 <span data-ttu-id="522bf-113"><xref:System.Xml.Linq.XContainer> 對於可能擁有子節點的所有節點而言，是抽象基底類別。</span><span class="sxs-lookup"><span data-stu-id="522bf-113"><xref:System.Xml.Linq.XContainer> is an abstract base class for all nodes that can have child nodes.</span></span> <span data-ttu-id="522bf-114">下列類別衍生自 <xref:System.Xml.Linq.XContainer> 類別：</span><span class="sxs-lookup"><span data-stu-id="522bf-114">The following classes derive from the <xref:System.Xml.Linq.XContainer> class:</span></span>  
  
-   <xref:System.Xml.Linq.XElement>  
  
-   <xref:System.Xml.Linq.XDocument>  
  
### <a name="xdeclaration-class"></a><span data-ttu-id="522bf-115">XDeclaration 類別</span><span class="sxs-lookup"><span data-stu-id="522bf-115">XDeclaration Class</span></span>  
 <span data-ttu-id="522bf-116"><xref:System.Xml.Linq.XDeclaration> 代表 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="522bf-116"><xref:System.Xml.Linq.XDeclaration> represents an XML declaration.</span></span> <span data-ttu-id="522bf-117">XML 宣告用於宣告 XML 版本與文件的編碼。</span><span class="sxs-lookup"><span data-stu-id="522bf-117">An XML declaration is used to declare the XML version and the encoding of a document.</span></span> <span data-ttu-id="522bf-118">此外，XML 宣告會指定 XML 文件是否為獨立的。</span><span class="sxs-lookup"><span data-stu-id="522bf-118">In addition, an XML declaration specifies whether the XML document is stand-alone.</span></span> <span data-ttu-id="522bf-119">如果文件是獨立的，外部 DTD 或內部子集所參考的外部參數實體 (Entity) 就不會包含任何外部標記宣告。</span><span class="sxs-lookup"><span data-stu-id="522bf-119">If a document is stand-alone, there are no external markup declarations, either in an external DTD, or in an external parameter entity referenced from the internal subset.</span></span>  
  
### <a name="xdocument-class"></a><span data-ttu-id="522bf-120">XDocument 類別</span><span class="sxs-lookup"><span data-stu-id="522bf-120">XDocument Class</span></span>  
 <span data-ttu-id="522bf-121"><xref:System.Xml.Linq.XDocument> 代表 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="522bf-121"><xref:System.Xml.Linq.XDocument> represents an XML document.</span></span> <span data-ttu-id="522bf-122">如需詳細的資訊和範例，請參閱 < [XDocument 類別概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="522bf-122">For detailed information and examples, see [XDocument Class Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).</span></span>  
  
### <a name="xdocumenttype-class"></a><span data-ttu-id="522bf-123">XDocumentType 類別</span><span class="sxs-lookup"><span data-stu-id="522bf-123">XDocumentType Class</span></span>  
 <span data-ttu-id="522bf-124"><xref:System.Xml.Linq.XDocumentType> 代表 XML 文件類型定義 (DTD)。</span><span class="sxs-lookup"><span data-stu-id="522bf-124"><xref:System.Xml.Linq.XDocumentType> represents an XML Document Type Definition (DTD).</span></span>  
  
### <a name="xelement-class"></a><span data-ttu-id="522bf-125">XElement 類別</span><span class="sxs-lookup"><span data-stu-id="522bf-125">XElement Class</span></span>  
 <span data-ttu-id="522bf-126"><xref:System.Xml.Linq.XElement> 代表 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="522bf-126"><xref:System.Xml.Linq.XElement> represents an XML element.</span></span> <span data-ttu-id="522bf-127">如需詳細的資訊和範例，請參閱 < [XElement 類別概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="522bf-127">For detailed information and examples, see [XElement Class Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md).</span></span>  
  
### <a name="xname-class"></a><span data-ttu-id="522bf-128">XName 類別</span><span class="sxs-lookup"><span data-stu-id="522bf-128">XName Class</span></span>  
 <span data-ttu-id="522bf-129"><xref:System.Xml.Linq.XName> 代表項目的名稱 (<xref:System.Xml.Linq.XElement>) 與屬性 (<xref:System.Xml.Linq.XAttribute>)。</span><span class="sxs-lookup"><span data-stu-id="522bf-129"><xref:System.Xml.Linq.XName> represents names of elements (<xref:System.Xml.Linq.XElement>) and attributes (<xref:System.Xml.Linq.XAttribute>).</span></span> <span data-ttu-id="522bf-130">如需詳細的資訊和範例，請參閱 < [XDocument 類別概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="522bf-130">For detailed information and examples, see [XDocument Class Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="522bf-131"> 的設計是讓 XML 名稱盡可能直接。</span><span class="sxs-lookup"><span data-stu-id="522bf-131"> is designed to make XML names as straightforward as possible.</span></span> <span data-ttu-id="522bf-132">由於其複雜性的緣故，XML 名稱通常被視為 XML 的進階主題。</span><span class="sxs-lookup"><span data-stu-id="522bf-132">Due to their complexity, XML names are often considered to be an advanced topic in XML.</span></span> <span data-ttu-id="522bf-133">在論證上，這個複雜性不是來自於開發人員一般用於程式設計的命名空間，而是來自於命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="522bf-133">Arguably, this complexity comes not from namespaces, which developers use regularly in programming, but from namespace prefixes.</span></span> <span data-ttu-id="522bf-134">命名空間前置詞在減少輸入 XML 時所需的按鍵或在讓 XML 更容易讀取上，可能相當實用。</span><span class="sxs-lookup"><span data-stu-id="522bf-134">Namespace prefixes can be useful to reduce the keystrokes required when you input XML, or to make XML easier to read.</span></span> <span data-ttu-id="522bf-135">不過，前置詞通常只是用來使用完整 XML 命名空間的捷徑，因此大部分情況中都不需要。</span><span class="sxs-lookup"><span data-stu-id="522bf-135">However, prefixes are often just a shortcut for using the full XML namespace, and are not required in most cases.</span></span> [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="522bf-136"> 會將所有前置詞解析為其對應的 XML 命名空間，藉以簡化 XML 名稱。</span><span class="sxs-lookup"><span data-stu-id="522bf-136"> simplifies XML names by resolving all prefixes to their corresponding XML namespace.</span></span> <span data-ttu-id="522bf-137">如果需要前置詞，可透過 <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> 方法使用。</span><span class="sxs-lookup"><span data-stu-id="522bf-137">Prefixes are available, if they are required, through the <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> method.</span></span>  
  
 <span data-ttu-id="522bf-138">如有需要，可以控制命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="522bf-138">It is possible, if necessary, to control namespace prefixes.</span></span> <span data-ttu-id="522bf-139">在某些情況下，如果您要使用其他 XML 系統 (例如，XSLT 或 XAML)，您必須控制命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="522bf-139">In some circumstances, if you are working with other XML systems, such as XSLT or XAML, you need to control namespace prefixes.</span></span> <span data-ttu-id="522bf-140">例如，如果您所擁有的 XPath 運算式使用內嵌在 XSLT 樣式表中的命名空間前置詞，您就必須確認 XML 文件有利用符合 XPath 運算式中使用之命名空間前置詞的命名空間前置詞進行序列化。</span><span class="sxs-lookup"><span data-stu-id="522bf-140">For example, if you have an XPath expression that uses namespace prefixes and is embedded in an XSLT stylesheet, you must make sure that your XML document is serialized with namespace prefixes that match those used in the XPath expression.</span></span>  
  
### <a name="xnamespace-class"></a><span data-ttu-id="522bf-141">XNamespace 類別</span><span class="sxs-lookup"><span data-stu-id="522bf-141">XNamespace Class</span></span>  
 <span data-ttu-id="522bf-142"><xref:System.Xml.Linq.XNamespace> 代表 <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> 的命名空間。</span><span class="sxs-lookup"><span data-stu-id="522bf-142"><xref:System.Xml.Linq.XNamespace> represents a namespace for an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="522bf-143">命名空間是 <xref:System.Xml.Linq.XName> 的元件。</span><span class="sxs-lookup"><span data-stu-id="522bf-143">Namespaces are a component of an <xref:System.Xml.Linq.XName>.</span></span>  
  
### <a name="xnode-class"></a><span data-ttu-id="522bf-144">XNode 類別</span><span class="sxs-lookup"><span data-stu-id="522bf-144">XNode Class</span></span>  
 <span data-ttu-id="522bf-145"><xref:System.Xml.Linq.XNode> 是代表 XML 樹狀結構節點的抽象類別。</span><span class="sxs-lookup"><span data-stu-id="522bf-145"><xref:System.Xml.Linq.XNode> is an abstract class that represents the nodes of an XML tree.</span></span> <span data-ttu-id="522bf-146">下列類別衍生自 <xref:System.Xml.Linq.XNode> 類別：</span><span class="sxs-lookup"><span data-stu-id="522bf-146">The following classes derive from the <xref:System.Xml.Linq.XNode> class:</span></span>  
  
-   <xref:System.Xml.Linq.XText>  
  
-   <xref:System.Xml.Linq.XContainer>  
  
-   <xref:System.Xml.Linq.XComment>  
  
-   <xref:System.Xml.Linq.XProcessingInstruction>  
  
-   <xref:System.Xml.Linq.XDocumentType>  
  
### <a name="xnodedocumentordercomparer-class"></a><span data-ttu-id="522bf-147">XNodeDocumentOrderComparer 類別</span><span class="sxs-lookup"><span data-stu-id="522bf-147">XNodeDocumentOrderComparer Class</span></span>  
 <span data-ttu-id="522bf-148"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> 會提供功能，針對其文件順序比較節點。</span><span class="sxs-lookup"><span data-stu-id="522bf-148"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> provides functionality to compare nodes for their document order.</span></span>  
  
### <a name="xnodeequalitycomparer-class"></a><span data-ttu-id="522bf-149">XNodeEqualityComparer 類別</span><span class="sxs-lookup"><span data-stu-id="522bf-149">XNodeEqualityComparer Class</span></span>  
 <span data-ttu-id="522bf-150"><xref:System.Xml.Linq.XNodeEqualityComparer> 會提供功能，針對值的相等性比較節點。</span><span class="sxs-lookup"><span data-stu-id="522bf-150"><xref:System.Xml.Linq.XNodeEqualityComparer> provides functionality to compare nodes for value equality.</span></span>  
  
### <a name="xobject-class"></a><span data-ttu-id="522bf-151">XObject 類別</span><span class="sxs-lookup"><span data-stu-id="522bf-151">XObject Class</span></span>  
 <span data-ttu-id="522bf-152"><xref:System.Xml.Linq.XObject> 是 <xref:System.Xml.Linq.XNode> 和 <xref:System.Xml.Linq.XAttribute> 的抽象基底類別。</span><span class="sxs-lookup"><span data-stu-id="522bf-152"><xref:System.Xml.Linq.XObject> is an abstract base class of <xref:System.Xml.Linq.XNode> and <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="522bf-153">它提供附註和事件的功能。</span><span class="sxs-lookup"><span data-stu-id="522bf-153">It provides annotation and event functionality.</span></span>  
  
### <a name="xobjectchange-class"></a><span data-ttu-id="522bf-154">XObjectChange 類別</span><span class="sxs-lookup"><span data-stu-id="522bf-154">XObjectChange Class</span></span>  
 <span data-ttu-id="522bf-155">引發 <xref:System.Xml.Linq.XObjectChange> 的事件時，<xref:System.Xml.Linq.XObject> 會指定事件類型。</span><span class="sxs-lookup"><span data-stu-id="522bf-155"><xref:System.Xml.Linq.XObjectChange> specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>  
  
### <a name="xobjectchangeeventargs-class"></a><span data-ttu-id="522bf-156">XObjectChangeEventArgs 類別</span><span class="sxs-lookup"><span data-stu-id="522bf-156">XObjectChangeEventArgs Class</span></span>  
 <span data-ttu-id="522bf-157"><xref:System.Xml.Linq.XObjectChangeEventArgs> 會提供 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed> 事件的資料。</span><span class="sxs-lookup"><span data-stu-id="522bf-157"><xref:System.Xml.Linq.XObjectChangeEventArgs> provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>  
  
### <a name="xprocessinginstruction-class"></a><span data-ttu-id="522bf-158">XProcessingInstruction 類別</span><span class="sxs-lookup"><span data-stu-id="522bf-158">XProcessingInstruction Class</span></span>  
 <span data-ttu-id="522bf-159"><xref:System.Xml.Linq.XProcessingInstruction> 代表 XML 處理指示。</span><span class="sxs-lookup"><span data-stu-id="522bf-159"><xref:System.Xml.Linq.XProcessingInstruction> represents an XML processing instruction.</span></span> <span data-ttu-id="522bf-160">處理指示會將資訊傳達到處理 XML 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="522bf-160">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
### <a name="xtext-class"></a><span data-ttu-id="522bf-161">XText 類別</span><span class="sxs-lookup"><span data-stu-id="522bf-161">XText Class</span></span>  
 <span data-ttu-id="522bf-162"><xref:System.Xml.Linq.XText> 代表文字節點。</span><span class="sxs-lookup"><span data-stu-id="522bf-162"><xref:System.Xml.Linq.XText> represents a text node.</span></span> <span data-ttu-id="522bf-163">在大部分的情況下，您不必使用這個類別。</span><span class="sxs-lookup"><span data-stu-id="522bf-163">In most cases, you do not have to use this class.</span></span> <span data-ttu-id="522bf-164">這個類別主要用於混合的內容。</span><span class="sxs-lookup"><span data-stu-id="522bf-164">This class is primarily used for mixed content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="522bf-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="522bf-165">See Also</span></span>  
 [<span data-ttu-id="522bf-166">LINQ to XML 程式設計概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="522bf-166">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
