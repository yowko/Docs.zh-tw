---
title: Association Set - 關聯集
ms.date: 03/30/2017
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
ms.openlocfilehash: 58d8794a21cc37ab84386c820b192fb29946095c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91153426"
---
# <a name="association-set"></a>Association Set - 關聯集

*關聯集*是相同類型之[關聯](association-type.md)實例的邏輯容器。 關聯集不是資料模型建構，也就是說，它不會描述資料或關聯性的結構。 反之，關聯集會提供建構，讓裝載或儲存環境 (例如 Common Language Runtime 或 SQL Server 資料庫) 群組關聯執行個體，以將其對應至資料存放區。  
  
 關聯集是在實體容器中定義的，而 [實體容器](entity-container.md)是 [實體集](entity-set.md) 和關聯集的邏輯群組。  
  
 關聯集的定義包含下列資訊：  
  
- 關聯集名稱。 (必要)  
  
- 將包含執行個體的關聯。 (必要)  
  
- 兩個 [關聯集 end](association-set-end.md)。  
  
## <a name="example"></a>範例  

 下圖顯示包含兩個關聯 (`PublishedBy` 和 `WrittenBy`) 的概念模型。 雖然圖中並未提供關聯集的相關資訊，但下圖會顯示以此模型為基礎的關聯集和實體集範例。  
  
 ![包含三種實體類型的範例模型](./media/association-set/example-model-three-entity-types.gif)  
  
 下列範例顯示以前述概念模型為基礎的一個關聯集 (`PublishedBy`) 和兩個實體集 (`Books` 和 `Publishers`)。 `Books`實體集中的 Bi 代表 `Book` 執行時間的實體型別實例。 同樣地，Pj `Publisher` 則代表 `Publishers` 實體集中的實例。 BiPj 代表 `PublishedBy` 關聯集中關聯的實例 `PublishedBy` 。  
  
 ![顯示集合範例的螢幕擷取畫面。](./media/association-set/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](./ef/index.md)會使用 (DSL) 稱為概念結構定義語言 ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) 來定義概念模型的特定領域語言。 下列 CSDL 定義上圖所示之實體實體容器，每個關聯具有一個關聯集。 請注意，每個關聯集的名稱和關聯都是使用 XML 屬性定義的。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 您可以定義每個關聯的多個關聯集，只要沒有兩個關聯集共用 [關聯集 end](association-set-end.md)。 下列 CSDL 可定義具有兩個 `WrittenBy` 關聯之關聯集的實體容體。 請注意，`Book` 和 `Author` 實體類型皆定義了多個實體集，且所有關聯集皆不共用關聯集 End。  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](entity-data-model-key-concepts.md)
- [實體資料模型](entity-data-model.md)
- [外部索引鍵屬性](foreign-key-property.md)
