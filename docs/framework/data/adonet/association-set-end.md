---
title: 關聯集 End
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 48ba84d46e380462405551cc2d826d84368b351a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786938"
---
# <a name="association-set-end"></a><span data-ttu-id="2d92a-102">關聯集 End</span><span class="sxs-lookup"><span data-stu-id="2d92a-102">association set end</span></span>
<span data-ttu-id="2d92a-103">*關聯集 end*會識別[關聯集](association-set.md)結尾的[實體類型](entity-type.md)和[實體集](entity-set.md)。</span><span class="sxs-lookup"><span data-stu-id="2d92a-103">An *association set end* identifies the [entity type](entity-type.md) and the [entity set](entity-set.md) at the end of an [association set](association-set.md).</span></span> <span data-ttu-id="2d92a-104">關聯集 End 會定義為關聯集的部分。一個關聯集必須擁有兩個關聯集 End。</span><span class="sxs-lookup"><span data-stu-id="2d92a-104">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="2d92a-105">關聯集 End 定義包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="2d92a-105">An association set end definition contains the following information:</span></span>  
  
- <span data-ttu-id="2d92a-106">關聯集中相關的其中一個屬性類型。</span><span class="sxs-lookup"><span data-stu-id="2d92a-106">One of the entity types involved in the association set.</span></span> <span data-ttu-id="2d92a-107">(必要項)</span><span class="sxs-lookup"><span data-stu-id="2d92a-107">(Required)</span></span>  
  
- <span data-ttu-id="2d92a-108">關聯集中相關實體類型的實體集。</span><span class="sxs-lookup"><span data-stu-id="2d92a-108">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="2d92a-109">(必要項)</span><span class="sxs-lookup"><span data-stu-id="2d92a-109">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d92a-110">範例</span><span class="sxs-lookup"><span data-stu-id="2d92a-110">Example</span></span>  
 <span data-ttu-id="2d92a-111">下圖顯示包含兩個關聯 (`WrittenBy` 和 `PublishedBy`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="2d92a-111">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 ![具有三個實體類型的範例模型](./media/association-set-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="2d92a-113">下圖顯示以前述概念模型為基礎的一個關聯集 (`PublishedBy`) 和兩個實體集 (`Books` 和 `Publishers`)。</span><span class="sxs-lookup"><span data-stu-id="2d92a-113">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="2d92a-114">關聯集 End 為 `Books` 和 `Publishers` 實體集。</span><span class="sxs-lookup"><span data-stu-id="2d92a-114">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="2d92a-115">實體集中的 Bi 表示在執行時間的`Book`實體類型實例。 `Books`</span><span class="sxs-lookup"><span data-stu-id="2d92a-115">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="2d92a-116">同樣地，Pj 代表`Publisher` `Publishers`實體集中的實例。</span><span class="sxs-lookup"><span data-stu-id="2d92a-116">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="2d92a-117">BiPj 代表`PublishedBy` `PublishedBy`關聯集中關聯的實例。</span><span class="sxs-lookup"><span data-stu-id="2d92a-117">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![顯示集合範例的螢幕擷取畫面。](./media/association-set-end/sets-example-association.gif)  
  
 <span data-ttu-id="2d92a-119">[ADO.NET Entity Framework](./ef/index.md)會使用稱為概念結構定義語言（[CSDL](./ef/language-reference/csdl-specification.md)）的 DSL 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="2d92a-119">The [ADO.NET Entity Framework](./ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="2d92a-120">下列 CSDL 定義上圖所示之實體實體容器，每個關聯具有一個關聯集。</span><span class="sxs-lookup"><span data-stu-id="2d92a-120">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="2d92a-121">請注意，關聯集 End 會定義為每個關聯集定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="2d92a-121">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="2d92a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d92a-122">See also</span></span>

- [<span data-ttu-id="2d92a-123">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="2d92a-123">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="2d92a-124">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="2d92a-124">Entity Data Model</span></span>](entity-data-model.md)
