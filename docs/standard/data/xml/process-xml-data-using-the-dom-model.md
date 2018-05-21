---
title: 使用 DOM 模型處理 XML 資料
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 56b6e9c7-ed82-4a65-a647-7be32c83bcc8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c59d84148aae35794410f5f7237cef96ab5b7560
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="process-xml-data-using-the-dom-model"></a><span data-ttu-id="38ff0-102">使用 DOM 模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="38ff0-102">Process XML Data Using the DOM Model</span></span>
<span data-ttu-id="38ff0-103">XML 文件物件模型 (DOM) 會將 XML 資料視為一組標準物件來處理，可用於處理記憶體中的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="38ff0-103">The XML Document Object Model (DOM) treats XML data as a standard set of objects and is used to process XML data in memory.</span></span> <span data-ttu-id="38ff0-104">`System.Xml` 命名空間提供以程式設計方式表示的 XML 文件、片段、節點或節點集。</span><span class="sxs-lookup"><span data-stu-id="38ff0-104">The `System.Xml` namespace provides a programmatic representation of XML documents, fragments, nodes, or node-sets.</span></span> <span data-ttu-id="38ff0-105">它是以全球資訊網協會 (W3C) DOM 層級 1 核心及 DOM 層級 2 核心建議事項為基礎。</span><span class="sxs-lookup"><span data-stu-id="38ff0-105">It is based on the World Wide Web Consortium (W3C) DOM Level 1 Core and the DOM Level 2 Core recommendations.</span></span>  
  
 <span data-ttu-id="38ff0-106"><xref:System.Xml.XmlDocument> 類別表示 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="38ff0-106">The <xref:System.Xml.XmlDocument> class represents an XML document.</span></span> <span data-ttu-id="38ff0-107">它包含可用於擷取及建立所有其他 XML 物件的成員。</span><span class="sxs-lookup"><span data-stu-id="38ff0-107">It includes members for retrieving and creating all other XML objects.</span></span> <span data-ttu-id="38ff0-108">透過 <xref:System.Xml.XmlDocument> 及其相關類別，您可以建構 XML 文件、載入並存取資料、修改資料，以及儲存變更。</span><span class="sxs-lookup"><span data-stu-id="38ff0-108">Using the <xref:System.Xml.XmlDocument>, and its related classes, you can construct XML documents, load and access data, modify data, and save changes.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="38ff0-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="38ff0-109">In This Section</span></span>  
  
-   [<span data-ttu-id="38ff0-110">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="38ff0-110">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)  
  
-   [<span data-ttu-id="38ff0-111">XML 節點的類型</span><span class="sxs-lookup"><span data-stu-id="38ff0-111">Types of XML Nodes</span></span>](../../../../docs/standard/data/xml/types-of-xml-nodes.md)  
  
-   [<span data-ttu-id="38ff0-112">XML 文件物件模型 (DOM) 階層</span><span class="sxs-lookup"><span data-stu-id="38ff0-112">XML Document Object Model (DOM) Hierarchy</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md)  
  
-   [<span data-ttu-id="38ff0-113">將物件階層對應至 XML 資料</span><span class="sxs-lookup"><span data-stu-id="38ff0-113">Mapping the Object Hierarchy to XML Data</span></span>](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md)  
  
-   [<span data-ttu-id="38ff0-114">建立 XML 文件</span><span class="sxs-lookup"><span data-stu-id="38ff0-114">XML Document Creation</span></span>](../../../../docs/standard/data/xml/xml-document-creation.md)  
  
-   [<span data-ttu-id="38ff0-115">將 XML 文件讀取到 DOM</span><span class="sxs-lookup"><span data-stu-id="38ff0-115">Reading an XML Document into the DOM</span></span>](../../../../docs/standard/data/xml/reading-an-xml-document-into-the-dom.md)  
  
-   [<span data-ttu-id="38ff0-116">將節點插入 XML 文件</span><span class="sxs-lookup"><span data-stu-id="38ff0-116">Inserting Nodes into an XML Document</span></span>](../../../../docs/standard/data/xml/inserting-nodes-into-an-xml-document.md)  
  
-   [<span data-ttu-id="38ff0-117">從 XML 文件移除節點、內容和值</span><span class="sxs-lookup"><span data-stu-id="38ff0-117">Removing Nodes, Content, and Values from an XML Document</span></span>](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md)  
  
-   [<span data-ttu-id="38ff0-118">修改 XML 文件中的節點、內容和值</span><span class="sxs-lookup"><span data-stu-id="38ff0-118">Modifying Nodes, Content, and Values in an XML Document</span></span>](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md)  
  
-   [<span data-ttu-id="38ff0-119">驗證 DOM 中的 XML 文件</span><span class="sxs-lookup"><span data-stu-id="38ff0-119">Validating an XML Document in the DOM</span></span>](../../../../docs/standard/data/xml/validating-an-xml-document-in-the-dom.md)  
  
-   [<span data-ttu-id="38ff0-120">儲存與寫入文件</span><span class="sxs-lookup"><span data-stu-id="38ff0-120">Saving and Writing a Document</span></span>](../../../../docs/standard/data/xml/saving-and-writing-a-document.md)  
  
-   [<span data-ttu-id="38ff0-121">使用 XPath 導覽選取節點</span><span class="sxs-lookup"><span data-stu-id="38ff0-121">Select Nodes Using XPath Navigation</span></span>](../../../../docs/standard/data/xml/select-nodes-using-xpath-navigation.md)  
  
-   [<span data-ttu-id="38ff0-122">解析外部資源</span><span class="sxs-lookup"><span data-stu-id="38ff0-122">Resolving External Resources</span></span>](../../../../docs/standard/data/xml/resolving-external-resources.md)  
  
-   [<span data-ttu-id="38ff0-123">使用 XmlNameTable 進行物件比較</span><span class="sxs-lookup"><span data-stu-id="38ff0-123">Object Comparison Using XmlNameTable</span></span>](../../../../docs/standard/data/xml/object-comparison-using-xmlnametable.md)  
  
-   [<span data-ttu-id="38ff0-124">NamedNodeMap 和 NodeList 中的節點集合</span><span class="sxs-lookup"><span data-stu-id="38ff0-124">Node Collections in NamedNodeMaps and NodeLists</span></span>](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md)  
  
-   [<span data-ttu-id="38ff0-125">動態更新 NodeList 和 NamedNodeMap</span><span class="sxs-lookup"><span data-stu-id="38ff0-125">Dynamic Updates to NodeLists and NamedNodeMaps</span></span>](../../../../docs/standard/data/xml/dynamic-updates-to-nodelists-and-namednodemaps.md)  
  
-   [<span data-ttu-id="38ff0-126">DOM 中的命名空間支援</span><span class="sxs-lookup"><span data-stu-id="38ff0-126">Namespace Support in the DOM</span></span>](../../../../docs/standard/data/xml/namespace-support-in-the-dom.md)  
  
-   [<span data-ttu-id="38ff0-127">使用 XmlNodeChangedEventArgs 之 XML 文件中的事件處理</span><span class="sxs-lookup"><span data-stu-id="38ff0-127">Event Handling in an XML Document Using the XmlNodeChangedEventArgs</span></span>](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)  
  
-   [<span data-ttu-id="38ff0-128">擴充 DOM</span><span class="sxs-lookup"><span data-stu-id="38ff0-128">Extending the DOM</span></span>](../../../../docs/standard/data/xml/extending-the-dom.md)  
  
## <a name="related-sections"></a><span data-ttu-id="38ff0-129">相關章節</span><span class="sxs-lookup"><span data-stu-id="38ff0-129">Related Sections</span></span>  
 [<span data-ttu-id="38ff0-130">使用 XPath 資料模型處理 XML 資料</span><span class="sxs-lookup"><span data-stu-id="38ff0-130">Process XML Data Using the XPath Data Model</span></span>](../../../../docs/standard/data/xml/process-xml-data-using-the-xpath-data-model.md)  
 <span data-ttu-id="38ff0-131">討論如何使用 <xref:System.Xml.XPath.XPathNavigator> 類別進行 XML 處理。</span><span class="sxs-lookup"><span data-stu-id="38ff0-131">Discusses XML processing using the <xref:System.Xml.XPath.XPathNavigator> class.</span></span>
