---
title: "探索公告與公告用戶端"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 426c6437-f8d2-4968-b23a-18afd671aa4b
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a6da9c2e251a6592bb0af039d552d02e7e4fd3fd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="discovery-announcements-and-announcement-client"></a><span data-ttu-id="fc589-102">探索公告與公告用戶端</span><span class="sxs-lookup"><span data-stu-id="fc589-102">Discovery Announcements and Announcement Client</span></span>
<span data-ttu-id="fc589-103">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 探索功能可讓元件公告其可用性。</span><span class="sxs-lookup"><span data-stu-id="fc589-103">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] discovery feature enables components to announce their availability.</span></span> <span data-ttu-id="fc589-104">如果進行此設定，服務會傳送 Hello 和 Bye 公告。</span><span class="sxs-lookup"><span data-stu-id="fc589-104">If configured to do so, a service sends Hello and Bye announcements.</span></span> <span data-ttu-id="fc589-105">用戶端或其他元件可以接聽此類公告訊息，然後採取行動。</span><span class="sxs-lookup"><span data-stu-id="fc589-105">Clients or other components can listen for such announcement messages and act on them.</span></span> <span data-ttu-id="fc589-106">此方法是讓用戶端注意服務存在的替代方法。</span><span class="sxs-lookup"><span data-stu-id="fc589-106">This provides an alternative method for clients to be aware of services.</span></span> <span data-ttu-id="fc589-107">公告功能具有多種用途，例如，如果服務頻繁進出網路，公告便可能會是較搜尋服務更好的方法。</span><span class="sxs-lookup"><span data-stu-id="fc589-107">Announcement functionality has several uses, for example, if the services enter and leave a network frequently, announcements may be a better alternative than searching for services.</span></span> <span data-ttu-id="fc589-108">透過此方法，除了可降低網路流量之外，用戶端也會在收到公告的同時得知服務的出現或離開。</span><span class="sxs-lookup"><span data-stu-id="fc589-108">With this approach, the network traffic is reduced and the client can learn about the presence or departure of the service as soon as announcements are received.</span></span>  
  
## <a name="discovery-announcements"></a><span data-ttu-id="fc589-109">探索公告</span><span class="sxs-lookup"><span data-stu-id="fc589-109">Discovery Announcements</span></span>  
 <span data-ttu-id="fc589-110">當設定為公告的服務加入網路且變成可探索時，公告將會傳送 Hello 訊息，向接聽的用戶端告知其可用性。</span><span class="sxs-lookup"><span data-stu-id="fc589-110">When a service configured for announcements joins a network and becomes discoverable, it sends a Hello message announcing its availability to listening clients.</span></span> <span data-ttu-id="fc589-111">訊息會包含與服務有關的探索相關資訊，例如合約、端點位址和關聯範圍。</span><span class="sxs-lookup"><span data-stu-id="fc589-111">The message contains discovery related information about the service, such as its contract, endpoint address and associated scopes.</span></span> <span data-ttu-id="fc589-112">您可以指定與 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> 類別一同傳送的公告訊息位置。</span><span class="sxs-lookup"><span data-stu-id="fc589-112">You can specify where the announcement message is sent with the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> class.</span></span> <span data-ttu-id="fc589-113">如果公告端點為 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>，則會視情形多點傳送 Hello 和 Bye，或者如果公告端點為單點傳送，則會將訊息直接傳送至指定的端點。</span><span class="sxs-lookup"><span data-stu-id="fc589-113">If the announcement endpoint is a <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> then the Hello and Bye are multicast appropriately, or if the announcement endpoint is unicast, the messages are sent directly to the specified endpoint.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc589-114">當服務主機開啟和關閉時會傳送公告。</span><span class="sxs-lookup"><span data-stu-id="fc589-114">Announcements are sent when the service host opens and closes.</span></span> <span data-ttu-id="fc589-115">如果這些呼叫並未順利完成，則可能不會傳送公告訊息。例如，如果服務發生錯誤，則不會傳送 Bye 公告訊息。</span><span class="sxs-lookup"><span data-stu-id="fc589-115">If these calls do not finish properly the announcement message may not be sent out. For example if the service faults, then the Bye announcement message is not sent.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="fc589-116">您可以自訂公告功能，以便在選定的時間傳送公告。</span><span class="sxs-lookup"><span data-stu-id="fc589-116">You can customize the announcement functionality, allowing you to send announcements whenever you choose.</span></span>  
  
 [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]<span data-ttu-id="fc589-117"> 會將 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> 和 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> 定義為標準端點，使服務和用戶端可輕鬆地傳送 Hello 和 Bye 公告。</span><span class="sxs-lookup"><span data-stu-id="fc589-117"> defines the <xref:System.ServiceModel.Discovery.AnnouncementEndpoint> and <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint> as standard endpoints to allow services and clients to easily send Hello and Bye announcements.</span></span>  
  
### <a name="announcements-on-the-service"></a><span data-ttu-id="fc589-118">服務上的公告</span><span class="sxs-lookup"><span data-stu-id="fc589-118">Announcements on the Service</span></span>  
 <span data-ttu-id="fc589-119">若要設定服務以傳送公告，請透過公告端點加入 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>。</span><span class="sxs-lookup"><span data-stu-id="fc589-119">To configure the service to send announcements, add a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> with an announcement endpoint.</span></span> <span data-ttu-id="fc589-120">下列範例示範如何將此行為以程式設計方式加入至服務主機。</span><span class="sxs-lookup"><span data-stu-id="fc589-120">The following example shows how to programmatically add this behavior to the service host.</span></span> <span data-ttu-id="fc589-121">此範例使用 `UdpAnnouncementEndpoint`，這表示公告會多點傳送至由該標準端點指定的位置。</span><span class="sxs-lookup"><span data-stu-id="fc589-121">This example uses the `UdpAnnouncementEndpoint`, which implies that the announcements are multicast to a location specified by that standard endpoint.</span></span>  
  
```  
ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();
serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());
serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);
```  
  
 <span data-ttu-id="fc589-122">此行為也可以在組態檔中設定，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="fc589-122">The behavior can be configured in the configuration file as well, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="fc589-123">先前的範例會將服務設定為自動傳送公告訊息。</span><span class="sxs-lookup"><span data-stu-id="fc589-123">The preceding examples configure a service to automatically send announcement messages.</span></span> <span data-ttu-id="fc589-124">您也可以使用 <xref:System.ServiceModel.Discovery.AnnouncementClient> 類別，明確傳送公告訊息。</span><span class="sxs-lookup"><span data-stu-id="fc589-124">You can also send announcement messages explicitly by using the <xref:System.ServiceModel.Discovery.AnnouncementClient> class.</span></span>  
  
### <a name="announcements-on-the-client"></a><span data-ttu-id="fc589-125">用戶端上的公告</span><span class="sxs-lookup"><span data-stu-id="fc589-125">Announcements on the Client</span></span>  
 <span data-ttu-id="fc589-126">用戶端應用程式必須裝載公告服務才能回應 Hello 和 Bye 訊息，並訂閱 <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> 和 <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> 事件。</span><span class="sxs-lookup"><span data-stu-id="fc589-126">A client application must host an announcement service to respond to the Hello and Bye messages and subscribe to the <xref:System.ServiceModel.Discovery.AnnouncementService.OnlineAnnouncementReceived> and <xref:System.ServiceModel.Discovery.AnnouncementService.OfflineAnnouncementReceived> events.</span></span> <span data-ttu-id="fc589-127">下列範例顯示如何執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="fc589-127">The following example shows how to do this.</span></span>  
  
```  
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
  
 <span data-ttu-id="fc589-128">收到 Hello 或 Bye 訊息時，您可以透過 <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> 存取端點探索中繼資料，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="fc589-128">When a Hello or Bye message is received, you can access the endpoint discovery metadata through <xref:System.ServiceModel.Discovery.AnnouncementEventArgs> as shown in the following example.</span></span>  
  
```  
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
