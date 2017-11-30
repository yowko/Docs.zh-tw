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
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 770c714e8f5942ea733c417ae9b06f69e4acf1a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="entity-references-are-preserved"></a><span data-ttu-id="0f779-102">保留實體參照</span><span class="sxs-lookup"><span data-stu-id="0f779-102">Entity References are Preserved</span></span>
<span data-ttu-id="0f779-103">當實體參照並未擴充，但保留時，XML 文件物件模型 (DOM) 建置**XmlEntityReference**時遇到實體參照節點。</span><span class="sxs-lookup"><span data-stu-id="0f779-103">When the entity reference is not expanded, but preserved, the XML Document Object Model (DOM) builds an **XmlEntityReference** node when it encounters an entity reference.</span></span>  
  
 <span data-ttu-id="0f779-104">使用下列 XML，</span><span class="sxs-lookup"><span data-stu-id="0f779-104">Using the following XML,</span></span>  
  
```xml  
<author>Fred</author>  
<pubinfo>Published by &publisher;</pubinfo>  
```  
  
 <span data-ttu-id="0f779-105">DOM 建置**XmlEntityReference**節點時遇到`&publisher;`參考。</span><span class="sxs-lookup"><span data-stu-id="0f779-105">the DOM builds an **XmlEntityReference** node when it encounters the `&publisher;` reference.</span></span> <span data-ttu-id="0f779-106">**XmlEntityReference**包含從實體宣告中的內容複製的子節點。</span><span class="sxs-lookup"><span data-stu-id="0f779-106">The **XmlEntityReference** contains child nodes copied from the content in the entity declaration.</span></span> <span data-ttu-id="0f779-107">上述程式碼範例包含實體宣告中，因此**XmlText**節點會建立為實體參照節點的子節點。</span><span class="sxs-lookup"><span data-stu-id="0f779-107">The preceding code example contains text in the entity declaration, so an **XmlText** node is created as the child node of the entity reference node.</span></span>  
  
 <span data-ttu-id="0f779-108">![保留的實體參考的樹狀](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span><span class="sxs-lookup"><span data-stu-id="0f779-108">![Tree structure for preserved entity references](../../../../docs/standard/data/xml/media/xmlentityref-notexpanded-nodes.gif "xmlentityref_notexpanded_nodes")</span></span>  
<span data-ttu-id="0f779-109">保留之實體參照的樹狀</span><span class="sxs-lookup"><span data-stu-id="0f779-109">Tree structure for entity references that are preserved</span></span>  
  
 <span data-ttu-id="0f779-110">子節點**XmlEntityReference**是複本的所有子節點建立從**XmlEntity**節點時遇到實體宣告。</span><span class="sxs-lookup"><span data-stu-id="0f779-110">The child nodes of the **XmlEntityReference** are copies of all the child nodes created from the **XmlEntity** node when the entity declaration was encountered.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f779-111">從複製的節點**XmlEntity**不一定是曾置於實體參照節點下的完整複本。</span><span class="sxs-lookup"><span data-stu-id="0f779-111">The nodes copied from the **XmlEntity** are not always exact copies once placed under the entity reference node.</span></span> <span data-ttu-id="0f779-112">在實體參照節點的範圍中可能有命名空間，這會影響子節點的最後組態。</span><span class="sxs-lookup"><span data-stu-id="0f779-112">There can be namespaces that are in scope at the entity reference node, and that affects the final configuration of the child nodes.</span></span>  
  
 <span data-ttu-id="0f779-113">根據預設，之類的一般實體`&abc;`會保留和**XmlEntityReference**一律所建立的節點。</span><span class="sxs-lookup"><span data-stu-id="0f779-113">By default, general entities like `&abc;` are preserved and **XmlEntityReference** nodes always created.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f779-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f779-114">See Also</span></span>  
 [<span data-ttu-id="0f779-115">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="0f779-115">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
