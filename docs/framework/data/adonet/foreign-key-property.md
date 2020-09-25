---
title: 外部索引鍵屬性
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: be0fcb94b0b457a33c17e7125cd22db50f298cc6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189314"
---
# <a name="foreign-key-property"></a>外部索引鍵屬性

實體資料模型 (EDM) 中的*外鍵屬性*是基本型別[屬性](property.md) (或一組基本類型屬性) 在包含另一個實體類型之[實體索引鍵](entity-key.md)的[實體類型](entity-type.md)上。  
  
 外部索引鍵屬性類似關聯式資料庫中的外部索引鍵資料行。 在關係資料庫中使用外鍵資料行來建立資料表中資料列之間的關聯性，概念模型中的外鍵屬性是用來建立實體類型之間的 [關聯](association-type.md) 。 當其中一個類型具有外鍵屬性時，會使用 [參考完整性條件約束](referential-integrity-constraint.md) 來定義兩個實體類型之間的關聯。  
  
## <a name="example"></a>範例  

 下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。 `Book` 實體類型具有屬性 `PublisherId`，當您定義 `Publisher` 關聯的參考完整性條件約束時，此屬性會參考 `PublishedBy` 實體類型的實體索引鍵。  
  
 ![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "參考條件約束模型的範例")  
  
 [ADO.NET Entity Framework](./ef/index.md)會使用 (DSL) 稱為概念結構定義語言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 來定義概念模型的特定領域語言。 下列 CSDL 使用外部索引鍵屬性 `PublisherId`，針對上述概念模型中的 `PublishedBy` 關聯定義參考完整性條件約束。  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
