---
title: 從 Web 瀏覽器存取服務 (WCF 資料服務快速入門)
ms.date: 03/30/2017
ms.assetid: 5a6fa180-3094-4e6e-ba2b-8c80975d18d1
ms.openlocfilehash: ebeda2805f3393b298e43aa4dcc601298ce176f6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59330320"
---
# <a name="accessing-the-service-from-a-web-browser-wcf-data-services-quickstart"></a><span data-ttu-id="6a2d4-102">從 Web 瀏覽器存取服務 (WCF 資料服務快速入門)</span><span class="sxs-lookup"><span data-stu-id="6a2d4-102">Accessing the Service from a Web Browser (WCF Data Services Quickstart)</span></span>

<span data-ttu-id="6a2d4-103">這是在 WCF Data Services 快速入門的第二項工作。</span><span class="sxs-lookup"><span data-stu-id="6a2d4-103">This is the second task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="6a2d4-104">在這個工作中，您可以從 Visual Studio 啟動 WCF Data Services，並選擇性地停用 Web 瀏覽器中的摘要的讀取。</span><span class="sxs-lookup"><span data-stu-id="6a2d4-104">In this task, you start the WCF Data Services from Visual Studio and optionally disable feed reading in the Web browser.</span></span> <span data-ttu-id="6a2d4-105">您接著擷取服務定義文件，以及透過送出 HTTP GET 要求的網頁瀏覽器至公開的資源存取資料服務資源。</span><span class="sxs-lookup"><span data-stu-id="6a2d4-105">You then retrieve the service definition document as well as access data service resources by submitting HTTP GET requests through a Web browser to the exposed resources.</span></span>

> [!NOTE]
> <span data-ttu-id="6a2d4-106">根據預設，Visual Studio 會在您的電腦上自動指派連接埠號碼給 `localhost` URI。</span><span class="sxs-lookup"><span data-stu-id="6a2d4-106">By default, Visual Studio auto-assigns a port number to the `localhost` URI on your computer.</span></span> <span data-ttu-id="6a2d4-107">這項工作會在 URI 範例中使用連接埠號碼 `12345`。</span><span class="sxs-lookup"><span data-stu-id="6a2d4-107">This task uses the port number `12345` in the URI examples.</span></span> <span data-ttu-id="6a2d4-108">如需如何設定 Visual Studio 專案中的特定連接埠號碼的詳細資訊，請參閱[建立資料服務](../../../../docs/framework/data/wcf/creating-the-data-service.md)。</span><span class="sxs-lookup"><span data-stu-id="6a2d4-108">For more information about how to set a specific port number in your Visual Studio project see [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>

## <a name="to-request-the-default-service-document-by-using-internet-explorer"></a><span data-ttu-id="6a2d4-109">若要使用 Internet Explorer 要求預設服務文件</span><span class="sxs-lookup"><span data-stu-id="6a2d4-109">To request the default service document by using Internet Explorer</span></span>

1. <span data-ttu-id="6a2d4-110">在 Internet Explorer 中，從**工具**功能表上，選取**網際網路選項**，按一下 **內容**索引標籤上，按一下 **設定**，並清除**開啟摘要讀取檢視**。</span><span class="sxs-lookup"><span data-stu-id="6a2d4-110">In Internet Explorer, from the **Tools** menu, select **Internet Options**, click the **Content** tab, click **Settings**, and clear **Turn on feed viewing**.</span></span>

     <span data-ttu-id="6a2d4-111">這樣可以確保摘要讀取功能已停用。</span><span class="sxs-lookup"><span data-stu-id="6a2d4-111">This makes sure that feed reading is disabled.</span></span> <span data-ttu-id="6a2d4-112">如果未停用此功能，Web 瀏覽器會將傳回的 AtomPub 編碼文件視為 XML 摘要，而不會顯示原始的 XML 資料。</span><span class="sxs-lookup"><span data-stu-id="6a2d4-112">If you do not disable this functionality, then the Web browser will treat the returned AtomPub encoded document as an XML feed instead of displaying the raw XML data.</span></span>

    > [!NOTE]
    > <span data-ttu-id="6a2d4-113">如果您的瀏覽器無法將摘要顯示為原始的 XML 資料，您應該仍然可以將摘要檢視為頁面的原始程式碼。</span><span class="sxs-lookup"><span data-stu-id="6a2d4-113">If your browser cannot display the feed as raw XML data, you should still be able to view the feed as the source code for the page.</span></span>

2. <span data-ttu-id="6a2d4-114">在 Visual Studio 中按**F5**鍵開始偵錯應用程式。</span><span class="sxs-lookup"><span data-stu-id="6a2d4-114">In Visual Studio, press the **F5** key to start debugging the application.</span></span>

3. <span data-ttu-id="6a2d4-115">開啟本機電腦上的 Web 瀏覽器。</span><span class="sxs-lookup"><span data-stu-id="6a2d4-115">Open a Web browser on the local computer.</span></span> <span data-ttu-id="6a2d4-116">在位址列中輸入下列 URI：</span><span class="sxs-lookup"><span data-stu-id="6a2d4-116">In the address bar, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc
    ```

     <span data-ttu-id="6a2d4-117">這樣會傳回預設的服務文件，其中包含此資料服務所公開的實體集清單。</span><span class="sxs-lookup"><span data-stu-id="6a2d4-117">This returns the default service document, which contains a list of entity sets that are exposed by this data service.</span></span>

## <a name="to-access-entity-set-resources-from-a-web-browser"></a><span data-ttu-id="6a2d4-118">從 Web 瀏覽器存取實體集資源</span><span class="sxs-lookup"><span data-stu-id="6a2d4-118">To access entity set resources from a Web browser</span></span>

1. <span data-ttu-id="6a2d4-119">在 Web 瀏覽器的位址列中輸入下列 URI：</span><span class="sxs-lookup"><span data-stu-id="6a2d4-119">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers
    ```

     <span data-ttu-id="6a2d4-120">這樣會傳回 Northwind 範例資料庫中的所有客戶。</span><span class="sxs-lookup"><span data-stu-id="6a2d4-120">This returns a set of all customers in the Northwind sample database.</span></span>

2. <span data-ttu-id="6a2d4-121">在 Web 瀏覽器的位址列中輸入下列 URI：</span><span class="sxs-lookup"><span data-stu-id="6a2d4-121">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')
    ```

     <span data-ttu-id="6a2d4-122">這樣會傳回特定客戶 `ALFKI` 的實體執行個體。</span><span class="sxs-lookup"><span data-stu-id="6a2d4-122">This returns an entity instance for the specific customer, `ALFKI`.</span></span>

3. <span data-ttu-id="6a2d4-123">在 Web 瀏覽器的位址列中輸入下列 URI：</span><span class="sxs-lookup"><span data-stu-id="6a2d4-123">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders
    ```

     <span data-ttu-id="6a2d4-124">這樣會周遊客戶與訂單之間的關聯性，傳回特定客戶 `ALFKI` 的所有訂單。</span><span class="sxs-lookup"><span data-stu-id="6a2d4-124">This traverses the relationship between customers and orders to return a set of all orders for the specific customer `ALFKI`.</span></span>

4. <span data-ttu-id="6a2d4-125">在 Web 瀏覽器的位址列中輸入下列 URI：</span><span class="sxs-lookup"><span data-stu-id="6a2d4-125">In the address bar of your Web browser, enter the following URI:</span></span>

    ```
    http://localhost:12345/northwind.svc/Customers('ALFKI')/Orders?$filter=OrderID eq 10643
    ```

     <span data-ttu-id="6a2d4-126">這樣會篩選屬於特定客戶 `ALFKI` 的訂單，因此僅根據所提供的 `OrderID` 值傳回特定訂單。</span><span class="sxs-lookup"><span data-stu-id="6a2d4-126">This filters orders that belong to the specific customer `ALFKI` so that only a specific order is returned based on the supplied `OrderID` value.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6a2d4-127">後續步驟</span><span class="sxs-lookup"><span data-stu-id="6a2d4-127">Next Steps</span></span>

<span data-ttu-id="6a2d4-128">您已順利從 Web 瀏覽器中，且瀏覽器 HTTP GET 要求發出至指定的資源存取 WCF 資料服務。</span><span class="sxs-lookup"><span data-stu-id="6a2d4-128">You have successfully accessed the WCF Data Services from a Web browser, with the browser issuing HTTP GET requests to specified resources.</span></span> <span data-ttu-id="6a2d4-129">Web 瀏覽器可讓您輕鬆地實驗要求的定址語法並檢視結果。</span><span class="sxs-lookup"><span data-stu-id="6a2d4-129">A Web browser provides an easy way to experiment with the addressing syntax of requests and view the results.</span></span> <span data-ttu-id="6a2d4-130">不過，此方法通常並不適用於存取實際執行資料服務。</span><span class="sxs-lookup"><span data-stu-id="6a2d4-130">However, a production data service is not generally accessed by this method.</span></span> <span data-ttu-id="6a2d4-131">一般而言，應用程式會透過應用程式碼或指令碼語言與資料服務互動。</span><span class="sxs-lookup"><span data-stu-id="6a2d4-131">Typically, applications interact with the data service through application code or scripting languages.</span></span> <span data-ttu-id="6a2d4-132">接下來，您將建立使用用戶端程式庫的用戶端應用程式，將資料服務資源視為 Common Language Runtime (CLR) 物件來加以存取：</span><span class="sxs-lookup"><span data-stu-id="6a2d4-132">Next, you will create a client application that uses client libraries to access data service resources as if they were common language runtime (CLR) objects:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6a2d4-133">建立 .NET Framework 用戶端應用程式</span><span class="sxs-lookup"><span data-stu-id="6a2d4-133">Creating the .NET Framework Client Application</span></span>](../../../../docs/framework/data/wcf/creating-the-dotnet-client-application-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="6a2d4-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6a2d4-134">See also</span></span>

- [<span data-ttu-id="6a2d4-135">存取資料服務資源</span><span class="sxs-lookup"><span data-stu-id="6a2d4-135">Accessing Data Service Resources</span></span>](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)
