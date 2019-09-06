---
title: 執行階段設定結構描述
ms.date: 03/30/2017
helpviewer_keywords:
- schema runtime settings
- configuration schema [.NET Framework], runtime settings
- runtime settings schema
ms.assetid: f04816ab-110d-4e28-9283-845d6d9a4a68
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5b340ef99b489b66c62971cacedccdfe609d0b1a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252526"
---
# <a name="runtime-settings-schema"></a>執行階段設定結構描述

執行階段設定會由通用語言執行平台使用，以設定目標是 .NET Framework 的應用程式。

## <a name="the-runtime-section-and-its-parent-and-child-elements"></a>\<執行時間 > 區段及其父系和子項目

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;[\<執行時間 >](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainManagerType>](appdomainmanagertype-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<assemblyBinding>](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<dependentAssembly>](dependentassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<assemblyIdentity >](assemblyidentity-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<bindingRedirect>](bindingredirect-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<codeBase>](codebase-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<publisherPolicy >](publisherpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<探查 >](probing-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<qualifyAssembly>](qualifyassembly-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<Supportportability> >](supportportability-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<developmentMode>](developmentmode-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<etwEnable>](etwenable-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcAllowVeryLargeObjects>](gcconcurrent-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcConcurrent>](gcconcurrent-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<GCCpuGroup>](gccpugroup-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<gcServer>](gcserver-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<generatePublisherEvidence>](generatepublisherevidence-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<legacyImpersonationPolicy>](legacyimpersonationpolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<loadfromRemoteSources>](loadfromremotesources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx40_PInvokeStackResilience>](netfx40-pinvokestackresilience-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<PreferComInsteadOfManagedRemoting>](prefercominsteadofmanagedremoting-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<relativeBindForResources>](relativebindforresources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<shadowCopyVerifyByTimeStamp>](shadowcopyverifybytimestamp-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<TimeSpan_LegacyFormatMode>](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<useLegacyJit>](uselegacyjit-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)\
&nbsp;&nbsp;[\<> 的緩存](system-runtime-caching-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[\<memoryCache >](memorycache-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<namedCaches >](namedcaches-element-cache-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<新增 >](add-element-for-namedcaches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<清除 >](clear-element-for-namedcaches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[\<移除 >](remove-element-for-namedcaches.md)  

## <a name="alphabetical-list-of-runtime-elements"></a>依字母順序\<排列的執行時間 > 元素清單

|項目|說明|
|-------------|-----------------|
|[\<add>](add-element-for-namedcaches.md)|將具名快取新增到記憶體快取的 `namedCaches` 集合。|
|[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)|指定 Windows 識別一律流經非同步點，而不論模擬的執行方式為何。|
|[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)|定義一或多個由 <xref:System.AppContext> 類別所使用的參數，以提供新功能的退出機制。|
|[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)|針對處理序中的預設應用程式網域，指定提供應用程式網域管理員的組件。|
|[\<appDomainManagerType>](appdomainmanagertype-element.md)|針對預設應用程式網域，指定做為應用程式網域管理員的類型。|
|[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)|針對處理序存留期間，指示執行階段收集處理序中所有應用程式網域的統計資料。|
|[\<assemblyBinding>](assemblybinding-element-for-runtime.md)|包含有關組件版本重新導向和組件位置的資訊。|
|[\<assemblyIdentity>](assemblyidentity-element-for-runtime.md)|包含組件的識別資訊。|
|[\<bindingRedirect>](bindingredirect-element.md)|將一個組件版本重新導向至另一個版本。|
|[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)|指定是否應略過信任組件的強式名稱驗證。|
|[\<clear>](clear-element-for-namedcaches.md)|清除記憶體快取的 `namedCaches` 集合。|
|[\<codeBase>](codebase-element.md)|指定執行階段尋找組件的位置。|
|[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)|指定執行階段在執行字串比較時，應使用舊版排序行為|
|[\<dependentAssembly>](dependentassembly-element.md)|封裝每一個組件的繫結原則和組件位置。|
|[\<developmentMode>](developmentmode-element.md)|指定執行階段是否要在 DEVPATH 環境變數所指定的目錄中搜尋組件。|
|[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)|指定是否停用系結失敗的快取（這是 .NET Framework 2.0 中的預設行為）。|
|[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)|指定啟動執行緒時是否認可整個執行緒堆疊。|
|[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)|指定是否停用預設行為 (亦即允許執行階段主機覆寫應用程式網域的組態設定)。|
|[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)|針對只包含日期、月份、小時和上午/下午指示項的日期字串，決定日期及時間剖析方法是否使用一組調整過的規則來剖析。|
|[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)|指定是否強制執行電腦設定需求，以便讓密碼編譯演算法符合美國聯邦資訊處理標準 (FIPS) 的規範。|
|[\<etwEnable>](etwenable-element.md)|指定是否為通用語言執行平台事件啟用 Windows 事件追蹤 (ETW)。|
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)|指定 PerfCounter.dll 是否在 .NET Framework 1.1 版的應用程式中使用 CategoryOptions 登錄設定，以決定要從類別特定共用記憶體或從全域記憶體載入效能計數器資料。|
|[\<gcAllowVeryLargeObjects>](gcallowverylargeobjects-element.md)|在 64 位元平台上，啟用總大小大於 2 GB 的陣列。|
|[\<gcConcurrent>](gcconcurrent-element.md)|指定執行階段是否同時執行記憶體回收。|
|[\<GCCpuGroup>](gccpugroup-element.md)|指定記憶體回收是否支援多個 CPU 群組。|
|[\<gcServer>](gcserver-element.md)|指定 Common Language Runtime 是否執行伺服器記憶體回收。|
|[\<generatePublisherEvidence>](generatepublisherevidence-element.md)|指定執行階段是否使用程式碼存取安全性 (CAS) 發行者原則。|
|[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)|指定執行階段是否允許 Managed 程式碼攔截存取違規和其他損毀狀態例外狀況。|
|[\<legacyImpersonationPolicy>](legacyimpersonationpolicy-element.md)|指定 Windows 識別不會流經非同步點，而不論目前執行緒上執行內容的流程設定為何。|
|[\<loadfromRemoteSources>](loadfromremotesources-element.md)|指定是否以完全信任的方式載入來自遠端來源的組件。|
|[\<memoryCache>](memorycache-element-cache-settings.md)|定義用來設定根據 <xref:System.Runtime.Caching.MemoryCache> 類別之快取的項目。|
|[\<namedCaches>](namedcaches-element-cache-settings.md)|包含 `namedCache` 執行個體的組態設定集合。|
|[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)|指定執行階段是否使用舊版程式碼存取安全性 (CAS) 原則。|
|[\<NetFx40_PInvokeStackResilience>](netfx40-pinvokestackresilience-element.md)|指定執行階段是否會在執行階段自動修復不正確的平台叫用宣告，即使這麼做會使 Managed 和 Unmanaged 程式碼之間的轉換變慢。|
|[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)|指定執行階段是否使用固定的記憶體數量計算 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法的雜湊碼。|
|[\<PreferComInsteadOfManagedRemoting>](prefercominsteadofmanagedremoting-element.md)|指定執行階段會使用 COM Interop，而不是跨越應用程式網域界限的遠端處理。|
|[\<probing>](probing-element.md)|指定執行階段在載入組件時要搜尋的子目錄。|
|[\<publisherPolicy>](publisherpolicy-element.md)|指定執行階段是否套用發行者原則。|
|[\<qualifyAssembly>](qualifyassembly-element.md)|指定應該在使用部分名稱時以動態方式載入的組件的完整名稱。|
|[\<relativeBindForResources>](relativebindforresources-element.md)|最佳化附屬組件的探查。|
|[\<remove>](remove-element-for-namedcaches.md)|從記憶體快取的 `namedCaches` 集合移除具名快取項目。|
|[\<runtime>](runtime-element.md)|包含有關組件繫結和記憶體回收行為的資訊。|
|[\<shadowCopyTimeStampVerification>](shadowcopyverifybytimestamp-element.md)|指定陰影複製是否使用 .NET Framework 4 中引進的預設啟動行為，或還原為舊版 .NET Framework 的啟動行為。|
|[\<supportPortability>](supportportability-element.md)|指定應用程式可以在兩個不同的 .NET Framework 實作中參考相同的組件，方法是停用將組件視為同等的預設行為 (此預設行為是基於應用程式可攜性的考量)。|
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|提供預設記憶體內部物件快取的組態資訊。|
|[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)|指定執行階段是否會將 Managed 執行緒分散到所有 CPU 群組。|
|[\<ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md)|指定未處理的工作例外狀況是否應終止執行中的處理序。|
|[\<TimeSpan_LegacyFormatMode>](runtime-element.md)|指定執行階段是否針對 <xref:System.TimeSpan> 值使用舊版格式。|
|[\<useLegacyJit>](uselegacyjit-element.md)|決定通用語言執行平台是否針對 Just-In-Time 編譯使用舊版 64 位元 JIT 編譯器。|
|[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)|指定執行階段是否依照應用程式網域來計算字串的雜湊碼。|
|[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)|要求執行階段在建立內部使用的特定執行緒時，使用明確的堆疊大小，而不是預設的堆疊大小。|

## <a name="see-also"></a>另請參閱

- [組態檔結構描述](../index.md)
- [停用並行垃圾收集](gcconcurrent-element.md#to-disable-background-garbage-collection)
- [重新導向組件版本](../../redirect-assembly-versions.md)
