---
title: '&lt;performanceCounter&gt;項目 （網路設定）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounter element
- <performanceCounter> element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: ea0eba097505741aba31bce4f23e0cc9ca1d4608
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712479"
---
# <a name="ltperformancecountergt-element-network-settings"></a><span data-ttu-id="0fb3f-102">&lt;performanceCounter&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="0fb3f-102">&lt;performanceCounter&gt; Element (Network Settings)</span></span>
<span data-ttu-id="0fb3f-103">啟用或停用網路的效能計數器。</span><span class="sxs-lookup"><span data-stu-id="0fb3f-103">Enables or disables networking performance counters.</span></span>  
  
 <span data-ttu-id="0fb3f-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0fb3f-104">\<configuration></span></span>  
<span data-ttu-id="0fb3f-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="0fb3f-105">\<system.net></span></span>  
<span data-ttu-id="0fb3f-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="0fb3f-106">\<settings></span></span>  
<span data-ttu-id="0fb3f-107">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="0fb3f-107">\<performanceCounters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fb3f-108">語法</span><span class="sxs-lookup"><span data-stu-id="0fb3f-108">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fb3f-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0fb3f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0fb3f-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0fb3f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fb3f-111">屬性</span><span class="sxs-lookup"><span data-stu-id="0fb3f-111">Attributes</span></span>  
  
|<span data-ttu-id="0fb3f-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0fb3f-112">Attribute</span></span>|<span data-ttu-id="0fb3f-113">描述</span><span class="sxs-lookup"><span data-stu-id="0fb3f-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="0fb3f-114">指定是否啟用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="0fb3f-114">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="0fb3f-115">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="0fb3f-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0fb3f-116">子元素</span><span class="sxs-lookup"><span data-stu-id="0fb3f-116">Child Elements</span></span>  
 <span data-ttu-id="0fb3f-117">無。</span><span class="sxs-lookup"><span data-stu-id="0fb3f-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0fb3f-118">父項目</span><span class="sxs-lookup"><span data-stu-id="0fb3f-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0fb3f-119">項目</span><span class="sxs-lookup"><span data-stu-id="0fb3f-119">Element</span></span>|<span data-ttu-id="0fb3f-120">描述</span><span class="sxs-lookup"><span data-stu-id="0fb3f-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0fb3f-121">settings</span><span class="sxs-lookup"><span data-stu-id="0fb3f-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="0fb3f-122">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="0fb3f-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fb3f-123">備註</span><span class="sxs-lookup"><span data-stu-id="0fb3f-123">Remarks</span></span>  
 <span data-ttu-id="0fb3f-124">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="0fb3f-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="0fb3f-125">需要在組態檔中啟用，才能使用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="0fb3f-125">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="0fb3f-126">藉由組態檔中的單一設定可啟用或停用所有網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="0fb3f-126">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="0fb3f-127">不能啟用或停用個別的網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="0fb3f-127">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="0fb3f-128">如需有關特定的網路效能計數器的詳細資訊，請參閱[網路效能計數器](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking)。</span><span class="sxs-lookup"><span data-stu-id="0fb3f-128">For more information on the specific networking performance counters, see [Networking Performance Counters](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking).</span></span>  
  
 <span data-ttu-id="0fb3f-129">預設值是該網路的效能計數器已停用。</span><span class="sxs-lookup"><span data-stu-id="0fb3f-129">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="0fb3f-130"><xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>屬性可用來取得目前的值**啟用**適用的組態檔中的屬性。</span><span class="sxs-lookup"><span data-stu-id="0fb3f-130">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fb3f-131">範例</span><span class="sxs-lookup"><span data-stu-id="0fb3f-131">Example</span></span>  
 <span data-ttu-id="0fb3f-132">下列範例示範如何設定<xref:System.Net>和相關命名空間，以啟用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="0fb3f-132">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0fb3f-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0fb3f-133">See also</span></span>
- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0fb3f-134">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="0fb3f-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
- [<span data-ttu-id="0fb3f-135">網路效能計數器</span><span class="sxs-lookup"><span data-stu-id="0fb3f-135">Networking Performance Counters</span></span>](../../../../../docs/framework/debug-trace-profile/performance-counters.md#networking)
