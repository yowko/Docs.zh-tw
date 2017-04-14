---
title: "&lt;appDomainResourceMonitoring&gt; 項目 | Microsoft Docs"
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
  - "<appDomainResourceMonitoring> 項目"
  - "appDomainResourceMonitoring 項目"
ms.assetid: 02119ab6-1e91-448e-97ad-e7b2e5c4bbbd
caps.latest.revision: 14
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# &lt;appDomainResourceMonitoring&gt; 項目
指示執行階段收集處理序中，所有應用程式定義域在處理序存留期間的統計資料。  
  
## 語法  
  
```  
<appDomainResourceMonitoring    
   enabled="true|false"/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`enabled`|必要屬性。<br /><br /> 指定執行階段是否要收集應用程式定義域資源監視的統計資料。|  
  
## 啟用屬性  
  
|值|描述|  
|-------|--------|  
|`true`|要收集應用程式定義域資源監視的統計資料。|  
|`false`|不要收集應用程式定義域資源監視的統計資料。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 透過 Managed 應用程式定義域類別、進行裝載的 [ICLRAppDomainResourceMonitor](../../../../../ocs/framework/unmanaged-api/hosting/iclrappdomainresourcemonitor-interface.md) 介面和 Windows 事件追蹤 \(ETW\)，即可使用應用程式定義域資源監視。  啟用監視功能時，會收集處理序中所有應用程式定義域在處理序存留期間的統計資料。  
  
 若要從 Managed 程式碼啟用監視功能，請使用 <xref:System.AppDomain.MonitoringIsEnabled%2A> 屬性。  
  
 這個組態項目只能在 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] \(含\) 以後版本中使用。  
  
## 範例  
 下列範例示範如何啟用應用程式定義域資源監視。  
  
```  
<configuration>  
   <runtime>  
      <appDomainResourceMonitoring enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=fullName>   
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)