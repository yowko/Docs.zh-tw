---
title: "將資源登記成為交易中的參與者"
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
ms.assetid: 786a12c2-d530-49f4-9c59-5c973e15a11d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 98ac35edc458e370f2b7b9b116d2872d0db2da71
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="enlisting-resources-as-participants-in-a-transaction"></a>將資源登記成為交易中的參與者
參與交易的每項資源都會受到資源管理員的管理，而這些資源管理員在採取行動時必須經過交易管理員的協調。 訂閱者透過交易管理員登記到交易中，並收到告知來完成整個協調程序。  
  
 本主題將涵蓋如何在交易中登記資源 (或多項資源)，以及登記的型別有哪些。 [認可的交易中單一和多重階段](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md)主題涵蓋如何交易認可可能已登錄的資源之間協調。  
  
## <a name="enlisting-resources-in-a-transaction"></a>將資源登記到交易中  
 為了讓資源參與交易，資源必須登記到交易中。 <xref:System.Transactions.Transaction>類別會定義一組方法名稱開頭為**登錄**可提供這項功能。 不同**登錄**方法會對應至不同類型的資源管理員可能有的登記。 具體來說，您可以使用變動性資源的 <xref:System.Transactions.Transaction.EnlistVolatile%2A> 方法，以及永久性資源的 <xref:System.Transactions.Transaction.EnlistDurable%2A> 方法。 資源管理員的永久性 (反之為變動性) 指的是資源管理員是否支援故障復原。 如果資源管理員支援故障復原，會在第一階段 (準備階段) 將資料保存在永久性儲存裝置中。這樣一來，如果資源管理員故障，資料就可以在復原後重新登記到交易中，並依據接收自 TM 的告知執行適當的動作。 一般來說，變動性資源管理員會將變動性資源當成記憶體中的資料結構來管理 (例如，記憶體中的交易雜湊表)，而永久性資源管理員則會管理具有較持久之備份存放區的資源 (例如，使用磁碟做為備份存放區的資料庫)。  
  
 在依據資源永久性支援來決定是否採用 <xref:System.Transactions.Transaction.EnlistDurable%2A> 或 <xref:System.Transactions.Transaction.EnlistVolatile%2A> 方法之後，為了方便作業，您應該實作資源管理員的 <xref:System.Transactions.IEnlistmentNotification> 介面，以便登記資源並讓其參與兩階段交易認可 (2PC)。 如需有關 2PC 的詳細資訊，請參閱[認可的交易中單一和多重階段](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md)。  
  
 單一參與者可藉由呼叫 <xref:System.Transactions.Transaction.EnlistDurable%2A> 與 <xref:System.Transactions.Transaction.EnlistVolatile%2A> 數次為一個以上的這類通訊協定進行登記。  
  
### <a name="durable-enlistment"></a>永久性登記  
 您可以使用 <xref:System.Transactions.Transaction.EnlistDurable%2A> 方法來登記資源管理員，以便以永久性資源身分參與交易。  如果永久性資源管理員在交易中途停機，預期它會重新登記 (使用 <xref:System.Transactions.TransactionManager.Reenlist%2A> 方法) 到所有已參與但未完成第二階段的交易中，並於重新上線後執行復原。一旦完成復原程序，資源管理員便會呼叫 <xref:System.Transactions.TransactionManager.RecoveryComplete%2A>。 如需復原的詳細資訊，請參閱[執行復原](../../../../docs/framework/data/transactions/performing-recovery.md)。  
  
 所有 <xref:System.Transactions.Transaction.EnlistDurable%2A> 方法都會將 <xref:System.Guid> 物件當成第一個參數。 交易管理員會使用 <xref:System.Guid>，將永久性登記與特定的資源管理員關聯在一起。 這麼一來，資源管理員在重新啟動時就必須持續使用相同的 <xref:System.Guid> 來辨識自己 (即使是在不同的資源管理員之間亦然)，否則復原會失敗。  
  
 <xref:System.Transactions.Transaction.EnlistDurable%2A> 方法的第二個參數會參考某個資源管理員實作以接收交易告知的物件。 您會使用多載來告知交易管理員有關資源管理員是否支援單一階段交易認可 (SPC) 最佳化。 在大部分情況下，您應該實作 <xref:System.Transactions.IEnlistmentNotification>介面來參與兩階段交易認可 (2PC)。 但是，如果您希望最佳化交易認可處理序，則可以考慮實作 SPC 的 <xref:System.Transactions.ISinglePhaseNotification> 介面。 如需有關 SPC 的詳細資訊，請參閱[認可的交易中單一和多重階段](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md)和[最佳化使用單一階段認可和可提升單一階段通知](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)。  
  
 第三個參數是一種 <xref:System.Transactions.EnlistmentOptions> 列舉型別，其值可為 <xref:System.Transactions.EnlistmentOptions.None> 或 <xref:System.Transactions.EnlistmentOptions.EnlistDuringPrepareRequired>。 如果將值設為 <xref:System.Transactions.EnlistmentOptions.EnlistDuringPrepareRequired>，登記作業可能會在收到來自交易管理員的準備告知時登記額外的資源管理員。 但是，您應該了解這種登記型別不適用於單一階段交易認可最佳化作業。  
  
### <a name="volatile-enlistment"></a>變動性登記  
 管理快取之類的變動性資源的參與者，應該使用 <xref:System.Transactions.Transaction.EnlistVolatile%2A> 方法來登記。 此類物件也許無法取得交易結果，或是在系統故障後復原所參與的任何交易狀態。  
  
 如同先前所述，如果資源管理員負責管理記憶體中的變動性資源，就需要進行變動性登記作業。 使用 <xref:System.Transactions.Transaction.EnlistVolatile%2A> 的其中一項好處就是，它不會強制擴大不必要的交易規模。 如需有關交易擴大規模的詳細資訊，請參閱[交易管理擴大](../../../../docs/framework/data/transactions/transaction-management-escalation.md)主題。 登記變動性資源同時意指交易管理員處理交易的方式，以及交易管理員對資源管理員的期待等各項差異。 這是因為變動性資源管理員無法執行復原。 <xref:System.Transactions.Transaction.EnlistVolatile%2A> 方法不會使用 <xref:System.Guid> 參數，因為變動性資源管理員無法執行復原，也無法呼叫需要 <xref:System.Transactions.TransactionManager.Reenlist%2A> 的 <xref:System.Guid> 方法。  
  
 有關永久性登記方面，不管您使用哪種多載方法來登記，都會向交易管理員表示您的資源管理員是否支援單一階段交易認可最佳化。 由於變動性資源管理員無法執行復原，因此準備階段期間不會針對變動性登記寫入復原資訊。 如此一來，呼叫 <xref:System.Transactions.PreparingEnlistment.RecoveryInformation%2A> 方法將產生 <xref:System.InvalidOperationException> 的結果。  
  
 下列範例會顯示如何使用 <xref:System.Transactions.Transaction.EnlistVolatile%2A> 方法將此類物件登記為交易中的參與者。  
  
 [!code-csharp[Tx_Enlist#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/tx_enlist/cs/enlist.cs#1)]
 [!code-vb[Tx_Enlist#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/tx_enlist/vb/enlist.vb#1)]  
  
### <a name="optimizing-performance"></a>最佳化效能  
 <xref:System.Transactions.Transaction> 類別也會提供 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> 方法，以便登記可提升單一階段登記 (PSPE)。 這樣一來永久性資源管理員 (RM) 就可以裝載並「擁有」交易，並可在稍後視需要將規模擴大為由 MSDTC 管理。 如需詳細資訊，請參閱[最佳化使用單一階段認可和可提升單一階段通知](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)。  
  
## <a name="see-also"></a>另請參閱  
 [使用單一階段認可，並可提升單一階段通知最佳化](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)  
 [認可交易，以在單一和多重階段](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md)
