---
title: '&lt;serviceDiscovery&gt;'
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 78f1c7be1d8285cd2fdf79af1e1220a7e48b2893
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751242"
---
# <a name="ltservicediscoverygt"></a><span data-ttu-id="3d0bb-102">&lt;serviceDiscovery&gt;</span><span class="sxs-lookup"><span data-stu-id="3d0bb-102">&lt;serviceDiscovery&gt;</span></span>
<span data-ttu-id="3d0bb-103">指定服務端點的探索能力。</span><span class="sxs-lookup"><span data-stu-id="3d0bb-103">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="3d0bb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3d0bb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3d0bb-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="3d0bb-105">\<behaviors></span></span>  
<span data-ttu-id="3d0bb-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="3d0bb-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="3d0bb-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="3d0bb-107">\<behavior></span></span>  
<span data-ttu-id="3d0bb-108">\<serviceDiscovery ></span><span class="sxs-lookup"><span data-stu-id="3d0bb-108">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d0bb-109">語法</span><span class="sxs-lookup"><span data-stu-id="3d0bb-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3d0bb-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3d0bb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3d0bb-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3d0bb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3d0bb-112">屬性</span><span class="sxs-lookup"><span data-stu-id="3d0bb-112">Attributes</span></span>  
 <span data-ttu-id="3d0bb-113">無。</span><span class="sxs-lookup"><span data-stu-id="3d0bb-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3d0bb-114">子項目</span><span class="sxs-lookup"><span data-stu-id="3d0bb-114">Child Elements</span></span>  
  
|<span data-ttu-id="3d0bb-115">項目</span><span class="sxs-lookup"><span data-stu-id="3d0bb-115">Element</span></span>|<span data-ttu-id="3d0bb-116">描述</span><span class="sxs-lookup"><span data-stu-id="3d0bb-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3d0bb-117">\<announcementEndpoint ></span><span class="sxs-lookup"><span data-stu-id="3d0bb-117">\<announcementEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|<span data-ttu-id="3d0bb-118">公告端點的集合。</span><span class="sxs-lookup"><span data-stu-id="3d0bb-118">A collection of announcement endpoints.</span></span> <span data-ttu-id="3d0bb-119">使用此區段指定用於傳送公告訊息的端點。</span><span class="sxs-lookup"><span data-stu-id="3d0bb-119">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="3d0bb-120">\<discoveryEndpoint ></span><span class="sxs-lookup"><span data-stu-id="3d0bb-120">\<discoveryEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|<span data-ttu-id="3d0bb-121">探索端點的集合。</span><span class="sxs-lookup"><span data-stu-id="3d0bb-121">A collection of discovery endpoints.</span></span> <span data-ttu-id="3d0bb-122">使用此區段指定用於接聽探索訊息的端點。</span><span class="sxs-lookup"><span data-stu-id="3d0bb-122">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3d0bb-123">父項目</span><span class="sxs-lookup"><span data-stu-id="3d0bb-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3d0bb-124">項目</span><span class="sxs-lookup"><span data-stu-id="3d0bb-124">Element</span></span>|<span data-ttu-id="3d0bb-125">描述</span><span class="sxs-lookup"><span data-stu-id="3d0bb-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3d0bb-126">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="3d0bb-126">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="3d0bb-127">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="3d0bb-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3d0bb-128">備註</span><span class="sxs-lookup"><span data-stu-id="3d0bb-128">Remarks</span></span>  
 <span data-ttu-id="3d0bb-129">加入至服務的行為組態時，這個組態項目會將該服務的所有端點標示為可探索。</span><span class="sxs-lookup"><span data-stu-id="3d0bb-129">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="3d0bb-130">您可以使用，以進一步設定這類端點的探索功能[ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)或[ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)子項目。</span><span class="sxs-lookup"><span data-stu-id="3d0bb-130">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) or [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) child elements.</span></span> <span data-ttu-id="3d0bb-131">使用[ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)區段，即可藉由指定用來傳送 （線上/Hello 和 Bye 離線/） 的服務公告端點組態設定的公告。</span><span class="sxs-lookup"><span data-stu-id="3d0bb-131">Use the [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="3d0bb-132">使用[ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)區段，以手動指定要接聽探索訊息的端點。</span><span class="sxs-lookup"><span data-stu-id="3d0bb-132">Use the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d0bb-133">範例</span><span class="sxs-lookup"><span data-stu-id="3d0bb-133">Example</span></span>  
 <span data-ttu-id="3d0bb-134">下列組態範例將 CalculatorService 指定為可探索，並且選擇性地指定要使用的公告端點。</span><span class="sxs-lookup"><span data-stu-id="3d0bb-134">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3d0bb-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d0bb-135">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
