---
title: "&lt;disableFusionUpdatesFromADManager&gt; 項目 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<disableFusionUpdatesFromADManager> 項目"
  - "disableFusionUpdatesFromADManager 項目"
ms.assetid: 58d2866c-37bd-4ffa-abaf-ff35926a2939
caps.latest.revision: 7
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;disableFusionUpdatesFromADManager&gt; 項目
指定是否停用預設行為 \(允許執行階段主機覆寫應用程式定義域的組態設定\)。  
  
## 語法  
  
```  
<disableFusionUpdatesFromADManager enabled="0|1"/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|enabled|必要屬性。<br /><br /> 指定是否停用覆寫融合設定的預設功能。|  
  
## 啟用屬性  
  
|值|說明|  
|-------|--------|  
|0|不要停用覆寫融合設定的功能。  從 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 開始，這是預設行為。|  
|1|停用覆寫融合設定的功能。  這會還原成舊版 .NET Framework 的行為。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 從 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 開始，預設行為是在 <xref:System.AppDomainManager> 的子類別中，使用傳遞至 <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=fullName> 方法實作之 <xref:System.AppDomainSetup> 物件的 <xref:System.AppDomainSetup.ConfigurationFile%2A> 屬性或 <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 方法，允許 <xref:System.AppDomainManager> 物件覆寫組態設定。  對預設應用程式定義域來說，您變更的設定會覆寫應用程式組態檔指定的設定。  至於其他應用程式定義域，這些設定會覆寫傳遞至 <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=fullName> 或 <xref:System.AppDomain.CreateDomain%2A?displayProperty=fullName> 方法的組態設定。  
  
 您可以傳遞新的組態資訊，或是傳遞 null \(在 Visual Basic 中則為 `Nothing`\) 來排除已傳入的組態資訊。  
  
 不要將組態資訊同時傳遞至 <xref:System.AppDomainSetup.ConfigurationFile%2A> 屬性和 <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 方法。  如果將組態資訊同時傳遞至兩者，便會忽略您傳遞給 <xref:System.AppDomainSetup.ConfigurationFile%2A> 屬性的資訊，因為 <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 方法會覆寫來自應用程式組態檔的組態資訊。  如果您使用 <xref:System.AppDomainSetup.ConfigurationFile%2A> 屬性，則可以將 null \(在 Visual Basic 中則為 `Nothing`\) 傳遞至 <xref:System.AppDomainSetup.SetConfigurationBytes%2A> 方法，以排除呼叫 <xref:System.AppDomainManager.CreateDomain%2A?displayProperty=fullName> 或 <xref:System.AppDomain.CreateDomain%2A?displayProperty=fullName> 方法時指定的任何組態位元。  
  
 除了組態資訊之外，您還可以在傳遞至 <xref:System.AppDomainManager.InitializeNewDomain%2A?displayProperty=fullName> 方法實作的 <xref:System.AppDomainSetup> 物件上變更下列設定：<xref:System.AppDomainSetup.ApplicationBase%2A>、<xref:System.AppDomainSetup.ApplicationName%2A>、<xref:System.AppDomainSetup.CachePath%2A>、<xref:System.AppDomainSetup.DisallowApplicationBaseProbing%2A>、<xref:System.AppDomainSetup.DisallowBindingRedirects%2A>、<xref:System.AppDomainSetup.DisallowCodeDownload%2A>、<xref:System.AppDomainSetup.DisallowPublisherPolicy%2A>、<xref:System.AppDomainSetup.DynamicBase%2A>、<xref:System.AppDomainSetup.LoaderOptimization%2A>、<xref:System.AppDomainSetup.PrivateBinPath%2A>、<xref:System.AppDomainSetup.PrivateBinPathProbe%2A>、<xref:System.AppDomainSetup.ShadowCopyDirectories%2A> 和 <xref:System.AppDomainSetup.ShadowCopyFiles%2A>。  
  
 有另一個辦法可以使用 `<disableFusionUpdatesFromADManager>` 項目，也就是建立登錄設定或設定環境變數來停用預設行為。  在登錄的 `HKCU\Software\Microsoft\.NETFramework` 或 `HKLM\Software\Microsoft\.NETFramework` 底下建立名為 `COMPLUS_disableFusionUpdatesFromADManager` 的 DWORD 值，然後將這個值設定為 1。  在命令列中，將環境變數 `COMPLUS_disableFusionUpdatesFromADManager` 設定為 1。  
  
## 範例  
 下列程式碼範例示範如何使用 `<disableFusionUpdatesFromADManager>` 項目停用覆寫融合設定的功能。  
  
```  
<configuration>  
   <runtime>  
      <disableFusionUpdatesFromADManager enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [執行階段如何找出組件](../../../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)