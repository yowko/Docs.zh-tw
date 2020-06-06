---
title: <serviceThrottling>
ms.date: 03/30/2017
ms.assetid: a337d064-1e64-4209-b4a9-db7fdb7e3eaf
ms.openlocfilehash: ad87a5876381a7224341babdb076c85edcd1dd87
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399568"
---
# \<serviceThrottling>
<span data-ttu-id="6164f-101">指定 Windows Communication Foundation (WCF) 服務的節流機制。</span><span class="sxs-lookup"><span data-stu-id="6164f-101">Specifies the throttling mechanism of a Windows Communication Foundation (WCF) service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceThrottling>**  
  
## <a name="syntax"></a><span data-ttu-id="6164f-102">語法</span><span class="sxs-lookup"><span data-stu-id="6164f-102">Syntax</span></span>  
  
```xml  
<serviceThrottling maxConcurrentCalls="Integer"
                   maxConcurrentInstances="Integer"
                   maxConcurrentSessions="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6164f-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6164f-103">Attributes and Elements</span></span>  
 <span data-ttu-id="6164f-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6164f-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6164f-105">屬性</span><span class="sxs-lookup"><span data-stu-id="6164f-105">Attributes</span></span>  
  
|<span data-ttu-id="6164f-106">屬性</span><span class="sxs-lookup"><span data-stu-id="6164f-106">Attribute</span></span>|<span data-ttu-id="6164f-107">描述</span><span class="sxs-lookup"><span data-stu-id="6164f-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6164f-108">maxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="6164f-108">maxConcurrentCalls</span></span>|<span data-ttu-id="6164f-109">正整數，限制同時在 <xref:System.ServiceModel.ServiceHost> 上進行處理的訊息數目。</span><span class="sxs-lookup"><span data-stu-id="6164f-109">A positive integer that limits the number of messages that currently process across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="6164f-110">超出上限的呼叫將排入佇列。</span><span class="sxs-lookup"><span data-stu-id="6164f-110">Calls in excess of the limit are queued.</span></span> <span data-ttu-id="6164f-111">將這個值設定為 0 相當於設定為 Int32.MaxValue。</span><span class="sxs-lookup"><span data-stu-id="6164f-111">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="6164f-112">預設值是 16 \* 處理器計數。</span><span class="sxs-lookup"><span data-stu-id="6164f-112">The default is 16 \* processor count.</span></span>|  
|<span data-ttu-id="6164f-113">maxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="6164f-113">maxConcurrentInstances</span></span>|<span data-ttu-id="6164f-114">正整數，限制同時在 <xref:System.ServiceModel.InstanceContext> 上執行的 <xref:System.ServiceModel.ServiceHost> 物件數目。</span><span class="sxs-lookup"><span data-stu-id="6164f-114">A positive integer that limits the number of <xref:System.ServiceModel.InstanceContext> objects that execute at one time across a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="6164f-115">當限制之內的位置可供使用時，建立其他執行個體的要求便會進入佇列並完成。</span><span class="sxs-lookup"><span data-stu-id="6164f-115">Requests to create additional instances are queued and complete when a slot below the limit becomes available.</span></span> <span data-ttu-id="6164f-116">預設值是 maxConcurrentSessions 和 MaxConcurrentCalls 的總和</span><span class="sxs-lookup"><span data-stu-id="6164f-116">The default is the sum of maxConcurrentSessions and MaxConcurrentCalls</span></span>|  
|<span data-ttu-id="6164f-117">maxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="6164f-117">maxConcurrentSessions</span></span>|<span data-ttu-id="6164f-118">正整數，限制 <xref:System.ServiceModel.ServiceHost> 物件可以接受的工作階段數目。</span><span class="sxs-lookup"><span data-stu-id="6164f-118">A positive integer that limits the number of sessions a <xref:System.ServiceModel.ServiceHost> object can accept.</span></span><br /><br /> <span data-ttu-id="6164f-119">服務將接受超過限制的連線，但只有低於限制個數的通道為作用中 (可從該通道讀取訊息)。</span><span class="sxs-lookup"><span data-stu-id="6164f-119">The service will accept connections in excess of the limit, but only the channels below the limit are active (messages are read from the channel).</span></span> <span data-ttu-id="6164f-120">將這個值設定為 0 相當於設定為 Int32.MaxValue。</span><span class="sxs-lookup"><span data-stu-id="6164f-120">Setting this value to 0 is equivalent to setting it to Int32.MaxValue.</span></span> <span data-ttu-id="6164f-121">預設值是 100 \* 處理器計數。</span><span class="sxs-lookup"><span data-stu-id="6164f-121">The default is 100 \* processor count.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6164f-122">子元素</span><span class="sxs-lookup"><span data-stu-id="6164f-122">Child Elements</span></span>  
 <span data-ttu-id="6164f-123">無。</span><span class="sxs-lookup"><span data-stu-id="6164f-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6164f-124">父項目</span><span class="sxs-lookup"><span data-stu-id="6164f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="6164f-125">元素</span><span class="sxs-lookup"><span data-stu-id="6164f-125">Element</span></span>|<span data-ttu-id="6164f-126">描述</span><span class="sxs-lookup"><span data-stu-id="6164f-126">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="6164f-127">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="6164f-127">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6164f-128">備註</span><span class="sxs-lookup"><span data-stu-id="6164f-128">Remarks</span></span>  
 <span data-ttu-id="6164f-129">節流控制會限制同時呼叫、並行執行個體或工作階段的數目，以防止過度消耗資源。</span><span class="sxs-lookup"><span data-stu-id="6164f-129">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span>  
  
 <span data-ttu-id="6164f-130">每次達到這些屬性值時，就會寫入追蹤。</span><span class="sxs-lookup"><span data-stu-id="6164f-130">A trace is written every time the value of attributes is reached.</span></span> <span data-ttu-id="6164f-131">第一個追蹤會寫入成為警告。</span><span class="sxs-lookup"><span data-stu-id="6164f-131">The first trace is written as a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6164f-132">範例</span><span class="sxs-lookup"><span data-stu-id="6164f-132">Example</span></span>  
 <span data-ttu-id="6164f-133">下列組態範例指定服務將同時呼叫上限限制為 2，且將並行執行個體上限限制為 10。</span><span class="sxs-lookup"><span data-stu-id="6164f-133">The following configuration example specifies that the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span> <span data-ttu-id="6164f-134">如需執行此範例的詳細範例，請參閱[節流](../../../wcf/samples/throttling.md)。</span><span class="sxs-lookup"><span data-stu-id="6164f-134">For a detailed example of running this example, see [Throttling](../../../wcf/samples/throttling.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6164f-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6164f-135">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
- <xref:System.ServiceModel.Configuration.ServiceThrottlingElement>
- [<span data-ttu-id="6164f-136">使用 ServiceThrottlingBehavior 來控制 WCF 服務效能</span><span class="sxs-lookup"><span data-stu-id="6164f-136">Using ServiceThrottlingBehavior to Control WCF Service Performance</span></span>](../../../wcf/feature-details/using-servicethrottlingbehavior-to-control-wcf-service-performance.md)
