---
title: "使用 DependentTransaction 管理並行存取"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b85a97d8-8e02-4555-95df-34c8af095148
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ffda721459ef81d148d55359362fe1aeaf9e699e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="managing-concurrency-with-dependenttransaction"></a><span data-ttu-id="f0b12-102">使用 DependentTransaction 管理並行存取</span><span class="sxs-lookup"><span data-stu-id="f0b12-102">Managing Concurrency with DependentTransaction</span></span>
<span data-ttu-id="f0b12-103"><xref:System.Transactions.Transaction> 物件係使用 <xref:System.Transactions.Transaction.DependentClone%2A> 方法建立。</span><span class="sxs-lookup"><span data-stu-id="f0b12-103">The <xref:System.Transactions.Transaction> object is created using the <xref:System.Transactions.Transaction.DependentClone%2A> method.</span></span> <span data-ttu-id="f0b12-104">其唯一目的在於保證當其他程式碼片段 (例如，背景工作執行緒仍在執行交易工作時，不會認可交易。</span><span class="sxs-lookup"><span data-stu-id="f0b12-104">Its sole purpose is to guarantee that the transaction cannot commit while some other pieces of code (for example, a worker thread) are still performing work on the transaction.</span></span> <span data-ttu-id="f0b12-105">當完成並準備好認可在複製之交易中所執行的工作時，可以使用 <xref:System.Transactions.DependentTransaction.Complete%2A> 方法來通知交易的建立者。</span><span class="sxs-lookup"><span data-stu-id="f0b12-105">When the work done within the cloned transaction is complete and ready to be committed, it can notify the creator of the transaction using the <xref:System.Transactions.DependentTransaction.Complete%2A> method.</span></span> <span data-ttu-id="f0b12-106">這麼一來，您便可保持資料的一致性和正確性。</span><span class="sxs-lookup"><span data-stu-id="f0b12-106">Thus, you can preserve the consistency and correctness of data.</span></span>  
  
 <span data-ttu-id="f0b12-107">您也可以使用 <xref:System.Transactions.DependentTransaction> 類別來管理非同步工作之間的並行存取。</span><span class="sxs-lookup"><span data-stu-id="f0b12-107">The <xref:System.Transactions.DependentTransaction> class can also be used to manage concurrency between asynchronous tasks.</span></span> <span data-ttu-id="f0b12-108">在此情況下，當相依的複製工作在執行自己的工作時，父項仍舊可以繼續執行任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="f0b12-108">In this scenario, the parent can continue to execute any code while the dependent clone works on its own tasks.</span></span> <span data-ttu-id="f0b12-109">換句話說，不管相依項是否完成工作，都不會影響父項執行工作。</span><span class="sxs-lookup"><span data-stu-id="f0b12-109">In other words, the parent's execution is not blocked until the dependent completes.</span></span>  
  
## <a name="creating-a-dependent-clone"></a><span data-ttu-id="f0b12-110">建立相依的複製品</span><span class="sxs-lookup"><span data-stu-id="f0b12-110">Creating a Dependent Clone</span></span>  
 <span data-ttu-id="f0b12-111">若要建立相依的交易，請呼叫 <xref:System.Transactions.Transaction.DependentClone%2A> 方法，並將 <xref:System.Transactions.DependentCloneOption> 列舉型別當成參數傳送出去。</span><span class="sxs-lookup"><span data-stu-id="f0b12-111">To create a dependent transaction, call the <xref:System.Transactions.Transaction.DependentClone%2A> method and pass the <xref:System.Transactions.DependentCloneOption> enumeration as a parameter.</span></span> <span data-ttu-id="f0b12-112">在相依的複製品表示它以準備好認可交易 (藉由呼叫 `Commit` 方法) 之前，如果在父交易呼叫 <xref:System.Transactions.DependentTransaction.Complete%2A> 的話，此參數將會定義交易行為。</span><span class="sxs-lookup"><span data-stu-id="f0b12-112">This parameter defines the behavior of the transaction if `Commit` is called on the parent transaction before the dependent clone indicates that it is ready for the transaction to commit (by calling the <xref:System.Transactions.DependentTransaction.Complete%2A> method).</span></span> <span data-ttu-id="f0b12-113">下列各值為此參數可用的有效值：</span><span class="sxs-lookup"><span data-stu-id="f0b12-113">The following values are valid for this parameter:</span></span>  
  
-   <span data-ttu-id="f0b12-114"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> 會建立在父交易逾時之前，或直到在所有表示已完成交易的相依項上呼叫 <xref:System.Transactions.DependentTransaction.Complete%2A> 時，封鎖父交易之認可處理序的相依交易。</span><span class="sxs-lookup"><span data-stu-id="f0b12-114"><xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> creates a dependent transaction that blocks the commit process of the parent transaction until the parent transaction times out, or until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on all dependents indicating their completion.</span></span> <span data-ttu-id="f0b12-115">當用戶端不想在完成相依交易之前即認可父交易時，這個參數就會非常有用。</span><span class="sxs-lookup"><span data-stu-id="f0b12-115">This is useful when the client does not want the parent transaction to commit until the dependent transactions have completed.</span></span> <span data-ttu-id="f0b12-116">如果父項比相依交易早一步完成工作，並在交易上呼叫 <xref:System.Transactions.CommittableTransaction.Commit%2A>，則會將認可處理序封鎖在某個狀態下。在此狀態下，您仍可以在交易上執行其他工作，並建立新的登記，直到所有相依項都呼叫 <xref:System.Transactions.DependentTransaction.Complete%2A> 為止。</span><span class="sxs-lookup"><span data-stu-id="f0b12-116">If the parent finishes its work earlier than the dependent transaction and calls <xref:System.Transactions.CommittableTransaction.Commit%2A> on the transaction, the commit process is blocked in a state where additional work can be done on the transaction and new enlistments can be created, until all of the dependents call <xref:System.Transactions.DependentTransaction.Complete%2A>.</span></span> <span data-ttu-id="f0b12-117">一旦全部都完成各自的工作並呼叫 <xref:System.Transactions.DependentTransaction.Complete%2A>，就會馬上開始交易的認可處理序。</span><span class="sxs-lookup"><span data-stu-id="f0b12-117">As soon as all of them have finished their work and call <xref:System.Transactions.DependentTransaction.Complete%2A>, the commit process for the transaction begins.</span></span>  
  
-   <span data-ttu-id="f0b12-118">另一方面，如果在呼叫 <xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete> 之前，先在父交易上呼叫了 <xref:System.Transactions.CommittableTransaction.Commit%2A>，則 <xref:System.Transactions.DependentTransaction.Complete%2A> 會建立能自動中止的相依交易。</span><span class="sxs-lookup"><span data-stu-id="f0b12-118"><xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete>, on the other hand, creates a dependent transaction that automatically aborts if <xref:System.Transactions.CommittableTransaction.Commit%2A> is called on the parent transaction before <xref:System.Transactions.DependentTransaction.Complete%2A> is called.</span></span> <span data-ttu-id="f0b12-119">在此情況下，所有在相依交易中完成的工作會保留一段交易存留期不變，而且沒人有機會認可其中一部分。</span><span class="sxs-lookup"><span data-stu-id="f0b12-119">In this case, all the work done in the dependent transaction is intact within one transaction lifetime, and no one has a chance to commit just a portion of it.</span></span>  
  
 <span data-ttu-id="f0b12-120">當您的應用程式完成了在相依交易上的工作，必須呼叫 <xref:System.Transactions.DependentTransaction.Complete%2A> 方法一次 (而且只能一次)；否則，會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="f0b12-120">The <xref:System.Transactions.DependentTransaction.Complete%2A> method must be called only once when your application finishes its work on the dependent transaction; otherwise, a <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="f0b12-121">在叫用這個呼叫後，您不應嘗試在交易上執行任何額外的工作，否則會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f0b12-121">After this call is invoked, you must not attempt any additional work on the transaction, or an exception is thrown.</span></span>  
  
 <span data-ttu-id="f0b12-122">下列程式碼範例說明如何藉由複製相依的交易並將其傳遞至背景工作執行緒，來建立相依交易以管理兩個並行的工作。</span><span class="sxs-lookup"><span data-stu-id="f0b12-122">The following code example shows how to create a dependent transaction to manage two concurrent tasks by cloning a dependent transaction and passing it to a worker thread.</span></span>  
  
```csharp  
public class WorkerThread  
{  
    public void DoWork(DependentTransaction dependentTransaction)  
    {  
        Thread thread = new Thread(ThreadMethod);  
        thread.Start(dependentTransaction);   
    }  
  
    public void ThreadMethod(object transaction)   
    {   
        DependentTransaction dependentTransaction = transaction as DependentTransaction;  
        Debug.Assert(dependentTransaction != null);   
        try  
        {  
            using(TransactionScope ts = new TransactionScope(dependentTransaction))  
            {  
                /* Perform transactional work here */   
                ts.Complete();  
            }  
        }  
        finally  
        {  
            dependentTransaction.Complete();   
             dependentTransaction.Dispose();   
        }  
    }  
  
//Client code   
using(TransactionScope scope = new TransactionScope())  
{  
    Transaction currentTransaction = Transaction.Current;  
    DependentTransaction dependentTransaction;      
    dependentTransaction = currentTransaction.DependentClone(DependentCloneOption.BlockCommitUntilComplete);  
    WorkerThread workerThread = new WorkerThread();  
    workerThread.DoWork(dependentTransaction);  
    /* Do some transactional work here, then: */  
    scope.Complete();  
}  
```  
  
 <span data-ttu-id="f0b12-123">用戶端程式碼可建立同時能設定環境交易的交易範圍。</span><span class="sxs-lookup"><span data-stu-id="f0b12-123">The client code creates a transactional scope that also sets the ambient transaction.</span></span> <span data-ttu-id="f0b12-124">您不應該將環境交易傳遞至背景工作執行緒。</span><span class="sxs-lookup"><span data-stu-id="f0b12-124">You should not pass the ambient transaction to the worker thread.</span></span> <span data-ttu-id="f0b12-125">反之，您應該呼叫目前交易上的 <xref:System.Transactions.Transaction.DependentClone%2A> 方法來複製目前 (環境) 交易，並將相依交易傳遞給背景工作執行緒。</span><span class="sxs-lookup"><span data-stu-id="f0b12-125">Instead, you should clone the current (ambient) transaction by calling the <xref:System.Transactions.Transaction.DependentClone%2A> method on the current transaction, and pass the dependent to the worker thread.</span></span>  
  
 <span data-ttu-id="f0b12-126">`ThreadMethod` 方法會在新執行緒上執行。</span><span class="sxs-lookup"><span data-stu-id="f0b12-126">The `ThreadMethod` method executes on the new thread.</span></span> <span data-ttu-id="f0b12-127">用戶端開始新的執行緒後，會將相依交易當成 `ThreadMethod` 參數傳送出去。</span><span class="sxs-lookup"><span data-stu-id="f0b12-127">The client starts a new thread, passing the dependent transaction as the `ThreadMethod` parameter.</span></span>  
  
 <span data-ttu-id="f0b12-128">由於相依交易係由 <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> 所建立，因此可以保證直到第二個執行緒上所有執行的交易工作都已完成，並且在相依交易上呼叫 <xref:System.Transactions.DependentTransaction.Complete%2A> 後，才會認可交易。</span><span class="sxs-lookup"><span data-stu-id="f0b12-128">Because the dependent transaction is created with <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete>, you are guaranteed that the transaction cannot be committed until all of the transactional work done on the second thread is finished and <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent transaction.</span></span> <span data-ttu-id="f0b12-129">這表示，如果用戶端的範圍結束 (當它嘗試處置交易物件的結尾**使用**陳述式) 的新的執行緒呼叫之前<xref:System.Transactions.DependentTransaction.Complete%2A>相依的交易，直到會封鎖用戶端程式碼<xref:System.Transactions.DependentTransaction.Complete%2A>相依項上呼叫。</span><span class="sxs-lookup"><span data-stu-id="f0b12-129">This means that if the client's scope ends (when it tries to dispose of the transaction object at the end of the **using** statement) before the new thread calls <xref:System.Transactions.DependentTransaction.Complete%2A> on the dependent transaction, the client code blocks until <xref:System.Transactions.DependentTransaction.Complete%2A> is called on the dependent.</span></span> <span data-ttu-id="f0b12-130">接著，交易便可完成認可或中止。</span><span class="sxs-lookup"><span data-stu-id="f0b12-130">Then the transaction can finish committing or aborting.</span></span>  
  
## <a name="concurrency-issues"></a><span data-ttu-id="f0b12-131">並行問題</span><span class="sxs-lookup"><span data-stu-id="f0b12-131">Concurrency Issues</span></span>  
 <span data-ttu-id="f0b12-132">使用 <xref:System.Transactions.DependentTransaction> 類別時，您需要注意下列幾項額外的並行問題：</span><span class="sxs-lookup"><span data-stu-id="f0b12-132">There are a few additional concurrency issues that you need to be aware of when using the <xref:System.Transactions.DependentTransaction> class:</span></span>  
  
-   <span data-ttu-id="f0b12-133">如果背景工作執行緒復原了交易，但是父交易卻嘗試認可它，則會擲回 <xref:System.Transactions.TransactionAbortedException>。</span><span class="sxs-lookup"><span data-stu-id="f0b12-133">If the worker thread rolls back the transaction but the parent tries to commit it, a <xref:System.Transactions.TransactionAbortedException> is thrown.</span></span>  
  
-   <span data-ttu-id="f0b12-134">您應該為交易中的每個背景工作執行緒建立新的相依複製品。</span><span class="sxs-lookup"><span data-stu-id="f0b12-134">You should create a new dependent clone for each worker thread in the transaction.</span></span> <span data-ttu-id="f0b12-135">請勿將同樣的相依複製品傳遞給多個執行緒，因為其中只有一個執行緒可以在相依交易上呼叫 <xref:System.Transactions.DependentTransaction.Complete%2A>。</span><span class="sxs-lookup"><span data-stu-id="f0b12-135">Do not pass the same dependent clone to multiple threads, because only one of them can call <xref:System.Transactions.DependentTransaction.Complete%2A> on it.</span></span>  
  
-   <span data-ttu-id="f0b12-136">如果背景工作執行緒繁衍出新的背景工作執行緒，請記得從相依複製品中建立一個相依複製品，並將其傳遞給背景工作執行緒。</span><span class="sxs-lookup"><span data-stu-id="f0b12-136">If the worker thread spawns a new worker thread, make sure to create a dependent clone from the dependent clone and pass it to the new thread.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0b12-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="f0b12-137">See Also</span></span>  
 <xref:System.Transactions.DependentTransaction>
