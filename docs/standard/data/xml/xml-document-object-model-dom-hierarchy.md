---
title: "XML 文件物件模型 (DOM) 階層架構"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4d2ffaa994ce3c9b02ed0937967845be1b803f6d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="dc489-102">XML 文件物件模型 (DOM) 階層架構</span><span class="sxs-lookup"><span data-stu-id="dc489-102">XML Document Object Model (DOM) Hierarchy</span></span>
<span data-ttu-id="dc489-103">下圖顯示 XML 文件物件模型 (DOM) 的類別階層架構，括弧中有全球資訊網協會 (W3C) 名稱和相關的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="dc489-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="dc489-104">![XML 文件物件模型 &#40;DOM&#41; 階層](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="dc489-104">![XML Document Object Model &#40;DOM&#41; hierarchy](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="dc489-105">XML 文件物件模型 (DOM) 階層</span><span class="sxs-lookup"><span data-stu-id="dc489-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="dc489-106">下列類別不是繼承自 **XmlNode**：</span><span class="sxs-lookup"><span data-stu-id="dc489-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
-   <span data-ttu-id="dc489-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="dc489-107">**XmlImplementation**</span></span>  
  
-   <span data-ttu-id="dc489-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="dc489-108">**XmlNamedNodeMap**</span></span>  
  
-   <span data-ttu-id="dc489-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="dc489-109">**XmlNodeList**</span></span>  
  
-   <span data-ttu-id="dc489-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="dc489-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="dc489-111">**XmlImplementation** 類別是用來建立 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="dc489-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="dc489-112">如需詳細資訊，請參閱 [XML 文件建立](../../../../docs/standard/data/xml/xml-document-creation.md)。</span><span class="sxs-lookup"><span data-stu-id="dc489-112">For more information, see [XML Document Creation](../../../../docs/standard/data/xml/xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="dc489-113">**XmlNamedNodeMap** 類別處理未排序的節點組。</span><span class="sxs-lookup"><span data-stu-id="dc489-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="dc489-114">如需詳細資訊，請參閱[根據名稱或索引擷取的未排序節點](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md)。</span><span class="sxs-lookup"><span data-stu-id="dc489-114">For more information, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="dc489-115">**XmlNodeList** 類別處理已排序的節點清單。</span><span class="sxs-lookup"><span data-stu-id="dc489-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="dc489-116">如需詳細資訊，請參閱[根據索引擷取的已排序節點](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md)。</span><span class="sxs-lookup"><span data-stu-id="dc489-116">For more information, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="dc489-117">**XmlNodeChangedEventArgs** 類別處理在 **XmlDocument** 上註冊的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="dc489-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="dc489-118">如需詳細資訊，請參閱[使用 XmlNodeChangedEventArgs 之 XML 文件中的事件處理](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)。</span><span class="sxs-lookup"><span data-stu-id="dc489-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="dc489-119">**XmlLinkedNode** 類別繼承自 **XmlNode**。</span><span class="sxs-lookup"><span data-stu-id="dc489-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="dc489-120">其目的在於覆寫 **XmlNode** 的兩個方法：**PreviousSibling** 與 **NextSibling** 方法。</span><span class="sxs-lookup"><span data-stu-id="dc489-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="dc489-121">這些覆寫的方法會由擁有之前同層級和之後同層級的類別 **XmlCharacterData**、**XmlDeclaration**、**XmlDocumentType**、**XmlElement**、**XmlEntityReference** 和 **XmlProcessingInstruction** 繼承和使用。</span><span class="sxs-lookup"><span data-stu-id="dc489-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc489-122">請參閱</span><span class="sxs-lookup"><span data-stu-id="dc489-122">See Also</span></span>  
 [<span data-ttu-id="dc489-123">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="dc489-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
