---
title: <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: 8dabf8845126705d082d080b643688ed62883f39
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854910"
---
# <a name="udpannouncementendpoint"></a><span data-ttu-id="756d6-101">\<udpAnnouncementEndpoint></span><span class="sxs-lookup"><span data-stu-id="756d6-101">\<udpAnnouncementEndpoint></span></span>
<span data-ttu-id="756d6-102">這個組態項目會定義標準端點，服務會使用此端點透過 UDP 繫結傳送公告訊息。</span><span class="sxs-lookup"><span data-stu-id="756d6-102">This configuration element defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="756d6-103">此端點具備固定合約，而且支援兩種探索版本。</span><span class="sxs-lookup"><span data-stu-id="756d6-103">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="756d6-104">此外，它擁有固定的 UDP 繫結和預設位址值，如 WS-Discovery 規格 (WS-Discovery 2005 年 4 月或 WS-Discovery 1.1 版) 中所指定。</span><span class="sxs-lookup"><span data-stu-id="756d6-104">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="756d6-105">您可以指定傳送及接收公告訊息時所使用的多點傳送位址。</span><span class="sxs-lookup"><span data-stu-id="756d6-105">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>  
  
<span data-ttu-id="756d6-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="756d6-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="756d6-107">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="756d6-107">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="756d6-108">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="756d6-108">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="756d6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Udptransportsettings >**</span><span class="sxs-lookup"><span data-stu-id="756d6-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpAnnouncementEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="756d6-110">語法</span><span class="sxs-lookup"><span data-stu-id="756d6-110">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxAnnouncementDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="756d6-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="756d6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="756d6-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="756d6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="756d6-113">屬性</span><span class="sxs-lookup"><span data-stu-id="756d6-113">Attributes</span></span>  
  
|<span data-ttu-id="756d6-114">屬性</span><span class="sxs-lookup"><span data-stu-id="756d6-114">Attribute</span></span>|<span data-ttu-id="756d6-115">說明</span><span class="sxs-lookup"><span data-stu-id="756d6-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="756d6-116">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="756d6-116">discoveryVersion</span></span>|<span data-ttu-id="756d6-117">字串，此字串會指定兩個 WS-Discovery 通訊協定版本的其中之一。</span><span class="sxs-lookup"><span data-stu-id="756d6-117">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="756d6-118">有效的值為 WSDiscovery11 和 WSDiscoveryApril2005。</span><span class="sxs-lookup"><span data-stu-id="756d6-118">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="756d6-119">這個值的型別為 <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>。</span><span class="sxs-lookup"><span data-stu-id="756d6-119">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="756d6-120">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="756d6-120">maxAnnouncementDelay</span></span>|<span data-ttu-id="756d6-121">Timespan 值，這個值指定 Discovery 通訊協定傳送 Hello 訊息之前會等候的延遲值上限。</span><span class="sxs-lookup"><span data-stu-id="756d6-121">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="756d6-122">系統會等候一段隨機時間值 (介於 0 和此屬性的值之間)，之後才傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="756d6-122">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="756d6-123">這個屬性用於設定一小段隨機的延遲，避免網路關閉而所有服務同時再次上線時網路負荷過大。</span><span class="sxs-lookup"><span data-stu-id="756d6-123">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="756d6-124">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="756d6-124">multicastAddress</span></span>|<span data-ttu-id="756d6-125">URI，這個 URI 會指定傳送及接收探索訊息時所使用的多點傳送位址。</span><span class="sxs-lookup"><span data-stu-id="756d6-125">A URI that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="756d6-126">預設值是與通訊協定規格一致的多點傳送位址。</span><span class="sxs-lookup"><span data-stu-id="756d6-126">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|<span data-ttu-id="756d6-127">NAME</span><span class="sxs-lookup"><span data-stu-id="756d6-127">name</span></span>|<span data-ttu-id="756d6-128">字串，這個字串會指定標準端點之組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="756d6-128">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="756d6-129">這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。</span><span class="sxs-lookup"><span data-stu-id="756d6-129">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="756d6-130">子元素</span><span class="sxs-lookup"><span data-stu-id="756d6-130">Child Elements</span></span>  
  
|<span data-ttu-id="756d6-131">項目</span><span class="sxs-lookup"><span data-stu-id="756d6-131">Element</span></span>|<span data-ttu-id="756d6-132">描述</span><span class="sxs-lookup"><span data-stu-id="756d6-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="756d6-133">\<udpTransportSettings></span><span class="sxs-lookup"><span data-stu-id="756d6-133">\<udpTransportSettings></span></span>](udptransportsettings.md)|<span data-ttu-id="756d6-134">設定的集合，可讓您設定 UDP 端點的 UDP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="756d6-134">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="756d6-135">父項目</span><span class="sxs-lookup"><span data-stu-id="756d6-135">Parent Elements</span></span>  
  
|<span data-ttu-id="756d6-136">項目</span><span class="sxs-lookup"><span data-stu-id="756d6-136">Element</span></span>|<span data-ttu-id="756d6-137">描述</span><span class="sxs-lookup"><span data-stu-id="756d6-137">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="756d6-138">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="756d6-138">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="756d6-139">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="756d6-139">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="756d6-140">範例</span><span class="sxs-lookup"><span data-stu-id="756d6-140">Example</span></span>  
 <span data-ttu-id="756d6-141">下列範例示範透過具預設多點傳送位址的 UDP 多點傳送傳輸與具指定多點傳送位址的 UDP 多點傳送傳輸接聽公告的用戶端。</span><span class="sxs-lookup"><span data-stu-id="756d6-141">The following example demonstrates a client listening for announcement over a UDP multicast transport with default multicast address, and UDP multicast transport with specified multicast address.</span></span>  
  
```xml  
<services>
  <service name="ServiceAnnouncementListener">
    <endpoint name="udpAnnouncementEndpointStandard"
              kind="udpAnnouncementEndpoint"
              bindingConfiguration="..." />
    <endpoint name="udpAnnouncementEndpoint2"
              kind="udpAnnouncementEndpoint"
              endpointConfiguration="AnnouncementConfiguration3702"
              bindingConfiguration="..." />
    ...
  </service>
</services>
<standardEndpoints>
  <udpAnnouncementEndpoint>
    <standardEndpoint name="AnnouncementConfiguration2"
                      version="WSDiscoveryApril2005"
                      multicastAddress="soap.udp://239.255.255.250:3703"/>
  </udpAnnouncementEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="756d6-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="756d6-142">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
