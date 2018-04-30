---
title: '&lt;factorySettings&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 202aad17-1b8b-4c87-ad57-4ca5de18ed35
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ebca545a7d2d9b00a0e9eb82012450785e68fd58
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/30/2018
---
# <a name="ltfactorysettingsgt"></a><span data-ttu-id="d87fc-102">&lt;factorySettings&gt;</span><span class="sxs-lookup"><span data-stu-id="d87fc-102">&lt;factorySettings&gt;</span></span>
<span data-ttu-id="d87fc-103">指定通道處理站快取的設定。</span><span class="sxs-lookup"><span data-stu-id="d87fc-103">Specifies the settings of the channel factory cache.</span></span>  
  
<span data-ttu-id="d87fc-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d87fc-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d87fc-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="d87fc-105">\<behaviors></span></span>  
<span data-ttu-id="d87fc-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="d87fc-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="d87fc-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="d87fc-107">\<behavior></span></span>  
<span data-ttu-id="d87fc-108">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="d87fc-108">\<sendMessageChannelCache></span></span>  
<span data-ttu-id="d87fc-109">\<factorySettings ></span><span class="sxs-lookup"><span data-stu-id="d87fc-109">\<factorySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d87fc-110">語法</span><span class="sxs-lookup"><span data-stu-id="d87fc-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d87fc-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d87fc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d87fc-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d87fc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d87fc-113">屬性</span><span class="sxs-lookup"><span data-stu-id="d87fc-113">Attributes</span></span>  
  
|<span data-ttu-id="d87fc-114">屬性</span><span class="sxs-lookup"><span data-stu-id="d87fc-114">Attribute</span></span>|<span data-ttu-id="d87fc-115">描述</span><span class="sxs-lookup"><span data-stu-id="d87fc-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d87fc-116">idleTimeout</span><span class="sxs-lookup"><span data-stu-id="d87fc-116">idleTimeout</span></span>|<span data-ttu-id="d87fc-117">TimeSpan 值，可指定物件處置前可在快取中維持閒置的最長時間間隔。</span><span class="sxs-lookup"><span data-stu-id="d87fc-117">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="d87fc-118">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="d87fc-118">leaseTimeout</span></span>|<span data-ttu-id="d87fc-119">TimeSpan 值，指定一段時間之後從快取移除物件。</span><span class="sxs-lookup"><span data-stu-id="d87fc-119">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="d87fc-120">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="d87fc-120">maxItemsInCache</span></span>|<span data-ttu-id="d87fc-121">整數，可指定快取中可容納的最大物件數量。</span><span class="sxs-lookup"><span data-stu-id="d87fc-121">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d87fc-122">子項目</span><span class="sxs-lookup"><span data-stu-id="d87fc-122">Child Elements</span></span>  
 <span data-ttu-id="d87fc-123">無。</span><span class="sxs-lookup"><span data-stu-id="d87fc-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d87fc-124">父項目</span><span class="sxs-lookup"><span data-stu-id="d87fc-124">Parent Elements</span></span>  
  
|<span data-ttu-id="d87fc-125">項目</span><span class="sxs-lookup"><span data-stu-id="d87fc-125">Element</span></span>|<span data-ttu-id="d87fc-126">描述</span><span class="sxs-lookup"><span data-stu-id="d87fc-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d87fc-127">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="d87fc-127">\<sendMessageChannelCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|<span data-ttu-id="d87fc-128">服務行為，能讓您自訂快取共用層級、 通道處理站快取的設定和傳送訊息至服務端點使用傳訊活動傳送的工作流程之通道快取的設定。</span><span class="sxs-lookup"><span data-stu-id="d87fc-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d87fc-129">備註</span><span class="sxs-lookup"><span data-stu-id="d87fc-129">Remarks</span></span>  
 <span data-ttu-id="d87fc-130">這個服務行為適用於將訊息傳送至服務端點的工作流程。</span><span class="sxs-lookup"><span data-stu-id="d87fc-130">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="d87fc-131">這些工作流程通常是用戶端工作流程，但也可以是裝載於 <xref:System.ServiceModel.WorkflowServiceHost> 中的工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="d87fc-131">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="d87fc-132">根據預設，在 <xref:System.ServiceModel.WorkflowServiceHost> 所裝載的工作流程中，<xref:System.ServiceModel.Activities.Send> 中的所有工作流程執行個體會共用 <xref:System.ServiceModel.WorkflowServiceHost> 傳訊活動使用的快取 (主機層級快取)。</span><span class="sxs-lookup"><span data-stu-id="d87fc-132">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="d87fc-133">針對並非由 <xref:System.ServiceModel.WorkflowServiceHost> 裝載的用戶端工作流程，快取只能供工作流程執行個體使用 (執行個體層級快取)。</span><span class="sxs-lookup"><span data-stu-id="d87fc-133">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="d87fc-134">工作流程中的傳送活動若在組態中定義了端點，快取會依預設停用。</span><span class="sxs-lookup"><span data-stu-id="d87fc-134">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="d87fc-135">如需如何變更預設快取共用層級以及通道處理站和通道快取的快取設定的詳細資訊，請參閱[傳送活動的變更快取共用層級](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="d87fc-135">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d87fc-136">範例</span><span class="sxs-lookup"><span data-stu-id="d87fc-136">Example</span></span>  
 <span data-ttu-id="d87fc-137">在裝載的工作流程服務中，您可以在應用程式組態檔中，指定處理站快取和通道快取設定。</span><span class="sxs-lookup"><span data-stu-id="d87fc-137">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="d87fc-138">若要執行這項操作，請加入包含處理站快取設定和通道快取的服務行為，然後將這個服務行為加入您的服務中。</span><span class="sxs-lookup"><span data-stu-id="d87fc-138">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="d87fc-139">下列範例顯示組態檔中包含的內容**MyChannelCacheBehavior**使用自訂處理站快取和通道快取設定服務行為。</span><span class="sxs-lookup"><span data-stu-id="d87fc-139">The following example shows the contents of a configuration file that contains the **MyChannelCacheBehavior**  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="d87fc-140">這個服務行為加入至服務，透過**behaviorConfiguarion**屬性。</span><span class="sxs-lookup"><span data-stu-id="d87fc-140">This service behavior is added to the service through the **behaviorConfiguarion** attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d87fc-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d87fc-141">See Also</span></span>  
 <xref:System.ServiceModel.Activities.SendMessageChannelCache>  
 <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>  
 <xref:System.ServiceModel.Activities.Send>  
 <xref:System.ServiceModel.Activities.ChannelCacheSettings>  
 [<span data-ttu-id="d87fc-142">變更傳送活動的快取共用層級</span><span class="sxs-lookup"><span data-stu-id="d87fc-142">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
