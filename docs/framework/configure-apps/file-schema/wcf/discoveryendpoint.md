---
title: <discoveryEndpoint>
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 32b14f8fb3235040a51455f2099a403c8312c699
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855403"
---
# <a name="discoveryendpoint"></a><span data-ttu-id="f6e2d-101">\<discoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="f6e2d-101">\<discoveryEndpoint></span></span>

<span data-ttu-id="f6e2d-102">這個組態項目會定義具有固定探索合約的標準端點。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-102">This configuration element defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="f6e2d-103">加入至服務組態時，此組態項目會指定接聽探索訊息的位置。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-103">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="f6e2d-104">加入至用戶端組態時，此組態項目會指定傳送探索查詢的位置。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-104">When added to the client configuration it specifies where to send the discovery queries.</span></span>  
  
<span data-ttu-id="f6e2d-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f6e2d-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f6e2d-106">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f6e2d-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f6e2d-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="f6e2d-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="f6e2d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<discoveryEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="f6e2d-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6e2d-109">語法</span><span class="sxs-lookup"><span data-stu-id="f6e2d-109">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed"
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"
                        maxResponseDelay="Timespan"
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f6e2d-110">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="f6e2d-110">Attributes and elements</span></span>

<span data-ttu-id="f6e2d-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f6e2d-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f6e2d-112">Attributes</span></span>

| <span data-ttu-id="f6e2d-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f6e2d-113">Attribute</span></span>        | <span data-ttu-id="f6e2d-114">說明</span><span class="sxs-lookup"><span data-stu-id="f6e2d-114">Description</span></span> |  
| ---------------- | ----------- |  
| <span data-ttu-id="f6e2d-115">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="f6e2d-115">discoveryMode</span></span>    | <span data-ttu-id="f6e2d-116">字串，這個字串會指定探索通訊協定的模式。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-116">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="f6e2d-117">有效的值為「臨機操作」和「受控」。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-117">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="f6e2d-118">在 Managed 模式中，通訊協定會依賴探索 Proxy，此 Proxy 的作用是可探索之服務的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-118">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="f6e2d-119">Adhoc 模式會要求通訊協定使用 UDP 多點傳送機制尋找可用的服務。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-119">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="f6e2d-120">如需屬性的詳細資訊，請<xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>參閱。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-120">For more information on the property, see <xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>.</span></span> |  
| <span data-ttu-id="f6e2d-121">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="f6e2d-121">discoveryVersion</span></span> | <span data-ttu-id="f6e2d-122">字串，此字串會指定兩個 WS-Discovery 通訊協定版本的其中之一。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-122">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="f6e2d-123">有效的值為 WSDiscovery11 和 WSDiscoveryApril2005。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-123">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="f6e2d-124">這個值的型別為 <xref:System.ServiceModel.Discovery.DiscoveryVersion>。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-124">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span> |  
| <span data-ttu-id="f6e2d-125">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="f6e2d-125">maxResponseDelay</span></span> | <span data-ttu-id="f6e2d-126">Timespan 值，這個值指定 Discovery 通訊協定傳送某些訊息 (例如「探查相符」或「解析相符」) 之前會等候的延遲值上限。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-126">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="f6e2d-127">如果所有 ProbeMatches 同時傳送，則會導致網路負荷過大。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-127">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="f6e2d-128">為避免發生這種情況，傳送 ProbeMatches 時，兩次 ProbeMatch 傳送之間會有隨機的延遲時間。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-128">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="f6e2d-129">隨機的延遲範圍介於 0 到這個屬性所設定的值之間。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-129">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="f6e2d-130">如果這個屬性設為 0，則 ProbeMatches 訊息會以緊湊的迴圈傳送，且不會有任何延遲。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-130">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="f6e2d-131">否則，ProbeMatches 訊息傳送時會有隨機延遲，而傳送所有 ProbeMatches 訊息花費的總時間不會超過 maxResponseDelay。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-131">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="f6e2d-132">這個值只與服務有關，不會由用戶端使用。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-132">This value is only relevant for services, it is not used by clients.</span></span> |  
| `name`           | <span data-ttu-id="f6e2d-133">字串，這個字串會指定標準端點之組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-133">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="f6e2d-134">這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-134">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span> |  
  
### <a name="child-elements"></a><span data-ttu-id="f6e2d-135">子元素</span><span class="sxs-lookup"><span data-stu-id="f6e2d-135">Child elements</span></span>

<span data-ttu-id="f6e2d-136">無。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-136">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f6e2d-137">父元素</span><span class="sxs-lookup"><span data-stu-id="f6e2d-137">Parent elements</span></span>

| <span data-ttu-id="f6e2d-138">元素</span><span class="sxs-lookup"><span data-stu-id="f6e2d-138">Element</span></span> | <span data-ttu-id="f6e2d-139">說明</span><span class="sxs-lookup"><span data-stu-id="f6e2d-139">Description</span></span> |  
| ------- | ----------- |  
| [<span data-ttu-id="f6e2d-140">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="f6e2d-140">\<standardEndpoints></span></span>](standardendpoints.md) | <span data-ttu-id="f6e2d-141">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-141">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span> |  
  
## <a name="example"></a><span data-ttu-id="f6e2d-142">範例</span><span class="sxs-lookup"><span data-stu-id="f6e2d-142">Example</span></span>

<span data-ttu-id="f6e2d-143">下列範例示範透過對等網路多點傳送傳輸接聽探索訊息的服務。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-143">The following example demonstrates a service listening on the discovery messages over a peer net multicast transport.</span></span> <span data-ttu-id="f6e2d-144">此範例會明確地指定 WS-Discovery April 2005 版本。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-144">The example explicitly specifies WS-Discovery April 2005 version.</span></span>  
  
<span data-ttu-id="f6e2d-145">標準端點組態是依每個服務定義的，無法跨服務共用。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-145">The standard endpoint configuration is defined per service and cannot be shared across the service.</span></span> <span data-ttu-id="f6e2d-146">如果另一個服務想擁有同樣的探索端點，就需要將同樣的組態加入至該服務的區段中。</span><span class="sxs-lookup"><span data-stu-id="f6e2d-146">If another service would like to have the same discovery endpoint, the same configuration needs to be added to that service’s section.</span></span>  
  
```xml  
<services>
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding"
              address="calculator"
              contract="ICalculatorService" />
    <endpoint name="peerNetDiscovery"
              binding="peerTcpBinding"
              address="net.p2p://discoveryMesh/multicast"
              kind="discoveryEndpoint"
              endpointConfiguration="peerTcpDiscoveryEndpointConfiguration"
              bindingConfiguration="discoveryPeerTcpBindingConfig" />
  </service>
</services>
<standardEndpoints>
  <discoveryEndpoint>
    <standardEndpoint name="peerTcpDiscoveryEndpointConfiguration"
                      version="WSDiscoveryApril2005" />
  </discoveryEndpoint>
</standardEndpoints>
```  
  
## <a name="see-also"></a><span data-ttu-id="f6e2d-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6e2d-147">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
