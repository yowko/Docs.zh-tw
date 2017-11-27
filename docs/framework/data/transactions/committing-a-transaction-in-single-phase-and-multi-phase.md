---
title: "在單一階段和多重階段中認可交易"
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
ms.assetid: 694ea153-e4db-41ae-96ac-9ac66dcb69a9
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 83a65f6973c64b14e17b701ba4b5562eab8641f4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="committing-a-transaction-in-single-phase-and-multi-phase"></a>在單一階段和多重階段中認可交易
交易所使用的每項資源都會受到資源管理員 (RM) 的管理，而這些資源管理員在採取行動時必須經過交易管理員 (TM) 的協調。 [編列的資源，以在交易中的參與者身分](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)主題討論如何在交易中編列的資源 （或多個資源）。 本主題討論如何在眾多登記的資源中協調要認可的交易。  
  
 在交易結束時，應用程式會要求認可或復原交易。 交易管理員必須消除某些資源管理員投票決定認可，而其他資源管理員卻投票決定復原交易之類的風險。  
  
 如果您的交易涉及一個以上的資源，則您必須執行兩階段交易認可 (2PC)。 兩階段交易認可通訊協定 (準備階段與認可階段) 可確保當交易結束時，對全部資源的所有變更都能全部經過認可，或是全部復原回來。 接著所有參與者都會收到最後結果的通知。 如兩階段認可通訊協定的詳細討論，請參閱活頁簿 」*交易處理： 概念和技巧 （Morgan Kaufmann 數列中資料管理系統） ISBN:1558601902*"Jim Gray 所。  
  
 您也可以藉由參與單一階段交易認可通訊協定來最佳化您的交易效能。 如需詳細資訊，請參閱[最佳化使用單一階段認可和可提升單一階段通知](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)。  
  
 如果您只是想要知道交易的結果，但不想參與投票，則應該註冊 <xref:System.Transactions.Transaction.TransactionCompleted> 事件。  
  
## <a name="two-phase-commit-2pc"></a>兩階段交易認可 (2PC)  
 在第一個交易階段，交易管理員會查詢每個資源，決定是否應該認可或復原交易。 在第二個交易階段，交易管理員會將其查詢結果通知每個資源，讓資源執行任何必要的清除作業。  
  
 為了參與這種交易類型，資源管理員必須實作 <xref:System.Transactions.IEnlistmentNotification> 介面，以便在 2PC 期間提供由 TM 所呼叫的方法做為告知項目。  下列範例將說明此類實作。  
  
 [!code-csharp[Tx_Enlist#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#2)]
 [!code-vb[Tx_Enlist#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#2)]  
  
### <a name="prepare-phase-phase-1"></a>準備階段 (第一階段)  
 在收到來自應用程式的 <xref:System.Transactions.CommittableTransaction.Commit%2A> 要求之後，交易管理員會呼叫每個登記資源上的 <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> 方法來開始所有登記參與者的準備階段，以取得每個資源對交易的投票。  
  
 負責實作 <xref:System.Transactions.IEnlistmentNotification> 介面的資源管理員應該先實作 <xref:System.Transactions.IEnlistmentNotification.Prepare%28System.Transactions.PreparingEnlistment%29> 方法，如下列簡單範例所示。  
  
```  
public void Prepare(PreparingEnlistment preparingEnlistment)  
{  
     Console.WriteLine("Prepare notification received");  
     //Perform work  
  
     Console.Write("reply with prepared? [Y|N] ");  
     c = Console.ReadKey();  
     Console.WriteLine();  
  
     //If work finished correctly, reply with prepared  
     if ((c.KeyChar == 'Y') || (c.KeyChar == 'y'))  
     {  
          preparingEnlistment.Prepared();  
          break;  
     }  
  
     // otherwise, do a ForceRollback  
     else if ((c.KeyChar == 'N') || (c.KeyChar == 'n'))  
     {  
          preparingEnlistment.ForceRollback();  
          break;  
     }  
}  
```  
  
 當永久性資源管理員收到此呼叫，它應該將交易的復原資訊 (可藉由擷取 <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> 屬性而得) 以及完成交易認可所需的任何資訊記錄下來。 由於 RM 可在工作執行緒上進行這項作業，因此您不需要透過 <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> 方法來做這件事。  
  
 當 RM 完整準備工作時，就會呼叫 <xref:System.Transactions.PreparingEnlistment.Prepared%2A> 或 <xref:System.Transactions.PreparingEnlistment.ForceRollback%2A> 方法來投票認可或復原交易。 請注意，<xref:System.Transactions.PreparingEnlistment> 類別會繼承來自 <xref:System.Transactions.Enlistment.Done%2A> 類別的 <xref:System.Transactions.Enlistment> 方法。 如果您在準備階段於 <xref:System.Transactions.PreparingEnlistment> 回呼上呼叫此方法，則它會通知 TM 已登記為唯讀 (亦即，資源管理員可以讀取但無法更新交易保護的資料) 而且 RM 也將無法繼續收到來自交易管理員有關第二階段交易結果的任何告知。  
  
 當所有資源管理員都投票選擇 <xref:System.Transactions.PreparingEnlistment.Prepared%2A> 時，應用程式將被告知已經成功認可交易。  
  
### <a name="commit-phase-phase-2"></a>交易階段 (第二階段)  
 在交易的第二階段，如果交易管理員收到來自所有資源管理員的準備成功消息 (所有資源管理員在第一階段結束時都叫用了 <xref:System.Transactions.PreparingEnlistment.Prepared%2A>)，則它會為每個資源管理員叫用 <xref:System.Transactions.IEnlistmentNotification.Commit%2A> 方法。 資源管理員會接著進行永久性變更並完成交易認可動作。  
  
 如果有任何資源管理員在第一階段中報告準備失敗，則交易管理員會為每個資源管理員叫用 <xref:System.Transactions.IEnlistmentNotification.Rollback%2A> 方法，並向應用程式指出交易認可失敗之處。  
  
 因此，您的資源管理員應該實作下列方法。  
  
```  
public void Commit (Enlistment enlistment)  
{  
     // Do any work necessary when commit notification is received  
  
     // Declare done on the enlistment  
     enlistment.Done();  
}  
  
public void Rollback (Enlistment enlistment)  
{  
     // Do any work necessary when rollback notification is received  
  
     // Declare done on the enlistment    
     enlistment.Done();    
}  
```  
  
 RM 應該依據告知型別執行任何必要的工作以完成交易，並呼叫 <xref:System.Transactions.Enlistment.Done%2A> 參數上的 <xref:System.Transactions.Enlistment> 方法，告知 TM 已完成交易。 這項工作可在工作執行緒上完成。 請注意，第二階段告知會發生並內嵌在第一階段中呼叫 <xref:System.Transactions.PreparingEnlistment.Prepared%2A> 方法的同一個執行緒上。 因此，當您預期在收到第二階段告知之前會完成 <xref:System.Transactions.PreparingEnlistment.Prepared%2A> 呼叫時，請勿在此呼叫之後執行任何工作 (例如，釋放鎖定)。  
  
### <a name="implementing-indoubt"></a>實作 InDoubt  
 最後，您應該為變動性資源管理員實作 <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> 方法。 如果交易管理員失去與一或多個參與者的聯繫而無法得知其個別狀態時，就會呼叫此方法。 如果發生這種情況，不管是否有任何交易參與者仍舊維持在不一致的狀態，您都應該將此事實記錄下來以便稍後進一步探究原因。  
  
```  
public void InDoubt (Enlistment enlistment)  
{  
     // log this  
     enlistment.Done();  
}  
```  
  
## <a name="single-phase-commit-optimization"></a>單一階段交易認可最佳化  
 在執行階段使用單一階段交易認可通訊協定會比較有效率，因為所有的更新不需要任何個別的協調作業就可完成。 如需有關這個通訊協定的詳細資訊，請參閱[最佳化使用單一階段認可和可提升單一階段通知](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用單一階段認可，並可提升單一階段通知最佳化](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)  
 [登記資源，以在交易中的參與者身分](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)
