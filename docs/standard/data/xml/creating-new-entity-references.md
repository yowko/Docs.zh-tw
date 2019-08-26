---
title: 建立新實體參考
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: a42f81b3-0403-4e34-b346-7d2129804e54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d8d4e9e1e2dfd9882504c935912bcf235608485
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965901"
---
# <a name="creating-new-entity-references"></a><span data-ttu-id="71216-102">建立新實體參考</span><span class="sxs-lookup"><span data-stu-id="71216-102">Creating New Entity References</span></span>
<span data-ttu-id="71216-103">**CreateEntityReference** 方法建立新 **XmlEntityReference** 節點。</span><span class="sxs-lookup"><span data-stu-id="71216-103">The **CreateEntityReference** method creates a new **XmlEntityReference** node.</span></span> <span data-ttu-id="71216-104">XML 文件物件模型 (DOM) 會查看所要參考的實體名稱是否已進行宣告。</span><span class="sxs-lookup"><span data-stu-id="71216-104">The XML Document Object Model (DOM) looks to see if the entity name being referenced has already been declared.</span></span> <span data-ttu-id="71216-105">如果是，**XmlEntityReference** 節點的子節點會從實體宣告節點複製。</span><span class="sxs-lookup"><span data-stu-id="71216-105">If it has, the child nodes of **XmlEntityReference** node are copied from the entity declaration node.</span></span> <span data-ttu-id="71216-106">如果沒有符合的實體宣告，會將空白文字節點當成實體參考節點的唯一子代附加上去。</span><span class="sxs-lookup"><span data-stu-id="71216-106">If there is no entity declaration that matches, an empty text node is attached as the only child of the entity reference node.</span></span> <span data-ttu-id="71216-107">因為 **XmlEntityReference** 節點的子節點是其他節點的複本，因此這些子節點是唯讀的而且無法修改。</span><span class="sxs-lookup"><span data-stu-id="71216-107">Because the child nodes of the **XmlEntityReference** node are copies of other nodes, these child nodes are read-only and cannot be modified.</span></span>  
  
 <span data-ttu-id="71216-108">複製節點時，在實體參考的範圍可能有命名空間。</span><span class="sxs-lookup"><span data-stu-id="71216-108">When the nodes are copied, there may be a namespace in scope at the point of the entity reference.</span></span> <span data-ttu-id="71216-109">這個命名空間影響任何產生的項目或屬性節點的組態。</span><span class="sxs-lookup"><span data-stu-id="71216-109">This namespace affects the configuration of any element or attribute nodes generated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="71216-110">只有在您將 **EntityReference** 節點插入文件時，DOM 才會將子節點加入 **EntityReference**。</span><span class="sxs-lookup"><span data-stu-id="71216-110">The DOM adds child nodes to the **EntityReference** only when you insert the **EntityReference** node to the document.</span></span> <span data-ttu-id="71216-111">新建的 **EntityReference** 節點沒有子節點。</span><span class="sxs-lookup"><span data-stu-id="71216-111">Newly created **EntityReference** nodes have no child nodes.</span></span>  
  
 <span data-ttu-id="71216-112">雖然 **XmlDataDocument** 是 **XmlDocument** 的衍生類別，但是 **XmlDataDocument** 卻不能建立實體參考。</span><span class="sxs-lookup"><span data-stu-id="71216-112">Even though the **XmlDataDocument** is a derived class of the **XmlDocument**, the **XmlDataDocument** does not support the creation of entity references.</span></span> <span data-ttu-id="71216-113">這是因為 **EntityReference** 子系是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="71216-113">This is because **EntityReference** children are read-only.</span></span> <span data-ttu-id="71216-114">**EntityReference** 節點的子系可以擴展一個以上的區域。</span><span class="sxs-lookup"><span data-stu-id="71216-114">The children of an **EntityReference** node can span more than one region.</span></span> <span data-ttu-id="71216-115">因此，與包含部分 **EntityReference** 的區域相關之資料列的部分也會是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="71216-115">In this case, part of a row associated with the region that contains a part of an **EntityReference** will be read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71216-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71216-116">See also</span></span>

- [<span data-ttu-id="71216-117">XML 文件物件模型 (DOM)</span><span class="sxs-lookup"><span data-stu-id="71216-117">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
