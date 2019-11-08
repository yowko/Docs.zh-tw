---
title: Entity Container - 實體容器
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: 0c194d86e6276c948a545f830e569cbc68f86a14
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737879"
---
# <a name="entity-container"></a>Entity Container - 實體容器
*實體容器*是[實體集](entity-set.md)、[關聯集](association-set.md)和函式匯[入](model-declared-function.md)的邏輯群組。  
  
 在概念模型中定義的實體容器，下列必須為 true：  
  
- 每個概念模型中至少必須定義一個實體容器。  
  
- 每個概念模型中的實體容器必須要有一個唯一的名稱。  
  
 實體容器可以定義使用一或多個命名空間中定義之實體類型或關聯的實體集或關聯集。 如需詳細資訊，請參閱[實體資料模型：命名空間](entity-data-model-namespaces.md)。  
  
## <a name="example"></a>範例  
 下圖顯示包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 的概念模型。  如需詳細資訊，請參閱下一個範例。  
  
 ![具有三個實體類型的範例模型](./media/entity-container/example-model-three-entity-types.gif)  
  
 雖然圖表並未提供實體容器資訊，但概念模型必須定義實體容器。 [ADO.NET Entity Framework](./ef/index.md)會使用稱為概念結構定義語言（[CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)）的 DSL 來定義概念模型。 下列 CSDL 會定義上圖所示之概念模型的實體容器。 請注意，實體容器的名稱是在 XML 屬性中定義的。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a>請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
