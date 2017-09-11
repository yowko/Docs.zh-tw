---
title: "LINQ to XML 類別概觀 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: f11b62b5-d522-4c23-92ae-23186dc16447
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 8c999860ed04c754855792d814cd3801f5f92c90
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="linq-to-xml-classes-overview-visual-basic"></a><span data-ttu-id="4914a-102">LINQ to XML 類別概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4914a-102">LINQ to XML Classes Overview (Visual Basic)</span></span>
<span data-ttu-id="4914a-103">本主題提供一份[!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]中的類別<xref:System.Xml.Linq>命名空間，以及個別的簡短說明。</xref:System.Xml.Linq></span><span class="sxs-lookup"><span data-stu-id="4914a-103">This topic provides a list of the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] classes in the <xref:System.Xml.Linq> namespace, and a short description of each.</span></span>  
  
## <a name="linq-to-xml-classes"></a><span data-ttu-id="4914a-104">LINQ to XML 類別</span><span class="sxs-lookup"><span data-stu-id="4914a-104">LINQ to XML Classes</span></span>  
  
### <a name="xattribute-class"></a><span data-ttu-id="4914a-105">XAttribute 類別</span><span class="sxs-lookup"><span data-stu-id="4914a-105">XAttribute Class</span></span>  
 <span data-ttu-id="4914a-106"><xref:System.Xml.Linq.XAttribute>代表 XML 屬性。</xref:System.Xml.Linq.XAttribute></span><span class="sxs-lookup"><span data-stu-id="4914a-106"><xref:System.Xml.Linq.XAttribute> represents an XML attribute.</span></span> <span data-ttu-id="4914a-107">如需詳細的資訊和範例，請參閱[XAttribute 類別概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4914a-107">For detailed information and examples, see [XAttribute Class Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xattribute-class-overview.md).</span></span>  
  
### <a name="xcdata-class"></a><span data-ttu-id="4914a-108">XCData 類別</span><span class="sxs-lookup"><span data-stu-id="4914a-108">XCData Class</span></span>  
 <span data-ttu-id="4914a-109"><xref:System.Xml.Linq.XCData>代表 CDATA 文字節點。</xref:System.Xml.Linq.XCData></span><span class="sxs-lookup"><span data-stu-id="4914a-109"><xref:System.Xml.Linq.XCData> represents a CDATA text node.</span></span>  
  
### <a name="xcomment-class"></a><span data-ttu-id="4914a-110">XComment 類別</span><span class="sxs-lookup"><span data-stu-id="4914a-110">XComment Class</span></span>  
 <span data-ttu-id="4914a-111"><xref:System.Xml.Linq.XComment>代表 XML 註解。</xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="4914a-111"><xref:System.Xml.Linq.XComment> represents an XML comment.</span></span>  
  
### <a name="xcontainer-class"></a><span data-ttu-id="4914a-112">XContainer 類別</span><span class="sxs-lookup"><span data-stu-id="4914a-112">XContainer Class</span></span>  
 <span data-ttu-id="4914a-113"><xref:System.Xml.Linq.XContainer>是可以有子節點的所有節點的抽象基底類別。</xref:System.Xml.Linq.XContainer></span><span class="sxs-lookup"><span data-stu-id="4914a-113"><xref:System.Xml.Linq.XContainer> is an abstract base class for all nodes that can have child nodes.</span></span> <span data-ttu-id="4914a-114">下列類別衍生自<xref:System.Xml.Linq.XContainer>類別︰</xref:System.Xml.Linq.XContainer></span><span class="sxs-lookup"><span data-stu-id="4914a-114">The following classes derive from the <xref:System.Xml.Linq.XContainer> class:</span></span>  
  
-   <span data-ttu-id="4914a-115"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="4914a-115"><xref:System.Xml.Linq.XElement></span></span>  
  
-   <span data-ttu-id="4914a-116"><xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="4914a-116"><xref:System.Xml.Linq.XDocument></span></span>  
  
### <a name="xdeclaration-class"></a><span data-ttu-id="4914a-117">XDeclaration 類別</span><span class="sxs-lookup"><span data-stu-id="4914a-117">XDeclaration Class</span></span>  
 <span data-ttu-id="4914a-118"><xref:System.Xml.Linq.XDeclaration>代表 XML 宣告。</xref:System.Xml.Linq.XDeclaration></span><span class="sxs-lookup"><span data-stu-id="4914a-118"><xref:System.Xml.Linq.XDeclaration> represents an XML declaration.</span></span> <span data-ttu-id="4914a-119">XML 宣告用於宣告 XML 版本與文件的編碼。</span><span class="sxs-lookup"><span data-stu-id="4914a-119">An XML declaration is used to declare the XML version and the encoding of a document.</span></span> <span data-ttu-id="4914a-120">此外，XML 宣告會指定 XML 文件是否為獨立的。</span><span class="sxs-lookup"><span data-stu-id="4914a-120">In addition, an XML declaration specifies whether the XML document is stand-alone.</span></span> <span data-ttu-id="4914a-121">如果文件是獨立的，外部 DTD 或內部子集所參考的外部參數實體 (Entity) 就不會包含任何外部標記宣告。</span><span class="sxs-lookup"><span data-stu-id="4914a-121">If a document is stand-alone, there are no external markup declarations, either in an external DTD, or in an external parameter entity referenced from the internal subset.</span></span>  
  
### <a name="xdocument-class"></a><span data-ttu-id="4914a-122">XDocument 類別</span><span class="sxs-lookup"><span data-stu-id="4914a-122">XDocument Class</span></span>  
 <span data-ttu-id="4914a-123"><xref:System.Xml.Linq.XDocument>表示 XML 文件。</xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="4914a-123"><xref:System.Xml.Linq.XDocument> represents an XML document.</span></span> <span data-ttu-id="4914a-124">如需詳細的資訊和範例，請參閱[XDocument 類別概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4914a-124">For detailed information and examples, see [XDocument Class Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).</span></span>  
  
### <a name="xdocumenttype-class"></a><span data-ttu-id="4914a-125">XDocumentType 類別</span><span class="sxs-lookup"><span data-stu-id="4914a-125">XDocumentType Class</span></span>  
 <span data-ttu-id="4914a-126"><xref:System.Xml.Linq.XDocumentType>代表 XML 文件類型定義 (DTD)。</xref:System.Xml.Linq.XDocumentType></span><span class="sxs-lookup"><span data-stu-id="4914a-126"><xref:System.Xml.Linq.XDocumentType> represents an XML Document Type Definition (DTD).</span></span>  
  
### <a name="xelement-class"></a><span data-ttu-id="4914a-127">XElement 類別</span><span class="sxs-lookup"><span data-stu-id="4914a-127">XElement Class</span></span>  
 <span data-ttu-id="4914a-128"><xref:System.Xml.Linq.XElement>表示 XML 項目。</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="4914a-128"><xref:System.Xml.Linq.XElement> represents an XML element.</span></span> <span data-ttu-id="4914a-129">如需詳細的資訊和範例，請參閱[XElement 類別概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4914a-129">For detailed information and examples, see [XElement Class Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xelement-class-overview.md).</span></span>  
  
### <a name="xname-class"></a><span data-ttu-id="4914a-130">XName 類別</span><span class="sxs-lookup"><span data-stu-id="4914a-130">XName Class</span></span>  
 <span data-ttu-id="4914a-131"><xref:System.Xml.Linq.XName>代表項目的名稱 (<xref:System.Xml.Linq.XElement>) 和屬性 (<xref:System.Xml.Linq.XAttribute>)。</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XElement></xref:System.Xml.Linq.XName></span><span class="sxs-lookup"><span data-stu-id="4914a-131"><xref:System.Xml.Linq.XName> represents names of elements (<xref:System.Xml.Linq.XElement>) and attributes (<xref:System.Xml.Linq.XAttribute>).</span></span> <span data-ttu-id="4914a-132">如需詳細的資訊和範例，請參閱[XDocument 類別概觀 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="4914a-132">For detailed information and examples, see [XDocument Class Overview (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/xdocument-class-overview.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="4914a-133"> 的設計是讓 XML 名稱盡可能直接。</span><span class="sxs-lookup"><span data-stu-id="4914a-133"> is designed to make XML names as straightforward as possible.</span></span> <span data-ttu-id="4914a-134">由於其複雜性的緣故，XML 名稱通常被視為 XML 的進階主題。</span><span class="sxs-lookup"><span data-stu-id="4914a-134">Due to their complexity, XML names are often considered to be an advanced topic in XML.</span></span> <span data-ttu-id="4914a-135">在論證上，這個複雜性不是來自於開發人員一般用於程式設計的命名空間，而是來自於命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="4914a-135">Arguably, this complexity comes not from namespaces, which developers use regularly in programming, but from namespace prefixes.</span></span> <span data-ttu-id="4914a-136">命名空間前置詞在減少輸入 XML 時所需的按鍵或在讓 XML 更容易讀取上，可能相當實用。</span><span class="sxs-lookup"><span data-stu-id="4914a-136">Namespace prefixes can be useful to reduce the keystrokes required when you input XML, or to make XML easier to read.</span></span> <span data-ttu-id="4914a-137">不過，前置詞通常是只使用完整的 XML 命名空間的捷徑，且不需要在大部分情況下。</span><span class="sxs-lookup"><span data-stu-id="4914a-137">However, prefixes are often just a shortcut for using the full XML namespace, and are not required in most cases.</span></span> [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="4914a-138">所有前置詞解析為其對應的 XML 命名空間，藉以簡化 XML 名稱。</span><span class="sxs-lookup"><span data-stu-id="4914a-138"> simplifies XML names by resolving all prefixes to their corresponding XML namespace.</span></span> <span data-ttu-id="4914a-139">前置詞可供使用，如有必要，透過<xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A>方法。</xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A></span><span class="sxs-lookup"><span data-stu-id="4914a-139">Prefixes are available, if they are required, through the <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> method.</span></span>  
  
 <span data-ttu-id="4914a-140">如有需要，可以控制命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="4914a-140">It is possible, if necessary, to control namespace prefixes.</span></span> <span data-ttu-id="4914a-141">在某些情況下，如果您要使用其他 XML 系統 (例如，XSLT 或 XAML)，您必須控制命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="4914a-141">In some circumstances, if you are working with other XML systems, such as XSLT or XAML, you need to control namespace prefixes.</span></span> <span data-ttu-id="4914a-142">例如，如果您所擁有的 XPath 運算式使用內嵌在 XSLT 樣式表中的命名空間前置詞，您就必須確認 XML 文件有利用符合 XPath 運算式中使用之命名空間前置詞的命名空間前置詞進行序列化。</span><span class="sxs-lookup"><span data-stu-id="4914a-142">For example, if you have an XPath expression that uses namespace prefixes and is embedded in an XSLT stylesheet, you must make sure that your XML document is serialized with namespace prefixes that match those used in the XPath expression.</span></span>  
  
### <a name="xnamespace-class"></a><span data-ttu-id="4914a-143">XNamespace 類別</span><span class="sxs-lookup"><span data-stu-id="4914a-143">XNamespace Class</span></span>  
 <span data-ttu-id="4914a-144"><xref:System.Xml.Linq.XNamespace>代表系統<xref:System.Xml.Linq.XElement>或<xref:System.Xml.Linq.XAttribute>.</xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XElement>的命名空間</xref:System.Xml.Linq.XNamespace></span><span class="sxs-lookup"><span data-stu-id="4914a-144"><xref:System.Xml.Linq.XNamespace> represents a namespace for an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="4914a-145">命名空間是<xref:System.Xml.Linq.XName>。</xref:System.Xml.Linq.XName>的元件</span><span class="sxs-lookup"><span data-stu-id="4914a-145">Namespaces are a component of an <xref:System.Xml.Linq.XName>.</span></span>  
  
### <a name="xnode-class"></a><span data-ttu-id="4914a-146">XNode 類別</span><span class="sxs-lookup"><span data-stu-id="4914a-146">XNode Class</span></span>  
 <span data-ttu-id="4914a-147"><xref:System.Xml.Linq.XNode>是抽象類別代表 XML 樹狀結構的節點。</xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="4914a-147"><xref:System.Xml.Linq.XNode> is an abstract class that represents the nodes of an XML tree.</span></span> <span data-ttu-id="4914a-148">下列類別衍生自<xref:System.Xml.Linq.XNode>類別︰</xref:System.Xml.Linq.XNode></span><span class="sxs-lookup"><span data-stu-id="4914a-148">The following classes derive from the <xref:System.Xml.Linq.XNode> class:</span></span>  
  
-   <span data-ttu-id="4914a-149"><xref:System.Xml.Linq.XText></xref:System.Xml.Linq.XText></span><span class="sxs-lookup"><span data-stu-id="4914a-149"><xref:System.Xml.Linq.XText></span></span>  
  
-   <span data-ttu-id="4914a-150"><xref:System.Xml.Linq.XContainer></xref:System.Xml.Linq.XContainer></span><span class="sxs-lookup"><span data-stu-id="4914a-150"><xref:System.Xml.Linq.XContainer></span></span>  
  
-   <span data-ttu-id="4914a-151"><xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="4914a-151"><xref:System.Xml.Linq.XComment></span></span>  
  
-   <span data-ttu-id="4914a-152"><xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="4914a-152"><xref:System.Xml.Linq.XProcessingInstruction></span></span>  
  
-   <span data-ttu-id="4914a-153"><xref:System.Xml.Linq.XDocumentType></xref:System.Xml.Linq.XDocumentType></span><span class="sxs-lookup"><span data-stu-id="4914a-153"><xref:System.Xml.Linq.XDocumentType></span></span>  
  
### <a name="xnodedocumentordercomparer-class"></a><span data-ttu-id="4914a-154">XNodeDocumentOrderComparer 類別</span><span class="sxs-lookup"><span data-stu-id="4914a-154">XNodeDocumentOrderComparer Class</span></span>  
 <span data-ttu-id="4914a-155"><xref:System.Xml.Linq.XNodeDocumentOrderComparer>提供功能，可針對其文件順序比較節點。</xref:System.Xml.Linq.XNodeDocumentOrderComparer></span><span class="sxs-lookup"><span data-stu-id="4914a-155"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> provides functionality to compare nodes for their document order.</span></span>  
  
### <a name="xnodeequalitycomparer-class"></a><span data-ttu-id="4914a-156">XNodeEqualityComparer 類別</span><span class="sxs-lookup"><span data-stu-id="4914a-156">XNodeEqualityComparer Class</span></span>  
 <span data-ttu-id="4914a-157"><xref:System.Xml.Linq.XNodeEqualityComparer>提供功能比較節點值相等。</xref:System.Xml.Linq.XNodeEqualityComparer></span><span class="sxs-lookup"><span data-stu-id="4914a-157"><xref:System.Xml.Linq.XNodeEqualityComparer> provides functionality to compare nodes for value equality.</span></span>  
  
### <a name="xobject-class"></a><span data-ttu-id="4914a-158">XObject 類別</span><span class="sxs-lookup"><span data-stu-id="4914a-158">XObject Class</span></span>  
 <span data-ttu-id="4914a-159"><xref:System.Xml.Linq.XObject>是抽象的基底類別和<xref:System.Xml.Linq.XNode><xref:System.Xml.Linq.XAttribute>。</xref:System.Xml.Linq.XAttribute> </xref:System.Xml.Linq.XNode></xref:System.Xml.Linq.XObject></span><span class="sxs-lookup"><span data-stu-id="4914a-159"><xref:System.Xml.Linq.XObject> is an abstract base class of <xref:System.Xml.Linq.XNode> and <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="4914a-160">它提供附註和事件的功能。</span><span class="sxs-lookup"><span data-stu-id="4914a-160">It provides annotation and event functionality.</span></span>  
  
### <a name="xobjectchange-class"></a><span data-ttu-id="4914a-161">XObjectChange 類別</span><span class="sxs-lookup"><span data-stu-id="4914a-161">XObjectChange Class</span></span>  
 <span data-ttu-id="4914a-162"><xref:System.Xml.Linq.XObjectChange><xref:System.Xml.Linq.XObject>.</xref:System.Xml.Linq.XObject>引發事件時指定的事件類型</xref:System.Xml.Linq.XObjectChange></span><span class="sxs-lookup"><span data-stu-id="4914a-162"><xref:System.Xml.Linq.XObjectChange> specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>  
  
### <a name="xobjectchangeeventargs-class"></a><span data-ttu-id="4914a-163">XObjectChangeEventArgs 類別</span><span class="sxs-lookup"><span data-stu-id="4914a-163">XObjectChangeEventArgs Class</span></span>  
 <span data-ttu-id="4914a-164"><xref:System.Xml.Linq.XObjectChangeEventArgs>提供資料給<xref:System.Xml.Linq.XObject.Changing>和<xref:System.Xml.Linq.XObject.Changed>事件。</xref:System.Xml.Linq.XObject.Changed> </xref:System.Xml.Linq.XObject.Changing></xref:System.Xml.Linq.XObjectChangeEventArgs></span><span class="sxs-lookup"><span data-stu-id="4914a-164"><xref:System.Xml.Linq.XObjectChangeEventArgs> provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>  
  
### <a name="xprocessinginstruction-class"></a><span data-ttu-id="4914a-165">XProcessingInstruction 類別</span><span class="sxs-lookup"><span data-stu-id="4914a-165">XProcessingInstruction Class</span></span>  
 <span data-ttu-id="4914a-166"><xref:System.Xml.Linq.XProcessingInstruction>代表 XML 處理指示。</xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="4914a-166"><xref:System.Xml.Linq.XProcessingInstruction> represents an XML processing instruction.</span></span> <span data-ttu-id="4914a-167">處理指示會將資訊傳達到處理 XML 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="4914a-167">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
### <a name="xtext-class"></a><span data-ttu-id="4914a-168">XText 類別</span><span class="sxs-lookup"><span data-stu-id="4914a-168">XText Class</span></span>  
 <span data-ttu-id="4914a-169"><xref:System.Xml.Linq.XText>代表文字節點。</xref:System.Xml.Linq.XText></span><span class="sxs-lookup"><span data-stu-id="4914a-169"><xref:System.Xml.Linq.XText> represents a text node.</span></span> <span data-ttu-id="4914a-170">在大部分的情況下，您不必使用這個類別。</span><span class="sxs-lookup"><span data-stu-id="4914a-170">In most cases, you do not have to use this class.</span></span> <span data-ttu-id="4914a-171">這個類別主要用於混合的內容。</span><span class="sxs-lookup"><span data-stu-id="4914a-171">This class is primarily used for mixed content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4914a-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4914a-172">See Also</span></span>  
 [<span data-ttu-id="4914a-173">LINQ to XML 程式設計概觀 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4914a-173">LINQ to XML Programming Overview (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
