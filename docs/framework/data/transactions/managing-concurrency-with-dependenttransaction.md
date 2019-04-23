---
title: 使用 DependentTransaction 管理並行存取
ms.date: 03/30/2017
ms.assetid: b85a97d8-8e02-4555-95df-34c8af095148
ms.openlocfilehash: b06470ed76c15208f019874db8573d0ed4778d33
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59216297"
---
# <a name="managing-concurrency-with-dependenttransaction"></a>使用 DependentTransaction 管理並行存取
<xref:System.Transactions.Transaction> 物件係使用 <xref:System.Transactions.Transaction.DependentClone%2A> 方法建立。 其唯一目的在於保證當其他程式碼片段 (例如，背景工作執行緒仍在執行交易工作時，不會認可交易。 當完成並準備好認可在複製之交易中所執行的工作時，可以使用 <xref:System.Transactions.DependentTransaction.Complete%2A> 方法來通知交易的建立者。 這麼一來，您便可保持資料的一致性和正確性。  
  
 您也可以使用 <xref:System.Transactions.DependentTransaction> 類別來管理非同步工作之間的並行存取。 在此情況下，當相依的複製工作在執行自己的工作時，父項仍舊可以繼續執行任何程式碼。 換句話說，不管相依項是否完成工作，都不會影響父項執行工作。  
  
## <a name="creating-a-dependent-clone"></a>建立相依的複製品  
 若要建立相依的交易，請呼叫 <xref:System.Transactions.Transaction.DependentClone%2A> 方法，並將 <xref:System.Transactions.DependentCloneOption> 列舉型別當成參數傳送出去。 在相依的複製品表示它以準備好認可交易 (藉由呼叫 `Commit` 方法) 之前，如果在父交易呼叫 <xref:System.Transactions.DependentTransaction.Complete%2A> 的話，此參數將會定義交易行為。 下列各值為此參數可用的有效值：  
  
-   <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> 建立相依的交易封鎖父交易中，直到父交易時間的認可處理序，縮小，或直到<xref:System.Transactions.DependentTransaction.Complete%2A>上表示已完成的所有相依性呼叫。 當用戶端不想在完成相依交易之前即認可父交易時，這個參數就會非常有用。 如果父項比相依交易早一步完成工作，並在交易上呼叫 <xref:System.Transactions.CommittableTransaction.Commit%2A>，則會將認可處理序封鎖在某個狀態下。在此狀態下，您仍可以在交易上執行其他工作，並建立新的登記，直到所有相依項都呼叫 <xref:System.Transactions.DependentTransaction.Complete%2A> 為止。 一旦全部都完成各自的工作並呼叫 <xref:System.Transactions.DependentTransaction.Complete%2A>，就會馬上開始交易的認可處理序。  
  
-   另一方面，如果在呼叫 <xref:System.Transactions.DependentCloneOption.RollbackIfNotComplete> 之前，先在父交易上呼叫了 <xref:System.Transactions.CommittableTransaction.Commit%2A>，則 <xref:System.Transactions.DependentTransaction.Complete%2A> 會建立能自動中止的相依交易。 在此情況下，所有在相依交易中完成的工作會保留一段交易存留期不變，而且沒人有機會認可其中一部分。  
  
 當您的應用程式完成了在相依交易上的工作，必須呼叫 <xref:System.Transactions.DependentTransaction.Complete%2A> 方法一次 (而且只能一次)；否則，會擲回 <xref:System.InvalidOperationException>。 在叫用這個呼叫後，您不應嘗試在交易上執行任何額外的工作，否則會擲回例外狀況。  
  
 下列程式碼範例說明如何藉由複製相依的交易並將其傳遞至背景工作執行緒，來建立相依交易以管理兩個並行的工作。  
  
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
  
 用戶端程式碼可建立同時能設定環境交易的交易範圍。 您不應該將環境交易傳遞至背景工作執行緒。 反之，您應該呼叫目前交易上的 <xref:System.Transactions.Transaction.DependentClone%2A> 方法來複製目前 (環境) 交易，並將相依交易傳遞給背景工作執行緒。  
  
 `ThreadMethod` 方法會在新執行緒上執行。 用戶端開始新的執行緒後，會將相依交易當成 `ThreadMethod` 參數傳送出去。  
  
 由於相依交易係由 <xref:System.Transactions.DependentCloneOption.BlockCommitUntilComplete> 所建立，因此可以保證直到第二個執行緒上所有執行的交易工作都已完成，並且在相依交易上呼叫 <xref:System.Transactions.DependentTransaction.Complete%2A> 後，才會認可交易。 這表示，如果用戶端的範圍結束 (當它嘗試處置交易物件的結尾**使用**陳述式) 之前的新的執行緒呼叫<xref:System.Transactions.DependentTransaction.Complete%2A>相依的交易，在用戶端程式碼封鎖，直到<xref:System.Transactions.DependentTransaction.Complete%2A>上的相依性呼叫。 接著，交易便可完成認可或中止。  
  
## <a name="concurrency-issues"></a>並行問題  
 使用 <xref:System.Transactions.DependentTransaction> 類別時，您需要注意下列幾項額外的並行問題：  
  
-   如果背景工作執行緒復原了交易，但是父交易卻嘗試認可它，則會擲回 <xref:System.Transactions.TransactionAbortedException>。  
  
-   您應該為交易中的每個背景工作執行緒建立新的相依複製品。 請勿將同樣的相依複製品傳遞給多個執行緒，因為其中只有一個執行緒可以在相依交易上呼叫 <xref:System.Transactions.DependentTransaction.Complete%2A>。  
  
-   如果背景工作執行緒繁衍出新的背景工作執行緒，請記得從相依複製品中建立一個相依複製品，並將其傳遞給背景工作執行緒。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Transactions.DependentTransaction>
