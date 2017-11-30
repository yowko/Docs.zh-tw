---
title: "應用程式定義域資源監視"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- monitoring managed memory use by application domain
- application domains, memory use
- memory use, monitoring
- application domains, resource monitoring
ms.assetid: 318bedf8-7f35-4f00-b34a-2b7b8e3fa315
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 62a514f94857044af5020d36a1cfd6ce06741ac7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="application-domain-resource-monitoring"></a>應用程式定義域資源監視
應用程式定義域資源監視 (ARM) 可讓主機監視由應用程式定義域的 CPU 和記憶體使用量。 這非常有用，例如 ASP.NET 使用長時間執行的處理序中的許多應用程式定義域的主機。 主機可以卸載嚴重影響效能的整個程序，但僅限於如果它可以識別問題的應用程式的應用程式的應用程式定義域。 ARM 提供可用來協助您制定這類的資訊。  
  
 例如，主機服務可能有許多 ASP.NET 伺服器上執行的應用程式。 如果程序中的一個應用程式開始耗用太多記憶體或太多處理器時間，則裝載服務可以使用 ARM 找出造成問題的應用程式定義域。  
  
 ARM 是充分輕量型即時應用程式中使用。 您可以使用 Windows (ETW) 或直接透過 managed 或原生應用程式開發介面的事件追蹤來存取資訊。  
  
## <a name="enabling-resource-monitoring"></a>啟用資源的監視  
 ARM 可以用四種方式啟用： 所提供的組態檔，common language runtime (CLR) 啟動時，使用 unmanaged 裝載 API，使用 managed 程式碼，或接聽 ARM ETW 事件。  
  
 只要啟用 ARM 時，就會開始收集程序中的所有應用程式定義域的資料。如果啟用 ARM 之前，已建立應用程式定義域，累積資料會啟動啟用 ARM 時，不會在建立應用程式網域。一旦啟用後，就無法停用 ARM。  
  
-   您也可以加入在 CLR 啟動啟用 ARM [ \<appDomainResourceMonitoring >](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)組態檔，以及設定項目`enabled`屬性`true`。 值為`false`（預設值） 只表示 ARM 未啟用在啟動時，您可以啟動它之後使用其中一種其他啟動機制。  
  
-   主應用程式可以藉由要求來啟用 ARM [ICLRAppDomainResourceMonitor](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)裝載介面。 一旦成功取得此介面，會啟用 ARM。  
  
-   Managed 程式碼可以藉由設定靜態啟用 ARM (`Shared`在 Visual Basic 中)<xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>屬性`true`。 一旦設定屬性，則會啟用 ARM。  
  
-   您可以接聽 ETW 事件，在啟動之後啟用 ARM。 ARM 已啟用並開始時啟用公用提供者引發事件的所有應用程式定義域`Microsoft-Windows-DotNETRuntime`使用`AppDomainResourceManagementKeyword`關鍵字。 若要讓資料相互關聯與應用程式定義域和執行緒，您必須同時啟用`Microsoft-Windows-DotNETRuntimeRundown`提供者與`ThreadingKeyword`關鍵字。  
  
## <a name="using-arm"></a>使用 ARM  
 ARM 提供由應用程式定義域和記憶體使用量的相關資訊的三種類型的總處理器時間。  
  
-   **應用程式定義域，以秒為單位的處理器時間總計**： 這加上所花費的時間在應用程式定義域中執行其存留期間的所有執行緒的作業系統所回報的執行緒時間計算。 封鎖或睡眠中的執行緒不會使用處理器時間。 當執行緒呼叫原生程式碼時，執行緒花在原生程式碼的時間會包含在所呼叫的應用程式定義域計數。  
  
    -   Managed API:<xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>屬性。  
  
    -   裝載 API: [iclrappdomainresourcemonitor:: Getcurrentcputime](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentcputime-method.md)方法。  
  
    -   ETW 事件： `ThreadCreated`， `ThreadAppDomainEnter`，和`ThreadTerminated`事件。 提供者和關鍵字的相關資訊，請參閱 「 AppDomain 資源監視事件 」，在[CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)。  
  
-   **在其生命週期，以位元組為單位進行應用程式定義域的 managed 的配置的總**： 總配置不一定會反映應用程式定義域的記憶體使用因為配置的物件可能存留較短。 不過，如果應用程式會配置與釋放大量物件，配置的記憶體成本可能會很大。  
  
    -   Managed API:<xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>屬性。  
  
    -   裝載 API: [iclrappdomainresourcemonitor:: Getcurrentallocated](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentallocated-method.md)方法。  
  
    -   ETW 事件：`AppDomainMemAllocated`事件，`Allocated`欄位。  
  
-   **受管理的記憶體，以位元組為單位，由應用程式定義域所參考且未被記憶體的最新的完整的封鎖集合**： 這個數字之後，即正確只執行完整的封鎖集合。 （這是相較於並行的集合，會在背景進行，而不會封鎖應用程式）。例如，<xref:System.GC.Collect?displayProperty=nameWithType>方法多載會導致執行完整的封鎖集合。  
  
    -   Managed API:<xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>屬性。  
  
    -   裝載 API: [iclrappdomainresourcemonitor:: Getcurrentsurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)方法，`pAppDomainBytesSurvived`參數。  
  
    -   ETW 事件：`AppDomainMemSurvived`事件，`Survived`欄位。  
  
-   **總計受管理的記憶體，以位元組為單位，程序所參考且未被記憶體的最新的完整的封鎖集合**： 這個數字，就可以比較的個別應用程式定義域的未被回收的記憶體。  
  
    -   Managed API:<xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>屬性。  
  
    -   裝載 API: [iclrappdomainresourcemonitor:: Getcurrentsurvived](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-getcurrentsurvived-method.md)方法，`pTotalBytesSurvived`參數。  
  
    -   ETW 事件：`AppDomainMemSurvived`事件，`ProcessSurvived`欄位。  
  
### <a name="determining-when-a-full-blocking-collection-occurs"></a>決定完整時，封鎖集合就會發生  
 若要判斷未被回收記憶體的計數是精確時，您需要知道完整的封鎖集合只在發生時。 執行此作業的方法取決於您使用來檢查 ARM 統計資料的 API。  
  
#### <a name="managed-api"></a>受管理的應用程式開發介面  
 如果您使用的屬性<xref:System.AppDomain>類別，您可以使用<xref:System.GC.RegisterForFullGCNotification%2A?displayProperty=nameWithType>方法來註冊通知的完整集合。 您使用的臨界值並不重要，因為您正在等候完成的集合，而不是集合的方法。 您可以接著呼叫<xref:System.GC.WaitForFullGCComplete%2A?displayProperty=nameWithType>方法，這個方法會封鎖，直到完成完整的集合。 您可以建立在迴圈中呼叫的方法，且沒有任何必要的分析，每當此方法會傳回的執行緒。  
  
 或者，您可以呼叫<xref:System.GC.CollectionCount%2A?displayProperty=nameWithType>定期以查看是否增加的層代 2 回收計數的方法。 根據輪詢頻率，這項技術可能無法提供最精確的完整集合的項目表示。  
  
#### <a name="hosting-api"></a>裝載 API  
 如果您使用未受管理的裝載 API，您的主機必須將傳遞 CLR 的實作[IHostGCManager](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)介面。 CLR 會呼叫[ihostgcmanager:: Suspensionending](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)方法時，它會繼續執行而回收時已暫止的執行緒。 CLR 會產生已完成的集合傳遞做為參數的方法，讓主機可以判斷集合是否完整或部分。 實作[ihostgcmanager:: Suspensionending](../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-suspensionending-method.md)方法可以查詢未被回收的記憶體，以確定更新時，已擷取計數。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
 [ICLRAppDomainResourceMonitor 介面](../../../docs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md)  
 [\<appDomainResourceMonitoring>](../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)  
 [CLR ETW 事件](../../../docs/framework/performance/clr-etw-events.md)
