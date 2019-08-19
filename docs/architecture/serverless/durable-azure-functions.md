---
title: 持久的 Azure 函式-無伺服器應用程式
description: 持久的 Azure 函式會擴充 Azure Functions 執行時間, 以在程式碼中啟用具狀態工作流程。
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: f7ee74926d6658042120113b49dc763383881423
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577511"
---
# <a name="durable-azure-functions"></a>永久的 Azure 函式

使用 Azure Functions 建立無伺服器應用程式時, 您的作業通常會設計成以無狀態的方式執行。 這種設計選擇的原因是因為平臺會調整, 所以難以得知程式碼執行所在的伺服器。 此外, 也很難以知道有多少實例在任何指定的時間點處於作用中狀態。 不過, 有些類別的應用程式需要已知進程的目前狀態。 請考慮將訂單提交到線上商店的程式。 簽出作業可能是由多個需要知道進程狀態的作業所組成的工作流程。 這類資訊可能包括產品清查、客戶的帳戶上是否有任何信用額度, 還有處理信用卡的結果。 這些作業很容易就是自己的內部工作流程, 甚至是協力廠商系統的服務。

目前有各種模式可協助協調內部和外部系統之間的應用程式狀態。 在依賴集中式佇列系統、分散式索引鍵/值存放區或共用資料庫來管理該狀態的解決方案中, 通常會有這種情況。 不過, 這些都是現在需要布建和管理的其他資源。 在無伺服器環境中, 您的程式碼可能會變得麻煩地嘗試與這些資源手動協調。 Azure Functions 提供建立名為 Durable Functions 的具狀態函式的替代方法。

Durable Functions 是 Azure Functions 執行時間的延伸模組, 可讓您在程式碼中定義具狀態工作流程。 藉由將工作流程分解成活動, Durable Functions 擴充功能可以管理狀態、建立進度檢查點, 以及處理跨伺服器的函式呼叫分佈。 在背景中, 它會使用 Azure 儲存體帳戶來保存執行歷程記錄、排程活動函式, 以及取得回應。 您的無伺服器程式碼應該永遠不會與該儲存體帳戶中的保存資訊互動, 而且通常不是開發人員需要互動的東西。

## <a name="triggering-a-stateful-workflow"></a>觸發具狀態工作流程

Durable Functions 中可設定狀態的工作流程可以分成兩個內部元件;協調流程和活動觸發程式。 觸發程式和系結是 Azure Functions 所使用的核心元件, 可讓您的無伺服器函式在啟動、接收輸入和傳回結果時收到通知。

### <a name="working-with-the-orchestration-client"></a>使用協調流程用戶端

相較于 Azure Functions 中的其他已觸發作業樣式, 協調流程是唯一的。 Durable Functions 可執行可能需要數小時或甚至數天才能完成的函式。 該類型的行為需要能夠檢查執行中協調流程的狀態、事先終止, 或傳送外來事件的通知。

在這種情況下, Durable Functions 擴充功能`DurableOrchestrationClient`會提供類別, 讓您能夠與協調的函式互動。 您可以使用`OrchestrationClientAttribute`系結取得協調流程用戶端的存取權。 一般來說, 您會將這個屬性包含在另一個觸發程式`HttpTrigger`類型, 例如或。 `ServiceBusTrigger` 一旦觸發了來源函式, 就可以使用協調流程用戶端來啟動協調器函數。

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

### <a name="the-orchestrator-function"></a>協調器函式

使用 Azure Functions 標記中的 OrchestrationTriggerAttribute 來標注函式, 以作為協調器函數。 負責管理組成具狀態工作流程的各種活動。

協調器函式無法利用 OrchestrationTriggerAttribute 以外的系結。 這個屬性只能搭配 DurableOrchestrationCoNtext 的參數類型使用。 因為不支援在函式簽章中的輸入還原序列化, 所以不能使用其他輸入。 若要取得協調流程用戶端所提供的輸入\<,\>必須使用 getinput t> T 方法。

此外, 協調流程函式的傳回類型必須是 void、Task 或 JSON 可序列化的值。

> *為了簡潔起見, 已省略錯誤處理常式代碼*

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

協調流程的多個實例可以同時啟動和執行。 在上呼叫`StartNewAsync`方法會啟動協調流程`DurableOrchestrationClient`的新實例。 方法`Task<string>`會傳回協調流程啟動時完成的。 如果協調流程未`TimeoutException`在30秒內啟動, 則會擲回類型的例外狀況。

[完成`Task<string>`來源`StartNewAsync` ] 應該包含協調流程實例的唯一識別碼。 此實例識別碼可用來叫用該特定協調流程上的作業。 可以查詢協調流程中的狀態或已傳送的事件通知。

### <a name="the-activity-functions"></a>活動函式

活動函式是離散作業, 會在協調流程函數內一起撰寫以建立工作流程。 以下是大部分實際工作發生的地方。 它們代表商務邏輯、長時間執行的程式, 以及更大的解決方案的拼圖片段。

是用來標注類型`DurableActivityContext`的函數參數。 `ActivityTriggerAttribute` 使用批註會通知執行時間函式要當做活動函數使用。 活動函式的輸入值是使用`GetInput<T>` `DurableActivityContext`參數的方法來抓取。

與協調流程函式類似, 活動函式的傳回類型必須是 void、Task 或 JSON 可序列化的值。

任何在活動函式中擲回的未處理例外狀況, 都會傳送至呼叫的協調器函`TaskFailedException`式, 並以形式呈現。 此時, 可能會攔截到錯誤並記錄在協調器中, 而且可以重試活動。

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

* [Durable Functions](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [Durable Functions 的系結](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
* [管理 Durable Functions 中的實例](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
>[上一頁](event-grid.md)
>[下一頁](orchestration-patterns.md)
