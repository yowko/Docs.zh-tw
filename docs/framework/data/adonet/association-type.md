---
title: 關聯類型
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: e1430e6255dce2bae6d82411db5d2a9f11f46e1a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738562"
---
# <a name="association-type"></a>關聯類型
*關聯類型*（也稱為關聯）是用來描述實體資料模型（EDM）中關聯性的基本建立區塊。 在概念模型中，關聯代表兩個[實體類型](entity-type.md)之間的關聯性（例如 `Customer` 和 `Order`）。 在應用程式中，關聯的執行個體代表特定的關聯 (例如 `Customer` 執行個體和 `Order` 執行個體之間的關聯)。 關聯實例會以邏輯方式分組在[關聯集](association-set.md)內。  
  
 關聯定義包含下列資訊：  
  
- 唯一名稱。 (必要項)  
  
- 兩個[關聯結束](association-end.md)，關係中的每個實體類型各一個。 (必要項)  
  
    > [!NOTE]
    > 一個關聯 (association) 不能代表兩個實體型別以上的關聯性 (relationship)。 不過，關聯可以為其每一個關聯 End 指定同樣的實體型別，以定義自我關聯性。  
  
- [參考完整性條件約束](referential-integrity-constraint.md)。 (選擇項)  
  
 每個關聯 end 都必須指定一個[關聯 end 多重性](association-end-multiplicity.md)，以指出可以在關聯一端的實體類型實例數目。 關聯 end 多重性的值可以是一（1）、零或一（0 ..1），或多個（\*）。 關聯的一端的實體型別實例可以透過[導覽屬性](navigation-property.md)或外鍵來存取（如果它們是在實體型別上公開）。 如需詳細資訊，請參閱[實體資料模型：外鍵](foreign-key-property.md)。  
  
## <a name="example"></a>範例  
 下圖顯示包含兩個關聯 (`PublishedBy` 和 `WrittenBy`) 的概念模型。 `PublishedBy` 關聯的關聯 End 為 `Book` 和 `Publisher` 實體類型。 `Publisher` end 的多重性是一（1），而 `Book` 結束的多重性則是多個（\*），表示發行者發行許多書籍，而書籍是由一個發行者發行。  
  
 ![具有三個實體類型的範例模型](./media/association-type/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md)會使用稱為概念結構定義語言（[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)）的特定領域語言（DSL）來定義概念模型。 下列 CSDL 定義上圖中的 `PublishedBy` 關聯。  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
