---
title: 非同步方法的傳回型別 (C#)
ms.date: 04/14/2020
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: 73a6e1924652c8635377547e2faddc864ac5540a
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389139"
---
# <a name="async-return-types-c"></a>非同步方法的傳回型別 (C#)

非同步方法可有下列傳回型別：

- 傳回值的非同步方法為 <xref:System.Threading.Tasks.Task%601>。
- 執行作業但不傳回任何值的非同步方法為 <xref:System.Threading.Tasks.Task>。
- 處理常式為 `void`。
- 自 C# 7.0 開始，任何具有可存取 `GetAwaiter` 方法的型別。 `GetAwaiter` 方法傳回的物件必須實作 <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> 介面。
- 從 C# 8.0<xref:System.Collections.Generic.IAsyncEnumerable%601>開始,對於返回*非同步流的*非同步方法。

如需非同步方法的詳細資訊，請參閱[使用 async 和 await 進行非同步程式設計 (C#)](./index.md)。  
  
## <a name="tasktresult-return-type"></a> Task\<TResult\> 傳回型別  
傳<xref:System.Threading.Tasks.Task%601>回 型態包含[傳回](../../../language-reference/keywords/return.md)(C#) 語句的非同步方法`TResult`,其中操作數為 。  
  
在下列範例中，`GetLeisureHours` 非同步方法包含一個傳回整數的 `return` 陳述式。 因此，方法宣告必須指定 `Task<int>` 傳回型別。  <xref:System.Threading.Tasks.Task.FromResult%2A> 非同步方法是傳回字串作業的預留位置。
  
:::code language="csharp" source="./snippets/async-returns1.cs" id="SnippetFirstExample":::

從 `ShowTodaysInfo` 方法的 await 運算式內呼叫 `GetLeisureHours` 時，await 運算式會擷取儲存在 `GetLeisureHours` 方法所傳回之工作中的整數值 (`leisureHours` 的值)。 如需 await 運算式的詳細資訊，請參閱 [await](../../../language-reference/operators/await.md)。  
  
正如以下代碼所示,`await`通過將調用與`Task<T>``GetLeisureHours``await`應用程式 分離,可以更好地瞭解如何從 中檢索結果。 呼叫不會立即等候的 `GetLeisureHours` 方法，會傳回 `Task<int>`，如您所預期的方法宣告。 在範例中，工作會指派給 `integerTask` 變數。 因為 `integerTask` 是 <xref:System.Threading.Tasks.Task%601>，所以它包含 `TResult` 類型的 <xref:System.Threading.Tasks.Task%601.Result> 屬性。 在本例中，`TResult` 代表整數類型。 當 `await` 套用至 `integerTask` 時，await 運算式評估為 `integerTask` 之 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性的內容。 值會指派給 `ret` 變數。  
  
> [!IMPORTANT]
> <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性是封鎖的屬性。 如果您嘗試在其工作完成之前先存取它，目前使用中的執行緒會封鎖，直到工作完成並且有可用的值為止。 在大部分情況下，您應該使用 `await` 來存取值，而不是直接存取屬性。 <br/> 前一個範例擷取 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性的值，封鎖主執行緒，讓 `ShowTodaysInfo` 方法在應用程式結束之前可以完成執行。  

:::code language="csharp" source="./snippets/async-returns1a.cs" id="SnippetSecondVersion":::

## <a name="task-return-type"></a>工作傳回型別  
不包含 `return` 陳述式的非同步方法，或包含不會傳回運算元的 `return` 陳述式的非同步方法，通常具有傳回型別 <xref:System.Threading.Tasks.Task>。 這類方法如果以同步方式執行，會傳回 `void`。 如果您針對非同步方法使用 <xref:System.Threading.Tasks.Task> 傳回型別，則除非被呼叫的非同步方法完成，否則呼叫的方法可以使用 `await` 運算子暫止呼叫端完成。  
  
在下列範例中，`WaitAndApologize` 非同步方法不包含 `return` 陳述式，所以方法傳回 <xref:System.Threading.Tasks.Task> 物件。 返回要`Task`等待`WaitAndApologize`的啟用。 類型<xref:System.Threading.Tasks.Task>不包括屬性`Result`, 因為它沒有返回值。  

:::code language="csharp" source="./snippets/async-returns2.cs" id="SnippetTaskReturn":::

`WaitAndApologize` 是透過使用 await 陳述式而非 await 運算式成為等候的，類似同步 void 傳回方法的呼叫陳述式。 在此情況下，await 運算子的應用不會產生值。  
  
如先前的 <xref:System.Threading.Tasks.Task%601> 範例所示，您可以隔開對 `WaitAndApologize` 的呼叫和 await 運算子的應用程式，如下列程式碼所示。 不過，請記住，`Task` 沒有 `Result` 屬性，且將 await 運算子套用至 `Task` 時不會產生任何值。  
  
下列程式碼隔開呼叫 `WaitAndApologize` 方法與等候方法傳回的工作。  

:::code language="csharp" source="./snippets/async-returns2a.cs" id="SnippetAwaitTask":::

## <a name="void-return-type"></a> Void 傳回型別

您在非同步事件處理常式中使用 `void` 傳回型別，這需要 `void` 傳回型別。 對於不傳回值的事件處理常式以外的方法，您應該要改傳回 <xref:System.Threading.Tasks.Task>，因為傳回 `void` 的非同步方法不能是等候的。 此方法的任何調用方都必須繼續完成,而無需等待調用的非同步方法完成。 調用方必須獨立於非同步方法生成的任何值或異常。  
  
void 返回非同步方法的調用方無法捕獲從 該方法引發的異常,並且此類未處理的異常可能會導致應用程式失敗。 如果返回<xref:System.Threading.Tasks.Task><xref:System.Threading.Tasks.Task%601>或引發異常的方法,則異常存儲在返回的任務中。 等待任務時,將重新引發異常。 因此，請確定任何可能會產生例外狀況的非同步方法具有傳回型別 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>，且會等候對方法的呼叫。  
  
有關如何捕獲異步方法中的異常的詳細資訊,請參閱[try-catch](../../../language-reference/keywords/try-catch.md)一文[的「非同步方法」](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods)部分中的異常。  
  
下列範例示範非同步事件處理常式的行為。 在示例代碼中,非同步事件處理程式必須讓主線程知道何時完成。 然後主執行緒可以等候非同步事件處理常式完成，再結束程式。

:::code language="csharp" source="./snippets/async-returns3.cs":::

## <a name="generalized-async-return-types-and-valuetasktresult"></a>通用的非同步傳回型別和 ValueTask\<TResult\>

自 C# 7.0 開始，非同步方法可以傳回具有可存取 `GetAwaiter` 方法的任何型別。

因為 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 是參考型別，所以效能關鍵路徑中的記憶體配置，會對效能造成不良影響，特別是當配置出現在緊密迴圈中時。 支援通用的傳回型別，表示您可以傳回輕量型的實值型別，而不是參考型別，以避免額外的記憶體配置。

.NET 提供 <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> 結構作為通用工作傳回值的輕量級實作。 若要使用 <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> 類型，您必須將 `System.Threading.Tasks.Extensions` NuGet 套件新增至專案。 下列範例會使用 <xref:System.Threading.Tasks.ValueTask%601> 結構，擷取擲兩次骰子的值。
  
:::code language="csharp" source="./snippets/async-valuetask.cs":::

## <a name="async-streams-with-iasyncenumerablet"></a>具有 IAsync 可\<數 T 的非同步\>

從 C# 8.0 開始,非同步方法可以<xref:System.Collections.Generic.IAsyncEnumerable%601>傳回由 表示*的非同步流*。 非同步提供一種在具有重複非同步調用的塊中生成元素時從流中讀取的專案的枚舉方法。 下面的範例顯示了生成非同步串流的非同步方法:

:::code language="csharp" source="./snippets/AsyncStreams.cs" id="SnippetGenerateAsyncStream":::

前面的範例非同步地從字串中讀取行。 讀取每行後,代碼將枚舉字串中的每個單詞。 調用方將使用`await foreach`語句枚舉每個單詞。 當需要從源字串非同步讀取下一行時,該方法將等待。

## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [逐步解說：使用 async 和 await 存取 Web (C#)](./walkthrough-accessing-the-web-by-using-async-and-await.md)
- [同步程式中的控制串流 (C#)](./control-flow-in-async-programs.md)
- [async](../../../language-reference/keywords/async.md)
- [等待](../../../language-reference/operators/await.md)
