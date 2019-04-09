---
title: SystemWebRouting 整合範例
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 244a7b7b73217086864b16945bc1521a3383aeac
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59147806"
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="44bb1-102">SystemWebRouting 整合範例</span><span class="sxs-lookup"><span data-stu-id="44bb1-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="44bb1-103">這個範例示範裝載層與 <xref:System.Web.Routing> 命名空間中的類別整合。</span><span class="sxs-lookup"><span data-stu-id="44bb1-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="44bb1-104"><xref:System.Web.Routing> 命名空間中的類別可讓應用程式使用不會直接回應實體資源的 URL。</span><span class="sxs-lookup"><span data-stu-id="44bb1-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="44bb1-105">使用 Web 路由可讓開發人員建立的虛擬位址會接著對應回實際的 WCF 服務的 http。</span><span class="sxs-lookup"><span data-stu-id="44bb1-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual WCF services.</span></span> <span data-ttu-id="44bb1-106">當 WCF 服務必須在不需要實體檔案或資源的情況下裝載，或是服務必須使用不包含 .html 或 .aspx 等檔案的 URL 存取時，這種方式會相當實用。</span><span class="sxs-lookup"><span data-stu-id="44bb1-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="44bb1-107">這個範例將示範如何使用 <xref:System.Web.Routing.RouteTable> 類別來建立虛擬 URI，以便對應至 global.asax 中所定義的執行中服務。</span><span class="sxs-lookup"><span data-stu-id="44bb1-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span> 

> [!NOTE]
>  <span data-ttu-id="44bb1-108"><xref:System.Web.Routing> 命名空間中的類別只適用於透過 HTTP 裝載的服務。</span><span class="sxs-lookup"><span data-stu-id="44bb1-108">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
<span data-ttu-id="44bb1-109">此範例會使用 WCF 來建立兩個 RSS 摘要：`movies`摘要和`channels`摘要。</span><span class="sxs-lookup"><span data-stu-id="44bb1-109">This example uses WCF to create two RSS feeds: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="44bb1-110">啟動服務的 Url 不包含延伸模組，在中註冊`Application_Start`方法`Global`類別衍生自<xref:System.Web.HttpApplication>類別。</span><span class="sxs-lookup"><span data-stu-id="44bb1-110">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44bb1-111">此範例僅適用於 Internet Information Services (IIS) 7.0 中，並更新版本，與 IIS 6.0 使用不同的方法支援無副檔名 Url。</span><span class="sxs-lookup"><span data-stu-id="44bb1-111">This sample only works in Internet Information Services (IIS) 7.0 and later, as IIS 6.0 uses a different method for supporting extension-less URLs.</span></span>  

#### <a name="to-download-this-sample"></a><span data-ttu-id="44bb1-112">若要下載此範例</span><span class="sxs-lookup"><span data-stu-id="44bb1-112">To download this sample</span></span>
  
<span data-ttu-id="44bb1-113">此範例可能已經安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="44bb1-113">This sample may already be installed on your computer.</span></span> <span data-ttu-id="44bb1-114">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="44bb1-114">Check for the following (default) directory before continuing.</span></span>  
   
`<InstallDrive>:\WF_WCF_Samples`  
   
 <span data-ttu-id="44bb1-115">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="44bb1-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="44bb1-116">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="44bb1-116">This sample is located in the following directory.</span></span>  
   
`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="44bb1-117">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="44bb1-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="44bb1-118">使用 Visual Studio，開啟 WebRoutingIntegration.sln 檔案。</span><span class="sxs-lookup"><span data-stu-id="44bb1-118">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="44bb1-119">若要執行方案並啟動 Web 程式開發伺服器，請按下 F5。</span><span class="sxs-lookup"><span data-stu-id="44bb1-119">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="44bb1-120">範例的目錄清單隨即出現。</span><span class="sxs-lookup"><span data-stu-id="44bb1-120">A directory listing for the sample appears.</span></span> <span data-ttu-id="44bb1-121">請注意，沒有副檔名 .svc 的檔案。</span><span class="sxs-lookup"><span data-stu-id="44bb1-121">Note that there are no files with an .svc file extension.</span></span>  
  
3.  <span data-ttu-id="44bb1-122">在 [網址] 列中，加入`movies`url，使其讀`http://localhost:[port]/movies`按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="44bb1-122">In the address bar, add `movies` to the URL, so that it reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="44bb1-123">影片摘要會出現在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="44bb1-123">The movies feed appears in the browser.</span></span>  
  
4.  <span data-ttu-id="44bb1-124">在 [網址] 列中，加入`channels`url，這就是讀取`http://localhost:[port]/channels`按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="44bb1-124">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="44bb1-125">通道摘要會出現在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="44bb1-125">The channels feed appears in the browser.</span></span>  
  
5.  <span data-ttu-id="44bb1-126">按 ALT+F4，關閉 Web 瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="44bb1-126">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="44bb1-127">如果程式開發伺服器尚未結束，以滑鼠右鍵按一下通知區域圖示，然後選取**停止**。</span><span class="sxs-lookup"><span data-stu-id="44bb1-127">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="44bb1-128">若要在 IIS 中裝載時使用這個範例</span><span class="sxs-lookup"><span data-stu-id="44bb1-128">To use this sample when hosted in IIS</span></span>  
  
1.  <span data-ttu-id="44bb1-129">使用 Visual Studio，開啟 WebRoutingIntegration.sln 檔案。</span><span class="sxs-lookup"><span data-stu-id="44bb1-129">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="44bb1-130">按下 CTRL+SHIFT+B 建置此專案。</span><span class="sxs-lookup"><span data-stu-id="44bb1-130">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="44bb1-131">在 [Internet Information Services (IIS) 管理員] 中建立 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="44bb1-131">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1.  <span data-ttu-id="44bb1-132">在 [IIS 管理員] 中，以滑鼠右鍵按一下**Default Web Site** ，然後選取**新增應用程式**。</span><span class="sxs-lookup"><span data-stu-id="44bb1-132">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2.  <span data-ttu-id="44bb1-133">針對**別名**，輸入`WebRoutingIntegration`。</span><span class="sxs-lookup"><span data-stu-id="44bb1-133">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3.  <span data-ttu-id="44bb1-134">針對**實體路徑**，選取專案內的 [服務] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="44bb1-134">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4.  <span data-ttu-id="44bb1-135">按 [確定]。</span><span class="sxs-lookup"><span data-stu-id="44bb1-135">Press **OK**.</span></span>  
  
4.  <span data-ttu-id="44bb1-136">啟動應用程式，以滑鼠右鍵按一下 Web 應用程式，然後選取**管理的應用程式**，然後**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="44bb1-136">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5.  <span data-ttu-id="44bb1-137">在 [網址] 列中，加入`movies`url，這就是讀取`http://localhost:[port]/movies`按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="44bb1-137">In the address bar, add `movies` to the URL, so that is reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="44bb1-138">影片摘要會出現在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="44bb1-138">The movies feed appears in the browser.</span></span>  
  
6.  <span data-ttu-id="44bb1-139">在 [網址] 列中，加入`channels`url，這就是讀取`http://localhost:[port]/channels`按 ENTER 鍵。</span><span class="sxs-lookup"><span data-stu-id="44bb1-139">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="44bb1-140">通道摘要會出現在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="44bb1-140">The channels feed appears in the browser.</span></span>  
  
7.  <span data-ttu-id="44bb1-141">按 ALT+F4，關閉 Web 瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="44bb1-141">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="44bb1-142">這個範例將示範裝載層能夠使用 <xref:System.Web.Routing> 命名空間中的類別撰寫，以便路由傳送透過 HTTP 裝載之服務的要求。</span><span class="sxs-lookup"><span data-stu-id="44bb1-142">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44bb1-143">您必須更新預設應用程式集區版本[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]如果設定為 第 2 版。</span><span class="sxs-lookup"><span data-stu-id="44bb1-143">You must update the default application pool version to [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44bb1-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44bb1-144">See also</span></span>

- [<span data-ttu-id="44bb1-145">AppFabric 主控與持續性範例</span><span class="sxs-lookup"><span data-stu-id="44bb1-145">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
