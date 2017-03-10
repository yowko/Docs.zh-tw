---
title: "async (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "async_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "async [C#]"
  - "async 關鍵字 [C#]"
  - "async 方法 [C#]"
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
caps.latest.revision: 52
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 52
---
# async (C# 參考)
使用 `async` 修飾詞可將方法、[Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)或[匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)指定為非同步。  如果您在方法或運算式上使用這個修飾詞，則它是指非同步方法。  
  
```c#  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
  
```  
  
 如果您不熟悉非同步程式設計或不了解非同步方法如何使用 `await` 關鍵字進行可能需要長期執行的工作，而不封鎖呼叫端執行緒，建議您閱讀[使用 Async 和 Await 設計非同步程式](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md) 的簡介。  
  
```  
string contents = await contentsTask;  
```  
  
 方法會以同步方式執行，直到抵達第一個 `await` 運算式，此時方法會暫停，直到等候的工作完成。  同時，控制項會返回方法的呼叫端，如下一節中的範例所示。  
  
 如果 `async` 關鍵字修改的方法不包含 `await` 運算式或陳述式，則方法會以同步方式執行。  如果有任何非同步方法未包含 `await`，編譯器警告就會發出警示，因為這種情況可能表示發生錯誤。  請參閱 [編譯器警告 \(層級 1\) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md)。  
  
 `async` 關鍵字與內容相關，它只有在修改方法、Lambda 運算式或匿名方法時，才是關鍵字。  在所有其他內容中，它會解譯為識別項。  
  
## 範例  
 下列範例將示範非同步事件處理常式 `StartButton_Click` 與非同步方法 `ExampleMethodAsync` 之間的控制結構與流程。  非同步方法產生的結果是所下載網站的長度。  此程式碼適用於您在 [!INCLUDE[vs_dev12](../../../csharp/getting-started/includes/vs-dev12-md.md)] 中建立的 Windows Presentation Foundation \(WPF\) 應用程式或 Windows 市集應用程式。請參閱有關設定應用程式的程式碼註解。  
  
```c#  
// You can run this code in Visual Studio 2013 as a WPF app or a Windows Store app.  
// You need a button (StartButton) and a textbox (ResultsTextBox).  
// Remember to set the names and handler so that you have something like this:  
// <Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
//         Click="StartButton_Click" Name="StartButton"/>  
// <TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
//          Text="TextBox" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
  
// To run the code as a WPF app:  
//    paste this code into the MainWindow class in MainWindow.xaml.cs,  
//    add a reference to System.Net.Http, and  
//    add a using directive for System.Net.Http.  
  
// To run the code as a Windows Store app:  
//    paste this code into the MainPage class in MainPage.xaml.cs, and  
//    add using directives for System.Net.Http and System.Threading.Tasks.  
  
private async void StartButton_Click(object sender, RoutedEventArgs e)  
{  
    // ExampleMethodAsync returns a Task<int>, which means that the method  
    // eventually produces an int result. However, ExampleMethodAsync returns  
    // the Task<int> value as soon as it reaches an await.  
    ResultsTextBox.Text += "\n";  
    try  
    {  
        int length = await ExampleMethodAsync();  
        // Note that you could put "await ExampleMethodAsync()" in the next line where  
        // "length" is, but due to when '+=' fetches the value of ResultsTextBox, you  
        // would not see the global side effect of ExampleMethodAsync setting the text.  
        ResultsTextBox.Text += String.Format("Length: {0}\n", length);  
    }  
    catch (Exception)  
    {  
        // Process the exception if one occurs.  
    }  
}  
  
public async Task<int> ExampleMethodAsync()  
{  
    var httpClient = new HttpClient();  
    int exampleInt = (await httpClient.GetStringAsync("http://msdn.microsoft.com")).Length;  
    ResultsTextBox.Text += "Preparing to finish ExampleMethodAsync.\n";  
    // After the following return statement, any method that's awaiting  
    // ExampleMethodAsync (in this case, StartButton_Click) can get the   
    // integer result.  
    return exampleInt;  
}  
// Output:  
// Preparing to finish ExampleMethodAsync.  
// Length: 53292  
  
```  
  
> [!IMPORTANT]
>  如需有關工作和等候工作時執行之程式碼的詳細資訊，請參閱[使用 Async 和 Await 設計非同步程式](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)。如需使用類似項目的完整 WPF 範例，請參閱[逐步解說：使用 Async 和 Await 存取 Web](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)。  您可以從[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkId=255191)下載逐步解說程式碼。  
  
## 傳回類型  
 非同步方法的傳回類型可以是 <xref:System.Threading.Tasks.Task>、<xref:System.Threading.Tasks.Task%601> 或 [void](../../../csharp/language-reference/keywords/void.md)。  此方法不可以宣告任何 [ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out.md) 參數，但是可以呼叫具有這類參數的方法。  
  
 如果方法的 [return](../../../csharp/language-reference/keywords/return.md) 陳述式指定 `TResult` 類型的運算元，請指定 `Task<TResult>` 做為非同步方法的傳回類型。  如果方法完成時未傳回任何有意義的值，則使用 `Task`。  也就是說，呼叫方法會傳回 `Task`，但是當 `Task` 完成時，等候 `Task` 的任何 `await` 運算式都會判斷值為 `void`。  
  
 您主要是使用 `void` 傳回類型定義需要該傳回類型的事件處理常式。  傳回 `void` 之非同步方法的呼叫端無法等候它，而且無法攔截方法擲回的例外狀況。  
  
 如需詳細資訊與範例，請參閱[非同步方法的傳回類型](../Topic/Async%20Return%20Types%20\(C%23%20and%20Visual%20Basic\).md)。  
  
## 請參閱  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>   
 [await](../../../csharp/language-reference/keywords/await.md)   
 [逐步解說：使用 Async 和 Await 存取 Web](../Topic/Walkthrough:%20Accessing%20the%20Web%20by%20Using%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)   
 [使用 Async 和 Await 設計非同步程式](../Topic/Asynchronous%20Programming%20with%20Async%20and%20Await%20\(C%23%20and%20Visual%20Basic\).md)