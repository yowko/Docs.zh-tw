---
title: "異動和並行存取"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f46570de-9e50-4fe6-8710-a8c31fa8569b
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 6e6dfa946313bb9d43077bad68b761e8f03c175c
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/17/2018
---
# <a name="transactions-and-concurrency"></a><span data-ttu-id="b4d91-102">異動和並行存取</span><span class="sxs-lookup"><span data-stu-id="b4d91-102">Transactions and Concurrency</span></span>
<span data-ttu-id="b4d91-103">異動是由單一命令或當做封裝 (Package) 執行的命令群組所組成。</span><span class="sxs-lookup"><span data-stu-id="b4d91-103">A transaction consists of a single command or a group of commands that execute as a package.</span></span> <span data-ttu-id="b4d91-104">交易可讓您將多項作業結合成單一工作單位。</span><span class="sxs-lookup"><span data-stu-id="b4d91-104">Transactions allow you to combine multiple operations into a single unit of work.</span></span> <span data-ttu-id="b4d91-105">如果交易的某一處失敗，則所有更新都會復原到交易之前的狀態。</span><span class="sxs-lookup"><span data-stu-id="b4d91-105">If a failure occurs at one point in the transaction, all of the updates can be rolled back to their pre-transaction state.</span></span>  
  
 <span data-ttu-id="b4d91-106">交易必須符合 ACID 屬性 (單元性 (Atomicity)、一致性 (Consistency)、隔離性 (Isolation) 和持續性 (Durability)，才能保證資料一致性。</span><span class="sxs-lookup"><span data-stu-id="b4d91-106">A transaction must conform to the ACID properties—atomicity, consistency, isolation, and durability—in order to guarantee data consistency.</span></span> <span data-ttu-id="b4d91-107">大多數關聯式資料庫系統 (例如 Microsoft SQL Server) 都可以支援交易，其方法是在每次用戶端應用程式執行更新、插入或刪除作業時，提供鎖定、記錄和交易管理功能。</span><span class="sxs-lookup"><span data-stu-id="b4d91-107">Most relational database systems, such as Microsoft SQL Server, support transactions by providing locking, logging, and transaction management facilities whenever a client application performs an update, insert, or delete operation.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4d91-108">如果鎖定保留時間太久，包含多個資源的交易可能會降低並行。</span><span class="sxs-lookup"><span data-stu-id="b4d91-108">Transactions that involve multiple resources can lower concurrency if locks are held too long.</span></span> <span data-ttu-id="b4d91-109">因此，請盡可能縮短交易的時間長度。</span><span class="sxs-lookup"><span data-stu-id="b4d91-109">Therefore, keep transactions as short as possible.</span></span>  
  
 <span data-ttu-id="b4d91-110">如果某筆交易包含相同資料庫或伺服器中的多個資料表，則預存程序 (Stored Procedure) 中的明確交易通常會有較佳的效能。</span><span class="sxs-lookup"><span data-stu-id="b4d91-110">If a transaction involves multiple tables in the same database or server, then explicit transactions in stored procedures often perform better.</span></span> <span data-ttu-id="b4d91-111">您可以使用 Transact-SQL `BEGIN TRANSACTION`、`COMMIT TRANSACTION` 和 `ROLLBACK TRANSACTION` 陳述式，在 SQL Server 預存程序中建立交易。</span><span class="sxs-lookup"><span data-stu-id="b4d91-111">You can create transactions in SQL Server stored procedures by using the Transact-SQL `BEGIN TRANSACTION`, `COMMIT TRANSACTION`, and `ROLLBACK TRANSACTION` statements.</span></span> <span data-ttu-id="b4d91-112">如需詳細資訊，請參閱《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="b4d91-112">For more information, see SQL Server Books Online.</span></span>  
  
 <span data-ttu-id="b4d91-113">包含不同資源管理員的交易 (例如 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 與 Oracle 之間的交易) 需要分散式交易。</span><span class="sxs-lookup"><span data-stu-id="b4d91-113">Transactions involving different resource managers, such as a transaction between [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] and Oracle, require a distributed transaction.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b4d91-114">本節內容</span><span class="sxs-lookup"><span data-stu-id="b4d91-114">In This Section</span></span>  
 [<span data-ttu-id="b4d91-115">本機異動</span><span class="sxs-lookup"><span data-stu-id="b4d91-115">Local Transactions</span></span>](../../../../docs/framework/data/adonet/local-transactions.md)  
 <span data-ttu-id="b4d91-116">示範如何針對資料庫執行異動。</span><span class="sxs-lookup"><span data-stu-id="b4d91-116">Demonstrates how to perform transactions against a database.</span></span>  
  
 [<span data-ttu-id="b4d91-117">分散式異動</span><span class="sxs-lookup"><span data-stu-id="b4d91-117">Distributed Transactions</span></span>](../../../../docs/framework/data/adonet/distributed-transactions.md)  
 <span data-ttu-id="b4d91-118">說明如何在 ADO.NET 中執行分散式異動。</span><span class="sxs-lookup"><span data-stu-id="b4d91-118">Describes how to perform distributed transactions in ADO.NET.</span></span>  
  
 [<span data-ttu-id="b4d91-119">System.Transactions 與 SQL Server 整合</span><span class="sxs-lookup"><span data-stu-id="b4d91-119">System.Transactions Integration with SQL Server</span></span>](../../../../docs/framework/data/adonet/system-transactions-integration-with-sql-server.md)  
 <span data-ttu-id="b4d91-120">說明 <xref:System.Transactions> 如何與 [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] 整合以使用分散式交易。</span><span class="sxs-lookup"><span data-stu-id="b4d91-120">Describes <xref:System.Transactions> integration with [!INCLUDE[ssNoVersion](../../../../includes/ssnoversion-md.md)] for working with distributed transactions.</span></span>  
  
 [<span data-ttu-id="b4d91-121">開放式並行存取</span><span class="sxs-lookup"><span data-stu-id="b4d91-121">Optimistic Concurrency</span></span>](../../../../docs/framework/data/adonet/optimistic-concurrency.md)  
 <span data-ttu-id="b4d91-122">說明開放式與封閉式同步存取，以及如何測試並行違規。</span><span class="sxs-lookup"><span data-stu-id="b4d91-122">Describes optimistic and pessimistic concurrency, and how you can test for concurrency violations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4d91-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="b4d91-123">See Also</span></span>  
 [<span data-ttu-id="b4d91-124">交易基礎概念</span><span class="sxs-lookup"><span data-stu-id="b4d91-124">Transaction Fundamentals</span></span>](../../../../docs/framework/data/transactions/transaction-fundamentals.md)  
 [<span data-ttu-id="b4d91-125">連接至資料來源</span><span class="sxs-lookup"><span data-stu-id="b4d91-125">Connecting to a Data Source</span></span>](../../../../docs/framework/data/adonet/connecting-to-a-data-source.md)  
 [<span data-ttu-id="b4d91-126">命令和參數</span><span class="sxs-lookup"><span data-stu-id="b4d91-126">Commands and Parameters</span></span>](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [<span data-ttu-id="b4d91-127">DataAdapter 和 DataReader</span><span class="sxs-lookup"><span data-stu-id="b4d91-127">DataAdapters and DataReaders</span></span>](../../../../docs/framework/data/adonet/dataadapters-and-datareaders.md)  
 [<span data-ttu-id="b4d91-128">DbProviderFactories</span><span class="sxs-lookup"><span data-stu-id="b4d91-128">DbProviderFactories</span></span>](../../../../docs/framework/data/adonet/dbproviderfactories.md)  
 [<span data-ttu-id="b4d91-129">ADO.NET Managed 提供者和 DataSet 開發人員中心</span><span class="sxs-lookup"><span data-stu-id="b4d91-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
