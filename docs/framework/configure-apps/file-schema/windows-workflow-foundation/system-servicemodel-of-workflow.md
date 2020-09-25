---
title: <System.servicemodel> 的工作流程
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a8eb2bf-f925-40e1-ba5c-a49b1d3a3ac6
ms.openlocfilehash: c18cc4886d3e7a19b750a005b27d00a841b9fc5d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194852"
---
# <a name="systemservicemodel-of-workflow"></a><span data-ttu-id="557f8-102">工作流程的 \<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="557f8-102">\<system.serviceModel> of workflow</span></span>

<span data-ttu-id="557f8-103">這個組態區段包含所有工作流程組態項目。</span><span class="sxs-lookup"><span data-stu-id="557f8-103">This configuration section contains all the workflow configuration elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.ServiceModel>**  
  
## <a name="syntax"></a><span data-ttu-id="557f8-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="557f8-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="557f8-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="557f8-105">Attributes and Elements</span></span>  

 <span data-ttu-id="557f8-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="557f8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="557f8-107">屬性</span><span class="sxs-lookup"><span data-stu-id="557f8-107">Attributes</span></span>  

 <span data-ttu-id="557f8-108">無</span><span class="sxs-lookup"><span data-stu-id="557f8-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="557f8-109">子元素</span><span class="sxs-lookup"><span data-stu-id="557f8-109">Child Elements</span></span>  
  
|<span data-ttu-id="557f8-110">項目</span><span class="sxs-lookup"><span data-stu-id="557f8-110">Element</span></span>|<span data-ttu-id="557f8-111">描述</span><span class="sxs-lookup"><span data-stu-id="557f8-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviors>](behaviors-of-workflow.md)|<span data-ttu-id="557f8-112">此區段會定義 **>servicebehaviors>** 集合。</span><span class="sxs-lookup"><span data-stu-id="557f8-112">This section defines the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="557f8-113">集合中的每個項目都會定義服務使用的行為項目。</span><span class="sxs-lookup"><span data-stu-id="557f8-113">Each element in the collection defines behavior elements consumed by services.</span></span> <span data-ttu-id="557f8-114">每個行為元素都是由其唯一 **名稱** 屬性來識別。</span><span class="sxs-lookup"><span data-stu-id="557f8-114">Each behavior element is identified by its unique **name** attribute.</span></span>|  
|[\<tracking>](tracking.md)|<span data-ttu-id="557f8-115">代表定義工作流程服務之追蹤設定的組態區段。</span><span class="sxs-lookup"><span data-stu-id="557f8-115">Represents a configuration section for defining tracking settings for a workflow service.</span></span><br /><br /> <span data-ttu-id="557f8-116">如需工作流程追蹤及其設定的詳細資訊，請參閱工作流程 [追蹤和追蹤](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) 和設定 [工作流程的追蹤](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md)。</span><span class="sxs-lookup"><span data-stu-id="557f8-116">For more information in workflow tracking and its configuration, see [Workflow Tracking and Tracing](../../../windows-workflow-foundation/workflow-tracking-and-tracing.md) and [Configuring Tracking for a Workflow](../../../windows-workflow-foundation/configuring-tracking-for-a-workflow.md).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="557f8-117">父項目</span><span class="sxs-lookup"><span data-stu-id="557f8-117">Parent Elements</span></span>  
  
|<span data-ttu-id="557f8-118">項目</span><span class="sxs-lookup"><span data-stu-id="557f8-118">Element</span></span>|<span data-ttu-id="557f8-119">描述</span><span class="sxs-lookup"><span data-stu-id="557f8-119">Description</span></span>|  
|-------------|-----------------|  
|[\<configuration>](../configuration-element.md)|<span data-ttu-id="557f8-120">.NET 組態檔中所有組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="557f8-120">The root element for all configuration elements in a .NET configuration file.</span></span>|
