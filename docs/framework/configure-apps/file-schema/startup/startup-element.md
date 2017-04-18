---
title: "&lt;startup&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#startup"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<startup> 項目"
  - "容器標記, <startup> 項目"
  - "startup 項目"
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
caps.latest.revision: 19
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 19
---
# &lt;startup&gt; 項目
指定 Common Language Runtime 啟動資訊。  
  
## 語法  
  
```  
<startup useLegacyV2RuntimeActivationPolicy="true|false" >   
</startup>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`useLegacyV2RuntimeActivationPolicy`|選擇性屬性。<br /><br /> 指定應啟用 [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] 執行階段啟動原則，或是使用 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 啟動原則。|  
  
## useLegacyV2RuntimeActivationPolicy 屬性  
  
|值|說明|  
|-------|--------|  
|`true`|啟用所選執行階段的 [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] 執行階段啟動原則，目的是要將舊版執行階段啟動技術 \(例如 [CorBindToRuntimeEx 函式](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)\) 繫結至選擇自組態檔案的執行階段，而不是將其蓋在 CLR 2.0 版本之上。  因此，如果從組態檔案中選擇 CLR 版本 4 \(含\) 以後版本，就會使用與所選 CLR 版本一起載入的舊版 .NET Framework 來建立混合模式組件。  設定此值可避免 CLR 1.1 版或 CLR 2.0 版載入至相同的處理序，並有效停用同處理序並存功能。|  
|`false`|使用 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] \(含\) 以後版本的預設啟動原則，目的是要讓舊版執行階段啟動技術將 CLR 版本 1.1 或 2.0 載入至處理序中。  設定此值可防止混合模式組件載入至 .NET Framework 4 \(含\) 以後版本，除非這些組件是以 .NET Framework 4 \(含\) 以後版本所建置。  這個值為預設值。|  
  
### 子項目  
  
|元素|說明|  
|--------|--------|  
|[\<requiredRuntime\>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md)|指定應用程式只支援 Common Language Runtime 1.0 版。  以執行階段版本 1.1 \(含\) 以後版本所建置的應用程式，應該要使用 **\<supportedRuntime\>** 項目。|  
|[\<supportedRuntime\>](../../../../../docs/framework/configure-apps/file-schema/startup/supportedruntime-element.md)|指定應用程式所支援的 Common Language Runtime 版本。|  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
  
## 備註  
 所有使用執行階段 1.1 \(含\) 以後版本所建置的應用程式，都應使用 **\<supportedRuntime\>** 項目。  建置只支援 1.0 版的應用程式時，必須使用 **\<requiredRuntime\>** 項目。  
  
 裝載在 Microsoft Internet Explorer 中的應用程式啟始程式碼會忽略 **\<startup\>** 項目和其子項目。  
  
## useLegacyV2RuntimeActivationPolicy 屬性  
 如果應用程式使用舊版啟動路徑 \(例如 [CorBindToRuntimeEx 函式](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)\)，而您希望這些路徑啟動 CLR 的版本 4 而不是較早的版本，或者應用程式是使用 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 所建置，但相依於使用舊版 .NET Framework 建置的混合模式組件，這個屬性就很有用。  在這些情節中，請將屬性設定為 `true`。  
  
> [!NOTE]
>  將屬性設定為 `true` 可避免 CLR 1.1 版或 CLR 2.0 版載入至相同的處理序，並有效停用同處理序並存功能 \(請參閱[Side\-by\-Side Execution for COM Interop](http://msdn.microsoft.com/zh-tw/4302318c-3586-49bf-8620-b9a39cdf4a32)\)。  
  
## 範例  
 下列範例顯示如何在組態檔中指定 Runtime 版本。  
  
```  
<!-- When used with version 1.0 of the .NET Framework runtime -->  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
<!-- When used with version 1.1 (or later) of the runtime -->  
<configuration>  
   <startup>  
      <supportedRuntime version="v1.1.4322"/>  
      <supportedRuntime version="v1.0.3705"/>  
   </startup>  
</configuration>  
```  
  
## 請參閱  
 [啟動設定結構描述](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<PaveOver\> Specifying Which Runtime Version to Use](http://msdn.microsoft.com/zh-tw/c376208d-980d-42b4-865b-fbe0d9cc97c2)   
 [Side\-by\-Side Execution for COM Interop](http://msdn.microsoft.com/zh-tw/4302318c-3586-49bf-8620-b9a39cdf4a32)   
 [同處理序並存執行](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)