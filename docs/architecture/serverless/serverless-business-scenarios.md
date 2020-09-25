---
title: 無伺服器應用程式的範例商務案例和使用案例
description: 存取從影像處理到行動支援和 ETL 管線的範例，以學習無伺服器的方法。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/17/2020
ms.openlocfilehash: df76b132579eb3a6d05ce38c94cb9fceb9281aef
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171607"
---
# <a name="serverless-business-scenarios-and-use-cases"></a><span data-ttu-id="a7670-103">無伺服器商務情節和使用案例</span><span class="sxs-lookup"><span data-stu-id="a7670-103">Serverless business scenarios and use cases</span></span>

<span data-ttu-id="a7670-104">無伺服器應用程式有許多使用案例和案例。</span><span class="sxs-lookup"><span data-stu-id="a7670-104">There are many use cases and scenarios for serverless applications.</span></span> <span data-ttu-id="a7670-105">本章包含說明不同案例的範例。</span><span class="sxs-lookup"><span data-stu-id="a7670-105">This chapter includes samples that illustrate the different scenarios.</span></span> <span data-ttu-id="a7670-106">這些案例包括相關檔和公用原始程式碼存放庫的連結。</span><span class="sxs-lookup"><span data-stu-id="a7670-106">The scenarios include links to related documentation and public source code repositories.</span></span> <span data-ttu-id="a7670-107">本章中的範例可讓您開始使用自己的組建和執行無伺服器解決方案。</span><span class="sxs-lookup"><span data-stu-id="a7670-107">The samples in this chapter enable you to get started on your own building and implementing serverless solutions.</span></span>

## <a name="big-data-processing"></a><span data-ttu-id="a7670-108">巨量資料處理</span><span class="sxs-lookup"><span data-stu-id="a7670-108">Big data processing</span></span>

![地圖/減少圖表](/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/media/mapreducearchitecture.png)

<span data-ttu-id="a7670-110">此範例會使用無伺服器，在大型資料集上進行對應/減少作業。</span><span class="sxs-lookup"><span data-stu-id="a7670-110">This example uses serverless to do a map/reduce operation on a big data set.</span></span> <span data-ttu-id="a7670-111">它會判斷2017中每天紐約每日出租車行程的平均速度。</span><span class="sxs-lookup"><span data-stu-id="a7670-111">It determines the average speed of New York Yellow taxi trips per day in 2017.</span></span>

[<span data-ttu-id="a7670-112">大型資料處理： Azure 上的無伺服器 MapReduce</span><span class="sxs-lookup"><span data-stu-id="a7670-112">Big Data Processing: Serverless MapReduce on Azure</span></span>](/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)

## <a name="create-serverless-applications-hands-on-lab"></a><span data-ttu-id="a7670-113">建立無伺服器應用程式：實際操作實驗室</span><span class="sxs-lookup"><span data-stu-id="a7670-113">Create serverless applications: hands-on lab</span></span>

<span data-ttu-id="a7670-114">了解如何使用函式來執行伺服器端邏輯，並建置無伺服器架構。</span><span class="sxs-lookup"><span data-stu-id="a7670-114">Learn how to use functions to execute server-side logic and build serverless architectures.</span></span>

- <span data-ttu-id="a7670-115">為您的企業選擇最佳的 Azure 服務</span><span class="sxs-lookup"><span data-stu-id="a7670-115">Choosing the best Azure service for your business</span></span>
- <span data-ttu-id="a7670-116">建立 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="a7670-116">Creating Azure Functions</span></span>
- <span data-ttu-id="a7670-117">使用觸發程序</span><span class="sxs-lookup"><span data-stu-id="a7670-117">Using triggers</span></span>
- <span data-ttu-id="a7670-118">連結函數</span><span class="sxs-lookup"><span data-stu-id="a7670-118">Chaining functions</span></span>
- <span data-ttu-id="a7670-119">長時間執行的工作流程</span><span class="sxs-lookup"><span data-stu-id="a7670-119">Long-running workflows</span></span>
- <span data-ttu-id="a7670-120">監視</span><span class="sxs-lookup"><span data-stu-id="a7670-120">Monitoring</span></span>
- <span data-ttu-id="a7670-121">開發、測試和部署</span><span class="sxs-lookup"><span data-stu-id="a7670-121">Development, testing, and deployment</span></span>

[<span data-ttu-id="a7670-122">建立無伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="a7670-122">Create serverless applications</span></span>](/learn/paths/create-serverless-applications/)

## <a name="customer-reviews"></a><span data-ttu-id="a7670-123">客戶評論</span><span class="sxs-lookup"><span data-stu-id="a7670-123">Customer reviews</span></span>

<span data-ttu-id="a7670-124">此範例示範 Visual Studio 中 c # 類別庫的新 Azure Functions 工具。</span><span class="sxs-lookup"><span data-stu-id="a7670-124">This sample showcases the new Azure Functions tooling for C# Class Libraries in Visual Studio.</span></span> <span data-ttu-id="a7670-125">建立網站，讓客戶提交儲存在 Azure 儲存體 blob 和 CosmosDB 中的產品評論。</span><span class="sxs-lookup"><span data-stu-id="a7670-125">Create a website where customers submit product reviews that are stored in Azure storage blobs and CosmosDB.</span></span> <span data-ttu-id="a7670-126">新增 Azure 函式，以使用 Azure 認知服務來執行客戶評論的自動審核。</span><span class="sxs-lookup"><span data-stu-id="a7670-126">Add an Azure Function to perform automated moderation of the customer reviews using Azure Cognitive Services.</span></span> <span data-ttu-id="a7670-127">使用 Azure 儲存體佇列來分離網站與函式。</span><span class="sxs-lookup"><span data-stu-id="a7670-127">Use an Azure storage queue to decouple the website from the function.</span></span>

[<span data-ttu-id="a7670-128">使用認知服務的客戶評論應用程式</span><span class="sxs-lookup"><span data-stu-id="a7670-128">Customer Reviews App with Cognitive Services</span></span>](/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)

## <a name="docker-linux-image-support"></a><span data-ttu-id="a7670-129">Docker Linux 映射支援</span><span class="sxs-lookup"><span data-stu-id="a7670-129">Docker Linux image support</span></span>

<span data-ttu-id="a7670-130">這個範例會示範如何建立， `Dockerfile` 以在 Linux Docker 容器上建立並執行 Azure Functions。</span><span class="sxs-lookup"><span data-stu-id="a7670-130">This sample demonstrates how to create a `Dockerfile` to build and run Azure Functions on a Linux Docker container.</span></span>

[<span data-ttu-id="a7670-131">Linux 上的 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="a7670-131">Azure Functions on Linux</span></span>](/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)

## <a name="file-processing-and-validation"></a><span data-ttu-id="a7670-132">檔案處理和驗證</span><span class="sxs-lookup"><span data-stu-id="a7670-132">File processing and validation</span></span>

<span data-ttu-id="a7670-133">此範例會剖析假想客戶的一組 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="a7670-133">This example parses a set of CSV files from hypothetical customers.</span></span> <span data-ttu-id="a7670-134">它可確保客戶「批次」所需的所有檔案都已就緒，然後驗證每個檔案的結構。</span><span class="sxs-lookup"><span data-stu-id="a7670-134">It ensures that all files required for a customer "batch" are ready, then validates the structure of each file.</span></span> <span data-ttu-id="a7670-135">使用 Azure Functions、Logic Apps 和 Durable Functions 會顯示不同的解決方案。</span><span class="sxs-lookup"><span data-stu-id="a7670-135">Different solutions are presented using Azure Functions, Logic Apps, and Durable Functions.</span></span>

[<span data-ttu-id="a7670-136">使用 Azure Functions、Logic Apps 和 Durable Functions 進行檔案處理和驗證</span><span class="sxs-lookup"><span data-stu-id="a7670-136">File processing and validation using Azure Functions, Logic Apps, and Durable Functions</span></span>](/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)

## <a name="game-data-visualization"></a><span data-ttu-id="a7670-137">遊戲資料視覺效果</span><span class="sxs-lookup"><span data-stu-id="a7670-137">Game data visualization</span></span>

![遊戲遙測](/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/media/points.png)

<span data-ttu-id="a7670-139">開發人員如何為其遊戲執行編輯器內資料視覺效果解決方案的範例。</span><span class="sxs-lookup"><span data-stu-id="a7670-139">An example of how a developer could implement an in-editor data visualization solution for their game.</span></span> <span data-ttu-id="a7670-140">事實上，Unreal Engine 4 外掛程式和 Unity 外掛程式是使用此範例作為其後端來開發。</span><span class="sxs-lookup"><span data-stu-id="a7670-140">In fact, an Unreal Engine 4 Plugin and Unity Plugin were developed using this sample as its backend.</span></span> <span data-ttu-id="a7670-141">服務元件與遊戲引擎無關。</span><span class="sxs-lookup"><span data-stu-id="a7670-141">The service component is game engine agnostic.</span></span>

[<span data-ttu-id="a7670-142">編輯器內遊戲遙測視覺效果</span><span class="sxs-lookup"><span data-stu-id="a7670-142">In-editor game telemetry visualization</span></span>](/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)

## <a name="graphql"></a><span data-ttu-id="a7670-143">GraphQL</span><span class="sxs-lookup"><span data-stu-id="a7670-143">GraphQL</span></span>

<span data-ttu-id="a7670-144">建立可公開 GraphQL API 的無伺服器函式。</span><span class="sxs-lookup"><span data-stu-id="a7670-144">Create a serverless function that exposes a GraphQL API.</span></span>

[<span data-ttu-id="a7670-145">適用于 GraphQL 的無伺服器函式</span><span class="sxs-lookup"><span data-stu-id="a7670-145">Serverless functions for GraphQL</span></span>](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)

## <a name="internet-of-things-iot-reliable-edge-relay"></a><span data-ttu-id="a7670-146">物聯網 (IoT) 可靠的邊緣轉送</span><span class="sxs-lookup"><span data-stu-id="a7670-146">Internet of Things (IoT) reliable edge relay</span></span>

![IoT 架構](/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/media/architecture.png)

<span data-ttu-id="a7670-148">此範例會執行新的通訊協定，以啟用來自 IoT 裝置的可靠上游通訊。</span><span class="sxs-lookup"><span data-stu-id="a7670-148">This sample implements a new communication protocol to enable reliable upstream communication from IoT devices.</span></span> <span data-ttu-id="a7670-149">它會將資料間距偵測和回填自動化。</span><span class="sxs-lookup"><span data-stu-id="a7670-149">It automates data gap detection and backfill.</span></span>

[<span data-ttu-id="a7670-150">IoT 可靠邊緣轉送</span><span class="sxs-lookup"><span data-stu-id="a7670-150">IoT Reliable Edge Relay</span></span>](/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)

## <a name="microservices-reference-architecture"></a><span data-ttu-id="a7670-151">微服務參考架構</span><span class="sxs-lookup"><span data-stu-id="a7670-151">Microservices reference architecture</span></span>

![參考架構](/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/media/macro-architecture.png)

<span data-ttu-id="a7670-153">此參考架構會逐步引導您完成將 Rideshare by Relecloud 應用程式設計、開發和傳遞的決策程式， (虛構的公司) 。</span><span class="sxs-lookup"><span data-stu-id="a7670-153">A reference architecture that walks you through the decision-making process involved in designing, developing, and delivering the Rideshare by Relecloud application (a fictitious company).</span></span> <span data-ttu-id="a7670-154">它包含設定和部署所有架構元件的實際操作指示。</span><span class="sxs-lookup"><span data-stu-id="a7670-154">It includes hands-on instructions for configuring and deploying all of the architecture's components.</span></span>

[<span data-ttu-id="a7670-155">無伺服器微服務參考架構</span><span class="sxs-lookup"><span data-stu-id="a7670-155">Serverless Microservices reference architecture</span></span>](/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

## <a name="migrate-console-apps-to-serverless"></a><span data-ttu-id="a7670-156">將主控台應用程式遷移至無伺服器</span><span class="sxs-lookup"><span data-stu-id="a7670-156">Migrate console apps to serverless</span></span>

<span data-ttu-id="a7670-157">這個範例是泛型函式 (檔案 `.csx`) ，可用來將任何主控台應用程式轉換成 Azure Functions 中的 HTTP web 服務。</span><span class="sxs-lookup"><span data-stu-id="a7670-157">This sample is a generic function (`.csx` file) that can be used to convert any console application to an HTTP web service in Azure Functions.</span></span> <span data-ttu-id="a7670-158">您只需要編輯設定檔，並指定要將哪些輸入參數當作引數傳遞給 `.exe` 。</span><span class="sxs-lookup"><span data-stu-id="a7670-158">All you have to do is edit a configuration file and specify what input parameters will be passed as arguments to the `.exe`.</span></span>

[<span data-ttu-id="a7670-159">在 Azure Functions 上執行主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="a7670-159">Run Console Apps on Azure Functions</span></span>](/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)

## <a name="serverless-for-mobile"></a><span data-ttu-id="a7670-160">無伺服器的行動裝置</span><span class="sxs-lookup"><span data-stu-id="a7670-160">Serverless for mobile</span></span>

<span data-ttu-id="a7670-161">Azure Functions 很容易執行和維護，而且可透過 HTTP 存取。</span><span class="sxs-lookup"><span data-stu-id="a7670-161">Azure Functions are easy to implement and maintain, and accessible through HTTP.</span></span> <span data-ttu-id="a7670-162">它們是針對行動應用程式執行 API 的絕佳方式。</span><span class="sxs-lookup"><span data-stu-id="a7670-162">They are a great way to implement an API for a mobile application.</span></span> <span data-ttu-id="a7670-163">Microsoft 透過 Xamarin 提供適用于 iOS、Android 和 Windows 的絕佳跨平臺工具。</span><span class="sxs-lookup"><span data-stu-id="a7670-163">Microsoft offers great cross-platform tools for iOS, Android, and Windows with Xamarin.</span></span> <span data-ttu-id="a7670-164">因此，Xamarin 和 Azure Functions 可一起運作。</span><span class="sxs-lookup"><span data-stu-id="a7670-164">As such, Xamarin and Azure Functions are working great together.</span></span> <span data-ttu-id="a7670-165">本文說明如何先在 Azure 入口網站或 Visual Studio 中執行 Azure 函數，並使用在 Android、iOS 和 Windows 上執行的 Xamarin 建立跨平臺用戶端。</span><span class="sxs-lookup"><span data-stu-id="a7670-165">This article shows how to implement an Azure Function in the Azure portal or in Visual Studio at first, and build a cross-platform client with Xamarin.Forms running on Android, iOS, and Windows.</span></span>

[<span data-ttu-id="a7670-166">使用 Xamarin 用戶端執行簡單的 Azure 函數</span><span class="sxs-lookup"><span data-stu-id="a7670-166">Implementing a simple Azure Function with a Xamarin.Forms client</span></span>](/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)

## <a name="serverless-messaging"></a><span data-ttu-id="a7670-167">無伺服器訊息</span><span class="sxs-lookup"><span data-stu-id="a7670-167">Serverless messaging</span></span>

<span data-ttu-id="a7670-168">此範例示範如何利用 Durable Functions 的「展開傳送」模式，在任意數目的會話/分割區上載入任意數量的訊息。</span><span class="sxs-lookup"><span data-stu-id="a7670-168">This sample shows how to utilize Durable Functions' fan-out pattern to load an arbitrary number of messages across any number of sessions/partitions.</span></span> <span data-ttu-id="a7670-169">其目標為服務匯流排、事件中樞或儲存體佇列。</span><span class="sxs-lookup"><span data-stu-id="a7670-169">It targets Service Bus, Event Hubs, or Storage Queues.</span></span> <span data-ttu-id="a7670-170">此範例也會新增使用其他 Azure 函式來取用這些訊息的功能，並將產生的計時資料載入至另一個事件中樞。</span><span class="sxs-lookup"><span data-stu-id="a7670-170">The sample also adds the ability to consume those messages with another Azure Function and load the resulting timing data in to another Event Hub.</span></span> <span data-ttu-id="a7670-171">然後，資料會內嵌至 Azure 資料總管等分析服務。</span><span class="sxs-lookup"><span data-stu-id="a7670-171">The data is then ingested into analytics services like Azure Data Explorer.</span></span>

[<span data-ttu-id="a7670-172">透過 Azure Functions 的服務匯流排、事件中樞和儲存體佇列來產生和取用訊息</span><span class="sxs-lookup"><span data-stu-id="a7670-172">Produce and Consume messages through Service Bus, Event Hubs, and Storage Queues with Azure Functions</span></span>](/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)

## <a name="recommended-resources"></a><span data-ttu-id="a7670-173">建議的資源</span><span class="sxs-lookup"><span data-stu-id="a7670-173">Recommended resources</span></span>

- [<span data-ttu-id="a7670-174">Linux 上的 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="a7670-174">Azure Functions on Linux</span></span>](/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)
- [<span data-ttu-id="a7670-175">大型資料處理： Azure 上的無伺服器 MapReduce</span><span class="sxs-lookup"><span data-stu-id="a7670-175">Big Data Processing: Serverless MapReduce on Azure</span></span>](/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)
- [<span data-ttu-id="a7670-176">建立無伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="a7670-176">Create serverless applications</span></span>](/learn/paths/create-serverless-applications/)
- [<span data-ttu-id="a7670-177">使用認知服務的客戶評論應用程式</span><span class="sxs-lookup"><span data-stu-id="a7670-177">Customer Reviews App with Cognitive Services</span></span>](/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)
- [<span data-ttu-id="a7670-178">使用 Azure Functions、Logic Apps 和 Durable Functions 進行檔案處理和驗證</span><span class="sxs-lookup"><span data-stu-id="a7670-178">File processing and validation using Azure Functions, Logic Apps, and Durable Functions</span></span>](/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)
- [<span data-ttu-id="a7670-179">使用 Xamarin 用戶端執行簡單的 Azure 函數</span><span class="sxs-lookup"><span data-stu-id="a7670-179">Implementing a simple Azure Function with a Xamarin.Forms client</span></span>](/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)
- [<span data-ttu-id="a7670-180">編輯器內遊戲遙測視覺效果</span><span class="sxs-lookup"><span data-stu-id="a7670-180">In-editor game telemetry visualization</span></span>](/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)
- [<span data-ttu-id="a7670-181">IoT 可靠邊緣轉送</span><span class="sxs-lookup"><span data-stu-id="a7670-181">IoT Reliable Edge Relay</span></span>](/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)
- [<span data-ttu-id="a7670-182">透過 Azure Functions 的服務匯流排、事件中樞和儲存體佇列來產生和取用訊息</span><span class="sxs-lookup"><span data-stu-id="a7670-182">Produce and Consume messages through Service Bus, Event Hubs, and Storage Queues with Azure Functions</span></span>](/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)
- [<span data-ttu-id="a7670-183">在 Azure Functions 上執行主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="a7670-183">Run Console Apps on Azure Functions</span></span>](/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)
- [<span data-ttu-id="a7670-184">適用于 GraphQL 的無伺服器函式</span><span class="sxs-lookup"><span data-stu-id="a7670-184">Serverless functions for GraphQL</span></span>](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)
- [<span data-ttu-id="a7670-185">無伺服器微服務參考架構</span><span class="sxs-lookup"><span data-stu-id="a7670-185">Serverless Microservices reference architecture</span></span>](/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

>[!div class="step-by-step"]
><span data-ttu-id="a7670-186">[上一個](orchestration-patterns.md) 
>[下一步](serverless-conclusion.md)</span><span class="sxs-lookup"><span data-stu-id="a7670-186">[Previous](orchestration-patterns.md)
[Next](serverless-conclusion.md)</span></span>
