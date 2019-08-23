---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: a99edd3a62a40c2efbc63a166b8c0b0d124e8a72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936279"
---
# <a name="servicediscovery"></a><span data-ttu-id="1cd44-101">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="1cd44-101">\<serviceDiscovery></span></span>
<span data-ttu-id="1cd44-102">指定服務端點的探索能力。</span><span class="sxs-lookup"><span data-stu-id="1cd44-102">Specifies the discoverability of service endpoints.</span></span>  
  
 <span data-ttu-id="1cd44-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1cd44-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="1cd44-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="1cd44-104">\<behaviors></span></span>  
<span data-ttu-id="1cd44-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="1cd44-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="1cd44-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="1cd44-106">\<behavior></span></span>  
<span data-ttu-id="1cd44-107">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="1cd44-107">\<serviceDiscovery></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cd44-108">語法</span><span class="sxs-lookup"><span data-stu-id="1cd44-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1cd44-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1cd44-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1cd44-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1cd44-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1cd44-111">屬性</span><span class="sxs-lookup"><span data-stu-id="1cd44-111">Attributes</span></span>  
 <span data-ttu-id="1cd44-112">無。</span><span class="sxs-lookup"><span data-stu-id="1cd44-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1cd44-113">子元素</span><span class="sxs-lookup"><span data-stu-id="1cd44-113">Child Elements</span></span>  
  
|<span data-ttu-id="1cd44-114">項目</span><span class="sxs-lookup"><span data-stu-id="1cd44-114">Element</span></span>|<span data-ttu-id="1cd44-115">描述</span><span class="sxs-lookup"><span data-stu-id="1cd44-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1cd44-116">\<announcementEndpoint></span><span class="sxs-lookup"><span data-stu-id="1cd44-116">\<announcementEndpoint></span></span>](announcementendpoint.md)|<span data-ttu-id="1cd44-117">公告端點的集合。</span><span class="sxs-lookup"><span data-stu-id="1cd44-117">A collection of announcement endpoints.</span></span> <span data-ttu-id="1cd44-118">使用此區段指定用於傳送公告訊息的端點。</span><span class="sxs-lookup"><span data-stu-id="1cd44-118">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="1cd44-119">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="1cd44-119">\<discoveryEndpoint></span></span>](discoveryendpoint.md)|<span data-ttu-id="1cd44-120">探索端點的集合。</span><span class="sxs-lookup"><span data-stu-id="1cd44-120">A collection of discovery endpoints.</span></span> <span data-ttu-id="1cd44-121">使用此區段指定用於接聽探索訊息的端點。</span><span class="sxs-lookup"><span data-stu-id="1cd44-121">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1cd44-122">父項目</span><span class="sxs-lookup"><span data-stu-id="1cd44-122">Parent Elements</span></span>  
  
|<span data-ttu-id="1cd44-123">項目</span><span class="sxs-lookup"><span data-stu-id="1cd44-123">Element</span></span>|<span data-ttu-id="1cd44-124">描述</span><span class="sxs-lookup"><span data-stu-id="1cd44-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1cd44-125">\<behavior></span><span class="sxs-lookup"><span data-stu-id="1cd44-125">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="1cd44-126">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="1cd44-126">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1cd44-127">備註</span><span class="sxs-lookup"><span data-stu-id="1cd44-127">Remarks</span></span>  
 <span data-ttu-id="1cd44-128">加入至服務的行為組態時，這個組態項目會將該服務的所有端點標示為可探索。</span><span class="sxs-lookup"><span data-stu-id="1cd44-128">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="1cd44-129">您可以使用[ \<discoveryEndpoint >](discoveryendpoint.md)或[ \<announcementEndpoint >](announcementendpoint.md)子項目, 進一步設定這類端點的探索功能。</span><span class="sxs-lookup"><span data-stu-id="1cd44-129">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="1cd44-130">使用[announcementEndpoint > 區段來設定通知, 方法是指定要用來傳送服務宣告 (online/Hello 和 offline/再見) 的端點設定。 \< ](announcementendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="1cd44-130">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="1cd44-131">使用 [ [ \<discoveryEndpoint >](discoveryendpoint.md) ] 區段, 以手動方式指定要接聽探索訊息的端點。</span><span class="sxs-lookup"><span data-stu-id="1cd44-131">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1cd44-132">範例</span><span class="sxs-lookup"><span data-stu-id="1cd44-132">Example</span></span>  
 <span data-ttu-id="1cd44-133">下列組態範例將 CalculatorService 指定為可探索，並且選擇性地指定要使用的公告端點。</span><span class="sxs-lookup"><span data-stu-id="1cd44-133">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1cd44-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cd44-134">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
