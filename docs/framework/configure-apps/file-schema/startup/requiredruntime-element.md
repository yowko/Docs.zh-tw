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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "71697492"
---
# <a name="requiredruntime-element"></a><span data-ttu-id="329c2-102">\<requiredRuntime> 項目</span><span class="sxs-lookup"><span data-stu-id="329c2-102">\<requiredRuntime> element</span></span>

<span data-ttu-id="329c2-103">指定應用程式只支援 Common Language Runtime 1.0 版。</span><span class="sxs-lookup"><span data-stu-id="329c2-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="329c2-104">此元素已被取代，不應該再使用。</span><span class="sxs-lookup"><span data-stu-id="329c2-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="329c2-105">[`supportedRuntime`](supportedruntime-element.md)應改為使用元素。</span><span class="sxs-lookup"><span data-stu-id="329c2-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<startup>**](startup-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requiredRuntime>**  

## <a name="syntax"></a><span data-ttu-id="329c2-106">語法</span><span class="sxs-lookup"><span data-stu-id="329c2-106">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="329c2-107">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="329c2-107">Attributes and elements</span></span>

<span data-ttu-id="329c2-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="329c2-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="329c2-109">屬性</span><span class="sxs-lookup"><span data-stu-id="329c2-109">Attributes</span></span>

|<span data-ttu-id="329c2-110">屬性</span><span class="sxs-lookup"><span data-stu-id="329c2-110">Attribute</span></span>|<span data-ttu-id="329c2-111">描述</span><span class="sxs-lookup"><span data-stu-id="329c2-111">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="329c2-112">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="329c2-112">Optional attribute.</span></span><br /><br /> <span data-ttu-id="329c2-113">字串值，指定此應用程式支援的 .NET Framework 版本。</span><span class="sxs-lookup"><span data-stu-id="329c2-113">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="329c2-114">字串值必須符合在 .NET Framework 安裝根目錄下找到的目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="329c2-114">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="329c2-115">不會剖析字串值的內容。</span><span class="sxs-lookup"><span data-stu-id="329c2-115">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="329c2-116">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="329c2-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="329c2-117">指定執行時間啟動程式碼是否會搜尋登錄，以判斷執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="329c2-117">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="329c2-118">安全模式屬性</span><span class="sxs-lookup"><span data-stu-id="329c2-118">safemode attribute</span></span>

|<span data-ttu-id="329c2-119">值</span><span class="sxs-lookup"><span data-stu-id="329c2-119">Value</span></span>|<span data-ttu-id="329c2-120">描述</span><span class="sxs-lookup"><span data-stu-id="329c2-120">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="329c2-121">執行時間啟動程式碼會在登錄中尋找。</span><span class="sxs-lookup"><span data-stu-id="329c2-121">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="329c2-122">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="329c2-122">This is the default value.</span></span>|
|`true`|<span data-ttu-id="329c2-123">執行時間啟動程式碼不會在登錄中尋找。</span><span class="sxs-lookup"><span data-stu-id="329c2-123">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="329c2-124">子元素</span><span class="sxs-lookup"><span data-stu-id="329c2-124">Child elements</span></span>

<span data-ttu-id="329c2-125">無。</span><span class="sxs-lookup"><span data-stu-id="329c2-125">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="329c2-126">父元素</span><span class="sxs-lookup"><span data-stu-id="329c2-126">Parent elements</span></span>

|<span data-ttu-id="329c2-127">元素</span><span class="sxs-lookup"><span data-stu-id="329c2-127">Element</span></span>|<span data-ttu-id="329c2-128">描述</span><span class="sxs-lookup"><span data-stu-id="329c2-128">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="329c2-129">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="329c2-129">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="329c2-130">包含 `<requiredRuntime>` 元素。</span><span class="sxs-lookup"><span data-stu-id="329c2-130">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="329c2-131">備註</span><span class="sxs-lookup"><span data-stu-id="329c2-131">Remarks</span></span>
 <span data-ttu-id="329c2-132">為了僅支援1.0 版執行時間所建立的應用程式，必須使用專案 `<requiredRuntime>` 。</span><span class="sxs-lookup"><span data-stu-id="329c2-132">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="329c2-133">使用1.1 版或更新版本的執行時間所建立的應用程式必須使用 `<supportedRuntime>` 元素。</span><span class="sxs-lookup"><span data-stu-id="329c2-133">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="329c2-134">如果您使用[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)函數來指定設定檔，您必須 `<requiredRuntime>` 針對所有版本的執行時間使用元素。</span><span class="sxs-lookup"><span data-stu-id="329c2-134">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="329c2-135">`<supportedRuntime>`當您使用[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)時，會忽略元素。</span><span class="sxs-lookup"><span data-stu-id="329c2-135">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="329c2-136">`version`屬性字串必須符合指定之 .NET Framework 版本的安裝資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="329c2-136">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="329c2-137">不會解讀此字串。</span><span class="sxs-lookup"><span data-stu-id="329c2-137">This string is not interpreted.</span></span> <span data-ttu-id="329c2-138">如果執行時間啟動程式碼找不到相符的資料夾，則不會載入執行時間;啟動程式碼會顯示錯誤訊息並結束。</span><span class="sxs-lookup"><span data-stu-id="329c2-138">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="329c2-139">Microsoft Internet Explorer 中裝載之應用程式的啟動代碼會忽略 `<requiredRuntime>` 元素。</span><span class="sxs-lookup"><span data-stu-id="329c2-139">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="329c2-140">範例</span><span class="sxs-lookup"><span data-stu-id="329c2-140">Example</span></span>

<span data-ttu-id="329c2-141">下列範例顯示如何指定設定檔中的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="329c2-141">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="329c2-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="329c2-142">See also</span></span>

- [<span data-ttu-id="329c2-143">啟動設定結構描述</span><span class="sxs-lookup"><span data-stu-id="329c2-143">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="329c2-144">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="329c2-144">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="329c2-145">如何：將應用程式設定為支援 .NET Framework 4 或更新版本</span><span class="sxs-lookup"><span data-stu-id="329c2-145">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)
