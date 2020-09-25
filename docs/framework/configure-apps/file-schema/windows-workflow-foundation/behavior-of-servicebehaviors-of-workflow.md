---
title: 工作流程<behavior> 的 <serviceBehaviors>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 14c528746963a3078e0ab377d095414d2fca0dbe
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189613"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a><span data-ttu-id="5e7cc-102">工作流程\<behavior> 的 \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="5e7cc-102">\<behavior> of \<serviceBehaviors> of workflow</span></span>

<span data-ttu-id="5e7cc-103">**行為**元素包含服務行為的設定集合。</span><span class="sxs-lookup"><span data-stu-id="5e7cc-103">The **behavior** element contains a collection of settings for the behavior of a service.</span></span> <span data-ttu-id="5e7cc-104">每個行為都會依其 **名稱**來編制索引。</span><span class="sxs-lookup"><span data-stu-id="5e7cc-104">Each behavior is indexed by its **name**.</span></span> <span data-ttu-id="5e7cc-105">服務可以使用專案的 **behaviorConfiguration** 屬性，透過這個名稱連結到每個行為 [\<endpoint>](../wcf/endpoint-element.md) 。</span><span class="sxs-lookup"><span data-stu-id="5e7cc-105">Services can link to each behavior through this name using the **behaviorConfiguration** attribute of the [\<endpoint>](../wcf/endpoint-element.md) element.</span></span> <span data-ttu-id="5e7cc-106">如此可允許端點共用通用行為組態，而不用重新定義設定。</span><span class="sxs-lookup"><span data-stu-id="5e7cc-106">This allows endpoints to share common behavior configurations without redefining the settings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="5e7cc-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="5e7cc-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5e7cc-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5e7cc-108">Attributes and Elements</span></span>  

 <span data-ttu-id="5e7cc-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="5e7cc-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5e7cc-110">屬性</span><span class="sxs-lookup"><span data-stu-id="5e7cc-110">Attributes</span></span>  
  
|<span data-ttu-id="5e7cc-111">屬性</span><span class="sxs-lookup"><span data-stu-id="5e7cc-111">Attribute</span></span>|<span data-ttu-id="5e7cc-112">描述</span><span class="sxs-lookup"><span data-stu-id="5e7cc-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5e7cc-113">NAME</span><span class="sxs-lookup"><span data-stu-id="5e7cc-113">name</span></span>|<span data-ttu-id="5e7cc-114">唯一的字串，其中包含行為的組態名稱。</span><span class="sxs-lookup"><span data-stu-id="5e7cc-114">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="5e7cc-115">這個值是使用者定義的字串，它必須是唯一的，因為它會充當項目的識別字串。</span><span class="sxs-lookup"><span data-stu-id="5e7cc-115">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5e7cc-116">子元素</span><span class="sxs-lookup"><span data-stu-id="5e7cc-116">Child Elements</span></span>  
  
|<span data-ttu-id="5e7cc-117">項目</span><span class="sxs-lookup"><span data-stu-id="5e7cc-117">Element</span></span>|<span data-ttu-id="5e7cc-118">描述</span><span class="sxs-lookup"><span data-stu-id="5e7cc-118">Description</span></span>|  
|-------------|-----------------|  
|[\<bufferReceive>](bufferreceive.md)|<span data-ttu-id="5e7cc-119">讓服務可以使用緩衝接收處理的服務行為，該處理可讓工作流程服務處理失序的訊息。</span><span class="sxs-lookup"><span data-stu-id="5e7cc-119">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>|  
|[\<routing>](../wcf/routing-of-servicebehavior.md)|<span data-ttu-id="5e7cc-120">服務行為，可讓服務透過使用 <xref:System.Activities.Tracking.EtwTrackingParticipant> 來利用 ETW 追蹤。</span><span class="sxs-lookup"><span data-stu-id="5e7cc-120">A service behavior that allows a service to utilize ETW tracking using an <xref:System.Activities.Tracking.EtwTrackingParticipant>.</span></span>|  
|[\<sendMessageChannelCache>](sendmessagechannelcache.md)|<span data-ttu-id="5e7cc-121">這個服務行為可讓您自訂快取共用層級、通道處理站快取的設定，以及工作流程使用傳送訊息活動來傳送訊息至服務端點的通道快取設定。</span><span class="sxs-lookup"><span data-stu-id="5e7cc-121">A service behavior that enables the customization of the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using Send messaging activities.</span></span>|  
|[\<sqlWorkflowInstanceStore>](sqlworkflowinstancestore.md)|<span data-ttu-id="5e7cc-122">可讓您設定 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 功能的服務行為，該功能支援將工作流程服務執行個體的狀態資訊保存在 SQL Server 2005 或 SQL Server 2008 資料庫中。</span><span class="sxs-lookup"><span data-stu-id="5e7cc-122">A service behavior that allows you to configure the <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> feature, which supports persisting state information for workflow service instances into an SQL Server 2005 or SQL Server 2008 database.</span></span>|  
|[\<workflowIdle>](workflowidle.md)|<span data-ttu-id="5e7cc-123">這個服務行為可控制卸載及保存閒置工作流程執行個體的時間。</span><span class="sxs-lookup"><span data-stu-id="5e7cc-123">A service behavior that controls when idle workflow instances are unloaded and persisted.</span></span>|  
|[\<workflowInstanceManagement>](workflowinstancemanagement.md)|<span data-ttu-id="5e7cc-124">可讓您指定設定的服務行為，這些設定會控制工作流程執行個體的執行方式，包括持續性、未處理的例外狀況行為和閒置行為。</span><span class="sxs-lookup"><span data-stu-id="5e7cc-124">A service behavior that enables you to specify settings that control how workflow instances are run, including persistence, unhandled Exception behavior and idle behavior.</span></span>|  
|[\<workflowUnhandledException>](workflowunhandledexception.md)|<span data-ttu-id="5e7cc-125">這個服務行為可讓您指定工作流程服務內發生未處理的例外狀況時要採取的動作。</span><span class="sxs-lookup"><span data-stu-id="5e7cc-125">A service behavior that enables you to specify the action to take when an unhandled exception occurs within a workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5e7cc-126">父項目</span><span class="sxs-lookup"><span data-stu-id="5e7cc-126">Parent Elements</span></span>  
  
|<span data-ttu-id="5e7cc-127">項目</span><span class="sxs-lookup"><span data-stu-id="5e7cc-127">Element</span></span>|<span data-ttu-id="5e7cc-128">描述</span><span class="sxs-lookup"><span data-stu-id="5e7cc-128">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|<span data-ttu-id="5e7cc-129">服務行為項目的集合。</span><span class="sxs-lookup"><span data-stu-id="5e7cc-129">A collection of service behavior elements.</span></span>|
