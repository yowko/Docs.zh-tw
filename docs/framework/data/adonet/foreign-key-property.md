---
title: 外部索引鍵屬性
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: e2f41c2db9aea26c7954a99ebf3f40b03e8df735
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795036"
---
# <a name="foreign-key-property"></a><span data-ttu-id="b070e-102">外部索引鍵屬性</span><span class="sxs-lookup"><span data-stu-id="b070e-102">foreign key property</span></span>
<span data-ttu-id="b070e-103">在實體資料模型（EDM）中的*外鍵屬性*是[實體類型](entity-type.md)上的基本型別[屬性](property.md)（或一組基本類型屬性），其中包含另一個實體類型的[實體索引鍵](entity-key.md)。</span><span class="sxs-lookup"><span data-stu-id="b070e-103">A *foreign key property* in the Entity Data Model (EDM) is a primitive type [property](property.md) (or a set of primitive type properties) on an [entity type](entity-type.md) that contains the [entity key](entity-key.md) of another entity type.</span></span>  
  
 <span data-ttu-id="b070e-104">外部索引鍵屬性類似關聯式資料庫中的外部索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="b070e-104">A foreign key property is analogous to a foreign key column in a relational database.</span></span> <span data-ttu-id="b070e-105">在關係資料庫中，使用外鍵資料行來建立資料表中資料列之間的關聯性，概念模型中的外鍵屬性會用來建立實體類型之間的[關聯](association-type.md)。</span><span class="sxs-lookup"><span data-stu-id="b070e-105">In the same way that foreign key columns are used in a relational database to create relationships between rows in tables, foreign key properties in a conceptual model are used to establish [associations](association-type.md) between entity types.</span></span> <span data-ttu-id="b070e-106">當其中一個類型具有外鍵屬性時，會使用[參考完整性條件約束](referential-integrity-constraint.md)來定義兩個實體類型之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="b070e-106">A [referential integrity constraint](referential-integrity-constraint.md) is used to define an association between two entity types when one of the types has a foreign key property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b070e-107">範例</span><span class="sxs-lookup"><span data-stu-id="b070e-107">Example</span></span>  
 <span data-ttu-id="b070e-108">下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="b070e-108">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="b070e-109">`Book` 實體類型具有屬性 `PublisherId`，當您定義 `Publisher` 關聯的參考完整性條件約束時，此屬性會參考 `PublishedBy` 實體類型的實體索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b070e-109">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="b070e-110">![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "參考條件約束模型的範例")</span><span class="sxs-lookup"><span data-stu-id="b070e-110">![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "Example of a referential constraint model")</span></span>  
  
 <span data-ttu-id="b070e-111">[ADO.NET Entity Framework](./ef/index.md)會使用稱為概念結構定義語言（[CSDL](./ef/language-reference/csdl-specification.md)）的特定領域語言（DSL）來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="b070e-111">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="b070e-112">下列 CSDL 使用外部索引鍵屬性 `PublisherId`，針對上述概念模型中的 `PublishedBy` 關聯定義參考完整性條件約束。</span><span class="sxs-lookup"><span data-stu-id="b070e-112">The following CSDL uses the foreign key property `PublisherId` to define a referential integrity constraint on the `PublishedBy` association shown in the conceptual model shown above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="b070e-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b070e-113">See also</span></span>

- [<span data-ttu-id="b070e-114">實體資料模型索引鍵概念</span><span class="sxs-lookup"><span data-stu-id="b070e-114">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="b070e-115">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="b070e-115">Entity Data Model</span></span>](entity-data-model.md)
