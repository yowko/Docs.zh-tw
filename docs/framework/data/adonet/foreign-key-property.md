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
# <a name="foreign-key-property"></a>外部索引鍵屬性
在實體資料模型（EDM）中的*外鍵屬性*是[實體類型](entity-type.md)上的基本型別[屬性](property.md)（或一組基本類型屬性），其中包含另一個實體類型的[實體索引鍵](entity-key.md)。  
  
 外部索引鍵屬性類似關聯式資料庫中的外部索引鍵資料行。 在關係資料庫中，使用外鍵資料行來建立資料表中資料列之間的關聯性，概念模型中的外鍵屬性會用來建立實體類型之間的[關聯](association-type.md)。 當其中一個類型具有外鍵屬性時，會使用[參考完整性條件約束](referential-integrity-constraint.md)來定義兩個實體類型之間的關聯。  
  
## <a name="example"></a>範例  
 下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。 `Book` 實體類型具有屬性 `PublisherId`，當您定義 `Publisher` 關聯的參考完整性條件約束時，此屬性會參考 `PublishedBy` 實體類型的實體索引鍵。  
  
 ![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "參考條件約束模型的範例")  
  
 [ADO.NET Entity Framework](./ef/index.md)會使用稱為概念結構定義語言（[CSDL](./ef/language-reference/csdl-specification.md)）的特定領域語言（DSL）來定義概念模型。 下列 CSDL 使用外部索引鍵屬性 `PublisherId`，針對上述概念模型中的 `PublishedBy` 關聯定義參考完整性條件約束。  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
