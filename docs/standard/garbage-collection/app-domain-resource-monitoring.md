---
title: "Application Domain Resource Monitoring | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "monitoring managed memory use by application domain"
  - "application domains, memory use"
  - "memory use, monitoring"
  - "application domains, resource monitoring"
ms.assetid: 318bedf8-7f35-4f00-b34a-2b7b8e3fa315
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Application Domain Resource Monitoring
應用程式定義域資源監視 \(ARM\) 可讓主機監視應用程式定義域的 CPU 和記憶體使用量。  對於在長時間執行之處理序中使用許多應用程式定義域的主機 \(例如 ASP.NET\) 而言，這項功能很有用。  雖然主機可以卸載對整個處理序效能造成負面影響之應用程式的應用程式定義域，不過只有當它識別出有問題的應用程式時，才能進行卸載。  ARM 會提供一些可用來協助進行這類決策的資訊。  
  
 例如，主機服務可能會有許多在 ASP.NET 伺服器上執行的應用程式。  如果處理序中的某個應用程式開始耗用過多記憶體或過多處理器時間，主機服務就可以使用 ARM 來識別造成此問題的應用程式定義域。  
  
 ARM 相當精簡，很適合在即時應用程式中使用。  您可以使用 Windows 事件追蹤 \(ETW\) 或是直接透過 Managed 或原生 API 存取這項資訊。  
  
## 啟用資源監視  
 您可以用下列四種方式啟用 ARM：在 Common Language Runtime \(CLR\) 已啟動時提供組態檔、使用 Unmanaged 裝載 API、使用 Managed 程式碼，或是接聽 ARM ETW 事件。  
  
 一旦啟用 ARM 之後，它就會開始收集處理序中所有應用程式定義域的資料。  如果某個應用程式定義域是在啟用 ARM 之前建立的，就會在啟用 ARM 時 \(而非建立應用程式定義域時\) 開始累積資料。一旦啟用 ARM 之後，就無法停用。  
  
-   您可以將 [\<appDomainResourceMonitoring\>](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md) 項目加入至設定檔，並將 `enabled` 屬性設定為 `true`，藉以在 CLR 啟動時啟用 ARM。  `false` 值 \(預設值\) 只表示 ARM 不會在啟動時啟用。您之後仍然可以使用其他啟動機制來啟動它。  
  
-   主機可以透過要求 [ICLRAppDomainResourceMonitor](../../../ocs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) 裝載介面，啟用 ARM。  一旦成功取得這個介面之後，就會啟用 ARM。  
  
-   Managed 程式碼可以將靜態 \(Visual Basic 中的 `Shared`\) <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=fullName> 屬性設定為 `true`，藉以啟用 ARM。  一旦設定這個屬性之後，就會啟用 ARM。  
  
-   您可以透過接聽 ETW 事件，在啟動之後啟用 ARM。  當您使用 `AppDomainResourceManagementKeyword` 關鍵字來啟用公用提供者 `Microsoft-Windows-DotNETRuntime` 時，ARM 就會啟用並開始針對所有應用程式定義域引發事件。  若要讓資料與應用程式定義域和執行緒相互關聯，您也必須使用 `ThreadingKeyword` 關鍵字來啟用 `Microsoft-Windows-DotNETRuntimeRundown` 提供者。  
  
## 使用 ARM  
 ARM 會提供應用程式定義域所使用的處理器時間總計以及三種有關記憶體使用的資訊。  
  
-   **應用程式定義域的處理器時間總計，以秒為單位**：這個項目的計算方式為，針對存留期間於應用程式定義域中花費時間執行的所有執行緒，加總作業系統所回報的執行緒時間。  封鎖或休眠的執行緒不會使用處理器時間。  當某個執行緒呼叫進入原生程式碼時，該執行緒在原生程式碼中花費的時間就會納入進行呼叫之應用程式定義域的計算中。  
  
    -   Managed API：<xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=fullName> 屬性。  
  
    -   裝載 API：[ICLRAppDomainResourceMonitor::GetCurrentCpuTime](../Topic/ICLRAppDomainResourceMonitor::GetCurrentCpuTime%20Method.md) 方法。  
  
    -   ETW 事件：`ThreadCreated`、`ThreadAppDomainEnter` 和 `ThreadTerminated` 事件。  如需提供者和關鍵字的詳細資訊，請參閱 [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)中的＜AppDomain 資源監視事件＞。  
  
-   **在存留期間由應用程式定義域所進行的 Managed 配置總計，以位元組為單位**：配置總計不一定會反映應用程式定義域的記憶體使用，因為配置的物件可能存留較短。  不過，如果某個應用程式配置並釋放大量物件，配置的成本可能就很明顯。  
  
    -   Managed API：<xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=fullName> 屬性。  
  
    -   裝載 API：[ICLRAppDomainResourceMonitor::GetCurrentAllocated](../Topic/ICLRAppDomainResourceMonitor::GetCurrentAllocated%20Method.md) 方法。  
  
    -   ETW 事件：`AppDomainMemAllocated` 事件、`Allocated` 欄位。  
  
-   **由應用程式定義域所參考而且在最近一次完整、封鎖的記憶體回收時未被回收的 Managed 記憶體，以位元組為單位**：這個數字只有在完整、封鎖的記憶體回收之後才會正確。\(這與並行記憶體回收相反，因為這種作業是在背景中進行而且不會封鎖應用程式\)。例如，<xref:System.GC.Collect?displayProperty=fullName> 方法多載會執行完整、封鎖的記憶體回收。  
  
    -   Managed API：<xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=fullName> 屬性。  
  
    -   裝載 API：[ICLRAppDomainResourceMonitor::GetCurrentSurvived](../Topic/ICLRAppDomainResourceMonitor::GetCurrentSurvived%20Method.md) 方法、`pAppDomainBytesSurvived` 參數。  
  
    -   ETW 事件：`AppDomainMemSurvived` 事件、`Survived` 欄位。  
  
-   **由處理序所參考而且在最近一次完整、封鎖的記憶體回收時未被回收的 Managed 記憶體總計，以位元組為單位**：個別應用程式定義域未被回收的記憶體可以與這個數字比較。  
  
    -   Managed API：<xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=fullName> 屬性。  
  
    -   裝載 API：[ICLRAppDomainResourceMonitor::GetCurrentSurvived](../Topic/ICLRAppDomainResourceMonitor::GetCurrentSurvived%20Method.md) 方法、`pTotalBytesSurvived` 參數。  
  
    -   ETW 事件：`AppDomainMemSurvived` 事件、`ProcessSurvived` 欄位。  
  
### 判斷進行完整、封鎖記憶體回收的時間  
 若要判斷未被回收記憶體計數正確的時間，您必須知道進行完整、封鎖記憶體回收的時間。  進行這項作業的方法取決於您用來檢查 ARM 統計資料的 API。  
  
#### Managed API  
 如果您使用 <xref:System.AppDomain> 類別的屬性，就可以使用 <xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=fullName> 方法來註冊完整回收的通知。  您所使用的臨界值並不重要，因為您要等候回收完成，而非回收的方法。  然後，您可以呼叫 <xref:System.GC.WaitForFullGCComplete%2A?displayProperty=fullName> 方法，以便封鎖直到完整回收完成為止。  您可以建立執行緒，以便在迴圈中呼叫此方法並且每當方法傳回時進行任何必要的分析。  
  
 或者，您也可以定期呼叫 <xref:System.GC.CollectionCount%2A?displayProperty=fullName> 方法來查看層代 2 回收的計數是否增加。  根據輪詢頻率，這項技術可能無法提供如同進行完整回收的精確度。  
  
#### 裝載 API  
 如果您使用 Unmanaged 裝載 API，您的主機就必須傳遞 [IHostGCManager](../../../ocs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md) 介面的實作給 CLR。  當 CLR 繼續執行在進行回收時已經暫停的執行緒時，它就會呼叫 [IHostGCManager::SuspensionEnding](../Topic/IHostGCManager::SuspensionEnding%20Method.md) 方法。  CLR 會傳遞已完成回收的層代當做此方法的參數，因此主機就可以判斷回收是完整還是部分。  您的 [IHostGCManager::SuspensionEnding](../Topic/IHostGCManager::SuspensionEnding%20Method.md) 方法實作可以查詢未被回收的記憶體，以便確保一旦更新計數，就會擷取計數。  
  
## 請參閱  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=fullName>   
 [ICLRAppDomainResourceMonitor 介面](../../../ocs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)   
 [\<appDomainResourceMonitoring\>](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)   
 [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)