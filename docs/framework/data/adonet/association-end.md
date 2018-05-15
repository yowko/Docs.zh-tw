---
title: 關聯 End
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: 9d7bd6fa92a4337add18deafbeb5ad28fefcb749
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="association-end"></a><span data-ttu-id="ade3f-102">關聯 End</span><span class="sxs-lookup"><span data-stu-id="ade3f-102">association end</span></span>
<span data-ttu-id="ade3f-103">*關聯 end*識別[實體類型](../../../../docs/framework/data/adonet/entity-type.md)的一個 end 上[關聯](../../../../docs/framework/data/adonet/association-type.md)以及關聯的結尾處，輸入可以存在的執行個體的實體數目。</span><span class="sxs-lookup"><span data-stu-id="ade3f-103">An *association end* identifies the [entity type](../../../../docs/framework/data/adonet/entity-type.md) on one end of an [association](../../../../docs/framework/data/adonet/association-type.md) and the number of entity type instances that can exist at that end of an association.</span></span> <span data-ttu-id="ade3f-104">關聯 End 會定義為關聯的部分。關聯必須具有兩個關聯 End。</span><span class="sxs-lookup"><span data-stu-id="ade3f-104">Association ends are defined as part of an association; an association must have exactly two association ends.</span></span> <span data-ttu-id="ade3f-105">[導覽屬性](../../../../docs/framework/data/adonet/navigation-property.md)允許從一個關聯 end 導覽至其他。</span><span class="sxs-lookup"><span data-stu-id="ade3f-105">[Navigation properties](../../../../docs/framework/data/adonet/navigation-property.md) allow for navigation from one association end to the other.</span></span>  
  
 <span data-ttu-id="ade3f-106">關聯 End 定義包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="ade3f-106">An association end definition contains the following information:</span></span>  
  
-   <span data-ttu-id="ade3f-107">關聯中相關的其中一個屬性類型。</span><span class="sxs-lookup"><span data-stu-id="ade3f-107">One of the entity types involved in the association.</span></span> <span data-ttu-id="ade3f-108">(必要項)</span><span class="sxs-lookup"><span data-stu-id="ade3f-108">(Required)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="ade3f-109">若為指定關聯，各關聯的指定實體類型可以相同。</span><span class="sxs-lookup"><span data-stu-id="ade3f-109">For a given association, the entity type specified for each association end can be the same.</span></span> <span data-ttu-id="ade3f-110">這樣會建立自我關聯。</span><span class="sxs-lookup"><span data-stu-id="ade3f-110">This creates a self-association.</span></span>  
  
-   <span data-ttu-id="ade3f-111">[關聯 end 多重性](../../../../docs/framework/data/adonet/association-end-multiplicity.md)表示可以是位於關聯某一端的實體類型執行個體數目。</span><span class="sxs-lookup"><span data-stu-id="ade3f-111">An [association end multiplicity](../../../../docs/framework/data/adonet/association-end-multiplicity.md) that indicates the number of entity type instances that can be at one end of the association.</span></span> <span data-ttu-id="ade3f-112">關聯 End 多重性的值可以是一 (0)、零或一 (0..1)，或許多 (\*)。</span><span class="sxs-lookup"><span data-stu-id="ade3f-112">An association end multiplicity can have a value of one (1), zero or one (0..1), or many (\*).</span></span>  
  
-   <span data-ttu-id="ade3f-113">關聯 End 的名稱。</span><span class="sxs-lookup"><span data-stu-id="ade3f-113">A name for the association end.</span></span> <span data-ttu-id="ade3f-114">(選擇項)</span><span class="sxs-lookup"><span data-stu-id="ade3f-114">(Optional)</span></span>  
  
-   <span data-ttu-id="ade3f-115">在關聯 End 中所執行的作業相關資訊，例如刪除時的重疊顯示。</span><span class="sxs-lookup"><span data-stu-id="ade3f-115">Information about operations that are performed on the association end, such as cascade on delete.</span></span> <span data-ttu-id="ade3f-116">(選擇項)</span><span class="sxs-lookup"><span data-stu-id="ade3f-116">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="ade3f-117">範例</span><span class="sxs-lookup"><span data-stu-id="ade3f-117">Example</span></span>  
 <span data-ttu-id="ade3f-118">下圖顯示包含兩個關聯 (`PublishedBy` 和 `WrittenBy`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="ade3f-118">The diagram below shows a conceptual model with two associations: `PublishedBy` and `WrittenBy`.</span></span> <span data-ttu-id="ade3f-119">`PublishedBy` 關聯的關聯 End 為 `Book` 和 `Publisher` 實體類型。</span><span class="sxs-lookup"><span data-stu-id="ade3f-119">The association ends for the `PublishedBy` association are the `Book` and `Publisher` entity types.</span></span> <span data-ttu-id="ade3f-120">`Publisher` End 的多重性是 (1)，而 `Book` End 的多重性是許多 (\*)，表示一個發行者發行許多書籍，而一本書籍由一個發行者發行。</span><span class="sxs-lookup"><span data-stu-id="ade3f-120">The multiplicity of the `Publisher` end is one (1) and the multiplicity of the `Book` end is many (\*), indicating that a publisher publishes many books and a book is published by one publisher.</span></span>  
  
 <span data-ttu-id="ade3f-121">![範例模型](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span><span class="sxs-lookup"><span data-stu-id="ade3f-121">![Example Model](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")</span></span>  
  
 <span data-ttu-id="ade3f-122">ADO.NET Entity Framework 會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="ade3f-122">The ADO.NET Entity Framework uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="ade3f-123">下列的 CSDL 會定義上圖顯示的 `PublishedBy` 關聯。</span><span class="sxs-lookup"><span data-stu-id="ade3f-123">The CSDL below defines the `PublishedBy` association shown in the diagram above.</span></span> <span data-ttu-id="ade3f-124">請注意，各個關聯 End 的類型、名稱和多重性是由 XML 屬性 (分別為 `Type`、`Role` 和 `Multiplicity` 屬性) 指定的。</span><span class="sxs-lookup"><span data-stu-id="ade3f-124">Note that the type, name, and multiplicity of each association end are specified by XML attributes (the `Type`, `Role`, and `Multiplicity` attributes, respectively).</span></span> <span data-ttu-id="ade3f-125">關於針對其中一端執行之作業的選擇性資訊會在 XML 項目 (`OnDelete` 項目) 中指定。</span><span class="sxs-lookup"><span data-stu-id="ade3f-125">Optional information about operations performed on an end is specified in an XML element (the `OnDelete` element).</span></span> <span data-ttu-id="ade3f-126">在此情況中，如果刪除發行者，也會刪除所有相關的書籍。</span><span class="sxs-lookup"><span data-stu-id="ade3f-126">In this case, if a publisher is deleted, so are all associated books.</span></span>  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a><span data-ttu-id="ade3f-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ade3f-127">See Also</span></span>  
 [<span data-ttu-id="ade3f-128">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="ade3f-128">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="ade3f-129">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="ade3f-129">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
