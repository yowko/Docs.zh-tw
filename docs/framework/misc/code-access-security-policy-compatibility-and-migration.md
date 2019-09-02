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
# <a name="code-access-security-policy-compatibility-and-migration"></a><span data-ttu-id="64a75-102">程式碼存取安全性原則相容性和移轉</span><span class="sxs-lookup"><span data-stu-id="64a75-102">Code Access Security Policy Compatibility and Migration</span></span>

[!INCLUDE[net_security_note](../../../includes/net-security-note-md.md)]

<span data-ttu-id="64a75-103">代碼啟用安全性 (CAS) 的原則部分在 .NET Framework 4 中已過時。</span><span class="sxs-lookup"><span data-stu-id="64a75-103">The policy portion of code access security (CAS) has been made obsolete in the .NET Framework 4.</span></span> <span data-ttu-id="64a75-104">因此, 如果您以[明確](#explicit_use)或[隱含](#implicit_use)方式 (透過其他類型和成員) 呼叫過時的原則類型和成員, 可能會遇到編譯警告和執行時間例外狀況。</span><span class="sxs-lookup"><span data-stu-id="64a75-104">As a result, you may encounter compilation warnings and runtime exceptions if you call the obsolete policy types and members [explicitly](#explicit_use) or [implicitly](#implicit_use) (through other types and members).</span></span>

<span data-ttu-id="64a75-105">您可以透過下列方式避免出現警告和錯誤：</span><span class="sxs-lookup"><span data-stu-id="64a75-105">You can avoid the warnings and errors by either:</span></span>

- <span data-ttu-id="64a75-106">[遷移](#migration)至已淘汰呼叫的 .NET Framework 4 取代專案。</span><span class="sxs-lookup"><span data-stu-id="64a75-106">[Migrating](#migration) to the .NET Framework 4 replacements for the obsolete calls.</span></span>

   <span data-ttu-id="64a75-107">\-或-</span><span class="sxs-lookup"><span data-stu-id="64a75-107">\- or -</span></span>

- <span data-ttu-id="64a75-108">使用[NetFx40_LegacySecurityPolicy > configuration 專案, 加入宣告舊版的 CAS 原則行為。 \< ](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)</span><span class="sxs-lookup"><span data-stu-id="64a75-108">Using the [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) to opt into the legacy CAS policy behavior.</span></span>

<span data-ttu-id="64a75-109">本主題包含下列幾節：</span><span class="sxs-lookup"><span data-stu-id="64a75-109">This topic contains the following sections:</span></span>

- [<span data-ttu-id="64a75-110">明確使用</span><span class="sxs-lookup"><span data-stu-id="64a75-110">Explicit Use</span></span>](#explicit_use)

- [<span data-ttu-id="64a75-111">隱含使用</span><span class="sxs-lookup"><span data-stu-id="64a75-111">Implicit Use</span></span>](#implicit_use)

- [<span data-ttu-id="64a75-112">錯誤與警告</span><span class="sxs-lookup"><span data-stu-id="64a75-112">Errors and Warnings</span></span>](#errors_and_warnings)

- [<span data-ttu-id="64a75-113">移動取代過時的呼叫</span><span class="sxs-lookup"><span data-stu-id="64a75-113">Migration: Replacement for Obsolete Calls</span></span>](#migration)

- [<span data-ttu-id="64a75-114">為了使用 CAS 原則舊版選項</span><span class="sxs-lookup"><span data-stu-id="64a75-114">Compatibility: Using the CAS Policy Legacy Option</span></span>](#compatibility)

<a name="explicit_use"></a>

## <a name="explicit-use"></a><span data-ttu-id="64a75-115">明確使用</span><span class="sxs-lookup"><span data-stu-id="64a75-115">Explicit Use</span></span>

<span data-ttu-id="64a75-116">直接管理安全性原則或要求 CAS 原則進行沙箱化的成員都已過時，而且預設會出現錯誤。</span><span class="sxs-lookup"><span data-stu-id="64a75-116">Members that directly manipulate security policy or require CAS policy to sandbox are obsolete and will produce errors by default.</span></span>

<span data-ttu-id="64a75-117">範例如下：</span><span class="sxs-lookup"><span data-stu-id="64a75-117">Examples of these are:</span></span>

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

## <a name="implicit-use"></a><span data-ttu-id="64a75-118">隱含使用</span><span class="sxs-lookup"><span data-stu-id="64a75-118">Implicit Use</span></span>

<span data-ttu-id="64a75-119">有幾個載入多載的組件出現錯誤，因為它們隱含使用了 CAS 原則。</span><span class="sxs-lookup"><span data-stu-id="64a75-119">Several assembly loading overloads produce errors because of their implicit use of CAS policy.</span></span> <span data-ttu-id="64a75-120">這些多載會接受用於解析 CAS 原則的 <xref:System.Security.Policy.Evidence> 參數，並且為組件提供權限授權集。</span><span class="sxs-lookup"><span data-stu-id="64a75-120">These overloads take an <xref:System.Security.Policy.Evidence> parameter that is used to resolve CAS policy and provide a permission grant set for an assembly.</span></span>

<span data-ttu-id="64a75-121">以下是一些範例。</span><span class="sxs-lookup"><span data-stu-id="64a75-121">Here are some examples.</span></span> <span data-ttu-id="64a75-122">過時的多載是指接受 <xref:System.Security.Policy.Evidence> 做為參數的下列多載：</span><span class="sxs-lookup"><span data-stu-id="64a75-122">The obsolete overloads are those that take <xref:System.Security.Policy.Evidence> as a parameter:</span></span>

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

## <a name="errors-and-warnings"></a><span data-ttu-id="64a75-123">錯誤和警告</span><span class="sxs-lookup"><span data-stu-id="64a75-123">Errors and Warnings</span></span>

<span data-ttu-id="64a75-124">如果使用了過時的類型和成員，會出現下列錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="64a75-124">The obsolete types and members produce the following error messages when they are used.</span></span> <span data-ttu-id="64a75-125">請注意，<xref:System.Security.Policy.Evidence?displayProperty=nameWithType> 類型本身並沒有過時。</span><span class="sxs-lookup"><span data-stu-id="64a75-125">Note that the <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> type itself is not obsolete.</span></span>

<span data-ttu-id="64a75-126">編譯時期的警告：</span><span class="sxs-lookup"><span data-stu-id="64a75-126">Compile-time warning:</span></span>

`warning CS0618: '<API Name>' is obsolete: 'This method is obsolete and will be removed in a future release of the .NET Framework. Please use <suggested alternate API>. See <link> for more information.'`

<span data-ttu-id="64a75-127">執行階段例外狀況：</span><span class="sxs-lookup"><span data-stu-id="64a75-127">Run-time exception:</span></span>

<span data-ttu-id="64a75-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span><span class="sxs-lookup"><span data-stu-id="64a75-128"><xref:System.NotSupportedException>: `This method uses CAS policy, which has been obsoleted by the .NET Framework. In order to enable CAS policy for compatibility reasons, please use the <NetFx40_LegacySecurityPolicy> configuration switch. Please see <link> for more information.`</span></span>

<a name="migration"></a>

## <a name="migration-replacement-for-obsolete-calls"></a><span data-ttu-id="64a75-129">移動取代過時的呼叫</span><span class="sxs-lookup"><span data-stu-id="64a75-129">Migration: Replacement for Obsolete Calls</span></span>

### <a name="determining-an-assemblys-trust-level"></a><span data-ttu-id="64a75-130">決定組件的信任層級</span><span class="sxs-lookup"><span data-stu-id="64a75-130">Determining an Assembly’s Trust Level</span></span>

<span data-ttu-id="64a75-131">CAS 原則通常用於決定組件或應用程式定義域的權限授權集或信任層級。</span><span class="sxs-lookup"><span data-stu-id="64a75-131">CAS policy is often used to determine an assembly’s or application domain’s permission grant set or trust level.</span></span> <span data-ttu-id="64a75-132">.NET Framework 4 會公開下列有用的屬性, 這些內容不需要解析安全性原則:</span><span class="sxs-lookup"><span data-stu-id="64a75-132">The .NET Framework 4 exposes the following useful properties that do not need to resolve security policy:</span></span>

- <xref:System.Reflection.Assembly.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.Reflection.Assembly.IsFullyTrusted%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.PermissionSet%2A?displayProperty=nameWithType>

- <xref:System.AppDomain.IsFullyTrusted%2A?displayProperty=nameWithType>

### <a name="application-domain-sandboxing"></a><span data-ttu-id="64a75-133">應用程式定義域沙箱作業</span><span class="sxs-lookup"><span data-stu-id="64a75-133">Application Domain Sandboxing</span></span>

<span data-ttu-id="64a75-134"><xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> 方法通常用於對應用程式定義域中的組件進行沙箱化處理。</span><span class="sxs-lookup"><span data-stu-id="64a75-134">The <xref:System.AppDomain.SetAppDomainPolicy%2A?displayProperty=nameWithType> method is typically used for sandboxing the assemblies in an application domain.</span></span> <span data-ttu-id="64a75-135">.NET Framework 4 會公開不需要<xref:System.Security.Policy.PolicyLevel>用於此用途的成員。</span><span class="sxs-lookup"><span data-stu-id="64a75-135">The .NET Framework 4 exposes members that do not have to use <xref:System.Security.Policy.PolicyLevel> for this purpose.</span></span> <span data-ttu-id="64a75-136">如需詳細資訊，請參閱[如何：在沙箱中執行部分信任的程式碼](how-to-run-partially-trusted-code-in-a-sandbox.md)中所述。</span><span class="sxs-lookup"><span data-stu-id="64a75-136">For more information, see [How to: Run Partially Trusted Code in a Sandbox](how-to-run-partially-trusted-code-in-a-sandbox.md).</span></span>

### <a name="determining-a-safe-or-reasonable-permission-set-for-partially-trusted-code"></a><span data-ttu-id="64a75-137">決定部分信任程式碼的安全或合理權限集合</span><span class="sxs-lookup"><span data-stu-id="64a75-137">Determining a Safe or Reasonable Permission Set for Partially Trusted Code</span></span>

<span data-ttu-id="64a75-138">主機通常需要決定對裝載的程式碼進行沙箱化處理的適當權限。</span><span class="sxs-lookup"><span data-stu-id="64a75-138">Hosts often need to determine the permissions that are appropriate for sandboxing hosted code.</span></span> <span data-ttu-id="64a75-139">在 .NET Framework 4 之前, CAS 原則提供了使用<xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType>方法來執行此動作的方法。</span><span class="sxs-lookup"><span data-stu-id="64a75-139">Before the .NET Framework 4, CAS policy provided a way to do this with the <xref:System.Security.SecurityManager.ResolvePolicy%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="64a75-140">做為取代, .NET Framework 4 會提供<xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType>方法, 以傳回所提供辨識項的安全標準許可權集合。</span><span class="sxs-lookup"><span data-stu-id="64a75-140">As a replacement, .NET Framework 4 provides the <xref:System.Security.SecurityManager.GetStandardSandbox%2A?displayProperty=nameWithType> method, which returns a safe, standard permission set for the provided evidence.</span></span>

### <a name="non-sandboxing-scenarios-overloads-for-assembly-loads"></a><span data-ttu-id="64a75-141">非沙箱案例:元件載入的多載</span><span class="sxs-lookup"><span data-stu-id="64a75-141">Non-Sandboxing Scenarios: Overloads for Assembly Loads</span></span>

<span data-ttu-id="64a75-142">不對組件進行沙箱化處理，而使用組件載入多載的原因，可能是為了要使用在其他情況下無法使用的參數。</span><span class="sxs-lookup"><span data-stu-id="64a75-142">The reason for using an assembly load overload might be to use parameters that are not otherwise available, instead of sandboxing the assembly.</span></span> <span data-ttu-id="64a75-143">從 .NET Framework 4 開始, 不需要<xref:System.Security.Policy.Evidence?displayProperty=nameWithType>物件做為參數 ( <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>例如) 的元件載入多載會啟用此案例。</span><span class="sxs-lookup"><span data-stu-id="64a75-143">Starting with the .NET Framework 4, assembly load overloads that do not require a <xref:System.Security.Policy.Evidence?displayProperty=nameWithType> object as a parameter, for example, <xref:System.AppDomain.ExecuteAssembly%28System.String%2CSystem.String%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Configuration.Assemblies.AssemblyHashAlgorithm%29?displayProperty=nameWithType>, enable this scenario.</span></span>

<span data-ttu-id="64a75-144">如果您要對組件進行沙箱化處理，請使用 <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> 多載。</span><span class="sxs-lookup"><span data-stu-id="64a75-144">If you want to sandbox an assembly, use the <xref:System.AppDomain.CreateDomain%28System.String%2CSystem.Security.Policy.Evidence%2CSystem.AppDomainSetup%2CSystem.Security.PermissionSet%2CSystem.Security.Policy.StrongName%5B%5D%29?displayProperty=nameWithType> overload.</span></span>

<a name="compatibility"></a>

## <a name="compatibility-using-the-cas-policy-legacy-option"></a><span data-ttu-id="64a75-145">為了使用 CAS 原則舊版選項</span><span class="sxs-lookup"><span data-stu-id="64a75-145">Compatibility: Using the CAS Policy Legacy Option</span></span>

<span data-ttu-id="64a75-146">NetFx40_LegacySecurityPolicy > configuration 元素可讓您指定進程或程式庫使用舊版的 CAS 原則。 [ \< ](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md)</span><span class="sxs-lookup"><span data-stu-id="64a75-146">The [\<NetFx40_LegacySecurityPolicy> configuration element](../configure-apps/file-schema/runtime/netfx40-legacysecuritypolicy-element.md) lets you specify that a process or library uses legacy CAS policy.</span></span> <span data-ttu-id="64a75-147">當您啟用這個項目時，原則和辨識項多載的運作方式與在舊版 Framework 中的運作方式相同。</span><span class="sxs-lookup"><span data-stu-id="64a75-147">When you enable this element, the policy and evidence overloads will work as they did in previous versions of the framework.</span></span>

> [!NOTE]
> <span data-ttu-id="64a75-148">CAS 原則行為是以執行階段版本為依據所指定，如此一來，修改某一個執行階段版本的 CAS 原則，就不會影響另一個版本的 CAS 原則。</span><span class="sxs-lookup"><span data-stu-id="64a75-148">CAS policy behavior is specified on a runtime version basis, so modifying CAS policy for one runtime version does not affect the CAS policy of another version.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_LegacySecurityPolicy enabled="true"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="64a75-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64a75-149">See also</span></span>

- [<span data-ttu-id="64a75-150">如何：在沙箱中執行部分信任的程式碼</span><span class="sxs-lookup"><span data-stu-id="64a75-150">How to: Run Partially Trusted Code in a Sandbox</span></span>](how-to-run-partially-trusted-code-in-a-sandbox.md)
- [<span data-ttu-id="64a75-151">安全程式碼撰寫方針</span><span class="sxs-lookup"><span data-stu-id="64a75-151">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
