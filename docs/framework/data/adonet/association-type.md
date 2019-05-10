---
title: 關聯類型
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: 7fbdc0316b1f9fd0bb282fd466857b1426c41df1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583724"
---
# <a name="association-type"></a><span data-ttu-id="df72f-102">關聯類型</span><span class="sxs-lookup"><span data-stu-id="df72f-102">association type</span></span>
<span data-ttu-id="df72f-103">*關聯型別*（亦稱為關聯） 是描述 Entity Data Model (EDM) 中的關聯性的基本建置組塊。</span><span class="sxs-lookup"><span data-stu-id="df72f-103">An *association type* (also called an association) is the fundamental building block for describing relationships in the Entity Data Model (EDM).</span></span> <span data-ttu-id="df72f-104">在概念模型中，關聯代表兩個關聯性[實體類型](../../../../docs/framework/data/adonet/entity-type.md)(例如`Customer`和`Order`)。</span><span class="sxs-lookup"><span data-stu-id="df72f-104">In a conceptual model, an association represents a relationship between two [entity types](../../../../docs/framework/data/adonet/entity-type.md) (such as `Customer` and `Order`).</span></span> <span data-ttu-id="df72f-105">在應用程式中，關聯的執行個體代表特定的關聯 (例如 `Customer` 執行個體和 `Order` 執行個體之間的關聯)。</span><span class="sxs-lookup"><span data-stu-id="df72f-105">In an application, an instance of an association represents a specific association (such as an association between an instance of `Customer` and an instance of `Order`).</span></span> <span data-ttu-id="df72f-106">關聯執行個體會以邏輯方式分組[關聯集](../../../../docs/framework/data/adonet/association-set.md)。</span><span class="sxs-lookup"><span data-stu-id="df72f-106">Association instances are logically grouped in an [association set](../../../../docs/framework/data/adonet/association-set.md).</span></span>  
  
 <span data-ttu-id="df72f-107">關聯定義包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="df72f-107">An association definition contains the following information:</span></span>  
  
- <span data-ttu-id="df72f-108">唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="df72f-108">A unique name.</span></span> <span data-ttu-id="df72f-109">(必要項)</span><span class="sxs-lookup"><span data-stu-id="df72f-109">(Required)</span></span>  
  
- <span data-ttu-id="df72f-110">兩個[關聯 end](../../../../docs/framework/data/adonet/association-end.md)，一個用於關聯性中的每個實體類型。</span><span class="sxs-lookup"><span data-stu-id="df72f-110">Two [association ends](../../../../docs/framework/data/adonet/association-end.md), one for each entity type in the relationship.</span></span> <span data-ttu-id="df72f-111">(必要項)</span><span class="sxs-lookup"><span data-stu-id="df72f-111">(Required)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="df72f-112">一個關聯 (association) 不能代表兩個實體型別以上的關聯性 (relationship)。</span><span class="sxs-lookup"><span data-stu-id="df72f-112">An association cannot represent a relationship among more than two entity types.</span></span> <span data-ttu-id="df72f-113">不過，關聯可以為其每一個關聯 End 指定同樣的實體型別，以定義自我關聯性。</span><span class="sxs-lookup"><span data-stu-id="df72f-113">An association can, however, define a self-relationship by specifying the same entity type for each of its association ends.</span></span>  
  
- <span data-ttu-id="df72f-114">A[參考完整性條件約束](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)。</span><span class="sxs-lookup"><span data-stu-id="df72f-114">A [referential integrity constraint](../../../../docs/framework/data/adonet/referential-integrity-constraint.md).</span></span> <span data-ttu-id="df72f-115">(選擇項)</span><span class="sxs-lookup"><span data-stu-id="df72f-115">(Optional)</span></span>  
  
 <span data-ttu-id="df72f-116">每個關聯 end 必須指定[關聯 end 多重性](../../../../docs/framework/data/adonet/association-end-multiplicity.md)表示可以是位於關聯某一端的實體類型執行個體數目。</span><span class="sxs-lookup"><span data-stu-id="df72f-116">Each association end must specify an [association end multiplicity](../../../../docs/framework/data/adonet/association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="df72f-117">關聯 end 多重性可以有值為一 (1)、 零或一個 (0..1)，或多個 (\*)。</span><span class="sxs-lookup"><span data-stu-id="df72f-117">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (\*).</span></span> <span data-ttu-id="df72f-118">您可以透過位於關聯某一端的實體類型執行個體[導覽屬性](../../../../docs/framework/data/adonet/navigation-property.md)或外部索引鍵，如果實體類型上公開。</span><span class="sxs-lookup"><span data-stu-id="df72f-118">Entity type instances at one end of an association can be accessed through [navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) or foreign keys if they are exposed on an entity type.</span></span> <span data-ttu-id="df72f-119">如需詳細資訊，請參閱[實體資料模型：外部索引鍵](../../../../docs/framework/data/adonet/foreign-key-property.md)。</span><span class="sxs-lookup"><span data-stu-id="df72f-119">For more information, see [Entity Data Model: Foreign Keys](../../../../docs/framework/data/adonet/foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="df72f-120">範例</span><span class="sxs-lookup"><span data-stu-id="df72f-120">Example</span></span>  
 <span data-ttu-id="df72f-121">下圖顯示包含兩個關聯 (`PublishedBy` 和 `WrittenBy`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="df72f-121">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="df72f-122">`PublishedBy` 關聯的關聯 End 為 `Book` 和 `Publisher` 實體類型。</span><span class="sxs-lookup"><span data-stu-id="df72f-122">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="df72f-123">端點的多重性`Publisher`結尾是一 (1) 和端點的多重性`Book`端是許多 (\*)，表示一個發行者發行許多書籍，以及一本書籍由一個發行者發行。</span><span class="sxs-lookup"><span data-stu-id="df72f-123">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 ![具有三種實體類型的範例模型](./media/association-type/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="df72f-125">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="df72f-125">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="df72f-126">下列 CSDL 定義上圖中的 `PublishedBy` 關聯。</span><span class="sxs-lookup"><span data-stu-id="df72f-126">The following CSDL defines the `PublishedBy` association shown in the diagram above:</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a><span data-ttu-id="df72f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df72f-127">See also</span></span>

- [<span data-ttu-id="df72f-128">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="df72f-128">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="df72f-129">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="df72f-129">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
