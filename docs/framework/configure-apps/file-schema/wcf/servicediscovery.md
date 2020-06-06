---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: 7ac067e84f2a4d2724e3d8f2d0af9b220fd15538
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399625"
---
# \<serviceDiscovery>
<span data-ttu-id="d5dab-101">指定服務端點的探索能力。</span><span class="sxs-lookup"><span data-stu-id="d5dab-101">Specifies the discoverability of service endpoints.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDiscovery>**  
  
## <a name="syntax"></a><span data-ttu-id="d5dab-102">語法</span><span class="sxs-lookup"><span data-stu-id="d5dab-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d5dab-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d5dab-103">Attributes and Elements</span></span>  
 <span data-ttu-id="d5dab-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d5dab-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d5dab-105">屬性</span><span class="sxs-lookup"><span data-stu-id="d5dab-105">Attributes</span></span>  
 <span data-ttu-id="d5dab-106">無。</span><span class="sxs-lookup"><span data-stu-id="d5dab-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d5dab-107">子元素</span><span class="sxs-lookup"><span data-stu-id="d5dab-107">Child Elements</span></span>  
  
|<span data-ttu-id="d5dab-108">元素</span><span class="sxs-lookup"><span data-stu-id="d5dab-108">Element</span></span>|<span data-ttu-id="d5dab-109">描述</span><span class="sxs-lookup"><span data-stu-id="d5dab-109">Description</span></span>|  
|-------------|-----------------|  
|[\<announcementEndpoint>](announcementendpoint.md)|<span data-ttu-id="d5dab-110">公告端點的集合。</span><span class="sxs-lookup"><span data-stu-id="d5dab-110">A collection of announcement endpoints.</span></span> <span data-ttu-id="d5dab-111">使用此區段指定用於傳送公告訊息的端點。</span><span class="sxs-lookup"><span data-stu-id="d5dab-111">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|<span data-ttu-id="d5dab-112">探索端點的集合。</span><span class="sxs-lookup"><span data-stu-id="d5dab-112">A collection of discovery endpoints.</span></span> <span data-ttu-id="d5dab-113">使用此區段指定用於接聽探索訊息的端點。</span><span class="sxs-lookup"><span data-stu-id="d5dab-113">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d5dab-114">父項目</span><span class="sxs-lookup"><span data-stu-id="d5dab-114">Parent Elements</span></span>  
  
|<span data-ttu-id="d5dab-115">元素</span><span class="sxs-lookup"><span data-stu-id="d5dab-115">Element</span></span>|<span data-ttu-id="d5dab-116">描述</span><span class="sxs-lookup"><span data-stu-id="d5dab-116">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="d5dab-117">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="d5dab-117">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d5dab-118">備註</span><span class="sxs-lookup"><span data-stu-id="d5dab-118">Remarks</span></span>  
 <span data-ttu-id="d5dab-119">加入至服務的行為組態時，這個組態項目會將該服務的所有端點標示為可探索。</span><span class="sxs-lookup"><span data-stu-id="d5dab-119">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="d5dab-120">您可以使用 [\<discoveryEndpoint>](discoveryendpoint.md) 或子項目，進一步設定這類端點的探索功能 [\<announcementEndpoint>](announcementendpoint.md) 。</span><span class="sxs-lookup"><span data-stu-id="d5dab-120">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="d5dab-121">使用 [\<announcementEndpoint>](announcementendpoint.md) 區段來設定通知，方法是指定要用來傳送服務宣告的端點設定（online/Hello 和 offline/再見）。</span><span class="sxs-lookup"><span data-stu-id="d5dab-121">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="d5dab-122">使用 [\<discoveryEndpoint>](discoveryendpoint.md) 區段來手動指定要接聽探索訊息的端點。</span><span class="sxs-lookup"><span data-stu-id="d5dab-122">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5dab-123">範例</span><span class="sxs-lookup"><span data-stu-id="d5dab-123">Example</span></span>  
 <span data-ttu-id="d5dab-124">下列組態範例將 CalculatorService 指定為可探索，並且選擇性地指定要使用的公告端點。</span><span class="sxs-lookup"><span data-stu-id="d5dab-124">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d5dab-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d5dab-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
