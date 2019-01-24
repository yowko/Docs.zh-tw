---
title: 處理非同步應用程式 (Visual Basic) 中的重新進入
ms.date: 07/20/2015
ms.assetid: ef3dc73d-13fb-4c5f-a686-6b84148bbffe
ms.openlocfilehash: 6187b3a519da2930136aab8df9451f757079c2a5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535615"
---
# <a name="handling-reentrancy-in-async-apps-visual-basic"></a><span data-ttu-id="0e407-102">處理非同步應用程式 (Visual Basic) 中的重新進入</span><span class="sxs-lookup"><span data-stu-id="0e407-102">Handling Reentrancy in Async Apps (Visual Basic)</span></span>
<span data-ttu-id="0e407-103">當您將非同步程式碼納入您的應用程式時，應該考慮並防止可能發生的重新進入，也就是在完成前重新進入的非同步作業。</span><span class="sxs-lookup"><span data-stu-id="0e407-103">When you include asynchronous code in your app, you should consider and possibly prevent reentrancy, which refers to reentering an asynchronous operation before it has completed.</span></span> <span data-ttu-id="0e407-104">如果您不找出並處理重新進入的可能性，它可能會導致非預期的結果。</span><span class="sxs-lookup"><span data-stu-id="0e407-104">If you don't identify and handle possibilities for reentrancy, it can cause unexpected results.</span></span>  
  
 <span data-ttu-id="0e407-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="0e407-105">**In this topic**</span></span>  
  
-   [<span data-ttu-id="0e407-106">辨識重新進入</span><span class="sxs-lookup"><span data-stu-id="0e407-106">Recognizing Reentrancy</span></span>](#BKMK_RecognizingReentrancy)  
  
-   [<span data-ttu-id="0e407-107">處理重新進入</span><span class="sxs-lookup"><span data-stu-id="0e407-107">Handling Reentrancy</span></span>](#BKMK_HandlingReentrancy)  
  
    -   [<span data-ttu-id="0e407-108">停用開始按鈕</span><span class="sxs-lookup"><span data-stu-id="0e407-108">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)  
  
    -   [<span data-ttu-id="0e407-109">取消後再重新啟動作業</span><span class="sxs-lookup"><span data-stu-id="0e407-109">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)  
  
    -   [<span data-ttu-id="0e407-110">執行多個作業並將輸出加入佇列</span><span class="sxs-lookup"><span data-stu-id="0e407-110">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)  
  
-   [<span data-ttu-id="0e407-111">檢閱及執行範例應用程式</span><span class="sxs-lookup"><span data-stu-id="0e407-111">Reviewing and Running the Example App</span></span>](#BKMD_SettingUpTheExample)  
  
> [!NOTE]
>  <span data-ttu-id="0e407-112">若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="0e407-112">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
##  <a name="BKMK_RecognizingReentrancy"></a> <span data-ttu-id="0e407-113">辨識重新進入</span><span class="sxs-lookup"><span data-stu-id="0e407-113">Recognizing Reentrancy</span></span>  
 <span data-ttu-id="0e407-114">在本主題的範例中，使用者選擇 [開始] 按鈕來起始非同步應用程式，該應用程式會下載一系列網站，並計算下載的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="0e407-114">In the example in this topic, users choose a **Start** button to initiate an asynchronous app that downloads a series of websites and calculates the total number of bytes that are downloaded.</span></span> <span data-ttu-id="0e407-115">此範例的同步版本會回應相同的方式，不論使用者選擇按鈕的次數為何，因為在第一次之後，UI 執行緒會忽略這些事件，直到應用程式完成執行為止。</span><span class="sxs-lookup"><span data-stu-id="0e407-115">A synchronous version of the example would respond the same way regardless of how many times a user chooses the button because, after the first time, the UI thread ignores those events until the app finishes running.</span></span> <span data-ttu-id="0e407-116">但在非同步應用程式中，UI 執行緒會繼續回應，而且您可能在它完成之前重新進入非同步作業。</span><span class="sxs-lookup"><span data-stu-id="0e407-116">In an asynchronous app, however, the UI thread continues to respond, and you might reenter the asynchronous operation before it has completed.</span></span>  
  
 <span data-ttu-id="0e407-117">如果使用者只選擇一次 [開始] 按鈕，則下列範例會顯示預期的輸出。</span><span class="sxs-lookup"><span data-stu-id="0e407-117">The following example shows the expected output if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="0e407-118">下載的網站清單會顯示每個網站的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="0e407-118">A list of the downloaded websites appears with the size, in bytes, of each site.</span></span> <span data-ttu-id="0e407-119">結尾會出現位元組總數。</span><span class="sxs-lookup"><span data-stu-id="0e407-119">The total number of bytes appears at the end.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="0e407-120">不過，如果使用者選擇按鈕多次，則會重複叫用事件處理常式，且每次都會重新進入下載程序。</span><span class="sxs-lookup"><span data-stu-id="0e407-120">However, if the user chooses the button more than once, the event handler is invoked repeatedly, and the download process is reentered each time.</span></span> <span data-ttu-id="0e407-121">如此一來，同時會執行數個非同步作業，輸出會與結果交錯，且導出令人困惑的位元組總數。</span><span class="sxs-lookup"><span data-stu-id="0e407-121">As a result, several asynchronous operations are running at the same time, the output interleaves the results, and the total number of bytes is confusing.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
7. msdn.microsoft.com                                            42972  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
7. msdn.microsoft.com                                            42972  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="0e407-122">您可以捲動到本主題的結尾來檢閱產生此輸出的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0e407-122">You can review the code that produces this output by scrolling to the end of this topic.</span></span> <span data-ttu-id="0e407-123">您可以將方案下載到本機電腦，然後執行 WebsiteDownload 專案；或使用本主題結尾的程式碼來建立您自己的專案，以實驗程式碼。如需詳細資訊和指示，請參閱[檢閱及執行範例應用程式](#BKMD_SettingUpTheExample)。</span><span class="sxs-lookup"><span data-stu-id="0e407-123">You can experiment with the code by downloading the solution to your local computer and then running the WebsiteDownload project or by using the code at the end of this topic to create your own project For more information and instructions, see [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span>  
  
##  <a name="BKMK_HandlingReentrancy"></a><span data-ttu-id="0e407-124">處理重新進入</span><span class="sxs-lookup"><span data-stu-id="0e407-124">Handling Reentrancy</span></span>  
 <span data-ttu-id="0e407-125">您可以各種不同的方式重新進入，視您要應用程式執行的工作而定。</span><span class="sxs-lookup"><span data-stu-id="0e407-125">You can handle reentrancy in a variety of ways, depending on what you want your app to do.</span></span> <span data-ttu-id="0e407-126">本主題提供下列範例：</span><span class="sxs-lookup"><span data-stu-id="0e407-126">This topic presents the following examples:</span></span>  
  
-   [<span data-ttu-id="0e407-127">停用開始按鈕</span><span class="sxs-lookup"><span data-stu-id="0e407-127">Disable the Start Button</span></span>](#BKMK_DisableTheStartButton)  
  
     <span data-ttu-id="0e407-128">在執行作業時停用 [開始] 按鈕，讓使用者無法中斷它。</span><span class="sxs-lookup"><span data-stu-id="0e407-128">Disable the **Start** button while the operation is running so that the user can't interrupt it.</span></span>  
  
-   [<span data-ttu-id="0e407-129">取消後再重新啟動作業</span><span class="sxs-lookup"><span data-stu-id="0e407-129">Cancel and Restart the Operation</span></span>](#BKMK_CancelAndRestart)  
  
     <span data-ttu-id="0e407-130">當使用者再次選擇 [開始] 按鈕，然後讓最近要求的作業繼續進行時，取消仍在執行的任何作業。</span><span class="sxs-lookup"><span data-stu-id="0e407-130">Cancel any operation that is still running when the user chooses the **Start** button again, and then let the most recently requested operation continue.</span></span>  
  
-   [<span data-ttu-id="0e407-131">執行多個作業並將輸出加入佇列</span><span class="sxs-lookup"><span data-stu-id="0e407-131">Run Multiple Operations and Queue the Output</span></span>](#BKMK_RunMultipleOperations)  
  
     <span data-ttu-id="0e407-132">允許所有要求的作業以非同步方式執行，但協調輸出的顯示，以一起並循序顯示每個作業的結果。</span><span class="sxs-lookup"><span data-stu-id="0e407-132">Allow all requested operations to run asynchronously, but coordinate the display of output so that the results from each operation appear together and in order.</span></span>  
  
###  <a name="BKMK_DisableTheStartButton"></a> <span data-ttu-id="0e407-133">停用 [開始] 按鈕</span><span class="sxs-lookup"><span data-stu-id="0e407-133">Disable the Start Button</span></span>  
 <span data-ttu-id="0e407-134">您可以停用 `StartButton_Click` 事件處理常式頂端的按鈕，以便在執行作業時封鎖 [開始] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0e407-134">You can block the **Start** button while an operation is running by disabling the button at the top of the `StartButton_Click` event handler.</span></span> <span data-ttu-id="0e407-135">作業完成時，您可以在 `Finally` 區塊中重新啟用按鈕，讓使用者可再次執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="0e407-135">You can then reenable the button from within a  `Finally` block when the operation finishes so that users can run the app again.</span></span>  
  
 <span data-ttu-id="0e407-136">下列程式碼會顯示這些變更 (以星號標記)。</span><span class="sxs-lookup"><span data-stu-id="0e407-136">The following code shows these changes, which are marked with asterisks.</span></span> <span data-ttu-id="0e407-137">您可以加入本主題結尾的程式碼所做的變更，或者您可以下載完成的應用程式，從[非同步範例：重新進入.NET 桌面應用程式](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)。</span><span class="sxs-lookup"><span data-stu-id="0e407-137">You can add the changes to the code at the end of this topic, or you can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="0e407-138">專案名稱是 DisableStartButton。</span><span class="sxs-lookup"><span data-stu-id="0e407-138">The project name is DisableStartButton.</span></span>  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
    ' This line is commented out to make the results clearer in the output.  
    'ResultsTextBox.Text = ""  
  
    ' ***Disable the Start button until the downloads are complete.   
    StartButton.IsEnabled = False  
  
    Try  
        Await AccessTheWebAsync()  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
    ' ***Enable the Start button in case you want to run the program again.   
    Finally  
        StartButton.IsEnabled = True  
  
    End Try  
End Sub  
```  
  
 <span data-ttu-id="0e407-139">因為變更，按鈕不會在 `AccessTheWebAsync` 正在下載網站時反應，因此程序將無法重新進入。</span><span class="sxs-lookup"><span data-stu-id="0e407-139">As a result of the changes, the button doesn't respond while `AccessTheWebAsync` is downloading the websites, so the process can’t be reentered.</span></span>  
  
###  <a name="BKMK_CancelAndRestart"></a> <span data-ttu-id="0e407-140">取消後再重新啟動作業</span><span class="sxs-lookup"><span data-stu-id="0e407-140">Cancel and Restart the Operation</span></span>  
 <span data-ttu-id="0e407-141">您不必停用 [開始] 按鈕，您可以讓按鈕保持作用中，但如果使用者再次選擇該按鈕，請取消已在執行的作業，並讓最近啟動的作業繼續執行。</span><span class="sxs-lookup"><span data-stu-id="0e407-141">Instead of disabling the **Start** button, you can keep the button active but, if the user chooses that button again, cancel the operation that's already running and let the most recently started operation continue.</span></span>  
  
 <span data-ttu-id="0e407-142">如需有關取消的詳細資訊，請參閱 <<c0> [ 微調非同步應用程式 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md)。</span><span class="sxs-lookup"><span data-stu-id="0e407-142">For more information about cancellation, see [Fine-Tuning Your Async Application (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/fine-tuning-your-async-application.md).</span></span>  
  
 <span data-ttu-id="0e407-143">若要設定此案例，請對[檢閱及執行範例應用程式](#BKMD_SettingUpTheExample)中提供的基本程式碼進行下列變更。</span><span class="sxs-lookup"><span data-stu-id="0e407-143">To set up this scenario, make the following changes to the basic code that is provided in [Reviewing and Running the Example App](#BKMD_SettingUpTheExample).</span></span> <span data-ttu-id="0e407-144">您也可以下載完成的應用程式，從[非同步範例：重新進入.NET 桌面應用程式](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)。</span><span class="sxs-lookup"><span data-stu-id="0e407-144">You also can download the finished app from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span> <span data-ttu-id="0e407-145">此專案的名稱是 CancelAndRestart。</span><span class="sxs-lookup"><span data-stu-id="0e407-145">The name of this project is CancelAndRestart.</span></span>  
  
1.  <span data-ttu-id="0e407-146">宣告 <xref:System.Threading.CancellationTokenSource> 變數 `cts`，這是在所有方法的範圍內。</span><span class="sxs-lookup"><span data-stu-id="0e407-146">Declare a <xref:System.Threading.CancellationTokenSource> variable, `cts`, that’s in scope for all methods.</span></span>  
  
    ```vb  
    Class MainWindow // Or Class MainPage  
  
        ' *** Declare a System.Threading.CancellationTokenSource.  
        Dim cts As CancellationTokenSource  
    ```  
  
2.  <span data-ttu-id="0e407-147">在 `StartButton_Click` 中，判定作業是否已在進行中。</span><span class="sxs-lookup"><span data-stu-id="0e407-147">In `StartButton_Click`, determine whether an operation is already underway.</span></span> <span data-ttu-id="0e407-148">如果值`cts`是`Nothing`，沒有任何作業已在使用中。</span><span class="sxs-lookup"><span data-stu-id="0e407-148">If the value of `cts` is `Nothing`, no operation is already active.</span></span> <span data-ttu-id="0e407-149">如果值不是`Nothing`，已在執行的作業已取消。</span><span class="sxs-lookup"><span data-stu-id="0e407-149">If the value isn't `Nothing`, the operation that is already running is canceled.</span></span>  
  
    ```vb  
    ' *** If a download process is already underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
    ```  
  
3.  <span data-ttu-id="0e407-150">將 `cts` 設為代表目前程序的不同值。</span><span class="sxs-lookup"><span data-stu-id="0e407-150">Set `cts` to a different value that represents the current process.</span></span>  
  
    ```vb  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
    ```  
  
4.  <span data-ttu-id="0e407-151">在結尾`StartButton_Click`目前的程序已完成，因此設定的值`cts`回到`Nothing`。</span><span class="sxs-lookup"><span data-stu-id="0e407-151">At the end of `StartButton_Click`, the current process is complete, so set the value of `cts` back to `Nothing`.</span></span>  
  
    ```vb  
    ' *** When the process completes, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
    ```  
  
 <span data-ttu-id="0e407-152">下列程式碼顯示 `StartButton_Click` 中的所有變更。</span><span class="sxs-lookup"><span data-stu-id="0e407-152">The following code shows all the changes in `StartButton_Click`.</span></span> <span data-ttu-id="0e407-153">新增的項目會以星號標記。</span><span class="sxs-lookup"><span data-stu-id="0e407-153">The additions are marked with asterisks.</span></span>  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
  
    ' This line is commented out to make the results clearer.   
    'ResultsTextBox.Text = ""  
  
    ' *** If a download process is underway, cancel it.  
    If cts IsNot Nothing Then  
        cts.Cancel()  
    End If  
  
    ' *** Now set cts to cancel the current process if the button is chosen again.  
    Dim newCTS As CancellationTokenSource = New CancellationTokenSource()  
    cts = newCTS  
  
    Try  
        ' *** Send a token to carry the message if the operation is canceled.  
        Await AccessTheWebAsync(cts.Token)  
  
    Catch ex As OperationCanceledException  
        ResultsTextBox.Text &= vbCrLf & "Download canceled." & vbCrLf  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
    End Try  
  
    ' *** When the process is complete, signal that another process can proceed.  
    If cts Is newCTS Then  
        cts = Nothing  
    End If  
End Sub  
```  
  
 <span data-ttu-id="0e407-154">在 `AccessTheWebAsync` 中進行下列變更。</span><span class="sxs-lookup"><span data-stu-id="0e407-154">In `AccessTheWebAsync`, make the following changes.</span></span>  
  
-   <span data-ttu-id="0e407-155">加入參數以接受來自 `StartButton_Click` 的取消語彙基元。</span><span class="sxs-lookup"><span data-stu-id="0e407-155">Add a parameter to accept the cancellation token from `StartButton_Click`.</span></span>  
  
-   <span data-ttu-id="0e407-156">使用 <xref:System.Net.Http.HttpClient.GetAsync%2A> 方法來下載網站，因為 `GetAsync` 接受 <xref:System.Threading.CancellationToken> 引數。</span><span class="sxs-lookup"><span data-stu-id="0e407-156">Use the <xref:System.Net.Http.HttpClient.GetAsync%2A> method to download the websites because `GetAsync` accepts a <xref:System.Threading.CancellationToken> argument.</span></span>  
  
-   <span data-ttu-id="0e407-157">在呼叫 `DisplayResults` 顯示每個下載網站的結果前，請檢查 `ct` 以確認目前的作業尚未取消。</span><span class="sxs-lookup"><span data-stu-id="0e407-157">Before calling `DisplayResults` to display the results for each downloaded website, check `ct` to verify that the current operation hasn’t been canceled.</span></span>  
  
 <span data-ttu-id="0e407-158">下列程式碼會顯示這些變更 (以星號標記)。</span><span class="sxs-lookup"><span data-stu-id="0e407-158">The following code shows these changes, which are marked with asterisks.</span></span>  
  
```vb  
' *** Provide a parameter for the CancellationToken from StartButton_Click.  
Private Async Function AccessTheWebAsync(ct As CancellationToken) As Task  
  
    ' Declare an HttpClient object.  
    Dim client = New HttpClient()  
  
    ' Make a list of web addresses.  
    Dim urlList As List(Of String) = SetUpURLList()  
  
    Dim total = 0  
    Dim position = 0  
  
    For Each url In urlList  
        ' *** Use the HttpClient.GetAsync method because it accepts a   
        ' cancellation token.  
        Dim response As HttpResponseMessage = Await client.GetAsync(url, ct)  
  
        ' *** Retrieve the website contents from the HttpResponseMessage.  
        Dim urlContents As Byte() = Await response.Content.ReadAsByteArrayAsync()  
  
        ' *** Check for cancellations before displaying information about the   
        ' latest site.   
        ct.ThrowIfCancellationRequested()  
  
        position += 1  
        DisplayResults(url, urlContents, position)  
  
        ' Update the total.  
        total += urlContents.Length  
    Next  
  
    ' Display the total count for all of the websites.  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
End Function  
```  
  
 <span data-ttu-id="0e407-159">如果在這個應用程式正在執行時選擇 [開始] 按鈕多次，則應該會產生類似下列的輸出結果。</span><span class="sxs-lookup"><span data-stu-id="0e407-159">If you choose the **Start** button several times while this app is running, it should produce results that resemble the following output.</span></span>  
  
```  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               122505  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
Download canceled.  
  
1. msdn.microsoft.com/library/hh191443.aspx                83732  
2. msdn.microsoft.com/library/aa578028.aspx               205273  
3. msdn.microsoft.com/library/jj155761.aspx                29019  
4. msdn.microsoft.com/library/hh290140.aspx               117152  
5. msdn.microsoft.com/library/hh524395.aspx                68959  
6. msdn.microsoft.com/library/ms404677.aspx               197325  
7. msdn.microsoft.com                                            42972  
8. msdn.microsoft.com/library/ff730837.aspx               146159  
  
TOTAL bytes returned:  890591  
```  
  
 <span data-ttu-id="0e407-160">若要排除部分清單，請取消註解 `StartButton_Click` 中程式碼的第一行，以清除每次使用者重新啟動作業時出現的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="0e407-160">To eliminate the partial lists, uncomment the first line of code in `StartButton_Click` to clear the text box each time the user restarts the operation.</span></span>  
  
###  <a name="BKMK_RunMultipleOperations"></a> <span data-ttu-id="0e407-161">執行多個作業並將輸出加入佇列</span><span class="sxs-lookup"><span data-stu-id="0e407-161">Run Multiple Operations and Queue the Output</span></span>  
 <span data-ttu-id="0e407-162">此第三個範例是最複雜的，因為每當使用者選擇 [開始] 按鈕時，應用程式就會啟動另一個非同步作業，而且所有作業都會執行到完成為止。</span><span class="sxs-lookup"><span data-stu-id="0e407-162">This third example is the most complicated in that the app starts another asynchronous operation each time that the user chooses the **Start** button, and all the operations run to completion.</span></span> <span data-ttu-id="0e407-163">所有要求的作業會以非同步方式從清單下載網站，但作業的輸出會以循序方式呈現。</span><span class="sxs-lookup"><span data-stu-id="0e407-163">All the requested operations download websites from the list asynchronously, but the output from the operations is presented sequentially.</span></span> <span data-ttu-id="0e407-164">也就是隨[辨識重新進入](#BKMK_RecognizingReentrancy)顯示輸出，實際的下載活動會交錯進行，但每個群組的結果清單會循序呈現。</span><span class="sxs-lookup"><span data-stu-id="0e407-164">That is, the actual downloading activity is interleaved, as the output in [Recognizing Reentrancy](#BKMK_RecognizingReentrancy) shows, but the list of results for each group is presented separately.</span></span>  
  
 <span data-ttu-id="0e407-165">作業會共用全域 <xref:System.Threading.Tasks.Task>，`pendingWork`，做為顯示程序的閘道管理員。</span><span class="sxs-lookup"><span data-stu-id="0e407-165">The operations share a global <xref:System.Threading.Tasks.Task>, `pendingWork`, which serves as a gatekeeper for the display process.</span></span>  
  
 <span data-ttu-id="0e407-166">您可以執行這個範例，方法是將變更貼至[建置應用程式](#BKMK_BuildingTheApp)中的程式碼，或者遵循[下載應用程式](#BKMK_DownloadingTheApp)的指示來下載範例，然後執行 QueueResults 專案。</span><span class="sxs-lookup"><span data-stu-id="0e407-166">You can run this example by pasting the changes into the code in [Building the App](#BKMK_BuildingTheApp), or you can follow the instructions in [Downloading the App](#BKMK_DownloadingTheApp) to download the sample and then run the QueueResults project.</span></span>  
  
 <span data-ttu-id="0e407-167">下列輸出顯示當使用者只選擇 [開始] 按鈕一次時的結果。</span><span class="sxs-lookup"><span data-stu-id="0e407-167">The following output shows the result if the user chooses the **Start** button only once.</span></span> <span data-ttu-id="0e407-168">字母標籤 A，表示第一次選擇 [開始] 按鈕時的結果。</span><span class="sxs-lookup"><span data-stu-id="0e407-168">The letter label, A, indicates that the result is from the first time the **Start** button is chosen.</span></span> <span data-ttu-id="0e407-169">數字顯示下載目標清單中的 URL 順序。</span><span class="sxs-lookup"><span data-stu-id="0e407-169">The numbers show the order of the URLs in the list of download targets.</span></span>  
  
```  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               209858  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
A-7. msdn.microsoft.com                                            53266  
A-8. msdn.microsoft.com/library/ff730837.aspx               148020  
  
TOTAL bytes returned:  918876  
  
#Group A is complete.  
```  
  
 <span data-ttu-id="0e407-170">如果使用者選擇 [開始] 按鈕三次，應用程式會產生類似下列幾行的輸出。</span><span class="sxs-lookup"><span data-stu-id="0e407-170">If the user chooses the **Start** button three times, the app produces output that resembles the following lines.</span></span> <span data-ttu-id="0e407-171">以井字號 (#) 開頭的資訊行會追蹤應用程式的進度。</span><span class="sxs-lookup"><span data-stu-id="0e407-171">The information lines that start with a pound sign (#) trace the progress of the application.</span></span>  
  
```  
#Starting group A.  
#Task assigned for group A.  
  
A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
A-4. msdn.microsoft.com/library/hh290140.aspx               119027  
A-5. msdn.microsoft.com/library/hh524395.aspx                71259  
A-6. msdn.microsoft.com/library/ms404677.aspx               199185  
  
#Starting group B.  
#Task assigned for group B.  
  
A-7. msdn.microsoft.com                                            53266  
  
#Starting group C.  
#Task assigned for group C.  
  
A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916095  
  
B-1. msdn.microsoft.com/library/hh191443.aspx                87389  
B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
  
#Group A is complete.  
  
B-7. msdn.microsoft.com                                            53266  
B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  916097  
  
C-1. msdn.microsoft.com/library/hh191443.aspx                87389  
C-2. msdn.microsoft.com/library/aa578028.aspx               207089  
  
#Group B is complete.  
  
C-3. msdn.microsoft.com/library/jj155761.aspx                30870  
C-4. msdn.microsoft.com/library/hh290140.aspx               119027  
C-5. msdn.microsoft.com/library/hh524395.aspx                72765  
C-6. msdn.microsoft.com/library/ms404677.aspx               199186  
C-7. msdn.microsoft.com                                            56190  
C-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
TOTAL bytes returned:  920526  
  
#Group C is complete.  
```  
  
 <span data-ttu-id="0e407-172">群組 B 和 C 在群組 A 完成前啟動，但每個群組的輸出會單獨顯示。</span><span class="sxs-lookup"><span data-stu-id="0e407-172">Groups B and C start before group A has finished, but the output for the each group appears separately.</span></span> <span data-ttu-id="0e407-173">先顯示群組 A 的所有輸出，接著是群組 B 的所有輸出，然後是群組 C 的所有輸出。應用程式一律依序顯示群組，且對每個群組，一律會根據 URL 在 URL 清單中的出現順序，顯示個別網站的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="0e407-173">All the output for group A appears first, followed by all the output for group B, and then all the output for group C. The app always displays the groups in order and, for each group, always displays the information about the individual websites in the order that the URLs appear in the list of URLs.</span></span>  
  
 <span data-ttu-id="0e407-174">不過，您無法預測實際的下載順序。</span><span class="sxs-lookup"><span data-stu-id="0e407-174">However, you can't predict the order in which the downloads actually happen.</span></span> <span data-ttu-id="0e407-175">啟動多個群組之後，它們產生的下載工作會全部啟用。</span><span class="sxs-lookup"><span data-stu-id="0e407-175">After multiple groups have been started, the download tasks that they generate are all active.</span></span> <span data-ttu-id="0e407-176">您不能假設 A-1 將在 B-1 之前下載，也不能假設 A-1 將在 A-2 之前下載。</span><span class="sxs-lookup"><span data-stu-id="0e407-176">You can't assume that A-1 will be downloaded before B-1, and you can't assume that A-1 will be downloaded before A-2.</span></span>  
  
#### <a name="global-definitions"></a><span data-ttu-id="0e407-177">全域定義</span><span class="sxs-lookup"><span data-stu-id="0e407-177">Global Definitions</span></span>  
 <span data-ttu-id="0e407-178">範例程式碼包含所有方法都會看見的下列兩個全域宣告。</span><span class="sxs-lookup"><span data-stu-id="0e407-178">The sample code contains the following two global declarations that are visible from all methods.</span></span>  
  
```vb  
Class MainWindow    ' Class MainPage in Windows Store app.  
  
    ' ***Declare the following variables where all methods can access them.   
    Private pendingWork As Task = Nothing  
    Private group As Char = ChrW(AscW("A") - 1)  
```  
  
 <span data-ttu-id="0e407-179">`Task` 變數 `pendingWork` 會監督顯示程序，並防止任何群組中斷另一個群組的顯示作業。</span><span class="sxs-lookup"><span data-stu-id="0e407-179">The `Task` variable, `pendingWork`, oversees the display process and prevents any group from interrupting another group's display operation.</span></span> <span data-ttu-id="0e407-180">字元變數 `group` 會標示不同群組的輸出，確認以預期的順序顯示結果。</span><span class="sxs-lookup"><span data-stu-id="0e407-180">The character variable, `group`, labels the output from different groups to verify that results appear in the expected order.</span></span>  
  
#### <a name="the-click-event-handler"></a><span data-ttu-id="0e407-181">Click 事件處理常式</span><span class="sxs-lookup"><span data-stu-id="0e407-181">The Click Event Handler</span></span>  
 <span data-ttu-id="0e407-182">每當使用者選擇 [開始] 按鈕，事件處理常式 `StartButton_Click` 就會增加群組字母。</span><span class="sxs-lookup"><span data-stu-id="0e407-182">The event handler, `StartButton_Click`, increments the group letter each time the user chooses the **Start** button.</span></span> <span data-ttu-id="0e407-183">處理常式接著會呼叫 `AccessTheWebAsync` 來執行下載作業。</span><span class="sxs-lookup"><span data-stu-id="0e407-183">Then the handler calls `AccessTheWebAsync` to run the downloading operation.</span></span>  
  
```vb  
Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
    ' ***Verify that each group's results are displayed together, and that  
    ' the groups display in order, by marking each group with a letter.  
    group = ChrW(AscW(group) + 1)  
    ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Starting group {0}.", group)  
  
    Try  
        ' *** Pass the group value to AccessTheWebAsync.  
        Dim finishedGroup As Char = Await AccessTheWebAsync(group)  
  
        ' The following line verifies a successful return from the download and   
        ' display procedures.   
        ResultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "#Group {0} is complete." & vbCrLf, finishedGroup)  
  
    Catch ex As Exception  
        ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
  
    End Try  
End Sub  
```  
  
#### <a name="the-accessthewebasync-method"></a><span data-ttu-id="0e407-184">AccessTheWebAsync 方法</span><span class="sxs-lookup"><span data-stu-id="0e407-184">The AccessTheWebAsync Method</span></span>  
 <span data-ttu-id="0e407-185">此範例會將 `AccessTheWebAsync` 分為兩個方法。</span><span class="sxs-lookup"><span data-stu-id="0e407-185">This example splits `AccessTheWebAsync` into two methods.</span></span> <span data-ttu-id="0e407-186">第一種方法為 `AccessTheWebAsync`，可啟動群組的所有下載工作，並且設定 `pendingWork` 來控制顯示程序。</span><span class="sxs-lookup"><span data-stu-id="0e407-186">The first method, `AccessTheWebAsync`, starts all the download tasks for a group and sets up `pendingWork` to control the display process.</span></span> <span data-ttu-id="0e407-187">此方法會使用 Language Integrated Query (LINQ 查詢) 和 <xref:System.Linq.Enumerable.ToArray%2A> 來同時啟動所有下載工作。</span><span class="sxs-lookup"><span data-stu-id="0e407-187">The method uses a Language Integrated Query (LINQ query) and <xref:System.Linq.Enumerable.ToArray%2A> to start all the download tasks at the same time.</span></span>  
  
 <span data-ttu-id="0e407-188">`AccessTheWebAsync` 接著呼叫 `FinishOneGroupAsync` 來等候每個下載完成，並顯示它的長度。</span><span class="sxs-lookup"><span data-stu-id="0e407-188">`AccessTheWebAsync` then calls `FinishOneGroupAsync` to await the completion of each download and display its length.</span></span>  
  
 <span data-ttu-id="0e407-189">`FinishOneGroupAsync` 傳回工作，該工作指派給 `AccessTheWebAsync` 中的 `pendingWork`。</span><span class="sxs-lookup"><span data-stu-id="0e407-189">`FinishOneGroupAsync` returns a task that's assigned to `pendingWork` in `AccessTheWebAsync`.</span></span> <span data-ttu-id="0e407-190">在工作完成前，該值會防止另一項作業中斷該工作。</span><span class="sxs-lookup"><span data-stu-id="0e407-190">That value prevents interruption by another operation before the task is complete.</span></span>  
  
```vb  
Private Async Function AccessTheWebAsync(grp As Char) As Task(Of Char)  
  
    Dim client = New HttpClient()  
  
    ' Make a list of the web addresses to download.  
    Dim urlList As List(Of String) = SetUpURLList()  
  
    ' ***Kick off the downloads. The application of ToArray activates all the download tasks.  
    Dim getContentTasks As Task(Of Byte())() =  
        urlList.Select(Function(addr) client.GetByteArrayAsync(addr)).ToArray()  
  
    ' ***Call the method that awaits the downloads and displays the results.  
    ' Assign the Task that FinishOneGroupAsync returns to the gatekeeper task, pendingWork.  
    pendingWork = FinishOneGroupAsync(urlList, getContentTasks, grp)  
  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & "#Task assigned for group {0}. Download tasks are active." & vbCrLf, grp)  
  
    ' ***This task is complete when a group has finished downloading and displaying.  
    Await pendingWork  
  
    ' You can do other work here or just return.  
    Return grp  
End Function  
```  
  
#### <a name="the-finishonegroupasync-method"></a><span data-ttu-id="0e407-191">FinishOneGroupAsync 方法</span><span class="sxs-lookup"><span data-stu-id="0e407-191">The FinishOneGroupAsync Method</span></span>  
 <span data-ttu-id="0e407-192">這個方法不斷循環群組中的下載工作，等待每一項、顯示下載網站的長度，並將長度加總到總計。</span><span class="sxs-lookup"><span data-stu-id="0e407-192">This method cycles through the download tasks in a group, awaiting each one, displaying the length of the downloaded website, and adding the length to the total.</span></span>  
  
 <span data-ttu-id="0e407-193">`FinishOneGroupAsync` 中的第一個陳述式使用 `pendingWork`，確保進入方法不會干擾已在顯示程序中的作業，或已在等候的作業。</span><span class="sxs-lookup"><span data-stu-id="0e407-193">The first statement in `FinishOneGroupAsync` uses `pendingWork` to make sure that entering the method doesn't interfere with an operation that is already in the display process or that's already waiting.</span></span> <span data-ttu-id="0e407-194">如果這類作業正在進行，進入作業必須等候。</span><span class="sxs-lookup"><span data-stu-id="0e407-194">If such an operation is in progress, the entering operation must wait its turn.</span></span>  
  
```vb  
Private Async Function FinishOneGroupAsync(urls As List(Of String), contentTasks As Task(Of Byte())(), grp As Char) As Task  
  
    ' Wait for the previous group to finish displaying results.  
    If pendingWork IsNot Nothing Then  
        Await pendingWork  
    End If  
  
    Dim total = 0  
  
    ' contentTasks is the array of Tasks that was created in AccessTheWebAsync.  
    For i As Integer = 0 To contentTasks.Length - 1  
        ' Await the download of a particular URL, and then display the URL and  
        ' its length.  
        Dim content As Byte() = Await contentTasks(i)  
        DisplayResults(urls(i), content, i, grp)  
        total += content.Length  
    Next  
  
    ' Display the total count for all of the websites.  
    ResultsTextBox.Text &=  
        String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
End Function  
```  
  
 <span data-ttu-id="0e407-195">您可以執行這個範例，方法是將變更貼至[建置應用程式](#BKMK_BuildingTheApp)中的程式碼，或者遵循[下載應用程式](#BKMK_DownloadingTheApp)的指示來下載範例，然後執行 QueueResults 專案。</span><span class="sxs-lookup"><span data-stu-id="0e407-195">You can run this example by pasting the changes into the code in [Building the App](#BKMK_BuildingTheApp), or you can follow the instructions in [Downloading the App](#BKMK_DownloadingTheApp) to download the sample, and then run the QueueResults project.</span></span>  
  
#### <a name="points-of-interest"></a><span data-ttu-id="0e407-196">參考資訊</span><span class="sxs-lookup"><span data-stu-id="0e407-196">Points of Interest</span></span>  
 <span data-ttu-id="0e407-197">在輸出中以井字號 (#) 開頭的資訊行會釐清此範例的運作方式。</span><span class="sxs-lookup"><span data-stu-id="0e407-197">The information lines that start with a pound sign (#) in the output clarify how this example works.</span></span>  
  
 <span data-ttu-id="0e407-198">輸出會顯示下列模式。</span><span class="sxs-lookup"><span data-stu-id="0e407-198">The output shows the following patterns.</span></span>  
  
-   <span data-ttu-id="0e407-199">當前一個群組顯示其輸出時，就可以啟動一個群組，但不會中斷前一個群組的輸出顯示。</span><span class="sxs-lookup"><span data-stu-id="0e407-199">A group can be started while a previous group is displaying its output, but the display of the previous group's output isn't interrupted.</span></span>  
  
    ```  
    #Starting group A.  
    #Task assigned for group A. Download tasks are active.  
  
    A-1. msdn.microsoft.com/library/hh191443.aspx                87389  
    A-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    A-3. msdn.microsoft.com/library/jj155761.aspx                30870  
    A-4. msdn.microsoft.com/library/hh290140.aspx               119037  
    A-5. msdn.microsoft.com/library/hh524395.aspx                71260  
  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
  
    A-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    A-7. msdn.microsoft.com                                            53078  
    A-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915919  
  
    B-1. msdn.microsoft.com/library/hh191443.aspx                87388  
    B-2. msdn.microsoft.com/library/aa578028.aspx               207089  
    B-3. msdn.microsoft.com/library/jj155761.aspx                30870  
  
    #Group A is complete.  
  
    B-4. msdn.microsoft.com/library/hh290140.aspx               119027  
    B-5. msdn.microsoft.com/library/hh524395.aspx                71260  
    B-6. msdn.microsoft.com/library/ms404677.aspx               199186  
    B-7. msdn.microsoft.com                                            53078  
    B-8. msdn.microsoft.com/library/ff730837.aspx               148010  
  
    TOTAL bytes returned:  915908  
    ```  
  
-   <span data-ttu-id="0e407-200">`pendingWork`任務`Nothing`開頭的`FinishOneGroupAsync`只有針對群組 A 啟動第一個。</span><span class="sxs-lookup"><span data-stu-id="0e407-200">The `pendingWork` task is `Nothing` at the start of `FinishOneGroupAsync` only for group A, which started first.</span></span> <span data-ttu-id="0e407-201">當群組 A 到達 `FinishOneGroupAsync` 時，它尚未完成 await 運算式。</span><span class="sxs-lookup"><span data-stu-id="0e407-201">Group A hasn’t yet completed an await expression when it reaches `FinishOneGroupAsync`.</span></span> <span data-ttu-id="0e407-202">因此，尚未將控制項返回 `AccessTheWebAsync`，且尚未針對 `pendingWork` 進行第一次指派。</span><span class="sxs-lookup"><span data-stu-id="0e407-202">Therefore, control hasn't returned to `AccessTheWebAsync`, and the first assignment to `pendingWork` hasn't occurred.</span></span>  
  
-   <span data-ttu-id="0e407-203">下列兩行一律會在輸出中一起出現。</span><span class="sxs-lookup"><span data-stu-id="0e407-203">The following two lines always appear together in the output.</span></span> <span data-ttu-id="0e407-204">在 `StartButton_Click` 中啟動群組的作業，與將群組的工作指派給 `pendingWork` 之間，程式碼永遠不會中斷</span><span class="sxs-lookup"><span data-stu-id="0e407-204">The code is never interrupted between starting a group's operation in `StartButton_Click` and assigning a task for the group to `pendingWork`.</span></span>  
  
    ```  
    #Starting group B.  
    #Task assigned for group B. Download tasks are active.  
    ```  
  
     <span data-ttu-id="0e407-205">在群組進入 `StartButton_Click` 後，作業尚未完成 await 運算式，需直到作業進入 `FinishOneGroupAsync` 為止。</span><span class="sxs-lookup"><span data-stu-id="0e407-205">After a group enters `StartButton_Click`, the operation doesn't complete an await expression until the operation enters `FinishOneGroupAsync`.</span></span> <span data-ttu-id="0e407-206">因此，沒有其他作業可在該程式碼區段的過程中取得控制項。</span><span class="sxs-lookup"><span data-stu-id="0e407-206">Therefore, no other operation can gain control during that segment of code.</span></span>  
  
##  <a name="BKMD_SettingUpTheExample"></a> <span data-ttu-id="0e407-207">檢閱及執行範例應用程式</span><span class="sxs-lookup"><span data-stu-id="0e407-207">Reviewing and Running the Example App</span></span>  
 <span data-ttu-id="0e407-208">若要進一步了解範例應用程式，您可以下載它、自行建置它，或檢閱本主題結尾的程式碼而不必實作應用程式。</span><span class="sxs-lookup"><span data-stu-id="0e407-208">To better understand the example app, you can download it, build it yourself, or review the code at the end of this topic without implementing the app.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0e407-209">若要執行範例作為 Windows Presentation Foundation (WPF) 傳統型應用程式，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="0e407-209">To run the example as a Windows Presentation Foundation (WPF) desktop app, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
###  <a name="BKMK_DownloadingTheApp"></a> <span data-ttu-id="0e407-210">下載應用程式</span><span class="sxs-lookup"><span data-stu-id="0e407-210">Downloading the App</span></span>  
  
1.  <span data-ttu-id="0e407-211">下載的壓縮的檔從[非同步範例：重新進入.NET 桌面應用程式](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06)。</span><span class="sxs-lookup"><span data-stu-id="0e407-211">Download the compressed file from [Async Samples: Reentrancy in .NET Desktop Apps](https://code.msdn.microsoft.com/Async-Sample-Preventing-a8489f06).</span></span>  
  
2.  <span data-ttu-id="0e407-212">解壓縮您下載的檔案，然後啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="0e407-212">Decompress the file that you downloaded, and then start Visual Studio.</span></span>  
  
3.  <span data-ttu-id="0e407-213">在功能表列上，依序選擇 [檔案] 、[開啟舊檔] 及 [專案/方案] 。</span><span class="sxs-lookup"><span data-stu-id="0e407-213">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
4.  <span data-ttu-id="0e407-214">導覽至保存解壓縮之範例程式碼的資料夾，然後開啟方案 (.sln) 檔案。</span><span class="sxs-lookup"><span data-stu-id="0e407-214">Navigate to the folder that holds the decompressed sample code, and then open the solution (.sln) file.</span></span>  
  
5.  <span data-ttu-id="0e407-215">在方案總管中，開啟要執行之專案的捷徑功能表，然後選擇 [設定為啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="0e407-215">In **Solution Explorer**, open the shortcut menu for the project that you want to run, and then choose **Set as StartUpProject**.</span></span>  
  
6.  <span data-ttu-id="0e407-216">選擇 CTRL + F5 鍵以建置並執行專案。</span><span class="sxs-lookup"><span data-stu-id="0e407-216">Choose the CTRL+F5 keys to build and run the project.</span></span>  
  
###  <a name="BKMK_BuildingTheApp"></a> <span data-ttu-id="0e407-217">建置應用程式</span><span class="sxs-lookup"><span data-stu-id="0e407-217">Building the App</span></span>  
 <span data-ttu-id="0e407-218">下節提供將範例建置為 WPF 應用程式的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0e407-218">The following section provides the code to build the example as a WPF app.</span></span>  
  
##### <a name="to-build-a-wpf-app"></a><span data-ttu-id="0e407-219">若要建置 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="0e407-219">To build a WPF app</span></span>  
  
1.  <span data-ttu-id="0e407-220">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="0e407-220">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="0e407-221">在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。</span><span class="sxs-lookup"><span data-stu-id="0e407-221">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="0e407-222">[ **新增專案** ] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="0e407-222">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="0e407-223">在 **已安裝的範本**窗格中，展開**Visual Basic**，然後展開**Windows**。</span><span class="sxs-lookup"><span data-stu-id="0e407-223">In the **Installed Templates** pane, expand **Visual Basic**, and then expand **Windows**.</span></span>  
  
4.  <span data-ttu-id="0e407-224">在專案類型清單中，選擇 [WPF 應用程式]。</span><span class="sxs-lookup"><span data-stu-id="0e407-224">In the list of project types, choose **WPF Application**.</span></span>  
  
5.  <span data-ttu-id="0e407-225">將專案命名為 `WebsiteDownloadWPF`，然後選擇 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0e407-225">Name the project `WebsiteDownloadWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="0e407-226">新的專案隨即會出現在方案總管中。</span><span class="sxs-lookup"><span data-stu-id="0e407-226">The new project appears in **Solution Explorer**.</span></span>  
  
6.  <span data-ttu-id="0e407-227">在 Visual Studio 程式碼編輯器中，選擇 [ **MainWindow.xaml** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0e407-227">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="0e407-228">如未顯示索引標籤，請在方案總管中開啟 MainWindow.xaml 的捷徑功能表，然後選擇 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="0e407-228">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
7.  <span data-ttu-id="0e407-229">在 MainWindow.xaml 的 [XAML] 檢視中，以下列程式碼取代程式碼。</span><span class="sxs-lookup"><span data-stu-id="0e407-229">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```vb  
    <Window x:Class="MainWindow"  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:local="using:WebsiteDownloadWPF"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"  
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"  
        mc:Ignorable="d">  
  
        <Grid Width="517" Height="360">  
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="-1,0,0,0" VerticalAlignment="Top" Click="StartButton_Click" Height="53" Background="#FFA89B9B" FontSize="36" Width="518"  />  
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" Margin="-1,53,0,-36" TextWrapping="Wrap" VerticalAlignment="Top" Height="343" FontSize="10" ScrollViewer.VerticalScrollBarVisibility="Visible" Width="518" FontFamily="Lucida Console" />  
        </Grid>  
    </Window>  
    ```  
  
     <span data-ttu-id="0e407-230">包含文字方塊和按鈕的簡易視窗會出現在 MainWindow.xaml 的 [設計] 檢視中。</span><span class="sxs-lookup"><span data-stu-id="0e407-230">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
8.  <span data-ttu-id="0e407-231">加入 <xref:System.Net.Http> 的參考。</span><span class="sxs-lookup"><span data-stu-id="0e407-231">Add a reference for <xref:System.Net.Http>.</span></span>  
  
9. <span data-ttu-id="0e407-232">在 **方案總管**，開啟 MainWindow.xaml.vb，捷徑功能表，然後選擇**檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="0e407-232">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
10. <span data-ttu-id="0e407-233">在 MainWindow.xaml.vb，取代下列程式碼中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="0e407-233">In MainWindow.xaml.vb , replace the code with the following code.</span></span>  
  
    ```vb  
    ' Add the following Imports statements, and add a reference for System.Net.Http.  
    Imports System.Net.Http  
    Imports System.Threading  
  
    Class MainWindow  
  
        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs)  
            ' This line is commented out to make the results clearer in the output.  
            'ResultsTextBox.Text = ""  
  
            Try  
                Await AccessTheWebAsync()  
  
            Catch ex As Exception  
                ResultsTextBox.Text &= vbCrLf & "Downloads failed."  
  
            End Try  
        End Sub  
  
        Private Async Function AccessTheWebAsync() As Task  
  
            ' Declare an HttpClient object.  
            Dim client = New HttpClient()  
  
            ' Make a list of web addresses.  
            Dim urlList As List(Of String) = SetUpURLList()  
  
            Dim total = 0  
            Dim position = 0  
  
            For Each url In urlList  
                ' GetByteArrayAsync returns a task. At completion, the task  
                ' produces a byte array.  
                Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
  
                position += 1  
                DisplayResults(url, urlContents, position)  
  
                ' Update the total.  
                total += urlContents.Length  
            Next  
  
            ' Display the total count for all of the websites.  
            ResultsTextBox.Text &=  
                String.Format(vbCrLf & vbCrLf & "TOTAL bytes returned:  " & total & vbCrLf)  
        End Function  
  
        Private Function SetUpURLList() As List(Of String)  
            Dim urls = New List(Of String) From  
            {  
                "https://msdn.microsoft.com/library/hh191443.aspx",  
                "https://msdn.microsoft.com/library/aa578028.aspx",  
                "https://msdn.microsoft.com/library/jj155761.aspx",  
                "https://msdn.microsoft.com/library/hh290140.aspx",  
                "https://msdn.microsoft.com/library/hh524395.aspx",  
                "https://msdn.microsoft.com/library/ms404677.aspx",  
                "https://msdn.microsoft.com",  
                "https://msdn.microsoft.com/library/ff730837.aspx"  
            }  
            Return urls  
        End Function  
  
        Private Sub DisplayResults(url As String, content As Byte(), pos As Integer)  
            ' Display the length of each website. The string format is designed  
            ' to be used with a monospaced font, such as Lucida Console or  
            ' Global Monospace.  
  
            ' Strip off the "http:'".  
            Dim displayURL = url.Replace("https://", "")  
            ' Display position in the URL list, the URL, and the number of bytes.  
            ResultsTextBox.Text &= String.Format(vbCrLf & "{0}. {1,-58} {2,8}", pos, displayURL, content.Length)  
        End Sub  
    End Class  
    ```  
  
11. <span data-ttu-id="0e407-234">選擇 CTRL+F5 鍵以執行程式，然後選擇 [開始] 按鈕數次。</span><span class="sxs-lookup"><span data-stu-id="0e407-234">Choose the CTRL+F5 keys to run the program, and then choose the **Start** button several times.</span></span>  
  
12. <span data-ttu-id="0e407-235">從[停用開始按鈕](#BKMK_DisableTheStartButton)、[取消後再重新啟動作業](#BKMK_CancelAndRestart)或[執行多個作業並將輸出加入佇列](#BKMK_RunMultipleOperations)進行變更以處理重新進入。</span><span class="sxs-lookup"><span data-stu-id="0e407-235">Make the changes from [Disable the Start Button](#BKMK_DisableTheStartButton), [Cancel and Restart the Operation](#BKMK_CancelAndRestart), or [Run Multiple Operations and Queue the Output](#BKMK_RunMultipleOperations) to handle the reentrancy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e407-236">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e407-236">See also</span></span>

- [<span data-ttu-id="0e407-237">逐步解說：存取 Web 使用 Async 和 Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e407-237">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)
- [<span data-ttu-id="0e407-238">使用 Async 和 Await 進行非同步程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e407-238">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
