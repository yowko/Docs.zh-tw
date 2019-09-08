---
title: 關聯類型
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: e75037223b235cf09df0bca85c6a4feb0b340174
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786888"
---
# <a name="association-type"></a><span data-ttu-id="32b71-102">關聯類型</span><span class="sxs-lookup"><span data-stu-id="32b71-102">association type</span></span>
<span data-ttu-id="32b71-103">*關聯類型*（也稱為關聯）是用來描述實體資料模型（EDM）中關聯性的基本建立區塊。</span><span class="sxs-lookup"><span data-stu-id="32b71-103">An *association type* (also called an association) is the fundamental building block for describing relationships in the Entity Data Model (EDM).</span></span> <span data-ttu-id="32b71-104">在概念模型中，「關聯」（association）代表兩個[實體類型](entity-type.md)（ `Customer`例如`Order`和）之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="32b71-104">In a conceptual model, an association represents a relationship between two [entity types](entity-type.md) (such as `Customer` and `Order`).</span></span> <span data-ttu-id="32b71-105">在應用程式中，關聯的執行個體代表特定的關聯 (例如 `Customer` 執行個體和 `Order` 執行個體之間的關聯)。</span><span class="sxs-lookup"><span data-stu-id="32b71-105">In an application, an instance of an association represents a specific association (such as an association between an instance of `Customer` and an instance of `Order`).</span></span> <span data-ttu-id="32b71-106">關聯實例會以邏輯方式分組在[關聯集](association-set.md)內。</span><span class="sxs-lookup"><span data-stu-id="32b71-106">Association instances are logically grouped in an [association set](association-set.md).</span></span>  
  
 <span data-ttu-id="32b71-107">關聯定義包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="32b71-107">An association definition contains the following information:</span></span>  
  
- <span data-ttu-id="32b71-108">唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="32b71-108">A unique name.</span></span> <span data-ttu-id="32b71-109">(必要項)</span><span class="sxs-lookup"><span data-stu-id="32b71-109">(Required)</span></span>  
  
- <span data-ttu-id="32b71-110">兩個[關聯結束](association-end.md)，關係中的每個實體類型各一個。</span><span class="sxs-lookup"><span data-stu-id="32b71-110">Two [association ends](association-end.md), one for each entity type in the relationship.</span></span> <span data-ttu-id="32b71-111">(必要項)</span><span class="sxs-lookup"><span data-stu-id="32b71-111">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="32b71-112">一個關聯 (association) 不能代表兩個實體型別以上的關聯性 (relationship)。</span><span class="sxs-lookup"><span data-stu-id="32b71-112">An association cannot represent a relationship among more than two entity types.</span></span> <span data-ttu-id="32b71-113">不過，關聯可以為其每一個關聯 End 指定同樣的實體型別，以定義自我關聯性。</span><span class="sxs-lookup"><span data-stu-id="32b71-113">An association can, however, define a self-relationship by specifying the same entity type for each of its association ends.</span></span>  
  
- <span data-ttu-id="32b71-114">[參考完整性條件約束](referential-integrity-constraint.md)。</span><span class="sxs-lookup"><span data-stu-id="32b71-114">A [referential integrity constraint](referential-integrity-constraint.md).</span></span> <span data-ttu-id="32b71-115">(選擇項)</span><span class="sxs-lookup"><span data-stu-id="32b71-115">(Optional)</span></span>  
  
 <span data-ttu-id="32b71-116">每個關聯 end 都必須指定一個[關聯 end 多重性](association-end-multiplicity.md)，以指出可以在關聯一端的實體類型實例數目。</span><span class="sxs-lookup"><span data-stu-id="32b71-116">Each association end must specify an [association end multiplicity](association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="32b71-117">關聯 end 多重性的值可以是一（1）、零或一（0 ..1），或多個（\*）。</span><span class="sxs-lookup"><span data-stu-id="32b71-117">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (\*).</span></span> <span data-ttu-id="32b71-118">關聯的一端的實體型別實例可以透過[導覽屬性](navigation-property.md)或外鍵來存取（如果它們是在實體型別上公開）。</span><span class="sxs-lookup"><span data-stu-id="32b71-118">Entity type instances at one end of an association can be accessed through [navigation properties](navigation-property.md) or foreign keys if they are exposed on an entity type.</span></span> <span data-ttu-id="32b71-119">如需詳細資訊， [請參閱實體資料模型：外鍵](foreign-key-property.md)。</span><span class="sxs-lookup"><span data-stu-id="32b71-119">For more information, see [Entity Data Model: Foreign Keys](foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="32b71-120">範例</span><span class="sxs-lookup"><span data-stu-id="32b71-120">Example</span></span>  
 <span data-ttu-id="32b71-121">下圖顯示包含兩個關聯 (`PublishedBy` 和 `WrittenBy`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="32b71-121">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="32b71-122">`PublishedBy` 關聯的關聯 End 為 `Book` 和 `Publisher` 實體類型。</span><span class="sxs-lookup"><span data-stu-id="32b71-122">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="32b71-123">`Publisher` End 的多重性是一（1），而`Book` end 的多重性是 many （\*），表示發行者發行許多書籍，而書籍是由一個發行者發行。</span><span class="sxs-lookup"><span data-stu-id="32b71-123">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 ![具有三個實體類型的範例模型](./media/association-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="32b71-125">[ADO.NET Entity Framework](./ef/index.md)會使用稱為概念結構定義語言（[CSDL](./ef/language-reference/csdl-specification.md)）的特定領域語言（DSL）來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="32b71-125">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="32b71-126">下列 CSDL 定義上圖中的 `PublishedBy` 關聯。</span><span class="sxs-lookup"><span data-stu-id="32b71-126">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="32b71-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32b71-127">See also</span></span>

- [<span data-ttu-id="32b71-128">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="32b71-128">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="32b71-129">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="32b71-129">Entity Data Model</span></span>](entity-data-model.md)
