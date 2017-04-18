---
title: "工作流程 &lt;serviceBehaviors&gt; 的 &lt;behavior&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 6a4b718a-1b40-4957-935a-f6122819ab3c
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 工作流程 &lt;serviceBehaviors&gt; 的 &lt;behavior&gt;
**behavior** 項目包含服務行為之設定的集合。  各個行為是依其 **name** 進行索引。  服務可透過使用[\<endpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)項目之**behaviorConfiguration**屬性的這個名稱，連結至每一個行為。  如此可允許端點共用通用行為組態，而不用重新定義設定。  
  
## 語法  
  
```  
  
<system.ServiceModel>  
  <behaviors>  
    <serviceBehaviors>  
    <behavior name=String">  
      <bufferReceive maxPendingMessagesPerChannel=”Integer” />  
      <etwTracking profileName=”String” />  
     <sendMessageChannelCache allowUnsafeCaching="Boolean" >          
        <channelSettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
        <factorySettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
     </sendMessageChannelCache>  
      <sqlWorkflowInstanceStore   
          connectionStringName=”String”   
          honstLockRenewalPeriod=”TimeSpan”  
          instanceCompletionAction=”DeleteNothing/DeleteAll”  
          instanceEncodingAction=”None/GZip”  
          instanceLockedExceptionAction=”NoRetry/BasicRetry/AggressiveRetry”  
          runnableInstancesDetectionPeriod=”TimeSpan” />  
      <workflowIdle timeToPersist=”TimeSpan”  
          timeToUnload=”TimeSpan” />  
      <workflowUnhandledException action=”Abandon/AbandonAndSuspend/Cancel/Terminate” />  
    </behavior>  
    </serviceBehaviors>  
  </behaviors>  
</system.ServiceModel>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|name|唯一的字串，其中包含行為的組態名稱。  這個值是使用者定義的字串，它必須是唯一的，因為它會充當項目的識別字串。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<bufferReceive\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/bufferreceive.md)|讓服務可以使用緩衝接收處理的服務行為，該處理可讓工作流程服務處理失序的訊息。|  
|[\<傳送\>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing-of-servicebehavior.md)|可讓服務透過使用 <xref:System.Activities.Tracking.ETWTrackingParticipant> 來利用 ETW 進行追蹤的服務行為。|  
|[\<sendMessageChannelCache\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|這個服務行為可讓您自訂快取共用層級、通道處理站快取的設定，以及工作流程使用傳送訊息活動來傳送訊息至服務端點的通道快取設定。|  
|[\<sqlWorkflowInstanceStore\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sqlworkflowinstancestore.md)|這個服務行為可讓您設定 <xref:System.Activities.DurableInstancing.SqlWorkflowInstanceStore> 功能，該功能支援將工作流程服務執行個體的狀態資訊保存在 SQL Server 2005 或 SQL Server 2008 資料庫中。|  
|[\<workflowIdle\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowidle.md)|這個服務行為可控制卸載及保存閒置工作流程執行個體的時間。|  
|[\<workflowInstanceManagement\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowinstancemanagement.md)|可讓您指定設定的服務行為，這些設定會控制工作流程執行個體的執行方式，包括持續性、未處理的例外狀況行為和閒置行為。|  
|[\<workflowUnhandledException\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflowunhandledexception.md)|這個服務行為可讓您指定工作流程服務內發生未處理的例外狀況時要採取的動作。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<serviceBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|服務行為項目的集合。|