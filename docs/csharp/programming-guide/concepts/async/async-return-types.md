---
title: 非同步方法的傳回型別 (C#)
ms.date: 04/14/2020
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: c2584f1e285a7ab76eb43f9a211a8d2a51c2c55e
ms.sourcegitcommit: c76c8b2c39ed2f0eee422b61a2ab4c05ca7771fa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/21/2020
ms.locfileid: "83761872"
---
# <a name="async-return-types-c"></a>非同步方法的傳回型別 (C#)

非同步方法可有下列傳回型別：

- 傳回值的非同步方法為 <xref:System.Threading.Tasks.Task%601>。
- 執行作業但不傳回任何值的非同步方法為 <xref:System.Threading.Tasks.Task>。
- 處理常式為 `void`。
- 自 C# 7.0 開始，任何具有可存取 `GetAwaiter` 方法的型別。 `GetAwaiter` 方法傳回的物件必須實作 <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> 介面。
- 從 c # 8.0 開始， <xref:System.Collections.Generic.IAsyncEnumerable%601> 適用于傳回*非同步資料流程*的非同步方法。

如需非同步方法的詳細資訊，請參閱[使用 async 和 await 進行非同步程式設計 (C#)](./index.md)。  
  
## <a name="tasktresult-return-type"></a> Task\<TResult\> 傳回型別  
傳回 <xref:System.Threading.Tasks.Task%601> 型別用於非同步方法，其中包含[return](../../../language-reference/keywords/return.md) （c #）語句，其中運算元為 `TResult` 。  
  
在下列範例中，`GetLeisureHours` 非同步方法包含一個傳回整數的 `return` 陳述式。 因此，方法宣告必須指定 `Task<int>` 傳回型別。  <xref:System.Threading.Tasks.Task.FromResult%2A> 非同步方法是傳回字串作業的預留位置。
  
:::code language="csharp" source="./snippets/async-return-types/async-returns1.cs" id="SnippetFirstExample":::

從 `ShowTodaysInfo` 方法的 await 運算式內呼叫 `GetLeisureHours` 時，await 運算式會擷取儲存在 `GetLeisureHours` 方法所傳回之工作中的整數值 (`leisureHours` 的值)。 如需 await 運算式的詳細資訊，請參閱 [await](../../../language-reference/operators/await.md)。  
  
`await` `Task<T>` `GetLeisureHours` `await` 如下列程式碼所示，您可以藉由區隔對的呼叫，以進一步瞭解如何從取得的結果。 呼叫不會立即等候的 `GetLeisureHours` 方法，會傳回 `Task<int>`，如您所預期的方法宣告。 在範例中，工作會指派給 `integerTask` 變數。 因為 `integerTask` 是 <xref:System.Threading.Tasks.Task%601>，所以它包含 `TResult` 類型的 <xref:System.Threading.Tasks.Task%601.Result> 屬性。 在本例中，`TResult` 代表整數類型。 當 `await` 套用至 `integerTask` 時，await 運算式評估為 `integerTask` 之 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性的內容。 值會指派給 `ret` 變數。  
  
> [!IMPORTANT]
> <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性是封鎖的屬性。 如果您嘗試在其工作完成之前先存取它，目前使用中的執行緒會封鎖，直到工作完成並且有可用的值為止。 在大部分情況下，您應該使用 `await` 來存取值，而不是直接存取屬性。 <br/> 前一個範例擷取 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性的值，封鎖主執行緒，讓 `ShowTodaysInfo` 方法在應用程式結束之前可以完成執行。  

:::code language="csharp" source="./snippets/async-return-types/async-returns1a.cs" id="SnippetSecondVersion":::

## <a name="task-return-type"></a>工作傳回型別  
不包含 `return` 陳述式的非同步方法，或包含不會傳回運算元的 `return` 陳述式的非同步方法，通常具有傳回型別 <xref:System.Threading.Tasks.Task>。 這類方法如果以同步方式執行，會傳回 `void`。 如果您針對非同步方法使用 <xref:System.Threading.Tasks.Task> 傳回型別，則除非被呼叫的非同步方法完成，否則呼叫的方法可以使用 `await` 運算子暫止呼叫端完成。  
  
在下列範例中，`WaitAndApologize` 非同步方法不包含 `return` 陳述式，所以方法傳回 <xref:System.Threading.Tasks.Task> 物件。 傳回可等候的 `Task` `WaitAndApologize` 。 <xref:System.Threading.Tasks.Task>類型並未包含 `Result` 屬性，因為它沒有傳回值。  

:::code language="csharp" source="./snippets/async-return-types/async-returns2.cs" id="SnippetTaskReturn":::

`WaitAndApologize` 是透過使用 await 陳述式而非 await 運算式成為等候的，類似同步 void 傳回方法的呼叫陳述式。 在此情況下，await 運算子的應用不會產生值。  
  
如先前的 <xref:System.Threading.Tasks.Task%601> 範例所示，您可以隔開對 `WaitAndApologize` 的呼叫和 await 運算子的應用程式，如下列程式碼所示。 不過，請記住，`Task` 沒有 `Result` 屬性，且將 await 運算子套用至 `Task` 時不會產生任何值。  
  
下列程式碼隔開呼叫 `WaitAndApologize` 方法與等候方法傳回的工作。  

:::code language="csharp" source="./snippets/async-return-types/async-returns2a.cs" id="SnippetAwaitTask":::

## <a name="void-return-type"></a> Void 傳回型別

您在非同步事件處理常式中使用 `void` 傳回型別，這需要 `void` 傳回型別。 對於不傳回值的事件處理常式以外的方法，您應該要改傳回 <xref:System.Threading.Tasks.Task>，因為傳回 `void` 的非同步方法不能是等候的。 這種方法的任何呼叫端都必須繼續完成，而不需要等候呼叫的非同步方法完成。 呼叫端必須獨立于非同步方法所產生的任何值或例外狀況。  
  
傳回 void 的非同步方法的呼叫端無法攔截方法擲回的例外狀況，而且這類未處理的例外狀況可能會導致您的應用程式失敗。 如果傳回或的方法擲 <xref:System.Threading.Tasks.Task> 回 <xref:System.Threading.Tasks.Task%601> 例外狀況，則例外狀況會儲存在傳回的工作中。 等待工作時，會重新擲回例外狀況。 因此，請確定任何可能會產生例外狀況的非同步方法具有傳回型別 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>，且會等候對方法的呼叫。  
  
如需如何在非同步方法中攔截例外狀況的詳細資訊，請參閱[try-catch](../../../language-reference/keywords/try-catch.md)文章的[async 方法](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods)一節中的例外狀況。  
  
下列範例示範非同步事件處理常式的行為。 在範例程式碼中，非同步事件處理常式必須讓主執行緒知道其完成時間。 然後主執行緒可以等候非同步事件處理常式完成，再結束程式。

:::code language="csharp" source="./snippets/async-return-types/async-returns3.cs":::

## <a name="generalized-async-return-types-and-valuetasktresult"></a>通用的非同步傳回型別和 ValueTask\<TResult\>

自 C# 7.0 開始，非同步方法可以傳回具有可存取 `GetAwaiter` 方法的任何型別。

因為 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 是參考型別，所以效能關鍵路徑中的記憶體配置，會對效能造成不良影響，特別是當配置出現在緊密迴圈中時。 支援通用的傳回型別，表示您可以傳回輕量型的實值型別，而不是參考型別，以避免額外的記憶體配置。

.NET 提供 <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> 結構作為通用工作傳回值的輕量級實作。 若要使用 <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> 類型，您必須將 `System.Threading.Tasks.Extensions` NuGet 套件新增至專案。 下列範例會使用 <xref:System.Threading.Tasks.ValueTask%601> 結構，擷取擲兩次骰子的值。
  
:::code language="csharp" source="./snippets/async-return-types/async-valuetask.cs":::

## <a name="async-streams-with-iasyncenumerablet"></a>具有 IAsyncEnumerable T 的非同步資料流程 \<\>

從 c # 8.0 開始，非同步方法可能會傳回以表示的*非同步資料流程* <xref:System.Collections.Generic.IAsyncEnumerable%601> 。 當以重複非同步呼叫的區塊產生元素時，非同步資料流程提供了一種方法來列舉從資料流程讀取的專案。 下列範例顯示會產生非同步資料流程的非同步方法：

:::code language="csharp" source="./snippets/async-return-types/AsyncStreams.cs" id="SnippetGenerateAsyncStream":::

上述範例會以非同步方式讀取字串中的行。 讀取每一行之後，程式碼會列舉字串中的每個字。 呼叫端會使用語句來列舉每個字組 `await foreach` 。 方法會等候何時需要以非同步方式讀取來源字串中的下一行。

## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [逐步解說：使用 async 和 await 存取 Web (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [非同步程式中的控制流程（c #）](./control-flow-in-async-programs.md)
- [async](../../../language-reference/keywords/async.md)
- [遇到](../../../language-reference/operators/await.md)
