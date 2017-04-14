---
title: "搭配 LINQ to SQL 使用緊密結合的主從架構應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: e083d805-dcf6-459d-b9af-9ef0563f2dd7
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 搭配 LINQ to SQL 使用緊密結合的主從架構應用程式
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 可用於展示層上為緊密結合的智慧型用戶端的中介層上。  在唯讀資料存取的案例中，不需要開放式並行存取 \(Optimistic Concurrency\) 檢查或使用時間戳記的開放式並行存取，處理起來並不複雜，與簡單的非遠端案例相去不遠。  不過，當資料庫需要使用原始值的開放式並行存取檢查時，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 無法提供與資料集中反覆存取資料相同的支援能力。  不過，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 中介層可與任何平台上的用戶端交換資料。  
  
 [!INCLUDE[vs_orcas_long](../../../../../../includes/vs-orcas-long-md.md)] 中的 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 並未提供追蹤實體狀態的基礎結構，因此無法追蹤實體在序列化到用戶端之後的狀態。  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 可啟用服務導向架構，在此架構中，資料和展示層之間的互動不多，而且多屬於不可部分完成的作業，但它不會反覆存取原始值。  因此，如果您要使用緊密結合的智慧型用戶端搭配 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]，而資料庫使用以原始值為基礎的開放式並行存取，就必須實作自己的機制，讓展示層與中介層得以溝通變更。  系統設計人員可自行決定是否要在此額外工作與 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 在中介層所提供的功能之間做取捨。  另一方面，如果資料庫有時間戳記，那麼就不需要自訂變更追蹤邏輯。  
  
## 請參閱  
 [使用 LINQ to SQL 的 N\-Tier 和遠端應用程式](../../../../../../docs/framework/data/adonet/sql/linq/n-tier-and-remote-applications-with-linq-to-sql.md)   
 [搭配 Web 服務使用 LINQ to SQL N\-Tier](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)   
 [使用多層式架構應用程式中的資料集](../Topic/Work%20with%20datasets%20in%20n-tier%20applications.md)