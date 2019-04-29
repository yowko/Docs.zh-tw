---
title: 關聯集 End
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 7b6c646592c1878ea30396d98b4976dc8fa0be12
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769574"
---
# <a name="association-set-end"></a><span data-ttu-id="afb58-102">關聯集 End</span><span class="sxs-lookup"><span data-stu-id="afb58-102">association set end</span></span>
<span data-ttu-id="afb58-103">*關聯集 end*識別[實體型別](../../../../docs/framework/data/adonet/entity-type.md)並[實體集](../../../../docs/framework/data/adonet/entity-set.md)結尾[關聯集](../../../../docs/framework/data/adonet/association-set.md)。</span><span class="sxs-lookup"><span data-stu-id="afb58-103">An *association set end* identifies the [entity type](../../../../docs/framework/data/adonet/entity-type.md) and the [entity set](../../../../docs/framework/data/adonet/entity-set.md) at the end of an [association set](../../../../docs/framework/data/adonet/association-set.md).</span></span> <span data-ttu-id="afb58-104">關聯集 End 會定義為關聯集的部分。一個關聯集必須擁有兩個關聯集 End。</span><span class="sxs-lookup"><span data-stu-id="afb58-104">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="afb58-105">關聯集 End 定義包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="afb58-105">An association set end definition contains the following information:</span></span>  
  
- <span data-ttu-id="afb58-106">關聯集中相關的其中一個屬性類型。</span><span class="sxs-lookup"><span data-stu-id="afb58-106">One of the entity types involved in the association set.</span></span> <span data-ttu-id="afb58-107">(必要項)</span><span class="sxs-lookup"><span data-stu-id="afb58-107">(Required)</span></span>  
  
- <span data-ttu-id="afb58-108">關聯集中相關實體類型的實體集。</span><span class="sxs-lookup"><span data-stu-id="afb58-108">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="afb58-109">(必要項)</span><span class="sxs-lookup"><span data-stu-id="afb58-109">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="afb58-110">範例</span><span class="sxs-lookup"><span data-stu-id="afb58-110">Example</span></span>  
 <span data-ttu-id="afb58-111">下圖顯示包含兩個關聯 (`WrittenBy` 和 `PublishedBy`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="afb58-111">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 ![具有三種實體類型的範例模型](./media/association-set-end/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="afb58-113">下圖顯示以前述概念模型為基礎的一個關聯集 (`PublishedBy`) 和兩個實體集 (`Books` 和 `Publishers`)。</span><span class="sxs-lookup"><span data-stu-id="afb58-113">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="afb58-114">關聯集 End 為 `Books` 和 `Publishers` 實體集。</span><span class="sxs-lookup"><span data-stu-id="afb58-114">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="afb58-115">在 bi`Books`實體集代表的執行個體`Book`在執行階段的實體類型。</span><span class="sxs-lookup"><span data-stu-id="afb58-115">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="afb58-116">同樣地，Pj 代表`Publisher`執行個體中`Publishers`實體集。</span><span class="sxs-lookup"><span data-stu-id="afb58-116">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="afb58-117">BiPj 表示的執行個體`PublishedBy`中的關聯`PublishedBy`關聯集。</span><span class="sxs-lookup"><span data-stu-id="afb58-117">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![如果螢幕擷取畫面顯示設定範例。](./media/association-set-end/sets-example-association.gif)  
  
 <span data-ttu-id="afb58-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的 DSL ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="afb58-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="afb58-120">下列 CSDL 定義上圖所示之實體實體容器，每個關聯具有一個關聯集。</span><span class="sxs-lookup"><span data-stu-id="afb58-120">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="afb58-121">請注意，關聯集 End 會定義為每個關聯集定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="afb58-121">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="afb58-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="afb58-122">See also</span></span>

- [<span data-ttu-id="afb58-123">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="afb58-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="afb58-124">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="afb58-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
