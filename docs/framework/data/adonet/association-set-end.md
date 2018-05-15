---
title: 關聯集 End
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: 440cfdee4581496d9d131fbaf3d1796f38931532
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="association-set-end"></a><span data-ttu-id="09116-102">關聯集 End</span><span class="sxs-lookup"><span data-stu-id="09116-102">association set end</span></span>
<span data-ttu-id="09116-103">*關聯集 end*識別[實體類型](../../../../docs/framework/data/adonet/entity-type.md)和[實體集](../../../../docs/framework/data/adonet/entity-set.md)結尾[關聯集](../../../../docs/framework/data/adonet/association-set.md)。</span><span class="sxs-lookup"><span data-stu-id="09116-103">An *association set end* identifies the [entity type](../../../../docs/framework/data/adonet/entity-type.md) and the [entity set](../../../../docs/framework/data/adonet/entity-set.md) at the end of an [association set](../../../../docs/framework/data/adonet/association-set.md).</span></span> <span data-ttu-id="09116-104">關聯集 End 會定義為關聯集的部分。一個關聯集必須擁有兩個關聯集 End。</span><span class="sxs-lookup"><span data-stu-id="09116-104">Association set ends are defined as part of an association set; an association set must have exactly two association set ends.</span></span>  
  
 <span data-ttu-id="09116-105">關聯集 End 定義包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="09116-105">An association set end definition contains the following information:</span></span>  
  
-   <span data-ttu-id="09116-106">關聯集中相關的其中一個屬性類型。</span><span class="sxs-lookup"><span data-stu-id="09116-106">One of the entity types involved in the association set.</span></span> <span data-ttu-id="09116-107">(必要項)</span><span class="sxs-lookup"><span data-stu-id="09116-107">(Required)</span></span>  
  
-   <span data-ttu-id="09116-108">關聯集中相關實體類型的實體集。</span><span class="sxs-lookup"><span data-stu-id="09116-108">The entity set for the entity type involved in the association set.</span></span> <span data-ttu-id="09116-109">(必要項)</span><span class="sxs-lookup"><span data-stu-id="09116-109">(Required)</span></span>  
  
## <a name="example"></a><span data-ttu-id="09116-110">範例</span><span class="sxs-lookup"><span data-stu-id="09116-110">Example</span></span>  
 <span data-ttu-id="09116-111">下圖顯示包含兩個關聯 (`WrittenBy` 和 `PublishedBy`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="09116-111">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span>  
  
 <span data-ttu-id="09116-112">![範例模型](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="09116-112">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="09116-113">下圖顯示以前述概念模型為基礎的一個關聯集 (`PublishedBy`) 和兩個實體集 (`Books` 和 `Publishers`)。</span><span class="sxs-lookup"><span data-stu-id="09116-113">The following diagram shows an association set (`PublishedBy`) and two entity sets (`Books` and `Publishers`) based on the conceptual model shown above.</span></span> <span data-ttu-id="09116-114">關聯集 End 為 `Books` 和 `Publishers` 實體集。</span><span class="sxs-lookup"><span data-stu-id="09116-114">The association set ends are the `Books` and `Publishers` entity sets.</span></span> <span data-ttu-id="09116-115">在 bi`Books`實體集表示的執行個體`Book`在執行階段的實體類型。</span><span class="sxs-lookup"><span data-stu-id="09116-115">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="09116-116">同樣地，Pj 代表`Publisher`執行個體中`Publishers`實體集。</span><span class="sxs-lookup"><span data-stu-id="09116-116">Similarly, Pj represents a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="09116-117">BiPj 表示的執行個體`PublishedBy`中的關聯`PublishedBy`關聯集。</span><span class="sxs-lookup"><span data-stu-id="09116-117">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 <span data-ttu-id="09116-118">![設定範例](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span><span class="sxs-lookup"><span data-stu-id="09116-118">![Sets Example](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span></span>  
  
 <span data-ttu-id="09116-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的 DSL ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="09116-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="09116-120">下列 CSDL 定義上圖所示之實體實體容器，每個關聯具有一個關聯集。</span><span class="sxs-lookup"><span data-stu-id="09116-120">The following CSDL defines an entity container with one association set for each association in the diagram above.</span></span> <span data-ttu-id="09116-121">請注意，關聯集 End 會定義為每個關聯集定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="09116-121">Note that association set ends are defined as part of each association set definition.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="09116-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09116-122">See Also</span></span>  
 [<span data-ttu-id="09116-123">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="09116-123">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="09116-124">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="09116-124">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
