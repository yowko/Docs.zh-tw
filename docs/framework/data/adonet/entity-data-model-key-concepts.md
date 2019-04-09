---
title: 實體資料模型索引鍵概念
ms.date: 03/30/2017
ms.assetid: c635a16d-6674-45aa-9344-dcb7df992bab
ms.openlocfilehash: 2efa54b6bd656129812cc9dd7c2ce38a4fb2a89a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59074441"
---
# <a name="entity-data-model-key-concepts"></a>實體資料模型索引鍵概念
Entity Data Model (EDM) 來描述資料結構會使用三個主要概念：*實體類型*，*關聯型別*，並*屬性*。 描述任何 EDM 實作中的資料結構時，這些是最重要的概念。  
  
## <a name="entity-type"></a>實體類型  
 [實體類型](../../../../docs/framework/data/adonet/entity-type.md)是描述實體資料模型的資料結構的基本建置組塊。 在概念模型中，實體類型建構自[屬性](../../../../docs/framework/data/adonet/property.md)和描述結構的最上層概念，例如客戶和訂單的商務應用程式。 電腦程式中的類別定義是類別執行個體的範本，同樣地，實體類型也是實體的範本。 實體代表特定的物件 (例如特定的客戶或訂單)。 每個實體必須有唯一[實體索引鍵](../../../../docs/framework/data/adonet/entity-key.md)內[實體集](../../../../docs/framework/data/adonet/entity-set.md)。  實體集是特定實體類型的執行個體集合。 實體集 (和[關聯集會](../../../../docs/framework/data/adonet/association-set.md)) 中時，會以邏輯方式分組[實體容器](../../../../docs/framework/data/adonet/entity-container.md)。  
  
 實體類型支援繼承：也就是說，一個實體類型可以衍生自另一個實體類型。 如需詳細資訊，請參閱[實體資料模型：繼承](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)。  
  
## <a name="association-type"></a>關聯型別  
 [關聯型別](../../../../docs/framework/data/adonet/association-type.md)（亦稱為關聯） 是描述實體資料模型中的關聯性的基本建置組塊。 在概念模型中，關聯 (association) 代表兩個實體類型 (例如 Customer 和 Order) 之間的關聯性 (relationship)。 每個關聯具有兩個[關聯 end](../../../../docs/framework/data/adonet/association-end.md)指定關聯中相關的實體類型。 每個關聯 end 也指定了[關聯 end 多重性](../../../../docs/framework/data/adonet/association-end-multiplicity.md)，指出可在該關聯 end 的實體數目。 關聯 End 多重性的值可以是一 (0)、零或一 (0..1)，或許多 (*)。 您可以透過位於關聯某一端的實體[導覽屬性](../../../../docs/framework/data/adonet/navigation-property.md)，或透過外部索引鍵，如果實體類型上公開。 如需詳細資訊，請參閱 <<c0> [ 外部索引鍵屬性](../../../../docs/framework/data/adonet/foreign-key-property.md)。  
  
 在應用程式中，關聯的執行個體代表特定的關聯 (例如 Customer 和 Order 執行個體之間的關聯)。 關聯執行個體會以邏輯方式分組[關聯集](../../../../docs/framework/data/adonet/association-set.md)。 關聯集 (和[實體集](../../../../docs/framework/data/adonet/entity-set.md)) 中時，會以邏輯方式分組[實體容器](../../../../docs/framework/data/adonet/entity-container.md)。  
  
## <a name="property"></a>屬性  
 [實體類型](../../../../docs/framework/data/adonet/entity-type.md)包含[屬性](../../../../docs/framework/data/adonet/property.md)，定義其結構和特性。 例如，一個 Customer 實體類型可能會有 CustomerId、Name 和 Address 之類的屬性。  
  
 概念模型中的屬性類似電腦程式中在類別定義的屬性。 如同類別上的屬性可定義類別的圖形並包含關於物件的資訊，概念模型的屬性可定義實體類別的圖形，並包含關於實體類型執行個體的資訊。  
  
 屬性可以包含基底資料 (例如字串、整數或布林值) 或結構化資料 (例如複雜類型)。 如需詳細資訊，請參閱[實體資料模型：基本資料型別](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)。  
  
## <a name="representations-of-a-conceptual-model"></a>概念模型的表現方式  
 A*概念模型*是以實體和關聯性的某些資料結構的特定表示法。 表示概念模型的方法之一就是使用圖表。 下圖代表包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 及兩種關聯 (`PublishedBy` 和 `WrittenBy`) 的概念模型；  
  
 ![顯示具有三種實體類型的概念模型的圖表。](./media/entity-data-model-key-concepts/conceptual-model-entity-types-associations.gif)  
  
 不過，若要使用這種表示方法傳達某些與模型相關的詳細資料，則會有些缺點。 例如，圖表中不會顯示屬性和實體集資訊。 以特定領域語言 (DSL) 傳達的概念模型豐富度會更清楚。 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為 XML 型 DSL*概念結構定義語言*([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。 以下是上圖所示之概念模型的 CSDL 定義：  
  
 [!code-xml[EDM_Example_Model#EDMExampleCSDL](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#edmexamplecsdl)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)
