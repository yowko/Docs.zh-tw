---
title: "實體集 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 59ec6ab0-88e5-4d25-b112-7a4eccbe61f0
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 實體集
「*實體集*」\(Entity Set\) 是[實體類型](../../../../docs/framework/data/adonet/entity-type.md)執行個體及衍生自該實體類型之任何型別執行個體的邏輯容器。  \(如需有關衍生型別的詳細資訊，請參閱[實體資料模型：繼承](../../../../docs/framework/data/adonet/entity-data-model-inheritance.md)\)。實體類型和實體集之間的關聯性，類似關聯式資料表中資料行和資料列的關聯性：實體類型和資料行一樣描述資料結構，而實體集則和資料表一樣包含指定結構的執行個體。  實體集不是資料模型建構，也就是說，它不會描述資料結構。  反之，實體集會提供建構，讓裝載或儲存環境 \(例如 Common Language Runtime 或 SQL Server 資料庫\) 群組實體類型執行個體，以將其對應至資料存放區。  
  
 實體集是在[實體容器](../../../../docs/framework/data/adonet/entity-container.md)中定義的，此實體容器是[實體集](../../../../docs/framework/data/adonet/association-set.md)和關聯集的邏輯群組。  
  
 實體類型執行個體若要存在於實體集中，下列條件必須為 true：  
  
-   執行個體的類型必須與該實體集所依據的實體類型相同，或者執行個體的型別為該實體類型的子類型。  
  
-   執行個體的[實體索引鍵](../../../../docs/framework/data/adonet/entity-key.md)在實體集內是唯一的。  
  
-   執行個體不存在於任何其他實體集中。  
  
    > [!NOTE]
    >  您可以使用相同的實體類型定義多個實體集，但指定實體類型的執行個體只能存在於一個實體集中。  
  
 您不需定義概念模型中每個實體類型的實體集。  
  
## 範例  
 下圖顯示包含三種實體類型 \(`Book`、`Publisher` 和 `Author`\) 的概念模型。  
  
 ![範例模型](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 下圖顯示以前述概念模型為基礎的兩個實體集 \(`Books` 和 `Publishers`\)，以及一個關聯集 `PublishedBy`\)。  `Books` 實體集中的 Bi 代表執行階段時的 `Book` 實體類型執行個體。  同樣地，Pj 則代表 `Publishers` 實體集中的 `Publisher` 執行個體。  BiPj 代表 `PublishedBy` 關聯集內的 `PublishedBy` 關聯執行個體。  
  
 ![設定範例](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) 會使用稱為概念結構定義語言 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) 的特定定義域語言 \(DSL\) 來定義概念模型。  下列 CSDL 定義實體容器，上述概念模型中的每個實體類型皆具有一個實體集。  請注意，每個實體集名稱和實體類型都是使用 XML 屬性定義的。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 您可以定義每個類型的多重實體集 \(MEST\)。  下列 CSDL 所定義的實體容體具有兩個 `Book` 實體類型的實體集：  
  
 [!code-xml[EDM_Example_Model#MESTExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#mestexample)]  
  
## 請參閱  
 [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)