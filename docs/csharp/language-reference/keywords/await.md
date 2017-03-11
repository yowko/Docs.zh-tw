---
title: "await (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "await_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "await [C#]"
  - "await 關鍵字 [C#]"
ms.assetid: 50725c24-ac76-4ca7-bca1-dd57642ffedb
caps.latest.revision: 36
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 36
---
# await (C# 參考)
`await` 運算子會套用至非同步方法中的工作以暫停執行方法，直到等候的工作完成為止。  工作代表進行中的工作。  
  
 在其中使用 `await` 的非同步方法必須由 [async](../../../csharp/language-reference/keywords/async.md) 關鍵字修改。  這種方法是使用 `async` 修飾詞所定義，且通常包含一或多個 `await` 運算式，我們稱之為*非同步方法*。  
  
> [!NOTE]
>  `async` 和 `await` 關鍵字是在 Visual Studio 2012 中引入。  如需非同步程式設計的簡介，請參閱[使用 Async 和 Await 設計非同步程式](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)。  
  
 `await` 運算子套用到的工作，通常是呼叫實作了[以工作為基礎的非同步模式](http://go.microsoft.com/fwlink/?LinkId=204847) \(英文\) 的方法所傳回的值。  範例包括類型 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 的值。  
  
 在下列程式碼中，<xref:System.Net.Http.HttpClient> 方法 <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> 會傳回 `Task<byte[]>`，也就是 `getContentsTask`。  這個工作可保證工作完成時，一定會產生實際位元組陣列。  `await` 運算子會套用至 `getContentsTask` 以暫停在 `SumPageSizesAsync` 中執行，直到 `getContentsTask` 完成。  同時，控制權會返回 `SumPageSizesAsync` 的呼叫端。  當 `getContentsTask` 完成之後，`await` 運算式會評估為位元組陣列。  
  
```c#  
  
private async Task SumPageSizesAsync()  
{  
    // To use the HttpClient type in desktop apps, you must include a using directive and add a   
    // reference for the System.Net.Http namespace.  
    HttpClient client = new HttpClient();  
    // . . .  
    Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);  
    byte[] urlContents = await getContentsTask;  
  
    // Equivalently, now that you see how it works, you can write the same thing in a single line.  
    //byte[] urlContents = await client.GetByteArrayAsync(url);  
    // . . .  
}  
  
```  
  
> [!IMPORTANT]
>  如需完整範例，請參閱[逐步解說：使用 Async 和 Await 存取 Web](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)。  您可以在 Microsoft 網站上，從[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkID=255191&clcid=0x409) \(英文\) 下載範例。  此範例位於 AsyncWalkthrough\_HttpClient 專案中。  
  
 如先前範例所示，如果將 `await` 套用至傳回 `Task<TResult>` 之方法呼叫的結果，則 `await` 運算式的類型為 TResult。  如果將 `await` 套用至傳回 `Task` 之方法呼叫的結果，則 `await` 運算式的類型為 void。  下列範例會說明其間的差異。  
  
```c#  
// Keyword await used with a method that returns a Task<TResult>.  
TResult result = await AsyncMethodThatReturnsTaskTResult();  
  
// Keyword await used with a method that returns a Task.  
await AsyncMethodThatReturnsTask();  
  
```  
  
 `await` 運算式不會封鎖其執行所在的執行緒。  但是它會造成編譯器將其餘非同步方法註冊為所等候工作的接續。  控制權接著會返回非同步方法的呼叫端。  當工作完成時，它會叫用其接續，並從中斷處繼續執行非同步方法。  
  
 `await` 運算式可能只會在 `async` 修飾詞所標示之立即封入方法、Lambda 運算式或匿名方法的主體中發生。  *await* 這個詞彙只在該內容中做為關鍵字。  在其他內容中，它會解譯為識別項。  在方法、Lambda 運算式或匿名方法中，`await` 運算式不能出現在同步函式、查詢運算式、[lock 陳述式](../../../csharp/language-reference/keywords/lock-statement.md)的區塊，或是 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 內容中。  
  
## 例外狀況  
 大部分的非同步方法會傳回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>。  傳回的工作屬性會隨附其狀態和記錄的相關資訊，例如工作是否完成、非同步方法是否造成例外狀況或已取消，以及最終結果為何。  `await` 運算子存取這些屬性。  
  
 如果您在等候工作傳回非同步方法時導致例外狀況，`await` 運算子會重新擲回例外狀況。  
  
 如果您等候已取消的工作傳回非同步方法，則 `await` 運算子會重新擲回 <xref:System.OperationCanceledException>。  
  
 處於錯誤狀態的單一工作可能反映多個例外狀況。  例如，工作可能是對 <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> 呼叫的結果。  當您等候這類工作時，await 作業只會重新擲回其中一個例外狀況。  不過，您無法預測重新擲回哪個例外狀況。  
  
 如需在非同步方法中錯誤處理的範例，請參閱 [try\-catch](../../../csharp/language-reference/keywords/try-catch.md)。  
  
## 範例  
 下列 Windows Form 範例說明如何在非同步方法 `WaitAsynchronouslyAsync` 中使用 `await`。  請對照該方法的行為與 `WaitSynchronously` 的行為。  若未將 `await` 運算子套用至工作，儘管在定義中使用 `WaitSynchronously` 修飾詞並在主體中呼叫 `async`，<xref:System.Threading.Thread.Sleep%2A?displayProperty=fullName> 仍會以同步方式執行。  
  
```c#  
  
private async void button1_Click(object sender, EventArgs e)  
{  
    // Call the method that runs asynchronously.  
    string result = await WaitAsynchronouslyAsync();  
  
    // Call the method that runs synchronously.  
    //string result = await WaitSynchronously ();  
  
    // Display the result.  
    textBox1.Text += result;  
}  
  
// The following method runs asynchronously. The UI thread is not  
// blocked during the delay. You can move or resize the Form1 window   
// while Task.Delay is running.  
public async Task<string> WaitAsynchronouslyAsync()  
{  
    await Task.Delay(10000);  
    return "Finished";  
}  
  
// The following method runs synchronously, despite the use of async.  
// You cannot move or resize the Form1 window while Thread.Sleep  
// is running because the UI thread is blocked.  
public async Task<string> WaitSynchronously()  
{  
    // Add a using directive for System.Threading.  
    Thread.Sleep(10000);  
    return "Finished";  
}  
```  
  
## 請參閱  
 [使用 Async 和 Await 設計非同步程式](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)   
 [逐步解說：使用 Async 和 Await 存取 Web](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)   
 [async](../../../csharp/language-reference/keywords/async.md)