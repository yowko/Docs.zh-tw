---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: ad87a5876381a7224341babdb076c85edcd1dd87
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399568"
---
# <a name="servicethrottling"></a><span data-ttu-id="5a022-101">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="5a022-101">\<serviceThrottling></span></span>
<span data-ttu-id="5a022-102">指定 Windows Communication Foundation (WCF) 服務的節流機制。</span><span class="sxs-lookup"><span data-stu-id="5a022-102">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
<span data-ttu-id="5a022-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5a022-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5a022-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5a022-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5a022-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5a022-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="5a022-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5a022-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="5a022-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5a022-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="5a022-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceThrottling >**</span><span class="sxs-lookup"><span data-stu-id="5a022-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceThrottling>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a022-109">語法</span><span class="sxs-lookup"><span data-stu-id="5a022-109">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a022-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5a022-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5a022-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5a022-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a022-112">屬性</span><span class="sxs-lookup"><span data-stu-id="5a022-112">Attributes</span></span>  
  
|<span data-ttu-id="5a022-113">屬性</span><span class="sxs-lookup"><span data-stu-id="5a022-113">Attribute</span></span>|<span data-ttu-id="5a022-114">說明</span><span class="sxs-lookup"><span data-stu-id="5a022-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5a022-115">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="5a022-115">maxConcurrentCalls</span></span>|<span data-ttu-id="5a022-116">正整數，限制同時在 <xref:System.ServiceModel.ServiceHost> 上進行處理的訊息數目。</span><span class="sxs-lookup"><span data-stu-id="5a022-116">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="5a022-117">超過限制的呼叫會進入佇列。</span><span class="sxs-lookup"><span data-stu-id="5a022-117">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="5a022-118">將這個值設定為 0 相當於設定為 Int32.MaxValue。</span><span class="sxs-lookup"><span data-stu-id="5a022-118">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="5a022-119">預設值是 16 \* 處理器計數。</span><span class="sxs-lookup"><span data-stu-id="5a022-119">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="5a022-120">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="5a022-120">maxConcurrentInstances</span></span>|<span data-ttu-id="5a022-121">正整數，限制同時在 <xref:System.ServiceModel.InstanceContext> 上執行的 <xref:System.ServiceModel.ServiceHost> 物件數目。</span><span class="sxs-lookup"><span data-stu-id="5a022-121">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="5a022-122">當限制之內的位置可供使用時，建立其他執行個體的要求便會進入佇列並完成。</span><span class="sxs-lookup"><span data-stu-id="5a022-122">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="5a022-123">預設值是 maxConcurrentSessions 和 MaxConcurrentCalls 的總和</span><span class="sxs-lookup"><span data-stu-id="5a022-123">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="5a022-124">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="5a022-124">maxConcurrentSessions</span></span>|<span data-ttu-id="5a022-125">正整數，限制 <xref:System.ServiceModel.ServiceHost> 物件可以接受的工作階段數目。</span><span class="sxs-lookup"><span data-stu-id="5a022-125">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="5a022-126">服務將接受超過限制的連線，但只有低於限制個數的通道為作用中 (可從該通道讀取訊息)。</span><span class="sxs-lookup"><span data-stu-id="5a022-126">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="5a022-127">將這個值設定為 0 相當於設定為 Int32.MaxValue。</span><span class="sxs-lookup"><span data-stu-id="5a022-127">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="5a022-128">預設值是 100 \* 處理器計數。</span><span class="sxs-lookup"><span data-stu-id="5a022-128">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a022-129">子元素</span><span class="sxs-lookup"><span data-stu-id="5a022-129">Child Elements</span></span>  
 <span data-ttu-id="5a022-130">無。</span><span class="sxs-lookup"><span data-stu-id="5a022-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5a022-131">父項目</span><span class="sxs-lookup"><span data-stu-id="5a022-131">Parent Elements</span></span>  
  
|<span data-ttu-id="5a022-132">項目</span><span class="sxs-lookup"><span data-stu-id="5a022-132">Element</span></span>|<span data-ttu-id="5a022-133">描述</span><span class="sxs-lookup"><span data-stu-id="5a022-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a022-134">\<behavior></span><span class="sxs-lookup"><span data-stu-id="5a022-134">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="5a022-135">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="5a022-135">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a022-136">備註</span><span class="sxs-lookup"><span data-stu-id="5a022-136">Remarks</span></span>  
 <span data-ttu-id="5a022-137">節流控制會限制同時呼叫、並行執行個體或工作階段的數目，以防止過度消耗資源。</span><span class="sxs-lookup"><span data-stu-id="5a022-137">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="5a022-138">每次達到這些屬性值時，就會寫入追蹤。</span><span class="sxs-lookup"><span data-stu-id="5a022-138">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="5a022-139">第一個追蹤會寫入成為警告。</span><span class="sxs-lookup"><span data-stu-id="5a022-139">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a022-140">範例</span><span class="sxs-lookup"><span data-stu-id="5a022-140">Example</span></span>  
 <span data-ttu-id="5a022-141">下列組態範例指定服務將同時呼叫上限限制為 2，且將並行執行個體上限限制為 10。</span><span class="sxs-lookup"><span data-stu-id="5a022-141">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="5a022-142">如需執行此範例的詳細範例，請參閱[節流](../../../wcf/samples/throttling.md)。</span><span class="sxs-lookup"><span data-stu-id="5a022-142">For a detailed example of running this example, see [Throttling](../../../wcf/samples/throttling.md).</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorServiceBehavior">
      <serviceDebug includeExceptionDetailInFaults="False" />
      <serviceMetadata httpGetEnabled="True" />
      <!-- Specify throttling behavior -->
      <serviceThrottling maxConcurrentCalls="2"
                         maxConcurrentInstances="10" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="5a022-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a022-143">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="5a022-144">使用 ServiceThrottlingBehavior 來控制 WCF 服務效能</span><span class="sxs-lookup"><span data-stu-id="5a022-144">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
