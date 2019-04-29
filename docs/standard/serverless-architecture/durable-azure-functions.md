---
title: 持久的 Azure functions-無伺服器應用程式
description: 持久的 Azure functions 會擴充的 Azure Functions 執行階段，以啟用程式碼中的具狀態工作流程。
author: cecilphillip
ms.author: cephilli
ms.date: 06/26/2018
ms.openlocfilehash: 8ad354e1708eb88f016130f8235f534b967eb122
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776008"
---
# <a name="durable-azure-functions"></a>永久的 Azure 函式

當使用 Azure Functions 建立無伺服器應用程式，您的作業將通常設計成無狀態的方式執行。 這種設計選擇的原因是因為平台的規模而調整，但是很難知道哪些伺服器執行的程式碼。 也就很難知道多少個執行個體是在任何指定的時間點作用中。 不過，有一些需要知道處理程序的目前狀態的應用程式的類別。 請考慮提交訂單的線上商店的程序。 簽出作業可能需要知道處理序狀態的多個作業所組成的工作流程。 這類資訊可能包含產品存貨，如果客戶有任何信用額度他們的帳戶，以及處理信用卡的結果。 這些作業很可能他們自己的內部工作流程或甚至是協力廠商系統服務。

各種模式現存內部和外部系統之間的應用程式狀態的協調輔助。 您常會遇到需要集中式的佇列系統、 分散式的索引鍵-值存放區或共用的資料庫，以管理該狀態的解決方案。 不過，這些是現在需要佈建和管理的所有其他資源。 在無伺服器環境中，您的程式碼可能會很麻煩嘗試以手動方式協調與這些資源。 Azure Functions 提供建立稱為 「 長期函式的具狀態函式的替代方式。

Durable Functions 是 Azure Functions 執行階段，讓您的程式碼中的具狀態工作流程定義的擴充功能。 細分成活動的工作流程，Durable Functions 擴充功能可以管理狀態、 建立進度的檢查點，以及在伺服器之間處理函式呼叫的分佈。 在背景中，它會使用 Azure 儲存體帳戶來保存執行歷程記錄、 排程活動函式，並擷取回應。 您的無伺服器程式碼與保存的資訊，儲存體帳戶，應該永遠不會互動，並通常並不是開發人員需要互動。

## <a name="triggering-a-stateful-workflow"></a>觸發具狀態的工作流程

Durable Functions 中的具狀態工作流程可以細分成兩個內建元件;協調流程和活動觸發程序。 觸發程序和繫結是 Azure Functions 可讓您啟動、 收到輸入，並傳回結果時收到通知的無伺服器函式的核心元件。

### <a name="working-with-the-orchestration-client"></a>使用 協調流程用戶端

協調流程是唯一，相較於在 Azure Functions 中觸發作業的其他樣式。 Durable Functions 可讓函式，可能需要幾小時甚至幾天才能完成執行。 該類型是行為的必須能夠檢查執行中協調流程的狀態，提前結束，或傳送的外部事件通知。

Durable Functions 擴充功能會提供這種情況下，`DurableOrchestrationClient`類別，可讓您與互動協調函式。 使用協調流程用戶端取得存取`OrchestrationClientAttribute`繫結。 一般而言，您會加入此屬性與另一個觸發程序類型，例如`HttpTrigger`或`ServiceBusTrigger`。 一旦已觸發來源函式，協調流程用戶端可用來啟動協調器函式。

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

註解的函式搭配 Azure Functions 標示 OrchestrationTriggerAttribute 該函式為協調器函式。 它會負責管理您可設定狀態的工作流程所構成的各種活動。

協調器函式都無法使用的繫結 OrchestrationTriggerAttribute 以外。 這個屬性只可以搭配 DurableOrchestrationContext 參數類型。 可以不使用任何其他輸入，因為不支援的輸入函式簽章中還原序列化。 若要取得協調流程用戶端，GetInput 所提供的輸入\<T\>必須使用的方法。

此外，協調流程函式的傳回型別必須是 void、 工作或 JSON 可序列化的值。

> *為求簡單明瞭的錯誤處理程式碼省略了*

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

在同一時間可以啟動並執行多個協調流程執行個體。 呼叫`StartNewAsync`方法`DurableOrchestrationClient`啟動協調流程的新執行個體。 此方法會傳回`Task<string>`完成協調流程已啟動。 類型的例外狀況`TimeoutException`取得擲回，如果協調流程沒有在 30 秒內啟動。

已完成`Task<string>`從`StartNewAsync`應該包含協調流程執行個體的唯一識別碼。 這個執行個體識別碼可用來叫用該特定協調流程上的作業。 協調流程可以查詢的狀態，或傳送事件通知。

### <a name="the-activity-functions"></a>活動函式

活動函式會取得一起包含協調流程函式來建立工作流程內的個別作業。 以下是其中大部分的實際工作也不會發生。 它們代表商務邏輯，長時間執行的處理程序和較大的解決方案拼圖。

`ActivityTriggerAttribute`用來標註函式參數的型別`DurableActivityContext`。 使用註解，會通知執行階段函式要用作活動函式。 使用擷取活動函式的輸入的值`GetInput<T>`方法的`DurableActivityContext`參數。

類似於協調流程函式，活動函式的傳回型別必須是 void、 工作或 JSON 可序列化的值。

取得在活動函式內擲回任何未處理例外狀況將會傳送至呼叫的協調器函式，並顯示`TaskFailedException`。 此時，錯誤可以捕捉及記錄在 orchestrator 中，並可重試活動的功能。

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

* [長期函式](https://docs.microsoft.com/azure/azure-functions/durable-functions-overview)
* [Durable Functions 的繫結](https://docs.microsoft.com/azure/azure-functions/durable-functions-bindings)
* [Durable Functions 中管理執行個體](https://docs.microsoft.com/azure/azure-functions/durable-functions-instance-management)

>[!div class="step-by-step"]
>[上一頁](event-grid.md)
>[下一頁](orchestration-patterns.md)