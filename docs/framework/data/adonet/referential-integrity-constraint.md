---
title: "參考完整性條件約束"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c343a0eba2478e041186f7bef18a85400c54bb5c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="referential-integrity-constraint"></a><span data-ttu-id="51763-102">參考完整性條件約束</span><span class="sxs-lookup"><span data-stu-id="51763-102">referential integrity constraint</span></span>
<span data-ttu-id="51763-103">A*參考完整性條件約束*實體資料模型 (EDM) 中是類似於關聯式資料庫中的參考完整性條件約束。</span><span class="sxs-lookup"><span data-stu-id="51763-103">A *referential integrity constraint* in the Entity Data Model (EDM) is similar to a referential integrity constraint in a relational database.</span></span> <span data-ttu-id="51763-104">從資料庫資料表資料行 （或資料行） 都可以參考另一個資料表的主索引鍵的方式相同[屬性](../../../../docs/framework/data/adonet/property.md)（或屬性） 的[實體類型](../../../../docs/framework/data/adonet/entity-type.md)可以參考[實體索引鍵](../../../../docs/framework/data/adonet/entity-key.md)另一個實體類型。</span><span class="sxs-lookup"><span data-stu-id="51763-104">In the same way that a column (or columns) from a database table can reference the primary key of another table, a [property](../../../../docs/framework/data/adonet/property.md) (or properties) of an [entity type](../../../../docs/framework/data/adonet/entity-type.md) can reference the [entity key](../../../../docs/framework/data/adonet/entity-key.md) of another entity type.</span></span> <span data-ttu-id="51763-105">參考的實體類型稱為*主要端點*條件約束。</span><span class="sxs-lookup"><span data-stu-id="51763-105">The entity type that is referenced is called the *principal end* of the constraint.</span></span> <span data-ttu-id="51763-106">參考主要端點的實體類型稱為*相依端點*條件約束。</span><span class="sxs-lookup"><span data-stu-id="51763-106">The entity type that references the principal end is called the *dependent end* of the constraint.</span></span>  
  
 <span data-ttu-id="51763-107">參考完整性條件約束定義的一部分為[關聯](../../../../docs/framework/data/adonet/association-type.md)兩個實體類型。</span><span class="sxs-lookup"><span data-stu-id="51763-107">A referential integrity constraint is defined as part of an [association](../../../../docs/framework/data/adonet/association-type.md) between two entity types.</span></span> <span data-ttu-id="51763-108">參考完整性條件約束的定義指定下列資訊：</span><span class="sxs-lookup"><span data-stu-id="51763-108">The definition for a referential integrity constraint specifies the following information:</span></span>  
  
-   <span data-ttu-id="51763-109">條件約束的主要端點。</span><span class="sxs-lookup"><span data-stu-id="51763-109">The principal end of the constraint.</span></span> <span data-ttu-id="51763-110">(實體類型，相依端點會參考其實體索引鍵。)</span><span class="sxs-lookup"><span data-stu-id="51763-110">(An entity type whose entity key is referenced by the dependent end.)</span></span>  
  
-   <span data-ttu-id="51763-111">主要端點的實體索引鍵。</span><span class="sxs-lookup"><span data-stu-id="51763-111">The entity key of the principal end.</span></span>  
  
-   <span data-ttu-id="51763-112">條件約束的相依端點。</span><span class="sxs-lookup"><span data-stu-id="51763-112">The dependent end of the constraint.</span></span> <span data-ttu-id="51763-113">(實體類型，具有參考主要端點之實體索引鍵的屬性。)</span><span class="sxs-lookup"><span data-stu-id="51763-113">(An entity type that has a property or properties that reference the entity key of the principal end.)</span></span>  
  
-   <span data-ttu-id="51763-114">相依端點的參考屬性。</span><span class="sxs-lookup"><span data-stu-id="51763-114">The referencing property or properties of the dependent end.</span></span>  
  
 <span data-ttu-id="51763-115">在 EDM 中，參考完整性條件約束的目的在於確保有效的關聯永遠存在。</span><span class="sxs-lookup"><span data-stu-id="51763-115">The purpose of referential integrity constraints in the EDM is to ensure that valid associations always exist.</span></span> <span data-ttu-id="51763-116">如需詳細資訊，請參閱[外部索引鍵屬性](../../../../docs/framework/data/adonet/foreign-key-property.md)。</span><span class="sxs-lookup"><span data-stu-id="51763-116">For more information, see [foreign key property](../../../../docs/framework/data/adonet/foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="51763-117">範例</span><span class="sxs-lookup"><span data-stu-id="51763-117">Example</span></span>  
 <span data-ttu-id="51763-118">下圖顯示包含兩個關聯 (`WrittenBy` 和 `PublishedBy`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="51763-118">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span> <span data-ttu-id="51763-119">`Book` 實體類型具有屬性 `PublisherId`，當您定義 `Publisher` 關聯的參考完整性條件約束時，此屬性會參考 `PublishedBy` 實體類型的實體索引鍵。</span><span class="sxs-lookup"><span data-stu-id="51763-119">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="51763-120">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span><span class="sxs-lookup"><span data-stu-id="51763-120">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span></span>  
  
 <span data-ttu-id="51763-121">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="51763-121">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="51763-122">下列 CSDL 會對上述概念模型中的 `PublishedBy` 關聯定義參考完整性條件約束。</span><span class="sxs-lookup"><span data-stu-id="51763-122">The following CSDL defines a referential integrity constraint on the `PublishedBy` association shown in the conceptual model above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="51763-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="51763-123">See Also</span></span>  
 [<span data-ttu-id="51763-124">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="51763-124">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="51763-125">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="51763-125">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
