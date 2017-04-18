---
title: "參考完整性條件約束 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d3ba44b-4302-40d8-a7a9-62932e0395e5
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 參考完整性條件約束
實體資料模型 \(EDM\) 中的「*參考完整性條件約束*」\(Referential Integrity Constraint\) 類似於關聯式資料庫中的參考完整性條件約束。  資料庫資料表中的資料行可以參考另一個資料表的主要索引鍵，同樣地，[實體類型](../../../../docs/framework/data/adonet/entity-type.md)的[屬性](../../../../docs/framework/data/adonet/property.md)也可以參考另一個實體類型的[實體索引鍵](../../../../docs/framework/data/adonet/entity-key.md)。  參考的實體類型稱為條件約束的「*主要端點*」\(Principal End\)。  參考主要端點的實體類型稱為條件約束的「*相依端點*」\(Dependent End\)。  
  
 參考完整性條件約束定義為兩個實體類型之[關聯](../../../../docs/framework/data/adonet/association-type.md)一部分。  參考完整性條件約束的定義指定下列資訊：  
  
-   條件約束的主要端點。  \(實體類型，相依端點會參考其實體索引鍵。\)  
  
-   主要端點的實體索引鍵。  
  
-   條件約束的相依端點。  \(實體類型，具有參考主要端點之實體索引鍵的屬性。\)  
  
-   相依端點的參考屬性。  
  
 在 EDM 中，參考完整性條件約束的目的在於確保有效的關聯永遠存在。  如需詳細資訊，請參閱[外部索引鍵屬性](../../../../docs/framework/data/adonet/foreign-key-property.md)。  
  
## 範例  
 下圖顯示包含兩個關聯 \(`WrittenBy` 和 `PublishedBy`\) 的概念模型。  `Book` 實體類型具有屬性 `PublisherId`，當您定義 `PublishedBy` 關聯的參考完整性條件約束時，此屬性會參考 `Publisher` 實體類型的實體索引鍵。  
  
 ![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) 會使用稱為概念結構定義語言 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) 的特定定義域語言 \(DSL\) 來定義概念模型。  下列 CSDL 會對上述概念模型中的 `PublishedBy` 關聯定義參考完整性條件約束。  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## 請參閱  
 [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)