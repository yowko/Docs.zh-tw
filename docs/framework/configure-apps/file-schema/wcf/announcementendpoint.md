---
title: <announcementEndpoint>
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: 4f3cf2748acc75b0ec83732664c5f97114f3663a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701251"
---
# <a name="announcementendpoint"></a><span data-ttu-id="7d505-101">\<announcementEndpoint></span><span class="sxs-lookup"><span data-stu-id="7d505-101">\<announcementEndpoint></span></span>
<span data-ttu-id="7d505-102">這個組態項目會定義具有固定公告合約的標準端點。</span><span class="sxs-lookup"><span data-stu-id="7d505-102">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="7d505-103">服務可以選擇性地公告其可用性，方法是分別在開啟與關閉該服務時傳送線上及離線公告訊息。</span><span class="sxs-lookup"><span data-stu-id="7d505-103">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="7d505-104">Windows Communication Foundation (WCF) 服務指定公告端點，在[ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)項目，並且使用 AnnouncementClient 來執行公告。</span><span class="sxs-lookup"><span data-stu-id="7d505-104">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="7d505-105">想要從其他服務公告所接聽的用戶端實際上做為 WCF 服務;因此您必須在該用戶端設定公告端點[ \<services >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)一節。</span><span class="sxs-lookup"><span data-stu-id="7d505-105">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section.</span></span>  
  
<span data-ttu-id="7d505-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7d505-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="7d505-107">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="7d505-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d505-108">語法</span><span class="sxs-lookup"><span data-stu-id="7d505-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <announcementEndpoint>
      <standardEndpoint discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxAnnouncementDelay="Timespan"
                        name="String" />
    </announcementEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d505-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7d505-109">Attributes and Elements</span></span>  
 <span data-ttu-id="7d505-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7d505-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d505-111">屬性</span><span class="sxs-lookup"><span data-stu-id="7d505-111">Attributes</span></span>  
  
|<span data-ttu-id="7d505-112">屬性</span><span class="sxs-lookup"><span data-stu-id="7d505-112">Attribute</span></span>|<span data-ttu-id="7d505-113">描述</span><span class="sxs-lookup"><span data-stu-id="7d505-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7d505-114">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="7d505-114">discoveryVersion</span></span>|<span data-ttu-id="7d505-115">字串，此字串會指定兩個 WS-Discovery 通訊協定版本的其中之一。</span><span class="sxs-lookup"><span data-stu-id="7d505-115">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="7d505-116">有效的值為 WSDiscovery11 和 WSDiscoveryApril2005。</span><span class="sxs-lookup"><span data-stu-id="7d505-116">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="7d505-117">這個值的型別為 <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>。</span><span class="sxs-lookup"><span data-stu-id="7d505-117">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="7d505-118">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="7d505-118">maxAnnouncementDelay</span></span>|<span data-ttu-id="7d505-119">Timespan 值，這個值指定 Discovery 通訊協定傳送 Hello 訊息之前會等候的延遲值上限。</span><span class="sxs-lookup"><span data-stu-id="7d505-119">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="7d505-120">系統會等候一段隨機時間值 (介於 0 和此屬性的值之間)，之後才傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="7d505-120">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="7d505-121">這個屬性用於設定一小段隨機的延遲，避免網路關閉而所有服務同時再次上線時網路負荷過大。</span><span class="sxs-lookup"><span data-stu-id="7d505-121">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="7d505-122">名稱</span><span class="sxs-lookup"><span data-stu-id="7d505-122">name</span></span>|<span data-ttu-id="7d505-123">字串，這個字串會指定標準端點之組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="7d505-123">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="7d505-124">這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。</span><span class="sxs-lookup"><span data-stu-id="7d505-124">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d505-125">子元素</span><span class="sxs-lookup"><span data-stu-id="7d505-125">Child Elements</span></span>  
 <span data-ttu-id="7d505-126">無。</span><span class="sxs-lookup"><span data-stu-id="7d505-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7d505-127">父項目</span><span class="sxs-lookup"><span data-stu-id="7d505-127">Parent Elements</span></span>  
  
|<span data-ttu-id="7d505-128">項目</span><span class="sxs-lookup"><span data-stu-id="7d505-128">Element</span></span>|<span data-ttu-id="7d505-129">描述</span><span class="sxs-lookup"><span data-stu-id="7d505-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d505-130">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="7d505-130">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="7d505-131">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="7d505-131">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7d505-132">範例</span><span class="sxs-lookup"><span data-stu-id="7d505-132">Example</span></span>  
 <span data-ttu-id="7d505-133">下列範例示範透過 http 及 peernet 接聽公告訊息的用戶端。</span><span class="sxs-lookup"><span data-stu-id="7d505-133">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
```xml  
<services>
  <service name="ServiceAnnouncementListener">
    <endpoint name="httpAnnouncementEndpoint"
              kind="announcementEndpoint"
              binding="basicHttpBinding"
              address="announcements" />
    <endpoint name="peerNetAnnouncementEndpoint"
              kind="announcementEndpoint"
              binding="peerTcpBinding"
              address="net.p2p://discoveryMesh/multicast"
              bindingConfiguration="discoveryPeerTcpBindingConfig" />
  ...
  </service>
</services>

<standardEndpoints>
  <announcementEndpoint>
    <standardEndpoint name="httpAnnouncementEndpoint"
                      version="WSDiscoveryApril2005" />
    <standardEndpoint name="peerNetAnnouncementEndpoint"
                      version="WSDiscoveryApril2005" />
  </announcementEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="7d505-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d505-134">See also</span></span>

- <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
