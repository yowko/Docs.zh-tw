---
title: 探索公告與公告用戶端
ms.date: 03/30/2017
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
ms.openlocfilehash: 4ad0b3ea5c257fa3117c426391bd59ad7b560d4f
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040173"
---
# <a name="discovery-announcements-and-announcement-client"></a>探索公告與公告用戶端

WCF 探索功能可讓元件宣告其可用性。 如果進行此設定，服務會傳送 Hello 和 Bye 公告。 用戶端或其他元件可以接聽此類公告訊息，然後採取行動。 此方法是讓用戶端注意服務存在的替代方法。 公告功能具有多種用途，例如，如果服務頻繁進出網路，公告便可能會是較搜尋服務更好的方法。 透過此方法，除了可降低網路流量之外，用戶端也會在收到公告的同時得知服務的出現或離開。

## <a name="discovery-announcements"></a>探索公告

當設定為公告的服務加入網路且變成可探索時，公告將會傳送 Hello 訊息，向接聽的用戶端告知其可用性。 訊息會包含與服務有關的探索相關資訊，例如合約、端點位址和關聯範圍。 您可以指定與 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> 類別一同傳送的公告訊息位置。 如果公告端點為 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>，則會視情形多點傳送 Hello 和 Bye，或者如果公告端點為單點傳送，則會將訊息直接傳送至指定的端點。

> [!NOTE]
> 當服務主機開啟和關閉時會傳送公告。 如果這些呼叫並未順利完成，則可能不會傳送公告訊息。例如，如果服務發生錯誤，則不會傳送 Bye 公告訊息。

> [!TIP]
> 您可以自訂公告功能，以便在選定的時間傳送公告。

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] 會將 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> 和 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> 定義為標準端點，使服務和用戶端可輕鬆地傳送 Hello 和 Bye 公告。

### <a name="announcements-on-the-service"></a>服務上的公告

若要設定服務以傳送公告，請透過公告端點加入 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>。 下列範例示範如何將此行為以程式設計方式加入至服務主機。 此範例使用 `UdpAnnouncementEndpoint`，這表示公告會多點傳送至由該標準端點指定的位置。

```csharp
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```

此行為也可以在組態檔中設定，如下列範例所示。

```xml
<services>
  <service behaviorConfiguration="CalculatorBehavior" name="Microsoft.Samples.Discovery.CalculatorService">
    <!--Add Discovery Endpoint-->
    <endpoint name="udpDiscoveryEpt" kind="udpDiscoveryEndpoint" />
  </service>
</services>
<behaviors>
  <serviceBehaviors>
    <behavior name="CalculatorBehavior">
      <!--Add Discovery behavior-->
      <serviceDiscovery>
        <announcementEndpoints>
          <endpoint kind="udpAnnouncementEndpoint" />
        </announcementEndpoints>
      </serviceDiscovery>
    </behavior>
  </serviceBehaviors>
</behaviors>
```

先前的範例會將服務設定為自動傳送公告訊息。 您也可以使用 <xref:System.ServiceModel.Discovery.AnnouncementClient> 類別，明確傳送公告訊息。

### <a name="announcements-on-the-client"></a>用戶端上的公告

用戶端應用程式必須裝載公告服務才能回應 Hello 和 Bye 訊息，並訂閱 <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> 和 <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> 事件。 下列範例顯示如何執行這項工作。

```csharp
// Create an AnnouncementService instance
AnnouncementService announcementService = new AnnouncementService();

// Subscribe the announcement events
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;

// Create ServiceHost for the AnnouncementService
using (ServiceHost announcementServiceHost = new ServiceHost(announcementService))
{
    // Listen for the announcements sent over UDP multicast
    announcementServiceHost.AddServiceEndpoint(new UdpAnnouncementEndpoint());
    announcementServiceHost.Open();

    Console.WriteLine("Press <ENTER> to terminate.");
    Console.ReadLine();
}
```

收到 Hello 或 Bye 訊息時，您可以透過 <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> 存取端點探索中繼資料，如下列範例所示。

```csharp
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine("Received an online announcement from {0}",
e.EndpointDiscoveryMetadata.Address);
}

static void OnOfflineEvent(object sender, AnnouncementEventArgs e)
{
    Console.WriteLine("Received an offline announcement from {0}",
e.EndpointDiscoveryMetadata.Address);
}
```
