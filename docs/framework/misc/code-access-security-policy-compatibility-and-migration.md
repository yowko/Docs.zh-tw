---
title: "Code Access Security Policy Compatibility and Migration | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
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
  - "policy migration, compatibility"
  - "CLR poliicy migration"
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
caps.latest.revision: 15
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# Code Access Security Policy Compatibility and Migration
程式碼存取安全性 \(CAS\) 的原則部分在 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 中已過時。  因此，如果您以[明確](#explicit_use)或[隱含](#implicit_use)方式 \(透過其他類型和成員\) 呼叫過時的原則類型和成員，可能會遇到編譯警告和執行階段例外狀況。  
  
 您可以透過下列方式避免出現警告和錯誤：  
  
-   [移轉](#migration)至 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)]，以取代過時呼叫。  
  
     \-或\-  
  
-   使用 [\<NetFx40\_LegacySecurityPolicy\> 組態項目](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)選擇使用舊版的 CAS 原則行為。  
  
 此主題包括下列章節：  
  
-   [明確使用](#explicit_use)  
  
-   [隱含使用](#implicit_use)  
  
-   [錯誤和警告](#errors_and_warnings)  
  
-   [移轉：取代過時呼叫](#migration)  
  
-   [相容性：使用 CAS 原則的舊版選項](#compatibility)  
  
> [!CAUTION]
>  程式碼存取安全性和部分信任的程式碼  
>   
>  .NET Framework 提供一個稱為程式碼存取安全性 \(CAS\) 的機制，可對在同一個應用程式中執行的不同程式碼強制執行各種信任層級。  .NET Framework 中的程式碼存取安全性不應該做為部分信任的程式碼 \(特別是未知來源的程式碼\) 的安全性界限使用。  建議不要載入及執行未知來源的程式碼，如此便不需要使用替代的安全措施。  
>   
>  這項原則適用於所有 .NET Framework 版本，但不適用於 Silverlight 隨附的 .NET Framework。  
  
<a name="explicit_use"></a>   
## 明確使用  
 直接管理安全性原則或要求 CAS 原則進行沙箱化的成員都已過時，而且預設會出現錯誤。  
  
 範例如下：  
  
-   <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=fullName>  
  
-   <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=fullName>  
  
-   <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=fullName>  
  
-   <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=fullName>  
  
-   <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=fullName>  
  
-   <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=fullName>  
  
-   <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=fullName>  
  
-   <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=fullName>  
  
-   <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=fullName>  
  
-   <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=fullName>  
  
<a name="implicit_use"></a>   
## 隱含使用  
 有幾個載入多載的組件出現錯誤，因為它們隱含使用了 CAS 原則。  這些多載會接受用於解析 CAS 原則的 <xref:System.Security.Policy.Evidence> 參數，並且為組件提供權限授權集。  
  
 以下是一些範例。  過時的多載是指接受 <xref:System.Security.Policy.Evidence> 做為參數的下列多載：  
  
-   <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.Load%2A?displayProperty=fullName>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName>  
  
-   <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>  
  
-   <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName>  
  
<a name="errors_and_warnings"></a>   
## 錯誤和警告  
 如果使用了過時的類型和成員，會出現下列錯誤訊息。  請注意，<xref:System.Security.Policy.Evidence?displayProperty=fullName> 類型本身並沒有過時。  
  
 編譯時期的警告：  
  
 `warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework.  Please use <suggested alternate API>.  See <link> for more information.'`  
  
 執行階段例外狀況：  
  
 <xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`  
  
<a name="migration"></a>   
## 移轉：取代過時呼叫  
  
### 決定組件的信任層級  
 CAS 原則通常用於決定組件或應用程式定義域的權限授權集或信任層級。  [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 會公開下列實用的屬性，這些屬性不需要解析安全性原則：  
  
-   <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=fullName>  
  
-   <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.PermissionSet%2A?displayProperty=fullName>  
  
-   <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=fullName>  
  
### 應用程式定義域沙箱作業  
 <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=fullName> 方法通常用於對應用程式定義域中的組件進行沙箱化處理。  [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 會公開不需基於這個目的而使用 <xref:System.Security.Policy.PolicyLevel> 的成員。 如需詳細資訊，請參閱[How to: Run Partially Trusted Code in a Sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)。  
  
### 決定部分信任程式碼的安全或合理權限集合  
 主機通常需要決定對裝載的程式碼進行沙箱化處理的適當權限。  在 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 之前，CAS 原則可透過 <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=fullName> 方法來執行這項作業。  為了取代這項功能，[!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 提供了 <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=fullName> 方法，為已提供的辨識項傳回安全、標準的權限集合。  
  
### 非沙箱化案例：組件載入的多載  
 不對組件進行沙箱化處理，而使用組件載入多載的原因，可能是為了要使用在其他情況下無法使用的參數。  從 [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 起，不需要 <xref:System.Security.Policy.Evidence?displayProperty=fullName> 物件做為參數 \(例如 [AppDomain.ExecuteAssembly\(String, String\[\], Byte\<xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=fullName>\) 的組件載入多載就適用這個案例。  
  
 如果您要對組件進行沙箱化處理，請使用 [AppDomain.CreateDomain\(String, Evidence, AppDomainSetup, PermissionSet, StrongName\<xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=fullName> 多載。  
  
<a name="compatibility"></a>   
## 相容性：使用 CAS 原則的舊版選項  
 [\<NetFx40\_LegacySecurityPolicy\> 組態項目](../../../docs/framework/configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)可以讓您指定處理序或程式庫要使用舊版 CAS 原則。  當您啟用這個項目時，原則和辨識項多載的運作方式與在舊版 Framework 中的運作方式相同。  
  
> [!NOTE]
>  CAS 原則行為是以執行階段版本為依據所指定，如此一來，修改某一個執行階段版本的 CAS 原則，就不會影響另一個版本的 CAS 原則。  
  
```  
<configuration>  
   <runtime>  
      <NetFx40_LegacySecurityPolicy enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## 請參閱  
 [How to: Run Partially Trusted Code in a Sandbox](../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)