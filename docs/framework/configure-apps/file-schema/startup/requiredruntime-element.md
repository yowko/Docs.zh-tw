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
ms.openlocfilehash: 19fa1561ca3acd845918d952379c5227121465b4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174065"
---
# <a name="requiredruntime-element"></a><span data-ttu-id="f7db6-102">\<requiredRuntime> 項目</span><span class="sxs-lookup"><span data-stu-id="f7db6-102">\<requiredRuntime> element</span></span>

<span data-ttu-id="f7db6-103">指定應用程式只支援 Common Language Runtime 1.0 版。</span><span class="sxs-lookup"><span data-stu-id="f7db6-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="f7db6-104">這個元素已被取代，不應該再使用。</span><span class="sxs-lookup"><span data-stu-id="f7db6-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="f7db6-105">[`supportedRuntime`](supportedruntime-element.md)應改為使用元素。</span><span class="sxs-lookup"><span data-stu-id="f7db6-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<startup>**](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requiredRuntime>**  

## <a name="syntax"></a><span data-ttu-id="f7db6-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f7db6-106">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f7db6-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="f7db6-107">Attributes and elements</span></span>

<span data-ttu-id="f7db6-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f7db6-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="f7db6-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f7db6-109">Attributes</span></span>

|<span data-ttu-id="f7db6-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f7db6-110">Attribute</span></span>|<span data-ttu-id="f7db6-111">描述</span><span class="sxs-lookup"><span data-stu-id="f7db6-111">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="f7db6-112">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f7db6-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f7db6-113">字串值，指定此應用程式支援的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="f7db6-113">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="f7db6-114">字串值必須符合 .NET Framework 安裝根目錄下找到的目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="f7db6-114">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="f7db6-115">不會剖析字串值的內容。</span><span class="sxs-lookup"><span data-stu-id="f7db6-115">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="f7db6-116">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="f7db6-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="f7db6-117">指定執行時間啟動程式碼是否會搜尋登錄以判斷執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="f7db6-117">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="f7db6-118">安全模式屬性</span><span class="sxs-lookup"><span data-stu-id="f7db6-118">safemode attribute</span></span>

|<span data-ttu-id="f7db6-119">值</span><span class="sxs-lookup"><span data-stu-id="f7db6-119">Value</span></span>|<span data-ttu-id="f7db6-120">描述</span><span class="sxs-lookup"><span data-stu-id="f7db6-120">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="f7db6-121">執行時間啟動程式碼會在登錄中尋找。</span><span class="sxs-lookup"><span data-stu-id="f7db6-121">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="f7db6-122">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="f7db6-122">This is the default value.</span></span>|
|`true`|<span data-ttu-id="f7db6-123">執行時間啟動程式碼不會在登錄中尋找。</span><span class="sxs-lookup"><span data-stu-id="f7db6-123">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="f7db6-124">子元素</span><span class="sxs-lookup"><span data-stu-id="f7db6-124">Child elements</span></span>

<span data-ttu-id="f7db6-125">無。</span><span class="sxs-lookup"><span data-stu-id="f7db6-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f7db6-126">父元素</span><span class="sxs-lookup"><span data-stu-id="f7db6-126">Parent elements</span></span>

|<span data-ttu-id="f7db6-127">項目</span><span class="sxs-lookup"><span data-stu-id="f7db6-127">Element</span></span>|<span data-ttu-id="f7db6-128">描述</span><span class="sxs-lookup"><span data-stu-id="f7db6-128">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="f7db6-129">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="f7db6-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="f7db6-130">包含 `<requiredRuntime>` 元素。</span><span class="sxs-lookup"><span data-stu-id="f7db6-130">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f7db6-131">備註</span><span class="sxs-lookup"><span data-stu-id="f7db6-131">Remarks</span></span>

 <span data-ttu-id="f7db6-132">為了僅支援1.0 版執行時間所建立的應用程式，必須使用 `<requiredRuntime>` 元素。</span><span class="sxs-lookup"><span data-stu-id="f7db6-132">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="f7db6-133">使用1.1 或更新版本執行時間所建立的應用程式必須使用 `<supportedRuntime>` 元素。</span><span class="sxs-lookup"><span data-stu-id="f7db6-133">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="f7db6-134">如果您使用 [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) 函式來指定設定檔，則必須將專案 `<requiredRuntime>` 用於所有版本的執行時間。</span><span class="sxs-lookup"><span data-stu-id="f7db6-134">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="f7db6-135">`<supportedRuntime>`當您使用[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)時，會忽略元素。</span><span class="sxs-lookup"><span data-stu-id="f7db6-135">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="f7db6-136">`version`屬性字串必須符合指定 .NET Framework 版本的安裝資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="f7db6-136">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="f7db6-137">不會解讀這個字串。</span><span class="sxs-lookup"><span data-stu-id="f7db6-137">This string is not interpreted.</span></span> <span data-ttu-id="f7db6-138">如果執行時間啟動程式碼找不到相符的資料夾，則不會載入執行時間;啟始程式碼會顯示錯誤訊息並結束。</span><span class="sxs-lookup"><span data-stu-id="f7db6-138">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="f7db6-139">裝載于 Microsoft Internet Explorer 的應用程式啟動程式碼會忽略 `<requiredRuntime>` 元素。</span><span class="sxs-lookup"><span data-stu-id="f7db6-139">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="f7db6-140">範例</span><span class="sxs-lookup"><span data-stu-id="f7db6-140">Example</span></span>

<span data-ttu-id="f7db6-141">下列範例顯示如何在設定檔中指定執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="f7db6-141">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="f7db6-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7db6-142">See also</span></span>

- [<span data-ttu-id="f7db6-143">啟動設定架構</span><span class="sxs-lookup"><span data-stu-id="f7db6-143">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="f7db6-144">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="f7db6-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="f7db6-145">如何：設定應用程式以支援 .NET Framework 4 或更新版本</span><span class="sxs-lookup"><span data-stu-id="f7db6-145">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
