---
title: 啟用 Multiple Active Result Sets
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 576079e4-debe-4ab5-9204-fcbe2ca7a5e2
ms.openlocfilehash: 70e589fcff241a664ef470dfeb746412cde6b515
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54570196"
---
# <a name="enabling-multiple-active-result-sets"></a><span data-ttu-id="b4748-102">啟用 Multiple Active Result Sets</span><span class="sxs-lookup"><span data-stu-id="b4748-102">Enabling Multiple Active Result Sets</span></span>
<span data-ttu-id="b4748-103">Multiple Active Result Set (MARS) 是與 SQL Server 搭配使用的功能，它允許在單一連接中執行多個批次作業。</span><span class="sxs-lookup"><span data-stu-id="b4748-103">Multiple Active Result Sets (MARS) is a feature that works with SQL Server to allow the execution of multiple batches on a single connection.</span></span> <span data-ttu-id="b4748-104">啟用 MARS 以與 SQL Server 搭配使用時，使用的每個命令物件都會在連接中加入工作階段。</span><span class="sxs-lookup"><span data-stu-id="b4748-104">When MARS is enabled for use with SQL Server, each command object used adds a session to the connection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4748-105">單一的 MARS 工作階段會開啟一個邏輯連接供 MARS 使用，然後再針對每個使用中的命令開啟邏輯連接。</span><span class="sxs-lookup"><span data-stu-id="b4748-105">A single MARS session opens one logical connection for MARS to use and then one logical connection for each active command.</span></span>  
  
## <a name="enabling-and-disabling-mars-in-the-connection-string"></a><span data-ttu-id="b4748-106">在連接字串中啟用及停用 MARS</span><span class="sxs-lookup"><span data-stu-id="b4748-106">Enabling and Disabling MARS in the Connection String</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4748-107">下列連接字串使用範例**AdventureWorks**隨附於 SQL Server 的資料庫。</span><span class="sxs-lookup"><span data-stu-id="b4748-107">The following connection strings use the sample **AdventureWorks** database included with SQL Server.</span></span> <span data-ttu-id="b4748-108">提供的連接字串會假設伺服器上已安裝名為 MSSQL1 的資料庫。</span><span class="sxs-lookup"><span data-stu-id="b4748-108">The connection strings provided assume that the database is installed on a server named MSSQL1.</span></span> <span data-ttu-id="b4748-109">視環境需要修改連接字串。</span><span class="sxs-lookup"><span data-stu-id="b4748-109">Modify the connection string as necessary for your environment.</span></span>  
  
 <span data-ttu-id="b4748-110">預設會停用 MARS 功能。</span><span class="sxs-lookup"><span data-stu-id="b4748-110">The MARS feature is disabled by default.</span></span> <span data-ttu-id="b4748-111">藉由將 "MultipleActiveResultSets=True" 關鍵字配對加入連接字串，可啟用該功能。</span><span class="sxs-lookup"><span data-stu-id="b4748-111">It can be enabled by adding the "MultipleActiveResultSets=True" keyword pair to your connection string.</span></span> <span data-ttu-id="b4748-112">"True" 是啟用 MARS 的唯一有效值。</span><span class="sxs-lookup"><span data-stu-id="b4748-112">"True" is the only valid value for enabling MARS.</span></span> <span data-ttu-id="b4748-113">下列範例會說明如何連接至 SQL Server 的執行個體，以及如何指定應該啟用 MARS。</span><span class="sxs-lookup"><span data-stu-id="b4748-113">The following example demonstrates how to connect to an instance of SQL Server and how to specify that MARS should be enabled.</span></span>  
  
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
  
 <span data-ttu-id="b4748-114">藉由將 "MultipleActiveResultSets=False" 關鍵字配對加入連接字串，可停用 MARS。</span><span class="sxs-lookup"><span data-stu-id="b4748-114">You can disable MARS by adding the "MultipleActiveResultSets=False" keyword pair to your connection string.</span></span> <span data-ttu-id="b4748-115">"False" 是停用 MARS 的唯一有效值。</span><span class="sxs-lookup"><span data-stu-id="b4748-115">"False" is the only valid value for disabling MARS.</span></span> <span data-ttu-id="b4748-116">下列連接字串會示範如何停用 MARS。</span><span class="sxs-lookup"><span data-stu-id="b4748-116">The following connection string demonstrates how to disable MARS.</span></span>  
  
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
  
## <a name="special-considerations-when-using-mars"></a><span data-ttu-id="b4748-117">使用 MARS 時的特殊考量</span><span class="sxs-lookup"><span data-stu-id="b4748-117">Special Considerations When Using MARS</span></span>  
 <span data-ttu-id="b4748-118">一般而言，現有應用程式不需修改即可使用啟用 MARS 的連接。</span><span class="sxs-lookup"><span data-stu-id="b4748-118">In general, existing applications should not need modification to use a MARS-enabled connection.</span></span> <span data-ttu-id="b4748-119">但是，如果您要在應用程式中使用 MARS 功能，應了解下列特殊考量。</span><span class="sxs-lookup"><span data-stu-id="b4748-119">However, if you wish to use MARS features in your applications, you should understand the following special considerations.</span></span>  
  
### <a name="statement-interleaving"></a><span data-ttu-id="b4748-120">陳述式交錯</span><span class="sxs-lookup"><span data-stu-id="b4748-120">Statement Interleaving</span></span>  
 <span data-ttu-id="b4748-121">MARS 作業會在伺服器上同步執行。</span><span class="sxs-lookup"><span data-stu-id="b4748-121">MARS operations execute synchronously on the server.</span></span> <span data-ttu-id="b4748-122">允許 SELECT 及 BULK INSERT 陳述式的陳述式交錯。</span><span class="sxs-lookup"><span data-stu-id="b4748-122">Statement interleaving of SELECT and BULK INSERT statements is allowed.</span></span> <span data-ttu-id="b4748-123">但是，資料管理語言 (DML) 及資料定義語言 (DDL) 陳述式會以原子方式執行。</span><span class="sxs-lookup"><span data-stu-id="b4748-123">However, data manipulation language (DML) and data definition language (DDL) statements execute atomically.</span></span> <span data-ttu-id="b4748-124">嘗試於原子批次執行時執行的任何陳述式都會被封鎖。</span><span class="sxs-lookup"><span data-stu-id="b4748-124">Any statements attempting to execute while an atomic batch is executing are blocked.</span></span> <span data-ttu-id="b4748-125">伺服器的平行執行不是 MARS 功能。</span><span class="sxs-lookup"><span data-stu-id="b4748-125">Parallel execution at the server is not a MARS feature.</span></span>  
  
 <span data-ttu-id="b4748-126">如果在 MARS 連接下送出兩個批次作業，其中一個包含 SELECT 陳述式，另一個包含 DML 陳述式，則可以在執行 SELECT 陳述式時開始執行 DML。</span><span class="sxs-lookup"><span data-stu-id="b4748-126">If two batches are submitted under a MARS connection, one of them containing a SELECT statement, the other containing a DML statement, the DML can begin execution within execution of the SELECT statement.</span></span> <span data-ttu-id="b4748-127">不過，DML 陳述式必須先完成執行，才能繼續執行 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="b4748-127">However, the DML statement must run to completion before the SELECT statement can make progress.</span></span> <span data-ttu-id="b4748-128">如果兩個陳述式同時在同一個交易下執行，則 DML 陳述式在 SELECT 陳述式已開始執行後所進行的任何變更，對於讀取作業都是不可見的。</span><span class="sxs-lookup"><span data-stu-id="b4748-128">If both statements are running under the same transaction, any changes made by a DML statement after the SELECT statement has started execution are not visible to the read operation.</span></span>  
  
 <span data-ttu-id="b4748-129">SELECT 陳述式內的 WAITFOR 陳述式在等待期間，即產生第一個資料列之前，不會產生交易。</span><span class="sxs-lookup"><span data-stu-id="b4748-129">A WAITFOR statement inside a SELECT statement does not yield the transaction while it is waiting, that is, until the first row is produced.</span></span> <span data-ttu-id="b4748-130">這表示在 WAITFOR 陳述式等待期間，無法在同一連接內執行其他批次作業。</span><span class="sxs-lookup"><span data-stu-id="b4748-130">This implies that no other batches can execute within the same connection while a WAITFOR statement is waiting.</span></span>  
  
### <a name="mars-session-cache"></a><span data-ttu-id="b4748-131">MARS 工作階段快取</span><span class="sxs-lookup"><span data-stu-id="b4748-131">MARS Session Cache</span></span>  
 <span data-ttu-id="b4748-132">開啟啟用 MARS 的連接時，會建立邏輯工作階段，如此會增加額外負荷。</span><span class="sxs-lookup"><span data-stu-id="b4748-132">When a connection is opened with MARS enabled, a logical session is created, which adds additional overhead.</span></span> <span data-ttu-id="b4748-133">若要最小化負荷並提高效能， **SqlClient**快取連接內的 MARS 工作階段。</span><span class="sxs-lookup"><span data-stu-id="b4748-133">To minimize overhead and enhance performance, **SqlClient** caches the MARS session within a connection.</span></span> <span data-ttu-id="b4748-134">快取包含最多 10 個 MARS 工作階段。</span><span class="sxs-lookup"><span data-stu-id="b4748-134">The cache contains at most 10 MARS sessions.</span></span> <span data-ttu-id="b4748-135">使用者不可調整此值。</span><span class="sxs-lookup"><span data-stu-id="b4748-135">This value is not user adjustable.</span></span> <span data-ttu-id="b4748-136">如果達到工作階段限制，則會建立新的工作階段而不會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="b4748-136">If the session limit is reached, a new session is created—an error is not generated.</span></span> <span data-ttu-id="b4748-137">其中包含的快取及工作階段是以每個連接為基礎的，不可跨連接共用。</span><span class="sxs-lookup"><span data-stu-id="b4748-137">The cache and sessions contained in it are per-connection; they are not shared across connections.</span></span> <span data-ttu-id="b4748-138">釋放工作階段時，會將其傳回集區，直至達到集區上限為止。</span><span class="sxs-lookup"><span data-stu-id="b4748-138">When a session is released, it is returned to the pool unless the pool's upper limit has been reached.</span></span> <span data-ttu-id="b4748-139">如果快取集區已滿，則工作階段會關閉。</span><span class="sxs-lookup"><span data-stu-id="b4748-139">If the cache pool is full, the session is closed.</span></span> <span data-ttu-id="b4748-140">MARS 工作階段不會過期。</span><span class="sxs-lookup"><span data-stu-id="b4748-140">MARS sessions do not expire.</span></span> <span data-ttu-id="b4748-141">只會在處置連接物件時清除它們。</span><span class="sxs-lookup"><span data-stu-id="b4748-141">They are only cleaned up when the connection object is disposed.</span></span> <span data-ttu-id="b4748-142">MARS 工作階段快取不會預先載入。</span><span class="sxs-lookup"><span data-stu-id="b4748-142">The MARS session cache is not preloaded.</span></span> <span data-ttu-id="b4748-143">應用程式需要更多工作階段時會將其載入。</span><span class="sxs-lookup"><span data-stu-id="b4748-143">It is loaded as the application requires more sessions.</span></span>  
  
### <a name="thread-safety"></a><span data-ttu-id="b4748-144">執行緒安全</span><span class="sxs-lookup"><span data-stu-id="b4748-144">Thread Safety</span></span>  
 <span data-ttu-id="b4748-145">MARS 作業不是安全執行緒。</span><span class="sxs-lookup"><span data-stu-id="b4748-145">MARS operations are not thread-safe.</span></span>  
  
### <a name="connection-pooling"></a><span data-ttu-id="b4748-146">連接共用</span><span class="sxs-lookup"><span data-stu-id="b4748-146">Connection Pooling</span></span>  
 <span data-ttu-id="b4748-147">啟用 MARS 的連接共用方式與其他連接一樣。</span><span class="sxs-lookup"><span data-stu-id="b4748-147">MARS-enabled connections are pooled like any other connection.</span></span> <span data-ttu-id="b4748-148">如果應用程式開啟兩個連接，一個啟用 MARS，另一個停用 MARS，則兩個連接會位於不同的集區中。</span><span class="sxs-lookup"><span data-stu-id="b4748-148">If an application opens two connections, one with MARS enabled and one with MARS disabled, the two connections are in separate pools.</span></span> <span data-ttu-id="b4748-149">如需詳細資訊，請參閱 [SQL Server 連共用ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md)。</span><span class="sxs-lookup"><span data-stu-id="b4748-149">For more information, see [SQL Server Connection Pooling (ADO.NET)](../../../../../docs/framework/data/adonet/sql-server-connection-pooling.md).</span></span>  
  
### <a name="sql-server-batch-execution-environment"></a><span data-ttu-id="b4748-150">SQL Server 批次執行環境</span><span class="sxs-lookup"><span data-stu-id="b4748-150">SQL Server Batch Execution Environment</span></span>  
 <span data-ttu-id="b4748-151">連接開啟時，會定義預設的環境。</span><span class="sxs-lookup"><span data-stu-id="b4748-151">When a connection is opened, a default environment is defined.</span></span> <span data-ttu-id="b4748-152">然後會將此環境複製到邏輯 MARS 工作階段。</span><span class="sxs-lookup"><span data-stu-id="b4748-152">This environment is then copied into a logical MARS session.</span></span>  
  
 <span data-ttu-id="b4748-153">批次執行環境包含下列元件：</span><span class="sxs-lookup"><span data-stu-id="b4748-153">The batch execution environment includes the following components:</span></span>  
  
-   <span data-ttu-id="b4748-154">設定選項 (例如，ANSI_NULLS、DATE_FORMAT、LANGUAGE、TEXTSIZE)</span><span class="sxs-lookup"><span data-stu-id="b4748-154">Set options (for example, ANSI_NULLS, DATE_FORMAT, LANGUAGE, TEXTSIZE)</span></span>  
  
-   <span data-ttu-id="b4748-155">安全性內容 (使用者/應用程式角色)</span><span class="sxs-lookup"><span data-stu-id="b4748-155">Security context (user/application role)</span></span>  
  
-   <span data-ttu-id="b4748-156">資料庫內容 (目前資料庫)</span><span class="sxs-lookup"><span data-stu-id="b4748-156">Database context (current database)</span></span>  
  
-   <span data-ttu-id="b4748-157">執行狀態變數 (例如，@@ERROR，@@ROWCOUNT，@@FETCH_STATUS @@IDENTITY)</span><span class="sxs-lookup"><span data-stu-id="b4748-157">Execution state variables (for example, @@ERROR, @@ROWCOUNT, @@FETCH_STATUS @@IDENTITY)</span></span>  
  
-   <span data-ttu-id="b4748-158">最上層暫存資料表</span><span class="sxs-lookup"><span data-stu-id="b4748-158">Top-level temporary tables</span></span>  
  
 <span data-ttu-id="b4748-159">使用 MARS，預設的執行環境可與連接產生關聯。</span><span class="sxs-lookup"><span data-stu-id="b4748-159">With MARS, a default execution environment is associated to a connection.</span></span> <span data-ttu-id="b4748-160">在指定連接下開始執行的每個新批次作業，都會收到預設環境的複本。</span><span class="sxs-lookup"><span data-stu-id="b4748-160">Every new batch that starts executing under a given connection receives a copy of the default environment.</span></span> <span data-ttu-id="b4748-161">每當程式碼在指定批次作業下執行時，對環境所做的所有變更都只限於該特定批次作業。</span><span class="sxs-lookup"><span data-stu-id="b4748-161">Whenever code is executed under a given batch, all changes made to the environment are scoped to the specific batch.</span></span> <span data-ttu-id="b4748-162">執行一旦完成，便會將執行設定複製到預設環境中。</span><span class="sxs-lookup"><span data-stu-id="b4748-162">Once execution finishes, the execution settings are copied into the default environment.</span></span> <span data-ttu-id="b4748-163">當單一批次作業發出要在同一交易下循序執行的數個命令時，其語意與舊版用戶端或伺服器相關的連接所公開的語意相同。</span><span class="sxs-lookup"><span data-stu-id="b4748-163">In the case of a single batch issuing several commands to be executed sequentially under the same transaction, semantics are the same as those exposed by connections involving earlier clients or servers.</span></span>  
  
### <a name="parallel-execution"></a><span data-ttu-id="b4748-164">平行執行</span><span class="sxs-lookup"><span data-stu-id="b4748-164">Parallel Execution</span></span>  
 <span data-ttu-id="b4748-165">MARS 未設計為在應用程式內移除對多重連接的所有需求。</span><span class="sxs-lookup"><span data-stu-id="b4748-165">MARS is not designed to remove all requirements for multiple connections in an application.</span></span> <span data-ttu-id="b4748-166">如果應用程式確實需要針對伺服器平行執行命令，則應使用多重連接。</span><span class="sxs-lookup"><span data-stu-id="b4748-166">If an application needs true parallel execution of commands against a server, multiple connections should be used.</span></span>  
  
 <span data-ttu-id="b4748-167">例如，請考量下列案例。</span><span class="sxs-lookup"><span data-stu-id="b4748-167">For example, consider the following scenario.</span></span> <span data-ttu-id="b4748-168">建立兩個命令物件，一個用於處理結果集，另一個用於更新資料，它們透過 MARS 共用通用連接。</span><span class="sxs-lookup"><span data-stu-id="b4748-168">Two command objects are created, one for processing a result set and another for updating data; they share a common connection via MARS.</span></span> <span data-ttu-id="b4748-169">在此案例中， `Transaction`。`Commit`</span><span class="sxs-lookup"><span data-stu-id="b4748-169">In this scenario, the `Transaction`.`Commit`</span></span> <span data-ttu-id="b4748-170">更新失敗，直到在第一個命令物件，進而產生下列例外狀況已讀取所有結果：</span><span class="sxs-lookup"><span data-stu-id="b4748-170">fails on the update until all the results have been read on the first command object, yielding the following exception:</span></span>  
  
 <span data-ttu-id="b4748-171">訊息：其他工作階段正在使用交易內容。</span><span class="sxs-lookup"><span data-stu-id="b4748-171">Message: Transaction context in use by another session.</span></span>  
  
 <span data-ttu-id="b4748-172">來源：.Net SqlClient Data Provider</span><span class="sxs-lookup"><span data-stu-id="b4748-172">Source: .Net SqlClient Data Provider</span></span>  
  
 <span data-ttu-id="b4748-173">預期：(null)</span><span class="sxs-lookup"><span data-stu-id="b4748-173">Expected: (null)</span></span>  
  
 <span data-ttu-id="b4748-174">已接收：System.Data.SqlClient.SqlException</span><span class="sxs-lookup"><span data-stu-id="b4748-174">Received: System.Data.SqlClient.SqlException</span></span>  
  
 <span data-ttu-id="b4748-175">處理此案例有三個選項：</span><span class="sxs-lookup"><span data-stu-id="b4748-175">There are three options for handling this scenario:</span></span>  
  
1.  <span data-ttu-id="b4748-176">在建立讀取器後啟動交易，使其不會成為交易的一部分。</span><span class="sxs-lookup"><span data-stu-id="b4748-176">Start the transaction after the reader is created, so that it is not part of the transaction.</span></span> <span data-ttu-id="b4748-177">然後每個更新會成為其自身的交易。</span><span class="sxs-lookup"><span data-stu-id="b4748-177">Every update then becomes its own transaction.</span></span>  
  
2.  <span data-ttu-id="b4748-178">在讀取器關閉後認可所有工作。</span><span class="sxs-lookup"><span data-stu-id="b4748-178">Commit all work after the reader is closed.</span></span> <span data-ttu-id="b4748-179">如此可能會發生大量批次的更新。</span><span class="sxs-lookup"><span data-stu-id="b4748-179">This has the potential for a substantial batch of updates.</span></span>  
  
3.  <span data-ttu-id="b4748-180">請勿針對每個命令物件使用 MARS，而是使用 MARS 之前的單獨連接。</span><span class="sxs-lookup"><span data-stu-id="b4748-180">Don't use MARS; instead use a separate connection for each command object as you would have before MARS.</span></span>  
  
### <a name="detecting-mars-support"></a><span data-ttu-id="b4748-181">偵測 MARS 支援</span><span class="sxs-lookup"><span data-stu-id="b4748-181">Detecting MARS Support</span></span>  
 <span data-ttu-id="b4748-182">應用程式可以藉由讀取 `SqlConnection.ServerVersion` 值來檢查 MARS 支援。</span><span class="sxs-lookup"><span data-stu-id="b4748-182">An application can check for MARS support by reading the `SqlConnection.ServerVersion` value.</span></span> <span data-ttu-id="b4748-183">SQL Server 2005 和 SQL Server 2008 的主版本號碼應為分別為 9 和 10。</span><span class="sxs-lookup"><span data-stu-id="b4748-183">The major number should be 9 for SQL Server 2005 and 10 for SQL Server 2008.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4748-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4748-184">See also</span></span>
- [<span data-ttu-id="b4748-185">Multiple Active Result Set (MARS)</span><span class="sxs-lookup"><span data-stu-id="b4748-185">Multiple Active Result Sets (MARS)</span></span>](../../../../../docs/framework/data/adonet/sql/multiple-active-result-sets-mars.md)
- [<span data-ttu-id="b4748-186">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="b4748-186">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
