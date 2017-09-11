---
title: "LINQ to XML 類別概觀 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f75a7a2aa3f9fca867562807595c6387b0be23d4
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-classes-overview-c"></a><span data-ttu-id="c3404-102">LINQ to XML 類別概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="c3404-102">LINQ to XML Classes Overview (C#)</span></span>
<span data-ttu-id="c3404-103">本主題提供 <xref:System.Xml.Linq> 命名空間中的 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] 類別清單，以及每個類別的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="c3404-103">This topic provides a list of the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] classes in the <xref:System.Xml.Linq> namespace, and a short description of each.</span></span>  
  
## <a name="linq-to-xml-classes"></a><span data-ttu-id="c3404-104">LINQ to XML 類別</span><span class="sxs-lookup"><span data-stu-id="c3404-104">LINQ to XML Classes</span></span>  
  
### <a name="xattribute-class"></a><span data-ttu-id="c3404-105">XAttribute 類別</span><span class="sxs-lookup"><span data-stu-id="c3404-105">XAttribute Class</span></span>  
 <span data-ttu-id="c3404-106"><xref:System.Xml.Linq.XAttribute> 代表 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="c3404-106"><xref:System.Xml.Linq.XAttribute> represents an XML attribute.</span></span> <span data-ttu-id="c3404-107">如需詳細的資訊和範例，請參閱 [XAttribute 類別概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/xattribute-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c3404-107">For detailed information and examples, see [XAttribute Class Overview (C#)](../../../../csharp/programming-guide/concepts/linq/xattribute-class-overview.md).</span></span>  
  
### <a name="xcdata-class"></a><span data-ttu-id="c3404-108">XCData 類別</span><span class="sxs-lookup"><span data-stu-id="c3404-108">XCData Class</span></span>  
 <span data-ttu-id="c3404-109"><xref:System.Xml.Linq.XCData> 代表 CDATA 文字節點。</span><span class="sxs-lookup"><span data-stu-id="c3404-109"><xref:System.Xml.Linq.XCData> represents a CDATA text node.</span></span>  
  
### <a name="xcomment-class"></a><span data-ttu-id="c3404-110">XComment 類別</span><span class="sxs-lookup"><span data-stu-id="c3404-110">XComment Class</span></span>  
 <span data-ttu-id="c3404-111"><xref:System.Xml.Linq.XComment> 代表 XML 註解。</span><span class="sxs-lookup"><span data-stu-id="c3404-111"><xref:System.Xml.Linq.XComment> represents an XML comment.</span></span>  
  
### <a name="xcontainer-class"></a><span data-ttu-id="c3404-112">XContainer 類別</span><span class="sxs-lookup"><span data-stu-id="c3404-112">XContainer Class</span></span>  
 <span data-ttu-id="c3404-113"><xref:System.Xml.Linq.XContainer> 對於可能擁有子節點的所有節點而言，是抽象基底類別。</span><span class="sxs-lookup"><span data-stu-id="c3404-113"><xref:System.Xml.Linq.XContainer> is an abstract base class for all nodes that can have child nodes.</span></span> <span data-ttu-id="c3404-114">下列類別衍生自 <xref:System.Xml.Linq.XContainer> 類別：</span><span class="sxs-lookup"><span data-stu-id="c3404-114">The following classes derive from the <xref:System.Xml.Linq.XContainer> class:</span></span>  
  
-   <span data-ttu-id="c3404-115"><xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="c3404-115"><xref:System.Xml.Linq.XElement></span></span>  
  
-   <span data-ttu-id="c3404-116"><xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XDocument></span><span class="sxs-lookup"><span data-stu-id="c3404-116"><xref:System.Xml.Linq.XDocument></span></span>  
  
### <a name="xdeclaration-class"></a><span data-ttu-id="c3404-117">XDeclaration 類別</span><span class="sxs-lookup"><span data-stu-id="c3404-117">XDeclaration Class</span></span>  
 <span data-ttu-id="c3404-118"><xref:System.Xml.Linq.XDeclaration> 代表 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="c3404-118"><xref:System.Xml.Linq.XDeclaration> represents an XML declaration.</span></span> <span data-ttu-id="c3404-119">XML 宣告用於宣告 XML 版本與文件的編碼。</span><span class="sxs-lookup"><span data-stu-id="c3404-119">An XML declaration is used to declare the XML version and the encoding of a document.</span></span> <span data-ttu-id="c3404-120">此外，XML 宣告會指定 XML 文件是否為獨立的。</span><span class="sxs-lookup"><span data-stu-id="c3404-120">In addition, an XML declaration specifies whether the XML document is stand-alone.</span></span> <span data-ttu-id="c3404-121">如果文件是獨立的，外部 DTD 或內部子集所參考的外部參數實體 (Entity) 就不會包含任何外部標記宣告。</span><span class="sxs-lookup"><span data-stu-id="c3404-121">If a document is stand-alone, there are no external markup declarations, either in an external DTD, or in an external parameter entity referenced from the internal subset.</span></span>  
  
### <a name="xdocument-class"></a><span data-ttu-id="c3404-122">XDocument 類別</span><span class="sxs-lookup"><span data-stu-id="c3404-122">XDocument Class</span></span>  
 <span data-ttu-id="c3404-123"><xref:System.Xml.Linq.XDocument> 代表 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="c3404-123"><xref:System.Xml.Linq.XDocument> represents an XML document.</span></span> <span data-ttu-id="c3404-124">如需詳細的資訊和範例，請參閱 [XDocument 類別概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/xdocument-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c3404-124">For detailed information and examples, see [XDocument Class Overview (C#)](../../../../csharp/programming-guide/concepts/linq/xdocument-class-overview.md).</span></span>  
  
### <a name="xdocumenttype-class"></a><span data-ttu-id="c3404-125">XDocumentType 類別</span><span class="sxs-lookup"><span data-stu-id="c3404-125">XDocumentType Class</span></span>  
 <span data-ttu-id="c3404-126"><xref:System.Xml.Linq.XDocumentType> 代表 XML 文件類型定義 (DTD)。</span><span class="sxs-lookup"><span data-stu-id="c3404-126"><xref:System.Xml.Linq.XDocumentType> represents an XML Document Type Definition (DTD).</span></span>  
  
### <a name="xelement-class"></a><span data-ttu-id="c3404-127">XElement 類別</span><span class="sxs-lookup"><span data-stu-id="c3404-127">XElement Class</span></span>  
 <span data-ttu-id="c3404-128"><xref:System.Xml.Linq.XElement> 代表 XML 元素。</span><span class="sxs-lookup"><span data-stu-id="c3404-128"><xref:System.Xml.Linq.XElement> represents an XML element.</span></span> <span data-ttu-id="c3404-129">如需詳細的資訊和範例，請參閱 [XElement 類別概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/xelement-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c3404-129">For detailed information and examples, see [XElement Class Overview (C#)](../../../../csharp/programming-guide/concepts/linq/xelement-class-overview.md).</span></span>  
  
### <a name="xname-class"></a><span data-ttu-id="c3404-130">XName 類別</span><span class="sxs-lookup"><span data-stu-id="c3404-130">XName Class</span></span>  
 <span data-ttu-id="c3404-131"><xref:System.Xml.Linq.XName> 代表項目的名稱 (<xref:System.Xml.Linq.XElement>) 和屬性 (<xref:System.Xml.Linq.XAttribute>)。</span><span class="sxs-lookup"><span data-stu-id="c3404-131"><xref:System.Xml.Linq.XName> represents names of elements (<xref:System.Xml.Linq.XElement>) and attributes (<xref:System.Xml.Linq.XAttribute>).</span></span> <span data-ttu-id="c3404-132">如需詳細的資訊和範例，請參閱 [XDocument 類別概觀 (C#)](../../../../csharp/programming-guide/concepts/linq/xdocument-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="c3404-132">For detailed information and examples, see [XDocument Class Overview (C#)](../../../../csharp/programming-guide/concepts/linq/xdocument-class-overview.md).</span></span>  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="c3404-133"> 的設計是讓 XML 名稱盡可能直接。</span><span class="sxs-lookup"><span data-stu-id="c3404-133"> is designed to make XML names as straightforward as possible.</span></span> <span data-ttu-id="c3404-134">由於其複雜性的緣故，XML 名稱通常被視為 XML 的進階主題。</span><span class="sxs-lookup"><span data-stu-id="c3404-134">Due to their complexity, XML names are often considered to be an advanced topic in XML.</span></span> <span data-ttu-id="c3404-135">在論證上，這個複雜性不是來自於開發人員一般用於程式設計的命名空間，而是來自於命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="c3404-135">Arguably, this complexity comes not from namespaces, which developers use regularly in programming, but from namespace prefixes.</span></span> <span data-ttu-id="c3404-136">命名空間前置詞在減少輸入 XML 時所需的按鍵或在讓 XML 更容易讀取上，可能相當實用。</span><span class="sxs-lookup"><span data-stu-id="c3404-136">Namespace prefixes can be useful to reduce the keystrokes required when you input XML, or to make XML easier to read.</span></span> <span data-ttu-id="c3404-137">不過，前置詞通常只是用來使用完整 XML 命名空間的捷徑，因此大部分情況中都不需要。</span><span class="sxs-lookup"><span data-stu-id="c3404-137">However, prefixes are often just a shortcut for using the full XML namespace, and are not required in most cases.</span></span> [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]<span data-ttu-id="c3404-138"> 會將所有前置詞解析為其對應的 XML 命名空間，藉以簡化 XML 名稱。</span><span class="sxs-lookup"><span data-stu-id="c3404-138"> simplifies XML names by resolving all prefixes to their corresponding XML namespace.</span></span> <span data-ttu-id="c3404-139">若有必要，您可以透過 <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> 方法取得前置詞。</span><span class="sxs-lookup"><span data-stu-id="c3404-139">Prefixes are available, if they are required, through the <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> method.</span></span>  
  
 <span data-ttu-id="c3404-140">如有需要，可以控制命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="c3404-140">It is possible, if necessary, to control namespace prefixes.</span></span> <span data-ttu-id="c3404-141">在某些情況下，如果您要使用其他 XML 系統 (例如，XSLT 或 XAML)，您必須控制命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="c3404-141">In some circumstances, if you are working with other XML systems, such as XSLT or XAML, you need to control namespace prefixes.</span></span> <span data-ttu-id="c3404-142">例如，如果您所擁有的 XPath 運算式使用內嵌在 XSLT 樣式表中的命名空間前置詞，您就必須確認 XML 文件有利用符合 XPath 運算式中使用之命名空間前置詞的命名空間前置詞進行序列化。</span><span class="sxs-lookup"><span data-stu-id="c3404-142">For example, if you have an XPath expression that uses namespace prefixes and is embedded in an XSLT stylesheet, you must make sure that your XML document is serialized with namespace prefixes that match those used in the XPath expression.</span></span>  
  
### <a name="xnamespace-class"></a><span data-ttu-id="c3404-143">XNamespace 類別</span><span class="sxs-lookup"><span data-stu-id="c3404-143">XNamespace Class</span></span>  
 <span data-ttu-id="c3404-144"><xref:System.Xml.Linq.XNamespace> 代表 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 的命名空間。</span><span class="sxs-lookup"><span data-stu-id="c3404-144"><xref:System.Xml.Linq.XNamespace> represents a namespace for an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="c3404-145">命名空間是 <xref:System.Xml.Linq.XName> 的元件。</span><span class="sxs-lookup"><span data-stu-id="c3404-145">Namespaces are a component of an <xref:System.Xml.Linq.XName>.</span></span>  
  
### <a name="xnode-class"></a><span data-ttu-id="c3404-146">XNode 類別</span><span class="sxs-lookup"><span data-stu-id="c3404-146">XNode Class</span></span>  
 <span data-ttu-id="c3404-147"><xref:System.Xml.Linq.XNode> 是代表 XML 樹狀結構節點的抽象類別。</span><span class="sxs-lookup"><span data-stu-id="c3404-147"><xref:System.Xml.Linq.XNode> is an abstract class that represents the nodes of an XML tree.</span></span> <span data-ttu-id="c3404-148">下列類別衍生自 <xref:System.Xml.Linq.XNode> 類別：</span><span class="sxs-lookup"><span data-stu-id="c3404-148">The following classes derive from the <xref:System.Xml.Linq.XNode> class:</span></span>  
  
-   <span data-ttu-id="c3404-149"><xref:System.Xml.Linq.XText></span><span class="sxs-lookup"><span data-stu-id="c3404-149"><xref:System.Xml.Linq.XText></span></span>  
  
-   <span data-ttu-id="c3404-150"><xref:System.Xml.Linq.XContainer></span><span class="sxs-lookup"><span data-stu-id="c3404-150"><xref:System.Xml.Linq.XContainer></span></span>  
  
-   <span data-ttu-id="c3404-151"><xref:System.Xml.Linq.XComment></span><span class="sxs-lookup"><span data-stu-id="c3404-151"><xref:System.Xml.Linq.XComment></span></span>  
  
-   <span data-ttu-id="c3404-152"><xref:System.Xml.Linq.XProcessingInstruction></span><span class="sxs-lookup"><span data-stu-id="c3404-152"><xref:System.Xml.Linq.XProcessingInstruction></span></span>  
  
-   <span data-ttu-id="c3404-153"><xref:System.Xml.Linq.XDocumentType></span><span class="sxs-lookup"><span data-stu-id="c3404-153"><xref:System.Xml.Linq.XDocumentType></span></span>  
  
### <a name="xnodedocumentordercomparer-class"></a><span data-ttu-id="c3404-154">XNodeDocumentOrderComparer 類別</span><span class="sxs-lookup"><span data-stu-id="c3404-154">XNodeDocumentOrderComparer Class</span></span>  
 <span data-ttu-id="c3404-155"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> 提供針對文件順序來比較節點的功能。</span><span class="sxs-lookup"><span data-stu-id="c3404-155"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> provides functionality to compare nodes for their document order.</span></span>  
  
### <a name="xnodeequalitycomparer-class"></a><span data-ttu-id="c3404-156">XNodeEqualityComparer 類別</span><span class="sxs-lookup"><span data-stu-id="c3404-156">XNodeEqualityComparer Class</span></span>  
 <span data-ttu-id="c3404-157"><xref:System.Xml.Linq.XNodeEqualityComparer> 提供可比較節點是否實值相等的功能。</span><span class="sxs-lookup"><span data-stu-id="c3404-157"><xref:System.Xml.Linq.XNodeEqualityComparer> provides functionality to compare nodes for value equality.</span></span>  
  
### <a name="xobject-class"></a><span data-ttu-id="c3404-158">XObject 類別</span><span class="sxs-lookup"><span data-stu-id="c3404-158">XObject Class</span></span>  
 <span data-ttu-id="c3404-159"><xref:System.Xml.Linq.XObject> 是 <xref:System.Xml.Linq.XNode> 和 <xref:System.Xml.Linq.XAttribute> 的抽象基底類別。</span><span class="sxs-lookup"><span data-stu-id="c3404-159"><xref:System.Xml.Linq.XObject> is an abstract base class of <xref:System.Xml.Linq.XNode> and <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="c3404-160">它提供附註和事件的功能。</span><span class="sxs-lookup"><span data-stu-id="c3404-160">It provides annotation and event functionality.</span></span>  
  
### <a name="xobjectchange-class"></a><span data-ttu-id="c3404-161">XObjectChange 類別</span><span class="sxs-lookup"><span data-stu-id="c3404-161">XObjectChange Class</span></span>  
 <span data-ttu-id="c3404-162"><xref:System.Xml.Linq.XObjectChange> 指定引發 <xref:System.Xml.Linq.XObject> 事件時的事件類型。</span><span class="sxs-lookup"><span data-stu-id="c3404-162"><xref:System.Xml.Linq.XObjectChange> specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>  
  
### <a name="xobjectchangeeventargs-class"></a><span data-ttu-id="c3404-163">XObjectChangeEventArgs 類別</span><span class="sxs-lookup"><span data-stu-id="c3404-163">XObjectChangeEventArgs Class</span></span>  
 <span data-ttu-id="c3404-164"><xref:System.Xml.Linq.XObjectChangeEventArgs> 可提供 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed> 事件的資料。</span><span class="sxs-lookup"><span data-stu-id="c3404-164"><xref:System.Xml.Linq.XObjectChangeEventArgs> provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>  
  
### <a name="xprocessinginstruction-class"></a><span data-ttu-id="c3404-165">XProcessingInstruction 類別</span><span class="sxs-lookup"><span data-stu-id="c3404-165">XProcessingInstruction Class</span></span>  
 <span data-ttu-id="c3404-166"><xref:System.Xml.Linq.XProcessingInstruction> 代表 XML 處理指示。</span><span class="sxs-lookup"><span data-stu-id="c3404-166"><xref:System.Xml.Linq.XProcessingInstruction> represents an XML processing instruction.</span></span> <span data-ttu-id="c3404-167">處理指示會將資訊傳達到處理 XML 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="c3404-167">A processing instruction communicates information to an application that processes the XML.</span></span>  
  
### <a name="xtext-class"></a><span data-ttu-id="c3404-168">XText 類別</span><span class="sxs-lookup"><span data-stu-id="c3404-168">XText Class</span></span>  
 <span data-ttu-id="c3404-169"><xref:System.Xml.Linq.XText> 代表文字節點。</span><span class="sxs-lookup"><span data-stu-id="c3404-169"><xref:System.Xml.Linq.XText> represents a text node.</span></span> <span data-ttu-id="c3404-170">在大部分的情況下，您不必使用這個類別。</span><span class="sxs-lookup"><span data-stu-id="c3404-170">In most cases, you do not have to use this class.</span></span> <span data-ttu-id="c3404-171">這個類別主要用於混合的內容。</span><span class="sxs-lookup"><span data-stu-id="c3404-171">This class is primarily used for mixed content.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3404-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c3404-172">See Also</span></span>  
 [<span data-ttu-id="c3404-173">LINQ to XML 程式設計概觀 (C#)</span><span class="sxs-lookup"><span data-stu-id="c3404-173">LINQ to XML Programming Overview (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-programming-overview.md)
