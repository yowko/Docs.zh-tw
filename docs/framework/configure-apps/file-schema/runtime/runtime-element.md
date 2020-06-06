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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74430452"
---
# <a name="runtime-element"></a><span data-ttu-id="02d08-102">\<runtime> 項目</span><span class="sxs-lookup"><span data-stu-id="02d08-102">\<runtime> Element</span></span>

<span data-ttu-id="02d08-103">提供 common language runtime 用來設定應用程式的資訊。</span><span class="sxs-lookup"><span data-stu-id="02d08-103">Provides information used by the common language runtime to configure applications.</span></span>

[\<configuration>](../configuration-element.md)\
&nbsp;&nbsp;\<runtime>

## <a name="syntax"></a><span data-ttu-id="02d08-104">語法</span><span class="sxs-lookup"><span data-stu-id="02d08-104">Syntax</span></span>

```xml
<runtime>
</runtime>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="02d08-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="02d08-105">Attributes and Elements</span></span>

<span data-ttu-id="02d08-106">下列各節描述子項目和父元素。</span><span class="sxs-lookup"><span data-stu-id="02d08-106">The following sections describe child elements and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="02d08-107">屬性</span><span class="sxs-lookup"><span data-stu-id="02d08-107">Attributes</span></span>

<span data-ttu-id="02d08-108">無。</span><span class="sxs-lookup"><span data-stu-id="02d08-108">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="02d08-109">子元素</span><span class="sxs-lookup"><span data-stu-id="02d08-109">Child Elements</span></span>

|<span data-ttu-id="02d08-110">元素</span><span class="sxs-lookup"><span data-stu-id="02d08-110">Element</span></span>|<span data-ttu-id="02d08-111">描述</span><span class="sxs-lookup"><span data-stu-id="02d08-111">Description</span></span>|
|-------------|-----------------|
|[\<alwaysFlowImpersonationPolicy>](alwaysflowimpersonationpolicy-element.md)|<span data-ttu-id="02d08-112">指定 Windows 識別一律流經非同步點，而不論模擬的執行方式為何。</span><span class="sxs-lookup"><span data-stu-id="02d08-112">Specifies that the Windows identity always flows across asynchronous points, regardless of how impersonation was performed.</span></span>|
|[\<AppContextSwitchOverrides>](appcontextswitchoverrides-element.md)|<span data-ttu-id="02d08-113">定義一或多個由 <xref:System.AppContext> 類別所使用的參數，以提供新功能的退出機制。</span><span class="sxs-lookup"><span data-stu-id="02d08-113">Defines one or more switches used by the <xref:System.AppContext> class to provide an opt-out mechanism for new functionality.</span></span>|
|[\<appDomainManagerAssembly>](appdomainmanagerassembly-element.md)|<span data-ttu-id="02d08-114">針對處理序中的預設應用程式網域，指定提供應用程式網域管理員的組件。</span><span class="sxs-lookup"><span data-stu-id="02d08-114">Specifies the assembly that provides the application domain manager for the default application domain in the process.</span></span>|
|[\<appDomainManagerType>](appdomainmanagertype-element.md)|<span data-ttu-id="02d08-115">針對預設應用程式網域，指定做為應用程式網域管理員的類型。</span><span class="sxs-lookup"><span data-stu-id="02d08-115">Specifies the type that serves as the application domain manager for the default application domain.</span></span>|
|[\<appDomainResourceMonitoring>](appdomainresourcemonitoring-element.md)|<span data-ttu-id="02d08-116">針對處理序存留期間，指示執行階段收集處理序中所有應用程式網域的統計資料。</span><span class="sxs-lookup"><span data-stu-id="02d08-116">Instructs the runtime to collect statistics on all application domains in the process for the life of the process.</span></span>|
|[\<assemblyBinding>](assemblybinding-element-for-runtime.md)|<span data-ttu-id="02d08-117">包含有關組件版本重新導向和組件位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="02d08-117">Contains information about assembly version redirection and the locations of assemblies.</span></span>|
|[\<bypassTrustedAppStrongNames>](bypasstrustedappstrongnames-element.md)|<span data-ttu-id="02d08-118">指定是否應略過信任組件的強式名稱驗證。</span><span class="sxs-lookup"><span data-stu-id="02d08-118">Specifies whether strong name verification for trusted assemblies should be bypassed.</span></span>|
|[\<CompatSortNLSVersion>](compatsortnlsversion-element.md)|<span data-ttu-id="02d08-119">指定執行時間在執行字串比較時，應使用舊版排序行為。</span><span class="sxs-lookup"><span data-stu-id="02d08-119">Specifies that the runtime should use legacy sorting behavior when performing string comparisons.</span></span>|
|[\<developmentMode>](developmentmode-element.md)|<span data-ttu-id="02d08-120">指定執行階段是否要在 DEVPATH 環境變數所指定的目錄中搜尋組件。</span><span class="sxs-lookup"><span data-stu-id="02d08-120">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|
|[\<disableCachingBindingFailures>](disablecachingbindingfailures-element.md)|<span data-ttu-id="02d08-121">指定是否停用系結失敗的快取（這是 .NET Framework 版本2.0 中的預設行為）。</span><span class="sxs-lookup"><span data-stu-id="02d08-121">Specifies whether the caching of binding failures, which is the default behavior in the .NET Framework version 2.0, is disabled.</span></span>|
|[\<disableCommitThreadStack>](disablecommitthreadstack-element.md)|<span data-ttu-id="02d08-122">指定是否在執行緒啟動時認可完整執行緒堆疊。</span><span class="sxs-lookup"><span data-stu-id="02d08-122">Specifies whether the full thread stack is committed when a thread is started.</span></span>|
|[\<disableFusionUpdatesFromADManager>](disablefusionupdatesfromadmanager-element.md)|<span data-ttu-id="02d08-123">指定是否停用預設行為 (亦即允許執行階段主機覆寫應用程式網域的組態設定)。</span><span class="sxs-lookup"><span data-stu-id="02d08-123">Specifies whether the default behavior, which is to allow the runtime host to override configuration settings for an application domain, is disabled.</span></span>|
|[\<EnableAmPmParseAdjustment>](enableampmparseadjustment-element.md)|<span data-ttu-id="02d08-124">針對只包含日期、月份、小時和上午/下午指示項的日期字串，決定日期及時間剖析方法是否使用一組調整過的規則來剖析。</span><span class="sxs-lookup"><span data-stu-id="02d08-124">Determines whether date and time parsing methods use an adjusted set of rules to parse date strings that contain only a day, month, hour, and AM/PM designator.</span></span>|
|[\<enforceFIPSPolicy>](enforcefipspolicy-element.md)|<span data-ttu-id="02d08-125">指定是否強制執行電腦設定需求，以便讓密碼編譯演算法符合美國聯邦資訊處理標準 (FIPS) 的規範。</span><span class="sxs-lookup"><span data-stu-id="02d08-125">Specifies whether to enforce a computer configuration requirement that cryptographic algorithms must comply with the Federal Information Processing Standards (FIPS).</span></span>|
|[\<etwEnable>](etwenable-element.md)|<span data-ttu-id="02d08-126">指定是否為通用語言執行平台事件啟用 Windows 事件追蹤 (ETW)。</span><span class="sxs-lookup"><span data-stu-id="02d08-126">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>|
|[\<forcePerformanceCounterUniqueSharedMemoryReads>](forceperformancecounteruniquesharedmemoryreads-element.md)|<span data-ttu-id="02d08-127">指定 PerfCounter.dll 是否在 .NET Framework 1.1 版的應用程式中使用 CategoryOptions 登錄設定，以決定要從類別特定共用記憶體或從全域記憶體載入效能計數器資料。</span><span class="sxs-lookup"><span data-stu-id="02d08-127">Specifies whether PerfCounter.dll uses the CategoryOptions registry setting in a .NET Framework version 1.1 application to determine whether to load performance counter data from category-specific shared memory or global memory.</span></span>|
|[\<gcAllowVeryLargeObjects>](gcallowverylargeobjects-element.md)|<span data-ttu-id="02d08-128">在 64 位元平台上，啟用總大小大於 2 GB 的陣列。</span><span class="sxs-lookup"><span data-stu-id="02d08-128">On 64-bit platforms, enables arrays that are greater than 2 gigabytes (GB) in total size.</span></span>|
|[\<gcConcurrent>](gcconcurrent-element.md)|<span data-ttu-id="02d08-129">指定 common language runtime 是否同時執行垃圾收集。</span><span class="sxs-lookup"><span data-stu-id="02d08-129">Specifies whether the common language runtime runs garbage collection concurrently.</span></span>|
|[\<GCCpuGroup>](gccpugroup-element.md)|<span data-ttu-id="02d08-130">指定記憶體回收是否支援多個 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="02d08-130">Specifies whether garbage collection supports multiple CPU groups.</span></span>|
|[\<GCHeapAffinitizeMask>](gcheapaffinitizemask-element.md)|<span data-ttu-id="02d08-131">定義垃圾收集堆積與個別處理器之間的親和性。</span><span class="sxs-lookup"><span data-stu-id="02d08-131">Defines the affinity between garbage collection heaps and individual processors.</span></span>|
|[\<GCHeapCount>](gcheapcount-element.md)|<span data-ttu-id="02d08-132">指定要用於伺服器垃圾收集的堆積/執行緒數目。</span><span class="sxs-lookup"><span data-stu-id="02d08-132">Specifies the number of heaps/threads to use for server garbage collection.</span></span>|
|[\<GCLOHThreshold>](gclohthreshold-element.md)|<span data-ttu-id="02d08-133">指定導致垃圾收集行程將物件放在大型物件堆積上的臨界值大小。</span><span class="sxs-lookup"><span data-stu-id="02d08-133">Specifies the threshold size that causes the garbage collector to put objects on the large object heap.</span></span>|
|[\<GCNoAffinitize>](gcnoaffinitize-element.md)|<span data-ttu-id="02d08-134">指定是否要將相似化為具有 Cpu 的伺服器垃圾收集執行緒。</span><span class="sxs-lookup"><span data-stu-id="02d08-134">Specifies whether or not to affinitize server garbage collection threads with CPUs.</span></span>|
|[\<gcServer>](gcserver-element.md)|<span data-ttu-id="02d08-135">指定 Common Language Runtime 是否執行伺服器記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="02d08-135">Specifies whether the common language runtime runs server garbage collection.</span></span>|
|[\<generatePublisherEvidence>](generatepublisherevidence-element.md)|<span data-ttu-id="02d08-136">指定執行階段是否使用程式碼存取安全性 (CAS) 發行者原則。</span><span class="sxs-lookup"><span data-stu-id="02d08-136">Specifies whether the runtime uses code access security (CAS) publisher policy.</span></span>|
|[\<legacyCorruptedStateExceptionsPolicy>](legacycorruptedstateexceptionspolicy-element.md)|<span data-ttu-id="02d08-137">指定執行階段是否允許 Managed 程式碼攔截存取違規和其他損毀狀態例外狀況。</span><span class="sxs-lookup"><span data-stu-id="02d08-137">Specifies whether the runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>|
|[\<legacyImpersonationPolicy>](legacyimpersonationpolicy-element.md)|<span data-ttu-id="02d08-138">指定 Windows 識別不會流經非同步點，而不論目前執行緒上執行內容的流程設定為何。</span><span class="sxs-lookup"><span data-stu-id="02d08-138">Specifies that the Windows identity does not flow across asynchronous points, regardless of the flow settings for the execution context on the current thread.</span></span>|
|[\<loadfromRemoteSources>](loadfromremotesources-element.md)|<span data-ttu-id="02d08-139">指定是否以完全信任的方式載入來自遠端來源的組件。</span><span class="sxs-lookup"><span data-stu-id="02d08-139">Specifies whether assemblies from remote sources are loaded as full trust.</span></span>|
|[\<NetFx40_LegacySecurityPolicy>](netfx40-legacysecuritypolicy-element.md)|<span data-ttu-id="02d08-140">指定執行階段是否使用舊版程式碼存取安全性 (CAS) 原則。</span><span class="sxs-lookup"><span data-stu-id="02d08-140">Specifies whether the runtime uses legacy code access security (CAS) policy.</span></span>|
|[\<NetFx40_PInvokeStackResilience>](netfx40-pinvokestackresilience-element.md)|<span data-ttu-id="02d08-141">指定執行階段是否會在執行階段自動修復不正確的平台叫用宣告，即使這麼做會使 Managed 和 Unmanaged 程式碼之間的轉換變慢。</span><span class="sxs-lookup"><span data-stu-id="02d08-141">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>|
|[\<NetFx45_CultureAwareComparerGetHashCode_LongStrings>](netfx45-cultureawarecomparergethashcode-longstrings-element.md)|<span data-ttu-id="02d08-142">指定執行階段是否使用固定的記憶體數量計算 <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> 方法的雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="02d08-142">Specifies whether the runtime uses a fixed amount of memory to calculate hash codes for the <xref:System.StringComparer.GetHashCode%2A?displayProperty=nameWithType> method.</span></span>|
|[\<PreferComInsteadOfRemoting>](prefercominsteadofmanagedremoting-element.md)|<span data-ttu-id="02d08-143">指定執行階段會使用 COM Interop，而不是跨越應用程式網域界限的遠端處理。</span><span class="sxs-lookup"><span data-stu-id="02d08-143">Specifies that the runtime will use COM interop instead of remoting across application domain boundaries.</span></span>|
|[\<relativeBindForResources>](relativebindforresources-element.md)|<span data-ttu-id="02d08-144">最佳化附屬組件的探查。</span><span class="sxs-lookup"><span data-stu-id="02d08-144">Optimizes the probe for satellite assemblies.</span></span>|
|[\<shadowCopyVerifyByTimeStamp>](shadowcopyverifybytimestamp-element.md)|<span data-ttu-id="02d08-145">指定陰影複製是否使用 .NET Framework 4 中引進的預設啟動行為，或還原為舊版 .NET Framework 的啟動行為。</span><span class="sxs-lookup"><span data-stu-id="02d08-145">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>|
|[\<supportPortability>](supportportability-element.md)|<span data-ttu-id="02d08-146">指定應用程式可以在兩個不同的 .NET Framework 實作中參考相同的組件，方法是停用將組件視為同等的預設行為 (此預設行為是基於應用程式可攜性的考量)。</span><span class="sxs-lookup"><span data-stu-id="02d08-146">Specifies that an application can reference the same assembly in two different implementations of the .NET Framework, by disabling the default behavior that treats the assemblies as equivalent for application portability purposes.</span></span>|
|[\<system.runtime.caching>](system-runtime-caching-element-cache-settings.md)|<span data-ttu-id="02d08-147">提供預設記憶體內部物件快取的組態資訊。</span><span class="sxs-lookup"><span data-stu-id="02d08-147">Provides configuration information for the default in-memory object cache.</span></span>|
|[\<Thread_UseAllCpuGroups>](thread-useallcpugroups-element.md)|<span data-ttu-id="02d08-148">指定執行階段是否會將 Managed 執行緒分散到所有 CPU 群組。</span><span class="sxs-lookup"><span data-stu-id="02d08-148">Specifies whether the runtime distributes managed threads across all CPU groups.</span></span>|
|[\<ThrowUnobservedTaskExceptions>](throwunobservedtaskexceptions-element.md)|<span data-ttu-id="02d08-149">指定未處理的工作例外狀況是否應終止執行中的處理序。</span><span class="sxs-lookup"><span data-stu-id="02d08-149">Specifies whether unhandled task exceptions should terminate a running process.</span></span>|
|[\<TimeSpan_LegacyFormatMode>](timespan-legacyformatmode-element.md)|<span data-ttu-id="02d08-150">指定執行階段是否針對 <xref:System.TimeSpan> 值使用舊版格式。</span><span class="sxs-lookup"><span data-stu-id="02d08-150">Specifies whether the runtime uses legacy formatting for <xref:System.TimeSpan> values.</span></span>|
|[\<useLegacyJit>](uselegacyjit-element.md)|<span data-ttu-id="02d08-151">決定通用語言執行平台是否針對 Just-In-Time 編譯使用舊版 64 位元 JIT 編譯器。</span><span class="sxs-lookup"><span data-stu-id="02d08-151">Determines whether the common language runtime uses the legacy 64-bit JIT compiler for just-in-time compilation.</span></span>|
|[\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md)|<span data-ttu-id="02d08-152">指定執行階段是否依照應用程式網域來計算字串的雜湊碼。</span><span class="sxs-lookup"><span data-stu-id="02d08-152">Specifies whether the runtime calculates hash codes for strings on a per application domain basis.</span></span>|
|[\<UseSmallInternalThreadStacks>](usesmallinternalthreadstacks-element.md)|<span data-ttu-id="02d08-153">要求執行階段在建立內部使用的特定執行緒時，使用明確的堆疊大小，而不是預設的堆疊大小。</span><span class="sxs-lookup"><span data-stu-id="02d08-153">Requests that the runtime use explicit stack sizes when it creates certain threads that it uses internally, instead of the default stack size.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="02d08-154">父項目</span><span class="sxs-lookup"><span data-stu-id="02d08-154">Parent Elements</span></span>

|<span data-ttu-id="02d08-155">元素</span><span class="sxs-lookup"><span data-stu-id="02d08-155">Element</span></span>|<span data-ttu-id="02d08-156">描述</span><span class="sxs-lookup"><span data-stu-id="02d08-156">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="02d08-157">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="02d08-157">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="02d08-158">備註</span><span class="sxs-lookup"><span data-stu-id="02d08-158">Remarks</span></span>

<span data-ttu-id="02d08-159">[\<runtime>](runtime-element.md)通用語言執行平臺會使用設定檔區段中的子項目，來設定應用程式的執行方式。</span><span class="sxs-lookup"><span data-stu-id="02d08-159">The child elements in the [\<runtime>](runtime-element.md) section of a configuration file are used by the common language runtime to configure how an application executes.</span></span> <span data-ttu-id="02d08-160">例如，專案會 [\<gcServer>](gcserver-element.md) 判斷垃圾收集行程是否使用工作站垃圾收集或伺服器垃圾收集，元素會 [\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md) 決定通用語言執行平臺是否會針對每個應用程式或每個應用程式網域來計算字串的雜湊碼，而 `AppContextSwitchOverrides` 元素可讓程式庫使用者加入宣告或退出程式庫所提供的變更功能。</span><span class="sxs-lookup"><span data-stu-id="02d08-160">For example, the [\<gcServer>](gcserver-element.md) element determines whether the garbage collector uses workstation garbage collection or server garbage collection, the [\<UseRandomizedStringHashAlgorithm>](userandomizedstringhashalgorithm-element.md) element determines whether the common language runtime calculates hash codes for string on a per-application or a per-application domain basis, and the `AppContextSwitchOverrides` element allows library users to opt in or opt out of changed  functionality provided by a library.</span></span>

<span data-ttu-id="02d08-161">在 [\<runtime>](runtime-element.md) 應用程式啟動時，common language runtime 會自動讀取區段中的元素。</span><span class="sxs-lookup"><span data-stu-id="02d08-161">The elements in the [\<runtime>](runtime-element.md) section are read automatically by the common language runtime at application startup.</span></span> <span data-ttu-id="02d08-162">您也可以定義非預設應用程式域的設定檔，方法是將其名稱提供給 <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> 屬性; 載入應用程式域時，會自動讀取其設定。</span><span class="sxs-lookup"><span data-stu-id="02d08-162">You can also define the configuration file for a non-default application domain by supplying its name to the <xref:System.AppDomainSetup.ConfigurationFile%2A?displayProperty=nameWithType> property; its settings are read automatically when the application domain is loaded.</span></span> <span data-ttu-id="02d08-163">如果您需要直接讀取 [\<runtime>](runtime-element.md) 應用程式佈建檔中區段內的設定，您應該很少這麼做。</span><span class="sxs-lookup"><span data-stu-id="02d08-163">You should rarely, if ever, have a need to directly read the settings in the [\<runtime>](runtime-element.md) section in your application's configuration file.</span></span>

## <a name="see-also"></a><span data-ttu-id="02d08-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02d08-164">See also</span></span>

- [<span data-ttu-id="02d08-165">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="02d08-165">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="02d08-166">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="02d08-166">Configuration File Schema</span></span>](../index.md)
