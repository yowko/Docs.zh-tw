---
title: "SystemWebRouting 整合範例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1718ea9c6ea1e029b66955e88fd54e20db1a3527
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="b7f19-102">SystemWebRouting 整合範例</span><span class="sxs-lookup"><span data-stu-id="b7f19-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="b7f19-103">這個範例示範裝載層與 <xref:System.Web.Routing> 命名空間中的類別整合。</span><span class="sxs-lookup"><span data-stu-id="b7f19-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="b7f19-104"><xref:System.Web.Routing> 命名空間中的類別可讓應用程式使用不會直接回應實體資源的 URL。</span><span class="sxs-lookup"><span data-stu-id="b7f19-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="b7f19-105">使用 Web 路由可讓開發人員建立 HTTP 的虛擬位址，並且接著對應回實體 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務。</span><span class="sxs-lookup"><span data-stu-id="b7f19-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services.</span></span> <span data-ttu-id="b7f19-106">當 WCF 服務必須在不需要實體檔案或資源的情況下裝載，或是服務必須使用不包含 .html 或 .aspx 等檔案的 URL 存取時，這種方式會相當實用。</span><span class="sxs-lookup"><span data-stu-id="b7f19-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="b7f19-107">這個範例將示範如何使用 <xref:System.Web.Routing.RouteTable> 類別來建立虛擬 URI，以便對應至 global.asax 中所定義的執行中服務。</span><span class="sxs-lookup"><span data-stu-id="b7f19-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span> <span data-ttu-id="b7f19-108">在這個範例中，有兩個使用 WCF 建立的 RSS 摘要：`movies` 摘要和 `channels` 摘要。</span><span class="sxs-lookup"><span data-stu-id="b7f19-108">For this example, there are two RSS feeds created using WCF: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="b7f19-109">啟動服務的 Url 不包含副檔名且已登錄在`Application_Start`方法`Global`類別衍生自<xref:System.Web.HttpApplication.Application_Start>類別。</span><span class="sxs-lookup"><span data-stu-id="b7f19-109">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication.Application_Start> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7f19-110"><xref:System.Web.Routing> 命名空間中的類別只適用於透過 HTTP 裝載的服務。</span><span class="sxs-lookup"><span data-stu-id="b7f19-110">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7f19-111">這個範例僅適用於 [!INCLUDE[iisver](../../../../includes/iisver-md.md)]，因為 [!INCLUDE[iis60](../../../../includes/iis60-md.md)] 使用不同的方法支援無副檔名 URL。</span><span class="sxs-lookup"><span data-stu-id="b7f19-111">This sample only works in [!INCLUDE[iisver](../../../../includes/iisver-md.md)], as [!INCLUDE[iis60](../../../../includes/iis60-md.md)] uses a different method for supporting extension-less URLs.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b7f19-112">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="b7f19-112">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b7f19-113">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="b7f19-113">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b7f19-114">如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。</span><span class="sxs-lookup"><span data-stu-id="b7f19-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b7f19-115">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="b7f19-115">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="b7f19-116">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="b7f19-116">To use this sample</span></span>  
  
1.  <span data-ttu-id="b7f19-117">使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 WebRoutingIntegration.sln 檔案。</span><span class="sxs-lookup"><span data-stu-id="b7f19-117">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="b7f19-118">若要執行方案並啟動 Web 程式開發伺服器，請按下 F5。</span><span class="sxs-lookup"><span data-stu-id="b7f19-118">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="b7f19-119">範例的目錄清單隨即出現。</span><span class="sxs-lookup"><span data-stu-id="b7f19-119">A directory listing for the sample appears.</span></span> <span data-ttu-id="b7f19-120">請注意，沒有副檔名 .svc 的檔案。</span><span class="sxs-lookup"><span data-stu-id="b7f19-120">Note that there are no files with an .svc file extension.</span></span>  
  
3.  <span data-ttu-id="b7f19-121">在位址列中，將 `movies` 加入至 URL 成為 http://localhost:[port]/movies，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="b7f19-121">In the address bar, add `movies` to the URL, so that is reads http://localhost:[port]/movies and press ENTER.</span></span>  
  
     <span data-ttu-id="b7f19-122">影片摘要會出現在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="b7f19-122">The movies feed appears in the browser.</span></span>  
  
4.  <span data-ttu-id="b7f19-123">在位址列中，將 `channels` 加入至 URL 成為 http://localhost:[port]/channels，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="b7f19-123">In the address bar, add `channels` to the URL, so that is reads http://localhost:[port]/channels and press ENTER.</span></span>  
  
     <span data-ttu-id="b7f19-124">通道摘要會出現在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="b7f19-124">The channels feed appears in the browser.</span></span>  
  
5.  <span data-ttu-id="b7f19-125">按 ALT+F4，關閉 Web 瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="b7f19-125">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="b7f19-126">如果尚未結束程式開發伺服器，以滑鼠右鍵按一下通知區域圖示，然後選取**停止**。</span><span class="sxs-lookup"><span data-stu-id="b7f19-126">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="b7f19-127">若要在 IIS 中裝載時使用這個範例</span><span class="sxs-lookup"><span data-stu-id="b7f19-127">To use this sample when hosted in IIS</span></span>  
  
1.  <span data-ttu-id="b7f19-128">使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 WebRoutingIntegration.sln 檔案。</span><span class="sxs-lookup"><span data-stu-id="b7f19-128">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the WebRoutingIntegration.sln file.</span></span>  
  
2.  <span data-ttu-id="b7f19-129">按下 CTRL+SHIFT+B 建置此專案。</span><span class="sxs-lookup"><span data-stu-id="b7f19-129">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="b7f19-130">在 [Internet Information Services (IIS) 管理員] 中建立 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="b7f19-130">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1.  <span data-ttu-id="b7f19-131">在 [IIS 管理員] 中，以滑鼠右鍵按一下**Default Web Site**選取**新增應用程式**。</span><span class="sxs-lookup"><span data-stu-id="b7f19-131">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2.  <span data-ttu-id="b7f19-132">如**別名**，輸入`WebRoutingIntegration`。</span><span class="sxs-lookup"><span data-stu-id="b7f19-132">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3.  <span data-ttu-id="b7f19-133">如**實體路徑**，選取專案內的 [服務] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="b7f19-133">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4.  <span data-ttu-id="b7f19-134">Press **OK**.</span><span class="sxs-lookup"><span data-stu-id="b7f19-134">Press **OK**.</span></span>  
  
4.  <span data-ttu-id="b7f19-135">啟動應用程式，以滑鼠右鍵按一下 Web 應用程式，然後選取**管理應用程式**然後**瀏覽**。</span><span class="sxs-lookup"><span data-stu-id="b7f19-135">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5.  <span data-ttu-id="b7f19-136">在位址列中，將 `movies` 加入至 URL 成為 http://localhost:[port]/movies，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="b7f19-136">In the address bar, add `movies` to the URL, so that is reads http://localhost:[port]/movies and press ENTER.</span></span>  
  
     <span data-ttu-id="b7f19-137">影片摘要會出現在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="b7f19-137">The movies feed appears in the browser.</span></span>  
  
6.  <span data-ttu-id="b7f19-138">在位址列中，將 `channels` 加入至 URL 成為 http://localhost:[port]/channels，然後按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="b7f19-138">In the address bar, add `channels` to the URL, so that is reads http://localhost:[port]/channels and press ENTER.</span></span>  
  
     <span data-ttu-id="b7f19-139">通道摘要會出現在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="b7f19-139">The channels feed appears in the browser.</span></span>  
  
7.  <span data-ttu-id="b7f19-140">按 ALT+F4，關閉 Web 瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="b7f19-140">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="b7f19-141">這個範例將示範裝載層能夠使用 <xref:System.Web.Routing> 命名空間中的類別撰寫，以便路由傳送透過 HTTP 裝載之服務的要求。</span><span class="sxs-lookup"><span data-stu-id="b7f19-141">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b7f19-142">如果預設應用程式集區的版本設定為第 2 版，請將版本更新為 [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="b7f19-142">Please update the default application pool version to [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7f19-143">請參閱</span><span class="sxs-lookup"><span data-stu-id="b7f19-143">See Also</span></span>  
 [<span data-ttu-id="b7f19-144">AppFabric 主控與持續性範例</span><span class="sxs-lookup"><span data-stu-id="b7f19-144">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
