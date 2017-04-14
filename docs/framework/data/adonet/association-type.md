---
title: "關聯類型 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 26c409f6-06e8-4441-ac78-1b1076a3c005
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 關聯類型
「*關聯型別*」\(Association type，亦稱為關聯\) 是在實體資料模型 \(EDM\) 中描述關聯的基本組建區塊。  在概念模型中，關聯 \(association\) 代表兩個[實體型別](../../../../docs/framework/data/adonet/entity-type.md) \(例如 `Customer` 和 `Order`\) 之間的關聯性 \(relationship\)。  在應用程式中，關聯的執行個體代表特定的關聯 \(例如 `Customer` 執行個體和 `Order` 執行個體之間的關聯\)。  關聯執行個體會在邏輯上群組於[關聯集](../../../../docs/framework/data/adonet/association-set.md)中。  
  
 關聯定義包含下列資訊：  
  
-   唯一名稱。  \(必要項\)  
  
-   兩個[關聯 End](../../../../docs/framework/data/adonet/association-end.md)，關聯性中的每個實體類型各一個。  \(必要項\)  
  
    > [!NOTE]
    >  一個關聯 \(association\) 不能代表兩個實體型別以上的關聯性 \(relationship\)。  不過，關聯可以為其每一個關聯 End 指定同樣的實體型別，以定義自我關聯性。  
  
-   [參考完整性條件約束](../../../../docs/framework/data/adonet/referential-integrity-constraint.md)。  \(選擇項\)  
  
 每個關聯 End 必須指定一個[關聯 End 多重性](../../../../docs/framework/data/adonet/association-end-multiplicity.md)，代表可在關聯其中一端的實體型別執行個體數量。  關聯 End 多重性的值可以是一 \(0\)、零或一 \(0..1\)，或許多 \(\*\)。  關聯其中一端的實體型別執行個體可透過[導覽屬性](../../../../docs/framework/data/adonet/navigation-property.md)或外部索引鍵來存取 \(若在實體型別上公開\)。  如需詳細資訊，請參閱[實體資料模型：外部索引鍵](../../../../docs/framework/data/adonet/foreign-key-property.md)。  
  
## 範例  
 下圖顯示包含兩個關聯 \(`PublishedBy` 和 `WrittenBy`\) 的概念模型。  `PublishedBy` 關聯的關聯 End 為 `Book` 和 `Publisher` 實體類型。  `Publisher` End 的多重性是 \(1\)，而 `Book` End 的多重性是許多 \(\*\)，表示一個發行者發行許多書籍，而一本書籍由一個發行者發行。  
  
 ![範例模型](../../../../docs/framework/data/adonet/media/examplemodel.gif "ExampleModel")  
  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) 會使用稱為概念結構定義語言 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) 的特定定義域語言 \(DSL\) 來定義概念模型。  下列 CSDL 定義上圖中的 `PublishedBy` 關聯。  
  
 [!code-xml[EDM_Example_Model#AssociationExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#associationexample)]  
  
## 請參閱  
 [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)