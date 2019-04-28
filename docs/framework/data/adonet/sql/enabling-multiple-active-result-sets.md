---
title: 啟用 Multiple Active Result Sets
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
ms.openlocfilehash: 633aaa4a9540d0895252e56dbeabd97200081fc9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61877678"
---
# <a name="enabling-multiple-active-result-sets"></a>啟用 Multiple Active Result Sets
Multiple Active Result Set (MARS) 是與 SQL Server 搭配使用的功能，它允許在單一連接中執行多個批次作業。 啟用 MARS 以與 SQL Server 搭配使用時，使用的每個命令物件都會在連接中加入工作階段。  
  
> [!NOTE]
>  單一的 MARS 工作階段會開啟一個邏輯連接供 MARS 使用，然後再針對每個使用中的命令開啟邏輯連接。  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a>在連接字串中啟用及停用 MARS  
  
> [!NOTE]
>  下列連接字串使用範例**AdventureWorks**隨附於 SQL Server 的資料庫。 提供的連接字串會假設伺服器上已安裝名為 MSSQL1 的資料庫。 視環境需要修改連接字串。  
  
 預設會停用 MARS 功能。 藉由將 "MultipleActiveResultSets=True" 關鍵字配對加入連接字串，可啟用該功能。 "True" 是啟用 MARS 的唯一有效值。 下列範例會說明如何連接至 SQL Server 的執行個體，以及如何指定應該啟用 MARS。  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=True"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=True";  
```  
  
 藉由將 "MultipleActiveResultSets=False" 關鍵字配對加入連接字串，可停用 MARS。 "False" 是停用 MARS 的唯一有效值。 下列連接字串會示範如何停用 MARS。  
  
```vb  
Dim connectionString As String = "Data Source=MSSQL1;" & _  
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" & _  
    "MultipleActiveResultSets=False"  
```  
  
```csharp  
string connectionString = "Data Source=MSSQL1;" +   
    "Initial Catalog=AdventureWorks;Integrated Security=SSPI;" +  
    "MultipleActiveResultSets=False";  
```  
  
## <a name="special-considerations-when-using-mars"></a>使用 MARS 時的特殊考量  
 一般而言，現有應用程式不需修改即可使用啟用 MARS 的連接。 但是，如果您要在應用程式中使用 MARS 功能，應了解下列特殊考量。  
  
### <a name="statement-interleaving"></a>陳述式交錯  
 MARS 作業會在伺服器上同步執行。 允許 SELECT 及 BULK INSERT 陳述式的陳述式交錯。 但是，資料管理語言 (DML) 及資料定義語言 (DDL) 陳述式會以原子方式執行。 嘗試於原子批次執行時執行的任何陳述式都會被封鎖。 伺服器的平行執行不是 MARS 功能。  
  
 如果在 MARS 連接下送出兩個批次作業，其中一個包含 SELECT 陳述式，另一個包含 DML 陳述式，則可以在執行 SELECT 陳述式時開始執行 DML。 不過，DML 陳述式必須先完成執行，才能繼續執行 SELECT 陳述式。 如果兩個陳述式同時在同一個異動下執行，則 DML 陳述式在 SELECT 陳述式已開始執行後所進行的任何變更，對於讀取作業都是不可見的。  
  
 SELECT 陳述式內的 WAITFOR 陳述式在等待期間，即產生第一個資料列之前，不會產生異動。 這表示在 WAITFOR 陳述式等待期間，無法在同一連接內執行其他批次作業。  
  
### <a name="mars-session-cache"></a>MARS 工作階段快取  
 開啟啟用 MARS 的連接時，會建立邏輯工作階段，如此會增加額外負荷。 若要最小化負荷並提高效能， **SqlClient**快取連接內的 MARS 工作階段。 快取包含最多 10 個 MARS 工作階段。 使用者不可調整此值。 如果達到工作階段限制，則會建立新的工作階段而不會產生錯誤。 其中包含的快取及工作階段是以每個連接為基礎的，不可跨連接共用。 釋放工作階段時，會將其傳回集區，直至達到集區上限為止。 如果快取集區已滿，則工作階段會關閉。 MARS 工作階段不會過期。 只會在處置連接物件時清除它們。 MARS 工作階段快取不會預先載入。 應用程式需要更多工作階段時會將其載入。  
  
### <a name="thread-safety"></a>執行緒安全  
 MARS 作業不是安全執行緒。  
  
### <a name="connection-pooling"></a>連接共用  
 啟用 MARS 的連接共用方式與其他連接一樣。 如果應用程式開啟兩個連接，一個啟用 MARS，另一個停用 MARS，則兩個連接會位於不同的集區中。 如需詳細資訊，請參閱 [SQL Server 連共用ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)。  
  
### <a name="sql-server-batch-execution-environment"></a>SQL Server 批次執行環境  
 連接開啟時，會定義預設的環境。 然後會將此環境複製到邏輯 MARS 工作階段。  
  
 批次執行環境包含下列元件：  
  
- 設定選項 (例如，ANSI_NULLS、DATE_FORMAT、LANGUAGE、TEXTSIZE)  
  
- 安全性內容 (使用者/應用程式角色)  
  
- 資料庫內容 (目前資料庫)  
  
- 執行狀態變數 (例如，@@ERROR，@@ROWCOUNT，@@FETCH_STATUS @@IDENTITY)  
  
- 最上層暫存資料表  
  
 使用 MARS，預設的執行環境可與連接產生關聯。 在指定連接下開始執行的每個新批次作業，都會收到預設環境的複本。 每當程式碼在指定批次作業下執行時，對環境所做的所有變更都只限於該特定批次作業。 執行一旦完成，便會將執行設定複製到預設環境中。 當單一批次作業發出要在同一異動下循序執行的數個命令時，其語意與舊版用戶端或伺服器相關的連接所公開的語意相同。  
  
### <a name="parallel-execution"></a>平行執行  
 MARS 未設計為在應用程式內移除對多重連接的所有需求。 如果應用程式確實需要針對伺服器平行執行命令，則應使用多重連接。  
  
 例如，請考量下列案例。 建立兩個命令物件，一個用於處理結果集，另一個用於更新資料，它們透過 MARS 共用通用連接。 在此案例中， `Transaction`。`Commit` 更新失敗，直到在第一個命令物件，進而產生下列例外狀況已讀取所有結果：  
  
 訊息：其他工作階段正在使用交易內容。  
  
 來源：.NET SqlClient 資料提供者  
  
 預期：(null)  
  
 已接收：System.Data.SqlClient.SqlException  
  
 處理此案例有三個選項：  
  
1. 在建立讀取器後啟動交易，使其不會成為交易的一部分。 然後每個更新會成為其自身的交易。  
  
2. 在讀取器關閉後認可所有工作。 如此可能會發生大量批次的更新。  
  
3. 請勿針對每個命令物件使用 MARS，而是使用 MARS 之前的單獨連接。  
  
### <a name="detecting-mars-support"></a>偵測 MARS 支援  
 應用程式可以藉由讀取 `SqlConnection.ServerVersion` 值來檢查 MARS 支援。 SQL Server 2005 和 SQL Server 2008 的主版本號碼應為分別為 9 和 10。  
  
## <a name="see-also"></a>另請參閱

- [Multiple Active Result Set (MARS)](../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)
- [ADO.NET Managed 提供者和 DataSet 開發人員中心](https://go.microsoft.com/fwlink/?LinkId=217917)
