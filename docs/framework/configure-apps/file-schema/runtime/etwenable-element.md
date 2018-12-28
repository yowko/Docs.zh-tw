---
title: '&lt;etwEnable&gt;項目'
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6ea2f8a32a18dfce6be54ce52ce8fef4abf92ce
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610771"
---
# <a name="ltetwenablegt-element"></a><span data-ttu-id="81f98-102">&lt;etwEnable&gt;項目</span><span class="sxs-lookup"><span data-stu-id="81f98-102">&lt;etwEnable&gt; Element</span></span>
<span data-ttu-id="81f98-103">指定是否為通用語言執行平台事件啟用 Windows 事件追蹤 (ETW)。</span><span class="sxs-lookup"><span data-stu-id="81f98-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
 <span data-ttu-id="81f98-104">\<組態 > 項目</span><span class="sxs-lookup"><span data-stu-id="81f98-104">\<configuration> Element</span></span>  
<span data-ttu-id="81f98-105">\<執行階段 > 項目</span><span class="sxs-lookup"><span data-stu-id="81f98-105">\<runtime> Element</span></span>  
<span data-ttu-id="81f98-106">\<etwEnabled ></span><span class="sxs-lookup"><span data-stu-id="81f98-106">\<etwEnabled></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81f98-107">語法</span><span class="sxs-lookup"><span data-stu-id="81f98-107">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81f98-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="81f98-108">Attributes and Elements</span></span>  
 <span data-ttu-id="81f98-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="81f98-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81f98-110">屬性</span><span class="sxs-lookup"><span data-stu-id="81f98-110">Attributes</span></span>  
  
|<span data-ttu-id="81f98-111">屬性</span><span class="sxs-lookup"><span data-stu-id="81f98-111">Attribute</span></span>|<span data-ttu-id="81f98-112">描述</span><span class="sxs-lookup"><span data-stu-id="81f98-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81f98-113">enabled</span><span class="sxs-lookup"><span data-stu-id="81f98-113">enabled</span></span>|<span data-ttu-id="81f98-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="81f98-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="81f98-115">指定是否應該啟用 ETW。</span><span class="sxs-lookup"><span data-stu-id="81f98-115">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="81f98-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="81f98-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="81f98-117">值</span><span class="sxs-lookup"><span data-stu-id="81f98-117">Value</span></span>|<span data-ttu-id="81f98-118">描述</span><span class="sxs-lookup"><span data-stu-id="81f98-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="81f98-119">true</span><span class="sxs-lookup"><span data-stu-id="81f98-119">true</span></span>|<span data-ttu-id="81f98-120">啟用 ETW。</span><span class="sxs-lookup"><span data-stu-id="81f98-120">Enable ETW.</span></span> <span data-ttu-id="81f98-121">這是 Windows Vista 和 Windows Server 2008 作業系統的 Windows 開頭的版本的預設值。</span><span class="sxs-lookup"><span data-stu-id="81f98-121">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="81f98-122">False</span><span class="sxs-lookup"><span data-stu-id="81f98-122">false</span></span>|<span data-ttu-id="81f98-123">停用 ETW。</span><span class="sxs-lookup"><span data-stu-id="81f98-123">Disable ETW.</span></span> <span data-ttu-id="81f98-124">這是舊版 Windows 的預設值。</span><span class="sxs-lookup"><span data-stu-id="81f98-124">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81f98-125">子元素</span><span class="sxs-lookup"><span data-stu-id="81f98-125">Child Elements</span></span>  
 <span data-ttu-id="81f98-126">無。</span><span class="sxs-lookup"><span data-stu-id="81f98-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81f98-127">父項目</span><span class="sxs-lookup"><span data-stu-id="81f98-127">Parent Elements</span></span>  
  
|<span data-ttu-id="81f98-128">項目</span><span class="sxs-lookup"><span data-stu-id="81f98-128">Element</span></span>|<span data-ttu-id="81f98-129">描述</span><span class="sxs-lookup"><span data-stu-id="81f98-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="81f98-130">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="81f98-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="81f98-131">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="81f98-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81f98-132">備註</span><span class="sxs-lookup"><span data-stu-id="81f98-132">Remarks</span></span>  
 <span data-ttu-id="81f98-133">從 Windows Vista 開始，預設會啟用 ETW。</span><span class="sxs-lookup"><span data-stu-id="81f98-133">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="81f98-134">使用這個項目來停用 ETW 應用程式。</span><span class="sxs-lookup"><span data-stu-id="81f98-134">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="81f98-135">在舊版的 Windows 中，使用這個項目來啟用 ETW 應用程式。</span><span class="sxs-lookup"><span data-stu-id="81f98-135">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="81f98-136">ETW 可以啟用或停用全域的伺服器上使用登錄設定。</span><span class="sxs-lookup"><span data-stu-id="81f98-136">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="81f98-137">請參閱[控制.NET Framework 記錄](../../../../../docs/framework/performance/controlling-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="81f98-137">See [Controlling .NET Framework Logging](../../../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="81f98-138">範例</span><span class="sxs-lookup"><span data-stu-id="81f98-138">Example</span></span>  
 <span data-ttu-id="81f98-139">下列範例示範如何啟用應用程式的 ETW 追蹤。</span><span class="sxs-lookup"><span data-stu-id="81f98-139">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="81f98-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81f98-140">See Also</span></span>  
- [<span data-ttu-id="81f98-141">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="81f98-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
- [<span data-ttu-id="81f98-142">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="81f98-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
- [<span data-ttu-id="81f98-143">控制 .NET Framework 記錄</span><span class="sxs-lookup"><span data-stu-id="81f98-143">Controlling .NET Framework Logging</span></span>](../../../../../docs/framework/performance/controlling-logging.md)
