---
title: <serviceDiscovery>
ms.date: 03/30/2017
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
ms.openlocfilehash: b38496b77d80fcb66b1b48485a9eef6abfd72299
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91198817"
---
# \<serviceDiscovery>

<span data-ttu-id="261a5-101">指定服務端點的探索能力。</span><span class="sxs-lookup"><span data-stu-id="261a5-101">Specifies the discoverability of service endpoints.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceDiscovery>**  
  
## <a name="syntax"></a><span data-ttu-id="261a5-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="261a5-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="261a5-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="261a5-103">Attributes and Elements</span></span>  

 <span data-ttu-id="261a5-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="261a5-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="261a5-105">屬性</span><span class="sxs-lookup"><span data-stu-id="261a5-105">Attributes</span></span>  

 <span data-ttu-id="261a5-106">無。</span><span class="sxs-lookup"><span data-stu-id="261a5-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="261a5-107">子元素</span><span class="sxs-lookup"><span data-stu-id="261a5-107">Child Elements</span></span>  
  
|<span data-ttu-id="261a5-108">項目</span><span class="sxs-lookup"><span data-stu-id="261a5-108">Element</span></span>|<span data-ttu-id="261a5-109">描述</span><span class="sxs-lookup"><span data-stu-id="261a5-109">Description</span></span>|  
|-------------|-----------------|  
|[\<announcementEndpoint>](announcementendpoint.md)|<span data-ttu-id="261a5-110">公告端點的集合。</span><span class="sxs-lookup"><span data-stu-id="261a5-110">A collection of announcement endpoints.</span></span> <span data-ttu-id="261a5-111">使用此區段指定用於傳送公告訊息的端點。</span><span class="sxs-lookup"><span data-stu-id="261a5-111">Use this section to specify the endpoints to use for sending announcement messages.</span></span>|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|<span data-ttu-id="261a5-112">探索端點的集合。</span><span class="sxs-lookup"><span data-stu-id="261a5-112">A collection of discovery endpoints.</span></span> <span data-ttu-id="261a5-113">使用此區段指定用於接聽探索訊息的端點。</span><span class="sxs-lookup"><span data-stu-id="261a5-113">Use this section to specify the endpoints on which to listen for the discovery messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="261a5-114">父項目</span><span class="sxs-lookup"><span data-stu-id="261a5-114">Parent Elements</span></span>  
  
|<span data-ttu-id="261a5-115">項目</span><span class="sxs-lookup"><span data-stu-id="261a5-115">Element</span></span>|<span data-ttu-id="261a5-116">描述</span><span class="sxs-lookup"><span data-stu-id="261a5-116">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="261a5-117">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="261a5-117">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="261a5-118">備註</span><span class="sxs-lookup"><span data-stu-id="261a5-118">Remarks</span></span>  

 <span data-ttu-id="261a5-119">加入至服務的行為組態時，這個組態項目會將該服務的所有端點標示為可探索。</span><span class="sxs-lookup"><span data-stu-id="261a5-119">When added to the service’s behavior configuration, this configuration element makes all of the endpoints of that service discoverable.</span></span> <span data-ttu-id="261a5-120">您可以使用 [\<discoveryEndpoint>](discoveryendpoint.md) 或子項目，進一步設定這類端點的探索功能 [\<announcementEndpoint>](announcementendpoint.md) 。</span><span class="sxs-lookup"><span data-stu-id="261a5-120">You can further configure the discovery features of such endpoints by using the [\<discoveryEndpoint>](discoveryendpoint.md) or [\<announcementEndpoint>](announcementendpoint.md) child elements.</span></span> <span data-ttu-id="261a5-121">使用 [\<announcementEndpoint>](announcementendpoint.md) 區段來設定公告，方法是指定要用來將服務公告傳送 (online/Hello 和 offline/再見) 的端點設定。</span><span class="sxs-lookup"><span data-stu-id="261a5-121">Use the [\<announcementEndpoint>](announcementendpoint.md) section to configure the announcements by specifying the endpoint configuration to be use to send service announcements (online/Hello and offline/Bye).</span></span> <span data-ttu-id="261a5-122">使用 [\<discoveryEndpoint>](discoveryendpoint.md) 區段以手動方式指定要接聽探索訊息的端點。</span><span class="sxs-lookup"><span data-stu-id="261a5-122">Use the [\<discoveryEndpoint>](discoveryendpoint.md) section to manually specify the endpoint on which to listen for the discovery messages.</span></span>  
  
## <a name="example"></a><span data-ttu-id="261a5-123">範例</span><span class="sxs-lookup"><span data-stu-id="261a5-123">Example</span></span>  

 <span data-ttu-id="261a5-124">下列組態範例將 CalculatorService 指定為可探索，並且選擇性地指定要使用的公告端點。</span><span class="sxs-lookup"><span data-stu-id="261a5-124">The following configuration example specifies that the CalculatorService to be discoverable, and optionally specifies the announcement endpoint to be used.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="261a5-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="261a5-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>
