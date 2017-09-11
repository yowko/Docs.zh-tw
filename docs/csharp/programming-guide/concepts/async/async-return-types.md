---
title: "非同步方法的傳回型別 (C#) | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: d974e93c3c50a61889a9ed37ad5f68f7a131a538
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="async-return-types-c"></a><span data-ttu-id="bfc90-102">非同步方法的傳回型別 (C#)</span><span class="sxs-lookup"><span data-stu-id="bfc90-102">Async Return Types (C#)</span></span>
<span data-ttu-id="bfc90-103">非同步方法有三個可能的傳回型別：<xref:System.Threading.Tasks.Task%601>、<xref:System.Threading.Tasks.Task> 和 void。</span><span class="sxs-lookup"><span data-stu-id="bfc90-103">Async methods have three possible return types: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, and void.</span></span> <span data-ttu-id="bfc90-104">在 Visual Basic 中，void 傳回型別會撰寫為 [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) 程序。</span><span class="sxs-lookup"><span data-stu-id="bfc90-104">In Visual Basic, the void return type is written as a [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure.</span></span> <span data-ttu-id="bfc90-105">如需非同步方法的詳細資訊，請參閱[使用 async 和 await 進行非同步程式設計 (C#)](../../../../csharp/programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="bfc90-105">For more information about async methods, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="bfc90-106">每個傳回型別在下列其中一節探討，您可以在主題結尾處找到使用全部三種類型的完整範例。</span><span class="sxs-lookup"><span data-stu-id="bfc90-106">Each return type is examined in one of the following sections, and you can find a full example that uses all three types at the end of the topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bfc90-107">若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="bfc90-107">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <span data-ttu-id="bfc90-108"><a name="BKMK_TaskTReturnType"></a> Task(T) 傳回型別</span><span class="sxs-lookup"><span data-stu-id="bfc90-108"><a name="BKMK_TaskTReturnType"></a> Task(T) Return Type</span></span>  
 <span data-ttu-id="bfc90-109"><xref:System.Threading.Tasks.Task%601> 傳回型別用於非同步方法，其中包含運算元的類型為 `TResult` 的 [return](../../../../csharp/language-reference/keywords/return.md) (C#) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bfc90-109">The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a[return](../../../../csharp/language-reference/keywords/return.md) (C#) statement in which the operand has type `TResult`.</span></span>  
  
 <span data-ttu-id="bfc90-110">在下列範例中，`TaskOfT_MethodAsync` 非同步方法包含一個傳回整數的 return 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bfc90-110">In the following example, the `TaskOfT_MethodAsync` async method contains a return statement that returns an integer.</span></span> <span data-ttu-id="bfc90-111">因此，方法宣告必須指定 `Task<int>` 傳回型別。</span><span class="sxs-lookup"><span data-stu-id="bfc90-111">Therefore, the method declaration must specify a return type of `Task<int>`.</span></span>  
  
```csharp  
// TASK<T> EXAMPLE  
async Task<int> TaskOfT_MethodAsync()  
{  
    // The body of the method is expected to contain an awaited asynchronous  
    // call.  
    // Task.FromResult is a placeholder for actual work that returns a string.  
    var today = await Task.FromResult<string>(DateTime.Now.DayOfWeek.ToString());  
  
    // The method then can process the result in some way.  
    int leisureHours;  
    if (today.First() == 'S')  
        leisureHours = 16;  
    else  
        leisureHours = 5;  
  
    // Because the return statement specifies an operand of type int, the  
    // method must have a return type of Task<int>.  
    return leisureHours;  
}  
```  
  
 <span data-ttu-id="bfc90-112">從 await 運算式內呼叫 `TaskOfT_MethodAsync` 時，await 運算式會擷取儲存在 `TaskOfT_MethodAsync` 所傳回之工作中的整數值 (`leisureHours` 的值)。</span><span class="sxs-lookup"><span data-stu-id="bfc90-112">When `TaskOfT_MethodAsync` is called from within an await expression, the await expression retrieves the integer value (the value of `leisureHours`) that's stored in the task that's returned by `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="bfc90-113">如需 await 運算式的詳細資訊，請參閱 [await](../../../../csharp/language-reference/keywords/await.md)。</span><span class="sxs-lookup"><span data-stu-id="bfc90-113">For more information about await expressions, see [await](../../../../csharp/language-reference/keywords/await.md).</span></span>  
  
 <span data-ttu-id="bfc90-114">下列程式碼會呼叫並等候方法 `TaskOfT_MethodAsync`。</span><span class="sxs-lookup"><span data-stu-id="bfc90-114">The following code calls and awaits method `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="bfc90-115">結果會指派給 `result1` 變數。</span><span class="sxs-lookup"><span data-stu-id="bfc90-115">The result is assigned to the `result1` variable.</span></span>  
  
```csharp  
// Call and await the Task<T>-returning async method in the same statement.  
int result1 = await TaskOfT_MethodAsync();  
```  
  
 <span data-ttu-id="bfc90-116">您可以藉由區隔對 `TaskOfT_MethodAsync` 的呼叫與 `await` 的應用，深入了解這種運作方式，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="bfc90-116">You can better understand how this happens by separating the call to `TaskOfT_MethodAsync` from the application of `await`, as the following code shows.</span></span> <span data-ttu-id="bfc90-117">呼叫不會立即等候的 `TaskOfT_MethodAsync` 方法，會傳回 `Task<int>`，如您所預期的方法宣告。</span><span class="sxs-lookup"><span data-stu-id="bfc90-117">A call to method `TaskOfT_MethodAsync` that isn't immediately awaited returns a `Task<int>`, as you would expect from the declaration of the method.</span></span> <span data-ttu-id="bfc90-118">在範例中，工作會指派給 `integerTask` 變數。</span><span class="sxs-lookup"><span data-stu-id="bfc90-118">The task is assigned to the `integerTask` variable in the example.</span></span> <span data-ttu-id="bfc90-119">因為 `integerTask` 是 <xref:System.Threading.Tasks.Task%601>，所以會包含 `TResult` 類型的 <xref:System.Threading.Tasks.Task%601.Result> 屬性。</span><span class="sxs-lookup"><span data-stu-id="bfc90-119">Because `integerTask` is a <xref:System.Threading.Tasks.Task%601>, it contains a <xref:System.Threading.Tasks.Task%601.Result> property of type `TResult`.</span></span> <span data-ttu-id="bfc90-120">在此情況下，TResult 代表整數類型。</span><span class="sxs-lookup"><span data-stu-id="bfc90-120">In this case, TResult represents an integer type.</span></span> <span data-ttu-id="bfc90-121">將 `await` 套用至 `integerTask` 時，await 運算式會評估為 `integerTask` 之 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性的內容。</span><span class="sxs-lookup"><span data-stu-id="bfc90-121">When `await` is applied to `integerTask`, the await expression evaluates to the contents of the <xref:System.Threading.Tasks.Task%601.Result%2A> property of `integerTask`.</span></span> <span data-ttu-id="bfc90-122">值會指派給 `result2` 變數。</span><span class="sxs-lookup"><span data-stu-id="bfc90-122">The value is assigned to the `result2` variable.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="bfc90-123"><xref:System.Threading.Tasks.Task%601.Result%2A> 屬性是封鎖屬性。</span><span class="sxs-lookup"><span data-stu-id="bfc90-123">The <xref:System.Threading.Tasks.Task%601.Result%2A> property is a blocking property.</span></span> <span data-ttu-id="bfc90-124">如果您嘗試在其工作完成之前先存取它，目前使用中的執行緒會封鎖，直到工作完成並且有可用的值為止。</span><span class="sxs-lookup"><span data-stu-id="bfc90-124">If you try to access it before its task is finished, the thread that's currently active is blocked until the task completes and the value is available.</span></span> <span data-ttu-id="bfc90-125">在大部分情況下，您應該使用 `await` 來存取值，而不是直接存取屬性。</span><span class="sxs-lookup"><span data-stu-id="bfc90-125">In most cases, you should access the value by using `await` instead of accessing the property directly.</span></span>  
  
```csharp  
// Call and await in separate statements.  
Task<int> integerTask = TaskOfT_MethodAsync();  
  
// You can do other work that does not rely on integerTask before awaiting.  
textBox1.Text += String.Format("Application can continue working while the Task<T> runs. . . . \r\n");  
  
int result2 = await integerTask;  
```  
  
 <span data-ttu-id="bfc90-126">下列程式碼中的 display 陳述式會驗證 `result1` 變數、`result2` 變數和 `Result` 屬性的值相同。</span><span class="sxs-lookup"><span data-stu-id="bfc90-126">The display statements in the following code verify that the values of the `result1` variable, the `result2` variable, and the `Result` property are the same.</span></span> <span data-ttu-id="bfc90-127">請記住，`Result` 屬性是封鎖屬性，在等候其工作之前不應該存取它。</span><span class="sxs-lookup"><span data-stu-id="bfc90-127">Remember that the `Result` property is a blocking property and shouldn't be accessed before its task has been awaited.</span></span>  
  
```csharp  
// Display the values of the result1 variable, the result2 variable, and  
// the integerTask.Result property.  
textBox1.Text += String.Format("\r\nValue of result1 variable:   {0}\r\n", result1);  
textBox1.Text += String.Format("Value of result2 variable:   {0}\r\n", result2);  
textBox1.Text += String.Format("Value of integerTask.Result: {0}\r\n", integerTask.Result);  
```  
  
##  <span data-ttu-id="bfc90-128"><a name="BKMK_TaskReturnType"></a> 工作傳回型別</span><span class="sxs-lookup"><span data-stu-id="bfc90-128"><a name="BKMK_TaskReturnType"></a> Task Return Type</span></span>  
 <span data-ttu-id="bfc90-129">不包含 return 陳述式的非同步方法，或包含不會傳回運算元之 return 陳述式的非同步方法，通常具有 <xref:System.Threading.Tasks.Task> 傳回型別。</span><span class="sxs-lookup"><span data-stu-id="bfc90-129">Async methods that don't contain a return statement or that contain a return statement that doesn't return an operand usually have a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="bfc90-130">這類方法是會傳回 void 的方法，如果它們撰寫成同步執行的話。</span><span class="sxs-lookup"><span data-stu-id="bfc90-130">Such methods would be void-returning methods if they were written to run synchronously.</span></span> <span data-ttu-id="bfc90-131">如果您針對非同步方法使用 `Task` 傳回型別，則除非被呼叫的非同步方法完成，否則呼叫的方法可以使用 await 運算子暫止呼叫端完成。</span><span class="sxs-lookup"><span data-stu-id="bfc90-131">If you use a `Task` return type for an async method, a calling method can use an await operator to suspend the caller's completion until the called async method has finished.</span></span>  
  
 <span data-ttu-id="bfc90-132">在下列範例中，非同步方法 `Task_MethodAsync` 不包含 return 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bfc90-132">In the following example, async method `Task_MethodAsync` doesn't contain a return statement.</span></span> <span data-ttu-id="bfc90-133">因此，您為方法指定 `Task` 傳回型別，如此可等候 `Task_MethodAsync`。</span><span class="sxs-lookup"><span data-stu-id="bfc90-133">Therefore, you specify a return type of `Task` for the method, which enables `Task_MethodAsync` to be awaited.</span></span> <span data-ttu-id="bfc90-134">`Task` 類型的定義不包含用來儲存傳回值的 `Result` 屬性。</span><span class="sxs-lookup"><span data-stu-id="bfc90-134">The definition of the `Task` type doesn't include a `Result` property to store a return value.</span></span>  
  
```csharp  
// TASK EXAMPLE  
async Task Task_MethodAsync()  
{  
    // The body of an async method is expected to contain an awaited   
    // asynchronous call.  
    // Task.Delay is a placeholder for actual work.  
    await Task.Delay(2000);  
    // Task.Delay delays the following line by two seconds.  
    textBox1.Text += String.Format("\r\nSorry for the delay. . . .\r\n");  
  
    // This method has no return statement, so its return type is Task.    
}  
```  
  
 <span data-ttu-id="bfc90-135">使用 await 陳述式呼叫並等候 `Task_MethodAsync`，而不是使用 await 運算式，類似於同步傳回 void 方法的呼叫陳述式。</span><span class="sxs-lookup"><span data-stu-id="bfc90-135">`Task_MethodAsync` is called and awaited by using an await statement instead of an await expression, similar to the calling statement for a synchronous void-returning method.</span></span> <span data-ttu-id="bfc90-136">在此情況下，await 運算子的應用不會產生值。</span><span class="sxs-lookup"><span data-stu-id="bfc90-136">The application of an await operator in this case doesn't produce a value.</span></span>  
  
 <span data-ttu-id="bfc90-137">下列程式碼會呼叫並等候方法 `Task_MethodAsync`。</span><span class="sxs-lookup"><span data-stu-id="bfc90-137">The following code calls and awaits method `Task_MethodAsync`.</span></span>  
  
```csharp  
// Call and await the Task-returning async method in the same statement.  
await Task_MethodAsync();  
```  
  
 <span data-ttu-id="bfc90-138">如先前的 <xref:System.Threading.Tasks.Task%601> 範例中所示，您可以區隔 `Task_MethodAsync` 呼叫和 await 運算子的應用，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="bfc90-138">As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an await operator, as the following code shows.</span></span> <span data-ttu-id="bfc90-139">不過，請記住，`Task` 沒有 `Result` 屬性，且將 await 運算子套用至 `Task` 時不會產生任何值。</span><span class="sxs-lookup"><span data-stu-id="bfc90-139">However, remember that a `Task` doesn't have a `Result` property, and that no value is produced when an await operator is applied to a `Task`.</span></span>  
  
 <span data-ttu-id="bfc90-140">下列程式碼會區隔 `Task_MethodAsync` 的呼叫與等候 `Task_MethodAsync` 傳回的工作。</span><span class="sxs-lookup"><span data-stu-id="bfc90-140">The following code separates calling `Task_MethodAsync` from awaiting the task that `Task_MethodAsync` returns.</span></span>  
  
```csharp  
// Call and await in separate statements.  
Task simpleTask = Task_MethodAsync();  
  
// You can do other work that does not rely on simpleTask before awaiting.  
textBox1.Text += String.Format("\r\nApplication can continue working while the Task runs. . . .\r\n");  
  
await simpleTask;  
```  
  
##  <span data-ttu-id="bfc90-141"><a name="BKMK_VoidReturnType"></a> Void 傳回型別</span><span class="sxs-lookup"><span data-stu-id="bfc90-141"><a name="BKMK_VoidReturnType"></a> Void Return Type</span></span>  
 <span data-ttu-id="bfc90-142">void 傳回型別的主要用途是在事件處理常式中，此時需要 void 傳回型別。</span><span class="sxs-lookup"><span data-stu-id="bfc90-142">The primary use of the void return type is in event handlers, where a void return type is required.</span></span> <span data-ttu-id="bfc90-143">void 傳回也可用來覆寫傳回 void 的方法，或執行可分類為「射後不理」(fire and forget) 之活動的方法。</span><span class="sxs-lookup"><span data-stu-id="bfc90-143">A void return also can be used to override void-returning methods or for methods that perform activities that can be categorized as "fire and forget."</span></span> <span data-ttu-id="bfc90-144">不過，您應該盡可能傳回 `Task`，因為無法等候傳回 void 的非同步方法。</span><span class="sxs-lookup"><span data-stu-id="bfc90-144">However, you should return a `Task` wherever possible, because a void-returning async method can't be awaited.</span></span> <span data-ttu-id="bfc90-145">這種方法的任何呼叫端必須要能夠繼續完成而不需等待呼叫的非同步方法完成，且呼叫端必須與非同步方法產生的任何值或例外狀況無關。</span><span class="sxs-lookup"><span data-stu-id="bfc90-145">Any caller of such a method must be able to continue to completion without waiting for the called async method to finish, and the caller must be independent of any values or exceptions that the async method generates.</span></span>  
  
 <span data-ttu-id="bfc90-146">傳回 void 的非同步方法的呼叫端無法攔截方法擲回的例外狀況，這類未處理的例外狀況有可能造成應用程式失敗。</span><span class="sxs-lookup"><span data-stu-id="bfc90-146">The caller of a void-returning async method can't catch exceptions that are thrown from the method, and such unhandled exceptions are likely to cause your application to fail.</span></span> <span data-ttu-id="bfc90-147">如果例外狀況發生在會傳回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 的非同步方法，則例外狀況會儲存在傳回的工作中，並在等候工作時再次擲回。</span><span class="sxs-lookup"><span data-stu-id="bfc90-147">If an exception occurs in an async method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>, the exception is stored in the returned task, and rethrown when the task is awaited.</span></span> <span data-ttu-id="bfc90-148">因此，請確定任何可能會產生例外狀況的非同步方法具有 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 傳回型別，且會等候對方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="bfc90-148">Therefore, make sure that any async method that can produce an exception has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> and that calls to the method are awaited.</span></span>  
  
 <span data-ttu-id="bfc90-149">如需如何在非同步方法中攔截例外狀況的詳細資訊，請參閱 [try-catch](../../../../csharp/language-reference/keywords/try-catch.md)。</span><span class="sxs-lookup"><span data-stu-id="bfc90-149">For more information about how to catch exceptions in async methods, see [try-catch](../../../../csharp/language-reference/keywords/try-catch.md) .</span></span>  
  
 <span data-ttu-id="bfc90-150">下列程式碼會定義非同步事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="bfc90-150">The following code defines an async event handler.</span></span>  
  
```csharp  
// VOID EXAMPLE  
private async void button1_Click(object sender, RoutedEventArgs e)  
{  
    textBox1.Clear();  
  
    // Start the process and await its completion. DriverAsync is a   
    // Task-returning async method.  
    await DriverAsync();  
  
    // Say goodbye.  
    textBox1.Text += "\r\nAll done, exiting button-click event handler.";  
}  
```  
  
##  <span data-ttu-id="bfc90-151"><a name="BKMK_Example"></a> 完整範例</span><span class="sxs-lookup"><span data-stu-id="bfc90-151"><a name="BKMK_Example"></a> Complete Example</span></span>  
 <span data-ttu-id="bfc90-152">下列 Windows Presentation Foundation (WPF) 專案包含本土的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="bfc90-152">The following Windows Presentation Foundation (WPF) project contains the code examples from this topic.</span></span>  
  
 <span data-ttu-id="bfc90-153">若要執行專案，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="bfc90-153">To run the project, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="bfc90-154">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="bfc90-154">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="bfc90-155">在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。</span><span class="sxs-lookup"><span data-stu-id="bfc90-155">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="bfc90-156">[ **新增專案** ] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="bfc90-156">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="bfc90-157">在 [已安裝的範本] 分類中，選擇 [Visual C#]，然後選擇 [Windows]。</span><span class="sxs-lookup"><span data-stu-id="bfc90-157">In the **Installed**, **Templates** category, choose Visual C#, and then choose **Windows**.</span></span> <span data-ttu-id="bfc90-158">在專案類型清單中，選擇 [WPF 應用程式]。</span><span class="sxs-lookup"><span data-stu-id="bfc90-158">Choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="bfc90-159">輸入 `AsyncReturnTypes` 作為專案的名稱，然後選擇 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="bfc90-159">Enter `AsyncReturnTypes` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="bfc90-160">新的專案隨即出現在方案總管中。</span><span class="sxs-lookup"><span data-stu-id="bfc90-160">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="bfc90-161">在 Visual Studio 程式碼編輯器中，選擇 [ **MainWindow.xaml** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="bfc90-161">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="bfc90-162">如果未顯示索引標籤，請在方案總管中開啟 MainWindow.xaml 的捷徑功能表，然後選擇 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="bfc90-162">If the tab is not visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **Open**.</span></span>  
  
6.  <span data-ttu-id="bfc90-163">在 MainWindow.xaml 的 [XAML] 視窗中，將程式碼取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="bfc90-163">In the **XAML** window of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```csharp  
    <Window x:Class="AsyncReturnTypes.MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            Title="MainWindow" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="button1" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="button1_Click"/>  
            <TextBox x:Name="textBox1" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>  
  
        </Grid>  
    </Window>  
  
    ```  
  
     <span data-ttu-id="bfc90-164">包含文字方塊和按鈕的簡單視窗會出現在 MainWindow.xaml 的 [設計] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="bfc90-164">A simple window that contains a text box and a button appears in the **Design** window of MainWindow.xaml.</span></span>  
  
7.  <span data-ttu-id="bfc90-165">在方案總管中，開啟 MainWindow.xaml.cs 的捷徑功能表，然後選擇 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="bfc90-165">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
8.  <span data-ttu-id="bfc90-166">將 MainWindow.xaml.cs 中的程式碼取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="bfc90-166">Replace the code in MainWindow.xaml.cs with the following code.</span></span>  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.Threading.Tasks;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Data;  
    using System.Windows.Documents;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    using System.Windows.Media.Imaging;  
    using System.Windows.Navigation;  
    using System.Windows.Shapes;  
  
    namespace AsyncReturnTypes  
    {  
        public partial class MainWindow : Window  
        {  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
  
            // VOID EXAMPLE  
            private async void button1_Click(object sender, RoutedEventArgs e)  
            {  
                textBox1.Clear();  
  
                // Start the process and await its completion. DriverAsync is a   
                // Task-returning async method.  
                await DriverAsync();  
  
                // Say goodbye.  
                textBox1.Text += "\r\nAll done, exiting button-click event handler.";  
            }  
  
            async Task DriverAsync()  
            {  
                // Task<T>   
                // Call and await the Task<T>-returning async method in the same statement.  
                int result1 = await TaskOfT_MethodAsync();  
  
                // Call and await in separate statements.  
                Task<int> integerTask = TaskOfT_MethodAsync();  
  
                // You can do other work that does not rely on integerTask before awaiting.  
                textBox1.Text += String.Format("Application can continue working while the Task<T> runs. . . . \r\n");  
  
                int result2 = await integerTask;  
  
                // Display the values of the result1 variable, the result2 variable, and  
                // the integerTask.Result property.  
                textBox1.Text += String.Format("\r\nValue of result1 variable:   {0}\r\n", result1);  
                textBox1.Text += String.Format("Value of result2 variable:   {0}\r\n", result2);  
                textBox1.Text += String.Format("Value of integerTask.Result: {0}\r\n", integerTask.Result);  
  
                // Task  
                // Call and await the Task-returning async method in the same statement.  
                await Task_MethodAsync();  
  
                // Call and await in separate statements.  
                Task simpleTask = Task_MethodAsync();  
  
                // You can do other work that does not rely on simpleTask before awaiting.  
                textBox1.Text += String.Format("\r\nApplication can continue working while the Task runs. . . .\r\n");  
  
                await simpleTask;  
            }  
  
            // TASK<T> EXAMPLE  
            async Task<int> TaskOfT_MethodAsync()  
            {  
                // The body of the method is expected to contain an awaited asynchronous  
                // call.  
                // Task.FromResult is a placeholder for actual work that returns a string.  
                var today = await Task.FromResult<string>(DateTime.Now.DayOfWeek.ToString());  
  
                // The method then can process the result in some way.  
                int leisureHours;  
                if (today.First() == 'S')  
                    leisureHours = 16;  
                else  
                    leisureHours = 5;  
  
                // Because the return statement specifies an operand of type int, the  
                // method must have a return type of Task<int>.  
                return leisureHours;  
            }  
  
            // TASK EXAMPLE  
            async Task Task_MethodAsync()  
            {  
                // The body of an async method is expected to contain an awaited   
                // asynchronous call.  
                // Task.Delay is a placeholder for actual work.  
                await Task.Delay(2000);  
                // Task.Delay delays the following line by two seconds.  
                textBox1.Text += String.Format("\r\nSorry for the delay. . . .\r\n");  
  
                // This method has no return statement, so its return type is Task.    
            }  
        }  
    }  
    ```  
  
9. <span data-ttu-id="bfc90-167">選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="bfc90-167">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="bfc90-168">應該出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="bfc90-168">The following output should appear.</span></span>  
  
    ```  
    Application can continue working while the Task<T> runs. . . .   
  
    Value of result1 variable:   5  
    Value of result2 variable:   5  
    Value of integerTask.Result: 5  
  
    Sorry for the delay. . . .  
  
    Application can continue working while the Task runs. . . .  
  
    Sorry for the delay. . . .  
  
    All done, exiting button-click event handler.  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="bfc90-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfc90-169">See Also</span></span>  
 <span data-ttu-id="bfc90-170"><xref:System.Threading.Tasks.Task.FromResult%2A></span><span class="sxs-lookup"><span data-stu-id="bfc90-170"><xref:System.Threading.Tasks.Task.FromResult%2A></span></span>   
<span data-ttu-id="bfc90-171"> [逐步解說：使用 async 和 await 存取 Web (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span><span class="sxs-lookup"><span data-stu-id="bfc90-171"> [Walkthrough: Accessing the Web by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span></span>  
<span data-ttu-id="bfc90-172"> [非同步程式中的控制流程 (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md) </span><span class="sxs-lookup"><span data-stu-id="bfc90-172"> [Control Flow in Async Programs (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md) </span></span>  
<span data-ttu-id="bfc90-173"> [async](../../../../csharp/language-reference/keywords/async.md) </span><span class="sxs-lookup"><span data-stu-id="bfc90-173"> [async](../../../../csharp/language-reference/keywords/async.md) </span></span>  
<span data-ttu-id="bfc90-174"> [await](../../../../csharp/language-reference/keywords/await.md)</span><span class="sxs-lookup"><span data-stu-id="bfc90-174"> [await](../../../../csharp/language-reference/keywords/await.md)</span></span>
