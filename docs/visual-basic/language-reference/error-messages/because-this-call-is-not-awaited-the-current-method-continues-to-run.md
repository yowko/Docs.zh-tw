---
title: 因為未等候此呼叫，所以在呼叫完成之前會繼續執行目前方法
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42358
- vbc42358
helpviewer_keywords:
- BC42358
ms.assetid: 43342515-c3c8-4155-9263-c302afabcbc2
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a0d0a5e7c50bacc657a3f54a7f08036ede59cbfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="because-this-call-is-not-awaited-the-current-method-continues-to-run-before-the-call-is-completed"></a><span data-ttu-id="0740a-102">因為未等候此呼叫，所以在呼叫完成之前會繼續執行目前方法</span><span class="sxs-lookup"><span data-stu-id="0740a-102">Because this call is not awaited, the current method continues to run before the call is completed</span></span>
<span data-ttu-id="0740a-103">因為未等候此呼叫，所以在呼叫完成之前會繼續執行目前的方法。</span><span class="sxs-lookup"><span data-stu-id="0740a-103">Because this call is not awaited, execution of the current method continues before the call is completed.</span></span> <span data-ttu-id="0740a-104">請考慮將 'Await' 運算子套用至呼叫的結果。</span><span class="sxs-lookup"><span data-stu-id="0740a-104">Consider applying the 'Await' operator to the result of the call.</span></span>  
  
 <span data-ttu-id="0740a-105">目前的方法會呼叫傳回 <xref:System.Threading.Tasks.Task> 或 <xref:System.Threading.Tasks.Task%601> 且不會將 [Await](../../../visual-basic/language-reference/operators/await-operator.md) 運算子套用至結果的非同步方法。</span><span class="sxs-lookup"><span data-stu-id="0740a-105">The current method calls an async method that returns a <xref:System.Threading.Tasks.Task> or a <xref:System.Threading.Tasks.Task%601> and doesn’t apply the [Await](../../../visual-basic/language-reference/operators/await-operator.md) operator to the result.</span></span> <span data-ttu-id="0740a-106">非同步方法的呼叫會啟動非同步工作。</span><span class="sxs-lookup"><span data-stu-id="0740a-106">The call to the async method starts an asynchronous task.</span></span> <span data-ttu-id="0740a-107">不過，由於不會套用任何 `Await` 運算子，因此程式會繼續執行，而不等候工作完成。</span><span class="sxs-lookup"><span data-stu-id="0740a-107">However, because no `Await` operator is applied, the program continues without waiting for the task to complete.</span></span> <span data-ttu-id="0740a-108">在大部分情況下，不應該有此行為。</span><span class="sxs-lookup"><span data-stu-id="0740a-108">In most cases, that behavior isn't expected.</span></span> <span data-ttu-id="0740a-109">通常呼叫方法的其他方面取決於呼叫的結果，或至少被呼叫的方法必須完成，才能從包含呼叫的方法傳回。</span><span class="sxs-lookup"><span data-stu-id="0740a-109">Usually other aspects of the calling method depend on the results of the call or, minimally, the called method is expected to complete before you return from the method that contains the call.</span></span>  
  
 <span data-ttu-id="0740a-110">同樣重要的問題是，在呼叫的非同步方法中引發的例外狀況會發生什麼情形。</span><span class="sxs-lookup"><span data-stu-id="0740a-110">An equally important issue is what happens with exceptions that are raised in the called async method.</span></span> <span data-ttu-id="0740a-111">在傳回 <xref:System.Threading.Tasks.Task> 或  <xref:System.Threading.Tasks.Task%601> 的方法中引發的例外狀況會儲存到傳回的工作中。</span><span class="sxs-lookup"><span data-stu-id="0740a-111">An exception that’s raised in a method that returns a <xref:System.Threading.Tasks.Task> or  <xref:System.Threading.Tasks.Task%601> is stored in the returned task.</span></span> <span data-ttu-id="0740a-112">如果您未等候工作，也未明確檢查例外狀況，例外狀況就會遺失。</span><span class="sxs-lookup"><span data-stu-id="0740a-112">If you don't await the task or explicitly check for exceptions, the exception is lost.</span></span> <span data-ttu-id="0740a-113">如果您等候工作，則其例外狀況會再次擲回。</span><span class="sxs-lookup"><span data-stu-id="0740a-113">If you await the task, its exception is rethrown.</span></span>  
  
 <span data-ttu-id="0740a-114">因此最佳做法是一律等候呼叫。</span><span class="sxs-lookup"><span data-stu-id="0740a-114">As a best practice, you should always await the call.</span></span>  
  
 <span data-ttu-id="0740a-115">根據預設，這個訊息是一個警告。</span><span class="sxs-lookup"><span data-stu-id="0740a-115">By default, this message is a warning.</span></span> <span data-ttu-id="0740a-116">如需隱藏警告或將警告視為錯誤的詳細資訊，請參閱[Visual Basic 中的 設定警告](/visualstudio/ide/configuring-warnings-in-visual-basic)。</span><span class="sxs-lookup"><span data-stu-id="0740a-116">For more information about hiding warnings or treating warnings as errors, see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="0740a-117">**錯誤 ID︰** BC42358</span><span class="sxs-lookup"><span data-stu-id="0740a-117">**Error ID:** BC42358</span></span>  
  
### <a name="to-address-this-warning"></a><span data-ttu-id="0740a-118">解決這個警告</span><span class="sxs-lookup"><span data-stu-id="0740a-118">To address this warning</span></span>  
  
-   <span data-ttu-id="0740a-119">只有在您確定不要等候非同步呼叫完成，而且被呼叫的方法不會引發任何例外狀況時，才應考慮隱藏警告。</span><span class="sxs-lookup"><span data-stu-id="0740a-119">You should consider suppressing the warning only if you're sure that you don't want to wait for the asynchronous call to complete and that the called method won't raise any exceptions.</span></span> <span data-ttu-id="0740a-120">在這種情況下，您可以藉由將呼叫的工作結果指定至變數來隱藏警告。</span><span class="sxs-lookup"><span data-stu-id="0740a-120">In that case, you can suppress the warning by assigning the task result of the call to a variable.</span></span>  
  
     <span data-ttu-id="0740a-121">下列範例將示範如何產生警告、如何隱藏警告，以及如何等候呼叫。</span><span class="sxs-lookup"><span data-stu-id="0740a-121">The following example shows how to cause the warning, how to suppress it, and how to await the call.</span></span>  
  
    ```vb  
    Async Function CallingMethodAsync() As Task  
  
        ResultsTextBox.Text &= vbCrLf & "  Entering calling method."  
  
        ' Variable delay is used to slow down the called method so that you  
        ' can distinguish between awaiting and not awaiting in the program's output.   
        ' You can adjust the value to produce the output that this topic shows   
        ' after the code.  
        Dim delay = 5000  
  
        ' Call #1.  
        ' Call an async method. Because you don't await it, its completion isn't   
        ' coordinated with the current method, CallingMethodAsync.  
        ' The following line causes the warning.  
        CalledMethodAsync(delay)  
  
        ' Call #2.  
        ' To suppress the warning without awaiting, you can assign the   
        ' returned task to a variable. The assignment doesn't change how  
        ' the program runs. However, the recommended practice is always to  
        ' await a call to an async method.  
        ' Replace Call #1 with the following line.  
        'Task delayTask = CalledMethodAsync(delay)  
  
        ' Call #3  
        ' To contrast with an awaited call, replace the unawaited call   
        ' (Call #1 or Call #2) with the following awaited call. The best   
        ' practice is to await the call.  
  
        'Await CalledMethodAsync(delay)  
  
        ' If the call to CalledMethodAsync isn't awaited, CallingMethodAsync  
        ' continues to run and, in this example, finishes its work and returns  
        ' to its caller.  
        ResultsTextBox.Text &= vbCrLf & "  Returning from calling method."  
    End Function  
  
    Async Function CalledMethodAsync(howLong As Integer) As Task  
  
        ResultsTextBox.Text &= vbCrLf & "    Entering called method, starting and awaiting Task.Delay."  
        ' Slow the process down a little so you can distinguish between awaiting  
        ' and not awaiting. Adjust the value for howLong if necessary.  
        Await Task.Delay(howLong)  
        ResultsTextBox.Text &= vbCrLf & "    Task.Delay is finished--returning from called method."  
    End Function  
    ```  
  
     <span data-ttu-id="0740a-122">在此範例中，如果您選擇呼叫 #1 或呼叫 #2，則未等候的非同步方法 (`CalledMethodAsync`) 會在其呼叫端 (`CallingMethodAsync`) 和呼叫端的呼叫端 (`StartButton_Click`) 都完成之後才完成。</span><span class="sxs-lookup"><span data-stu-id="0740a-122">In the example, if you choose Call #1 or Call #2, the unawaited async method (`CalledMethodAsync`) finishes after both its caller (`CallingMethodAsync`) and the caller's caller (`StartButton_Click`) are complete.</span></span> <span data-ttu-id="0740a-123">下列輸出的最後一行將顯示被呼叫的方法完成的時間。</span><span class="sxs-lookup"><span data-stu-id="0740a-123">The last line in the following output shows you when the called method finishes.</span></span> <span data-ttu-id="0740a-124">輸入中會標記在完整範例中進入和結束呼叫 `CallingMethodAsync` 的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="0740a-124">Entry to and exit from the event handler that calls `CallingMethodAsync` in the full example are marked in the output.</span></span>  
  
    ```  
    Entering the Click event handler.  
      Entering calling method.  
        Entering called method, starting and awaiting Task.Delay.  
      Returning from calling method.  
    Exiting the Click event handler.  
        Task.Delay is finished--returning from called method.  
    ```  
  
## <a name="example"></a><span data-ttu-id="0740a-125">範例</span><span class="sxs-lookup"><span data-stu-id="0740a-125">Example</span></span>  
 <span data-ttu-id="0740a-126">下列 Windows Presentation Foundation (WPF) 應用程式包含了前述範例的方法。</span><span class="sxs-lookup"><span data-stu-id="0740a-126">The following Windows Presentation Foundation (WPF) application contains the methods from the previous example.</span></span> <span data-ttu-id="0740a-127">下列步驟將會設定應用程式。</span><span class="sxs-lookup"><span data-stu-id="0740a-127">The following steps set up the application.</span></span>  
  
1.  <span data-ttu-id="0740a-128">建立 WPF 應用程式，並將其命名為 `AsyncWarning`。</span><span class="sxs-lookup"><span data-stu-id="0740a-128">Create a WPF application, and name it `AsyncWarning`.</span></span>  
  
2.  <span data-ttu-id="0740a-129">在 Visual Studio 程式碼編輯器中，選擇 [ **MainWindow.xaml** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0740a-129">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="0740a-130">如果未顯示索引標籤，請在 [ **方案總管**] 中開啟 MainWindow.xaml 的捷徑功能表，然後選擇 [ **檢視程式碼**]。</span><span class="sxs-lookup"><span data-stu-id="0740a-130">If the tab isn't visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
3.  <span data-ttu-id="0740a-131">在 MainWindow.xaml 的 [ **XAML** ] 檢視中，將程式碼取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="0740a-131">Replace the code in the **XAML** view of MainWindow.xaml with the following code.</span></span>  
  
    ```vb  
    <Window x:Class="MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            Title="MainWindow" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="StartButton_Click" />  
            <TextBox x:Name="ResultsTextBox" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>  
        </Grid>  
    </Window>  
    ```  
  
     <span data-ttu-id="0740a-132">包含按鈕和文字方塊的簡單視窗會出現在 MainWindow.xaml 的 [ **設計** ] 檢視中。</span><span class="sxs-lookup"><span data-stu-id="0740a-132">A simple window that contains a button and a text box appears in the **Design** view of MainWindow.xaml.</span></span>  
  
     <span data-ttu-id="0740a-133">如需 XAML 設計工具的詳細資訊，請參閱[使用 XAML 設計工具建立 UI](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="0740a-133">For more information about the XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span> <span data-ttu-id="0740a-134">如需如何建置您自己的簡單 UI 的資訊，請參閱[逐步解說：使用 Async 和 Await 存取 Web](http://msdn.microsoft.com/library/25879a6d-fdee-4a38-bc98-bb8c24d16042)的＜建立 WPF 應用程式＞和＜設計簡單的 WPF MainWindow＞章節。</span><span class="sxs-lookup"><span data-stu-id="0740a-134">For information about how to build your own simple UI, see the "To create a WPF application" and "To design a simple WPF MainWindow" sections of [Walkthrough: Accessing the Web by Using Async and Await](http://msdn.microsoft.com/library/25879a6d-fdee-4a38-bc98-bb8c24d16042).</span></span>  
  
4.  <span data-ttu-id="0740a-135">以下列程式碼取代 MainWindow.xaml.vb 中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0740a-135">Replace the code in MainWindow.xaml.vb with the following code.</span></span>  
  
    ```vb  
    Class MainWindow   
  
        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
  
            ResultsTextBox.Text &= vbCrLf & "Entering the Click event handler."  
            Await CallingMethodAsync()  
            ResultsTextBox.Text &= vbCrLf & "Exiting the Click event handler."  
        End Sub  
  
        Async Function CallingMethodAsync() As Task  
  
            ResultsTextBox.Text &= vbCrLf & "  Entering calling method."  
  
            ' Variable delay is used to slow down the called method so that you  
            ' can distinguish between awaiting and not awaiting in the program's output.   
            ' You can adjust the value to produce the output that this topic shows   
            ' after the code.  
            Dim delay = 5000  
  
            ' Call #1.  
            ' Call an async method. Because you don't await it, its completion isn't   
            ' coordinated with the current method, CallingMethodAsync.  
            ' The following line causes the warning.  
            CalledMethodAsync(delay)  
  
            ' Call #2.  
            ' To suppress the warning without awaiting, you can assign the   
            ' returned task to a variable. The assignment doesn't change how  
            ' the program runs. However, the recommended practice is always to  
            ' await a call to an async method.  
  
            ' Replace Call #1 with the following line.  
            'Task delayTask = CalledMethodAsync(delay)  
  
            ' Call #3  
            ' To contrast with an awaited call, replace the unawaited call   
            ' (Call #1 or Call #2) with the following awaited call. The best   
            ' practice is to await the call.  
  
            'Await CalledMethodAsync(delay)  
  
            ' If the call to CalledMethodAsync isn't awaited, CallingMethodAsync  
            ' continues to run and, in this example, finishes its work and returns  
            ' to its caller.  
            ResultsTextBox.Text &= vbCrLf & "  Returning from calling method."  
        End Function  
  
        Async Function CalledMethodAsync(howLong As Integer) As Task  
  
            ResultsTextBox.Text &= vbCrLf & "    Entering called method, starting and awaiting Task.Delay."  
            ' Slow the process down a little so you can distinguish between awaiting  
            ' and not awaiting. Adjust the value for howLong if necessary.  
            Await Task.Delay(howLong)  
            ResultsTextBox.Text &= vbCrLf & "    Task.Delay is finished--returning from called method."  
        End Function  
  
    End Class  
  
    ' Output  
  
    ' Entering the Click event handler.  
    '   Entering calling method.  
    '     Entering called method, starting and awaiting Task.Delay.  
    '   Returning from calling method.  
    ' Exiting the Click event handler.  
    '     Task.Delay is finished--returning from called method.  
  
    ' Output  
  
    ' Entering the Click event handler.  
    '   Entering calling method.  
    '     Entering called method, starting and awaiting Task.Delay.  
    '     Task.Delay is finished--returning from called method.  
    '   Returning from calling method.  
    ' Exiting the Click event handler.  
    ```  
  
5.  <span data-ttu-id="0740a-136">選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0740a-136">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="0740a-137">預期的輸出會出現在程式碼結尾。</span><span class="sxs-lookup"><span data-stu-id="0740a-137">The expected output appears at the end of the code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0740a-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0740a-138">See Also</span></span>  
 [<span data-ttu-id="0740a-139">Await 運算子</span><span class="sxs-lookup"><span data-stu-id="0740a-139">Await Operator</span></span>](../../../visual-basic/language-reference/operators/await-operator.md)  
 [<span data-ttu-id="0740a-140">使用 Async 和 Await 進行非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="0740a-140">Asynchronous Programming with Async and Await</span></span>](../../../visual-basic/programming-guide/concepts/async/index.md)
