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
ms.openlocfilehash: 3fe6b19d0055aafad859b55960800d9786d7fa08
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697992"
---
# <a name="performancecounter-element-network-settings"></a><span data-ttu-id="bc88c-102">@no__t 0performanceCounter > 元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="bc88c-102">\<performanceCounter> Element (Network Settings)</span></span>
<span data-ttu-id="bc88c-103">啟用或停用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="bc88c-103">Enables or disables networking performance counters.</span></span>  
  
[<span data-ttu-id="bc88c-104"> **\<configuration>** </span><span class="sxs-lookup"><span data-stu-id="bc88c-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="bc88c-105">&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="bc88c-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="bc88c-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="bc88c-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>  
<span data-ttu-id="bc88c-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<performanceCounters >**</span><span class="sxs-lookup"><span data-stu-id="bc88c-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc88c-108">語法</span><span class="sxs-lookup"><span data-stu-id="bc88c-108">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc88c-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bc88c-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bc88c-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="bc88c-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc88c-111">屬性</span><span class="sxs-lookup"><span data-stu-id="bc88c-111">Attributes</span></span>  
  
|<span data-ttu-id="bc88c-112">屬性</span><span class="sxs-lookup"><span data-stu-id="bc88c-112">Attribute</span></span>|<span data-ttu-id="bc88c-113">描述</span><span class="sxs-lookup"><span data-stu-id="bc88c-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="bc88c-114">指定是否啟用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="bc88c-114">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="bc88c-115">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="bc88c-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bc88c-116">子元素</span><span class="sxs-lookup"><span data-stu-id="bc88c-116">Child Elements</span></span>  
 <span data-ttu-id="bc88c-117">無。</span><span class="sxs-lookup"><span data-stu-id="bc88c-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc88c-118">父項目</span><span class="sxs-lookup"><span data-stu-id="bc88c-118">Parent Elements</span></span>  
  
|<span data-ttu-id="bc88c-119">項目</span><span class="sxs-lookup"><span data-stu-id="bc88c-119">Element</span></span>|<span data-ttu-id="bc88c-120">描述</span><span class="sxs-lookup"><span data-stu-id="bc88c-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc88c-121">設置</span><span class="sxs-lookup"><span data-stu-id="bc88c-121">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="bc88c-122">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="bc88c-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc88c-123">備註</span><span class="sxs-lookup"><span data-stu-id="bc88c-123">Remarks</span></span>  
 <span data-ttu-id="bc88c-124">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="bc88c-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="bc88c-125">需要在組態檔中啟用，才能使用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="bc88c-125">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="bc88c-126">藉由組態檔中的單一設定可啟用或停用所有網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="bc88c-126">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="bc88c-127">不能啟用或停用個別的網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="bc88c-127">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="bc88c-128">如需特定網路效能計數器的詳細資訊，請參閱[網路效能計數器](../../../debug-trace-profile/performance-counters.md#networking)。</span><span class="sxs-lookup"><span data-stu-id="bc88c-128">For more information on the specific networking performance counters, see [Networking Performance Counters](../../../debug-trace-profile/performance-counters.md#networking).</span></span>  
  
 <span data-ttu-id="bc88c-129">預設值是網路效能計數器已停用。</span><span class="sxs-lookup"><span data-stu-id="bc88c-129">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="bc88c-130">@No__t-0 屬性可以用來從適用的設定檔取得**已啟用**屬性的目前值。</span><span class="sxs-lookup"><span data-stu-id="bc88c-130">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc88c-131">範例</span><span class="sxs-lookup"><span data-stu-id="bc88c-131">Example</span></span>  
 <span data-ttu-id="bc88c-132">下列範例顯示如何設定 @no__t 0 和相關的命名空間，以啟用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="bc88c-132">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bc88c-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc88c-133">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="bc88c-134">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="bc88c-134">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="bc88c-135">網路效能計數器</span><span class="sxs-lookup"><span data-stu-id="bc88c-135">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking)
