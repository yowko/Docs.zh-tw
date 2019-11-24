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
ms.openlocfilehash: 3825ae7c3e35193cb835981600fe1ef83097cd2d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430452"
---
# <a name="runtime-element"></a>\<runtime> Element

Provides information used by the common language runtime to configure applications.

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;\<runtime>

## <a name="syntax"></a>語法

```xml
<runtime>
</runtime>
```

## <a name="attributes-and-elements"></a>屬性和項目

The following sections describe child elements and parent elements.

### <a name="attributes"></a>屬性

無。

### <a name="child-elements"></a>子項目

|項目|描述|
|-------------|-----------------|
|[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)|指定 Windows 識別一律流經非同步點，而不論模擬的執行方式為何。|
|[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)|定義一或多個由 <xref:System.AppContext> 類別所使用的參數，以提供新功能的退出機制。|
|[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)|針對處理序中的預設應用程式網域，指定提供應用程式網域管理員的組件。|
|[\<appDomainManagerType>](appdomainmanagertype-element.md)|針對預設應用程式網域，指定做為應用程式網域管理員的類型。|
|[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)|針對處理序存留期間，指示執行階段收集處理序中所有應用程式網域的統計資料。|
|[\<assemblyBinding>](assemblybinding-element-for-runtime.md)|包含有關組件版本重新導向和組件位置的資訊。|
|[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)|指定是否應略過信任組件的強式名稱驗證。|
|[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)|Specifies that the runtime should use legacy sorting behavior when performing string comparisons.|
|[\<developmentMode>](developmentmode-element.md)|指定執行階段是否要在 DEVPATH 環境變數所指定的目錄中搜尋組件。|
|[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)|Specifies whether the caching of binding failures, which is the default behavior in the .NET Framework version 2.0, is disabled.|
|[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)|指定是否在執行緒啟動時認可完整執行緒堆疊。|
|[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)|指定是否停用預設行為 (亦即允許執行階段主機覆寫應用程式網域的組態設定)。|
|[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)|針對只包含日期、月份、小時和上午/下午指示項的日期字串，決定日期及時間剖析方法是否使用一組調整過的規則來剖析。|
|[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)|指定是否強制執行電腦設定需求，以便讓密碼編譯演算法符合美國聯邦資訊處理標準 (FIPS) 的規範。|
|[\<etwEnable>](etwenable-element.md)|指定是否為通用語言執行平台事件啟用 Windows 事件追蹤 (ETW)。|
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)|指定 PerfCounter.dll 是否在 .NET Framework 1.1 版的應用程式中使用 CategoryOptions 登錄設定，以決定要從類別特定共用記憶體或從全域記憶體載入效能計數器資料。|
|[\<gcAllowVeryLargeObjects>](gcallowverylargeobjects-element.md)|在 64 位元平台上，啟用總大小大於 2 GB 的陣列。|
|[\<gcConcurrent>](gcconcurrent-element.md)|Specifies whether the common language runtime runs garbage collection concurrently.|
|[\<GCCpuGroup>](gccpugroup-element.md)|指定記憶體回收是否支援多個 CPU 群組。|
|[\<GCHeapAffinitizeMask>](gcheapaffinitizemask-element.md)|Defines the affinity between garbage collection heaps and individual processors.|
|[\<GCHeapCount>](gcheapcount-element.md)|Specifies the number of heaps/threads to use for server garbage collection.|
|[\<GCLOHThreshold>](gclohthreshold-element.md)|Specifies the threshold size that causes the garbage collector to put objects on the large object heap.|
|[\<GCNoAffinitize>](gcnoaffinitize-element.md)|Specifies whether or not to affinitize server garbage collection threads with CPUs.|
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
|[\<shadowCopyVerifyByTimeStamp>](shadowcopyverifybytimestamp-element.md)|Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.|
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

The child elements in the [\<runtime>](runtime-element.md) section of a configuration file are used by the common language runtime to configure how an application executes. For example, the [\<gcServer>](gcserver-element.md) element determines whether the garbage collector uses workstation garbage collection or server garbage collection, the [\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md) element determines whether the common language runtime calculates hash codes for string on a per-application or a per-application domain basis, and the `AppContextSwitchOverrides` element allows library users to opt in or opt out of changed  functionality provided by a library.

The elements in the [\<runtime>](runtime-element.md) section are read automatically by the common language runtime at application startup. You can also define the configuration file for a non-default application domain by supplying its name to the <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> property; its settings are read automatically when the application domain is loaded. You should rarely, if ever, have a need to directly read the settings in the [\<runtime>](runtime-element.md) section in your application's configuration file.

## <a name="see-also"></a>請參閱

- [執行階段設定結構描述](index.md)
- [組態檔結構描述](../index.md)
