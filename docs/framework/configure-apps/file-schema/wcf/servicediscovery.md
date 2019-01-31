---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 564410fdc4085cc3ed14c394006551cddb028910
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267868"
---
# <a name="servicediscovery"></a><span data-ttu-id="2888e-101">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="2888e-101">\<serviceDiscovery></span></span>
<span data-ttu-id="2888e-102">指定服務端點的探索能力。</span><span class="sxs-lookup"><span data-stu-id="2888e-102">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="2888e-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2888e-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="2888e-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="2888e-104">\<behaviors></span></span>  
<span data-ttu-id="2888e-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="2888e-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="2888e-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="2888e-106">\<behavior></span></span>  
<span data-ttu-id="2888e-107">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="2888e-107">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2888e-108">語法</span><span class="sxs-lookup"><span data-stu-id="2888e-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2888e-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2888e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2888e-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2888e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2888e-111">屬性</span><span class="sxs-lookup"><span data-stu-id="2888e-111">Attributes</span></span>  
 <span data-ttu-id="2888e-112">無。</span><span class="sxs-lookup"><span data-stu-id="2888e-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2888e-113">子元素</span><span class="sxs-lookup"><span data-stu-id="2888e-113">Child Elements</span></span>  
  
|<span data-ttu-id="2888e-114">項目</span><span class="sxs-lookup"><span data-stu-id="2888e-114">Element</span></span>|<span data-ttu-id="2888e-115">描述</span><span class="sxs-lookup"><span data-stu-id="2888e-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2888e-116">\<announcementEndpoint></span><span class="sxs-lookup"><span data-stu-id="2888e-116">\<announcementEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|<span data-ttu-id="2888e-117">公告端點的集合。</span><span class="sxs-lookup"><span data-stu-id="2888e-117">A collection of announcement endpoints.</span></span> <span data-ttu-id="2888e-118">使用此區段指定用於傳送公告訊息的端點。</span><span class="sxs-lookup"><span data-stu-id="2888e-118">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="2888e-119">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="2888e-119">\<discoveryEndpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|<span data-ttu-id="2888e-120">探索端點的集合。</span><span class="sxs-lookup"><span data-stu-id="2888e-120">A collection of discovery endpoints.</span></span> <span data-ttu-id="2888e-121">使用此區段指定用於接聽探索訊息的端點。</span><span class="sxs-lookup"><span data-stu-id="2888e-121">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2888e-122">父項目</span><span class="sxs-lookup"><span data-stu-id="2888e-122">Parent Elements</span></span>  
  
|<span data-ttu-id="2888e-123">項目</span><span class="sxs-lookup"><span data-stu-id="2888e-123">Element</span></span>|<span data-ttu-id="2888e-124">描述</span><span class="sxs-lookup"><span data-stu-id="2888e-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2888e-125">\<behavior></span><span class="sxs-lookup"><span data-stu-id="2888e-125">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="2888e-126">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="2888e-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2888e-127">備註</span><span class="sxs-lookup"><span data-stu-id="2888e-127">Remarks</span></span>  
 <span data-ttu-id="2888e-128">加入至服務的行為組態時，這個組態項目會將該服務的所有端點標示為可探索。</span><span class="sxs-lookup"><span data-stu-id="2888e-128">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="2888e-129">您可以使用，以進一步設定這類端點的探索功能[ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)或是[ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)子項目。</span><span class="sxs-lookup"><span data-stu-id="2888e-129">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) or [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) child elements.</span></span> <span data-ttu-id="2888e-130">使用  [ \<announcementEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)一節，以指定用來傳送服務公告 （線上 /hello 與離線 /bye） 的端點組態，以設定公告。</span><span class="sxs-lookup"><span data-stu-id="2888e-130">Use the [\<announcementEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="2888e-131">使用[ \<discoveryEndpoint >](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)區段手動指定用於接聽探索訊息的端點。</span><span class="sxs-lookup"><span data-stu-id="2888e-131">Use the [\<discoveryEndpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2888e-132">範例</span><span class="sxs-lookup"><span data-stu-id="2888e-132">Example</span></span>  
 <span data-ttu-id="2888e-133">下列組態範例將 CalculatorService 指定為可探索，並且選擇性地指定要使用的公告端點。</span><span class="sxs-lookup"><span data-stu-id="2888e-133">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2888e-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2888e-134">See also</span></span>
- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
