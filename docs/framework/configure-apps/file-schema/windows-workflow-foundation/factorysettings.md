---
title: "&lt;factorySettings&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: 202aad17-1b8b-4c87-ad57-4ca5de18ed35
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;factorySettings&gt;
指定通道處理站快取的設定。  
  
## 語法  
  
```  
  
<behaviors>  
  <serviceBehaviors>  
    <behavior name=String">  
       <sendMessageChannelCache allowUnsafeCaching="Boolean" >          
           <factorySettings idleTimeout="TimeSpan" leaseTimeout="TimeSpan" maxItemsInCache="Integer" />  
       </sendMessageChannelCache>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|idleTimeout|TimeSpan 值，可指定物件處置前可在快取中維持閒置的最長時間間隔。|  
|leaseTimeout|TimeSpan 值，可指定物件自快取移除後的時間間隔。|  
|maxItemsInCache|整數，可指定快取中可容納的最大物件數量。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<sendMessageChannelCache\>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/sendmessagechannelcache.md)|這個服務行為可讓您自訂快取共用層級、通道處理站快取的設定，以及工作流程使用傳送訊息活動來傳送訊息至服務端點的通道快取設定。|  
  
## 備註  
 這個服務行為適用於將訊息傳送至服務端點的工作流程。  這些工作流程通常是用戶端工作流程，但也可以是裝載於 <xref:System.ServiceModel.WorkflowServiceHost> 中的工作流程服務。  
  
 根據預設，在 <xref:System.ServiceModel.WorkflowServiceHost> 所裝載的工作流程中，<xref:System.ServiceModel.Activities.Send> 中的所有工作流程執行個體會共用 <xref:System.ServiceModel.WorkflowServiceHost> 傳訊活動使用的快取 \(主機層級快取\)。  針對並非由 <xref:System.ServiceModel.WorkflowServiceHost> 裝載的用戶端工作流程，快取只能供工作流程執行個體使用 \(執行個體層級快取\)。  工作流程中的傳送活動若在組態中定義了端點，快取會依預設停用。  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]如何變更預設快取共用層級以及通道處理站與通道快取的快取設定，請參閱[變更傳送活動的快取共用層級](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)。  
  
## 範例  
 在裝載的工作流程服務中，您可以在應用程式組態檔中，指定處理站快取和通道快取設定。  若要執行這項操作，請加入包含處理站快取設定和通道快取的服務行為，然後將這個服務行為加入您的服務中。  下列範例顯示組態檔的內容，其中包含 **MyChannelCacheBehavior**  服務行為及自訂的處理站快取和通道快取設定。  這個服務行為是透過 **behaviorConfiguarion**  屬性加入服務的。  
  
```  
  
<configuration>    
  <system.serviceModel>  
    <!-- List of other config sections here -->   
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->   
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Activities.SendMessageChannelCache>   
 <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>   
 <xref:System.ServiceModel.Activities.Send>   
 <xref:System.ServiceModel.Activities.ChannelCacheSettings>   
 [變更傳送活動的快取共用層級](../../../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)