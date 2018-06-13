---
title: 變更傳送活動的快取共用層級
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: 359a9189cee34eeb814a2303be3d2da725456e39
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494529"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a>變更傳送活動的快取共用層級
<xref:System.ServiceModel.Activities.SendMessageChannelCache> 擴充可讓您為使用 <xref:System.ServiceModel.Activities.Send> 傳訊活動傳送訊息至服務端點的工作流程自訂快取共用層級、通道處理站快取的設定，以及通道快取的設定。 這些工作流程通常是用戶端工作流程，但也可以是裝載於 <xref:System.ServiceModel.WorkflowServiceHost> 中的工作流程服務。 通道處理站快取會包含快取的 <xref:System.ServiceModel.ChannelFactory%601> 物件。 通道快取則包含快取的通道。  
  
> [!NOTE]
>  工作流程可以利用 <xref:System.ServiceModel.Activities.Send> 傳訊活動傳送訊息或參數。 工作流程執行階段會將通道處理站加入快取，這個快取會在您使用 <xref:System.ServiceModel.Channels.IRequestChannel> 活動搭配 <xref:System.ServiceModel.Activities.ReceiveReply> 活動時建立 <xref:System.ServiceModel.Activities.Send> 型別的通道，以及在您只使用 <xref:System.ServiceModel.Channels.IOutputChannel> 活動 (無 <xref:System.ServiceModel.Activities.Send>) 時建立 <xref:System.ServiceModel.Activities.ReceiveReply> 型別的通道。  
  
## <a name="the-cache-sharing-levels"></a>快取共用層級  
 根據預設，在 <xref:System.ServiceModel.WorkflowServiceHost> 所裝載的工作流程中，<xref:System.ServiceModel.Activities.Send> 中的所有工作流程執行個體會共用 <xref:System.ServiceModel.WorkflowServiceHost> 傳訊活動使用的快取 (主機層級快取)。 針對並非由 <xref:System.ServiceModel.WorkflowServiceHost> 裝載的用戶端工作流程，快取只能供工作流程執行個體使用 (執行個體層級快取)。 此快取僅適用於 <xref:System.ServiceModel.Activities.Send> 活動 (此活動不使用組態中定義的端點，除非已啟用不安全的快取)。  
  
 以下是工作流程中的 <xref:System.ServiceModel.Activities.Send> 活動適用的不同快取共用層級，以及其建議用法：  
  
-   **主機層級**： 在主機共用層級，快取是僅適用於裝載工作流程服務主機中的工作流程執行個體。 整個處理序快取中的工作流程服務主機間也可以共用快取。  
  
-   **執行個體層級**： 共用層級的執行個體，在快取可在其存留期的特定工作流程執行個體，但快取不適用於其他工作流程執行個體。  
  
-   **無快取**： 快取預設關閉如果您有使用端點組態中定義的工作流程。 在此情況下，建議保持關閉快取，因為開啟快取可能不安全。 例如，如果每次傳送都需要不同的識別 (不同的認證或使用模擬)。  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a>變更用戶端工作流程的快取共用層級  
 若要在用戶端工作流程中設定快取共用，請將 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 類別的執行個體做為擴充，加入所需的一組工作流程執行個體。 這樣會跨所有工作流程執行個體共用快取。 下列程式碼範例示範如何執行這些步驟。  
  
 首先，宣告 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 型別的執行個體。  
  
```  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 接下來，將快取擴充加入每個用戶端工作流程執行個體。  
  
```  
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object   
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a>變更裝載之工作流程服務的快取共用層級。  
 若要在裝載的工作流程服務中設定快取共用，請將 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 類別的執行個體加入至所有工作流程服務主機做為擴充。 這樣會跨所有工作流程服務主機共用快取。 下列程式碼範例示範如何執行這些步驟。  
  
 首先，在類別層級宣告 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 型別的執行個體。  
  
```  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 接下來，將靜態快取擴充加入每個工作流程服務主機。  
  
```  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 若要在裝載的工作流程服務中將快取共用設定至執行個體層級，請將 `Func<SendMessageChannelCache>` 委派加入至工作流程服務主機做為擴充，並且將這個委派指派至執行個體化 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 類別的新執行個體的程式碼。 這樣會讓每個個別工作流程執行個體產生不同的快取，而不是工作流程服務主機中的所有工作流程執行個體共用單一快取。 下列程式碼範例示範如何使用 Lambda 運算式直接定義委派所指向的 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 擴充，以達到這個目的。  
  
```  
serviceHost.WorkflowExtensions.Add(() => new SendMessageChannelCache  
{  
    // Use FactorySettings property to add custom factory cache settings.  
    FactorySettings = new ChannelCacheSettings   
    { MaxItemsInCache = 5, },  
    // Use ChannelSettings property to add custom channel cache settings.  
    ChannelSettings = new ChannelCacheSettings   
    { MaxItemsInCache = 10 },  
});  
```  
  
## <a name="customizing-cache-settings"></a>自訂快取設定  
 您可以自訂通道處理站快取與通道快取的快取設定。 快取設定是在 <xref:System.ServiceModel.Activities.ChannelCacheSettings> 類別中所定義的。 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 類別會定義在其預設的建構函式中之通道處理站快取與通道快取的設定。 下表列出這些屬於每個快取型別之快取設定的預設值。  
  
|設定|LeaseTimeout (分鐘)|IdleTimeout (分鐘)|MaxItemsInCache|  
|-|-|-|-|  
|處理站快取預設值|TimeSpan.MaxValue|2|16|  
|通道快取預設值|5|2|16|  
  
 若要自訂處理站快取與通道快取設定，請使用參數化的建構函式 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 將 <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> 類別執行具現化，並且將 <xref:System.ServiceModel.Activities.ChannelCacheSettings> 的新執行個體 (具有自訂值)，傳遞至每個 `factorySettings` 和 `channelSettings` 參數。 接著，請將這個類別的新執行個體加入工作流程服務主機或工作流程執行個體，做為擴充。 下列程式碼範例示範如何針對工作流程執行個體執行這些步驟。  
  
```  
ChannelCacheSettings factorySettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,   
                        IdleTimeout = TimeSpan.FromMinutes(5),   
                        LeaseTimeout = TimeSpan.FromMinutes(20)};  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,   
                        IdleTimeout = TimeSpan.FromMinutes(2),  
                        LeaseTimeout = TimeSpan.FromMinutes(10) };  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 當您的工作流程服務中具有在組態中定義的端點時，若要啟用快取，請使用參數化建構函式 <xref:System.ServiceModel.Activities.SendMessageChannelCache> 執行具現化 <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> 類別 (`allowUnsafeCaching` 參數設定為 `true`)。 接著，請將這個類別的新執行個體加入工作流程服務主機或工作流程執行個體，做為擴充。 下列程式碼範例示範如何啟用工作流程執行個體的快取。  
  
```  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 若要完全停用通道處理站與通道的快取，請停用通道處理站快取。 這麼做也會關閉通道快取，因為通道的擁有者是與其對應的通道處理站。 若要停用通道處理站快取，請將 `factorySettings` 參數傳送至 <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> 建構函式，這個建構函式已經初始化為 <xref:System.ServiceModel.Activities.ChannelCacheSettings> 執行個體，其 <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> 的值為 0。 下列程式碼範例會顯示這點。  
  
```  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 您可以選擇只使用通道處理站快取並停用通道快取，方法是將 `channelSettings` 參數傳送至 <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> 建構函式，這個建構函式已初始化為 <xref:System.ServiceModel.Activities.ChannelCacheSettings> 執行個體，其 <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> 值為 0。 下列程式碼範例會顯示這點。  
  
```  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =   
    new SendMessageChannelCache(factorySettings, channelSettings);   
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 在裝載的工作流程服務中，您可以在應用程式組態檔中，指定處理站快取和通道快取設定。 若要執行這項操作，請加入包含處理站快取設定和通道快取的服務行為，然後將這個服務行為加入您的服務中。 下列範例顯示組態檔中包含的內容`MyChannelCacheBehavior`使用自訂處理站快取和通道快取設定服務行為。 這個服務行為加入至服務，透過`behaviorConfiguarion`屬性。  
  
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
