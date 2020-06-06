---
title: <etwEnable> 項目
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
ms.openlocfilehash: 14cea171a4a25e148ea32f75a8ef09b83a4ec8ad
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73117388"
---
# <a name="etwenable-element"></a><span data-ttu-id="fd13a-102">\<etwEnable> 項目</span><span class="sxs-lookup"><span data-stu-id="fd13a-102">\<etwEnable> Element</span></span>
<span data-ttu-id="fd13a-103">指定是否為通用語言執行平台事件啟用 Windows 事件追蹤 (ETW)。</span><span class="sxs-lookup"><span data-stu-id="fd13a-103">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<etwEnabled>**  
  
## <a name="syntax"></a><span data-ttu-id="fd13a-104">語法</span><span class="sxs-lookup"><span data-stu-id="fd13a-104">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd13a-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fd13a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="fd13a-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fd13a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd13a-107">屬性</span><span class="sxs-lookup"><span data-stu-id="fd13a-107">Attributes</span></span>  
  
|<span data-ttu-id="fd13a-108">屬性</span><span class="sxs-lookup"><span data-stu-id="fd13a-108">Attribute</span></span>|<span data-ttu-id="fd13a-109">描述</span><span class="sxs-lookup"><span data-stu-id="fd13a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fd13a-110">已啟用</span><span class="sxs-lookup"><span data-stu-id="fd13a-110">enabled</span></span>|<span data-ttu-id="fd13a-111">必要屬性。</span><span class="sxs-lookup"><span data-stu-id="fd13a-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="fd13a-112">指定是否應該啟用 ETW。</span><span class="sxs-lookup"><span data-stu-id="fd13a-112">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="fd13a-113">啟用屬性</span><span class="sxs-lookup"><span data-stu-id="fd13a-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="fd13a-114">值</span><span class="sxs-lookup"><span data-stu-id="fd13a-114">Value</span></span>|<span data-ttu-id="fd13a-115">描述</span><span class="sxs-lookup"><span data-stu-id="fd13a-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fd13a-116">true</span><span class="sxs-lookup"><span data-stu-id="fd13a-116">true</span></span>|<span data-ttu-id="fd13a-117">啟用 ETW。</span><span class="sxs-lookup"><span data-stu-id="fd13a-117">Enable ETW.</span></span> <span data-ttu-id="fd13a-118">從 Windows Vista 和 Windows Server 2008 作業系統開始，這是 Windows 版本的預設值。</span><span class="sxs-lookup"><span data-stu-id="fd13a-118">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="fd13a-119">false</span><span class="sxs-lookup"><span data-stu-id="fd13a-119">false</span></span>|<span data-ttu-id="fd13a-120">停用 ETW。</span><span class="sxs-lookup"><span data-stu-id="fd13a-120">Disable ETW.</span></span> <span data-ttu-id="fd13a-121">這是舊版 Windows 的預設值。</span><span class="sxs-lookup"><span data-stu-id="fd13a-121">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd13a-122">子元素</span><span class="sxs-lookup"><span data-stu-id="fd13a-122">Child Elements</span></span>  
 <span data-ttu-id="fd13a-123">無。</span><span class="sxs-lookup"><span data-stu-id="fd13a-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd13a-124">父項目</span><span class="sxs-lookup"><span data-stu-id="fd13a-124">Parent Elements</span></span>  
  
|<span data-ttu-id="fd13a-125">元素</span><span class="sxs-lookup"><span data-stu-id="fd13a-125">Element</span></span>|<span data-ttu-id="fd13a-126">描述</span><span class="sxs-lookup"><span data-stu-id="fd13a-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="fd13a-127">通用語言執行平台和 .NET Framework 應用程式所使用之每個組態檔中的根項目。</span><span class="sxs-lookup"><span data-stu-id="fd13a-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="fd13a-128">包含有關組件繫結和記憶體回收的資訊。</span><span class="sxs-lookup"><span data-stu-id="fd13a-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd13a-129">備註</span><span class="sxs-lookup"><span data-stu-id="fd13a-129">Remarks</span></span>  
 <span data-ttu-id="fd13a-130">從 Windows Vista 開始，預設會啟用 ETW。</span><span class="sxs-lookup"><span data-stu-id="fd13a-130">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="fd13a-131">使用此元素可停用應用程式的 ETW。</span><span class="sxs-lookup"><span data-stu-id="fd13a-131">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="fd13a-132">在舊版的 Windows 中，請使用此元素來啟用應用程式的 ETW。</span><span class="sxs-lookup"><span data-stu-id="fd13a-132">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fd13a-133">您可以使用登錄設定，在伺服器上全域啟用或停用 ETW。</span><span class="sxs-lookup"><span data-stu-id="fd13a-133">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="fd13a-134">請參閱[控制 .NET Framework 記錄](../../../performance/controlling-logging.md)。</span><span class="sxs-lookup"><span data-stu-id="fd13a-134">See [Controlling .NET Framework Logging](../../../performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd13a-135">範例</span><span class="sxs-lookup"><span data-stu-id="fd13a-135">Example</span></span>  
 <span data-ttu-id="fd13a-136">下列範例顯示如何啟用應用程式的 ETW 追蹤。</span><span class="sxs-lookup"><span data-stu-id="fd13a-136">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd13a-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd13a-137">See also</span></span>

- [<span data-ttu-id="fd13a-138">執行時間設定架構</span><span class="sxs-lookup"><span data-stu-id="fd13a-138">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="fd13a-139">設定檔架構</span><span class="sxs-lookup"><span data-stu-id="fd13a-139">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="fd13a-140">控制 .NET Framework 記錄</span><span class="sxs-lookup"><span data-stu-id="fd13a-140">Controlling .NET Framework Logging</span></span>](../../../performance/controlling-logging.md)
