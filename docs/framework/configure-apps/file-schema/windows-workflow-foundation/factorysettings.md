---
title: <factorySettings>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 202aad17-1b8b-4c87-ad57-4ca5de18ed35
ms.openlocfilehash: afb129407bc9dff752375f6e9fd69c728a809b37
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152180"
---
# \<factorySettings>
<span data-ttu-id="73313-101">指定通道處理站快取的設定。</span><span class="sxs-lookup"><span data-stu-id="73313-101">Specifies the settings of the channel factory cache.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<sendMessageChannelCache>**](sendmessagechannelcache.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<factorySettings>**  
  
## <a name="syntax"></a><span data-ttu-id="73313-102">語法</span><span class="sxs-lookup"><span data-stu-id="73313-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="73313-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="73313-103">Attributes and Elements</span></span>  
 <span data-ttu-id="73313-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="73313-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="73313-105">屬性</span><span class="sxs-lookup"><span data-stu-id="73313-105">Attributes</span></span>  
  
|<span data-ttu-id="73313-106">屬性</span><span class="sxs-lookup"><span data-stu-id="73313-106">Attribute</span></span>|<span data-ttu-id="73313-107">描述</span><span class="sxs-lookup"><span data-stu-id="73313-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="73313-108">idleTimeout</span><span class="sxs-lookup"><span data-stu-id="73313-108">idleTimeout</span></span>|<span data-ttu-id="73313-109">TimeSpan 值，可指定物件處置前可在快取中維持閒置的最長時間間隔。</span><span class="sxs-lookup"><span data-stu-id="73313-109">A TimeSpan value that specifies the maximum interval of time for which the object can remain idle in the cache before being disposed.</span></span>|  
|<span data-ttu-id="73313-110">leaseTimeout</span><span class="sxs-lookup"><span data-stu-id="73313-110">leaseTimeout</span></span>|<span data-ttu-id="73313-111">TimeSpan 值，可指定物件自快取移除後的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="73313-111">A TimeSpan value that specifies  the interval of time after which an object is removed from the cache.</span></span>|  
|<span data-ttu-id="73313-112">maxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="73313-112">maxItemsInCache</span></span>|<span data-ttu-id="73313-113">整數，可指定快取中可容納的最大物件數量。</span><span class="sxs-lookup"><span data-stu-id="73313-113">An integer that specifies the maximum number of objects that can be in the cache.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="73313-114">子元素</span><span class="sxs-lookup"><span data-stu-id="73313-114">Child Elements</span></span>  
 <span data-ttu-id="73313-115">無。</span><span class="sxs-lookup"><span data-stu-id="73313-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="73313-116">父項目</span><span class="sxs-lookup"><span data-stu-id="73313-116">Parent Elements</span></span>  
  
|<span data-ttu-id="73313-117">元素</span><span class="sxs-lookup"><span data-stu-id="73313-117">Element</span></span>|<span data-ttu-id="73313-118">描述</span><span class="sxs-lookup"><span data-stu-id="73313-118">Description</span></span>|  
|-------------|-----------------|  
|[\<sendMessageChannelCache>](sendmessagechannelcache.md)|<span data-ttu-id="73313-119">這個服務行為可讓您自訂快取共用層級、通道處理站快取的設定，以及工作流程使用傳送訊息活動來傳送訊息至服務端點的通道快取設定。</span><span class="sxs-lookup"><span data-stu-id="73313-119">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73313-120">備註</span><span class="sxs-lookup"><span data-stu-id="73313-120">Remarks</span></span>  
 <span data-ttu-id="73313-121">這個服務行為適用於將訊息傳送至服務端點的工作流程。</span><span class="sxs-lookup"><span data-stu-id="73313-121">This service behavior is intended for workflows that send messages to service endpoints.</span></span> <span data-ttu-id="73313-122">這些工作流程通常是用戶端工作流程，但也可以是裝載於 <xref:System.ServiceModel.WorkflowServiceHost> 中的工作流程服務。</span><span class="sxs-lookup"><span data-stu-id="73313-122">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span>  
  
 <span data-ttu-id="73313-123">根據預設，在 <xref:System.ServiceModel.WorkflowServiceHost> 所裝載的工作流程中，<xref:System.ServiceModel.Activities.Send> 中的所有工作流程執行個體會共用 <xref:System.ServiceModel.WorkflowServiceHost> 傳訊活動使用的快取 (主機層級快取)。</span><span class="sxs-lookup"><span data-stu-id="73313-123">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="73313-124">針對並非由 <xref:System.ServiceModel.WorkflowServiceHost> 裝載的用戶端工作流程，快取只能供工作流程執行個體使用 (執行個體層級快取)。</span><span class="sxs-lookup"><span data-stu-id="73313-124">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="73313-125">工作流程中的傳送活動若在組態中定義了端點，快取會依預設停用。</span><span class="sxs-lookup"><span data-stu-id="73313-125">Caching is disabled by default for any send activity in your workflow that has endpoints defined in configuration.</span></span>  
  
 <span data-ttu-id="73313-126">如需如何變更通道處理站和通道快取的預設快取共用層級和快取設定的詳細資訊，請參閱[變更傳送活動的快取共用層級](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)。</span><span class="sxs-lookup"><span data-stu-id="73313-126">For more information about how to change the default cache sharing levels and cache settings for the channel factory and channel cache, see [Changing the Cache Sharing Levels for Send Activities](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="73313-127">範例</span><span class="sxs-lookup"><span data-stu-id="73313-127">Example</span></span>  
 <span data-ttu-id="73313-128">在裝載的工作流程服務中，您可以在應用程式組態檔中，指定處理站快取和通道快取設定。</span><span class="sxs-lookup"><span data-stu-id="73313-128">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="73313-129">若要執行這項操作，請加入包含處理站快取設定和通道快取的服務行為，然後將這個服務行為加入您的服務中。</span><span class="sxs-lookup"><span data-stu-id="73313-129">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="73313-130">下列範例會顯示設定檔案的內容，其中包含 `MyChannelCacheBehavior` 具有自訂處理站快取和通道快取設定的服務行為。</span><span class="sxs-lookup"><span data-stu-id="73313-130">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="73313-131">此服務行為會透過屬性加入至服務 `behaviorConfiguration` 。</span><span class="sxs-lookup"><span data-stu-id="73313-131">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="73313-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="73313-132">See also</span></span>

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- <xref:System.ServiceModel.Activities.ChannelCacheSettings>
- [<span data-ttu-id="73313-133">變更傳送活動的快取共用層級</span><span class="sxs-lookup"><span data-stu-id="73313-133">Changing the Cache Sharing Levels for Send Activities</span></span>](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
