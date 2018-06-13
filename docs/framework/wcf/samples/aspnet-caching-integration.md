---
title: ASP.NET 快取整合
ms.date: 03/30/2017
ms.assetid: f581923a-8a72-42fc-bd6a-46de2aaeecc1
ms.openlocfilehash: 744ecbff8b51565906ff4c619ba8c8aecff123c7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33805404"
---
# <a name="aspnet-caching-integration"></a><span data-ttu-id="0f824-102">ASP.NET 快取整合</span><span class="sxs-lookup"><span data-stu-id="0f824-102">ASP.NET Caching Integration</span></span>
<span data-ttu-id="0f824-103">這個範例示範如何使用 ASP.NET 輸出快取搭配 WCF WEB HTTP 程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="0f824-103">This sample demonstrates how to utilize the ASP.NET output cache with the WCF WEB HTTP programming model.</span></span> <span data-ttu-id="0f824-104">請參閱[基本資源服務](../../../../docs/framework/wcf/samples/basic-resource-service.md)之自我裝載的版本，討論深度的服務實作此案例的範例。</span><span class="sxs-lookup"><span data-stu-id="0f824-104">Please see the [Basic Resource Service](../../../../docs/framework/wcf/samples/basic-resource-service.md) sample for a self-hosted version of this scenario that discusses the service implementation in depth.</span></span> <span data-ttu-id="0f824-105">本主題著重在 ASP.NET 輸出快取整合功能。</span><span class="sxs-lookup"><span data-stu-id="0f824-105">This topic focuses on the ASP.NET output cache integration feature.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="0f824-106">示範</span><span class="sxs-lookup"><span data-stu-id="0f824-106">Demonstrates</span></span>  
 <span data-ttu-id="0f824-107">與 ASP.NET 輸出快取整合</span><span class="sxs-lookup"><span data-stu-id="0f824-107">Integration with the ASP.NET Output Cache</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0f824-108">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="0f824-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0f824-109">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="0f824-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0f824-110">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="0f824-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0f824-111">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="0f824-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AspNetCachingIntegration`  
  
## <a name="discussion"></a><span data-ttu-id="0f824-112">討論</span><span class="sxs-lookup"><span data-stu-id="0f824-112">Discussion</span></span>  
 <span data-ttu-id="0f824-113">此範例會使用<xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>來利用 ASP.NET 輸出快取與 Windows Communication Foundation (WCF) 服務。</span><span class="sxs-lookup"><span data-stu-id="0f824-113">The sample uses the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> to utilize ASP.NET output caching with the Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="0f824-114"><xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> 會套用至服務作業，並提供應套用至所指作業之回應的組態檔中快取設定檔的名稱。</span><span class="sxs-lookup"><span data-stu-id="0f824-114">The <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute> is applied to service operations, and provides the name of a cache profile in a configuration file that should be applied to responses from the given operation.</span></span>  
  
 <span data-ttu-id="0f824-115">範例服務專案的 Service.cs 檔案中同時`GetCustomer`和`GetCustomers`作業會標示<xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>，這樣會提供快取設定檔名稱"CacheFor60Seconds"。</span><span class="sxs-lookup"><span data-stu-id="0f824-115">In the Service.cs file of the sample Service project, both the `GetCustomer` and `GetCustomers` operations are marked with the <xref:System.ServiceModel.Web.AspNetCacheProfileAttribute>, which provides the cache profile name "CacheFor60Seconds".</span></span> <span data-ttu-id="0f824-116">在服務專案的 Web.config 檔案中，快取設定檔"CacheFor60Seconds"提供下 <`caching`> 項目 <`system.web`>。</span><span class="sxs-lookup"><span data-stu-id="0f824-116">In the Web.config file of the Service project, the cache profile "CacheFor60Seconds" is provided under the <`caching`> element of <`system.web`>.</span></span> <span data-ttu-id="0f824-117">此快取設定檔，值`duration`屬性是"60"，因此與這個設定檔相關聯的回應會在 ASP.NET 輸出快取中快取 60 秒。</span><span class="sxs-lookup"><span data-stu-id="0f824-117">For this cache profile, the value of the `duration` attribute is "60", so responses associated with this profile are cached in the ASP.NET output cache for 60 seconds.</span></span> <span data-ttu-id="0f824-118">此外，對於這個快取設定檔，`varmByParam`屬性設定為"format"這樣的要求包含不同的值`format`查詢字串參數另行快取其回應。</span><span class="sxs-lookup"><span data-stu-id="0f824-118">Also, for this cache profile, the `varmByParam` attribute is set to "format" so requests with different values for the `format` query string parameter have their responses cached separately.</span></span> <span data-ttu-id="0f824-119">最後，快取設定檔的`varyByHeader`屬性設為"Accept"，因此對於 Accept 標頭值不同的要求，必須另行快取其回應。</span><span class="sxs-lookup"><span data-stu-id="0f824-119">Lastly, the cache profile’s `varyByHeader` attribute is set to "Accept", so requests with different Accept header values have their responses cached separately.</span></span>  
  
 <span data-ttu-id="0f824-120">用戶端專案中的 Program.cs 會示範如何使用 <xref:System.Net.HttpWebRequest> 編寫這種用戶端。</span><span class="sxs-lookup"><span data-stu-id="0f824-120">Program.cs in the Client project demonstrates how such a client can be authored using <xref:System.Net.HttpWebRequest>.</span></span> <span data-ttu-id="0f824-121">請注意，這只是存取 WCF 服務的其中一種方式。</span><span class="sxs-lookup"><span data-stu-id="0f824-121">Note that this is just one way to access a WCF service.</span></span> <span data-ttu-id="0f824-122">它也可使用其他.NET Framework 類別，例如 WCF 通道處理站存取服務和<xref:System.Net.WebClient>。</span><span class="sxs-lookup"><span data-stu-id="0f824-122">It is also possible to access the service using other .NET Framework classes like the WCF channel factory and <xref:System.Net.WebClient>.</span></span> <span data-ttu-id="0f824-123">SDK 中的其他範例 (例如[基本 HTTP 服務](../../../../docs/framework/wcf/samples/basic-http-service.md)範例和[自動格式選取](../../../../docs/framework/wcf/samples/automatic-format-selection.md)範例) 說明如何使用這些類別，與 WCF 服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="0f824-123">Other samples in the SDK (such as the [Basic HTTP Service](../../../../docs/framework/wcf/samples/basic-http-service.md) sample and the [Automatic Format Selection](../../../../docs/framework/wcf/samples/automatic-format-selection.md) sample) illustrate how to use these classes to communicate with a WCF service.</span></span>  
  
## <a name="to-run-the-sample"></a><span data-ttu-id="0f824-124">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="0f824-124">To run the sample</span></span>  
 <span data-ttu-id="0f824-125">此範例包含三個專案：</span><span class="sxs-lookup"><span data-stu-id="0f824-125">The sample consists of three projects:</span></span>  
  
-   <span data-ttu-id="0f824-126">**服務**： 包含 ASP.NET 中裝載之 WCF HTTP 服務的 Web 應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="0f824-126">**Service**: A Web Application project that includes a WCF HTTP service hosted in ASP.NET.</span></span>  
  
-   <span data-ttu-id="0f824-127">**用戶端**： 呼叫服務的主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="0f824-127">**Client**: A console application project that makes calls to the service.</span></span>  
  
-   <span data-ttu-id="0f824-128">**一般**： 包含用戶端和服務所使用之 Customer 類型的共用程式庫。</span><span class="sxs-lookup"><span data-stu-id="0f824-128">**Common**: A shared library that contains the Customer type used by the client and service.</span></span>  
  
 <span data-ttu-id="0f824-129">當用戶端主控台應用程式執行時，用戶端會對服務發出要求，然後將相關的資訊從回應寫入至主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="0f824-129">As the Client console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="0f824-130">若要執行範例</span><span class="sxs-lookup"><span data-stu-id="0f824-130">To run the sample</span></span>  
  
1.  <span data-ttu-id="0f824-131">開啟「ASP.NET 快取整合範例」的方案。</span><span class="sxs-lookup"><span data-stu-id="0f824-131">Open the solution for the ASP.NET Caching Integration Sample.</span></span>  
  
2.  <span data-ttu-id="0f824-132">按下 CTRL+SHIFT+B 以建置方案。</span><span class="sxs-lookup"><span data-stu-id="0f824-132">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="0f824-133">如果**方案總管 中**視窗尚未開啟，請按 CTRL + W + S。</span><span class="sxs-lookup"><span data-stu-id="0f824-133">If the **Solution Explorer** window is not already open, press CTRL+W+S.</span></span>  
  
4.  <span data-ttu-id="0f824-134">從**方案總管 中**視窗中，以滑鼠右鍵按一下**服務**專案，然後選取**開始新執行個體**。</span><span class="sxs-lookup"><span data-stu-id="0f824-134">From the **Solution Explorer** window, right click the **Service** project and select **Start New Instance**.</span></span> <span data-ttu-id="0f824-135">這樣會啟動裝載服務的 ASP.NET 程式開發伺服器。</span><span class="sxs-lookup"><span data-stu-id="0f824-135">This launches the ASP.NET development server, which hosts the service.</span></span>  
  
5.  <span data-ttu-id="0f824-136">從**方案總管 中**視窗中，以滑鼠右鍵按一下**用戶端**專案，然後選取**開始新執行個體**。</span><span class="sxs-lookup"><span data-stu-id="0f824-136">From the **Solution Explorer** window, right click the **Client** project and select **Start New Instance**.</span></span>  
  
6.  <span data-ttu-id="0f824-137">用戶端主控台視窗隨即出現，並提供執行中服務的 URI，以及執行中服務之 HTML 說明頁的 URI。</span><span class="sxs-lookup"><span data-stu-id="0f824-137">The client console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span> <span data-ttu-id="0f824-138">您可以隨時在瀏覽器中輸入說明頁的 URI 來檢視 HTML 說明頁。</span><span class="sxs-lookup"><span data-stu-id="0f824-138">At any point in time you can view the HTML help page by typing the URI of the help page in a browser.</span></span>  
  
7.  <span data-ttu-id="0f824-139">當範例執行時，用戶端會寫入目前活動的狀態。</span><span class="sxs-lookup"><span data-stu-id="0f824-139">As the sample runs, the client writes the status of the current activity.</span></span>  
  
8.  <span data-ttu-id="0f824-140">按下任何按鍵可終止用戶端主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="0f824-140">Press any key to terminate the client console application.</span></span>  
  
9. <span data-ttu-id="0f824-141">按 SHIFT+F5 停止對服務偵錯。</span><span class="sxs-lookup"><span data-stu-id="0f824-141">Press SHIFT+F5 to stop debugging the service.</span></span>  
  
10. <span data-ttu-id="0f824-142">在 Windows 通知區域中，以滑鼠右鍵按一下 ASP.NET 程式開發伺服器圖示，然後選取**停止**。</span><span class="sxs-lookup"><span data-stu-id="0f824-142">In the Windows Notification Area, right click the ASP.NET development server icon and select **Stop**.</span></span>
