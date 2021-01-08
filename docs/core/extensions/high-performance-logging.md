---
title: .NET 中的高效能記錄
author: IEvangelist
description: 了解如何使用 LoggerMessage 來建立可快取的委派，其對於高效能記錄案例需要較少的物件配置。
ms.author: dapine
ms.date: 01/04/2021
ms.openlocfilehash: 0031ff7a9f70cb0cf724fdf6dfa4fbe0a44af7c1
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025441"
---
# <a name="high-performance-logging-in-net"></a>.NET 中的高效能記錄

<xref:Microsoft.Extensions.Logging.LoggerMessage>類別會公開功能來建立可快取的委派，相較于[記錄器擴充方法](xref:Microsoft.Extensions.Logging.LoggerExtensions)（例如和），其需要的物件配置較少且計算額外負荷較低 <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogInformation%2A> <xref:Microsoft.Extensions.Logging.LoggerExtensions.LogDebug%2A> 。 對於高效能記錄的案例，請使用 <xref:Microsoft.Extensions.Logging.LoggerMessage> 模式。

相較於記錄器擴充方法，<xref:Microsoft.Extensions.Logging.LoggerMessage> 提供下列效能優勢：

- 記錄器擴充方法需要 "boxing" (轉換) 實值型別，例如將 `int` 轉換為 `object`。 <xref:Microsoft.Extensions.Logging.LoggerMessage> 模式可使用靜態 <xref:System.Action> 欄位和擴充方法搭配強型別參數來避免 boxing。
- 記錄器擴充方法在每次寫入記錄訊息時，都必須剖析訊息範本 (具名格式字串)。 <xref:Microsoft.Extensions.Logging.LoggerMessage> 只需在定義訊息時剖析範本一次。

範例應用程式會示範 <xref:Microsoft.Extensions.Logging.LoggerMessage> 具有優先權佇列處理背景工作服務的功能。 應用程式會依優先權連續處理工作專案。 在進行這些作業時，將會使用 <xref:Microsoft.Extensions.Logging.LoggerMessage> 模式來產生記錄訊息。

## <a name="define-a-logger-message"></a>定義記錄器訊息

使用 [Define (LogLevel、EventId、String) ](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A) 來建立 <xref:System.Action> 用來記錄訊息的委派。 <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> 多載允許最多將六個型別參數傳遞至具名格式字串 (範本)。

提供給 <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> 方法的字串是範本，而不是內插字串。 預留位置會依照指定類型的順序填入。 範本中的預留位置名稱應該是描述性名稱，而且在範本之間應該保持一致。 它們將作為結構化記錄資料內的屬性名稱。 建議您針對預留位置名稱使用 [Pascal 大小寫](../../standard/design-guidelines/capitalization-conventions.md)。 例如，`{Item}`、`{DateTime}`。

每個記錄訊息都是 [LoggerMessage.Define](xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A) 所建立之靜態欄位中保存的 <xref:System.Action>。 例如，範例應用程式會建立一個欄位來描述處理工作專案的記錄訊息：

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="FailedProcessingField":::

針對 <xref:System.Action>，請指定：

- 記錄層級。
- 含有靜態擴充方法名稱的唯一事件識別碼 (<xref:Microsoft.Extensions.Logging.EventId>)。
- 訊息範本 (具名格式字串)。

當工作專案被清除佇列來處理背景工作服務應用程式時，會將下列專案設定為：

- 將記錄層級設定為 <xref:Microsoft.Extensions.Logging.LogLevel.Critical?displayProperty=nameWithType>。
- 將事件識別碼設定為含有 `FailedToProcessWorkItem` 方法名稱的 `13`。
- 將訊息範本 (具名格式字串) 設定為字串。

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="FailedProcessingAssignment":::

結構化的記錄存放區提供事件識別碼來加強記錄時，可以使用事件名稱。 例如，[Serilog](https://github.com/serilog/serilog-extensions-logging) 會使用事件名稱。

<xref:System.Action> 是透過強型別擴充方法叫用。 `PriorityItemProcessed`方法會在每次處理工作專案時記錄訊息。 然而， `FailedToProcessWorkItem` 會在 (時呼叫，如果) 例外狀況，則會呼叫：

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="15-18":::

檢查應用程式的主控台輸出：

```console
crit: WorkerServiceOptions.Example.Worker[13]
      Epic failure processing item!
      System.Exception: Failed to verify communications.
         at WorkerServiceOptions.Example.Worker.ExecuteAsync(CancellationToken stoppingToken) in
         ..\Worker.cs:line 27
```

若要將參數傳遞至記錄訊息，請在建立靜態欄位時定義最多六個型別。 範例應用程式會在處理專案時，藉由定義欄位的類型來記錄工作專案的詳細資料 `WorkItem` <xref:System.Action> ：

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemField":::

委派的記錄訊息範本會從所提供的類型接收其預留位置值。 範例應用程式會定義委派，以新增專案參數為的工作專案 `WorkItem` ：

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemAssignment":::

用於記錄正在處理工作專案的靜態擴充方法，會 `PriorityItemProcessed` 接收工作專案引數值，並將它傳遞給 <xref:System.Action> 委派：

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingItemMethod":::

在背景工作服務的 `ExecuteAsync` 方法中， `PriorityItemProcessed` 會呼叫來記錄訊息：

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="12":::

檢查應用程式的主控台輸出：

```console
info: WorkerServiceOptions.Example.Worker[1]
      Processing priority item: Priority-Extreme (50db062a-9732-4418-936d-110549ad79e4): 'Verify communications'
```

## <a name="define-logger-message-scope"></a>定義記錄器訊息範圍

[DefineScope (string) ](xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A)方法會建立用 <xref:System.Func%601> 來定義[記錄範圍](logging.md#log-scopes)的委派。 <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> 多載允許最多將三個型別參數傳遞至具名格式字串 (範本)。

就像 <xref:Microsoft.Extensions.Logging.LoggerMessage.Define%2A> 方法的情況一樣，提供給 <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> 方法的字串是範本，而不是內插字串。 預留位置會依照指定類型的順序填入。 範本中的預留位置名稱應該是描述性名稱，而且在範本之間應該保持一致。 它們將作為結構化記錄資料內的屬性名稱。 建議您針對預留位置名稱使用 [Pascal 大小寫](../../standard/design-guidelines/capitalization-conventions.md)。 例如，`{Item}`、`{DateTime}`。

使用 <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> 方法，定義要套用至一系列記錄訊息的[記錄範圍](logging.md#log-scopes)。 在 *appsettings.json* 的主控台記錄器區段中啟用 `IncludeScopes`：

:::code language="json" source="snippets/configuration/worker-service-options/appsettings.json" highlight="3-5":::

若要建立記錄範圍，請新增欄位以保留該範圍的 <xref:System.Func%601> 委派。 範例應用程式會建立稱為 `_processingWorkScope` (*Internal/LoggerExtensions.cs*) 的欄位：

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkField":::

請使用 <xref:Microsoft.Extensions.Logging.LoggerMessage.DefineScope%2A> 來建立委派。 叫用委派時，最多可以指定三種類型作為範本引數。 範例應用程式會使用訊息範本，其中包含處理開始的日期時間：

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkAssignment":::

提供記錄訊息的靜態擴充方法。 包含訊息範本中出現之具名屬性的任何型別參數。 範例應用程式會使用，以取得 `DateTime` 自訂時間戳記來記錄並傳回 `_processingWorkScope` ：

:::code language="csharp" source="snippets/configuration/worker-service-options/Extensions/LoggerExtensions.cs" id="ProcessingWorkMethod":::

此範圍會將記錄擴充呼叫包裝在 [using](../../csharp/language-reference/keywords/using-statement.md) 區塊中：

:::code language="csharp" source="snippets/configuration/worker-service-options/Worker.cs" range="18-39" highlight="4":::

檢查應用程式主控台輸出中的記錄訊息。 下列結果會顯示記錄檔訊息的優先順序順序，其中包含記錄範圍訊息：

```console
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Extreme (f5090ede-a337-4041-b914-f6bc0db5ae64): 'Verify communications'
info: Microsoft.Hosting.Lifetime[0]
      Application started. Press Ctrl+C to shut down.
info: Microsoft.Hosting.Lifetime[0]
      Hosting environment: Development
info: Microsoft.Hosting.Lifetime[0]
      Content root path: ..\worker-service-options
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-High (496d440f-2007-4391-b179-09d75ab52373): 'Validate collection'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Medium (dea9e3f4-d7df-46d2-b7cd-5e0232eb98a5): 'Propagate selections'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Medium (089d7f0d-da72-4b55-92fe-57b147838056): 'Enter pooling [contention]'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Low (6e68c4be-089f-4450-9080-1ea63fcbb686): 'Health check network'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Deferred (6f324134-6bb6-455f-81d4-553ab307c421): 'Ping weather service'
info: WorkerServiceOptions.Example.Worker[1]
      => Processing work, started at: 09/25/2020 14:30:45
      Processing priority item: Priority-Deferred (37bf736c-7a26-4a2a-9e56-e89bcf3b8f35): 'Set process state'
```

## <a name="see-also"></a>另請參閱

- [.NET 中的記錄](logging.md)
