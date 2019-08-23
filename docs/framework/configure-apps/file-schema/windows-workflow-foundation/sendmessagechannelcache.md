---
title: <sendMessageChannelCache>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: de53eb16d53d1e37209e36f2f6bfdc4bdfd84465
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947550"
---
# <a name="sendmessagechannelcache"></a><span data-ttu-id="35ac3-101">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="35ac3-101">\<sendMessageChannelCache></span></span>
<span data-ttu-id="35ac3-102">一種服務行為, 可自訂快取共用層級、通道處理站快取的設定, 以及使用傳送訊息活動傳送訊息至服務端點的工作流程之通道快取的設定。</span><span class="sxs-lookup"><span data-stu-id="35ac3-102">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
<span data-ttu-id="35ac3-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="35ac3-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="35ac3-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="35ac3-104">\<behaviors></span></span>  
<span data-ttu-id="35ac3-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="35ac3-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="35ac3-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="35ac3-106">\<behavior></span></span>  
<span data-ttu-id="35ac3-107">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="35ac3-107">\<sendMessageChannelCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35ac3-108">語法</span><span class="sxs-lookup"><span data-stu-id="35ac3-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean">
        <channelSettings idleTimeout="TimeSpan"
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
        <factorySettings idleTimeout="TimeSpan" 
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="35ac3-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="35ac3-109">Attributes and Elements</span></span>  
 <span data-ttu-id="35ac3-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="35ac3-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="35ac3-111">屬性</span><span class="sxs-lookup"><span data-stu-id="35ac3-111">Attributes</span></span>  
  
|<span data-ttu-id="35ac3-112">屬性</span><span class="sxs-lookup"><span data-stu-id="35ac3-112">Attribute</span></span>|<span data-ttu-id="35ac3-113">說明</span><span class="sxs-lookup"><span data-stu-id="35ac3-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="35ac3-114">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="35ac3-114">allowUnsafeCaching</span></span>|<span data-ttu-id="35ac3-115">指出是否要開啟快取功能的布林值。</span><span class="sxs-lookup"><span data-stu-id="35ac3-115">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="35ac3-116">如果您的工作流程服務有自訂繫結或自訂行為，快取可能會不安全，因此快取功能會依預設停用。</span><span class="sxs-lookup"><span data-stu-id="35ac3-116">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="35ac3-117">不過, 如果您想要開啟快取, 請將此屬性設定為**true**。</span><span class="sxs-lookup"><span data-stu-id="35ac3-117">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="35ac3-118">子元素</span><span class="sxs-lookup"><span data-stu-id="35ac3-118">Child Elements</span></span>  
  
|<span data-ttu-id="35ac3-119">項目</span><span class="sxs-lookup"><span data-stu-id="35ac3-119">Element</span></span>|<span data-ttu-id="35ac3-120">描述</span><span class="sxs-lookup"><span data-stu-id="35ac3-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35ac3-121">\<channelSettings></span><span class="sxs-lookup"><span data-stu-id="35ac3-121">\<channelSettings></span></span>](channelsettings.md)|<span data-ttu-id="35ac3-122">指定通道快取的設定。</span><span class="sxs-lookup"><span data-stu-id="35ac3-122">Specifies the settings of the channel cache.</span></span>|  
|[<span data-ttu-id="35ac3-123">\<factorySettings></span><span class="sxs-lookup"><span data-stu-id="35ac3-123">\<factorySettings></span></span>](factorysettings.md)|<span data-ttu-id="35ac3-124">指定通道處理站快取的設定。</span><span class="sxs-lookup"><span data-stu-id="35ac3-124">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="35ac3-125">父項目</span><span class="sxs-lookup"><span data-stu-id="35ac3-125">Parent Elements</span></span>  
  
|<span data-ttu-id="35ac3-126">項目</span><span class="sxs-lookup"><span data-stu-id="35ac3-126">Element</span></span>|<span data-ttu-id="35ac3-127">描述</span><span class="sxs-lookup"><span data-stu-id="35ac3-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="35ac3-128">\<serviceBehaviors > 的\<行為 ></span><span class="sxs-lookup"><span data-stu-id="35ac3-128">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="35ac3-129">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="35ac3-129">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35ac3-130">備註</span><span class="sxs-lookup"><span data-stu-id="35ac3-130">Remarks</span></span>  
 <span data-ttu-id="35ac3-131">這個服務行為適用於將訊息傳送至服務端點的工作流程。</span><span class="sxs-lookup"><span data-stu-id="35ac3-131">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="35ac3-132">這些工作流程通常是用戶端工作流程，但也可以是裝載於 <xref:System.ServiceModel.WorkflowServiceHost> 中的工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="35ac3-132">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="35ac3-133">根據預設，在 <xref:System.ServiceModel.WorkflowServiceHost> 所裝載的工作流程中，<xref:System.ServiceModel.Activities.Send> 中的所有工作流程執行個體會共用 <xref:System.ServiceModel.WorkflowServiceHost> 傳訊活動使用的快取 (主機層級快取)。</span><span class="sxs-lookup"><span data-stu-id="35ac3-133">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="35ac3-134">針對並非由 <xref:System.ServiceModel.WorkflowServiceHost> 裝載的用戶端工作流程，快取只能供工作流程執行個體使用 (執行個體層級快取)。</span><span class="sxs-lookup"><span data-stu-id="35ac3-134">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="35ac3-135">工作流程中的傳送活動若在組態中定義了端點，快取會依預設停用。</span><span class="sxs-lookup"><span data-stu-id="35ac3-135">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="35ac3-136">如需如何變更通道處理站和通道快取的預設快取共用層級和快取設定的詳細資訊, 請參閱[變更傳送活動的快取共用層級](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="35ac3-136">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="35ac3-137">範例</span><span class="sxs-lookup"><span data-stu-id="35ac3-137">Example</span></span>  
 <span data-ttu-id="35ac3-138">在裝載的工作流程服務中，您可以在應用程式組態檔中，指定處理站快取和通道快取設定。</span><span class="sxs-lookup"><span data-stu-id="35ac3-138">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="35ac3-139">若要執行這項操作，請加入包含處理站快取設定和通道快取的服務行為，然後將這個服務行為加入您的服務中。</span><span class="sxs-lookup"><span data-stu-id="35ac3-139">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="35ac3-140">下列範例會顯示設定檔案的內容, 其中包含`MyChannelCacheBehavior`具有自訂處理站快取和通道快取設定的服務行為。</span><span class="sxs-lookup"><span data-stu-id="35ac3-140">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior`  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="35ac3-141">此服務行為會透過`behaviorConfiguration`屬性加入至服務。</span><span class="sxs-lookup"><span data-stu-id="35ac3-141">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>    
  <system.serviceModel>  
    <!-- List of other config sections here -->   
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->   
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="35ac3-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="35ac3-142">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [<span data-ttu-id="35ac3-143">變更傳送活動的快取共用層級</span><span class="sxs-lookup"><span data-stu-id="35ac3-143">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
