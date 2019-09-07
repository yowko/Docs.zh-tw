---
title: 工作流程<behavior> 的 <serviceBehaviors>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 65bde45ffdd4af166d5b44308162c23257659802
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398883"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="f0737-102">\<工作流程\<serviceBehaviors > 的行為 ></span><span class="sxs-lookup"><span data-stu-id="f0737-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>
<span data-ttu-id="f0737-103">**行為**元素包含服務行為的設定集合。</span><span class="sxs-lookup"><span data-stu-id="f0737-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="f0737-104">每個行為都會依其**名稱**編制索引。</span><span class="sxs-lookup"><span data-stu-id="f0737-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="f0737-105">服務可以透過這個名稱連結至每個行為，其方式是使用[ \<端點 >](../wcf/endpoint-element.md)專案的**behaviorConfiguration**屬性。</span><span class="sxs-lookup"><span data-stu-id="f0737-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="f0737-106">如此可允許端點共用通用行為組態，而不用重新定義設定。</span><span class="sxs-lookup"><span data-stu-id="f0737-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="f0737-107">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f0737-107">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f0737-108">&nbsp;&nbsp;[ **\<筆記本電腦.System.servicemodel >** ](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f0737-108">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="f0737-109">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f0737-109">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)</span></span>\
<span data-ttu-id="f0737-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="f0737-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)</span></span>\
<span data-ttu-id="f0737-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<行為 >**</span><span class="sxs-lookup"><span data-stu-id="f0737-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0737-112">語法</span><span class="sxs-lookup"><span data-stu-id="f0737-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0737-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f0737-113">Attributes and Elements</span></span>  
 <span data-ttu-id="f0737-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f0737-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0737-115">屬性</span><span class="sxs-lookup"><span data-stu-id="f0737-115">Attributes</span></span>  
  
|<span data-ttu-id="f0737-116">屬性</span><span class="sxs-lookup"><span data-stu-id="f0737-116">Attribute</span></span>|<span data-ttu-id="f0737-117">描述</span><span class="sxs-lookup"><span data-stu-id="f0737-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f0737-118">NAME</span><span class="sxs-lookup"><span data-stu-id="f0737-118">name</span></span>|<span data-ttu-id="f0737-119">唯一的字串，其中包含行為的組態名稱。</span><span class="sxs-lookup"><span data-stu-id="f0737-119">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="f0737-120">這個值是使用者定義的字串，它必須是唯一的，因為它會充當項目的識別字串。</span><span class="sxs-lookup"><span data-stu-id="f0737-120">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0737-121">子元素</span><span class="sxs-lookup"><span data-stu-id="f0737-121">Child Elements</span></span>  
  
|<span data-ttu-id="f0737-122">項目</span><span class="sxs-lookup"><span data-stu-id="f0737-122">Element</span></span>|<span data-ttu-id="f0737-123">說明</span><span class="sxs-lookup"><span data-stu-id="f0737-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0737-124">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="f0737-124">\<bufferReceive></span></span>](bufferreceive.md)|<span data-ttu-id="f0737-125">讓服務可以使用緩衝接收處理的服務行為，該處理可讓工作流程服務處理失序的訊息。</span><span class="sxs-lookup"><span data-stu-id="f0737-125">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="f0737-126">\<routing></span><span class="sxs-lookup"><span data-stu-id="f0737-126">\<routing></span></span>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="f0737-127">一種服務行為，可讓服務利用來使用<xref:System.Activities.Tracking.EtwTrackingParticipant>ETW 追蹤。</span><span class="sxs-lookup"><span data-stu-id="f0737-127">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="f0737-128">\<sendMessageChannelCache></span><span class="sxs-lookup"><span data-stu-id="f0737-128">\<sendMessageChannelCache></span></span>](sendmessagechannelcache.md)|<span data-ttu-id="f0737-129">一種服務行為，可自訂快取共用層級、通道處理站快取的設定，以及使用傳送訊息活動傳送訊息至服務端點的工作流程之通道快取的設定。</span><span class="sxs-lookup"><span data-stu-id="f0737-129">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="f0737-130">\<sqlWorkflowInstanceStore></span><span class="sxs-lookup"><span data-stu-id="f0737-130">\<sqlWorkflowInstanceStore></span></span>](sqlworkflowinstancestore.md)|<span data-ttu-id="f0737-131">可讓您設定<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>功能的服務行為，其支援將工作流程服務實例的狀態資訊保存到 SQL Server 2005 或 SQL Server 2008 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f0737-131">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="f0737-132">\<workflowIdle></span><span class="sxs-lookup"><span data-stu-id="f0737-132">\<workflowIdle></span></span>](workflowidle.md)|<span data-ttu-id="f0737-133">這個服務行為可控制卸載及保存閒置工作流程執行個體的時間。</span><span class="sxs-lookup"><span data-stu-id="f0737-133">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="f0737-134">\<workflowInstanceManagement></span><span class="sxs-lookup"><span data-stu-id="f0737-134">\<workflowInstanceManagement></span></span>](workflowinstancemanagement.md)|<span data-ttu-id="f0737-135">可讓您指定設定的服務行為，這些設定會控制工作流程執行個體的執行方式，包括持續性、未處理的例外狀況行為和閒置行為。</span><span class="sxs-lookup"><span data-stu-id="f0737-135">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="f0737-136">\<workflowUnhandledException></span><span class="sxs-lookup"><span data-stu-id="f0737-136">\<workflowUnhandledException></span></span>](workflowunhandledexception.md)|<span data-ttu-id="f0737-137">這個服務行為可讓您指定工作流程服務內發生未處理的例外狀況時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="f0737-137">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f0737-138">父項目</span><span class="sxs-lookup"><span data-stu-id="f0737-138">Parent Elements</span></span>  
  
|<span data-ttu-id="f0737-139">項目</span><span class="sxs-lookup"><span data-stu-id="f0737-139">Element</span></span>|<span data-ttu-id="f0737-140">描述</span><span class="sxs-lookup"><span data-stu-id="f0737-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0737-141">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="f0737-141">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="f0737-142">服務行為項目的集合。</span><span class="sxs-lookup"><span data-stu-id="f0737-142">A collection of service behavior elements.</span></span>|
