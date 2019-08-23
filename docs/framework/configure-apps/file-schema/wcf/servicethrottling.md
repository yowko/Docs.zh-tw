---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: 77ed5e91f09d9e658deeb7996baaca445b4e0c90
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937101"
---
# <a name="servicethrottling"></a><span data-ttu-id="06ce6-101">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="06ce6-101">\<serviceThrottling></span></span>
<span data-ttu-id="06ce6-102">指定 Windows Communication Foundation (WCF) 服務的節流機制。</span><span class="sxs-lookup"><span data-stu-id="06ce6-102">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="06ce6-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="06ce6-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="06ce6-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="06ce6-104">\<behaviors></span></span>  
<span data-ttu-id="06ce6-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="06ce6-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="06ce6-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="06ce6-106">\<behavior></span></span>  
<span data-ttu-id="06ce6-107">\<serviceThrottling></span><span class="sxs-lookup"><span data-stu-id="06ce6-107">\<serviceThrottling></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06ce6-108">語法</span><span class="sxs-lookup"><span data-stu-id="06ce6-108">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06ce6-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="06ce6-109">Attributes and Elements</span></span>  
 <span data-ttu-id="06ce6-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="06ce6-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06ce6-111">屬性</span><span class="sxs-lookup"><span data-stu-id="06ce6-111">Attributes</span></span>  
  
|<span data-ttu-id="06ce6-112">屬性</span><span class="sxs-lookup"><span data-stu-id="06ce6-112">Attribute</span></span>|<span data-ttu-id="06ce6-113">描述</span><span class="sxs-lookup"><span data-stu-id="06ce6-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="06ce6-114">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="06ce6-114">maxConcurrentCalls</span></span>|<span data-ttu-id="06ce6-115">正整數，限制同時在 <xref:System.ServiceModel.ServiceHost> 上進行處理的訊息數目。</span><span class="sxs-lookup"><span data-stu-id="06ce6-115">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="06ce6-116">超過限制的呼叫會進入佇列。</span><span class="sxs-lookup"><span data-stu-id="06ce6-116">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="06ce6-117">將這個值設定為 0 相當於設定為 Int32.MaxValue。</span><span class="sxs-lookup"><span data-stu-id="06ce6-117">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="06ce6-118">預設值是 16 \* 處理器計數。</span><span class="sxs-lookup"><span data-stu-id="06ce6-118">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="06ce6-119">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="06ce6-119">maxConcurrentInstances</span></span>|<span data-ttu-id="06ce6-120">正整數，限制同時在 <xref:System.ServiceModel.InstanceContext> 上執行的 <xref:System.ServiceModel.ServiceHost> 物件數目。</span><span class="sxs-lookup"><span data-stu-id="06ce6-120">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="06ce6-121">當限制之內的位置可供使用時，建立其他執行個體的要求便會進入佇列並完成。</span><span class="sxs-lookup"><span data-stu-id="06ce6-121">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="06ce6-122">預設值是 maxConcurrentSessions 和 MaxConcurrentCalls 的總和</span><span class="sxs-lookup"><span data-stu-id="06ce6-122">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="06ce6-123">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="06ce6-123">maxConcurrentSessions</span></span>|<span data-ttu-id="06ce6-124">正整數，限制 <xref:System.ServiceModel.ServiceHost> 物件可以接受的工作階段數目。</span><span class="sxs-lookup"><span data-stu-id="06ce6-124">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="06ce6-125">服務將接受超過限制的連線，但只有低於限制個數的通道為作用中 (可從該通道讀取訊息)。</span><span class="sxs-lookup"><span data-stu-id="06ce6-125">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="06ce6-126">將這個值設定為 0 相當於設定為 Int32.MaxValue。</span><span class="sxs-lookup"><span data-stu-id="06ce6-126">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="06ce6-127">預設值是 100 \* 處理器計數。</span><span class="sxs-lookup"><span data-stu-id="06ce6-127">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="06ce6-128">子元素</span><span class="sxs-lookup"><span data-stu-id="06ce6-128">Child Elements</span></span>  
 <span data-ttu-id="06ce6-129">無。</span><span class="sxs-lookup"><span data-stu-id="06ce6-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="06ce6-130">父項目</span><span class="sxs-lookup"><span data-stu-id="06ce6-130">Parent Elements</span></span>  
  
|<span data-ttu-id="06ce6-131">項目</span><span class="sxs-lookup"><span data-stu-id="06ce6-131">Element</span></span>|<span data-ttu-id="06ce6-132">描述</span><span class="sxs-lookup"><span data-stu-id="06ce6-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="06ce6-133">\<behavior></span><span class="sxs-lookup"><span data-stu-id="06ce6-133">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="06ce6-134">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="06ce6-134">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="06ce6-135">備註</span><span class="sxs-lookup"><span data-stu-id="06ce6-135">Remarks</span></span>  
 <span data-ttu-id="06ce6-136">節流控制會限制同時呼叫、並行執行個體或工作階段的數目，以防止過度消耗資源。</span><span class="sxs-lookup"><span data-stu-id="06ce6-136">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="06ce6-137">每次達到這些屬性值時，就會寫入追蹤。</span><span class="sxs-lookup"><span data-stu-id="06ce6-137">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="06ce6-138">第一個追蹤會寫入成為警告。</span><span class="sxs-lookup"><span data-stu-id="06ce6-138">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06ce6-139">範例</span><span class="sxs-lookup"><span data-stu-id="06ce6-139">Example</span></span>  
 <span data-ttu-id="06ce6-140">下列組態範例指定服務將同時呼叫上限限制為 2，且將並行執行個體上限限制為 10。</span><span class="sxs-lookup"><span data-stu-id="06ce6-140">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="06ce6-141">如需執行此範例的詳細範例, 請參閱[節流](../../../wcf/samples/throttling.md)。</span><span class="sxs-lookup"><span data-stu-id="06ce6-141">For a detailed example of running this example, see [Throttling](../../../wcf/samples/throttling.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="06ce6-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06ce6-142">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="06ce6-143">使用 ServiceThrottlingBehavior 來控制 WCF 服務效能</span><span class="sxs-lookup"><span data-stu-id="06ce6-143">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
