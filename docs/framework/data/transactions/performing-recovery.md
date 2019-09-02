---
title: 執行復原
ms.date: 03/30/2017
ms.assetid: 6dd17bf6-ba42-460a-a44b-8046f52b10d0
ms.openlocfilehash: fe0e096c31b2ef62a1bc50d40c87f2e12c87343f
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205892"
---
# <a name="performing-recovery"></a>執行復原
資源管理員會在資源失敗後重新登記異動參與者，以協助解析異動中的永久性登記。  
  
## <a name="the-recovery-process"></a>復原程序  
 若要永久地登記稍後可用於復原的資源 (如 <xref:System.Transactions.IEnlistmentNotification> 介面實作所述)，您應該呼叫 <xref:System.Transactions.Transaction.EnlistDurable%2A> 方法。 此外，您必須提供一個包含資源管理員識別項 (<xref:System.Transactions.Transaction.EnlistDurable%2A>) 的 <xref:System.Guid> 方法，此識別項可在發生資源失敗時，用來為交易參與者持續加上標籤。 基於這個理由, 提供<xref:System.Guid>給初始登錄呼叫的會與復原期間<xref:System.Transactions.TransactionManager.Reenlist%2A>呼叫中的*resourceManagerIdentifier*參數相同。 否則，會擲回 <xref:System.Transactions.TransactionException>。 如需永久性登記的詳細資訊, 請參閱[將資源登記為交易中的參與者](enlisting-resources-as-participants-in-a-transaction.md)。  
  
 在 2PC 通訊協定準備階段 (第一階段) 中，當您實作的永久性資源管理員收到 <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> 告知，就應該會在此階段記錄下自己的準備記錄。 該記錄應包含完成交易認可所需的所有資訊。 您稍後可以藉由抓取<xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> *preparingEnlistment*回呼的屬性, 在復原期間存取準備記錄。 由於 RM 可以在背景工作執行緒 (Worker Thread) 上進行記錄，因此您不需要透過 <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> 方法來執行。  
  
 復原程序包含下列兩個步驟：  
  
### <a name="step-1---reenlist"></a>步驟 1 - 重新登記  
 資源管理員會檢查每個不確定之登記的準備資訊記錄。 它會檢查 <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> 回呼的 <xref:System.Transactions.PreparingEnlistment> 屬性，這個屬性會在第一階段透過 <xref:System.Transactions.IEnlistmentNotification.Prepare%2A> 告知傳遞給資源管理員。  
  
 它會針對每個所檢查的此類登記，叫用交易管理員上的 <xref:System.Transactions.TransactionManager.Reenlist%2A>。 此方法會傳遞可識別資源管理員的唯一 <xref:System.Guid>，以及位元組陣列中的登記資訊。 隨即會傳回新的 <xref:System.Transactions.Enlistment> 物件。 如果重新登記因為例外狀況而失敗，則資源管理員需要在稍後重試。  
  
 只有在資源管理員從失敗中重新啟動時，您才應該呼叫 <xref:System.Transactions.TransactionManager.Reenlist%2A> 方法。 此外，您只應該重新登記無法解析的交易，這些交易是由資源管理員在兩階段交易認可 (Two-Phase Commit) 的初始準備階段所記錄。 任何嘗試在無效時間呼叫這個方法的動作，都可能產生錯誤性結果。  
  
 當使用這個方法重新登記參與者時，會依適合的情況呼叫對應至異動結果 (也就是，<xref:System.Transactions.IEnlistmentNotification>、<xref:System.Transactions.IEnlistmentNotification.Commit%2A> 或 <xref:System.Transactions.IEnlistmentNotification.Rollback%2A>) 之 <xref:System.Transactions.IEnlistmentNotification.InDoubt%2A> 的第二階段方法。  
  
### <a name="step-2---completing-the-recovery"></a>步驟 2 - 完成復原  
 完成所有重新登記後，資源管理員就會呼叫 <xref:System.Transactions.TransactionManager.RecoveryComplete%2A> 方法。 此方法會完成復原並告知交易管理員，資源管理員已不包含任何不確定的交易。 當資源管理員這麼做，即保證不會再次叫用 <xref:System.Transactions.TransactionManager.Reenlist%2A> 方法。  
  
 在登記新的交易之前，不需要透過資源管理員來解析所有不確定的交易。 在資源管理員與交易管理員建立關聯性之後, 您可以隨時執行第一個步驟, 但是在被叫<xref:System.Transactions.TransactionManager.RecoveryComplete%2A>用之後 (步驟 2), 就無法再次執行步驟1。 步驟 2 可以重複執行多次，而不會影響到交易結果。
