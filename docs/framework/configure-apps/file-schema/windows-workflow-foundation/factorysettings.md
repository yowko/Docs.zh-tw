---
title: <factorySettings>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 202aad17-1b8b-4c87-ad57-4ca5de18ed35
ms.openlocfilehash: d8e87799962638ac6514ebb31bbc9e209b39c98d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790165"
---
# <a name="factorysettings"></a><span data-ttu-id="96b04-101">\<factorySettings></span><span class="sxs-lookup"><span data-stu-id="96b04-101">\<factorySettings></span></span>
<span data-ttu-id="96b04-102">指定通道處理站快取的設定。</span><span class="sxs-lookup"><span data-stu-id="96b04-102">Specifies the settings of the channel factory cache.</span></span>  
  
<span data-ttu-id="96b04-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="96b04-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="96b04-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="96b04-104">\<behaviors></span></span>  
<span data-ttu-id="96b04-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="96b04-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="96b04-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="96b04-106">\<behavior></span></span>  
<span data-ttu-id="96b04-107">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="96b04-107">\<sendMessageChannelCache></span></span>  
<span data-ttu-id="96b04-108">\<factorySettings></span><span class="sxs-lookup"><span data-stu-id="96b04-108">\<factorySettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96b04-109">語法</span><span class="sxs-lookup"><span data-stu-id="96b04-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96b04-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="96b04-110">Attributes and Elements</span></span>  
 <span data-ttu-id="96b04-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="96b04-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96b04-112">屬性</span><span class="sxs-lookup"><span data-stu-id="96b04-112">Attributes</span></span>  
  
|<span data-ttu-id="96b04-113">屬性</span><span class="sxs-lookup"><span data-stu-id="96b04-113">Attribute</span></span>|<span data-ttu-id="96b04-114">描述</span><span class="sxs-lookup"><span data-stu-id="96b04-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="96b04-115">idleTimeout</span><span class="sxs-lookup"><span data-stu-id="96b04-115">idleTimeout</span></span>|<span data-ttu-id="96b04-116">TimeSpan 值，可指定物件處置前可在快取中維持閒置的最長時間間隔。</span><span class="sxs-lookup"><span data-stu-id="96b04-116">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="96b04-117">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="96b04-117">leaseTimeout</span></span>|<span data-ttu-id="96b04-118">TimeSpan 值，指定的間隔時間後從快取移除物件。</span><span class="sxs-lookup"><span data-stu-id="96b04-118">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="96b04-119">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="96b04-119">maxItemsInCache</span></span>|<span data-ttu-id="96b04-120">整數，可指定快取中可容納的最大物件數量。</span><span class="sxs-lookup"><span data-stu-id="96b04-120">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="96b04-121">子元素</span><span class="sxs-lookup"><span data-stu-id="96b04-121">Child Elements</span></span>  
 <span data-ttu-id="96b04-122">無。</span><span class="sxs-lookup"><span data-stu-id="96b04-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="96b04-123">父項目</span><span class="sxs-lookup"><span data-stu-id="96b04-123">Parent Elements</span></span>  
  
|<span data-ttu-id="96b04-124">項目</span><span class="sxs-lookup"><span data-stu-id="96b04-124">Element</span></span>|<span data-ttu-id="96b04-125">描述</span><span class="sxs-lookup"><span data-stu-id="96b04-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96b04-126">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="96b04-126">\<sendMessageChannelCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|<span data-ttu-id="96b04-127">服務行為可讓您自訂快取共用層級、 通道處理站快取的設定，以及傳送訊息至服務端點使用傳訊活動傳送的工作流程的通道快取的設定。</span><span class="sxs-lookup"><span data-stu-id="96b04-127">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96b04-128">備註</span><span class="sxs-lookup"><span data-stu-id="96b04-128">Remarks</span></span>  
 <span data-ttu-id="96b04-129">這個服務行為適用於將訊息傳送至服務端點的工作流程。</span><span class="sxs-lookup"><span data-stu-id="96b04-129">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="96b04-130">這些工作流程通常是用戶端工作流程，但也可以是裝載於 <xref:System.ServiceModel.WorkflowServiceHost> 中的工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="96b04-130">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="96b04-131">根據預設，在 <xref:System.ServiceModel.WorkflowServiceHost> 所裝載的工作流程中，<xref:System.ServiceModel.Activities.Send> 中的所有工作流程執行個體會共用 <xref:System.ServiceModel.WorkflowServiceHost> 傳訊活動使用的快取 (主機層級快取)。</span><span class="sxs-lookup"><span data-stu-id="96b04-131">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="96b04-132">針對並非由 <xref:System.ServiceModel.WorkflowServiceHost> 裝載的用戶端工作流程，快取只能供工作流程執行個體使用 (執行個體層級快取)。</span><span class="sxs-lookup"><span data-stu-id="96b04-132">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="96b04-133">工作流程中的傳送活動若在組態中定義了端點，快取會依預設停用。</span><span class="sxs-lookup"><span data-stu-id="96b04-133">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="96b04-134">如需如何變更預設快取共用層級以及通道處理站和通道快取的快取設定的詳細資訊，請參閱[變更傳送活動的快取共用層級](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="96b04-134">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="96b04-135">範例</span><span class="sxs-lookup"><span data-stu-id="96b04-135">Example</span></span>  
 <span data-ttu-id="96b04-136">在裝載的工作流程服務中，您可以在應用程式組態檔中，指定處理站快取和通道快取設定。</span><span class="sxs-lookup"><span data-stu-id="96b04-136">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="96b04-137">若要執行這項操作，請加入包含處理站快取設定和通道快取的服務行為，然後將這個服務行為加入您的服務中。</span><span class="sxs-lookup"><span data-stu-id="96b04-137">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="96b04-138">下列範例顯示組態檔中包含的內容**MyChannelCacheBehavior**服務行為及自訂的處理站快取和通道快取設定。</span><span class="sxs-lookup"><span data-stu-id="96b04-138">The following example shows the contents of a configuration file that contains the **MyChannelCacheBehavior**  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="96b04-139">這個服務行為新增至服務，透過**behaviorConfiguarion**屬性。</span><span class="sxs-lookup"><span data-stu-id="96b04-139">This service behavior is added to the service through the **behaviorConfiguarion** attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="96b04-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="96b04-140">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- <xref:System.ServiceModel.Activities.ChannelCacheSettings>
- [<span data-ttu-id="96b04-141">變更傳送活動的快取共用層級</span><span class="sxs-lookup"><span data-stu-id="96b04-141">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
