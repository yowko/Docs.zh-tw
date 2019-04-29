---
title: 實作資源管理員
ms.date: 03/30/2017
ms.assetid: d5c153f6-4419-49e3-a5f1-a50ae4c81bf3
ms.openlocfilehash: f3e29dae095fbe56181cf7b67787c1044efa07ae
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793701"
---
# <a name="implementing-a-resource-manager"></a>實作資源管理員
交易所使用的每項資源都會受到資源管理員的管理，而這些資源管理員在採取行動時必須經過交易管理員的協調。 資源管理員會和交易管理員一起合作以提供應用程式單元性 (Atomicity) 和隔離性 (Isolation) 的保證。 Microsoft SQL Server、永久性訊息佇列、記憶體中的雜湊資料表，通通都是資源管理員的範例。  
  
 資源管理員會負責管理永久性或變動性資料。 資源管理員的永久性 (反之為變動性) 指的是資源管理員是否支援故障復原。 如果資源管理員支援故障復原，會在第一階段 (準備階段) 將資料保存在永久性儲存裝置中。這樣一來，如果資源管理員故障，資料就可以在復原後重新登記到交易中，並依據接收自交易管理員的告知執行適當的動作。 一般來說，變動性資源管理員會將變動性資源當成記憶體中的資料結構來管理 (例如，記憶體中的交易雜湊表)，而永久性資源管理員則會管理具有較持久之備份存放區的資源 (例如，使用磁碟做為備份存放區的資料庫)。  
  
 為了讓資源參與交易，資源必須登記到交易中。 <xref:System.Transactions.Transaction>類別會定義一組方法名稱開頭**登錄**可提供這項功能。 不同**登錄**方法會對應至不同類型的資源管理員可能具有的登記。 具體來說，您可以使用變動性資源的 <xref:System.Transactions.Transaction.EnlistVolatile%2A> 方法，以及永久性資源的 <xref:System.Transactions.Transaction.EnlistDurable%2A> 方法。 在依據資源永久性支援來決定是否採用 <xref:System.Transactions.Transaction.EnlistDurable%2A> 或 <xref:System.Transactions.Transaction.EnlistVolatile%2A> 方法之後，為了方便作業，您應該實作資源管理員的 <xref:System.Transactions.IEnlistmentNotification> 介面，以便登記資源並讓其參與兩階段交易認可 (2PC)。 如需 2PC 的詳細資訊，請參閱[認可交易，以在單一階段和多重階段](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md)。  
  
 資源管理員藉由登記來確保當交易認可或中止時，能夠從交易管理員中取得回呼。 每項登記都有一個 <xref:System.Transactions.IEnlistmentNotification> 執行個體。 一般來說，每個交易都會包含一個登記，但是資源管理員可以選擇在同一個交易中登記多次。  
  
 登記完之後，資源管理員會回應交易要求。 永久性資源管理員會儲存足夠的資訊，方便它復原或重做交易對它所管理的資源的變更。 有許多方式可以這麼做；保存不同的資料版本，或是保存一份變更記錄，都是常見的方法。  
  
 當應用程式認可交易時，交易管理員會啟始兩階段的交易認可通訊協定。 交易管理員會先詢問每個登記的資源管理員是否已經準備好認可交易。 資源管理員必須準備認可交易，它可以準備認可或是中止交易。  
  
 在準備階段，永久性資源管理員會將新舊資料記錄到穩定的儲存位置，這樣一來，就算系統故障，資源管理員還是能夠加以復原。 如果資源管理員可以準備，就會告知交易管理員它已投票認可或中止交易。 如果有任何資源管理員報告準備失敗，則交易管理員會將回呼指令傳給每個資源管理員，並向應用程式指出交易認可失敗之處。  
  
 準備好之後，資源管理員必須等到第二階段從交易管理員取得交易認可或中止的回呼。 一般來說，整個準備與認可通訊協定會在一瞬間完成。 如果發生系統故障或通訊失敗，則認可或中止告知可能無法在幾分鐘或幾小時內抵達。 在這段期間，資源管理員將無法確定交易的結果。 它不知道交易是否已經認可或中止。 當資源管理員不確定交易結果時，會鎖定交易來持續修改資料，進而將這些變更從其他所有交易中隔離出來。  
  
 當資源管理員失敗，所有登記的交易都會中止 (在失敗前已經準備好或認可的交易除外)。 當永久性資源管理員重新啟動，會擷取於準備階段中寫入的準備資訊來重新建構所管理的資源認可狀態，並據此認可或中止交易。  
  
 簡言之，兩階段交易認可通訊協定與資源管理員會共同讓交易變成不可部分完成且具有永久性。  
  
 <xref:System.Transactions.Transaction> 類別也會提供 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> 方法，以便登記可提升單一階段登記 (PSPE)。 這樣一來永久性資源管理員 (RM) 就可以裝載並「擁有」交易，並可在稍後視需要將規模擴大為由 MSDTC 管理。 如需詳細資訊，請參閱[使用單一階段交易認可和可提升單一階段告知進行最佳化](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)。  
  
## <a name="in-this-section"></a>本節內容  
 如下列各主題所述，這些步驟通常會緊接著資源管理員。  
  
 [將資源登記為異動中的參與者](../../../../docs/framework/data/transactions/enlisting-resources-as-participants-in-a-transaction.md)  
  
 說明如何在交易中登記永久性或變動性資源。  
  
 [在單一階段和多重階段中認可異動](../../../../docs/framework/data/transactions/committing-a-transaction-in-single-phase-and-multi-phase.md)  
  
 說明資源管理員如何回應認可告知以及準備認可。  
  
 [執行復原](../../../../docs/framework/data/transactions/performing-recovery.md)  
  
 說明永久性資源管理員如何從故障中復原。  
  
 [存取資源的安全性信任層級](../../../../docs/framework/data/transactions/security-trust-levels-in-accessing-resources.md)  
  
 說明 System.Transactions 的三個信任層級如何對 <xref:System.Transactions> 所公開的資源型別限制其存取。  
  
 [使用單一階段認可和可提升單一階段通知進行最佳化](../../../../docs/framework/data/transactions/optimization-spc-and-promotable-spn.md)  
  
 說明可用來實作資源管理員的最佳化準則。
