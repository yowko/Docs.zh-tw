---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 7ac067e84f2a4d2724e3d8f2d0af9b220fd15538
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399625"
---
# <a name="servicediscovery"></a><span data-ttu-id="c8e45-101">\<serviceDiscovery></span><span class="sxs-lookup"><span data-stu-id="c8e45-101">\<serviceDiscovery></span></span>
<span data-ttu-id="c8e45-102">指定服務端點的探索能力。</span><span class="sxs-lookup"><span data-stu-id="c8e45-102">Specifies the discoverability of service endpoints.</span></span>  
  
<span data-ttu-id="c8e45-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c8e45-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c8e45-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c8e45-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c8e45-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c8e45-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="c8e45-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c8e45-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="c8e45-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="c8e45-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="c8e45-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceDiscovery >**</span><span class="sxs-lookup"><span data-stu-id="c8e45-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDiscovery>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8e45-109">語法</span><span class="sxs-lookup"><span data-stu-id="c8e45-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8e45-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c8e45-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c8e45-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c8e45-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8e45-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c8e45-112">Attributes</span></span>  
 <span data-ttu-id="c8e45-113">無。</span><span class="sxs-lookup"><span data-stu-id="c8e45-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c8e45-114">子元素</span><span class="sxs-lookup"><span data-stu-id="c8e45-114">Child Elements</span></span>  
  
|<span data-ttu-id="c8e45-115">項目</span><span class="sxs-lookup"><span data-stu-id="c8e45-115">Element</span></span>|<span data-ttu-id="c8e45-116">描述</span><span class="sxs-lookup"><span data-stu-id="c8e45-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c8e45-117">\<announcementEndpoint></span><span class="sxs-lookup"><span data-stu-id="c8e45-117">\<announcementEndpoint></span></span>](announcementendpoint.md)|<span data-ttu-id="c8e45-118">公告端點的集合。</span><span class="sxs-lookup"><span data-stu-id="c8e45-118">A collection of announcement endpoints.</span></span> <span data-ttu-id="c8e45-119">使用此區段指定用於傳送公告訊息的端點。</span><span class="sxs-lookup"><span data-stu-id="c8e45-119">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[<span data-ttu-id="c8e45-120">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="c8e45-120">\<discoveryEndpoint></span></span>](discoveryendpoint.md)|<span data-ttu-id="c8e45-121">探索端點的集合。</span><span class="sxs-lookup"><span data-stu-id="c8e45-121">A collection of discovery endpoints.</span></span> <span data-ttu-id="c8e45-122">使用此區段指定用於接聽探索訊息的端點。</span><span class="sxs-lookup"><span data-stu-id="c8e45-122">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c8e45-123">父項目</span><span class="sxs-lookup"><span data-stu-id="c8e45-123">Parent Elements</span></span>  
  
|<span data-ttu-id="c8e45-124">項目</span><span class="sxs-lookup"><span data-stu-id="c8e45-124">Element</span></span>|<span data-ttu-id="c8e45-125">描述</span><span class="sxs-lookup"><span data-stu-id="c8e45-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c8e45-126">\<behavior></span><span class="sxs-lookup"><span data-stu-id="c8e45-126">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="c8e45-127">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="c8e45-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8e45-128">備註</span><span class="sxs-lookup"><span data-stu-id="c8e45-128">Remarks</span></span>  
 <span data-ttu-id="c8e45-129">加入至服務的行為組態時，這個組態項目會將該服務的所有端點標示為可探索。</span><span class="sxs-lookup"><span data-stu-id="c8e45-129">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="c8e45-130">您可以使用[ \<discoveryEndpoint >](discoveryendpoint.md)或[ \<announcementEndpoint >](announcementendpoint.md)子項目，進一步設定這類端點的探索功能。</span><span class="sxs-lookup"><span data-stu-id="c8e45-130">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="c8e45-131">使用[announcementEndpoint > 區段來設定通知，方法是指定要用來傳送服務宣告（online/Hello 和 offline/再見）的端點設定。 \< ](announcementendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="c8e45-131">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="c8e45-132">使用 [ [ \<discoveryEndpoint >](discoveryendpoint.md) ] 區段，以手動方式指定要接聽探索訊息的端點。</span><span class="sxs-lookup"><span data-stu-id="c8e45-132">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8e45-133">範例</span><span class="sxs-lookup"><span data-stu-id="c8e45-133">Example</span></span>  
 <span data-ttu-id="c8e45-134">下列組態範例將 CalculatorService 指定為可探索，並且選擇性地指定要使用的公告端點。</span><span class="sxs-lookup"><span data-stu-id="c8e45-134">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c8e45-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c8e45-135">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
