---
title: 關聯集 End
ms.date: 03/30/2017
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
ms.openlocfilehash: bd104ffb46cbd02a886ce87822ddc37159961174
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198791"
---
# <a name="association-set-end"></a>關聯集 End

*關聯集 end*可識別[關聯集](association-set.md)結尾的[實體類型](entity-type.md)和[實體集](entity-set.md)。 關聯集 End 會定義為關聯集的部分。一個關聯集必須擁有兩個關聯集 End。  
  
 關聯集 End 定義包含下列資訊：  
  
- 關聯集中相關的其中一個屬性類型。 (必要)  
  
- 關聯集中相關實體類型的實體集。 (必要)  
  
## <a name="example"></a>範例  

 下圖顯示包含兩個關聯 (`WrittenBy` 和 `PublishedBy`) 的概念模型。  
  
 ![包含三種實體類型的範例模型](./media/association-set-end/example-model-three-entity-types.gif)  
  
 下圖顯示以前述概念模型為基礎的一個關聯集 (`PublishedBy`) 和兩個實體集 (`Books` 和 `Publishers`)。 關聯集 End 為 `Books` 和 `Publishers` 實體集。 `Books`實體集中的 Bi 代表 `Book` 執行時間的實體型別實例。 同樣地，Pj `Publisher` 則代表 `Publishers` 實體集中的實例。 BiPj 代表 `PublishedBy` 關聯集中關聯的實例 `PublishedBy` 。  
  
 ![顯示集合範例的螢幕擷取畫面。](./media/association-set-end/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md)會使用名為概念結構定義語言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 來定義概念模型的 DSL。 下列 CSDL 定義上圖所示之實體實體容器，每個關聯具有一個關聯集。 請注意，關聯集 End 會定義為每個關聯集定義的一部分。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
