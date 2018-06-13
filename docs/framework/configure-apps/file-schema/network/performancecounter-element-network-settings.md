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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5879614fd34fe645899f1b95f41e9b0675418292
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742633"
---
# <a name="ltperformancecountergt-element-network-settings"></a><span data-ttu-id="c057b-102">&lt;performanceCounter&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="c057b-102">&lt;performanceCounter&gt; Element (Network Settings)</span></span>
<span data-ttu-id="c057b-103">啟用或停用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="c057b-103">Enables or disables networking performance counters.</span></span>  
  
 <span data-ttu-id="c057b-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="c057b-104">\<configuration></span></span>  
<span data-ttu-id="c057b-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="c057b-105">\<system.net></span></span>  
<span data-ttu-id="c057b-106">\<設定 ></span><span class="sxs-lookup"><span data-stu-id="c057b-106">\<settings></span></span>  
<span data-ttu-id="c057b-107">\<performanceCounters></span><span class="sxs-lookup"><span data-stu-id="c057b-107">\<performanceCounters></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c057b-108">語法</span><span class="sxs-lookup"><span data-stu-id="c057b-108">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c057b-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c057b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c057b-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c057b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c057b-111">屬性</span><span class="sxs-lookup"><span data-stu-id="c057b-111">Attributes</span></span>  
  
|<span data-ttu-id="c057b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c057b-112">Attribute</span></span>|<span data-ttu-id="c057b-113">描述</span><span class="sxs-lookup"><span data-stu-id="c057b-113">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="c057b-114">指定是否啟用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="c057b-114">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="c057b-115">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="c057b-115">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c057b-116">子項目</span><span class="sxs-lookup"><span data-stu-id="c057b-116">Child Elements</span></span>  
 <span data-ttu-id="c057b-117">無。</span><span class="sxs-lookup"><span data-stu-id="c057b-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c057b-118">父項目</span><span class="sxs-lookup"><span data-stu-id="c057b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="c057b-119">項目</span><span class="sxs-lookup"><span data-stu-id="c057b-119">Element</span></span>|<span data-ttu-id="c057b-120">描述</span><span class="sxs-lookup"><span data-stu-id="c057b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c057b-121">設定</span><span class="sxs-lookup"><span data-stu-id="c057b-121">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="c057b-122">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="c057b-122">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c057b-123">備註</span><span class="sxs-lookup"><span data-stu-id="c057b-123">Remarks</span></span>  
 <span data-ttu-id="c057b-124">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="c057b-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="c057b-125">需要在組態檔中啟用，才能使用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="c057b-125">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="c057b-126">藉由組態檔中的單一設定可啟用或停用所有網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="c057b-126">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="c057b-127">不能啟用或停用個別的網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="c057b-127">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="c057b-128">如需有關特定網路的效能計數器的詳細資訊，請參閱[網路效能計數器](http://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd)。</span><span class="sxs-lookup"><span data-stu-id="c057b-128">For more information on the specific networking performance counters, see [Networking Performance Counters](http://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd).</span></span>  
  
 <span data-ttu-id="c057b-129">預設值是該網路的效能計數器已停用。</span><span class="sxs-lookup"><span data-stu-id="c057b-129">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="c057b-130"><xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>屬性可以用來取得目前的值**啟用**適用的組態檔中的屬性。</span><span class="sxs-lookup"><span data-stu-id="c057b-130">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c057b-131">範例</span><span class="sxs-lookup"><span data-stu-id="c057b-131">Example</span></span>  
 <span data-ttu-id="c057b-132">下列範例示範如何設定<xref:System.Net>和相關命名空間，以啟用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="c057b-132">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c057b-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c057b-133">See Also</span></span>  
 <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="c057b-134">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="c057b-134">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)  
 [<span data-ttu-id="c057b-135">網路效能計數器</span><span class="sxs-lookup"><span data-stu-id="c057b-135">Networking Performance Counters</span></span>](http://msdn.microsoft.com/library/d1860235-f643-46ae-846c-ff0ed8b0e3cd)
