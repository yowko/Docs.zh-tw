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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153723"
---
# <a name="startup-element"></a><span data-ttu-id="c296a-102">\<啟動>元素</span><span class="sxs-lookup"><span data-stu-id="c296a-102">\<startup> element</span></span>

<span data-ttu-id="c296a-103">指定通用語言運行時啟動資訊。</span><span class="sxs-lookup"><span data-stu-id="c296a-103">Specifies common language runtime startup information.</span></span>

[<span data-ttu-id="c296a-104">**\<配置>**</span><span class="sxs-lookup"><span data-stu-id="c296a-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="c296a-105">&nbsp;&nbsp;**\<啟動>**</span><span class="sxs-lookup"><span data-stu-id="c296a-105">&nbsp;&nbsp;**\<startup>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="c296a-106">語法</span><span class="sxs-lookup"><span data-stu-id="c296a-106">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" >
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c296a-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="c296a-107">Attributes and elements</span></span>

 <span data-ttu-id="c296a-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c296a-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="c296a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="c296a-109">Attributes</span></span>

|<span data-ttu-id="c296a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c296a-110">Attribute</span></span>|<span data-ttu-id="c296a-111">描述</span><span class="sxs-lookup"><span data-stu-id="c296a-111">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="c296a-112">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="c296a-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="c296a-113">指定是啟用 .NET 框架 2.0 運行時啟動策略還是使用 .NET 框架 4 啟動策略。</span><span class="sxs-lookup"><span data-stu-id="c296a-113">Specifies whether to enable the .NET Framework 2.0 runtime activation policy or to use the .NET Framework 4 activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="c296a-114">使用傳統V2運行時啟動策略屬性</span><span class="sxs-lookup"><span data-stu-id="c296a-114">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="c296a-115">值</span><span class="sxs-lookup"><span data-stu-id="c296a-115">Value</span></span>|<span data-ttu-id="c296a-116">描述</span><span class="sxs-lookup"><span data-stu-id="c296a-116">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="c296a-117">為所選運行時啟用 .NET Framework 2.0 運行時啟動策略，即將舊式運行時啟動技術（如[CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)）綁定到從設定檔中選擇的運行時，而不是在 CLR 版本 2.0 上將其封頂。</span><span class="sxs-lookup"><span data-stu-id="c296a-117">Enable .NET Framework 2.0 runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="c296a-118">因此，如果從設定檔中選擇 CLR 版本 4 或更高版本，則使用早期版本的 .NET Framework 創建的混合模式程式集將載入所選 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="c296a-118">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="c296a-119">設置此值可防止 CLR 版本 1.1 或 CLR 版本 2.0 載入到同一進程中，從而有效地禁用進程內並排功能。</span><span class="sxs-lookup"><span data-stu-id="c296a-119">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="c296a-120">對 .NET 框架 4 及更高版本使用預設啟動策略，即允許舊式運行時啟動技術將 CLR 版本 1.1 或 2.0 載入到進程中。</span><span class="sxs-lookup"><span data-stu-id="c296a-120">Use the default activation policy for the .NET Framework 4 and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="c296a-121">設置此值可防止混合模式程式集載入到 .NET 框架 4 或更高版本，除非這些程式集是使用 .NET 框架 4 或更高版本構建的。</span><span class="sxs-lookup"><span data-stu-id="c296a-121">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="c296a-122">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="c296a-122">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="c296a-123">子元素</span><span class="sxs-lookup"><span data-stu-id="c296a-123">Child elements</span></span>

|<span data-ttu-id="c296a-124">元素</span><span class="sxs-lookup"><span data-stu-id="c296a-124">Element</span></span>|<span data-ttu-id="c296a-125">描述</span><span class="sxs-lookup"><span data-stu-id="c296a-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c296a-126">\<所需的運行時></span><span class="sxs-lookup"><span data-stu-id="c296a-126">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="c296a-127">指定應用程式只支援 Common Language Runtime 1.0 版。</span><span class="sxs-lookup"><span data-stu-id="c296a-127">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="c296a-128">使用執行階段版本 1.1 或更高版本構建的應用程式應使用**\<支援的 Runtime>** 元素。</span><span class="sxs-lookup"><span data-stu-id="c296a-128">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="c296a-129">\<支援的運行時></span><span class="sxs-lookup"><span data-stu-id="c296a-129">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="c296a-130">指定應用程式支援的通用語言執行平台版本。</span><span class="sxs-lookup"><span data-stu-id="c296a-130">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c296a-131">父元素</span><span class="sxs-lookup"><span data-stu-id="c296a-131">Parent elements</span></span>

|<span data-ttu-id="c296a-132">元素</span><span class="sxs-lookup"><span data-stu-id="c296a-132">Element</span></span>|<span data-ttu-id="c296a-133">描述</span><span class="sxs-lookup"><span data-stu-id="c296a-133">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="c296a-134">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="c296a-134">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c296a-135">備註</span><span class="sxs-lookup"><span data-stu-id="c296a-135">Remarks</span></span>

 <span data-ttu-id="c296a-136">\*\* \<支援的 Runtime>\*\* 元素應由使用執行階段版本 1.1 或更高版本構建的所有應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="c296a-136">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="c296a-137">為僅支援執行階段版本 1.0 而構建的應用程式必須使用**\<所需的 Runtime>** 元素。</span><span class="sxs-lookup"><span data-stu-id="c296a-137">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="c296a-138">Microsoft Internet Explorer 中託管的應用程式的啟動代碼忽略**\<啟動>** 元素及其子項目。</span><span class="sxs-lookup"><span data-stu-id="c296a-138">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="c296a-139">使用傳統V2運行時啟動策略屬性</span><span class="sxs-lookup"><span data-stu-id="c296a-139">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="c296a-140">如果應用程式使用舊版啟動路徑（如[CorBindToRuntimeEx 函數](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)），並且希望這些路徑啟動 CLR 的版本 4 而不是早期版本，或者應用程式是使用 .NET 框架 4 構建的，但依賴于使用早期版本的 .NET Framework 構建的混合模式程式集，則此屬性非常有用。</span><span class="sxs-lookup"><span data-stu-id="c296a-140">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the .NET Framework 4 but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="c296a-141">在這些情況下，將屬性設置為`true`。</span><span class="sxs-lookup"><span data-stu-id="c296a-141">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="c296a-142">設置屬性以防止`true`CLR 版本 1.1 或 CLR 版本 2.0 載入到同一進程中，從而有效地禁用進程內並行功能（請參閱[COM 內部操作的並存執行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))）。</span><span class="sxs-lookup"><span data-stu-id="c296a-142">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="c296a-143">範例</span><span class="sxs-lookup"><span data-stu-id="c296a-143">Example</span></span>

 <span data-ttu-id="c296a-144">下面的示例演示如何在設定檔中指定執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="c296a-144">The following example shows how to specify the runtime version in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c296a-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c296a-145">See also</span></span>

- [<span data-ttu-id="c296a-146">啟動設置架構</span><span class="sxs-lookup"><span data-stu-id="c296a-146">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="c296a-147">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="c296a-147">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="c296a-148">如何：將應用配置為支援 .NET 框架 4 或更高版本</span><span class="sxs-lookup"><span data-stu-id="c296a-148">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="c296a-149">[COM Interop 的並存執行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="c296a-149">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="c296a-150">同處理序並存執行</span><span class="sxs-lookup"><span data-stu-id="c296a-150">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
