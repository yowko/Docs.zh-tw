---
title: <udpAnnouncementEndpoint>
ms.date: 03/30/2017
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
ms.openlocfilehash: 04f5fb27a0da7e553ff3c0308f7fb2e2df2e0b20
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59210005"
---
# <a name="udpannouncementendpoint"></a><span data-ttu-id="dd549-101">\<udpAnnouncementEndpoint></span><span class="sxs-lookup"><span data-stu-id="dd549-101">\<udpAnnouncementEndpoint></span></span>
<span data-ttu-id="dd549-102">這個組態項目會定義標準端點，服務會使用此端點透過 UDP 繫結傳送公告訊息。</span><span class="sxs-lookup"><span data-stu-id="dd549-102">This configuration element defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="dd549-103">此端點具備固定合約，而且支援兩種探索版本。</span><span class="sxs-lookup"><span data-stu-id="dd549-103">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="dd549-104">此外，它擁有固定的 UDP 繫結和預設位址值，如 WS-Discovery 規格 (WS-Discovery 2005 年 4 月或 WS-Discovery 1.1 版) 中所指定。</span><span class="sxs-lookup"><span data-stu-id="dd549-104">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="dd549-105">您可以指定傳送及接收公告訊息時所使用的多點傳送位址。</span><span class="sxs-lookup"><span data-stu-id="dd549-105">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>  
  
<span data-ttu-id="dd549-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dd549-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="dd549-107">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="dd549-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd549-108">語法</span><span class="sxs-lookup"><span data-stu-id="dd549-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd549-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dd549-109">Attributes and Elements</span></span>  
 <span data-ttu-id="dd549-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="dd549-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd549-111">屬性</span><span class="sxs-lookup"><span data-stu-id="dd549-111">Attributes</span></span>  
  
|<span data-ttu-id="dd549-112">屬性</span><span class="sxs-lookup"><span data-stu-id="dd549-112">Attribute</span></span>|<span data-ttu-id="dd549-113">描述</span><span class="sxs-lookup"><span data-stu-id="dd549-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd549-114">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="dd549-114">discoveryVersion</span></span>|<span data-ttu-id="dd549-115">字串，此字串會指定兩個 WS-Discovery 通訊協定版本的其中之一。</span><span class="sxs-lookup"><span data-stu-id="dd549-115">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="dd549-116">有效的值為 WSDiscovery11 和 WSDiscoveryApril2005。</span><span class="sxs-lookup"><span data-stu-id="dd549-116">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="dd549-117">這個值的型別為 <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>。</span><span class="sxs-lookup"><span data-stu-id="dd549-117">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="dd549-118">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="dd549-118">maxAnnouncementDelay</span></span>|<span data-ttu-id="dd549-119">Timespan 值，這個值指定 Discovery 通訊協定傳送 Hello 訊息之前會等候的延遲值上限。</span><span class="sxs-lookup"><span data-stu-id="dd549-119">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="dd549-120">系統會等候一段隨機時間值 (介於 0 和此屬性的值之間)，之後才傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="dd549-120">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="dd549-121">這個屬性用於設定一小段隨機的延遲，避免網路關閉而所有服務同時再次上線時網路負荷過大。</span><span class="sxs-lookup"><span data-stu-id="dd549-121">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="dd549-122">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="dd549-122">multicastAddress</span></span>|<span data-ttu-id="dd549-123">URI，這個 URI 會指定傳送及接收探索訊息時所使用的多點傳送位址。</span><span class="sxs-lookup"><span data-stu-id="dd549-123">A URI that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="dd549-124">預設值是與通訊協定規格一致的多點傳送位址。</span><span class="sxs-lookup"><span data-stu-id="dd549-124">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|<span data-ttu-id="dd549-125">名稱</span><span class="sxs-lookup"><span data-stu-id="dd549-125">name</span></span>|<span data-ttu-id="dd549-126">字串，這個字串會指定標準端點之組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="dd549-126">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="dd549-127">這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。</span><span class="sxs-lookup"><span data-stu-id="dd549-127">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd549-128">子元素</span><span class="sxs-lookup"><span data-stu-id="dd549-128">Child Elements</span></span>  
  
|<span data-ttu-id="dd549-129">項目</span><span class="sxs-lookup"><span data-stu-id="dd549-129">Element</span></span>|<span data-ttu-id="dd549-130">描述</span><span class="sxs-lookup"><span data-stu-id="dd549-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd549-131">\<udpTransportSettings></span><span class="sxs-lookup"><span data-stu-id="dd549-131">\<udpTransportSettings></span></span>](udptransportsettings.md)|<span data-ttu-id="dd549-132">設定的集合，可讓您設定 UDP 端點的 UDP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="dd549-132">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dd549-133">父項目</span><span class="sxs-lookup"><span data-stu-id="dd549-133">Parent Elements</span></span>  
  
|<span data-ttu-id="dd549-134">項目</span><span class="sxs-lookup"><span data-stu-id="dd549-134">Element</span></span>|<span data-ttu-id="dd549-135">描述</span><span class="sxs-lookup"><span data-stu-id="dd549-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd549-136">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="dd549-136">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="dd549-137">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="dd549-137">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="dd549-138">範例</span><span class="sxs-lookup"><span data-stu-id="dd549-138">Example</span></span>  
 <span data-ttu-id="dd549-139">下列範例示範透過具預設多點傳送位址的 UDP 多點傳送傳輸與具指定多點傳送位址的 UDP 多點傳送傳輸接聽公告的用戶端。</span><span class="sxs-lookup"><span data-stu-id="dd549-139">The following example demonstrates a client listening for announcement over a UDP multicast transport with default multicast address, and UDP multicast transport with specified multicast address.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dd549-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dd549-140">See also</span></span>

- <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>
