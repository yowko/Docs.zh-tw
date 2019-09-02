---
title: 程式碼存取安全性原則相容性和移轉
ms.date: 03/30/2017
helpviewer_keywords:
- policy migration, compatibility
- CLR policy migration
ms.assetid: 19cb4d39-e38a-4262-b507-458915303115
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9563dae9ba5d144300549e7f33f5f5a9feb1d410
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70205644"
---
# <a name="code-access-security-policy-compatibility-and-migration"></a>程式碼存取安全性原則相容性和移轉

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

代碼啟用安全性 (CAS) 的原則部分在 .NET Framework 4 中已過時。 因此, 如果您以[明確](#explicit_use)或[隱含](#implicit_use)方式 (透過其他類型和成員) 呼叫過時的原則類型和成員, 可能會遇到編譯警告和執行時間例外狀況。

您可以透過下列方式避免出現警告和錯誤：

- [遷移](#migration)至已淘汰呼叫的 .NET Framework 4 取代專案。

   \-或-

- 使用[NetFx40_LegacySecurityPolicy > configuration 專案, 加入宣告舊版的 CAS 原則行為。 \< ](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)

本主題包含下列幾節：

- [明確使用](#explicit_use)

- [隱含使用](#implicit_use)

- [錯誤與警告](#errors_and_warnings)

- [移動取代過時的呼叫](#migration)

- [為了使用 CAS 原則舊版選項](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a>明確使用

直接管理安全性原則或要求 CAS 原則進行沙箱化的成員都已過時，而且預設會出現錯誤。

範例如下：

- <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.HostSecurityManager.DomainPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.Policy.PolicyLevel.CreateAppDomainLevel%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromString%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.LoadPolicyLevelFromFile%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolveSystemPolicy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.ResolvePolicyGroups%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.PolicyHierarchy%2A?displayProperty=nameWithType>

- <xref:System.Security.SecurityManager.SavePolicy%2A?displayProperty=nameWithType>

<a name="implicit_use"></a>

## <a name="implicit-use"></a>隱含使用

有幾個載入多載的組件出現錯誤，因為它們隱含使用了 CAS 原則。 這些多載會接受用於解析 CAS 原則的 <xref:System.Security.Policy.Evidence> 參數，並且為組件提供權限授權集。

以下是一些範例。 過時的多載是指接受 <xref:System.Security.Policy.Evidence> 做為參數的下列多載：

- <xref:System.Activator.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceFrom%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.DefineDynamicAssembly%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.ExecuteAssemblyByName%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>

<a name="errors_and_warnings"></a>

## <a name="errors-and-warnings"></a>錯誤和警告

如果使用了過時的類型和成員，會出現下列錯誤訊息。 請注意，<xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 類型本身並沒有過時。

編譯時期的警告：

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

執行階段例外狀況：

<xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a>移動取代過時的呼叫

### <a name="determining-an-assemblys-trust-level"></a>決定組件的信任層級

CAS 原則通常用於決定組件或應用程式定義域的權限授權集或信任層級。 .NET Framework 4 會公開下列有用的屬性, 這些內容不需要解析安全性原則:

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a>應用程式定義域沙箱作業

<xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> 方法通常用於對應用程式定義域中的組件進行沙箱化處理。 .NET Framework 4 會公開不需要<xref:System.Security.Policy.PolicyLevel>用於此用途的成員。 如需詳細資訊，請參閱[如何：在沙箱中執行部分信任的程式碼](how-to-run-partially-trusted-code-in-a-sandbox.md)中所述。

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a>決定部分信任程式碼的安全或合理權限集合

主機通常需要決定對裝載的程式碼進行沙箱化處理的適當權限。 在 .NET Framework 4 之前, CAS 原則提供了使用<xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>方法來執行此動作的方法。 做為取代, .NET Framework 4 會提供<xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType>方法, 以傳回所提供辨識項的安全標準許可權集合。

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a>非沙箱案例:元件載入的多載

不對組件進行沙箱化處理，而使用組件載入多載的原因，可能是為了要使用在其他情況下無法使用的參數。 從 .NET Framework 4 開始, 不需要<xref:System.Security.Policy.Evidence?displayProperty=nameWithType>物件做為參數 ( <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>例如) 的元件載入多載會啟用此案例。

如果您要對組件進行沙箱化處理，請使用 <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> 多載。

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a>為了使用 CAS 原則舊版選項

NetFx40_LegacySecurityPolicy > configuration 元素可讓您指定進程或程式庫使用舊版的 CAS 原則。 [ \< ](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) 當您啟用這個項目時，原則和辨識項多載的運作方式與在舊版 Framework 中的運作方式相同。

> [!NOTE]
> CAS 原則行為是以執行階段版本為依據所指定，如此一來，修改某一個執行階段版本的 CAS 原則，就不會影響另一個版本的 CAS 原則。

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a>另請參閱

- [如何：在沙箱中執行部分信任的程式碼](how-to-run-partially-trusted-code-in-a-sandbox.md)
- [安全程式碼撰寫方針](../../standard/security/secure-coding-guidelines.md)
