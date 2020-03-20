---
title: <sendMessageChannelCache>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: b68c6d2e526eb22328806558d7c167b7f2ed0820
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151997"
---
# <a name="sendmessagechannelcache"></a><span data-ttu-id="d34af-101">\<發送消息頻道緩存></span><span class="sxs-lookup"><span data-stu-id="d34af-101">\<sendMessageChannelCache></span></span>
<span data-ttu-id="d34af-102">這個服務行為可讓您自訂快取共用層級、通道處理站快取的設定，以及工作流程使用傳送訊息活動來傳送訊息至服務端點的通道快取設定。</span><span class="sxs-lookup"><span data-stu-id="d34af-102">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>  
  
<span data-ttu-id="d34af-103">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d34af-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d34af-104">&nbsp;&nbsp;[**\<系統。服務模式>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d34af-104">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="d34af-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<行為>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d34af-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="d34af-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<服務行為>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d34af-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="d34af-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<行為>**](behavior-of-servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="d34af-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="d34af-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<發送消息通道緩存>**</span><span class="sxs-lookup"><span data-stu-id="d34af-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sendMessageChannelCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d34af-109">語法</span><span class="sxs-lookup"><span data-stu-id="d34af-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d34af-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d34af-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d34af-111">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="d34af-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d34af-112">屬性</span><span class="sxs-lookup"><span data-stu-id="d34af-112">Attributes</span></span>  
  
|<span data-ttu-id="d34af-113">屬性</span><span class="sxs-lookup"><span data-stu-id="d34af-113">Attribute</span></span>|<span data-ttu-id="d34af-114">描述</span><span class="sxs-lookup"><span data-stu-id="d34af-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d34af-115">allowUnsafeCaching</span><span class="sxs-lookup"><span data-stu-id="d34af-115">allowUnsafeCaching</span></span>|<span data-ttu-id="d34af-116">指出是否要開啟快取功能的布林值。</span><span class="sxs-lookup"><span data-stu-id="d34af-116">A Boolean value that indicates whether to turn caching on.</span></span> <span data-ttu-id="d34af-117">如果您的工作流程服務有自訂繫結或自訂行為，快取可能會不安全，因此快取功能會依預設停用。</span><span class="sxs-lookup"><span data-stu-id="d34af-117">If your workflow service has custom bindings or custom behaviors, caching could be unsecure and therefore is disabled by default.</span></span> <span data-ttu-id="d34af-118">但是，如果要在將緩存打開，則將此屬性設置為**true**。</span><span class="sxs-lookup"><span data-stu-id="d34af-118">However, if you want to turn caching on set this property to **true**.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d34af-119">子元素</span><span class="sxs-lookup"><span data-stu-id="d34af-119">Child Elements</span></span>  
  
|<span data-ttu-id="d34af-120">元素</span><span class="sxs-lookup"><span data-stu-id="d34af-120">Element</span></span>|<span data-ttu-id="d34af-121">描述</span><span class="sxs-lookup"><span data-stu-id="d34af-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d34af-122">\<通道設置></span><span class="sxs-lookup"><span data-stu-id="d34af-122">\<channelSettings></span></span>](channelsettings.md)|<span data-ttu-id="d34af-123">指定通道快取的設定。</span><span class="sxs-lookup"><span data-stu-id="d34af-123">Specifies the settings of the channel cache.</span></span>|  
|[<span data-ttu-id="d34af-124">\<工廠設置></span><span class="sxs-lookup"><span data-stu-id="d34af-124">\<factorySettings></span></span>](factorysettings.md)|<span data-ttu-id="d34af-125">指定通道處理站快取的設定。</span><span class="sxs-lookup"><span data-stu-id="d34af-125">Specifies the settings of the channel factory cache.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d34af-126">父項目</span><span class="sxs-lookup"><span data-stu-id="d34af-126">Parent Elements</span></span>  
  
|<span data-ttu-id="d34af-127">元素</span><span class="sxs-lookup"><span data-stu-id="d34af-127">Element</span></span>|<span data-ttu-id="d34af-128">描述</span><span class="sxs-lookup"><span data-stu-id="d34af-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d34af-129">\<服務行為行為\<>></span><span class="sxs-lookup"><span data-stu-id="d34af-129">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="d34af-130">指定行為項目。</span><span class="sxs-lookup"><span data-stu-id="d34af-130">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d34af-131">備註</span><span class="sxs-lookup"><span data-stu-id="d34af-131">Remarks</span></span>  
 <span data-ttu-id="d34af-132">這個服務行為適用於將訊息傳送至服務端點的工作流程。</span><span class="sxs-lookup"><span data-stu-id="d34af-132">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="d34af-133">這些工作流程通常是用戶端工作流程，但也可以是裝載於 <xref:System.ServiceModel.WorkflowServiceHost> 中的工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="d34af-133">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="d34af-134">根據預設，在 <xref:System.ServiceModel.WorkflowServiceHost> 所裝載的工作流程中，<xref:System.ServiceModel.Activities.Send> 中的所有工作流程執行個體會共用 <xref:System.ServiceModel.WorkflowServiceHost> 傳訊活動使用的快取 (主機層級快取)。</span><span class="sxs-lookup"><span data-stu-id="d34af-134">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="d34af-135">針對並非由 <xref:System.ServiceModel.WorkflowServiceHost> 裝載的用戶端工作流程，快取只能供工作流程執行個體使用 (執行個體層級快取)。</span><span class="sxs-lookup"><span data-stu-id="d34af-135">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="d34af-136">工作流程中的傳送活動若在組態中定義了端點，快取會依預設停用。</span><span class="sxs-lookup"><span data-stu-id="d34af-136">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="d34af-137">有關如何更改通道工廠和通道緩存的預設緩存共用級別和緩存設置的詳細資訊，請參閱[更改"發送活動"的緩存共用級別](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="d34af-137">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d34af-138">範例</span><span class="sxs-lookup"><span data-stu-id="d34af-138">Example</span></span>  
 <span data-ttu-id="d34af-139">在裝載的工作流程服務中，您可以在應用程式組態檔中，指定處理站快取和通道快取設定。</span><span class="sxs-lookup"><span data-stu-id="d34af-139">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="d34af-140">若要執行這項操作，請加入包含處理站快取設定和通道快取的服務行為，然後將這個服務行為加入您的服務中。</span><span class="sxs-lookup"><span data-stu-id="d34af-140">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="d34af-141">下面的示例顯示包含自訂工廠緩存和通道緩存設置`MyChannelCacheBehavior`的服務行為的設定檔的內容。</span><span class="sxs-lookup"><span data-stu-id="d34af-141">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior`  service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="d34af-142">此服務行為通過 屬性添加到服務中`behaviorConfiguration`。</span><span class="sxs-lookup"><span data-stu-id="d34af-142">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d34af-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d34af-143">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [<span data-ttu-id="d34af-144">變更傳送活動的快取共用層級</span><span class="sxs-lookup"><span data-stu-id="d34af-144">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
