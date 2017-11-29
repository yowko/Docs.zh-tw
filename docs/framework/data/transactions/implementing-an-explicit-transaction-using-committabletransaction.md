---
title: "使用 CommittableTransaction 實作明確交易"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 29efe5e5-897b-46c2-a35f-e599a273acc8
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f045356fa2de6543a3b24490cb7964640a8d802c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-an-explicit-transaction-using-committabletransaction"></a>使用 CommittableTransaction 實作明確交易
<xref:System.Transactions.CommittableTransaction> 類別為應用程式提供使用交易的明確方式，而非隱含地使用 <xref:System.Transactions.TransactionScope> 類別。 這個方法對想要跨多個函式呼叫或多個執行緒呼叫來使用相同交易的應用程式也很有用處。 與 <xref:System.Transactions.TransactionScope> 類別不同的是，應用程式寫入器需要特別呼叫 <xref:System.Transactions.CommittableTransaction.Commit%2A> 和 <xref:System.Transactions.Transaction.Rollback%2A> 方法，才能認可或中止交易。  
  
## <a name="overview-of-the-committabletransaction-class"></a>CommittableTransaction 類別的概觀  
 <xref:System.Transactions.CommittableTransaction> 類別係衍生自 <xref:System.Transactions.Transaction> 類別，因此可提供後者所有功能。 <xref:System.Transactions.Transaction.Rollback%2A> 類別上的 <xref:System.Transactions.Transaction> 方法特別有用，因為它同時能用來復原 <xref:System.Transactions.CommittableTransaction> 物件。  
  
 <xref:System.Transactions.Transaction> 類別與 <xref:System.Transactions.CommittableTransaction> 類別類似，但是不會提供 `Commit` 方法。 它能讓您在控制交易認可時間的同時，將交易物件 (或其複製品) 傳遞給其他方法 (可能透過其他執行緒)。 呼叫的程式碼可以登記並投票給交易，但是只有 <xref:System.Transactions.CommittableTransaction> 物件的建立者有能力認可交易。  
  
 使用 <xref:System.Transactions.CommittableTransaction> 類別時，您應該注意下列事項。  
  
-   建立 <xref:System.Transactions.CommittableTransaction> 交易不會設定環境交易。 您需要特別設定及重設環境交易，以確保資源管理員在適當時機，於正確的交易內容下作業。 您可以在全域 <xref:System.Transactions.Transaction.Current%2A> 物件上設定靜態 <xref:System.Transactions.Transaction> 屬性，來設定目前的環境交易。  
  
-   您無法重複使用 <xref:System.Transactions.CommittableTransaction> 物件， 一旦 <xref:System.Transactions.CommittableTransaction> 物件已經認可或復原，將無法重複使用在交易中。 亦即，您無法將其設為目前的環境交易內容。  
  
## <a name="creating-a-committabletransaction"></a>建立 CommittableTransaction  
 下列範例會建立新的 <xref:System.Transactions.CommittableTransaction> 並加以認可。  
  
 [!code-csharp[Tx_CommittableTx#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_committabletx/cs/committabletxwithsql.cs#1)]
 [!code-vb[Tx_CommittableTx#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_committabletx/vb/committabletxwithsql.vb#1)]  
  
 建立 <xref:System.Transactions.CommittableTransaction> 執行個體不會自動設定環境交易內容。 因此，資源管理員上的任何作業都不是該交易的一部分。 全域 <xref:System.Transactions.Transaction.Current%2A> 物件上的靜態 <xref:System.Transactions.Transaction> 屬性是用來設定或擷取環境交易，應用程式必須手動加以設定以確保資源管理員可以參與交易。 儲存舊有的環境交易並在 <xref:System.Transactions.CommittableTransaction> 物件使用完畢時將其還原是很好的使用習慣。  
  
 為了認可交易，您需要明確地呼叫 <xref:System.Transactions.CommittableTransaction.Commit%2A> 方法。 若要復原交易，您應該呼叫 <xref:System.Transactions.Transaction.Rollback%2A> 方法。 在已認可或復原 <xref:System.Transactions.CommittableTransaction> 之前，所有與該交易有關的資源都會保持鎖定，這點請您特別注意。  
  
 <xref:System.Transactions.CommittableTransaction> 物件可以供多個函式呼叫與執行緒使用。 然而，應用程式開發人員有權決定是否要在發生失敗時，處理例外狀況並特別呼叫 <xref:System.Transactions.Transaction.Rollback%28System.Exception%29> 方法。  
  
## <a name="asynchronous-commit"></a>非同步認可  
 <xref:System.Transactions.CommittableTransaction> 類別同時提供您以非同步方式認可交易的機制。 交易認可作業會花掉很多時間，因為此作業牽涉到多個資料庫存取，而且可能會讓網路產生延遲現象。 當您想要避免高輸送量應用程式中出現死結 (Deadlock) 的情況時，可以使用非同步認可方式來儘速完成交易作業，並以背景工作方式來執行認可作業。 <xref:System.Transactions.CommittableTransaction.BeginCommit%2A> 類別的 <xref:System.Transactions.CommittableTransaction.EndCommit%2A> 與 <xref:System.Transactions.CommittableTransaction> 方法可讓您這麼做。  
  
 您可以呼叫 <xref:System.Transactions.CommittableTransaction.BeginCommit%2A>，將認可停頓分配給來自執行緒集區的執行緒。 您也可以呼叫 <xref:System.Transactions.CommittableTransaction.EndCommit%2A> 來判斷交易是否已實際認可。 如果交易因為某種原因而失敗，則 <xref:System.Transactions.CommittableTransaction.EndCommit%2A> 會引發交易例外狀況。 如果交易在呼叫 <xref:System.Transactions.CommittableTransaction.EndCommit%2A> 時尚未認可，則呼叫端會在交易認可或中止之前一直保持封鎖狀態。  
  
 進行非同步認可的最簡便方式，就是提供可在完成認可時加以呼叫的回呼方法。 但是，您必須在用於叫用呼叫的原始 <xref:System.Transactions.CommittableTransaction.EndCommit%2A> 物件上呼叫 <xref:System.Transactions.CommittableTransaction> 方法。 若要取得該物件，您可以向下轉型*IAsyncResult*回呼方法參數，因為<xref:System.Transactions.CommittableTransaction>類別會實作<xref:System.IAsyncResult>類別。  
  
 下列範例示範如何完成非同步認可。  
  
```csharp  
public void DoTransactionalWork()  
{  
     Transaction oldAmbient = Transaction.Current;  
     CommittableTransaction committableTransaction = new CommittableTransaction();  
     Transaction.Current = committableTransaction;  
  
     try  
     {  
          /* Perform transactional work here */  
          // No errors - commit transaction asynchronously  
          committableTransaction.BeginCommit(OnCommitted,null);  
     }  
     finally  
     {  
          //Restore the ambient transaction   
          Transaction.Current = oldAmbient;  
     }  
}  
void OnCommitted(IAsyncResult asyncResult)  
{  
     CommittableTransaction committableTransaction;  
     committableTransaction = asyncResult as CommittableTransaction;     
     Debug.Assert(committableTransaction != null);  
     try  
     {  
          using(committableTransaction)  
          {  
               committableTransaction.EndCommit(asyncResult);  
          }  
     }  
     catch(TransactionException e)  
     {  
          //Handle the failure to commit  
     }  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [實作隱含交易使用交易範圍](../../../../docs/framework/data/transactions/implementing-an-implicit-transaction-using-transaction-scope.md)  
 [交易處理](../../../../docs/framework/data/transactions/index.md)
