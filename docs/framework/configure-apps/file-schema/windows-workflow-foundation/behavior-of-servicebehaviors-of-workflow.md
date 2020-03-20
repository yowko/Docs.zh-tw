---
title: 工作流程<behavior> 的 <serviceBehaviors>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 071cff8e9f6ec3fa0546a07d19160869d8b43f60
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152316"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="c1314-102">\<\<服務行為>>工作流</span><span class="sxs-lookup"><span data-stu-id="c1314-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>
<span data-ttu-id="c1314-103">**行為**元素包含服務行為的設置集合。</span><span class="sxs-lookup"><span data-stu-id="c1314-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="c1314-104">每個行為都按其**名稱**編制索引。</span><span class="sxs-lookup"><span data-stu-id="c1314-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="c1314-105">服務可以使用[\<終結點>](../wcf/endpoint-element.md)元素**的行為配置**屬性通過此名稱連結到每個行為。</span><span class="sxs-lookup"><span data-stu-id="c1314-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="c1314-106">如此可允許端點共用通用行為組態，而不用重新定義設定。</span><span class="sxs-lookup"><span data-stu-id="c1314-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="c1314-107">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c1314-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c1314-108">&nbsp;&nbsp;[**\<系統。服務模式>**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="c1314-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="c1314-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<行為>**](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="c1314-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="c1314-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<服務行為>**](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="c1314-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="c1314-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<行為>**</span><span class="sxs-lookup"><span data-stu-id="c1314-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1314-112">語法</span><span class="sxs-lookup"><span data-stu-id="c1314-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1314-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c1314-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c1314-114">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c1314-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1314-115">屬性</span><span class="sxs-lookup"><span data-stu-id="c1314-115">Attributes</span></span>  
  
|<span data-ttu-id="c1314-116">屬性</span><span class="sxs-lookup"><span data-stu-id="c1314-116">Attribute</span></span>|<span data-ttu-id="c1314-117">描述</span><span class="sxs-lookup"><span data-stu-id="c1314-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c1314-118">NAME</span><span class="sxs-lookup"><span data-stu-id="c1314-118">name</span></span>|<span data-ttu-id="c1314-119">唯一的字串，其中包含行為的組態名稱。</span><span class="sxs-lookup"><span data-stu-id="c1314-119">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="c1314-120">這個值是使用者定義的字串，它必須是唯一的，因為它會充當項目的識別字串。</span><span class="sxs-lookup"><span data-stu-id="c1314-120">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1314-121">子元素</span><span class="sxs-lookup"><span data-stu-id="c1314-121">Child Elements</span></span>  
  
|<span data-ttu-id="c1314-122">元素</span><span class="sxs-lookup"><span data-stu-id="c1314-122">Element</span></span>|<span data-ttu-id="c1314-123">描述</span><span class="sxs-lookup"><span data-stu-id="c1314-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1314-124">\<緩衝區接收></span><span class="sxs-lookup"><span data-stu-id="c1314-124">\<bufferReceive></span></span>](bufferreceive.md)|<span data-ttu-id="c1314-125">讓服務可以使用緩衝接收處理的服務行為，該處理可讓工作流程服務處理失序的訊息。</span><span class="sxs-lookup"><span data-stu-id="c1314-125">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="c1314-126">\<路由></span><span class="sxs-lookup"><span data-stu-id="c1314-126">\<routing></span></span>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="c1314-127">服務行為，可讓服務透過使用 <xref:System.Activities.Tracking.EtwTrackingParticipant> 來利用 ETW 追蹤。</span><span class="sxs-lookup"><span data-stu-id="c1314-127">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="c1314-128">\<發送消息通道緩存></span><span class="sxs-lookup"><span data-stu-id="c1314-128">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="c1314-129">這個服務行為可讓您自訂快取共用層級、通道處理站快取的設定，以及工作流程使用傳送訊息活動來傳送訊息至服務端點的通道快取設定。</span><span class="sxs-lookup"><span data-stu-id="c1314-129">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="c1314-130">\<sqlWorkflow 實例存儲></span><span class="sxs-lookup"><span data-stu-id="c1314-130">\<sqlWorkflowInstanceStore></span></span>](sqlworkflowinstancestore.md)|<span data-ttu-id="c1314-131">可讓您設定 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 功能的服務行為，該功能支援將工作流程服務執行個體的狀態資訊保存在 SQL Server 2005 或 SQL Server 2008 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="c1314-131">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="c1314-132">\<工作流 空閒></span><span class="sxs-lookup"><span data-stu-id="c1314-132">\<workflowIdle></span></span>](workflowidle.md)|<span data-ttu-id="c1314-133">這個服務行為可控制卸載及保存閒置工作流程執行個體的時間。</span><span class="sxs-lookup"><span data-stu-id="c1314-133">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="c1314-134">\<工作流實例管理></span><span class="sxs-lookup"><span data-stu-id="c1314-134">\<workflowInstanceManagement></span></span>](workflowinstancemanagement.md)|<span data-ttu-id="c1314-135">可讓您指定設定的服務行為，這些設定會控制工作流程執行個體的執行方式，包括持續性、未處理的例外狀況行為和閒置行為。</span><span class="sxs-lookup"><span data-stu-id="c1314-135">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="c1314-136">\<工作流未處理異常></span><span class="sxs-lookup"><span data-stu-id="c1314-136">\<workflowUnhandledException></span></span>](workflowunhandledexception.md)|<span data-ttu-id="c1314-137">這個服務行為可讓您指定工作流程服務內發生未處理的例外狀況時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="c1314-137">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c1314-138">父項目</span><span class="sxs-lookup"><span data-stu-id="c1314-138">Parent Elements</span></span>  
  
|<span data-ttu-id="c1314-139">元素</span><span class="sxs-lookup"><span data-stu-id="c1314-139">Element</span></span>|<span data-ttu-id="c1314-140">描述</span><span class="sxs-lookup"><span data-stu-id="c1314-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1314-141">\<服務行為></span><span class="sxs-lookup"><span data-stu-id="c1314-141">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="c1314-142">服務行為項目的集合。</span><span class="sxs-lookup"><span data-stu-id="c1314-142">A collection of service behavior elements.</span></span>|
