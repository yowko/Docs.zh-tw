---
title: 關聯 End
ms.date: 03/30/2017
ms.assetid: 2c345213-0296-4d90-ac6d-cef179798a75
ms.openlocfilehash: 00e3a7d855957ae539ea652dc8cde3ed8841dda5
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153439"
---
# <a name="association-end"></a>關聯 End

*關聯 end*會識別[關聯](association-type.md)一端的[實體類型](entity-type.md)，以及可以存在於關聯的那一端之實體類型實例的數目。 關聯 End 會定義為關聯的部分。關聯必須具有兩個關聯 End。 [導覽屬性](navigation-property.md) 可讓您從一個關聯端導覽至另一個關聯。  
  
 關聯 End 定義包含下列資訊：  
  
- 關聯中相關的其中一個屬性類型。 (必要)  
  
    > [!NOTE]
    > 若為指定關聯，各關聯的指定實體類型可以相同。 這樣會建立自我關聯。  
  
- [關聯 end 多重性](association-end-multiplicity.md)，表示可以位於關聯之一端的實體類型實例數目。 關聯 end 多重性可以有一個 (1) 、零個或一個 (0 ..1) 或許多 () 的值。 \*  
  
- 關聯 End 的名稱。 (選用)  
  
- 在關聯 End 中所執行的作業相關資訊，例如刪除時的重疊顯示。 (選用)  
  
## <a name="example"></a>範例  

 下圖顯示包含兩個關聯 (`PublishedBy` 和 `WrittenBy`) 的概念模型。 `PublishedBy` 關聯的關聯 End 為 `Book` 和 `Publisher` 實體類型。 End 的多重性 `Publisher` 是一個 (1) 而 end 的多重性 `Book` 是許多 (\*) ，表示發行者會發行許多書籍，而一本書由一個發行者發行。  
  
 ![包含三種實體類型的範例模型](./media/association-end/example-model-three-entity-types.gif)  
  
 ADO.NET Entity Framework 會使用 (DSL) 稱為概念結構定義語言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 來定義概念模型的特定領域語言。 下列的 CSDL 會定義上圖顯示的 `PublishedBy` 關聯。 請注意，各個關聯 End 的類型、名稱和多重性是由 XML 屬性 (分別為 `Type`、`Role` 和 `Multiplicity` 屬性) 指定的。 關於針對其中一端執行之作業的選擇性資訊會在 XML 項目 (`OnDelete` 項目) 中指定。 在此情況中，如果刪除發行者，也會刪除所有相關的書籍。  
  
 [!code-xml[EDM_Example_Model#AssociationEnd](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#associationend)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
