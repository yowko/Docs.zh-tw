---
title: "外部索引鍵屬性"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 626feac70099667e0dc15b12043834bda6d4b20e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="foreign-key-property"></a><span data-ttu-id="a0919-102">外部索引鍵屬性</span><span class="sxs-lookup"><span data-stu-id="a0919-102">foreign key property</span></span>
<span data-ttu-id="a0919-103">A*外部索引鍵屬性*實體資料模型 (EDM) 中是基本型別[屬性](../../../../docs/framework/data/adonet/property.md)（或基本型別屬性的一組） 上[實體類型](../../../../docs/framework/data/adonet/entity-type.md)包含[實體索引鍵](../../../../docs/framework/data/adonet/entity-key.md)另一個實體類型。</span><span class="sxs-lookup"><span data-stu-id="a0919-103">A *foreign key property* in the Entity Data Model (EDM) is a primitive type [property](../../../../docs/framework/data/adonet/property.md) (or a set of primitive type properties) on an [entity type](../../../../docs/framework/data/adonet/entity-type.md) that contains the [entity key](../../../../docs/framework/data/adonet/entity-key.md) of another entity type.</span></span>  
  
 <span data-ttu-id="a0919-104">外部索引鍵屬性類似關聯式資料庫中的外部索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="a0919-104">A foreign key property is analogous to a foreign key column in a relational database.</span></span> <span data-ttu-id="a0919-105">外部索引鍵資料行用於建立資料表中的資料列之間的關聯性的關聯式資料庫的相同方式，在概念模型中的外部索引鍵屬性用來建立[關聯](../../../../docs/framework/data/adonet/association-type.md)實體類型之間。</span><span class="sxs-lookup"><span data-stu-id="a0919-105">In the same way that foreign key columns are used in a relational database to create relationships between rows in tables, foreign key properties in a conceptual model are used to establish [associations](../../../../docs/framework/data/adonet/association-type.md) between entity types.</span></span> <span data-ttu-id="a0919-106">A[參考完整性條件約束](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)用來定義兩個實體類型，當其中一個型別具有外部索引鍵屬性之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="a0919-106">A [referential integrity constraint](../../../../docs/framework/data/adonet/referential-integrity-constraint.md) is used to define an association between two entity types when one of the types has a foreign key property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0919-107">範例</span><span class="sxs-lookup"><span data-stu-id="a0919-107">Example</span></span>  
 <span data-ttu-id="a0919-108">下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。</span><span class="sxs-lookup"><span data-stu-id="a0919-108">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span> <span data-ttu-id="a0919-109">`Book` 實體類型具有屬性 `PublisherId`，當您定義 `Publisher` 關聯的參考完整性條件約束時，此屬性會參考 `PublishedBy` 實體類型的實體索引鍵。</span><span class="sxs-lookup"><span data-stu-id="a0919-109">The `Book` entity type has a property, `PublisherId`, that references the entity key of the `Publisher` entity type when you define a referential integrity constraint on the `PublishedBy` association.</span></span>  
  
 <span data-ttu-id="a0919-110">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span><span class="sxs-lookup"><span data-stu-id="a0919-110">![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")</span></span>  
  
 <span data-ttu-id="a0919-111">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。</span><span class="sxs-lookup"><span data-stu-id="a0919-111">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="a0919-112">下列 CSDL 使用外部索引鍵屬性 `PublisherId`，針對上述概念模型中的 `PublishedBy` 關聯定義參考完整性條件約束。</span><span class="sxs-lookup"><span data-stu-id="a0919-112">The following CSDL uses the foreign key property `PublisherId` to define a referential integrity constraint on the `PublishedBy` association shown in the conceptual model shown above.</span></span>  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a><span data-ttu-id="a0919-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0919-113">See Also</span></span>  
 [<span data-ttu-id="a0919-114">實體資料模型的重要概念</span><span class="sxs-lookup"><span data-stu-id="a0919-114">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="a0919-115">實體資料模型</span><span class="sxs-lookup"><span data-stu-id="a0919-115">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
