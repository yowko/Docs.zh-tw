---
title: 關聯類型
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: 6f6eb91d4f292c7e98b8c9a1d814ed6bf71b7370
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198752"
---
# <a name="association-type"></a><span data-ttu-id="5b363-102">關聯類型</span><span class="sxs-lookup"><span data-stu-id="5b363-102">association type</span></span>

<span data-ttu-id="5b363-103">*關聯類型* (也稱為關聯) 是在實體資料模型 (EDM) 中描述關聯性的基本組建區塊。</span><span class="sxs-lookup"><span data-stu-id="5b363-103">An *association type* (also called an association) is the fundamental building block for describing relationships in the Entity Data Model (EDM).</span></span> <span data-ttu-id="5b363-104">在概念模型中，關聯代表兩個 [實體類型](entity-type.md) 之間的關聯性 (例如 `Customer` 和 `Order`) 。</span><span class="sxs-lookup"><span data-stu-id="5b363-104">In a conceptual model, an association represents a relationship between two [entity types](entity-type.md) (such as `Customer` and `Order`).</span></span> <span data-ttu-id="5b363-105">在應用程式中，關聯的執行個體代表特定的關聯 (例如 `Customer` 執行個體和 `Order` 執行個體之間的關聯)。</span><span class="sxs-lookup"><span data-stu-id="5b363-105">In an application, an instance of an association represents a specific association (such as an association between an instance of `Customer` and an instance of `Order`).</span></span> <span data-ttu-id="5b363-106">關聯實例會在邏輯上群組于 [關聯集中](association-set.md)。</span><span class="sxs-lookup"><span data-stu-id="5b363-106">Association instances are logically grouped in an [association set](association-set.md).</span></span>  
  
 <span data-ttu-id="5b363-107">關聯定義包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="5b363-107">An association definition contains the following information:</span></span>  
  
- <span data-ttu-id="5b363-108">唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="5b363-108">A unique name.</span></span> <span data-ttu-id="5b363-109">(必要)</span><span class="sxs-lookup"><span data-stu-id="5b363-109">(Required)</span></span>  
  
- <span data-ttu-id="5b363-110">兩個 [關聯會結束，關聯](association-end.md)性中的每個實體類型各一個。</span><span class="sxs-lookup"><span data-stu-id="5b363-110">Two [association ends](association-end.md), one for each entity type in the relationship.</span></span> <span data-ttu-id="5b363-111">(必要)</span><span class="sxs-lookup"><span data-stu-id="5b363-111">(Required)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="5b363-112">一個關聯 (association) 不能代表兩個實體型別以上的關聯性 (relationship)。</span><span class="sxs-lookup"><span data-stu-id="5b363-112">An association cannot represent a relationship among more than two entity types.</span></span> <span data-ttu-id="5b363-113">不過，關聯可以為其每一個關聯 End 指定同樣的實體型別，以定義自我關聯性。</span><span class="sxs-lookup"><span data-stu-id="5b363-113">An association can, however, define a self-relationship by specifying the same entity type for each of its association ends.</span></span>  
  
- <span data-ttu-id="5b363-114">[參考完整性條件約束](referential-integrity-constraint.md)。</span><span class="sxs-lookup"><span data-stu-id="5b363-114">A [referential integrity constraint](referential-integrity-constraint.md).</span></span> <span data-ttu-id="5b363-115">(選用)</span><span class="sxs-lookup"><span data-stu-id="5b363-115">(Optional)</span></span>  
  
 <span data-ttu-id="5b363-116">每個關聯端都必須指定 [關聯 end 多重性](association-end-multiplicity.md) ，以指出可以位於關聯之一端的實體類型實例數目。</span><span class="sxs-lookup"><span data-stu-id="5b363-116">Each association end must specify an [association end multiplicity](association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="5b363-117">關聯 end 多重性可以有一個 (1) 、零個或一個 (0 ..1) 或許多 () 的值。 \*</span><span class="sxs-lookup"><span data-stu-id="5b363-117">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (\*).</span></span> <span data-ttu-id="5b363-118">您可以透過 [導覽屬性](navigation-property.md) 或外鍵來存取關聯某一端的實體類型實例（如果它們是在實體類型上公開）。</span><span class="sxs-lookup"><span data-stu-id="5b363-118">Entity type instances at one end of an association can be accessed through [navigation properties](navigation-property.md) or foreign keys if they are exposed on an entity type.</span></span> <span data-ttu-id="5b363-119">如需詳細資訊，請參閱 [實體資料模型：外鍵](foreign-key-property.md)。</span><span class="sxs-lookup"><span data-stu-id="5b363-119">For more information, see [Entity Data Model: Foreign Keys](foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b363-120">範例</span><span class="sxs-lookup"><span data-stu-id="5b363-120">Example</span></span>  

 <span data-ttu-id="5b363-121">下圖顯示包含兩個關聯 (`PublishedBy` 和 `WrittenBy`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="5b363-121">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="5b363-122">`PublishedBy` 關聯的關聯 End 為 `Book` 和 `Publisher` 實體類型。</span><span class="sxs-lookup"><span data-stu-id="5b363-122">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="5b363-123">End 的多重性 `Publisher` 是一個 (1) 而 end 的多重性 `Book` 是許多 (\*) ，表示發行者會發行許多書籍，而一本書由一個發行者發行。</span><span class="sxs-lookup"><span data-stu-id="5b363-123">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 ![包含三種實體類型的範例模型](./media/association-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="5b363-125">[ADO.NET Entity Framework](./ef/index.md)會使用 (DSL) 稱為概念結構定義語言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 來定義概念模型的特定領域語言。</span><span class="sxs-lookup"><span data-stu-id="5b363-125">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="5b363-126">下列 CSDL 定義上圖中的 `PublishedBy` 關聯。</span><span class="sxs-lookup"><span data-stu-id="5b363-126">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="5b363-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b363-127">See also</span></span>

- [<span data-ttu-id="5b363-128">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="5b363-128">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="5b363-129">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="5b363-129">Entity Data Model</span></span>](entity-data-model.md)
