---
title: await (C# 參考)
ms.date: 05/22/2017
f1_keywords:
- await_CSharpKeyword
helpviewer_keywords:
- await keyword [C#]
- await [C#]
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
ms.openlocfilehash: e32c7007ca98ce2153386665b60c45ff9e90cc3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="await-c-reference"></a>await (C# 參考)
`await` 運算子會套用至非同步方法中的工作，以在執行方法中插入暫停點，直到等候的工作完成為止。 工作代表進行中的工作。  
  
`await` 只能用於 [async](../../../csharp/language-reference/keywords/async.md) 關鍵字所修改的非同步方法中。 這種方法是使用 `async` 修飾詞所定義，且通常包含一或多個 `await` 運算式，我們稱之為「非同步方法」。  
  
> [!NOTE]
>  `async` 和 `await` 關鍵字是在 C# 5 中引入。 如需非同步程式設計的簡介，請參閱[使用 async 和 await 進行非同步程式設計](../../../csharp/programming-guide/concepts/async/index.md)。  
  
套用了 `await` 運算子的工作，通常是呼叫傳回給實作[工作式非同步模式](../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)的方法。 它們包括傳回 <xref:System.Threading.Tasks.Task>、<xref:System.Threading.Tasks.Task%601> 和 `System.Threading.Tasks.ValueType<TResult>` 物件的方法。  

  
 在下列範例中，<xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A?displayProperty=nameWithType> 方法會傳回 `Task<byte[]>`。 這個工作可保證工作完成時，一定會產生實際位元組陣列。 `await` 運算子會暫停執行，直到 <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> 方法的工作完成為止。 同時，控制權會返回 `GetPageSizeAsync` 的呼叫端。 在工作執行完成後，`await` 運算式評估為位元組陣列。  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await1.cs)]  

> [!IMPORTANT]
>  如需完整範例，請參閱[逐步解說：使用 async 和 await 存取 Web](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。 您可以從 Microsoft 網站的[開發人員程式碼範例](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) 下載此範例。 此範例位於 AsyncWalkthrough_HttpClient 專案中。  
  
如先前範例所示，如果將 `await` 套用至傳回 `Task<TResult>` 之方法呼叫的結果，則 `await` 運算式的類型為 `TResult`。 如果將 `await` 套用至傳回 `Task` 之方法呼叫的結果，則 `await` 運算式的類型為 `void`。 下列範例會說明其間的差異。  
  
```csharp  
// await keyword used with a method that returns a Task<TResult>.  
TResult result = await AsyncMethodThatReturnsTaskTResult();  
  
// await keyword used with a method that returns a Task.  
await AsyncMethodThatReturnsTask();  

// await keyword used with a method that returns a ValueTask<TResult>.
TResult result = await AsyncMethodThatReturnsValueTaskTResult();
```  
  
`await` 運算式不會封鎖其執行所在的執行緒。 但是它會造成編譯器將其餘非同步方法註冊為所等候工作的接續。 控制權接著會返回非同步方法的呼叫端。 當工作完成時，它會叫用其接續，並從中斷處繼續執行非同步方法。  
  
`await` 運算式只會出現在必須以 `async` 修飾詞標示的封入方法、Lambda 運算式或匿名方法的主體中。 *await* 這個詞彙只在該內容中作為關鍵字。 在其他內容中，它會解譯為識別項。 在方法、Lambda 運算式或匿名方法中，`await` 運算式不能出現在同步函式、查詢運算式、[lock 陳述式](../../../csharp/language-reference/keywords/lock-statement.md)的區塊，或是 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 內容中。  
  
## <a name="exceptions"></a>例外狀況  
大部分的非同步方法會傳回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>。 傳回的工作屬性會隨附其狀態和記錄的相關資訊，例如工作是否完成、非同步方法是否造成例外狀況或已取消，以及最終結果為何。 `await` 運算子透過呼叫 `GetAwaiter` 方法所傳回之物件上的方法，來存取這些屬性。  
  
如果您在等候工作傳回非同步方法時導致例外狀況，`await` 運算子會重新擲回例外狀況。  
  
如果您等候已取消的工作傳回非同步方法，則 `await` 運算子會重新擲回 <xref:System.OperationCanceledException>。  
  
處於錯誤狀態的單一工作可能反映多個例外狀況。 例如，工作可能是對 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> 呼叫的結果。 當您等候這類工作時，await 作業只會重新擲回其中一個例外狀況。 不過，您無法預測重新擲回哪個例外狀況。  
  
如需非同步方法中錯誤處理的範例，請參閱 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)。  
  
## <a name="example"></a>範例  
下列範例會傳回頁面的總字元數，這些頁面的 URL 會傳遞給它當做命令列引數。 本例會呼叫 `GetPageLengthsAsync` 方法，這會以 `async` 關鍵字標示。 `GetPageLengthsAsync` 方法接著會使用 `await` 關鍵字來等候對 <xref:System.Net.Http.HttpClient.GetStringAsync%2A?displayProperty=nameWithType> 方法的呼叫。  

[!code-csharp[await-example](../../../../samples/snippets/csharp/language-reference/keywords/await/await2.cs)]  

因為不支援在應用程式進入點中使用 `async` 和 `await`，所以我們無法將 `async` 屬性套用至 `Main` 方法，也不能等候 `GetPageLengthsAsync` 方法呼叫。 擷取 <xref:System.Threading.Tasks.Task%601.Result?displayProperty=nameWithType> 屬性的值，以確保 `Main` 方法等候非同步作業完成。 針對不傳回值的工作，您可以呼叫 <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType> 方法。 

## <a name="see-also"></a>另請參閱  
[使用 async 和 await 進行非同步程式設計](../../../csharp/programming-guide/concepts/async/index.md)   
[逐步解說：使用 async 和 await 存取 Web](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
[async](../../../csharp/language-reference/keywords/async.md)
