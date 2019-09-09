---
title: 關聯 End 多重性
ms.date: 03/30/2017
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
ms.openlocfilehash: cdcf69e7118620b2f8febd02d7695d429bf8cc2c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786940"
---
# <a name="association-end-multiplicity"></a>關聯 End 多重性
*關聯 end 多重性*會定義可位於[關聯](association-type.md)一端的[實體類型](entity-type.md)實例數目。  
  
 關聯 End 多重性可以具有下列其中一個值：  
  
- 一（1）：表示只有一個實體類型實例存在於關聯 end。  
  
- 零或一（0 ..1）：表示關聯 end 有零或一個實體類型實例。  
  
- many （\*）：表示關聯 end 有零個、一個或多個實體類型實例。  
  
 關聯通常以其關聯 End 多重性來區分。 例如，如果關聯的兩端具有多重性一（1）和多個（\*），則關聯稱為一對多關聯。 在下列範例中，`PublishedBy` 關聯集為一對多關聯 (一個發行者發行許多書籍，以及一本書籍由一個發行者發行)。 `WrittenBy` 關聯式多對多關聯 (一本書可以有多位作者，一位作者可以撰寫許多本書)。  
  
## <a name="example"></a>範例  
 下圖顯示包含兩個關聯 (`PublishedBy` 和 `WrittenBy`) 的概念模型。 `PublishedBy` 關聯的關聯 End 為 `Book` 和 `Publisher` 實體類型。 `Publisher` End 的多重性是一（1），而`Book` end 的多重性則是多個（\*）。  
  
 ![具有三個實體類型的範例模型](./media/association-end-multiplicity/example-model-three-entity-types.gif)  
  
 ADO.NET Entity Framework 會使用稱為概念結構定義語言（[CSDL](./ef/language-reference/csdl-specification.md)）的特定領域語言（DSL）來定義概念模型。 下列 CSDL 定義上圖中的 `PublishedBy` 關聯。  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
