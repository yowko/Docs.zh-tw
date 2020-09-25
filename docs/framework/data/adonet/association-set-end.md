---
title: 關聯集 End
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: bd104ffb46cbd02a886ce87822ddc37159961174
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198791"
---
# <a name="association-set-end"></a><span data-ttu-id="f7d7c-102">關聯集 End</span><span class="sxs-lookup"><span data-stu-id="f7d7c-102">association set end</span></span>

<span data-ttu-id="f7d7c-103">*關聯集 end*可識別[關聯集](association-set.md)結尾的[實體類型](entity-type.md)和[實體集](entity-set.md)。</span><span class="sxs-lookup"><span data-stu-id="f7d7c-103">An *association set end* identifies the [entity type](entity-type.md) and the [entity set](entity-set.md) at the end of an [association set](association-set.md).</span></span> <span data-ttu-id="f7d7c-104">關聯集 End 會定義為關聯集的部分。一個關聯集必須擁有兩個關聯集 End。</span><span class="sxs-lookup"><span data-stu-id="f7d7c-104">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="f7d7c-105">關聯集 End 定義包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="f7d7c-105">An association set end definition contains the following information:</span></span>  
  
- <span data-ttu-id="f7d7c-106">關聯集中相關的其中一個屬性類型。</span><span class="sxs-lookup"><span data-stu-id="f7d7c-106">One of the entity types involved in the association set.</span></span> <span data-ttu-id="f7d7c-107">(必要)</span><span class="sxs-lookup"><span data-stu-id="f7d7c-107">(Required)</span></span>  
  
- <span data-ttu-id="f7d7c-108">關聯集中相關實體類型的實體集。</span><span class="sxs-lookup"><span data-stu-id="f7d7c-108">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="f7d7c-109">(必要)</span><span class="sxs-lookup"><span data-stu-id="f7d7c-109">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7d7c-110">範例</span><span class="sxs-lookup"><span data-stu-id="f7d7c-110">Example</span></span>  

 <span data-ttu-id="f7d7c-111">下圖顯示包含兩個關聯 (`WrittenBy` 和 `PublishedBy`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="f7d7c-111">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 ![包含三種實體類型的範例模型](./media/association-set-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="f7d7c-113">下圖顯示以前述概念模型為基礎的一個關聯集 (`PublishedBy`) 和兩個實體集 (`Books` 和 `Publishers`)。</span><span class="sxs-lookup"><span data-stu-id="f7d7c-113">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="f7d7c-114">關聯集 End 為 `Books` 和 `Publishers` 實體集。</span><span class="sxs-lookup"><span data-stu-id="f7d7c-114">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="f7d7c-115">`Books`實體集中的 Bi 代表 `Book` 執行時間的實體型別實例。</span><span class="sxs-lookup"><span data-stu-id="f7d7c-115">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="f7d7c-116">同樣地，Pj `Publisher` 則代表 `Publishers` 實體集中的實例。</span><span class="sxs-lookup"><span data-stu-id="f7d7c-116">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="f7d7c-117">BiPj 代表 `PublishedBy` 關聯集中關聯的實例 `PublishedBy` 。</span><span class="sxs-lookup"><span data-stu-id="f7d7c-117">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![顯示集合範例的螢幕擷取畫面。](./media/association-set-end/sets-example-association.gif)  
  
 <span data-ttu-id="f7d7c-119">[ADO.NET Entity Framework](./ef/index.md)會使用名為概念結構定義語言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 來定義概念模型的 DSL。</span><span class="sxs-lookup"><span data-stu-id="f7d7c-119">The [ADO.NET Entity Framework](./ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="f7d7c-120">下列 CSDL 定義上圖所示之實體實體容器，每個關聯具有一個關聯集。</span><span class="sxs-lookup"><span data-stu-id="f7d7c-120">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="f7d7c-121">請注意，關聯集 End 會定義為每個關聯集定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="f7d7c-121">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="f7d7c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7d7c-122">See also</span></span>

- [<span data-ttu-id="f7d7c-123">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="f7d7c-123">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="f7d7c-124">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="f7d7c-124">Entity Data Model</span></span>](entity-data-model.md)
