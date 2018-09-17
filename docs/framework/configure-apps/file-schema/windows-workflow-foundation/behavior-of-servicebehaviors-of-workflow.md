---
title: 工作流程 &lt;serviceBehaviors&gt; 的 &lt;behavior&gt;
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 9b16aad6138d79d3dbff4994250f05d617d54140
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45749825"
---
# <a name="ltbehaviorgt-of-ltservicebehaviorsgt-of-workflow"></a><span data-ttu-id="63552-102">工作流程 &lt;serviceBehaviors&gt; 的 &lt;behavior&gt;</span><span class="sxs-lookup"><span data-stu-id="63552-102">&lt;behavior&gt; of &lt;serviceBehaviors&gt; of workflow</span></span>
<span data-ttu-id="63552-103">**行為**項目包含服務行為設定的集合。</span><span class="sxs-lookup"><span data-stu-id="63552-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="63552-104">每個行為由編製索引及其**名稱**。</span><span class="sxs-lookup"><span data-stu-id="63552-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="63552-105">服務可連結至每個透過名稱使用的行為**behaviorConfiguration**屬性[\<端點 >](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)項目。</span><span class="sxs-lookup"><span data-stu-id="63552-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="63552-106">如此可允許端點共用通用行為組態，而不用重新定義設定。</span><span class="sxs-lookup"><span data-stu-id="63552-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
<span data-ttu-id="63552-107">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="63552-107">\<system.ServiceModel></span></span>  
<span data-ttu-id="63552-108">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="63552-108">\<behaviors></span></span>  
<span data-ttu-id="63552-109">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="63552-109">\<serviceBehaviors></span></span>  
<span data-ttu-id="63552-110">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="63552-110">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63552-111">語法</span><span class="sxs-lookup"><span data-stu-id="63552-111">Syntax</span></span>  
  
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
                                  honstLockRenewalPeriod="TimeSpan" 
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="63552-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="63552-112">Attributes and Elements</span></span>  
 <span data-ttu-id="63552-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="63552-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="63552-114">屬性</span><span class="sxs-lookup"><span data-stu-id="63552-114">Attributes</span></span>  
  
|<span data-ttu-id="63552-115">屬性</span><span class="sxs-lookup"><span data-stu-id="63552-115">Attribute</span></span>|<span data-ttu-id="63552-116">描述</span><span class="sxs-lookup"><span data-stu-id="63552-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="63552-117">name</span><span class="sxs-lookup"><span data-stu-id="63552-117">name</span></span>|<span data-ttu-id="63552-118">唯一的字串，其中包含行為的組態名稱。</span><span class="sxs-lookup"><span data-stu-id="63552-118">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="63552-119">這個值是使用者定義的字串，它必須是唯一的，因為它會充當項目的識別字串。</span><span class="sxs-lookup"><span data-stu-id="63552-119">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="63552-120">子元素</span><span class="sxs-lookup"><span data-stu-id="63552-120">Child Elements</span></span>  
  
|<span data-ttu-id="63552-121">項目</span><span class="sxs-lookup"><span data-stu-id="63552-121">Element</span></span>|<span data-ttu-id="63552-122">描述</span><span class="sxs-lookup"><span data-stu-id="63552-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63552-123">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="63552-123">\<bufferReceive></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bufferreceive.md)|<span data-ttu-id="63552-124">讓服務可以使用緩衝接收處理的服務行為，該處理可讓工作流程服務處理失序的訊息。</span><span class="sxs-lookup"><span data-stu-id="63552-124">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[<span data-ttu-id="63552-125">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="63552-125">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|<span data-ttu-id="63552-126">這個服務行為可讓服務能夠利用 ETW 追蹤使用<xref:System.Activities.Tracking.EtwTrackingParticipant>。</span><span class="sxs-lookup"><span data-stu-id="63552-126">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[<span data-ttu-id="63552-127">\<sendMessageChannelCache ></span><span class="sxs-lookup"><span data-stu-id="63552-127">\<sendMessageChannelCache></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|<span data-ttu-id="63552-128">服務行為可讓您自訂快取共用層級、 通道處理站快取的設定，以及傳送訊息至服務端點使用傳訊活動傳送的工作流程的通道快取的設定。</span><span class="sxs-lookup"><span data-stu-id="63552-128">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[<span data-ttu-id="63552-129">\<sqlWorkflowInstanceStore ></span><span class="sxs-lookup"><span data-stu-id="63552-129">\<sqlWorkflowInstanceStore></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sqlworkflowinstancestore.md)|<span data-ttu-id="63552-130">可讓您設定的服務行為<xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore>功能，支援的狀態資訊保存在 SQL Server 2005 或 SQL Server 2008 資料庫的工作流程服務執行個體。</span><span class="sxs-lookup"><span data-stu-id="63552-130">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[<span data-ttu-id="63552-131">\<workflowIdle ></span><span class="sxs-lookup"><span data-stu-id="63552-131">\<workflowIdle></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowidle.md)|<span data-ttu-id="63552-132">這個服務行為可控制卸載及保存閒置工作流程執行個體的時間。</span><span class="sxs-lookup"><span data-stu-id="63552-132">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[<span data-ttu-id="63552-133">\<workflowInstanceManagement ></span><span class="sxs-lookup"><span data-stu-id="63552-133">\<workflowInstanceManagement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancemanagement.md)|<span data-ttu-id="63552-134">可讓您指定設定的服務行為，這些設定會控制工作流程執行個體的執行方式，包括持續性、未處理的例外狀況行為和閒置行為。</span><span class="sxs-lookup"><span data-stu-id="63552-134">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[<span data-ttu-id="63552-135">\<workflowUnhandledException ></span><span class="sxs-lookup"><span data-stu-id="63552-135">\<workflowUnhandledException></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowunhandledexception.md)|<span data-ttu-id="63552-136">這個服務行為可讓您指定工作流程服務內發生未處理的例外狀況時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="63552-136">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="63552-137">父項目</span><span class="sxs-lookup"><span data-stu-id="63552-137">Parent Elements</span></span>  
  
|<span data-ttu-id="63552-138">項目</span><span class="sxs-lookup"><span data-stu-id="63552-138">Element</span></span>|<span data-ttu-id="63552-139">描述</span><span class="sxs-lookup"><span data-stu-id="63552-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="63552-140">\<v ></span><span class="sxs-lookup"><span data-stu-id="63552-140">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="63552-141">服務行為項目的集合。</span><span class="sxs-lookup"><span data-stu-id="63552-141">A collection of service behavior elements.</span></span>|
