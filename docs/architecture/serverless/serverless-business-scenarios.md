---
title: 無伺服器應用程式的範例商務案例和使用案例
description: 存取從影像處理到行動後端和 ETL 管線範圍的範例，以瞭解無伺服器的實際操作方法。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: cb761524976125c816aae925f0c369eb8c76e7de
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926474"
---
# <a name="serverless-business-scenarios-and-use-cases"></a><span data-ttu-id="7a20a-103">無伺服器商務情節和使用案例</span><span class="sxs-lookup"><span data-stu-id="7a20a-103">Serverless business scenarios and use cases</span></span>

<span data-ttu-id="7a20a-104">無伺服器應用程式有許多使用案例和情節。</span><span class="sxs-lookup"><span data-stu-id="7a20a-104">There are many use cases and scenarios for serverless applications.</span></span> <span data-ttu-id="7a20a-105">本章包含說明不同案例的範例。</span><span class="sxs-lookup"><span data-stu-id="7a20a-105">This chapter includes samples that illustrate the different scenarios.</span></span> <span data-ttu-id="7a20a-106">這些案例包括相關檔和公用原始程式碼存放庫的連結。</span><span class="sxs-lookup"><span data-stu-id="7a20a-106">The scenarios include links to related documentation and public source code repositories.</span></span> <span data-ttu-id="7a20a-107">本章中的範例可讓您開始建立自己的建築物和執行無伺服器解決方案。</span><span class="sxs-lookup"><span data-stu-id="7a20a-107">The samples in this chapter enable you to get started on your own building and implementing serverless solutions.</span></span>

## <a name="analyze-and-archive-images"></a><span data-ttu-id="7a20a-108">分析和封存映射</span><span class="sxs-lookup"><span data-stu-id="7a20a-108">Analyze and archive images</span></span>

<span data-ttu-id="7a20a-109">這個範例示範無伺服器事件（事件方格）、工作流程（邏輯應用程式）和程式碼（Azure Functions）。</span><span class="sxs-lookup"><span data-stu-id="7a20a-109">This sample demonstrates serverless events (Event Grid), workflows (Logic App), and code (Azure Functions).</span></span> <span data-ttu-id="7a20a-110">它也會示範如何與另一個資源整合，在此案例中認知服務用於影像分析。</span><span class="sxs-lookup"><span data-stu-id="7a20a-110">It also shows how to integrate with another resource, in this case Cognitive Services for image analysis.</span></span>

<span data-ttu-id="7a20a-111">主控台應用程式可讓您將連結傳遞至 web 上的 URL。</span><span class="sxs-lookup"><span data-stu-id="7a20a-111">A console application allows you to pass a link to a URL on the web.</span></span> <span data-ttu-id="7a20a-112">應用程式會將 URL 發佈為事件方格訊息。</span><span class="sxs-lookup"><span data-stu-id="7a20a-112">The app publishes the URL as an event grid message.</span></span> <span data-ttu-id="7a20a-113">以平行方式，無伺服器函式應用程式和邏輯應用程式會訂閱該訊息。</span><span class="sxs-lookup"><span data-stu-id="7a20a-113">In parallel, a serverless function app and a logic app subscribe to the message.</span></span> <span data-ttu-id="7a20a-114">無伺服器函數應用程式會將映射序列化至 blob 儲存體。</span><span class="sxs-lookup"><span data-stu-id="7a20a-114">The serverless function app serializes the image to blob storage.</span></span> <span data-ttu-id="7a20a-115">它也會將資訊儲存在 Azure 表格儲存體。</span><span class="sxs-lookup"><span data-stu-id="7a20a-115">It also stores information in Azure Table Storage.</span></span> <span data-ttu-id="7a20a-116">中繼資料會儲存原始的影像 URL 和 blob 映射的名稱。</span><span class="sxs-lookup"><span data-stu-id="7a20a-116">The metadata stores the original image URL and the name of the blob image.</span></span> <span data-ttu-id="7a20a-117">邏輯應用程式會與自訂視覺 API 互動，以分析影像並建立電腦產生的標題。</span><span class="sxs-lookup"><span data-stu-id="7a20a-117">The logic app interacts with the Custom Vision API to analyze the image and create a machine-generated caption.</span></span> <span data-ttu-id="7a20a-118">標題會儲存在中繼資料資料表中。</span><span class="sxs-lookup"><span data-stu-id="7a20a-118">The caption is stored in the metadata table.</span></span>

![分析和封存映射架構](./media/image-processing-example.png)

<span data-ttu-id="7a20a-120">個別的單一頁面應用程式（SPA）會呼叫無伺服器函式，以取得映射和中繼資料的清單。</span><span class="sxs-lookup"><span data-stu-id="7a20a-120">A separate single page application (SPA) calls a serverless function to get a list of images and metadata.</span></span> <span data-ttu-id="7a20a-121">針對每個映射，它會呼叫另一個函式，以從封存傳遞影像資料。</span><span class="sxs-lookup"><span data-stu-id="7a20a-121">For each image, it calls another function that delivers the image data from the archive.</span></span> <span data-ttu-id="7a20a-122">最終結果是具有自動字幕的資源庫。</span><span class="sxs-lookup"><span data-stu-id="7a20a-122">The final result is a gallery with automatic captions.</span></span>

![自動映射庫](./media/automated-image-gallery.png)

<span data-ttu-id="7a20a-124">您可以在這裡找到完整的存放庫和建立邏輯應用程式的指示：[事件格線粘附](https://github.com/JeremyLikness/Event-Grid-Glue)。</span><span class="sxs-lookup"><span data-stu-id="7a20a-124">The full repository and instructions to build the logic app are available here: [Event grid glue](https://github.com/JeremyLikness/Event-Grid-Glue).</span></span>

## <a name="cross-platform-mobile-client-using-xamarinforms-and-functions"></a><span data-ttu-id="7a20a-125">使用 Xamarin 的跨平臺行動用戶端。表單和函式</span><span class="sxs-lookup"><span data-stu-id="7a20a-125">Cross-platform mobile client using Xamarin.Forms and functions</span></span>

<span data-ttu-id="7a20a-126">請參閱如何在 Azure 入口網站中或 Visual Studio 中執行簡單的無伺服器 Azure 函式。</span><span class="sxs-lookup"><span data-stu-id="7a20a-126">See how to implement a simple serverless Azure Function in the Azure Web Portal or in Visual Studio.</span></span> <span data-ttu-id="7a20a-127">使用在 Android、iOS 和 Windows 上執行的 Xamarin 來建立用戶端。</span><span class="sxs-lookup"><span data-stu-id="7a20a-127">Build a client with Xamarin.Forms that runs on Android, iOS, and Windows.</span></span> <span data-ttu-id="7a20a-128">然後，應用程式會經過精簡，以使用 JavaScript 物件標記法（JSON）做為伺服器和行動用戶端之間的通訊媒介（具有無伺服器後端）。</span><span class="sxs-lookup"><span data-stu-id="7a20a-128">The application is then refined to use JavaScript Object Notation (JSON) as a communication medium between the server and the mobile clients with a serverless back end.</span></span>

<span data-ttu-id="7a20a-129">如需詳細資訊，請參閱[使用 Xamarin. Forms 用戶端執行簡單的 Azure 函數](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)</span><span class="sxs-lookup"><span data-stu-id="7a20a-129">For more information, see [Implementing a simple Azure Function with a Xamarin.Forms client](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)</span></span>

## <a name="generate-a-photo-mosaic-with-serverless-image-recognition"></a><span data-ttu-id="7a20a-130">使用無伺服器影像辨識產生相片馬賽克</span><span class="sxs-lookup"><span data-stu-id="7a20a-130">Generate a photo mosaic with serverless image recognition</span></span>

<span data-ttu-id="7a20a-131">此範例會使用 Azure Functions 和 Microsoft 認知服務自訂視覺服務，從輸入影像產生相片馬賽克。</span><span class="sxs-lookup"><span data-stu-id="7a20a-131">The sample uses Azure Functions and Microsoft Cognitive Services Custom Vision Service to generate a photo mosaic from an input image.</span></span> <span data-ttu-id="7a20a-132">模型已定型，可辨識影像。</span><span class="sxs-lookup"><span data-stu-id="7a20a-132">The model is trained to recognize images.</span></span> <span data-ttu-id="7a20a-133">上傳影像時，它會辨識影像，並使用 Bing 進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="7a20a-133">When an image is uploaded, it recognizes the image and searches with Bing.</span></span> <span data-ttu-id="7a20a-134">使用搜尋結果重新組合原始影像。</span><span class="sxs-lookup"><span data-stu-id="7a20a-134">The original image is recomposed using the search results.</span></span>

![奧蘭多眼相片和馬賽克](./media/orlando-eye-both.png)

<span data-ttu-id="7a20a-136">例如，您可以使用奧蘭多地標（例如佛羅里達眼）來定型您的模型。</span><span class="sxs-lookup"><span data-stu-id="7a20a-136">For example, you can train your model with Orlando landmarks, such as the Orlando Eye.</span></span> <span data-ttu-id="7a20a-137">自訂視覺會辨識奧蘭多眼的影像，而此函式會建立相片馬賽克，其中包含「奧蘭多眼」的 Bing 影像搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="7a20a-137">Custom Vision will recognize an image of the Orlando Eye, and the function will create a photo mosaic composed of Bing image search results for "Orlando Eye."</span></span>

<span data-ttu-id="7a20a-138">如需詳細資訊，請參閱[Azure Functions 相片馬賽克](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)產生器。</span><span class="sxs-lookup"><span data-stu-id="7a20a-138">For more information, see [Azure Functions photo mosaic generator](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/).</span></span>

## <a name="migrate-an-existing-application-to-the-cloud"></a><span data-ttu-id="7a20a-139">將現有的應用程式遷移至雲端</span><span class="sxs-lookup"><span data-stu-id="7a20a-139">Migrate an existing application to the cloud</span></span>

<span data-ttu-id="7a20a-140">如先前章節所討論，通常會採用多層式架構來裝載您在內部部署的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7a20a-140">As discussed in previous chapters, it's common to embrace an N-Tier architecture to host your application on-premises.</span></span> <span data-ttu-id="7a20a-141">雖然使用虛擬機器以「原樣」遷移資源是雲端最具風險的途徑，但許多公司選擇使用此機會來重構其應用程式。</span><span class="sxs-lookup"><span data-stu-id="7a20a-141">Although migrating resources "as is" using virtual machines is the least risky path to the cloud, many companies choose to use the opportunity to refactor their applications.</span></span> <span data-ttu-id="7a20a-142">幸好，重構不一定要有「全有或無」的成果。</span><span class="sxs-lookup"><span data-stu-id="7a20a-142">Fortunately, refactoring doesn't have to be an "all-or-nothing" effort.</span></span> <span data-ttu-id="7a20a-143">事實上，您可以遷移您的應用程式，然後將元件分次取代為雲端原生對應專案。</span><span class="sxs-lookup"><span data-stu-id="7a20a-143">In fact, it's possible to migrate your app then piecemeal replace components with cloud native counterparts.</span></span>

<span data-ttu-id="7a20a-144">應用程式會使用 Azure Functions 的 proxy 功能，啟用將端點從舊版內部部署程式碼重構至無伺服器端點。</span><span class="sxs-lookup"><span data-stu-id="7a20a-144">The application uses the proxies feature of Azure Functions to enable refactoring an endpoint from legacy on-premises code to a serverless endpoint.</span></span>

![遷移架構](./media/migration-architecture.png)

<span data-ttu-id="7a20a-146">Proxy 提供單一 API 端點，其會在將個別要求移至無伺服器函式時進行更新，以重新路由傳送它們。</span><span class="sxs-lookup"><span data-stu-id="7a20a-146">The proxy provides a single API endpoint that is updated to reroute individual requests as they're moved into serverless functions.</span></span>

<span data-ttu-id="7a20a-147">您可以觀看影片來逐步完成整個遷移：[使用無伺服器 Azure](https://channel9.msdn.com/Events/Connect/2017/E102)函式的隨即轉移。</span><span class="sxs-lookup"><span data-stu-id="7a20a-147">You can view a video that walks through the entire migration: [Lift and shift with serverless Azure functions](https://channel9.msdn.com/Events/Connect/2017/E102).</span></span> <span data-ttu-id="7a20a-148">存取範例程式碼：[攜帶您自己的應用程式](https://github.com/JeremyLikness/bring-own-app-connect-17)。</span><span class="sxs-lookup"><span data-stu-id="7a20a-148">Access the sample code: [Bring your own app](https://github.com/JeremyLikness/bring-own-app-connect-17).</span></span>

## <a name="parse-a-csv-file-and-insert-into-a-database"></a><span data-ttu-id="7a20a-149">剖析 CSV 檔案並插入資料庫</span><span class="sxs-lookup"><span data-stu-id="7a20a-149">Parse a CSV file and insert into a database</span></span>

<span data-ttu-id="7a20a-150">「解壓縮」、「轉換」和「載入」（ETL）是整合不同系統的常見商務功能。</span><span class="sxs-lookup"><span data-stu-id="7a20a-150">Extract, Transform, and Load (ETL) is a common business function that integrates different systems.</span></span> <span data-ttu-id="7a20a-151">傳統的方法通常會牽涉到設定專用的 FTP 伺服器，然後部署排程的工作來剖析檔案並加以轉譯，以供企業使用。</span><span class="sxs-lookup"><span data-stu-id="7a20a-151">Traditional approaches often involve setting up dedicated FTP servers then deploying scheduled jobs to parse files and translate them for business use.</span></span> <span data-ttu-id="7a20a-152">無伺服器架構可讓工作變得更容易，因為上傳檔案時會引發觸發程式。</span><span class="sxs-lookup"><span data-stu-id="7a20a-152">Serverless architecture makes the job easier because a trigger can fire when the file is uploaded.</span></span> <span data-ttu-id="7a20a-153">Azure Functions 透過其適用于特定問題的小型程式碼片段，來 esposito 著手處理 ETL 之類的工作。</span><span class="sxs-lookup"><span data-stu-id="7a20a-153">Azure Functions tackles tasks like ETL through its ideal composition of small pieces of code that focus on a specific problem.</span></span>

![顯示 csv 剖析進程的螢幕擷取畫面。](./media/serverless-business-scenarios/csv-parse-database-import.png)

<span data-ttu-id="7a20a-155">如需原始碼和實際操作實驗室，請參閱[CSV 匯入實驗室](https://github.com/JeremyLikness/azure-fn-file-process-hol)。</span><span class="sxs-lookup"><span data-stu-id="7a20a-155">For source code and a hands-on lab, see [CSV import lab](https://github.com/JeremyLikness/azure-fn-file-process-hol).</span></span>

## <a name="shorten-links-and-track-metrics"></a><span data-ttu-id="7a20a-156">縮短連結和追蹤計量</span><span class="sxs-lookup"><span data-stu-id="7a20a-156">Shorten links and track metrics</span></span>

<span data-ttu-id="7a20a-157">連結縮短工具原本有助於在短 twitter 文章中編碼 Url，以配合140字元的限制。</span><span class="sxs-lookup"><span data-stu-id="7a20a-157">Link shortening tools originally helped encode URLs in short twitter posts to accommodate the 140 character limit.</span></span> <span data-ttu-id="7a20a-158">它們已成長成包含數個用途，最常用來追蹤解說以進行分析。</span><span class="sxs-lookup"><span data-stu-id="7a20a-158">They've grown to encompass several uses, most commonly to track click-throughs for analytics.</span></span> <span data-ttu-id="7a20a-159">連結 shortener 案例是一個完全無伺服器的應用程式，可管理連結和報告計量。</span><span class="sxs-lookup"><span data-stu-id="7a20a-159">The link shortener scenario is an entirely serverless application that manages links and reports metrics.</span></span>

<span data-ttu-id="7a20a-160">Azure Functions 可用來提供單一頁面應用程式（SPA），讓您可以貼上長 URL 並產生簡短的 url。</span><span class="sxs-lookup"><span data-stu-id="7a20a-160">Azure Functions is used to serve a Single Page Application (SPA) that allows you to paste the long URL and generate short URLs.</span></span> <span data-ttu-id="7a20a-161">Url 會加上標籤，以追蹤行銷活動（主題）和媒體（例如，連結張貼的社交網路）等專案。</span><span class="sxs-lookup"><span data-stu-id="7a20a-161">The URLs are tagged to track things like campaigns (topics) and mediums (such as social networks that the links are posted to).</span></span> <span data-ttu-id="7a20a-162">簡短的程式碼會以金鑰的形式儲存在 Azure 表格儲存體中，並以完整的 URL 做為值。</span><span class="sxs-lookup"><span data-stu-id="7a20a-162">The short code is stored in Azure Table Storage as the key, with the long URL as the value.</span></span> <span data-ttu-id="7a20a-163">當您按一下 [簡短] 連結時，另一個函式會查閱完整的 URL、傳送重新導向，並將事件的相關資訊放在佇列上。</span><span class="sxs-lookup"><span data-stu-id="7a20a-163">When you click on the short link, another function looks up the long URL, sends a redirect, and places information about the event on a queue.</span></span> <span data-ttu-id="7a20a-164">另一個 Azure 函式會處理佇列，並將資訊放入 Azure Cosmos DB。</span><span class="sxs-lookup"><span data-stu-id="7a20a-164">Another Azure Function processes the queue and places the information into Azure Cosmos DB.</span></span>

![連結 shortener 架構](./media/link-shortener-architecture.png)

<span data-ttu-id="7a20a-166">接著，您可以建立 Power BI 儀表板，以收集所收集資料的深入解析。</span><span class="sxs-lookup"><span data-stu-id="7a20a-166">You can then create a Power BI dashboard to gather insights about the data collected.</span></span> <span data-ttu-id="7a20a-167">在後端，Application Insights 提供重要的計量。</span><span class="sxs-lookup"><span data-stu-id="7a20a-167">On the back end, Application Insights provides important metrics.</span></span> <span data-ttu-id="7a20a-168">遙測包含平均使用者重新導向所需的時間，以及存取 Azure 表格儲存體所需的時間。</span><span class="sxs-lookup"><span data-stu-id="7a20a-168">Telemetry includes how long it takes for the average user to redirect and how long it takes to access Azure Table Storage.</span></span>

![Power BI 範例](./media/power-bi-example.png)

<span data-ttu-id="7a20a-170">您可以在這裡取得完整連結 shortener 存放庫與指示：[無伺服器 URL shortener](https://github.com/jeremylikness/serverless-url-shortener)。</span><span class="sxs-lookup"><span data-stu-id="7a20a-170">The full link shortener repository with instructions is available here: [Serverless URL shortener](https://github.com/jeremylikness/serverless-url-shortener).</span></span> <span data-ttu-id="7a20a-171">您可以在這裡閱讀簡化版本的相關資訊：[幾分鐘內就能 Azure 儲存體無伺服器 .net 應用程式](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/)。</span><span class="sxs-lookup"><span data-stu-id="7a20a-171">You can read about a simplified version here: [Azure Storage for serverless .NET apps in minutes](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/).</span></span>

## <a name="verify-device-connectivity-using-a-ping"></a><span data-ttu-id="7a20a-172">使用 ping 來驗證裝置連線能力</span><span class="sxs-lookup"><span data-stu-id="7a20a-172">Verify device connectivity using a ping</span></span>

<span data-ttu-id="7a20a-173">此範例是由 Azure IoT 中樞和 Azure 函數所組成。</span><span class="sxs-lookup"><span data-stu-id="7a20a-173">The sample consists of an Azure IoT Hub and an Azure Function.</span></span> <span data-ttu-id="7a20a-174">IoT 中樞上的新訊息會觸發 Azure Function。</span><span class="sxs-lookup"><span data-stu-id="7a20a-174">A new message on the IoT Hub triggers the Azure Function.</span></span> <span data-ttu-id="7a20a-175">無伺服器程式碼會將相同的訊息內容傳回給傳送它的裝置。</span><span class="sxs-lookup"><span data-stu-id="7a20a-175">The serverless code sends the same message content back to the device that sent it.</span></span> <span data-ttu-id="7a20a-176">專案具有方案所需的所有程式碼和部署設定。</span><span class="sxs-lookup"><span data-stu-id="7a20a-176">The project has all the code and deployment configuration needed for the solution.</span></span>

<span data-ttu-id="7a20a-177">如需詳細資訊，請參閱[Azure IoT 中樞 ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)。</span><span class="sxs-lookup"><span data-stu-id="7a20a-177">For more information, see [Azure IoT Hub ping](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/).</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="7a20a-178">建議的資源</span><span class="sxs-lookup"><span data-stu-id="7a20a-178">Recommended resources</span></span>

* [<span data-ttu-id="7a20a-179">Azure Functions 相片馬賽克產生器</span><span class="sxs-lookup"><span data-stu-id="7a20a-179">Azure Functions photo mosaic generator</span></span>](https://azure.microsoft.com/resources/samples/functions-dotnet-photo-mosaic/)
* [<span data-ttu-id="7a20a-180">Azure IoT 中樞 ping</span><span class="sxs-lookup"><span data-stu-id="7a20a-180">Azure IoT Hub ping</span></span>](https://azure.microsoft.com/resources/samples/iot-hub-node-ping/)
* [<span data-ttu-id="7a20a-181">幾分鐘內無伺服器 .NET 應用程式的 Azure 儲存體</span><span class="sxs-lookup"><span data-stu-id="7a20a-181">Azure Storage for serverless .NET apps in minutes</span></span>](https://devblogs.microsoft.com/aspnet/azure-storage-for-serverless-net-apps-in-minutes/)
* [<span data-ttu-id="7a20a-182">攜帶您自己的應用程式</span><span class="sxs-lookup"><span data-stu-id="7a20a-182">Bring your own app</span></span>](https://github.com/JeremyLikness/bring-own-app-connect-17)
* [<span data-ttu-id="7a20a-183">CSV 匯入實驗室</span><span class="sxs-lookup"><span data-stu-id="7a20a-183">CSV import lab</span></span>](https://github.com/JeremyLikness/azure-fn-file-process-hol)
* [<span data-ttu-id="7a20a-184">事件方格粘附</span><span class="sxs-lookup"><span data-stu-id="7a20a-184">Event grid glue</span></span>](https://github.com/JeremyLikness/Event-Grid-Glue)
* [<span data-ttu-id="7a20a-185">使用 Xamarin. Forms 用戶端來執行簡單的 Azure 函數</span><span class="sxs-lookup"><span data-stu-id="7a20a-185">Implementing a simple Azure Function with a Xamarin.Forms client</span></span>](https://azure.microsoft.com/resources/samples/functions-xamarin-getting-started/)
* [<span data-ttu-id="7a20a-186">無伺服器 Azure 函式的隨即轉移</span><span class="sxs-lookup"><span data-stu-id="7a20a-186">Lift and shift with serverless Azure functions</span></span>](https://channel9.msdn.com/Events/Connect/2017/E102)
* [<span data-ttu-id="7a20a-187">無伺服器 URL shortener</span><span class="sxs-lookup"><span data-stu-id="7a20a-187">Serverless URL shortener</span></span>](https://github.com/jeremylikness/serverless-url-shortener)

>[!div class="step-by-step"]
><span data-ttu-id="7a20a-188">[上一頁](orchestration-patterns.md)
>[下一頁](serverless-conclusion.md)</span><span class="sxs-lookup"><span data-stu-id="7a20a-188">[Previous](orchestration-patterns.md)
[Next](serverless-conclusion.md)</span></span>
