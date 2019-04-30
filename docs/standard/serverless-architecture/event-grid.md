---
title: Azure Event Grid-無伺服器應用程式
description: Azure Event Grid 是可靠的事件傳遞和路由事件支付每個模型上大規模的無伺服器解決方案。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 4970130ede0c96c645129ee6c8c7d54cb1114042
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61959358"
---
# <a name="event-grid"></a><span data-ttu-id="d802f-103">Event Grid</span><span class="sxs-lookup"><span data-stu-id="d802f-103">Event Grid</span></span>

<span data-ttu-id="d802f-104">[Azure Event Grid](/azure/event-grid/overview)事件為基礎的應用程式提供無伺服器的基礎結構。</span><span class="sxs-lookup"><span data-stu-id="d802f-104">[Azure Event Grid](/azure/event-grid/overview) provides serverless infrastructure for event-based applications.</span></span> <span data-ttu-id="d802f-105">您可以從任何來源發佈至 Event Grid，並從任何平台取用訊息。</span><span class="sxs-lookup"><span data-stu-id="d802f-105">You can publish to Event Grid from any source and consume messages from any platform.</span></span> <span data-ttu-id="d802f-106">Event Grid 也有內建支援來簡化您的應用程式與整合的 Azure 資源的事件。</span><span class="sxs-lookup"><span data-stu-id="d802f-106">Event Grid also has built-in support for events from Azure resources to streamline integration with your applications.</span></span> <span data-ttu-id="d802f-107">例如，您可以訂閱通知您的應用程式，當檔案上傳的 blob 儲存體事件。</span><span class="sxs-lookup"><span data-stu-id="d802f-107">For example, you can subscribe to blob storage events to notify your app when a file is uploaded.</span></span> <span data-ttu-id="d802f-108">然後，您的應用程式可以發佈的自訂事件格線訊息由其他雲端或內部應用程式。</span><span class="sxs-lookup"><span data-stu-id="d802f-108">Your application can then publish a custom event grid message that is consumed by other cloud or on-premises applications.</span></span> <span data-ttu-id="d802f-109">Event Grid 是建置成能夠可靠處理大規模。</span><span class="sxs-lookup"><span data-stu-id="d802f-109">Event Grid was built to reliably handle massive scale.</span></span> <span data-ttu-id="d802f-110">您會獲得發佈和訂閱訊息，無需額外設定必要的基礎結構的優點。</span><span class="sxs-lookup"><span data-stu-id="d802f-110">You get the benefits of publishing and subscribing to messages without the overhead of setting up the necessary infrastructure.</span></span>

![事件格線標誌](./media/event-grid-logo.png)

<span data-ttu-id="d802f-112">事件格線的主要功能包括：</span><span class="sxs-lookup"><span data-stu-id="d802f-112">The major features of event grid include:</span></span>

* <span data-ttu-id="d802f-113">完全受控的事件路由。</span><span class="sxs-lookup"><span data-stu-id="d802f-113">Fully managed event routing.</span></span>
* <span data-ttu-id="d802f-114">近乎即時的事件傳遞分散。</span><span class="sxs-lookup"><span data-stu-id="d802f-114">Near real-time event delivery at scale.</span></span>
* <span data-ttu-id="d802f-115">涵蓋 Azure 內外的廣泛範圍。</span><span class="sxs-lookup"><span data-stu-id="d802f-115">Broad coverage both inside and outside of Azure.</span></span>

## <a name="scenarios"></a><span data-ttu-id="d802f-116">案例</span><span class="sxs-lookup"><span data-stu-id="d802f-116">Scenarios</span></span>

<span data-ttu-id="d802f-117">Event Grid 可解決數個不同的案例。</span><span class="sxs-lookup"><span data-stu-id="d802f-117">Event Grid addresses several different scenarios.</span></span> <span data-ttu-id="d802f-118">本章節涵蓋三種最常見的。</span><span class="sxs-lookup"><span data-stu-id="d802f-118">This section covers three of the most common ones.</span></span>

### <a name="ops-automation"></a><span data-ttu-id="d802f-119">作業自動化</span><span class="sxs-lookup"><span data-stu-id="d802f-119">Ops automation</span></span>

![作業自動化](./media/ops-automation.png)

<span data-ttu-id="d802f-121">Event Grid 可協助速度自動化和簡化原則強制執行通知[Azure 自動化](https://docs.microsoft.com/azure/automation)佈建基礎結構時。</span><span class="sxs-lookup"><span data-stu-id="d802f-121">Event Grid can help speed automation and simplify policy enforcement by notifying [Azure Automation](https://docs.microsoft.com/azure/automation) when infrastructure is provisioned.</span></span>

### <a name="application-integration"></a><span data-ttu-id="d802f-122">應用程式整合</span><span class="sxs-lookup"><span data-stu-id="d802f-122">Application integration</span></span>

![應用程式整合](./media/app-integration.png)

<span data-ttu-id="d802f-124">您可以使用 Event Grid，將應用程式連接至其他服務。</span><span class="sxs-lookup"><span data-stu-id="d802f-124">You can use Event Grid to connect your app to other services.</span></span> <span data-ttu-id="d802f-125">使用標準 HTTP 通訊協定，即使是舊版應用程式可以輕鬆地修改以 Event Grid 訊息發佈。</span><span class="sxs-lookup"><span data-stu-id="d802f-125">Using standard HTTP protocols, even legacy apps can be easily modified to publish Event Grid messages.</span></span> <span data-ttu-id="d802f-126">Webhook 可供其他服務和使用事件格線訊息的平台。</span><span class="sxs-lookup"><span data-stu-id="d802f-126">Web hooks are available for other services and platforms to consume Event Grid messages.</span></span>

### <a name="serverless-apps"></a><span data-ttu-id="d802f-127">無伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="d802f-127">Serverless apps</span></span>

![無伺服器應用程式](./media/serverless-apps.png)

<span data-ttu-id="d802f-129">Event Grid 可以觸發 Azure Functions、 Logic Apps 中或您自己的自訂程式碼。</span><span class="sxs-lookup"><span data-stu-id="d802f-129">Event Grid can trigger Azure Functions, Logic Apps, or your own custom code.</span></span> <span data-ttu-id="d802f-130">使用 Event Grid 的主要優點是它會使用*推播*事件發生時傳送訊息的機制。</span><span class="sxs-lookup"><span data-stu-id="d802f-130">A major benefit of using Event Grid is that it uses a *push* mechanism to send messages when events occur.</span></span> <span data-ttu-id="d802f-131">推播架構會耗用較少的資源，以及進行的擴充優於*輪詢*機制。</span><span class="sxs-lookup"><span data-stu-id="d802f-131">The push architecture consumes fewer resources and scales better than *polling* mechanisms.</span></span> <span data-ttu-id="d802f-132">輪詢必須檢查定期更新。</span><span class="sxs-lookup"><span data-stu-id="d802f-132">Polling must check for updates on a regular interval.</span></span>

## <a name="event-grid-vs-other-azure-messaging-services"></a><span data-ttu-id="d802f-133">事件格線與其他 Azure 傳訊服務</span><span class="sxs-lookup"><span data-stu-id="d802f-133">Event Grid vs. other Azure messaging services</span></span>

<span data-ttu-id="d802f-134">Azure 提供數個訊息的服務，包括[事件中樞](https://docs.microsoft.com/azure/event-hubs)並[Service Bus](https://docs.microsoft.com/azure/service-bus-messaging)。</span><span class="sxs-lookup"><span data-stu-id="d802f-134">Azure provides several messaging services, including [Event Hubs](https://docs.microsoft.com/azure/event-hubs) and [Service Bus](https://docs.microsoft.com/azure/service-bus-messaging).</span></span> <span data-ttu-id="d802f-135">每個旨在解決一組特定的使用案例。</span><span class="sxs-lookup"><span data-stu-id="d802f-135">Each is designed to address a specific set of use cases.</span></span> <span data-ttu-id="d802f-136">下圖提供服務之間差異的高階概觀。</span><span class="sxs-lookup"><span data-stu-id="d802f-136">The following diagram provides a high-level overview of the differences between the services.</span></span>

![Azure 訊息比較](./media/azure-messaging-services.png)

<span data-ttu-id="d802f-138">如需更深入的比較，請參閱[比較訊息服務](https://docs.microsoft.com/azure/event-grid/compare-messaging-services)。</span><span class="sxs-lookup"><span data-stu-id="d802f-138">For a more in-depth comparison, see [Compare messaging services](https://docs.microsoft.com/azure/event-grid/compare-messaging-services).</span></span>

## <a name="performance-targets"></a><span data-ttu-id="d802f-139">效能目標</span><span class="sxs-lookup"><span data-stu-id="d802f-139">Performance targets</span></span>

<span data-ttu-id="d802f-140">使用事件格線，您可以利用下列效能保證：</span><span class="sxs-lookup"><span data-stu-id="d802f-140">Using Event Grid you can take advantage of the following performance guarantees:</span></span>

* <span data-ttu-id="d802f-141">少於一秒內的第 99 個百分位數的端對端延遲。</span><span class="sxs-lookup"><span data-stu-id="d802f-141">Subsecond end-to-end latency in the 99th percentile.</span></span>
* <span data-ttu-id="d802f-142">99.99%可用性。</span><span class="sxs-lookup"><span data-stu-id="d802f-142">99.99% availability.</span></span>
* <span data-ttu-id="d802f-143">每個區域每秒 10 萬個事件。</span><span class="sxs-lookup"><span data-stu-id="d802f-143">10 million events per second per region.</span></span>
* <span data-ttu-id="d802f-144">每個區域 100 萬個訂用帳戶。</span><span class="sxs-lookup"><span data-stu-id="d802f-144">100 million subscriptions per region.</span></span>
* <span data-ttu-id="d802f-145">發行者延遲 50 毫秒。</span><span class="sxs-lookup"><span data-stu-id="d802f-145">50-ms publisher latency.</span></span>
* <span data-ttu-id="d802f-146">使用指數退避法為保證傳遞，在 1 天 視窗中的 24 小時重試。</span><span class="sxs-lookup"><span data-stu-id="d802f-146">24-hour retry with exponential back-off for guaranteed delivery in the 1-day window.</span></span>
* <span data-ttu-id="d802f-147">透明的區域性容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="d802f-147">Transparent regional failover.</span></span>

## <a name="event-grid-schema"></a><span data-ttu-id="d802f-148">Event Grid 結構描述</span><span class="sxs-lookup"><span data-stu-id="d802f-148">Event Grid schema</span></span>

<span data-ttu-id="d802f-149">Event Grid 會使用標準的結構描述，來包裝自訂事件。</span><span class="sxs-lookup"><span data-stu-id="d802f-149">Event Grid uses a standard schema to wrap custom events.</span></span> <span data-ttu-id="d802f-150">結構描述就像是信封包裝您的自訂資料元素。</span><span class="sxs-lookup"><span data-stu-id="d802f-150">The schema is like an envelope that wraps your custom data element.</span></span> <span data-ttu-id="d802f-151">以下是事件格線訊息的範例：</span><span class="sxs-lookup"><span data-stu-id="d802f-151">Here is an example Event Grid message:</span></span>

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

<span data-ttu-id="d802f-152">有關訊息的所有項目是除了標準`data`屬性。</span><span class="sxs-lookup"><span data-stu-id="d802f-152">Everything about the message is standard except the `data` property.</span></span> <span data-ttu-id="d802f-153">您可以檢查訊息，並使用`eventType`和`dataVersion`還原序列化的自訂承載一部分。</span><span class="sxs-lookup"><span data-stu-id="d802f-153">You can inspect the message and use the `eventType` and `dataVersion` to de-serialize the custom portion of the payload.</span></span>

## <a name="azure-resources"></a><span data-ttu-id="d802f-154">Azure 資源</span><span class="sxs-lookup"><span data-stu-id="d802f-154">Azure resources</span></span>

<span data-ttu-id="d802f-155">使用 Event Grid 的主要優點是由 Azure 產生的自動訊息。</span><span class="sxs-lookup"><span data-stu-id="d802f-155">A major benefit of using Event Grid is the automatic messages produced by Azure.</span></span> <span data-ttu-id="d802f-156">在 Azure 中，資源會自動發行至*主題*，可讓您各種事件訂閱。</span><span class="sxs-lookup"><span data-stu-id="d802f-156">In Azure, resources automatically publish to a *topic* that allows you to subscribe for various events.</span></span> <span data-ttu-id="d802f-157">下表列出的資源類型、 訊息類型和事件，可自動。</span><span class="sxs-lookup"><span data-stu-id="d802f-157">The following table lists the resource types, message types, and events that are available automatically.</span></span>

| <span data-ttu-id="d802f-158">Azure 資源</span><span class="sxs-lookup"><span data-stu-id="d802f-158">Azure resource</span></span> | <span data-ttu-id="d802f-159">事件類型</span><span class="sxs-lookup"><span data-stu-id="d802f-159">Event type</span></span> | <span data-ttu-id="d802f-160">描述</span><span class="sxs-lookup"><span data-stu-id="d802f-160">Description</span></span> |
| -------------- | ---------- | ----------- |
| <span data-ttu-id="d802f-161">Azure 訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="d802f-161">Azure subscription</span></span> | <span data-ttu-id="d802f-162">Microsoft.Resources.ResourceWriteSuccess</span><span class="sxs-lookup"><span data-stu-id="d802f-162">Microsoft.Resources.ResourceWriteSuccess</span></span> | <span data-ttu-id="d802f-163">當資源建立或更新作業成功引發。</span><span class="sxs-lookup"><span data-stu-id="d802f-163">Raised when a resource create or update operation succeeds.</span></span> |
| | <span data-ttu-id="d802f-164">Microsoft.Resources.ResourceWriteFailure</span><span class="sxs-lookup"><span data-stu-id="d802f-164">Microsoft.Resources.ResourceWriteFailure</span></span> | <span data-ttu-id="d802f-165">在資源建立或更新作業失敗時引發。</span><span class="sxs-lookup"><span data-stu-id="d802f-165">Raised when a resource create or update operation fails.</span></span> |
| | <span data-ttu-id="d802f-166">Microsoft.Resources.ResourceWriteCancel</span><span class="sxs-lookup"><span data-stu-id="d802f-166">Microsoft.Resources.ResourceWriteCancel</span></span> | <span data-ttu-id="d802f-167">當資源建立或更新作業取消引發。</span><span class="sxs-lookup"><span data-stu-id="d802f-167">Raised when a resource create or update operation is canceled.</span></span> |
|  | <span data-ttu-id="d802f-168">Microsoft.Resources.ResourceDeleteSuccess</span><span class="sxs-lookup"><span data-stu-id="d802f-168">Microsoft.Resources.ResourceDeleteSuccess</span></span> | <span data-ttu-id="d802f-169">在資源刪除作業成功時，就會引發。</span><span class="sxs-lookup"><span data-stu-id="d802f-169">Raised when a resource delete operation succeeds.</span></span> |
|  | <span data-ttu-id="d802f-170">Microsoft.Resources.ResourceDeleteFailure</span><span class="sxs-lookup"><span data-stu-id="d802f-170">Microsoft.Resources.ResourceDeleteFailure</span></span> | <span data-ttu-id="d802f-171">在資源刪除作業失敗時引發。</span><span class="sxs-lookup"><span data-stu-id="d802f-171">Raised when a resource delete operation fails.</span></span> |
| | <span data-ttu-id="d802f-172">Microsoft.Resources.ResourceDeleteCancel</span><span class="sxs-lookup"><span data-stu-id="d802f-172">Microsoft.Resources.ResourceDeleteCancel</span></span> | <span data-ttu-id="d802f-173">當資源刪除作業取消時引發。</span><span class="sxs-lookup"><span data-stu-id="d802f-173">Raised when a resource delete operation is canceled.</span></span> <span data-ttu-id="d802f-174">取消範本部署時，就會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="d802f-174">This event happens when a template deployment is canceled.</span></span> |
| <span data-ttu-id="d802f-175">Blob 儲存體</span><span class="sxs-lookup"><span data-stu-id="d802f-175">Blob storage</span></span> | <span data-ttu-id="d802f-176">Microsoft.Storage.BlobCreated</span><span class="sxs-lookup"><span data-stu-id="d802f-176">Microsoft.Storage.BlobCreated</span></span> | <span data-ttu-id="d802f-177">在建立 blob 時引發。</span><span class="sxs-lookup"><span data-stu-id="d802f-177">Raised when a blob is created.</span></span> |
| | <span data-ttu-id="d802f-178">Microsoft.Storage.BlobDeleted</span><span class="sxs-lookup"><span data-stu-id="d802f-178">Microsoft.Storage.BlobDeleted</span></span> | <span data-ttu-id="d802f-179">刪除 blob 時引發。</span><span class="sxs-lookup"><span data-stu-id="d802f-179">Raised when a blob is deleted.</span></span> |
| <span data-ttu-id="d802f-180">事件中樞</span><span class="sxs-lookup"><span data-stu-id="d802f-180">Event hubs</span></span> | <span data-ttu-id="d802f-181">Microsoft.EventHub.CaptureFileCreated</span><span class="sxs-lookup"><span data-stu-id="d802f-181">Microsoft.EventHub.CaptureFileCreated</span></span> | <span data-ttu-id="d802f-182">當擷取檔案建立時引發。</span><span class="sxs-lookup"><span data-stu-id="d802f-182">Raised when a capture file is created.</span></span>
| <span data-ttu-id="d802f-183">IoT 中樞</span><span class="sxs-lookup"><span data-stu-id="d802f-183">IoT Hub</span></span> | <span data-ttu-id="d802f-184">Microsoft.Devices.DeviceCreated</span><span class="sxs-lookup"><span data-stu-id="d802f-184">Microsoft.Devices.DeviceCreated</span></span> | <span data-ttu-id="d802f-185">發行到 IoT 中樞註冊裝置。</span><span class="sxs-lookup"><span data-stu-id="d802f-185">Published when a device is registered to an IoT hub.</span></span> |
| | <span data-ttu-id="d802f-186">Microsoft.Devices.DeviceDeleted</span><span class="sxs-lookup"><span data-stu-id="d802f-186">Microsoft.Devices.DeviceDeleted</span></span> | <span data-ttu-id="d802f-187">從 IoT 中樞刪除裝置時，就會發行。</span><span class="sxs-lookup"><span data-stu-id="d802f-187">Published when a device is deleted from an IoT hub.</span></span> |
| <span data-ttu-id="d802f-188">資源群組</span><span class="sxs-lookup"><span data-stu-id="d802f-188">Resource groups</span></span> | <span data-ttu-id="d802f-189">Microsoft.Resources.ResourceWriteSuccess</span><span class="sxs-lookup"><span data-stu-id="d802f-189">Microsoft.Resources.ResourceWriteSuccess</span></span> | <span data-ttu-id="d802f-190">當資源建立或更新作業成功引發。</span><span class="sxs-lookup"><span data-stu-id="d802f-190">Raised when a resource create or update operation succeeds.</span></span> |
| | <span data-ttu-id="d802f-191">Microsoft.Resources.ResourceWriteFailure</span><span class="sxs-lookup"><span data-stu-id="d802f-191">Microsoft.Resources.ResourceWriteFailure</span></span> | <span data-ttu-id="d802f-192">在資源建立或更新作業失敗時引發。</span><span class="sxs-lookup"><span data-stu-id="d802f-192">Raised when a resource create or update operation fails.</span></span> |
| | <span data-ttu-id="d802f-193">Microsoft.Resources.ResourceWriteCancel</span><span class="sxs-lookup"><span data-stu-id="d802f-193">Microsoft.Resources.ResourceWriteCancel</span></span> | <span data-ttu-id="d802f-194">當資源建立或更新作業取消引發。</span><span class="sxs-lookup"><span data-stu-id="d802f-194">Raised when a resource create or update operation is canceled.</span></span> |
| | <span data-ttu-id="d802f-195">Microsoft.Resources.ResourceDeleteSuccess</span><span class="sxs-lookup"><span data-stu-id="d802f-195">Microsoft.Resources.ResourceDeleteSuccess</span></span> | <span data-ttu-id="d802f-196">在資源刪除作業成功時，就會引發。</span><span class="sxs-lookup"><span data-stu-id="d802f-196">Raised when a resource delete operation succeeds.</span></span> |
| | <span data-ttu-id="d802f-197">Microsoft.Resources.ResourceDeleteFailure</span><span class="sxs-lookup"><span data-stu-id="d802f-197">Microsoft.Resources.ResourceDeleteFailure</span></span> | <span data-ttu-id="d802f-198">在資源刪除作業失敗時引發。</span><span class="sxs-lookup"><span data-stu-id="d802f-198">Raised when a resource delete operation fails.</span></span> |
| | <span data-ttu-id="d802f-199">Microsoft.Resources.ResourceDeleteCancel</span><span class="sxs-lookup"><span data-stu-id="d802f-199">Microsoft.Resources.ResourceDeleteCancel</span></span> | <span data-ttu-id="d802f-200">當資源刪除作業取消時引發。</span><span class="sxs-lookup"><span data-stu-id="d802f-200">Raised when a resource delete operation is canceled.</span></span> <span data-ttu-id="d802f-201">取消範本部署時，就會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="d802f-201">This event happens when a template deployment is canceled.</span></span> |

<span data-ttu-id="d802f-202">如需詳細資訊，請參閱 < [Azure Event Grid 事件結構描述](https://docs.microsoft.com/azure/event-grid/event-schema)。</span><span class="sxs-lookup"><span data-stu-id="d802f-202">For more information, see [Azure Event Grid event schema](https://docs.microsoft.com/azure/event-grid/event-schema).</span></span>

<span data-ttu-id="d802f-203">您可以從任何類型的應用程式，甚至是內部部署上執行的一個來存取事件格線。</span><span class="sxs-lookup"><span data-stu-id="d802f-203">You can access Event Grid from any type of application, even one that runs on-premises.</span></span>

## <a name="conclusion"></a><span data-ttu-id="d802f-204">結論</span><span class="sxs-lookup"><span data-stu-id="d802f-204">Conclusion</span></span>

<span data-ttu-id="d802f-205">在這一章中您已了解 Azure Functions、 Logic Apps 和 Event Grid 組成 Azure 無伺服器平台。</span><span class="sxs-lookup"><span data-stu-id="d802f-205">In this chapter you learned about the Azure serverless platform that is composed of Azure Functions, Logic Apps, and Event Grid.</span></span> <span data-ttu-id="d802f-206">您可以使用這些資源來建置完全無伺服器應用程式架構，或建立混合式解決方案，與其他雲端資源互動，並在內部部署伺服器。</span><span class="sxs-lookup"><span data-stu-id="d802f-206">You can use these resources to build an entirely serverless app architecture, or create a hybrid solution that interacts with other cloud resources and on-premises servers.</span></span> <span data-ttu-id="d802f-207">這類結合的無伺服器的資料平台[Azure SQL](https://docs.microsoft.com/azure/sql-database)或是[CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction)，您可以建置完全受控的雲端原生應用程式。</span><span class="sxs-lookup"><span data-stu-id="d802f-207">Combined with a serverless data platform such as [Azure SQL](https://docs.microsoft.com/azure/sql-database) or [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction), you can build fully managed cloud native applications.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="d802f-208">建議的資源</span><span class="sxs-lookup"><span data-stu-id="d802f-208">Recommended resources</span></span>

* [<span data-ttu-id="d802f-209">App service 方案</span><span class="sxs-lookup"><span data-stu-id="d802f-209">App service plans</span></span>](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
* [<span data-ttu-id="d802f-210">Application Insights</span><span class="sxs-lookup"><span data-stu-id="d802f-210">Application Insights</span></span>](https://docs.microsoft.com/azure/application-insights)
* [<span data-ttu-id="d802f-211">Application Insights 分析</span><span class="sxs-lookup"><span data-stu-id="d802f-211">Application Insights Analytics</span></span>](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
* [<span data-ttu-id="d802f-212">Azure:將應用程式帶至雲端，無伺服器 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="d802f-212">Azure: Bring your app to the cloud with serverless Azure Functions</span></span>](https://channel9.msdn.com/events/Connect/2017/E102)
* [<span data-ttu-id="d802f-213">Azure 事件格線</span><span class="sxs-lookup"><span data-stu-id="d802f-213">Azure Event Grid</span></span>](https://docs.microsoft.com/azure/event-grid/overview)
* [<span data-ttu-id="d802f-214">Azure Event Grid 事件結構描述</span><span class="sxs-lookup"><span data-stu-id="d802f-214">Azure Event Grid event schema</span></span>](https://docs.microsoft.com/azure/event-grid/event-schema)
* [<span data-ttu-id="d802f-215">Azure 事件中樞</span><span class="sxs-lookup"><span data-stu-id="d802f-215">Azure Event Hubs</span></span>](https://docs.microsoft.com/azure/event-hubs)
* [<span data-ttu-id="d802f-216">Azure Functions 文件</span><span class="sxs-lookup"><span data-stu-id="d802f-216">Azure Functions documentation</span></span>](https://docs.microsoft.com/azure/azure-functions)
* [<span data-ttu-id="d802f-217">Azure Functions 觸發程序和繫結概念</span><span class="sxs-lookup"><span data-stu-id="d802f-217">Azure Functions triggers and bindings concepts</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
* [<span data-ttu-id="d802f-218">Azure Logic Apps</span><span class="sxs-lookup"><span data-stu-id="d802f-218">Azure Logic Apps</span></span>](https://docs.microsoft.com/azure/logic-apps)
* [<span data-ttu-id="d802f-219">Azure 服務匯流排</span><span class="sxs-lookup"><span data-stu-id="d802f-219">Azure Service Bus</span></span>](https://docs.microsoft.com/azure/service-bus-messaging)
* [<span data-ttu-id="d802f-220">Azure 資料表儲存體</span><span class="sxs-lookup"><span data-stu-id="d802f-220">Azure Table Storage</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
* [<span data-ttu-id="d802f-221">比較 functions 1.x 和 2.x</span><span class="sxs-lookup"><span data-stu-id="d802f-221">Compare functions 1.x and 2.x</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-versions)
* [<span data-ttu-id="d802f-222">連接到 Azure 內部部署資料閘道的內部部署資料來源</span><span class="sxs-lookup"><span data-stu-id="d802f-222">Connecting to on-premises data sources with Azure On-premises Data Gateway</span></span>](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
* [<span data-ttu-id="d802f-223">在 Azure 入口網站中建立您的第一個函式</span><span class="sxs-lookup"><span data-stu-id="d802f-223">Create your first function in the Azure portal</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
* [<span data-ttu-id="d802f-224">建立您使用 Azure CLI 的第一個函式</span><span class="sxs-lookup"><span data-stu-id="d802f-224">Create your first function using the Azure CLI</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
* [<span data-ttu-id="d802f-225">建立您使用 Visual Studio 的第一個函式</span><span class="sxs-lookup"><span data-stu-id="d802f-225">Create your first function using Visual Studio</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
* [<span data-ttu-id="d802f-226">支援語言的函式</span><span class="sxs-lookup"><span data-stu-id="d802f-226">Functions supported languages</span></span>](https://docs.microsoft.com/azure/azure-functions/supported-languages)
* [<span data-ttu-id="d802f-227">監視 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="d802f-227">Monitor Azure Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)
* [<span data-ttu-id="d802f-228">使用 Azure Functions Proxy</span><span class="sxs-lookup"><span data-stu-id="d802f-228">Work with Azure Functions Proxies</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-proxies)

>[!div class="step-by-step"]
><span data-ttu-id="d802f-229">[上一頁](logic-apps.md)
>[下一頁](durable-azure-functions.md)</span><span class="sxs-lookup"><span data-stu-id="d802f-229">[Previous](logic-apps.md)
[Next](durable-azure-functions.md)</span></span>
