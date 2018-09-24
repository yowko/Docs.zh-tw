---
title: XML 文件物件模型 (DOM) 階層架構
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef2b5b200f95cdfac9b08a33c328c1dfb797e59e
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/21/2018
ms.locfileid: "46537770"
---
# <a name="xml-document-object-model-dom-hierarchy"></a><span data-ttu-id="01a31-102">XML 文件物件模型 (DOM) 階層架構</span><span class="sxs-lookup"><span data-stu-id="01a31-102">XML Document Object Model (DOM) Hierarchy</span></span>
<span data-ttu-id="01a31-103">下圖顯示 XML 文件物件模型 (DOM) 的類別階層架構，括弧中有全球資訊網協會 (W3C) 名稱和相關的類別名稱。</span><span class="sxs-lookup"><span data-stu-id="01a31-103">The following illustration shows the class hierarchy for the XML Document Object Model (DOM), with the World Wide Web Consortium (W3C) name in parenthesis along with the class name where it is relevant.</span></span>  
  
 <span data-ttu-id="01a31-104">![XML 文件物件模型 &#40;DOM&#41; 階層](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="01a31-104">![XML Document Object Model &#40;DOM&#41; hierarchy](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")</span></span>  
<span data-ttu-id="01a31-105">XML 文件物件模型 (DOM) 階層</span><span class="sxs-lookup"><span data-stu-id="01a31-105">XML Document Object Model (DOM) hierarchy</span></span>  
  
 <span data-ttu-id="01a31-106">下列類別不是繼承自 **XmlNode**：</span><span class="sxs-lookup"><span data-stu-id="01a31-106">The following classes do not inherit from the **XmlNode**:</span></span>  
  
-   <span data-ttu-id="01a31-107">**XmlImplementation**</span><span class="sxs-lookup"><span data-stu-id="01a31-107">**XmlImplementation**</span></span>  
  
-   <span data-ttu-id="01a31-108">**XmlNamedNodeMap**</span><span class="sxs-lookup"><span data-stu-id="01a31-108">**XmlNamedNodeMap**</span></span>  
  
-   <span data-ttu-id="01a31-109">**XmlNodeList**</span><span class="sxs-lookup"><span data-stu-id="01a31-109">**XmlNodeList**</span></span>  
  
-   <span data-ttu-id="01a31-110">**XmlNodeChangedEventArgs**</span><span class="sxs-lookup"><span data-stu-id="01a31-110">**XmlNodeChangedEventArgs**</span></span>  
  
 <span data-ttu-id="01a31-111">**XmlImplementation** 類別是用來建立 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="01a31-111">The **XmlImplementation** class is used to create an XML document.</span></span> <span data-ttu-id="01a31-112">如需詳細資訊，請參閱 [XML 文件建立](../../../../docs/standard/data/xml/xml-document-creation.md)。</span><span class="sxs-lookup"><span data-stu-id="01a31-112">For more information, see [XML Document Creation](../../../../docs/standard/data/xml/xml-document-creation.md).</span></span>  
  
 <span data-ttu-id="01a31-113">**XmlNamedNodeMap** 類別處理未排序的節點組。</span><span class="sxs-lookup"><span data-stu-id="01a31-113">The **XmlNamedNodeMap** class handles an unordered set of nodes.</span></span> <span data-ttu-id="01a31-114">如需詳細資訊，請參閱[根據名稱或索引擷取的未排序節點](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md)。</span><span class="sxs-lookup"><span data-stu-id="01a31-114">For more information, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span>  
  
 <span data-ttu-id="01a31-115">**XmlNodeList** 類別處理已排序的節點清單。</span><span class="sxs-lookup"><span data-stu-id="01a31-115">The **XmlNodeList** class handles an ordered list of nodes.</span></span> <span data-ttu-id="01a31-116">如需詳細資訊，請參閱[根據索引擷取的已排序節點](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md)。</span><span class="sxs-lookup"><span data-stu-id="01a31-116">For more information, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
 <span data-ttu-id="01a31-117">**XmlNodeChangedEventArgs** 類別處理在 **XmlDocument** 上註冊的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="01a31-117">The **XmlNodeChangedEventArgs** class handles event handlers registered on the **XmlDocument**.</span></span> <span data-ttu-id="01a31-118">如需詳細資訊，請參閱[使用 XmlNodeChangedEventArgs 之 XML 文件中的事件處理](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md)。</span><span class="sxs-lookup"><span data-stu-id="01a31-118">For more information, see [Event Handling in an XML Document using the XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).</span></span>  
  
 <span data-ttu-id="01a31-119">**XmlLinkedNode** 類別繼承自 **XmlNode**。</span><span class="sxs-lookup"><span data-stu-id="01a31-119">The **XmlLinkedNode** class inherits from **XmlNode**.</span></span> <span data-ttu-id="01a31-120">其目的在於覆寫 **XmlNode** 的兩個方法：**PreviousSibling** 與 **NextSibling** 方法。</span><span class="sxs-lookup"><span data-stu-id="01a31-120">Its purpose is to override two methods from **XmlNode**: the **PreviousSibling** and **NextSibling** methods.</span></span> <span data-ttu-id="01a31-121">這些覆寫的方法會由擁有之前同層級和之後同層級的類別 **XmlCharacterData**、**XmlDeclaration**、**XmlDocumentType**、**XmlElement**、**XmlEntityReference** 和 **XmlProcessingInstruction** 繼承和使用。</span><span class="sxs-lookup"><span data-stu-id="01a31-121">These overridden methods are then inherited and used by **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, and **XmlProcessingInstruction**, which are classes that have previous and next siblings.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01a31-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01a31-122">See also</span></span>

- [<span data-ttu-id="01a31-123">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="01a31-123">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
