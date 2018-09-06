---
title: 公告範例
ms.date: 03/30/2017
ms.assetid: 954a75e4-9a97-41d6-94fc-43765d4205a9
ms.openlocfilehash: a82056844c9ec8f77bce4b0adec481a025894d1f
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43749258"
---
# <a name="announcements-sample"></a><span data-ttu-id="5eed2-102">公告範例</span><span class="sxs-lookup"><span data-stu-id="5eed2-102">Announcements Sample</span></span>
<span data-ttu-id="5eed2-103">此範例示範如何使用探索功能的公告功能。</span><span class="sxs-lookup"><span data-stu-id="5eed2-103">This sample shows how to use the Announcement functionality of the Discovery feature.</span></span> <span data-ttu-id="5eed2-104">公告功能可讓服務送出包含服務相關中繼資料的公告訊息。</span><span class="sxs-lookup"><span data-stu-id="5eed2-104">Announcements allow services to send out announcement messages that contain metadata about the service.</span></span> <span data-ttu-id="5eed2-105">當服務啟動時，預設會傳送一個 Hello 公告，而當服務關閉時，則會傳送一個 Bye 公告。</span><span class="sxs-lookup"><span data-stu-id="5eed2-105">By default a hello announcement is sent when the service starts up and a bye announcement is sent when the service shuts down.</span></span> <span data-ttu-id="5eed2-106">這些公告可以多點傳送，也可以點對點傳送。</span><span class="sxs-lookup"><span data-stu-id="5eed2-106">These announcements can be multicast or they can be sent point-to-point.</span></span> <span data-ttu-id="5eed2-107">這個範例包含兩個專案，也就是服務和用戶端。</span><span class="sxs-lookup"><span data-stu-id="5eed2-107">This sample consists of two projects service and client.</span></span>  
  
## <a name="service"></a><span data-ttu-id="5eed2-108">服務</span><span class="sxs-lookup"><span data-stu-id="5eed2-108">Service</span></span>  
 <span data-ttu-id="5eed2-109">此專案包含自我裝載的計算機服務。</span><span class="sxs-lookup"><span data-stu-id="5eed2-109">This project contains a self-hosted calculator service.</span></span> <span data-ttu-id="5eed2-110">在 `Main` 方法中會建立一個服務主機，並在其中加入一個服務端點。</span><span class="sxs-lookup"><span data-stu-id="5eed2-110">In the `Main` method, a service host is created and a service endpoint is added to it.</span></span> <span data-ttu-id="5eed2-111">接著，建立 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>。</span><span class="sxs-lookup"><span data-stu-id="5eed2-111">Next, a <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior> is created.</span></span> <span data-ttu-id="5eed2-112">若要啟用公告，公告端點必須加入至 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>。</span><span class="sxs-lookup"><span data-stu-id="5eed2-112">To enable announcements, an announcement endpoint must be added to the <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>.</span></span> <span data-ttu-id="5eed2-113">在此情況下，標準端點會使用 UDP 多點傳送，當做公告端點加入。</span><span class="sxs-lookup"><span data-stu-id="5eed2-113">In this case a standard endpoint, using UDP multicast is added as the announcement endpoint.</span></span> <span data-ttu-id="5eed2-114">這樣會透過已知的 UDP 位址廣播公告。</span><span class="sxs-lookup"><span data-stu-id="5eed2-114">This broadcasts the announcements over a well-known UDP address.</span></span>  
  
```  
Uri baseAddress = new Uri("http://localhost:8000/" + Guid.NewGuid().ToString());  
  
// Create a ServiceHost for the CalculatorService type.  
using (ServiceHost serviceHost = new ServiceHost(typeof(CalculatorService), baseAddress))  
{  
     serviceHost.AddServiceEndpoint(typeof(ICalculatorService), new WSHttpBinding(), String.Empty);  
  
     ServiceDiscoveryBehavior serviceDiscoveryBehavior = new ServiceDiscoveryBehavior();  
  
     // Announce the availability of the service over UDP multicast  
    serviceDiscoveryBehavior.AnnouncementEndpoints.Add(new UdpAnnouncementEndpoint());  
  
    // Make the service discoverable over UDP multicast.  
    serviceHost.Description.Behaviors.Add(serviceDiscoveryBehavior);                  
    serviceHost.AddServiceEndpoint(new UdpDiscoveryEndpoint());  
    serviceHost.Open();  
    // ...  
}  
```  
  
## <a name="client"></a><span data-ttu-id="5eed2-115">用戶端</span><span class="sxs-lookup"><span data-stu-id="5eed2-115">Client</span></span>  
 <span data-ttu-id="5eed2-116">請注意，此專案中的用戶端會裝載 <xref:System.ServiceModel.Discovery.AnnouncementService>。</span><span class="sxs-lookup"><span data-stu-id="5eed2-116">In this project, note that the client hosts an <xref:System.ServiceModel.Discovery.AnnouncementService>.</span></span> <span data-ttu-id="5eed2-117">此外，系統會向事件註冊兩個委派。</span><span class="sxs-lookup"><span data-stu-id="5eed2-117">Furthermore, two delegates are registered with events.</span></span> <span data-ttu-id="5eed2-118">這些事件會控制收到線上和離線公告時的用戶端作法。</span><span class="sxs-lookup"><span data-stu-id="5eed2-118">These events dictate what the client does when online and offline announcements are received.</span></span>  
  
```  
// Create an AnnouncementService instance  
AnnouncementService announcementService = new AnnouncementService();  
  
// Subscribe the announcement events  
announcementService.OnlineAnnouncementReceived += OnOnlineEvent;  
announcementService.OfflineAnnouncementReceived += OnOfflineEvent;  
```  
  
 <span data-ttu-id="5eed2-119">`OnOnlineEvent` 和 `OnOfflineEvent` 方法會分別處理 Hello 和 Bye 公告訊息。</span><span class="sxs-lookup"><span data-stu-id="5eed2-119">The `OnOnlineEvent` and `OnOfflineEvent` methods handle the hello and bye announcement messages respectively.</span></span>  
  
```  
static void OnOnlineEvent(object sender, AnnouncementEventArgs e)  
{  
    Console.WriteLine();              
    Console.WriteLine("Received an online announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);  
PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);  
}  
  
static void OnOfflineEvent(object sender, AnnouncementEventArgs e)  
{  
    Console.WriteLine();  
    Console.WriteLine("Received an offline announcement from {0}:", e.AnnouncementMessage.EndpointDiscoveryMetadata.Address);  
            PrintEndpointDiscoveryMetadata(e.AnnouncementMessage.EndpointDiscoveryMetadata);  
}  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="5eed2-120">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="5eed2-120">To use this sample</span></span>  
  
1.  <span data-ttu-id="5eed2-121">此範例使用 HTTP 端點，若要執行這個範例，適當的 URL Acl 必須加入，請參閱[設定 HTTP 和 HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="5eed2-121">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details.</span></span> <span data-ttu-id="5eed2-122">以更高的權限執行下列命令應該就能加入適當的 ACL。</span><span class="sxs-lookup"><span data-stu-id="5eed2-122">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="5eed2-123">如果命令未正確執行，您可能要將 Domain 和 Username 替換成下列引數。</span><span class="sxs-lookup"><span data-stu-id="5eed2-123">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  <span data-ttu-id="5eed2-124">建置方案。</span><span class="sxs-lookup"><span data-stu-id="5eed2-124">Build the solution.</span></span>  
  
3.  <span data-ttu-id="5eed2-125">執行 client.exe 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5eed2-125">Run the client.exe application.</span></span>  
  
4.  <span data-ttu-id="5eed2-126">執行 service.exe 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5eed2-126">Run the service.exe application.</span></span> <span data-ttu-id="5eed2-127">請注意，用戶端會收到線上公告。</span><span class="sxs-lookup"><span data-stu-id="5eed2-127">Note the client receives an online announcement.</span></span>  
  
5.  <span data-ttu-id="5eed2-128">關閉 service.exe 應用程式。</span><span class="sxs-lookup"><span data-stu-id="5eed2-128">Close the service.exe application.</span></span> <span data-ttu-id="5eed2-129">請注意，用戶端會收到離線公告。</span><span class="sxs-lookup"><span data-stu-id="5eed2-129">Note the client receives an offline announcement.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5eed2-130">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="5eed2-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5eed2-131">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="5eed2-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="5eed2-132">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="5eed2-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5eed2-133">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="5eed2-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Announcements`  
  
## <a name="see-also"></a><span data-ttu-id="5eed2-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5eed2-134">See Also</span></span>
