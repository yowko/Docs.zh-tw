---
title: SystemWebRouting 整合範例
ms.date: 03/30/2017
ms.assetid: f1c94802-95c4-49e4-b1e2-ee9dd126ff93
ms.openlocfilehash: 2f12d80085e3ac27dac8ce80b6bb09f69337bfd8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143950"
---
# <a name="systemwebrouting-integration-sample"></a><span data-ttu-id="adc7d-102">SystemWebRouting 整合範例</span><span class="sxs-lookup"><span data-stu-id="adc7d-102">SystemWebRouting Integration Sample</span></span>
<span data-ttu-id="adc7d-103">這個範例示範裝載層與 <xref:System.Web.Routing> 命名空間中的類別整合。</span><span class="sxs-lookup"><span data-stu-id="adc7d-103">This sample demonstrates the hosting layer’s integration with the classes in the <xref:System.Web.Routing> namespace.</span></span> <span data-ttu-id="adc7d-104"><xref:System.Web.Routing> 命名空間中的類別可讓應用程式使用不會直接回應實體資源的 URL。</span><span class="sxs-lookup"><span data-stu-id="adc7d-104">The classes in the <xref:System.Web.Routing> namespace allow an application to use URLs that do not directly correspond to a physical resource.</span></span> <span data-ttu-id="adc7d-105">使用 Web 路由允許開發人員為 HTTP 創建虛擬位址，然後映射回實際的 WCF 服務。</span><span class="sxs-lookup"><span data-stu-id="adc7d-105">Using Web routing allows the developer to create virtual addresses for HTTP that are then mapped back to actual WCF services.</span></span> <span data-ttu-id="adc7d-106">當 WCF 服務必須在不需要實體檔案或資源的情況下裝載，或是服務必須使用不包含 .html 或 .aspx 等檔案的 URL 存取時，這種方式會相當實用。</span><span class="sxs-lookup"><span data-stu-id="adc7d-106">This is useful when a WCF service must be hosted without requiring a physical file or resource, or when services must be accessed with URLs that do not contain files such as .html or .aspx.</span></span> <span data-ttu-id="adc7d-107">這個範例將示範如何使用 <xref:System.Web.Routing.RouteTable> 類別來建立虛擬 URI，以便對應至 global.asax 中所定義的執行中服務。</span><span class="sxs-lookup"><span data-stu-id="adc7d-107">This sample demonstrates how to utilize the <xref:System.Web.Routing.RouteTable> class to create virtual URIs that map to running services defined in global.asax.</span></span>

> [!NOTE]
> <span data-ttu-id="adc7d-108"><xref:System.Web.Routing> 命名空間中的類別只適用於透過 HTTP 裝載的服務。</span><span class="sxs-lookup"><span data-stu-id="adc7d-108">The classes in the <xref:System.Web.Routing> namespace only work for services hosted over HTTP.</span></span>  
  
<span data-ttu-id="adc7d-109">此示例使用 WCF 創建兩個 RSS`movies`源：一`channels`個源和一個源。</span><span class="sxs-lookup"><span data-stu-id="adc7d-109">This example uses WCF to create two RSS feeds: a `movies` feed and a `channels` feed.</span></span> <span data-ttu-id="adc7d-110">要啟動服務的 URL 不包含擴展，並且在從`Application_Start``Global`<xref:System.Web.HttpApplication>類派生的類的方法中註冊。</span><span class="sxs-lookup"><span data-stu-id="adc7d-110">The URLs to activate the services do not contain an extension and are registered in the `Application_Start` method of the `Global` class derived from the <xref:System.Web.HttpApplication> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="adc7d-111">此示例僅適用于 Internet 資訊服務 （IIS） 7.0 及更高版本，因為 IIS 6.0 使用不同的方法來支援無擴展 URL。</span><span class="sxs-lookup"><span data-stu-id="adc7d-111">This sample only works in Internet Information Services (IIS) 7.0 and later, as IIS 6.0 uses a different method for supporting extension-less URLs.</span></span>  

#### <a name="to-download-this-sample"></a><span data-ttu-id="adc7d-112">下載此示例</span><span class="sxs-lookup"><span data-stu-id="adc7d-112">To download this sample</span></span>
  
<span data-ttu-id="adc7d-113">此示例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="adc7d-113">This sample may already be installed on your computer.</span></span> <span data-ttu-id="adc7d-114">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="adc7d-114">Check for the following (default) directory before continuing.</span></span>  

`<InstallDrive>:\WF_WCF_Samples`  

 <span data-ttu-id="adc7d-115">如果此目錄不存在，請轉到[Windows 通信基礎 （WCF） 和 Windows 工作流基礎 （WF） 示例 .NET 框架 4](https://www.microsoft.com/download/details.aspx?id=21459)以下載[!INCLUDE[wf1](../../../../includes/wf1-md.md)]所有 Windows 通信基礎 （WCF） 和示例。</span><span class="sxs-lookup"><span data-stu-id="adc7d-115">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="adc7d-116">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="adc7d-116">This sample is located in the following directory.</span></span>  

`<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebRoutingIntegration`  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="adc7d-117">若要使用這個範例</span><span class="sxs-lookup"><span data-stu-id="adc7d-117">To use this sample</span></span>  
  
1. <span data-ttu-id="adc7d-118">使用視覺化工作室，打開 Web 路由集成.sln 檔。</span><span class="sxs-lookup"><span data-stu-id="adc7d-118">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="adc7d-119">若要執行方案並啟動 Web 程式開發伺服器，請按下 F5。</span><span class="sxs-lookup"><span data-stu-id="adc7d-119">To run the solution and start the Web development server, press F5.</span></span>  
  
     <span data-ttu-id="adc7d-120">範例的目錄清單隨即出現。</span><span class="sxs-lookup"><span data-stu-id="adc7d-120">A directory listing for the sample appears.</span></span> <span data-ttu-id="adc7d-121">請注意，沒有副檔名 .svc 的檔案。</span><span class="sxs-lookup"><span data-stu-id="adc7d-121">Note that there are no files with an .svc file extension.</span></span>  
  
3. <span data-ttu-id="adc7d-122">在網址列中，添加到`movies`URL 中，以便讀取`http://localhost:[port]/movies`並按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="adc7d-122">In the address bar, add `movies` to the URL, so that it reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="adc7d-123">影片摘要會出現在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="adc7d-123">The movies feed appears in the browser.</span></span>  
  
4. <span data-ttu-id="adc7d-124">在網址列中，添加到`channels`URL 中，以便讀取`http://localhost:[port]/channels`並按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="adc7d-124">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="adc7d-125">通道摘要會出現在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="adc7d-125">The channels feed appears in the browser.</span></span>  
  
5. <span data-ttu-id="adc7d-126">按 ALT+F4，關閉 Web 瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="adc7d-126">Close the Web browser, by pressing ALT+F4.</span></span>  
  
     <span data-ttu-id="adc7d-127">如果開發伺服器尚未退出，請按右鍵通知區域圖示並選擇 **"停止**"。</span><span class="sxs-lookup"><span data-stu-id="adc7d-127">If the development server has not exited, right-click the notification area icon and select **Stop**.</span></span>  
  
#### <a name="to-use-this-sample-when-hosted-in-iis"></a><span data-ttu-id="adc7d-128">若要在 IIS 中裝載時使用這個範例</span><span class="sxs-lookup"><span data-stu-id="adc7d-128">To use this sample when hosted in IIS</span></span>  
  
1. <span data-ttu-id="adc7d-129">使用視覺化工作室，打開 Web 路由集成.sln 檔。</span><span class="sxs-lookup"><span data-stu-id="adc7d-129">Using Visual Studio, open the WebRoutingIntegration.sln file.</span></span>  
  
2. <span data-ttu-id="adc7d-130">按下 CTRL+SHIFT+B 建置此專案。</span><span class="sxs-lookup"><span data-stu-id="adc7d-130">Build the project, by pressing CTRL+SHIFT+B.</span></span>  
  
3. <span data-ttu-id="adc7d-131">在 [Internet Information Services (IIS) 管理員] 中建立 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="adc7d-131">Create a Web application in Internet Information Services (IIS) Manager.</span></span>  
  
    1. <span data-ttu-id="adc7d-132">在 IIS 管理器中，按右鍵**預設網站**並選擇"**添加應用程式**"。</span><span class="sxs-lookup"><span data-stu-id="adc7d-132">In IIS Manager, right click the **Default Web Site** and select **Add an Application**.</span></span>  
  
    2. <span data-ttu-id="adc7d-133">對於**別名**，鍵入`WebRoutingIntegration`。</span><span class="sxs-lookup"><span data-stu-id="adc7d-133">For the **alias**, type in `WebRoutingIntegration`.</span></span>  
  
    3. <span data-ttu-id="adc7d-134">對於**實體路徑**，選擇專案中的服務資料夾。</span><span class="sxs-lookup"><span data-stu-id="adc7d-134">For the **Physical Path**, select the Service folder inside the project.</span></span>  
  
    4. <span data-ttu-id="adc7d-135">按下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="adc7d-135">Press **OK**.</span></span>  
  
4. <span data-ttu-id="adc7d-136">通過按右鍵 Web 應用程式並選擇 **"管理應用程式**"然後 **"流覽"** 來啟動應用程式。</span><span class="sxs-lookup"><span data-stu-id="adc7d-136">Start the application, by right-clicking the Web application and selecting **Manage Application** and then **Browse**.</span></span>  
  
5. <span data-ttu-id="adc7d-137">在網址列中，添加到`movies`URL 中，以便讀取`http://localhost:[port]/movies`並按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="adc7d-137">In the address bar, add `movies` to the URL, so that is reads `http://localhost:[port]/movies` and press ENTER.</span></span>  
  
     <span data-ttu-id="adc7d-138">影片摘要會出現在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="adc7d-138">The movies feed appears in the browser.</span></span>  
  
6. <span data-ttu-id="adc7d-139">在網址列中，添加到`channels`URL 中，以便讀取`http://localhost:[port]/channels`並按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="adc7d-139">In the address bar, add `channels` to the URL, so that is reads `http://localhost:[port]/channels` and press ENTER.</span></span>  
  
     <span data-ttu-id="adc7d-140">通道摘要會出現在瀏覽器中。</span><span class="sxs-lookup"><span data-stu-id="adc7d-140">The channels feed appears in the browser.</span></span>  
  
7. <span data-ttu-id="adc7d-141">按 ALT+F4，關閉 Web 瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="adc7d-141">Close the Web browser, by pressing ALT+F4.</span></span>  
  
 <span data-ttu-id="adc7d-142">這個範例將示範裝載層能夠使用 <xref:System.Web.Routing> 命名空間中的類別撰寫，以便路由傳送透過 HTTP 裝載之服務的要求。</span><span class="sxs-lookup"><span data-stu-id="adc7d-142">This sample demonstrates that the hosting layer is capable of composing with the classes in the <xref:System.Web.Routing> namespace for routing the requests of services hosted over HTTP.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="adc7d-143">如果預設應用程式池版本設置為版本 2，則必須將其更新為 .NET 框架 4。</span><span class="sxs-lookup"><span data-stu-id="adc7d-143">You must update the default application pool version to .NET Framework 4 if it’s set to version 2.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adc7d-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adc7d-144">See also</span></span>

- <span data-ttu-id="adc7d-145">[AppFabric 主控與持續性範例](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="adc7d-145">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
