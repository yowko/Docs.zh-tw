---
title: "執行復原  | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6dd17bf6-ba42-460a-a44b-8046f52b10d0
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 執行復原 
資源管理員會在資源失敗後重新登記交易參與者，以協助解析交易中的永久性登記。  
  
## 復原程序  
 若要永久地登記稍後可用於復原的資源 \(如 <xref:System.Transactions.IEnlistmentNotification> 介面實作所述\)，您應該呼叫 <xref:System.Transactions.Transaction.EnlistDurable%2A> 方法。此外，您必須提供一個包含資源管理員識別項 \(<xref:System.Guid>\) 的 <xref:System.Transactions.Transaction.EnlistDurable%2A> 方法，此識別項可在發生資源失敗時，用來為交易參與者持續加上標籤。因此，提供給初始登記呼叫的 <xref:System.Guid> 應該與復原期間 <xref:System.Transactions.TransactionManager.Reenlist%2A> 呼叫中的 *resourceManagerIdentifier* 參數一模一樣。否則，會擲回 <xref:System.Transactions.TransactionException>。如需永久性登記的詳細資訊，請參閱[將資源登記成為交易中的參與者 ](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)。  
  
 在 2PC 通訊協定準備階段 \(第一階段\) 中，當您實作的永久性資源管理員收到 <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> 告知，就應該會在此階段記錄下自己的準備記錄。該記錄應包含完成交易認可所需的所有資訊。您稍後可以在復原期間藉由擷取 *preparingEnlistment* 回呼 \(Callback\) 的 <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> 屬性來存取準備記錄。由於 RM 可以在背景工作執行緒 \(Worker Thread\) 上進行記錄，因此您不需要透過 <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> 方法來執行。  
  
 復原程序包含下列兩個步驟：  
  
### 步驟 1 \- 重新登記  
 資源管理員會檢查每個不確定之登記的準備資訊記錄。它會檢查 <xref:System.Transactions.PreparingEnlistment> 回呼的 <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> 屬性，這個屬性會在第一階段透過 <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> 告知傳遞給資源管理員。  
  
 它會針對每個所檢查的此類登記，叫用交易管理員上的 <xref:System.Transactions.TransactionManager.Reenlist%2A>。此方法會傳遞可識別資源管理員的唯一 <xref:System.Guid>，以及位元組陣列中的登記資訊。隨即會傳回新的 <xref:System.Transactions.Enlistment> 物件。如果重新登記因為例外狀況而失敗，則資源管理員需要在稍後重試。  
  
 只有在資源管理員從失敗中重新啟動時，您才應該呼叫 <xref:System.Transactions.TransactionManager.Reenlist%2A> 方法。此外，您只應該重新登記無法解析的交易，這些交易是由資源管理員在兩階段交易認可 \(Two\-Phase Commit\) 的初始準備階段所記錄。任何嘗試在無效時間呼叫這個方法的動作，都可能產生錯誤性結果。  
  
 當使用這個方法重新登記參與者時，會依適合的情況呼叫對應至交易結果 \(也就是，<xref:System.Transactions.IEnlistmentNotification.Commit%2A>、<xref:System.Transactions.IEnlistmentNotification.Rollback%2A> 或 <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A>\) 之 <xref:System.Transactions.IEnlistmentNotification> 的第二階段方法。  
  
### 步驟 2 \- 完成復原  
 完成所有重新登記後，資源管理員就會呼叫 <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> 方法。此方法會完成復原並告知交易管理員，資源管理員已不包含任何不確定的交易。當資源管理員這麼做，即保證不會再次叫用 <xref:System.Transactions.TransactionManager.Reenlist%2A> 方法。  
  
 在登記新的交易之前，不需要透過資源管理員來解析所有不確定的交易。第一個步驟可以在資源管理員與交易管理員建立關係之後隨時執行，但是一旦叫用了 <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> \(步驟 2\)，則無法再次執行步驟 1。步驟 2 可以重複執行多次，而不會影響到交易結果。