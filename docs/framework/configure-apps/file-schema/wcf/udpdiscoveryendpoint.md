---
title: <udpDiscoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
ms.openlocfilehash: f02cbddcdd4390d754f93e6f6d9aae6646cb137b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91183620"
---
# \<udpDiscoveryEndpoint>

<span data-ttu-id="5a4b2-101">這個組態項目會定義標準端點，此端點是針對透過 UDP 多點傳送繫結進行探索作業而預先設定的。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-101">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="5a4b2-102">此端點具備固定合約，而且支援兩種 WS-Discovery 通訊協定版本。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-102">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="5a4b2-103">此外，它擁有固定的 UDP 繫結和預設位址，如 WS-Discovery 規格 (WS-Discovery 2005 年 4 月或 WS-Discovery V1.1) 中所指定。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-103">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<udpDiscoveryEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="5a4b2-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="5a4b2-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        multicastAddress="Uri"
                        name="String" />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a4b2-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5a4b2-105">Attributes and Elements</span></span>  

 <span data-ttu-id="5a4b2-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a4b2-107">屬性</span><span class="sxs-lookup"><span data-stu-id="5a4b2-107">Attributes</span></span>  
  
|<span data-ttu-id="5a4b2-108">屬性</span><span class="sxs-lookup"><span data-stu-id="5a4b2-108">Attribute</span></span>|<span data-ttu-id="5a4b2-109">描述</span><span class="sxs-lookup"><span data-stu-id="5a4b2-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5a4b2-110">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="5a4b2-110">discoveryMode</span></span>|<span data-ttu-id="5a4b2-111">字串，這個字串會指定探索通訊協定的模式。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-111">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="5a4b2-112">有效的值為「臨機操作」和「受控」。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-112">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="5a4b2-113">在 Managed 模式中，通訊協定會依賴探索 Proxy，此 Proxy 的作用是可探索之服務的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-113">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="5a4b2-114">Adhoc 模式會要求通訊協定使用 UDP 多點傳送機制尋找可用的服務。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-114">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="5a4b2-115">這個值的型別為 <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-115">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="5a4b2-116">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="5a4b2-116">discoveryVersion</span></span>|<span data-ttu-id="5a4b2-117">字串，此字串會指定兩個 WS-Discovery 通訊協定版本的其中之一。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-117">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="5a4b2-118">有效的值為 WSDiscovery11 和 WSDiscoveryApril2005。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-118">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="5a4b2-119">這個值的型別為 <xref:System.ServiceModel.Discovery.DiscoveryVersion>。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-119">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="5a4b2-120">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="5a4b2-120">maxResponseDelay</span></span>|<span data-ttu-id="5a4b2-121">Timespan 值，這個值指定 Discovery 通訊協定傳送某些訊息 (例如「探查相符」或「解析相符」) 之前會等候的延遲值上限。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-121">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="5a4b2-122">如果所有 ProbeMatches 同時傳送，則會導致網路負荷過大。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-122">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="5a4b2-123">為避免發生這種情況，傳送 ProbeMatches 時，兩次 ProbeMatch 傳送之間會有隨機的延遲時間。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-123">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="5a4b2-124">隨機的延遲範圍介於 0 到這個屬性所設定的值之間。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-124">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="5a4b2-125">如果這個屬性設為 0，則 ProbeMatches 訊息會以緊湊的迴圈傳送，且不會有任何延遲。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-125">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="5a4b2-126">否則，ProbeMatches 訊息傳送時會有隨機延遲，而傳送所有 ProbeMatches 訊息花費的總時間不會超過 maxResponseDelay。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-126">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="5a4b2-127">這個值只與服務有關，不會由用戶端使用。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-127">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="5a4b2-128">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="5a4b2-128">multicastAddress</span></span>|<span data-ttu-id="5a4b2-129">URI，這個 URI 會指定傳送及接收探索訊息時所使用的多點傳送位址。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-129">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="5a4b2-130">預設值是與通訊協定規格一致的多點傳送位址。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-130">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="5a4b2-131">字串，這個字串會指定標準端點之組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-131">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="5a4b2-132">這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-132">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a4b2-133">子元素</span><span class="sxs-lookup"><span data-stu-id="5a4b2-133">Child Elements</span></span>  
  
|<span data-ttu-id="5a4b2-134">項目</span><span class="sxs-lookup"><span data-stu-id="5a4b2-134">Element</span></span>|<span data-ttu-id="5a4b2-135">描述</span><span class="sxs-lookup"><span data-stu-id="5a4b2-135">Description</span></span>|  
|-------------|-----------------|  
|[\<udpTransportSettings>](udptransportsettings.md)|<span data-ttu-id="5a4b2-136">設定的集合，可讓您設定 UDP 端點的 UDP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-136">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a4b2-137">父項目</span><span class="sxs-lookup"><span data-stu-id="5a4b2-137">Parent Elements</span></span>  
  
|<span data-ttu-id="5a4b2-138">項目</span><span class="sxs-lookup"><span data-stu-id="5a4b2-138">Element</span></span>|<span data-ttu-id="5a4b2-139">描述</span><span class="sxs-lookup"><span data-stu-id="5a4b2-139">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="5a4b2-140">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-140">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5a4b2-141">範例</span><span class="sxs-lookup"><span data-stu-id="5a4b2-141">Example</span></span>  

 <span data-ttu-id="5a4b2-142">下列範例示範透過 UDP 多點傳送傳輸接聽探索訊息的服務。</span><span class="sxs-lookup"><span data-stu-id="5a4b2-142">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="DiscoveryEndpoint"
              kind="udpDiscoveryEndpoint" />
  </service>
  <standardEndpoints>
    <udpDiscoveryEndpoint>
      <standardEndpoint name="DiscoveryEndpoint"
                        version="WSDiscoveryApril2005" />
    </udpDiscoveryEndpoint>
  </standardEndpoints>
</services>
```  
  
## <a name="see-also"></a><span data-ttu-id="5a4b2-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a4b2-143">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
