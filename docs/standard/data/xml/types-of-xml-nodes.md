---
title: "XML 節點的型別"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71d03b78-6898-4ce7-b0fc-1282573f31f7
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3914a2c5c06a2cc73f14bc473984094b474d537e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="types-of-xml-nodes"></a><span data-ttu-id="2e26a-102">XML 節點的型別</span><span class="sxs-lookup"><span data-stu-id="2e26a-102">Types of XML Nodes</span></span>
<span data-ttu-id="2e26a-103">當 XML 文件讀入記憶體作為節點的樹狀時，節點建立時即會決定節點型別。</span><span class="sxs-lookup"><span data-stu-id="2e26a-103">When an XML document is read into memory as a tree of nodes, the node types for the nodes are decided when the nodes are created.</span></span> <span data-ttu-id="2e26a-104">XML 文件物件模型 (DOM) 有許多種節點型別，由全球資訊網協會 (W3C) 決定並列示於＜1.1.1 DOM 架構模型＞(英文) 一節中。</span><span class="sxs-lookup"><span data-stu-id="2e26a-104">The XML Document Object Model (DOM) has several kinds of node types, determined by the World Wide Web Consortium (W3C) and listed in section 1.1.1 The DOM Structure Model.</span></span> <span data-ttu-id="2e26a-105">下列表格會列出節點型別、指派給該節點類型的物件，以及每個節點型別的簡要說明。</span><span class="sxs-lookup"><span data-stu-id="2e26a-105">The following table lists the node types, the object assigned to that node type, and a short description of each.</span></span>  
  
|<span data-ttu-id="2e26a-106">DOM 節點型別</span><span class="sxs-lookup"><span data-stu-id="2e26a-106">DOM node type</span></span>|<span data-ttu-id="2e26a-107">物件</span><span class="sxs-lookup"><span data-stu-id="2e26a-107">Object</span></span>|<span data-ttu-id="2e26a-108">描述</span><span class="sxs-lookup"><span data-stu-id="2e26a-108">Description</span></span>|  
|-------------------|------------|-----------------|  
|<span data-ttu-id="2e26a-109">文件</span><span class="sxs-lookup"><span data-stu-id="2e26a-109">Document</span></span>|<xref:System.Xml.XmlDocument>|<span data-ttu-id="2e26a-110">樹狀中所有節點的容器。</span><span class="sxs-lookup"><span data-stu-id="2e26a-110">The container of all the nodes in the tree.</span></span> <span data-ttu-id="2e26a-111">它也稱為文件根，不一定總是與根項目相同。</span><span class="sxs-lookup"><span data-stu-id="2e26a-111">It is also known as the document root, which is not always the same as the root element.</span></span>|  
|<span data-ttu-id="2e26a-112">DocumentFragment</span><span class="sxs-lookup"><span data-stu-id="2e26a-112">DocumentFragment</span></span>|<xref:System.Xml.XmlDocumentFragment>|<span data-ttu-id="2e26a-113">包含一或多個節點，而沒有樹狀的暫存封包。</span><span class="sxs-lookup"><span data-stu-id="2e26a-113">A temporary bag containing one or more nodes without any tree structure.</span></span>|  
|<span data-ttu-id="2e26a-114">DocumentType</span><span class="sxs-lookup"><span data-stu-id="2e26a-114">DocumentType</span></span>|<xref:System.Xml.XmlDocumentType>|<span data-ttu-id="2e26a-115">表示 `<!DOCTYPE…>` 節點。</span><span class="sxs-lookup"><span data-stu-id="2e26a-115">Represents the `<!DOCTYPE…>` node.</span></span>|  
|<span data-ttu-id="2e26a-116">EntityReference</span><span class="sxs-lookup"><span data-stu-id="2e26a-116">EntityReference</span></span>|<xref:System.Xml.XmlEntityReference>|<span data-ttu-id="2e26a-117">表示未擴充的實體參考文字。</span><span class="sxs-lookup"><span data-stu-id="2e26a-117">Represents the non-expanded entity reference text.</span></span>|  
|<span data-ttu-id="2e26a-118">項目</span><span class="sxs-lookup"><span data-stu-id="2e26a-118">Element</span></span>|<xref:System.Xml.XmlElement>|<span data-ttu-id="2e26a-119">表示項目節點。</span><span class="sxs-lookup"><span data-stu-id="2e26a-119">Represents an element node.</span></span>|  
|<span data-ttu-id="2e26a-120">Attr</span><span class="sxs-lookup"><span data-stu-id="2e26a-120">Attr</span></span>|<xref:System.Xml.XmlAttribute>|<span data-ttu-id="2e26a-121">是項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="2e26a-121">Is an attribute of an element.</span></span>|  
|<span data-ttu-id="2e26a-122">ProcessingInstruction</span><span class="sxs-lookup"><span data-stu-id="2e26a-122">ProcessingInstruction</span></span>|<xref:System.Xml.XmlProcessingInstruction>|<span data-ttu-id="2e26a-123">是處理的指示節點。</span><span class="sxs-lookup"><span data-stu-id="2e26a-123">Is a processing instruction node.</span></span>|  
|<span data-ttu-id="2e26a-124">註解</span><span class="sxs-lookup"><span data-stu-id="2e26a-124">Comment</span></span>|<xref:System.Xml.XmlComment>|<span data-ttu-id="2e26a-125">註解節點。</span><span class="sxs-lookup"><span data-stu-id="2e26a-125">A comment node.</span></span>|  
|<span data-ttu-id="2e26a-126">Text</span><span class="sxs-lookup"><span data-stu-id="2e26a-126">Text</span></span>|<xref:System.Xml.XmlText>|<span data-ttu-id="2e26a-127">屬於項目或屬性的文字。</span><span class="sxs-lookup"><span data-stu-id="2e26a-127">Text belonging to an element or attribute.</span></span>|  
|<span data-ttu-id="2e26a-128">CDATASection</span><span class="sxs-lookup"><span data-stu-id="2e26a-128">CDATASection</span></span>|<xref:System.Xml.XmlCDataSection>|<span data-ttu-id="2e26a-129">表示 CDATA。</span><span class="sxs-lookup"><span data-stu-id="2e26a-129">Represents CDATA.</span></span>|  
|<span data-ttu-id="2e26a-130">實體</span><span class="sxs-lookup"><span data-stu-id="2e26a-130">Entity</span></span>|<xref:System.Xml.XmlEntity>|<span data-ttu-id="2e26a-131">表示 XML 文件中的 `<!ENTITY…>` 宣告，可能來自內部文件類型定義 (DTD) 子集，或來自外部 DTD 和參數實體。</span><span class="sxs-lookup"><span data-stu-id="2e26a-131">Represents the `<!ENTITY…>` declarations in an XML document, either from an internal document type definition (DTD) subset or from external DTDs and parameter entities.</span></span>|  
|<span data-ttu-id="2e26a-132">Notation</span><span class="sxs-lookup"><span data-stu-id="2e26a-132">Notation</span></span>|<xref:System.Xml.XmlNotation>|<span data-ttu-id="2e26a-133">表示 DTD 中宣告的標記法。</span><span class="sxs-lookup"><span data-stu-id="2e26a-133">Represents a notation declared in the DTD.</span></span>|  
  
 <span data-ttu-id="2e26a-134">即使屬性 (*attr*) 會列在 W3C DOM 層級 1 1.2 節 < Fundamental Interfaces > 的節點，其會被視為任何項目節點的子系。</span><span class="sxs-lookup"><span data-stu-id="2e26a-134">Even though an attribute (*attr*) is listed in the W3C DOM Level 1 section 1.2 Fundamental Interfaces as a node, it is not considered a child of any element node.</span></span>  
  
 <span data-ttu-id="2e26a-135">下表顯示 w3c 未定義的其他節點型別，但在可供使用，做為 Microsoft.NET Framework 物件模型中**XmlNodeType**列舉型別。</span><span class="sxs-lookup"><span data-stu-id="2e26a-135">The following table shows additional node types not defined by the W3C, however they are available for use in the Microsoft .NET Framework object model as **XmlNodeType** enumerations.</span></span> <span data-ttu-id="2e26a-136">因此，這些節點型別沒有相符的 DOM 節點型別資料行。</span><span class="sxs-lookup"><span data-stu-id="2e26a-136">Therefore, there is no matching DOM node type column for these node types.</span></span>  
  
|<span data-ttu-id="2e26a-137">節點類型</span><span class="sxs-lookup"><span data-stu-id="2e26a-137">Node type</span></span>|<span data-ttu-id="2e26a-138">描述</span><span class="sxs-lookup"><span data-stu-id="2e26a-138">Description</span></span>|  
|---------------|-----------------|  
|<xref:System.Xml.XmlDeclaration>|<span data-ttu-id="2e26a-139">表示宣告節點 `<?xml version="1.0"…>`。</span><span class="sxs-lookup"><span data-stu-id="2e26a-139">Represents the declaration node `<?xml version="1.0"…>`.</span></span>|  
|<xref:System.Xml.XmlSignificantWhitespace>|<span data-ttu-id="2e26a-140">表示顯著的空白字元，這是混合內容中的空白字元。</span><span class="sxs-lookup"><span data-stu-id="2e26a-140">Represents significant white space, which is white space in mixed content.</span></span>|  
|<xref:System.Xml.XmlWhitespace>|<span data-ttu-id="2e26a-141">表示項目內容中的泛空白字元。</span><span class="sxs-lookup"><span data-stu-id="2e26a-141">Represents the white space in the content of an element.</span></span>|  
|<span data-ttu-id="2e26a-142">EndElement</span><span class="sxs-lookup"><span data-stu-id="2e26a-142">EndElement</span></span>|<span data-ttu-id="2e26a-143">傳回當**XmlReader**取得項目的結尾。</span><span class="sxs-lookup"><span data-stu-id="2e26a-143">Returned when **XmlReader** gets to the end of an element.</span></span><br /><br /> <span data-ttu-id="2e26a-144">範例 XML:  **\< /項目 >**</span><span class="sxs-lookup"><span data-stu-id="2e26a-144">Example XML: **\</item>**</span></span><br /><br /> <span data-ttu-id="2e26a-145">如需詳細資訊，請參閱<xref:System.Xml.XmlNodeType>。</span><span class="sxs-lookup"><span data-stu-id="2e26a-145">For more information, see <xref:System.Xml.XmlNodeType>.</span></span>|  
|<span data-ttu-id="2e26a-146">EndEntity</span><span class="sxs-lookup"><span data-stu-id="2e26a-146">EndEntity</span></span>|<span data-ttu-id="2e26a-147">傳回當**XmlReader**到達實體取代，由於呼叫的結尾<xref:System.Xml.XmlReader.ResolveEntity%2A>。</span><span class="sxs-lookup"><span data-stu-id="2e26a-147">Returned when **XmlReader** gets to the end of the entity replacement as a result of a call to <xref:System.Xml.XmlReader.ResolveEntity%2A>.</span></span> <span data-ttu-id="2e26a-148">如需詳細資訊，請參閱<xref:System.Xml.XmlNodeType>。</span><span class="sxs-lookup"><span data-stu-id="2e26a-148">For more information, see <xref:System.Xml.XmlNodeType>.</span></span>|  
  
 <span data-ttu-id="2e26a-149">若要檢視來讀取 XML，並使用的案例建構來列印節點和其內容的相關資訊的節點型別上的程式碼範例，請參閱<xref:System.Xml.XmlSignificantWhitespace.NodeType%2A>。</span><span class="sxs-lookup"><span data-stu-id="2e26a-149">To view a code example that reads in XML and uses a case construct on the node types to print information about the node and its contents, see <xref:System.Xml.XmlSignificantWhitespace.NodeType%2A>.</span></span>  
  
 <span data-ttu-id="2e26a-150">節點型別和其對等的物件名稱的物件階層架構資訊，請參閱[XML 文件物件模型 (DOM) 階層](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md)。</span><span class="sxs-lookup"><span data-stu-id="2e26a-150">For more information on the object hierarchy of the node types and their equivalent object name, see [XML Document Object Model (DOM) Hierarchy](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md).</span></span> <span data-ttu-id="2e26a-151">如需在節點樹狀目錄中建立之物件的詳細資訊，請參閱[將物件階層架構對應至 XML 資料](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)。</span><span class="sxs-lookup"><span data-stu-id="2e26a-151">For more information on the objects created in the node tree, see [Mapping the Object Hierarchy to XML Data](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e26a-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2e26a-152">See Also</span></span>  
 [<span data-ttu-id="2e26a-153">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="2e26a-153">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
