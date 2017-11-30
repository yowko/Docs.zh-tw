---
title: "NamedNodeMap 和 NodeList 中的節點集合"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 025954b8-7aa8-47c5-a1c1-f81064fb4d65
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7eeed46782eb6c55af23559035fb8b6bcb14301f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="node-collections-in-namednodemaps-and-nodelists"></a><span data-ttu-id="611f1-102">NamedNodeMap 和 NodeList 中的節點集合</span><span class="sxs-lookup"><span data-stu-id="611f1-102">Node Collections in NamedNodeMaps and NodeLists</span></span>
<span data-ttu-id="611f1-103">您可以擷取一組節點，並且將它放入已排序或未排序的集合。</span><span class="sxs-lookup"><span data-stu-id="611f1-103">You can retrieve a set of nodes and put it in an ordered or unordered collection.</span></span> <span data-ttu-id="611f1-104">全球資訊網協會 (W3C) 將一組置於未排序之集合的節點稱為 NamedNodeMap；您可以根據這種集合型別的名稱或索引來擷取資料。</span><span class="sxs-lookup"><span data-stu-id="611f1-104">When putting a set of nodes into an unordered collection, the set is called a NamedNodeMap by the World Wide Web Consortium (W3C); you can retrieve the data by name or index in this type of collection.</span></span> <span data-ttu-id="611f1-105">而 W3C 將一組置於已排序之集合的節點稱為 NodeList，可以使用從零開始的索引擷取資料。</span><span class="sxs-lookup"><span data-stu-id="611f1-105">Putting a set of nodes in an ordered collection is called a NodeList by the W3C, and the data can be retrieved by a zero-based index.</span></span> <span data-ttu-id="611f1-106">NamedNodeMaps 和 NodeLists 是由 W3C 說明。</span><span class="sxs-lookup"><span data-stu-id="611f1-106">NamedNodeMaps and NodeLists are described by the W3C.</span></span> <span data-ttu-id="611f1-107">Microsoft.NET Framework 中，NamedNodeMap 的實作是**XmlNamedNodeMap**，藉由 NodeList 和**XmlNodeList**。</span><span class="sxs-lookup"><span data-stu-id="611f1-107">The implementations in the Microsoft .NET Framework for the NamedNodeMap is the **XmlNamedNodeMap**, and the NodeList is implemented by the **XmlNodeList**.</span></span>  
  
 <span data-ttu-id="611f1-108">未排序之集合的資訊，請參閱[根據名稱或索引擷取的未排序節點](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md)。</span><span class="sxs-lookup"><span data-stu-id="611f1-108">For information on the unordered collection, see [Unordered Node Retrieval by Name or Index](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).</span></span> <span data-ttu-id="611f1-109">已排序之集合的資訊，請參閱[依索引擷取的已排序節點](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md)。</span><span class="sxs-lookup"><span data-stu-id="611f1-109">For information on the ordered collection, see [Ordered Node Retrieval by Index](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="611f1-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="611f1-110">See Also</span></span>  
 [<span data-ttu-id="611f1-111">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="611f1-111">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
