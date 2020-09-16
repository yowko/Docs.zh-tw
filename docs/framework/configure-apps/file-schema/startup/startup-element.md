---
title: <startup> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup
- http://schemas.microsoft.com/.NetConfiguration/v2.0#startup
helpviewer_keywords:
- container tags, <startup> element
- <startup> element
- startup element
ms.assetid: 536acfd8-f827-452f-838a-e14fa3b87621
ms.openlocfilehash: cd91abb288c1cfb281f17f2fce95d4956908468f
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90550842"
---
# <a name="startup-element"></a><span data-ttu-id="90fe3-102">\<startup> 項目</span><span class="sxs-lookup"><span data-stu-id="90fe3-102">\<startup> element</span></span>

<span data-ttu-id="90fe3-103">指定 common language runtime 啟動資訊。</span><span class="sxs-lookup"><span data-stu-id="90fe3-103">Specifies common language runtime startup information.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<startup>**  

## <a name="syntax"></a><span data-ttu-id="90fe3-104">語法</span><span class="sxs-lookup"><span data-stu-id="90fe3-104">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" >
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="90fe3-105">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="90fe3-105">Attributes and elements</span></span>

 <span data-ttu-id="90fe3-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="90fe3-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="90fe3-107">屬性</span><span class="sxs-lookup"><span data-stu-id="90fe3-107">Attributes</span></span>

|<span data-ttu-id="90fe3-108">屬性</span><span class="sxs-lookup"><span data-stu-id="90fe3-108">Attribute</span></span>|<span data-ttu-id="90fe3-109">描述</span><span class="sxs-lookup"><span data-stu-id="90fe3-109">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="90fe3-110">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="90fe3-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="90fe3-111">指定是否要啟用 .NET Framework 2.0 執行時間啟用原則，或使用 .NET Framework 4 啟用原則。</span><span class="sxs-lookup"><span data-stu-id="90fe3-111">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="90fe3-112">useLegacyV2RuntimeActivationPolicy 屬性</span><span class="sxs-lookup"><span data-stu-id="90fe3-112">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="90fe3-113">值</span><span class="sxs-lookup"><span data-stu-id="90fe3-113">Value</span></span>|<span data-ttu-id="90fe3-114">描述</span><span class="sxs-lookup"><span data-stu-id="90fe3-114">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="90fe3-115">針對所選執行時間啟用 .NET Framework 2.0 執行時間啟用原則，也就是系結舊版執行時間啟動技巧 (例如 [CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md) 函式) 至從設定檔中選擇的執行時間，而不是在 CLR 2.0 版中將它們設為上限。</span><span class="sxs-lookup"><span data-stu-id="90fe3-115">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="90fe3-116">因此，如果從設定檔選擇 CLR 4 版或更新版本，使用舊版 .NET Framework 所建立的混合模式元件會載入所選的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="90fe3-116">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="90fe3-117">設定此值可防止 CLR 1.1 版或 CLR 2.0 版載入相同的進程中，有效地停用同進程並存功能。</span><span class="sxs-lookup"><span data-stu-id="90fe3-117">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="90fe3-118">針對 .NET Framework 4 和更新版本使用預設啟用原則，這是為了允許舊版執行時間啟用技術將 CLR 1.1 或2.0 版載入至程式。</span><span class="sxs-lookup"><span data-stu-id="90fe3-118">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="90fe3-119">設定此值可防止混合模式元件載入 .NET Framework 4 或更新版本，除非它們是以 .NET Framework 4 或更新版本所建立。</span><span class="sxs-lookup"><span data-stu-id="90fe3-119">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="90fe3-120">此值為預設值。</span><span class="sxs-lookup"><span data-stu-id="90fe3-120">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="90fe3-121">子元素</span><span class="sxs-lookup"><span data-stu-id="90fe3-121">Child elements</span></span>

|<span data-ttu-id="90fe3-122">項目</span><span class="sxs-lookup"><span data-stu-id="90fe3-122">Element</span></span>|<span data-ttu-id="90fe3-123">描述</span><span class="sxs-lookup"><span data-stu-id="90fe3-123">Description</span></span>|
|-------------|-----------------|
|[\<requiredRuntime>](requiredruntime-element.md)|<span data-ttu-id="90fe3-124">指定應用程式只支援 Common Language Runtime 1.0 版。</span><span class="sxs-lookup"><span data-stu-id="90fe3-124">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="90fe3-125">使用執行階段版本1.1 或更新版本所建立的應用程式應該使用 **\<supportedRuntime>** 元素。</span><span class="sxs-lookup"><span data-stu-id="90fe3-125">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[\<supportedRuntime>](supportedruntime-element.md)|<span data-ttu-id="90fe3-126">指定應用程式支援的通用語言執行平台版本。</span><span class="sxs-lookup"><span data-stu-id="90fe3-126">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="90fe3-127">父元素</span><span class="sxs-lookup"><span data-stu-id="90fe3-127">Parent elements</span></span>

|<span data-ttu-id="90fe3-128">項目</span><span class="sxs-lookup"><span data-stu-id="90fe3-128">Element</span></span>|<span data-ttu-id="90fe3-129">描述</span><span class="sxs-lookup"><span data-stu-id="90fe3-129">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="90fe3-130">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="90fe3-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="90fe3-131">備註</span><span class="sxs-lookup"><span data-stu-id="90fe3-131">Remarks</span></span>

 <span data-ttu-id="90fe3-132">**\<supportedRuntime>** 使用1.1 版或更新版本的執行時間所建立的所有應用程式都應該使用元素。</span><span class="sxs-lookup"><span data-stu-id="90fe3-132">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="90fe3-133">為了僅支援1.0 版執行時間所建立的應用程式，必須使用 **\<requiredRuntime>** 元素。</span><span class="sxs-lookup"><span data-stu-id="90fe3-133">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="90fe3-134">Microsoft Internet Explorer 中裝載之應用程式的啟始程式碼會忽略 **\<startup>** 元素和其子項目。</span><span class="sxs-lookup"><span data-stu-id="90fe3-134">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="90fe3-135">UseLegacyV2RuntimeActivationPolicy 屬性</span><span class="sxs-lookup"><span data-stu-id="90fe3-135">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="90fe3-136">如果您的應用程式使用舊版啟動路徑（例如 [CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)函式），而您想要讓這些路徑啟用 CLR 的第4版（而不是舊版），或如果您的應用程式是以 .NET Framework 4 建立，但相依于使用舊版 .NET Framework 所建立的混合模式元件，則此屬性會很有用。</span><span class="sxs-lookup"><span data-stu-id="90fe3-136">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="90fe3-137">在這些情況下，請將屬性設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="90fe3-137">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="90fe3-138">設定屬性以 `true` 防止 clr 1.1 或 clr 2.0 版載入至相同的進程，有效地停用同進程並存功能 (查看 [COM Interop) 的並存執行](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100)) 。</span><span class="sxs-lookup"><span data-stu-id="90fe3-138">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="90fe3-139">範例</span><span class="sxs-lookup"><span data-stu-id="90fe3-139">Example</span></span>

 <span data-ttu-id="90fe3-140">下列範例顯示如何在設定檔中指定執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="90fe3-140">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
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

## <a name="see-also"></a><span data-ttu-id="90fe3-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90fe3-141">See also</span></span>

- [<span data-ttu-id="90fe3-142">啟動設定架構</span><span class="sxs-lookup"><span data-stu-id="90fe3-142">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="90fe3-143">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="90fe3-143">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="90fe3-144">如何：設定應用程式以支援 .NET Framework 4 或更新版本</span><span class="sxs-lookup"><span data-stu-id="90fe3-144">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="90fe3-145">[COM Interop 的並存執行](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="90fe3-145">[Side-by-Side Execution for COM Interop](/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="90fe3-146">同處理序並存執行</span><span class="sxs-lookup"><span data-stu-id="90fe3-146">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
