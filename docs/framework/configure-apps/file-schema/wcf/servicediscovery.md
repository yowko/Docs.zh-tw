---
title: '&lt;serviceDiscovery&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9bdd16e02742baa14d1ebd11ea95591df7093705
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltservicediscoverygt"></a><span data-ttu-id="516ee-102">&lt;serviceDiscovery&gt;</span><span class="sxs-lookup"><span data-stu-id="516ee-102">&lt;serviceDiscovery&gt;</span></span>
<span data-ttu-id="516ee-103">指定服務端點的探索能力。</span><span class="sxs-lookup"><span data-stu-id="516ee-103">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="516ee-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="516ee-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="516ee-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="516ee-105">\<behaviors></span></span>  
<span data-ttu-id="516ee-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="516ee-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="516ee-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="516ee-107">\<behavior></span></span>  
<span data-ttu-id="516ee-108">\<serviceDiscovery ></span><span class="sxs-lookup"><span data-stu-id="516ee-108">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="516ee-109">語法</span><span class="sxs-lookup"><span data-stu-id="516ee-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint name="String" 
                    kind="Type" />
        </announcementEndpoints>
        <discoveryEndpoints>
          <endpoint name="String" 
                    kind="Type" />
        </discoveryEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="516ee-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="516ee-110">Attributes and Elements</span></span>  
 <span data-ttu-id="516ee-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="516ee-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="516ee-112">屬性</span><span class="sxs-lookup"><span data-stu-id="516ee-112">Attributes</span></span>  
 <span data-ttu-id="516ee-113">無。</span><span class="sxs-lookup"><span data-stu-id="516ee-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="516ee-114">子項目</span><span class="sxs-lookup"><span data-stu-id="516ee-114">Child Elements</span></span>  
  
|<span data-ttu-id="516ee-115">項目</span><span class="sxs-lookup"><span data-stu-id="516ee-115">Element</span></span>|<span data-ttu-id="516ee-116">說明</span><span class="sxs-lookup"><span data-stu-id="516ee-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="516ee-117">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="516ee-117">\<announcementEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|<span data-ttu-id="516ee-118">公告端點的集合。</span><span class="sxs-lookup"><span data-stu-id="516ee-118">A collection of announcement endpoints.</span></span> <span data-ttu-id="516ee-119">使用此區段指定用於傳送公告訊息的端點。</span><span class="sxs-lookup"><span data-stu-id="516ee-119">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="516ee-120">\<discoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="516ee-120">\<discoveryEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|<span data-ttu-id="516ee-121">探索端點的集合。</span><span class="sxs-lookup"><span data-stu-id="516ee-121">A collection of discovery endpoints.</span></span> <span data-ttu-id="516ee-122">使用此區段指定用於接聽探索訊息的端點。</span><span class="sxs-lookup"><span data-stu-id="516ee-122">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="516ee-123">父項目</span><span class="sxs-lookup"><span data-stu-id="516ee-123">Parent Elements</span></span>  
  
|<span data-ttu-id="516ee-124">項目</span><span class="sxs-lookup"><span data-stu-id="516ee-124">Element</span></span>|<span data-ttu-id="516ee-125">說明</span><span class="sxs-lookup"><span data-stu-id="516ee-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="516ee-126">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="516ee-126">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="516ee-127">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="516ee-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="516ee-128">備註</span><span class="sxs-lookup"><span data-stu-id="516ee-128">Remarks</span></span>  
 <span data-ttu-id="516ee-129">加入至服務的行為組態時，這個組態項目會將該服務的所有端點標示為可探索。</span><span class="sxs-lookup"><span data-stu-id="516ee-129">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="516ee-130">您可以使用，以進一步設定這類端點的探索功能[ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)或[ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)子項目。</span><span class="sxs-lookup"><span data-stu-id="516ee-130">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) or [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) child elements.</span></span> <span data-ttu-id="516ee-131">使用[ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)區段，即可藉由指定用來傳送 （線上/Hello 和 Bye 離線/） 的服務公告端點組態設定的公告。</span><span class="sxs-lookup"><span data-stu-id="516ee-131">Use the [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="516ee-132">使用[ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)區段，以手動指定要接聽探索訊息的端點。</span><span class="sxs-lookup"><span data-stu-id="516ee-132">Use the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="516ee-133">範例</span><span class="sxs-lookup"><span data-stu-id="516ee-133">Example</span></span>  
 <span data-ttu-id="516ee-134">下列組態範例將 CalculatorService 指定為可探索，並且選擇性地指定要使用的公告端點。</span><span class="sxs-lookup"><span data-stu-id="516ee-134">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
```xml  
<services>  
  <service name="CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
  ...  
  </service>  
</services>  
  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDiscovery>  
        <announcementEndpoints>  
              <endpoint name="udpEndpoint"  
                        kind="udpAnnouncementEndpoint" />  
        </announcementEndpoints>  
      </serviceDiscovery>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="516ee-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="516ee-135">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
