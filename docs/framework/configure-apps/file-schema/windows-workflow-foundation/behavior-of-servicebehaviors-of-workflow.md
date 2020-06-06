---
title: 工作流程<behavior> 的 <serviceBehaviors>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
ms.openlocfilehash: 071cff8e9f6ec3fa0546a07d19160869d8b43f60
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152316"
---
# <a name="behavior-of-servicebehaviors-of-workflow"></a>工作流程\<behavior> 的 \<serviceBehaviors>
**行為**元素包含服務行為的設定集合。 每個行為都會依其**名稱**編制索引。 服務可以使用元素的**behaviorConfiguration**屬性，透過這個名稱連結至每個行為 [\<endpoint>](../wcf/endpoint-element.md) 。 如此可允許端點共用通用行為組態，而不用重新定義設定。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a>語法  
  
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
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|NAME|唯一的字串，其中包含行為的組態名稱。 這個值是使用者定義的字串，它必須是唯一的，因為它會充當項目的識別字串。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<bufferReceive>](bufferreceive.md)|讓服務可以使用緩衝接收處理的服務行為，該處理可讓工作流程服務處理失序的訊息。|  
|[\<routing>](../wcf/routing-of-servicebehavior.md)|服務行為，可讓服務透過使用 <xref:System.Activities.Tracking.EtwTrackingParticipant> 來利用 ETW 追蹤。|  
|[\<sendMessageChannelCache>](sendmessagechannelcache.md)|這個服務行為可讓您自訂快取共用層級、通道處理站快取的設定，以及工作流程使用傳送訊息活動來傳送訊息至服務端點的通道快取設定。|  
|[\<sqlWorkflowInstanceStore>](sqlworkflowinstancestore.md)|可讓您設定 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 功能的服務行為，該功能支援將工作流程服務執行個體的狀態資訊保存在 SQL Server 2005 或 SQL Server 2008 資料庫中。|  
|[\<workflowIdle>](workflowidle.md)|這個服務行為可控制卸載及保存閒置工作流程執行個體的時間。|  
|[\<workflowInstanceManagement>](workflowinstancemanagement.md)|可讓您指定設定的服務行為，這些設定會控制工作流程執行個體的執行方式，包括持續性、未處理的例外狀況行為和閒置行為。|  
|[\<workflowUnhandledException>](workflowunhandledexception.md)|這個服務行為可讓您指定工作流程服務內發生未處理的例外狀況時要採取的動作。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|服務行為項目的集合。|
