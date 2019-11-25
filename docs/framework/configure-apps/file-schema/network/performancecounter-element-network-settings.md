---
title: <performanceCounter> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: 58a2bf5118a3a2cd9c33301eca5dcc751c2351bf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74283084"
---
# <a name="performancecounter-element-network-settings"></a><span data-ttu-id="072a4-102">\<performanceCounter > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="072a4-102">\<performanceCounter> Element (Network Settings)</span></span>
<span data-ttu-id="072a4-103">啟用或停用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="072a4-103">Enables or disables networking performance counters.</span></span>  

<span data-ttu-id="072a4-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="072a4-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="072a4-105">&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="072a4-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="072a4-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<設定 >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="072a4-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>\
<span data-ttu-id="072a4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<performanceCounters >**</span><span class="sxs-lookup"><span data-stu-id="072a4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**</span></span>

## <a name="syntax"></a><span data-ttu-id="072a4-108">語法</span><span class="sxs-lookup"><span data-stu-id="072a4-108">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="072a4-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="072a4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="072a4-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="072a4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="072a4-111">屬性</span><span class="sxs-lookup"><span data-stu-id="072a4-111">Attributes</span></span>  
  
|<span data-ttu-id="072a4-112">屬性</span><span class="sxs-lookup"><span data-stu-id="072a4-112">Attribute</span></span>|<span data-ttu-id="072a4-113">描述</span><span class="sxs-lookup"><span data-stu-id="072a4-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="072a4-114">指定是否啟用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="072a4-114">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="072a4-115">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="072a4-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="072a4-116">子元素</span><span class="sxs-lookup"><span data-stu-id="072a4-116">Child Elements</span></span>  
 <span data-ttu-id="072a4-117">無。</span><span class="sxs-lookup"><span data-stu-id="072a4-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="072a4-118">父項目</span><span class="sxs-lookup"><span data-stu-id="072a4-118">Parent Elements</span></span>  
  
|<span data-ttu-id="072a4-119">項目</span><span class="sxs-lookup"><span data-stu-id="072a4-119">Element</span></span>|<span data-ttu-id="072a4-120">描述</span><span class="sxs-lookup"><span data-stu-id="072a4-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="072a4-121">設置</span><span class="sxs-lookup"><span data-stu-id="072a4-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="072a4-122">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="072a4-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="072a4-123">備註</span><span class="sxs-lookup"><span data-stu-id="072a4-123">Remarks</span></span>  
 <span data-ttu-id="072a4-124">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="072a4-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="072a4-125">需要在組態檔中啟用，才能使用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="072a4-125">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="072a4-126">藉由組態檔中的單一設定可啟用或停用所有網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="072a4-126">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="072a4-127">不能啟用或停用個別的網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="072a4-127">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="072a4-128">如需特定網路效能計數器的詳細資訊，請參閱[網路效能計數器](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)。</span><span class="sxs-lookup"><span data-stu-id="072a4-128">For more information on the specific networking performance counters, see [Networking performance counters](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span></span>  
  
 <span data-ttu-id="072a4-129">預設值是網路效能計數器已停用。</span><span class="sxs-lookup"><span data-stu-id="072a4-129">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="072a4-130"><xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> 屬性可以用來從適用的設定檔取得**已啟用**屬性的目前值。</span><span class="sxs-lookup"><span data-stu-id="072a4-130">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="072a4-131">範例</span><span class="sxs-lookup"><span data-stu-id="072a4-131">Example</span></span>  
 <span data-ttu-id="072a4-132">下列範例顯示如何設定 <xref:System.Net> 和相關的命名空間，以啟用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="072a4-132">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="072a4-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="072a4-133">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="072a4-134">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="072a4-134">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="072a4-135">網路效能計數器</span><span class="sxs-lookup"><span data-stu-id="072a4-135">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)
