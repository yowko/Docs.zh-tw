---
title: "如何︰ 同時發出多個 Web 要求使用 Async 和 Await (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: a894b99b-7cfd-4a38-adfb-20d24f986730
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 14abadaf548e228244a1ff7ca72fa3896ef4eb5d
ms.openlocfilehash: af0917bebd54fe713b620be92087279e8f580fbb
ms.contentlocale: zh-tw
ms.lasthandoff: 05/23/2017

---
# <a name="how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await-visual-basic"></a><span data-ttu-id="5c663-102">如何︰ 同時發出多個 Web 要求使用 Async 和 Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5c663-102">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>
<span data-ttu-id="5c663-103">在非同步方法，在建立時即會啟動工作。</span><span class="sxs-lookup"><span data-stu-id="5c663-103">In an async method, tasks are started when they’re created.</span></span> <span data-ttu-id="5c663-104">[Await](../../../../visual-basic/language-reference/operators/await-operator.md)運算子會套用至方法中的點，而無法繼續處理直到工作完成工作。</span><span class="sxs-lookup"><span data-stu-id="5c663-104">The [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator is applied to the task at the point in the method where processing can’t continue until the task finishes.</span></span> <span data-ttu-id="5c663-105">通常工作會等候由於它建立，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="5c663-105">Often a task is awaited as soon as it’s created, as the following example shows.</span></span>  
  
```vb  
Dim result = Await someWebAccessMethodAsync(url)  
```  
  
 <span data-ttu-id="5c663-106">不過，您可以將建立不相關的工作完成從等候工作，如果您的程式有其他工作来完成工作。</span><span class="sxs-lookup"><span data-stu-id="5c663-106">However, you can separate creating the task from awaiting the task if your program has other work to accomplish that doesn’t depend on the completion of the task.</span></span>  
  
```vb  
' The following line creates and starts the task.  
Dim myTask = someWebAccessMethodAsync(url)  
  
' While the task is running, you can do other work that does not depend  
' on the results of the task.  
' . . . . .  
  
' The application of Await suspends the rest of this method until the task is   
' complete.  
Dim result = Await myTask  
```  
  
 <span data-ttu-id="5c663-107">啟動工作和之間等候它，您可以啟動其他工作。</span><span class="sxs-lookup"><span data-stu-id="5c663-107">Between starting a task and awaiting it, you can start other tasks.</span></span> <span data-ttu-id="5c663-108">以平行方式，以隱含方式執行的其他工作，但沒有其他執行緒會建立。</span><span class="sxs-lookup"><span data-stu-id="5c663-108">The additional tasks implicitly run in parallel, but no additional threads are created.</span></span>  
  
 <span data-ttu-id="5c663-109">下列程式會啟動三個非同步 web 下載項目，然後等候它們在所呼叫的順序。</span><span class="sxs-lookup"><span data-stu-id="5c663-109">The following program starts three asynchronous web downloads and then awaits them in the order in which they’re called.</span></span> <span data-ttu-id="5c663-110">請注意，當您執行的程式，工作不一定都他們所建立，以及等候完成。</span><span class="sxs-lookup"><span data-stu-id="5c663-110">Notice, when you run the program, that the tasks don’t always finish in the order in which they’re created and awaited.</span></span> <span data-ttu-id="5c663-111">便會開始執行時建立的與之前的方法到達 await 運算式，則可能會完成一或多個工作。</span><span class="sxs-lookup"><span data-stu-id="5c663-111">They start to run when they’re created, and one or more of the tasks might finish before the method reaches the await expressions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5c663-112">若要完成此專案，您必須擁有 Visual Studio 2012 或更新版本和.NET Framework 4.5 或更新版本安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="5c663-112">To complete this project, you must have Visual Studio 2012 or higher and the .NET Framework 4.5 or higher installed on your computer.</span></span>  
  
 <span data-ttu-id="5c663-113">如需同時啟動多個工作的其他範例，請參閱[How to︰ 擴充非同步逐步解說使用 Task.WhenAll (Visual Basic) 的](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)。</span><span class="sxs-lookup"><span data-stu-id="5c663-113">For another example that starts multiple tasks at the same time, see [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>  
  
 <span data-ttu-id="5c663-114">您可以下載這個範例中的程式碼[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkId=254906)。</span><span class="sxs-lookup"><span data-stu-id="5c663-114">You can download the code for this example from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=254906).</span></span>  
  
### <a name="to-set-up-the-project"></a><span data-ttu-id="5c663-115">若要設定專案</span><span class="sxs-lookup"><span data-stu-id="5c663-115">To set up the project</span></span>  
  
1.  <span data-ttu-id="5c663-116">若要設定 WPF 應用程式，請完成下列步驟。</span><span class="sxs-lookup"><span data-stu-id="5c663-116">To set up a WPF application, complete the following steps.</span></span> <span data-ttu-id="5c663-117">您可以找到這些步驟的詳細的指示[逐步解說︰ 存取 Web 使用 Async 和 Await (Visual Basic) 的](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)。</span><span class="sxs-lookup"><span data-stu-id="5c663-117">You can find detailed instructions for these steps in [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
    -   <span data-ttu-id="5c663-118">建立 WPF 應用程式，其中包含一個文字方塊和按鈕。</span><span class="sxs-lookup"><span data-stu-id="5c663-118">Create a WPF application that contains a text box and a button.</span></span> <span data-ttu-id="5c663-119">將按鈕`startButton`，並將文字方塊`resultsTextBox`。</span><span class="sxs-lookup"><span data-stu-id="5c663-119">Name the button `startButton`, and name the text box `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="5c663-120">加入<xref:System.Net.Http>.</xref:System.Net.Http>的參考</span><span class="sxs-lookup"><span data-stu-id="5c663-120">Add a reference for <xref:System.Net.Http>.</span></span>  
  
    -   <span data-ttu-id="5c663-121">在 MainWindow.xaml.vb 檔案中，加入`Imports`陳述式`System.Net.Http`。</span><span class="sxs-lookup"><span data-stu-id="5c663-121">In the MainWindow.xaml.vb file, add an `Imports` statement for `System.Net.Http`.</span></span>  
  
### <a name="to-add-the-code"></a><span data-ttu-id="5c663-122">若要加入程式碼</span><span class="sxs-lookup"><span data-stu-id="5c663-122">To add the code</span></span>  
  
1.  <span data-ttu-id="5c663-123">在 [設計] 視窗，MainWindow.xaml，連按兩下按鈕，以建立`startButton_Click`MainWindow.xaml.vb 中的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5c663-123">In the design window, MainWindow.xaml, double-click the button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="5c663-124">下列程式碼中，複製並貼到主體`startButton_Click`MainWindow.xaml.vb 中。</span><span class="sxs-lookup"><span data-stu-id="5c663-124">Copy the following code, and paste it into the body of `startButton_Click` in MainWindow.xaml.vb.</span></span>  
  
    ```vb  
    resultsTextBox.Clear()  
    Await CreateMultipleTasksAsync()  
    resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    ```  
  
     <span data-ttu-id="5c663-125">程式碼會呼叫非同步方法， `CreateMultipleTasksAsync`，哪些磁碟機的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5c663-125">The code calls an asynchronous method, `CreateMultipleTasksAsync`, which drives the application.</span></span>  
  
3.  <span data-ttu-id="5c663-126">將下列的支援方法加入至專案︰</span><span class="sxs-lookup"><span data-stu-id="5c663-126">Add the following support methods to the project:</span></span>  
  
    -   <span data-ttu-id="5c663-127">`ProcessURLAsync`使用<xref:System.Net.Http.HttpClient>方法，以下載網站，以做為位元組陣列的內容。</xref:System.Net.Http.HttpClient></span><span class="sxs-lookup"><span data-stu-id="5c663-127">`ProcessURLAsync` uses an <xref:System.Net.Http.HttpClient> method to download the contents of a website as a byte array.</span></span> <span data-ttu-id="5c663-128">支援的方法，`ProcessURLAsync`然後顯示，並傳回陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="5c663-128">The support method, `ProcessURLAsync` then displays and returns the length of the array.</span></span>  
  
    -   <span data-ttu-id="5c663-129">`DisplayResults`顯示每個 URL 位元組陣列中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="5c663-129">`DisplayResults` displays the number of bytes in the byte array for each URL.</span></span> <span data-ttu-id="5c663-130">每一項工作已下載完成時，這會顯示說明。</span><span class="sxs-lookup"><span data-stu-id="5c663-130">This display shows when each task has finished downloading.</span></span>  
  
     <span data-ttu-id="5c663-131">將下列方法中，複製並貼上它們之後`startButton_Click`MainWindow.xaml.vb 中的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="5c663-131">Copy the following methods, and paste them after the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
    ```vb  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
    ```  
  
4.  <span data-ttu-id="5c663-132">最後，方法定義`CreateMultipleTasksAsync`，其可執行下列步驟。</span><span class="sxs-lookup"><span data-stu-id="5c663-132">Finally, define method `CreateMultipleTasksAsync`, which performs the following steps.</span></span>  
  
    -   <span data-ttu-id="5c663-133">方法宣告`HttpClient`物件，您需要存取方法<xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A>中`ProcessURLAsync`。</xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A></span><span class="sxs-lookup"><span data-stu-id="5c663-133">The method declares an `HttpClient` object,which you need  to access method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%2A> in `ProcessURLAsync`.</span></span>  
  
    -   <span data-ttu-id="5c663-134">此方法會建立並啟動三個類型的工作<xref:System.Threading.Tasks.Task%601>，其中`TResult`是一個整數。</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="5c663-134">The method creates and starts three tasks of type <xref:System.Threading.Tasks.Task%601>, where `TResult` is an integer.</span></span> <span data-ttu-id="5c663-135">隨著每個工作完成，`DisplayResults`會顯示工作的 URL 和下載內容的長度。</span><span class="sxs-lookup"><span data-stu-id="5c663-135">As each task finishes, `DisplayResults` displays the task's URL and the length of the downloaded contents.</span></span> <span data-ttu-id="5c663-136">因為工作都以非同步方式執行，結果會出現的順序可能會因所宣告的順序。</span><span class="sxs-lookup"><span data-stu-id="5c663-136">Because the tasks are running asynchronously, the order in which the results appear might differ from the order in which they were declared.</span></span>  
  
    -   <span data-ttu-id="5c663-137">此方法會等候每個工作的完成。</span><span class="sxs-lookup"><span data-stu-id="5c663-137">The method awaits the completion of each task.</span></span> <span data-ttu-id="5c663-138">每個`Await`運算子暫停執行`CreateMultipleTasksAsync`直到等候的工作。</span><span class="sxs-lookup"><span data-stu-id="5c663-138">Each `Await` operator suspends execution of `CreateMultipleTasksAsync` until the awaited task is finished.</span></span> <span data-ttu-id="5c663-139">運算子也會擷取傳回值，呼叫`ProcessURLAsync`從每個已完成的工作。</span><span class="sxs-lookup"><span data-stu-id="5c663-139">The operator also retrieves the return value from the call to `ProcessURLAsync` from each completed task.</span></span>  
  
    -   <span data-ttu-id="5c663-140">當工作完成後，已擷取的整數值的方法加總長度的網站，並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="5c663-140">When the tasks have been completed and the integer values have been retrieved, the method sums the lengths of the websites and displays the result.</span></span>  
  
     <span data-ttu-id="5c663-141">複製下列的方法，並將它貼到您的方案。</span><span class="sxs-lookup"><span data-stu-id="5c663-141">Copy the following method, and paste it into your solution.</span></span>  
  
    ```vb  
    Private Async Function CreateMultipleTasksAsync() As Task  
  
        ' Declare an HttpClient object, and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Create and start the tasks. As each task finishes, DisplayResults   
        ' displays its length.  
        Dim download1 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com", client)  
        Dim download2 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client)  
  
        ' Await each task.  
        Dim length1 As Integer = Await download1  
        Dim length2 As Integer = Await download2  
        Dim length3 As Integer = Await download3  
  
        Dim total As Integer = length1 + length2 + length3  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
    ```  
  
5.  <span data-ttu-id="5c663-142">選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5c663-142">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="5c663-143">若要確認三項工作不一定完成相同的順序和它們完成的順序不一定就是建立及等候的順序執行程式數次。</span><span class="sxs-lookup"><span data-stu-id="5c663-143">Run the program several times to verify that the three tasks don’t always finish in the same order and that the order in which they finish isn't necessarily the order in which they’re created and awaited.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c663-144">範例</span><span class="sxs-lookup"><span data-stu-id="5c663-144">Example</span></span>  
 <span data-ttu-id="5c663-145">下列程式碼包含完整的範例。</span><span class="sxs-lookup"><span data-stu-id="5c663-145">The following code contains the full example.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
        resultsTextBox.Clear()  
        Await CreateMultipleTasksAsync()  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
    End Sub  
  
    Private Async Function CreateMultipleTasksAsync() As Task  
  
        ' Declare an HttpClient object, and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Create and start the tasks. As each task finishes, DisplayResults   
        ' displays its length.  
        Dim download1 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com", client)  
        Dim download2 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/hh156528(VS.110).aspx", client)  
        Dim download3 As Task(Of Integer) =  
            ProcessURLAsync("http://msdn.microsoft.com/library/67w7t67f.aspx", client)  
  
        ' Await each task.  
        Dim length1 As Integer = Await download1  
        Dim length2 As Integer = Await download2  
        Dim length3 As Integer = Await download3  
  
        Dim total As Integer = length1 + length2 + length3  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Async Function ProcessURLAsync(url As String, client As HttpClient) As Task(Of Integer)  
  
        Dim byteArray = Await client.GetByteArrayAsync(url)  
        DisplayResults(url, byteArray)  
        Return byteArray.Length  
    End Function  
  
    Private Sub DisplayResults(url As String, content As Byte())  
  
        ' Display the length of each website. The string format   
        ' is designed to be used with a monospaced font, such as  
        ' Lucida Console or Global Monospace.  
        Dim bytes = content.Length  
        ' Strip off the "http://".  
        Dim displayURL = url.Replace("http://", "")  
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)  
    End Sub  
End Class  
```  
  
## <a name="see-also"></a><span data-ttu-id="5c663-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c663-146">See Also</span></span>  
 <span data-ttu-id="5c663-147">[逐步解說︰ 存取 Web 使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span><span class="sxs-lookup"><span data-stu-id="5c663-147">[Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span></span>  
<span data-ttu-id="5c663-148"> [非同步程式設計使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="5c663-148"> [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="5c663-149"> [如何︰ 使用 Task.WhenAll (Visual Basic) 來擴充非同步逐步解說](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)</span><span class="sxs-lookup"><span data-stu-id="5c663-149"> [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)</span></span>

