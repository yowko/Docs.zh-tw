---
title: 關聯類型
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: 17465dbec3f5e2896cf755a1f8585734388f54ca
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69948293"
---
# <a name="association-type"></a><span data-ttu-id="416a4-102">關聯類型</span><span class="sxs-lookup"><span data-stu-id="416a4-102">association type</span></span>
<span data-ttu-id="416a4-103">*關聯類型*(也稱為關聯) 是用來描述實體資料模型 (EDM) 中關聯性的基本建立區塊。</span><span class="sxs-lookup"><span data-stu-id="416a4-103">An *association type* (also called an association) is the fundamental building block for describing relationships in the Entity Data Model (EDM).</span></span> <span data-ttu-id="416a4-104">在概念模型中, 「關聯」 (association) 代表兩個[實體類型](../../../../docs/framework/data/adonet/entity-type.md)( `Customer`例如`Order`和) 之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="416a4-104">In a conceptual model, an association represents a relationship between two [entity types](../../../../docs/framework/data/adonet/entity-type.md) (such as `Customer` and `Order`).</span></span> <span data-ttu-id="416a4-105">在應用程式中，關聯的執行個體代表特定的關聯 (例如 `Customer` 執行個體和 `Order` 執行個體之間的關聯)。</span><span class="sxs-lookup"><span data-stu-id="416a4-105">In an application, an instance of an association represents a specific association (such as an association between an instance of `Customer` and an instance of `Order`).</span></span> <span data-ttu-id="416a4-106">關聯實例會以邏輯方式分組在[關聯集](../../../../docs/framework/data/adonet/association-set.md)內。</span><span class="sxs-lookup"><span data-stu-id="416a4-106">Association instances are logically grouped in an [association set](../../../../docs/framework/data/adonet/association-set.md).</span></span>  
  
 <span data-ttu-id="416a4-107">關聯定義包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="416a4-107">An association definition contains the following information:</span></span>  
  
- <span data-ttu-id="416a4-108">唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="416a4-108">A unique name.</span></span> <span data-ttu-id="416a4-109">(必要項)</span><span class="sxs-lookup"><span data-stu-id="416a4-109">(Required)</span></span>  
  
- <span data-ttu-id="416a4-110">兩個[關聯結束](../../../../docs/framework/data/adonet/association-end.md), 關係中的每個實體類型各一個。</span><span class="sxs-lookup"><span data-stu-id="416a4-110">Two [association ends](../../../../docs/framework/data/adonet/association-end.md), one for each entity type in the relationship.</span></span> <span data-ttu-id="416a4-111">(必要項)</span><span class="sxs-lookup"><span data-stu-id="416a4-111">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="416a4-112">一個關聯 (association) 不能代表兩個實體型別以上的關聯性 (relationship)。</span><span class="sxs-lookup"><span data-stu-id="416a4-112">An association cannot represent a relationship among more than two entity types.</span></span> <span data-ttu-id="416a4-113">不過，關聯可以為其每一個關聯 End 指定同樣的實體型別，以定義自我關聯性。</span><span class="sxs-lookup"><span data-stu-id="416a4-113">An association can, however, define a self-relationship by specifying the same entity type for each of its association ends.</span></span>  
  
- <span data-ttu-id="416a4-114">[參考完整性條件約束](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)。</span><span class="sxs-lookup"><span data-stu-id="416a4-114">A [referential integrity constraint](../../../../docs/framework/data/adonet/referential-integrity-constraint.md).</span></span> <span data-ttu-id="416a4-115">(選擇項)</span><span class="sxs-lookup"><span data-stu-id="416a4-115">(Optional)</span></span>  
  
 <span data-ttu-id="416a4-116">每個關聯 end 都必須指定一個[關聯 end 多重性](../../../../docs/framework/data/adonet/association-end-multiplicity.md), 以指出可以在關聯一端的實體類型實例數目。</span><span class="sxs-lookup"><span data-stu-id="416a4-116">Each association end must specify an [association end multiplicity](../../../../docs/framework/data/adonet/association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="416a4-117">關聯 end 多重性的值可以是一 (1)、零或一 (0 ..1), 或多個 (\*)。</span><span class="sxs-lookup"><span data-stu-id="416a4-117">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (\*).</span></span> <span data-ttu-id="416a4-118">關聯的一端的實體型別實例可以透過[導覽屬性](../../../../docs/framework/data/adonet/navigation-property.md)或外鍵來存取 (如果它們是在實體型別上公開)。</span><span class="sxs-lookup"><span data-stu-id="416a4-118">Entity type instances at one end of an association can be accessed through [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) or foreign keys if they are exposed on an entity type.</span></span> <span data-ttu-id="416a4-119">如需詳細資訊, [請參閱實體資料模型:外鍵](../../../../docs/framework/data/adonet/foreign-key-property.md)。</span><span class="sxs-lookup"><span data-stu-id="416a4-119">For more information, see [Entity Data Model: Foreign Keys](../../../../docs/framework/data/adonet/foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="416a4-120">範例</span><span class="sxs-lookup"><span data-stu-id="416a4-120">Example</span></span>  
 <span data-ttu-id="416a4-121">下圖顯示包含兩個關聯 (`PublishedBy` 和 `WrittenBy`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="416a4-121">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="416a4-122">`PublishedBy` 關聯的關聯 End 為 `Book` 和 `Publisher` 實體類型。</span><span class="sxs-lookup"><span data-stu-id="416a4-122">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="416a4-123">`Publisher` End 的多重性是一 (1), 而`Book` end 的多重性是 many (\*), 表示發行者發行許多書籍, 而書籍是由一個發行者發行。</span><span class="sxs-lookup"><span data-stu-id="416a4-123">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 ![具有三個實體類型的範例模型](./media/association-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="416a4-125">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言 ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 的特定領域語言 (DSL) 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="416a4-125">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="416a4-126">下列 CSDL 定義上圖中的 `PublishedBy` 關聯。</span><span class="sxs-lookup"><span data-stu-id="416a4-126">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="416a4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="416a4-127">See also</span></span>

- [<span data-ttu-id="416a4-128">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="416a4-128">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="416a4-129">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="416a4-129">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
