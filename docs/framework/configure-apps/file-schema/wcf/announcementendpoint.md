---
title: '&lt;announcementEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
ms.openlocfilehash: 15d60cd277b77fd52b2b77bfcdf4d0da1de7167a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33351822"
---
# <a name="ltannouncementendpointgt"></a><span data-ttu-id="386ce-102">&lt;announcementEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="386ce-102">&lt;announcementEndpoint&gt;</span></span>
<span data-ttu-id="386ce-103">這個組態項目會定義具有固定公告合約的標準端點。</span><span class="sxs-lookup"><span data-stu-id="386ce-103">This configuration element defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="386ce-104">服務可以選擇性地公告其可用性，方法是分別在開啟與關閉該服務時傳送線上及離線公告訊息。</span><span class="sxs-lookup"><span data-stu-id="386ce-104">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="386ce-105">Windows Communication Foundation (WCF) 服務指定公告端點，在[ \<serviceDiscovery >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md)項目，並使用執行公告 AnnouncementClient。</span><span class="sxs-lookup"><span data-stu-id="386ce-105">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="386ce-106">用戶端想要從其他服務公告接聽實際上做為 WCF 服務。因此您必須在該用戶端設定公告端點[\<服務 >](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) > 一節。</span><span class="sxs-lookup"><span data-stu-id="386ce-106">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) section.</span></span>  
  
<span data-ttu-id="386ce-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="386ce-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="386ce-108">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="386ce-108">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="386ce-109">語法</span><span class="sxs-lookup"><span data-stu-id="386ce-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="386ce-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="386ce-110">Attributes and Elements</span></span>  
 <span data-ttu-id="386ce-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="386ce-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="386ce-112">屬性</span><span class="sxs-lookup"><span data-stu-id="386ce-112">Attributes</span></span>  
  
|<span data-ttu-id="386ce-113">屬性</span><span class="sxs-lookup"><span data-stu-id="386ce-113">Attribute</span></span>|<span data-ttu-id="386ce-114">描述</span><span class="sxs-lookup"><span data-stu-id="386ce-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="386ce-115">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="386ce-115">discoveryVersion</span></span>|<span data-ttu-id="386ce-116">字串，此字串會指定兩個 WS-Discovery 通訊協定版本的其中之一。</span><span class="sxs-lookup"><span data-stu-id="386ce-116">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="386ce-117">有效的值為 WSDiscovery11 和 WSDiscoveryApril2005。</span><span class="sxs-lookup"><span data-stu-id="386ce-117">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="386ce-118">這個值的型別為 <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>。</span><span class="sxs-lookup"><span data-stu-id="386ce-118">This value is of type <xref:System.ServiceModel.Discovery.Configuration.AnnouncementEndpointElement.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="386ce-119">maxAnnouncementDelay</span><span class="sxs-lookup"><span data-stu-id="386ce-119">maxAnnouncementDelay</span></span>|<span data-ttu-id="386ce-120">Timespan 值，這個值指定 Discovery 通訊協定傳送 Hello 訊息之前會等候的延遲值上限。</span><span class="sxs-lookup"><span data-stu-id="386ce-120">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending a Hello message.</span></span> <span data-ttu-id="386ce-121">系統會等候一段隨機時間值 (介於 0 和此屬性的值之間)，之後才傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="386ce-121">The messages will wait for a random time value between 0 and the value of this attribute before being sent.</span></span> <span data-ttu-id="386ce-122">這個屬性用於設定一小段隨機的延遲，避免網路關閉而所有服務同時再次上線時網路負荷過大。</span><span class="sxs-lookup"><span data-stu-id="386ce-122">This attribute is used to set a small, random delay to prevent network storms when a network goes out and all services come back online at the same time.</span></span>|  
|<span data-ttu-id="386ce-123">name</span><span class="sxs-lookup"><span data-stu-id="386ce-123">name</span></span>|<span data-ttu-id="386ce-124">字串，這個字串會指定標準端點之組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="386ce-124">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="386ce-125">這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。</span><span class="sxs-lookup"><span data-stu-id="386ce-125">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="386ce-126">子項目</span><span class="sxs-lookup"><span data-stu-id="386ce-126">Child Elements</span></span>  
 <span data-ttu-id="386ce-127">無。</span><span class="sxs-lookup"><span data-stu-id="386ce-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="386ce-128">父項目</span><span class="sxs-lookup"><span data-stu-id="386ce-128">Parent Elements</span></span>  
  
|<span data-ttu-id="386ce-129">項目</span><span class="sxs-lookup"><span data-stu-id="386ce-129">Element</span></span>|<span data-ttu-id="386ce-130">描述</span><span class="sxs-lookup"><span data-stu-id="386ce-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="386ce-131">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="386ce-131">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="386ce-132">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="386ce-132">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="386ce-133">範例</span><span class="sxs-lookup"><span data-stu-id="386ce-133">Example</span></span>  
 <span data-ttu-id="386ce-134">下列範例示範透過 http 及 peernet 接聽公告訊息的用戶端。</span><span class="sxs-lookup"><span data-stu-id="386ce-134">The following example demonstrates a client listening for announcements messages over http and peernet.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="386ce-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="386ce-135">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>
