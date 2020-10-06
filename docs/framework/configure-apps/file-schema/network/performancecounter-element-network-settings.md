---
title: <performanceCounters> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters
- http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters
helpviewer_keywords:
- performanceCounters element
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
ms.openlocfilehash: 584bdafbbd60303401cbc6ad96b8654fe11c7077
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756256"
---
# <a name="performancecounters-element-network-settings"></a><span data-ttu-id="fd301-102">\<performanceCounters> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="fd301-102">\<performanceCounters> Element (Network Settings)</span></span>

<span data-ttu-id="fd301-103">啟用或停用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="fd301-103">Enables or disables networking performance counters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<performanceCounters>**

## <a name="syntax"></a><span data-ttu-id="fd301-104">語法</span><span class="sxs-lookup"><span data-stu-id="fd301-104">Syntax</span></span>  
  
```xml  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fd301-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fd301-105">Attributes and Elements</span></span>  

 <span data-ttu-id="fd301-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="fd301-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fd301-107">屬性</span><span class="sxs-lookup"><span data-stu-id="fd301-107">Attributes</span></span>  
  
|<span data-ttu-id="fd301-108">屬性</span><span class="sxs-lookup"><span data-stu-id="fd301-108">Attribute</span></span>|<span data-ttu-id="fd301-109">描述</span><span class="sxs-lookup"><span data-stu-id="fd301-109">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="fd301-110">指定是否啟用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="fd301-110">Specifies whether the networking performance counters are enabled.</span></span> <span data-ttu-id="fd301-111">預設值是 `false`。</span><span class="sxs-lookup"><span data-stu-id="fd301-111">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fd301-112">子元素</span><span class="sxs-lookup"><span data-stu-id="fd301-112">Child Elements</span></span>  

 <span data-ttu-id="fd301-113">無。</span><span class="sxs-lookup"><span data-stu-id="fd301-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fd301-114">父項目</span><span class="sxs-lookup"><span data-stu-id="fd301-114">Parent Elements</span></span>  
  
|<span data-ttu-id="fd301-115">元素</span><span class="sxs-lookup"><span data-stu-id="fd301-115">Element</span></span>|<span data-ttu-id="fd301-116">描述</span><span class="sxs-lookup"><span data-stu-id="fd301-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fd301-117">設定</span><span class="sxs-lookup"><span data-stu-id="fd301-117">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="fd301-118">為 <xref:System.Net> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="fd301-118">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fd301-119">備註</span><span class="sxs-lookup"><span data-stu-id="fd301-119">Remarks</span></span>  

 <span data-ttu-id="fd301-120">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="fd301-120">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
 <span data-ttu-id="fd301-121">需要在組態檔中啟用，才能使用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="fd301-121">Networking performance counters need to be enabled in the configuration file to be used.</span></span> <span data-ttu-id="fd301-122">藉由組態檔中的單一設定可啟用或停用所有網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="fd301-122">All networking performance counters are enabled or disabled with a single setting in the configuration file.</span></span> <span data-ttu-id="fd301-123">不能啟用或停用個別的網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="fd301-123">Individual networking performance counters cannot be enabled or disabled.</span></span> <span data-ttu-id="fd301-124">如需特定網路效能計數器的詳細資訊，請參閱 [網路效能計數器](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)。</span><span class="sxs-lookup"><span data-stu-id="fd301-124">For more information on the specific networking performance counters, see [Networking performance counters](../../../debug-trace-profile/performance-counters.md#networking-performance-counters).</span></span>  
  
 <span data-ttu-id="fd301-125">預設值是網路效能計數器已停用。</span><span class="sxs-lookup"><span data-stu-id="fd301-125">The default value is that networking performance counters are disabled.</span></span>  
  
 <span data-ttu-id="fd301-126"><xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>屬性可以用來從適用的設定檔案取得**已啟用**屬性的目前值。</span><span class="sxs-lookup"><span data-stu-id="fd301-126">The <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType> property can be used to get the current value of the **enabled** attribute from applicable configuration files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd301-127">範例</span><span class="sxs-lookup"><span data-stu-id="fd301-127">Example</span></span>  

 <span data-ttu-id="fd301-128">下列範例顯示如何設定 <xref:System.Net> 和相關的命名空間，以啟用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="fd301-128">The following example shows how to configure the <xref:System.Net> and related namespaces to enable networking performance counters.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fd301-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd301-129">See also</span></span>

- <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=nameWithType>
- <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=nameWithType>
- [<span data-ttu-id="fd301-130">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="fd301-130">Network Settings Schema</span></span>](index.md)
- [<span data-ttu-id="fd301-131">網路效能計數器</span><span class="sxs-lookup"><span data-stu-id="fd301-131">Networking Performance Counters</span></span>](../../../debug-trace-profile/performance-counters.md#networking-performance-counters)
