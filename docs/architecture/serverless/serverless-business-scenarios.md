---
title: 無伺服器應用程式的範例商務案例和使用案例
description: 存取從影像處理到行動支援和 ETL 管線範圍的範例，以瞭解無伺服器的實際操作方法。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/17/2020
ms.openlocfilehash: 5c2ee70b86fbc9a54d2a532eaa3d7509f23825df
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135655"
---
# <a name="serverless-business-scenarios-and-use-cases"></a><span data-ttu-id="205cd-103">無伺服器商務情節和使用案例</span><span class="sxs-lookup"><span data-stu-id="205cd-103">Serverless business scenarios and use cases</span></span>

<span data-ttu-id="205cd-104">無伺服器應用程式有許多使用案例和情節。</span><span class="sxs-lookup"><span data-stu-id="205cd-104">There are many use cases and scenarios for serverless applications.</span></span> <span data-ttu-id="205cd-105">本章包含說明不同案例的範例。</span><span class="sxs-lookup"><span data-stu-id="205cd-105">This chapter includes samples that illustrate the different scenarios.</span></span> <span data-ttu-id="205cd-106">這些案例包括相關檔和公用原始程式碼存放庫的連結。</span><span class="sxs-lookup"><span data-stu-id="205cd-106">The scenarios include links to related documentation and public source code repositories.</span></span> <span data-ttu-id="205cd-107">本章中的範例可讓您開始建立自己的建築物和執行無伺服器解決方案。</span><span class="sxs-lookup"><span data-stu-id="205cd-107">The samples in this chapter enable you to get started on your own building and implementing serverless solutions.</span></span>

## <a name="big-data-processing"></a><span data-ttu-id="205cd-108">巨量資料處理</span><span class="sxs-lookup"><span data-stu-id="205cd-108">Big data processing</span></span>

![地圖/減少圖表](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/media/mapreducearchitecture.png)

<span data-ttu-id="205cd-110">這個範例會使用無伺服器，在大型資料集上進行對應/減少作業。</span><span class="sxs-lookup"><span data-stu-id="205cd-110">This example uses serverless to do a map/reduce operation on a big data set.</span></span> <span data-ttu-id="205cd-111">它會判斷2017中每日紐約的黃色計程車行程的平均速度。</span><span class="sxs-lookup"><span data-stu-id="205cd-111">It determines the average speed of New York Yellow taxi trips per day in 2017.</span></span>

[<span data-ttu-id="205cd-112">海量資料處理： Azure 上的無伺服器 MapReduce</span><span class="sxs-lookup"><span data-stu-id="205cd-112">Big Data Processing: Serverless MapReduce on Azure</span></span>](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)

## <a name="create-serverless-applications-hands-on-lab"></a><span data-ttu-id="205cd-113">建立無伺服器應用程式：實際操作實驗室</span><span class="sxs-lookup"><span data-stu-id="205cd-113">Create serverless applications: hands-on lab</span></span>

<span data-ttu-id="205cd-114">瞭解如何使用函式來執行伺服器端邏輯，並建立無伺服器架構。</span><span class="sxs-lookup"><span data-stu-id="205cd-114">Learn how to use functions to execute server-side logic and build serverless architectures.</span></span>

- <span data-ttu-id="205cd-115">選擇適用于您企業的最佳 Azure 服務</span><span class="sxs-lookup"><span data-stu-id="205cd-115">Choosing the best Azure service for your business</span></span>
- <span data-ttu-id="205cd-116">建立 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="205cd-116">Creating Azure Functions</span></span>
- <span data-ttu-id="205cd-117">使用觸發程序</span><span class="sxs-lookup"><span data-stu-id="205cd-117">Using triggers</span></span>
- <span data-ttu-id="205cd-118">連結函式</span><span class="sxs-lookup"><span data-stu-id="205cd-118">Chaining functions</span></span>
- <span data-ttu-id="205cd-119">長時間執行的工作流程</span><span class="sxs-lookup"><span data-stu-id="205cd-119">Long-running workflows</span></span>
- <span data-ttu-id="205cd-120">監視</span><span class="sxs-lookup"><span data-stu-id="205cd-120">Monitoring</span></span>
- <span data-ttu-id="205cd-121">開發、測試和部署</span><span class="sxs-lookup"><span data-stu-id="205cd-121">Development, testing, and deployment</span></span>

[<span data-ttu-id="205cd-122">建立無伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="205cd-122">Create serverless applications</span></span>](https://docs.microsoft.com/learn/paths/create-serverless-applications/)

## <a name="customer-reviews"></a><span data-ttu-id="205cd-123">客戶評論</span><span class="sxs-lookup"><span data-stu-id="205cd-123">Customer reviews</span></span>

<span data-ttu-id="205cd-124">這個範例會展示 Visual Studio 中 c # 類別庫的新 Azure Functions 工具。</span><span class="sxs-lookup"><span data-stu-id="205cd-124">This sample showcases the new Azure Functions tooling for C# Class Libraries in Visual Studio.</span></span> <span data-ttu-id="205cd-125">建立網站，讓客戶提交儲存在 Azure 儲存體 blob 和 CosmosDB 中的產品評論。</span><span class="sxs-lookup"><span data-stu-id="205cd-125">Create a website where customers submit product reviews that are stored in Azure storage blobs and CosmosDB.</span></span> <span data-ttu-id="205cd-126">使用 Azure 認知服務新增 Azure 函式，以執行客戶審核的自動化審核。</span><span class="sxs-lookup"><span data-stu-id="205cd-126">Add an Azure Function to perform automated moderation of the customer reviews using Azure Cognitive Services.</span></span> <span data-ttu-id="205cd-127">使用 Azure 儲存體佇列，將網站與函數分離。</span><span class="sxs-lookup"><span data-stu-id="205cd-127">Use an Azure storage queue to decouple the website from the function.</span></span>

[<span data-ttu-id="205cd-128">客戶評論應用程式與認知服務</span><span class="sxs-lookup"><span data-stu-id="205cd-128">Customer Reviews App with Cognitive Services</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)

## <a name="docker-linux-image-support"></a><span data-ttu-id="205cd-129">Docker Linux 映射支援</span><span class="sxs-lookup"><span data-stu-id="205cd-129">Docker Linux image support</span></span>

<span data-ttu-id="205cd-130">這個範例會示範如何建立， `Dockerfile`以在 Linux Docker 容器上建立和執行 Azure Functions。</span><span class="sxs-lookup"><span data-stu-id="205cd-130">This sample demonstrates how to create a `Dockerfile` to build and run Azure Functions on a Linux Docker container.</span></span>

[<span data-ttu-id="205cd-131">Linux 上的 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="205cd-131">Azure Functions on Linux</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)

## <a name="file-processing-and-validation"></a><span data-ttu-id="205cd-132">檔案處理和驗證</span><span class="sxs-lookup"><span data-stu-id="205cd-132">File processing and validation</span></span>

<span data-ttu-id="205cd-133">這個範例會剖析來自假設客戶的一組 CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="205cd-133">This example parses a set of CSV files from hypothetical customers.</span></span> <span data-ttu-id="205cd-134">它可確保客戶「批次」所需的所有檔案都已準備就緒，然後驗證每個檔案的結構。</span><span class="sxs-lookup"><span data-stu-id="205cd-134">It ensures that all files required for a customer "batch" are ready, then validates the structure of each file.</span></span> <span data-ttu-id="205cd-135">不同的解決方案會使用 Azure Functions、Logic Apps 和 Durable Functions 來呈現。</span><span class="sxs-lookup"><span data-stu-id="205cd-135">Different solutions are presented using Azure Functions, Logic Apps, and Durable Functions.</span></span>

[<span data-ttu-id="205cd-136">使用 Azure Functions、Logic Apps 和 Durable Functions 進行檔案處理和驗證</span><span class="sxs-lookup"><span data-stu-id="205cd-136">File processing and validation using Azure Functions, Logic Apps, and Durable Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)

## <a name="game-data-visualization"></a><span data-ttu-id="205cd-137">遊戲資料視覺效果</span><span class="sxs-lookup"><span data-stu-id="205cd-137">Game data visualization</span></span>

![遊戲遙測](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/media/points.png)

<span data-ttu-id="205cd-139">開發人員如何為其遊戲實作為編輯器內資料視覺效果解決方案的範例。</span><span class="sxs-lookup"><span data-stu-id="205cd-139">An example of how a developer could implement an in-editor data visualization solution for their game.</span></span> <span data-ttu-id="205cd-140">事實上，Unreal Engine 4 外掛程式和 Unity 外掛程式是使用此範例作為其後端所開發。</span><span class="sxs-lookup"><span data-stu-id="205cd-140">In fact, an Unreal Engine 4 Plugin and Unity Plugin were developed using this sample as its backend.</span></span> <span data-ttu-id="205cd-141">服務元件與遊戲引擎無關。</span><span class="sxs-lookup"><span data-stu-id="205cd-141">The service component is game engine agnostic.</span></span>

[<span data-ttu-id="205cd-142">編輯器內遊戲遙測視覺效果</span><span class="sxs-lookup"><span data-stu-id="205cd-142">In-editor game telemetry visualization</span></span>](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)

## <a name="graphql"></a><span data-ttu-id="205cd-143">GraphQL</span><span class="sxs-lookup"><span data-stu-id="205cd-143">GraphQL</span></span>

<span data-ttu-id="205cd-144">建立可公開 GraphQL API 的無伺服器函式。</span><span class="sxs-lookup"><span data-stu-id="205cd-144">Create a serverless function that exposes a GraphQL API.</span></span>

[<span data-ttu-id="205cd-145">GraphQL 的無伺服器函式</span><span class="sxs-lookup"><span data-stu-id="205cd-145">Serverless functions for GraphQL</span></span>](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)

## <a name="internet-of-things-iot-reliable-edge-relay"></a><span data-ttu-id="205cd-146">物聯網（IoT）可靠的邊緣轉送</span><span class="sxs-lookup"><span data-stu-id="205cd-146">Internet of Things (IoT) reliable edge relay</span></span>

![IoT 架構](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/media/architecture.png)

<span data-ttu-id="205cd-148">這個範例會執行新的通訊協定，以啟用來自 IoT 裝置的可靠上游通訊。</span><span class="sxs-lookup"><span data-stu-id="205cd-148">This sample implements a new communication protocol to enable reliable upstream communication from IoT devices.</span></span> <span data-ttu-id="205cd-149">它會自動進行資料差距偵測和回填。</span><span class="sxs-lookup"><span data-stu-id="205cd-149">It automates data gap detection and backfill.</span></span>

[<span data-ttu-id="205cd-150">IoT 可靠的邊緣轉送</span><span class="sxs-lookup"><span data-stu-id="205cd-150">IoT Reliable Edge Relay</span></span>](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)

## <a name="microservices-reference-architecture"></a><span data-ttu-id="205cd-151">微服務參考架構</span><span class="sxs-lookup"><span data-stu-id="205cd-151">Microservices reference architecture</span></span>

![參考架構](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/media/macro-architecture.png)

<span data-ttu-id="205cd-153">參考架構，引導您完成設計、開發及傳遞 Rideshare by Relecloud 應用程式（虛構公司）所牽涉到的決策制定流程。</span><span class="sxs-lookup"><span data-stu-id="205cd-153">A reference architecture that walks you through the decision-making process involved in designing, developing, and delivering the Rideshare by Relecloud application (a fictitious company).</span></span> <span data-ttu-id="205cd-154">其中包含設定和部署所有架構元件的實際操作指示。</span><span class="sxs-lookup"><span data-stu-id="205cd-154">It includes hands-on instructions for configuring and deploying all of the architecture's components.</span></span>

[<span data-ttu-id="205cd-155">無伺服器微服務參考架構</span><span class="sxs-lookup"><span data-stu-id="205cd-155">Serverless Microservices reference architecture</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

## <a name="migrate-console-apps-to-serverless"></a><span data-ttu-id="205cd-156">將主控台應用程式遷移至無伺服器</span><span class="sxs-lookup"><span data-stu-id="205cd-156">Migrate console apps to serverless</span></span>

<span data-ttu-id="205cd-157">這個範例是泛型函式（`.csx`檔案），可以用來將任何主控台應用程式轉換成 Azure Functions 中的 HTTP web 服務。</span><span class="sxs-lookup"><span data-stu-id="205cd-157">This sample is a generic function (`.csx` file) that can be used to convert any console application to an HTTP web service in Azure Functions.</span></span> <span data-ttu-id="205cd-158">您只需要編輯設定檔，並指定要將哪些輸入參數當做引數傳遞至`.exe`。</span><span class="sxs-lookup"><span data-stu-id="205cd-158">All you have to do is edit a configuration file and specify what input parameters will be passed as arguments to the `.exe`.</span></span>

[<span data-ttu-id="205cd-159">在 Azure Functions 上執行主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="205cd-159">Run Console Apps on Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)

## <a name="serverless-for-mobile"></a><span data-ttu-id="205cd-160">適用于 mobile 的無伺服器</span><span class="sxs-lookup"><span data-stu-id="205cd-160">Serverless for mobile</span></span>

<span data-ttu-id="205cd-161">Azure Functions 很容易執行和維護，而且可透過 HTTP 存取。</span><span class="sxs-lookup"><span data-stu-id="205cd-161">Azure Functions are easy to implement and maintain, and accessible through HTTP.</span></span> <span data-ttu-id="205cd-162">這是為行動應用程式執行 API 的絕佳方式。</span><span class="sxs-lookup"><span data-stu-id="205cd-162">They are a great way to implement an API for a mobile application.</span></span> <span data-ttu-id="205cd-163">Microsoft 透過 Xamarin 提供適用于 iOS、Android 和 Windows 的絕佳跨平臺工具。</span><span class="sxs-lookup"><span data-stu-id="205cd-163">Microsoft offers great cross-platform tools for iOS, Android, and Windows with Xamarin.</span></span> <span data-ttu-id="205cd-164">因此，Xamarin 和 Azure Functions 都能完美搭配運作。</span><span class="sxs-lookup"><span data-stu-id="205cd-164">As such, Xamarin and Azure Functions are working great together.</span></span> <span data-ttu-id="205cd-165">本文說明如何在 Azure 入口網站中或在 Visual Studio 中先執行 Azure 函式，並使用在 Android、iOS 和 Windows 上執行的 Xamarin 建立跨平臺用戶端。</span><span class="sxs-lookup"><span data-stu-id="205cd-165">This article shows how to implement an Azure Function in the Azure Web Portal or in Visual Studio at first, and build a cross-platform client with Xamarin.Forms, running on Android, iOS, and Windows.</span></span>

[<span data-ttu-id="205cd-166">使用 Xamarin. Forms 用戶端來執行簡單的 Azure 函數</span><span class="sxs-lookup"><span data-stu-id="205cd-166">Implementing a simple Azure Function with a Xamarin.Forms client</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)

## <a name="serverless-messaging"></a><span data-ttu-id="205cd-167">無伺服器訊息</span><span class="sxs-lookup"><span data-stu-id="205cd-167">Serverless messaging</span></span>

<span data-ttu-id="205cd-168">這個範例示範如何利用 Durable Functions 的「扇線」模式，在任意數目的會話/資料分割上載入任意數目的訊息。</span><span class="sxs-lookup"><span data-stu-id="205cd-168">This sample shows how to utilize Durable Functions' fan out pattern to load an arbitrary number of messages across any number of sessions/partitions.</span></span> <span data-ttu-id="205cd-169">它的目標是服務匯流排、事件中樞或儲存體佇列。</span><span class="sxs-lookup"><span data-stu-id="205cd-169">It targets Service Bus, Event Hubs, or Storage Queues.</span></span> <span data-ttu-id="205cd-170">此範例也會新增使用其他 Azure 函式來取用這些訊息的功能，並將產生的計時資料載入至另一個事件中樞。</span><span class="sxs-lookup"><span data-stu-id="205cd-170">The sample also adds the ability to consume those messages with another Azure Function and load the resulting timing data in to another Event Hub.</span></span> <span data-ttu-id="205cd-171">然後將資料內嵌至 Azure 資料總管之類的分析服務。</span><span class="sxs-lookup"><span data-stu-id="205cd-171">The data is then ingested into analytics services like Azure Data Explorer.</span></span>

[<span data-ttu-id="205cd-172">使用 Azure Functions，透過服務匯流排、事件中樞和儲存體佇列產生和取用訊息</span><span class="sxs-lookup"><span data-stu-id="205cd-172">Produce and Consume messages through Service Bus, Event Hubs, and Storage Queues with Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)

## <a name="recommended-resources"></a><span data-ttu-id="205cd-173">建議的資源</span><span class="sxs-lookup"><span data-stu-id="205cd-173">Recommended resources</span></span>

- [<span data-ttu-id="205cd-174">Linux 上的 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="205cd-174">Azure Functions on Linux</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-linux-custom-image/azure-functions-on-linux-custom-image-tutorial-sample-project/)
- [<span data-ttu-id="205cd-175">海量資料處理： Azure 上的無伺服器 MapReduce</span><span class="sxs-lookup"><span data-stu-id="205cd-175">Big Data Processing: Serverless MapReduce on Azure</span></span>](https://docs.microsoft.com/samples/azure-samples/durablefunctions-mapreduce-dotnet/big-data-processing-serverless-mapreduce-on-azure/)
- [<span data-ttu-id="205cd-176">建立無伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="205cd-176">Create serverless applications</span></span>](https://docs.microsoft.com/learn/paths/create-serverless-applications/)
- [<span data-ttu-id="205cd-177">客戶評論應用程式與認知服務</span><span class="sxs-lookup"><span data-stu-id="205cd-177">Customer Reviews App with Cognitive Services</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-customer-reviews/customer-reviews-cognitive-services/)
- [<span data-ttu-id="205cd-178">使用 Azure Functions、Logic Apps 和 Durable Functions 進行檔案處理和驗證</span><span class="sxs-lookup"><span data-stu-id="205cd-178">File processing and validation using Azure Functions, Logic Apps, and Durable Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-file-validation/file-processing-and-validation-using-azure-functions-logic-apps-and-durable-functions/)
- [<span data-ttu-id="205cd-179">使用 Xamarin. Forms 用戶端來執行簡單的 Azure 函數</span><span class="sxs-lookup"><span data-stu-id="205cd-179">Implementing a simple Azure Function with a Xamarin.Forms client</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-xamarin-getting-started/implementing-a-simple-azure-function-with-a-xamarinforms-client/)
- [<span data-ttu-id="205cd-180">編輯器內遊戲遙測視覺效果</span><span class="sxs-lookup"><span data-stu-id="205cd-180">In-editor game telemetry visualization</span></span>](https://docs.microsoft.com/samples/azure-samples/gaming-in-editor-telemetry/in-editor-telemetry-visualization/)
- [<span data-ttu-id="205cd-181">IoT 可靠的邊緣轉送</span><span class="sxs-lookup"><span data-stu-id="205cd-181">IoT Reliable Edge Relay</span></span>](https://docs.microsoft.com/samples/azure-samples/iot-reliable-edge-relay/iot-reliable-edge-relay/)
- [<span data-ttu-id="205cd-182">使用 Azure Functions，透過服務匯流排、事件中樞和儲存體佇列產生和取用訊息</span><span class="sxs-lookup"><span data-stu-id="205cd-182">Produce and Consume messages through Service Bus, Event Hubs, and Storage Queues with Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/durable-functions-producer-consumer/product-consume-messages-az-functions/)
- [<span data-ttu-id="205cd-183">在 Azure Functions 上執行主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="205cd-183">Run Console Apps on Azure Functions</span></span>](https://docs.microsoft.com/samples/azure-samples/functions-dotnet-migrating-console-apps/run-console-apps-on-azure-functions/)
- [<span data-ttu-id="205cd-184">GraphQL 的無伺服器函式</span><span class="sxs-lookup"><span data-stu-id="205cd-184">Serverless functions for GraphQL</span></span>](https://github.com/softchris/graphql-workshop-dotnet/blob/master/docs/workshop/4.md)
- [<span data-ttu-id="205cd-185">無伺服器微服務參考架構</span><span class="sxs-lookup"><span data-stu-id="205cd-185">Serverless Microservices reference architecture</span></span>](https://docs.microsoft.com/samples/azure-samples/serverless-microservices-reference-architecture/serverless-microservices-reference-architecture/)

>[!div class="step-by-step"]
><span data-ttu-id="205cd-186">[上一頁](orchestration-patterns.md)
>[下一頁](serverless-conclusion.md)</span><span class="sxs-lookup"><span data-stu-id="205cd-186">[Previous](orchestration-patterns.md)
[Next](serverless-conclusion.md)</span></span>
