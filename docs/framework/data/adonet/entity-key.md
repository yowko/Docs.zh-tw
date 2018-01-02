---
title: "實體索引鍵"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d447a6d-fa7a-4db0-8e7a-fd45e385fca0
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 184a55c3c5479f1999057e55dcc761a250051e5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="entity-key"></a><span data-ttu-id="ceded-102">實體索引鍵</span><span class="sxs-lookup"><span data-stu-id="ceded-102">entity key</span></span>
<span data-ttu-id="ceded-103">*實體索引鍵*是[屬性](../../../../docs/framework/data/adonet/property.md)或一組屬性的[實體類型](../../../../docs/framework/data/adonet/entity-type.md)，用於判斷識別。</span><span class="sxs-lookup"><span data-stu-id="ceded-103">An *entity key* is a [property](../../../../docs/framework/data/adonet/property.md) or a set of properties of an [entity type](../../../../docs/framework/data/adonet/entity-type.md) that are used to determine identity.</span></span> <span data-ttu-id="ceded-104">構成實體索引鍵的屬性是在設計階段選取的。</span><span class="sxs-lookup"><span data-stu-id="ceded-104">The properties that make up an entity key are chosen at design time.</span></span> <span data-ttu-id="ceded-105">實體索引鍵屬性的值必須唯一識別實體類型執行個體中的[實體集](../../../../docs/framework/data/adonet/entity-set.md)在執行階段。</span><span class="sxs-lookup"><span data-stu-id="ceded-105">The values of entity key properties must uniquely identify an entity type instance within an [entity set](../../../../docs/framework/data/adonet/entity-set.md) at run time.</span></span> <span data-ttu-id="ceded-106">您應選取構成實體索引鍵的屬性，以保證執行個體在實體集中的唯一性。</span><span class="sxs-lookup"><span data-stu-id="ceded-106">The properties that make up an entity key should be chosen to guarantee uniqueness of instances in an entity set.</span></span>  
  
 <span data-ttu-id="ceded-107">屬性集若要成為實體索引鍵，需求如下：</span><span class="sxs-lookup"><span data-stu-id="ceded-107">The following are the requirements for a set of properties to be an entity key:</span></span>  
  
-   <span data-ttu-id="ceded-108">實體集中的任兩個實體索引鍵均不可完全相同。</span><span class="sxs-lookup"><span data-stu-id="ceded-108">No two entity keys within an entity set can be identical.</span></span> <span data-ttu-id="ceded-109">也就是說，以實體集中任兩個實體來說，構成索引鍵的所有屬性的值不可完全相同。</span><span class="sxs-lookup"><span data-stu-id="ceded-109">That is, for any two entities within an entity set, the values for all of the properties that constitute a key cannot be the same.</span></span> <span data-ttu-id="ceded-110">不過，構成實體索引鍵的部分 (非所有) 值可以相同。</span><span class="sxs-lookup"><span data-stu-id="ceded-110">However, some (but not all) of the values that make up an entity key can be the same.</span></span>  
  
-   <span data-ttu-id="ceded-111">實體索引鍵必須包含一組不可為 null、 不可變的[基本型別屬性](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="ceded-111">An entity key must consist of a set of non-nullable, immutable, [primitive type properties](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md).</span></span>  
  
-   <span data-ttu-id="ceded-112">構成指定實體類型之實體索引鍵的屬性不可變更。</span><span class="sxs-lookup"><span data-stu-id="ceded-112">The properties that make up an entity key for a given entity type cannot change.</span></span> <span data-ttu-id="ceded-113">您不能允許指定的實體類型擁有多個可能的實體索引鍵，不支援 Surrogate 索引鍵。</span><span class="sxs-lookup"><span data-stu-id="ceded-113">You cannot allow more than one possible entity key for a given entity type; surrogate keys are not supported.</span></span>  
  
-   <span data-ttu-id="ceded-114">實體與繼承階層相關時，根實體必須包含構成實體索引鍵的所有屬性，而且必須在根實體類型定義該實體索引鍵。</span><span class="sxs-lookup"><span data-stu-id="ceded-114">When an entity is involved in an inheritance hierarchy, the root entity must contain all the properties that make up the entity key, and the entity key must be defined on the root entity type.</span></span> <span data-ttu-id="ceded-115">如需詳細資訊，請參閱[實體資料模型： 繼承](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)。</span><span class="sxs-lookup"><span data-stu-id="ceded-115">For more information, see [Entity Data Model: Inheritance](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ceded-116">範例</span><span class="sxs-lookup"><span data-stu-id="ceded-116">Example</span></span>  
 <span data-ttu-id="ceded-117">下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="ceded-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="ceded-118">構成實體索引鍵之每個實體類型的屬性皆加註「(索引鍵)」。</span><span class="sxs-lookup"><span data-stu-id="ceded-118">The properties of each entity type that make up its entity key are denoted with "(Key)".</span></span> <span data-ttu-id="ceded-119">請注意，`Author` 實體類型的實體索引鍵包含兩個屬性：`Name` 和 `Address`。</span><span class="sxs-lookup"><span data-stu-id="ceded-119">Note that the `Author` entity type has an entity key that consists of two properties, `Name` and `Address`.</span></span>  
  
 <span data-ttu-id="ceded-120">![範例模型](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="ceded-120">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="ceded-121">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="ceded-121">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="ceded-122">下列的 CSDL 會定義上圖顯示的 `Book` 實體類型。</span><span class="sxs-lookup"><span data-stu-id="ceded-122">The CSDL below defines the `Book` entity type shown in the diagram above.</span></span> <span data-ttu-id="ceded-123">請注意，實體索引鍵是藉由參考實體類型的 `ISBN` 屬性而定義的。</span><span class="sxs-lookup"><span data-stu-id="ceded-123">Note that the entity key is defined by referencing the `ISBN` property of the entity type.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
 <span data-ttu-id="ceded-124">`ISBN` 屬性是實體索引鍵的最佳選擇，因為國際標準書號 (International Standard Book Number，ISBN) 可明確識別一本書。</span><span class="sxs-lookup"><span data-stu-id="ceded-124">The `ISBN` property is a good choice for the entity key because an International Standard Book Number (ISBN) uniquely identifies a book.</span></span>  
  
 <span data-ttu-id="ceded-125">下列的 CSDL 會定義上圖顯示的 `Author` 實體類型。</span><span class="sxs-lookup"><span data-stu-id="ceded-125">The CSDL below defines the `Author` entity type shown in the diagram above.</span></span> <span data-ttu-id="ceded-126">請注意，實體索引鍵包含兩個屬性：`Name` 和 `Address`。</span><span class="sxs-lookup"><span data-stu-id="ceded-126">Note that the entity key consists of two properties, `Name` and `Address`.</span></span>  
  
 [!code-xml[EDM_Example_Model#CompositeKeyExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#compositekeyexample)]  
  
 <span data-ttu-id="ceded-127">針對實體索引鍵使用 `Name` 和 `Address` 是合理的選擇，因為相同名稱的兩位作者不太可能住在同一個地址。</span><span class="sxs-lookup"><span data-stu-id="ceded-127">Using `Name` and `Address` for the entity key is a reasonable choice, because two authors of the same name are unlikely to live at the same address.</span></span> <span data-ttu-id="ceded-128">不過，針對實體索引鍵所做的這個選擇不能絕對保證實體集中的唯一實體索引鍵。</span><span class="sxs-lookup"><span data-stu-id="ceded-128">However, this choice for an entity key does not absolutely guarantee unique entity keys in an entity set.</span></span> <span data-ttu-id="ceded-129">在這種情況下，建議您加入一個屬性，例如 `AuthorId`，可用於明確識別作者。</span><span class="sxs-lookup"><span data-stu-id="ceded-129">Adding a property, such as `AuthorId`, that could be used to uniquely identify an author would be recommended in this case.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceded-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="ceded-130">See Also</span></span>  
 [<span data-ttu-id="ceded-131">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="ceded-131">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="ceded-132">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="ceded-132">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
