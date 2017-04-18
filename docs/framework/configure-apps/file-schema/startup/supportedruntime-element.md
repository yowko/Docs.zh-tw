---
title: "&lt;supportedRuntime&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#supportedRuntime"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/supportedRuntime"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<supportedRuntime> 項目"
  - "supportedRuntime 項目"
ms.assetid: 1ae16e23-afbe-4de4-b413-bc457f37b69f
caps.latest.revision: 33
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 28
---
# &lt;supportedRuntime&gt; 項目
指定應用程式支援的通用語言執行平台版本。 所有以 .NET Framework 1.1 \(含\) 以後版本建置的應用程式都應使用這個項目。  
  
 [\<configuration\>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<startup\>](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)  
  
 **\<supportedRuntime\>**  
  
## 語法  
  
```  
  
<supportedRuntime version="runtime version" sku="sku id"/>  
```  
  
## 屬性  
  
|屬性|描述|  
|--------|--------|  
|**版本**|選擇性屬性。<br /><br /> 字串值，用於指定這個應用程式支援的通用語言執行平台 \(CLR\) 版本。 如需 `version` 屬性的有效值，請參閱 [「執行階段版本」值](#version) 一節。 **Note:**  透過 .NET Framework 3.5，「*執行階段版本*」值會採用 *major*.*minor*.*build* 的形式。 從 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 開始，只需要主要和次要版本號碼 \(也就是 "v4.0"，不需要 "v4.0.30319"\)。 建議使用較短的字串。|  
|**sku**|選擇性屬性。<br /><br /> 字串值，指定庫存單位 \(SKU\)，進而指定哪些應用程式支援的.NET Framework 版本。<br /><br /> 從 .NET Framework 4.0 開始，建議使用 `sku` 屬性。  該屬性存在時，會指出應用程式作為目標的 .NET Framework 版本。<br /><br /> 如需 SKU 屬性的有效值，請參閱 [「SKU 識別碼」值](#sku) 一節。|  
  
## 備註  
 如果應用程式組態檔中沒有 **\<supportedRuntime\>** 項目，則會使用建置應用程式時使用的執行階段版本。  
  
 所有使用執行階段 1.1 \(含\) 以後版本所建置的應用程式，都應使用 **\<supportedRuntime\>** 項目。 若建置的應用程式只支援執行階段的 1.0 版，則必須使用 [\<requiredRuntime\>](../../../../../docs/framework/configure-apps/file-schema/startup/requiredruntime-element.md) 項目。  
  
> [!NOTE]
>  如果您使用 [CorBindToRuntimeByCfg](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) 函式指定組態檔，則必須針對該執行階段的所有版本使用 `<requiredRuntime>` 項目。 當您使用 [CorBindToRuntimeByCfg](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) 時，會忽略 `<supportedRuntime>` 項目。  
  
 針對所支援執行階段為 .NET Framework 1.1 到 3.5 版本的應用程式，當支援多個執行階段版本時，第一個項目應該指定最常用的執行階段版本，而最後一個項目則指定最少用的版本。 針對支援 .NET Framework 4.0 或更新版本的應用程式，`version` 屬性會指出 CLR 版本，其對 .NET Framework 4 與更新版本而言為常用項目，而 `sku` 屬性會指出應用程式用以作為目標的單一 .NET Framework 版本。  
  
> [!NOTE]
>  如果您的應用程式使用像是 [CorBindToRuntimeEx 函式](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)這類舊版啟用路徑，而您希望這些路徑啟用 CLR 4 版而不是更舊的版本，或者您的應用程式是使用 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 所建置，但是相依於使用舊版 .NET Framework 建置的混合模式組件，那麼在支援的執行階段清單中指定 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 並不足夠。 此外，在組態檔的 [\<startup\> 項目](../../../../../docs/framework/configure-apps/file-schema/startup/startup-element.md)中，您必須將 `useLegacyV2RuntimeActivationPolicy` 屬性設定為 `true`。 但是，將這個屬性設定為 `true`，即表示以舊版 .NET Framework 建置的所有元件都會使用 [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 執行，而不是原本建置時所使用的執行階段。  
  
 建議您使用應用程式能夠執行的所有 .NET Framework 版本進行應用程式測試。  
  
<a name="version"></a>   
## 「執行階段版本」值  
 下表列出 `version` 屬性*執行階段版本*值的有效值。  
  
|.NET Framework 版本|`version` 屬性|  
|-----------------------|------------------|  
|1.0|"v1.0.3705"|  
|1.1|"v1.1.4322"|  
|2.0|"v2.0.50727"|  
|3.0|"v2.0.50727"|  
|3.5|"v2.0.50727"|  
|4.0|"v4.0"|  
|4.5|"v4.0"|  
|4.5.1|"v4.0"|  
|4.5.2|"v4.0"|  
|4.6|"v4.0"|  
|4.6.1|"v4.0"|  
  
<a name="sku"></a>   
## 「SKU 識別碼」值  
 下表列出 `sku` 屬性所支援以 .NET Framework 4 起始的 .NET framework 版本。  請注意，以 .NET Framework 4 起始的 `sku` 屬性會指出應用程式用以作為目標的 .NET Framework 版本。  
  
|.NET Framework 版本|`sku` 屬性|  
|-----------------------|--------------|  
|4.0|".NETFramework,Version\=v4.0"|  
|4.0，Client Profile|".NETFramework,Version\=v4.0,Profile\=Client"|  
|4.0，平台更新 1|.NETFramework,Version\=v4.0.1|  
|4.0，Client Profile，更新 1|.NETFramework,Version\=v4.0.1,Profile\=Client|  
|4.0，平台更新 2|.NETFramework,Version\=v4.0.2|  
|4.0，Client Profile，更新 2|.NETFramework,Version\=v4.0.2,Profile\=Client|  
|4.0，平台更新 3|.NETFramework,Version\=v4.0.3|  
|4.0，Client Profile，更新 3|.NETFramework,Version\=v4.0.3,Profile\=Client|  
|4.5|".NETFramework,Version\=v4.5"|  
|4.5.1|".NETFramework,Version\=v4.5.1"|  
|4.5.2|".NETFramework,Version\=v4.5.2"|  
|4.6|".NETFramework,Version\=v4.6"|  
|4.6.1|".NETFramework,Version\=v4.6.1"|  
  
 下表顯示當 `version` 屬性為 v4.0 且 `sku` 屬性會識別 .NET Framework 4 或其中一個更新 \(PU\) 時，應用程式將針對不同的 `sku` 屬性值在哪一個已安裝的 .NET Framework 4 版本上執行。  
  
|`sku` 屬性的值|4.0 用戶端版本|4.0 完整版本|4.0 用戶端 \+ PU 1|4.0 完整版 \+ PU 1|4.0 用戶端 \+ PU 2|4.0 完整版 \+ PU 2|4.0 用戶端 \+ PU 3|4.0 完整版 \+ PU 3|4.5 及更新版本|  
|----------------|---------------|--------------|---------------------|---------------------|---------------------|---------------------|---------------------|---------------------|---------------|  
|.NETFramework,Version\=v4.0,Profile\=Client|是|是|是|是|是|是|是|是|是|  
|.NETFramework,Version\=v4.0||是||是||是||是|是|  
|.NETFramework,Version\=v4.0.1,Profile\=Client|||是|是|是|是|是|是|是|  
|.NETFramework,Version\=v4.0.1||||是||是||是|是|  
|.NETFramework,Version\=v4.0.2,Profile\=Client|||||是|是|是|是|是|  
|.NETFramework,Version\=v4.0.2||||||是||是|是|  
|.NETFramework,Version\=v4.0.3,Profile\=Client|||||||是|是|是|  
|.NETFramework,Version\=v4.0.3||||||||是|是|  
  
## 範例  
 下列範例將示範如何在設定檔中指定支援的執行階段版本。 設定檔會指出應用程式將.NET Framework 4.6 作為目標。  
  
```xml  
  
<configuration> <startup> <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.6" /> </startup> </configuration>  
  
```  
  
## 組態檔  
 這個項目可以在應用程式組態檔中使用。  
  
## 請參閱  
 [啟動設定結構描述](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<PaveOver\> 指定要使用哪一個執行階段版本](http://msdn.microsoft.com/zh-tw/c376208d-980d-42b4-865b-fbe0d9cc97c2)   
 [同處理序並存執行](../../../../../docs/framework/deployment/in-process-side-by-side-execution.md)