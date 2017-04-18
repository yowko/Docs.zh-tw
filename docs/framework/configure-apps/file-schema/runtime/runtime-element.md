---
title: "&lt;runtime&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#runtime"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<runtime> 項目"
  - "容器標記, <runtime> 項目"
  - "runtime 項目"
ms.assetid: 1eb2fae3-de4b-45b6-852f-517c39b751bd
caps.latest.revision: 70
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 62
---
# &lt;runtime&gt; 項目
包含有關組件繫結和記憶體回收的資訊。  
  
## 語法  
  
```  
<runtime>  
</runtime>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|元素|說明|  
|--------|--------|  
|[\<alwaysFlowImpersonationPolicy\>](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)|指定 Windows 識別一定會跨非同步點流動，不論如何執行模擬。|  
|[\<appDomainManagerAssembly\>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagerassembly-element.md)|指定在處理序中為預設應用程式定義域提供應用程式定義域管理員的組件。|  
|[\<appDomainManagerType\>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainmanagertype-element.md)|指定當做預設應用程式定義域之應用程式定義域管理員使用的型別。|  
|[\<appDomainResourceMonitoring\>](../../../../../docs/framework/configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)|指示執行階段收集處理序中，所有應用程式定義域在處理序存留期間的統計資料。|  
|[\<assemblyBinding\>](../../../../../docs/framework/configure-apps/file-schema/runtime/assemblybinding-element-for-runtime.md)|包含有關組件版本重新導向和組件位置的資訊。|  
|[\<bypassTrustedAppStrongNames\>](../../../../../docs/framework/configure-apps/file-schema/runtime/bypasstrustedappstrongnames-element.md)|指定是否應略過信任組件的強式名稱驗證。|  
|[\<CompatSortNLSVersion\>](../../../../../docs/framework/configure-apps/file-schema/runtime/compatsortnlsversion-element.md)|指定執行階段在執行字串比較時，應使用舊版排序行為。|  
|[\<developmentMode\>](../../../../../docs/framework/configure-apps/file-schema/runtime/developmentmode-element.md)|指定執行階段是否在 DEVPATH 環境變數所指定的目錄中搜尋組件。|  
|[\<disableCachingBindingFailures\>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecachingbindingfailures-element.md)|指定是否停用繫結失敗的快取，這是 .NET Framework 2.0 版內的預設行為。|  
|[\<disableCommitThreadStack\>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablecommitthreadstack-element.md)|指定執行緒啟動時，是否認可完整執行緒堆疊。|  
|[\<disableFusionUpdatesFromADManager\>](../../../../../docs/framework/configure-apps/file-schema/runtime/disablefusionupdatesfromadmanager-element.md)|指定是否停用預設行為 \(允許執行階段主機覆寫應用程式定義域的組態設定\)。|  
|[\<enforceFIPSPolicy\>](../../../../../docs/framework/configure-apps/file-schema/runtime/enforcefipspolicy-element.md)|指定是否強制電腦組態要求，也就是加密演算法必須遵守聯邦資訊處理標準 \(FIPS\)。|  
|[\<etwEnable\>](../../../../../docs/framework/configure-apps/file-schema/runtime/etwenable-element.md)|指定是否針對 Common Language Runtime 事件啟用 Windows \(ETW\) 的事件追蹤。|  
|[\<forcePerformanceCounterUniqueSharedMemoryReads\>](../../../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md)|指定 PerfCounter.dll 是否在 .NET Framework 1.1 版應用程式中使用 CategoryOptions 登錄設定，來決定要從分類特定的共用記憶體或全域記憶體載入效能計數器資料。|  
|[\<gcAllowVeryLargeObjects\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)|在 64 位元平台上，啟用大小超過 2 GB 的陣列。|  
|[\<gcConcurrent\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md)|指定 Common Language Runtime 是否並行執行記憶體回收。|  
|[\<GCCpuGroup\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gccpugroup-element.md)|指定記憶體回收是否支援多個 CPU 群組。|  
|[\<gcServer\>](../../../../../docs/framework/configure-apps/file-schema/runtime/gcserver-element.md)|指定 Common Language Runtime 是否要執行伺服器記憶體回收。|  
|[\<generatePublisherEvidence\>](../../../../../docs/framework/configure-apps/file-schema/runtime/generatepublisherevidence-element.md)|指定 Runtime 是否要使用程式碼存取安全性 \(CAS\) 發行者原則。|  
|[\<legacyCorruptedStateExceptionsPolicy\>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)|指定執行階段是否允許 Managed 程式碼攔截存取違規，以及其他毀損狀態例外狀況。|  
|[\<legacyImpersonationPolicy\>](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)|指定 Windows 識別不會跨非同步點流動，不論目前執行緒上的執行內容之流程設定為何。|  
|[\<loadfromRemoteSources\>](../../../../../docs/framework/configure-apps/file-schema/runtime/loadfromremotesources-element.md)|指定是否以完全信任的方式載入遠端來源的組件。|  
|[\<NetFx40\_LegacySecurityPolicy\>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)|指定執行階段是否會使用舊有的程式碼存取安全性 \(CAS\) 原則。|  
|[\<NetFx40\_PInvokeStackResilience\>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx40-pinvokestackresilience-element.md)|指定執行階段是否會在執行階段期間自動修正不正確的平台叫用，其代價是 Managed 與 Unmanaged 程式碼之間的較慢轉換。|  
|[\<NetFx45\_CultureAwareComparerGetHashCode\_LongStrings\>](../../../../../docs/framework/configure-apps/file-schema/runtime/netfx45-cultureawarecomparergethashcode-longstrings-element.md)|指定執行階段是否使用一定數目的記憶體來計算 <xref:System.StringComparer.GetHashCode%2A?displayProperty=fullName> 方法的雜湊程式碼。|  
|[\<PreferComInsteadOfRemoting\>](../../../../../docs/framework/configure-apps/file-schema/runtime/prefercominsteadofmanagedremoting-element.md)|指示執行階段會使用 COM Interop，而不會從遠端跨越應用程式定義域界限。|  
|[\<relativeBindForResources\>](../../../../../docs/framework/configure-apps/file-schema/runtime/relativebindforresources-element.md)|最佳化附屬組件的探查。|  
|[\<shadowCopyVerifyByTimeStamp\>](../../../../../docs/framework/configure-apps/file-schema/runtime/shadowcopyverifybytimestamp-element.md)|指定陰影複製是否使用在 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 中引入的預設啟動行為，或者會還原到舊版 .NET Framework 的啟動行為。|  
|[\<supportPortability\>](../../../../../docs/framework/configure-apps/file-schema/runtime/supportportability-element.md)|指定應用程式可以停用為了達到應用程式可攜性而將組件視為相等的預設行為，以參考兩個不同 .NET Framework 實作中的同一個組件。|  
|[\<system.runtime.caching\>](../../../../../docs/framework/configure-apps/file-schema/runtime/system-runtime-caching-element-cache-settings.md)|提供預設記憶體中物件快取的組態資訊。|  
|[\<Thread\_UseAllCpuGroups\>](../../../../../docs/framework/configure-apps/file-schema/runtime/thread-useallcpugroups-element.md)|指定執行階段是否在所有 CPU 群組分配 Managed 執行緒。|  
|[\<ThrowUnobservedTaskExceptions\>](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)|指定未處理的工作例外狀況是否應該結束執行中處理序。|  
|[\<TimeSpan\_LegacyFormatMode\>](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)|指定執行階段是否會使用 <xref:System.TimeSpan> 值的舊格式。|  
|[\<UseRandomizedStringHashAlgorithm\>](../../../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)|指定執行階段是否以每個應用程式定義域為基準，計算字串的雜湊碼。|  
|[\<UseSmallInternalThreadStacks\>](../../../../../docs/framework/configure-apps/file-schema/runtime/usesmallinternalthreadstacks-element.md)|會要求執行階段於建立某些在內部使用的執行緒時，使用明確的堆疊大小，而非預設的堆疊大小。|  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
  
## 備註  
 在 .NET Framework 2.0 版中，模擬的識別 \(Identity\) 會跨越應用程式定義域內的非同步 \(Asynchronous\) 點流動。  在 .NET Framework 2.0 版中，您可以在 machine.config 檔或應用程式組態檔內適當地設定執行階段項目，以啟用或停用跨越非同步點的模擬流動。  對ASP.NET來說，可在 aspnet.config 檔案內設定模擬流動，而這個檔案位於 \<Windows Folder\>\\Microsoft.NET\\Framework\\vx.x.xxxx 目錄中。  
  
 根據預設，ASP.NET 會使用下列組態設定，在 aspnet.config 檔案內停用模擬流動：  
  
```  
configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
      <alwaysFlowImpersonationPolicy enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 在 ASP.NET 內，如果您要改為允許模擬流動，則必須明確使用下列組態設定：  
  
```  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="false"/>  
      <alwaysFlowImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
 如需詳細資訊，請參閱[\<legacyImpersonationPolicy\> 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)與[\<alwaysFlowImpersonationPolicy\> 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)。  
  
## 範例  
 下列範例顯示如何將一個組件版本重新導向為另一個版本。  
  
```  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
             <bindingRedirect oldVersion="1.0.0.0"  
                              newVersion="2.0.0.0"/>  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [重新導向組件版本](../../../../../docs/framework/configure-apps/redirect-assembly-versions.md)   
 [How to: Disable Concurrent Garbage Collection](http://msdn.microsoft.com/zh-tw/ba2c6c67-5778-497c-9fac-5f793b5500c7)