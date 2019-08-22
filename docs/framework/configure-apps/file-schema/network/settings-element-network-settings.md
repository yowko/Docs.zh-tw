---
title: <settings> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: 12797e2f06d03aacd81700eae57d5776c1a6f354
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664000"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="fc32e-102">\<設定 > 元素 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="fc32e-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="fc32e-103">為 <xref:System.Net?displayProperty=nameWithType> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="fc32e-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="fc32e-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="fc32e-104">\<configuration></span></span>  
<span data-ttu-id="fc32e-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="fc32e-105">\<system.net></span></span>  
<span data-ttu-id="fc32e-106">\<設定 ></span><span class="sxs-lookup"><span data-stu-id="fc32e-106">\<settings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc32e-107">語法</span><span class="sxs-lookup"><span data-stu-id="fc32e-107">Syntax</span></span>  
  
```xml  
<settings>  
  <httpListener>...</httpListener>  
  <httpWebRequest>...</httpWebRequest>  
  <ipv6>...</ipv6>  
  <performanceCounters>...</performanceCounters>  
  <servicePointManager>...</servicePointManager>  
  <socket>...</socket>  
  <webProxyScript>...</webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc32e-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fc32e-108">Attributes and Elements</span></span>  
 <span data-ttu-id="fc32e-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="fc32e-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc32e-110">屬性</span><span class="sxs-lookup"><span data-stu-id="fc32e-110">Attributes</span></span>  
 <span data-ttu-id="fc32e-111">無。</span><span class="sxs-lookup"><span data-stu-id="fc32e-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="fc32e-112">子元素</span><span class="sxs-lookup"><span data-stu-id="fc32e-112">Child Elements</span></span>  
  
|<span data-ttu-id="fc32e-113">項目</span><span class="sxs-lookup"><span data-stu-id="fc32e-113">Element</span></span>|<span data-ttu-id="fc32e-114">說明</span><span class="sxs-lookup"><span data-stu-id="fc32e-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc32e-115">httpListener</span><span class="sxs-lookup"><span data-stu-id="fc32e-115">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="fc32e-116">自訂類別所<xref:System.Net.HttpListener>使用的參數。</span><span class="sxs-lookup"><span data-stu-id="fc32e-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="fc32e-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="fc32e-117">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="fc32e-118">自訂 Web 要求參數。</span><span class="sxs-lookup"><span data-stu-id="fc32e-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="fc32e-119">ipv6</span><span class="sxs-lookup"><span data-stu-id="fc32e-119">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="fc32e-120">啟用網際網路通訊協定第6版 (IPv6) 支援。</span><span class="sxs-lookup"><span data-stu-id="fc32e-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="fc32e-121">\<performanceCounter > 元素 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="fc32e-121">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="fc32e-122">啟用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="fc32e-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="fc32e-123">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="fc32e-123">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="fc32e-124">設定網路資源的連接。</span><span class="sxs-lookup"><span data-stu-id="fc32e-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="fc32e-125">socket</span><span class="sxs-lookup"><span data-stu-id="fc32e-125">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="fc32e-126">指定通訊端作業是否使用完成埠。</span><span class="sxs-lookup"><span data-stu-id="fc32e-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="fc32e-127">\<webProxyScript > 元素 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="fc32e-127">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="fc32e-128">設定用來探索 Web proxy 之腳本的特性。</span><span class="sxs-lookup"><span data-stu-id="fc32e-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fc32e-129">父項目</span><span class="sxs-lookup"><span data-stu-id="fc32e-129">Parent Elements</span></span>  
  
|<span data-ttu-id="fc32e-130">項目</span><span class="sxs-lookup"><span data-stu-id="fc32e-130">Element</span></span>|<span data-ttu-id="fc32e-131">描述</span><span class="sxs-lookup"><span data-stu-id="fc32e-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fc32e-132">system.net</span><span class="sxs-lookup"><span data-stu-id="fc32e-132">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="fc32e-133">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="fc32e-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc32e-134">備註</span><span class="sxs-lookup"><span data-stu-id="fc32e-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="fc32e-135">組態檔</span><span class="sxs-lookup"><span data-stu-id="fc32e-135">Configuration Files</span></span>  
 <span data-ttu-id="fc32e-136">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="fc32e-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc32e-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fc32e-137">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="fc32e-138">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="fc32e-138">Network Settings Schema</span></span>](index.md)
