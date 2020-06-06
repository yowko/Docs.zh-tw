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
ms.openlocfilehash: e936c069275bfa9f7ac81ef1c6fc6228828182a8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79153723"
---
# <a name="startup-element"></a><span data-ttu-id="7b08c-102">\<startup> 項目</span><span class="sxs-lookup"><span data-stu-id="7b08c-102">\<startup> element</span></span>

<span data-ttu-id="7b08c-103">指定 common language runtime 啟動資訊。</span><span class="sxs-lookup"><span data-stu-id="7b08c-103">Specifies common language runtime startup information.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;**\<startup>**  

## <a name="syntax"></a><span data-ttu-id="7b08c-104">語法</span><span class="sxs-lookup"><span data-stu-id="7b08c-104">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" >
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7b08c-105">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="7b08c-105">Attributes and elements</span></span>

 <span data-ttu-id="7b08c-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="7b08c-106">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="7b08c-107">屬性</span><span class="sxs-lookup"><span data-stu-id="7b08c-107">Attributes</span></span>

|<span data-ttu-id="7b08c-108">屬性</span><span class="sxs-lookup"><span data-stu-id="7b08c-108">Attribute</span></span>|<span data-ttu-id="7b08c-109">描述</span><span class="sxs-lookup"><span data-stu-id="7b08c-109">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="7b08c-110">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="7b08c-110">Optional attribute.</span></span><br /><br /> <span data-ttu-id="7b08c-111">指定是否要啟用 .NET Framework 2.0 執行時間啟動原則，或使用 .NET Framework 4 啟用原則。</span><span class="sxs-lookup"><span data-stu-id="7b08c-111">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="7b08c-112">useLegacyV2RuntimeActivationPolicy 屬性</span><span class="sxs-lookup"><span data-stu-id="7b08c-112">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="7b08c-113">值</span><span class="sxs-lookup"><span data-stu-id="7b08c-113">Value</span></span>|<span data-ttu-id="7b08c-114">描述</span><span class="sxs-lookup"><span data-stu-id="7b08c-114">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="7b08c-115">啟用所選執行時間的 .NET Framework 2.0 執行時間啟動原則，這是將舊版執行時間啟用技術（例如[CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)函式）系結至從設定檔案選擇的執行時間，而不是在 CLR 2.0 版上加以上限。</span><span class="sxs-lookup"><span data-stu-id="7b08c-115">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="7b08c-116">因此，如果從設定檔中選擇 CLR 4 版（含）以後版本，則會使用所選擇的 CLR 版本載入以舊版 .NET Framework 建立的混合模式元件。</span><span class="sxs-lookup"><span data-stu-id="7b08c-116">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="7b08c-117">設定此值可防止 CLR 版本1.1 或 CLR 版本2.0 載入相同的進程中，有效地停用同進程並存功能。</span><span class="sxs-lookup"><span data-stu-id="7b08c-117">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="7b08c-118">使用 .NET Framework 4 和更新版本的預設啟用原則，這是為了允許舊版的執行時間啟用技術將 CLR 版本1.1 或2.0 載入至進程中。</span><span class="sxs-lookup"><span data-stu-id="7b08c-118">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="7b08c-119">設定此值可防止混合模式元件載入至 .NET Framework 4 或更新版本，除非它們是以 .NET Framework 4 或更新版本建立的。</span><span class="sxs-lookup"><span data-stu-id="7b08c-119">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="7b08c-120">此值為預設。</span><span class="sxs-lookup"><span data-stu-id="7b08c-120">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="7b08c-121">子元素</span><span class="sxs-lookup"><span data-stu-id="7b08c-121">Child elements</span></span>

|<span data-ttu-id="7b08c-122">元素</span><span class="sxs-lookup"><span data-stu-id="7b08c-122">Element</span></span>|<span data-ttu-id="7b08c-123">描述</span><span class="sxs-lookup"><span data-stu-id="7b08c-123">Description</span></span>|
|-------------|-----------------|
|[\<requiredRuntime>](requiredruntime-element.md)|<span data-ttu-id="7b08c-124">指定應用程式只支援 Common Language Runtime 1.0 版。</span><span class="sxs-lookup"><span data-stu-id="7b08c-124">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="7b08c-125">以執行階段版本1.1 或更新版本建立的應用程式應該使用 **\<supportedRuntime>** 元素。</span><span class="sxs-lookup"><span data-stu-id="7b08c-125">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[\<supportedRuntime>](supportedruntime-element.md)|<span data-ttu-id="7b08c-126">指定應用程式支援的通用語言執行平台版本。</span><span class="sxs-lookup"><span data-stu-id="7b08c-126">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7b08c-127">父元素</span><span class="sxs-lookup"><span data-stu-id="7b08c-127">Parent elements</span></span>

|<span data-ttu-id="7b08c-128">元素</span><span class="sxs-lookup"><span data-stu-id="7b08c-128">Element</span></span>|<span data-ttu-id="7b08c-129">描述</span><span class="sxs-lookup"><span data-stu-id="7b08c-129">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="7b08c-130">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="7b08c-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7b08c-131">備註</span><span class="sxs-lookup"><span data-stu-id="7b08c-131">Remarks</span></span>

 <span data-ttu-id="7b08c-132">專案 **\<supportedRuntime>** 應該由使用1.1 版或更新版本的執行時間所建立的所有應用程式所使用。</span><span class="sxs-lookup"><span data-stu-id="7b08c-132">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="7b08c-133">為了僅支援1.0 版執行時間所建立的應用程式，必須使用專案 **\<requiredRuntime>** 。</span><span class="sxs-lookup"><span data-stu-id="7b08c-133">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="7b08c-134">Microsoft Internet Explorer 中裝載之應用程式的啟動程式碼會忽略 **\<startup>** 元素及其子專案。</span><span class="sxs-lookup"><span data-stu-id="7b08c-134">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="7b08c-135">UseLegacyV2RuntimeActivationPolicy 屬性</span><span class="sxs-lookup"><span data-stu-id="7b08c-135">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="7b08c-136">如果您的應用程式使用舊版啟用路徑（例如[CorBindToRuntimeEx](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)函式），而您想要讓這些路徑啟動 CLR 的第4版（而不是舊版），或如果您的應用程式是以 .NET Framework 4 建立，但相依于使用舊版 .NET Framework 所建立的混合模式元件，這個屬性就很有用。</span><span class="sxs-lookup"><span data-stu-id="7b08c-136">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="7b08c-137">在這些情況下，請將屬性設定為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="7b08c-137">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="7b08c-138">將屬性設為 `true` 可防止 clr 版本1.1 或 clr 版本2.0 載入相同的進程中，實際上會停用同進程並存功能（請參閱[COM Interop 的並存執行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))）。</span><span class="sxs-lookup"><span data-stu-id="7b08c-138">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="7b08c-139">範例</span><span class="sxs-lookup"><span data-stu-id="7b08c-139">Example</span></span>

 <span data-ttu-id="7b08c-140">下列範例顯示如何指定設定檔中的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="7b08c-140">The following example shows how to specify the runtime version in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7b08c-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b08c-141">See also</span></span>

- [<span data-ttu-id="7b08c-142">啟動設定結構描述</span><span class="sxs-lookup"><span data-stu-id="7b08c-142">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="7b08c-143">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="7b08c-143">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="7b08c-144">如何：將應用程式設定為支援 .NET Framework 4 或更新版本</span><span class="sxs-lookup"><span data-stu-id="7b08c-144">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="7b08c-145">[COM Interop 的並存執行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="7b08c-145">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="7b08c-146">同處理序並存執行</span><span class="sxs-lookup"><span data-stu-id="7b08c-146">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
