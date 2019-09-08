---
title: 參考完整性條件約束
ms.date: 03/30/2017
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
ms.openlocfilehash: 28880c7085f8b4e3dd2e51b5633c1f0e2a984a4b
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794451"
---
# <a name="referential-integrity-constraint"></a>參考完整性條件約束
實體資料模型（EDM）中的*參考完整性條件約束*類似關係資料庫中的參考完整性條件約束。 與資料庫資料表的資料行（或資料行）可以參考另一個資料表的主要索引鍵一樣，[實體類型](entity-type.md)的[屬性](property.md)（或屬性）可以參考另一個實體類型的[實體索引鍵](entity-key.md)。 參考的實體類型稱為條件約束的*主要端點*。 參考主要端點的實體類型稱為條件約束的*相依端點*。  
  
 參考完整性條件約束會定義為兩個實體類型之間[關聯](association-type.md)的一部分。 參考完整性條件約束的定義指定下列資訊：  
  
- 條件約束的主要端點。 (實體類型，相依端點會參考其實體索引鍵。)  
  
- 主要端點的實體索引鍵。  
  
- 條件約束的相依端點。 (實體類型，具有參考主要端點之實體索引鍵的屬性。)  
  
- 相依端點的參考屬性。  
  
 在 EDM 中，參考完整性條件約束的目的在於確保有效的關聯永遠存在。 如需詳細資訊，請參閱[外鍵屬性](foreign-key-property.md)。  
  
## <a name="example"></a>範例  
 下圖顯示包含兩個關聯 (`WrittenBy` 和 `PublishedBy`) 的概念模型。 `Book` 實體類型具有屬性 `PublisherId`，當您定義 `Publisher` 關聯的參考完整性條件約束時，此屬性會參考 `PublishedBy` 實體類型的實體索引鍵。  
  
 ![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "參考條件約束模型的範例")  
  
 [ADO.NET Entity Framework](./ef/index.md)會使用稱為概念結構定義語言（[CSDL](./ef/language-reference/csdl-specification.md)）的特定領域語言（DSL）來定義概念模型。 下列 CSDL 會對上述概念模型中的 `PublishedBy` 關聯定義參考完整性條件約束。  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
