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
ms.openlocfilehash: 5e528a8b81fa3d9abc4f345d18f01e33f483a4a9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254726"
---
# <a name="requiredruntime-element"></a><span data-ttu-id="b6d70-102">\<Requiredruntime> > 項目</span><span class="sxs-lookup"><span data-stu-id="b6d70-102">\<requiredRuntime> element</span></span>

<span data-ttu-id="b6d70-103">指定應用程式只支援 Common Language Runtime 1.0 版。</span><span class="sxs-lookup"><span data-stu-id="b6d70-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="b6d70-104">這個項目已被取代，無法再使用。</span><span class="sxs-lookup"><span data-stu-id="b6d70-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="b6d70-105">[ `supportedRuntime` ](supportedruntime-element.md)應該改為使用項目。</span><span class="sxs-lookup"><span data-stu-id="b6d70-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>

<span data-ttu-id="b6d70-106">\<configuration> \<startup> \<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="b6d70-106">\<configuration> \<startup> \<requiredRuntime></span></span>

## <a name="syntax"></a><span data-ttu-id="b6d70-107">語法</span><span class="sxs-lookup"><span data-stu-id="b6d70-107">Syntax</span></span>

```xml
   <requiredRuntime  
version="runtime version"
safemode="true|false"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b6d70-108">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="b6d70-108">Attributes and elements</span></span>

<span data-ttu-id="b6d70-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b6d70-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="b6d70-110">屬性</span><span class="sxs-lookup"><span data-stu-id="b6d70-110">Attributes</span></span>

|<span data-ttu-id="b6d70-111">屬性</span><span class="sxs-lookup"><span data-stu-id="b6d70-111">Attribute</span></span>|<span data-ttu-id="b6d70-112">描述</span><span class="sxs-lookup"><span data-stu-id="b6d70-112">Description</span></span>|
|---------------|-----------------|
|`version`|<span data-ttu-id="b6d70-113">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="b6d70-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b6d70-114">字串值，指定這個應用程式支援的.NET framework 版本。</span><span class="sxs-lookup"><span data-stu-id="b6d70-114">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="b6d70-115">字串值必須符合.NET Framework 安裝根下找到的目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="b6d70-115">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="b6d70-116">未剖析的字串值的內容。</span><span class="sxs-lookup"><span data-stu-id="b6d70-116">The contents of the string value are not parsed.</span></span>|
|`safemode`|<span data-ttu-id="b6d70-117">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="b6d70-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b6d70-118">指定是否要在執行階段啟始程式碼搜尋登錄，以判斷執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="b6d70-118">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|

## <a name="safemode-attribute"></a><span data-ttu-id="b6d70-119">安全模式屬性</span><span class="sxs-lookup"><span data-stu-id="b6d70-119">safemode attribute</span></span>

|<span data-ttu-id="b6d70-120">值</span><span class="sxs-lookup"><span data-stu-id="b6d70-120">Value</span></span>|<span data-ttu-id="b6d70-121">描述</span><span class="sxs-lookup"><span data-stu-id="b6d70-121">Description</span></span>|
|-----------|-----------------|
|`false`|<span data-ttu-id="b6d70-122">執行階段啟始程式碼會尋找在登錄中。</span><span class="sxs-lookup"><span data-stu-id="b6d70-122">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="b6d70-123">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="b6d70-123">This is the default value.</span></span>|
|`true`|<span data-ttu-id="b6d70-124">執行階段啟始程式碼不會在登錄中尋找。</span><span class="sxs-lookup"><span data-stu-id="b6d70-124">The runtime startup code does not look in the registry.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="b6d70-125">子元素</span><span class="sxs-lookup"><span data-stu-id="b6d70-125">Child elements</span></span>

<span data-ttu-id="b6d70-126">無。</span><span class="sxs-lookup"><span data-stu-id="b6d70-126">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b6d70-127">父元素</span><span class="sxs-lookup"><span data-stu-id="b6d70-127">Parent elements</span></span>

|<span data-ttu-id="b6d70-128">元素</span><span class="sxs-lookup"><span data-stu-id="b6d70-128">Element</span></span>|<span data-ttu-id="b6d70-129">描述</span><span class="sxs-lookup"><span data-stu-id="b6d70-129">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="b6d70-130">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="b6d70-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`startup`|<span data-ttu-id="b6d70-131">包含`<requiredRuntime>`項目。</span><span class="sxs-lookup"><span data-stu-id="b6d70-131">Contains the `<requiredRuntime>` element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b6d70-132">備註</span><span class="sxs-lookup"><span data-stu-id="b6d70-132">Remarks</span></span>
 <span data-ttu-id="b6d70-133">若要只支援 1.0 版的執行階段所建置的應用程式必須使用`<requiredRuntime>`項目。</span><span class="sxs-lookup"><span data-stu-id="b6d70-133">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="b6d70-134">使用 1.1 版或更新版本的執行階段所建置的應用程式必須使用`<supportedRuntime>`項目。</span><span class="sxs-lookup"><span data-stu-id="b6d70-134">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>

> [!NOTE]
> <span data-ttu-id="b6d70-135">如果您使用[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)函數來指定組態檔，您必須使用`<requiredRuntime>`的執行階段的所有版本的項目。</span><span class="sxs-lookup"><span data-stu-id="b6d70-135">If you use the [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="b6d70-136">`<supportedRuntime>`當您使用時，便會忽略元素[CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md)。</span><span class="sxs-lookup"><span data-stu-id="b6d70-136">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>

 <span data-ttu-id="b6d70-137">`version`屬性字串必須符合指定之版本的.NET framework 的安裝資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="b6d70-137">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="b6d70-138">此字串無法加以解譯。</span><span class="sxs-lookup"><span data-stu-id="b6d70-138">This string is not interpreted.</span></span> <span data-ttu-id="b6d70-139">如果執行階段啟始程式碼找不到相符的資料夾，則執行階段不會載入;啟動程式碼會顯示錯誤訊息，並結束。</span><span class="sxs-lookup"><span data-stu-id="b6d70-139">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>

> [!NOTE]
> <span data-ttu-id="b6d70-140">在 Microsoft Internet Explorer 中裝載的應用程式的啟始程式碼會忽略`<requiredRuntime>`項目。</span><span class="sxs-lookup"><span data-stu-id="b6d70-140">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>

## <a name="example"></a><span data-ttu-id="b6d70-141">範例</span><span class="sxs-lookup"><span data-stu-id="b6d70-141">Example</span></span>

<span data-ttu-id="b6d70-142">下列範例示範如何在組態檔中指定的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="b6d70-142">The following example shows how to specify the runtime version in a configuration file.</span></span>

```xml
<configuration>
   <startup>
      <requiredRuntime version="v1.0.3705" safemode="true"/>
   </startup>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="b6d70-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b6d70-143">See also</span></span>

- [<span data-ttu-id="b6d70-144">啟動設定結構描述</span><span class="sxs-lookup"><span data-stu-id="b6d70-144">Startup Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b6d70-145">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="b6d70-145">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="b6d70-146">如何：設定應用程式以支援 .NET Framework 4 或更新版本</span><span class="sxs-lookup"><span data-stu-id="b6d70-146">How to: Configure an app to support .NET Framework 4 or later versions</span></span>](../../../migration-guide/how-to-configure-an-app-to-support-net-framework-4-or-4-5.md)