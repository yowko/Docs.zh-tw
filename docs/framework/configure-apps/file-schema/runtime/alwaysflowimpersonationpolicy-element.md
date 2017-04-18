---
title: "&lt;alwaysFlowImpersonationPolicy&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/alwaysFlowImpersonationPolicy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#alwaysFlowImpersonationPolicy"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<alwaysFlowImpersonationPolicy> 項目"
  - "alwaysFlowImpersonationPolicy 項目"
ms.assetid: ee622801-9e46-470b-85ab-88c4b1dd2ee1
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 7
---
# &lt;alwaysFlowImpersonationPolicy&gt; 項目
指定 Windows 識別一定會跨非同步點流動，不論如何執行模擬。  
  
## 語法  
  
```  
<alwaysFlowImpersonationPolicy    
  enabled="true|false"/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`enabled`|必要屬性。<br /><br /> 指出 Windows 識別是否會跨非同步點流動。|  
  
## 啟用屬性  
  
|值|描述|  
|-------|--------|  
|`false`|Windows 識別不會跨非同步點流動，除非是透過如 <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> 的 Managed 方法來執行模擬。  這是預設值。|  
|`true`|Windows 識別一定會跨非同步點流動，不論如何執行模擬。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 在 .NET Framework 1.0 和 1.1 版中，Windows 識別不會跨非同步點流動。  在 .NET Framework 2.0 版中，有一個 <xref:System.Threading.ExecutionContext> 物件包含了與目前執行之執行緒有關的資訊，而且它會在應用程式定義域內跨非同步點流動。  <xref:System.Security.Principal.WindowsIdentity> 也會當做此資訊的一部分進行跨非同步點流動，但前提是模擬作業是利用類似 <xref:System.Security.Principal.WindowsIdentity.Impersonate%2A> 的 Managed 方法所完成，而不是透過類似原生方法的平台叫用等其他方法來完成。  這個項目是用來指定 Windows 識別不會跨非同步點流動，不論模擬作業是如何完成。  
  
 您可以使用兩種其他方式來更改此預設行為：  
  
1.  針對個別執行緒在 Managed 程式碼中進行。  
  
     您可以針對個別執行緒來隱藏此流程，其方式是使用 <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=fullName>、<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=fullName> 或 <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=fullName> 方法修改 <xref:System.Threading.ExecutionContext> 和 <xref:System.Security.SecurityContext> 設定。  
  
2.  在 Unmanaged 裝載介面的呼叫中，用來載入 Common Language Runtime \(CLR\)。  
  
     如果使用 Unmanaged 裝載介面 \(而非單一 Managed 可執行檔\) 來載入 CLR，您可以在 [CorBindToRuntimeEx 函式](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) 函式的呼叫中指定特殊旗標。  若要為整個處理序啟用相容性模式，請將 [CorBindToRuntimeEx 函式](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) 的 `flags` 參數設定為 STARTUP\_ALWAYSFLOW\_IMPERSONATION。  
  
## 組態檔  
 這個項目只能在應用程式組態檔中使用。  
  
## 範例  
 下列範例將示範如何指定 Windows 識別會跨非同步點流動，即使是透過 Managed 方法以外的方式來完成模擬。  
  
```  
<configuration>  
  <runtime>  
    <alwaysFlowImpersonationPolicy enabled="true"/>  
  </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)   
 [\<legacyImpersonationPolicy\> 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/legacyimpersonationpolicy-element.md)