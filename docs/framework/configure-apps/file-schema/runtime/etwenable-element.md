---
title: "&lt;etwEnable&gt;項目"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b36c52338754df0f4fd3c963848e36afeb140501
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltetwenablegt-element"></a><span data-ttu-id="3c130-102">&lt;etwEnable&gt;項目</span><span class="sxs-lookup"><span data-stu-id="3c130-102">&lt;etwEnable&gt; Element</span></span>
<span data-ttu-id="3c130-103">指定是否為通用語言執行平台事件啟用 Windows 事件追蹤 (ETW)。</span><span class="sxs-lookup"><span data-stu-id="3c130-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
 <span data-ttu-id="3c130-104">\<設定 > 項目</span><span class="sxs-lookup"><span data-stu-id="3c130-104">\<configuration> Element</span></span>  
<span data-ttu-id="3c130-105">\<runtime > 項目</span><span class="sxs-lookup"><span data-stu-id="3c130-105">\<runtime> Element</span></span>  
<span data-ttu-id="3c130-106">\<etwEnabled ></span><span class="sxs-lookup"><span data-stu-id="3c130-106">\<etwEnabled></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c130-107">語法</span><span class="sxs-lookup"><span data-stu-id="3c130-107">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c130-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3c130-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3c130-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3c130-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c130-110">屬性</span><span class="sxs-lookup"><span data-stu-id="3c130-110">Attributes</span></span>  
  
|<span data-ttu-id="3c130-111">屬性</span><span class="sxs-lookup"><span data-stu-id="3c130-111">Attribute</span></span>|<span data-ttu-id="3c130-112">描述</span><span class="sxs-lookup"><span data-stu-id="3c130-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3c130-113">enabled</span><span class="sxs-lookup"><span data-stu-id="3c130-113">enabled</span></span>|<span data-ttu-id="3c130-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="3c130-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="3c130-115">指定是否應該啟用 ETW。</span><span class="sxs-lookup"><span data-stu-id="3c130-115">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="3c130-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="3c130-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="3c130-117">值</span><span class="sxs-lookup"><span data-stu-id="3c130-117">Value</span></span>|<span data-ttu-id="3c130-118">描述</span><span class="sxs-lookup"><span data-stu-id="3c130-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3c130-119">true</span><span class="sxs-lookup"><span data-stu-id="3c130-119">true</span></span>|<span data-ttu-id="3c130-120">啟用 ETW。</span><span class="sxs-lookup"><span data-stu-id="3c130-120">Enable ETW.</span></span> <span data-ttu-id="3c130-121">這是預設值為開頭的 Windows Windows Vista 和 Windows Server 2008 作業系統的版本。</span><span class="sxs-lookup"><span data-stu-id="3c130-121">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="3c130-122">false</span><span class="sxs-lookup"><span data-stu-id="3c130-122">false</span></span>|<span data-ttu-id="3c130-123">停用 ETW。</span><span class="sxs-lookup"><span data-stu-id="3c130-123">Disable ETW.</span></span> <span data-ttu-id="3c130-124">這是舊版的 Windows 版本的預設值。</span><span class="sxs-lookup"><span data-stu-id="3c130-124">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3c130-125">子元素</span><span class="sxs-lookup"><span data-stu-id="3c130-125">Child Elements</span></span>  
 <span data-ttu-id="3c130-126">無。</span><span class="sxs-lookup"><span data-stu-id="3c130-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3c130-127">父項目</span><span class="sxs-lookup"><span data-stu-id="3c130-127">Parent Elements</span></span>  
  
|<span data-ttu-id="3c130-128">項目</span><span class="sxs-lookup"><span data-stu-id="3c130-128">Element</span></span>|<span data-ttu-id="3c130-129">描述</span><span class="sxs-lookup"><span data-stu-id="3c130-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="3c130-130">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="3c130-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="3c130-131">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="3c130-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c130-132">備註</span><span class="sxs-lookup"><span data-stu-id="3c130-132">Remarks</span></span>  
 <span data-ttu-id="3c130-133">從 Windows Vista 開始，預設會啟用 ETW。</span><span class="sxs-lookup"><span data-stu-id="3c130-133">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="3c130-134">若要停用 ETW，應用程式中使用這個元素。</span><span class="sxs-lookup"><span data-stu-id="3c130-134">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="3c130-135">在舊版的 Windows 中，使用這個項目來啟用 ETW 應用程式。</span><span class="sxs-lookup"><span data-stu-id="3c130-135">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3c130-136">ETW 可以啟用或停用全域伺服器上使用登錄設定。</span><span class="sxs-lookup"><span data-stu-id="3c130-136">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="3c130-137">請參閱[控制.NET Framework 記錄](../../../../../docs/framework/performance/controlling-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="3c130-137">See [Controlling .NET Framework Logging](../../../../../docs/framework/performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c130-138">範例</span><span class="sxs-lookup"><span data-stu-id="3c130-138">Example</span></span>  
 <span data-ttu-id="3c130-139">下列範例會示範如何啟用 ETW 追蹤，應用程式。</span><span class="sxs-lookup"><span data-stu-id="3c130-139">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c130-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c130-140">See Also</span></span>  
 [<span data-ttu-id="3c130-141">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="3c130-141">Runtime Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [<span data-ttu-id="3c130-142">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="3c130-142">Configuration File Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [<span data-ttu-id="3c130-143">控制 .NET Framework 記錄</span><span class="sxs-lookup"><span data-stu-id="3c130-143">Controlling .NET Framework Logging</span></span>](../../../../../docs/framework/performance/controlling-logging.md)
