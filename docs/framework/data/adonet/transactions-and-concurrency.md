---
title: "交易和並行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# 交易和並行
交易是由單一命令或當做封裝 \(Package\) 執行的命令群組所組成。  交易可讓您將多項作業結合成單一工作單位。  如果交易的某一處失敗，則所有更新都會復原到交易之前的狀態。  
  
 交易必須符合 ACID 屬性 \(單元性 \(Atomicity\)、一致性 \(Consistency\)、隔離性 \(Isolation\) 和持續性 \(Durability\)，才能保證資料一致性。  大多數關聯式資料庫系統 \(例如 Microsoft SQL Server\) 都可以支援交易，其方法是在每次用戶端應用程式執行更新、插入或刪除作業時，提供鎖定、記錄和交易管理功能。  
  
> [!NOTE]
>  如果鎖定保留時間太久，包含多個資源的交易可能會降低並行。  因此，請盡可能縮短交易的時間長度。  
  
 如果某筆交易包含相同資料庫或伺服器中的多個資料表，則預存程序 \(Stored Procedure\) 中的明確交易通常會有較佳的效能。  您可以使用 Transact\-SQL `BEGIN TRANSACTION`、`COMMIT TRANSACTION` 和 `ROLLBACK TRANSACTION` 陳述式，在 SQL Server 預存程序中建立交易。  如需詳細資訊，請參閱《SQL Server 線上叢書》。  
  
 包含不同資源管理員的交易 \(例如 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 與 Oracle 之間的交易\) 需要分散式交易。  
  
## 在本節中  
 [本機交易](../../../../docs/framework/data/adonet/local-transactions.md)  
 示範如何針對資料庫執行交易。  
  
 [分散式交易](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 說明如何在 ADO.NET 中執行分散式交易。  
  
 [System.Transactions 與 SQL Server 整合](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 說明 <xref:System.Transactions> 如何與 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 整合以使用分散式交易。  
  
 [開放式並行存取](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 說明開放式與封閉式同步存取，以及如何測試並行違規。  
  
## 請參閱  
 [Transaction Fundamentals](http://msdn.microsoft.com/zh-tw/2a476b63-b94f-443f-992d-53943fdf4e5d)   
 [連接資料來源](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)   
 [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)   
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)   
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)