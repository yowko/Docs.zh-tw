---
title: 關聯 End 多重性
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: 6d1b31c5b5ead701fbe808b91d7191fb84dc86c8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54502633"
---
# <a name="association-end-multiplicity"></a>關聯 End 多重性
*關聯 end 多重性*定義的數目[實體類型](../../../../docs/framework/data/adonet/entity-type.md)其中一端的可執行個體[關聯](../../../../docs/framework/data/adonet/association-type.md)。  
  
 關聯 End 多重性可以具有下列其中一個值：  
  
-   一 (1):指出該只有一個實體類型執行個體存在於關聯 end。  
  
-   零或一 (0..1):表示零個或一個實體類型執行個體存在於關聯 end。  
  
-   許多 （*）：表示零個、 一個或多個實體類型執行個體存在於關聯 end。  
  
 關聯通常以其關聯 End 多重性來區分。 例如，如果關聯的 End 具有多重性一 (0) 和許多 (*)，則該關聯稱為一對多關聯。 在下列範例中，`PublishedBy` 關聯集為一對多關聯 (一個發行者發行許多書籍，以及一本書籍由一個發行者發行)。 `WrittenBy` 關聯式多對多關聯 (一本書可以有多位作者，一位作者可以撰寫許多本書)。  
  
## <a name="example"></a>範例  
 下圖顯示包含兩個關聯 (`PublishedBy` 和 `WrittenBy`) 的概念模型。 `PublishedBy` 關聯的關聯 End 為 `Book` 和 `Publisher` 實體類型。 `Publisher` 端的多重性是一 (1)，而 `Book` 端的多重性則是多個 (*)。  
  
 ![範例模型](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 ADO.NET Entity Framework 會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。 下列 CSDL 定義上圖中的 `PublishedBy` 關聯。  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>另請參閱
- [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)
