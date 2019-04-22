---
title: Association Set - 關聯集
ms.date: 03/30/2017
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
ms.openlocfilehash: af9297d9c827b12ed8611e99930234511f7f661c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59204480"
---
# <a name="association-set"></a>Association Set - 關聯集
*關聯集*是邏輯容器[關聯](../../../../docs/framework/data/adonet/association-type.md)相同類型的執行個體。 關聯集不是資料模型建構，也就是說，它不會描述資料或關聯性的結構。 反之，關聯集會提供建構，讓裝載或儲存環境 (例如 Common Language Runtime 或 SQL Server 資料庫) 群組關聯執行個體，以將其對應至資料存放區。  
  
 關聯集內定義[實體容器](../../../../docs/framework/data/adonet/entity-container.md)，這是邏輯分組[實體集](../../../../docs/framework/data/adonet/entity-set.md)和關聯集。  
  
 關聯集的定義包含下列資訊：  
  
-   關聯集名稱。 (必要項)  
  
-   將包含執行個體的關聯。 (必要項)  
  
-   兩個[關聯集 end](../../../../docs/framework/data/adonet/association-set-end.md)。  
  
## <a name="example"></a>範例  
 下圖顯示包含兩個關聯 (`PublishedBy` 和 `WrittenBy`) 的概念模型。 雖然圖中並未提供關聯集的相關資訊，但下圖會顯示以此模型為基礎的關聯集和實體集範例。  
  
 ![具有三種實體類型的範例模型](./media/association-set/example-model-three-entity-types.gif)  
  
 下列範例顯示以前述概念模型為基礎的一個關聯集 (`PublishedBy`) 和兩個實體集 (`Books` 和 `Publishers`)。 在 bi`Books`實體集代表的執行個體`Book`在執行階段的實體類型。 同樣地，Pj 代表`Publisher`執行個體中`Publishers`實體集。 BiPj 表示的執行個體`PublishedBy`中的關聯`PublishedBy`關聯集。  
  
 ![如果螢幕擷取畫面顯示設定範例。](./media/association-set/sets-example-association.gif)  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md)會使用稱為概念結構定義語言的特定領域語言 (DSL) ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) 來定義概念模型。 下列 CSDL 定義上圖所示之實體實體容器，每個關聯具有一個關聯集。 請注意，每個關聯集的名稱和關聯都是使用 XML 屬性定義的。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 您可定義每個關聯，只要沒有兩個關聯集共用的多個關聯集[關聯集 end](../../../../docs/framework/data/adonet/association-set-end.md)。 下列 CSDL 可定義具有兩個 `WrittenBy` 關聯之關聯集的實體容體。 請注意，`Book` 和 `Author` 實體類型皆定義了多個實體集，且所有關聯集皆不共用關聯集 End。  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## <a name="see-also"></a>另請參閱

- [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)
- [外部索引鍵屬性](../../../../docs/framework/data/adonet/foreign-key-property.md)
