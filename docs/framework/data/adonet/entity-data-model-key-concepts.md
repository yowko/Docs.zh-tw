---
title: 實體資料模型索引鍵概念
ms.date: 03/30/2017
ms.assetid: c635a16d-6674-45aa-9344-dcb7df992bab
ms.openlocfilehash: d020de65ff64d93c0ea925b71e5f1546eb4402aa
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191758"
---
# <a name="entity-data-model-key-concepts"></a>實體資料模型索引鍵概念

實體資料模型 (EDM) 會使用三個主要概念來描述資料的結構： *實體類型*、 *關聯型*別和 *屬性*。 描述任何 EDM 實作中的資料結構時，這些是最重要的概念。  
  
## <a name="entity-type"></a>實體類型  

 [實體類型](entity-type.md)是用來描述資料結構與實體資料模型的基本組建區塊。 在概念模型中，實體類型是由 [屬性](property.md) 所構成，並描述最上層概念的結構，例如商務應用程式中的客戶和訂單。 電腦程式中的類別定義是類別執行個體的範本，同樣地，實體類型也是實體的範本。 實體代表特定的物件 (例如特定的客戶或訂單)。 每個實體在[實體集](entity-set.md)內都必須有唯一的[實體索引鍵](entity-key.md)。  實體集是特定實體類型的執行個體集合。 實體集 (和 [關聯集](association-set.md)) 會以邏輯方式分組在 [實體容器](entity-container.md)中。  
  
 實體類型支援繼承：也就是說，一個實體類型可以衍生自另一個實體類型。 如需詳細資訊，請參閱 [實體資料模型：繼承](entity-data-model-inheritance.md)。  
  
## <a name="association-type"></a>關聯型別  

 [關聯類型](association-type.md) (也稱為關聯) 是用來描述實體資料模型中關聯性的基本組建區塊。 在概念模型中，關聯 (association) 代表兩個實體類型 (例如 Customer 和 Order) 之間的關聯性 (relationship)。 每個關聯都有兩個 [關聯 end](association-end.md) ，可指定關聯中相關的實體類型。 每個關聯 end 也會指定 [關聯 end 多重性](association-end-multiplicity.md) ，以表示可以位於關聯之一端的實體數目。 關聯 end 多重性可以有一個 (1) 、零個或一個 (0 ..1) 或許多 () 的值。 \* 關聯某一端的實體可透過 [導覽屬性](navigation-property.md)來存取，或在實體類型上公開時，透過外鍵來存取。 如需詳細資訊，請參閱 [外鍵屬性](foreign-key-property.md)。  
  
 在應用程式中，關聯的執行個體代表特定的關聯 (例如 Customer 和 Order 執行個體之間的關聯)。 關聯實例會在邏輯上群組于 [關聯集中](association-set.md)。 關聯集 (和 [實體集](entity-set.md)) 會以邏輯方式分組在 [實體容器](entity-container.md)中。  
  
## <a name="property"></a>屬性  

 [實體類型](entity-type.md) 包含定義其結構和特性的 [屬性](property.md) 。 例如，一個 Customer 實體類型可能會有 CustomerId、Name 和 Address 之類的屬性。  
  
 概念模型中的屬性類似電腦程式中在類別定義的屬性。 如同類別上的屬性可定義類別的圖形並包含關於物件的資訊，概念模型的屬性可定義實體類別的圖形，並包含關於實體類型執行個體的資訊。  
  
 屬性可以包含基底資料 (例如字串、整數或布林值) 或結構化資料 (例如複雜類型)。 如需詳細資訊，請參閱 [實體資料模型：基本資料類型](entity-data-model-primitive-data-types.md)。  
  
## <a name="representations-of-a-conceptual-model"></a>概念模型的表現方式  

 *概念模型*是某些資料結構的特定標記法，作為實體和關聯性。 表示概念模型的方法之一就是使用圖表。 下圖代表包含三種實體類型 (`Book`、`Publisher` 和 `Author`) 及兩種關聯 (`PublishedBy` 和 `WrittenBy`) 的概念模型；  
  
 ![顯示具有三個實體類型之概念模型的圖表。](./media/entity-data-model-key-concepts/conceptual-model-entity-types-associations.gif)  
  
 不過，若要使用這種表示方法傳達某些與模型相關的詳細資料，則會有些缺點。 例如，圖表中不會顯示屬性和實體集資訊。 以特定領域語言 (DSL) 傳達的概念模型豐富度會更清楚。 [ADO.NET Entity Framework](./ef/index.md)會使用名為*概念結構定義語言* ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 的 XML 型 DSL 來定義概念模型。 以下是上圖所示之概念模型的 CSDL 定義：  
  
 [!code-xml[EDM_Example_Model#EDMExampleCSDL](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#edmexamplecsdl)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型](entity-data-model.md)
