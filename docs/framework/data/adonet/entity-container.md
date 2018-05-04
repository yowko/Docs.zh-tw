---
title: Entity Container - 實體容器
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: ed2123629c61b179e07e86effa0c39d9a3222b62
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="entity-container"></a>Entity Container - 實體容器
*實體容器*是邏輯群組[實體集](../../../../docs/framework/data/adonet/entity-set.md)，[關聯集](../../../../docs/framework/data/adonet/association-set.md)，和[函式匯入](../../../../docs/framework/data/adonet/model-declared-function.md)。  
  
 在概念模型中定義的實體容器，下列必須為 true：  
  
-   每個概念模型中至少必須定義一個實體容器。  
  
-   每個概念模型中的實體容器必須要有一個唯一的名稱。  
  
 實體容器可以定義使用一或多個命名空間中定義之實體類型或關聯的實體集或關聯集。 如需詳細資訊，請參閱[實體資料模型： 命名空間](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md)。  
  
## <a name="example"></a>範例  
 下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。  如需詳細資訊，請參閱下一個範例。  
  
 ![範例模型](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 雖然圖表並未提供實體容器資訊，但概念模型必須定義實體容器。 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的 DSL ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。 下列 CSDL 會定義上圖所示之概念模型的實體容器。 請注意，實體容器的名稱是在 XML 屬性中定義的。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>另請參閱  
 [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)
