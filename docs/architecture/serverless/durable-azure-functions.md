---
title: 持久 Azure Functions-無伺服器應用程式
description: 持久 Azure Functions 擴充 Azure Functions 執行時間，以在程式碼中啟用可設定狀態的工作流程。
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: c3ee628b5c2239cd13395fda7714b38b06efa058
ms.sourcegitcommit: f99115e12a5eb75638abe45072e023a3ce3351ac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2020
ms.locfileid: "94557151"
---
# <a name="durable-azure-functions"></a>持久 Azure Functions

使用 Azure Functions 建立無伺服器應用程式時，通常會將您的作業設計成以無狀態的方式執行。 這種設計選擇的原因是因為當平臺進行調整時，會變得難以得知程式碼執行所在的伺服器。 在任何指定的時間點都有作用中的實例數目，也會變得很難瞭解。 不過，有一些應用程式類別需要已知進程的目前狀態。 請考慮將訂單提交到線上商店的流程。 簽出作業可能是由多個作業所組成的工作流程，這些作業需要知道進程的狀態。 如果客戶在其帳戶上有任何信用額度，以及處理信用卡的結果，這類資訊可能包含產品清查。 這些作業可以輕易地成為本身的內部工作流程，甚至是協力廠商系統的服務。

現今有各種模式，可協助在內部與外部系統之間協調應用程式狀態。 通常會跨越依賴集中式佇列系統、分散式金鑰值存放區或共用資料庫的解決方案來管理該狀態。 不過，這些都是現在需要布建和管理的所有其他資源。 在無伺服器環境中，您的程式碼可能會很麻煩地嘗試以手動方式與這些資源協調。 Azure Functions 提供建立稱為 Durable Functions 之具狀態函式的替代方案。

Durable Functions 是 Azure Functions 執行時間的延伸模組，可讓您在程式碼中定義可設定狀態的工作流程。 藉由將工作流程細分為活動，Durable Functions 延伸模組可以管理狀態、建立進度檢查點，以及處理跨伺服器的函式呼叫分佈。 在背景中，它會利用 Azure 儲存體帳戶來保存執行歷程記錄、排程活動函式和取得回應。 您的無伺服器程式碼永遠不應該與該儲存體帳戶中的持續性資訊互動，而且通常不會與開發人員需要互動的東西互動。

## <a name="triggering-a-stateful-workflow"></a>觸發具狀態工作流程

Durable Functions 中的可設定狀態工作流程可細分成兩個內建元件;協調流程和活動觸發程式。 觸發程式和系結是 Azure Functions 所使用的核心元件，可讓您的無伺服器函式在啟動、接收輸入和傳回結果時收到通知。

### <a name="working-with-the-orchestration-client"></a>使用協調流程用戶端

相較于 Azure Functions 中的其他已觸發作業樣式，協調流程是唯一的。 Durable Functions 可執行可能需要數小時或甚至數天才能完成的函數。 這種行為的需要能夠檢查執行中的協調流程狀態、事先終止或傳送外來事件的通知。

在這種情況下，Durable Functions 擴充功能會提供可 `DurableOrchestrationClient` 讓您與協調的函式互動的類別。 您可以使用系結取得協調流程用戶端的存取權 `OrchestrationClientAttribute` 。 一般來說，您會將此屬性包含在另一個觸發程式類型，例如 `HttpTrigger` 或 `ServiceBusTrigger` 。 一旦觸發了來源函數，協調流程用戶端就可以用來啟動協調器函式。

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

在 Azure Functions 將函式標注為協調器函式時，使用 OrchestrationTriggerAttribute 來標注函式。 它負責管理組成具狀態工作流程的各種活動。

協調器函數無法使用 OrchestrationTriggerAttribute 以外的系結。 這個屬性只能搭配 >durableorchestrationcoNtext 的參數類型使用。 因為不支援在函式簽章中的輸入還原序列化，所以不能使用其他輸入。 若要取得協調流程用戶端所提供的輸入， \<T\> 必須使用 >getinput 方法。

此外，協調流程函式的傳回類型必須是 void、Task 或 JSON 可序列化值。

> *為了簡潔起見，已省略錯誤處理常式代碼*

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

協調流程的多個實例可以同時啟動及執行。 `StartNewAsync`在上呼叫方法會 `DurableOrchestrationClient` 啟動協調流程的新實例。 方法 `Task<string>` 會傳回當協調流程啟動時完成的。 `TimeoutException`如果協調流程未在30秒內啟動，則會擲回類型的例外狀況。

完成的 `Task<string>` `StartNewAsync` 應該包含協調流程實例的唯一識別碼。 此實例識別碼可以用來叫用該特定協調流程上的作業。 您可以查詢協調流程中的狀態或傳送的事件通知。

### <a name="the-activity-functions"></a>活動函式

活動函式是在協調流程函式中組合在一起以建立工作流程的離散作業。 以下是大部分實際工作的發生位置。 它們代表商務邏輯、長時間執行的程式，以及更大型解決方案的拼圖部分。

`ActivityTriggerAttribute`用來標注類型的函式參數 `DurableActivityContext` 。 使用批註可告知執行時間函式要當做活動函式使用。 使用參數的方法抓取活動函式的輸入值 `GetInput<T>` `DurableActivityContext` 。

與協調流程函式類似，活動函式的傳回類型必須是 void、Task 或 JSON 可序列化值。

在活動函式中擲回的任何未處理例外狀況，都會傳送至呼叫協調器函式，並顯示為 `TaskFailedException` 。 此時，此錯誤可能會被攔截並記錄在 orchestrator 中，並且可以重試活動。

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

- [Durable Functions](/azure/azure-functions/durable-functions-overview)
- [Durable Functions 的系結](/azure/azure-functions/durable-functions-bindings)
- [管理 Durable Functions 中的實例](/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
>[上一個](event-grid.md) 
>[下一步](orchestration-patterns.md)
