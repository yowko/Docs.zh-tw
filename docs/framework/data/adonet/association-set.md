---
title: "關聯集 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a65247b6-ce59-44ea-974c-14ae20a7995f
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 關聯集
「*關聯集*」\(Association Set\) 是相同類型之[關聯](../../../../docs/framework/data/adonet/association-type.md)執行個體的邏輯容器。  關聯集不是資料模型建構，也就是說，它不會描述資料或關聯性的結構。  反之，關聯集會提供建構，讓裝載或儲存環境 \(例如 Common Language Runtime 或 SQL Server 資料庫\) 群組關聯執行個體，以將其對應至資料存放區。  
  
 關聯集是在[實體容器](../../../../docs/framework/data/adonet/entity-container.md)中定義的，此實體容器是[實體集](../../../../docs/framework/data/adonet/entity-set.md)和關聯集的邏輯群組。  
  
 關聯集的定義包含下列資訊：  
  
-   關聯集名稱。  \(必要項\)  
  
-   將包含執行個體的關聯。  \(必要項\)  
  
-   兩個[關聯集 End](../../../../docs/framework/data/adonet/association-set-end.md)。  
  
## 範例  
 下圖顯示包含兩個關聯 \(`PublishedBy` 和 `WrittenBy`\) 的概念模型。  雖然圖中並未提供關聯集的相關資訊，但下圖會顯示以此模型為基礎的關聯集和實體集範例。  
  
 ![範例模型](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 下列範例顯示以前述概念模型為基礎的一個關聯集 \(`PublishedBy`\) 和兩個實體集 \(`Books` 和 `Publishers`\)。  `Books` 實體集中的 Bi 代表執行階段時的 `Book` 實體類型執行個體。  同樣地，Pj 則代表 `Publishers` 實體集中的 `Publisher` 執行個體。  BiPj 代表 `PublishedBy` 關聯集內的 `PublishedBy` 關聯執行個體。  
  
 ![設定範例](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) 會使用稱為概念結構定義語言 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) 的特定定義域語言 \(DSL\) 來定義概念模型。  下列 CSDL 定義上圖所示之實體實體容器，每個關聯具有一個關聯集。  請注意，每個關聯集的名稱和關聯都是使用 XML 屬性定義的。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
 每個關聯可以定義多個屬性集，前提是所有關聯集皆不共用[關聯集 End](../../../../docs/framework/data/adonet/association-set-end.md)。  下列 CSDL 可定義具有兩個 `WrittenBy` 關聯之關聯集的實體容體。  請注意，`Book` 和 `Author` 實體類型皆定義了多個實體集，且所有關聯集皆不共用關聯集 End。  
  
 [!code-xml[EDM_Example_Model#MultipleAssociationSets](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#multipleassociationsets)]  
  
## 請參閱  
 [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)   
 [外部索引鍵屬性](../../../../docs/framework/data/adonet/foreign-key-property.md)