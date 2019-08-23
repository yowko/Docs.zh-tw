---
title: < 的 System.servicemodel > 工作流程
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: faa8154c4d7ac5c6aa2f9f1707cf8f0d39eefad5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947358"
---
# <a name="systemservicemodel-of-workflow"></a><span data-ttu-id="dbe37-102">\<工作流程的 System.servicemodel ></span><span class="sxs-lookup"><span data-stu-id="dbe37-102">\<system.serviceModel> of workflow</span></span>
<span data-ttu-id="dbe37-103">這個組態區段包含所有工作流程組態項目。</span><span class="sxs-lookup"><span data-stu-id="dbe37-103">This configuration section contains all the workflow configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dbe37-104">語法</span><span class="sxs-lookup"><span data-stu-id="dbe37-104">Syntax</span></span>  
  
```xml  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
    <behavior name="String">  
      <bufferReceive maxPendingMessagesPerChannel="Integer" />  
      <etwTracking profileName="String" />  
     <sendMessageChannelCache allowUnsafeCaching="Boolean" >          
        <channelSettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
        <factorySettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
     </sendMessageChannelCache>  
      <sqlWorkflowInstanceStore   
          connectionStringName="String"   
          hostLockRenewalPeriod="TimeSpan"  
          instanceCompletionAction="DeleteNothing/DeleteAll"  
          instanceEncodingAction="None/GZip"  
          instanceLockedExceptionAction="NoRetry/BasicRetry/AggressiveRetry"  
          runnableInstancesDetectionPeriod="TimeSpan" />  
      <workflowIdle timeToPersist="TimeSpan"  
          timeToUnload="TimeSpan" />  
      <workflowUnhandledExceptionAction="Abandon/AbandonAndSuspend/Cancel/Terminate" />  
    </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <tracking>    
     <participants>   
      <add name="String"   
           profileName="String"  
           type="String" />   
     </participants>   
    <trackingProfile name="String">  
      <workflow activityDefinitionId="String">  
          <activityScheduledQueries>  
             <activityScheduledQuery activityName="String"  
                 childActivityName="String"/>  
          </activityScheduledQueries>  
             <activityStateQuery activityName="String" />  
                <arguments>  
                   <argument name="String"/>  
                </arguments>  
                <states>  
                   <state name="String"/>  
                </states>  
                <variables>  
                   <variable name="String"/>  
                </variables>  
          </activityStateQueries>  
          <bookmarkResumptionQueries>  
             <bookmarkResumptionQuery name="String" />  
          </bookmarkResumptionQueries>  
          <cancelRequestQueries>  
             <cancelRequestQuery activityName="String"  
                 childActivityName="String"/>  
          </cancelRequestQueries>  
          <customTrackingQueries>  
             <customTrackingQuery activityName="String"  
                 name="String"/>  
          </customTrackingQueries>  
          <faultPropagationQueries>  
             <faultPropagationQuery activityName="String"  
                 faultHandlerActivityName="String"/>  
          </faultPropagationQueries>  
         <workflowInstanceQueries>  
            <workflowInstanceQuery>  
              <states>  
                 <state name="String"/>  
              </states>  
          </workflowInstanceQuery>  
        </workflowInstanceQueries>  
      </workflow>  
    </trackingProfile>          
   </profiles>  
  </tracking>  
</system.ServiceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dbe37-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dbe37-105">Attributes and Elements</span></span>  
 <span data-ttu-id="dbe37-106">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="dbe37-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dbe37-107">屬性</span><span class="sxs-lookup"><span data-stu-id="dbe37-107">Attributes</span></span>  
 <span data-ttu-id="dbe37-108">None</span><span class="sxs-lookup"><span data-stu-id="dbe37-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="dbe37-109">子元素</span><span class="sxs-lookup"><span data-stu-id="dbe37-109">Child Elements</span></span>  
  
|<span data-ttu-id="dbe37-110">項目</span><span class="sxs-lookup"><span data-stu-id="dbe37-110">Element</span></span>|<span data-ttu-id="dbe37-111">說明</span><span class="sxs-lookup"><span data-stu-id="dbe37-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dbe37-112">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="dbe37-112">\<behaviors></span></span>](behaviors-of-workflow.md)|<span data-ttu-id="dbe37-113">這個區段會定義**serviceBehaviors**集合。</span><span class="sxs-lookup"><span data-stu-id="dbe37-113">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="dbe37-114">集合中的每個項目都會定義服務使用的行為項目。</span><span class="sxs-lookup"><span data-stu-id="dbe37-114">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="dbe37-115">每個行為元素都是由其唯一的**名稱**屬性來識別。</span><span class="sxs-lookup"><span data-stu-id="dbe37-115">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[<span data-ttu-id="dbe37-116">\<tracking></span><span class="sxs-lookup"><span data-stu-id="dbe37-116">\<tracking></span></span>](tracking.md)|<span data-ttu-id="dbe37-117">代表定義工作流程服務之追蹤設定的組態區段。</span><span class="sxs-lookup"><span data-stu-id="dbe37-117">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="dbe37-118">如需工作流程追蹤及其設定的詳細資訊, 請參閱工作流程[追蹤和](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)追蹤和設定[工作流程的追蹤](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="dbe37-118">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dbe37-119">父項目</span><span class="sxs-lookup"><span data-stu-id="dbe37-119">Parent Elements</span></span>  
  
|<span data-ttu-id="dbe37-120">項目</span><span class="sxs-lookup"><span data-stu-id="dbe37-120">Element</span></span>|<span data-ttu-id="dbe37-121">描述</span><span class="sxs-lookup"><span data-stu-id="dbe37-121">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dbe37-122">\<configuration></span><span class="sxs-lookup"><span data-stu-id="dbe37-122">\<configuration></span></span>|<span data-ttu-id="dbe37-123">.NET 組態檔中所有組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="dbe37-123">The root element for all configuration elements in a .NET configuration file.</span></span>|
