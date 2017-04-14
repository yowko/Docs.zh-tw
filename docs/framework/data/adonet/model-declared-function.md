---
title: "模型宣告函式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
caps.latest.revision: 3
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 3
---
# 模型宣告函式
「*模型宣告函式*」\(Model\-declared Function\) 是指在概念模型中宣告、但並不是在該概念模型中定義的函式。  該函式可能是在裝載或儲存環境中定義的。  例如，模型宣告函式可能對應到在資料庫中定義的函式，因而在概念模型中公開伺服器端的功能。  
  
 模型宣告函式的宣告包含下列資訊：  
  
-   函式的名稱。  \(必要項\)  
  
-   傳回值的型別。  \(選擇項\)  
  
    > [!NOTE]
    >  若未指定任何傳回值，則傳回型別為 void。  
  
-   參數資訊，包括參數名稱和型別。  \(選擇項\)  
  
## 範例  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) 會使用稱為概念結構定義語言 \([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)\) 的特定定義域語言 \(DSL\) 來定義概念模型。  在 CSDL 中，模型宣告函式的其中一個實作是[函式匯入](http://msdn.microsoft.com/zh-tw/125704ae-56c7-4233-80b7-389a10f3a65d)。  下列 CSDL 定義具有函式匯入定義的實體容器。  請注意，由於沒有指定傳回型別，因此該函式的傳回型別為 void。  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## 請參閱  
 [實體資料模型索引鍵概念](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)   
 [實體資料模型](../../../../docs/framework/data/adonet/entity-data-model.md)