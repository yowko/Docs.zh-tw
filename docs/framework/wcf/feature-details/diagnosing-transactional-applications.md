---
title: "診斷異動式應用程式"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a993492-1088-4d10-871b-0c09916af05f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0826881bac88f2bfa933ae71b798186dafc55303
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="diagnosing-transactional-applications"></a>診斷異動式應用程式
本主題說明如何使用 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 的管理和診斷功能，對交易式應用程式進行疑難排解。  
  
## <a name="performance-counters"></a>效能計數器  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 提供了一組標準的效能計數器，可讓您測量交易式應用程式的效能。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][效能計數器](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)。  
  
 效能計數器分為三種不同的層級：服務、端點和作業，如下表所述。  
  
### <a name="service-performance-counters"></a>服務效能計數器  
  
|效能計數器|描述|  
|-------------------------|-----------------|  
|流動的交易數|流動至此服務中作業的交易數。 每當傳送給服務的訊息中出現一筆交易時，此計數器就會遞增。|  
|每秒流動的交易數|每秒鐘流動至此服務中作業的交易數。 每當傳送給服務的訊息中出現一筆交易時，此計數器就會遞增。|  
|認可的交易作業數|此服務中交易已完成且其結果已經過認可的交易作業數。 在這類作業下完成的工作會完全經過認可。 資源會根據作業中完成的工作來更新。|  
|每秒認可的交易作業數|每秒鐘此服務中交易已完成且其結果已經過認可的交易作業數。 在這類作業下完成的工作會完全經過認可。 資源會根據作業中完成的工作來更新。|  
|中止的交易作業數|此服務中交易已完成且其結果已中止的交易作業數。 在這類作業下完成的工作會復原。 資源會還原為其先前狀態。|  
|每秒中止的交易作業數|每秒鐘此服務中交易已完成且其結果已中止的交易作業數。 在這類作業下完成的工作會復原。 資源會還原為其先前狀態。|  
|不確定的交易作業數|此服務中交易已完成且其結果不確定的交易作業數。 結果不確定的已完成工作會處於不定狀態。 資源會保留，以等待結果。|  
|每秒不確定的交易作業數|每秒鐘此服務中交易已完成且其結果不確定的交易作業數。 結果不確定的已完成工作會處於不定狀態。 資源會保留，以等待結果。|  
  
### <a name="endpoint-performance-counters"></a>端點效能計數器  
  
|效能計數器|描述|  
|-------------------------|-----------------|  
|流動的交易數|流動至此端點處作業的交易數。 每當傳送給端點的訊息中出現一筆交易時，此計數器就會遞增。|  
|每秒流動的交易數|每秒鐘流動至此端點處作業的交易數。 每當傳送給端點的訊息中出現一筆交易時，此計數器就會遞增。|  
  
### <a name="operation-performance-counters"></a>作業效能計數器  
  
|效能計數器|描述|  
|-------------------------|-----------------|  
|流動的交易數|流動至此端點處作業的交易數。 每當傳送給端點的訊息中出現一筆交易時，此計數器就會遞增。|  
|每秒流動的交易數|每秒鐘流動至此端點處作業的交易數。 每當傳送給端點的訊息中出現一筆交易時，此計數器就會遞增。|  
  
## <a name="windows-management-instrumentation"></a>Windows Management Instrumentation  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 會透過 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Windows Management Instrumentation (WMI) 提供者，在執行階段公開服務的檢查資料。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]存取 WMI 資料，請參閱[使用 Windows Management Instrumentation 進行診斷](../../../../docs/framework/wcf/diagnostics/wmi/index.md)。  
  
 許多唯讀的 WMI 屬性會指示服務套用的異動設定， 下表則列出這些設定。  
  
 服務的 `ServiceBehaviorAttribute` 具有下列屬性。  
  
|名稱|類型|描述|  
|----------|----------|-----------------|  
|ReleaseServiceInstanceOnTransactionComplete|Boolean|指定是否會在目前的交易完成時回收服務物件。|  
|TransactionAutoCompleteOnSessionClose|Boolean|指定當目前的工作階段關閉時，是否會完成暫止的交易。|  
|TransactionIsolationLevel|字串，其中包含 <xref:System.Transactions.IsolationLevel> 列舉的有效值。|指定服務支援的交易隔離等級。|  
|TransactionTimeout|<xref:System.DateTime>|指定異動必須完成的期間。|  
  
 `ServiceTimeoutsBehavior` 具有下列屬性。  
  
|名稱|類型|描述|  
|----------|----------|-----------------|  
|TransactionTimeout|<xref:System.DateTime>|指定異動必須完成的期間。|  
  
 繫結的 `TransactionFlowBindingElement` 具有下列屬性。  
  
|名稱|類型|描述|  
|----------|----------|-----------------|  
|TransactionProtocol|字串，其中包含 <xref:System.ServiceModel.TransactionProtocol> 型別的有效值。|指定用於流動交易的交易通訊協定。|  
|TransactionFlow|Boolean|指定是否已啟用傳入交易流程。|  
  
 作業的 `OperationBehaviorAttribute` 具有下列屬性：  
  
|名稱|類型|描述|  
|----------|----------|-----------------|  
|TransactionAutoComplete|Boolean|指定未發生未處理的例外狀況時是否要自動認可目前的交易。|  
|TransactionScopeRequired|Boolean|指定作業是否需要交易。|  
  
 作業的 `TransactionFlowAttribute` 具有下列屬性。  
  
|名稱|類型|描述|  
|----------|----------|-----------------|  
|TransactionFlowOption|字串，其中包含 <xref:System.ServiceModel.TransactionFlowOption> 列舉的有效值。|指定交易流程被需要的程度。|  
  
## <a name="tracing"></a>追蹤  
 追蹤可讓您監視及分析交易式應用程式內的錯誤。 您可以使用下列方式啟用追蹤：  
  
-   標準 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 追蹤  
  
     這種追蹤型別與追蹤任何 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式相同。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][設定追蹤](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)。  
  
-   WS-AtomicTransaction 追蹤  
  
     可以使用來啟用 Ws-atomictransaction 追蹤[Ws-atomictransaction 組態公用程式 (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)。 此類追蹤可讓您深入了解系統內異動和參與者的狀態。 若要同時啟用內部服務模型追蹤，您可以將 `HKLM\SOFTWARE\Microsoft\WSAT\3.0\ServiceModelDiagnosticTracing` 登錄機碼設定為 <xref:System.Diagnostics.SourceLevels> 列舉的有效值。 您可以使用和其他 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式相同的方法，啟用訊息記錄。  
  
-   `System.Transactions` 追蹤  
  
     使用 OleTransactions 通訊協定時，無法追蹤通訊協定訊息。 <xref:System.Transactions> 基礎結構提供的追蹤支援 (使用 OleTransactions) 可讓使用者檢視交易發生的事件。 若要啟用 <xref:System.Transactions> 應用程式的追蹤，請在 `App.config` 組態檔內加入下列程式碼。  
  
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
  
     這個程式碼也可以啟用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 追蹤，因為 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 也會使用 <xref:System.Transactions> 基礎結構。  
  
## <a name="see-also"></a>請參閱  
 [管理與診斷](../../../../docs/framework/wcf/diagnostics/index.md)  
 [設定追蹤](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [WS-AtomicTransaction 設定公用程式 (wsatConfig.exe)](../../../../docs/framework/wcf/ws-atomictransaction-configuration-utility-wsatconfig-exe.md)
