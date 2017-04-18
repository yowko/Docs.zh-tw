---
title: "關聯集 End | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fe4bf1d3-047a-4a37-98c5-a66e70811346
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 關聯集 End
「*關聯集 End*」\(Association Set End\) 可識別[關聯集](../../../../docs/framework/data/adonet/association-set.md) End 的[實體類型](../../../../docs/framework/data/adonet/entity-type.md)和[實體集](../../../../docs/framework/data/adonet/entity-set.md)。  關聯集 End 會定義為關聯集的部分。一個關聯集必須擁有兩個關聯集 End。  
  
 關聯集 End 定義包含下列資訊：  
  
-   關聯集中相關的其中一個屬性類型。  \(必要項\)  
  
-   關聯集中相關實體類型的實體集。  \(必要項\)  
  
## 範例  
 下圖顯示包含兩個關聯 \(`WrittenBy` 和 `PublishedBy`\) 的概念模型。  
  
 ![範例模型](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 下圖顯示以前述概念模型為基礎的一個關聯集 \(`PublishedBy`\) 和兩個實體集 \(`Books` 和 `Publishers`\)。  關聯集 End 為 `Books` 和 `Publishers` 實體集。  `Books` 實體集中的 Bi 代表執行階段時的 `Book` 實體類型執行個體。  同樣地，Pj 則代表 `Publishers` 實體集中的 `Publisher` 執行個體。  BiPj 代表 `PublishedBy` 關聯集內的 `PublishedBy` 關聯執行個體。  
  
 ![設定範例](../../../../docs/framework/data/adonet/media/setsexample.gif "SetsExample")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) 會使用稱為概念結構定義語言 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) 的 DSL 來定義概念模型。  下列 CSDL 定義上圖所示之實體實體容器，每個關聯具有一個關聯集。  請注意，關聯集 End 會定義為每個關聯集定義的一部分。  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## 請參閱  
 [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)