---
title: 工作流程<behavior> 的 <serviceBehaviors>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 91883c42aa7bc0aa8fa0c63c3c45184ba69225d0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946070"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="407b9-102">\<工作流程\<serviceBehaviors > 的行為 ></span><span class="sxs-lookup"><span data-stu-id="407b9-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>
<span data-ttu-id="407b9-103">**行為**元素包含服務行為的設定集合。</span><span class="sxs-lookup"><span data-stu-id="407b9-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="407b9-104">每個行為都會依其**名稱**編制索引。</span><span class="sxs-lookup"><span data-stu-id="407b9-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="407b9-105">服務可以透過這個名稱連結至每個行為, 其方式是使用[ \<端點 >](../wcf/endpoint-element.md)專案的**behaviorConfiguration**屬性。</span><span class="sxs-lookup"><span data-stu-id="407b9-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="407b9-106">如此可允許端點共用通用行為組態，而不用重新定義設定。</span><span class="sxs-lookup"><span data-stu-id="407b9-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="407b9-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="407b9-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="407b9-108">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="407b9-108">\<behaviors></span></span>  
<span data-ttu-id="407b9-109">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="407b9-109">\<serviceBehaviors></span></span>  
<span data-ttu-id="407b9-110">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="407b9-110">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="407b9-111">語法</span><span class="sxs-lookup"><span data-stu-id="407b9-111">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="String">
        <bufferReceive maxPendingMessagesPerChannel="Integer" />
        <etwTracking profileName="String" />
        <sendMessageChannelCache allowUnsafeCaching="Boolean">
          <channelSettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
          <factorySettings idleTimeout="TimeSpan" 
                           leaseTimeout="TimeSpan" 
                           maxItemsInCache="Integer" />
        </sendMessageChannelCache>
        <sqlWorkflowInstanceStore connectionStringName="String" 
                                  hostLockRenewalPeriod="TimeSpan" 
                                  instanceCompletionAction="DeleteNothing/DeleteAll" 
                                  instanceEncodingAction="None/GZip" 
                                  instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry" 
                                  runnableInstancesDetectionPeriod="TimeSpan" />
        <workflowIdle timeToPersist="TimeSpan" 
                      timeToUnload="TimeSpan" />
        <workflowUnhandledException action="Abandon/AbandonAndSuspend/Cancel/Terminate" />
      </behavior>
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="407b9-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="407b9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="407b9-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="407b9-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="407b9-114">屬性</span><span class="sxs-lookup"><span data-stu-id="407b9-114">Attributes</span></span>  
  
|<span data-ttu-id="407b9-115">屬性</span><span class="sxs-lookup"><span data-stu-id="407b9-115">Attribute</span></span>|<span data-ttu-id="407b9-116">描述</span><span class="sxs-lookup"><span data-stu-id="407b9-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="407b9-117">NAME</span><span class="sxs-lookup"><span data-stu-id="407b9-117">name</span></span>|<span data-ttu-id="407b9-118">唯一的字串，其中包含行為的組態名稱。</span><span class="sxs-lookup"><span data-stu-id="407b9-118">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="407b9-119">這個值是使用者定義的字串，它必須是唯一的，因為它會充當項目的識別字串。</span><span class="sxs-lookup"><span data-stu-id="407b9-119">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="407b9-120">子元素</span><span class="sxs-lookup"><span data-stu-id="407b9-120">Child Elements</span></span>  
  
|<span data-ttu-id="407b9-121">項目</span><span class="sxs-lookup"><span data-stu-id="407b9-121">Element</span></span>|<span data-ttu-id="407b9-122">說明</span><span class="sxs-lookup"><span data-stu-id="407b9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="407b9-123">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="407b9-123">\<bufferReceive></span></span>](bufferreceive.md)|<span data-ttu-id="407b9-124">讓服務可以使用緩衝接收處理的服務行為，該處理可讓工作流程服務處理失序的訊息。</span><span class="sxs-lookup"><span data-stu-id="407b9-124">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="407b9-125">\<routing></span><span class="sxs-lookup"><span data-stu-id="407b9-125">\<routing></span></span>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="407b9-126">一種服務行為, 可讓服務利用來使用<xref:System.Activities.Tracking.EtwTrackingParticipant>ETW 追蹤。</span><span class="sxs-lookup"><span data-stu-id="407b9-126">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="407b9-127">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="407b9-127">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="407b9-128">一種服務行為, 可自訂快取共用層級、通道處理站快取的設定, 以及使用傳送訊息活動傳送訊息至服務端點的工作流程之通道快取的設定。</span><span class="sxs-lookup"><span data-stu-id="407b9-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="407b9-129">\<sqlWorkflowInstanceStore></span><span class="sxs-lookup"><span data-stu-id="407b9-129">\<sqlWorkflowInstanceStore></span></span>](sqlworkflowinstancestore.md)|<span data-ttu-id="407b9-130">可讓您設定<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>功能的服務行為, 其支援將工作流程服務實例的狀態資訊保存到 SQL Server 2005 或 SQL Server 2008 資料庫。</span><span class="sxs-lookup"><span data-stu-id="407b9-130">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="407b9-131">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="407b9-131">\<workflowIdle></span></span>](workflowidle.md)|<span data-ttu-id="407b9-132">這個服務行為可控制卸載及保存閒置工作流程執行個體的時間。</span><span class="sxs-lookup"><span data-stu-id="407b9-132">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="407b9-133">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="407b9-133">\<workflowInstanceManagement></span></span>](workflowinstancemanagement.md)|<span data-ttu-id="407b9-134">可讓您指定設定的服務行為，這些設定會控制工作流程執行個體的執行方式，包括持續性、未處理的例外狀況行為和閒置行為。</span><span class="sxs-lookup"><span data-stu-id="407b9-134">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="407b9-135">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="407b9-135">\<workflowUnhandledException></span></span>](workflowunhandledexception.md)|<span data-ttu-id="407b9-136">這個服務行為可讓您指定工作流程服務內發生未處理的例外狀況時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="407b9-136">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="407b9-137">父項目</span><span class="sxs-lookup"><span data-stu-id="407b9-137">Parent Elements</span></span>  
  
|<span data-ttu-id="407b9-138">項目</span><span class="sxs-lookup"><span data-stu-id="407b9-138">Element</span></span>|<span data-ttu-id="407b9-139">說明</span><span class="sxs-lookup"><span data-stu-id="407b9-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="407b9-140">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="407b9-140">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="407b9-141">服務行為項目的集合。</span><span class="sxs-lookup"><span data-stu-id="407b9-141">A collection of service behavior elements.</span></span>|
