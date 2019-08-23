---
title: WCF 探索概觀
ms.date: 03/30/2017
ms.assetid: 84fad0e4-23b1-45b5-a2d4-c9cdf90bbb22
ms.openlocfilehash: fce16038b4c9ab65047125be1881be4b86976aee
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931848"
---
# <a name="wcf-discovery-overview"></a><span data-ttu-id="4b27b-102">WCF 探索概觀</span><span class="sxs-lookup"><span data-stu-id="4b27b-102">WCF Discovery Overview</span></span>
<span data-ttu-id="4b27b-103">探索 API 為使用 WS-Discovery 通訊協定動態發行和探索 Web 服務的作業，提供了統一的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="4b27b-103">The Discovery APIs provide a unified programming model for the dynamic publication and discovery of Web services using the WS-Discovery protocol.</span></span> <span data-ttu-id="4b27b-104">這些 API 可讓服務自行發行，並且讓用戶端尋找發行的服務。</span><span class="sxs-lookup"><span data-stu-id="4b27b-104">These APIs allow services to publish themselves and clients to find published services.</span></span> <span data-ttu-id="4b27b-105">一旦服務變成可探索，就能夠傳送公告訊息，以及接聽和回應探索要求。</span><span class="sxs-lookup"><span data-stu-id="4b27b-105">Once a service is made discoverable, the service has the ability to send announcement messages as well as listen for and respond to discovery requests.</span></span> <span data-ttu-id="4b27b-106">可探索的服務可以傳送 Hello 訊息，公告服務抵達網路，以及傳送 Bye 訊息，公告服務離開網路。</span><span class="sxs-lookup"><span data-stu-id="4b27b-106">Discoverable services can send Hello messages to announce their arrival on a network and Bye messages to announce their departure from a network.</span></span> <span data-ttu-id="4b27b-107">若要尋找服務，用戶端可傳送包含特定準則的 `Probe` 要求，例如服務合約型別、關鍵字以及在網路上的範圍。</span><span class="sxs-lookup"><span data-stu-id="4b27b-107">To find a service, clients send a `Probe` request that contains specific criteria such as service contract type, keywords, and scope on the network.</span></span> <span data-ttu-id="4b27b-108">服務會接收 `Probe` 要求並判斷是否符合準則。</span><span class="sxs-lookup"><span data-stu-id="4b27b-108">Services receive the `Probe` request and determine whether they match the criteria.</span></span> <span data-ttu-id="4b27b-109">如果服務符合準則，則會將 `ProbeMatch` 訊息傳回至用戶端做為回應，其中包含連絡服務所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="4b27b-109">If a service matches, it responds by sending a `ProbeMatch` message back to the client with the information necessary to contact the service.</span></span> <span data-ttu-id="4b27b-110">用戶端也可以傳送 `Resolve` 要求，以尋找可能已變更其端點位址的服務。</span><span class="sxs-lookup"><span data-stu-id="4b27b-110">Clients can also send `Resolve` requests that allow them to find services that may have changed their endpoint address.</span></span> <span data-ttu-id="4b27b-111">相符的服務會透過將 `Resolve` 訊息傳回用戶端的方式回應 `ResolveMatch` 要求。</span><span class="sxs-lookup"><span data-stu-id="4b27b-111">Matching services respond to `Resolve` requests by sending a `ResolveMatch` message back to the client.</span></span>  
  
## <a name="ad-hoc-and-managed-modes"></a><span data-ttu-id="4b27b-112">特定和 Managed 模式</span><span class="sxs-lookup"><span data-stu-id="4b27b-112">Ad-Hoc and Managed Modes</span></span>  
 <span data-ttu-id="4b27b-113">探索 API 支援兩種不同的模式:受控和臨機操作。</span><span class="sxs-lookup"><span data-stu-id="4b27b-113">The Discovery API supports two different modes: Managed and Ad-Hoc.</span></span> <span data-ttu-id="4b27b-114">Managed 模式中會有稱為探索 Proxy 的集中式伺服器，用於維護可用服務的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4b27b-114">In Managed mode there is a centralized server called a discovery proxy that maintains information about available services.</span></span> <span data-ttu-id="4b27b-115">探索 Proxy 中可以透過各種方式填入有關服務的資訊。</span><span class="sxs-lookup"><span data-stu-id="4b27b-115">The discovery proxy can be populated with information about services in a variety of ways.</span></span> <span data-ttu-id="4b27b-116">例如，服務可以在啟動時傳送公告訊息至探索 Proxy，或者 Proxy 可從資料庫或組態檔讀取資料，以判斷哪些服務可用。</span><span class="sxs-lookup"><span data-stu-id="4b27b-116">For example, services can send announcement messages during start up to the discovery proxy or the proxy may read data from a database or a configuration file to determine what services are available.</span></span> <span data-ttu-id="4b27b-117">填入探索 Proxy 的方式完全取決於開發人員。</span><span class="sxs-lookup"><span data-stu-id="4b27b-117">How the discovery proxy is populated is completely up to the developer.</span></span> <span data-ttu-id="4b27b-118">用戶端會使用探索 Proxy 擷取可用服務的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="4b27b-118">Clients use the discovery proxy to retrieve information about available services.</span></span> <span data-ttu-id="4b27b-119">當用戶端搜尋服務時，會傳送 `Probe` 訊息給探索 Proxy，而 Proxy 會判斷已知的任何服務中，是否有符合用戶端所搜尋的服務。</span><span class="sxs-lookup"><span data-stu-id="4b27b-119">When a client searches for a service it sends a `Probe` message to the discovery proxy and the proxy determines whether any of the services it knows about match the service the client is searching for.</span></span> <span data-ttu-id="4b27b-120">如果有符合的服務，探索 Proxy 就會傳送 `ProbeMatch` 回應至用戶端。</span><span class="sxs-lookup"><span data-stu-id="4b27b-120">If there are matches the discovery proxy sends a `ProbeMatch` response back to the client.</span></span> <span data-ttu-id="4b27b-121">接著，用戶端就可以使用從 Proxy 傳回的服務資訊直接連絡服務。</span><span class="sxs-lookup"><span data-stu-id="4b27b-121">The client can then contact the service directly using the service information returned from the proxy.</span></span> <span data-ttu-id="4b27b-122">Managed 模式背後的主要原則是：探索要求以單點傳送的方式傳送至一個授權單位，也就是探索 Proxy。</span><span class="sxs-lookup"><span data-stu-id="4b27b-122">The key principle behind Managed mode is that the discovery requests are sent in a unicast manner to one authority, the discovery proxy.</span></span> <span data-ttu-id="4b27b-123">.NET Framework 中包含的主要元件可讓您建立自己的 Proxy。</span><span class="sxs-lookup"><span data-stu-id="4b27b-123">The .NET Framework contains key components that allow you to build your own proxy.</span></span> <span data-ttu-id="4b27b-124">用戶端和服務可以透過許多種方法尋找 Proxy：</span><span class="sxs-lookup"><span data-stu-id="4b27b-124">Clients and services can locate the proxy by multiple methods:</span></span>  
  
- <span data-ttu-id="4b27b-125">Proxy 可以回應特定訊息。</span><span class="sxs-lookup"><span data-stu-id="4b27b-125">The proxy can respond to ad-hoc messages.</span></span>  
  
- <span data-ttu-id="4b27b-126">Proxy 可以在啟動時傳送公告訊息。</span><span class="sxs-lookup"><span data-stu-id="4b27b-126">The proxy can send an announcement message during start up.</span></span>  
  
- <span data-ttu-id="4b27b-127">用戶端和服務可以撰寫為尋找特定的已知端點。</span><span class="sxs-lookup"><span data-stu-id="4b27b-127">Clients and services can be written to look for a specific well-known endpoint.</span></span>  
  
 <span data-ttu-id="4b27b-128">特定模式中沒有集中式伺服器。</span><span class="sxs-lookup"><span data-stu-id="4b27b-128">In Ad-Hoc mode, there is no centralized server.</span></span> <span data-ttu-id="4b27b-129">所有探索訊息 (例如服務公告和用戶端要求) 都是以多點傳送的方式傳送。</span><span class="sxs-lookup"><span data-stu-id="4b27b-129">All discovery messages such as service announcements and client requests are sent in a multicast fashion.</span></span> <span data-ttu-id="4b27b-130">根據預設，.NET Framework 包含透過 UDP 通訊協定支援特定探索的能力。</span><span class="sxs-lookup"><span data-stu-id="4b27b-130">By default the .NET Framework contains support for Ad-Hoc discovery over the UDP protocol.</span></span> <span data-ttu-id="4b27b-131">例如，如果服務設定為在啟動時送出 Hello 公告，則會透過使用 UDP 通訊協定的已知多點傳送位址送出該公告。</span><span class="sxs-lookup"><span data-stu-id="4b27b-131">For example, if a service is configured to send out a Hello announcement on start up, it sends it out over a well-known, multicast address using the UDP protocol.</span></span> <span data-ttu-id="4b27b-132">用戶端必須主動接聽這些公告，並且進行對應的處理。</span><span class="sxs-lookup"><span data-stu-id="4b27b-132">Clients have to actively listen for these announcements and process them accordingly.</span></span> <span data-ttu-id="4b27b-133">當用戶端傳送服務的 `Probe` 訊息時，會透過使用多點傳送通訊協定的網路進行傳送。</span><span class="sxs-lookup"><span data-stu-id="4b27b-133">When a client sends a `Probe` message for a service it is sent over the network using a multicast protocol.</span></span> <span data-ttu-id="4b27b-134">每一項接收要求的服務都會判斷本身是否符合 `Probe` 訊息中的準則，而如果服務符合 `ProbeMatch` 訊息中指定的準則，就會以 `Probe` 訊息直接回應用戶端。</span><span class="sxs-lookup"><span data-stu-id="4b27b-134">Each service that receives the request determines whether it matches the criteria in the `Probe` message and responds directly to the client with a `ProbeMatch` message if the service matches the criteria specified in the `Probe` message.</span></span>  
  
## <a name="benefits-of-using-wcf-discovery"></a><span data-ttu-id="4b27b-135">使用 WCF 探索的優點</span><span class="sxs-lookup"><span data-stu-id="4b27b-135">Benefits of Using WCF Discovery</span></span>  
 <span data-ttu-id="4b27b-136">由於 WCF 探索是使用 WS-Discovery 通訊協定實作，因此也能夠與其他實作 WS-Discovery 的用戶端、服務和 Proxy 互通。</span><span class="sxs-lookup"><span data-stu-id="4b27b-136">Because WCF Discovery is implemented using the WS-Discovery protocol it is interoperable with other clients, services, and proxies that implement WS-Discovery as well.</span></span> <span data-ttu-id="4b27b-137">WCF 探索建置於現有的 WCF API 之上，方便您將探索功能加入至現有的服務和用戶端。</span><span class="sxs-lookup"><span data-stu-id="4b27b-137">WCF Discovery is built upon the existing WCF APIs, which makes it easy to add Discovery functionality to your existing services and clients.</span></span> <span data-ttu-id="4b27b-138">服務探索功能可透過應用程式組態設定輕鬆加入。</span><span class="sxs-lookup"><span data-stu-id="4b27b-138">Service discoverability can be easily added through the application configuration settings.</span></span> <span data-ttu-id="4b27b-139">此外，WCF 探索還支援在其他傳輸上使用探索通訊協定，例如對等網路、命名重疊和 HTTP。</span><span class="sxs-lookup"><span data-stu-id="4b27b-139">In addition, WCF Discovery also supports using the discovery protocol over other transports such as peer net, naming overlay, and HTTP.</span></span> <span data-ttu-id="4b27b-140">WCF 探索支援使用探索 Proxy 的 Managed 模式作業。</span><span class="sxs-lookup"><span data-stu-id="4b27b-140">WCF Discovery provides support for a Managed mode of operation where a discovery proxy is used.</span></span> <span data-ttu-id="4b27b-141">這種方式可減少網路流量，因為訊息會直接傳送至探索 Proxy，而不會傳送多點傳送訊息至整個網路。</span><span class="sxs-lookup"><span data-stu-id="4b27b-141">This can reduce network traffic as messages are sent directly to the discovery proxy instead of sending multicast messages to the entire network.</span></span> <span data-ttu-id="4b27b-142">WCF 探索搭配 Web 服務使用時，還能提供更大的靈活度。</span><span class="sxs-lookup"><span data-stu-id="4b27b-142">WCF Discovery also allows for more flexibility when working with Web services.</span></span> <span data-ttu-id="4b27b-143">例如，您可以變更服務位址，而不需重新設定用戶端或服務。</span><span class="sxs-lookup"><span data-stu-id="4b27b-143">For example, you can change the address of a service without having to reconfigure the client or the service.</span></span> <span data-ttu-id="4b27b-144">當用戶端必須存取服務時，可以透過 `Probe` 要求發出 `Find` 訊息，並且預期服務以其目前位置回應。</span><span class="sxs-lookup"><span data-stu-id="4b27b-144">When a client must access the service it can issue a `Probe` message through a `Find` request and expect the service to respond with its current address.</span></span> <span data-ttu-id="4b27b-145">WCF 探索可讓用戶端根據不同的準則搜尋服務，包括合約型別、繫結項目、命名空間、範圍，以及關鍵字或版本號碼。</span><span class="sxs-lookup"><span data-stu-id="4b27b-145">WCF Discovery allows a client to search for a service based on different criteria including contract types, binding elements, namespace, scope, and keywords or version numbers.</span></span> <span data-ttu-id="4b27b-146">WCF 探索提供執行階段和設計階段探索的能力。</span><span class="sxs-lookup"><span data-stu-id="4b27b-146">WCF Discovery enables runtime and design time discovery.</span></span> <span data-ttu-id="4b27b-147">將探索加入至您的應用程式，即可啟用其他功能，例如容錯和自動組態。</span><span class="sxs-lookup"><span data-stu-id="4b27b-147">Adding discovery to your application can be used to enable other scenarios such as fault tolerance and auto configuration.</span></span>  
  
## <a name="service-publication"></a><span data-ttu-id="4b27b-148">服務發行</span><span class="sxs-lookup"><span data-stu-id="4b27b-148">Service Publication</span></span>  
 <span data-ttu-id="4b27b-149">若要讓服務變成可探索，則必須將 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 加入至服務主機，並且必須加入探索端點以指定要接聽探索訊息的位置。</span><span class="sxs-lookup"><span data-stu-id="4b27b-149">To make a service discoverable, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> must be added to the service host and a discovery endpoint must be added to specify where to listen for discovery messages.</span></span> <span data-ttu-id="4b27b-150">下列程式碼範例示範如何修改自我裝載服務，讓它成為可探索。</span><span class="sxs-lookup"><span data-stu-id="4b27b-150">The following code example shows how a self-hosted service can be modified to make it discoverable.</span></span>  
  
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
  
 <span data-ttu-id="4b27b-151"><xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> 執行個體必須加入至服務描述，服務才能變成可探索。</span><span class="sxs-lookup"><span data-stu-id="4b27b-151">A <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> instance must be added to a service description for the service to be discoverable.</span></span> <span data-ttu-id="4b27b-152"><xref:System.ServiceModel.Discovery.DiscoveryEndpoint> 執行個體必須加入至服務主機，以告知服務接聽探索要求的位置。</span><span class="sxs-lookup"><span data-stu-id="4b27b-152">A <xref:System.ServiceModel.Discovery.DiscoveryEndpoint> instance must be added to the service host to tell the service where to listen for discovery requests.</span></span> <span data-ttu-id="4b27b-153">此範例中會加入 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (衍生自 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>)，指定服務應該透過 UDP 多點傳送傳輸接聽探索要求。</span><span class="sxs-lookup"><span data-stu-id="4b27b-153">In this example, a <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> (which is derived from <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>) is added to specify that the service should listen for discovery requests over the UDP multicast transport.</span></span> <span data-ttu-id="4b27b-154"><xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 用於特定探索，因為所有訊息都會以多點傳送的方式傳送。</span><span class="sxs-lookup"><span data-stu-id="4b27b-154">The <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> is used for Ad-Hoc discovery because all messages are sent in a multicast fashion.</span></span>  
  
## <a name="announcement"></a><span data-ttu-id="4b27b-155">公告</span><span class="sxs-lookup"><span data-stu-id="4b27b-155">Announcement</span></span>  
 <span data-ttu-id="4b27b-156">根據預設，服務發行不會送出公告訊息。</span><span class="sxs-lookup"><span data-stu-id="4b27b-156">By default, service publication does not send out announcement messages.</span></span> <span data-ttu-id="4b27b-157">但是服務必須設定為送出公告訊息。</span><span class="sxs-lookup"><span data-stu-id="4b27b-157">The service must be configured to send out announcement messages.</span></span> <span data-ttu-id="4b27b-158">如此能為服務寫入器提供額外的彈性，因為這樣就能將服務與接聽探索訊息個別進行公告。</span><span class="sxs-lookup"><span data-stu-id="4b27b-158">This provides additional flexibility for service writers because they can announce the service separately from listening for discovery messages.</span></span> <span data-ttu-id="4b27b-159">服務公告也可以用來做為在探索 Proxy 或其他服務註冊中註冊服務的機制。</span><span class="sxs-lookup"><span data-stu-id="4b27b-159">Service announcement can also be used as a mechanism for registering services with a discovery proxy or other service registries.</span></span> <span data-ttu-id="4b27b-160">下列程式碼示範如何設定讓服務透過 UDP 繫結傳送公告訊息。</span><span class="sxs-lookup"><span data-stu-id="4b27b-160">The following code shows how to configure a service to send announcement messages over a UDP binding.</span></span>  
  
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
    serviceHost.Description.Behaviors.Add(discoveryBehavior);

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
  
## <a name="service-discovery"></a><span data-ttu-id="4b27b-161">服務探索</span><span class="sxs-lookup"><span data-stu-id="4b27b-161">Service Discovery</span></span>  
 <span data-ttu-id="4b27b-162">用戶端應用程式可以使用 <xref:System.ServiceModel.Discovery.DiscoveryClient> 類別尋找服務。</span><span class="sxs-lookup"><span data-stu-id="4b27b-162">A client application can use the <xref:System.ServiceModel.Discovery.DiscoveryClient> class to find services.</span></span> <span data-ttu-id="4b27b-163">開發人員會建立 <xref:System.ServiceModel.Discovery.DiscoveryClient> 類別的執行個體，該執行個體會傳遞探索端點，指定傳送 `Probe` 或 `Resolve` 訊息的位置。</span><span class="sxs-lookup"><span data-stu-id="4b27b-163">The developer creates an instance of the <xref:System.ServiceModel.Discovery.DiscoveryClient> class that passes in a discovery endpoint that specifies where to send `Probe` or `Resolve` messages.</span></span> <span data-ttu-id="4b27b-164">接著，用戶端會呼叫 <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A>，以便在 <xref:System.ServiceModel.Discovery.FindCriteria> 執行個體內指定搜尋準則。</span><span class="sxs-lookup"><span data-stu-id="4b27b-164">The client then calls <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> that specifies search criteria within a <xref:System.ServiceModel.Discovery.FindCriteria> instance.</span></span> <span data-ttu-id="4b27b-165">如果找到符合的服務，<xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> 就會傳回 <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata> 的集合。</span><span class="sxs-lookup"><span data-stu-id="4b27b-165">If matching services are found, <xref:System.ServiceModel.Discovery.DiscoveryClient.Find%2A> returns a collection of <xref:System.ServiceModel.Discovery.EndpointDiscoveryMetadata>.</span></span> <span data-ttu-id="4b27b-166">下列程式碼示範如何呼叫 `Find` 方法，然後連接到已探索的服務。</span><span class="sxs-lookup"><span data-stu-id="4b27b-166">The following code shows how to call the `Find` method and then connect to a discovered service.</span></span>  
  
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
  
## <a name="discovery-and-message-level-security"></a><span data-ttu-id="4b27b-167">探索和訊息層級安全性</span><span class="sxs-lookup"><span data-stu-id="4b27b-167">Discovery and Message Level Security</span></span>  
 <span data-ttu-id="4b27b-168">使用訊息層級安全性時，必須在服務探索端點上指定 <xref:System.ServiceModel.EndpointIdentity>，並在用戶端探索端點上指定相符的 <xref:System.ServiceModel.EndpointIdentity>。</span><span class="sxs-lookup"><span data-stu-id="4b27b-168">When using message level security it is necessary to specify an <xref:System.ServiceModel.EndpointIdentity> on the service discovery endpoint and a matching <xref:System.ServiceModel.EndpointIdentity> on the client discovery endpoint.</span></span> <span data-ttu-id="4b27b-169">如需訊息層級安全性的詳細資訊, 請參閱[訊息安全性](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)。</span><span class="sxs-lookup"><span data-stu-id="4b27b-169">For more information about message level security, see [Message Security](../../../../docs/framework/wcf/feature-details/message-security-in-wcf.md).</span></span>  
  
## <a name="discovery-and-web-hosted-services"></a><span data-ttu-id="4b27b-170">探索和 Web 裝載的服務</span><span class="sxs-lookup"><span data-stu-id="4b27b-170">Discovery and Web Hosted Services</span></span>  
 <span data-ttu-id="4b27b-171">WCF 服務必須處於執行中狀態，才能呈現可探索狀態。</span><span class="sxs-lookup"><span data-stu-id="4b27b-171">In order for WCF services to be discoverable they must be running.</span></span> <span data-ttu-id="4b27b-172">在 IIS 或 WAS 底下裝載的 WCF 服務要等到 IIS/WAS 接收預定傳送至服務的訊息時才會執行，因此這些服務預設無法呈現可探索狀態。</span><span class="sxs-lookup"><span data-stu-id="4b27b-172">WCF services hosted under IIS or WAS do not run until IIS/WAS receives a message bound for the service, so they cannot be discoverable by default.</span></span>  <span data-ttu-id="4b27b-173">有兩個選項可讓 Web 裝載的服務呈現可探索狀態：</span><span class="sxs-lookup"><span data-stu-id="4b27b-173">There are two options for making Web-Hosted services discoverable:</span></span>  
  
1. <span data-ttu-id="4b27b-174">使用 Windows Server AppFabric 自動啟動功能</span><span class="sxs-lookup"><span data-stu-id="4b27b-174">Use the Windows Server AppFabric Auto-Start feature</span></span>  
  
2. <span data-ttu-id="4b27b-175">使用探索 Proxy 來代表服務通訊</span><span class="sxs-lookup"><span data-stu-id="4b27b-175">Use a discovery proxy to communicate on behalf of the service</span></span>  
  
 <span data-ttu-id="4b27b-176">Windows Server AppFabric 具有自動啟動功能，可讓服務在接收任何訊息之前啟動。</span><span class="sxs-lookup"><span data-stu-id="4b27b-176">Windows Server AppFabric has an Auto-Start feature that will allow a service to be started before receiving any messages.</span></span> <span data-ttu-id="4b27b-177">設定這項自動啟動功能之後，即可將 IIS/WAS 裝載的服務設定為可探索。</span><span class="sxs-lookup"><span data-stu-id="4b27b-177">With this Auto-Start set, an IIS/WAS hosted service can be configured to be discoverable.</span></span> <span data-ttu-id="4b27b-178">如需有關自動啟動功能的詳細資訊, 請參閱[Windows Server AppFabric 自動啟動功能](https://go.microsoft.com/fwlink/?LinkId=205545)。</span><span class="sxs-lookup"><span data-stu-id="4b27b-178">For more information about the Auto-Start feature see, [Windows Server AppFabric Auto-Start Feature](https://go.microsoft.com/fwlink/?LinkId=205545).</span></span> <span data-ttu-id="4b27b-179">除了開啟自動啟動功能以外，您也必須針對探索設定服務。</span><span class="sxs-lookup"><span data-stu-id="4b27b-179">Along with turning on the Auto-Start feature, you must configure the service for discovery.</span></span> <span data-ttu-id="4b27b-180">如需詳細資訊，請參閱[如何：以程式設計方式將探索能力新增至](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)WCF 服務, 並[在設定檔中設定探索](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="4b27b-180">For more information, see [How to: Programmatically Add Discoverability to a WCF Service and Client](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)[Configuring Discovery in a Configuration File](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md).</span></span>  
  
 <span data-ttu-id="4b27b-181">當 WCF 服務並未執行時，探索 Proxy 可用來代表服務通訊。</span><span class="sxs-lookup"><span data-stu-id="4b27b-181">A discovery proxy can be used to communicate on behalf of the WCF service when the service is not running.</span></span> <span data-ttu-id="4b27b-182">此 Proxy 可接聽探查或解析訊息並回應用戶端。</span><span class="sxs-lookup"><span data-stu-id="4b27b-182">The proxy can listen for probe or resolve messages and respond to the client.</span></span> <span data-ttu-id="4b27b-183">然後，用戶端就可以將訊息直接傳送至服務。</span><span class="sxs-lookup"><span data-stu-id="4b27b-183">The client can then send messages directly to the service.</span></span> <span data-ttu-id="4b27b-184">當用戶端將訊息傳送至服務時，服務將具現化以回應訊息。</span><span class="sxs-lookup"><span data-stu-id="4b27b-184">When the client sends a message to the service it will be instantiated to respond to the message.</span></span> <span data-ttu-id="4b27b-185">如需有關如何執行探索 proxy 的詳細資訊, 請參閱[執行探索 proxy](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)。</span><span class="sxs-lookup"><span data-stu-id="4b27b-185">For more information about implementing a discovery proxy see, [Implementing a Discovery Proxy](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b27b-186">為了讓 WCF 探索正常運作, 所有 Nic (網路介面控制器) 都應該只有1個 IP 位址。</span><span class="sxs-lookup"><span data-stu-id="4b27b-186">For WCF Discovery to work correctly, all NICs (Network Interface Controller) should only have 1 IP address.</span></span>
