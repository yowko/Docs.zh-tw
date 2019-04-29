---
title: Entity Type - 實體類型
ms.date: 03/30/2017
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
ms.openlocfilehash: 026b0aef7cf2de8fe222721191afa459859701ee
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61667170"
---
# <a name="entity-type"></a>Entity Type - 實體類型
*實體類型*是描述與 Entity Data Model (EDM) 中的資料結構的基本建置組塊。 在概念模型中，實體類型代表最上層概念的結構，例如客戶或訂單。 實體類型是實體類型執行個體的範本。 每個範本包含下列資訊：  
  
- 唯一名稱。 (必要項。)  
  
- [實體索引鍵](../../../../docs/framework/data/adonet/entity-key.md)由一或多個屬性所定義。 (必要項。)  
  
- 資料的形式[屬性](../../../../docs/framework/data/adonet/property.md)。 (選擇性。)  
  
- [導覽屬性](../../../../docs/framework/data/adonet/navigation-property.md)可讓不同的瀏覽[結束](../../../../docs/framework/data/adonet/association-end.md)的[關聯](../../../../docs/framework/data/adonet/association-type.md)另一端。 (選擇項)  
  
 在應用程式中，實體類型的執行個體代表特定的物件 (例如特定的客戶或訂單)。 每個實體類型執行個體必須具有唯一[實體索引鍵](../../../../docs/framework/data/adonet/entity-key.md)內[實體集](../../../../docs/framework/data/adonet/entity-set.md)。  
  
 如果兩個實體類型執行個體屬於相同類型，而且索引鍵的值也相同，則會將這兩個執行個體視為相等。  
  
## <a name="example"></a>範例  
 下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型：  
  
 ![具有三種實體類型的範例模型](./media/entity-type/example-model-three-entity-types.gif)  
  
 請注意，構成實體索引鍵的每個實體類型屬性皆加註「(索引鍵)」。  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。 下列 CSDL 定義上圖所顯示的 `Book` 實體類型：  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)
- [facet](../../../../docs/framework/data/adonet/facet.md)
