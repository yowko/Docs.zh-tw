---
title: '&lt;sendMessageChannelCache&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d9d4fbfe06209806ab1be9887b2e26d1a11a8954
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltsendmessagechannelcachegt"></a><span data-ttu-id="5a3c8-102">&lt;sendMessageChannelCache&gt;</span><span class="sxs-lookup"><span data-stu-id="5a3c8-102">&lt;sendMessageChannelCache&gt;</span></span>
<span data-ttu-id="5a3c8-103">服務行為，能讓您自訂快取共用層級、 通道處理站快取的設定和傳送訊息至服務端點使用傳訊活動傳送的工作流程之通道快取的設定。</span><span class="sxs-lookup"><span data-stu-id="5a3c8-103">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
<span data-ttu-id="5a3c8-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="5a3c8-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="5a3c8-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="5a3c8-105">\<behaviors></span></span>  
<span data-ttu-id="5a3c8-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5a3c8-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="5a3c8-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="5a3c8-107">\<behavior></span></span>  
<span data-ttu-id="5a3c8-108">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="5a3c8-108">\<sendMessageChannelCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a3c8-109">語法</span><span class="sxs-lookup"><span data-stu-id="5a3c8-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5a3c8-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5a3c8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="5a3c8-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5a3c8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5a3c8-112">屬性</span><span class="sxs-lookup"><span data-stu-id="5a3c8-112">Attributes</span></span>  
  
|<span data-ttu-id="5a3c8-113">屬性</span><span class="sxs-lookup"><span data-stu-id="5a3c8-113">Attribute</span></span>|<span data-ttu-id="5a3c8-114">描述</span><span class="sxs-lookup"><span data-stu-id="5a3c8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5a3c8-115">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="5a3c8-115">allowUnsafeCaching</span></span>|<span data-ttu-id="5a3c8-116">指出是否要開啟快取功能的布林值。</span><span class="sxs-lookup"><span data-stu-id="5a3c8-116">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="5a3c8-117">如果您的工作流程服務有自訂繫結或自訂行為，快取可能會不安全，因此快取功能會依預設停用。</span><span class="sxs-lookup"><span data-stu-id="5a3c8-117">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="5a3c8-118">不過，如果您想要開啟快取上設定此屬性為**true**。</span><span class="sxs-lookup"><span data-stu-id="5a3c8-118">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5a3c8-119">子元素</span><span class="sxs-lookup"><span data-stu-id="5a3c8-119">Child Elements</span></span>  
  
|<span data-ttu-id="5a3c8-120">項目</span><span class="sxs-lookup"><span data-stu-id="5a3c8-120">Element</span></span>|<span data-ttu-id="5a3c8-121">說明</span><span class="sxs-lookup"><span data-stu-id="5a3c8-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a3c8-122">\<channelSettings ></span><span class="sxs-lookup"><span data-stu-id="5a3c8-122">\<channelSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/channelsettings.md)|<span data-ttu-id="5a3c8-123">指定通道快取的設定。</span><span class="sxs-lookup"><span data-stu-id="5a3c8-123">Specifies the settings of the channel cache.</span></span>|  
|[<span data-ttu-id="5a3c8-124">\<factorySettings ></span><span class="sxs-lookup"><span data-stu-id="5a3c8-124">\<factorySettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/factorysettings.md)|<span data-ttu-id="5a3c8-125">指定通道處理站快取的設定。</span><span class="sxs-lookup"><span data-stu-id="5a3c8-125">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5a3c8-126">父項目</span><span class="sxs-lookup"><span data-stu-id="5a3c8-126">Parent Elements</span></span>  
  
|<span data-ttu-id="5a3c8-127">項目</span><span class="sxs-lookup"><span data-stu-id="5a3c8-127">Element</span></span>|<span data-ttu-id="5a3c8-128">說明</span><span class="sxs-lookup"><span data-stu-id="5a3c8-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5a3c8-129">\<行為 > 的\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="5a3c8-129">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="5a3c8-130">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="5a3c8-130">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5a3c8-131">備註</span><span class="sxs-lookup"><span data-stu-id="5a3c8-131">Remarks</span></span>  
 <span data-ttu-id="5a3c8-132">這個服務行為適用於將訊息傳送至服務端點的工作流程。</span><span class="sxs-lookup"><span data-stu-id="5a3c8-132">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="5a3c8-133">這些工作流程通常是用戶端工作流程，但也可以是裝載於 <xref:System.ServiceModel.WorkflowServiceHost> 中的工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="5a3c8-133">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="5a3c8-134">根據預設，在 <xref:System.ServiceModel.WorkflowServiceHost> 所裝載的工作流程中，<xref:System.ServiceModel.Activities.Send> 中的所有工作流程執行個體會共用 <xref:System.ServiceModel.WorkflowServiceHost> 傳訊活動使用的快取 (主機層級快取)。</span><span class="sxs-lookup"><span data-stu-id="5a3c8-134">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="5a3c8-135">針對並非由 <xref:System.ServiceModel.WorkflowServiceHost> 裝載的用戶端工作流程，快取只能供工作流程執行個體使用 (執行個體層級快取)。</span><span class="sxs-lookup"><span data-stu-id="5a3c8-135">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="5a3c8-136">工作流程中的傳送活動若在組態中定義了端點，快取會依預設停用。</span><span class="sxs-lookup"><span data-stu-id="5a3c8-136">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]<span data-ttu-id="5a3c8-137">如何變更預設快取共用層級和快取通道處理站和通道快取設定，請參閱[傳送活動的變更快取共用層級](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="5a3c8-137"> how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a3c8-138">範例</span><span class="sxs-lookup"><span data-stu-id="5a3c8-138">Example</span></span>  
 <span data-ttu-id="5a3c8-139">在裝載的工作流程服務中，您可以在應用程式組態檔中，指定處理站快取和通道快取設定。</span><span class="sxs-lookup"><span data-stu-id="5a3c8-139">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="5a3c8-140">若要執行這項操作，請加入包含處理站快取設定和通道快取的服務行為，然後將這個服務行為加入您的服務中。</span><span class="sxs-lookup"><span data-stu-id="5a3c8-140">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="5a3c8-141">下列範例顯示組態檔中包含的內容**MyChannelCacheBehavior**使用自訂處理站快取和通道快取設定服務行為。</span><span class="sxs-lookup"><span data-stu-id="5a3c8-141">The following example shows the contents of a configuration file that contains the **MyChannelCacheBehavior**  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="5a3c8-142">這個服務行為加入至服務，透過**behaviorConfiguarion**屬性。</span><span class="sxs-lookup"><span data-stu-id="5a3c8-142">This service behavior is added to the service through the **behaviorConfiguarion** attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5a3c8-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5a3c8-143">See Also</span></span>  
 <xref:System.ServiceModel.Activities.SendMessageChannelCache>  
 <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>  
 <xref:System.ServiceModel.Activities.Send>  
 [<span data-ttu-id="5a3c8-144">變更快取共用層級傳送活動</span><span class="sxs-lookup"><span data-stu-id="5a3c8-144">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
