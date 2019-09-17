---
title: 非同步傳回類型（Visual Basic）
ms.date: 07/20/2015
ms.assetid: 07890291-ee72-42d3-932a-fa4d312f2c60
ms.openlocfilehash: f331546026ac6b0799947611b54e9a147a6fe7f1
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988831"
---
# <a name="async-return-types-visual-basic"></a><span data-ttu-id="6f7a4-102">非同步傳回類型（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="6f7a4-102">Async Return Types (Visual Basic)</span></span>
<span data-ttu-id="6f7a4-103">非同步方法有三種可能的傳回類型：<xref:System.Threading.Tasks.Task%601>、<xref:System.Threading.Tasks.Task> 和 void。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-103">Async methods have three possible return types: <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, and void.</span></span> <span data-ttu-id="6f7a4-104">在 Visual Basic 中，void 傳回型別會撰寫為 [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) 程序。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-104">In Visual Basic, the void return type is written as a [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedure.</span></span> <span data-ttu-id="6f7a4-105">如需非同步方法的詳細資訊，請參閱[使用 async 和 Await 進行非同步程式設計（Visual Basic）](../../../../visual-basic/programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-105">For more information about async methods, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="6f7a4-106">每個傳回型別在下列其中一節探討，您可以在主題結尾處找到使用全部三種類型的完整範例。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-106">Each return type is examined in one of the following sections, and you can find a full example that uses all three types at the end of the topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6f7a4-107">若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-107">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
## <a name="BKMK_TaskTReturnType"></a> <span data-ttu-id="6f7a4-108">Task(T) 傳回型別</span><span class="sxs-lookup"><span data-stu-id="6f7a4-108">Task(T) Return Type</span></span>  
 <span data-ttu-id="6f7a4-109"><xref:System.Threading.Tasks.Task%601> 傳回型別用於非同步方法，其中包含運算元具有類型 `TResult` 的 [return](../../../../visual-basic/language-reference/statements/return-statement.md) 語句。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-109">The <xref:System.Threading.Tasks.Task%601> return type is used for an async method that contains a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement in which the operand has type `TResult`.</span></span>  
  
 <span data-ttu-id="6f7a4-110">在下列範例中，`TaskOfT_MethodAsync` 非同步方法包含一個傳回整數的 return 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-110">In the following example, the `TaskOfT_MethodAsync` async method contains a return statement that returns an integer.</span></span> <span data-ttu-id="6f7a4-111">因此，方法宣告必須指定 `Task(Of Integer)` 傳回型別。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-111">Therefore, the method declaration must specify a return type of `Task(Of Integer)`.</span></span>  
  
```vb  
' TASK(OF T) EXAMPLE  
Async Function TaskOfT_MethodAsync() As Task(Of Integer)  
  
    ' The body of an async method is expected to contain an awaited   
    ' asynchronous call.  
    ' Task.FromResult is a placeholder for actual work that returns a string.  
    Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())  
  
    ' The method then can process the result in some way.  
    Dim leisureHours As Integer  
    If today.First() = "S" Then  
        leisureHours = 16  
    Else  
        leisureHours = 5  
    End If  
  
    ' Because the return statement specifies an operand of type Integer, the   
    ' method must have a return type of Task(Of Integer).   
    Return leisureHours  
End Function  
```  
  
 <span data-ttu-id="6f7a4-112">從 await 運算式內呼叫 `TaskOfT_MethodAsync` 時，await 運算式會擷取儲存在 `TaskOfT_MethodAsync` 所傳回之工作中的整數值 (`leisureHours` 的值)。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-112">When `TaskOfT_MethodAsync` is called from within an await expression, the await expression retrieves the integer value (the value of `leisureHours`) that's stored in the task that's returned by `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="6f7a4-113">如需 await 運算式的詳細資訊，請參閱[Await 運算子](../../../../visual-basic/language-reference/operators/await-operator.md)。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-113">For more information about await expressions, see [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md).</span></span>  
  
 <span data-ttu-id="6f7a4-114">下列程式碼會呼叫並等候方法 `TaskOfT_MethodAsync`。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-114">The following code calls and awaits method `TaskOfT_MethodAsync`.</span></span> <span data-ttu-id="6f7a4-115">結果會指派給 `result1` 變數。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-115">The result is assigned to the `result1` variable.</span></span>  
  
```vb  
' Call and await the Task(Of T)-returning async method in the same statement.  
Dim result1 As Integer = Await TaskOfT_MethodAsync()  
```  
  
 <span data-ttu-id="6f7a4-116">您可以藉由區隔對 `TaskOfT_MethodAsync` 的呼叫與 `Await` 的應用，深入了解這種運作方式，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-116">You can better understand how this happens by separating the call to `TaskOfT_MethodAsync` from the application of `Await`, as the following code shows.</span></span> <span data-ttu-id="6f7a4-117">呼叫不會立即等候的 `TaskOfT_MethodAsync` 方法，會傳回 `Task(Of Integer)`，如您所預期的方法宣告。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-117">A call to method `TaskOfT_MethodAsync` that isn't immediately awaited returns a `Task(Of Integer)`, as you would expect from the declaration of the method.</span></span> <span data-ttu-id="6f7a4-118">在範例中，工作會指派給 `integerTask` 變數。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-118">The task is assigned to the `integerTask` variable in the example.</span></span> <span data-ttu-id="6f7a4-119">因為 `integerTask` 是 <xref:System.Threading.Tasks.Task%601>，所以它包含 `TResult` 類型的 <xref:System.Threading.Tasks.Task%601.Result> 屬性。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-119">Because `integerTask` is a <xref:System.Threading.Tasks.Task%601>, it contains a <xref:System.Threading.Tasks.Task%601.Result> property of type `TResult`.</span></span> <span data-ttu-id="6f7a4-120">在此情況下，TResult 代表整數類型。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-120">In this case, TResult represents an integer type.</span></span> <span data-ttu-id="6f7a4-121">當 `Await` 套用至 `integerTask` 時，await 運算式評估為 `integerTask` 之 <xref:System.Threading.Tasks.Task%601.Result%2A> 屬性的內容。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-121">When `Await` is applied to `integerTask`, the await expression evaluates to the contents of the <xref:System.Threading.Tasks.Task%601.Result%2A> property of `integerTask`.</span></span> <span data-ttu-id="6f7a4-122">值會指派給 `result2` 變數。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-122">The value is assigned to the `result2` variable.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="6f7a4-123"><xref:System.Threading.Tasks.Task%601.Result%2A> 屬性是封鎖的屬性。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-123">The <xref:System.Threading.Tasks.Task%601.Result%2A> property is a blocking property.</span></span> <span data-ttu-id="6f7a4-124">如果您嘗試在其工作完成之前先存取它，目前使用中的執行緒會封鎖，直到工作完成並且有可用的值為止。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-124">If you try to access it before its task is finished, the thread that's currently active is blocked until the task completes and the value is available.</span></span> <span data-ttu-id="6f7a4-125">在大部分情況下，您應該使用 `Await` 來存取值，而不是直接存取屬性。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-125">In most cases, you should access the value by using `Await` instead of accessing the property directly.</span></span>  
  
```vb  
' Call and await in separate statements.  
Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
' You can do other work that does not rely on resultTask before awaiting.  
textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
Dim result2 As Integer = Await integerTask  
```  
  
 <span data-ttu-id="6f7a4-126">下列程式碼中的 display 陳述式會驗證 `result1` 變數、`result2` 變數和 `Result` 屬性的值相同。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-126">The display statements in the following code verify that the values of the `result1` variable, the `result2` variable, and the `Result` property are the same.</span></span> <span data-ttu-id="6f7a4-127">請記住，`Result` 屬性是封鎖屬性，在等候其工作之前不應該存取它。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-127">Remember that the `Result` property is a blocking property and shouldn't be accessed before its task has been awaited.</span></span>  
  
```vb  
' Display the values of the result1 variable, the result2 variable, and  
' the resultTask.Result property.  
textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
```  
  
## <a name="BKMK_TaskReturnType"></a> <span data-ttu-id="6f7a4-128">工作傳回型別</span><span class="sxs-lookup"><span data-stu-id="6f7a4-128">Task Return Type</span></span>  
 <span data-ttu-id="6f7a4-129">不包含 return 陳述式的非同步方法，或包含不會傳回運算元的 return 陳述式的非同步方法，通常具有傳回型別 <xref:System.Threading.Tasks.Task>。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-129">Async methods that don't contain a return statement or that contain a return statement that doesn't return an operand usually have a return type of <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="6f7a4-130">這類方法是撰寫成同步執行的[Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md)程式。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-130">Such methods would be [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md) procedures if they were written to run synchronously.</span></span> <span data-ttu-id="6f7a4-131">如果您針對非同步方法使用 `Task` 傳回型別，則除非被呼叫的非同步方法完成，否則呼叫的方法可以使用 `Await` 運算子暫止呼叫端完成。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-131">If you use a `Task` return type for an async method, a calling method can use an `Await` operator to suspend the caller's completion until the called async method has finished.</span></span>  
  
 <span data-ttu-id="6f7a4-132">在下列範例中，非同步方法 `Task_MethodAsync` 不包含 return 陳述式。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-132">In the following example, async method `Task_MethodAsync` doesn't contain a return statement.</span></span> <span data-ttu-id="6f7a4-133">因此，您為方法指定 `Task` 傳回型別，如此可等候 `Task_MethodAsync`。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-133">Therefore, you specify a return type of `Task` for the method, which enables `Task_MethodAsync` to be awaited.</span></span> <span data-ttu-id="6f7a4-134">`Task` 類型的定義不包含用來儲存傳回值的 `Result` 屬性。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-134">The definition of the `Task` type doesn't include a `Result` property to store a return value.</span></span>  
  
```vb  
' TASK EXAMPLE  
Async Function Task_MethodAsync() As Task  
  
    ' The body of an async method is expected to contain an awaited   
    ' asynchronous call.  
    ' Task.Delay is a placeholder for actual work.  
    Await Task.Delay(2000)  
    textBox1.Text &= String.Format(vbCrLf & "Sorry for the delay. . . ." & vbCrLf)  
  
    ' This method has no return statement, so its return type is Task.   
End Function  
```  
  
 <span data-ttu-id="6f7a4-135">使用 await 陳述式呼叫並等候 `Task_MethodAsync`，而不是使用 await 運算式，類似於同步 `Sub` 或傳回 void 方法的呼叫陳述式。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-135">`Task_MethodAsync` is called and awaited by using an await statement instead of an await expression, similar to the calling statement for a synchronous `Sub` or void-returning method.</span></span> <span data-ttu-id="6f7a4-136">在此情況下`Await` ，運算子的應用不會產生值。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-136">The application of an `Await` operator in this case doesn't produce a value.</span></span>  
  
 <span data-ttu-id="6f7a4-137">下列程式碼會呼叫並等候方法 `Task_MethodAsync`。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-137">The following code calls and awaits method `Task_MethodAsync`.</span></span>  
  
```vb  
' Call and await the Task-returning async method in the same statement.  
Await Task_MethodAsync()  
```  
  
 <span data-ttu-id="6f7a4-138">如先前<xref:System.Threading.Tasks.Task%601>範例所示，您可以`Task_MethodAsync` `Await`從運算子的應用程式中分隔的呼叫，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-138">As in the previous <xref:System.Threading.Tasks.Task%601> example, you can separate the call to `Task_MethodAsync` from the application of an `Await` operator, as the following code shows.</span></span> <span data-ttu-id="6f7a4-139">不過，請記住，`Task` 沒有 `Result` 屬性，且將 await 運算子套用至 `Task` 時不會產生任何值。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-139">However, remember that a `Task` doesn't have a `Result` property, and that no value is produced when an await operator is applied to a `Task`.</span></span>  
  
 <span data-ttu-id="6f7a4-140">下列程式碼會區隔 `Task_MethodAsync` 的呼叫與等候 `Task_MethodAsync` 傳回的工作。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-140">The following code separates calling `Task_MethodAsync` from awaiting the task that `Task_MethodAsync` returns.</span></span>  
  
```vb  
' Call and await in separate statements.  
Dim simpleTask As Task = Task_MethodAsync()  
  
' You can do other work that does not rely on simpleTask before awaiting.  
textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
Await simpleTask  
```  
  
## <a name="BKMK_VoidReturnType"></a> <span data-ttu-id="6f7a4-141">Void 傳回型別</span><span class="sxs-lookup"><span data-stu-id="6f7a4-141">Void Return Type</span></span>  
 <span data-ttu-id="6f7a4-142">`Sub`程式的主要用途是在事件處理常式中，沒有傳回型別（稱為其他語言的 void 傳回型別）。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-142">The primary use of `Sub` procedures is in event handlers, where there is no return type (referred to as a void return type in other languages).</span></span> <span data-ttu-id="6f7a4-143">void 傳回也可用來覆寫傳回 void 的方法，或執行可分類為「射後不理」(fire and forget) 之活動的方法。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-143">A void return also can be used to override void-returning methods or for methods that perform activities that can be categorized as "fire and forget."</span></span> <span data-ttu-id="6f7a4-144">不過，您應該盡可能傳回 `Task`，因為無法等候傳回 void 的非同步方法。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-144">However, you should return a `Task` wherever possible, because a void-returning async method can't be awaited.</span></span> <span data-ttu-id="6f7a4-145">這種方法的任何呼叫端必須要能夠繼續完成而不需等待呼叫的非同步方法完成，且呼叫端必須與非同步方法產生的任何值或例外狀況無關。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-145">Any caller of such a method must be able to continue to completion without waiting for the called async method to finish, and the caller must be independent of any values or exceptions that the async method generates.</span></span>  
  
 <span data-ttu-id="6f7a4-146">傳回 void 的非同步方法的呼叫端無法攔截方法擲回的例外狀況，這類未處理的例外狀況有可能造成應用程式失敗。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-146">The caller of a void-returning async method can't catch exceptions that are thrown from the method, and such unhandled exceptions are likely to cause your application to fail.</span></span> <span data-ttu-id="6f7a4-147">如果例外狀況發生在會傳回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 的非同步方法，則例外狀況會儲存在傳回的工作中，並在等候工作時再次擲回。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-147">If an exception occurs in an async method that returns a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601>, the exception is stored in the returned task, and rethrown when the task is awaited.</span></span> <span data-ttu-id="6f7a4-148">因此，請確定任何可能會產生例外狀況的非同步方法具有傳回型別 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601>，且會等候對方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-148">Therefore, make sure that any async method that can produce an exception has a return type of <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> and that calls to the method are awaited.</span></span>  
  
 <span data-ttu-id="6f7a4-149">如需如何在非同步方法中攔截例外狀況的詳細資訊，請參閱 [Try...Catch...Finally 陳述式](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-149">For more information about how to catch exceptions in async methods, see [Try...Catch...Finally Statement](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).</span></span>  
  
 <span data-ttu-id="6f7a4-150">下列程式碼會定義非同步事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-150">The following code defines an async event handler.</span></span>  
  
```vb  
' SUB EXAMPLE  
Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
  
    textBox1.Clear()  
  
    ' Start the process and await its completion. DriverAsync is a   
    ' Task-returning async method.  
    Await DriverAsync()  
  
    ' Say goodbye.  
    textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."  
End Sub  
```  
  
## <a name="BKMK_Example"></a> <span data-ttu-id="6f7a4-151">完整範例</span><span class="sxs-lookup"><span data-stu-id="6f7a4-151">Complete Example</span></span>  
 <span data-ttu-id="6f7a4-152">下列 Windows Presentation Foundation (WPF) 專案包含本土的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-152">The following Windows Presentation Foundation (WPF) project contains the code examples from this topic.</span></span>  
  
 <span data-ttu-id="6f7a4-153">若要執行專案，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="6f7a4-153">To run the project, perform the following steps:</span></span>  
  
1. <span data-ttu-id="6f7a4-154">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-154">Start Visual Studio.</span></span>  
  
2. <span data-ttu-id="6f7a4-155">在功能表列上，選擇 [檔案]、[新增]、[專案]。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-155">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="6f7a4-156">[ **新增專案** ] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-156">The **New Project** dialog box opens.</span></span>  
  
3. <span data-ttu-id="6f7a4-157">在 [**已安裝**的**範本**] 分類中，選擇 [ **Visual Basic**]，然後選擇 [ **Windows**]。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-157">In the **Installed**, **Templates** category, choose **Visual Basic**, and then choose **Windows**.</span></span> <span data-ttu-id="6f7a4-158">在專案類型清單中，選擇 [WPF 應用程式]。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-158">Choose **WPF Application** from the list of project types.</span></span>  
  
4. <span data-ttu-id="6f7a4-159">輸入 `AsyncReturnTypes` 作為專案的名稱，然後選擇 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-159">Enter `AsyncReturnTypes` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="6f7a4-160">新的專案隨即出現在方案總管中。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-160">The new project appears in **Solution Explorer**.</span></span>  
  
5. <span data-ttu-id="6f7a4-161">在 Visual Studio 程式碼編輯器中，選擇 [ **MainWindow.xaml** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-161">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="6f7a4-162">如果未顯示索引標籤，請在方案總管中開啟 MainWindow.xaml 的捷徑功能表，然後選擇 [開啟]。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-162">If the tab is not visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **Open**.</span></span>  
  
6. <span data-ttu-id="6f7a4-163">在 MainWindow.xaml 的 [XAML] 視窗中，將程式碼取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-163">In the **XAML** window of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```vb  
    <Window x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            Title="MainWindow" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="button1" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="button1_Click"/>  
            <TextBox x:Name="textBox1" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>  
  
        </Grid>  
    </Window>  
    ```  
  
     <span data-ttu-id="6f7a4-164">包含文字方塊和按鈕的簡單視窗會出現在 MainWindow.xaml 的 [設計] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-164">A simple window that contains a text box and a button appears in the **Design** window of MainWindow.xaml.</span></span>  
  
7. <span data-ttu-id="6f7a4-165">在**方案總管**中，開啟 mainwindow.xaml 的快捷方式功能表，然後選擇 [ **View Code**]。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-165">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
8. <span data-ttu-id="6f7a4-166">以下列程式碼取代 MainWindow.xaml.vb 中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-166">Replace the code in MainWindow.xaml.vb with the following code.</span></span>  
  
    ```vb  
    Class MainWindow  
  
        ' SUB EXAMPLE  
        Async Sub button1_Click(sender As Object, e As RoutedEventArgs) Handles button1.Click  
  
            textBox1.Clear()  
  
            ' Start the process and await its completion. DriverAsync is a   
            ' Task-returning async method.  
            Await DriverAsync()  
  
            ' Say goodbye.  
            textBox1.Text &= vbCrLf & "All done, exiting button-click event handler."  
        End Sub  
  
        Async Function DriverAsync() As Task  
  
            ' Task(Of T)   
            ' Call and await the Task(Of T)-returning async method in the same statement.  
            Dim result1 As Integer = Await TaskOfT_MethodAsync()  
  
            ' Call and await in separate statements.  
            Dim integerTask As Task(Of Integer) = TaskOfT_MethodAsync()  
  
            ' You can do other work that does not rely on resultTask before awaiting.  
            textBox1.Text &= String.Format("Application can continue working while the Task(Of T) runs. . . . " & vbCrLf)  
  
            Dim result2 As Integer = Await integerTask  
  
            ' Display the values of the result1 variable, the result2 variable, and  
            ' the resultTask.Result property.  
            textBox1.Text &= String.Format(vbCrLf & "Value of result1 variable:   {0}" & vbCrLf, result1)  
            textBox1.Text &= String.Format("Value of result2 variable:   {0}" & vbCrLf, result2)  
            textBox1.Text &= String.Format("Value of resultTask.Result:  {0}" & vbCrLf, integerTask.Result)  
  
            ' Task   
            ' Call and await the Task-returning async method in the same statement.  
            Await Task_MethodAsync()  
  
            ' Call and await in separate statements.  
            Dim simpleTask As Task = Task_MethodAsync()  
  
            ' You can do other work that does not rely on simpleTask before awaiting.  
            textBox1.Text &= String.Format(vbCrLf & "Application can continue working while the Task runs. . . ." & vbCrLf)  
  
            Await simpleTask  
        End Function  
  
        ' TASK(OF T) EXAMPLE  
        Async Function TaskOfT_MethodAsync() As Task(Of Integer)  
  
            ' The body of an async method is expected to contain an awaited   
            ' asynchronous call.  
            ' Task.FromResult is a placeholder for actual work that returns a string.  
            Dim today As String = Await Task.FromResult(Of String)(DateTime.Now.DayOfWeek.ToString())  
  
            ' The method then can process the result in some way.  
            Dim leisureHours As Integer  
            If today.First() = "S" Then  
                leisureHours = 16  
            Else  
                leisureHours = 5  
            End If  
  
            ' Because the return statement specifies an operand of type Integer, the   
            ' method must have a return type of Task(Of Integer).   
            Return leisureHours  
        End Function  
  
        ' TASK EXAMPLE  
        Async Function Task_MethodAsync() As Task  
  
            ' The body of an async method is expected to contain an awaited   
            ' asynchronous call.  
            ' Task.Delay is a placeholder for actual work.  
            Await Task.Delay(2000)  
            textBox1.Text &= String.Format(vbCrLf & "Sorry for the delay. . . ." & vbCrLf)  
  
            ' This method has no return statement, so its return type is Task.   
        End Function  
  
    End Class  
    ```  
  
9. <span data-ttu-id="6f7a4-167">選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-167">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="6f7a4-168">應該出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="6f7a4-168">The following output should appear.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6f7a4-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f7a4-169">See also</span></span>

- <xref:System.Threading.Tasks.Task.FromResult%2A>
- [<span data-ttu-id="6f7a4-170">逐步解說：使用 Async 和 Await 存取 Web （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="6f7a4-170">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="6f7a4-171">非同步程式中的控制流程 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6f7a4-171">Control Flow in Async Programs (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)
- [<span data-ttu-id="6f7a4-172">Async</span><span class="sxs-lookup"><span data-stu-id="6f7a4-172">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)
- [<span data-ttu-id="6f7a4-173">Await 運算子</span><span class="sxs-lookup"><span data-stu-id="6f7a4-173">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)
