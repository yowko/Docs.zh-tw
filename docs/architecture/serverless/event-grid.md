---
title: Azure 事件方格-無伺服器應用程式
description: Azure 事件格線是一種無伺服器解決方案，可在每個事件的隨用隨付模型上大規模地進行可靠的事件傳遞和路由。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/06/2020
ms.openlocfilehash: 408e1b9cd1b1e5316c7c6a17bb1b0c76a38f9e11
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135707"
---
# <a name="event-grid"></a><span data-ttu-id="24588-103">Event Grid</span><span class="sxs-lookup"><span data-stu-id="24588-103">Event Grid</span></span>

<span data-ttu-id="24588-104">[Azure 事件方格](/azure/event-grid/overview)提供事件型應用程式的無伺服器基礎結構。</span><span class="sxs-lookup"><span data-stu-id="24588-104">[Azure Event Grid](/azure/event-grid/overview) provides serverless infrastructure for event-based applications.</span></span> <span data-ttu-id="24588-105">您可以從任何來源發佈至事件方格，並取用來自任何平臺的訊息。</span><span class="sxs-lookup"><span data-stu-id="24588-105">You can publish to Event Grid from any source and consume messages from any platform.</span></span> <span data-ttu-id="24588-106">事件方格也提供來自 Azure 資源的事件內建支援，以簡化與您應用程式的整合。</span><span class="sxs-lookup"><span data-stu-id="24588-106">Event Grid also has built-in support for events from Azure resources to streamline integration with your applications.</span></span> <span data-ttu-id="24588-107">例如，您可以訂閱 blob 儲存體事件，以在上傳檔案時通知您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="24588-107">For example, you can subscribe to blob storage events to notify your app when a file is uploaded.</span></span> <span data-ttu-id="24588-108">您的應用程式接著可以發佈其他雲端或內部部署應用程式所使用的自訂事件方格訊息。</span><span class="sxs-lookup"><span data-stu-id="24588-108">Your application can then publish a custom event grid message that is consumed by other cloud or on-premises applications.</span></span> <span data-ttu-id="24588-109">事件方格是為了可靠地處理大規模而建立的。</span><span class="sxs-lookup"><span data-stu-id="24588-109">Event Grid was built to reliably handle massive scale.</span></span> <span data-ttu-id="24588-110">您可以獲得發佈和訂閱訊息的優點，而不需要額外設定所需的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="24588-110">You get the benefits of publishing and subscribing to messages without the overhead of setting up the necessary infrastructure.</span></span>

![事件方格標誌](./media/event-grid-logo.png)

<span data-ttu-id="24588-112">事件方格的主要功能包括：</span><span class="sxs-lookup"><span data-stu-id="24588-112">The major features of event grid include:</span></span>

- <span data-ttu-id="24588-113">完全受控的事件路由。</span><span class="sxs-lookup"><span data-stu-id="24588-113">Fully managed event routing.</span></span>
- <span data-ttu-id="24588-114">近乎即時的大規模事件傳遞。</span><span class="sxs-lookup"><span data-stu-id="24588-114">Near real-time event delivery at scale.</span></span>
- <span data-ttu-id="24588-115">Azure 內部和外部的廣泛涵蓋範圍。</span><span class="sxs-lookup"><span data-stu-id="24588-115">Broad coverage both inside and outside of Azure.</span></span>

## <a name="scenarios"></a><span data-ttu-id="24588-116">案例</span><span class="sxs-lookup"><span data-stu-id="24588-116">Scenarios</span></span>

<span data-ttu-id="24588-117">事件方格會解決幾個不同的案例。</span><span class="sxs-lookup"><span data-stu-id="24588-117">Event Grid addresses several different scenarios.</span></span> <span data-ttu-id="24588-118">本節涵蓋三個最常見的部分。</span><span class="sxs-lookup"><span data-stu-id="24588-118">This section covers three of the most common ones.</span></span>

### <a name="ops-automation"></a><span data-ttu-id="24588-119">作業自動化</span><span class="sxs-lookup"><span data-stu-id="24588-119">Ops automation</span></span>

![作業自動化](./media/ops-automation.png)

<span data-ttu-id="24588-121">事件方格可以在布建基礎結構時通知[Azure 自動化](https://docs.microsoft.com/azure/automation)，以協助加快自動化速度並簡化原則強制執行。</span><span class="sxs-lookup"><span data-stu-id="24588-121">Event Grid can help speed automation and simplify policy enforcement by notifying [Azure Automation](https://docs.microsoft.com/azure/automation) when infrastructure is provisioned.</span></span>

### <a name="application-integration"></a><span data-ttu-id="24588-122">應用程式整合</span><span class="sxs-lookup"><span data-stu-id="24588-122">Application integration</span></span>

![應用程式整合](./media/app-integration.png)

<span data-ttu-id="24588-124">您可以使用事件方格，將您的應用程式連線到其他服務。</span><span class="sxs-lookup"><span data-stu-id="24588-124">You can use Event Grid to connect your app to other services.</span></span> <span data-ttu-id="24588-125">使用標準 HTTP 通訊協定，甚至可以輕鬆地修改繼承應用程式來發佈事件方格訊息。</span><span class="sxs-lookup"><span data-stu-id="24588-125">Using standard HTTP protocols, even legacy apps can be easily modified to publish Event Grid messages.</span></span> <span data-ttu-id="24588-126">Web 勾點可供其他服務和平臺使用事件方格訊息。</span><span class="sxs-lookup"><span data-stu-id="24588-126">Web hooks are available for other services and platforms to consume Event Grid messages.</span></span>

### <a name="serverless-apps"></a><span data-ttu-id="24588-127">無伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="24588-127">Serverless apps</span></span>

![無伺服器應用程式](./media/serverless-apps.png)

<span data-ttu-id="24588-129">事件方格可以觸發 Azure Functions、Logic Apps 或您自己的自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="24588-129">Event Grid can trigger Azure Functions, Logic Apps, or your own custom code.</span></span> <span data-ttu-id="24588-130">使用「事件方格」的主要優點是，它會在發生事件時使用*推*播機制來傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="24588-130">A major benefit of using Event Grid is that it uses a *push* mechanism to send messages when events occur.</span></span> <span data-ttu-id="24588-131">推播架構會耗用較少的資源，而且比*輪詢*機制更適合進行調整。</span><span class="sxs-lookup"><span data-stu-id="24588-131">The push architecture consumes fewer resources and scales better than *polling* mechanisms.</span></span> <span data-ttu-id="24588-132">輪詢必須定期檢查是否有更新。</span><span class="sxs-lookup"><span data-stu-id="24588-132">Polling must check for updates on a regular interval.</span></span>

## <a name="event-grid-vs-other-azure-messaging-services"></a><span data-ttu-id="24588-133">事件方格與其他 Azure 訊息服務的比較</span><span class="sxs-lookup"><span data-stu-id="24588-133">Event Grid vs. other Azure messaging services</span></span>

<span data-ttu-id="24588-134">Azure 提供數個訊息服務，包括[事件中樞](https://docs.microsoft.com/azure/event-hubs)和[服務匯流排](https://docs.microsoft.com/azure/service-bus-messaging)。</span><span class="sxs-lookup"><span data-stu-id="24588-134">Azure provides several messaging services, including [Event Hubs](https://docs.microsoft.com/azure/event-hubs) and [Service Bus](https://docs.microsoft.com/azure/service-bus-messaging).</span></span> <span data-ttu-id="24588-135">每個都是設計來處理一組特定的使用案例。</span><span class="sxs-lookup"><span data-stu-id="24588-135">Each is designed to address a specific set of use cases.</span></span> <span data-ttu-id="24588-136">下圖提供服務之間差異的高層級總覽。</span><span class="sxs-lookup"><span data-stu-id="24588-136">The following diagram provides a high-level overview of the differences between the services.</span></span>

![Azure 訊息比較](./media/azure-messaging-services.png)

<span data-ttu-id="24588-138">如需更深入的比較，請參閱[比較訊息服務](https://docs.microsoft.com/azure/event-grid/compare-messaging-services)。</span><span class="sxs-lookup"><span data-stu-id="24588-138">For a more in-depth comparison, see [Compare messaging services](https://docs.microsoft.com/azure/event-grid/compare-messaging-services).</span></span>

## <a name="performance-targets"></a><span data-ttu-id="24588-139">效能目標</span><span class="sxs-lookup"><span data-stu-id="24588-139">Performance targets</span></span>

<span data-ttu-id="24588-140">使用「事件方格」，您可以利用下列效能保證：</span><span class="sxs-lookup"><span data-stu-id="24588-140">Using Event Grid you can take advantage of the following performance guarantees:</span></span>

- <span data-ttu-id="24588-141">次秒第99個百分位數的端對端延遲。</span><span class="sxs-lookup"><span data-stu-id="24588-141">Subsecond end-to-end latency in the 99th percentile.</span></span>
- <span data-ttu-id="24588-142">99.99% 可用性。</span><span class="sxs-lookup"><span data-stu-id="24588-142">99.99% availability.</span></span>
- <span data-ttu-id="24588-143">每個區域每秒10000000個事件。</span><span class="sxs-lookup"><span data-stu-id="24588-143">10 million events per second per region.</span></span>
- <span data-ttu-id="24588-144">每個區域100000000個訂閱。</span><span class="sxs-lookup"><span data-stu-id="24588-144">100 million subscriptions per region.</span></span>
- <span data-ttu-id="24588-145">50-ms 發行者延遲。</span><span class="sxs-lookup"><span data-stu-id="24588-145">50-ms publisher latency.</span></span>
- <span data-ttu-id="24588-146">以指數輪詢的24小時重試，在1天的時間範圍內提供保證。</span><span class="sxs-lookup"><span data-stu-id="24588-146">24-hour retry with exponential back-off for guaranteed delivery in the 1-day window.</span></span>
- <span data-ttu-id="24588-147">透明的區域性容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="24588-147">Transparent regional failover.</span></span>

## <a name="event-grid-schema"></a><span data-ttu-id="24588-148">事件格線結構描述</span><span class="sxs-lookup"><span data-stu-id="24588-148">Event Grid schema</span></span>

<span data-ttu-id="24588-149">事件方格會使用標準架構來包裝自訂事件。</span><span class="sxs-lookup"><span data-stu-id="24588-149">Event Grid uses a standard schema to wrap custom events.</span></span> <span data-ttu-id="24588-150">架構就像是包裝自訂資料元素的信封。</span><span class="sxs-lookup"><span data-stu-id="24588-150">The schema is like an envelope that wraps your custom data element.</span></span> <span data-ttu-id="24588-151">以下是事件方格的範例訊息：</span><span class="sxs-lookup"><span data-stu-id="24588-151">Here is an example Event Grid message:</span></span>

```json
[{
    "id": "03e24f21-a955-43cc-8921-1f61a6081ce0",
    "eventType": "myCustomEvent",
    "subject": "foo/bar/12",
    "eventTime": "2018-09-22T10:36:01+00:00",
    "data": {
        "favoriteColor": "blue",
        "favoriteAnimal": "panther",
        "favoritePlanet": "Jupiter"
    },
    "dataVersion": "1.0"
}]
```

<span data-ttu-id="24588-152">除了`data`屬性外，訊息的所有內容都是標準的。</span><span class="sxs-lookup"><span data-stu-id="24588-152">Everything about the message is standard except the `data` property.</span></span> <span data-ttu-id="24588-153">您可以檢查訊息，並使用`eventType`和`dataVersion`來還原序列化裝載的自訂部分。</span><span class="sxs-lookup"><span data-stu-id="24588-153">You can inspect the message and use the `eventType` and `dataVersion` to de-serialize the custom portion of the payload.</span></span>

## <a name="azure-resources"></a><span data-ttu-id="24588-154">Azure 資源</span><span class="sxs-lookup"><span data-stu-id="24588-154">Azure resources</span></span>

<span data-ttu-id="24588-155">使用「事件方格」的主要優點是 Azure 所產生的自動訊息。</span><span class="sxs-lookup"><span data-stu-id="24588-155">A major benefit of using Event Grid is the automatic messages produced by Azure.</span></span> <span data-ttu-id="24588-156">在 Azure 中，資源會自動發行至可讓您訂閱各種事件的*主題*。</span><span class="sxs-lookup"><span data-stu-id="24588-156">In Azure, resources automatically publish to a *topic* that allows you to subscribe for various events.</span></span> <span data-ttu-id="24588-157">下表列出可自動使用的資源類型、訊息類型和事件。</span><span class="sxs-lookup"><span data-stu-id="24588-157">The following table lists the resource types, message types, and events that are available automatically.</span></span>

| <span data-ttu-id="24588-158">Azure 資源</span><span class="sxs-lookup"><span data-stu-id="24588-158">Azure resource</span></span> | <span data-ttu-id="24588-159">事件類型</span><span class="sxs-lookup"><span data-stu-id="24588-159">Event type</span></span> | <span data-ttu-id="24588-160">說明</span><span class="sxs-lookup"><span data-stu-id="24588-160">Description</span></span> |
| -------------- | ---------- | ----------- |
| <span data-ttu-id="24588-161">Azure 訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="24588-161">Azure subscription</span></span> | <span data-ttu-id="24588-162">Microsoft.Resources.ResourceWriteSuccess</span><span class="sxs-lookup"><span data-stu-id="24588-162">Microsoft.Resources.ResourceWriteSuccess</span></span> | <span data-ttu-id="24588-163">在資源建立或是更新作業成功時引發。</span><span class="sxs-lookup"><span data-stu-id="24588-163">Raised when a resource create or update operation succeeds.</span></span> |
| | <span data-ttu-id="24588-164">Microsoft.Resources.ResourceWriteFailure</span><span class="sxs-lookup"><span data-stu-id="24588-164">Microsoft.Resources.ResourceWriteFailure</span></span> | <span data-ttu-id="24588-165">在資源建立或是更新作業失敗時引發。</span><span class="sxs-lookup"><span data-stu-id="24588-165">Raised when a resource create or update operation fails.</span></span> |
| | <span data-ttu-id="24588-166">Microsoft.Resources.ResourceWriteCancel</span><span class="sxs-lookup"><span data-stu-id="24588-166">Microsoft.Resources.ResourceWriteCancel</span></span> | <span data-ttu-id="24588-167">在資源建立或是更新作業取消時引發。</span><span class="sxs-lookup"><span data-stu-id="24588-167">Raised when a resource create or update operation is canceled.</span></span> |
|  | <span data-ttu-id="24588-168">Microsoft.Resources.ResourceDeleteSuccess</span><span class="sxs-lookup"><span data-stu-id="24588-168">Microsoft.Resources.ResourceDeleteSuccess</span></span> | <span data-ttu-id="24588-169">在資源刪除作業成功時引發。</span><span class="sxs-lookup"><span data-stu-id="24588-169">Raised when a resource delete operation succeeds.</span></span> |
|  | <span data-ttu-id="24588-170">Microsoft.Resources.ResourceDeleteFailure</span><span class="sxs-lookup"><span data-stu-id="24588-170">Microsoft.Resources.ResourceDeleteFailure</span></span> | <span data-ttu-id="24588-171">在資源刪除作業失敗時引發。</span><span class="sxs-lookup"><span data-stu-id="24588-171">Raised when a resource delete operation fails.</span></span> |
| | <span data-ttu-id="24588-172">Microsoft.Resources.ResourceDeleteCancel</span><span class="sxs-lookup"><span data-stu-id="24588-172">Microsoft.Resources.ResourceDeleteCancel</span></span> | <span data-ttu-id="24588-173">在資源刪除作業取消時引發。</span><span class="sxs-lookup"><span data-stu-id="24588-173">Raised when a resource delete operation is canceled.</span></span> <span data-ttu-id="24588-174">此事件會於範本部署取消時發生。</span><span class="sxs-lookup"><span data-stu-id="24588-174">This event happens when a template deployment is canceled.</span></span> |
| <span data-ttu-id="24588-175">Blob 儲存體</span><span class="sxs-lookup"><span data-stu-id="24588-175">Blob storage</span></span> | <span data-ttu-id="24588-176">Microsoft.Storage.BlobCreated</span><span class="sxs-lookup"><span data-stu-id="24588-176">Microsoft.Storage.BlobCreated</span></span> | <span data-ttu-id="24588-177">建立 blob 時引發。</span><span class="sxs-lookup"><span data-stu-id="24588-177">Raised when a blob is created.</span></span> |
| | <span data-ttu-id="24588-178">Microsoft.Storage.BlobDeleted</span><span class="sxs-lookup"><span data-stu-id="24588-178">Microsoft.Storage.BlobDeleted</span></span> | <span data-ttu-id="24588-179">刪除 blob 時引發。</span><span class="sxs-lookup"><span data-stu-id="24588-179">Raised when a blob is deleted.</span></span> |
| <span data-ttu-id="24588-180">事件中樞</span><span class="sxs-lookup"><span data-stu-id="24588-180">Event hubs</span></span> | <span data-ttu-id="24588-181">CaptureFileCreated</span><span class="sxs-lookup"><span data-stu-id="24588-181">Microsoft.EventHub.CaptureFileCreated</span></span> | <span data-ttu-id="24588-182">建立 capture 檔案時引發。</span><span class="sxs-lookup"><span data-stu-id="24588-182">Raised when a capture file is created.</span></span>
| <span data-ttu-id="24588-183">IoT 中樞</span><span class="sxs-lookup"><span data-stu-id="24588-183">IoT Hub</span></span> | <span data-ttu-id="24588-184">Microsoft.Devices.DeviceCreated</span><span class="sxs-lookup"><span data-stu-id="24588-184">Microsoft.Devices.DeviceCreated</span></span> | <span data-ttu-id="24588-185">向 IoT 中樞註冊裝置時發佈。</span><span class="sxs-lookup"><span data-stu-id="24588-185">Published when a device is registered to an IoT hub.</span></span> |
| | <span data-ttu-id="24588-186">Microsoft.Devices.DeviceDeleted</span><span class="sxs-lookup"><span data-stu-id="24588-186">Microsoft.Devices.DeviceDeleted</span></span> | <span data-ttu-id="24588-187">從 IoT 中樞刪除裝置時發佈。</span><span class="sxs-lookup"><span data-stu-id="24588-187">Published when a device is deleted from an IoT hub.</span></span> |
| <span data-ttu-id="24588-188">資源群組</span><span class="sxs-lookup"><span data-stu-id="24588-188">Resource groups</span></span> | <span data-ttu-id="24588-189">Microsoft.Resources.ResourceWriteSuccess</span><span class="sxs-lookup"><span data-stu-id="24588-189">Microsoft.Resources.ResourceWriteSuccess</span></span> | <span data-ttu-id="24588-190">在資源建立或是更新作業成功時引發。</span><span class="sxs-lookup"><span data-stu-id="24588-190">Raised when a resource create or update operation succeeds.</span></span> |
| | <span data-ttu-id="24588-191">Microsoft.Resources.ResourceWriteFailure</span><span class="sxs-lookup"><span data-stu-id="24588-191">Microsoft.Resources.ResourceWriteFailure</span></span> | <span data-ttu-id="24588-192">在資源建立或是更新作業失敗時引發。</span><span class="sxs-lookup"><span data-stu-id="24588-192">Raised when a resource create or update operation fails.</span></span> |
| | <span data-ttu-id="24588-193">Microsoft.Resources.ResourceWriteCancel</span><span class="sxs-lookup"><span data-stu-id="24588-193">Microsoft.Resources.ResourceWriteCancel</span></span> | <span data-ttu-id="24588-194">在資源建立或是更新作業取消時引發。</span><span class="sxs-lookup"><span data-stu-id="24588-194">Raised when a resource create or update operation is canceled.</span></span> |
| | <span data-ttu-id="24588-195">Microsoft.Resources.ResourceDeleteSuccess</span><span class="sxs-lookup"><span data-stu-id="24588-195">Microsoft.Resources.ResourceDeleteSuccess</span></span> | <span data-ttu-id="24588-196">在資源刪除作業成功時引發。</span><span class="sxs-lookup"><span data-stu-id="24588-196">Raised when a resource delete operation succeeds.</span></span> |
| | <span data-ttu-id="24588-197">Microsoft.Resources.ResourceDeleteFailure</span><span class="sxs-lookup"><span data-stu-id="24588-197">Microsoft.Resources.ResourceDeleteFailure</span></span> | <span data-ttu-id="24588-198">在資源刪除作業失敗時引發。</span><span class="sxs-lookup"><span data-stu-id="24588-198">Raised when a resource delete operation fails.</span></span> |
| | <span data-ttu-id="24588-199">Microsoft.Resources.ResourceDeleteCancel</span><span class="sxs-lookup"><span data-stu-id="24588-199">Microsoft.Resources.ResourceDeleteCancel</span></span> | <span data-ttu-id="24588-200">在資源刪除作業取消時引發。</span><span class="sxs-lookup"><span data-stu-id="24588-200">Raised when a resource delete operation is canceled.</span></span> <span data-ttu-id="24588-201">此事件會於範本部署取消時發生。</span><span class="sxs-lookup"><span data-stu-id="24588-201">This event happens when a template deployment is canceled.</span></span> |

<span data-ttu-id="24588-202">如需詳細資訊，請參閱[Azure Event Grid 事件架構](https://docs.microsoft.com/azure/event-grid/event-schema)。</span><span class="sxs-lookup"><span data-stu-id="24588-202">For more information, see [Azure Event Grid event schema](https://docs.microsoft.com/azure/event-grid/event-schema).</span></span>

<span data-ttu-id="24588-203">您可以從任何類型的應用程式存取事件方格，即使是在內部部署環境中執行。</span><span class="sxs-lookup"><span data-stu-id="24588-203">You can access Event Grid from any type of application, even one that runs on-premises.</span></span>

## <a name="conclusion"></a><span data-ttu-id="24588-204">結論</span><span class="sxs-lookup"><span data-stu-id="24588-204">Conclusion</span></span>

<span data-ttu-id="24588-205">在本章中，您已瞭解由 Azure Functions、Logic Apps 和事件方格組成的 Azure 無伺服器平臺。</span><span class="sxs-lookup"><span data-stu-id="24588-205">In this chapter you learned about the Azure serverless platform that is composed of Azure Functions, Logic Apps, and Event Grid.</span></span> <span data-ttu-id="24588-206">您可以使用這些資源來建立完全無伺服器的應用程式架構，或建立與其他雲端資源和內部部署伺服器互動的混合式解決方案。</span><span class="sxs-lookup"><span data-stu-id="24588-206">You can use these resources to build an entirely serverless app architecture, or create a hybrid solution that interacts with other cloud resources and on-premises servers.</span></span> <span data-ttu-id="24588-207">結合了無伺服器資料平臺（例如[AZURE SQL](https://docs.microsoft.com/azure/sql-database)或[CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction)），您可以建立完全受控的雲端原生應用程式。</span><span class="sxs-lookup"><span data-stu-id="24588-207">Combined with a serverless data platform such as [Azure SQL](https://docs.microsoft.com/azure/sql-database) or [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction), you can build fully managed cloud native applications.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="24588-208">建議的資源</span><span class="sxs-lookup"><span data-stu-id="24588-208">Recommended resources</span></span>

- [<span data-ttu-id="24588-209">App service 方案</span><span class="sxs-lookup"><span data-stu-id="24588-209">App service plans</span></span>](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
- [<span data-ttu-id="24588-210">Application Insights</span><span class="sxs-lookup"><span data-stu-id="24588-210">Application Insights</span></span>](https://docs.microsoft.com/azure/application-insights)
- [<span data-ttu-id="24588-211">Application Insights 分析</span><span class="sxs-lookup"><span data-stu-id="24588-211">Application Insights Analytics</span></span>](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
- [<span data-ttu-id="24588-212">Azure：使用無伺服器 Azure Functions 將您的應用程式帶入雲端</span><span class="sxs-lookup"><span data-stu-id="24588-212">Azure: Bring your app to the cloud with serverless Azure Functions</span></span>](https://channel9.msdn.com/events/Connect/2017/E102)
- [<span data-ttu-id="24588-213">事件格線</span><span class="sxs-lookup"><span data-stu-id="24588-213">Azure Event Grid</span></span>](https://docs.microsoft.com/azure/event-grid/overview)
- [<span data-ttu-id="24588-214">Azure Event Grid 事件結構描述</span><span class="sxs-lookup"><span data-stu-id="24588-214">Azure Event Grid event schema</span></span>](https://docs.microsoft.com/azure/event-grid/event-schema)
- [<span data-ttu-id="24588-215">Azure 事件中樞</span><span class="sxs-lookup"><span data-stu-id="24588-215">Azure Event Hubs</span></span>](https://docs.microsoft.com/azure/event-hubs)
- [<span data-ttu-id="24588-216">Azure Functions 文件</span><span class="sxs-lookup"><span data-stu-id="24588-216">Azure Functions documentation</span></span>](https://docs.microsoft.com/azure/azure-functions)
- [<span data-ttu-id="24588-217">Azure Functions 觸發程序和繫結概念</span><span class="sxs-lookup"><span data-stu-id="24588-217">Azure Functions triggers and bindings concepts</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
- [<span data-ttu-id="24588-218">Azure Logic Apps</span><span class="sxs-lookup"><span data-stu-id="24588-218">Azure Logic Apps</span></span>](https://docs.microsoft.com/azure/logic-apps)
- [<span data-ttu-id="24588-219">Azure 服務匯流排</span><span class="sxs-lookup"><span data-stu-id="24588-219">Azure Service Bus</span></span>](https://docs.microsoft.com/azure/service-bus-messaging)
- [<span data-ttu-id="24588-220">Azure 表格儲存體</span><span class="sxs-lookup"><span data-stu-id="24588-220">Azure Table Storage</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
- [<span data-ttu-id="24588-221">透過 Azure 內部部署資料閘道連線至內部部署資料來源</span><span class="sxs-lookup"><span data-stu-id="24588-221">Connecting to on-premises data sources with Azure On-premises Data Gateway</span></span>](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
- [<span data-ttu-id="24588-222">在 Azure 入口網站中建立您的第一個函式</span><span class="sxs-lookup"><span data-stu-id="24588-222">Create your first function in the Azure portal</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
- [<span data-ttu-id="24588-223">在 Azure CLI 建立您的第一個函式</span><span class="sxs-lookup"><span data-stu-id="24588-223">Create your first function using the Azure CLI</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
- [<span data-ttu-id="24588-224">使用 Visual Studio 建立第一個函式</span><span class="sxs-lookup"><span data-stu-id="24588-224">Create your first function using Visual Studio</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
- [<span data-ttu-id="24588-225">功能支援的語言</span><span class="sxs-lookup"><span data-stu-id="24588-225">Functions supported languages</span></span>](https://docs.microsoft.com/azure/azure-functions/supported-languages)
- [<span data-ttu-id="24588-226">監視 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="24588-226">Monitor Azure Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)

>[!div class="step-by-step"]
><span data-ttu-id="24588-227">[上一頁](logic-apps.md)
>[下一頁](durable-azure-functions.md)</span><span class="sxs-lookup"><span data-stu-id="24588-227">[Previous](logic-apps.md)
[Next](durable-azure-functions.md)</span></span>
