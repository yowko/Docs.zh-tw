---
title: 參考完整性條件約束
ms.date: 03/30/2017
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
ms.openlocfilehash: a8ef035872317c6eaea0401164e7fa8c95f5f7ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59073971"
---
# <a name="referential-integrity-constraint"></a>參考完整性條件約束
A*參考完整性條件約束*Entity Data Model (EDM) 中是類似於關聯式資料庫中的參考完整性條件約束。 從資料庫資料表資料行 （或資料行） 可以參考另一個資料表的主索引鍵的方式相同[屬性](../../../../docs/framework/data/adonet/property.md)（或屬性） 的[實體型別](../../../../docs/framework/data/adonet/entity-type.md)可以參考[實體索引鍵](../../../../docs/framework/data/adonet/entity-key.md)另一個實體類型。 參考的實體類型稱為*主體端點*條件約束。 參考主要端點的實體類型稱為*相依端點*條件約束。  
  
 參考完整性條件約束定義的一部分[關聯](../../../../docs/framework/data/adonet/association-type.md)兩個實體類型。 參考完整性條件約束的定義指定下列資訊：  
  
-   條件約束的主要端點。 (實體類型，相依端點會參考其實體索引鍵。)  
  
-   主要端點的實體索引鍵。  
  
-   條件約束的相依端點。 (實體類型，具有參考主要端點之實體索引鍵的屬性。)  
  
-   相依端點的參考屬性。  
  
 在 EDM 中，參考完整性條件約束的目的在於確保有效的關聯永遠存在。 如需詳細資訊，請參閱 <<c0> [ 外部索引鍵屬性](../../../../docs/framework/data/adonet/foreign-key-property.md)。  
  
## <a name="example"></a>範例  
 下圖顯示包含兩個關聯 (`WrittenBy` 和 `PublishedBy`) 的概念模型。 `Book` 實體類型具有屬性 `PublisherId`，當您定義 `Publisher` 關聯的參考完整性條件約束時，此屬性會參考 `PublishedBy` 實體類型的實體索引鍵。  
  
 ![RefConstraintModel](./media/referential-integrity-constraint/reference-constraint-model.gif "的參考條件約束模型範例")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。 下列 CSDL 會對上述概念模型中的 `PublishedBy` 關聯定義參考完整性條件約束。  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)
