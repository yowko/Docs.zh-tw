---
title: 關聯類型
ms.date: 03/30/2017
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
ms.openlocfilehash: 7fbdc0316b1f9fd0bb282fd466857b1426c41df1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583724"
---
# <a name="association-type"></a>關聯類型
*關聯型別*（亦稱為關聯） 是描述 Entity Data Model (EDM) 中的關聯性的基本建置組塊。 在概念模型中，關聯代表兩個關聯性[實體類型](../../../../docs/framework/data/adonet/entity-type.md)(例如`Customer`和`Order`)。 在應用程式中，關聯的執行個體代表特定的關聯 (例如 `Customer` 執行個體和 `Order` 執行個體之間的關聯)。 關聯執行個體會以邏輯方式分組[關聯集](../../../../docs/framework/data/adonet/association-set.md)。  
  
 關聯定義包含下列資訊：  
  
- 唯一名稱。 (必要項)  
  
- 兩個[關聯 end](../../../../docs/framework/data/adonet/association-end.md)，一個用於關聯性中的每個實體類型。 (必要項)  
  
    > [!NOTE]
    >  一個關聯 (association) 不能代表兩個實體型別以上的關聯性 (relationship)。 不過，關聯可以為其每一個關聯 End 指定同樣的實體型別，以定義自我關聯性。  
  
- A[參考完整性條件約束](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)。 (選擇項)  
  
 每個關聯 end 必須指定[關聯 end 多重性](../../../../docs/framework/data/adonet/association-end-multiplicity.md)表示可以是位於關聯某一端的實體類型執行個體數目。 關聯 end 多重性可以有值為一 (1)、 零或一個 (0..1)，或多個 (\*)。 您可以透過位於關聯某一端的實體類型執行個體[導覽屬性](../../../../docs/framework/data/adonet/navigation-property.md)或外部索引鍵，如果實體類型上公開。 如需詳細資訊，請參閱[實體資料模型：外部索引鍵](../../../../docs/framework/data/adonet/foreign-key-property.md)。  
  
## <a name="example"></a>範例  
 下圖顯示包含兩個關聯 (`PublishedBy` 和 `WrittenBy`) 的概念模型。 `PublishedBy` 關聯的關聯 End 為 `Book` 和 `Publisher` 實體類型。 端點的多重性`Publisher`結尾是一 (1) 和端點的多重性`Book`端是許多 (\*)，表示一個發行者發行許多書籍，以及一本書籍由一個發行者發行。  
  
 ![具有三種實體類型的範例模型](./media/association-type/example-model-three-entity-types.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。 下列 CSDL 定義上圖中的 `PublishedBy` 關聯。  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)
