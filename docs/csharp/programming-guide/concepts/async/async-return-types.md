---
title: '非同步傳回類型 (c # ) '
description: '瞭解非同步方法可以在 c # 中使用的傳回型別，以及每種類型的程式碼範例和其他資源。'
ms.date: 08/19/2020
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 71e560ed8ee0cae14da396e5ea2f3ab29611ebab
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88811492"
---
# <a name="async-return-types-c"></a>非同步傳回類型 (c # ) 

非同步方法可有下列傳回型別：

- 執行作業但不傳回任何值的非同步方法為 <xref:System.Threading.Tasks.Task>。
- 傳回值的非同步方法為 <xref:System.Threading.Tasks.Task%601>。
- 處理常式為 `void`。
- 自 C# 7.0 開始，任何具有可存取 `GetAwaiter` 方法的型別。 `GetAwaiter` 方法傳回的物件必須實作 <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> 介面。
- 從 c # 8.0 開始， <xref:System.Collections.Generic.IAsyncEnumerable%601> 適用于傳回 *非同步資料流程*的非同步方法。

如需非同步方法的詳細資訊，請參閱 [使用 async 和 await 進行非同步程式設計 (c # ) ](./index.md)。

另外還有一些 Windows 工作負載特有的類型：

- <xref:System.Windows.Threading.DispatcherOperation>，適用于僅限 Windows 的非同步作業。
- <xref:Windows.Foundation.IAsyncAction>，適用于 UWP 中不會傳回值的非同步動作。
- <xref:Windows.Foundation.IAsyncActionWithProgress%601>，適用于 UWP 中報告進度但未傳回值的非同步動作。
- <xref:Windows.Foundation.IAsyncOperation%601>，適用于 UWP 中傳回值的非同步作業。
- <xref:Windows.Foundation.IAsyncOperationWithProgress%602>，適用于 UWP 中的非同步作業，可報告進度並傳回值。

## <a name="task-return-type"></a>工作傳回類型

不包含 `return` 陳述式的非同步方法，或包含不會傳回運算元的 `return` 陳述式的非同步方法，通常具有傳回型別 <xref:System.Threading.Tasks.Task>。 這類方法如果以同步方式執行，會傳回 `void`。 如果您針對非同步方法使用 <xref:System.Threading.Tasks.Task> 傳回型別，則除非被呼叫的非同步方法完成，否則呼叫的方法可以使用 `await` 運算子暫止呼叫端完成。

在下列範例中， `WaitAndApologizeAsync` 方法不包含 `return` 語句，因此方法會傳回 <xref:System.Threading.Tasks.Task> 物件。 傳回可 `Task` 等候 `WaitAndApologizeAsync` 。 <xref:System.Threading.Tasks.Task>型別不包含 `Result` 屬性，因為它沒有傳回值。

:::code language="csharp" source="snippets/async-return-types/async-returns2.cs" id="TaskReturn":::

`WaitAndApologizeAsync` 是透過使用 await 陳述式而非 await 運算式成為等候的，類似同步 void 傳回方法的呼叫陳述式。 在此情況下，await 運算子的應用不會產生值。 若要澄清詞彙語句和運算式，請參閱下表：

| Await 種類 | 範例                                      | 類型                                   |
|------------|----------------------------------------------|----------------------------------------|
| 引數  | `await SomeTaskMethodAsync()`                | <xref:System.Threading.Tasks.Task>     |
| 運算式 | `T result = await SomeTaskMethodAsync<T>();` | <xref:System.Threading.Tasks.Task%601> |

您可以將的呼叫與 `WaitAndApologizeAsync` await 運算子的應用程式分開，如下列程式碼所示。 不過，請記住，`Task` 沒有 `Result` 屬性，且將 await 運算子套用至 `Task` 時不會產生任何值。

下列程式碼隔開呼叫 `WaitAndApologizeAsync` 方法與等候方法傳回的工作。

:::code language="csharp" source="snippets/async-return-types/async-returns2a.cs" id="AwaitTask":::

## <a name="tasktresult-return-type"></a>工作傳回 \<TResult\> 類型

傳回 <xref:System.Threading.Tasks.Task%601> 型別用於非同步方法，其中包含運算元為的 [return](../../../language-reference/keywords/return.md) 語句 `TResult` 。

在下列範例中， `GetLeisureHoursAsync` 方法包含會傳回 `return` 整數的語句。 因此，方法宣告必須指定 `Task<int>` 傳回型別。 非同步方法是傳回之作業的 <xref:System.Threading.Tasks.Task.FromResult%2A> 預留位置 <xref:System.DateTime.DayOfWeek> 。

:::code language="csharp" source="snippets/async-return-types/async-returns1.cs" id="LeisureHours":::

從 `ShowTodaysInfo` 方法的 await 運算式內呼叫 `GetLeisureHoursAsync` 時，await 運算式會擷取儲存在 `GetLeisureHours` 方法所傳回之工作中的整數值 (`leisureHours` 的值)。 如需 await 運算式的詳細資訊，請參閱 [await](../../../language-reference/operators/await.md)。

`await` `Task<T>` `GetLeisureHoursAsync` 如下列程式碼所示，您可以進一步瞭解如何從的應用程式分隔呼叫，以抓取的結果 `await` 。 呼叫不會立即等候的 `GetLeisureHoursAsync` 方法，會傳回 `Task<int>`，如您所預期的方法宣告。 在範例中，工作會指派給 `getLeisureHoursTask` 變數。 因為 `getLeisureHoursTask` 是 <xref:System.Threading.Tasks.Task%601>，所以它包含 `TResult` 類型的 <xref:System.Threading.Tasks.Task%601.Result> 屬性。 在本例中，`TResult` 代表整數類型。 當 `await` 套用至 `getLeisureHoursTask` 時，await 運算式評估為 `getLeisureHoursTask` 之 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性的內容。 值會指派給 `ret` 變數。

> [!IMPORTANT]
> <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性是封鎖的屬性。 如果您嘗試在其工作完成之前先存取它，目前使用中的執行緒會封鎖，直到工作完成並且有可用的值為止。 在大部分情況下，您應該使用 `await` 來存取值，而不是直接存取屬性。
>
> 先前的範例抓取了屬性的值 <xref:System.Threading.Tasks.Task%601.Result%2A> 來封鎖主執行緒，讓 `Main` 方法可以在 `message` 應用程式結束之前將輸出到主控台。

:::code language="csharp" source="snippets/async-return-types/async-returns1a.cs" id="StoreTask":::

## <a name="void-return-type"></a> Void 傳回型別

您在非同步事件處理常式中使用 `void` 傳回型別，這需要 `void` 傳回型別。 對於不傳回值的事件處理常式以外的方法，您應該要改傳回 <xref:System.Threading.Tasks.Task>，因為傳回 `void` 的非同步方法不能是等候的。 這類方法的任何呼叫端都必須繼續完成，而不需等待來電的非同步方法完成。 呼叫端必須獨立于非同步方法所產生的任何值或例外狀況。

傳回 void 的非同步方法的呼叫端無法攔截方法擲回的例外狀況，而這類未處理的例外狀況可能會導致您的應用程式失敗。 如果傳回或的方法擲 <xref:System.Threading.Tasks.Task> 回 <xref:System.Threading.Tasks.Task%601> 例外狀況，則例外狀況會儲存在傳回的工作中。 等候工作時，會重新擲回例外狀況。 因此，請確定任何可能會產生例外狀況的非同步方法具有傳回型別 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>，且會等候對方法的呼叫。

如需如何在非同步方法中攔截例外狀況的詳細資訊，請參閱[try-catch](../../../language-reference/keywords/try-catch.md)文章的[非同步方法中的例外](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods)狀況一節。

下列範例示範非同步事件處理常式的行為。 在範例程式碼中，非同步事件處理常式必須讓主執行緒知道它完成的時間。 然後主執行緒可以等候非同步事件處理常式完成，再結束程式。

:::code language="csharp" source="snippets/async-return-types/async-returns3.cs":::

## <a name="generalized-async-return-types-and-valuetasktresult"></a>通用的非同步傳回型別和 ValueTask\<TResult\>

自 C# 7.0 開始，非同步方法可以傳回具有可存取 `GetAwaiter` 方法的任何型別。

因為 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 是參考型別，所以效能關鍵路徑中的記憶體配置，會對效能造成不良影響，特別是當配置出現在緊密迴圈中時。 支援通用的傳回型別，表示您可以傳回輕量型的實值型別，而不是參考型別，以避免額外的記憶體配置。

.NET 提供 <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> 結構作為通用工作傳回值的輕量級實作。 若要使用 <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> 類型，您必須將 `System.Threading.Tasks.Extensions` NuGet 套件新增至專案。 下列範例會使用 <xref:System.Threading.Tasks.ValueTask%601> 結構，擷取擲兩次骰子的值。

:::code language="csharp" source="snippets/async-return-types/async-valuetask.cs":::

## <a name="async-streams-with-iasyncenumerablet"></a>使用 IAsyncEnumerable 的非同步資料流程\<T\>

從 c # 8.0 開始，非同步方法可能會傳回以表示的 *非同步資料流程* <xref:System.Collections.Generic.IAsyncEnumerable%601> 。 非同步資料流程會提供一種方法，以列舉在具有重複非同步呼叫的區塊中產生專案時，從資料流程讀取的專案。 下列範例顯示會產生非同步資料流程的非同步方法：

:::code language="csharp" source="snippets/async-return-types/AsyncStreams.cs" id="GenerateAsyncStream":::

上述範例會以非同步方式讀取字串中的行。 讀取每一行之後，程式碼就會列舉字串中的每個字。 呼叫端會使用語句來列舉每個字 `await foreach` 。 當方法需要以非同步方式從來源字串讀取下一行時，方法就會等候。

## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [在非同步工作完成時進行處理](start-multiple-async-tasks-and-process-them-as-they-complete.md)
- [使用 async 和 await 進行非同步程式設計 (c # ) ](index.md)
- [async](../../../language-reference/keywords/async.md)
- [await](../../../language-reference/operators/await.md)
