---
title: WCF 探索概觀
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7b44a1587c704b0995821c7126f0264695861558
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="wcf-discovery-overview"></a>WCF 探索概觀
探索 API 為使用 WS-Discovery 通訊協定動態發行和探索 Web 服務的作業，提供了統一的程式設計模型。 這些 API 可讓服務自行發行，並且讓用戶端尋找發行的服務。 一旦服務變成可探索，就能夠傳送公告訊息，以及接聽和回應探索要求。 可探索的服務可以傳送 Hello 訊息，公告服務抵達網路，以及傳送 Bye 訊息，公告服務離開網路。 若要尋找服務，用戶端可傳送包含特定準則的 `Probe` 要求，例如服務合約型別、關鍵字以及在網路上的範圍。 服務會接收 `Probe` 要求並判斷是否符合準則。 如果服務符合準則，則會將 `ProbeMatch` 訊息傳回至用戶端做為回應，其中包含連絡服務所需的資訊。 用戶端也可以傳送 `Resolve` 要求，以尋找可能已變更其端點位址的服務。 相符的服務會透過將 `Resolve` 訊息傳回用戶端的方式回應 `ResolveMatch` 要求。  
  
## <a name="ad-hoc-and-managed-modes"></a>特定和 Managed 模式  
 探索 API 支援兩種不同的模式：Managed 和特定 (Ad-Hoc)。 Managed 模式中會有稱為探索 Proxy 的集中式伺服器，用於維護可用服務的相關資訊。 探索 Proxy 中可以透過各種方式填入有關服務的資訊。 例如，服務可以在啟動時傳送公告訊息至探索 Proxy，或者 Proxy 可從資料庫或組態檔讀取資料，以判斷哪些服務可用。 填入探索 Proxy 的方式完全取決於開發人員。 用戶端會使用探索 Proxy 擷取可用服務的相關資訊。 當用戶端搜尋服務時，會傳送 `Probe` 訊息給探索 Proxy，而 Proxy 會判斷已知的任何服務中，是否有符合用戶端所搜尋的服務。 如果有符合的服務，探索 Proxy 就會傳送 `ProbeMatch` 回應至用戶端。 接著，用戶端就可以使用從 Proxy 傳回的服務資訊直接連絡服務。 Managed 模式背後的主要原則是：探索要求以單點傳送的方式傳送至一個授權單位，也就是探索 Proxy。 .NET Framework 中包含的主要元件可讓您建立自己的 Proxy。 用戶端和服務可以透過許多種方法尋找 Proxy：  
  
-   Proxy 可以回應特定訊息。  
  
-   Proxy 可以在啟動時傳送公告訊息。  
  
-   用戶端和服務可以撰寫為尋找特定的已知端點。  
  
 特定模式中沒有集中式伺服器。 所有探索訊息 (例如服務公告和用戶端要求) 都是以多點傳送的方式傳送。 根據預設，.NET Framework 包含透過 UDP 通訊協定支援特定探索的能力。 例如，如果服務設定為在啟動時送出 Hello 公告，則會透過使用 UDP 通訊協定的已知多點傳送位址送出該公告。 用戶端必須主動接聽這些公告，並且進行對應的處理。 當用戶端傳送服務的 `Probe` 訊息時，會透過使用多點傳送通訊協定的網路進行傳送。 每一項接收要求的服務都會判斷本身是否符合 `Probe` 訊息中的準則，而如果服務符合 `ProbeMatch` 訊息中指定的準則，就會以 `Probe` 訊息直接回應用戶端。  
  
## <a name="benefits-of-using-wcf-discovery"></a>使用 WCF 探索的優點  
 由於 WCF 探索是使用 WS-Discovery 通訊協定實作，因此也能夠與其他實作 WS-Discovery 的用戶端、服務和 Proxy 互通。 WCF 探索建置於現有的 WCF API 之上，方便您將探索功能加入至現有的服務和用戶端。 服務探索功能可透過應用程式組態設定輕鬆加入。 此外，WCF 探索還支援在其他傳輸上使用探索通訊協定，例如對等網路、命名重疊和 HTTP。 WCF 探索支援使用探索 Proxy 的 Managed 模式作業。 這種方式可減少網路流量，因為訊息會直接傳送至探索 Proxy，而不會傳送多點傳送訊息至整個網路。 WCF 探索搭配 Web 服務使用時，還能提供更大的靈活度。 例如，您可以變更服務位址，而不需重新設定用戶端或服務。 當用戶端必須存取服務時，可以透過 `Probe` 要求發出 `Find` 訊息，並且預期服務以其目前位置回應。 WCF 探索可讓用戶端根據不同的準則搜尋服務，包括合約型別、繫結項目、命名空間、範圍，以及關鍵字或版本號碼。 WCF 探索提供執行階段和設計階段探索的能力。 將探索加入至您的應用程式，即可啟用其他功能，例如容錯和自動組態。  
  
## <a name="service-publication"></a>服務發行  
 若要讓服務變成可探索，則必須將 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 加入至服務主機，並且必須加入探索端點以指定要接聽探索訊息的位置。 下列程式碼範例示範如何修改自我裝載服務，讓它成為可探索。  
  
```csharp  
Uri baseAddress = new Uri(string.Format("http://{0}:8000/discovery/scenarios/calculatorservice/{1}/",  
        System.Net.Dns.GetHostName(), Guid.NewGuid().ToString()));

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 執行個體必須加入至服務描述，服務才能變成可探索。 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> 執行個體必須加入至服務主機，以告知服務接聽探索要求的位置。 此範例中會加入 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (衍生自 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>)，指定服務應該透過 UDP 多點傳送傳輸接聽探索要求。 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 用於特定探索，因為所有訊息都會以多點傳送的方式傳送。  
  
## <a name="announcement"></a>公告  
 根據預設，服務發行不會送出公告訊息。 但是服務必須設定為送出公告訊息。 如此能為服務寫入器提供額外的彈性，因為這樣就能將服務與接聽探索訊息個別進行公告。 服務公告也可以用來做為在探索 Proxy 或其他服務註冊中註冊服務的機制。 下列程式碼示範如何設定讓服務透過 UDP 繫結傳送公告訊息。  
  
```csharp  
Uri baseAddress = new Uri(string.Format("http://{0}:8000/discovery/scenarios/calculatorservice/{1}/",
        System.Net.Dns.GetHostName(), Guid.NewGuid().ToString()));

// Create a ServiceHost for the CalculatorService type.
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))
{
    // Add calculator endpoint
    serviceHost.AddServiceEndpoint(typeof(ICalculator), new WSHttpBinding(), string.Empty);

    // ** DISCOVERY ** //
    // Make the service discoverable by adding the discovery behavior
    ServiceDiscoveryBehavior discoveryBehavior = new ServiceDiscoveryBehavior();
    serviceHost.Description.Behaviors.Add(new ServiceDiscoveryBehavior());

    // Send announcements on UDP multicast transport
    discoveryBehavior.AnnouncementEndpoints.Add(
      new UdpAnnouncementEndpoint());

    // ** DISCOVERY ** //
    // Add the discovery endpoint that specifies where to publish the services
    serviceHost.Description.Endpoints.Add(new UdpDiscoveryEndpoint());

    // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();

    // The service can now be accessed.
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.ReadLine();
}
```  
  
## <a name="service-discovery"></a>服務探索  
 用戶端應用程式可以使用 <xref:System.ServiceModel.Discovery.DiscoveryClient> 類別尋找服務。 開發人員會建立 <xref:System.ServiceModel.Discovery.DiscoveryClient> 類別的執行個體，該執行個體會傳遞探索端點，指定傳送 `Probe` 或 `Resolve` 訊息的位置。 接著，用戶端會呼叫 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>，以便在 <xref:System.ServiceModel.Discovery.FindCriteria> 執行個體內指定搜尋準則。 如果找到符合的服務，<xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 就會傳回 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> 的集合。 下列程式碼示範如何呼叫 `Find` 方法，然後連接到已探索的服務。  
  
```csharp  
class Client
{
    static EndpointAddress serviceAddress;
  
    static void Main()
    {  
        if (FindService()) 
        {
            InvokeService();
        }
    }  
  
    // ** DISCOVERY ** //  
    static bool FindService()  
    {  
        Console.WriteLine("\nFinding Calculator Service ..");  
        DiscoveryClient discoveryClient =   
            new DiscoveryClient(new UdpDiscoveryEndpoint());  
  
        Collection<EndpointDiscoveryMetadata> calculatorServices =   
            (Collection<EndpointDiscoveryMetadata>)discoveryClient.Find(new FindCriteria(typeof(ICalculator))).Endpoints;  
  
        discoveryClient.Close();  
  
        if (calculatorServices.Count == 0)  
        {  
            Console.WriteLine("\nNo services are found.");  
            return false;  
        }  
        else  
        {  
            serviceAddress = calculatorServices[0].Address;  
            return true;  
        }  
    }  
  
    static void InvokeService()  
    {  
        Console.WriteLine("\nInvoking Calculator Service at {0}\n", serviceAddress);  
  
        // Create a client  
        CalculatorClient client = new CalculatorClient();  
        client.Endpoint.Address = serviceAddress;  
        client.Add(10,3);  
    }
}  
```  
  
## <a name="discovery-and-message-level-security"></a>探索和訊息層級安全性  
 使用訊息層級安全性時，必須在服務探索端點上指定 <xref:System.ServiceModel.EndpointIdentity>，並在用戶端探索端點上指定相符的 <xref:System.ServiceModel.EndpointIdentity>。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 訊息層級安全性，請參閱[訊息安全性](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)。  
  
## <a name="discovery-and-web-hosted-services"></a>探索和 Web 裝載的服務  
 WCF 服務必須處於執行中狀態，才能呈現可探索狀態。 在 IIS 或 WAS 底下裝載的 WCF 服務要等到 IIS/WAS 接收預定傳送至服務的訊息時才會執行，因此這些服務預設無法呈現可探索狀態。  有兩個選項可讓 Web 裝載的服務呈現可探索狀態：  
  
1.  使用 Windows Server AppFabric 自動啟動功能  
  
2.  使用探索 Proxy 來代表服務通訊  
  
 Windows Server AppFabric 具有自動啟動功能，可讓服務在接收任何訊息之前啟動。 設定這項自動啟動功能之後，即可將 IIS/WAS 裝載的服務設定為可探索。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 自動啟動功能，請參閱[Windows Server AppFabric 自動啟動功能](http://go.microsoft.com/fwlink/?LinkId=205545)。 除了開啟自動啟動功能以外，您也必須針對探索設定服務。 如需詳細資訊，請參閱[How to： 以程式設計方式將探索能力的 WCF 服務和用戶端](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[組態檔中設定的探索](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md)。  
  
 當 WCF 服務並未執行時，探索 Proxy 可用來代表服務通訊。 此 Proxy 可接聽探查或解析訊息並回應用戶端。 然後，用戶端就可以將訊息直接傳送至服務。 當用戶端將訊息傳送至服務時，服務將具現化以回應訊息。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] 實作探索 proxy，請參閱[實作探索 Proxy](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)。  
  
> [!NOTE]
>  WCF 探索才能正常運作，所有 Nic （網路介面控制器） 應該都只有 1 個 IP 位址。
