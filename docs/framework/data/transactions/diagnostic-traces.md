---
title: 診斷追蹤
ms.date: 03/30/2017
ms.assetid: 28e77a63-d20d-4b6a-9caf-ddad86550427
ms.openlocfilehash: 56f79fb9140785188996cc413eca4dd530037ccd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="diagnostic-traces"></a>診斷追蹤
追蹤就是在應用程式執行期間，所產生的特定訊息之發行動作。 使用追蹤功能時，您必須具有收集和記錄所傳送訊息的機制。 追蹤訊息由「接聽項」負責接收。 接聽項的用途是收集、儲存和傳送追蹤訊息。 接聽項會將追蹤輸出導向至適當的目標，例如記錄檔、視窗或文字檔。  
  
 這類的接聽項，例如 <xref:System.Diagnostics.DefaultTraceListener>，會在啟用追蹤時自訂建立與初始。 如果您要將追蹤輸出傳送至任何其他來源，您必須建立和初始化其他的追蹤接聽項。 您建立的接聽項應反映出您個人的需求。 例如，您可能想要所有追蹤輸出的文字記錄。 在這種情況中，您建立的接聽項要在啟用時，將所有的輸出寫入新的文字檔。 另一方面，您可能只想在應用程式執行期間檢視輸出。 在這種情況中，您可建立導向所有輸出至主控台視窗的接聽項。 <xref:System.Diagnostics.EventLogTraceListener> 可以導向追蹤輸出至事件記錄檔，而 <xref:System.Diagnostics.TextWriterTraceListener> 可將追蹤輸出寫入資料流。  
  
## <a name="enabling-tracing"></a>啟用追蹤  
 若要在交易處理期間啟用追蹤，您應該編輯應用程式的組態檔。 下列為範例。  
  
```xml  
<configuration>  
<system.diagnostics>  
     <sources>  
          <source name="System.Transactions" switchValue="Warning">  
               <listeners>  
                    <add name="tx"   
                     type="System.Diagnostics.XmlWriterTraceListener"   
                     initializeData= "tx.log" />  
               </listeners>  
          </source>  
     </sources>  
</system.diagnostics>  
</configuration>  
```  
  
 <xref:System.Transactions> 追蹤會寫入名為 "System.Transactions" 的來源中。 您可以使用 `add` 來指定要使用的追蹤接聽項名稱與型別。 在我們的組態範例中，我們將接聽項命名為 "tx" 並將標準 .NET Framework 追蹤接聽項 (<xref:System.Diagnostics.XmlWriterTraceListener>) 當成要使用的型別加入。 請使用 `initializeData` 來設定該接聽項的記錄檔名稱。 此外，您可以使用完整路徑來取代簡單檔名。  
  
 每個追蹤訊息類型都會指派一個層級來代表自己的重要程度。 如果應用程式定義域的追蹤層級等於或小於事件型別的層級，則會產生該訊息。 追蹤層級可由組態檔中的 `switchValue` 設定來控制。 下表定義了與診斷追蹤訊息相關聯的層級。  
  
|追蹤層級|描述|  
|-----------------|-----------------|  
|Critical|已發生如下列所述的嚴重失敗情況：<br /><br /> -使用者功能可能會導致立即的遺失發生錯誤。<br />-需要事件的系統管理員可採取動作避免遺失的功能。<br />程式碼停止回應。<br />-此追蹤層級也可以提供足夠的內容，用於解譯其他重要的追蹤。 如此便可協助找出導致嚴重失敗的作業序列。|  
|錯誤|已經發生可導致使用者功能喪失的錯誤 (例如，無效的組態或網路行為)。|  
|警告|存在一個可間接導致錯誤或嚴重失敗的狀況 (例如，配置失敗或到達上限)。 對使用者程式碼錯誤的正常處理 (例如，交易中止、逾時、驗證失敗) 也可能產生警告。|  
|資訊|會產生對監控與診斷系統狀態、衡量效能，或描述分析有幫助的訊息。 這些訊息包含交易與登記存留期事件，例如正在建立或認可的交易、重要界限的跨越，或是重要資源的配置。 這時開發人員可以使用此類資訊來進行容量規劃與效能管理。|  
  
## <a name="trace-codes"></a>追蹤程式碼  
 下表列出由 <xref:System.Transactions> 基礎結構所產生的追蹤程式碼。 其中包含資料表中的追蹤程式碼識別項，<xref:System.Diagnostics.EventTypeFilter.EventType%2A>列舉型別層級追蹤，並中包含的額外資料**TraceRecord**追蹤。 此外，對應的追蹤層級的追蹤也會儲存在**TraceRecord**。  
  
|TraceCode|EventType|TraceRecord 中的額外資料|  
|---------------|---------------|-------------------------------|  
|TransactionCreated|Info|TransactionTraceId|  
|TransactionPromoted|Info|本機 TransactionTraceId、Distributed TransactionTraceId|  
|EnlistmentCreated|Info|TransactionTraceId、EnlistmentTraceId、EnlistmentType (永久性/變動性)、EnlistmentOptions|  
|EnlistmentCallbackNegative|警告|TransactionTraceId、EnlistmentTraceId、<br /><br /> 回呼 (forcerollback/中止/indoubt)|  
|TransactionRollbackCalled|警告|TransactionTraceId|  
|TransactionAborted|警告|TransactionTraceId|  
|TransactionInDoubt|警告|TransactionTraceId|  
|TransactionScopeCreated|Info|TransactionScopeResult，可能為下列各項：<br /><br /> -新的交易。<br />傳遞的交易。<br />-相依交易傳遞。<br />-使用目前的交易。<br />-沒有交易。<br /><br /> 目前新 TransactionTraceId|  
|TransactionScopeDisposed|資訊|TransactionTraceId 範圍的 「 預期 」 目前的交易。|  
|TransactionScopeIncomplete|警告|TransactionTraceId 範圍的 「 預期 」 目前的交易。|  
|TransactionScopeNestedIncorrectly|警告|TransactionTraceId 範圍的 「 預期 」 目前的交易。|  
|TransactionScopeCurrentTransactionChanged|警告|目前舊有 TransactionTraceId、其他 TransactionTraceId|  
|TransactionScopeTimeout|警告|TransactionTraceId 範圍的 「 預期 」 目前的交易。|  
|DependentCloneCreated|Info|TransactionTraceId、所建立的相依交易型別 (RollbackIfNotComplete/BlockCommitUntilComplete)|  
|DependentCloneComplete|Info|TransactionTraceId|  
|RecoveryComplete|Info|資源管理員 GUID (從基底)|  
|Reenlist|Info|資源管理員 GUID (從基底)|  
|TransactionSerialized|Info|TransactionTraceId。|  
|TransactionException|錯誤|例外狀況訊息|  
|InvalidOperationException|錯誤|例外狀況訊息|  
|InternalError|Critical|例外狀況訊息|  
|TransferEvent||當交易已還原序列化，或是由 <xref:System.Transactions> 交易提升為分散式交易，則會寫入來自 ExecutionContext 與分散式交易識別碼的目前 ActivityID。<br /><br /> 當 DTC 回呼 Managed 程式碼，分散式交易識別碼就會針對回呼的持續時間設為 ExecutionContext 中的 ActivityID。|  
|ConfiguredDefaultTimeoutAdjusted|警告|無額外的資料|  
|TransactionTimeout|警告|目前逾時的交易 TransactionTraceId。|  
  
 每個前置額外資料項目的 XML 結構描述都具有下列格式。  
  
### <a name="transactiontraceidentifier"></a>TransactionTraceIdentifier  
 `<TransactionTraceIdentifier>`  
  
 `<TransactionIdentifier >`  
  
 `string representation of transaction id`  
  
 `</TransactionIdentifier>`  
  
 `< CloneIdentifier >`  
  
 `the clone id number`  
  
 `</CloneIdentifier>`  
  
 `</TransactionTraceIdentifier>`  
  
### <a name="enlistmenttraceidentifier"></a>EnlistmentTraceIdentifier  
 `<EnlistmentTraceIdentifier>`  
  
 `<ResourceManagerId>`  
  
 `string form of guid`  
  
 `</ResourceManagerId>`  
  
 `<TransactionTraceIdentifier>`  
  
 `<TransactionIdentifier >`  
  
 `string representation of transaction id`  
  
 `</TransactionIdentifier>`  
  
 `<CloneIdentifier >`  
  
 `the clone id number`  
  
 `</CloneIdentifier>`  
  
 `<TransactionTraceIdentifier>`  
  
 `<EnlistmentIdentifier>`  
  
 `the enlistment id number`  
  
 `</EnlistmentIdentifier>`  
  
 `</EnlistmentTraceIdentifier>`  
  
### <a name="resource-manager-identifier"></a>資源管理員識別項  
 `<ResourceManagerId>`  
  
 `string form of guid`  
  
 `</ResourceManagerId>`  
  
## <a name="security-issues-for-tracing"></a>追蹤安全性問題  
 當您以系統管理員身分開啟追蹤時，機密資訊可能會公開可檢視的追蹤記錄檔寫入預設。 若要減輕任何可能的安全性威脅，您應該考慮將追蹤記錄檔儲存在安全的位置共用和檔案系統存取權限所控制。
