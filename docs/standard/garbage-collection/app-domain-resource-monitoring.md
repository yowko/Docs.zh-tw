---
title: 應用程式定義域資源監視
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- monitoring managed memory use by application domain
- application domains, memory use
- memory use, monitoring
- application domains, resource monitoring
ms.assetid: 318bedf8-7f35-4f00-b34a-2b7b8e3fa315
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50d601d711579bce2e2651a1efc65d824a50d47a
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2018
ms.locfileid: "47400695"
---
# <a name="application-domain-resource-monitoring"></a>應用程式定義域資源監視
應用程式定義域資源監視 (ARM) 可讓主機依應用程式定義域來監視 CPU 和記憶體的使用情況。 對於在長時間執行的處理序中使用許多應用程式定義域的主機 (例如 ASP.NET) 來說，這相當有用。 主機可以將對整個處理序的效能造成負面影響之應用程式的應用程式定義域卸載，但前提是它必須能夠識別有問題的應用程式。 ARM 提供可用來協助做出此判斷的資訊。  
  
 例如，主機服務可能有許多應用程式在 ASP.NET 伺服器上執行。 如果處理序中的某個應用程式開始耗用太多記憶體或太多處理器時間，主機服務可以使用 ARM 來識別造成問題的應用程式定義域。  
  
 ARM 非常輕量，足以在即時應用程式中使用。 您可以使用 Windows 事件追蹤 (ETW) 或直接透過受控 API 或原生 API 來存取資訊。  
  
## <a name="enabling-resource-monitoring"></a>啟用資源監視  
 有四種可啟用 ARM 的方式：藉由在通用語言執行平台 (CLR) 啟動時提供組態檔、藉由使用非受控裝載 API、藉由使用受控碼，或藉由接聽 ARM ETW 事件。  
  
 ARM 一經啟用之後，就會立即開始收集處理序中所有應用程式定義域上的資料。如果應用程式定義域的建立時間是在啟用 ARM 之前，就會在啟用 ARM 時開始累積資料，而不是在應用程式定義域建立時。ARM 在啟用後即無法停用。  
  
-   您可以在 CLR 啟動時啟用 ARM，方法是將 [\<appDomainResourceMonitoring>](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md) 元素新增至組態檔，然後將 `enabled` 屬性設定為 `true`。 值為 `false` (預設值) 時，表示只有該 ARM 未在啟動時啟用；您可以稍後使用其中一個其他啟用機制來啟用它。  
  
-   主機可以藉由要求 [ICLRAppDomainResourceMonitor](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) 主控介面來啟用 ARM。 順利取得此介面之後，便會啟用 ARM。  
  
-   受控碼可以藉由將靜態 (在 Visual Basic 中為 `Shared`) <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType> 屬性設定為 `true` 來啟用 ARM。 設定好此屬性之後，就會立即啟用 ARM。  
  
-   您可以啟動後藉由接聽 ETW 事件來啟用 ARM。 當您藉由使用 `AppDomainResourceManagementKeyword` 關鍵字來啟用公用提供者 `Microsoft-Windows-DotNETRuntime` 時，ARM 就會變成啟用並開始針對所有應用程式定義域引發事件。 若要將資料與應用程式定義域及執行緒相互關聯，您必須使用 `ThreadingKeyword` 關鍵字來一併啟用 `Microsoft-Windows-DotNETRuntimeRundown` 提供者。  
  
## <a name="using-arm"></a>使用 ARM  
 ARM 會提供應用程式定義域所使用的處理器時間總計，以及三種有關記憶體使用情況的資訊。  
  
-   **應用程式定義域的處理器時間總計 (單位為秒)**：計算方式是將作業系統所回報的執行緒時間加總，這包括所有在存留期內花時間在應用程式定義域中執行的執行緒。 已被封鎖或睡眠中的執行緒不會使用處理器時間。 當執行緒呼叫原生程式碼時，該執行緒花費在原生程式碼的時間會包含在進行呼叫之應用程式定義域的計數中。  
  
    -   受控 API：<xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> 屬性。  
  
    -   裝載 API：[ICLRAppDomainResourceMonitor::GetCurrentCpuTime](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md) 方法。  
  
    -   ETW 事件：`ThreadCreated``ThreadAppDomainEnter`及 `ThreadTerminated` 事件。 如需有關提供者和關鍵字的資訊，請參閱 [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)中的＜AppDomain 資源監視事件＞。  
  
-   **應用程式定義域在其存留期內所做的受控配置總計 (單位為位元組)**：配置總計並不一定會反映應用程式定義域所使用的記憶體，因為所配置物件的存留期可能很短。 不過，如果應用程式配置並釋出大量物件，配置成本就可能相當高。  
  
    -   受控 API：<xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> 屬性。  
  
    -   裝載 API：[ICLRAppDomainResourceMonitor::GetCurrentAllocated](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md) 方法。  
  
    -   ETW 事件：`AppDomainMemAllocated` 事件、`Allocated` 欄位。  
  
-   **應用程式定義域所參考並在最近的完整、阻斷式收集中未被回收的受控記憶體 (單位為位元組)**：此數字只有在進行完整、阻斷式收集後才會精確。 (這是相對於在背景中進行而不會阻斷應用程式的並行收集)。例如，<xref:System.GC.Collect?displayProperty=nameWithType> 方法多載就會造成完整、阻斷式收集。  
  
    -   受控 API：<xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType> 屬性。  
  
    -   裝載 API：[ICLRAppDomainResourceMonitor::GetCurrentSurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) 方法、`pAppDomainBytesSurvived` 參數。  
  
    -   ETW 事件：`AppDomainMemSurvived` 事件、`Survived` 欄位。  
  
-   **處理序所參考並在最近的完整、阻斷式收集中未被回收的受控記憶體總計 (單位為位元組)**：可以將個別應用程式定義域未被回收的記憶體與此數字做比較。  
  
    -   受控 API：<xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType> 屬性。  
  
    -   裝載 API：[ICLRAppDomainResourceMonitor::GetCurrentSurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md) 方法、`pTotalBytesSurvived` 參數。  
  
    -   ETW 事件：`AppDomainMemSurvived` 事件、`ProcessSurvived` 欄位。  
  
### <a name="determining-when-a-full-blocking-collection-occurs"></a>判斷發生完整、阻斷式收集的時間  
 若要判斷何時的未回收記憶體計數是精確的，您必須知道剛發生完整、阻斷式收集的時間。 執行這項操作的方法取決於您用來檢查 ARM 統計資料的 API。  
  
#### <a name="managed-api"></a>受控 API  
 如果您使用 <xref:System.AppDomain> 類別的屬性，則可以使用 <xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=nameWithType> 方法來註冊接收完整收集的通知。 您使用的閾值並不重要，因為您是要等候收集完成，而不是使用收集方法。 您可以接著呼叫 <xref:System.GC.WaitForFullGCComplete%2A?displayProperty=nameWithType> 方法，這會進行阻斷，直到完整收集完成為止。 您可以建立一個呼叫迴圈中方法並在方法返回時執行任何必要分析的執行緒。  
  
 或者，您也可以定期呼叫 <xref:System.GC.CollectionCount%2A?displayProperty=nameWithType> 方法，以查看第 2 代收集的計數是否已增加。 視輪詢頻率而定，此技術可能無法精確指出完整收集的發生次數。  
  
#### <a name="hosting-api"></a>裝載 API  
 如果您使用非受控裝載 API，您的主機就必須將 [IHostGCManager](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md) 介面實作傳遞給 CLR。 CLR 會在繼續執行發生收集時被暫止的執行緒時，呼叫 [IHostGCManager::SuspensionEnding](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) 方法。 CLR 會將已完成的收集世代以方法參數的形式傳遞，讓主機能夠判斷該收集是完整收集還是部分收集。 您的 [IHostGCManager::SuspensionEnding](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md) 方法實作可以查詢未被回收的記憶體，以確定計數是在更新後所立即擷取的計數。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
- [ICLRAppDomainResourceMonitor 介面](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
- [\<appDomainResourceMonitoring>](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
- [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)
