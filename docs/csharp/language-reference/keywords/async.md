---
title: async (C# 參考)
ms.date: 05/22/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
caps.latest.revision: 52
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 50b22ea94e8079e29c1e2ba2a595544ce23bd216
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="async-c-reference"></a><span data-ttu-id="ca5dd-102">async (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ca5dd-102">async (C# Reference)</span></span>
<span data-ttu-id="ca5dd-103">使用 `async` 修飾詞可將方法、[Lambda 運算式](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)或[匿名方法](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md)指定為非同步。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-103">Use the `async` modifier to specify that a method, [lambda expression](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), or [anonymous method](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) is asynchronous.</span></span> <span data-ttu-id="ca5dd-104">如果您在方法或運算式上使用這個修飾詞，則它是指「非同步方法」。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-104">If you use this modifier on a method or expression, it's referred to as an *async method*.</span></span> <span data-ttu-id="ca5dd-105">下例定義名為 `ExampleMethodAsync` 的非同步方法：</span><span class="sxs-lookup"><span data-stu-id="ca5dd-105">The following example defines an async method named `ExampleMethodAsync`:</span></span> 
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  
 
<span data-ttu-id="ca5dd-106">如果您不熟悉非同步程式設計或不了解非同步方法如何使用 `await` 關鍵字進行可能需要長期執行的工作，而不封鎖呼叫端執行緒，請閱讀[使用 async 和 await 進行非同步程式設計](../../../csharp/programming-guide/concepts/async/index.md)中的簡介。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-106">If you're new to asynchronous programming or do not understand how an async method uses the `await` keyword to do potentially long-running work without blocking the caller’s thread, read the introduction in [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="ca5dd-107">下列程式碼位於非同步方法中，會呼叫 <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> 方法：</span><span class="sxs-lookup"><span data-stu-id="ca5dd-107">The following code is found inside an async method and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> method:</span></span> 
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
<span data-ttu-id="ca5dd-108">非同步方法會以同步方式執行，直到抵達第一個 `await` 運算式，此時方法會暫停，直到等候的工作完成。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-108">An async method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="ca5dd-109">同時，控制項會返回方法的呼叫端，如下一節中的範例所示。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-109">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>  
  
<span data-ttu-id="ca5dd-110">如果 `async` 關鍵字修改的方法不包含 `await` 運算式或陳述式，則方法會以同步方式執行。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-110">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="ca5dd-111">如果有任何非同步方法未包含 `await` 陳述式，編譯器警告就會發出警示，因為這種情況可能表示發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-111">A compiler warning alerts you to any async methods that don't contain `await` statements, because that situation might indicate an error.</span></span> <span data-ttu-id="ca5dd-112">請參閱[編譯器警告 (層級 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md)。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-112">See [Compiler Warning (level 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).</span></span>  
  
 <span data-ttu-id="ca5dd-113">`async` 關鍵字與內容相關，它只有在修改方法、Lambda 運算式或匿名方法時，才是關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-113">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="ca5dd-114">在所有其他內容中，它會解譯為識別項。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-114">In all other contexts, it's interpreted as an identifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ca5dd-115">範例</span><span class="sxs-lookup"><span data-stu-id="ca5dd-115">Example</span></span>  
<span data-ttu-id="ca5dd-116">下列範例將示範非同步事件處理常式 `StartButton_Click` 與非同步方法 `ExampleMethodAsync` 之間的控制結構與流程。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-116">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="ca5dd-117">非同步方法的結果是網頁的字元數。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-117">The result from the async method is the number of characters of a web page.</span></span> <span data-ttu-id="ca5dd-118">此程式碼適用於您在 Visual Studio 中建立的 Windows Presentation Foundation (WPF) 應用程式或 Windows 市集應用程式。請參閱有關設定應用程式的程式碼註解。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-118">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>  

<span data-ttu-id="ca5dd-119">您可以在 Visual Studio 中將此程式碼執行為 Windows Presentation Foundation (WPF) 應用程式或 Windows 市集應用程式。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-119">You can run this code in Visual Studio as a Windows Presentation Foundation (WPF) app or a Windows Store app.</span></span> <span data-ttu-id="ca5dd-120">您需要名為 `StartButton` 的按鈕控制項和名為 `ResultsTextBox` 的文字方塊控制項。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-120">You need a Button control named `StartButton` and a Textbox control named `ResultsTextBox`.</span></span> <span data-ttu-id="ca5dd-121">請記住要設定名稱和處理常式，如此才會有像下面這樣的內容：</span><span class="sxs-lookup"><span data-stu-id="ca5dd-121">Remember to set the names and handler so that you have something like this:</span></span>  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
<span data-ttu-id="ca5dd-122">將程式碼執行為 WPF 應用程式：</span><span class="sxs-lookup"><span data-stu-id="ca5dd-122">To run the code as a WPF app:</span></span>  

- <span data-ttu-id="ca5dd-123">將此程式碼貼入 MainWindow.xaml.cs 的 `MainWindow` 類別。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-123">Paste this code into the `MainWindow` class in MainWindow.xaml.cs.</span></span>  
- <span data-ttu-id="ca5dd-124">將參考新增至 System.Net.Http。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-124">Add a reference to System.Net.Http.</span></span>  
- <span data-ttu-id="ca5dd-125">為 System.Net.Http 新增 `using` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-125">Add a `using` directive for System.Net.Http.</span></span>  
  
<span data-ttu-id="ca5dd-126">將程式碼執行為 Windows 市集應用程式：</span><span class="sxs-lookup"><span data-stu-id="ca5dd-126">To run the code as a Windows Store app:</span></span>  
- <span data-ttu-id="ca5dd-127">將此程式碼貼入 MainPage.xaml.cs 的 `MainPage` 類別。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-127">Paste this code into the `MainPage` class in MainPage.xaml.cs.</span></span>  
- <span data-ttu-id="ca5dd-128">為 System.Net.Http 和 System.Threading.Tasks 新增 using 指示詞。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-128">Add using directives for System.Net.Http and System.Threading.Tasks.</span></span>  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
>  <span data-ttu-id="ca5dd-129">如需工作以及等候工作時執行之程式碼的詳細資訊，請參閱[使用 async 和 await 進行非同步程式設計](../../../csharp/programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-129">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="ca5dd-130">如需使用類似項目的完整 WPF 範例，請參閱[逐步解說：使用 async 和 await 存取 Web](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-130">For a full WPF example that uses similar elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="ca5dd-131">傳回型別</span><span class="sxs-lookup"><span data-stu-id="ca5dd-131">Return Types</span></span>  
<span data-ttu-id="ca5dd-132">非同步方法可有下列傳回型別：</span><span class="sxs-lookup"><span data-stu-id="ca5dd-132">An async method can have the following return types:</span></span>

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- <span data-ttu-id="ca5dd-133">[void](../../../csharp/language-reference/keywords/void.md)，應該只用於事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-133">[void](../../../csharp/language-reference/keywords/void.md), which should only be used for event handlers.</span></span>
- <span data-ttu-id="ca5dd-134">自 C# 7.0 開始，任何具有可存取 `GetAwaiter` 方法的型別。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-134">Starting with C# 7.0, any type that has an accessible `GetAwaiter` method.</span></span> <span data-ttu-id="ca5dd-135">`System.Threading.Tasks.ValueTask<TResult>` 類型就是一個這種實作。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-135">The `System.Threading.Tasks.ValueTask<TResult>` type is one such implementation.</span></span> <span data-ttu-id="ca5dd-136">新增 NuGet 套件 `System.Threading.Tasks.Extensions` 即可使用。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-136">It is available by adding the NuGet package `System.Threading.Tasks.Extensions`.</span></span> 

<span data-ttu-id="ca5dd-137">非同步方法不可宣告任何 [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md)、[ref](../../../csharp/language-reference/keywords/ref.md) 或 [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) 參數，也不可以有 [參考傳回值](../../programming-guide/classes-and-structs/ref-returns.md)，但可以呼叫有這類參數的方法。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-137">The async method can't declare any [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters, nor can it have a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md), but it can call methods that have such parameters.</span></span>  
  
<span data-ttu-id="ca5dd-138">如果方法的 [return](../../../csharp/language-reference/keywords/return.md) 陳述式指定 `TResult` 類型的運算元，請指定 `Task<TResult>` 作為非同步方法的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-138">You specify `Task<TResult>` as the return type of an async method if the [return](../../../csharp/language-reference/keywords/return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="ca5dd-139">如果方法完成時未傳回任何有意義的值，則使用 `Task`。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-139">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="ca5dd-140">也就是說，呼叫方法會傳回 `Task`，但是當 `Task` 完成時，等候 `await` 的任何 `Task` 運算式都會判斷值為 `void`。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-140">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>  
  
<span data-ttu-id="ca5dd-141">您主要是使用 `void` 傳回類型定義需要該傳回類型的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-141">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="ca5dd-142">傳回 `void` 之非同步方法的呼叫端無法等候它，而且無法攔截方法擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-142">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>  

<span data-ttu-id="ca5dd-143">自 C# 7.0 開始，您會傳回另一個型別，通常是實值型別，具有 `GetAwaiter` 方法可將程式碼效能關鍵區段中的記憶體配置降至最低。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-143">Starting with C# 7.0, you return another type, typically a value type, that has a `GetAwaiter` method to miminize memory allocations in performance-critical sections of code.</span></span> 

<span data-ttu-id="ca5dd-144">如需詳細資訊和範例，請參閱[非同步方法的傳回型別](../../../csharp/programming-guide/concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="ca5dd-144">For more information and examples, see [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca5dd-145">請參閱</span><span class="sxs-lookup"><span data-stu-id="ca5dd-145">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>  
 [<span data-ttu-id="ca5dd-146">await</span><span class="sxs-lookup"><span data-stu-id="ca5dd-146">await</span></span>](../../../csharp/language-reference/keywords/await.md)  
 [<span data-ttu-id="ca5dd-147">逐步解說：使用 Async 和 Await 存取 Web</span><span class="sxs-lookup"><span data-stu-id="ca5dd-147">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 [<span data-ttu-id="ca5dd-148">使用 async 和 await 進行非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="ca5dd-148">Asynchronous Programming with async and await</span></span>](../../../csharp/programming-guide/concepts/async/index.md)
