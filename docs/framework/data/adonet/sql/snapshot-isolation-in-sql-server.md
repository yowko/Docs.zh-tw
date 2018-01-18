---
title: "SQL Server 中的快照隔離"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 43ae5dd3-50f5-43a8-8d01-e37a61664176
caps.latest.revision: "6"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: a1d263f74f312b34c97f54cd970334017a797652
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="snapshot-isolation-in-sql-server"></a>SQL Server 中的快照隔離
快照隔離可強化 OLTP 應用程式的並行功能。  
  
## <a name="understanding-snapshot-isolation-and-row-versioning"></a>瞭解快照集隔離及資料列版本控制  
 一旦啟用快照集隔離，維護每個交易更新的資料列版本，以在**tempdb**。 唯一異動序號識別每筆異動，並會針對每個資料列版本記錄這些唯一的號碼。 交易使用其序號在該交易序號之前的最新資料列版本。 該交易會忽略在交易開始之後建立的較新資料列版本。  
  
 「快照集」這個詞彙反映了根據交易開始時資料庫的狀態，交易中所有查詢都看到資料庫的同一版本 (或快照集) 這一事實。 在快照集交易中的基礎資料列或資料頁面上沒有鎖定，這允許其他交易執行，而不會被之前未完成的交易封鎖。 修改資料的交易不會封鎖讀取資料的交易，而讀取資料的交易也不會封鎖寫入資料的交易，因為它們通常處於 SQL Server 中預設的 READ COMMITTED 隔離等級中。 這種無封鎖的行為也會大幅降低複雜交易發生死結的可能性。  
  
 快照集隔離使用開放式同步存取模型。 如果快照集交易嘗試認可對交易開始後發生變更之資料的修改，則該交易將復原並將發生錯誤。 對存取要修改之資料的 SELECT 陳述式使用 UPDLOCK 提示，可避免發生上述情況。 如需詳細資訊，請參閱《SQL Server 線上叢書》的＜鎖定提示＞。  
  
 必須先設定 ALLOW_SNAPSHOT_ISOLATION ON 資料庫選項以啟用快照集隔離，才能在異動中使用快照集隔離。 這會啟動資料列版本儲存在暫存資料庫的機制 (**tempdb**)。 必須在搭配使用快照集隔離與 Transact-SQL ALTER DATABASE 陳述式的每個資料庫中啟用快照集隔離。 在這一方面，快照集隔離不同於無需設定的傳統隔離等級 READ COMMITTED、REPEATABLE READ、SERIALIZABLE 及 READ UNCOMMITTED。 下列陳述式會啟動快照集隔離，並以 SNAPSHOT 取代預設的 READ COMMITTED 行為：  
  
```  
ALTER DATABASE MyDatabase  
SET ALLOW_SNAPSHOT_ISOLATION ON  
  
ALTER DATABASE MyDatabase  
SET READ_COMMITTED_SNAPSHOT ON  
```  
  
 藉由設定 READ_COMMITTED_SNAPSHOT ON 選項，可存取預設 READ COMMITTED 隔離等級下已指定版本的資料列。 如果將 READ_COMMITTED_SNAPSHOT 選項設為 OFF，則必須明確設定每個工作階段的快照隔離等級，以便存取已指定版本的資料列。  
  
## <a name="managing-concurrency-with-isolation-levels"></a>使用隔離等級管理並行存取  
 Transact-SQL 陳述式執行所在的隔離等級決定了其鎖定及資料列版本控制行為。 隔離等級的範圍涵蓋整個連接，一旦以 SET TRANSACTION ISOLATION LEVEL 陳述式設定某連接的隔離等級後，它會持續有效，直到連接關閉或設定了另一隔離等級為止。 當連接關閉且傳回至集區時，會保留最後一個 SET TRANSACTION ISOLATION LEVEL 陳述式的隔離等級 (Isolation Level)。 重複使用共用連接的後續連接會使用在共用連接時有效的隔離等級。  
  
 在連接內發出的個別查詢可包含修改單一陳述式或交易之隔離的鎖定提示，但不會影響連接的隔離等級。 預存程序或函式中設定的隔離等級或鎖定提示，不會變更呼叫它們之連接的隔離等級，並僅在預存程序或函式呼叫期間有效。  
  
 舊版 SQL Server 支援 SQL-92 標準中定義的四種隔離等級：  
  
-   READ UNCOMMITTED 是最為寬鬆的隔離等級，因為它會忽略其他交易設定的鎖定。 在 READ UNCOMMITTED 之下執行的交易可讀取其他交易尚未認可的已修改資料值；這種讀取稱為 Dirty 讀取。  
  
-   READ COMMITTED 是 SQL Server 的預設隔離等級。 它藉由指定陳述式不可讀取已修改但未獲得其他交易認可的資料值，來防止 Dirty 讀取。 在目前交易內個別陳述式執行之間，其他交易仍可修改、插入或刪除資料，這會導致不可重複的讀取，即「虛設」資料。  
  
-   REPEATABLE READ 隔離等級比 READ COMMITTED 嚴格。 它包含 READ COMMITTED，並額外指定任何其他交易都不可修改或刪除目前交易已讀取的資料，直到目前交易認可資料為止。 此時的並行存取較 READ COMMITTED 封閉，因為在交易期間會保持對讀取資料的共用鎖定，而不是在每個陳述式結束時釋放鎖定。  
  
-   SERIALIZABLE 是最嚴格的隔離等級，因為它會鎖定整個範圍的索引鍵，並保持鎖定直到交易完成。 它包含 REPEATABLE READ，並增加了在交易完成之前，其他交易不可在該交易已讀取的範圍內插入新資料列的限制。  
  
 如需詳細資訊，請參閱《SQL Server 線上叢書》的＜隔離等級＞。  
  
### <a name="snapshot-isolation-level-extensions"></a>快照隔離等級擴充  
 SQL Server 在引進 SNAPSHOT 隔離等級的同時，還引進了 SQL-92 隔離等級的擴充及 READ COMMITTED 的其他實作。 READ_COMMITTED_SNAPSHOT 隔離等級可透明化取代所有交易的 READ COMMITTED。  
  
-   SNAPSHOT 隔離指定交易內的資料讀取永遠不會反映其他同時進行之交易所進行的變更。 交易使用交易開始時存在的資料列版本。 讀取資料時不會對資料設定鎖定，因此 SNAPSHOT 交易不會阻止其他交易寫入資料。 寫入資料的交易不會阻止快照集交易讀取資料。 您需要藉由設定 ALLOW_SNAPSHOT_ISOLATION 資料庫選項來啟用快照集隔離，以便使用該隔離。  
  
-   READ_COMMITTED_SNAPSHOT 資料庫選項可判斷在資料庫中啟用快照集隔離時，預設 READ COMMITTED 隔離等級的行為。 如果您未明確指定 READ_COMMITTED_SNAPSHOT ON，則 READ COMMITTED 會套用至所有隱含交易。 如此會產生與設定 READ_COMMITTED_SNAPSHOT OFF (預設值) 相同的行為。 READ_COMMITTED_SNAPSHOT OFF 生效後，資料庫引擎會使用共用鎖定來強制執行預設的隔離等級。 如果將 READ_COMMITTED_SNAPSHOT 資料庫選項設為 ON，則資料庫引擎會使用資料列版本控制及快照集隔離做為預設值，而不是使用鎖定保護資料。  
  
## <a name="how-snapshot-isolation-and-row-versioning-work"></a>快照集隔離及資料列版本控制的運作方式  
 SQL Server Database Engine 的快照集隔離層級啟用時，每次更新一個資料列時，儲存原始資料列中的複本**tempdb**，並將交易序號加入資料列。 以下是事件的發生順序：  
  
-   初始新異動，並為其指派異動序號。  
  
-   資料庫引擎讀取異動內的資料列並擷取資料列版本，從**tempdb**序號是，最接近且低於的交易序號。  
  
-   資料庫引擎檢查該異動序號是否不在快照集異動開始時啟用之未認可異動的序號清單中。  
  
-   交易讀取的資料列版本**tempdb**是最新交易的開頭。 它不會看到異動開始後插入的新資料列，因為那些序號值會高於該異動序號值。  
  
-   目前的交易可以看到已刪除之後開始交易，因為會有資料列版本中的資料列**tempdb**值較低順序。  
  
 快照集隔離的唯一影響是異動可看到異動開始時就存在的所有資料，而不會在基底資料表上接受或設定鎖定。 在發生爭用時，這可提升效能。  
  
 快照集交易通常使用開放式同步存取控制，抑制任何可防止其他交易更新資料列的鎖定。 如果快照集交易嘗試認可對交易開始後發生變更之資料列的更新，則該交易會復原並將發生錯誤。  
  
## <a name="working-with-snapshot-isolation-in-adonet"></a>在 ADO.NET 中使用快照集隔離  
 ADO.NET 中的 <xref:System.Data.SqlClient.SqlTransaction> 類別支援快照集隔離。 如果資料庫已啟用快照集隔離，但不是設定 READ_COMMITTED_SNAPSHOT ON，您必須起始<xref:System.Data.SqlClient.SqlTransaction>使用**IsolationLevel.Snapshot**列舉值時呼叫<xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A>方法。 此程式碼片段假設連接是開啟的 <xref:System.Data.SqlClient.SqlConnection> 物件。  
  
```vb  
Dim sqlTran As SqlTransaction = _  
  connection.BeginTransaction(IsolationLevel.Snapshot)  
```  
  
```csharp  
SqlTransaction sqlTran =   
  connection.BeginTransaction(IsolationLevel.Snapshot);  
```  
  
### <a name="example"></a>範例  
 下列範例說明不同隔離等級嘗試存取鎖定資料的行為方式，該範例不適用於實際執行的程式碼。  
  
 程式碼連接至**AdventureWorks**範例 SQL Server 中的資料庫，並會建立名為**TestSnapshot**並插入一個資料列。 該程式碼使用 ALTER DATABASE Transact-SQL 陳述式來啟用資料庫的快照集隔離，但不會設定 READ_COMMITTED_SNAPSHOT 選項，而是讓預設的 READ COMMITTED 隔離等級行為生效。 然後，程式碼執行下列動作：  
  
-   它會開始但不完成 sqlTransaction1，其使用 SERIALIZABLE 隔離等級來啟動更新交易。 它的作用是鎖定資料表。  
  
-   它會開啟第二個連接並初始使用 SNAPSHOT 隔離等級來讀取的資料中的第二筆交易**TestSnapshot**資料表。 因為已啟用快照集隔離，所以此異動可讀取 sqlTransaction1 啟動之前存在的資料。  
  
-   它會開啟第三個連接並初始使用 READ COMMITTED 隔離等級的交易，以嘗試讀取資料表中的資料。 在這種情況下，程式碼無法讀取資料，因為第一個交易在資料表上設定的鎖定阻止其讀取資料並發生逾時。如果使用 REPEATABLE READ 及 SERIALIZABLE 隔離等級也會導致相同的結果，因為第一個交易設定的鎖定也會阻止這些隔離等級進行讀取。  
  
-   它會開啟第四個連接並初始使用 READ UNCOMMITTED 隔離等級的交易，其會執行對 sqlTransaction1 中未認可值的 Dirty 讀取。 若未認可第一個異動，則資料庫實際上可能從未擁有此值。  
  
-   它會復原第一筆交易，並透過刪除清除**TestSnapshot**資料表以及關閉快照集隔離的**AdventureWorks**資料庫。  
  
> [!NOTE]
>  下列範例在連接共用 (Connection Pooling) 關閉時會使用相同的連接字串。 如果共用連接，則重設其隔離等級並不會重設伺服器的隔離等級。 因此，使用同一共用內部連接的後續連接在啟動時的隔離等級會設定為共用連接的隔離等級。 關閉連接共用的方法之一，是明確地設定每個連接的隔離等級。  
  
 [!code-csharp[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.Demo#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.Demo/VB/source.vb#1)]  
  
### <a name="example"></a>範例  
 下列範例說明修改資料時快照集隔離的行為。 該程式碼執行下列動作：  
  
-   連接到**AdventureWorks**範例資料庫並啟用 SNAPSHOT 隔離。  
  
-   會建立名為**TestSnapshotUpdate**並插入三個範例資料列。  
  
-   開始使用 SNAPSHOT 隔離的 sqlTransaction1 但不完成它。 在異動中選取三個資料列。  
  
-   建立第二個**SqlConnection**至**AdventureWorks**並建立第二個交易，使用 READ COMMITTED 隔離等級會更新 sqlTransaction1 中選取的資料列的其中一個值。  
  
-   認可 sqlTransaction2。  
  
-   返回 sqlTransaction1 並嘗試更新 sqlTransaction1 已認可的同一資料列。 發生錯誤 3960，sqlTransaction1 自動復原。 **SqlException.Number**和**SqlException.Message**會顯示在主控台視窗。  
  
-   執行清除程式碼，在快照集隔離**AdventureWorks**和刪除**TestSnapshotUpdate**資料表。  
  
 [!code-csharp[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/CS/source.cs#1)]
 [!code-vb[DataWorks SnapshotIsolation.DemoUpdate#1](../../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SnapshotIsolation.DemoUpdate/VB/source.vb#1)]  
  
### <a name="using-lock-hints-with-snapshot-isolation"></a>搭配使用鎖定提示與快照集隔離  
 在前一範例中，第一筆交易選取了資料，而第二筆交易在第一筆交易尚未完成時就更新該資料，因而在第一筆交易嘗試更新同一資料列時發生更新衝突。 藉由在交易開始時提供鎖定提示，可減少長期執行之快照集交易發生更新衝突的機率。 下列 SELECT 陳述式使用 UPDLOCK 提示來鎖定已選取的資料列：  
  
```  
SELECT * FROM TestSnapshotUpdate WITH (UPDLOCK)   
  WHERE PriKey BETWEEN 1 AND 3  
```  
  
 使用 UPDLOCK 鎖定提示可阻止任何資料列在第一筆交易完成之前嘗試更新資料列。 如此可確保交易中在稍後更新選取的資料列時不會發生衝突。 請參閱《SQL Server 線上叢書》的＜鎖定提示＞。  
  
 如果應用程式有許多衝突，快照集隔離也許並非是最佳選擇。 僅在確實需要時才使用提示。 您的應用程式不應設計為必須依賴鎖定提示來執行作業。  
  
## <a name="see-also"></a>請參閱  
 [SQL Server 和 ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [ADO.NET Managed 提供者和 DataSet 開發人員中心](http://go.microsoft.com/fwlink/?LinkId=217917)
