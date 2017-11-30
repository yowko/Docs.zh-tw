---
title: '&lt;udpDiscoveryEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 21f0165f8cda6701aa11058f2dac1bdde0f9ebbd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltudpdiscoveryendpointgt"></a><span data-ttu-id="5a807-102">&lt;udpDiscoveryEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="5a807-102">&lt;udpDiscoveryEndpoint&gt;</span></span>
<span data-ttu-id="5a807-103">這個組態項目會定義標準端點，此端點是針對透過 UDP 多點傳送繫結進行探索作業而預先設定的。</span><span class="sxs-lookup"><span data-stu-id="5a807-103">This configuration element defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="5a807-104">此端點具備固定合約，而且支援兩種 WS-Discovery 通訊協定版本。</span><span class="sxs-lookup"><span data-stu-id="5a807-104">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="5a807-105">此外，它擁有固定的 UDP 繫結和預設位址，如 WS-Discovery 規格 (WS-Discovery 2005 年 4 月或 WS-Discovery V1.1) 中所指定。</span><span class="sxs-lookup"><span data-stu-id="5a807-105">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1)..</span></span>  
  
 <span data-ttu-id="5a807-106">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5a807-106">\<system.ServiceModel></span></span>  
<span data-ttu-id="5a807-107">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="5a807-107">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a807-108">語法</span><span class="sxs-lookup"><span data-stu-id="5a807-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
    <standardEndpoints>       <discoveryEndpoint>           <standardEndpoint                  discoveryMode="Adhoc/Managed"                  discoveryVersion="WSDiscovery11/WSDiscoveryApril2005"                  maxResponseDelay="Timespan"                  multicastAddress="Uri"                   name="String" />       </discoveryEndpoint>            </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a807-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5a807-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5a807-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5a807-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a807-111">屬性</span><span class="sxs-lookup"><span data-stu-id="5a807-111">Attributes</span></span>  
  
|<span data-ttu-id="5a807-112">屬性</span><span class="sxs-lookup"><span data-stu-id="5a807-112">Attribute</span></span>|<span data-ttu-id="5a807-113">描述</span><span class="sxs-lookup"><span data-stu-id="5a807-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5a807-114">discoveryMode</span><span class="sxs-lookup"><span data-stu-id="5a807-114">discoveryMode</span></span>|<span data-ttu-id="5a807-115">字串，這個字串會指定探索通訊協定的模式。</span><span class="sxs-lookup"><span data-stu-id="5a807-115">A string that specifies the mode of discovery protocol.</span></span> <span data-ttu-id="5a807-116">有效值為"Adhoc"和"Managed"。</span><span class="sxs-lookup"><span data-stu-id="5a807-116">Valid values are "Adhoc" and "Managed".</span></span> <span data-ttu-id="5a807-117">在 Managed 模式中，通訊協定會依賴探索 Proxy，此 Proxy 的作用是可探索之服務的儲存機制。</span><span class="sxs-lookup"><span data-stu-id="5a807-117">In managed mode the protocol relies on a Discovery Proxy, which acts as a repository of Discoverable services.</span></span> <span data-ttu-id="5a807-118">Adhoc 模式會要求通訊協定使用 UDP 多點傳送機制尋找可用的服務。</span><span class="sxs-lookup"><span data-stu-id="5a807-118">Adhoc mode requires the protocol to use UDP multicast mechanism to find available services.</span></span> <span data-ttu-id="5a807-119">這個值的型別為 <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>。</span><span class="sxs-lookup"><span data-stu-id="5a807-119">This value is of type <xref:System.ServiceModel.Discovery.ServiceDiscoveryMode>.</span></span>|  
|<span data-ttu-id="5a807-120">discoveryVersion</span><span class="sxs-lookup"><span data-stu-id="5a807-120">discoveryVersion</span></span>|<span data-ttu-id="5a807-121">字串，此字串會指定兩個 WS-Discovery 通訊協定版本的其中之一。</span><span class="sxs-lookup"><span data-stu-id="5a807-121">A string that specifies one of the two versions of WS-Discovery protocol.</span></span> <span data-ttu-id="5a807-122">有效的值為 WSDiscovery11 和 WSDiscoveryApril2005。</span><span class="sxs-lookup"><span data-stu-id="5a807-122">Valid values are WSDiscovery11 and WSDiscoveryApril2005.</span></span> <span data-ttu-id="5a807-123">這個值的型別為 <xref:System.ServiceModel.Discovery.DiscoveryVersion>。</span><span class="sxs-lookup"><span data-stu-id="5a807-123">This value is of type <xref:System.ServiceModel.Discovery.DiscoveryVersion>.</span></span>|  
|<span data-ttu-id="5a807-124">maxResponseDelay</span><span class="sxs-lookup"><span data-stu-id="5a807-124">maxResponseDelay</span></span>|<span data-ttu-id="5a807-125">Timespan 值，這個值指定 Discovery 通訊協定傳送某些訊息 (例如「探查相符」或「解析相符」) 之前會等候的延遲值上限。</span><span class="sxs-lookup"><span data-stu-id="5a807-125">A Timespan value that specifies the maximum value for the delay the Discovery protocol will wait before sending certain messages such as Probe Match or Resolve Match.</span></span><br /><br /> <span data-ttu-id="5a807-126">如果所有 ProbeMatches 同時傳送，則會導致網路負荷過大。</span><span class="sxs-lookup"><span data-stu-id="5a807-126">If all ProbeMatches are sent at the same time, a network storm may result.</span></span> <span data-ttu-id="5a807-127">為避免發生這種情況，傳送 ProbeMatches 時，兩次 ProbeMatch 傳送之間會有隨機的延遲時間。</span><span class="sxs-lookup"><span data-stu-id="5a807-127">To prevent this from occurring, ProbeMatches are sent with a random delay between each ProbeMatch.</span></span> <span data-ttu-id="5a807-128">隨機的延遲範圍介於 0 到這個屬性所設定的值之間。</span><span class="sxs-lookup"><span data-stu-id="5a807-128">The random delay is in the range of 0 to the value set by this attribute.</span></span> <span data-ttu-id="5a807-129">如果這個屬性設為 0，則 ProbeMatches 訊息會以緊湊的迴圈傳送，且不會有任何延遲。</span><span class="sxs-lookup"><span data-stu-id="5a807-129">If this attribute is set to 0, then the ProbeMatches messages are sent in a tight loop without any delay.</span></span> <span data-ttu-id="5a807-130">否則，ProbeMatches 訊息傳送時會有隨機延遲，而傳送所有 ProbeMatches 訊息花費的總時間不會超過 maxResponseDelay。</span><span class="sxs-lookup"><span data-stu-id="5a807-130">Otherwise, the ProbeMatches messages are sent with some random delay such that the total time taken to send all ProbeMatches messages does not exceed the maxResponseDelay.</span></span> <span data-ttu-id="5a807-131">這個值只與服務有關，不會由用戶端使用。</span><span class="sxs-lookup"><span data-stu-id="5a807-131">This value is only relevant for services, it is not used by clients.</span></span>|  
|<span data-ttu-id="5a807-132">multicastAddress</span><span class="sxs-lookup"><span data-stu-id="5a807-132">multicastAddress</span></span>|<span data-ttu-id="5a807-133">URI，這個 URI 會指定傳送及接收探索訊息時所使用的多點傳送位址。</span><span class="sxs-lookup"><span data-stu-id="5a807-133">A Uri that specifies a multicast address to use for sending and receiving the discovery messages.</span></span> <span data-ttu-id="5a807-134">預設值是與通訊協定規格一致的多點傳送位址。</span><span class="sxs-lookup"><span data-stu-id="5a807-134">The default value is the multicast address as conformant to the protocol specification.</span></span>|  
|`name`|<span data-ttu-id="5a807-135">字串，這個字串會指定標準端點之組態的名稱。</span><span class="sxs-lookup"><span data-stu-id="5a807-135">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="5a807-136">這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。</span><span class="sxs-lookup"><span data-stu-id="5a807-136">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a807-137">子元素</span><span class="sxs-lookup"><span data-stu-id="5a807-137">Child Elements</span></span>  
  
|<span data-ttu-id="5a807-138">項目</span><span class="sxs-lookup"><span data-stu-id="5a807-138">Element</span></span>|<span data-ttu-id="5a807-139">說明</span><span class="sxs-lookup"><span data-stu-id="5a807-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a807-140">\<u d ></span><span class="sxs-lookup"><span data-stu-id="5a807-140">\<udpTransportSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|<span data-ttu-id="5a807-141">設定的集合，可讓您設定 UDP 端點的 UDP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="5a807-141">A collection of settings that allow you to configure UDP transport for the UDP endpoint.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a807-142">父項目</span><span class="sxs-lookup"><span data-stu-id="5a807-142">Parent Elements</span></span>  
  
|<span data-ttu-id="5a807-143">項目</span><span class="sxs-lookup"><span data-stu-id="5a807-143">Element</span></span>|<span data-ttu-id="5a807-144">說明</span><span class="sxs-lookup"><span data-stu-id="5a807-144">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a807-145">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="5a807-145">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="5a807-146">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="5a807-146">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="5a807-147">範例</span><span class="sxs-lookup"><span data-stu-id="5a807-147">Example</span></span>  
 <span data-ttu-id="5a807-148">下列範例示範透過 UDP 多點傳送傳輸接聽探索訊息的服務。</span><span class="sxs-lookup"><span data-stu-id="5a807-148">The following example demonstrates a service listening for discovery messages over a UDP multicast transport.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5a807-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a807-149">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
