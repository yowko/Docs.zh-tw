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
ms.openlocfilehash: d98f8d672ed1de1a5065a0390dba29992bcc1b39
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634463"
---
# <a name="startup-element"></a><span data-ttu-id="61259-102">\<啟動 > 項目</span><span class="sxs-lookup"><span data-stu-id="61259-102">\<startup> element</span></span>

<span data-ttu-id="61259-103">指定 common language runtime 的啟動資訊。</span><span class="sxs-lookup"><span data-stu-id="61259-103">Specifies common language runtime startup information.</span></span>

 <span data-ttu-id="61259-104">\<configuration> \<startup></span><span class="sxs-lookup"><span data-stu-id="61259-104">\<configuration> \<startup></span></span>

## <a name="syntax"></a><span data-ttu-id="61259-105">語法</span><span class="sxs-lookup"><span data-stu-id="61259-105">Syntax</span></span>

```xml
<startup useLegacyV2RuntimeActivationPolicy="true|false" > 
</startup>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="61259-106">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="61259-106">Attributes and elements</span></span>

 <span data-ttu-id="61259-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="61259-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="61259-108">屬性</span><span class="sxs-lookup"><span data-stu-id="61259-108">Attributes</span></span>

|<span data-ttu-id="61259-109">屬性</span><span class="sxs-lookup"><span data-stu-id="61259-109">Attribute</span></span>|<span data-ttu-id="61259-110">描述</span><span class="sxs-lookup"><span data-stu-id="61259-110">Description</span></span>|
|---------------|-----------------|
|`useLegacyV2RuntimeActivationPolicy`|<span data-ttu-id="61259-111">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="61259-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="61259-112">指定是否要啟用[!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)]執行階段啟用原則，或使用[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]啟用原則。</span><span class="sxs-lookup"><span data-stu-id="61259-112">Specifies whether to enable the [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy or to use the [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] activation policy.</span></span>|

## <a name="uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="61259-113">useLegacyV2RuntimeActivationPolicy 屬性</span><span class="sxs-lookup"><span data-stu-id="61259-113">useLegacyV2RuntimeActivationPolicy attribute</span></span>

|<span data-ttu-id="61259-114">值</span><span class="sxs-lookup"><span data-stu-id="61259-114">Value</span></span>|<span data-ttu-id="61259-115">描述</span><span class="sxs-lookup"><span data-stu-id="61259-115">Description</span></span>|
|-----------|-----------------|
|`true`|<span data-ttu-id="61259-116">啟用[!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)]執行階段啟用原則，針對所選的執行階段，也就是繫結舊版執行階段啟用技術 (例如[CorBindToRuntimeEx 函式](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) 至執行階段從組態檔，而不是選擇在 CLR 2.0 版將達到其上限。</span><span class="sxs-lookup"><span data-stu-id="61259-116">Enable [!INCLUDE[dnprdnext](../../../../../includes/dnprdnext-md.md)] runtime activation policy for the chosen runtime, which is to bind legacy runtime activation techniques (such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)) to the runtime chosen from the configuration file instead of capping them at CLR version 2.0.</span></span> <span data-ttu-id="61259-117">因此，如果從組態檔中選擇 CLR 版本 4 或更新版本，則建立與舊版.NET Framework 的混合模式組件會載入與所選的 CLR 版本。</span><span class="sxs-lookup"><span data-stu-id="61259-117">Thus, if CLR version 4 or later is chosen from the configuration file, mixed-mode assemblies created with earlier versions of the .NET Framework are loaded with the chosen CLR version.</span></span> <span data-ttu-id="61259-118">將此值設定防止 CLR 1.1 版或 CLR 2.0 版載入到相同的程序，並有效地停用內含式並排顯示功能。</span><span class="sxs-lookup"><span data-stu-id="61259-118">Setting this value prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature.</span></span>|
|`false`|<span data-ttu-id="61259-119">使用預設的啟用原則，如[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]和更新版本中，也就是允許舊版執行階段載入處理序中的 CLR 1.1 或 2.0 版的啟用技術。</span><span class="sxs-lookup"><span data-stu-id="61259-119">Use the default activation policy for the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] and later, which is to allow legacy runtime activation techniques to load CLR version 1.1 or 2.0 into the process.</span></span> <span data-ttu-id="61259-120">將此值可防止混合模式組件載入到.NET Framework 4 或更新版本，除非它們建置在.NET Framework 4 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="61259-120">Setting this value prevents mixed-mode assemblies from loading into the .NET Framework 4 or later unless they were built with the .NET Framework 4 or later.</span></span> <span data-ttu-id="61259-121">預設值為這個值。</span><span class="sxs-lookup"><span data-stu-id="61259-121">This value is the default.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="61259-122">子元素</span><span class="sxs-lookup"><span data-stu-id="61259-122">Child elements</span></span>

|<span data-ttu-id="61259-123">項目</span><span class="sxs-lookup"><span data-stu-id="61259-123">Element</span></span>|<span data-ttu-id="61259-124">描述</span><span class="sxs-lookup"><span data-stu-id="61259-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="61259-125">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="61259-125">\<requiredRuntime></span></span>](requiredruntime-element.md)|<span data-ttu-id="61259-126">指定應用程式只支援 Common Language Runtime 1.0 版。</span><span class="sxs-lookup"><span data-stu-id="61259-126">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="61259-127">使用執行階段版本 1.1 或更新版本建置的應用程式應該改用 **\<Supportedruntime> >** 項目。</span><span class="sxs-lookup"><span data-stu-id="61259-127">Applications built with runtime version 1.1 or later should use the **\<supportedRuntime>** element.</span></span>|
|[<span data-ttu-id="61259-128">\<supportedRuntime></span><span class="sxs-lookup"><span data-stu-id="61259-128">\<supportedRuntime></span></span>](supportedruntime-element.md)|<span data-ttu-id="61259-129">指定應用程式支援的通用語言執行平台版本。</span><span class="sxs-lookup"><span data-stu-id="61259-129">Specifies which versions of the common language runtime the application supports.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="61259-130">父元素</span><span class="sxs-lookup"><span data-stu-id="61259-130">Parent elements</span></span>

|<span data-ttu-id="61259-131">元素</span><span class="sxs-lookup"><span data-stu-id="61259-131">Element</span></span>|<span data-ttu-id="61259-132">描述</span><span class="sxs-lookup"><span data-stu-id="61259-132">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="61259-133">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="61259-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="remarks"></a><span data-ttu-id="61259-134">備註</span><span class="sxs-lookup"><span data-stu-id="61259-134">Remarks</span></span>

 <span data-ttu-id="61259-135"> *\*\<Supportedruntime> >** 項目應由使用 1.1 版或更新版本的執行階段所建置的所有應用程式。</span><span class="sxs-lookup"><span data-stu-id="61259-135">The **\<supportedRuntime>** element should be used by all applications built using version 1.1 or later of the runtime.</span></span> <span data-ttu-id="61259-136">若要只支援 1.0 版的執行階段所建置的應用程式必須使用 **\<Requiredruntime> >** 項目。</span><span class="sxs-lookup"><span data-stu-id="61259-136">Applications built to support only version 1.0 of the runtime must use the **\<requiredRuntime>** element.</span></span>

 <span data-ttu-id="61259-137">在 Microsoft Internet Explorer 中裝載的應用程式的啟動程式碼會忽略**\<啟動 >** 項目和其子項目。</span><span class="sxs-lookup"><span data-stu-id="61259-137">The startup code for an application hosted in Microsoft Internet Explorer ignores the **\<startup>** element and its child elements.</span></span>

## <a name="the-uselegacyv2runtimeactivationpolicy-attribute"></a><span data-ttu-id="61259-138">UseLegacyV2RuntimeActivationPolicy 屬性</span><span class="sxs-lookup"><span data-stu-id="61259-138">The useLegacyV2RuntimeActivationPolicy attribute</span></span>

 <span data-ttu-id="61259-139">此屬性才有用，如果您的應用程式使用舊版啟用路徑，例如[CorBindToRuntimeEx 函式](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md)，和您想要這些路徑來啟動第 4 版的 clr，而不是較早的版本，或如果您的應用程式使用建置[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]但有使用舊版.NET Framework 所建置的混合模式組件中的 相依性。</span><span class="sxs-lookup"><span data-stu-id="61259-139">This attribute is useful if your application uses legacy activation paths, such as the [CorBindToRuntimeEx function](../../../unmanaged-api/hosting/corbindtoruntimeex-function.md), and you want those paths to activate version 4 of the CLR instead of an earlier version, or if your application is built with the [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] but has a dependency on a mixed-mode assembly built with an earlier version of the .NET Framework.</span></span> <span data-ttu-id="61259-140">在這些情況下，將屬性設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="61259-140">In those scenarios, set the attribute to `true`.</span></span>

> [!NOTE]
> <span data-ttu-id="61259-141">將屬性設定為`true`載入至相同的程序，並有效地停用內含式並排顯示功能可防止 CLR 1.1 版或 CLR 2.0 版 (請參閱 < [COM interop 的並排顯示執行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100)))。</span><span class="sxs-lookup"><span data-stu-id="61259-141">Setting the attribute to `true` prevents CLR version 1.1 or CLR version 2.0 from loading into the same process, effectively disabling the in-process side-by-side feature (see [Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))).</span></span>

## <a name="example"></a><span data-ttu-id="61259-142">範例</span><span class="sxs-lookup"><span data-stu-id="61259-142">Example</span></span>

 <span data-ttu-id="61259-143">下列範例示範如何在組態檔中指定的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="61259-143">The following example shows how to specify the runtime version in a configuration file.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="61259-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61259-144">See also</span></span>

- [<span data-ttu-id="61259-145">啟動設定結構描述</span><span class="sxs-lookup"><span data-stu-id="61259-145">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="61259-146">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="61259-146">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="61259-147">如何：設定應用程式以支援 .NET Framework 4 或更新版本</span><span class="sxs-lookup"><span data-stu-id="61259-147">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
- <span data-ttu-id="61259-148">[COM interop 的並存執行](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="61259-148">[Side-by-Side Execution for COM Interop](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/8t8td04t(v=vs.100))</span></span>
- [<span data-ttu-id="61259-149">同處理序並存執行</span><span class="sxs-lookup"><span data-stu-id="61259-149">In-Process Side-by-Side Execution</span></span>](../../../deployment/in-process-side-by-side-execution.md)
