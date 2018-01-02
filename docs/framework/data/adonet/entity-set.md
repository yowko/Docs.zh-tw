---
title: "實體集"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 9d0cef0247c36f3c7819e37f8144635ebdbf610b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="entity-set"></a><span data-ttu-id="aacf4-102">實體集</span><span class="sxs-lookup"><span data-stu-id="aacf4-102">entity set</span></span>
<span data-ttu-id="aacf4-103">*實體集*是邏輯容器的執行個體[實體類型](../../../../docs/framework/data/adonet/entity-type.md)和衍生自該實體類型的任何類型的執行個體。</span><span class="sxs-lookup"><span data-stu-id="aacf4-103">An *entity set* is a logical container for instances of an [entity type](../../../../docs/framework/data/adonet/entity-type.md) and instances of any type derived from that entity type.</span></span> <span data-ttu-id="aacf4-104">(如需衍生型別資訊，請參閱[實體資料模型： 繼承](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)。)實體類型和實體集之間的關聯性，類似關聯式資料表中資料行和資料列的關聯性：實體類型和資料行一樣描述資料結構，而實體集則和資料表一樣包含指定結構的執行個體。</span><span class="sxs-lookup"><span data-stu-id="aacf4-104">(For information about derived types, see [Entity Data Model: Inheritance](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).) The relationship between an entity type and an entity set is analogous to the relationship between a row and a table in a relational database: Like a row, an entity type describes data structure, and, like a table, an entity set contains instances of a given structure.</span></span> <span data-ttu-id="aacf4-105">實體集不是資料模型建構，也就是說，它不會描述資料結構。</span><span class="sxs-lookup"><span data-stu-id="aacf4-105">An entity set is not a data modeling construct; it does not describe the structure of data.</span></span> <span data-ttu-id="aacf4-106">反之，實體集會提供建構，讓裝載或儲存環境 (例如 Common Language Runtime 或 SQL Server 資料庫) 群組實體類型執行個體，以將其對應至資料存放區。</span><span class="sxs-lookup"><span data-stu-id="aacf4-106">Instead, an entity set provides a construct for a hosting or storage environment (such as the common language runtime or a SQL Server database) to group entity type instances so that they can be mapped to a data store.</span></span>  
  
 <span data-ttu-id="aacf4-107">實體集內定義[實體容器](../../../../docs/framework/data/adonet/entity-container.md)，這是實體集的邏輯群組和[關聯集](../../../../docs/framework/data/adonet/association-set.md)。</span><span class="sxs-lookup"><span data-stu-id="aacf4-107">An entity set is defined within an [entity container](../../../../docs/framework/data/adonet/entity-container.md), which is a logical grouping of entity sets and [association sets](../../../../docs/framework/data/adonet/association-set.md).</span></span>  
  
 <span data-ttu-id="aacf4-108">實體類型執行個體若要存在於實體集中，下列條件必須為 true：</span><span class="sxs-lookup"><span data-stu-id="aacf4-108">For an entity type instance to exist in an entity set, the following must be true:</span></span>  
  
-   <span data-ttu-id="aacf4-109">執行個體的類型必須與該實體集所依據的實體類型相同，或者執行個體的型別為該實體類型的子類型。</span><span class="sxs-lookup"><span data-stu-id="aacf4-109">The type of the instance is either the same as the entity type on which the entity set is based, or the type of the instance is a subtype of the entity type.</span></span>  
  
-   <span data-ttu-id="aacf4-110">[實體索引鍵](../../../../docs/framework/data/adonet/entity-key.md)的執行個體中是唯一的實體集。</span><span class="sxs-lookup"><span data-stu-id="aacf4-110">The [entity key](../../../../docs/framework/data/adonet/entity-key.md) for the instance is unique within the entity set.</span></span>  
  
-   <span data-ttu-id="aacf4-111">執行個體不存在於任何其他實體集中。</span><span class="sxs-lookup"><span data-stu-id="aacf4-111">The instance does not exist in any other entity set.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="aacf4-112">您可以使用相同的實體類型定義多個實體集，但指定實體類型的執行個體只能存在於一個實體集中。</span><span class="sxs-lookup"><span data-stu-id="aacf4-112">Multiple entity sets can be defined using the same entity type, but an instance of a given entity type can only exist in one entity set.</span></span>  
  
 <span data-ttu-id="aacf4-113">您不需定義概念模型中每個實體類型的實體集。</span><span class="sxs-lookup"><span data-stu-id="aacf4-113">You do not have to define an entity set for each entity type in a conceptual model.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aacf4-114">範例</span><span class="sxs-lookup"><span data-stu-id="aacf4-114">Example</span></span>  
 <span data-ttu-id="aacf4-115">下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="aacf4-115">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 <span data-ttu-id="aacf4-116">![範例模型](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="aacf4-116">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="aacf4-117">下圖顯示以前述概念模型為基礎的兩個實體集 (`Books` 和 `Publishers`)，以及一個關聯集 `PublishedBy`)。</span><span class="sxs-lookup"><span data-stu-id="aacf4-117">The following diagram shows two entity sets (`Books` and `Publishers`) and an association set (`PublishedBy`) based on the conceptual model shown above.</span></span> <span data-ttu-id="aacf4-118">在 bi`Books`實體集表示的執行個體`Book`在執行階段的實體類型。</span><span class="sxs-lookup"><span data-stu-id="aacf4-118">Bi in the `Books` entity set represents an instance of the `Book` entity type at run time.</span></span> <span data-ttu-id="aacf4-119">同樣地，Pj 代表`Publisher`執行個體中`Publishers`實體集。</span><span class="sxs-lookup"><span data-stu-id="aacf4-119">Similarly, Pj represent a `Publisher` instance in the `Publishers` entity set.</span></span> <span data-ttu-id="aacf4-120">BiPj 表示的執行個體`PublishedBy`中的關聯`PublishedBy`關聯集。</span><span class="sxs-lookup"><span data-stu-id="aacf4-120">BiPj represents an instance of the `PublishedBy` association in the `PublishedBy` association set.</span></span>  
  
 <span data-ttu-id="aacf4-121">![設定範例](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span><span class="sxs-lookup"><span data-stu-id="aacf4-121">![Sets Example](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")</span></span>  
  
 <span data-ttu-id="aacf4-122">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="aacf4-122">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="aacf4-123">下列 CSDL 定義實體容器，上述概念模型中的每個實體類型皆具有一個實體集。</span><span class="sxs-lookup"><span data-stu-id="aacf4-123">The following CSDL defines an entity container with one entity set for each entity type in the conceptual model shown above.</span></span> <span data-ttu-id="aacf4-124">請注意，每個實體集名稱和實體類型都是使用 XML 屬性定義的。</span><span class="sxs-lookup"><span data-stu-id="aacf4-124">Note that the name and entity type for each entity set are defined using XML attributes.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 <span data-ttu-id="aacf4-125">您可以定義每個類型的多重實體集 (MEST)。</span><span class="sxs-lookup"><span data-stu-id="aacf4-125">It is possible to define multiple entity sets per type (MEST).</span></span> <span data-ttu-id="aacf4-126">下列 CSDL 所定義的實體容體具有兩個 `Book` 實體類型的實體集：</span><span class="sxs-lookup"><span data-stu-id="aacf4-126">The following CSDL defines an entity container with two entity sets for the `Book` entity type:</span></span>  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## <a name="see-also"></a><span data-ttu-id="aacf4-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="aacf4-127">See Also</span></span>  
 [<span data-ttu-id="aacf4-128">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="aacf4-128">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="aacf4-129">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="aacf4-129">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
