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
ms.openlocfilehash: c5fe0b9eccd1c429c0041fcfab06b0cc20a20aa2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91167271"
---
# <a name="settings-element-network-settings"></a><span data-ttu-id="f4f6c-102">\<settings> 項目 (網路設定)</span><span class="sxs-lookup"><span data-stu-id="f4f6c-102">\<settings> Element (Network Settings)</span></span>

<span data-ttu-id="f4f6c-103">為 <xref:System.Net?displayProperty=nameWithType> 命名空間設定基本的網路選項。</span><span class="sxs-lookup"><span data-stu-id="f4f6c-103">Configures basic network options for the <xref:System.Net?displayProperty=nameWithType> namespace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<settings>**

## <a name="syntax"></a><span data-ttu-id="f4f6c-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="f4f6c-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f4f6c-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f4f6c-105">Attributes and Elements</span></span>  

 <span data-ttu-id="f4f6c-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f4f6c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f4f6c-107">屬性</span><span class="sxs-lookup"><span data-stu-id="f4f6c-107">Attributes</span></span>  

 <span data-ttu-id="f4f6c-108">無。</span><span class="sxs-lookup"><span data-stu-id="f4f6c-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="f4f6c-109">子元素</span><span class="sxs-lookup"><span data-stu-id="f4f6c-109">Child Elements</span></span>  
  
|<span data-ttu-id="f4f6c-110">項目</span><span class="sxs-lookup"><span data-stu-id="f4f6c-110">Element</span></span>|<span data-ttu-id="f4f6c-111">描述</span><span class="sxs-lookup"><span data-stu-id="f4f6c-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4f6c-112">HTTPListener</span><span class="sxs-lookup"><span data-stu-id="f4f6c-112">httpListener</span></span>](httplistener-element-network-settings.md)|<span data-ttu-id="f4f6c-113">自訂類別使用的參數 <xref:System.Net.HttpListener> 。</span><span class="sxs-lookup"><span data-stu-id="f4f6c-113">Customizes parameters used by the <xref:System.Net.HttpListener> class.</span></span>|  
|[<span data-ttu-id="f4f6c-114">HTTPWebRequest</span><span class="sxs-lookup"><span data-stu-id="f4f6c-114">httpWebRequest</span></span>](httpwebrequest-element-network-settings.md)|<span data-ttu-id="f4f6c-115">自訂 Web 要求參數。</span><span class="sxs-lookup"><span data-stu-id="f4f6c-115">Customizes Web request parameters.</span></span>|  
|[<span data-ttu-id="f4f6c-116">ipv6</span><span class="sxs-lookup"><span data-stu-id="f4f6c-116">ipv6</span></span>](ipv6-element-network-settings.md)|<span data-ttu-id="f4f6c-117">啟用網際網路通訊協定第6版 (IPv6) 支援。</span><span class="sxs-lookup"><span data-stu-id="f4f6c-117">Enables Internet Protocol version 6 (IPv6) support.</span></span>|  
|[<span data-ttu-id="f4f6c-118">\<performanceCounter> (網路設定的元素) </span><span class="sxs-lookup"><span data-stu-id="f4f6c-118">\<performanceCounter> Element (Network Settings)</span></span>](performancecounter-element-network-settings.md)|<span data-ttu-id="f4f6c-119">啟用網路效能計數器。</span><span class="sxs-lookup"><span data-stu-id="f4f6c-119">Enables network performance counters.</span></span>|  
|[<span data-ttu-id="f4f6c-120">servicePointManager</span><span class="sxs-lookup"><span data-stu-id="f4f6c-120">servicePointManager</span></span>](servicepointmanager-element-network-settings.md)|<span data-ttu-id="f4f6c-121">設定網路資源的連接。</span><span class="sxs-lookup"><span data-stu-id="f4f6c-121">Configures connections to network resources.</span></span>|  
|[<span data-ttu-id="f4f6c-122">插座</span><span class="sxs-lookup"><span data-stu-id="f4f6c-122">socket</span></span>](socket-element-network-settings.md)|<span data-ttu-id="f4f6c-123">指定通訊端作業是否使用完成埠。</span><span class="sxs-lookup"><span data-stu-id="f4f6c-123">Specifies whether socket operations use completion ports.</span></span>|  
|[<span data-ttu-id="f4f6c-124">\<webProxyScript> (網路設定的元素) </span><span class="sxs-lookup"><span data-stu-id="f4f6c-124">\<webProxyScript> Element (Network Settings)</span></span>](webproxyscript-element-network-settings.md)|<span data-ttu-id="f4f6c-125">設定用來探索 Web proxy 的腳本特性。</span><span class="sxs-lookup"><span data-stu-id="f4f6c-125">Configures the characteristics of the script used to discover Web proxies.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f4f6c-126">父項目</span><span class="sxs-lookup"><span data-stu-id="f4f6c-126">Parent Elements</span></span>  
  
|<span data-ttu-id="f4f6c-127">項目</span><span class="sxs-lookup"><span data-stu-id="f4f6c-127">Element</span></span>|<span data-ttu-id="f4f6c-128">描述</span><span class="sxs-lookup"><span data-stu-id="f4f6c-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f4f6c-129">system.net</span><span class="sxs-lookup"><span data-stu-id="f4f6c-129">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="f4f6c-130">包含會指定 .NET Framework 如何連接至網路的設定。</span><span class="sxs-lookup"><span data-stu-id="f4f6c-130">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4f6c-131">備註</span><span class="sxs-lookup"><span data-stu-id="f4f6c-131">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="f4f6c-132">組態檔</span><span class="sxs-lookup"><span data-stu-id="f4f6c-132">Configuration Files</span></span>  

 <span data-ttu-id="f4f6c-133">此項目可以用於應用程式組態檔或電腦組態檔 (Machine.config)。</span><span class="sxs-lookup"><span data-stu-id="f4f6c-133">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4f6c-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4f6c-134">See also</span></span>

- <xref:System.Net?displayProperty=nameWithType>
- [<span data-ttu-id="f4f6c-135">網路設定結構描述</span><span class="sxs-lookup"><span data-stu-id="f4f6c-135">Network Settings Schema</span></span>](index.md)
