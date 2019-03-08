---
title: 外部索引鍵屬性
ms.date: 03/30/2017
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
ms.openlocfilehash: 8680019f6f1a53233b5c49163f474cf33409b69b
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/08/2019
ms.locfileid: "57674467"
---
# <a name="foreign-key-property"></a>外部索引鍵屬性
A*外部索引鍵屬性*Entity Data Model (EDM) 中是基本型別[屬性](../../../../docs/framework/data/adonet/property.md)（或一組基本型別屬性） 上[實體類型](../../../../docs/framework/data/adonet/entity-type.md)包含[實體索引鍵](../../../../docs/framework/data/adonet/entity-key.md)另一個實體類型。  
  
 外部索引鍵屬性類似關聯式資料庫中的外部索引鍵資料行。 同樣地，外部索引鍵資料行關聯式資料庫中用來建立資料表的資料列之間的關聯性，在概念模型中的外部索引鍵屬性用來建立[關聯](../../../../docs/framework/data/adonet/association-type.md)實體類型之間。 A[參考完整性條件約束](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)用來定義兩個實體類型，當其中一個型別具有外部索引鍵屬性之間的關聯。  
  
## <a name="example"></a>範例  
 下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。 
  `Book` 實體類型具有屬性 `PublisherId`，當您定義 `Publisher` 關聯的參考完整性條件約束時，此屬性會參考 `PublishedBy` 實體類型的實體索引鍵。  
  
 ![RefConstraintModel](./media/foreign-key-property/reference-constraint-model.gif "的參考條件約束模型範例")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。 下列 CSDL 使用外部索引鍵屬性 `PublisherId`，針對上述概念模型中的 `PublishedBy` 關聯定義參考完整性條件約束。  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>另請參閱
- [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)
