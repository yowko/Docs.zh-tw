---
title: 診斷交易式應用程式
ms.date: 03/30/2017
ms.assetid: 4a993492-1088-4d10-871b-0c09916af05f
ms.openlocfilehash: fb3a83083e876cf697621ba70dcf7dd67636f83a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599213"
---
# <a name="diagnosing-transactional-applications"></a>診斷交易式應用程式
本主題描述如何使用 Windows Communication Foundation （WCF）管理和診斷功能，對交易式應用程式進行疑難排解。  
  
## <a name="performance-counters"></a>效能計數器  
 WCF 提供一組標準的效能計數器，可讓您測量交易式應用程式的效能。 如需相關資訊，請參閱 [Performance Counters](../diagnostics/performance-counters/index.md)。  
  
 效能計數器分為三種不同的層級：服務、端點和作業，如下表所述。  
  
### <a name="service-performance-counters"></a>服務效能計數器  
  
|效能計數器|描述|  
|-------------------------|-----------------|  
|流動的交易數|流動至此服務中作業的異動數。 每當傳送給服務的訊息中出現一筆交易時，此計數器就會遞增。|  
|每秒流動的異動數|每秒鐘流動至此服務中作業的異動數。 每當傳送給服務的訊息中出現一筆交易時，此計數器就會遞增。|  
|認可的交易作業數|此服務中異動已完成且其結果已經過認可的異動作業數。 在這類作業下完成的工作會完全經過認可。 資源會根據作業中完成的工作來更新。|  
|每秒認可的交易作業數|每秒鐘此服務中異動已完成且其結果已經過認可的異動作業數。 在這類作業下完成的工作會完全經過認可。 資源會根據作業中完成的工作來更新。|  
|中止的交易作業數|此服務中異動已完成且其結果已中止的異動作業數。 在這類作業下完成的工作會復原。 資源會還原為其先前狀態。|  
|每秒中止的交易作業數|每秒鐘此服務中交易已完成且其結果已中止的交易作業數。 在這類作業下完成的工作會復原。 資源會還原為其先前狀態。|  
|不確定的交易作業數|此服務中交易已完成且其結果不確定的交易作業數。 結果不確定的已完成工作會處於不定狀態。 資源會保留，以等待結果。|  
|每秒不確定的交易作業數|每秒鐘此服務中交易已完成且其結果不確定的交易作業數。 結果不確定的已完成工作會處於不定狀態。 資源會保留，以等待結果。|  
  
### <a name="endpoint-performance-counters"></a>端點效能計數器  
  
|效能計數器|描述|  
|-------------------------|-----------------|  
|流動的交易數|流動至此端點處作業的異動數。 每當傳送給端點的訊息中出現一筆異動時，此計數器就會遞增。|  
|每秒流動的異動數|每秒鐘流動至此端點處作業的異動數。 每當傳送給端點的訊息中出現一筆異動時，此計數器就會遞增。|  
  
### <a name="operation-performance-counters"></a>作業效能計數器  
  
|效能計數器|描述|  
|-------------------------|-----------------|  
|流動的交易數|流動至此端點處作業的異動數。 每當傳送給端點的訊息中出現一筆異動時，此計數器就會遞增。|  
|每秒流動的異動數|每秒鐘流動至此端點處作業的異動數。 每當傳送給端點的訊息中出現一筆異動時，此計數器就會遞增。|  
  
## <a name="windows-management-instrumentation"></a>Windows Management Instrumentation  
 WCF 會透過 WCF Windows Management Instrumentation （WMI）提供者，在執行時間公開服務的檢查資料。 如需存取 WMI 資料的詳細資訊，請參閱[使用 Windows Management Instrumentation 進行診斷](../diagnostics/wmi/index.md)。  
  
 許多唯讀的 WMI 屬性會指示服務套用的異動設定， 下表則列出這些設定。  
  
 服務的 `ServiceBehaviorAttribute` 具有下列屬性。  
  
|名稱|類型|描述|  
|----------|----------|-----------------|  
|ReleaseServiceInstanceOnTransactionComplete|布林值|指定是否會在目前的異動完成時回收服務物件。|  
|TransactionAutoCompleteOnSessionClose|布林值|指定當目前的工作階段關閉時，是否會完成暫止的異動。|  
|TransactionIsolationLevel|字串，其中包含 <xref:System.Transactions.IsolationLevel> 列舉的有效值。|指定服務支援的異動隔離等級。|  
|TransactionTimeout|<xref:System.DateTime>|指定異動必須完成的期間。|  
  
 `ServiceTimeoutsBehavior` 具有下列屬性。  
  
|名稱|類型|描述|  
|----------|----------|-----------------|  
|TransactionTimeout|<xref:System.DateTime>|指定異動必須完成的期間。|  
  
 繫結的 `TransactionFlowBindingElement` 具有下列屬性。  
  
|名稱|類型|描述|  
|----------|----------|-----------------|  
|TransactionProtocol|字串，其中包含 <xref:System.ServiceModel.TransactionProtocol> 型別的有效值。|指定用於流動異動的異動通訊協定。|  
|TransactionFlow|布林值|指定是否已啟用傳入異動流程。|  
  
 作業的 `OperationBehaviorAttribute` 具有下列屬性：  
  
|名稱|類型|描述|  
|----------|----------|-----------------|  
|TransactionAutoComplete|布林值|指定未發生未處理的例外狀況時是否要自動認可目前的交易。|  
|TransactionScopeRequired|布林值|指定作業是否需要異動。|  
  
 作業的 `TransactionFlowAttribute` 具有下列屬性。  
  
|名稱|類型|描述|  
|----------|----------|-----------------|  
|TransactionFlowOption|字串，其中包含 <xref:System.ServiceModel.TransactionFlowOption> 列舉的有效值。|指定異動流程被需要的程度。|  
  
## <a name="tracing"></a>追蹤  
 追蹤可讓您監視及分析交易式應用程式內的錯誤。 您可以使用下列方式啟用追蹤：  
  
- 標準 WCF 追蹤  
  
     這種類型的追蹤與追蹤任何 WCF 應用程式相同。 如需詳細資訊，請參閱 [Configuring Tracing](../diagnostics/tracing/configuring-tracing.md)。  
  
- WS-AtomicTransaction 追蹤  
  
     您可以使用 ws-atomictransaction 設定[公用程式（wsatconfig.exe）](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md)來啟用 ws-atomictransaction 追蹤。 此類追蹤可讓您深入了解系統內交易和參與者的狀態。 若要同時啟用內部服務模型追蹤，您可以將 `HKLM\SOFTWARE\Microsoft\WSAT\3.0\ServiceModelDiagnosticTracing` 登錄機碼設定為 <xref:System.Diagnostics.SourceLevels> 列舉的有效值。 您可以使用與其他 WCF 應用程式相同的方式來啟用訊息記錄。  
  
- `System.Transactions` 追蹤  
  
     使用 OleTransactions 通訊協定時，無法追蹤通訊協定訊息。 <xref:System.Transactions> 基礎結構提供的追蹤支援 (使用 OleTransactions) 可讓使用者檢閱異動發生的事件。 若要啟用 <xref:System.Transactions> 應用程式的追蹤，請在 `App.config` 組態檔內加入下列程式碼。  
  
    ```xml  
    <configuration>  
      <system.diagnostics>  
         <sources>  
            <source name="System.Transactions" switchValue="Verbose, ActivityTracing">  
               <listeners>  
                  <add name="Text"  
                     type="System.Diagnostics.XmlWriterTraceListener"  
                     initializeData="SysTx.log"  
                     traceOutputOptions="Callstack" />  
               </listeners>  
            </source>  
         </sources>  
         <trace autoflush="true" indentsize="4">  
         </trace>  
      </system.diagnostics>  
    </configuration>  
    ```  
  
     這也會啟用 WCF 追蹤，因為 WCF 也會利用 <xref:System.Transactions> 基礎結構。  
  
## <a name="see-also"></a>請參閱

- [系統管理與診斷](../diagnostics/index.md)
- [設定追蹤](../diagnostics/tracing/configuring-tracing.md)
- [WS-AtomicTransaction 設定公用程式 (wsatConfig.exe)](../ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
