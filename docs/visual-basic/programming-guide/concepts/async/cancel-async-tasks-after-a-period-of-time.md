---
title: "一段時間 (Visual Basic) 後取消非同步工作 |Microsoft 文件"
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
ms.assetid: a48045a3-6a99-42af-b824-af340f0b9a5d
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 9c2c7c09f9af7c9b7bdcb6411b6db6e2ca4984cb
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="cancel-async-tasks-after-a-period-of-time-visual-basic"></a><span data-ttu-id="a1941-102">取消非同步工作一段時間 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a1941-102">Cancel Async Tasks after a Period of Time (Visual Basic)</span></span>
<span data-ttu-id="a1941-103">您可以取消非同步作業，在一段時間之後，使用<xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=fullName>方法，如果您不想等待作業完成。</xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="a1941-103">You can cancel an asynchronous operation after a period of time by using the  <xref:System.Threading.CancellationTokenSource.CancelAfter%2A?displayProperty=fullName> method if you don't want to wait for the operation to finish.</span></span> <span data-ttu-id="a1941-104">這個方法會排程所指定的期間內未完成的任何相關工作的取消`CancelAfter`運算式。</span><span class="sxs-lookup"><span data-stu-id="a1941-104">This method schedules the cancellation of any associated tasks that aren’t complete within the period of time that’s designated by the `CancelAfter` expression.</span></span>  
  
 <span data-ttu-id="a1941-105">這個範例會將開發中的程式碼加入[取消一項非同步工作或清單的工作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)下載的網站清單，並顯示每個內容的長度。</span><span class="sxs-lookup"><span data-stu-id="a1941-105">This example adds to the code that’s developed in [Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to download a list of websites and to display the length of the contents of each one.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a1941-106">若要執行範例，您必須 2012年或更新版本的 Visual Studio 和.NET Framework 4.5 或更新版本安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="a1941-106">To run the examples, you must have Visual Studio 2012 or later and the .NET Framework 4.5 or later installed on your computer.</span></span>  
  
## <a name="downloading-the-example"></a><span data-ttu-id="a1941-107">下載範例</span><span class="sxs-lookup"><span data-stu-id="a1941-107">Downloading the Example</span></span>  
 <span data-ttu-id="a1941-108">您可以下載完整的 Windows Presentation Foundation (WPF) 專案，從[非同步範例︰ 順利微調您的應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)，然後依照下列步驟。</span><span class="sxs-lookup"><span data-stu-id="a1941-108">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="a1941-109">解壓縮您下載的檔案，然後啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="a1941-109">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="a1941-110">在功能表列上，依序選擇 [檔案] ****、[開啟舊檔] ****及 [專案/方案] ****。</span><span class="sxs-lookup"><span data-stu-id="a1941-110">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="a1941-111">在**開啟專案**對話方塊中，開啟保存在解壓縮時，範例程式碼的資料夾，並接著開啟 AsyncFineTuningVB 方案 (.sln) 檔案。</span><span class="sxs-lookup"><span data-stu-id="a1941-111">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="a1941-112">在**方案總管 中**，開啟捷徑功能表**CancelAfterTime**專案，然後再選擇**設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="a1941-112">In **Solution Explorer**, open the shortcut menu for the **CancelAfterTime** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="a1941-113">選擇 F5 鍵以執行專案。</span><span class="sxs-lookup"><span data-stu-id="a1941-113">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="a1941-114">選擇 Ctrl + F5 鍵以執行專案，但不偵錯它。</span><span class="sxs-lookup"><span data-stu-id="a1941-114">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
6.  <span data-ttu-id="a1941-115">若要確認輸出可能會顯示輸出的所有網站、 任何網站，或某些網站執行程式數次。</span><span class="sxs-lookup"><span data-stu-id="a1941-115">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span>  
  
 <span data-ttu-id="a1941-116">如果您不想要下載的專案，您可以檢閱本主題結尾處的 MainWindow.xaml.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="a1941-116">If you don't want to download the project, you can review the MainWindow.xaml.vb file at the end of this topic.</span></span>  
  
## <a name="building-the-example"></a><span data-ttu-id="a1941-117">建置範例</span><span class="sxs-lookup"><span data-stu-id="a1941-117">Building the Example</span></span>  
 <span data-ttu-id="a1941-118">本主題中的範例將加入專案中開發[取消一項非同步工作或清單的工作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)取消的工作清單。</span><span class="sxs-lookup"><span data-stu-id="a1941-118">The example in this topic adds to the project that's developed in [Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) to cancel a list of tasks.</span></span> <span data-ttu-id="a1941-119">雖然此範例會使用相同的 UI，**取消**按鈕不會明確地使用。</span><span class="sxs-lookup"><span data-stu-id="a1941-119">The example uses the same UI, although the **Cancel** button isn’t used explicitly.</span></span>  
  
 <span data-ttu-id="a1941-120">若要建置範例自行逐步解說，依照指示下載 「 範例 」 一節中的，但是選擇**CancelAListOfTasks**為**啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="a1941-120">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelAListOfTasks** as the **StartUp Project**.</span></span> <span data-ttu-id="a1941-121">本主題中加入該專案所做的變更。</span><span class="sxs-lookup"><span data-stu-id="a1941-121">Add the changes in this topic to that project.</span></span>  
  
 <span data-ttu-id="a1941-122">若要指定最長時間的工作會標示為取消之前，新增呼叫至`CancelAfter`至`startButton_Click`，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a1941-122">To specify a maximum time before the tasks are marked as canceled, add a call to `CancelAfter` to `startButton_Click`, as the following example shows.</span></span> <span data-ttu-id="a1941-123">加入以星號標示。</span><span class="sxs-lookup"><span data-stu-id="a1941-123">The addition is marked with asterisks.</span></span>  
  
```vb  
Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
  
    ' Instantiate the CancellationTokenSource.  
    cts = New CancellationTokenSource()  
  
    resultsTextBox.Clear()  
  
    Try  
        ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You   
        ' can adjust the time.)  
        cts.CancelAfter(2500)  
  
        Await AccessTheWebAsync(cts.Token)  
        resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
    Catch ex As OperationCanceledException  
        resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
    Catch ex As Exception  
        resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
    End Try  
  
    ' Set the CancellationTokenSource to Nothing when the download is complete.  
    cts = Nothing  
End Sub  
```  
  
 <span data-ttu-id="a1941-124">若要確認輸出可能會顯示輸出的所有網站、 任何網站，或某些網站執行程式數次。</span><span class="sxs-lookup"><span data-stu-id="a1941-124">Run the program several times to verify that the output might show output for all websites, no websites, or some web sites.</span></span> <span data-ttu-id="a1941-125">下列的輸出是範例。</span><span class="sxs-lookup"><span data-stu-id="a1941-125">The following output is a sample.</span></span>  
  
```  
Length of the downloaded string: 35990.  
  
Length of the downloaded string: 407399.  
  
Length of the downloaded string: 226091.  
  
Downloads canceled.  
```  
  
## <a name="complete-example"></a><span data-ttu-id="a1941-126">完整範例</span><span class="sxs-lookup"><span data-stu-id="a1941-126">Complete Example</span></span>  
 <span data-ttu-id="a1941-127">下列程式碼是範例的 MainWindow.xaml.vb 檔案的完整文字。</span><span class="sxs-lookup"><span data-stu-id="a1941-127">The following code is the complete text of the MainWindow.xaml.vb file for the example.</span></span> <span data-ttu-id="a1941-128">星號標示此範例中所新增的項目。</span><span class="sxs-lookup"><span data-stu-id="a1941-128">Asterisks mark the elements that were added for this example.</span></span>  
  
 <span data-ttu-id="a1941-129">請注意，您必須加入<xref:System.Net.Http>.</xref:System.Net.Http>的參考</span><span class="sxs-lookup"><span data-stu-id="a1941-129">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="a1941-130">您可以下載的專案[非同步範例︰ 順利微調您的應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)。</span><span class="sxs-lookup"><span data-stu-id="a1941-130">You can download the project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
```vb  
' Add an Imports directive and a reference for System.Net.Http.  
Imports System.Net.Http  
  
' Add the following Imports directive for System.Threading.  
Imports System.Threading  
  
Class MainWindow  
  
    ' Declare a System.Threading.CancellationTokenSource.  
    Dim cts As CancellationTokenSource  
  
    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
  
        ' Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
  
        resultsTextBox.Clear()  
  
        Try  
            ' ***Set up the CancellationTokenSource to cancel after 2.5 seconds. (You   
            ' can adjust the time.)  
            cts.CancelAfter(2500)  
  
            Await AccessTheWebAsync(cts.Token)  
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
        End Try  
  
        ' Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' You can still include a Cancel button if you want to.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' Provide a parameter for the CancellationToken.  
    ' Change the return type to Task because the method has no return statement.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
        Dim client As HttpClient = New HttpClient()  
  
        ' Call SetUpURLList to make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' Process each element in the list of web addresses.  
        For Each url In urlList  
            ' GetAsync returns a Task(Of HttpResponseMessage).   
            ' Argument ct carries the message if the Cancel button is chosen.   
            ' Note that the Cancel button can cancel all remaining downloads.  
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
            ' Retrieve the website contents from the HttpResponseMessage.  
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        Next  
    End Function  
  
    ' Add a method that creates a list of web addresses.  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
End Class  
  
' Sample output:  
  
' Length of the downloaded string: 35990.  
  
' Length of the downloaded string: 407399.  
  
' Length of the downloaded string: 226091.  
  
' Downloads canceled.  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1941-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a1941-131">See Also</span></span>  
 <span data-ttu-id="a1941-132">[非同步程式設計使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="a1941-132">[Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="a1941-133"> [逐步解說︰ 存取 Web 使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span><span class="sxs-lookup"><span data-stu-id="a1941-133"> [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span></span>  
<span data-ttu-id="a1941-134"> [取消一項非同步工作或一份工作 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="a1941-134"> [Cancel an Async Task or a List of Tasks (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md) </span></span>  
<span data-ttu-id="a1941-135"> [微調非同步應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span><span class="sxs-lookup"><span data-stu-id="a1941-135"> [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span></span>  
<span data-ttu-id="a1941-136"> [非同步範例︰ 微調應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)</span><span class="sxs-lookup"><span data-stu-id="a1941-136"> [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046)</span></span>
