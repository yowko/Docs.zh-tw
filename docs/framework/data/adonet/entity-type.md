---
title: "實體類型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a6dee9ab-9e4a-48f2-a169-3f79cc15821c
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 實體類型
「*實體類型*」\(Entity Type\) 是基本的建置組塊，可透過實體資料模型 \(EDM\) 描述資料的結構。  在概念模型中，實體類型代表最上層概念的結構，例如客戶或訂單。  實體類型是實體類型執行個體的範本。  每個範本包含下列資訊：  
  
-   唯一名稱。  \(必要項。\)  
  
-   由一或多個屬性定義的[實體索引鍵](../../../../docs/framework/data/adonet/entity-key.md)。  \(必要項。\)  
  
-   [屬性](../../../../docs/framework/data/adonet/property.md)形式的資料。  \(選擇性。\)  
  
-   允許從[關聯](../../../../docs/framework/data/adonet/association-type.md)的一個 [End](../../../../docs/framework/data/adonet/association-end.md)導覽至另一個 End 的[導覽屬性](../../../../docs/framework/data/adonet/navigation-property.md)。  \(選擇項\)  
  
 在應用程式中，實體類型的執行個體代表特定的物件 \(例如特定的客戶或訂單\)。  實體類型的每一個執行個體都必須在[實體集](../../../../docs/framework/data/adonet/entity-set.md)中有唯一的[實體索引鍵](../../../../docs/framework/data/adonet/entity-key.md)。  
  
 如果兩個實體類型執行個體屬於相同類型，而且索引鍵的值也相同，則會將這兩個執行個體視為相等。  
  
## 範例  
 下圖顯示包含三種實體類型 \(`Book`、`Publisher` 和 `Author`\) 的概念模型：  
  
 ![範例模型](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 請注意，構成實體索引鍵的每個實體類型屬性皆加註「\(索引鍵\)」。  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) 會使用稱為概念結構定義語言 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) 的特定定義域語言 \(DSL\) 來定義概念模型。  下列 CSDL 定義上圖所顯示的 `Book` 實體類型：  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## 請參閱  
 [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)   
 [Facet](../../../../docs/framework/data/adonet/facet.md)