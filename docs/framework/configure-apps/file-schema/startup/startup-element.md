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
ms.openlocfilehash: 634d9c5248c33619abec50d441d95c111febdcbf
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699421"
---
# <a name="startup-element"></a><span data-ttu-id="a4eb3-102">@no__t 0startup > 元素</span><span class="sxs-lookup"><span data-stu-id="a4eb3-102">\<startup> element</span></span>

<span data-ttu-id="a4eb3-103">指定 common language runtime 啟動資訊。</span><span class="sxs-lookup"><span data-stu-id="a4eb3-103">Specifies common language runtime startup information.</span></span>

[<span data-ttu-id="a4eb3-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="a4eb3-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="a4eb3-105">&nbsp;&nbsp; **\<startup>**</span><span class="sxs-lookup"><span data-stu-id="a4eb3-105">&nbsp;&nbsp;**\<startup>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="a4eb3-106">語法</span><span class="sxs-lookup"><span data-stu-id="a4eb3-106">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" > 
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a4eb3-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="a4eb3-107">Attributes and elements</span></span>

 <span data-ttu-id="a4eb3-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a4eb3-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a4eb3-109">屬性</span><span class="sxs-lookup"><span data-stu-id="a4eb3-109">Attributes</span></span>

|<span data-ttu-id="a4eb3-110">屬性</span><span class="sxs-lookup"><span data-stu-id="a4eb3-110">Attribute</span></span>|<span data-ttu-id="a4eb3-111">描述</span><span class="sxs-lookup"><span data-stu-id="a4eb3-111">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="a4eb3-112">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="a4eb3-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a4eb3-113">指定是否要啟用 .NET Framework 2.0 執行時間啟動原則，或使用 .NET Framework 4 啟用原則。</span><span class="sxs-lookup"><span data-stu-id="a4eb3-113">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="a4eb3-114">useLegacyV2RuntimeActivationPolicy 屬性</span><span class="sxs-lookup"><span data-stu-id="a4eb3-114">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="a4eb3-115">值</span><span class="sxs-lookup"><span data-stu-id="a4eb3-115">Value</span></span>|<span data-ttu-id="a4eb3-116">描述</span><span class="sxs-lookup"><span data-stu-id="a4eb3-116">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="a4eb3-117">為選擇的執行時間啟用 .NET Framework 2.0 執行時間啟動原則，這會將舊版的執行時間啟用技術（例如[CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)函式）系結至從設定檔案選擇的執行時間，而不是在 CLR 上將它們設為上限版本2.0。</span><span class="sxs-lookup"><span data-stu-id="a4eb3-117">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="a4eb3-118">因此，如果從設定檔中選擇 CLR 4 版（含）以後版本，則會使用所選擇的 CLR 版本載入以舊版 .NET Framework 建立的混合模式元件。</span><span class="sxs-lookup"><span data-stu-id="a4eb3-118">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="a4eb3-119">設定此值可防止 CLR 版本1.1 或 CLR 版本2.0 載入相同的進程中，有效地停用同進程並存功能。</span><span class="sxs-lookup"><span data-stu-id="a4eb3-119">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="a4eb3-120">使用 .NET Framework 4 和更新版本的預設啟用原則，這是為了允許舊版的執行時間啟用技術將 CLR 版本1.1 或2.0 載入至進程中。</span><span class="sxs-lookup"><span data-stu-id="a4eb3-120">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="a4eb3-121">設定此值可防止混合模式元件載入至 .NET Framework 4 或更新版本，除非它們是以 .NET Framework 4 或更新版本建立的。</span><span class="sxs-lookup"><span data-stu-id="a4eb3-121">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="a4eb3-122">此為預設值。</span><span class="sxs-lookup"><span data-stu-id="a4eb3-122">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a4eb3-123">子元素</span><span class="sxs-lookup"><span data-stu-id="a4eb3-123">Child elements</span></span>

|<span data-ttu-id="a4eb3-124">元素</span><span class="sxs-lookup"><span data-stu-id="a4eb3-124">Element</span></span>|<span data-ttu-id="a4eb3-125">描述</span><span class="sxs-lookup"><span data-stu-id="a4eb3-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a4eb3-126">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="a4eb3-126">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="a4eb3-127">指定應用程式只支援 Common Language Runtime 1.0 版。</span><span class="sxs-lookup"><span data-stu-id="a4eb3-127">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="a4eb3-128">使用執行階段版本 1.1 或更新版本建置的應用程式應該改用 **\<Supportedruntime>** 項目。</span><span class="sxs-lookup"><span data-stu-id="a4eb3-128">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="a4eb3-129">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="a4eb3-129">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="a4eb3-130">指定應用程式支援的通用語言執行平台版本。</span><span class="sxs-lookup"><span data-stu-id="a4eb3-130">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="a4eb3-131">父元素</span><span class="sxs-lookup"><span data-stu-id="a4eb3-131">Parent elements</span></span>

|<span data-ttu-id="a4eb3-132">元素</span><span class="sxs-lookup"><span data-stu-id="a4eb3-132">Element</span></span>|<span data-ttu-id="a4eb3-133">描述</span><span class="sxs-lookup"><span data-stu-id="a4eb3-133">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="a4eb3-134">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="a4eb3-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a4eb3-135">備註</span><span class="sxs-lookup"><span data-stu-id="a4eb3-135">Remarks</span></span>

 <span data-ttu-id="a4eb3-136">**\<Supportedruntime>** 項目應由使用 1.1 版或更新版本的執行階段所建置的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="a4eb3-136">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="a4eb3-137">為了僅支援1.0 版執行時間所建立的應用程式，必須使用 **@no__t 1requiredRuntime 的 >** 元素。</span><span class="sxs-lookup"><span data-stu-id="a4eb3-137">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="a4eb3-138">Microsoft Internet Explorer 中裝載之應用程式的啟動程式碼會忽略 **@no__t 1startup >** 元素及其子項目。</span><span class="sxs-lookup"><span data-stu-id="a4eb3-138">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="a4eb3-139">UseLegacyV2RuntimeActivationPolicy 屬性</span><span class="sxs-lookup"><span data-stu-id="a4eb3-139">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="a4eb3-140">如果您的應用程式使用舊版啟動路徑（例如[CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)函式），而您想要讓這些路徑啟用 CLR 的第4版（而不是舊版），或如果您的應用程式是以 .net 建立，這個屬性就很有用。Framework 4，但相依于以舊版 .NET Framework 建立的混合模式元件。</span><span class="sxs-lookup"><span data-stu-id="a4eb3-140">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="a4eb3-141">在這些情況下，請將屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a4eb3-141">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="a4eb3-142">將屬性設定為 `true` 會防止 CLR 版本1.1 或 CLR 2.0 版載入相同的進程中，有效地停用同進程並存功能（請參閱[COM Interop 的並存執行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))）。</span><span class="sxs-lookup"><span data-stu-id="a4eb3-142">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="a4eb3-143">範例</span><span class="sxs-lookup"><span data-stu-id="a4eb3-143">Example</span></span>

 <span data-ttu-id="a4eb3-144">下列範例顯示如何指定設定檔中的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="a4eb3-144">The following example shows how to specify the runtime version in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a4eb3-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a4eb3-145">See also</span></span>

- [<span data-ttu-id="a4eb3-146">啟動設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a4eb3-146">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a4eb3-147">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="a4eb3-147">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a4eb3-148">如何：設定應用程式以支援 .NET Framework 4 或更新版本</span><span class="sxs-lookup"><span data-stu-id="a4eb3-148">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="a4eb3-149">[COM Interop 的並存執行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="a4eb3-149">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="a4eb3-150">同處理序並存執行</span><span class="sxs-lookup"><span data-stu-id="a4eb3-150">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
