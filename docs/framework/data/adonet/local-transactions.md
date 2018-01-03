---
title: "本機異動"
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
ms.assetid: 8ae3712f-ef5e-41a1-9ea9-b3d0399439f1
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: f7b002c1439a95929ca177aeced91164430220c6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="local-transactions"></a><span data-ttu-id="2f85a-102">本機異動</span><span class="sxs-lookup"><span data-stu-id="2f85a-102">Local Transactions</span></span>
<span data-ttu-id="2f85a-103">當您要將多個工作繫結在一起，以讓它們當做單一的工作單位來執行時，便會使用 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 中的交易。</span><span class="sxs-lookup"><span data-stu-id="2f85a-103">Transactions in [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] are used when you want to bind multiple tasks together so that they execute as a single unit of work.</span></span> <span data-ttu-id="2f85a-104">例如，想像應用程式正在執行兩項工作。</span><span class="sxs-lookup"><span data-stu-id="2f85a-104">For example, imagine that an application performs two tasks.</span></span> <span data-ttu-id="2f85a-105">首先，它會更新包含訂單資訊的資料表。</span><span class="sxs-lookup"><span data-stu-id="2f85a-105">First, it updates a table with order information.</span></span> <span data-ttu-id="2f85a-106">然後會更新包含存貨資訊的資料表，將訂購項目記入借方。</span><span class="sxs-lookup"><span data-stu-id="2f85a-106">Second, it updates a table that contains inventory information, debiting the items ordered.</span></span> <span data-ttu-id="2f85a-107">如果其中任何一項失敗，然後這兩個更新會回復。</span><span class="sxs-lookup"><span data-stu-id="2f85a-107">If either task fails, then both updates are rolled back.</span></span>  
  
## <a name="determining-the-transaction-type"></a><span data-ttu-id="2f85a-108">決定異動類型</span><span class="sxs-lookup"><span data-stu-id="2f85a-108">Determining the Transaction Type</span></span>  
 <span data-ttu-id="2f85a-109">交易是被視為本機交易時它是單一階段交易並直接處理資料庫。</span><span class="sxs-lookup"><span data-stu-id="2f85a-109">A transaction is considered to be a local transaction when it is a single-phase transaction and is handled by the database directly.</span></span> <span data-ttu-id="2f85a-110">交易是被視為分散式的交易時，它由交易監視器進行協調，並使用保全機制 （如兩階段認可） 進行異動解析。</span><span class="sxs-lookup"><span data-stu-id="2f85a-110">A transaction is considered to be a distributed transaction when it is coordinated by a transaction monitor and uses fail-safe mechanisms (such as two-phase commit) for transaction resolution.</span></span>  
  
 <span data-ttu-id="2f85a-111">每個 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 資料提供者都有它自己的 `Transaction` 物件，以執行本機交易。</span><span class="sxs-lookup"><span data-stu-id="2f85a-111">Each of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] data providers has its own `Transaction` object for performing local transactions.</span></span> <span data-ttu-id="2f85a-112">如果您需要在 SQL Server 資料庫中執行交易，請選擇 <xref:System.Data.SqlClient> 交易。</span><span class="sxs-lookup"><span data-stu-id="2f85a-112">If you require a transaction to be performed in a SQL Server database, select a <xref:System.Data.SqlClient> transaction.</span></span> <span data-ttu-id="2f85a-113">若為 Oracle 交易，請使用 <xref:System.Data.OracleClient> 提供者。</span><span class="sxs-lookup"><span data-stu-id="2f85a-113">For an Oracle transaction, use the <xref:System.Data.OracleClient> provider.</span></span> <span data-ttu-id="2f85a-114">此外，新 <xref:System.Data.Common.DbTransaction> 類別可用於寫入獨立於提供者以外且需要交易的程式碼。</span><span class="sxs-lookup"><span data-stu-id="2f85a-114">In addition, there is a new <xref:System.Data.Common.DbTransaction> class that is available for writing provider-independent code that requires transactions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f85a-115">在伺服器上執行交易是最有效率的。</span><span class="sxs-lookup"><span data-stu-id="2f85a-115">Transactions are most efficient when it is performed on the server.</span></span> <span data-ttu-id="2f85a-116">如果您使用的 SQL Server 資料庫大量使用明確的交易，請考慮使用 Transact-SQL BEGIN TRANSACTION 陳述式，將它們寫入為預存程序。</span><span class="sxs-lookup"><span data-stu-id="2f85a-116">If you are working with a SQL Server database that makes extensive use of explicit transactions, consider writing them as stored procedures using the Transact-SQL BEGIN TRANSACTION statement.</span></span> <span data-ttu-id="2f85a-117">如需執行伺服器端交易的詳細資訊，請參閱《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="2f85a-117">For more information about performing server-side transactions, see SQL Server Books Online.</span></span>  
  
## <a name="performing-a-transaction-using-a-single-connection"></a><span data-ttu-id="2f85a-118">使用單一連接執行交易</span><span class="sxs-lookup"><span data-stu-id="2f85a-118">Performing a Transaction Using a Single Connection</span></span>  
 <span data-ttu-id="2f85a-119">在 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 中，您會使用 `Connection` 物件控制交易。</span><span class="sxs-lookup"><span data-stu-id="2f85a-119">In [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], you control transactions with the `Connection` object.</span></span> <span data-ttu-id="2f85a-120">您可使用 `BeginTransaction` 方法來起始本機交易。</span><span class="sxs-lookup"><span data-stu-id="2f85a-120">You can initiate a local transaction with the `BeginTransaction` method.</span></span> <span data-ttu-id="2f85a-121">開始交易之後，您可使用 `Transaction` 物件的 `Command` 屬性，在該交易中登記命令。</span><span class="sxs-lookup"><span data-stu-id="2f85a-121">Once you have begun a transaction, you can enlist a command in that transaction with the `Transaction` property of a `Command` object.</span></span> <span data-ttu-id="2f85a-122">然後，您可根據交易元件的成敗，來認可或復原對資料來源所做的修改。</span><span class="sxs-lookup"><span data-stu-id="2f85a-122">You can then commit or roll back modifications made at the data source based on the success or failure of the components of the transaction.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f85a-123">`EnlistDistributedTransaction` 方法不可用於本機交易。</span><span class="sxs-lookup"><span data-stu-id="2f85a-123">The `EnlistDistributedTransaction` method should not be used for a local transaction.</span></span>  
  
 <span data-ttu-id="2f85a-124">交易的範圍僅限於連接。</span><span class="sxs-lookup"><span data-stu-id="2f85a-124">The scope of the transaction is limited to the connection.</span></span> <span data-ttu-id="2f85a-125">下列範例執行由 `try` 區塊中的兩個單獨命令所組成的明確交易。</span><span class="sxs-lookup"><span data-stu-id="2f85a-125">The following example performs an explicit transaction that consists of two separate commands in the `try` block.</span></span> <span data-ttu-id="2f85a-126">這些命令會針對 AdventureWorks [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 範例資料庫中的 Production.ScrapReason 資料表執行 INSERT 陳述式，如果未擲回例外狀況，該陳述式便會得到認可。</span><span class="sxs-lookup"><span data-stu-id="2f85a-126">The commands execute INSERT statements against the Production.ScrapReason table in the AdventureWorks [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] sample database, which are committed if no exceptions are thrown.</span></span> <span data-ttu-id="2f85a-127">如果擲回例外狀況，則 `catch` 區塊中的程式碼便會復原交易。</span><span class="sxs-lookup"><span data-stu-id="2f85a-127">The code in the `catch` block rolls back the transaction if an exception is thrown.</span></span> <span data-ttu-id="2f85a-128">如果交易在完成之前遭到中止或連接關閉，則會自動復原該交易。</span><span class="sxs-lookup"><span data-stu-id="2f85a-128">If the transaction is aborted or the connection is closed before the transaction has completed, it is automatically rolled back.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f85a-129">範例</span><span class="sxs-lookup"><span data-stu-id="2f85a-129">Example</span></span>  
 <span data-ttu-id="2f85a-130">請遵循下列步驟來執行交易。</span><span class="sxs-lookup"><span data-stu-id="2f85a-130">Follow these steps to perform a transaction.</span></span>  
  
1.  <span data-ttu-id="2f85a-131">呼叫 <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> 物件的 <xref:System.Data.SqlClient.SqlConnection> 方法，來標記交易的開始。</span><span class="sxs-lookup"><span data-stu-id="2f85a-131">Call the <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> method of the <xref:System.Data.SqlClient.SqlConnection> object to mark the start of the transaction.</span></span> <span data-ttu-id="2f85a-132"><xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> 方法會將參考傳回給交易。</span><span class="sxs-lookup"><span data-stu-id="2f85a-132">The <xref:System.Data.SqlClient.SqlConnection.BeginTransaction%2A> method returns a reference to the transaction.</span></span> <span data-ttu-id="2f85a-133">此參考會指派給登記在交易中的 <xref:System.Data.SqlClient.SqlCommand> 物件。</span><span class="sxs-lookup"><span data-stu-id="2f85a-133">This reference is assigned to the <xref:System.Data.SqlClient.SqlCommand> objects that are enlisted in the transaction.</span></span>  
  
2.  <span data-ttu-id="2f85a-134">將 `Transaction` 物件指派給要執行之 <xref:System.Data.SqlClient.SqlCommand.Transaction%2A> 的 <xref:System.Data.SqlClient.SqlCommand> 屬性。</span><span class="sxs-lookup"><span data-stu-id="2f85a-134">Assign the `Transaction` object to the <xref:System.Data.SqlClient.SqlCommand.Transaction%2A> property of the <xref:System.Data.SqlClient.SqlCommand> to be executed.</span></span> <span data-ttu-id="2f85a-135">如果在有交易正在作用中的連接上執行命令，且 `Transaction` 物件尚未指派給 `Transaction` 物件的 `Command` 屬性，便會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2f85a-135">If a command is executed on a connection with an active transaction, and the `Transaction` object has not been assigned to the `Transaction` property of the `Command` object, an exception is thrown.</span></span>  
  
3.  <span data-ttu-id="2f85a-136">執行必要的命令。</span><span class="sxs-lookup"><span data-stu-id="2f85a-136">Execute the required commands.</span></span>  
  
4.  <span data-ttu-id="2f85a-137">呼叫 <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> 物件的 <xref:System.Data.SqlClient.SqlTransaction> 方法來完成交易，或呼叫 <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> 方法來中止交易。</span><span class="sxs-lookup"><span data-stu-id="2f85a-137">Call the <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> method of the <xref:System.Data.SqlClient.SqlTransaction> object to complete the transaction, or call the <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> method to end the transaction.</span></span> <span data-ttu-id="2f85a-138">如果在執行 <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> 或 <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> 方法之前關閉或處置連接，則會復原交易。</span><span class="sxs-lookup"><span data-stu-id="2f85a-138">If the connection is closed or disposed before either the <xref:System.Data.SqlClient.SqlTransaction.Commit%2A> or <xref:System.Data.SqlClient.SqlTransaction.Rollback%2A> methods have been executed, the transaction is rolled back.</span></span>  
  
 <span data-ttu-id="2f85a-139">下列程式碼範例會藉由搭配使用 [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] 與 Microsoft SQL Server 來示範交易邏輯。</span><span class="sxs-lookup"><span data-stu-id="2f85a-139">The following code example demonstrates transactional logic using [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] with Microsoft SQL Server.</span></span>  
  
 [!code-csharp[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/CS/source.cs#1)]
 [!code-vb[DataWorks SqlTransaction.Local#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlTransaction.Local/VB/source.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2f85a-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="2f85a-140">See Also</span></span>  
 [<span data-ttu-id="2f85a-141">異動和並行存取</span><span class="sxs-lookup"><span data-stu-id="2f85a-141">Transactions and Concurrency</span></span>](../../../../docs/framework/data/adonet/transactions-and-concurrency.md)  
 [<span data-ttu-id="2f85a-142">分散式異動</span><span class="sxs-lookup"><span data-stu-id="2f85a-142">Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 [<span data-ttu-id="2f85a-143">System.Transactions 與 SQL Server 整合</span><span class="sxs-lookup"><span data-stu-id="2f85a-143">System.Transactions Integration with SQL Server</span></span>](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 [<span data-ttu-id="2f85a-144">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="2f85a-144">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
