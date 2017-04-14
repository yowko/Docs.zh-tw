---
title: "外部索引鍵屬性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 23cb6729-544d-4f67-9ee7-44e8a6545587
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 外部索引鍵屬性
在包含另一個實體類型之[體實體索引鍵](../../../../docs/framework/data/adonet/entity-key.md)的[實體類型](../../../../docs/framework/data/adonet/entity-type.md)上，實體資料模型 \(EDM\) 中的「*外部索引鍵屬性*」\(Foreign key property\) 是基本型別[屬性](../../../../docs/framework/data/adonet/property.md) \(或基本型別屬性集\)。  
  
 外部索引鍵屬性類似關聯式資料庫中的外部索引鍵資料行。  外部索引鍵資料行在關聯式資料庫中建立資料表之間的關聯性，同樣地，概念模型中的外部索引鍵屬性則用於建立實體類型之間的[關聯](../../../../docs/framework/data/adonet/association-type.md)。  當其中一個類型具有外部索引鍵屬性時，會使用[參考完整性條件約束](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)定義兩個實體類型之間的關聯。  
  
## 範例  
 下圖顯示包含三種實體類型 \(`Book`、`Publisher` 和 `Author`\) 的概念模型。  `Book` 實體類型具有屬性 `PublisherId`，當您定義 `PublishedBy` 關聯的參考完整性條件約束時，此屬性會參考 `Publisher` 實體類型的實體索引鍵。  
  
 ![RefConstraintModel](../../../../docs/framework/data/adonet/media/refconstraintmodel.gif "RefConstraintModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) 會使用稱為概念結構定義語言 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) 的特定定義域語言 \(DSL\) 來定義概念模型。  下列 CSDL 使用外部索引鍵屬性 `PublisherId`，針對上述概念模型中的 `PublishedBy` 關聯定義參考完整性條件約束。  
  
 [!code-xml[EDM_Example_Model#RefConstraint](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#refconstraint)]  
  
## 請參閱  
 [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)