---
title: "async (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- async_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
caps.latest.revision: 52
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 50e128137fde445f64e10cf7c2a1ee5fdecb34e6
ms.openlocfilehash: e7f4cfa81de3c4db41d9303abf65cfd0edc926a4
ms.contentlocale: zh-tw
ms.lasthandoff: 05/01/2017

---
# <a name="async-c-reference"></a><span data-ttu-id="50325-102">async (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="50325-102">async (C# Reference)</span></span>
<span data-ttu-id="50325-103">使用 `async` 修飾詞可將方法、[Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)或[匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)指定為非同步。</span><span class="sxs-lookup"><span data-stu-id="50325-103">Use the `async` modifier to specify that a method, [lambda expression](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), or [anonymous method](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) is asynchronous.</span></span> <span data-ttu-id="50325-104">如果您在方法或運算式上使用這個修飾詞，則它是指非同步方法。</span><span class="sxs-lookup"><span data-stu-id="50325-104">If you use this modifier on a method or expression, it's referred to as an async method.</span></span>  
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
  
```  
  
 <span data-ttu-id="50325-105">如果您不熟悉非同步程式設計或不了解非同步方法如何使用 `await` 關鍵字進行可能需要長期執行的工作，而不封鎖呼叫端執行緒，則應該閱讀[使用 async 和 await 進行非同步程式設計](../../../csharp/programming-guide/concepts/async/index.md)中的簡介。</span><span class="sxs-lookup"><span data-stu-id="50325-105">If you're new to asynchronous programming or do not understand how an async method uses the `await` keyword to do potentially long-running work without blocking the caller’s thread, you should read the introduction in [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
```  
string contents = await contentsTask;  
```  
  
 <span data-ttu-id="50325-106">方法會以同步方式執行，直到抵達第一個 `await` 運算式，此時方法會暫停，直到等候的工作完成。</span><span class="sxs-lookup"><span data-stu-id="50325-106">The method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="50325-107">同時，控制項會返回方法的呼叫端，如下一節中的範例所示。</span><span class="sxs-lookup"><span data-stu-id="50325-107">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>  
  
 <span data-ttu-id="50325-108">如果 `async` 關鍵字修改的方法不包含 `await` 運算式或陳述式，則方法會以同步方式執行。</span><span class="sxs-lookup"><span data-stu-id="50325-108">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="50325-109">如果有任何非同步方法未包含 `await`，編譯器警告就會發出警示，因為這種情況可能表示發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="50325-109">A compiler warning alerts you to any async methods that don't contain `await`, because that situation might indicate an error.</span></span> <span data-ttu-id="50325-110">請參閱[編譯器警告 (層級 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md)。</span><span class="sxs-lookup"><span data-stu-id="50325-110">See [Compiler Warning (level 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).</span></span>  
  
 <span data-ttu-id="50325-111">`async` 關鍵字與內容相關，它只有在修改方法、Lambda 運算式或匿名方法時，才是關鍵字。</span><span class="sxs-lookup"><span data-stu-id="50325-111">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="50325-112">在所有其他內容中，它會解譯為識別項。</span><span class="sxs-lookup"><span data-stu-id="50325-112">In all other contexts, it's interpreted as an identifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="50325-113">範例</span><span class="sxs-lookup"><span data-stu-id="50325-113">Example</span></span>  
 <span data-ttu-id="50325-114">下列範例將示範非同步事件處理常式 `StartButton_Click` 與非同步方法 `ExampleMethodAsync` 之間的控制結構與流程。</span><span class="sxs-lookup"><span data-stu-id="50325-114">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="50325-115">非同步方法產生的結果是所下載網站的長度。</span><span class="sxs-lookup"><span data-stu-id="50325-115">The result from the async method is the length of a downloaded website.</span></span> <span data-ttu-id="50325-116">此程式碼適用於您在 Visual Studio 中建立的 Windows Presentation Foundation (WPF) 應用程式或 Windows 市集應用程式。請參閱有關設定應用程式的程式碼註解。</span><span class="sxs-lookup"><span data-stu-id="50325-116">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>  
  
```csharp  
// You can run this code in Visual Studio as a WPF app or a Windows Store app.  
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
>  <span data-ttu-id="50325-117">如需工作以及等候工作時執行之程式碼的詳細資訊，請參閱[使用 async 和 await 進行非同步程式設計](../../../csharp/programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="50325-117">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="50325-118">如需使用類似項目的完整 WPF 範例，請參閱[逐步解說：使用 async 和 await 存取 Web](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。</span><span class="sxs-lookup"><span data-stu-id="50325-118">For a full WPF example that uses similar elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span> <span data-ttu-id="50325-119">您可以從[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkId=255191)下載逐步解說程式碼。</span><span class="sxs-lookup"><span data-stu-id="50325-119">You can download the walkthrough code from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191).</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="50325-120">傳回型別</span><span class="sxs-lookup"><span data-stu-id="50325-120">Return Types</span></span>  
 <span data-ttu-id="50325-121">非同步方法的傳回型別可以是 <xref:System.Threading.Tasks.Task>、<xref:System.Threading.Tasks.Task%601> 或 [void](../../../csharp/language-reference/keywords/void.md)。</span><span class="sxs-lookup"><span data-stu-id="50325-121">An async method can have a return type of <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or [void](../../../csharp/language-reference/keywords/void.md).</span></span> <span data-ttu-id="50325-122">此方法不可以宣告任何 [ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out.md) 參數，但是可以呼叫具有這類參數的方法。</span><span class="sxs-lookup"><span data-stu-id="50325-122">The method can't declare any [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out.md) parameters, but it can call methods that have such parameters.</span></span>  
  
 <span data-ttu-id="50325-123">如果方法的 [return](../../../csharp/language-reference/keywords/return.md) 陳述式指定 `TResult` 類型的運算元，請指定 `Task<TResult>` 作為非同步方法的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="50325-123">You specify `Task<TResult>` as the return type of an async method if the [return](../../../csharp/language-reference/keywords/return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="50325-124">如果方法完成時未傳回任何有意義的值，則使用 `Task`。</span><span class="sxs-lookup"><span data-stu-id="50325-124">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="50325-125">也就是說，呼叫方法會傳回 `Task`，但是當 `Task` 完成時，等候 `await` 的任何 `Task` 運算式都會判斷值為 `void`。</span><span class="sxs-lookup"><span data-stu-id="50325-125">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>  
  
 <span data-ttu-id="50325-126">您主要是使用 `void` 傳回類型定義需要該傳回類型的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="50325-126">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="50325-127">傳回 `void` 之非同步方法的呼叫端無法等候它，而且無法攔截方法擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="50325-127">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>  
  
 <span data-ttu-id="50325-128">如需詳細資訊和範例，請參閱[非同步方法的傳回型別](../../../csharp/programming-guide/concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="50325-128">For more information and examples, see [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50325-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50325-129">See Also</span></span>  
 <span data-ttu-id="50325-130"><xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute></span><span class="sxs-lookup"><span data-stu-id="50325-130"><xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute></span></span>   
<span data-ttu-id="50325-131"> [await](../../../csharp/language-reference/keywords/await.md) </span><span class="sxs-lookup"><span data-stu-id="50325-131"> [await](../../../csharp/language-reference/keywords/await.md) </span></span>  
<span data-ttu-id="50325-132"> [逐步解說：使用 async 和 await 存取 Web](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span><span class="sxs-lookup"><span data-stu-id="50325-132"> [Walkthrough: Accessing the Web by Using Async and Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span></span>  
<span data-ttu-id="50325-133"> [使用 async 和 await 進行非同步程式設計](../../../csharp/programming-guide/concepts/async/index.md)</span><span class="sxs-lookup"><span data-stu-id="50325-133"> [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md)</span></span>
