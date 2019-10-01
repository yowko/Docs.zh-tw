---
title: <requiredRuntime> 項目
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
ms.openlocfilehash: fe96673b95f48cb75d36662a680bf56a59363f9f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697492"
---
# <a name="requiredruntime-element"></a><span data-ttu-id="a3da3-102">@no__t 0requiredRuntime > 元素</span><span class="sxs-lookup"><span data-stu-id="a3da3-102">\<requiredRuntime> element</span></span>

<span data-ttu-id="a3da3-103">指定應用程式只支援 Common Language Runtime 1.0 版。</span><span class="sxs-lookup"><span data-stu-id="a3da3-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="a3da3-104">此元素已被取代，不應該再使用。</span><span class="sxs-lookup"><span data-stu-id="a3da3-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="a3da3-105">應該改為使用[@no__t 1](supportedruntime-element.md)元素。</span><span class="sxs-lookup"><span data-stu-id="a3da3-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

[<span data-ttu-id="a3da3-106"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="a3da3-106">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="a3da3-107">&nbsp; @ no__t-1[ **\<startup >** ](startup-element.md)</span><span class="sxs-lookup"><span data-stu-id="a3da3-107">&nbsp;&nbsp;[**\<startup>**](startup-element.md)</span></span>  
<span data-ttu-id="a3da3-108">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<requiredRuntime >**</span><span class="sxs-lookup"><span data-stu-id="a3da3-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<requiredRuntime>**</span></span>  

## <a name="syntax"></a><span data-ttu-id="a3da3-109">語法</span><span class="sxs-lookup"><span data-stu-id="a3da3-109">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a3da3-110">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="a3da3-110">Attributes and elements</span></span>

<span data-ttu-id="a3da3-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a3da3-111">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="a3da3-112">屬性</span><span class="sxs-lookup"><span data-stu-id="a3da3-112">Attributes</span></span>

|<span data-ttu-id="a3da3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="a3da3-113">Attribute</span></span>|<span data-ttu-id="a3da3-114">描述</span><span class="sxs-lookup"><span data-stu-id="a3da3-114">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="a3da3-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="a3da3-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a3da3-116">字串值，指定此應用程式支援的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="a3da3-116">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="a3da3-117">字串值必須符合在 .NET Framework 安裝根目錄下找到的目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="a3da3-117">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="a3da3-118">不會剖析字串值的內容。</span><span class="sxs-lookup"><span data-stu-id="a3da3-118">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="a3da3-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="a3da3-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a3da3-120">指定執行時間啟動程式碼是否會搜尋登錄，以判斷執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="a3da3-120">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="a3da3-121">安全模式屬性</span><span class="sxs-lookup"><span data-stu-id="a3da3-121">safemode attribute</span></span>

|<span data-ttu-id="a3da3-122">值</span><span class="sxs-lookup"><span data-stu-id="a3da3-122">Value</span></span>|<span data-ttu-id="a3da3-123">描述</span><span class="sxs-lookup"><span data-stu-id="a3da3-123">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="a3da3-124">執行時間啟動程式碼會在登錄中尋找。</span><span class="sxs-lookup"><span data-stu-id="a3da3-124">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="a3da3-125">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="a3da3-125">This is the default value.</span></span>|
|`true`|<span data-ttu-id="a3da3-126">執行時間啟動程式碼不會在登錄中尋找。</span><span class="sxs-lookup"><span data-stu-id="a3da3-126">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="a3da3-127">子元素</span><span class="sxs-lookup"><span data-stu-id="a3da3-127">Child elements</span></span>

<span data-ttu-id="a3da3-128">無。</span><span class="sxs-lookup"><span data-stu-id="a3da3-128">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a3da3-129">父元素</span><span class="sxs-lookup"><span data-stu-id="a3da3-129">Parent elements</span></span>

|<span data-ttu-id="a3da3-130">元素</span><span class="sxs-lookup"><span data-stu-id="a3da3-130">Element</span></span>|<span data-ttu-id="a3da3-131">描述</span><span class="sxs-lookup"><span data-stu-id="a3da3-131">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="a3da3-132">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="a3da3-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="a3da3-133">`<requiredRuntime>`包含元素。</span><span class="sxs-lookup"><span data-stu-id="a3da3-133">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="a3da3-134">備註</span><span class="sxs-lookup"><span data-stu-id="a3da3-134">Remarks</span></span>
 <span data-ttu-id="a3da3-135">為了僅支援1.0 版執行時間所建立的應用程式，必須使用 `<requiredRuntime>` 元素。</span><span class="sxs-lookup"><span data-stu-id="a3da3-135">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="a3da3-136">使用1.1 版或更新版本的執行時間所建立的應用程式必須使用 `<supportedRuntime>` 元素。</span><span class="sxs-lookup"><span data-stu-id="a3da3-136">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="a3da3-137">如果您使用[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)函數來指定設定檔，您必須針對所有版本的執行時間使用 `<requiredRuntime>` 元素。</span><span class="sxs-lookup"><span data-stu-id="a3da3-137">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="a3da3-138">當您使用[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)時，會忽略 `<supportedRuntime>` 元素。</span><span class="sxs-lookup"><span data-stu-id="a3da3-138">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="a3da3-139">@No__t-0 屬性字串必須符合指定之 .NET Framework 版本的安裝資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="a3da3-139">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="a3da3-140">不會解讀此字串。</span><span class="sxs-lookup"><span data-stu-id="a3da3-140">This string is not interpreted.</span></span> <span data-ttu-id="a3da3-141">如果執行時間啟動程式碼找不到相符的資料夾，則不會載入執行時間;啟動程式碼會顯示錯誤訊息並結束。</span><span class="sxs-lookup"><span data-stu-id="a3da3-141">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="a3da3-142">Microsoft Internet Explorer 中裝載之應用程式的啟動代碼會忽略 @no__t 0 元素。</span><span class="sxs-lookup"><span data-stu-id="a3da3-142">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="a3da3-143">範例</span><span class="sxs-lookup"><span data-stu-id="a3da3-143">Example</span></span>

<span data-ttu-id="a3da3-144">下列範例顯示如何指定設定檔中的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="a3da3-144">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="a3da3-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3da3-145">See also</span></span>

- [<span data-ttu-id="a3da3-146">啟動設定結構描述</span><span class="sxs-lookup"><span data-stu-id="a3da3-146">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a3da3-147">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="a3da3-147">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a3da3-148">如何：設定應用程式以支援 .NET Framework 4 或更新版本</span><span class="sxs-lookup"><span data-stu-id="a3da3-148">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
