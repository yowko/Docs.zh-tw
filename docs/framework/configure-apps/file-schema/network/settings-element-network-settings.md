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
ms.openlocfilehash: d510c445c585a36005ed415b14188efc4be03984
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089111"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="d3039-102">\<settings> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="d3039-102">\<settings> Element (Network Settings)</span></span>
<span data-ttu-id="d3039-103">為 <xref:System.Net?displayProperty=nameWithType> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="d3039-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**

## <a name="syntax"></a><span data-ttu-id="d3039-104">語法</span><span class="sxs-lookup"><span data-stu-id="d3039-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3039-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d3039-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d3039-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d3039-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3039-107">屬性</span><span class="sxs-lookup"><span data-stu-id="d3039-107">Attributes</span></span>  
 <span data-ttu-id="d3039-108">無。</span><span class="sxs-lookup"><span data-stu-id="d3039-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d3039-109">子元素</span><span class="sxs-lookup"><span data-stu-id="d3039-109">Child Elements</span></span>  
  
|<span data-ttu-id="d3039-110">元素</span><span class="sxs-lookup"><span data-stu-id="d3039-110">Element</span></span>|<span data-ttu-id="d3039-111">描述</span><span class="sxs-lookup"><span data-stu-id="d3039-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3039-112">HTTPListener</span><span class="sxs-lookup"><span data-stu-id="d3039-112">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="d3039-113">自訂類別所使用的參數 <xref:System.Net.HttpListener> 。</span><span class="sxs-lookup"><span data-stu-id="d3039-113">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="d3039-114">HTTPWebRequest</span><span class="sxs-lookup"><span data-stu-id="d3039-114">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="d3039-115">自訂 Web 要求參數。</span><span class="sxs-lookup"><span data-stu-id="d3039-115">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="d3039-116">ipv4</span><span class="sxs-lookup"><span data-stu-id="d3039-116">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="d3039-117">啟用網際網路通訊協定第6版（IPv6）支援。</span><span class="sxs-lookup"><span data-stu-id="d3039-117">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="d3039-118">\<performanceCounter>元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="d3039-118">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="d3039-119">啟用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="d3039-119">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="d3039-120">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="d3039-120">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="d3039-121">設定網路資源的連接。</span><span class="sxs-lookup"><span data-stu-id="d3039-121">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="d3039-122">插槽</span><span class="sxs-lookup"><span data-stu-id="d3039-122">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="d3039-123">指定通訊端作業是否使用完成埠。</span><span class="sxs-lookup"><span data-stu-id="d3039-123">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="d3039-124">\<webProxyScript>元素（網路設定）</span><span class="sxs-lookup"><span data-stu-id="d3039-124">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="d3039-125">設定用來探索 Web proxy 之腳本的特性。</span><span class="sxs-lookup"><span data-stu-id="d3039-125">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d3039-126">父項目</span><span class="sxs-lookup"><span data-stu-id="d3039-126">Parent Elements</span></span>  
  
|<span data-ttu-id="d3039-127">元素</span><span class="sxs-lookup"><span data-stu-id="d3039-127">Element</span></span>|<span data-ttu-id="d3039-128">描述</span><span class="sxs-lookup"><span data-stu-id="d3039-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3039-129">system.net</span><span class="sxs-lookup"><span data-stu-id="d3039-129">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="d3039-130">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="d3039-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3039-131">備註</span><span class="sxs-lookup"><span data-stu-id="d3039-131">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d3039-132">組態檔</span><span class="sxs-lookup"><span data-stu-id="d3039-132">Configuration Files</span></span>  
 <span data-ttu-id="d3039-133">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="d3039-133">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3039-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3039-134">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="d3039-135">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="d3039-135">Network Settings Schema</span></span>](index.md)
