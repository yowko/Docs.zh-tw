---
title: "&lt;legacyImpersonationPolicy&gt; 項目 | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#legacyImpersonationPolicy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/legacyImpersonationPolicy"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<legacyImpersonationPolicy> 項目"
  - "legacyImpersonationPolicy 項目"
ms.assetid: 6e00af10-42f3-4235-8415-1bb2db78394e
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# &lt;legacyImpersonationPolicy&gt; 項目
指定 Windows 識別不會跨非同步點流動，不論目前執行緒上的執行內容之流程設定為何。  
  
## 語法  
  
```  
<legacyImpersonationPolicy    
   enabled="true|false"/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`enabled`|必要屬性。<br /><br /> 指定 <xref:System.Security.Principal.WindowsIdentity> 不會跨非同步點流動，不論目前執行緒上的 <xref:System.Threading.ExecutionContext> 流程設定為何。|  
  
## 啟用屬性  
  
|值|描述|  
|-------|--------|  
|`false`|<xref:System.Security.Principal.WindowsIdentity> 會根據目前執行緒的 <xref:System.Threading.ExecutionContext> 流程設定，跨非同步點流動。  這是預設值。|  
|`true`|<xref:System.Security.Principal.WindowsIdentity> 不會跨非同步點流動，不論目前執行緒上的 <xref:System.Threading.ExecutionContext> 流程設定為何。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|`configuration`|Common Language Runtime 和 .NET Framework 應用程式所使用之每個組態檔中的根項目。|  
|`runtime`|包含有關組件繫結和記憶體回收的資訊。|  
  
## 備註  
 在 .NET Framework 1.0 和 1.1 版中，<xref:System.Security.Principal.WindowsIdentity> 不會跨任何使用者定義的非同步點流動。  在 .NET Framework 2.0 版中，有一個 <xref:System.Threading.ExecutionContext> 物件包含了與目前執行之執行緒有關的資訊，而且它會在應用程式定義域內跨非同步點流動。  <xref:System.Security.Principal.WindowsIdentity> 也會當成此資訊的一部分跨非同步點流動，這表示如果模擬內容結束，它也會流動。  這個項目是用來指定 <xref:System.Security.Principal.WindowsIdentity> 不會跨非同步點流動。  
  
> [!NOTE]
>  Common Language Runtime \(CLR\) 只會注意到使用 Managed 程式碼執行的模擬作業，而無法得知 Managed 程式碼外部執行的模擬作業，例如，透過對 Unmanaged 程式碼的平台叫用 \(Invoke\) 或直接呼叫 Win32 函式。  除非 `alwaysFlowImpersonationPolicy` 項目已設定為 true \(`<alwaysFlowImpersonationPolicy enabled="true"/>`\)，否則只有 Managed <xref:System.Security.Principal.WindowsIdentity> 物件可以跨非同步點流動。  將 `alwaysFlowImpersonationPolicy` 項目設定為 true 會指定 Windows 識別一定會跨非同步點流動，而不論如何執行模擬作業。  如需跨非同步點流動之 Unmanaged 模擬的詳細資訊，請參閱 [\<alwaysFlowImpersonationPolicy\> 項目](../../../../../docs/framework/configure-apps/file-schema/runtime/alwaysflowimpersonationpolicy-element.md)。  
  
 這個項目只能在應用程式組態檔中使用。  
  
 您可以使用兩種其他方式來更改此預設行為：  
  
1.  針對個別執行緒在 Managed 程式碼中進行。  
  
     您可以針對個別執行緒來隱藏此流程，其方式是使用 <xref:System.Threading.ExecutionContext.SuppressFlow%2A?displayProperty=fullName>、<xref:System.Security.SecurityContext.SuppressFlowWindowsIdentity%2A?displayProperty=fullName> 或 <xref:System.Security.SecurityContext.SuppressFlow%2A?displayProperty=fullName> 方法修改 <xref:System.Threading.ExecutionContext> 和 <xref:System.Security.SecurityContext> 設定。  
  
2.  在 Unmanaged 裝載介面的呼叫中，用來載入 Common Language Runtime \(CLR\)。  
  
     如果使用 Unmanaged 裝載介面 \(而非單一 Managed 可執行檔\) 來載入 CLR，您可以在 [CorBindToRuntimeEx 函式](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) 函式的呼叫中指定特殊旗標。  若要為整個處理序啟用相容性模式，請將 [CorBindToRuntimeEx 函式](../../../../../ocs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) 的 `flags` 參數設定為 STARTUP\_LEGACY\_IMPERSONATION。  
  
## 範例  
 下列範例將示範如何指定舊有的行為，此行為不會讓 Windows 識別跨非同步點流動。  
  
```  
<configuration>  
   <runtime>  
      <legacyImpersonationPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [執行階段設定結構描述](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [組態檔結構描述](../../../../../docs/framework/configure-apps/file-schema/index.md)