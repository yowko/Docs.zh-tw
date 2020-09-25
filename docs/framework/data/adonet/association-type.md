---
title: 關聯類型
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: 6f6eb91d4f292c7e98b8c9a1d814ed6bf71b7370
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198752"
---
# <a name="association-type"></a>關聯類型

*關聯類型* (也稱為關聯) 是在實體資料模型 (EDM) 中描述關聯性的基本組建區塊。 在概念模型中，關聯代表兩個 [實體類型](entity-type.md) 之間的關聯性 (例如 `Customer` 和 `Order`) 。 在應用程式中，關聯的執行個體代表特定的關聯 (例如 `Customer` 執行個體和 `Order` 執行個體之間的關聯)。 關聯實例會在邏輯上群組于 [關聯集中](association-set.md)。  
  
 關聯定義包含下列資訊：  
  
- 唯一名稱。 (必要)  
  
- 兩個 [關聯會結束，關聯](association-end.md)性中的每個實體類型各一個。 (必要)  
  
    > [!NOTE]
    > 一個關聯 (association) 不能代表兩個實體型別以上的關聯性 (relationship)。 不過，關聯可以為其每一個關聯 End 指定同樣的實體型別，以定義自我關聯性。  
  
- [參考完整性條件約束](referential-integrity-constraint.md)。 (選用)  
  
 每個關聯端都必須指定 [關聯 end 多重性](association-end-multiplicity.md) ，以指出可以位於關聯之一端的實體類型實例數目。 關聯 end 多重性可以有一個 (1) 、零個或一個 (0 ..1) 或許多 () 的值。 \* 您可以透過 [導覽屬性](navigation-property.md) 或外鍵來存取關聯某一端的實體類型實例（如果它們是在實體類型上公開）。 如需詳細資訊，請參閱 [實體資料模型：外鍵](foreign-key-property.md)。  
  
## <a name="example"></a>範例  

 下圖顯示包含兩個關聯 (`PublishedBy` 和 `WrittenBy`) 的概念模型。 `PublishedBy` 關聯的關聯 End 為 `Book` 和 `Publisher` 實體類型。 End 的多重性 `Publisher` 是一個 (1) 而 end 的多重性 `Book` 是許多 (\*) ，表示發行者會發行許多書籍，而一本書由一個發行者發行。  
  
 ![包含三種實體類型的範例模型](./media/association-type/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md)會使用 (DSL) 稱為概念結構定義語言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 來定義概念模型的特定領域語言。 下列 CSDL 定義上圖中的 `PublishedBy` 關聯。  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
