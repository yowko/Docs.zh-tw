---
title: Entity Type - 實體類型
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: efd3ea0972148e885d4b22b49040640539bb28cd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795127"
---
# <a name="entity-type"></a>Entity Type - 實體類型
*實體類型*是使用實體資料模型（EDM）描述資料結構的基本建立區塊。 在概念模型中，實體類型代表最上層概念的結構，例如客戶或訂單。 實體類型是實體類型執行個體的範本。 每個範本包含下列資訊：  
  
- 唯一名稱。 (必要項。)  
  
- 由一個或多個屬性所定義的[實體索引鍵](entity-key.md)。 (必要項。)  
  
- [屬性](property.md)形式的資料。 (選擇性。)  
  
- 允許從[關聯](association-type.md)[的一端導覽](association-end.md)至另一端的[導覽屬性](navigation-property.md)。 (選擇項)  
  
 在應用程式中，實體類型的執行個體代表特定的物件 (例如特定的客戶或訂單)。 實體類型的每個實例在[實體集](entity-set.md)內都必須有唯一的[實體索引鍵](entity-key.md)。  
  
 如果兩個實體類型執行個體屬於相同類型，而且索引鍵的值也相同，則會將這兩個執行個體視為相等。  
  
## <a name="example"></a>範例  
 下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型：  
  
 ![具有三個實體類型的範例模型](./media/entity-type/example-model-three-entity-types.gif)  
  
 請注意，構成實體索引鍵的每個實體類型屬性皆加註「(索引鍵)」。  
  
 [ADO.NET Entity Framework](./ef/index.md)會使用稱為概念結構定義語言（[CSDL](./ef/language-reference/csdl-specification.md)）的特定領域語言（DSL）來定義概念模型。 下列 CSDL 定義上圖所顯示的 `Book` 實體類型：  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
- [facet](facet.md)
