---
title: Azure 事件網格 - 無伺服器應用
description: Azure 事件網格是一種無伺服器解決方案，用於在按事件付費模型上大規模進行可靠的事件傳遞和路由。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 3c577139c12567e762aabd58c9dc29457fa37aa1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522711"
---
# <a name="event-grid"></a><span data-ttu-id="53519-103">Event Grid</span><span class="sxs-lookup"><span data-stu-id="53519-103">Event Grid</span></span>

<span data-ttu-id="53519-104">[Azure 事件網格](/azure/event-grid/overview)為基於事件的應用程式提供無伺服器基礎結構。</span><span class="sxs-lookup"><span data-stu-id="53519-104">[Azure Event Grid](/azure/event-grid/overview) provides serverless infrastructure for event-based applications.</span></span> <span data-ttu-id="53519-105">可以從任何源發佈到事件網格，並使用來自任何平臺的消息。</span><span class="sxs-lookup"><span data-stu-id="53519-105">You can publish to Event Grid from any source and consume messages from any platform.</span></span> <span data-ttu-id="53519-106">事件網格還內置了對 Azure 資源事件的支援，以簡化與應用程式的集成。</span><span class="sxs-lookup"><span data-stu-id="53519-106">Event Grid also has built-in support for events from Azure resources to streamline integration with your applications.</span></span> <span data-ttu-id="53519-107">例如，您可以訂閱 Blob 存儲事件，以便在上載檔時通知應用。</span><span class="sxs-lookup"><span data-stu-id="53519-107">For example, you can subscribe to blob storage events to notify your app when a file is uploaded.</span></span> <span data-ttu-id="53519-108">然後，應用程式可以發佈由其他雲或本地應用程式使用的自訂事件網格消息。</span><span class="sxs-lookup"><span data-stu-id="53519-108">Your application can then publish a custom event grid message that is consumed by other cloud or on-premises applications.</span></span> <span data-ttu-id="53519-109">事件網格的構建是為了可靠地處理大規模。</span><span class="sxs-lookup"><span data-stu-id="53519-109">Event Grid was built to reliably handle massive scale.</span></span> <span data-ttu-id="53519-110">無需設置必要的基礎結構的開銷，即可獲得發佈和訂閱郵件的好處。</span><span class="sxs-lookup"><span data-stu-id="53519-110">You get the benefits of publishing and subscribing to messages without the overhead of setting up the necessary infrastructure.</span></span>

![事件網格徽標](./media/event-grid-logo.png)

<span data-ttu-id="53519-112">事件網格的主要功能包括：</span><span class="sxs-lookup"><span data-stu-id="53519-112">The major features of event grid include:</span></span>

- <span data-ttu-id="53519-113">完全託管的事件路由。</span><span class="sxs-lookup"><span data-stu-id="53519-113">Fully managed event routing.</span></span>
- <span data-ttu-id="53519-114">規模近乎即時的事件交付。</span><span class="sxs-lookup"><span data-stu-id="53519-114">Near real-time event delivery at scale.</span></span>
- <span data-ttu-id="53519-115">Azure 內部和外部的廣泛覆蓋範圍。</span><span class="sxs-lookup"><span data-stu-id="53519-115">Broad coverage both inside and outside of Azure.</span></span>

## <a name="scenarios"></a><span data-ttu-id="53519-116">案例</span><span class="sxs-lookup"><span data-stu-id="53519-116">Scenarios</span></span>

<span data-ttu-id="53519-117">事件網格可處理幾個不同的方案。</span><span class="sxs-lookup"><span data-stu-id="53519-117">Event Grid addresses several different scenarios.</span></span> <span data-ttu-id="53519-118">本節介紹三個最常見的。</span><span class="sxs-lookup"><span data-stu-id="53519-118">This section covers three of the most common ones.</span></span>

### <a name="ops-automation"></a><span data-ttu-id="53519-119">作業自動化</span><span class="sxs-lookup"><span data-stu-id="53519-119">Ops automation</span></span>

![作業自動化](./media/ops-automation.png)

<span data-ttu-id="53519-121">事件網格通過在預配基礎結構時通知[Azure 自動化](https://docs.microsoft.com/azure/automation)來説明加快自動化並簡化策略實施。</span><span class="sxs-lookup"><span data-stu-id="53519-121">Event Grid can help speed automation and simplify policy enforcement by notifying [Azure Automation](https://docs.microsoft.com/azure/automation) when infrastructure is provisioned.</span></span>

### <a name="application-integration"></a><span data-ttu-id="53519-122">應用程式整合</span><span class="sxs-lookup"><span data-stu-id="53519-122">Application integration</span></span>

![應用程式整合](./media/app-integration.png)

<span data-ttu-id="53519-124">您可以使用事件網格將應用連接到其他服務。</span><span class="sxs-lookup"><span data-stu-id="53519-124">You can use Event Grid to connect your app to other services.</span></span> <span data-ttu-id="53519-125">使用標準 HTTP 協定，即使是舊版應用也可以輕鬆修改以發佈事件網格消息。</span><span class="sxs-lookup"><span data-stu-id="53519-125">Using standard HTTP protocols, even legacy apps can be easily modified to publish Event Grid messages.</span></span> <span data-ttu-id="53519-126">Web 掛鉤可用於其他服務和平臺，用於使用事件網格消息。</span><span class="sxs-lookup"><span data-stu-id="53519-126">Web hooks are available for other services and platforms to consume Event Grid messages.</span></span>

### <a name="serverless-apps"></a><span data-ttu-id="53519-127">無伺服器應用程式</span><span class="sxs-lookup"><span data-stu-id="53519-127">Serverless apps</span></span>

![無伺服器應用程式](./media/serverless-apps.png)

<span data-ttu-id="53519-129">事件網格可以觸發 Azure 函數、邏輯應用或您自己的自訂代碼。</span><span class="sxs-lookup"><span data-stu-id="53519-129">Event Grid can trigger Azure Functions, Logic Apps, or your own custom code.</span></span> <span data-ttu-id="53519-130">使用事件網格的一個主要好處是，它使用*推送*機制在事件發生時發送消息。</span><span class="sxs-lookup"><span data-stu-id="53519-130">A major benefit of using Event Grid is that it uses a *push* mechanism to send messages when events occur.</span></span> <span data-ttu-id="53519-131">推送體系結構消耗的資源更少，比*輪詢*機制更擴展。</span><span class="sxs-lookup"><span data-stu-id="53519-131">The push architecture consumes fewer resources and scales better than *polling* mechanisms.</span></span> <span data-ttu-id="53519-132">輪詢必須檢查常規間隔的更新。</span><span class="sxs-lookup"><span data-stu-id="53519-132">Polling must check for updates on a regular interval.</span></span>

## <a name="event-grid-vs-other-azure-messaging-services"></a><span data-ttu-id="53519-133">事件網格與其他 Azure 消息傳遞服務</span><span class="sxs-lookup"><span data-stu-id="53519-133">Event Grid vs. other Azure messaging services</span></span>

<span data-ttu-id="53519-134">Azure 提供多個消息傳遞服務，包括[事件中心](https://docs.microsoft.com/azure/event-hubs)[和服務匯流排](https://docs.microsoft.com/azure/service-bus-messaging)。</span><span class="sxs-lookup"><span data-stu-id="53519-134">Azure provides several messaging services, including [Event Hubs](https://docs.microsoft.com/azure/event-hubs) and [Service Bus](https://docs.microsoft.com/azure/service-bus-messaging).</span></span> <span data-ttu-id="53519-135">每個都旨在解決一組特定的用例。</span><span class="sxs-lookup"><span data-stu-id="53519-135">Each is designed to address a specific set of use cases.</span></span> <span data-ttu-id="53519-136">下圖提供了服務之間的差異的高級概述。</span><span class="sxs-lookup"><span data-stu-id="53519-136">The following diagram provides a high-level overview of the differences between the services.</span></span>

![Azure 消息傳遞比較](./media/azure-messaging-services.png)

<span data-ttu-id="53519-138">有關更深入的比較，請參閱[比較消息服務](https://docs.microsoft.com/azure/event-grid/compare-messaging-services)。</span><span class="sxs-lookup"><span data-stu-id="53519-138">For a more in-depth comparison, see [Compare messaging services](https://docs.microsoft.com/azure/event-grid/compare-messaging-services).</span></span>

## <a name="performance-targets"></a><span data-ttu-id="53519-139">效能目標</span><span class="sxs-lookup"><span data-stu-id="53519-139">Performance targets</span></span>

<span data-ttu-id="53519-140">使用事件網格，您可以利用以下性能保證：</span><span class="sxs-lookup"><span data-stu-id="53519-140">Using Event Grid you can take advantage of the following performance guarantees:</span></span>

- <span data-ttu-id="53519-141">第 99 個百分位數中的秒端到端延遲。</span><span class="sxs-lookup"><span data-stu-id="53519-141">Subsecond end-to-end latency in the 99th percentile.</span></span>
- <span data-ttu-id="53519-142">99.99% 可用性。</span><span class="sxs-lookup"><span data-stu-id="53519-142">99.99% availability.</span></span>
- <span data-ttu-id="53519-143">每個區域每秒 1000 萬個事件。</span><span class="sxs-lookup"><span data-stu-id="53519-143">10 million events per second per region.</span></span>
- <span data-ttu-id="53519-144">每個區域有 1 億個訂閱。</span><span class="sxs-lookup"><span data-stu-id="53519-144">100 million subscriptions per region.</span></span>
- <span data-ttu-id="53519-145">50 毫秒發佈延遲。</span><span class="sxs-lookup"><span data-stu-id="53519-145">50-ms publisher latency.</span></span>
- <span data-ttu-id="53519-146">24 小時重試，在 1 天時段內保證交貨，實現指數回退。</span><span class="sxs-lookup"><span data-stu-id="53519-146">24-hour retry with exponential back-off for guaranteed delivery in the 1-day window.</span></span>
- <span data-ttu-id="53519-147">透明區域容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="53519-147">Transparent regional failover.</span></span>

## <a name="event-grid-schema"></a><span data-ttu-id="53519-148">事件格線結構描述</span><span class="sxs-lookup"><span data-stu-id="53519-148">Event Grid schema</span></span>

<span data-ttu-id="53519-149">事件網格使用標準架構包裝自訂事件。</span><span class="sxs-lookup"><span data-stu-id="53519-149">Event Grid uses a standard schema to wrap custom events.</span></span> <span data-ttu-id="53519-150">架構類似于包裝自訂資料元素的信封。</span><span class="sxs-lookup"><span data-stu-id="53519-150">The schema is like an envelope that wraps your custom data element.</span></span> <span data-ttu-id="53519-151">下面是事件網格消息的示例：</span><span class="sxs-lookup"><span data-stu-id="53519-151">Here is an example Event Grid message:</span></span>

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

<span data-ttu-id="53519-152">消息的所有內容都是標準的，`data`但屬性除外。</span><span class="sxs-lookup"><span data-stu-id="53519-152">Everything about the message is standard except the `data` property.</span></span> <span data-ttu-id="53519-153">您可以檢查消息並使用`eventType`和`dataVersion`來取消序列化有效負載的自訂部分。</span><span class="sxs-lookup"><span data-stu-id="53519-153">You can inspect the message and use the `eventType` and `dataVersion` to de-serialize the custom portion of the payload.</span></span>

## <a name="azure-resources"></a><span data-ttu-id="53519-154">Azure 資源</span><span class="sxs-lookup"><span data-stu-id="53519-154">Azure resources</span></span>

<span data-ttu-id="53519-155">使用事件網格的主要好處是 Azure 生成的自動消息。</span><span class="sxs-lookup"><span data-stu-id="53519-155">A major benefit of using Event Grid is the automatic messages produced by Azure.</span></span> <span data-ttu-id="53519-156">在 Azure 中，資源會自動發佈到允許您訂閱各種事件*的主題*。</span><span class="sxs-lookup"><span data-stu-id="53519-156">In Azure, resources automatically publish to a *topic* that allows you to subscribe for various events.</span></span> <span data-ttu-id="53519-157">下表列出了自動可用的資源類型、訊息類型和事件。</span><span class="sxs-lookup"><span data-stu-id="53519-157">The following table lists the resource types, message types, and events that are available automatically.</span></span>

| <span data-ttu-id="53519-158">Azure 資源</span><span class="sxs-lookup"><span data-stu-id="53519-158">Azure resource</span></span> | <span data-ttu-id="53519-159">事件類型</span><span class="sxs-lookup"><span data-stu-id="53519-159">Event type</span></span> | <span data-ttu-id="53519-160">描述</span><span class="sxs-lookup"><span data-stu-id="53519-160">Description</span></span> |
| -------------- | ---------- | ----------- |
| <span data-ttu-id="53519-161">Azure 訂用帳戶</span><span class="sxs-lookup"><span data-stu-id="53519-161">Azure subscription</span></span> | <span data-ttu-id="53519-162">Microsoft.Resources.ResourceWriteSuccess</span><span class="sxs-lookup"><span data-stu-id="53519-162">Microsoft.Resources.ResourceWriteSuccess</span></span> | <span data-ttu-id="53519-163">在資源建立或是更新作業成功時引發。</span><span class="sxs-lookup"><span data-stu-id="53519-163">Raised when a resource create or update operation succeeds.</span></span> |
| | <span data-ttu-id="53519-164">Microsoft.Resources.ResourceWriteFailure</span><span class="sxs-lookup"><span data-stu-id="53519-164">Microsoft.Resources.ResourceWriteFailure</span></span> | <span data-ttu-id="53519-165">在資源建立或是更新作業失敗時引發。</span><span class="sxs-lookup"><span data-stu-id="53519-165">Raised when a resource create or update operation fails.</span></span> |
| | <span data-ttu-id="53519-166">Microsoft.Resources.ResourceWriteCancel</span><span class="sxs-lookup"><span data-stu-id="53519-166">Microsoft.Resources.ResourceWriteCancel</span></span> | <span data-ttu-id="53519-167">在資源建立或是更新作業取消時引發。</span><span class="sxs-lookup"><span data-stu-id="53519-167">Raised when a resource create or update operation is canceled.</span></span> |
|  | <span data-ttu-id="53519-168">Microsoft.Resources.ResourceDeleteSuccess</span><span class="sxs-lookup"><span data-stu-id="53519-168">Microsoft.Resources.ResourceDeleteSuccess</span></span> | <span data-ttu-id="53519-169">在資源刪除作業成功時引發。</span><span class="sxs-lookup"><span data-stu-id="53519-169">Raised when a resource delete operation succeeds.</span></span> |
|  | <span data-ttu-id="53519-170">Microsoft.Resources.ResourceDeleteFailure</span><span class="sxs-lookup"><span data-stu-id="53519-170">Microsoft.Resources.ResourceDeleteFailure</span></span> | <span data-ttu-id="53519-171">在資源刪除作業失敗時引發。</span><span class="sxs-lookup"><span data-stu-id="53519-171">Raised when a resource delete operation fails.</span></span> |
| | <span data-ttu-id="53519-172">Microsoft.Resources.ResourceDeleteCancel</span><span class="sxs-lookup"><span data-stu-id="53519-172">Microsoft.Resources.ResourceDeleteCancel</span></span> | <span data-ttu-id="53519-173">在資源刪除作業取消時引發。</span><span class="sxs-lookup"><span data-stu-id="53519-173">Raised when a resource delete operation is canceled.</span></span> <span data-ttu-id="53519-174">此事件會於範本部署取消時發生。</span><span class="sxs-lookup"><span data-stu-id="53519-174">This event happens when a template deployment is canceled.</span></span> |
| <span data-ttu-id="53519-175">Blob 儲存體</span><span class="sxs-lookup"><span data-stu-id="53519-175">Blob storage</span></span> | <span data-ttu-id="53519-176">Microsoft.Storage.BlobCreated</span><span class="sxs-lookup"><span data-stu-id="53519-176">Microsoft.Storage.BlobCreated</span></span> | <span data-ttu-id="53519-177">建立 blob 時引發。</span><span class="sxs-lookup"><span data-stu-id="53519-177">Raised when a blob is created.</span></span> |
| | <span data-ttu-id="53519-178">Microsoft.Storage.BlobDeleted</span><span class="sxs-lookup"><span data-stu-id="53519-178">Microsoft.Storage.BlobDeleted</span></span> | <span data-ttu-id="53519-179">刪除 blob 時引發。</span><span class="sxs-lookup"><span data-stu-id="53519-179">Raised when a blob is deleted.</span></span> |
| <span data-ttu-id="53519-180">事件中樞</span><span class="sxs-lookup"><span data-stu-id="53519-180">Event hubs</span></span> | <span data-ttu-id="53519-181">微軟.eventHub.捕獲檔已創建</span><span class="sxs-lookup"><span data-stu-id="53519-181">Microsoft.EventHub.CaptureFileCreated</span></span> | <span data-ttu-id="53519-182">創建捕獲檔時引發。</span><span class="sxs-lookup"><span data-stu-id="53519-182">Raised when a capture file is created.</span></span>
| <span data-ttu-id="53519-183">IoT 中樞</span><span class="sxs-lookup"><span data-stu-id="53519-183">IoT Hub</span></span> | <span data-ttu-id="53519-184">Microsoft.Devices.DeviceCreated</span><span class="sxs-lookup"><span data-stu-id="53519-184">Microsoft.Devices.DeviceCreated</span></span> | <span data-ttu-id="53519-185">向 IoT 中樞註冊裝置時發佈。</span><span class="sxs-lookup"><span data-stu-id="53519-185">Published when a device is registered to an IoT hub.</span></span> |
| | <span data-ttu-id="53519-186">Microsoft.Devices.DeviceDeleted</span><span class="sxs-lookup"><span data-stu-id="53519-186">Microsoft.Devices.DeviceDeleted</span></span> | <span data-ttu-id="53519-187">從 IoT 中樞刪除裝置時發佈。</span><span class="sxs-lookup"><span data-stu-id="53519-187">Published when a device is deleted from an IoT hub.</span></span> |
| <span data-ttu-id="53519-188">資源群組</span><span class="sxs-lookup"><span data-stu-id="53519-188">Resource groups</span></span> | <span data-ttu-id="53519-189">Microsoft.Resources.ResourceWriteSuccess</span><span class="sxs-lookup"><span data-stu-id="53519-189">Microsoft.Resources.ResourceWriteSuccess</span></span> | <span data-ttu-id="53519-190">在資源建立或是更新作業成功時引發。</span><span class="sxs-lookup"><span data-stu-id="53519-190">Raised when a resource create or update operation succeeds.</span></span> |
| | <span data-ttu-id="53519-191">Microsoft.Resources.ResourceWriteFailure</span><span class="sxs-lookup"><span data-stu-id="53519-191">Microsoft.Resources.ResourceWriteFailure</span></span> | <span data-ttu-id="53519-192">在資源建立或是更新作業失敗時引發。</span><span class="sxs-lookup"><span data-stu-id="53519-192">Raised when a resource create or update operation fails.</span></span> |
| | <span data-ttu-id="53519-193">Microsoft.Resources.ResourceWriteCancel</span><span class="sxs-lookup"><span data-stu-id="53519-193">Microsoft.Resources.ResourceWriteCancel</span></span> | <span data-ttu-id="53519-194">在資源建立或是更新作業取消時引發。</span><span class="sxs-lookup"><span data-stu-id="53519-194">Raised when a resource create or update operation is canceled.</span></span> |
| | <span data-ttu-id="53519-195">Microsoft.Resources.ResourceDeleteSuccess</span><span class="sxs-lookup"><span data-stu-id="53519-195">Microsoft.Resources.ResourceDeleteSuccess</span></span> | <span data-ttu-id="53519-196">在資源刪除作業成功時引發。</span><span class="sxs-lookup"><span data-stu-id="53519-196">Raised when a resource delete operation succeeds.</span></span> |
| | <span data-ttu-id="53519-197">Microsoft.Resources.ResourceDeleteFailure</span><span class="sxs-lookup"><span data-stu-id="53519-197">Microsoft.Resources.ResourceDeleteFailure</span></span> | <span data-ttu-id="53519-198">在資源刪除作業失敗時引發。</span><span class="sxs-lookup"><span data-stu-id="53519-198">Raised when a resource delete operation fails.</span></span> |
| | <span data-ttu-id="53519-199">Microsoft.Resources.ResourceDeleteCancel</span><span class="sxs-lookup"><span data-stu-id="53519-199">Microsoft.Resources.ResourceDeleteCancel</span></span> | <span data-ttu-id="53519-200">在資源刪除作業取消時引發。</span><span class="sxs-lookup"><span data-stu-id="53519-200">Raised when a resource delete operation is canceled.</span></span> <span data-ttu-id="53519-201">此事件會於範本部署取消時發生。</span><span class="sxs-lookup"><span data-stu-id="53519-201">This event happens when a template deployment is canceled.</span></span> |

<span data-ttu-id="53519-202">有關詳細資訊，請參閱[Azure 事件網格事件架構](https://docs.microsoft.com/azure/event-grid/event-schema)。</span><span class="sxs-lookup"><span data-stu-id="53519-202">For more information, see [Azure Event Grid event schema](https://docs.microsoft.com/azure/event-grid/event-schema).</span></span>

<span data-ttu-id="53519-203">可以從任何類型的應用程式（甚至是在本地運行的應用程式）訪問事件網格。</span><span class="sxs-lookup"><span data-stu-id="53519-203">You can access Event Grid from any type of application, even one that runs on-premises.</span></span>

## <a name="conclusion"></a><span data-ttu-id="53519-204">結論</span><span class="sxs-lookup"><span data-stu-id="53519-204">Conclusion</span></span>

<span data-ttu-id="53519-205">在本章中，您瞭解了由 Azure 函數、邏輯應用和事件網格組成的 Azure 無伺服器平臺。</span><span class="sxs-lookup"><span data-stu-id="53519-205">In this chapter you learned about the Azure serverless platform that is composed of Azure Functions, Logic Apps, and Event Grid.</span></span> <span data-ttu-id="53519-206">您可以使用這些資源構建完全無伺服器的應用體系結構，或創建與其他雲資源和本機伺服器交互的混合解決方案。</span><span class="sxs-lookup"><span data-stu-id="53519-206">You can use these resources to build an entirely serverless app architecture, or create a hybrid solution that interacts with other cloud resources and on-premises servers.</span></span> <span data-ttu-id="53519-207">結合無伺服器資料平臺（如[Azure SQL](https://docs.microsoft.com/azure/sql-database)或[CosmosDB），](https://docs.microsoft.com/azure/cosmos-db/introduction)可以構建完全託管的雲本機應用程式。</span><span class="sxs-lookup"><span data-stu-id="53519-207">Combined with a serverless data platform such as [Azure SQL](https://docs.microsoft.com/azure/sql-database) or [CosmosDB](https://docs.microsoft.com/azure/cosmos-db/introduction), you can build fully managed cloud native applications.</span></span>

## <a name="recommended-resources"></a><span data-ttu-id="53519-208">建議的資源</span><span class="sxs-lookup"><span data-stu-id="53519-208">Recommended resources</span></span>

- [<span data-ttu-id="53519-209">應用服務方案</span><span class="sxs-lookup"><span data-stu-id="53519-209">App service plans</span></span>](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)
- [<span data-ttu-id="53519-210">Application Insights</span><span class="sxs-lookup"><span data-stu-id="53519-210">Application Insights</span></span>](https://docs.microsoft.com/azure/application-insights)
- [<span data-ttu-id="53519-211">Application Insights 分析</span><span class="sxs-lookup"><span data-stu-id="53519-211">Application Insights Analytics</span></span>](https://docs.microsoft.com/azure/application-insights/app-insights-analytics)
- [<span data-ttu-id="53519-212">Azure：使用無伺服器 Azure 功能將應用帶到雲中</span><span class="sxs-lookup"><span data-stu-id="53519-212">Azure: Bring your app to the cloud with serverless Azure Functions</span></span>](https://channel9.msdn.com/events/Connect/2017/E102)
- [<span data-ttu-id="53519-213">Azure 事件網格</span><span class="sxs-lookup"><span data-stu-id="53519-213">Azure Event Grid</span></span>](https://docs.microsoft.com/azure/event-grid/overview)
- [<span data-ttu-id="53519-214">Azure Event Grid 事件結構描述</span><span class="sxs-lookup"><span data-stu-id="53519-214">Azure Event Grid event schema</span></span>](https://docs.microsoft.com/azure/event-grid/event-schema)
- [<span data-ttu-id="53519-215">Azure 事件中心</span><span class="sxs-lookup"><span data-stu-id="53519-215">Azure Event Hubs</span></span>](https://docs.microsoft.com/azure/event-hubs)
- [<span data-ttu-id="53519-216">Azure 函數文檔</span><span class="sxs-lookup"><span data-stu-id="53519-216">Azure Functions documentation</span></span>](https://docs.microsoft.com/azure/azure-functions)
- [<span data-ttu-id="53519-217">Azure Functions 觸發程序和繫結概念</span><span class="sxs-lookup"><span data-stu-id="53519-217">Azure Functions triggers and bindings concepts</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)
- [<span data-ttu-id="53519-218">Azure 邏輯應用</span><span class="sxs-lookup"><span data-stu-id="53519-218">Azure Logic Apps</span></span>](https://docs.microsoft.com/azure/logic-apps)
- [<span data-ttu-id="53519-219">Azure 服務匯流排</span><span class="sxs-lookup"><span data-stu-id="53519-219">Azure Service Bus</span></span>](https://docs.microsoft.com/azure/service-bus-messaging)
- [<span data-ttu-id="53519-220">Azure 表存儲</span><span class="sxs-lookup"><span data-stu-id="53519-220">Azure Table Storage</span></span>](https://docs.microsoft.com/azure/cosmos-db/table-storage-overview)
- [<span data-ttu-id="53519-221">比較函數 1.x 和 2.x</span><span class="sxs-lookup"><span data-stu-id="53519-221">Compare functions 1.x and 2.x</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-versions)
- [<span data-ttu-id="53519-222">透過 Azure 內部部署資料閘道連線至內部部署資料來源</span><span class="sxs-lookup"><span data-stu-id="53519-222">Connecting to on-premises data sources with Azure On-premises Data Gateway</span></span>](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)
- [<span data-ttu-id="53519-223">在 Azure 入口網站中建立您的第一個函式</span><span class="sxs-lookup"><span data-stu-id="53519-223">Create your first function in the Azure portal</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)
- [<span data-ttu-id="53519-224">在 Azure CLI 建立您的第一個函式</span><span class="sxs-lookup"><span data-stu-id="53519-224">Create your first function using the Azure CLI</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)
- [<span data-ttu-id="53519-225">使用 Visual Studio 建立第一個函式</span><span class="sxs-lookup"><span data-stu-id="53519-225">Create your first function using Visual Studio</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)
- [<span data-ttu-id="53519-226">功能支援的語言</span><span class="sxs-lookup"><span data-stu-id="53519-226">Functions supported languages</span></span>](https://docs.microsoft.com/azure/azure-functions/supported-languages)
- [<span data-ttu-id="53519-227">監視 Azure Functions</span><span class="sxs-lookup"><span data-stu-id="53519-227">Monitor Azure Functions</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-monitoring)
- [<span data-ttu-id="53519-228">使用 Azure Functions Proxy</span><span class="sxs-lookup"><span data-stu-id="53519-228">Work with Azure Functions Proxies</span></span>](https://docs.microsoft.com/azure/azure-functions/functions-proxies)

>[!div class="step-by-step"]
><span data-ttu-id="53519-229">[上一個](logic-apps.md)
>[下一個](durable-azure-functions.md)</span><span class="sxs-lookup"><span data-stu-id="53519-229">[Previous](logic-apps.md)
[Next](durable-azure-functions.md)</span></span>
