---
title: 實體集
ms.date: 03/30/2017
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
ms.openlocfilehash: 4473b74a4142bb49076068b50dc8b6f9c2c0d54a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959226"
---
# <a name="entity-set"></a><span data-ttu-id="4c702-102">實體集</span><span class="sxs-lookup"><span data-stu-id="4c702-102">entity set</span></span>
<span data-ttu-id="4c702-103">*實體集*是[實體類型](../../../../docs/framework/data/adonet/entity-type.md)實例的邏輯容器, 以及衍生自該實體類型之任何類型的實例。</span><span class="sxs-lookup"><span data-stu-id="4c702-103">An *entity set* is a logical container for instances of an [entity type](../../../../docs/framework/data/adonet/entity-type.md) and instances of any type derived from that entity type.</span></span> <span data-ttu-id="4c702-104">(如需衍生類型的詳細資訊[, 請參閱實體資料模型:繼承](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md))。實體類型和實體集之間的關聯性類似于關係資料庫中的資料列和資料表之間的關聯性:就像資料列一樣, 實體類型也會描述資料結構, 而且就像資料表一樣, 實體集會包含給定結構的實例。</span><span class="sxs-lookup"><span data-stu-id="4c702-104">(For information about derived types, see [Entity Data Model: Inheritance](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).) The relationship between an entity type and an entity set is analogous to the relationship between a row and a table in a relational database: Like a row, an entity type describes data structure, and, like a table, an entity set contains instances of a given structure.</span></span> <span data-ttu-id="4c702-105">實體集不是資料模型建構，也就是說，它不會描述資料結構。</span><span class="sxs-lookup"><span data-stu-id="4c702-105">An entity set is not a data modeling construct; it does not describe the structure of data.</span></span> <span data-ttu-id="4c702-106">反之，實體集會提供建構，讓裝載或儲存環境 (例如 Common Language Runtime 或 SQL Server 資料庫) 群組實體類型執行個體，以將其對應至資料存放區。</span><span class="sxs-lookup"><span data-stu-id="4c702-106">Instead, an entity set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group entity type instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="4c702-107">實體集會定義于[實體容器](../../../../docs/framework/data/adonet/entity-container.md)內, 這是實體集和[關聯集](../../../../docs/framework/data/adonet/association-set.md)的邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="4c702-107">An entity set is defined within an [entity container](../../../../docs/framework/data/adonet/entity-container.md), which is a logical grouping of entity sets and [association sets](../../../../docs/framework/data/adonet/association-set.md).</span></span>  
  
 <span data-ttu-id="4c702-108">實體類型執行個體若要存在於實體集中，下列條件必須為 true：</span><span class="sxs-lookup"><span data-stu-id="4c702-108">For an entity type instance to exist in an entity set, the following must be true:</span></span>  
  
- <span data-ttu-id="4c702-109">執行個體的類型必須與該實體集所依據的實體類型相同，或者執行個體的型別為該實體類型的子類型。</span><span class="sxs-lookup"><span data-stu-id="4c702-109">The type of the instance is either the same as the entity type on which the entity set is based, or the type of the instance is a subtype of the entity type.</span></span>  
  
- <span data-ttu-id="4c702-110">實例的[實體索引鍵](../../../../docs/framework/data/adonet/entity-key.md)在實體集內是唯一的。</span><span class="sxs-lookup"><span data-stu-id="4c702-110">The [entity key](../../../../docs/framework/data/adonet/entity-key.md) for the instance is unique within the entity set.</span></span>  
  
- <span data-ttu-id="4c702-111">執行個體不存在於任何其他實體集中。</span><span class="sxs-lookup"><span data-stu-id="4c702-111">The instance does not exist in any other entity set.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="4c702-112">您可以使用相同的實體類型定義多個實體集，但指定實體類型的執行個體只能存在於一個實體集中。</span><span class="sxs-lookup"><span data-stu-id="4c702-112">Multiple entity sets can be defined using the same entity type, but an instance of a given entity type can only exist in one entity set.</span></span>  
  
 <span data-ttu-id="4c702-113">您不需定義概念模型中每個實體類型的實體集。</span><span class="sxs-lookup"><span data-stu-id="4c702-113">You do not have to define an entity set for each entity type in a conceptual model.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c702-114">範例</span><span class="sxs-lookup"><span data-stu-id="4c702-114">Example</span></span>  
 <span data-ttu-id="4c702-115">下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="4c702-115">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![具有三個實體類型的範例模型](./media/entity-set/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="4c702-117">下圖顯示以前述概念模型為基礎的兩個實體集 (`Books` 和 `Publishers`)，以及一個關聯集 `PublishedBy`)。</span><span class="sxs-lookup"><span data-stu-id="4c702-117">The following diagram shows two entity sets (`Books` and `Publishers`) and an association set (`PublishedBy`) based on the conceptual model shown above.</span></span> <span data-ttu-id="4c702-118">實體集中的 Bi 表示在執行時間的`Book`實體類型實例。 `Books`</span><span class="sxs-lookup"><span data-stu-id="4c702-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="4c702-119">同樣地, Pj 代表`Publisher` `Publishers`實體集中的實例。</span><span class="sxs-lookup"><span data-stu-id="4c702-119">Similarly, Pj represent a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="4c702-120">BiPj 代表`PublishedBy` `PublishedBy`關聯集中關聯的實例。</span><span class="sxs-lookup"><span data-stu-id="4c702-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 ![顯示集合範例的螢幕擷取畫面。](./media/entity-set/sets-example-association.gif)  
  
 <span data-ttu-id="4c702-122">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言 ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 的特定領域語言 (DSL) 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="4c702-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="4c702-123">下列 CSDL 定義實體容器，上述概念模型中的每個實體類型皆具有一個實體集。</span><span class="sxs-lookup"><span data-stu-id="4c702-123">The following CSDL defines an entity container with one entity set for each entity type in the conceptual model shown above.</span></span> <span data-ttu-id="4c702-124">請注意，每個實體集名稱和實體類型都是使用 XML 屬性定義的。</span><span class="sxs-lookup"><span data-stu-id="4c702-124">Note that the name and entity type for each entity set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="4c702-125">您可以定義每個類型的多重實體集 (MEST)。</span><span class="sxs-lookup"><span data-stu-id="4c702-125">It is possible to define multiple entity sets per type (MEST).</span></span> <span data-ttu-id="4c702-126">下列 CSDL 所定義的實體容體具有兩個 `Book` 實體類型的實體集：</span><span class="sxs-lookup"><span data-stu-id="4c702-126">The following CSDL defines an entity container with two entity sets for the `Book` entity type:</span></span>  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a><span data-ttu-id="4c702-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c702-127">See also</span></span>

- [<span data-ttu-id="4c702-128">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="4c702-128">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="4c702-129">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="4c702-129">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
