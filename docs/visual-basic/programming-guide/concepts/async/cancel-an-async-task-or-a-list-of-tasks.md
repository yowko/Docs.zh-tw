---
title: "取消一項非同步工作或一份工作 (Visual Basic) |Microsoft 文件"
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
ms.assetid: a9ee1b71-5bec-4736-a1e9-448042dd7215
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fe2df73aaf49f1b61dafcad9a6c6e0f3d014f8ec
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="cancel-an-async-task-or-a-list-of-tasks-visual-basic"></a><span data-ttu-id="87a21-102">取消一項非同步工作或一份工作 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="87a21-102">Cancel an Async Task or a List of Tasks (Visual Basic)</span></span>
<span data-ttu-id="87a21-103">您可以設定按鈕可讓您取消非同步應用程式，如果您不想等候它完成。</span><span class="sxs-lookup"><span data-stu-id="87a21-103">You can set up a button that you can use to cancel an async application if you don't want to wait for it to finish.</span></span> <span data-ttu-id="87a21-104">依照本主題中的範例，您可以取消按鈕加入的應用程式，下載網站的內容或網站的清單。</span><span class="sxs-lookup"><span data-stu-id="87a21-104">By following the examples in this topic, you can add a cancellation button to an application that downloads the contents of one website or a list of websites.</span></span>  
  
 <span data-ttu-id="87a21-105">範例會使用 UI，[微調非同步應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)描述。</span><span class="sxs-lookup"><span data-stu-id="87a21-105">The examples use the UI that [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) describes.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="87a21-106">若要執行範例，您必須擁有 Visual Studio 2012 或較新和.NET Framework 4.5 或更新版本安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="87a21-106">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <span data-ttu-id="87a21-107"><a name="BKMK_CancelaTask"></a>取消工作</span><span class="sxs-lookup"><span data-stu-id="87a21-107"><a name="BKMK_CancelaTask"></a> Cancel a Task</span></span>  
 <span data-ttu-id="87a21-108">第一個範例將**取消**具有單一的下載工作的按鈕。</span><span class="sxs-lookup"><span data-stu-id="87a21-108">The first example associates the **Cancel** button with a single download task.</span></span> <span data-ttu-id="87a21-109">如果應用程式會下載內容時，您可以選擇該按鈕，則會取消下載。</span><span class="sxs-lookup"><span data-stu-id="87a21-109">If you choose the button while the application is downloading content, the download is canceled.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="87a21-110">下載範例</span><span class="sxs-lookup"><span data-stu-id="87a21-110">Downloading the Example</span></span>  
 <span data-ttu-id="87a21-111">您可以下載完整的 Windows Presentation Foundation (WPF) 專案，從[非同步範例︰ 順利微調您的應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)，然後依照下列步驟。</span><span class="sxs-lookup"><span data-stu-id="87a21-111">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="87a21-112">解壓縮您下載的檔案，然後啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="87a21-112">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="87a21-113">在功能表列上，依序選擇 [檔案] ****、[開啟舊檔] ****及 [專案/方案] ****。</span><span class="sxs-lookup"><span data-stu-id="87a21-113">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="87a21-114">在**開啟專案**對話方塊中，開啟保存在解壓縮時，範例程式碼的資料夾，並接著開啟 AsyncFineTuningVB 方案 (.sln) 檔案。</span><span class="sxs-lookup"><span data-stu-id="87a21-114">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="87a21-115">在**方案總管 中**，開啟捷徑功能表**CancelATask**專案，然後再選擇**設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="87a21-115">In **Solution Explorer**, open the shortcut menu for the **CancelATask** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="87a21-116">選擇 F5 鍵以執行專案。</span><span class="sxs-lookup"><span data-stu-id="87a21-116">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="87a21-117">選擇 Ctrl + F5 鍵以執行專案，但不偵錯它。</span><span class="sxs-lookup"><span data-stu-id="87a21-117">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="87a21-118">如果您不想要下載的專案，您可以檢閱本主題結尾處的 MainWindow.xaml.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="87a21-118">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="87a21-119">建置範例</span><span class="sxs-lookup"><span data-stu-id="87a21-119">Building the Example</span></span>  
 <span data-ttu-id="87a21-120">加入下列變更**取消** 按鈕，下載網站的應用程式。</span><span class="sxs-lookup"><span data-stu-id="87a21-120">The following changes add a **Cancel** button to an application that downloads a website.</span></span> <span data-ttu-id="87a21-121">如果您不想要下載或建置範例，您可以檢閱本主題結尾處的 「 完整的範例 」 一節中最終產品。</span><span class="sxs-lookup"><span data-stu-id="87a21-121">If you don't want to download or build the example, you can review the final product in the "Complete Examples" section at the end of this topic.</span></span> <span data-ttu-id="87a21-122">星號標示的程式碼變更。</span><span class="sxs-lookup"><span data-stu-id="87a21-122">Asterisks mark the changes in the code.</span></span>  
  
 <span data-ttu-id="87a21-123">若要建置範例自行逐步解說，依照指示下載 「 範例 」 一節中的，但是選擇**StarterCode**為**啟始專案**而不是**CancelATask**。</span><span class="sxs-lookup"><span data-stu-id="87a21-123">To build the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **StarterCode** as the **StartUp Project** instead of **CancelATask**.</span></span>  
  
 <span data-ttu-id="87a21-124">該專案的 MainWindow.xaml.vb 檔案，然後加入下列變更。</span><span class="sxs-lookup"><span data-stu-id="87a21-124">Then add the following changes to the MainWindow.xaml.vb file of that project.</span></span>  
  
1.  <span data-ttu-id="87a21-125">宣告`CancellationTokenSource`變數`cts`，這是所有的方法來存取該範圍內。</span><span class="sxs-lookup"><span data-stu-id="87a21-125">Declare a `CancellationTokenSource` variable, `cts`, that’s in scope for all methods that access it.</span></span>  
  
    ```vb  
    Class MainWindow  
  
        ' ***Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  <span data-ttu-id="87a21-126">新增下列事件處理常式**取消** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="87a21-126">Add the following event handler for the **Cancel** button.</span></span> <span data-ttu-id="87a21-127">事件處理常式會使用<xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName>方法來通知`cts`當使用者要求取消。</xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="87a21-127">The event handler uses the <xref:System.Threading.CancellationTokenSource.Cancel%2A?displayProperty=fullName> method to notify `cts` when the user requests cancellation.</span></span>  
  
    ```vb  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
    ```  
  
3.  <span data-ttu-id="87a21-128">進行下列變更在事件處理常式**啟動** 按鈕， `startButton_Click`。</span><span class="sxs-lookup"><span data-stu-id="87a21-128">Make the following changes in the event handler for the **Start** button, `startButton_Click`.</span></span>  
  
    -   <span data-ttu-id="87a21-129">具現化`CancellationTokenSource`， `cts`。</span><span class="sxs-lookup"><span data-stu-id="87a21-129">Instantiate the `CancellationTokenSource`, `cts`.</span></span>  
  
        ```vb  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
        ```  
  
    -   <span data-ttu-id="87a21-130">在呼叫`AccessTheWebAsync`、 下載指定的網站內容、 傳送<xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=fullName>屬性`cts`做為引數。</xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="87a21-130">In the call to `AccessTheWebAsync`, which downloads the contents of a specified website, send the <xref:System.Threading.CancellationTokenSource.Token%2A?displayProperty=fullName> property of `cts` as an argument.</span></span> <span data-ttu-id="87a21-131">`Token`屬性會傳播訊息，如果已要求取消。</span><span class="sxs-lookup"><span data-stu-id="87a21-131">The `Token` property propagates the message if cancellation is requested.</span></span> <span data-ttu-id="87a21-132">新增會顯示訊息，如果使用者選擇取消下載作業的 catch 區塊。</span><span class="sxs-lookup"><span data-stu-id="87a21-132">Add a catch block that displays a message if the user chooses to cancel the download operation.</span></span> <span data-ttu-id="87a21-133">下列程式碼顯示的變更。</span><span class="sxs-lookup"><span data-stu-id="87a21-133">The following code shows the changes.</span></span>  
  
        ```vb  
        Try  
            ' ***Send a token to carry the message if cancellation is requested.  
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
            ' *** If cancellation is requested, an OperationCanceledException results.  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
        ```  
  
4.  <span data-ttu-id="87a21-134">在`AccessTheWebAsync`，使用<xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=fullName>多載`GetAsync`方法中的<xref:System.Net.Http.HttpClient>下載網站的內容類型。</xref:System.Net.Http.HttpClient> </xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="87a21-134">In `AccessTheWebAsync`, use the  <xref:System.Net.Http.HttpClient.GetAsync%28System.String%2CSystem.Threading.CancellationToken%29?displayProperty=fullName> overload of the `GetAsync` method in the <xref:System.Net.Http.HttpClient> type to download the contents of a website.</span></span> <span data-ttu-id="87a21-135">傳遞`ct`、<xref:System.Threading.CancellationToken>參數`AccessTheWebAsync`，做為第二個引數。</xref:System.Threading.CancellationToken></span><span class="sxs-lookup"><span data-stu-id="87a21-135">Pass `ct`, the <xref:System.Threading.CancellationToken> parameter of `AccessTheWebAsync`, as the second argument.</span></span> <span data-ttu-id="87a21-136">如果使用者選擇權杖夾帶了訊息**取消** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="87a21-136">The token carries the message if the user chooses the **Cancel** button.</span></span>  
  
     <span data-ttu-id="87a21-137">下列程式碼將示範在變更`AccessTheWebAsync`。</span><span class="sxs-lookup"><span data-stu-id="87a21-137">The following code shows the changes in `AccessTheWebAsync`.</span></span>  
  
    ```vb  
    ' ***Provide a parameter for the CancellationToken.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)  
  
        Dim client As HttpClient = New HttpClient()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Ready to download." & vbCrLf)  
  
        ' You might need to slow things down to have a chance to cancel.  
        Await Task.Delay(250)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' ***The ct argument carries the message if the Cancel button is chosen.  
        Dim response As HttpResponseMessage = Await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' The result of the method is the length of the downloaded website.  
        Return urlContents.Length  
    End Function  
    ```  
  
5.  <span data-ttu-id="87a21-138">如果您沒有取消程式，便會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="87a21-138">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Length of the downloaded string: 158125.  
    ```  
  
     <span data-ttu-id="87a21-139">如果您選擇**取消**按鈕，然後再程式完成之後下載內容，此程式會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="87a21-139">If you choose the **Cancel** button before the program finishes downloading the content, the program produces the following output.</span></span>  
  
    ```  
    Ready to download.  
    Download canceled.  
    ```  
  
##  <span data-ttu-id="87a21-140"><a name="BKMK_CancelaListofTasks"></a>取消工作的清單</span><span class="sxs-lookup"><span data-stu-id="87a21-140"><a name="BKMK_CancelaListofTasks"></a> Cancel a List of Tasks</span></span>  
 <span data-ttu-id="87a21-141">您可以擴充先前的範例，若要取消產生關聯，以相同的許多工作`CancellationTokenSource`與每個工作的執行個體。</span><span class="sxs-lookup"><span data-stu-id="87a21-141">You can extend the previous example to cancel many tasks by associating the same `CancellationTokenSource` instance with each task.</span></span> <span data-ttu-id="87a21-142">如果您選擇**取消** 按鈕，取消尚無完整的所有工作。</span><span class="sxs-lookup"><span data-stu-id="87a21-142">If you choose the **Cancel** button, you cancel all tasks that aren’t yet complete.</span></span>  
  
### <a name="downloading-the-example"></a><span data-ttu-id="87a21-143">下載範例</span><span class="sxs-lookup"><span data-stu-id="87a21-143">Downloading the Example</span></span>  
 <span data-ttu-id="87a21-144">您可以下載完整的 Windows Presentation Foundation (WPF) 專案，從[非同步範例︰ 順利微調您的應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)，然後依照下列步驟。</span><span class="sxs-lookup"><span data-stu-id="87a21-144">You can download the complete Windows Presentation Foundation (WPF) project from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046) and then follow these steps.</span></span>  
  
1.  <span data-ttu-id="87a21-145">解壓縮您下載的檔案，然後啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="87a21-145">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="87a21-146">在功能表列上，依序選擇 [檔案] ****、[開啟舊檔] ****及 [專案/方案] ****。</span><span class="sxs-lookup"><span data-stu-id="87a21-146">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="87a21-147">在**開啟專案**對話方塊中，開啟保存在解壓縮時，範例程式碼的資料夾，並接著開啟 AsyncFineTuningVB 方案 (.sln) 檔案。</span><span class="sxs-lookup"><span data-stu-id="87a21-147">In the **Open Project** dialog box, open the folder that holds the sample code that you decompressed, and then open the solution (.sln) file for AsyncFineTuningVB.</span></span>  
  
4.  <span data-ttu-id="87a21-148">在**方案總管 中**，開啟捷徑功能表**CancelAListOfTasks**專案，然後再選擇**設定為啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="87a21-148">In **Solution Explorer**, open the shortcut menu for the **CancelAListOfTasks** project, and then choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="87a21-149">選擇 F5 鍵以執行專案。</span><span class="sxs-lookup"><span data-stu-id="87a21-149">Choose the F5 key to run the project.</span></span>  
  
     <span data-ttu-id="87a21-150">選擇 Ctrl + F5 鍵以執行專案，但不偵錯它。</span><span class="sxs-lookup"><span data-stu-id="87a21-150">Choose the Ctrl+F5 keys to run the project without debugging it.</span></span>  
  
 <span data-ttu-id="87a21-151">如果您不想要下載的專案，您可以檢閱本主題結尾處的 MainWindow.xaml.vb 檔案。</span><span class="sxs-lookup"><span data-stu-id="87a21-151">If you don't want to download the project, you can review the MainWindow.xaml.vb files at the end of this topic.</span></span>  
  
### <a name="building-the-example"></a><span data-ttu-id="87a21-152">建置範例</span><span class="sxs-lookup"><span data-stu-id="87a21-152">Building the Example</span></span>  
 <span data-ttu-id="87a21-153">若要擴充範例自行逐步解說，依照指示下載 「 範例 」 一節中的，但是選擇**CancelATask**為**啟始專案**。</span><span class="sxs-lookup"><span data-stu-id="87a21-153">To extend the example yourself, step by step, follow the instructions in the "Downloading the Example" section, but choose **CancelATask** as the **StartUp Project**.</span></span> <span data-ttu-id="87a21-154">專案中加入下列變更。</span><span class="sxs-lookup"><span data-stu-id="87a21-154">Add the following changes to that project.</span></span> <span data-ttu-id="87a21-155">星號標示的程式中的變更。</span><span class="sxs-lookup"><span data-stu-id="87a21-155">Asterisks mark the changes in the program.</span></span>  
  
1.  <span data-ttu-id="87a21-156">加入方法以建立一份 web 位址。</span><span class="sxs-lookup"><span data-stu-id="87a21-156">Add a method to create a list of web addresses.</span></span>  
  
    ```vb  
    ' ***Add a method that creates a list of web addresses.  
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
    ```  
  
2.  <span data-ttu-id="87a21-157">在呼叫方法`AccessTheWebAsync`。</span><span class="sxs-lookup"><span data-stu-id="87a21-157">Call the method in `AccessTheWebAsync`.</span></span>  
  
    ```vb  
    ' ***Call SetUpURLList to make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
    ```  
  
3.  <span data-ttu-id="87a21-158">將下列的迴圈中加入`AccessTheWebAsync`處理每個清單中的網址。</span><span class="sxs-lookup"><span data-stu-id="87a21-158">Add the following loop in `AccessTheWebAsync` to process each web address in the list.</span></span>  
  
    ```vb  
    ' ***Add a loop to process the list of web addresses.  
    For Each url In urlList  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' Argument ct carries the message if the Cancel button is chosen.   
        ' ***Note that the Cancel button can cancel all remaining downloads.  
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
    Next  
    ```  
  
4.  <span data-ttu-id="87a21-159">因為`AccessTheWebAsync`顯示長度，此方法不需傳回任何項目。</span><span class="sxs-lookup"><span data-stu-id="87a21-159">Because `AccessTheWebAsync` displays the lengths, the method doesn't need to return anything.</span></span> <span data-ttu-id="87a21-160">移除 return 陳述式，並將方法的傳回型別變更為 <xref:System.Threading.Tasks.Task>而不是<xref:System.Threading.Tasks.Task%601>。</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="87a21-160">Remove the return statement, and change the return type of the method to <xref:System.Threading.Tasks.Task> instead of <xref:System.Threading.Tasks.Task%601>.</span></span>  
  
<span data-ttu-id="87a21-161"><CodeContentPlaceHolder>10</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="87a21-161"><CodeContentPlaceHolder>10</CodeContentPlaceHolder></span></span>  
     <span data-ttu-id="87a21-162">呼叫這個方法從`startButton_Click`使用陳述式，而不是運算式。</span><span class="sxs-lookup"><span data-stu-id="87a21-162">Call the method from `startButton_Click` by using a statement instead of an expression.</span></span>  
  
    ```vb  
    Await AccessTheWebAsync(cts.Token)  
    ```  
  
5.  <span data-ttu-id="87a21-163">如果您沒有取消程式，便會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="87a21-163">If you don’t cancel the program, it produces the following output.</span></span>  
  
    ```  
  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Length of the downloaded string: 158124.  
  
    Length of the downloaded string: 204890.  
  
    Length of the downloaded string: 175488.  
  
    Length of the downloaded string: 145790.  
  
    Downloads complete.  
  
    ```  
  
     <span data-ttu-id="87a21-164">如果您選擇**取消**之前會完整下載 按鈕，輸出會包含完成之前取消下載的長度。</span><span class="sxs-lookup"><span data-stu-id="87a21-164">If you choose the **Cancel** button before the downloads are complete, the output contains the lengths of the downloads that completed before the cancellation.</span></span>  
  
    ```  
    Length of the downloaded string: 35939.  
  
    Length of the downloaded string: 237682.  
  
    Length of the downloaded string: 128607.  
  
    Downloads canceled.  
  
    ```  
  
##  <span data-ttu-id="87a21-165"><a name="BKMK_CompleteExamples"></a>完整範例</span><span class="sxs-lookup"><span data-stu-id="87a21-165"><a name="BKMK_CompleteExamples"></a> Complete Examples</span></span>  
 <span data-ttu-id="87a21-166">下列各節包含的程式碼，為每個先前的範例。</span><span class="sxs-lookup"><span data-stu-id="87a21-166">The following sections contain the code for each of the previous examples.</span></span> <span data-ttu-id="87a21-167">請注意，您必須加入<xref:System.Net.Http>.</xref:System.Net.Http>的參考</span><span class="sxs-lookup"><span data-stu-id="87a21-167">Notice that you must add a reference for <xref:System.Net.Http>.</span></span>  
  
 <span data-ttu-id="87a21-168">您可以下載的專案[非同步範例︰ 順利微調您的應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)。</span><span class="sxs-lookup"><span data-stu-id="87a21-168">You can download the projects from [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046).</span></span>  
  
### <a name="cancel-a-task-example"></a><span data-ttu-id="87a21-169">取消工作範例</span><span class="sxs-lookup"><span data-stu-id="87a21-169">Cancel a Task Example</span></span>  
 <span data-ttu-id="87a21-170">下列程式碼是完整的 MainWindow.xaml.vb 檔案，例如取消單一工作。</span><span class="sxs-lookup"><span data-stu-id="87a21-170">The following code is the complete MainWindow.xaml.vb file for the example that cancels a single task.</span></span>  
  
```vb  
' Add an Imports directive and a reference for System.Net.Http.  
Imports System.Net.Http  
  
' Add the following Imports directive for System.Threading.  
Imports System.Threading  
  
Class MainWindow  
  
    ' ***Declare a System.Threading.CancellationTokenSource.  
    Dim cts As CancellationTokenSource  
  
    Private Async Sub startButton_Click(sender As Object, e As RoutedEventArgs)  
        ' ***Instantiate the CancellationTokenSource.  
        cts = New CancellationTokenSource()  
  
        resultsTextBox.Clear()  
  
        Try  
            ' ***Send a token to carry the message if cancellation is requested.  
            Dim contentLength As Integer = Await AccessTheWebAsync(cts.Token)  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
            ' *** If cancellation is requested, an OperationCanceledException results.  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Download failed." & vbCrLf  
        End Try  
  
        ' ***Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' ***Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' ***Provide a parameter for the CancellationToken.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task(Of Integer)  
  
        Dim client As HttpClient = New HttpClient()  
  
        resultsTextBox.Text &=  
            String.Format(vbCrLf & "Ready to download." & vbCrLf)  
  
        ' You might need to slow things down to have a chance to cancel.  
        Await Task.Delay(250)  
  
        ' GetAsync returns a Task(Of HttpResponseMessage).   
        ' ***The ct argument carries the message if the Cancel button is chosen.  
        Dim response As HttpResponseMessage = Await client.GetAsync("http://msdn.microsoft.com/library/dd470362.aspx", ct)  
  
        ' Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' The result of the method is the length of the downloaded website.  
        Return urlContents.Length  
    End Function  
End Class  
  
' Output for a successful download:  
  
' Ready to download.  
  
' Length of the downloaded string: 158125.  
  
' Or, if you cancel:  
  
' Ready to download.  
  
' Download canceled.  
```  
  
### <a name="cancel-a-list-of-tasks-example"></a><span data-ttu-id="87a21-171">取消工作範例的清單</span><span class="sxs-lookup"><span data-stu-id="87a21-171">Cancel a List of Tasks Example</span></span>  
 <span data-ttu-id="87a21-172">下列程式碼是完整的 MainWindow.xaml.vb 檔案，例如取消的工作清單。</span><span class="sxs-lookup"><span data-stu-id="87a21-172">The following code is the complete MainWindow.xaml.vb file for the example that cancels a list of tasks.</span></span>  
  
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
            ' ***AccessTheWebAsync returns a Task, not a Task(Of Integer).  
            Await AccessTheWebAsync(cts.Token)  
            '  ***Small change in the display lines.  
            resultsTextBox.Text &= vbCrLf & "Downloads complete."  
  
        Catch ex As OperationCanceledException  
            resultsTextBox.Text &= vbCrLf & "Downloads canceled." & vbCrLf  
  
        Catch ex As Exception  
            resultsTextBox.Text &= vbCrLf & "Downloads failed." & vbCrLf  
        End Try  
  
        ' Set the CancellationTokenSource to Nothing when the download is complete.  
        cts = Nothing  
    End Sub  
  
    ' Add an event handler for the Cancel button.  
    Private Sub cancelButton_Click(sender As Object, e As RoutedEventArgs)  
  
        If cts IsNot Nothing Then  
            cts.Cancel()  
        End If  
    End Sub  
  
    ' Provide a parameter for the CancellationToken.  
    ' ***Change the return type to Task because the method has no return statement.  
    Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
        Dim client As HttpClient = New HttpClient()  
  
        ' ***Call SetUpURLList to make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        ' ***Add a loop to process the list of web addresses.  
        For Each url In urlList  
            ' GetAsync returns a Task(Of HttpResponseMessage).   
            ' Argument ct carries the message if the Cancel button is chosen.   
            ' ***Note that the Cancel button can cancel all remaining downloads.  
            Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
            ' Retrieve the website contents from the HttpResponseMessage.  
            Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
            resultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, urlContents.Length)  
        Next  
    End Function  
  
    ' ***Add a method that creates a list of web addresses.  
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
  
' Output if you do not choose to cancel:  
  
' Length of the downloaded string: 35939.  
  
' Length of the downloaded string: 237682.  
  
' Length of the downloaded string: 128607.  
  
' Length of the downloaded string: 158124.  
  
' Length of the downloaded string: 204890.  
  
' Length of the downloaded string: 175488.  
  
' Length of the downloaded string: 145790.  
  
' Downloads complete.  
  
'  Sample output if you choose to cancel:  
  
' Length of the downloaded string: 35939.  
  
' Length of the downloaded string: 237682.  
  
' Length of the downloaded string: 128607.  
  
' Downloads canceled.  
```  
  
## <a name="see-also"></a><span data-ttu-id="87a21-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87a21-173">See Also</span></span>  
 <span data-ttu-id="87a21-174"><xref:System.Threading.CancellationTokenSource></xref:System.Threading.CancellationTokenSource></span><span class="sxs-lookup"><span data-stu-id="87a21-174"><xref:System.Threading.CancellationTokenSource></span></span>   
 <span data-ttu-id="87a21-175"><xref:System.Threading.CancellationToken></xref:System.Threading.CancellationToken></span><span class="sxs-lookup"><span data-stu-id="87a21-175"><xref:System.Threading.CancellationToken></span></span>   
<span data-ttu-id="87a21-176"> [非同步程式設計使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="87a21-176"> [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="87a21-177"> [微調非同步應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span><span class="sxs-lookup"><span data-stu-id="87a21-177"> [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md) </span></span>  
<span data-ttu-id="87a21-178"> [非同步範例︰ 微調應用程式](http://go.microsoft.com/fwlink/?LinkId=255046)</span><span class="sxs-lookup"><span data-stu-id="87a21-178"> [Async Sample: Fine Tuning Your Application](http://go.microsoft.com/fwlink/?LinkId=255046)</span></span>
