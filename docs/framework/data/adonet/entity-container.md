---
title: Entity Container - 實體容器
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: ed2123629c61b179e07e86effa0c39d9a3222b62
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="entity-container"></a><span data-ttu-id="44dd5-102">Entity Container - 實體容器</span><span class="sxs-lookup"><span data-stu-id="44dd5-102">entity container</span></span>
<span data-ttu-id="44dd5-103">*實體容器*是邏輯群組[實體集](../../../../docs/framework/data/adonet/entity-set.md)，[關聯集](../../../../docs/framework/data/adonet/association-set.md)，和[函式匯入](../../../../docs/framework/data/adonet/model-declared-function.md)。</span><span class="sxs-lookup"><span data-stu-id="44dd5-103">An *entity container* is a logical grouping of [entity sets](../../../../docs/framework/data/adonet/entity-set.md), [association sets](../../../../docs/framework/data/adonet/association-set.md), and [function imports](../../../../docs/framework/data/adonet/model-declared-function.md).</span></span>  
  
 <span data-ttu-id="44dd5-104">在概念模型中定義的實體容器，下列必須為 true：</span><span class="sxs-lookup"><span data-stu-id="44dd5-104">The following must be true of an entity container defined in a conceptual model:</span></span>  
  
-   <span data-ttu-id="44dd5-105">每個概念模型中至少必須定義一個實體容器。</span><span class="sxs-lookup"><span data-stu-id="44dd5-105">At least one entity container must be defined in each conceptual model.</span></span>  
  
-   <span data-ttu-id="44dd5-106">每個概念模型中的實體容器必須要有一個唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="44dd5-106">The entity container must have a unique name within each conceptual model.</span></span>  
  
 <span data-ttu-id="44dd5-107">實體容器可以定義使用一或多個命名空間中定義之實體類型或關聯的實體集或關聯集。</span><span class="sxs-lookup"><span data-stu-id="44dd5-107">An entity container can define entity sets or association sets that use entity types or associations defined in one or more namespaces.</span></span> <span data-ttu-id="44dd5-108">如需詳細資訊，請參閱[實體資料模型： 命名空間](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md)。</span><span class="sxs-lookup"><span data-stu-id="44dd5-108">For more information, see [Entity Data Model: Namespaces](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="44dd5-109">範例</span><span class="sxs-lookup"><span data-stu-id="44dd5-109">Example</span></span>  
 <span data-ttu-id="44dd5-110">下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="44dd5-110">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  <span data-ttu-id="44dd5-111">如需詳細資訊，請參閱下一個範例。</span><span class="sxs-lookup"><span data-stu-id="44dd5-111">See the next example for more information.</span></span>  
  
 <span data-ttu-id="44dd5-112">![範例模型](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="44dd5-112">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="44dd5-113">雖然圖表並未提供實體容器資訊，但概念模型必須定義實體容器。</span><span class="sxs-lookup"><span data-stu-id="44dd5-113">Although the diagram does not convey entity container information, the conceptual model must define an entity container.</span></span> <span data-ttu-id="44dd5-114">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的 DSL ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="44dd5-114">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="44dd5-115">下列 CSDL 會定義上圖所示之概念模型的實體容器。</span><span class="sxs-lookup"><span data-stu-id="44dd5-115">The following CSDL defines an entity container for the conceptual model shown in the diagram above.</span></span> <span data-ttu-id="44dd5-116">請注意，實體容器的名稱是在 XML 屬性中定義的。</span><span class="sxs-lookup"><span data-stu-id="44dd5-116">Note that the entity container name is defined in an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="44dd5-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44dd5-117">See Also</span></span>  
 [<span data-ttu-id="44dd5-118">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="44dd5-118">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="44dd5-119">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="44dd5-119">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
