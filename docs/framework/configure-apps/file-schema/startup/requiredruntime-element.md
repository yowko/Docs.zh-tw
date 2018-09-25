---
title: '&lt;Requiredruntime>&gt;項目'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requiredRuntime
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/startup/requiredRuntime
helpviewer_keywords:
- requiredRuntime element
- <requiredRuntime> element
- container tags, <requiredRuntime> element
ms.assetid: 9fa1639e-beb8-43be-b7a4-12f7b229c34b
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 7cb5e29f3d7fc1faffdba01a5322f1883fca8af0
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47069695"
---
# <a name="ltrequiredruntimegt-element"></a><span data-ttu-id="0dc8d-102">&lt;Requiredruntime>&gt;項目</span><span class="sxs-lookup"><span data-stu-id="0dc8d-102">&lt;requiredRuntime&gt; Element</span></span>
<span data-ttu-id="0dc8d-103">指定應用程式只支援 Common Language Runtime 1.0 版。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-103">Specifies that the application supports only version 1.0 of the common language runtime.</span></span> <span data-ttu-id="0dc8d-104">這個項目已被取代，無法再使用。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-104">This element is deprecated and should no longer be used.</span></span> <span data-ttu-id="0dc8d-105">[ `supportedRuntime` ](supportedruntime-element.md)應該改為使用項目。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-105">The [`supportedRuntime`](supportedruntime-element.md) element should be used instead.</span></span>
  
 <span data-ttu-id="0dc8d-106">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0dc8d-106">\<configuration></span></span>  
<span data-ttu-id="0dc8d-107">\<啟動 ></span><span class="sxs-lookup"><span data-stu-id="0dc8d-107">\<startup></span></span>  
<span data-ttu-id="0dc8d-108">\<requiredRuntime></span><span class="sxs-lookup"><span data-stu-id="0dc8d-108">\<requiredRuntime></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dc8d-109">語法</span><span class="sxs-lookup"><span data-stu-id="0dc8d-109">Syntax</span></span>  
  
```xml  
   <requiredRuntime    
version="runtime version"  
safemode="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0dc8d-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0dc8d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0dc8d-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0dc8d-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0dc8d-112">Attributes</span></span>  
  
|<span data-ttu-id="0dc8d-113">屬性</span><span class="sxs-lookup"><span data-stu-id="0dc8d-113">Attribute</span></span>|<span data-ttu-id="0dc8d-114">描述</span><span class="sxs-lookup"><span data-stu-id="0dc8d-114">Description</span></span>|  
|---------------|-----------------|  
|`version`|<span data-ttu-id="0dc8d-115">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="0dc8d-116">字串值，指定這個應用程式支援的.NET framework 版本。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-116">A string value that specifies the version of the .NET Framework that this application supports.</span></span> <span data-ttu-id="0dc8d-117">字串值必須符合.NET Framework 安裝根下找到的目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-117">The string value must match the directory name found under the .NET Framework installation root.</span></span> <span data-ttu-id="0dc8d-118">未剖析的字串值的內容。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-118">The contents of the string value are not parsed.</span></span>|  
|`safemode`|<span data-ttu-id="0dc8d-119">選擇性屬性。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="0dc8d-120">指定是否要在執行階段啟始程式碼搜尋登錄，以判斷執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-120">Specifies whether the runtime startup code searches the registry to determine the runtime version.</span></span>|  
  
## <a name="safemode-attribute"></a><span data-ttu-id="0dc8d-121">安全模式屬性</span><span class="sxs-lookup"><span data-stu-id="0dc8d-121">safemode Attribute</span></span>  
  
|<span data-ttu-id="0dc8d-122">值</span><span class="sxs-lookup"><span data-stu-id="0dc8d-122">Value</span></span>|<span data-ttu-id="0dc8d-123">描述</span><span class="sxs-lookup"><span data-stu-id="0dc8d-123">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="0dc8d-124">執行階段啟始程式碼會尋找在登錄中。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-124">The runtime startup code looks in the registry.</span></span> <span data-ttu-id="0dc8d-125">這是預設值。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-125">This is the default value.</span></span>|  
|`true`|<span data-ttu-id="0dc8d-126">執行階段啟始程式碼不會在登錄中尋找。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-126">The runtime startup code does not look in the registry.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0dc8d-127">子元素</span><span class="sxs-lookup"><span data-stu-id="0dc8d-127">Child Elements</span></span>  
 <span data-ttu-id="0dc8d-128">無。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0dc8d-129">父項目</span><span class="sxs-lookup"><span data-stu-id="0dc8d-129">Parent Elements</span></span>  
  
|<span data-ttu-id="0dc8d-130">項目</span><span class="sxs-lookup"><span data-stu-id="0dc8d-130">Element</span></span>|<span data-ttu-id="0dc8d-131">描述</span><span class="sxs-lookup"><span data-stu-id="0dc8d-131">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="0dc8d-132">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-132">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`startup`|<span data-ttu-id="0dc8d-133">包含`<requiredRuntime>`項目。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-133">Contains the `<requiredRuntime>` element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0dc8d-134">備註</span><span class="sxs-lookup"><span data-stu-id="0dc8d-134">Remarks</span></span>  
 <span data-ttu-id="0dc8d-135">若要只支援 1.0 版的執行階段所建置的應用程式必須使用`<requiredRuntime>`項目。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-135">Applications built to support only version 1.0 of the runtime must use the `<requiredRuntime>` element.</span></span> <span data-ttu-id="0dc8d-136">使用 1.1 版或更新版本的執行階段所建置的應用程式必須使用`<supportedRuntime>`項目。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-136">Applications built using version 1.1 or later of the runtime must use the `<supportedRuntime>` element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0dc8d-137">如果您使用[CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)函數來指定組態檔，您必須使用`<requiredRuntime>`的執行階段的所有版本的項目。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-137">If you use the [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md) function to specify the configuration file, you must use the `<requiredRuntime>` element for all versions of the runtime.</span></span> <span data-ttu-id="0dc8d-138">`<supportedRuntime>`當您使用時，便會忽略元素[CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md)。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-138">The `<supportedRuntime>` element is ignored when you use [CorBindToRuntimeByCfg](../../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimebycfg-function.md).</span></span>  
  
 <span data-ttu-id="0dc8d-139">`version`屬性字串必須符合指定之版本的.NET framework 的安裝資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-139">The `version` attribute string must match the installation folder name for the specified version of the .NET Framework.</span></span> <span data-ttu-id="0dc8d-140">此字串無法加以解譯。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-140">This string is not interpreted.</span></span> <span data-ttu-id="0dc8d-141">如果執行階段啟始程式碼找不到相符的資料夾，則執行階段不會載入;啟動程式碼會顯示錯誤訊息，並結束。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-141">If the runtime startup code does not find a matching folder, the runtime is not loaded; the startup code shows an error message and quits.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0dc8d-142">在 Microsoft Internet Explorer 中裝載的應用程式的啟始程式碼會忽略`<requiredRuntime>`項目。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-142">The startup code for an application that is hosted in Microsoft Internet Explorer ignores the `<requiredRuntime>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0dc8d-143">範例</span><span class="sxs-lookup"><span data-stu-id="0dc8d-143">Example</span></span>  
 <span data-ttu-id="0dc8d-144">下列範例示範如何在組態檔中指定的執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="0dc8d-144">The following example shows how to specify the runtime version in a configuration file.</span></span>  
  
```xml  
<configuration>  
   <startup>  
      <requiredRuntime version="v1.0.3705" safemode="true"/>  
   </startup>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0dc8d-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0dc8d-145">See Also</span></span>  
 [<span data-ttu-id="0dc8d-146">啟動設定結構描述</span><span class="sxs-lookup"><span data-stu-id="0dc8d-146">Startup Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/startup/index.md)  
 [<span data-ttu-id="0dc8d-147">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="0dc8d-147">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="0dc8d-148">\<PaveOver> 指定要使用哪一個執行階段版本</span><span class="sxs-lookup"><span data-stu-id="0dc8d-148">\<PaveOver> Specifying Which Runtime Version to Use</span></span>](https://msdn.microsoft.com/library/c376208d-980d-42b4-865b-fbe0d9cc97c2)
