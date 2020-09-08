---
title: LINQ to XML 類別總覽
description: 本文提供 LINQ to XML 類別的清單，並提供每個類別的說明。
ms.date: 07/20/2015
ms.assetid: bf666100-5392-4968-97f4-f6b9d3287d7b
ms.openlocfilehash: 83258425b464d8547def5cce6a3e8da19ef21966
ms.sourcegitcommit: 0c3ce6d2e7586d925a30f231f32046b7b3934acb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2020
ms.locfileid: "89552236"
---
# <a name="linq-to-xml-classes-overview"></a><span data-ttu-id="80d94-103">LINQ to XML 類別總覽</span><span class="sxs-lookup"><span data-stu-id="80d94-103">LINQ to XML classes overview</span></span>

<span data-ttu-id="80d94-104">本文提供命名空間中 LINQ to XML 類別的清單 <xref:System.Xml.Linq> ，以及每個類別的簡短描述。</span><span class="sxs-lookup"><span data-stu-id="80d94-104">This article provides a list of the LINQ to XML classes in the <xref:System.Xml.Linq> namespace, and a short description of each.</span></span>

## <a name="linq-to-xml-classes"></a><span data-ttu-id="80d94-105">LINQ to XML 類別</span><span class="sxs-lookup"><span data-stu-id="80d94-105">LINQ to XML classes</span></span>

### <a name="xattribute-class"></a><span data-ttu-id="80d94-106">XAttribute 類別</span><span class="sxs-lookup"><span data-stu-id="80d94-106">XAttribute class</span></span>

<span data-ttu-id="80d94-107"><xref:System.Xml.Linq.XAttribute> 代表 XML 屬性。</span><span class="sxs-lookup"><span data-stu-id="80d94-107"><xref:System.Xml.Linq.XAttribute> represents an XML attribute.</span></span> <span data-ttu-id="80d94-108">如需詳細資訊和範例，請參閱 [system.xml.linq.xattribute> 類別總覽](xattribute-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="80d94-108">For detailed information and examples, see [XAttribute class overview](xattribute-class-overview.md).</span></span>

### <a name="xcdata-class"></a><span data-ttu-id="80d94-109">XCData 類別</span><span class="sxs-lookup"><span data-stu-id="80d94-109">XCData class</span></span>

<span data-ttu-id="80d94-110"><xref:System.Xml.Linq.XCData> 代表 CDATA 文字節點。</span><span class="sxs-lookup"><span data-stu-id="80d94-110"><xref:System.Xml.Linq.XCData> represents a CDATA text node.</span></span>

### <a name="xcomment-class"></a><span data-ttu-id="80d94-111">System.xml.linq.xcomment> 類別</span><span class="sxs-lookup"><span data-stu-id="80d94-111">XComment class</span></span>

<span data-ttu-id="80d94-112"><xref:System.Xml.Linq.XComment> 代表 XML 註解。</span><span class="sxs-lookup"><span data-stu-id="80d94-112"><xref:System.Xml.Linq.XComment> represents an XML comment.</span></span>

### <a name="xcontainer-class"></a><span data-ttu-id="80d94-113">System.xml.linq.xcontainer.elements 類別</span><span class="sxs-lookup"><span data-stu-id="80d94-113">XContainer class</span></span>

<span data-ttu-id="80d94-114"><xref:System.Xml.Linq.XContainer> 對於可能擁有子節點的所有節點而言，是抽象基底類別。</span><span class="sxs-lookup"><span data-stu-id="80d94-114"><xref:System.Xml.Linq.XContainer> is an abstract base class for all nodes that can have child nodes.</span></span> <span data-ttu-id="80d94-115">下列類別衍生自 <xref:System.Xml.Linq.XContainer> 類別：</span><span class="sxs-lookup"><span data-stu-id="80d94-115">The following classes derive from the <xref:System.Xml.Linq.XContainer> class:</span></span>

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XDocument>

### <a name="xdeclaration-class"></a><span data-ttu-id="80d94-116">XDeclaration 類別</span><span class="sxs-lookup"><span data-stu-id="80d94-116">XDeclaration class</span></span>

<span data-ttu-id="80d94-117"><xref:System.Xml.Linq.XDeclaration> 代表 XML 宣告。</span><span class="sxs-lookup"><span data-stu-id="80d94-117"><xref:System.Xml.Linq.XDeclaration> represents an XML declaration.</span></span> <span data-ttu-id="80d94-118">XML 宣告用於宣告 XML 版本與文件的編碼。</span><span class="sxs-lookup"><span data-stu-id="80d94-118">An XML declaration is used to declare the XML version and the encoding of a document.</span></span> <span data-ttu-id="80d94-119">此外，XML 宣告會指定 XML 文件是否為獨立的。</span><span class="sxs-lookup"><span data-stu-id="80d94-119">In addition, an XML declaration specifies whether the XML document is stand-alone.</span></span> <span data-ttu-id="80d94-120">如果文件是獨立的，外部 DTD 或內部子集所參考的外部參數實體 (Entity) 就不會包含任何外部標記宣告。</span><span class="sxs-lookup"><span data-stu-id="80d94-120">If a document is stand-alone, there are no external markup declarations, either in an external DTD, or in an external parameter entity referenced from the internal subset.</span></span>

### <a name="xdocument-class"></a><span data-ttu-id="80d94-121">XDocument 類別</span><span class="sxs-lookup"><span data-stu-id="80d94-121">XDocument class</span></span>

<span data-ttu-id="80d94-122"><xref:System.Xml.Linq.XDocument> 代表 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="80d94-122"><xref:System.Xml.Linq.XDocument> represents an XML document.</span></span> <span data-ttu-id="80d94-123">如需詳細資訊和範例，請參閱 [XDocument 類別總覽](xdocument-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="80d94-123">For detailed information and examples, see [XDocument class overview](xdocument-class-overview.md).</span></span>

### <a name="xdocumenttype-class"></a><span data-ttu-id="80d94-124">System.xml.linq.xdocumenttype> 類別</span><span class="sxs-lookup"><span data-stu-id="80d94-124">XDocumentType class</span></span>

<span data-ttu-id="80d94-125"><xref:System.Xml.Linq.XDocumentType> 代表 XML 文件類型定義 (DTD)。</span><span class="sxs-lookup"><span data-stu-id="80d94-125"><xref:System.Xml.Linq.XDocumentType> represents an XML Document Type Definition (DTD).</span></span>

### <a name="xelement-class"></a><span data-ttu-id="80d94-126">XElement 類別</span><span class="sxs-lookup"><span data-stu-id="80d94-126">XElement class</span></span>

<span data-ttu-id="80d94-127"><xref:System.Xml.Linq.XElement> 代表 XML 項目。</span><span class="sxs-lookup"><span data-stu-id="80d94-127"><xref:System.Xml.Linq.XElement> represents an XML element.</span></span> <span data-ttu-id="80d94-128">如需詳細資訊和範例，請參閱 [system.xml.linq.xelement> 類別總覽](xelement-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="80d94-128">For detailed information and examples, see [XElement class overview](xelement-class-overview.md).</span></span>

### <a name="xname-class"></a><span data-ttu-id="80d94-129">XName 類別</span><span class="sxs-lookup"><span data-stu-id="80d94-129">XName class</span></span>

<span data-ttu-id="80d94-130"><xref:System.Xml.Linq.XName> 代表項目的名稱 (<xref:System.Xml.Linq.XElement>) 與屬性 (<xref:System.Xml.Linq.XAttribute>)。</span><span class="sxs-lookup"><span data-stu-id="80d94-130"><xref:System.Xml.Linq.XName> represents names of elements (<xref:System.Xml.Linq.XElement>) and attributes (<xref:System.Xml.Linq.XAttribute>).</span></span> <span data-ttu-id="80d94-131">如需詳細資訊和範例，請參閱 [XDocument 類別總覽](xdocument-class-overview.md)。</span><span class="sxs-lookup"><span data-stu-id="80d94-131">For detailed information and examples, see [XDocument class overview](xdocument-class-overview.md).</span></span>

<span data-ttu-id="80d94-132">LINQ to XML 的設計目的是讓 XML 名稱盡可能簡單明瞭。</span><span class="sxs-lookup"><span data-stu-id="80d94-132">LINQ to XML is designed to make XML names as straightforward as possible.</span></span> <span data-ttu-id="80d94-133">由於複雜性的緣故，XML 名稱通常被視為 XML 的 advanced 文章。</span><span class="sxs-lookup"><span data-stu-id="80d94-133">Due to their complexity, XML names are often considered to be an advanced article in XML.</span></span> <span data-ttu-id="80d94-134">在論證上，這個複雜性不是來自於開發人員一般用於程式設計的命名空間，而是來自於命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="80d94-134">Arguably, this complexity comes not from namespaces, which developers use regularly in programming, but from namespace prefixes.</span></span> <span data-ttu-id="80d94-135">命名空間前置詞在減少輸入 XML 時所需的按鍵或在讓 XML 更容易讀取上，可能相當實用。</span><span class="sxs-lookup"><span data-stu-id="80d94-135">Namespace prefixes can be useful to reduce the keystrokes required when you input XML, or to make XML easier to read.</span></span> <span data-ttu-id="80d94-136">不過，前置詞通常只是使用完整 XML 命名空間的快捷方式，在大部分情況下都不需要。</span><span class="sxs-lookup"><span data-stu-id="80d94-136">However, prefixes are often just a shortcut for using the full XML namespace, and aren't required in most cases.</span></span> <span data-ttu-id="80d94-137">LINQ to XML 藉由將所有前置詞解析為其對應的 XML 命名空間，藉以簡化 XML 名稱。</span><span class="sxs-lookup"><span data-stu-id="80d94-137">LINQ to XML simplifies XML names by resolving all prefixes to their corresponding XML namespace.</span></span> <span data-ttu-id="80d94-138">您可以透過方法取得前置詞（如果需要的話） <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> 。</span><span class="sxs-lookup"><span data-stu-id="80d94-138">Prefixes are available, if they're required, through the <xref:System.Xml.Linq.XElement.GetPrefixOfNamespace%2A> method.</span></span>

<span data-ttu-id="80d94-139">如有必要，您可以控制命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="80d94-139">it's possible, if necessary, to control namespace prefixes.</span></span> <span data-ttu-id="80d94-140">在某些情況下，如果您要使用其他 XML 系統（例如 XSLT 或 XAML），則需要控制命名空間前置詞。</span><span class="sxs-lookup"><span data-stu-id="80d94-140">In some circumstances, if you're working with other XML systems, such as XSLT or XAML, you need to control namespace prefixes.</span></span> <span data-ttu-id="80d94-141">例如，如果您所擁有的 XPath 運算式使用內嵌在 XSLT 樣式表中的命名空間前置詞，您就必須確認 XML 文件有利用符合 XPath 運算式中使用之命名空間前置詞的命名空間前置詞進行序列化。</span><span class="sxs-lookup"><span data-stu-id="80d94-141">For example, if you have an XPath expression that uses namespace prefixes and is embedded in an XSLT stylesheet, you must make sure that your XML document is serialized with namespace prefixes that match those used in the XPath expression.</span></span>

### <a name="xnamespace-class"></a><span data-ttu-id="80d94-142">XNamespace 類別</span><span class="sxs-lookup"><span data-stu-id="80d94-142">XNamespace class</span></span>

<span data-ttu-id="80d94-143"><xref:System.Xml.Linq.XNamespace> 代表 <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute> 的命名空間。</span><span class="sxs-lookup"><span data-stu-id="80d94-143"><xref:System.Xml.Linq.XNamespace> represents a namespace for an <xref:System.Xml.Linq.XElement> or <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="80d94-144">命名空間是 <xref:System.Xml.Linq.XName> 的元件。</span><span class="sxs-lookup"><span data-stu-id="80d94-144">Namespaces are a component of an <xref:System.Xml.Linq.XName>.</span></span>

### <a name="xnode-class"></a><span data-ttu-id="80d94-145">System.xml.linq.xnode> 類別</span><span class="sxs-lookup"><span data-stu-id="80d94-145">XNode class</span></span>

<span data-ttu-id="80d94-146"><xref:System.Xml.Linq.XNode> 是代表 XML 樹狀結構節點的抽象類別。</span><span class="sxs-lookup"><span data-stu-id="80d94-146"><xref:System.Xml.Linq.XNode> is an abstract class that represents the nodes of an XML tree.</span></span> <span data-ttu-id="80d94-147">下列類別衍生自 <xref:System.Xml.Linq.XNode> 類別：</span><span class="sxs-lookup"><span data-stu-id="80d94-147">The following classes derive from the <xref:System.Xml.Linq.XNode> class:</span></span>

- <xref:System.Xml.Linq.XText>
- <xref:System.Xml.Linq.XContainer>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XDocumentType>

### <a name="xnodedocumentordercomparer-class"></a><span data-ttu-id="80d94-148">XNodeDocumentOrderComparer 類別</span><span class="sxs-lookup"><span data-stu-id="80d94-148">XNodeDocumentOrderComparer class</span></span>

<span data-ttu-id="80d94-149"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> 會提供功能，針對其文件順序比較節點。</span><span class="sxs-lookup"><span data-stu-id="80d94-149"><xref:System.Xml.Linq.XNodeDocumentOrderComparer> provides functionality to compare nodes for their document order.</span></span>

### <a name="xnodeequalitycomparer-class"></a><span data-ttu-id="80d94-150">XNodeEqualityComparer 類別</span><span class="sxs-lookup"><span data-stu-id="80d94-150">XNodeEqualityComparer class</span></span>

<span data-ttu-id="80d94-151"><xref:System.Xml.Linq.XNodeEqualityComparer> 會提供功能，針對值的相等性比較節點。</span><span class="sxs-lookup"><span data-stu-id="80d94-151"><xref:System.Xml.Linq.XNodeEqualityComparer> provides functionality to compare nodes for value equality.</span></span>

### <a name="xobject-class"></a><span data-ttu-id="80d94-152">XObject 類別</span><span class="sxs-lookup"><span data-stu-id="80d94-152">XObject class</span></span>

<span data-ttu-id="80d94-153"><xref:System.Xml.Linq.XObject> 是 <xref:System.Xml.Linq.XNode> 和 <xref:System.Xml.Linq.XAttribute> 的抽象基底類別。</span><span class="sxs-lookup"><span data-stu-id="80d94-153"><xref:System.Xml.Linq.XObject> is an abstract base class of <xref:System.Xml.Linq.XNode> and <xref:System.Xml.Linq.XAttribute>.</span></span> <span data-ttu-id="80d94-154">它提供附註和事件的功能。</span><span class="sxs-lookup"><span data-stu-id="80d94-154">It provides annotation and event functionality.</span></span>

### <a name="xobjectchange-class"></a><span data-ttu-id="80d94-155">XObjectChange 類別</span><span class="sxs-lookup"><span data-stu-id="80d94-155">XObjectChange class</span></span>

<span data-ttu-id="80d94-156">引發 <xref:System.Xml.Linq.XObjectChange> 的事件時，<xref:System.Xml.Linq.XObject> 會指定事件類型。</span><span class="sxs-lookup"><span data-stu-id="80d94-156"><xref:System.Xml.Linq.XObjectChange> specifies the event type when an event is raised for an <xref:System.Xml.Linq.XObject>.</span></span>

### <a name="xobjectchangeeventargs-class"></a><span data-ttu-id="80d94-157">XObjectChangeEventArgs 類別</span><span class="sxs-lookup"><span data-stu-id="80d94-157">XObjectChangeEventArgs class</span></span>

<span data-ttu-id="80d94-158"><xref:System.Xml.Linq.XObjectChangeEventArgs> 會提供 <xref:System.Xml.Linq.XObject.Changing> 和 <xref:System.Xml.Linq.XObject.Changed> 事件的資料。</span><span class="sxs-lookup"><span data-stu-id="80d94-158"><xref:System.Xml.Linq.XObjectChangeEventArgs> provides data for the <xref:System.Xml.Linq.XObject.Changing> and <xref:System.Xml.Linq.XObject.Changed> events.</span></span>

### <a name="xprocessinginstruction-class"></a><span data-ttu-id="80d94-159">System.xml.linq.xprocessinginstruction> 類別</span><span class="sxs-lookup"><span data-stu-id="80d94-159">XProcessingInstruction class</span></span>

<span data-ttu-id="80d94-160"><xref:System.Xml.Linq.XProcessingInstruction> 代表 XML 處理指示。</span><span class="sxs-lookup"><span data-stu-id="80d94-160"><xref:System.Xml.Linq.XProcessingInstruction> represents an XML processing instruction.</span></span> <span data-ttu-id="80d94-161">處理指示會將資訊傳達到處理 XML 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="80d94-161">A processing instruction communicates information to an application that processes the XML.</span></span>

### <a name="xtext-class"></a><span data-ttu-id="80d94-162">System.xml.linq.xtext> 類別</span><span class="sxs-lookup"><span data-stu-id="80d94-162">XText class</span></span>

<span data-ttu-id="80d94-163"><xref:System.Xml.Linq.XText> 代表文字節點。</span><span class="sxs-lookup"><span data-stu-id="80d94-163"><xref:System.Xml.Linq.XText> represents a text node.</span></span> <span data-ttu-id="80d94-164">在大多數情況下，您不需要使用這個類別。</span><span class="sxs-lookup"><span data-stu-id="80d94-164">In most cases, you don't have to use this class.</span></span> <span data-ttu-id="80d94-165">這個類別主要用於混合的內容。</span><span class="sxs-lookup"><span data-stu-id="80d94-165">This class is primarily used for mixed content.</span></span>
