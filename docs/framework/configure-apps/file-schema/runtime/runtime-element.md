---
title: '&lt;執行階段&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#runtime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime
helpviewer_keywords:
- <runtime> element
- runtime element
- container tags, <runtime> element
ms.assetid: 1eb2fae3-de4b-45b6-852f-517c39b751bd
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 10cc81bee24fb757e4d826eb42d4ccf2324e6dab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54659523"
---
# <a name="ltruntimegt-element"></a>&lt;執行階段&gt;項目
提供 common language runtime 用來設定應用程式的資訊。  
  
 \<configuration>  
\<執行階段 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<runtime>  
</runtime>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節會說明項目子系和父項目。  
  
### <a name="attributes"></a>屬性  
 無。  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<alwaysFlowImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)|指定 Windows 識別一律流經非同步點，而不論模擬的執行方式為何。|  
|[\<AppContextSwitchOverrides>](../../../../../docs/framework/configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)|定義一或多個由 <xref:System.AppContext> 類別所使用的參數，以提供新功能的退出機制。|  
|[\<appDomainManagerAssembly>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)|針對處理序中的預設應用程式網域，指定提供應用程式網域管理員的組件。|  
|[\<appDomainManagerType>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)|針對預設應用程式網域，指定做為應用程式網域管理員的類型。|  
|[\<appDomainResourceMonitoring>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)|針對處理序存留期間，指示執行階段收集處理序中所有應用程式網域的統計資料。|  
|[\<assemblyBinding>](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)|包含有關組件版本重新導向和組件位置的資訊。|  
|[\<bypassTrustedAppStrongNames>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)|指定是否應略過信任組件的強式名稱驗證。|  
|[\<CompatSortNLSVersion>](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)|指定執行階段在執行字串比較時，應該使用舊版排序行為。|  
|[\<developmentMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)|指定執行階段是否要在 DEVPATH 環境變數所指定的目錄中搜尋組件。|  
|[\<disableCachingBindingFailures>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)|指定是否快取繫結失敗，也就是.NET Framework 2.0 版中的預設行為，已停用。|  
|[\<disableCommitThreadStack>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)|指定是否在執行緒啟動時認可完整執行緒堆疊。|  
|[\<disableFusionUpdatesFromADManager>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)|指定是否停用預設行為 (亦即允許執行階段主機覆寫應用程式網域的組態設定)。|  
|[\<EnableAmPmParseAdjustment>](../../../../../docs/framework/configure-apps/file-schema/runtime/enableampmparseadjustment-element.md)|針對只包含日期、月份、小時和上午/下午指示項的日期字串，決定日期及時間剖析方法是否使用一組調整過的規則來剖析。|  
|[\<enforceFIPSPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)|指定是否強制執行電腦設定需求，以便讓密碼編譯演算法符合美國聯邦資訊處理標準 (FIPS) 的規範。|  
|[\<etwEnable>](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)|指定是否為通用語言執行平台事件啟用 Windows 事件追蹤 (ETW)。|  
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)|指定 PerfCounter.dll 是否在 .NET Framework 1.1 版的應用程式中使用 CategoryOptions 登錄設定，以決定要從類別特定共用記憶體或從全域記憶體載入效能計數器資料。|  
|[\<gcAllowVeryLargeObjects>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)|在 64 位元平台上，啟用總大小大於 2 GB 的陣列。|  
|[\<gcConcurrent>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)|指定 common language runtime 是否同時執行記憶體回收。|  
|[\<GCCpuGroup>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)|指定記憶體回收是否支援多個 CPU 群組。|  
|[\<gcServer>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)|指定 Common Language Runtime 是否執行伺服器記憶體回收。|  
|[\<generatePublisherEvidence>](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)|指定執行階段是否使用程式碼存取安全性 (CAS) 發行者原則。|  
|[\<legacyCorruptedStateExceptionsPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)|指定執行階段是否允許 Managed 程式碼攔截存取違規和其他損毀狀態例外狀況。|  
|[\<legacyImpersonationPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)|指定 Windows 識別不會流經非同步點，而不論目前執行緒上執行內容的流程設定為何。|  
|[\<loadfromRemoteSources>](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)|指定是否以完全信任的方式載入來自遠端來源的組件。|  
|[<NetFx40_LegacySecurityPolicy>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)|指定執行階段是否使用舊版程式碼存取安全性 (CAS) 原則。|  
|[<NetFx40_PInvokeStackResilience>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)|指定執行階段是否會在執行階段自動修復不正確的平台叫用宣告，即使這麼做會使 Managed 和 Unmanaged 程式碼之間的轉換變慢。|  
|[<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)|指定執行階段是否使用固定的記憶體數量計算 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法的雜湊碼。|  
|[\<PreferComInsteadOfRemoting>](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)|指定執行階段會使用 COM Interop，而不是跨越應用程式網域界限的遠端處理。|  
|[\<relativeBindForResources>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)|最佳化附屬組件的探查。|  
|[\<shadowCopyVerifyByTimeStamp>](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)|指定陰影複製是否使用在 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 引進的預設啟動行為，或是要還原成舊版 .NET Framework 的啟動行為。|  
|[\<supportPortability>](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)|指定應用程式可以在兩個不同的 .NET Framework 實作中參考相同的組件，方法是停用將組件視為同等的預設行為 (此預設行為是基於應用程式可攜性的考量)。|  
|[\<system.runtime.caching>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|提供預設記憶體內部物件快取的組態資訊。|  
|[<Thread_UseAllCpuGroups>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)|指定執行階段是否會將 Managed 執行緒分散到所有 CPU 群組。|  
|[\<ThrowUnobservedTaskExceptions>](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)|指定未處理的工作例外狀況是否應終止執行中的處理序。|  
|[<TimeSpan_LegacyFormatMode>](../../../../../docs/framework/configure-apps/file-schema/runtime/timespan-legacyformatmode-element.md)|指定執行階段是否針對 <xref:System.TimeSpan> 值使用舊版格式。|  
|[\<useLegacyJit>](../../../../../docs/framework/configure-apps/file-schema/runtime/uselegacyjit-element.md)|決定通用語言執行平台是否針對 Just-In-Time 編譯使用舊版 64 位元 JIT 編譯器。|  
|[\<UseRandomizedStringHashAlgorithm>](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)|指定執行階段是否依照應用程式網域來計算字串的雜湊碼。|  
|[\<UseSmallInternalThreadStacks>](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)|要求執行階段在建立內部使用的特定執行緒時，使用明確的堆疊大小，而不是預設的堆疊大小。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
  
## <a name="remarks"></a>備註  
 中的子項目[\<執行階段 >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)組態檔區段的 common language runtime 用來設定應用程式的執行方式。 例如， [ \<Gcserver> >](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)項目可讓您判斷記憶體回收行程使用工作站記憶體回收 」 或 「 伺服器記憶體回收[ \<UseRandomizedStringHashAlgorithm >](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)元素會決定 common language runtime 是否計算每個應用程式或以每個應用程式定義域為基準，字串的雜湊程式碼和`AppContextSwitchOverrides`元素可讓程式庫的使用者若要選擇加入或退出變更程式庫所提供的功能。  
  
 中的項目[\<執行階段 >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)區段將會自動讀取 common language runtime 在應用程式啟動。 您也可以藉由提供其名稱來定義的非預設應用程式定義域的組態檔<xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType>屬性，其設定讀取自動載入應用程式定義域的時機。 您應該很少，是否需要直接讀取中的設定[\<執行階段 >](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)在您的應用程式組態檔中的區段。  
  
## <a name="see-also"></a>另請參閱
- [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)
