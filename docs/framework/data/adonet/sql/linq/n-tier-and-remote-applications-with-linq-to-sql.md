---
title: "使用 LINQ to SQL 的 N-Tier 和遠端應用程式 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 854a1cdd-53cb-45f5-83ca-63962a9b3598
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# 使用 LINQ to SQL 的 N-Tier 和遠端應用程式
您可以建立使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的 N\-Tier 或多層應用程式。  一般來說，[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 資料內容、實體類別和查詢建構邏輯位於資料存取層 \(DAL\) 的中介層 \(Middle Tier\)。  商務邏輯以及任何非持續性資料則可完全實作在實體的部分類別和方法和資料內容，或可以實作在另外的類別中。  
  
 用戶端或展示層會在中介層的遠端介面上呼叫方法，而該層上的 DAL 將執行對應到 <xref:System.Data.Linq.DataContext> 方法的查詢或預存程序。  中介層一般會將資料以實體或 Proxy 物件的 XML 表示傳回用戶端。  
  
 在中介層上，實體是由資料內容建立的，資料內容會追蹤其狀態，以及管理資料庫的延後載入和提交變更。  這些實體會「附加」到 `DataContext`。  不過，實體在透過序列化 \(Serialization\) 傳送到另一層之後，就會中斷連結，表示 `DataContext` 不再追蹤其狀態。  用戶端傳回進行更新的實體必須重新附加到資料內容，如此 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 才能將變更提交至資料庫。  在開放式並行存取檢查需要的情況下，用戶端會負責將原始值和\/或時間戳記送回中介層。  
  
 在 ASP.NET 應用程式中，<xref:System.Web.UI.WebControls.LinqDataSource> 會負責這其中大多數複雜的作業。  如需詳細資訊，請參閱 [NIB: LinqDataSource Web Server Control Overview](http://msdn.microsoft.com/zh-tw/104cfc3f-7385-47d3-8a51-830dfa791136)。  
  
## 其他資源  
 如需如何實作使用 [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] 的 N\-Tier 應用程式，請參閱下列主題：  
  
-   [LINQ to SQL 多層式架構與 ASP.NET](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-aspnet.md)  
  
-   [搭配 Web 服務使用 LINQ to SQL N\-Tier](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-n-tier-with-web-services.md)  
  
-   [搭配 LINQ to SQL 使用緊密結合的主從架構應用程式](../../../../../../docs/framework/data/adonet/sql/linq/linq-to-sql-with-tightly-coupled-client-server-applications.md)  
  
-   [實作 N\-Tier 商務邏輯](../../../../../../docs/framework/data/adonet/sql/linq/implementing-business-logic-linq-to-sql.md)  
  
-   [N\-Tier 應用程式中的資料擷取和 CUD 作業 \(LINQ to SQL\)](../../../../../../docs/framework/data/adonet/sql/linq/data-retrieval-and-cud-operations-in-n-tier-applications.md)  
  
 如需使用 ADO.NET 資料集的多層式架構應用程式的詳細資訊，請參閱[使用多層式架構應用程式中的資料集](../Topic/Work%20with%20datasets%20in%20n-tier%20applications.md)。  
  
## 請參閱  
 [背景資訊](../../../../../../docs/framework/data/adonet/sql/linq/background-information.md)