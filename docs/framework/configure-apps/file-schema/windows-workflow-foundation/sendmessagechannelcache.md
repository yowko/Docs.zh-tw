---
title: <sendMessageChannelCache>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 241e428e-5030-4b13-8a0a-69f05288d3d9
ms.openlocfilehash: b68c6d2e526eb22328806558d7c167b7f2ed0820
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151997"
---
# <a name="sendmessagechannelcache"></a>\<發送消息頻道緩存>
這個服務行為可讓您自訂快取共用層級、通道處理站快取的設定，以及工作流程使用傳送訊息活動來傳送訊息至服務端點的通道快取設定。  
  
[**\<配置>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<系統。服務模式>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<行為>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<服務行為>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<行為>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<發送消息通道緩存>**  
  
## <a name="syntax"></a>語法  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <sendMessageChannelCache allowUnsafeCaching="Boolean">
        <channelSettings idleTimeout="TimeSpan"
                         leaseTimeout="TimeSpan"
                         maxItemsInCache="Integer" />
        <factorySettings idleTimeout="TimeSpan"
                         leaseTimeout="TimeSpan"
                         maxItemsInCache="Integer" />
      </sendMessageChannelCache>
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|allowUnsafeCaching|指出是否要開啟快取功能的布林值。 如果您的工作流程服務有自訂繫結或自訂行為，快取可能會不安全，因此快取功能會依預設停用。 但是，如果要在將緩存打開，則將此屬性設置為**true**。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<通道設置>](channelsettings.md)|指定通道快取的設定。|  
|[\<工廠設置>](factorysettings.md)|指定通道處理站快取的設定。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<服務行為行為\<>>](behavior-of-servicebehaviors-of-workflow.md)|指定行為項目。|  
  
## <a name="remarks"></a>備註  
 這個服務行為適用於將訊息傳送至服務端點的工作流程。 這些工作流程通常是用戶端工作流程，但也可以是裝載於 <xref:System.ServiceModel.WorkflowServiceHost> 中的工作流程服務。  
  
 根據預設，在 <xref:System.ServiceModel.WorkflowServiceHost> 所裝載的工作流程中，<xref:System.ServiceModel.Activities.Send> 中的所有工作流程執行個體會共用 <xref:System.ServiceModel.WorkflowServiceHost> 傳訊活動使用的快取 (主機層級快取)。 針對並非由 <xref:System.ServiceModel.WorkflowServiceHost> 裝載的用戶端工作流程，快取只能供工作流程執行個體使用 (執行個體層級快取)。 工作流程中的傳送活動若在組態中定義了端點，快取會依預設停用。  
  
 有關如何更改通道工廠和通道緩存的預設緩存共用級別和緩存設置的詳細資訊，請參閱[更改"發送活動"的緩存共用級別](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)。  
  
## <a name="example"></a>範例  
 在裝載的工作流程服務中，您可以在應用程式組態檔中，指定處理站快取和通道快取設定。 若要執行這項操作，請加入包含處理站快取設定和通道快取的服務行為，然後將這個服務行為加入您的服務中。 下面的示例顯示包含自訂工廠緩存和通道緩存設置`MyChannelCacheBehavior`的服務行為的設定檔的內容。 此服務行為通過 屬性添加到服務中`behaviorConfiguration`。  
  
```xml  
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
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Activities.SendMessageChannelCache>
- <xref:System.ServiceModel.Activities.Configuration.SendMessageChannelCacheElement>
- <xref:System.ServiceModel.Activities.Send>
- [變更傳送活動的快取共用層級](../../../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md)
