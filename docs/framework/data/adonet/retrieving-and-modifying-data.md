---
title: 抓取和修改資料
description: 在 .NET Framework 中，ADO.NET 中的資料提供者可做為應用程式與資料來源之間的橋樑，以讀取和更新資料。
ms.date: 03/30/2017
ms.assetid: 722e7f87-3691-46c6-87e8-7d159722d675
ms.openlocfilehash: 7620843e77b25606b2dec2bf6eae3a4f40d1b9fb
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150670"
---
# <a name="retrieving-and-modifying-data-in-adonet"></a>在 ADO.NET 中傳送和修改資料

任何資料庫應用程式都有一個主要功能，那就是連接到資料來源並擷取其內含的資料。 ADO.NET 的 .NET Framework 資料提供者可做為應用程式與資料來源之間的橋樑，讓您可以執行命令，以及使用 **DataReader** 或 **DataAdapter**來取出資料。 任何資料庫應用程式都有一個主要功能，那就是更新資料庫中儲存的資料。 在 ADO.NET 中，更新資料牽涉到使用 **DataAdapter** 和和 <xref:System.Data.DataSet> **命令** 物件，而且也可能牽涉到使用交易。  
  
## <a name="in-this-section"></a>本節內容  

 [連接到資料來源](connecting-to-a-data-source.md)  
 說明如何建立資料來源的連接，以及如何使用連接事件。  
  
 [連接字串](connection-strings.md)  
 包含一些主題，其中說明連接字串 (包含連接字串關鍵字、安全性資訊) 的使用、儲存和擷取的各種層面。  
  
 [連接共用](connection-pooling.md)  
 說明 .NET Framework 資料提供者的連接共用 (Connection Pooling)。  
  
 [命令和參數](commands-and-parameters.md)  
 包含一些主題，其中說明如何建立命令和命令產生器、設定參數，以及執行命令來擷取和修改資料。  
  
 [DataAdapter 和 DataReader](dataadapters-and-datareaders.md)  
 包含一些主題，其中說明 DataReader、DataAdapter、參數、處理 DataAdapter 事件，以及執行批次作業。  
  
 [異動和並行存取](transactions-and-concurrency.md)  
 包含一些主題，其中說明如何執行本機異動、分散式異動，以及使用開放式並行存取 (Optimistic Concurrency)。  
  
 [擷取識別或自動編號值](retrieving-identity-or-autonumber-values.md)  
 提供範例，說明如何將 SQL Server 資料表中的 **標識** 列或 Microsoft Access 資料表中的 **自動編號** 欄位所產生的值，對應至資料表中插入之資料列的資料行。 討論如何在 `DataTable` 中合併識別值。  
  
 [擷取二進位資料](retrieving-binary-data.md)  
 描述如何使用取出二進位資料或大型資料結構 `CommandBehavior` 。`SequentialAccess` 修改的預設行為 `DataReader` 。  
  
 [使用預存程序修改資料](modifying-data-with-stored-procedures.md)  
 說明如何使用預存程序 (Stored Procedure) 輸入參數和輸出參數，將資料列插入資料庫中，並傳回新的識別值。  
  
 [擷取資料庫結構描述資訊](retrieving-database-schema-information.md)  
 說明如何取得資料來源的可用資料庫或目錄、資料庫中的資料表和檢視表、資料表的條件約束，以及其他結構描述資訊。  
  
 [DbProviderFactory](dbproviderfactories.md)  
 說明提供者 Factory 模型並示範如何使用 `System.Data.Common` 命名空間 (Namespace) 中的基底類別 (Base Class)。  
  
 [ADO.NET 中的資料追蹤](data-tracing.md)  
 說明 ADO.NET 如何提供內建資料追蹤功能。  
  
 [效能計數器](performance-counters.md)  
 說明適用於 `SqlClient` 和 `OracleClient` 的效能計數器。  
  
 [非同步程式設計](asynchronous-programming.md)  
 描述非同步程式設計的 ADO.NET 支援。  
  
 [SqlClient 資料流支援](sqlclient-streaming-support.md)  
 討論如何撰寫應用程式，以從 SQL Server 串流資料，而不需要將它完全載入記憶體中。  
  
## <a name="see-also"></a>另請參閱

- [ADO.NET 中的資料類型對應](data-type-mappings-in-ado-net.md)
- [DataSet、DataTable 和 DataView](./dataset-datatable-dataview/index.md)
- [設定 ADO.NET 應用程式的安全性](securing-ado-net-applications.md)
- [SQL Server and ADO.NET](./sql/index.md) (SQL Server 和 ADO.NET)
- [ADO.NET 概觀](ado-net-overview.md) \(部分機器翻譯\)
