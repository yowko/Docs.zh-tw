---
title: 參考完整性條件約束
ms.date: 03/30/2017
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
ms.openlocfilehash: b442e15c75554e1b06e9ff89c7224430a0605f9c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649629"
---
# <a name="referential-integrity-constraint"></a><span data-ttu-id="d54c4-102">參考完整性條件約束</span><span class="sxs-lookup"><span data-stu-id="d54c4-102">referential integrity constraint</span></span>
<span data-ttu-id="d54c4-103">A*參考完整性條件約束*Entity Data Model (EDM) 中是類似於關聯式資料庫中的參考完整性條件約束。</span><span class="sxs-lookup"><span data-stu-id="d54c4-103">A *referential integrity constraint* in the Entity Data Model (EDM) is similar to a referential integrity constraint in a relational database.</span></span> <span data-ttu-id="d54c4-104">從資料庫資料表資料行 （或資料行） 可以參考另一個資料表的主索引鍵的方式相同[屬性](../../../../docs/framework/data/adonet/property.md)（或屬性） 的[實體型別](../../../../docs/framework/data/adonet/entity-type.md)可以參考[實體索引鍵](../../../../docs/framework/data/adonet/entity-key.md)另一個實體類型。</span><span class="sxs-lookup"><span data-stu-id="d54c4-104">In the same way that a column (or columns) from a database table can reference the primary key of another table, a [property](../../../../docs/framework/data/adonet/property.md) (or properties) of an [entity type](../../../../docs/framework/data/adonet/entity-type.md) can reference the [entity key](../../../../docs/framework/data/adonet/entity-key.md) of another entity type.</span></span> <span data-ttu-id="d54c4-105">參考的實體類型稱為*主體端點*條件約束。</span><span class="sxs-lookup"><span data-stu-id="d54c4-105">The entity type that is referenced is called the *principal end* of the constraint.</span></span> <span data-ttu-id="d54c4-106">參考主要端點的實體類型稱為*相依端點*條件約束。</span><span class="sxs-lookup"><span data-stu-id="d54c4-106">The entity type that references the principal end is called the *dependent end* of the constraint.</span></span>  
  
 <span data-ttu-id="d54c4-107">參考完整性條件約束定義的一部分[關聯](../../../../docs/framework/data/adonet/association-type.md)兩個實體類型。</span><span class="sxs-lookup"><span data-stu-id="d54c4-107">A referential integrity constraint is defined as part of an [association](../../../../docs/framework/data/adonet/association-type.md) between two entity types.</span></span> <span data-ttu-id="d54c4-108">參考完整性條件約束的定義指定下列資訊：</span><span class="sxs-lookup"><span data-stu-id="d54c4-108">The definition for a referential integrity constraint specifies the following information:</span></span>  
  
- <span data-ttu-id="d54c4-109">條件約束的主要端點。</span><span class="sxs-lookup"><span data-stu-id="d54c4-109">The principal end of the constraint.</span></span> <span data-ttu-id="d54c4-110">(實體類型，相依端點會參考其實體索引鍵。)</span><span class="sxs-lookup"><span data-stu-id="d54c4-110">(An entity type whose entity key is referenced by the dependent end.)</span></span>  
  
- <span data-ttu-id="d54c4-111">主要端點的實體索引鍵。</span><span class="sxs-lookup"><span data-stu-id="d54c4-111">The entity key of the principal end.</span></span>  
  
- <span data-ttu-id="d54c4-112">條件約束的相依端點。</span><span class="sxs-lookup"><span data-stu-id="d54c4-112">The dependent end of the constraint.</span></span> <span data-ttu-id="d54c4-113">(實體類型，具有參考主要端點之實體索引鍵的屬性。)</span><span class="sxs-lookup"><span data-stu-id="d54c4-113">(An entity type that has a property or properties that reference the entity key of the principal end.)</span></span>  
  
- <span data-ttu-id="d54c4-114">相依端點的參考屬性。</span><span class="sxs-lookup"><span data-stu-id="d54c4-114">The referencing property or properties of the dependent end.</span></span>  
  
 <span data-ttu-id="d54c4-115">在 EDM 中，參考完整性條件約束的目的在於確保有效的關聯永遠存在。</span><span class="sxs-lookup"><span data-stu-id="d54c4-115">The purpose of referential integrity constraints in the EDM is to ensure that valid associations always exist.</span></span> <span data-ttu-id="d54c4-116">如需詳細資訊，請參閱 <<c0> [ 外部索引鍵屬性](../../../../docs/framework/data/adonet/foreign-key-property.md)。</span><span class="sxs-lookup"><span data-stu-id="d54c4-116">For more information, see [foreign key property](../../../../docs/framework/data/adonet/foreign-key-property.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d54c4-117">範例</span><span class="sxs-lookup"><span data-stu-id="d54c4-117">Example</span></span>  
 <span data-ttu-id="d54c4-118">下圖顯示包含兩個關聯 (`WrittenBy` 和 `PublishedBy`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="d54c4-118">The diagram below shows a conceptual model with two associations: `WrittenBy` and `PublishedBy`.</span></span> <span data-ttu-id="d54c4-119">`Book` 實體類型具有屬性 `PublisherId`，當您定義 `Publisher` 關聯的參考完整性條件約束時，此屬性會參考 `PublishedBy` 實體類型的實體索引鍵。</span><span class="sxs-lookup"><span data-stu-id="d54c4-119">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="d54c4-120">![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "的參考條件約束模型範例")</span><span class="sxs-lookup"><span data-stu-id="d54c4-120">![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "Example of a referential constraint model")</span></span>  
  
 <span data-ttu-id="d54c4-121">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="d54c4-121">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="d54c4-122">下列 CSDL 會對上述概念模型中的 `PublishedBy` 關聯定義參考完整性條件約束。</span><span class="sxs-lookup"><span data-stu-id="d54c4-122">The following CSDL defines a referential integrity constraint on the `PublishedBy` association shown in the conceptual model above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="d54c4-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d54c4-123">See also</span></span>

- [<span data-ttu-id="d54c4-124">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="d54c4-124">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="d54c4-125">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="d54c4-125">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
