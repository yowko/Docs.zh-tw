---
title: "擷取和修改 ADO.NET 中的資料 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
caps.latest.revision: 5
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 5
---
# 擷取和修改 ADO.NET 中的資料
任何資料庫應用程式都有一個主要功能，那就是連接到資料來源並擷取其內含的資料。  ADO.NET 的 .NET Framework 資料提供者可做為應用程式和資料來源之間的橋樑，可讓您執行命令並使用 **DataReader** 或 **DataAdapter** 擷取資料。  任何資料庫應用程式都有一個主要功能，那就是更新資料庫中儲存的資料。  在 ADO.NET 中，更新資料牽涉到使用 **DataAdapter** 和 <xref:System.Data.DataSet>，以及 **Command** 物件；並且也可能需要使用交易。  
  
## 在本節中  
 [連接資料來源](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 說明如何建立資料來源的連接，以及如何使用連接事件。  
  
 [連接字串](../../../../docs/framework/data/adonet/connection-strings.md)  
 包含一些主題，其中說明連接字串 \(包含連接字串關鍵字、安全性資訊\) 的使用、儲存和擷取的各種層面。  
  
 [連接共用](../../../../docs/framework/data/adonet/connection-pooling.md)  
 說明 .NET Framework 資料提供者的連接共用 \(Connection Pooling\)。  
  
 [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 包含一些主題，其中說明如何建立命令和命令產生器、設定參數，以及執行命令來擷取和修改資料。  
  
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 包含一些主題，其中說明 DataReader、DataAdapter、參數、處理 DataAdapter 事件，以及執行批次作業。  
  
 [交易和並行](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 包含一些主題，其中說明如何執行本機交易、分散式交易，以及使用開放式並行存取 \(Optimistic Concurrency\)。  
  
 [擷取 Identity 或 Autonumber 值](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 提供範例，說明如何將針對 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 資料表中的 **identity** 資料行或針對 Microsoft Access 資料表中的 **Autonumber** 欄位所產生的值，對應至資料表中插入資料列的資料行。  討論如何在 `DataTable` 中合併識別值。  
  
 [擷取二進位資料](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 說明如何使用 `CommandBehavior`.`SequentialAccess` 來修改 `DataReader` 的預設行為，以擷取二進位資料或大型資料結構。  
  
 [使用預存程序修改資料](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 說明如何使用預存程序 \(Stored Procedure\) 輸入參數和輸出參數，將資料列插入資料庫中，並傳回新的識別值。  
  
 [擷取資料庫結構描述資訊](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 說明如何取得資料來源的可用資料庫或目錄、資料庫中的資料表和檢視表、資料表的條件約束，以及其他結構描述資訊。  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 說明提供者 Factory 模型並示範如何使用 `System.Data.Common` 命名空間 \(Namespace\) 中的基底類別 \(Base Class\)。  
  
 [ADO.NET 中的資料追蹤](../../../../docs/framework/data/adonet/data-tracing.md)  
 說明 ADO.NET 如何提供內建資料追蹤功能。  
  
 [效能計數器](../../../../docs/framework/data/adonet/performance-counters.md)  
 說明適用於 `SqlClient` 和 `OracleClient` 的效能計數器。  
  
 [非同步程式設計](../../../../docs/framework/data/adonet/asynchronous-programming.md)  
 描述 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 支援非同步程式設計。  
  
 [SqlClient 資料流支援](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 討論如何撰寫從 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 串流資料而不需將它完全載入到記憶體中的應用程式。  
  
## 請參閱  
 [ADO.NET 中的資料型別對應](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)   
 [DataSet、DataTable 及 DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)   
 [保護 ADO.NET 應用程式](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)   
 [SQL Server 和 ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)   
 [ADO.NET Managed 提供者和資料集開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)