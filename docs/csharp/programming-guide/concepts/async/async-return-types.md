---
title: 非同步方法的傳回型別 (C#)
ms.date: 05/29/2017
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
ms.openlocfilehash: ca429db9b3ad81555df3c7e02d8827136734e26c
ms.sourcegitcommit: 127343afce8422bfa944c8b0c4ecc8f79f653255
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2019
ms.locfileid: "67347747"
---
# <a name="async-return-types-c"></a>非同步方法的傳回型別 (C#)
非同步方法可有下列傳回型別：

- 傳回值的非同步方法為 <xref:System.Threading.Tasks.Task%601>。 
 
- 執行作業但不傳回任何值的非同步方法為 <xref:System.Threading.Tasks.Task>。

- 處理常式為 `void`。 

- 自 C# 7.0 開始，任何具有可存取 `GetAwaiter` 方法的型別。 `GetAwaiter` 方法傳回的物件必須實作 <xref:System.Runtime.CompilerServices.ICriticalNotifyCompletion?displayProperty=nameWithType> 介面。
  
如需非同步方法的詳細資訊，請參閱[使用 async 和 await 進行非同步程式設計 (C#)](../../../../csharp/programming-guide/concepts/async/index.md)。  
  
每個傳回型別在下列其中一節探討，您可以在主題結尾處找到使用全部三種類型的完整範例。  
  
## <a name="BKMK_TaskTReturnType"></a> Task\<TResult\> 傳回型別  
<xref:System.Threading.Tasks.Task%601> 傳回型別用於非同步方法，此方法包含 [return](../../../../csharp/language-reference/keywords/return.md) (C#) 陳述式，其運算元的類型為 `TResult`。  
  
在下列範例中，`GetLeisureHours` 非同步方法包含一個傳回整數的 `return` 陳述式。 因此，方法宣告必須指定 `Task<int>` 傳回型別。  <xref:System.Threading.Tasks.Task.FromResult%2A> 非同步方法是傳回字串作業的預留位置。
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1.cs)]

從 `ShowTodaysInfo` 方法的 await 運算式內呼叫 `GetLeisureHours` 時，await 運算式會擷取儲存在 `GetLeisureHours` 方法所傳回之工作中的整數值 (`leisureHours` 的值)。 如需 await 運算式的詳細資訊，請參閱 [await](../../../../csharp/language-reference/keywords/await.md)。  
  
您可以藉由區隔對 `GetLeisureHours` 的呼叫與 `await` 的應用，深入了解這種運作方式，如下列程式碼所示。 呼叫不會立即等候的 `GetLeisureHours` 方法，會傳回 `Task<int>`，如您所預期的方法宣告。 在範例中，工作會指派給 `integerTask` 變數。 因為 `integerTask` 是 <xref:System.Threading.Tasks.Task%601>，所以它包含 `TResult` 類型的 <xref:System.Threading.Tasks.Task%601.Result> 屬性。 在本例中，`TResult` 代表整數類型。 當 `await` 套用至 `integerTask` 時，await 運算式評估為 `integerTask` 之 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性的內容。 值會指派給 `ret` 變數。  
  
> [!IMPORTANT]
>  <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性是封鎖的屬性。 如果您嘗試在其工作完成之前先存取它，目前使用中的執行緒會封鎖，直到工作完成並且有可用的值為止。 在大部分情況下，您應該使用 `await` 來存取值，而不是直接存取屬性。 <br/> 前一個範例擷取 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性的值，封鎖主執行緒，讓 `ShowTodaysInfo` 方法在應用程式結束之前可以完成執行。  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns1a.cs#1)]
  
## <a name="BKMK_TaskReturnType"></a> 工作傳回型別  
不包含 `return` 陳述式的非同步方法，或包含不會傳回運算元的 `return` 陳述式的非同步方法，通常具有傳回型別 <xref:System.Threading.Tasks.Task>。 這類方法如果以同步方式執行，會傳回 `void`。 如果您針對非同步方法使用 <xref:System.Threading.Tasks.Task> 傳回型別，則除非被呼叫的非同步方法完成，否則呼叫的方法可以使用 `await` 運算子暫止呼叫端完成。  
  
在下列範例中，`WaitAndApologize` 非同步方法不包含 `return` 陳述式，所以方法傳回 <xref:System.Threading.Tasks.Task> 物件。 這就讓 `WaitAndApologize` 成為等候的。 請注意，<xref:System.Threading.Tasks.Task> 類型不包含 `Result` 屬性，因為它沒有傳回值。  

[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2.cs)]  
  
`WaitAndApologize` 是透過使用 await 陳述式而非 await 運算式成為等候的，類似同步 void 傳回方法的呼叫陳述式。 在此情況下，await 運算子的應用不會產生值。  
  
如先前的 <xref:System.Threading.Tasks.Task%601> 範例所示，您可以隔開對 `WaitAndApologize` 的呼叫和 await 運算子的應用程式，如下列程式碼所示。 不過，請記住，`Task` 沒有 `Result` 屬性，且將 await 運算子套用至 `Task` 時不會產生任何值。  
  
下列程式碼隔開呼叫 `WaitAndApologize` 方法與等候方法傳回的工作。  
 
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns2a.cs#1)]  
 
## <a name="BKMK_VoidReturnType"></a> Void 傳回型別

您在非同步事件處理常式中使用 `void` 傳回型別，這需要 `void` 傳回型別。 對於不傳回值的事件處理常式以外的方法，您應該要改傳回 <xref:System.Threading.Tasks.Task>，因為傳回 `void` 的非同步方法不能是等候的。 這種方法的任何呼叫端必須要能夠繼續完成而不需等待呼叫的非同步方法完成，且呼叫端必須與非同步方法產生的任何值或例外狀況無關。  
  
傳回 void 的非同步方法的呼叫端無法攔截方法擲回的例外狀況，這類未處理的例外狀況有可能造成應用程式失敗。 如果例外狀況發生在會傳回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 的非同步方法，則例外狀況會儲存在傳回的工作中，並在等候工作時再次擲回。 因此，請確定任何可能會產生例外狀況的非同步方法具有傳回型別 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>，且會等候對方法的呼叫。  
  
如需如何在非同步方法中攔截例外狀況的詳細資訊，請參閱 [try-catch](../../../language-reference/keywords/try-catch.md) 主題的[非同步方法中的例外狀況](../../../language-reference/keywords/try-catch.md#exceptions-in-async-methods)一節。  
  
下列範例示範非同步事件處理常式的行為。 請注意，在範例程式碼中，非同步事件處理常式完成時必須讓主執行緒知道。 然後主執行緒可以等候非同步事件處理常式完成，再結束程式。
 
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-returns3.cs)]  
 
## <a name="generalized-async-return-types-and-valuetasktresult"></a>通用的非同步傳回型別和 ValueTask\<TResult\>

自 C# 7.0 開始，非同步方法可以傳回具有可存取 `GetAwaiter` 方法的任何型別。
 
因為 <xref:System.Threading.Tasks.Task> 和 <xref:System.Threading.Tasks.Task%601> 是參考型別，所以效能關鍵路徑中的記憶體配置，會對效能造成不良影響，特別是當配置出現在緊密迴圈中時。 支援通用的傳回型別，表示您可以傳回輕量型的實值型別，而不是參考型別，以避免額外的記憶體配置。 

.NET 提供 <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> 結構作為通用工作傳回值的輕量級實作。 若要使用 <xref:System.Threading.Tasks.ValueTask%601?displayProperty=nameWithType> 類型，您必須將 `System.Threading.Tasks.Extensions` NuGet 套件新增至專案。 下列範例會使用 <xref:System.Threading.Tasks.ValueTask%601> 結構，擷取擲兩次骰子的值。 
  
[!code-csharp[return-value](../../../../../samples/snippets/csharp/programming-guide/async/async-valuetask.cs)]

## <a name="see-also"></a>另請參閱

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [逐步解說：使用 Async 和 Await 存取 Web (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [非同步程式中的控制流程 (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)
- [async](../../../../csharp/language-reference/keywords/async.md)
- [await](../../../../csharp/language-reference/keywords/await.md)
