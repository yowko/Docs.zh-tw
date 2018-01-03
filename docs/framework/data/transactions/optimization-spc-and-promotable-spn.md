---
title: "使用單一階段交易認可和可提升單一階段告知進行最佳化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 57beaf1a-fb4d-441a-ab1d-bc0c14ce7899
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6f85dabc8a447db13173a672db37b327ba4a9fe6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="optimization-using-single-phase-commit-and-promotable-single-phase-notification"></a>使用單一階段交易認可和可提升單一階段告知進行最佳化
本主題將說明 <xref:System.Transactions> 基礎結構所提供，用以最佳化效能的各項機制。  
  
## <a name="promotable-single-phase-enlistment"></a>可提升單一階段登記  
 <xref:System.Transactions> 基礎結構負責管理單一應用程式定義域 (最多涉及單一永久性資源或多個變動性資源) 內的交易。 由於 <xref:System.Transactions> 基礎結構只使用應用程式內部的網域呼叫，因此可得到最佳輸送量與效能。  
  
 然而，如果將交易提供給位於同一部電腦上另一個應用程式定義域 (包含跨處理序與電腦界限) 中的另一個物件時，<xref:System.Transactions> 基礎結構會自動擴大由 MSDTC 所管理的交易規模。 由 MSDTC 所管理的交易並不像由 <xref:System.Transactions> 基礎結構所管理的交易一樣注重效能。  
  
 為了最佳化效能，<xref:System.Transactions> 基礎結構會將提供可提升單一階段登記 (PSPE) 以允許位於不同應用程式定義域、處理序或電腦上的單一遠端永久性資源參與 <xref:System.Transactions> 交易，而不會導致它擴大為 MSDTC 交易規模。  此交易管理員 (RM) 可以裝載並「擁有」交易，並可在稍後視需要將規模擴大為分散式交易 (或 MSDTC 交易)。 這會減少 MSDTC 的使用。  
  
 這項特定的資源管理員通常擁有自己的內部非分散式交易，而且需要在執行階段支援將這些交易轉換為分散式交易。 例如，SQL Server 2005 就是這樣的資源管理員。 在此情況下，<xref:System.Transactions> 基礎結構會採取消極的管理作為，而且只會監控交易，看看是否需要擴大規模。 為了支援 <xref:System.Transactions> 基礎結構與資源管理員之間的互動，後者需要實作 <xref:System.Transactions.IPromotableSinglePhaseNotification> 介面。  
  
 您可以使用 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> 方法，來登記稍後要擴大規模的單一永久性資源。 此方法可確保必要時登記擴大規模。 如果登記作業順利，則 RM 會建立自己的內部交易並將其與 <xref:System.Transactions> 交易關聯在一起。 如果 PSPE 登記作業失敗，則 RM 應該改用 <xref:System.Transactions.Transaction.EnlistDurable%2A> 方法來登記。 當交易已經成為分散式交易時，或當另一個 RM 已經執行了 PSPE 登記作業時，PSPE 登記作業可能會失敗  
  
 登記好了以後，用戶端的 <xref:System.Transactions> 交易認可或中止呼叫會藉由個別叫用 <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> 方法或 <xref:System.Transactions.IPromotableSinglePhaseNotification.Rollback%2A>，轉換為對資源管理員的呼叫。  
  
 如果 <xref:System.Transactions> 交易從不需要擴大規模，則當認可交易時，RM 會收到一份 <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> 告知。 接著它會認可剛建立好的內部交易。  
  
 如果 <xref:System.Transactions> 交易需要擴大規模 (例如，用以支援多個 RM)，則 <xref:System.Transactions> 會呼叫 <xref:System.Transactions.ITransactionPromoter.Promote%2A> 介面之來源 <xref:System.Transactions.ITransactionPromoter> 介面上的 <xref:System.Transactions.IPromotableSinglePhaseNotification> 方法，以告知資源管理員。 接著，資源管理員會從內部將交易由本機交易 (不需要記錄) 轉換為可參與 DTC 交易的交易物件，並將其與已經完成的工作產生關聯。 一旦交易被要求認可，交易管理員仍舊會將 <xref:System.Transactions.IPromotableSinglePhaseNotification.SinglePhaseCommit%2A> 告知傳送給資源管理員，使其認可在擴大規模期間所建立的分散式交易。  
  
> [!NOTE]
>  **TransactionCommitted** （時，所產生已呈報的交易上叫用認可） 的追蹤就包含 DTC 交易的活動識別碼。  
  
 如需有關管理擴大的詳細資訊，請參閱[交易管理擴大](../../../../docs/framework/data/transactions/transaction-management-escalation.md)。  
  
## <a name="transaction-management-escalation-scenario"></a>交易管理擴大規模案例  
 下列案例說明了使用 <xref:System.Data> 命名空間做為資源管理員 Proxy 以便將規模擴大為分散式交易的情況。 此案例假定已經存在一個對資料庫的 <xref:System.Data> 連線 (CN1) 且此資料庫已經參與交易，而且應用程式想要在交易中加入另一個 <xref:System.Data> 連線 (CN2)。 此交易必須擴大至 DTC，才算完成整個分散式兩階段交易認可交易。  
  
 在此案例中，  
  
1.  CN1 會呼叫 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> 方法來登記交易。 接著，交易仍舊在本機上執行，而且未含其他可提升登記項目，因此 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> 呼叫能夠順利完成。  
  
2.  當第二個連線，也就是 CN2 呼叫 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> 時，由於已經內含另一個可提升登記項目，因此呼叫會失敗。 因為這個緣故，CN2 必須取得 DTC 交易以便將其傳送給 SQL。 為了達到這個目的，它會使用 <xref:System.Transactions.TransactionInterop> 類別所提供的其中一種方法來產生可提供給 SQL 的交易格式。  
  
3.  <xref:System.Transactions> 會呼叫 CN1 於 <xref:System.Transactions.ITransactionPromoter.Promote%2A> 介面上所實作的 <xref:System.Transactions.ITransactionPromoter> 方法。  
  
4.  此時，CN1 會藉助 SQL 2005 與 <xref:System.Data> 專屬的某些機制來擴大交易規模。  
  
5.  來自 <xref:System.Transactions.ITransactionPromoter.Promote%2A> 方法的傳回值是一種位元組陣列，其中包含用於交易的傳播權杖。 <xref:System.Transactions> 會使用此傳播權杖來建立 DTC 交易，以便加入至本機交易中。  
  
6.  此時，CN2 可以使用 <xref:System.Transactions.TransactionInterop> 來呼叫其中一種方法，並藉由呼叫後所收到的資料將交易傳遞給 SQL。  
  
7.  現在，兩者都已經登記在 DTC 分散式交易中了。  
  
## <a name="single-phase-commit-optimization"></a>單一階段交易認可最佳化  
 在執行階段使用單一階段交易認可通訊協定會比較有效率，因為所有的更新不需要任何個別的協調作業就可完成。 若要充分善用此最佳化優勢，您應該使用資源的 <xref:System.Transactions.ISinglePhaseNotification> 介面來實作資源管理員，並使用 <xref:System.Transactions.Transaction.EnlistDurable%2A> 或 <xref:System.Transactions.Transaction.EnlistVolatile%2A> 方法來登記交易。 具體來說， *EnlistmentOptions*參數應該等於<xref:System.Transactions.EnlistmentOptions.None>以確保會執行單一階段交易認可。  
  
 由於 <xref:System.Transactions.ISinglePhaseNotification> 介面是衍生自 <xref:System.Transactions.IEnlistmentNotification> 介面，即使 RM 無法執行單一階段交易認可，仍舊可以收到兩階段交易認可告知。  如果您的 RM 收到來自 TM 的 <xref:System.Transactions.ISinglePhaseNotification.SinglePhaseCommit%2A> 告知，它應該嘗試執行必要的工作以便認可交易，並接著藉由呼叫 <xref:System.Transactions.SinglePhaseEnlistment.Committed%2A> 參數上的 <xref:System.Transactions.SinglePhaseEnlistment.Aborted%2A>、<xref:System.Transactions.SinglePhaseEnlistment.InDoubt%2A>，或 <xref:System.Transactions.SinglePhaseEnlistment> 方法來告知交易管理員是否應該認可或復原交易。 此階段對登記項目的 <xref:System.Transactions.Enlistment.Done%2A> 回應將意指唯讀語意。 因此，您不應該在其他任何方法以外，回應 <xref:System.Transactions.Enlistment.Done%2A>。  
  
 如果只有一個的變動登記和任何的永久性登記，變動登記會接收 SPC 通知。  如果有任何 volatile 登記和只有一個的永久性登記，volatile 登記收到 2PC。 當它完成時，永久性登記會收到 SPC。  
  
## <a name="see-also"></a>請參閱  
 [將資源登記為異動中的參與者](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)  
 [在單一階段和多重階段中認可異動](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md)
