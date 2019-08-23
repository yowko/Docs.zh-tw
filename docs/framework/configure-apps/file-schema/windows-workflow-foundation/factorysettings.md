---
title: <factorySettings>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 202aad17-1b8b-4c87-ad57-4ca5de18ed35
ms.openlocfilehash: fed7fe192e7bc5cb37347d2eae42f75bbf1b7dee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946317"
---
# <a name="factorysettings"></a><span data-ttu-id="90de0-101">\<factorySettings></span><span class="sxs-lookup"><span data-stu-id="90de0-101">\<factorySettings></span></span>
<span data-ttu-id="90de0-102">指定通道處理站快取的設定。</span><span class="sxs-lookup"><span data-stu-id="90de0-102">Specifies the settings of the channel factory cache.</span></span>  
  
<span data-ttu-id="90de0-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="90de0-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="90de0-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="90de0-104">\<behaviors></span></span>  
<span data-ttu-id="90de0-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="90de0-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="90de0-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="90de0-106">\<behavior></span></span>  
<span data-ttu-id="90de0-107">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="90de0-107">\<sendMessageChannelCache></span></span>  
<span data-ttu-id="90de0-108">\<factorySettings></span><span class="sxs-lookup"><span data-stu-id="90de0-108">\<factorySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90de0-109">語法</span><span class="sxs-lookup"><span data-stu-id="90de0-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean" >
        <factorySettings idleTimeout="TimeSpan" 
                         leaseTimeout="TimeSpan" 
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="90de0-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="90de0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="90de0-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="90de0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90de0-112">屬性</span><span class="sxs-lookup"><span data-stu-id="90de0-112">Attributes</span></span>  
  
|<span data-ttu-id="90de0-113">屬性</span><span class="sxs-lookup"><span data-stu-id="90de0-113">Attribute</span></span>|<span data-ttu-id="90de0-114">描述</span><span class="sxs-lookup"><span data-stu-id="90de0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="90de0-115">idleTimeout</span><span class="sxs-lookup"><span data-stu-id="90de0-115">idleTimeout</span></span>|<span data-ttu-id="90de0-116">TimeSpan 值，可指定物件處置前可在快取中維持閒置的最長時間間隔。</span><span class="sxs-lookup"><span data-stu-id="90de0-116">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="90de0-117">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="90de0-117">leaseTimeout</span></span>|<span data-ttu-id="90de0-118">TimeSpan 值, 指定從快取中移除物件的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="90de0-118">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="90de0-119">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="90de0-119">maxItemsInCache</span></span>|<span data-ttu-id="90de0-120">整數，可指定快取中可容納的最大物件數量。</span><span class="sxs-lookup"><span data-stu-id="90de0-120">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90de0-121">子元素</span><span class="sxs-lookup"><span data-stu-id="90de0-121">Child Elements</span></span>  
 <span data-ttu-id="90de0-122">無。</span><span class="sxs-lookup"><span data-stu-id="90de0-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="90de0-123">父項目</span><span class="sxs-lookup"><span data-stu-id="90de0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="90de0-124">項目</span><span class="sxs-lookup"><span data-stu-id="90de0-124">Element</span></span>|<span data-ttu-id="90de0-125">說明</span><span class="sxs-lookup"><span data-stu-id="90de0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90de0-126">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="90de0-126">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="90de0-127">一種服務行為, 可自訂快取共用層級、通道處理站快取的設定, 以及使用傳送訊息活動傳送訊息至服務端點的工作流程之通道快取的設定。</span><span class="sxs-lookup"><span data-stu-id="90de0-127">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90de0-128">備註</span><span class="sxs-lookup"><span data-stu-id="90de0-128">Remarks</span></span>  
 <span data-ttu-id="90de0-129">這個服務行為適用於將訊息傳送至服務端點的工作流程。</span><span class="sxs-lookup"><span data-stu-id="90de0-129">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="90de0-130">這些工作流程通常是用戶端工作流程，但也可以是裝載於 <xref:System.ServiceModel.WorkflowServiceHost> 中的工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="90de0-130">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="90de0-131">根據預設，在 <xref:System.ServiceModel.WorkflowServiceHost> 所裝載的工作流程中，<xref:System.ServiceModel.Activities.Send> 中的所有工作流程執行個體會共用 <xref:System.ServiceModel.WorkflowServiceHost> 傳訊活動使用的快取 (主機層級快取)。</span><span class="sxs-lookup"><span data-stu-id="90de0-131">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="90de0-132">針對並非由 <xref:System.ServiceModel.WorkflowServiceHost> 裝載的用戶端工作流程，快取只能供工作流程執行個體使用 (執行個體層級快取)。</span><span class="sxs-lookup"><span data-stu-id="90de0-132">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="90de0-133">工作流程中的傳送活動若在組態中定義了端點，快取會依預設停用。</span><span class="sxs-lookup"><span data-stu-id="90de0-133">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="90de0-134">如需如何變更通道處理站和通道快取的預設快取共用層級和快取設定的詳細資訊, 請參閱[變更傳送活動的快取共用層級](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="90de0-134">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="90de0-135">範例</span><span class="sxs-lookup"><span data-stu-id="90de0-135">Example</span></span>  
 <span data-ttu-id="90de0-136">在裝載的工作流程服務中，您可以在應用程式組態檔中，指定處理站快取和通道快取設定。</span><span class="sxs-lookup"><span data-stu-id="90de0-136">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="90de0-137">若要執行這項操作，請加入包含處理站快取設定和通道快取的服務行為，然後將這個服務行為加入您的服務中。</span><span class="sxs-lookup"><span data-stu-id="90de0-137">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="90de0-138">下列範例會顯示設定檔案的內容, 其中包含`MyChannelCacheBehavior`具有自訂處理站快取和通道快取設定的服務行為。</span><span class="sxs-lookup"><span data-stu-id="90de0-138">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="90de0-139">此服務行為會透過`behaviorConfiguration`屬性加入至服務。</span><span class="sxs-lookup"><span data-stu-id="90de0-139">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="90de0-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90de0-140">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- <xref:System.ServiceModel.Activities.ChannelCacheSettings>
- [<span data-ttu-id="90de0-141">變更傳送活動的快取共用層級</span><span class="sxs-lookup"><span data-stu-id="90de0-141">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
