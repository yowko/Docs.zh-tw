---
title: <settings> 項目 （網路設定）
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#settings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings
helpviewer_keywords:
- settings element
- <settings> element
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
ms.openlocfilehash: a1733803d1f5a5bf64aeb69d0360cef3de3b3a69
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59096923"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="ceb07-102">\<設定 > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="ceb07-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="ceb07-103">為 <xref:System.Net?displayProperty=nameWithType> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="ceb07-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  
  
 <span data-ttu-id="ceb07-104">\<configuration></span><span class="sxs-lookup"><span data-stu-id="ceb07-104">\<configuration></span></span>  
<span data-ttu-id="ceb07-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="ceb07-105">\<system.net></span></span>  
<span data-ttu-id="ceb07-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="ceb07-106">\<settings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceb07-107">語法</span><span class="sxs-lookup"><span data-stu-id="ceb07-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ceb07-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ceb07-108">Attributes and Elements</span></span>  
 <span data-ttu-id="ceb07-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ceb07-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ceb07-110">屬性</span><span class="sxs-lookup"><span data-stu-id="ceb07-110">Attributes</span></span>  
 <span data-ttu-id="ceb07-111">無。</span><span class="sxs-lookup"><span data-stu-id="ceb07-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ceb07-112">子元素</span><span class="sxs-lookup"><span data-stu-id="ceb07-112">Child Elements</span></span>  
  
|<span data-ttu-id="ceb07-113">項目</span><span class="sxs-lookup"><span data-stu-id="ceb07-113">Element</span></span>|<span data-ttu-id="ceb07-114">描述</span><span class="sxs-lookup"><span data-stu-id="ceb07-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ceb07-115">httpListener</span><span class="sxs-lookup"><span data-stu-id="ceb07-115">httpListener</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|<span data-ttu-id="ceb07-116">自訂所使用的參數<xref:System.Net.HttpListener>類別。</span><span class="sxs-lookup"><span data-stu-id="ceb07-116">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="ceb07-117">httpWebRequest</span><span class="sxs-lookup"><span data-stu-id="ceb07-117">httpWebRequest</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|<span data-ttu-id="ceb07-118">自訂 Web 要求參數。</span><span class="sxs-lookup"><span data-stu-id="ceb07-118">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="ceb07-119">ipv6</span><span class="sxs-lookup"><span data-stu-id="ceb07-119">ipv6</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|<span data-ttu-id="ceb07-120">可讓網際網路通訊協定第 6 版 (IPv6) 支援。</span><span class="sxs-lookup"><span data-stu-id="ceb07-120">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="ceb07-121">\<performanceCounter > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="ceb07-121">\<performanceCounter> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|<span data-ttu-id="ceb07-122">啟用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="ceb07-122">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="ceb07-123">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="ceb07-123">servicePointManager</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|<span data-ttu-id="ceb07-124">設定網路資源的連線。</span><span class="sxs-lookup"><span data-stu-id="ceb07-124">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="ceb07-125">通訊端</span><span class="sxs-lookup"><span data-stu-id="ceb07-125">socket</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|<span data-ttu-id="ceb07-126">指定通訊端作業是否使用完成通訊埠。</span><span class="sxs-lookup"><span data-stu-id="ceb07-126">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="ceb07-127">\<webProxyScript > 項目 （網路設定）</span><span class="sxs-lookup"><span data-stu-id="ceb07-127">\<webProxyScript> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|<span data-ttu-id="ceb07-128">設定用來探索 Web proxy 指令碼的特性。</span><span class="sxs-lookup"><span data-stu-id="ceb07-128">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ceb07-129">父項目</span><span class="sxs-lookup"><span data-stu-id="ceb07-129">Parent Elements</span></span>  
  
|<span data-ttu-id="ceb07-130">項目</span><span class="sxs-lookup"><span data-stu-id="ceb07-130">Element</span></span>|<span data-ttu-id="ceb07-131">描述</span><span class="sxs-lookup"><span data-stu-id="ceb07-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ceb07-132">system.net</span><span class="sxs-lookup"><span data-stu-id="ceb07-132">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="ceb07-133">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="ceb07-133">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ceb07-134">備註</span><span class="sxs-lookup"><span data-stu-id="ceb07-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="ceb07-135">組態檔</span><span class="sxs-lookup"><span data-stu-id="ceb07-135">Configuration Files</span></span>  
 <span data-ttu-id="ceb07-136">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="ceb07-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceb07-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ceb07-137">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="ceb07-138">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="ceb07-138">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
