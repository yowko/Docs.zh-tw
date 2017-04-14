---
title: "分散式交易 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 718b257c-bcb2-408e-b004-a7b0adb1c176
caps.latest.revision: 7
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 7
---
# 分散式交易
交易是一組相關工作，尤其是它會做為一個單位的成功 \(認可\) 或失敗 \(中止\)。  *分散式交易*是影響幾個資源的交易。  對於要認可的分散式交易，所有參與者都必須保證資料的任何變更都是永久的。  不管系統是否當機，還是發生其他不可預見的事件，變更必須持續。  如果單一參與者無法做出此保證，則整個交易會失敗，交易範圍內的任何資料變更都將復原。  
  
> [!NOTE]
>  如果在交易作用期間啟動了 `DataReader`，而您嘗試認可或復原該交易，就會擲回例外狀況 \(Exception\)。  
  
## 使用 System.Transactions  
 在 .NET Framework 中，會透過 <xref:System.Transactions> 命名空間中的 API 來管理分散式交易。  當涉及多個持續性資源管理員時，<xref:System.Transactions> API 會將分散式交易處理委派給交易監視器，如 Microsoft 分散式交易協調器 \(MS DTC\)。  如需詳細資訊，請參閱[Transaction Fundamentals](http://msdn.microsoft.com/zh-tw/2a476b63-b94f-443f-992d-53943fdf4e5d)。  
  
 ADO.NET 2.0 支援使用 `EnlistTransaction` 方法在分散式交易中登記，該方法會在 <xref:System.Transactions.Transaction> 執行個體中登記連接。  在舊版 ADO.NET 中，會使用連接的 `EnlistDistributedTransaction` 方法在分散式交易中進行明確登記，以在支援回溯相容性的 <xref:System.EnterpriseServices.ITransaction> 執行個體 \(Instance\) 中登記連接。  如需企業服務交易的詳細資訊，請參閱 [Interoperability with Enterprise Services and COM\+ Transactions](http://msdn.microsoft.com/zh-tw/2e93b3c6-4d48-4b9b-82b2-7d5908a2c970)。  
  
 當針對 SQL Server 資料庫，使用具有 SQL Server 的 .NET Framework 提供者之 <xref:System.Transactions> 交易時，會自動使用輕量型 <xref:System.Transactions.Transaction>。  然後，交易可視需要提升為完全分散式交易。  如需詳細資訊，請參閱[System.Transactions 與 SQL Server 整合](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)。  
  
> [!NOTE]
>  Oracle 資料庫一次可參與的分散式交易數目上限預設為 10。  與 Oracle 資料庫連接時，在第 10 次交易後會擲回例外狀況。  Oracle 不支援分散式交易內的 `DDL`。  
  
## 自動登記分散式交易  
 自動登記是整合 ADO.NET 連接與 `System.Transactions` 的預設 \(及慣用\) 方式。  如果連接物件確定交易處於作用中 \(在 `System.Transaction` 詞彙中，表示 `Transaction.Current` 不為 Null\)，則會自動在現有分散式交易中登記。  當開啟連接時，即會發生自動交易登記。  之後即使在交易範圍內執行命令，該事件也不會發生。  您可藉由指定 `Enlist=false` 做為 <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A?displayProperty=fullName> 的連接字串參數，或指定 `OLE DB Services=-7` 做為 <xref:System.Data.OleDb.OleDbConnection.ConnectionString%2A?displayProperty=fullName> 的連接字串參數，停用現有交易中的自動登記。  如需 Oracle 及 ODBC 連接字串參數的詳細資訊，請參閱 <xref:System.Data.OracleClient.OracleConnection.ConnectionString%2A?displayProperty=fullName> 及 <xref:System.Data.Odbc.OdbcConnection.ConnectionString%2A?displayProperty=fullName>。  
  
## 在分散式交易中手動登記  
 如果停用了自動登記，或需要登記在開啟連接之後啟動的交易，您可以針對所使用的提供者，使用 <xref:System.Data.Common.DbConnection> 物件的 `EnlistTransaction` 方法，在現有的分散式交易中登記。  在現有的分散式交易中登記可確保，如果認可或復原交易，則也會認可或復原資料來源的程式碼所做的修改。  
  
 當共用商務物件時，在分散式交易中登記會特別適用。  如果與開啟的連接共用商務物件，則僅當該連接開啟時，才會發生自動交易登記。  如果使用共用的商務物件來執行多個交易，則該物件的開啟連接將不會自動在新起始的交易中登記。  在此情況下，您可以停用連接的自動交易登記，並使用 `EnlistTransaction` 在交易中登記連接。  
  
 `EnlistTransaction`  會取得型別 <xref:System.Transactions.Transaction> 的單一引數，該型別是現有交易的參考。  呼叫連接的 `EnlistTransaction` 方法之後，對使用連接之資料來源所做的所有修改都會包含在交易中。  傳遞 Null 值可將連接從目前的分散式交易登記中取消登記。  請注意，在呼叫 `EnlistTransaction` 之前，必須先開啟連接。  
  
> [!NOTE]
>  在交易上明確地登記連接之後，直到第一個交易完成之前，無法取消登記或在其他交易中登記它。  
  
> [!CAUTION]
>  如果連接已使用連接的 <xref:System.Data.Common.DbConnection.BeginTransaction%2A> 方法啟動交易，則 `EnlistTransaction` 會擲回例外狀況。  不過，如果交易是在資料來源上啟動的本機交易 \(例如，使用 <xref:System.Data.SqlClient.SqlCommand>，明確執行 BEGIN TRANSACTION 陳述式\)，則 `EnlistTransaction` 將復原本機交易，並按要求在現有的分散式交易中登記。  您不會收到復原本機交易的通知，而且必須管理所有非使用 <xref:System.Data.Common.DbConnection.BeginTransaction%2A> 啟動的本機交易。  如果您是將 .NET Framework Data Provider for SQL Server \(`SqlClient`\) 用於 SQL Server，則嘗試登記會擲回例外狀況。  將不會偵測到所有其他情況。  
  
## SQL Server 中的可提升交易  
 SQL Server 支援可提升交易，在該交易中，本機輕量型交易可在必要時自動提升為分散式交易。  除非需要已加入的負荷，否則可提升交易不會叫用分散式交易的已加入負荷。  如需詳細資訊和程式碼範例，請參閱[System.Transactions 與 SQL Server 整合](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)。  
  
## 設定分散式交易  
 您可能需要透過網路啟用 MS DTC，才能使用分散式交易。  如果已啟用 Windows 防火牆，則必須允許 MS DTC 服務使用網路或開啟 MS DTC 連接埠。  
  
## 請參閱  
 [交易和並行](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)   
 [System.Transactions 與 SQL Server 整合](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)