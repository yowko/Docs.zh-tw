---
title: AspNetRouteIntegration
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0638ce0e-d053-47df-a447-688e447a03fb
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b54de1c495dee466475979db7e6ba8d8ff9cf55b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="aspnetrouteintegration"></a><span data-ttu-id="fdefd-102">AspNetRouteIntegration</span><span class="sxs-lookup"><span data-stu-id="fdefd-102">AspNetRouteIntegration</span></span>
<span data-ttu-id="fdefd-103">此範例示範如何使用 ASP.NET 路由裝載 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] REST 服務。</span><span class="sxs-lookup"><span data-stu-id="fdefd-103">This sample demonstrates how to host a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] REST service using ASP.NET routes.</span></span> <span data-ttu-id="fdefd-104">[基本資源服務](../../../../docs/framework/wcf/samples/basic-resource-service.md)範例示範此案例中的自我裝載的版本，並討論深度的服務實作。</span><span class="sxs-lookup"><span data-stu-id="fdefd-104">The [Basic Resource Service](../../../../docs/framework/wcf/samples/basic-resource-service.md) sample shows a self-hosted version of this scenario and discusses the service implementation in depth.</span></span> <span data-ttu-id="fdefd-105">本主題著重在 ASP.NET 整合功能。</span><span class="sxs-lookup"><span data-stu-id="fdefd-105">This topic focuses on the ASP.NET integration feature.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="fdefd-106"> ASP.NET 路由的詳細資訊，請參閱 <xref:System.Web.Routing>。</span><span class="sxs-lookup"><span data-stu-id="fdefd-106"> ASP.NET Routing, see <xref:System.Web.Routing>.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="fdefd-107">範例詳細資料</span><span class="sxs-lookup"><span data-stu-id="fdefd-107">Sample Details</span></span>  
 <span data-ttu-id="fdefd-108">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務會以資源導向/REST 的方式公開客戶的集合。</span><span class="sxs-lookup"><span data-stu-id="fdefd-108">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service exposes a collection of customers in a resource-oriented/REST manner.</span></span> <span data-ttu-id="fdefd-109">此服務就像以 SOAP 為基礎的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務，可以使用 .svc 檔案在 ASP.NET 中裝載。</span><span class="sxs-lookup"><span data-stu-id="fdefd-109">Just like a SOAP-based [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, the service can be hosted in ASP.NET using a .svc file.</span></span> <span data-ttu-id="fdefd-110">不過，這通常不適用於 HTTP 情況，因為它必須在服務的 URL 中擁有 .svc。</span><span class="sxs-lookup"><span data-stu-id="fdefd-110">However, this is often not preferred for HTTP scenarios because it requires having .svc in the URL for the service.</span></span> <span data-ttu-id="fdefd-111">此外，它需要部署 .svc 檔案以及服務程式庫。</span><span class="sxs-lookup"><span data-stu-id="fdefd-111">In addition, it requires deploying a .svc file along with the service library.</span></span> <span data-ttu-id="fdefd-112">您可以如本範例中所示範的方式，使用 ASP.NET 路由裝載服務來避免這些限制。</span><span class="sxs-lookup"><span data-stu-id="fdefd-112">These limitations can be avoided by hosting the service using ASP.NET routes, as is demonstrated in this sample.</span></span>  
  
 <span data-ttu-id="fdefd-113">此範例會在 Global.asax 檔案中加入 <xref:System.ServiceModel.Activation.ServiceRoute> 來裝載 ASP.NET 中的服務。</span><span class="sxs-lookup"><span data-stu-id="fdefd-113">The sample hosts the service in ASP.NET by adding a <xref:System.ServiceModel.Activation.ServiceRoute> in a Global.asax file.</span></span> <span data-ttu-id="fdefd-114"><xref:System.ServiceModel.Activation.ServiceRoute> 會指定服務的類型 (在此案例中為 ‘Service’)、用於服務的服務主機處理站類型 (在此案例中為 <xref:System.ServiceModel.Activation.WebServiceHostFactory>)，以及服務的 HTTP 起始位址 (在此案例中為 ‘~/Customers’)。</span><span class="sxs-lookup"><span data-stu-id="fdefd-114">The <xref:System.ServiceModel.Activation.ServiceRoute> specifies the type of the service (‘Service’ in this case), the type of the service host factory to use for the service (<xref:System.ServiceModel.Activation.WebServiceHostFactory> in this case) and the HTTP base address for the service (‘~/Customers’ in this case).</span></span>  
  
 <span data-ttu-id="fdefd-115">除此之外，此範例還包含加入 <xref:System.Web.Routing.UrlRoutingModule> (以開啟 ASP.NET 路由) 的 Web.config 以及服務的組態。</span><span class="sxs-lookup"><span data-stu-id="fdefd-115">In addition to this, the sample includes a Web.config that adds the <xref:System.Web.Routing.UrlRoutingModule> (to turn on ASP.NET routes) and includes the configuration for the service.</span></span> <span data-ttu-id="fdefd-116">特別是，此組態會以預設的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 來設定 <xref:System.ServiceModel.Description.WebHttpEndpoint> 服務，且 <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> 設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="fdefd-116">In particular, the configuration configures the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with a default <xref:System.ServiceModel.Description.WebHttpEndpoint> that has the <xref:System.ServiceModel.Description.WebHttpEndpoint.HelpEnabled%2A> setting to `true`.</span></span> <span data-ttu-id="fdefd-117">因此，[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 基礎結構會在 `http://localhost/Customers/help` 中建立自動 HTML 說明頁，這個頁面會提供如何對服務建構 HTTP 要求以及如何存取服務之 HTTP 回應的相關資訊，例如，如何以 XML 和 JSON 表示客戶詳細資料的範例。</span><span class="sxs-lookup"><span data-stu-id="fdefd-117">As a result, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure creates an automatic HTML based help page at `http://localhost/Customers/help` that provides information about how to construct HTTP requests to the service and how to access the service’s HTTP response – for instance, an example of how the customer details are represented in XML and JSON.</span></span>  
  
 <span data-ttu-id="fdefd-118">以此方式公開客戶集合 (以及更普遍的任何資源) 可讓用戶端以統一的方式，使用 URI 和 HTTP `GET`、`PUT`、`DELETE` 以及 `POST` 與服務互動。</span><span class="sxs-lookup"><span data-stu-id="fdefd-118">Exposing the customer collection (and more generally, any resource) in this manner allows a client to interact with a service in a uniform way using URIs and HTTP `GET`, `PUT`, `DELETE` and `POST`.</span></span>  
  
 <span data-ttu-id="fdefd-119">用戶端專案中的 Program.cs 會示範如何使用 <xref:System.Net.HttpWebRequest> 編寫這種用戶端。</span><span class="sxs-lookup"><span data-stu-id="fdefd-119">Program.cs in the Client project demonstrates how such a client can be authored using <xref:System.Net.HttpWebRequest>.</span></span> <span data-ttu-id="fdefd-120">請注意，這只是存取 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務的其中一種方式。</span><span class="sxs-lookup"><span data-stu-id="fdefd-120">Note that this is just one way to access a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="fdefd-121">您也可以使用其他 .NET Framework 類別 (例如 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 通道處理站和 <xref:System.Net.WebClient>) 來存取服務。</span><span class="sxs-lookup"><span data-stu-id="fdefd-121">It is also possible to access the service using other .NET Framework classes like the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] channel factory and <xref:System.Net.WebClient>.</span></span> <span data-ttu-id="fdefd-122">SDK 中的其他範例 (例如[基本 HTTP 服務](../../../../docs/framework/wcf/samples/basic-http-service.md)範例和[自動格式選取](../../../../docs/framework/wcf/samples/automatic-format-selection.md)範例) 示範如何使用這些類別來與通訊[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]服務。</span><span class="sxs-lookup"><span data-stu-id="fdefd-122">Other samples in the SDK (such as the [Basic HTTP Service](../../../../docs/framework/wcf/samples/basic-http-service.md) sample and the [Automatic Format Selection](../../../../docs/framework/wcf/samples/automatic-format-selection.md) sample) show how to use these classes to communicate with a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span>  
  
 <span data-ttu-id="fdefd-123">此範例包含 3 個專案：</span><span class="sxs-lookup"><span data-stu-id="fdefd-123">This sample consists of 3 projects:</span></span>  
  
 <span data-ttu-id="fdefd-124">服務</span><span class="sxs-lookup"><span data-stu-id="fdefd-124">Service</span></span>  
 <span data-ttu-id="fdefd-125">包含 ASP.NET 中裝載之 WCF HTTP 服務的 Web 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="fdefd-125">A Web application project that includes a WCF HTTP service hosted in ASP.NET.</span></span>  
  
 <span data-ttu-id="fdefd-126">用戶端</span><span class="sxs-lookup"><span data-stu-id="fdefd-126">Client</span></span>  
 <span data-ttu-id="fdefd-127">呼叫服務的主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="fdefd-127">A console application project that makes calls to the service.</span></span>  
  
 <span data-ttu-id="fdefd-128">通用</span><span class="sxs-lookup"><span data-stu-id="fdefd-128">Common</span></span>  
 <span data-ttu-id="fdefd-129">包含用戶端和服務所使用之 `Customer` 類型的共用程式庫。</span><span class="sxs-lookup"><span data-stu-id="fdefd-129">A shared library that contains the `Customer` type used by the client and service.</span></span> <span data-ttu-id="fdefd-130">當用戶端主控台應用程式執行時，用戶端會對服務發出要求，然後將相關的資訊從回應寫入至主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="fdefd-130">As the client console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="fdefd-131">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="fdefd-131">To use this sample</span></span>  
  
1.  <span data-ttu-id="fdefd-132">在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中，開啟 ASP.NET 路由整合範例的方案。</span><span class="sxs-lookup"><span data-stu-id="fdefd-132">Open the solution for the ASP.NET Routes Integration sample in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
2.  <span data-ttu-id="fdefd-133">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="fdefd-133">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="fdefd-134">如果它尚未開啟，請按下 「 CTRL + W、 S 」 開啟**方案總管 中**視窗。</span><span class="sxs-lookup"><span data-stu-id="fdefd-134">If it is not already open, press "CTRL+W, S" to open the **Solution Explorer** window.</span></span>  
  
4.  <span data-ttu-id="fdefd-135">從**方案總管 中**windows 中，以滑鼠右鍵按一下**服務**專案，並將游標放在**偵錯**內容功能表選項，讓**開始新執行個體**會出現內容功能表，然後選取**開始新執行個體**。</span><span class="sxs-lookup"><span data-stu-id="fdefd-135">From the **Solution Explorer** windows, right-click the **Service** project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears and select **Start New Instance**.</span></span>  <span data-ttu-id="fdefd-136">這樣會啟動裝載服務的 ASP.NET 程式開發伺服器。</span><span class="sxs-lookup"><span data-stu-id="fdefd-136">This launches the ASP.NET development server, which hosts the service.</span></span>  
  
5.  <span data-ttu-id="fdefd-137">從**方案總管 中**windows 中，以滑鼠右鍵按一下**用戶端**專案，並將游標放在**偵錯**內容功能表選項，讓**新開始執行個體**會出現內容功能表，然後選取**開始新執行個體**。</span><span class="sxs-lookup"><span data-stu-id="fdefd-137">From the **Solution Explorer** windows, right-click the **Client** project and place the cursor over the **Debug** context menu option so that the **Start New Instance** context menu appears and select **Start New Instance**.</span></span>  
  
6.  <span data-ttu-id="fdefd-138">用戶端主控台視窗隨即出現，並提供執行中服務的 URI，以及執行中服務之 HTML 說明頁的 URI。</span><span class="sxs-lookup"><span data-stu-id="fdefd-138">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="fdefd-139">您可以隨時在瀏覽器中輸入說明頁的 URI 來檢視 HTML 說明頁。</span><span class="sxs-lookup"><span data-stu-id="fdefd-139">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span> <span data-ttu-id="fdefd-140">當範例執行時，用戶端會寫入目前活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="fdefd-140">As the sample runs, the client writes the status of the current activity.</span></span>  
  
7.  <span data-ttu-id="fdefd-141">按下任何按鍵可終止用戶端主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="fdefd-141">Press any key to terminate the client console application.</span></span>  
  
8.  <span data-ttu-id="fdefd-142">按 Shift + F5 停止偵錯服務並在 Windows 通知區域中，以滑鼠右鍵按一下 ASP.NET 程式開發伺服器圖示，然後選取**停止**從內容功能表。</span><span class="sxs-lookup"><span data-stu-id="fdefd-142">Press Shift+F5 to stop debugging the service and in the Windows Notification Area, right-click the ASP.NET development server icon and select **Stop** from the context menu.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="fdefd-143">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="fdefd-143">The samples may already be installed on your machine.</span></span> <span data-ttu-id="fdefd-144">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="fdefd-144">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="fdefd-145">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="fdefd-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="fdefd-146">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="fdefd-146">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetRouteIntegration`  
  
## <a name="see-also"></a><span data-ttu-id="fdefd-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fdefd-147">See Also</span></span>
