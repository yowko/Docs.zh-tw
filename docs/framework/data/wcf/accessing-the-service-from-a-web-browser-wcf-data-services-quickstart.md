---
title: "從 Web 瀏覽器存取服務 (WCF 資料服務快速入門)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71beb254bf258da97207f14afca73cd68c6927ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a><span data-ttu-id="b8b9f-102">從 Web 瀏覽器存取服務 (WCF 資料服務快速入門)</span><span class="sxs-lookup"><span data-stu-id="b8b9f-102">Accessing the Service from a Web Browser (WCF Data Services Quickstart)</span></span>
<span data-ttu-id="b8b9f-103">在這個工作中，您將從 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 啟動 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]，並且選擇性停用 Web 瀏覽器中的摘要讀取功能。</span><span class="sxs-lookup"><span data-stu-id="b8b9f-103">In this task, you will start the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] from [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] and optionally disable feed reading in the Web browser.</span></span> <span data-ttu-id="b8b9f-104">然後會擷取服務定義文件，以及提交至公開的資源的網頁瀏覽器透過 HTTP GET 要求來存取資料服務資源。</span><span class="sxs-lookup"><span data-stu-id="b8b9f-104">You will then retrieve the service definition document as well as access data service resources by submitting HTTP GET requests through a Web browser to the exposed resources.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8b9f-105">根據預設，[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 會在您的電腦上自動指派通訊埠編號給 `localhost` URI。</span><span class="sxs-lookup"><span data-stu-id="b8b9f-105">By default, [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] auto-assigns a port number to the `localhost` URI on your computer.</span></span> <span data-ttu-id="b8b9f-106">這項工作會在 URI 範例中使用連接埠號碼 `12345`。</span><span class="sxs-lookup"><span data-stu-id="b8b9f-106">This task uses the port number `12345` in the URI examples.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="b8b9f-107">如何設定特定通訊埠編號，您[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]專案，請參閱[建立資料服務](../../../../docs/framework/data/wcf/creating-the-data-service.md)。</span><span class="sxs-lookup"><span data-stu-id="b8b9f-107"> how to set a specific port number in your [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] project see [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>  
  
### <a name="to-request-the-default-service-document-by-using-internet-explorer"></a><span data-ttu-id="b8b9f-108">若要使用 Internet Explorer 要求預設服務文件</span><span class="sxs-lookup"><span data-stu-id="b8b9f-108">To request the default service document by using Internet Explorer</span></span>  
  
1.  <span data-ttu-id="b8b9f-109">在 Internet Explorer 中，從**工具**功能表上，選取**網際網路選項**，按一下 **內容**索引標籤上，按一下 **設定**，並清除**開啟摘要讀取檢視**。</span><span class="sxs-lookup"><span data-stu-id="b8b9f-109">In Internet Explorer, from the **Tools** menu, select **Internet Options**, click the **Content** tab, click **Settings**, and clear **Turn on feed viewing**.</span></span>  
  
     <span data-ttu-id="b8b9f-110">這樣可以確保摘要讀取功能已停用。</span><span class="sxs-lookup"><span data-stu-id="b8b9f-110">This makes sure that feed reading is disabled.</span></span> <span data-ttu-id="b8b9f-111">如果未停用此功能，Web 瀏覽器會將傳回的 AtomPub 編碼文件視為 XML 摘要，而不會顯示原始的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="b8b9f-111">If you do not disable this functionality, then the Web browser will treat the returned AtomPub encoded document as an XML feed instead of displaying the raw XML data.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b8b9f-112">如果您的瀏覽器無法將摘要顯示為原始的 XML 資料，您應該仍然可以將摘要檢視為頁面的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="b8b9f-112">If your browser cannot display the feed as raw XML data, you should still be able to view the feed as the source code for the page.</span></span>  
  
2.  <span data-ttu-id="b8b9f-113">在 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] 中，按 F5 鍵開始偵錯應用程式。</span><span class="sxs-lookup"><span data-stu-id="b8b9f-113">In [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)], press the F5 key to start debugging the application.</span></span>  
  
3.  <span data-ttu-id="b8b9f-114">開啟本機電腦上的 Web 瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="b8b9f-114">Open a Web browser on the local computer.</span></span> <span data-ttu-id="b8b9f-115">在位址列中輸入下列 URI：</span><span class="sxs-lookup"><span data-stu-id="b8b9f-115">In the address bar, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc  
    ```  
  
     <span data-ttu-id="b8b9f-116">這樣會傳回預設的服務文件，其中包含此資料服務所公開的實體集清單。</span><span class="sxs-lookup"><span data-stu-id="b8b9f-116">This returns the default service document, which contains a list of entity sets that are exposed by this data service.</span></span>  
  
### <a name="to-access-entity-set-resources-from-a-web-browser"></a><span data-ttu-id="b8b9f-117">從 Web 瀏覽器存取實體集資源</span><span class="sxs-lookup"><span data-stu-id="b8b9f-117">To access entity set resources from a Web browser</span></span>  
  
1.  <span data-ttu-id="b8b9f-118">在 Web 瀏覽器的位址列中輸入下列 URI：</span><span class="sxs-lookup"><span data-stu-id="b8b9f-118">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers  
    ```  
  
     <span data-ttu-id="b8b9f-119">這樣會傳回 Northwind 範例資料庫中的所有客戶。</span><span class="sxs-lookup"><span data-stu-id="b8b9f-119">This returns a set of all customers in the Northwind sample database.</span></span>  
  
2.  <span data-ttu-id="b8b9f-120">在 Web 瀏覽器的位址列中輸入下列 URI：</span><span class="sxs-lookup"><span data-stu-id="b8b9f-120">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')  
    ```  
  
     <span data-ttu-id="b8b9f-121">這樣會傳回特定客戶 `ALFKI` 的實體執行個體。</span><span class="sxs-lookup"><span data-stu-id="b8b9f-121">This returns an entity instance for the specific customer, `ALFKI`.</span></span>  
  
3.  <span data-ttu-id="b8b9f-122">在 Web 瀏覽器的位址列中輸入下列 URI：</span><span class="sxs-lookup"><span data-stu-id="b8b9f-122">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders  
    ```  
  
     <span data-ttu-id="b8b9f-123">這樣會周遊客戶與訂單之間的關聯性，傳回特定客戶 `ALFKI` 的所有訂單。</span><span class="sxs-lookup"><span data-stu-id="b8b9f-123">This traverses the relationship between customers and orders to return a set of all orders for the specific customer `ALFKI`.</span></span>  
  
4.  <span data-ttu-id="b8b9f-124">在 Web 瀏覽器的位址列中輸入下列 URI：</span><span class="sxs-lookup"><span data-stu-id="b8b9f-124">In the address bar of your Web browser, enter the following URI:</span></span>  
  
    ```  
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643  
    ```  
  
     <span data-ttu-id="b8b9f-125">這樣會篩選屬於特定客戶 `ALFKI` 的訂單，因此僅根據所提供的 `OrderID` 值傳回特定訂單。</span><span class="sxs-lookup"><span data-stu-id="b8b9f-125">This filters orders that belong to the specific customer `ALFKI` so that only a specific order is returned based on the supplied `OrderID` value.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="b8b9f-126">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b8b9f-126">Next Steps</span></span>  
 <span data-ttu-id="b8b9f-127">您已順利從 Web 瀏覽器存取 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]，且瀏覽器會將 HTTP GET 要求發出至指定的資源。</span><span class="sxs-lookup"><span data-stu-id="b8b9f-127">You have successfully accessed the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] from a Web browser, with the browser issuing HTTP GET requests to specified resources.</span></span> <span data-ttu-id="b8b9f-128">Web 瀏覽器可讓您輕鬆地實驗要求的定址語法並檢視結果。</span><span class="sxs-lookup"><span data-stu-id="b8b9f-128">A Web browser provides an easy way to experiment with the addressing syntax of requests and view the results.</span></span> <span data-ttu-id="b8b9f-129">不過，此方法通常並不適用於存取實際執行資料服務。</span><span class="sxs-lookup"><span data-stu-id="b8b9f-129">However, a production data service is not generally accessed by this method.</span></span> <span data-ttu-id="b8b9f-130">一般而言，應用程式會透過應用程式碼或指令碼語言與資料服務互動。</span><span class="sxs-lookup"><span data-stu-id="b8b9f-130">Typically, applications interact with the data service through application code or scripting languages.</span></span> <span data-ttu-id="b8b9f-131">接下來，您將建立使用用戶端程式庫的用戶端應用程式，將資料服務資源視為 Common Language Runtime (CLR) 物件來加以存取：</span><span class="sxs-lookup"><span data-stu-id="b8b9f-131">Next, you will create a client application that uses client libraries to access data service resources as if they were common language runtime (CLR) objects:</span></span>  
  
 [<span data-ttu-id="b8b9f-132">建立 .NET Framework 用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="b8b9f-132">Creating the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a><span data-ttu-id="b8b9f-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="b8b9f-133">See Also</span></span>  
 [<span data-ttu-id="b8b9f-134">存取資料服務資源</span><span class="sxs-lookup"><span data-stu-id="b8b9f-134">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
