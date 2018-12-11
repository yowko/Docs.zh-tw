---
title: '&lt;設定&gt;項目 （網路設定）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: 87a944eca6ea4158f15c9911c6b13fd4d3c0921d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151196"
---
# <a name="ltsettingsgt-element-network-settings"></a><span data-ttu-id="622ec-102">&lt;設定&gt;項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="622ec-102">&lt;settings&gt; Element (Network Settings)</span></span>
<span data-ttu-id="622ec-103">為 <xref:System.Net?displayProperty=nameWithType> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="622ec-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="622ec-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="622ec-104">\<configuration></span></span>  
<span data-ttu-id="622ec-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="622ec-105">\<system.net></span></span>  
<span data-ttu-id="622ec-106">\<設定 ></span><span class="sxs-lookup"><span data-stu-id="622ec-106">\<settings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="622ec-107">語法</span><span class="sxs-lookup"><span data-stu-id="622ec-107">Syntax</span></span>  
  
```xml  
<settings>  
  <httpListener> … </httpListener>  
  <httpWebRequest> … </httpWebRequest>  
  <ipv6> … </ipv6>  
  <performanceCounters> … </performanceCounters>  
  <servicePointManager> … </servicePointManager>  
  <socket> … </socket>  
  <webProxyScript> … </webProxyScript>  
</settings>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="622ec-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="622ec-108">Attributes and Elements</span></span>  
 <span data-ttu-id="622ec-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="622ec-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="622ec-110">屬性</span><span class="sxs-lookup"><span data-stu-id="622ec-110">Attributes</span></span>  
 <span data-ttu-id="622ec-111">無。</span><span class="sxs-lookup"><span data-stu-id="622ec-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="622ec-112">子元素</span><span class="sxs-lookup"><span data-stu-id="622ec-112">Child Elements</span></span>  
  
|<span data-ttu-id="622ec-113">項目</span><span class="sxs-lookup"><span data-stu-id="622ec-113">Element</span></span>|<span data-ttu-id="622ec-114">描述</span><span class="sxs-lookup"><span data-stu-id="622ec-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="622ec-115">httpListener</span><span class="sxs-lookup"><span data-stu-id="622ec-115">httpListener</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|<span data-ttu-id="622ec-116">自訂所使用的參數<xref:System.Net.HttpListener>類別。</span><span class="sxs-lookup"><span data-stu-id="622ec-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="622ec-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="622ec-117">httpWebRequest</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|<span data-ttu-id="622ec-118">自訂 Web 要求參數。</span><span class="sxs-lookup"><span data-stu-id="622ec-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="622ec-119">ipv6</span><span class="sxs-lookup"><span data-stu-id="622ec-119">ipv6</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|<span data-ttu-id="622ec-120">可讓網際網路通訊協定第 6 版 (IPv6) 支援。</span><span class="sxs-lookup"><span data-stu-id="622ec-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="622ec-121">\<performanceCounter > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="622ec-121">\<performanceCounter> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|<span data-ttu-id="622ec-122">啟用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="622ec-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="622ec-123">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="622ec-123">servicePointManager</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|<span data-ttu-id="622ec-124">設定網路資源的連線。</span><span class="sxs-lookup"><span data-stu-id="622ec-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="622ec-125">通訊端</span><span class="sxs-lookup"><span data-stu-id="622ec-125">socket</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|<span data-ttu-id="622ec-126">指定通訊端作業是否使用完成通訊埠。</span><span class="sxs-lookup"><span data-stu-id="622ec-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="622ec-127">\<webProxyScript > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="622ec-127">\<webProxyScript> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|<span data-ttu-id="622ec-128">設定用來探索 Web proxy 指令碼的特性。</span><span class="sxs-lookup"><span data-stu-id="622ec-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="622ec-129">父項目</span><span class="sxs-lookup"><span data-stu-id="622ec-129">Parent Elements</span></span>  
  
|<span data-ttu-id="622ec-130">項目</span><span class="sxs-lookup"><span data-stu-id="622ec-130">Element</span></span>|<span data-ttu-id="622ec-131">描述</span><span class="sxs-lookup"><span data-stu-id="622ec-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="622ec-132">system.net</span><span class="sxs-lookup"><span data-stu-id="622ec-132">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="622ec-133">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="622ec-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="622ec-134">備註</span><span class="sxs-lookup"><span data-stu-id="622ec-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="622ec-135">組態檔</span><span class="sxs-lookup"><span data-stu-id="622ec-135">Configuration Files</span></span>  
 <span data-ttu-id="622ec-136">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="622ec-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="622ec-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="622ec-137">See Also</span></span>  
- <xref:System.Net?displayProperty=nameWithType>  
- [<span data-ttu-id="622ec-138">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="622ec-138">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
