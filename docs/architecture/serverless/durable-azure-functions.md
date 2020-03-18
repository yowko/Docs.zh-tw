---
title: 耐用的 Azure 功能 - 無伺服器應用
description: 持久 Azure 函數擴展 Azure 函數運行時，以便在代碼中啟用有狀態的工作流。
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 2c0ad086640409ac187c3aa882add4d6b39b6ff9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72522858"
---
# <a name="durable-azure-functions"></a>永久的 Azure 函式

使用 Azure 函數創建無伺服器應用程式時，操作通常設計為以無狀態方式運行。 之所以選擇此設計，是因為隨著平臺的擴展，很難知道代碼在運行哪些伺服器。 也很難知道在任意給定點啟動了多少個實例。 但是，有些應用程式類需要已知的進程目前狀態。 考慮向線上商店提交訂單的過程。 簽出操作可能是一個工作流，由需要瞭解流程狀態的多個操作組成。 如果客戶帳戶上有任何積分，以及處理信用卡的結果，此類資訊可能包括產品庫存。 這些操作很容易成為它們自己的內部工作流，甚至是來自協力廠商系統的服務。

當今存在各種模式，有助於協調內部和外部系統之間的應用程式狀態。 通常遇到依賴集中式佇列系統、分散式金鑰值存儲或共用資料庫來管理該狀態的解決方案。 但是，這些都是現在需要預配和管理的其他資源。 在無伺服器環境中，嘗試手動與這些資源進行協調時，代碼可能會變得麻煩。 Azure 函數提供了創建稱為持久函數的有狀態函數的替代方法。

持久函數是 Azure 函數運行時的擴展，用於在代碼中定義有狀態工作流。 通過將工作流分解為活動，持久函數擴展可以管理狀態、創建進度檢查點和處理跨伺服器分發函式呼叫。 在後臺，它利用 Azure 存儲帳戶來保留執行歷史記錄、計畫活動函數和檢索回應。 無伺服器代碼絕不應與該存儲帳戶中的持久資訊進行交互，並且通常不是開發人員需要與之交互的內容。

## <a name="triggering-a-stateful-workflow"></a>觸發有狀態的工作流

持久函數中的有狀態工作流可以分為兩個內在元件;業務流程和活動觸發器。 觸發器和綁定是 Azure 函數使用的核心元件，用於使無伺服器函數在啟動、接收輸入和返回結果時收到通知。

### <a name="working-with-the-orchestration-client"></a>使用業務流程用戶端

與 Azure 函數中其他樣式的觸發操作相比，業務流程是唯一的。 持久功能允許執行可能需要數小時甚至數天才能完成的功能。 這種類型的行為需要能夠檢查正在運行的業務流程的狀態、先發制人地終止或發送外來事件的通知。

在這種情況下，持久函數擴展提供允許您與業務流程交互`DurableOrchestrationClient`的類。 您可以使用`OrchestrationClientAttribute`綁定訪問業務流程用戶端。 通常，您將此屬性包含為另一個觸發器類型，如 或`HttpTrigger``ServiceBusTrigger`。 觸發源函數後，業務流程用戶端可用於啟動協調器函數。

```csharp
[FunctionName("KickOff")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger(AuthorizationLevel.Function, "POST")]HttpRequestMessage req,
    [OrchestrationClient ] DurableOrchestrationClient<orchestrationClient>)
{
    OrderRequestData data = await req.Content.ReadAsAsync<OrderRequestData>();

    string instanceId = await orchestrationClient.StartNewAsync("PlaceOrder", data);

    return orchestrationClient.CreateCheckStatusResponse(req, instanceId);
}
```

### <a name="the-orchestrator-function"></a>協調器功能

在 Azure 函數中使用業務流程觸發器屬性對函數進行標記標記，該函數充當協調器函數。 它負責管理構成有狀態工作流的各種活動。

協調器函數無法使用業務流程觸發器屬性以外的綁定。 此屬性只能與持久管弦上下文的參數類型一起使用。 由於不支援函數簽名中輸入的序列化，因此無法使用任何其他輸入。 要獲取業務流程用戶端提供的輸入，必須使用 GetInput\<T\>方法。

此外，業務流程函數的返回類型必須是 void、任務或 JSON 可序列化值。

> *為了簡潔起見，錯誤處理代碼被遺漏了*

```csharp
[FunctionName("PlaceOrder")]
public static async Task<string> PlaceOrder([OrchestrationTrigger] DurableOrchestrationContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    await context.CallActivityAsync<bool>("CheckAndReserveInventory", orderData);
    await context.CallActivityAsync<string>("ProcessPayment", orderData);

    string trackingNumber = await context.CallActivityAsync<string>("ScheduleShipping", orderData);
    await context.CallActivityAsync<string>("EmailCustomer", trackingNumber);

    return trackingNumber;
}
```

可以同時啟動和運行業務流程的多個實例。 在`StartNewAsync`調用 上`DurableOrchestrationClient`的方法將啟動業務流程的新實例。 該方法返回在業務流程`Task<string>`啟動時完成的 。 如果業務流程在`TimeoutException`30 秒內未啟動，則引發類型的異常。

已完成`Task<string>`的`StartNewAsync`應包含業務流程實例的唯一 ID。 此實例 ID 可用於調用該特定業務流程的操作。 可以查詢業務流程的狀態或發送的事件通知。

### <a name="the-activity-functions"></a>活動功能

活動函數是在業務流程函數中組合以創建工作流的離散操作。 這裡大多數實際工作將發生的地方。 它們表示業務邏輯、長時間運行的流程以及較大解決方案的拼圖。

`ActivityTriggerAttribute`用於批批類型`DurableActivityContext`中的函數參數。 使用注釋通知運行時該函數旨在用作活動函數。 使用`GetInput<T>``DurableActivityContext`參數的方法檢索活動函數的輸入值。

與業務流程函數類似，活動函數的返回類型必須是 void、任務或 JSON 可序列化值。

在活動函數中引發的任何未處理異常都將發送到調用協調器函數，並呈現為`TaskFailedException`。 此時，錯誤可以捕獲並記錄在協調器中，並且可以重試活動。

```csharp
[FunctionName("CheckAndReserveInventory")]
public static bool CheckAndReserveInventory([ActivityTrigger] DurableActivityContext context)
{
    OrderRequestData orderData = context.GetInput<OrderRequestData>();

    // Connect to inventory system and try to reserve items
    return true;
}
```

## <a name="recommended-resources"></a>建議的資源

- [長期函式](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
- [持久函數綁定](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
- [在持久函數中管理實例](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
>[上一個](event-grid.md)
>[下一個](orchestration-patterns.md)
