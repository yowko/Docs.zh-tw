---
title: < 的 System.servicemodel > 工作流程
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: 757a7a132a6e765e257097d251a110297c6a40bf
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398605"
---
# <a name="systemservicemodel-of-workflow"></a><span data-ttu-id="0087e-102">\<工作流程的 System.servicemodel ></span><span class="sxs-lookup"><span data-stu-id="0087e-102">\<system.serviceModel> of workflow</span></span>
<span data-ttu-id="0087e-103">這個組態區段包含所有工作流程組態項目。</span><span class="sxs-lookup"><span data-stu-id="0087e-103">This configuration section contains all the workflow configuration elements.</span></span>  

<span data-ttu-id="0087e-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="0087e-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="0087e-105">&nbsp;&nbsp; **\<筆記本電腦.System.servicemodel >**</span><span class="sxs-lookup"><span data-stu-id="0087e-105">&nbsp;&nbsp;**\<system.ServiceModel>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0087e-106">語法</span><span class="sxs-lookup"><span data-stu-id="0087e-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0087e-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0087e-107">Attributes and Elements</span></span>  
 <span data-ttu-id="0087e-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0087e-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0087e-109">屬性</span><span class="sxs-lookup"><span data-stu-id="0087e-109">Attributes</span></span>  
 <span data-ttu-id="0087e-110">無</span><span class="sxs-lookup"><span data-stu-id="0087e-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0087e-111">子元素</span><span class="sxs-lookup"><span data-stu-id="0087e-111">Child Elements</span></span>  
  
|<span data-ttu-id="0087e-112">項目</span><span class="sxs-lookup"><span data-stu-id="0087e-112">Element</span></span>|<span data-ttu-id="0087e-113">說明</span><span class="sxs-lookup"><span data-stu-id="0087e-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0087e-114">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="0087e-114">\<behaviors></span></span>](behaviors-of-workflow.md)|<span data-ttu-id="0087e-115">這個區段會定義**serviceBehaviors**集合。</span><span class="sxs-lookup"><span data-stu-id="0087e-115">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="0087e-116">集合中的每個項目都會定義服務使用的行為項目。</span><span class="sxs-lookup"><span data-stu-id="0087e-116">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="0087e-117">每個行為元素都是由其唯一的**名稱**屬性來識別。</span><span class="sxs-lookup"><span data-stu-id="0087e-117">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[<span data-ttu-id="0087e-118">\<tracking></span><span class="sxs-lookup"><span data-stu-id="0087e-118">\<tracking></span></span>](tracking.md)|<span data-ttu-id="0087e-119">代表定義工作流程服務之追蹤設定的組態區段。</span><span class="sxs-lookup"><span data-stu-id="0087e-119">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="0087e-120">如需工作流程追蹤及其設定的詳細資訊，請參閱工作流程[追蹤和](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md)追蹤和設定[工作流程的追蹤](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="0087e-120">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0087e-121">父項目</span><span class="sxs-lookup"><span data-stu-id="0087e-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0087e-122">項目</span><span class="sxs-lookup"><span data-stu-id="0087e-122">Element</span></span>|<span data-ttu-id="0087e-123">說明</span><span class="sxs-lookup"><span data-stu-id="0087e-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0087e-124">\<configuration></span><span class="sxs-lookup"><span data-stu-id="0087e-124">\<configuration></span></span>](../configuration-element.md)|<span data-ttu-id="0087e-125">.NET 組態檔中所有組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="0087e-125">The root element for all configuration elements in a .NET configuration file.</span></span>|
