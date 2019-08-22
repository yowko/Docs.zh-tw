---
title: <runtime> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#runtime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime
helpviewer_keywords:
- <runtime> element
- runtime element
- container tags, <runtime> element
ms.assetid: 1eb2fae3-de4b-45b6-852f-517c39b751bd
ms.openlocfilehash: 3cf99a4dcf64b82846729d8663e398385b7a1086
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69663457"
---
# <a name="runtime-element"></a>\<執行時間 > 元素

提供 common language runtime 用來設定應用程式的資訊。

\<configuration > \
\<執行時間 >

## <a name="syntax"></a>語法

```xml
<runtime>
</runtime>
```

## <a name="attributes-and-elements"></a>屬性和項目

下列各節描述子項目和父元素。

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子元素

|項目|描述|
|-------------|-----------------|
|[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)|指定 Windows 識別一律流經非同步點，而不論模擬的執行方式為何。|
|[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)|定義一或多個由 <xref:System.AppContext> 類別所使用的參數，以提供新功能的退出機制。|
|[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)|針對處理序中的預設應用程式網域，指定提供應用程式網域管理員的組件。|
|[\<appDomainManagerType>](appdomainmanagertype-element.md)|針對預設應用程式網域，指定做為應用程式網域管理員的類型。|
|[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)|針對處理序存留期間，指示執行階段收集處理序中所有應用程式網域的統計資料。|
|[\<assemblyBinding>](assemblybinding-element-for-runtime.md)|包含有關組件版本重新導向和組件位置的資訊。|
|[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)|指定是否應略過信任組件的強式名稱驗證。|
|[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)|指定執行時間在執行字串比較時, 應使用舊版排序行為。|
|[\<developmentMode>](developmentmode-element.md)|指定執行階段是否要在 DEVPATH 環境變數所指定的目錄中搜尋組件。|
|[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)|指定是否停用系結失敗的快取 (這是 .NET Framework 版本2.0 中的預設行為)。|
|[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)|指定是否在執行緒啟動時認可完整執行緒堆疊。|
|[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)|指定是否停用預設行為 (亦即允許執行階段主機覆寫應用程式網域的組態設定)。|
|[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)|針對只包含日期、月份、小時和上午/下午指示項的日期字串，決定日期及時間剖析方法是否使用一組調整過的規則來剖析。|
|[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)|指定是否強制執行電腦設定需求，以便讓密碼編譯演算法符合美國聯邦資訊處理標準 (FIPS) 的規範。|
|[\<etwEnable>](etwenable-element.md)|指定是否為通用語言執行平台事件啟用 Windows 事件追蹤 (ETW)。|
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)|指定 PerfCounter.dll 是否在 .NET Framework 1.1 版的應用程式中使用 CategoryOptions 登錄設定，以決定要從類別特定共用記憶體或從全域記憶體載入效能計數器資料。|
|[\<gcAllowVeryLargeObjects>](gcallowverylargeobjects-element.md)|在 64 位元平台上，啟用總大小大於 2 GB 的陣列。|
|[\<gcConcurrent>](gcconcurrent-element.md)|指定 common language runtime 是否同時執行垃圾收集。|
|[\<GCCpuGroup>](gccpugroup-element.md)|指定記憶體回收是否支援多個 CPU 群組。|
|[\<gcServer>](gcserver-element.md)|指定 Common Language Runtime 是否執行伺服器記憶體回收。|
|[\<generatePublisherEvidence>](generatepublisherevidence-element.md)|指定執行階段是否使用程式碼存取安全性 (CAS) 發行者原則。|
|[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)|指定執行階段是否允許 Managed 程式碼攔截存取違規和其他損毀狀態例外狀況。|
|[\<legacyImpersonationPolicy>](legacyimpersonationpolicy-element.md)|指定 Windows 識別不會流經非同步點，而不論目前執行緒上執行內容的流程設定為何。|
|[\<loadfromRemoteSources>](loadfromremotesources-element.md)|指定是否以完全信任的方式載入來自遠端來源的組件。|
|[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)|指定執行階段是否使用舊版程式碼存取安全性 (CAS) 原則。|
|[\<NetFx40_PInvokeStackResilience>](netfx40-pinvokestackresilience-element.md)|指定執行階段是否會在執行階段自動修復不正確的平台叫用宣告，即使這麼做會使 Managed 和 Unmanaged 程式碼之間的轉換變慢。|
|[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)|指定執行階段是否使用固定的記憶體數量計算 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法的雜湊碼。|
|[\<PreferComInsteadOfRemoting>](prefercominsteadofmanagedremoting-element.md)|指定執行階段會使用 COM Interop，而不是跨越應用程式網域界限的遠端處理。|
|[\<relativeBindForResources>](relativebindforresources-element.md)|最佳化附屬組件的探查。|
|[\<shadowCopyVerifyByTimeStamp>](shadowcopyverifybytimestamp-element.md)|指定陰影複製是否使用 .NET Framework 4 中引進的預設啟動行為, 或還原為舊版 .NET Framework 的啟動行為。|
|[\<supportPortability>](supportportability-element.md)|指定應用程式可以在兩個不同的 .NET Framework 實作中參考相同的組件，方法是停用將組件視為同等的預設行為 (此預設行為是基於應用程式可攜性的考量)。|
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|提供預設記憶體內部物件快取的組態資訊。|
|[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)|指定執行階段是否會將 Managed 執行緒分散到所有 CPU 群組。|
|[\<ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md)|指定未處理的工作例外狀況是否應終止執行中的處理序。|
|[\<TimeSpan_LegacyFormatMode>](timespan-legacyformatmode-element.md)|指定執行階段是否針對 <xref:System.TimeSpan> 值使用舊版格式。|
|[\<useLegacyJit>](uselegacyjit-element.md)|決定通用語言執行平台是否針對 Just-In-Time 編譯使用舊版 64 位元 JIT 編譯器。|
|[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)|指定執行階段是否依照應用程式網域來計算字串的雜湊碼。|
|[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)|要求執行階段在建立內部使用的特定執行緒時，使用明確的堆疊大小，而不是預設的堆疊大小。|

### <a name="parent-elements"></a>父項目

|項目|描述|
|-------------|-----------------|
|`configuration`|通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|

## <a name="remarks"></a>備註

通用語言執行平臺會使用設定檔的[ \<執行時間 >](runtime-element.md)區段中的子項目, 來設定應用程式的執行方式。 例如, [ \<gcServer >](gcserver-element.md)元素會判斷垃圾收集行程是否使用工作站垃圾收集或伺服器[ \<](userandomizedstringhashalgorithm-element.md)垃圾收集、UseRandomizedStringHashAlgorithm > 元素判斷通用語言執行平臺是否會針對每個應用程式或每個應用程式網域, 計算字串的雜湊碼, `AppContextSwitchOverrides`而元素可讓程式庫使用者加入宣告或退出程式庫所提供的變更功能。

在應用程式啟動時, common language runtime 會自動讀取[ \<執行時間 >](runtime-element.md)區段中的元素。 您也可以定義非預設應用程式域的設定檔, 方法是將其名稱提供給<xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType>屬性; 載入應用程式域時, 會自動讀取其設定。 如果您需要在應用程式的設定檔中, 直接讀取[ \<執行時間 >](runtime-element.md)區段中的設定, 您應該很少。

## <a name="see-also"></a>另請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
