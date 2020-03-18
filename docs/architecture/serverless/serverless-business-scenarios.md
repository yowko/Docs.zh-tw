---
title: 無伺服器應用的業務方案和用例示例
description: 通過訪問從映射處理到移動後端和 ETL 管道的樣本，通過動手方法學習無伺服器。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 5f0d7a4c5cd736d1168ec76c1c0ea19627505f15
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76787886"
---
# <a name="serverless-business-scenarios-and-use-cases"></a><span data-ttu-id="f9b76-103">無伺服器商務情節和使用案例</span><span class="sxs-lookup"><span data-stu-id="f9b76-103">Serverless business scenarios and use cases</span></span>

<span data-ttu-id="f9b76-104">對於無伺服器應用程式，有許多用例和方案。</span><span class="sxs-lookup"><span data-stu-id="f9b76-104">There are many use cases and scenarios for serverless applications.</span></span> <span data-ttu-id="f9b76-105">本章包括說明不同方案的示例。</span><span class="sxs-lookup"><span data-stu-id="f9b76-105">This chapter includes samples that illustrate the different scenarios.</span></span> <span data-ttu-id="f9b76-106">這些方案包括指向相關文檔和公共原始程式碼存儲庫的連結。</span><span class="sxs-lookup"><span data-stu-id="f9b76-106">The scenarios include links to related documentation and public source code repositories.</span></span> <span data-ttu-id="f9b76-107">本章中的示例使您能夠開始構建和實現無伺服器解決方案。</span><span class="sxs-lookup"><span data-stu-id="f9b76-107">The samples in this chapter enable you to get started on your own building and implementing serverless solutions.</span></span>

## <a name="analyze-and-archive-images"></a><span data-ttu-id="f9b76-108">分析和存檔圖像</span><span class="sxs-lookup"><span data-stu-id="f9b76-108">Analyze and archive images</span></span>

<span data-ttu-id="f9b76-109">此示例演示無伺服器事件（事件網格）、工作流（邏輯應用）和代碼（Azure 函數）。</span><span class="sxs-lookup"><span data-stu-id="f9b76-109">This sample demonstrates serverless events (Event Grid), workflows (Logic App), and code (Azure Functions).</span></span> <span data-ttu-id="f9b76-110">它還演示如何與其他資源集成，在這種情況下，用於圖像分析的認知服務。</span><span class="sxs-lookup"><span data-stu-id="f9b76-110">It also shows how to integrate with another resource, in this case Cognitive Services for image analysis.</span></span>

<span data-ttu-id="f9b76-111">主控台應用程式允許您傳遞指向 Web 上 URL 的連結。</span><span class="sxs-lookup"><span data-stu-id="f9b76-111">A console application allows you to pass a link to a URL on the web.</span></span> <span data-ttu-id="f9b76-112">應用將 URL 發佈為事件網格消息。</span><span class="sxs-lookup"><span data-stu-id="f9b76-112">The app publishes the URL as an event grid message.</span></span> <span data-ttu-id="f9b76-113">並行，無伺服器函數應用和邏輯應用訂閱消息。</span><span class="sxs-lookup"><span data-stu-id="f9b76-113">In parallel, a serverless function app and a logic app subscribe to the message.</span></span> <span data-ttu-id="f9b76-114">無伺服器函數應用將映射序列化到 blob 存儲。</span><span class="sxs-lookup"><span data-stu-id="f9b76-114">The serverless function app serializes the image to blob storage.</span></span> <span data-ttu-id="f9b76-115">它還在 Azure 表存儲中存儲資訊。</span><span class="sxs-lookup"><span data-stu-id="f9b76-115">It also stores information in Azure Table Storage.</span></span> <span data-ttu-id="f9b76-116">中繼資料存儲原始圖像 URL 和 blob 圖像的名稱。</span><span class="sxs-lookup"><span data-stu-id="f9b76-116">The metadata stores the original image URL and the name of the blob image.</span></span> <span data-ttu-id="f9b76-117">邏輯應用與自訂視覺 API 交互以分析圖像並創建電腦生成的字幕。</span><span class="sxs-lookup"><span data-stu-id="f9b76-117">The logic app interacts with the Custom Vision API to analyze the image and create a machine-generated caption.</span></span> <span data-ttu-id="f9b76-118">標題存儲在中繼資料表中。</span><span class="sxs-lookup"><span data-stu-id="f9b76-118">The caption is stored in the metadata table.</span></span>

![分析和存檔圖像體系結構](./media/image-processing-example.png)

<span data-ttu-id="f9b76-120">單獨的單頁應用程式 （SPA） 調用無伺服器函數來獲取圖像和中繼資料的清單。</span><span class="sxs-lookup"><span data-stu-id="f9b76-120">A separate single page application (SPA) calls a serverless function to get a list of images and metadata.</span></span> <span data-ttu-id="f9b76-121">對於每個映射，它調用另一個從存檔中傳遞圖像資料的函數。</span><span class="sxs-lookup"><span data-stu-id="f9b76-121">For each image, it calls another function that delivers the image data from the archive.</span></span> <span data-ttu-id="f9b76-122">最終結果是具有自動字幕的庫。</span><span class="sxs-lookup"><span data-stu-id="f9b76-122">The final result is a gallery with automatic captions.</span></span>

![自動圖像庫](./media/automated-image-gallery.png)

<span data-ttu-id="f9b76-124">完整的存儲庫和說明，以建立邏輯應用程式在這裡可用：[事件網格膠水](https://github.com/JeremyLikness/Event-Grid-Glue)。</span><span class="sxs-lookup"><span data-stu-id="f9b76-124">The full repository and instructions to build the logic app are available here: [Event grid glue](https://github.com/JeremyLikness/Event-Grid-Glue).</span></span>

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a><span data-ttu-id="f9b76-125">使用 Xamarin 的跨平臺移動用戶端。</span><span class="sxs-lookup"><span data-stu-id="f9b76-125">Cross-platform mobile client using Xamarin.Forms and functions</span></span>

<span data-ttu-id="f9b76-126">瞭解如何在 Azure Web 門戶或視覺化工作室中實現簡單的無伺服器 Azure 函數。</span><span class="sxs-lookup"><span data-stu-id="f9b76-126">See how to implement a simple serverless Azure Function in the Azure Web Portal or in Visual Studio.</span></span> <span data-ttu-id="f9b76-127">使用在 Android、iOS 和 Windows 上運行的 Xamarin.表單構建用戶端。</span><span class="sxs-lookup"><span data-stu-id="f9b76-127">Build a client with Xamarin.Forms that runs on Android, iOS, and Windows.</span></span> <span data-ttu-id="f9b76-128">然後，對應用程式進行優化，使用 JavaScript 物件標記法 （JSON） 作為伺服器和具有無伺服器後端的移動用戶端之間的通信介質。</span><span class="sxs-lookup"><span data-stu-id="f9b76-128">The application is then refined to use JavaScript Object Notation (JSON) as a communication medium between the server and the mobile clients with a serverless back end.</span></span>

<span data-ttu-id="f9b76-129">有關詳細資訊，請參閱使用[Xamarin.Forms 用戶端實現簡單的 Azure 函數](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)。</span><span class="sxs-lookup"><span data-stu-id="f9b76-129">For more information, see [Implementing a simple Azure Function with a Xamarin.Forms client](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/).</span></span>

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a><span data-ttu-id="f9b76-130">生成具有無伺服器圖像識別的照片鑲嵌</span><span class="sxs-lookup"><span data-stu-id="f9b76-130">Generate a photo mosaic with serverless image recognition</span></span>

<span data-ttu-id="f9b76-131">該示例使用 Azure 函數和 Microsoft 認知服務自訂視覺服務從輸入圖像生成照片鑲嵌。</span><span class="sxs-lookup"><span data-stu-id="f9b76-131">The sample uses Azure Functions and Microsoft Cognitive Services Custom Vision Service to generate a photo mosaic from an input image.</span></span> <span data-ttu-id="f9b76-132">模型經過培訓，可以識別圖像。</span><span class="sxs-lookup"><span data-stu-id="f9b76-132">The model is trained to recognize images.</span></span> <span data-ttu-id="f9b76-133">上傳圖像時，它會識別圖像，並使用必應搜索。</span><span class="sxs-lookup"><span data-stu-id="f9b76-133">When an image is uploaded, it recognizes the image and searches with Bing.</span></span> <span data-ttu-id="f9b76-134">使用搜尋結果重新組合原始圖像。</span><span class="sxs-lookup"><span data-stu-id="f9b76-134">The original image is recomposed using the search results.</span></span>

![奧蘭多眼照片和馬賽克](./media/orlando-eye-both.png)

<span data-ttu-id="f9b76-136">例如，您可以使用奧蘭多地標（如奧蘭多眼）訓練模型。</span><span class="sxs-lookup"><span data-stu-id="f9b76-136">For example, you can train your model with Orlando landmarks, such as the Orlando Eye.</span></span> <span data-ttu-id="f9b76-137">自訂視覺將識別奧蘭多眼的圖像，該功能將創建由必應圖像搜尋結果組成的"奧蘭多眼"照片馬賽克。</span><span class="sxs-lookup"><span data-stu-id="f9b76-137">Custom Vision will recognize an image of the Orlando Eye, and the function will create a photo mosaic composed of Bing image search results for "Orlando Eye."</span></span>

<span data-ttu-id="f9b76-138">有關詳細資訊，請參閱[Azure 函數照片鑲嵌產生器](https://github.com/Azure-Samples/functions-dotnet-photo-mosaic)。</span><span class="sxs-lookup"><span data-stu-id="f9b76-138">For more information, see [Azure Functions photo mosaic generator](https://github.com/Azure-Samples/functions-dotnet-photo-mosaic).</span></span>

## <a name="migrate-an-existing-application-to-the-cloud"></a><span data-ttu-id="f9b76-139">將現有應用程式遷移到雲</span><span class="sxs-lookup"><span data-stu-id="f9b76-139">Migrate an existing application to the cloud</span></span>

<span data-ttu-id="f9b76-140">如前幾章所述，通常採用 N-Tier 體系結構在本地託管應用程式。</span><span class="sxs-lookup"><span data-stu-id="f9b76-140">As discussed in previous chapters, it's common to embrace an N-Tier architecture to host your application on-premises.</span></span> <span data-ttu-id="f9b76-141">儘管使用虛擬機器遷移資源是雲風險最小的路徑，但許多公司選擇利用這個機會重構其應用程式。</span><span class="sxs-lookup"><span data-stu-id="f9b76-141">Although migrating resources "as is" using virtual machines is the least risky path to the cloud, many companies choose to use the opportunity to refactor their applications.</span></span> <span data-ttu-id="f9b76-142">幸運的是，重構不一定是"全無"的努力。</span><span class="sxs-lookup"><span data-stu-id="f9b76-142">Fortunately, refactoring doesn't have to be an "all-or-nothing" effort.</span></span> <span data-ttu-id="f9b76-143">事實上，可以遷移應用，然後零敲碎打地將元件替換為雲本機組件。</span><span class="sxs-lookup"><span data-stu-id="f9b76-143">In fact, it's possible to migrate your app then piecemeal replace components with cloud native counterparts.</span></span>

<span data-ttu-id="f9b76-144">應用程式使用 Azure 函數的代理功能來啟用重構終結點，從舊本地代碼到無伺服器終結點。</span><span class="sxs-lookup"><span data-stu-id="f9b76-144">The application uses the proxies feature of Azure Functions to enable refactoring an endpoint from legacy on-premises code to a serverless endpoint.</span></span>

![移轉架構](./media/migration-architecture.png)

<span data-ttu-id="f9b76-146">代理提供單個 API 終結點，該終結點在移動到無伺服器函數時可重新路由各個請求。</span><span class="sxs-lookup"><span data-stu-id="f9b76-146">The proxy provides a single API endpoint that is updated to reroute individual requests as they're moved into serverless functions.</span></span>

<span data-ttu-id="f9b76-147">您可以查看貫穿整個遷移的視頻：[使用無伺服器 Azure 函數提升和移動](https://channel9.msdn.com/Events/Connect/2017/E102)。</span><span class="sxs-lookup"><span data-stu-id="f9b76-147">You can view a video that walks through the entire migration: [Lift and shift with serverless Azure functions](https://channel9.msdn.com/Events/Connect/2017/E102).</span></span> <span data-ttu-id="f9b76-148">訪問示例代碼：[自取自己的應用](https://github.com/JeremyLikness/bring-own-app-connect-17)。</span><span class="sxs-lookup"><span data-stu-id="f9b76-148">Access the sample code: [Bring your own app](https://github.com/JeremyLikness/bring-own-app-connect-17).</span></span>

## <a name="parse-a-csv-file-and-insert-into-a-database"></a><span data-ttu-id="f9b76-149">分析 CSV 檔並插入資料庫</span><span class="sxs-lookup"><span data-stu-id="f9b76-149">Parse a CSV file and insert into a database</span></span>

<span data-ttu-id="f9b76-150">擷取、轉換和下載 （ETL） 是集成不同系統的常見業務功能。</span><span class="sxs-lookup"><span data-stu-id="f9b76-150">Extract, Transform, and Load (ETL) is a common business function that integrates different systems.</span></span> <span data-ttu-id="f9b76-151">傳統方法通常涉及設置專用 FTP 伺服器，然後部署計畫作業來分析檔並將其轉換為業務用途。</span><span class="sxs-lookup"><span data-stu-id="f9b76-151">Traditional approaches often involve setting up dedicated FTP servers then deploying scheduled jobs to parse files and translate them for business use.</span></span> <span data-ttu-id="f9b76-152">無伺服器體系結構使作業更容易，因為上載檔時可能會觸發觸發器。</span><span class="sxs-lookup"><span data-stu-id="f9b76-152">Serverless architecture makes the job easier because a trigger can fire when the file is uploaded.</span></span> <span data-ttu-id="f9b76-153">Azure 函數通過專注于特定問題的小型程式碼片段的理想組合來處理 ETL 等任務。</span><span class="sxs-lookup"><span data-stu-id="f9b76-153">Azure Functions tackles tasks like ETL through its ideal composition of small pieces of code that focus on a specific problem.</span></span>

![顯示 csv 解析過程的螢幕截圖。](./media/serverless-business-scenarios/csv-parse-database-import.png)

<span data-ttu-id="f9b76-155">有關原始程式碼和動手實驗，請參閱[CSV 導入實驗室](https://github.com/JeremyLikness/azure-fn-file-process-hol)。</span><span class="sxs-lookup"><span data-stu-id="f9b76-155">For source code and a hands-on lab, see [CSV import lab](https://github.com/JeremyLikness/azure-fn-file-process-hol).</span></span>

## <a name="shorten-links-and-track-metrics"></a><span data-ttu-id="f9b76-156">縮短連結並跟蹤指標</span><span class="sxs-lookup"><span data-stu-id="f9b76-156">Shorten links and track metrics</span></span>

<span data-ttu-id="f9b76-157">連結縮短工具最初説明編碼URL在短推特帖子，以適應140個字元的限制。</span><span class="sxs-lookup"><span data-stu-id="f9b76-157">Link shortening tools originally helped encode URLs in short twitter posts to accommodate the 140 character limit.</span></span> <span data-ttu-id="f9b76-158">它們已發展到包括多種用途，最常見的是跟蹤分析的點擊率。</span><span class="sxs-lookup"><span data-stu-id="f9b76-158">They've grown to encompass several uses, most commonly to track click-throughs for analytics.</span></span> <span data-ttu-id="f9b76-159">連結縮短器方案是一個完全無伺服器的應用程式，用於管理連結和報告指標。</span><span class="sxs-lookup"><span data-stu-id="f9b76-159">The link shortener scenario is an entirely serverless application that manages links and reports metrics.</span></span>

<span data-ttu-id="f9b76-160">Azure 函數用於為單頁應用程式 （SPA） 提供服務，該應用程式允許您粘貼長 URL 並生成短 URL。</span><span class="sxs-lookup"><span data-stu-id="f9b76-160">Azure Functions is used to serve a Single Page Application (SPA) that allows you to paste the long URL and generate short URLs.</span></span> <span data-ttu-id="f9b76-161">URL 被標記以跟蹤市場活動（主題）和媒介（如連結發佈到的社交網路）等內容。</span><span class="sxs-lookup"><span data-stu-id="f9b76-161">The URLs are tagged to track things like campaigns (topics) and mediums (such as social networks that the links are posted to).</span></span> <span data-ttu-id="f9b76-162">短代碼作為鍵存儲在 Azure 表存儲中，長 URL 作為值。</span><span class="sxs-lookup"><span data-stu-id="f9b76-162">The short code is stored in Azure Table Storage as the key, with the long URL as the value.</span></span> <span data-ttu-id="f9b76-163">按一下短連結時，另一個函數會查找長 URL，發送重定向，並將有關事件的資訊放在佇列中。</span><span class="sxs-lookup"><span data-stu-id="f9b76-163">When you click on the short link, another function looks up the long URL, sends a redirect, and places information about the event on a queue.</span></span> <span data-ttu-id="f9b76-164">另一個 Azure 函數處理佇列並將資訊放入 Azure Cosmos DB 中。</span><span class="sxs-lookup"><span data-stu-id="f9b76-164">Another Azure Function processes the queue and places the information into Azure Cosmos DB.</span></span>

![連結縮短器體系結構](./media/link-shortener-architecture.png)

<span data-ttu-id="f9b76-166">然後，您可以創建 Power BI 儀表板來收集有關收集的資料的見解。</span><span class="sxs-lookup"><span data-stu-id="f9b76-166">You can then create a Power BI dashboard to gather insights about the data collected.</span></span> <span data-ttu-id="f9b76-167">在後端，應用程式見解提供了重要的指標。</span><span class="sxs-lookup"><span data-stu-id="f9b76-167">On the back end, Application Insights provides important metrics.</span></span> <span data-ttu-id="f9b76-168">遙測包括普通使用者重定向所需的時間以及訪問 Azure 表存儲所需的時間。</span><span class="sxs-lookup"><span data-stu-id="f9b76-168">Telemetry includes how long it takes for the average user to redirect and how long it takes to access Azure Table Storage.</span></span>

![電源 BI 示例](./media/power-bi-example.png)

<span data-ttu-id="f9b76-170">完整的連結縮短器存儲庫與說明可在這裡：[無伺服器 URL 縮短器](https://github.com/jeremylikness/serverless-url-shortener).</span><span class="sxs-lookup"><span data-stu-id="f9b76-170">The full link shortener repository with instructions is available here: [Serverless URL shortener](https://github.com/jeremylikness/serverless-url-shortener).</span></span> <span data-ttu-id="f9b76-171">您可以在此處閱讀有關簡化版本[：Azure 存儲，用於無伺服器 .NET 應用，在幾分鐘內](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/)即可。</span><span class="sxs-lookup"><span data-stu-id="f9b76-171">You can read about a simplified version here: [Azure Storage for serverless .NET apps in minutes](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/).</span></span>

## <a name="verify-device-connectivity-using-a-ping"></a><span data-ttu-id="f9b76-172">使用 ping 驗證設備連接</span><span class="sxs-lookup"><span data-stu-id="f9b76-172">Verify device connectivity using a ping</span></span>

<span data-ttu-id="f9b76-173">該示例由 Azure IoT 中心和 Azure 函陣列成。</span><span class="sxs-lookup"><span data-stu-id="f9b76-173">The sample consists of an Azure IoT Hub and an Azure Function.</span></span> <span data-ttu-id="f9b76-174">IoT 中心上的新消息將觸發 Azure 函數。</span><span class="sxs-lookup"><span data-stu-id="f9b76-174">A new message on the IoT Hub triggers the Azure Function.</span></span> <span data-ttu-id="f9b76-175">無伺服器代碼將相同的消息內容發送回發送它的設備。</span><span class="sxs-lookup"><span data-stu-id="f9b76-175">The serverless code sends the same message content back to the device that sent it.</span></span> <span data-ttu-id="f9b76-176">專案具有解決方案所需的所有代碼和部署配置。</span><span class="sxs-lookup"><span data-stu-id="f9b76-176">The project has all the code and deployment configuration needed for the solution.</span></span>

<span data-ttu-id="f9b76-177">有關詳細資訊，請參閱[Azure IoT 中心 ping](https://github.com/Azure-Samples/iot-hub-node-ping)。</span><span class="sxs-lookup"><span data-stu-id="f9b76-177">For more information, see [Azure IoT Hub ping](https://github.com/Azure-Samples/iot-hub-node-ping).</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="f9b76-178">建議的資源</span><span class="sxs-lookup"><span data-stu-id="f9b76-178">Recommended resources</span></span>

- [<span data-ttu-id="f9b76-179">Azure 功能照片鑲嵌產生器</span><span class="sxs-lookup"><span data-stu-id="f9b76-179">Azure Functions photo mosaic generator</span></span>](https://github.com/Azure-Samples/functions-dotnet-photo-mosaic)
- [<span data-ttu-id="f9b76-180">Azure IoT 中樞 ping</span><span class="sxs-lookup"><span data-stu-id="f9b76-180">Azure IoT Hub ping</span></span>](https://github.com/Azure-Samples/iot-hub-node-ping)
- [<span data-ttu-id="f9b76-181">用於無伺服器 .NET 應用的 Azure 存儲，在幾分鐘內</span><span class="sxs-lookup"><span data-stu-id="f9b76-181">Azure Storage for serverless .NET apps in minutes</span></span>](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/)
- [<span data-ttu-id="f9b76-182">自帶應用</span><span class="sxs-lookup"><span data-stu-id="f9b76-182">Bring your own app</span></span>](https://github.com/JeremyLikness/bring-own-app-connect-17)
- [<span data-ttu-id="f9b76-183">CSV 導入實驗室</span><span class="sxs-lookup"><span data-stu-id="f9b76-183">CSV import lab</span></span>](https://github.com/JeremyLikness/azure-fn-file-process-hol)
- [<span data-ttu-id="f9b76-184">事件網格粘合</span><span class="sxs-lookup"><span data-stu-id="f9b76-184">Event grid glue</span></span>](https://github.com/JeremyLikness/Event-Grid-Glue)
- [<span data-ttu-id="f9b76-185">使用 Xamarin 實現簡單的 Azure 函數。</span><span class="sxs-lookup"><span data-stu-id="f9b76-185">Implementing a simple Azure Function with a Xamarin.Forms client</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)
- [<span data-ttu-id="f9b76-186">使用無伺服器 Azure 功能提升和移動</span><span class="sxs-lookup"><span data-stu-id="f9b76-186">Lift and shift with serverless Azure functions</span></span>](https://channel9.msdn.com/Events/Connect/2017/E102)
- [<span data-ttu-id="f9b76-187">無伺服器 URL 縮短器</span><span class="sxs-lookup"><span data-stu-id="f9b76-187">Serverless URL shortener</span></span>](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
><span data-ttu-id="f9b76-188">[上一個](orchestration-patterns.md)
>[下一個](serverless-conclusion.md)</span><span class="sxs-lookup"><span data-stu-id="f9b76-188">[Previous](orchestration-patterns.md)
[Next](serverless-conclusion.md)</span></span>
