---
title: 在 ADO.NET 中傳送和修改資料
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: 5ef5191cf89f22fbaf0bb1bf4fbf47db1d4c06a1
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779347"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>在 ADO.NET 中傳送和修改資料
任何資料庫應用程式都有一個主要功能，那就是連接到資料來源並擷取其內含的資料。 ADO.NET 的.NET Framework 資料提供者做為應用程式和資料來源之間的橋樑可讓您執行命令也使用擷取資料**DataReader**或是**DataAdapter**. 任何資料庫應用程式都有一個主要功能，那就是更新資料庫中儲存的資料。 在 ADO.NET 中，更新資料牽涉到使用**DataAdapter**並<xref:System.Data.DataSet>，以及**命令**物件; 並且也可能需要使用交易。  
  
## <a name="in-this-section"></a>本章節內容  
 [連接至資料來源](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 說明如何建立資料來源的連接，以及如何使用連接事件。  
  
 [連接字串](../../../../docs/framework/data/adonet/connection-strings.md)  
 包含一些主題，其中說明連接字串 (包含連接字串關鍵字、安全性資訊) 的使用、儲存和擷取的各種層面。  
  
 [連接共用](../../../../docs/framework/data/adonet/connection-pooling.md)  
 說明 .NET Framework 資料提供者的連接共用 (Connection Pooling)。  
  
 [命令和參數](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 包含一些主題，其中說明如何建立命令和命令產生器、設定參數，以及執行命令來擷取和修改資料。  
  
 [DataAdapter 和 DataReader](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 包含一些主題，其中說明 DataReader、DataAdapter、參數、處理 DataAdapter 事件，以及執行批次作業。  
  
 [異動和並行存取](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 包含一些主題，其中說明如何執行本機交易、分散式交易，以及使用開放式並行存取 (Optimistic Concurrency)。  
  
 [擷取身分識別或自動編號值](../../../../docs/framework/data/adonet/retrieving-identity-or-autonumber-values.md)  
 提供的對應產生的值範例**身分識別**資料行中的 SQL Server 資料表或針對**Autonumber**欄位在 Microsoft Access 資料表中，資料表中插入資料列的資料行。 討論如何在 `DataTable` 中合併識別值。  
  
 [擷取二進位資料](../../../../docs/framework/data/adonet/retrieving-binary-data.md)  
 描述如何擷取二進位資料或大型資料結構使用`CommandBehavior`。`SequentialAccess` 若要修改的預設行為`DataReader`。  
  
 [使用預存程序修改資料](../../../../docs/framework/data/adonet/modifying-data-with-stored-procedures.md)  
 說明如何使用預存程序 (Stored Procedure) 輸入參數和輸出參數，將資料列插入資料庫中，並傳回新的識別值。  
  
 [擷取資料庫結構描述資訊](../../../../docs/framework/data/adonet/retrieving-database-schema-information.md)  
 說明如何取得資料來源的可用資料庫或目錄、資料庫中的資料表和檢視表、資料表的條件約束，以及其他結構描述資訊。  
  
 [DbProviderFactories](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 說明提供者 Factory 模型並示範如何使用 `System.Data.Common` 命名空間 (Namespace) 中的基底類別 (Base Class)。  
  
 [ADO.NET 中的資料追蹤](../../../../docs/framework/data/adonet/data-tracing.md)  
 說明 ADO.NET 如何提供內建資料追蹤功能。  
  
 [效能計數器](../../../../docs/framework/data/adonet/performance-counters.md)  
 說明適用於 `SqlClient` 和 `OracleClient` 的效能計數器。  
  
 [非同步程式設計](../../../../docs/framework/data/adonet/asynchronous-programming.md)  
 描述 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 支援非同步程式設計。  
  
 [SqlClient 資料流支援](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md)  
 討論如何撰寫的應用程式的資料流資料從 SQL Server 而不需要它完全載入記憶體中。  
  
## <a name="see-also"></a>另請參閱  
 [ADO.NET 中的資料類型對應](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [DataSet、DataTable 和 DataView](../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [設定 ADO.NET 應用程式的安全性](../../../../docs/framework/data/adonet/securing-ado-net-applications.md)  
 [SQL Server 和 ADO.NET](../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
