---
title: "安全性 (LINQ to DataSet) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 安全性 (LINQ to DataSet)
本主題討論 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 中的安全性問題。  
  
## 將查詢傳遞到不受信任的元件  
 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢可以在程式的一個位置編寫，並在另一個位置執行。  在編寫查詢的位置，查詢可以參考顯示在該位置的任何項目，例如，呼叫方法所屬類別的私用成員，或代表區域變數\/引數的符號。  在執行時間，即使呼叫程式碼沒有顯示出來，此查詢還是可以有效地存取查詢在編寫時參考的成員。  執行查詢的程式碼沒有任意增加的可見性，因為它無法選擇要存取的成員。  它將可以精確地存取查詢所存取的成員，而且僅透過查詢本身進行存取。  
  
 這暗示：藉由將查詢的參考傳遞到程式碼的其他片段，收到查詢的元件就會受到信任，可以存取該查詢所參考的所有公用和私用成員。  一般而言，除非已經仔細建構查詢，讓該查詢不會暴露應該保密的資訊，否則，不應將 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢傳遞到不受信任的元件。  
  
## 外部輸入  
 應用程式通常採用外部輸入 \(從使用者或其他外部代理程式\)，並根據該輸入執行動作。  若是 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)]，應用程式可能會根據外部輸入，或使用查詢中的外部輸入，以特定的方式建構查詢。[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢會接受所有接受常值之處的參數。  應用程式開發人員應該使用參數化的查詢，而非將常值從外部代理程式直接插入到查詢中。  
  
 從使用者或外部代理程式直接或間接衍生的任何輸入都可能具備運用目標語言之語法的內容，藉以執行未經授權的動作。  這是所謂的 SQL 插入式攻擊，這是以目標語言為 Transact\-SQL 的攻擊模式來命名的。  直接插入到查詢的使用者輸入用於卸除資料庫資料表、造成阻絕服務，或變更要執行之作業的本質。  雖然查詢撰寫可以在 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 中進行，但是查詢會透過物件模型 API 執行。使用字串操作或串連不會建立 [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] 查詢，因為這些查詢在 Transact\-SQL 中，而且在傳統意義上，不容易受到 SQL 插入式攻擊。  
  
## 請參閱  
 [程式設計手冊](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)