---
title: "關聯 End 多重性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 340926ee-aefb-4bef-92cc-453e5251fd03
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# 關聯 End 多重性
「*關聯 End 多重性*」\(Association end multiplicity\) 定義可在 [關聯](../../../../docs/framework/data/adonet/association-type.md) 其中一端定義之[實體類型](../../../../docs/framework/data/adonet/entity-type.md)執行個體數目。  
  
 關聯 End 多重性可以具有下列其中一個值：  
  
-   一 \(1\)：表示關聯 End 只存在唯一的一個實體類型執行個體。  
  
-   零或一 \(0..1\)：表示關聯 End 具有零個或一個實體類型執行個體。  
  
-   許多 \(\*\)：表示關聯 End 具有零個、一個或多個實體類型執行個體。  
  
 關聯通常以其關聯 End 多重性來區分。  例如，如果關聯的 End 具有多重性一 \(0\) 和許多 \(\*\)，則該關聯稱為一對多關聯。  在下列範例中，`PublishedBy` 關聯集為一對多關聯 \(一個發行者發行許多書籍，以及一本書籍由一個發行者發行\)。  `WrittenBy` 關聯式多對多關聯 \(一本書可以有多位作者，一位作者可以撰寫許多本書\)。  
  
## 範例  
 下圖顯示包含兩個關聯 \(`PublishedBy` 和 `WrittenBy`\) 的概念模型。  `PublishedBy` 關聯的關聯 End 為 `Book` 和 `Publisher` 實體類型。  `Publisher` 端的多重性是一 \(1\)，而 `Book` 端的多重性則是多個 \(\*\)。  
  
 ![範例模型](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 ADO.NET Entity Framework 會使用名為概念結構描述定義語言 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) 的網域特定定義域語言 \(DSL\) 來定義概念模型。  下列 CSDL 定義上圖中的 `PublishedBy` 關聯。  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## 請參閱  
 [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)