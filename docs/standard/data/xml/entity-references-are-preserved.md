---
title: "保留實體參照"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 000a6cae-5972-40d6-bd6c-a9b7d9649b3c
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: f5a867d1301355f4c9a77654556229274f96d00c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="b4f75-102">保留實體參照</span><span class="sxs-lookup"><span data-stu-id="b4f75-102">Entity References are Preserved</span></span>
<span data-ttu-id="b4f75-103">當實體參照並未擴充但保留下來時，若 XML 文件物件模型 (DOM) 遇到實體參照，就會建置 **XmlEntityReference** 節點。</span><span class="sxs-lookup"><span data-stu-id="b4f75-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="b4f75-104">使用下列 XML，</span><span class="sxs-lookup"><span data-stu-id="b4f75-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="b4f75-105">當 DOM 遇到 `&publisher;` 參照時，就會建置 **XmlEntityReference** 節點。</span><span class="sxs-lookup"><span data-stu-id="b4f75-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="b4f75-106">**XmlEntityReference** 包含從實體宣告中的內容所複製的子節點。</span><span class="sxs-lookup"><span data-stu-id="b4f75-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="b4f75-107">先前的程式碼範例包含實體宣告中的文字，因此 **XmlText** 節點會建立為實體參照節點的子節點。</span><span class="sxs-lookup"><span data-stu-id="b4f75-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="b4f75-108">![保留實體參考的樹狀結構](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="b4f75-108">![Tree structure for preserved entity references](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="b4f75-109">保留之實體參照的樹狀</span><span class="sxs-lookup"><span data-stu-id="b4f75-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="b4f75-110">**XmlEntityReference** 的子節點是在遇到實體宣告時，由 **XmlEntity** 節點建立的所有子節點的複本。</span><span class="sxs-lookup"><span data-stu-id="b4f75-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4f75-111">從 **XmlEntity** 複製的節點不一定就是曾置於實體參照節點下的複本。</span><span class="sxs-lookup"><span data-stu-id="b4f75-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="b4f75-112">在實體參照節點的範圍中可能有命名空間，這會影響子節點的最後組態。</span><span class="sxs-lookup"><span data-stu-id="b4f75-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="b4f75-113">根據預設，會保留 `&abc;` 之類的一般實體，且一律會建立 **XmlEntityReference** 節點。</span><span class="sxs-lookup"><span data-stu-id="b4f75-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4f75-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="b4f75-114">See Also</span></span>  
 [<span data-ttu-id="b4f75-115">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="b4f75-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
