---
title: 執行復原
ms.date: 03/30/2017
ms.assetid: 6dd17bf6-ba42-460a-a44b-8046f52b10d0
ms.openlocfilehash: 149ac6b6162893de830f59b3d18008d8298eab56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33363926"
---
# <a name="performing-recovery"></a>執行復原
資源管理員會在資源失敗後重新登記異動參與者，以協助解析異動中的永久性登記。  
  
## <a name="the-recovery-process"></a>復原程序  
 若要永久地登記稍後可用於復原的資源 (如 <xref:System.Transactions.IEnlistmentNotification> 介面實作所述)，您應該呼叫 <xref:System.Transactions.Transaction.EnlistDurable%2A> 方法。 此外，您必須提供一個包含資源管理員識別項 (<xref:System.Transactions.Transaction.EnlistDurable%2A>) 的 <xref:System.Guid> 方法，此識別項可在發生資源失敗時，用來為交易參與者持續加上標籤。 基於這個理由，<xref:System.Guid>提供初始登錄來呼叫應該相同會*resourcemanageridentifier 與*中的參數<xref:System.Transactions.TransactionManager.Reenlist%2A>在復原期間呼叫。 否則，會擲回 <xref:System.Transactions.TransactionException>。 如需有關長期登記進行的詳細資訊，請參閱[編列的資源，以在交易中的參與者身分](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)。  
  
 在 2PC 通訊協定準備階段 (第一階段) 中，當您實作的永久性資源管理員收到 <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> 告知，就應該會在此階段記錄下自己的準備記錄。 該記錄應包含完成交易認可所需的所有資訊。 準備記錄可以稍後透過在復原期間擷取<xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A>屬性*preparingEnlistment*回呼。 由於 RM 可以在背景工作執行緒 (Worker Thread) 上進行記錄，因此您不需要透過 <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> 方法來執行。  
  
 復原程序包含下列兩個步驟：  
  
### <a name="step-1---reenlist"></a>步驟 1 - 重新登記  
 資源管理員會檢查每個不確定之登記的準備資訊記錄。 它會檢查 <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> 回呼的 <xref:System.Transactions.PreparingEnlistment> 屬性，這個屬性會在第一階段透過 <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> 告知傳遞給資源管理員。  
  
 它會針對每個所檢查的此類登記，叫用交易管理員上的 <xref:System.Transactions.TransactionManager.Reenlist%2A>。 此方法會傳遞可識別資源管理員的唯一 <xref:System.Guid>，以及位元組陣列中的登記資訊。 隨即會傳回新的 <xref:System.Transactions.Enlistment> 物件。 如果重新登記因為例外狀況而失敗，則資源管理員需要在稍後重試。  
  
 只有在資源管理員從失敗中重新啟動時，您才應該呼叫 <xref:System.Transactions.TransactionManager.Reenlist%2A> 方法。 此外，您只應該重新登記無法解析的交易，這些交易是由資源管理員在兩階段交易認可 (Two-Phase Commit) 的初始準備階段所記錄。 任何嘗試在無效時間呼叫這個方法的動作，都可能產生錯誤性結果。  
  
 當使用這個方法重新登記參與者時，會依適合的情況呼叫對應至交易結果 (也就是，<xref:System.Transactions.IEnlistmentNotification>、<xref:System.Transactions.IEnlistmentNotification.Commit%2A> 或 <xref:System.Transactions.IEnlistmentNotification.Rollback%2A>) 之 <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> 的第二階段方法。  
  
### <a name="step-2---completing-the-recovery"></a>步驟 2 - 完成復原  
 完成所有重新登記後，資源管理員就會呼叫 <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> 方法。 此方法會完成復原並告知交易管理員，資源管理員已不包含任何不確定的交易。 當資源管理員這麼做，即保證不會再次叫用 <xref:System.Transactions.TransactionManager.Reenlist%2A> 方法。  
  
 在登記新的交易之前，不需要透過資源管理員來解析所有不確定的交易。 可以在資源管理員建立關聯性與交易管理員，但在之後的任何時間執行的第一個步驟<xref:System.Transactions.TransactionManager.RecoveryComplete%2A>已叫用 （步驟 2），而無法再次執行步驟 1。 步驟 2 可以重複執行多次，而不會影響到交易結果。
