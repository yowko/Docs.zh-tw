---
title: 參考完整性條件約束
description: 瞭解實體資料模型中的參考完整性條件約束，確保實體類型之間一律存在有效的關聯。
ms.date: 03/30/2017
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
ms.openlocfilehash: 6ade9d0155a6915757c7f47c5cb3ab0a51dbd437
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172732"
---
# <a name="referential-integrity-constraint"></a>參考完整性條件約束

實體資料模型 (EDM) 中的 *參考完整性條件約束* 類似于關係資料庫中的參考完整性條件約束。 與資料行 (或從資料庫資料表) 的資料行相同的方式可以參考另一個資料表的主鍵，而[實體類型](entity-type.md)) 的 ([屬性（property](property.md) ）可以參考另一個實體類型的[實體索引鍵](entity-key.md)。 參考的實體類型稱為條件約束的 *主要端點* 。 參考主體端的實體類型稱為條件約束的 *相依端點* 。  
  
 參考完整性條件約束定義為兩個實體類型之間 [關聯](association-type.md) 的一部分。 參考完整性條件約束的定義指定下列資訊：  
  
- 條件約束的主要端點。 (實體類型，相依端點會參考其實體索引鍵。)  
  
- 主要端點的實體索引鍵。  
  
- 條件約束的相依端點。 (實體類型，具有參考主要端點之實體索引鍵的屬性。)  
  
- 相依端點的參考屬性。  
  
 在 EDM 中，參考完整性條件約束的目的在於確保有效的關聯永遠存在。 如需詳細資訊，請參閱 [外鍵屬性](foreign-key-property.md)。  
  
## <a name="example"></a>範例  

 下圖顯示包含兩個關聯 (`WrittenBy` 和 `PublishedBy`) 的概念模型。 `Book` 實體類型具有屬性 `PublisherId`，當您定義 `Publisher` 關聯的參考完整性條件約束時，此屬性會參考 `PublishedBy` 實體類型的實體索引鍵。  
  
 ![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "參考條件約束模型的範例")  
  
 [ADO.NET Entity Framework](./ef/index.md)會使用 (DSL) 稱為概念結構定義語言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 來定義概念模型的特定領域語言。 下列 CSDL 會對上述概念模型中的 `PublishedBy` 關聯定義參考完整性條件約束。  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
