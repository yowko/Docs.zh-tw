---
title: <etwEnable> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
ms.openlocfilehash: 14cea171a4a25e148ea32f75a8ef09b83a4ec8ad
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2019
ms.locfileid: "73117388"
---
# <a name="etwenable-element"></a><span data-ttu-id="6224d-102">\<etwEnable > 元素</span><span class="sxs-lookup"><span data-stu-id="6224d-102">\<etwEnable> Element</span></span>
<span data-ttu-id="6224d-103">指定是否為通用語言執行平台事件啟用 Windows 事件追蹤 (ETW)。</span><span class="sxs-lookup"><span data-stu-id="6224d-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
<span data-ttu-id="6224d-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6224d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6224d-105">&nbsp; &nbsp;[ **\<runtime >** ](runtime-element.md) </span><span class="sxs-lookup"><span data-stu-id="6224d-105">&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)</span></span>\
<span data-ttu-id="6224d-106">&nbsp;&nbsp;&nbsp;&nbsp; **\<etwEnabled >**</span><span class="sxs-lookup"><span data-stu-id="6224d-106">&nbsp;&nbsp;&nbsp;&nbsp;**\<etwEnabled>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6224d-107">語法</span><span class="sxs-lookup"><span data-stu-id="6224d-107">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6224d-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6224d-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6224d-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="6224d-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6224d-110">屬性</span><span class="sxs-lookup"><span data-stu-id="6224d-110">Attributes</span></span>  
  
|<span data-ttu-id="6224d-111">屬性</span><span class="sxs-lookup"><span data-stu-id="6224d-111">Attribute</span></span>|<span data-ttu-id="6224d-112">描述</span><span class="sxs-lookup"><span data-stu-id="6224d-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6224d-113">enabled</span><span class="sxs-lookup"><span data-stu-id="6224d-113">enabled</span></span>|<span data-ttu-id="6224d-114">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="6224d-114">Required attribute.</span></span><br /><br /> <span data-ttu-id="6224d-115">指定是否應該啟用 ETW。</span><span class="sxs-lookup"><span data-stu-id="6224d-115">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="6224d-116">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="6224d-116">enabled Attribute</span></span>  
  
|<span data-ttu-id="6224d-117">值</span><span class="sxs-lookup"><span data-stu-id="6224d-117">Value</span></span>|<span data-ttu-id="6224d-118">描述</span><span class="sxs-lookup"><span data-stu-id="6224d-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6224d-119">true</span><span class="sxs-lookup"><span data-stu-id="6224d-119">true</span></span>|<span data-ttu-id="6224d-120">啟用 ETW。</span><span class="sxs-lookup"><span data-stu-id="6224d-120">Enable ETW.</span></span> <span data-ttu-id="6224d-121">從 Windows Vista 和 Windows Server 2008 作業系統開始，這是 Windows 版本的預設值。</span><span class="sxs-lookup"><span data-stu-id="6224d-121">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="6224d-122">False</span><span class="sxs-lookup"><span data-stu-id="6224d-122">false</span></span>|<span data-ttu-id="6224d-123">停用 ETW。</span><span class="sxs-lookup"><span data-stu-id="6224d-123">Disable ETW.</span></span> <span data-ttu-id="6224d-124">這是舊版 Windows 的預設值。</span><span class="sxs-lookup"><span data-stu-id="6224d-124">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6224d-125">子項目</span><span class="sxs-lookup"><span data-stu-id="6224d-125">Child Elements</span></span>  
 <span data-ttu-id="6224d-126">無。</span><span class="sxs-lookup"><span data-stu-id="6224d-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6224d-127">父項目</span><span class="sxs-lookup"><span data-stu-id="6224d-127">Parent Elements</span></span>  
  
|<span data-ttu-id="6224d-128">項目</span><span class="sxs-lookup"><span data-stu-id="6224d-128">Element</span></span>|<span data-ttu-id="6224d-129">描述</span><span class="sxs-lookup"><span data-stu-id="6224d-129">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="6224d-130">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="6224d-130">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="6224d-131">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="6224d-131">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6224d-132">備註</span><span class="sxs-lookup"><span data-stu-id="6224d-132">Remarks</span></span>  
 <span data-ttu-id="6224d-133">從 Windows Vista 開始，預設會啟用 ETW。</span><span class="sxs-lookup"><span data-stu-id="6224d-133">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="6224d-134">使用此元素可停用應用程式的 ETW。</span><span class="sxs-lookup"><span data-stu-id="6224d-134">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="6224d-135">在舊版的 Windows 中，請使用此元素來啟用應用程式的 ETW。</span><span class="sxs-lookup"><span data-stu-id="6224d-135">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6224d-136">您可以使用登錄設定，在伺服器上全域啟用或停用 ETW。</span><span class="sxs-lookup"><span data-stu-id="6224d-136">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="6224d-137">請參閱[控制 .NET Framework 記錄](../../../performance/controlling-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="6224d-137">See [Controlling .NET Framework Logging](../../../performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6224d-138">範例</span><span class="sxs-lookup"><span data-stu-id="6224d-138">Example</span></span>  
 <span data-ttu-id="6224d-139">下列範例顯示如何啟用應用程式的 ETW 追蹤。</span><span class="sxs-lookup"><span data-stu-id="6224d-139">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6224d-140">請參閱</span><span class="sxs-lookup"><span data-stu-id="6224d-140">See also</span></span>

- [<span data-ttu-id="6224d-141">執行階段設定結構描述</span><span class="sxs-lookup"><span data-stu-id="6224d-141">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="6224d-142">組態檔結構描述</span><span class="sxs-lookup"><span data-stu-id="6224d-142">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="6224d-143">控制 .NET Framework 記錄</span><span class="sxs-lookup"><span data-stu-id="6224d-143">Controlling .NET Framework Logging</span></span>](../../../performance/controlling-logging.md)
