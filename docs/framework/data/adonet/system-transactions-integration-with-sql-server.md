---
title: System.Transactions 與 SQL Server 整合
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: b555544e-7abb-4814-859b-ab9cdd7d8716
ms.openlocfilehash: 09fcf3f1a7e58a4bd8c2c6b0d25c24f32ea5ec5e
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880586"
---
# <a name="systemtransactions-integration-with-sql-server"></a><span data-ttu-id="d4891-102">System.Transactions 與 SQL Server 整合</span><span class="sxs-lookup"><span data-stu-id="d4891-102">System.Transactions Integration with SQL Server</span></span>
<span data-ttu-id="d4891-103">.NET Framework 2.0 版導入的交易架構，您可以透過<xref:System.Transactions>命名空間。</span><span class="sxs-lookup"><span data-stu-id="d4891-103">The .NET Framework version 2.0 introduced a transaction framework that can be accessed through the <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="d4891-104">此架構會公開在某種程度的完全整合在.NET Framework 中，包括 ADO.NET 中的交易。</span><span class="sxs-lookup"><span data-stu-id="d4891-104">This framework exposes transactions in a way that is fully integrated in the .NET Framework, including ADO.NET.</span></span>  
  
 <span data-ttu-id="d4891-105">可程式性增強功能，除了<xref:System.Transactions>，以及 ADO.NET 可以一起運作協調出最佳效能，當您使用交易時。</span><span class="sxs-lookup"><span data-stu-id="d4891-105">In addition to the programmability enhancements, <xref:System.Transactions> and ADO.NET can work together to coordinate optimizations when you work with transactions.</span></span> <span data-ttu-id="d4891-106">可提升的交易是可視需要自動提升為完全分散式交易的輕量型 (本機) 交易。</span><span class="sxs-lookup"><span data-stu-id="d4891-106">A promotable transaction is a lightweight (local) transaction that can be automatically promoted to a fully distributed transaction on an as-needed basis.</span></span>  
  
 <span data-ttu-id="d4891-107">從 ADO.NET 2.0 開始<xref:System.Data.SqlClient>支援可提升交易，當您使用 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="d4891-107">Starting with ADO.NET 2.0, <xref:System.Data.SqlClient> supports promotable transactions when you work with SQL Server.</span></span> <span data-ttu-id="d4891-108">除非需要已加入的負荷，否則可提升交易不會叫用分散式交易的已加入負荷。</span><span class="sxs-lookup"><span data-stu-id="d4891-108">A promotable transaction does not invoke the added overhead of a distributed transaction unless the added overhead is required.</span></span> <span data-ttu-id="d4891-109">可提升交易是自動的而且需要從開發人員不需要介入。</span><span class="sxs-lookup"><span data-stu-id="d4891-109">Promotable transactions are automatic and require no intervention from the developer.</span></span>  
  
 <span data-ttu-id="d4891-110">您可以使用.NET Framework Data Provider for SQL Server 時，才可以使用可提升交易 (`SqlClient`) 與 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="d4891-110">Promotable transactions are only available when you use the .NET Framework Data Provider for SQL Server (`SqlClient`) with SQL Server.</span></span>  
  
## <a name="creating-promotable-transactions"></a><span data-ttu-id="d4891-111">建立可提升交易</span><span class="sxs-lookup"><span data-stu-id="d4891-111">Creating Promotable Transactions</span></span>  
 <span data-ttu-id="d4891-112">.NET Framework Provider for SQL Server 支援可提升交易，都會透過.NET Framework 中的類別處理<xref:System.Transactions>命名空間。</span><span class="sxs-lookup"><span data-stu-id="d4891-112">The .NET Framework Provider for SQL Server provides support for promotable transactions, which are handled through the classes in the .NET Framework <xref:System.Transactions> namespace.</span></span> <span data-ttu-id="d4891-113">可提升交易藉由直到需要時才建立分散式交易的方式，來最佳化分散式交易。</span><span class="sxs-lookup"><span data-stu-id="d4891-113">Promotable transactions optimize distributed transactions by deferring creating a distributed transaction until it is needed.</span></span> <span data-ttu-id="d4891-114">如果只需要一個資源管理員，則不會發生分散式交易。</span><span class="sxs-lookup"><span data-stu-id="d4891-114">If only one resource manager is required, no distributed transaction occurs.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4891-115">在部分信任案例中，當某筆交易提升至分散式交易時， <xref:System.Transactions.DistributedTransactionPermission> 就是必要項目。</span><span class="sxs-lookup"><span data-stu-id="d4891-115">In a partially trusted scenario, the <xref:System.Transactions.DistributedTransactionPermission> is required when a transaction is promoted to a distributed transaction.</span></span>  
  
## <a name="promotable-transaction-scenarios"></a><span data-ttu-id="d4891-116">可提升交易案例</span><span class="sxs-lookup"><span data-stu-id="d4891-116">Promotable Transaction Scenarios</span></span>  
 <span data-ttu-id="d4891-117">分散式交易通常要耗用大量的系統資源，並由「Microsoft 分散式交易協調器 (MS DTC)」進行管理，其整合了交易中會存取的所有資源管理者。</span><span class="sxs-lookup"><span data-stu-id="d4891-117">Distributed transactions typically consume significant system resources, being managed by Microsoft Distributed Transaction Coordinator (MS DTC), which integrates all the resource managers accessed in the transaction.</span></span> <span data-ttu-id="d4891-118">可提升交易是一種特殊形式的<xref:System.Transactions>有效地委派工作給簡單的 SQL Server 交易的交易。</span><span class="sxs-lookup"><span data-stu-id="d4891-118">A promotable transaction is a special form of a <xref:System.Transactions> transaction that effectively delegates the work to a simple SQL Server transaction.</span></span> <span data-ttu-id="d4891-119"><xref:System.Transactions><xref:System.Data.SqlClient>，和 SQL Server 在視需要將其提升為完全分散式交易協調參與處理交易的工作。</span><span class="sxs-lookup"><span data-stu-id="d4891-119"><xref:System.Transactions>, <xref:System.Data.SqlClient>, and SQL Server coordinate the work involved in handling the transaction, promoting it to a full distributed transaction as needed.</span></span>  
  
 <span data-ttu-id="d4891-120">使用可提升交易的好處是：當以作用中的 <xref:System.Transactions.TransactionScope> 交易開啟連接，且未開啟其他連接時，會將交易認可為輕量型交易，不會產生完全分散式交易的額外負擔。</span><span class="sxs-lookup"><span data-stu-id="d4891-120">The benefit of using promotable transactions is that when a connection is opened by using an active <xref:System.Transactions.TransactionScope> transaction, and no other connections are opened, the transaction commits as a lightweight transaction, instead of incurring the additional overhead of a full distributed transaction.</span></span>  
  
### <a name="connection-string-keywords"></a><span data-ttu-id="d4891-121">連接字串關鍵字</span><span class="sxs-lookup"><span data-stu-id="d4891-121">Connection String Keywords</span></span>  
 <span data-ttu-id="d4891-122"><xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> 屬性支援關鍵字 `Enlist`，它表示 <xref:System.Data.SqlClient> 是否會偵測到交易內容，並自動在分散式交易中登記連接。</span><span class="sxs-lookup"><span data-stu-id="d4891-122">The <xref:System.Data.SqlClient.SqlConnection.ConnectionString%2A> property supports a keyword, `Enlist`, which indicates whether <xref:System.Data.SqlClient> will detect transactional contexts and automatically enlist the connection in a distributed transaction.</span></span> <span data-ttu-id="d4891-123">如果 `Enlist=true`，則會在開啟之執行緒的目前交易內容中自動登記連接。</span><span class="sxs-lookup"><span data-stu-id="d4891-123">If `Enlist=true`, the connection is automatically enlisted in the opening thread's current transaction context.</span></span> <span data-ttu-id="d4891-124">如果 `Enlist=false`，則 `SqlClient` 連接將不會與分散式交易進行互動。</span><span class="sxs-lookup"><span data-stu-id="d4891-124">If `Enlist=false`, the `SqlClient` connection does not interact with a distributed transaction.</span></span> <span data-ttu-id="d4891-125">`Enlist` 的預設值為 True。</span><span class="sxs-lookup"><span data-stu-id="d4891-125">The default value for `Enlist` is true.</span></span> <span data-ttu-id="d4891-126">如果未在連接字串中指定 `Enlist` ，則若在開啟連接時偵測到連接，便會自動在分散式交易中登記該連接。</span><span class="sxs-lookup"><span data-stu-id="d4891-126">If `Enlist` is not specified in the connection string, the connection is automatically enlisted in a distributed transaction if one is detected when the connection is opened.</span></span>  
  
 <span data-ttu-id="d4891-127">在 `Transaction Binding` 連接字串中的 <xref:System.Data.SqlClient.SqlConnection> 關鍵字會控制連接與已登記 `System.Transactions` 交易之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="d4891-127">The `Transaction Binding` keywords in a <xref:System.Data.SqlClient.SqlConnection> connection string control the connection's association with an enlisted `System.Transactions` transaction.</span></span> <span data-ttu-id="d4891-128">這也可以透過 <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> 的 <xref:System.Data.SqlClient.SqlConnectionStringBuilder>屬性取得。</span><span class="sxs-lookup"><span data-stu-id="d4891-128">It is also available through the <xref:System.Data.SqlClient.SqlConnectionStringBuilder.TransactionBinding%2A> property of a <xref:System.Data.SqlClient.SqlConnectionStringBuilder>.</span></span>  
  
 <span data-ttu-id="d4891-129">下表說明可能出現的值。</span><span class="sxs-lookup"><span data-stu-id="d4891-129">The following table describes the possible values.</span></span>  
  
|<span data-ttu-id="d4891-130">關鍵字</span><span class="sxs-lookup"><span data-stu-id="d4891-130">Keyword</span></span>|<span data-ttu-id="d4891-131">描述</span><span class="sxs-lookup"><span data-stu-id="d4891-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d4891-132">Implicit Unbind</span><span class="sxs-lookup"><span data-stu-id="d4891-132">Implicit Unbind</span></span>|<span data-ttu-id="d4891-133">預設值。</span><span class="sxs-lookup"><span data-stu-id="d4891-133">The default.</span></span> <span data-ttu-id="d4891-134">結束時，連接會與交易中斷連結，並切換回自動認可模式。</span><span class="sxs-lookup"><span data-stu-id="d4891-134">The connection detaches from the transaction when it ends, switching back to autocommit mode.</span></span>|  
|<span data-ttu-id="d4891-135">Explicit Unbind</span><span class="sxs-lookup"><span data-stu-id="d4891-135">Explicit Unbind</span></span>|<span data-ttu-id="d4891-136">連接會維持附加至交易的狀態，直到交易關閉為止。</span><span class="sxs-lookup"><span data-stu-id="d4891-136">The connection remains attached to the transaction until the transaction is closed.</span></span> <span data-ttu-id="d4891-137">如果相關聯的交易並非使用中或與 <xref:System.Transactions.Transaction.Current%2A>不符，連接將會失敗。</span><span class="sxs-lookup"><span data-stu-id="d4891-137">The connection will fail if the associated transaction is not active or does not match <xref:System.Transactions.Transaction.Current%2A>.</span></span>|  
  
## <a name="using-transactionscope"></a><span data-ttu-id="d4891-138">使用 TransactionScope</span><span class="sxs-lookup"><span data-stu-id="d4891-138">Using TransactionScope</span></span>  
 <span data-ttu-id="d4891-139"><xref:System.Transactions.TransactionScope> 類別可藉由在分散式交易中隱含地登記連接，來使程式碼區塊可進行交易。</span><span class="sxs-lookup"><span data-stu-id="d4891-139">The <xref:System.Transactions.TransactionScope> class makes a code block transactional by implicitly enlisting connections in a distributed transaction.</span></span> <span data-ttu-id="d4891-140">離開區塊之前，您必須呼叫 <xref:System.Transactions.TransactionScope.Complete%2A> 區塊結尾的 <xref:System.Transactions.TransactionScope> 方法。</span><span class="sxs-lookup"><span data-stu-id="d4891-140">You must call the <xref:System.Transactions.TransactionScope.Complete%2A> method at the end of the <xref:System.Transactions.TransactionScope> block before leaving it.</span></span> <span data-ttu-id="d4891-141">離開區塊會叫用 <xref:System.Transactions.TransactionScope.Dispose%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="d4891-141">Leaving the block invokes the <xref:System.Transactions.TransactionScope.Dispose%2A> method.</span></span> <span data-ttu-id="d4891-142">如果已擲回造成程式碼離開範圍的例外狀況，則會將交易視為中止。</span><span class="sxs-lookup"><span data-stu-id="d4891-142">If an exception has been thrown that causes the code to leave scope, the transaction is considered aborted.</span></span>  
  
 <span data-ttu-id="d4891-143">建議您使用 `using` 區塊，以確保結束 using 區塊時，會在 <xref:System.Transactions.TransactionScope.Dispose%2A> 物件上呼叫 <xref:System.Transactions.TransactionScope> 。</span><span class="sxs-lookup"><span data-stu-id="d4891-143">We recommend that you use a `using` block to make sure that <xref:System.Transactions.TransactionScope.Dispose%2A> is called on the <xref:System.Transactions.TransactionScope> object when the using block is exited.</span></span> <span data-ttu-id="d4891-144">無法認可或復原暫止的交易會嚴重損害效能，因為 default time-out for the <xref:System.Transactions.TransactionScope> 的預設逾時是 1 分鐘。</span><span class="sxs-lookup"><span data-stu-id="d4891-144">Failure to commit or roll back pending transactions can significantly damage performance because the default time-out for the <xref:System.Transactions.TransactionScope> is one minute.</span></span> <span data-ttu-id="d4891-145">如果您不使用 `using` 陳述式，則必須在 `Try` 區塊中執行所有工作，並明確呼叫 <xref:System.Transactions.TransactionScope.Dispose%2A> 區塊中的 `Finally` 方法。</span><span class="sxs-lookup"><span data-stu-id="d4891-145">If you do not use a `using` statement, you must perform all work in a `Try` block and explicitly call the <xref:System.Transactions.TransactionScope.Dispose%2A> method in the `Finally` block.</span></span>  
  
 <span data-ttu-id="d4891-146">如果 <xref:System.Transactions.TransactionScope>中發生例外狀況，則會將交易標記為不一致並放棄。</span><span class="sxs-lookup"><span data-stu-id="d4891-146">If an exception occurs in the <xref:System.Transactions.TransactionScope>, the transaction is marked as inconsistent and is abandoned.</span></span> <span data-ttu-id="d4891-147">處置 <xref:System.Transactions.TransactionScope> 時，則會復原該交易。</span><span class="sxs-lookup"><span data-stu-id="d4891-147">It will be rolled back when the <xref:System.Transactions.TransactionScope> is disposed.</span></span> <span data-ttu-id="d4891-148">如果沒有發生任何例外狀況，則會認可參與的交易。</span><span class="sxs-lookup"><span data-stu-id="d4891-148">If no exception occurs, participating transactions commit.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4891-149">根據預設， `TransactionScope` 類別會建立其 <xref:System.Transactions.Transaction.IsolationLevel%2A> 為 `Serializable` 的交易。</span><span class="sxs-lookup"><span data-stu-id="d4891-149">The `TransactionScope` class creates a transaction with a <xref:System.Transactions.Transaction.IsolationLevel%2A> of `Serializable` by default.</span></span> <span data-ttu-id="d4891-150">根據應用程式，您可能會考慮降低隔離等級，以避免應用程式中發生劇烈的爭用現象。</span><span class="sxs-lookup"><span data-stu-id="d4891-150">Depending on your application, you might want to consider lowering the isolation level to avoid high contention in your application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d4891-151">建議您在分散式交易內僅執行更新、插入及刪除作業，因為它們會耗用大量的資料庫資源。</span><span class="sxs-lookup"><span data-stu-id="d4891-151">We recommend that you perform only updates, inserts, and deletes within distributed transactions because they consume significant database resources.</span></span> <span data-ttu-id="d4891-152">SELECT 陳述式可能會不必要地鎖定資料庫資源，而在某些案例中，您可能需要使用交易而不是選取。</span><span class="sxs-lookup"><span data-stu-id="d4891-152">Select statements may lock database resources unnecessarily, and in some scenarios, you may have to use transactions for selects.</span></span> <span data-ttu-id="d4891-153">除非涉及其他已交易的資源管理者，否則所有非資料庫工作都應在交易範圍外執行。</span><span class="sxs-lookup"><span data-stu-id="d4891-153">Any non-database work should be done outside the scope of the transaction, unless it involves other transacted resource managers.</span></span> <span data-ttu-id="d4891-154">雖然交易範圍內的例外狀況會防止認可交易，但 <xref:System.Transactions.TransactionScope> 類別不支援針對在交易本身範圍外所做的任何程式碼變更進行復原。</span><span class="sxs-lookup"><span data-stu-id="d4891-154">Although an exception in the scope of the transaction prevents the transaction from committing, the <xref:System.Transactions.TransactionScope> class has no provision for rolling back any changes your code has made outside the scope of the transaction itself.</span></span> <span data-ttu-id="d4891-155">如果在復原交易時需要採取某些動作，則必須撰寫您自己的 <xref:System.Transactions.IEnlistmentNotification> 介面實作，並在交易中明確登記。</span><span class="sxs-lookup"><span data-stu-id="d4891-155">If you have to take some action when the transaction is rolled back, you must write your own implementation of the <xref:System.Transactions.IEnlistmentNotification> interface and explicitly enlist in the transaction.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4891-156">範例</span><span class="sxs-lookup"><span data-stu-id="d4891-156">Example</span></span>  
 <span data-ttu-id="d4891-157">您需要參考 System.Transactions.dll，才能使用 <xref:System.Transactions> 。</span><span class="sxs-lookup"><span data-stu-id="d4891-157">Working with <xref:System.Transactions> requires that you have a reference to System.Transactions.dll.</span></span>  
  
 <span data-ttu-id="d4891-158">下列函式示範如何針對由兩個不同的 <xref:System.Data.SqlClient.SqlConnection> 物件表示，並包裝於 <xref:System.Transactions.TransactionScope> 區塊中的兩個不同 SQL Server 執行個體，建立可提升交易。</span><span class="sxs-lookup"><span data-stu-id="d4891-158">The following function demonstrates how to create a promotable transaction against two different SQL Server instances, represented by two different <xref:System.Data.SqlClient.SqlConnection> objects, which are wrapped in a <xref:System.Transactions.TransactionScope> block.</span></span> <span data-ttu-id="d4891-159">程式碼會使用 <xref:System.Transactions.TransactionScope> 陳述式來建立 `using` 區塊，並開啟第一個連接，這樣會自動在 <xref:System.Transactions.TransactionScope>中登記它。</span><span class="sxs-lookup"><span data-stu-id="d4891-159">The code creates the <xref:System.Transactions.TransactionScope> block with a `using` statement and opens the first connection, which automatically enlists it in the <xref:System.Transactions.TransactionScope>.</span></span> <span data-ttu-id="d4891-160">一開始交易登記為輕量型交易，而不是完全分散式交易。</span><span class="sxs-lookup"><span data-stu-id="d4891-160">The transaction is initially enlisted as a lightweight transaction, not a full distributed transaction.</span></span> <span data-ttu-id="d4891-161">只有當第一個連接中的命令沒有擲回例外狀況時，第二個連接才會登記於 <xref:System.Transactions.TransactionScope> 中。</span><span class="sxs-lookup"><span data-stu-id="d4891-161">The second connection is enlisted in the <xref:System.Transactions.TransactionScope> only if the command in the first connection does not throw an exception.</span></span> <span data-ttu-id="d4891-162">開啟第二個連接時，交易會自動提升為完全分散式交易。</span><span class="sxs-lookup"><span data-stu-id="d4891-162">When the second connection is opened, the transaction is automatically promoted to a full distributed transaction.</span></span> <span data-ttu-id="d4891-163">此時，系統會叫用 <xref:System.Transactions.TransactionScope.Complete%2A> 方法，但是它只有在沒有擲回任何例外狀況時才會認可交易。</span><span class="sxs-lookup"><span data-stu-id="d4891-163">The <xref:System.Transactions.TransactionScope.Complete%2A> method is invoked, which commits the transaction only if no exceptions have been thrown.</span></span> <span data-ttu-id="d4891-164">如果在 <xref:System.Transactions.TransactionScope> 區塊中的任何一點擲回例外狀況，便不會呼叫 `Complete` ，且分散式交易會在 <xref:System.Transactions.TransactionScope> 區塊結束並處置 `using` 時復原。</span><span class="sxs-lookup"><span data-stu-id="d4891-164">If an exception has been thrown at any point in the <xref:System.Transactions.TransactionScope> block, `Complete` will not be called, and the distributed transaction will roll back when the <xref:System.Transactions.TransactionScope> is disposed at the end of its `using` block.</span></span>  
  
```csharp  
// This function takes arguments for the 2 connection strings and commands in order  
// to create a transaction involving two SQL Servers. It returns a value > 0 if the  
// transaction committed, 0 if the transaction rolled back. To test this code, you can   
// connect to two different databases on the same server by altering the connection string,  
// or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
static public int CreateTransactionScope(  
    string connectString1, string connectString2,  
    string commandText1, string commandText2)  
{  
    // Initialize the return value to zero and create a StringWriter to display results.  
    int returnValue = 0;  
    System.IO.StringWriter writer = new System.IO.StringWriter();  
  
    // Create the TransactionScope in which to execute the commands, guaranteeing  
    // that both commands will commit or roll back as a single unit of work.  
    using (TransactionScope scope = new TransactionScope())  
    {  
        using (SqlConnection connection1 = new SqlConnection(connectString1))  
        {  
            try  
            {  
                // Opening the connection automatically enlists it in the   
                // TransactionScope as a lightweight transaction.  
                connection1.Open();  
  
                // Create the SqlCommand object and execute the first command.  
                SqlCommand command1 = new SqlCommand(commandText1, connection1);  
                returnValue = command1.ExecuteNonQuery();  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue);  
  
                // if you get here, this means that command1 succeeded. By nesting  
                // the using block for connection2 inside that of connection1, you  
                // conserve server and network resources by opening connection2   
                // only when there is a chance that the transaction can commit.     
                using (SqlConnection connection2 = new SqlConnection(connectString2))  
                    try  
                    {  
                        // The transaction is promoted to a full distributed  
                        // transaction when connection2 is opened.  
                        connection2.Open();  
  
                        // Execute the second command in the second database.  
                        returnValue = 0;  
                        SqlCommand command2 = new SqlCommand(commandText2, connection2);  
                        returnValue = command2.ExecuteNonQuery();  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue);  
                    }  
                    catch (Exception ex)  
                    {  
                        // Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue);  
                        writer.WriteLine("Exception Message2: {0}", ex.Message);  
                    }  
            }  
            catch (Exception ex)  
            {  
                // Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue);  
                writer.WriteLine("Exception Message1: {0}", ex.Message);  
            }  
        }  
  
        // If an exception has been thrown, Complete will not   
        // be called and the transaction is rolled back.  
        scope.Complete();  
    }  
  
    // The returnValue is greater than 0 if the transaction committed.  
    if (returnValue > 0)  
    {  
        writer.WriteLine("Transaction was committed.");  
    }  
    else  
    {  
        // You could write additional business logic here, notify the caller by  
        // throwing a TransactionAbortedException, or log the failure.  
        writer.WriteLine("Transaction rolled back.");  
    }  
  
    // Display messages.  
    Console.WriteLine(writer.ToString());  
  
    return returnValue;  
}  
```  
  
```vb  
' This function takes arguments for the 2 connection strings and commands in order  
' to create a transaction involving two SQL Servers. It returns a value > 0 if the  
' transaction committed, 0 if the transaction rolled back. To test this code, you can   
' connect to two different databases on the same server by altering the connection string,  
' or to another RDBMS such as Oracle by altering the code in the connection2 code block.  
Public Function CreateTransactionScope( _  
  ByVal connectString1 As String, ByVal connectString2 As String, _  
  ByVal commandText1 As String, ByVal commandText2 As String) As Integer  
  
    ' Initialize the return value to zero and create a StringWriter to display results.  
    Dim returnValue As Integer = 0  
    Dim writer As System.IO.StringWriter = New System.IO.StringWriter  
  
    ' Create the TransactionScope in which to execute the commands, guaranteeing  
    ' that both commands will commit or roll back as a single unit of work.  
    Using scope As New TransactionScope()  
        Using connection1 As New SqlConnection(connectString1)  
            Try  
                ' Opening the connection automatically enlists it in the   
                ' TransactionScope as a lightweight transaction.  
                connection1.Open()  
  
                ' Create the SqlCommand object and execute the first command.  
                Dim command1 As SqlCommand = New SqlCommand(commandText1, connection1)  
                returnValue = command1.ExecuteNonQuery()  
                writer.WriteLine("Rows to be affected by command1: {0}", returnValue)  
  
                ' If you get here, this means that command1 succeeded. By nesting  
                ' the Using block for connection2 inside that of connection1, you  
                ' conserve server and network resources by opening connection2   
                ' only when there is a chance that the transaction can commit.     
                Using connection2 As New SqlConnection(connectString2)  
                    Try  
                        ' The transaction is promoted to a full distributed  
                        ' transaction when connection2 is opened.  
                        connection2.Open()  
  
                        ' Execute the second command in the second database.  
                        returnValue = 0  
                        Dim command2 As SqlCommand = New SqlCommand(commandText2, connection2)  
                        returnValue = command2.ExecuteNonQuery()  
                        writer.WriteLine("Rows to be affected by command2: {0}", returnValue)  
  
                    Catch ex As Exception  
                        ' Display information that command2 failed.  
                        writer.WriteLine("returnValue for command2: {0}", returnValue)  
                        writer.WriteLine("Exception Message2: {0}", ex.Message)  
                    End Try  
                End Using  
  
            Catch ex As Exception  
                ' Display information that command1 failed.  
                writer.WriteLine("returnValue for command1: {0}", returnValue)  
                writer.WriteLine("Exception Message1: {0}", ex.Message)  
            End Try  
        End Using  
  
        ' If an exception has been thrown, Complete will   
        ' not be called and the transaction is rolled back.  
        scope.Complete()  
    End Using  
  
    ' The returnValue is greater than 0 if the transaction committed.  
    If returnValue > 0 Then  
        writer.WriteLine("Transaction was committed.")  
    Else  
        ' You could write additional business logic here, notify the caller by  
        ' throwing a TransactionAbortedException, or log the failure.  
       writer.WriteLine("Transaction rolled back.")  
     End If  
  
    ' Display messages.  
    Console.WriteLine(writer.ToString())  
  
    Return returnValue  
End Function  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4891-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4891-165">See also</span></span>

- [<span data-ttu-id="d4891-166">異動和並行存取</span><span class="sxs-lookup"><span data-stu-id="d4891-166">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)
- [<span data-ttu-id="d4891-167">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="d4891-167">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
