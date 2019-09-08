---
title: Entity Container - 實體容器
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: 95740fb9d8b357a4fa160af6fdafb139711283cd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795251"
---
# <a name="entity-container"></a><span data-ttu-id="5e839-102">Entity Container - 實體容器</span><span class="sxs-lookup"><span data-stu-id="5e839-102">entity container</span></span>
<span data-ttu-id="5e839-103">*實體容器*是[實體集](entity-set.md)、[關聯集](association-set.md)和函式匯[入](model-declared-function.md)的邏輯群組。</span><span class="sxs-lookup"><span data-stu-id="5e839-103">An *entity container* is a logical grouping of [entity sets](entity-set.md), [association sets](association-set.md), and [function imports](model-declared-function.md).</span></span>  
  
 <span data-ttu-id="5e839-104">在概念模型中定義的實體容器，下列必須為 true：</span><span class="sxs-lookup"><span data-stu-id="5e839-104">The following must be true of an entity container defined in a conceptual model:</span></span>  
  
- <span data-ttu-id="5e839-105">每個概念模型中至少必須定義一個實體容器。</span><span class="sxs-lookup"><span data-stu-id="5e839-105">At least one entity container must be defined in each conceptual model.</span></span>  
  
- <span data-ttu-id="5e839-106">每個概念模型中的實體容器必須要有一個唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="5e839-106">The entity container must have a unique name within each conceptual model.</span></span>  
  
 <span data-ttu-id="5e839-107">實體容器可以定義使用一或多個命名空間中定義之實體類型或關聯的實體集或關聯集。</span><span class="sxs-lookup"><span data-stu-id="5e839-107">An entity container can define entity sets or association sets that use entity types or associations defined in one or more namespaces.</span></span> <span data-ttu-id="5e839-108">如需詳細資訊， [請參閱實體資料模型：命名](entity-data-model-namespaces.md)空間。</span><span class="sxs-lookup"><span data-stu-id="5e839-108">For more information, see [Entity Data Model: Namespaces](entity-data-model-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5e839-109">範例</span><span class="sxs-lookup"><span data-stu-id="5e839-109">Example</span></span>  
 <span data-ttu-id="5e839-110">下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="5e839-110">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  <span data-ttu-id="5e839-111">如需詳細資訊，請參閱下一個範例。</span><span class="sxs-lookup"><span data-stu-id="5e839-111">See the next example for more information.</span></span>  
  
 ![具有三個實體類型的範例模型](./media/entity-container/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="5e839-113">雖然圖表並未提供實體容器資訊，但概念模型必須定義實體容器。</span><span class="sxs-lookup"><span data-stu-id="5e839-113">Although the diagram does not convey entity container information, the conceptual model must define an entity container.</span></span> <span data-ttu-id="5e839-114">[ADO.NET Entity Framework](./ef/index.md)會使用稱為概念結構定義語言（[CSDL](./ef/language-reference/csdl-specification.md)）的 DSL 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="5e839-114">The [ADO.NET Entity Framework](./ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="5e839-115">下列 CSDL 會定義上圖所示之概念模型的實體容器。</span><span class="sxs-lookup"><span data-stu-id="5e839-115">The following CSDL defines an entity container for the conceptual model shown in the diagram above.</span></span> <span data-ttu-id="5e839-116">請注意，實體容器的名稱是在 XML 屬性中定義的。</span><span class="sxs-lookup"><span data-stu-id="5e839-116">Note that the entity container name is defined in an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="5e839-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5e839-117">See also</span></span>

- [<span data-ttu-id="5e839-118">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="5e839-118">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="5e839-119">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="5e839-119">Entity Data Model</span></span>](entity-data-model.md)
