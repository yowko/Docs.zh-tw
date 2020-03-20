---
title: <系統.服務模型>工作流
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: 9aa2bf0fdfd6fe4528a3fda4d05b3ba8f23637d3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151945"
---
# <a name="systemservicemodel-of-workflow"></a><span data-ttu-id="c7cef-102">\<系統.服務模型>工作流</span><span class="sxs-lookup"><span data-stu-id="c7cef-102">\<system.serviceModel> of workflow</span></span>
<span data-ttu-id="c7cef-103">這個組態區段包含所有工作流程組態項目。</span><span class="sxs-lookup"><span data-stu-id="c7cef-103">This configuration section contains all the workflow configuration elements.</span></span>  

<span data-ttu-id="c7cef-104">[**\<配置>**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c7cef-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c7cef-105">&nbsp;&nbsp;**\<系統。服務模式>**</span><span class="sxs-lookup"><span data-stu-id="c7cef-105">&nbsp;&nbsp;**\<system.ServiceModel>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7cef-106">語法</span><span class="sxs-lookup"><span data-stu-id="c7cef-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7cef-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c7cef-107">Attributes and Elements</span></span>  
 <span data-ttu-id="c7cef-108">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c7cef-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7cef-109">屬性</span><span class="sxs-lookup"><span data-stu-id="c7cef-109">Attributes</span></span>  
 <span data-ttu-id="c7cef-110">None</span><span class="sxs-lookup"><span data-stu-id="c7cef-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c7cef-111">子元素</span><span class="sxs-lookup"><span data-stu-id="c7cef-111">Child Elements</span></span>  
  
|<span data-ttu-id="c7cef-112">元素</span><span class="sxs-lookup"><span data-stu-id="c7cef-112">Element</span></span>|<span data-ttu-id="c7cef-113">描述</span><span class="sxs-lookup"><span data-stu-id="c7cef-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c7cef-114">\<行為></span><span class="sxs-lookup"><span data-stu-id="c7cef-114">\<behaviors></span></span>](behaviors-of-workflow.md)|<span data-ttu-id="c7cef-115">本節定義**服務行為**集合。</span><span class="sxs-lookup"><span data-stu-id="c7cef-115">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="c7cef-116">集合中的每個項目都會定義服務使用的行為項目。</span><span class="sxs-lookup"><span data-stu-id="c7cef-116">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="c7cef-117">每個行為元素都由其唯一**的名稱**屬性標識。</span><span class="sxs-lookup"><span data-stu-id="c7cef-117">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[<span data-ttu-id="c7cef-118">\<跟蹤></span><span class="sxs-lookup"><span data-stu-id="c7cef-118">\<tracking></span></span>](tracking.md)|<span data-ttu-id="c7cef-119">代表定義工作流程服務之追蹤設定的組態區段。</span><span class="sxs-lookup"><span data-stu-id="c7cef-119">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="c7cef-120">有關工作流跟蹤及其配置的詳細資訊，請參閱工作流[的工作流跟蹤和跟蹤](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)和[配置跟蹤](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="c7cef-120">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c7cef-121">父項目</span><span class="sxs-lookup"><span data-stu-id="c7cef-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c7cef-122">元素</span><span class="sxs-lookup"><span data-stu-id="c7cef-122">Element</span></span>|<span data-ttu-id="c7cef-123">描述</span><span class="sxs-lookup"><span data-stu-id="c7cef-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c7cef-124">\<配置></span><span class="sxs-lookup"><span data-stu-id="c7cef-124">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="c7cef-125">.NET 組態檔中所有組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="c7cef-125">The root element for all configuration elements in a .NET configuration file.</span></span>|
