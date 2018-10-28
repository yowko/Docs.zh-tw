---
title: 非同步程式 (Visual Basic) 中的控制流程
ms.date: 07/20/2015
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
ms.openlocfilehash: 368422338f6452bf5dbe968d4798bc0d5e937c92
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195212"
---
# <a name="control-flow-in-async-programs-visual-basic"></a><span data-ttu-id="3ce0c-102">非同步程式 (Visual Basic) 中的控制流程</span><span class="sxs-lookup"><span data-stu-id="3ce0c-102">Control Flow in Async Programs (Visual Basic)</span></span>
<span data-ttu-id="3ce0c-103">您可以使用 `Async` 和 `Await` 關鍵字更輕鬆地撰寫和維護非同步程式。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-103">You can write and maintain asynchronous programs more easily by using the `Async` and `Await` keywords.</span></span> <span data-ttu-id="3ce0c-104">不過，如果您不了解程式的運作方式，則結果可能會讓您大吃一驚。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="3ce0c-105">本主題透過簡單非同步程式來追蹤控制流程，以顯示控制何時從某個方法移至另一個方法以及每次傳輸的資訊。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ce0c-106">`Async` 和 `Await` 關鍵字是在 Visual Studio 2012 中引入。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-106">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="3ce0c-107">一般情況下，您將標記包含非同步程式碼的方法[非同步](../../../../visual-basic/language-reference/modifiers/async.md)修飾詞。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-107">In general, you mark methods that contain asynchronous code with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="3ce0c-108">在以非同步修飾詞標記方法中，您可以使用[Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md)運算子來指定方法暫停以等候被呼叫的非同步處理序完成的位置。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-108">In a method that's marked with an async modifier, you can use an [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="3ce0c-109">如需詳細資訊，請參閱 <<c0> [ 使用 Async 和 Await (Visual Basic) 的非同步程式設計](../../../../visual-basic/programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-109">For more information, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="3ce0c-110">下列範例會使用非同步方法，將所指定網站的內容下載為字串，以及顯示字串的長度。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="3ce0c-111">這個範例包含下列兩個方法。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-111">The example contains the following two methods.</span></span>  
  
-   <span data-ttu-id="3ce0c-112">`startButton_Click`，其呼叫 `AccessTheWebAsync` 並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-112">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>  
  
-   <span data-ttu-id="3ce0c-113">`AccessTheWebAsync`，會將網站的內容下載為字串，並傳回字串的長度。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-113">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="3ce0c-114">`AccessTheWebAsync`使用非同步的 <xref:System.Net.Http.HttpClient> 方法 <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> 來下載內容。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-114">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>  
  
 <span data-ttu-id="3ce0c-115">編號的顯示行會出現在程式中的策略點，協助您了解程式的執行方式，以及說明每個標記點所發生的情況。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="3ce0c-116">顯示行會標上 "ONE" 到 "SIX"。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="3ce0c-117">標籤代表程式到達這些程式碼行的順序。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-117">The labels represent the order in which the program reaches these lines of code.</span></span>  
  
 <span data-ttu-id="3ce0c-118">下列程式碼示範程式的大綱。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-118">The following code shows an outline of the program.</span></span>  
  
```vb  
Class MainWindow  
  
    Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click  
  
        ' ONE  
        Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()  
  
        ' FOUR  
        Dim contentLength As Integer = Await getLengthTask  
  
        ' SIX  
        ResultsTextBox.Text &=  
            String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
  
    End Sub  
  
    Async Function AccessTheWebAsync() As Task(Of Integer)  
  
        ' TWO  
        Dim client As HttpClient = New HttpClient()   
        Dim getStringTask As Task(Of String) =   
            client.GetStringAsync("https://msdn.microsoft.com")  
  
        ' THREE  
        Dim urlContents As String = Await getStringTask  
  
        ' FIVE  
        Return urlContents.Length  
    End Function  
  
End Class  
```  
  
 <span data-ttu-id="3ce0c-119">每個標記位置 "ONE" 到 "SIX" 都會顯示程式目前狀態的資訊。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="3ce0c-120">會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-120">The following output is produced.</span></span>  
  
```  
ONE:   Entering startButton_Click.  
           Calling AccessTheWebAsync.  
  
TWO:   Entering AccessTheWebAsync.  
           Calling HttpClient.GetStringAsync.  
  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
  
Length of the downloaded string: 33946.  
```  
  
## <a name="set-up-the-program"></a><span data-ttu-id="3ce0c-121">設定程式</span><span class="sxs-lookup"><span data-stu-id="3ce0c-121">Set Up the Program</span></span>  
 <span data-ttu-id="3ce0c-122">您可以從 MSDN 下載本主題所使用的程式碼，也可以自行建置。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ce0c-123">若要執行範例時，您必須擁有 Visual Studio 2012 或更新版本以及.NET Framework 4.5 或更新版本安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-123">To run the example, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
### <a name="download-the-program"></a><span data-ttu-id="3ce0c-124">下載程式</span><span class="sxs-lookup"><span data-stu-id="3ce0c-124">Download the Program</span></span>  
 <span data-ttu-id="3ce0c-125">您可以從 [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0) (非同步範例：非同步程式中的控制流程) 下載本主題的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0).</span></span> <span data-ttu-id="3ce0c-126">下列步驟會開啟和執行程式。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-126">The following steps open and run the program.</span></span>  
  
1.  <span data-ttu-id="3ce0c-127">解壓縮下載的檔案，然後啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-127">Unzip the downloaded file, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="3ce0c-128">在功能表列上，依序選擇 [檔案] 、[開啟舊檔] 及 [專案/方案] 。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-128">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="3ce0c-129">巡覽至保存解壓縮之範例程式碼的資料夾，並開啟方案 (.sln) 檔案，然後選擇 F5 鍵來建置和執行專案。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the F5 key to build and run the project.</span></span>  
  
### <a name="build-the-program-yourself"></a><span data-ttu-id="3ce0c-130">自行建立程式</span><span class="sxs-lookup"><span data-stu-id="3ce0c-130">Build the Program Yourself</span></span>  
 <span data-ttu-id="3ce0c-131">下列 Windows Presentation Foundation (WPF) 專案包含本主題的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>  
  
 <span data-ttu-id="3ce0c-132">若要執行專案，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="3ce0c-132">To run the project, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="3ce0c-133">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-133">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="3ce0c-134">在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-134">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="3ce0c-135">[ **新增專案** ] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-135">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="3ce0c-136">在**已安裝的範本**窗格中，選擇**Visual Basic**，然後選擇**WPF 應用程式**從專案類型清單。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-136">In the **Installed Templates** pane, choose **Visual Basic**, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="3ce0c-137">輸入 `AsyncTracer` 作為專案的名稱，然後選擇 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="3ce0c-138">新的專案隨即出現在方案總管中。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-138">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="3ce0c-139">在 Visual Studio 程式碼編輯器中，選擇 [ **MainWindow.xaml** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="3ce0c-140">如未顯示索引標籤，請在方案總管中開啟 MainWindow.xaml 的捷徑功能表，然後選擇 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6.  <span data-ttu-id="3ce0c-141">在 MainWindow.xaml 的 [XAML] 檢視中，以下列程式碼取代程式碼。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```vb  
    <Window  
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="MainWindow"  
        Title="Control Flow Trace" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="StartButton" Content="Start" HorizontalAlignment="Left" Margin="221,10,0,0" VerticalAlignment="Top" Width="75"/>  
            <TextBox x:Name="ResultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="510" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" d:LayoutOverrides="HorizontalMargin"/>  
  
        </Grid>  
    </Window>  
    ```  
  
     <span data-ttu-id="3ce0c-142">包含文字方塊和按鈕的簡易視窗會出現在 MainWindow.xaml 的 [設計] 檢視中。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
7.  <span data-ttu-id="3ce0c-143">加入 <xref:System.Net.Http> 的參考。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-143">Add a reference for <xref:System.Net.Http>.</span></span>  
  
8.  <span data-ttu-id="3ce0c-144">在 **方案總管**，開啟 MainWindow.xaml.vb，捷徑功能表，然後選擇**檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
9. <span data-ttu-id="3ce0c-145">在 MainWindow.xaml.vb，取代下列程式碼中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-145">In MainWindow.xaml.vb , replace the code with the following code.</span></span>  
  
    ```vb  
    ' Add an Imports statement and a reference for System.Net.Http.  
    Imports System.Net.Http  
  
    Class MainWindow  
  
        Private Async Sub StartButton_Click(sender As Object, e As RoutedEventArgs) Handles StartButton.Click  
  
            ' The display lines in the example lead you through the control shifts.  
            ResultsTextBox.Text &= "ONE:   Entering StartButton_Click." & vbCrLf &  
                "           Calling AccessTheWebAsync." & vbCrLf  
  
            Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()  
  
            ResultsTextBox.Text &= vbCrLf & "FOUR:  Back in StartButton_Click." & vbCrLf &  
                "           Task getLengthTask is started." & vbCrLf &  
                "           About to await getLengthTask -- no caller to return to." & vbCrLf  
  
            Dim contentLength As Integer = Await getLengthTask  
  
            ResultsTextBox.Text &= vbCrLf & "SIX:   Back in StartButton_Click." & vbCrLf &  
                "           Task getLengthTask is finished." & vbCrLf &  
                "           Result from AccessTheWebAsync is stored in contentLength." & vbCrLf &  
                "           About to display contentLength and exit." & vbCrLf  
  
            ResultsTextBox.Text &=  
                String.Format(vbCrLf & "Length of the downloaded string: {0}." & vbCrLf, contentLength)  
        End Sub  
  
        Async Function AccessTheWebAsync() As Task(Of Integer)  
  
            ResultsTextBox.Text &= vbCrLf & "TWO:   Entering AccessTheWebAsync."  
  
            ' Declare an HttpClient object.  
            Dim client As HttpClient = New HttpClient()  
  
            ResultsTextBox.Text &= vbCrLf & "           Calling HttpClient.GetStringAsync." & vbCrLf  
  
            ' GetStringAsync returns a Task(Of String).   
            Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")  
  
            ResultsTextBox.Text &= vbCrLf & "THREE: Back in AccessTheWebAsync." & vbCrLf &  
                "           Task getStringTask is started."  
  
            ' AccessTheWebAsync can continue to work until getStringTask is awaited.  
  
            ResultsTextBox.Text &=  
                vbCrLf & "           About to await getStringTask & return a Task(Of Integer) to StartButton_Click." & vbCrLf  
  
            ' Retrieve the website contents when task is complete.  
            Dim urlContents As String = Await getStringTask  
  
            ResultsTextBox.Text &= vbCrLf & "FIVE:  Back in AccessTheWebAsync." &  
                vbCrLf & "           Task getStringTask is complete." &  
                vbCrLf & "           Processing the return statement." &  
                vbCrLf & "           Exiting from AccessTheWebAsync." & vbCrLf  
  
            Return urlContents.Length  
        End Function  
  
    End Class  
    ```  
  
10. <span data-ttu-id="3ce0c-146">選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-146">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="3ce0c-147">應該出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-147">The following output should appear.</span></span>  
  
    ```  
    ONE:   Entering startButton_Click.  
               Calling AccessTheWebAsync.  
  
    TWO:   Entering AccessTheWebAsync.  
               Calling HttpClient.GetStringAsync.  
  
    THREE: Back in AccessTheWebAsync.  
               Task getStringTask is started.  
               About to await getStringTask & return a Task<int> to startButton_Click.  
  
    FOUR:  Back in startButton_Click.  
               Task getLengthTask is started.  
               About to await getLengthTask -- no caller to return to.  
  
    FIVE:  Back in AccessTheWebAsync.  
               Task getStringTask is complete.  
               Processing the return statement.  
               Exiting from AccessTheWebAsync.  
  
    SIX:   Back in startButton_Click.  
               Task getLengthTask is finished.  
               Result from AccessTheWebAsync is stored in contentLength.  
               About to display contentLength and exit.  
  
    Length of the downloaded string: 33946.  
    ```  
  
## <a name="trace-the-program"></a><span data-ttu-id="3ce0c-148">追蹤程式</span><span class="sxs-lookup"><span data-stu-id="3ce0c-148">Trace the Program</span></span>  
  
### <a name="steps-one-and-two"></a><span data-ttu-id="3ce0c-149">步驟一和二</span><span class="sxs-lookup"><span data-stu-id="3ce0c-149">Steps ONE and TWO</span></span>  
 <span data-ttu-id="3ce0c-150">前兩個顯示當 `startButton_Click` 呼叫 `AccessTheWebAsync`，以及 `AccessTheWebAsync` 呼叫非同步 <xref:System.Net.Http.HttpClient> 方法 <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> 時，追蹤路徑的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="3ce0c-151">下圖概述不同方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-151">The following image outlines the calls from method to method.</span></span>  
  
 <span data-ttu-id="3ce0c-152">![步驟一和二](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span><span class="sxs-lookup"><span data-stu-id="3ce0c-152">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>  
  
 <span data-ttu-id="3ce0c-153">`AccessTheWebAsync` 和 `client.GetStringAsync` 傳回的類型都是 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="3ce0c-154">針對 `AccessTheWebAsync`，TResult 是整數。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="3ce0c-155">針對 `GetStringAsync`，TResult 是字串。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="3ce0c-156">如需非同步方法傳回類型的詳細資訊，請參閱[非同步傳回型別 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-156">For more information about async method return types, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
 <span data-ttu-id="3ce0c-157">控制權返回呼叫端時，工作傳回非同步方法會傳回工作執行個體。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="3ce0c-158">在被呼叫的方法中發現 `Await` 運算子時，或被呼叫的方法結束時，控制權會從非同步方法返回其呼叫端。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-158">Control returns from an async method to its caller either when an `Await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="3ce0c-159">標上 "THREE" 到 "SIX" 的顯示行會追蹤處理程序的這個部分。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>  
  
### <a name="step-three"></a><span data-ttu-id="3ce0c-160">步驟三</span><span class="sxs-lookup"><span data-stu-id="3ce0c-160">Step THREE</span></span>  
 <span data-ttu-id="3ce0c-161">在 `AccessTheWebAsync` 中，呼叫非同步方法 <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> 以下載目標網頁的內容。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="3ce0c-162">傳回 `client.GetStringAsync` 時，控制項會從 `client.GetStringAsync` 返回 `AccessTheWebAsync`。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>  
  
 <span data-ttu-id="3ce0c-163">`client.GetStringAsync` 方法會傳回指派給 `AccessTheWebAsync` 中 `getStringTask` 變數的字串工作。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="3ce0c-164">範例程式中的下行示範 `client.GetStringAsync` 呼叫和指派。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>  
  
```vb  
Dim getStringTask As Task(Of String) = client.GetStringAsync("https://msdn.microsoft.com")  
```  
  
 <span data-ttu-id="3ce0c-165">您可以透過 `client.GetStringAsync` 將工作視為承諾，最後產生實際字串。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-165">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="3ce0c-166">同時，如果 `AccessTheWebAsync` 的工作未依存於來自 `client.GetStringAsync` 的承諾字串，則該工作可以在 `client.GetStringAsync` 等候時繼續進行。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-166">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="3ce0c-167">在此範例中，下列數行的輸出 (標上 "THREE”) 代表執行獨立工作的機會。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-167">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>  
  
```  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
```  
  
 <span data-ttu-id="3ce0c-168">下列陳述式會在等候 `getStringTask` 時暫止 `AccessTheWebAsync` 中的進度。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-168">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>  
  
```vb  
Dim urlContents As String = Await getStringTask  
```  
  
 <span data-ttu-id="3ce0c-169">下圖顯示從控制流程`client.GetStringAsync`到指派給`getStringTask`並從建立`getStringTask`Await 運算子的應用程式。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-169">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an Await operator.</span></span>  
  
 <span data-ttu-id="3ce0c-170">![步驟三](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span><span class="sxs-lookup"><span data-stu-id="3ce0c-170">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>  
  
 <span data-ttu-id="3ce0c-171">除非傳回 `client.GetStringAsync`，否則 await 運算式會暫止 `AccessTheWebAsync`。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-171">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="3ce0c-172">同時，控制項會返回 `AccessTheWebAsync` 的呼叫端 `startButton_Click`。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-172">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ce0c-173">一般而言，您會立即等候非同步方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-173">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="3ce0c-174">例如，下列指派可以取代可建立後等候 `getStringTask` 的先前程式碼：`Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`</span><span class="sxs-lookup"><span data-stu-id="3ce0c-174">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("https://msdn.microsoft.com")`</span></span>  
>   
>  <span data-ttu-id="3ce0c-175">在本主題中，稍後會套用 await 運算子，以容納透過程式標記控制流程的輸出行。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-175">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>  
  
### <a name="step-four"></a><span data-ttu-id="3ce0c-176">步驟四</span><span class="sxs-lookup"><span data-stu-id="3ce0c-176">Step FOUR</span></span>  
 <span data-ttu-id="3ce0c-177">`AccessTheWebAsync` 的已宣告傳回型別為 `Task(Of Integer)`。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-177">The declared return type of `AccessTheWebAsync` is `Task(Of Integer)`.</span></span> <span data-ttu-id="3ce0c-178">因此，暫止 `AccessTheWebAsync` 時，會將整數工作傳回給 `startButton_Click`。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-178">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="3ce0c-179">您應該了解所傳回的工作不是 `getStringTask`。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-179">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="3ce0c-180">傳回的工作是新整數工作，代表仍要在已暫止方法 `AccessTheWebAsync` 中執行的作業。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-180">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="3ce0c-181">這個工作是來自 `AccessTheWebAsync` 的承諾，可在工作完成時產生整數。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-181">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>  
  
 <span data-ttu-id="3ce0c-182">下列陳述式會將這個工作指派給 `getLengthTask` 變數。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-182">The following statement assigns this task to the `getLengthTask` variable.</span></span>  
  
```vb  
Dim getLengthTask As Task(Of Integer) = AccessTheWebAsync()  
```  
  
 <span data-ttu-id="3ce0c-183">如同 `AccessTheWebAsync`，除非等候非同步工作 (`getLengthTask`)，否則 `startButton_Click` 可以繼續執行未依存於該工作結果的工作。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-183">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="3ce0c-184">下列輸出行代表該工作。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-184">The following output lines represent that work.</span></span>  
  
```  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
```  
  
 <span data-ttu-id="3ce0c-185">等候 `getLengthTask` 時，會暫止 `startButton_Click` 中的進度。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-185">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="3ce0c-186">除非 `AccessTheWebAsync` 完成，否則下列指派陳述式會暫止 `startButton_Click`。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-186">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>  
  
```vb  
Dim contentLength As Integer = Await getLengthTask  
```  
  
 <span data-ttu-id="3ce0c-187">在下圖中，除非等候 `getLengthTask`，否則箭頭會顯示從 `AccessTheWebAsync` 中的 await 運算式到將值指派給 `getLengthTask` (後接 `startButton_Click` 中的正常處理) 的控制流程。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-187">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>  
  
 <span data-ttu-id="3ce0c-188">![步驟四](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span><span class="sxs-lookup"><span data-stu-id="3ce0c-188">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>  
  
### <a name="step-five"></a><span data-ttu-id="3ce0c-189">步驟五</span><span class="sxs-lookup"><span data-stu-id="3ce0c-189">Step FIVE</span></span>  
 <span data-ttu-id="3ce0c-190">`client.GetStringAsync` 指出完成時，會取消暫止 `AccessTheWebAsync` 中的處理，而且可以繼續略過 await 陳述式。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-190">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="3ce0c-191">下列數行的輸出代表繼續處理。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-191">The following lines of output represent the resumption of processing.</span></span>  
  
```  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
```  
  
 <span data-ttu-id="3ce0c-192">return 陳述式的運算元 `urlContents.Length` 儲存在 `AccessTheWebAsync` 所傳回的工作中。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-192">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="3ce0c-193">await 運算式會從 `startButton_Click` 中的 `getLengthTask` 擷取該值。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-193">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>  
  
 <span data-ttu-id="3ce0c-194">下圖顯示 `client.GetStringAsync` (和 `getStringTask`) 完成後的控制權轉移。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-194">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>  
  
 <span data-ttu-id="3ce0c-195">![步驟五](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span><span class="sxs-lookup"><span data-stu-id="3ce0c-195">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>  
  
 <span data-ttu-id="3ce0c-196">`AccessTheWebAsync` 會執行直到完成，而且控制項會返回正在等待完成的 `startButton_Click`。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-196">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>  
  
### <a name="step-six"></a><span data-ttu-id="3ce0c-197">步驟六</span><span class="sxs-lookup"><span data-stu-id="3ce0c-197">Step SIX</span></span>  
 <span data-ttu-id="3ce0c-198">`AccessTheWebAsync` 指出完成時，會繼續略過 `startButton_Async` 中 await 陳述式的處理。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-198">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="3ce0c-199">事實上，程式不需要再執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-199">In fact, the program has nothing more to do.</span></span>  
  
 <span data-ttu-id="3ce0c-200">下列數行的輸出代表在 `startButton_Async` 中繼續處理：</span><span class="sxs-lookup"><span data-stu-id="3ce0c-200">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>  
  
```  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
```  
  
 <span data-ttu-id="3ce0c-201">await 運算式會從 `getLengthTask` 擷取整數值，而整數值是 `AccessTheWebAsync` 中 return 陳述式的運算元。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-201">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="3ce0c-202">下列陳述式會將該值指派給 `contentLength` 變數。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-202">The following statement assigns that value to the `contentLength` variable.</span></span>  
  
```vb  
Dim contentLength As Integer = Await getLengthTask  
```  
  
 <span data-ttu-id="3ce0c-203">下圖顯示從 `AccessTheWebAsync` 到 `startButton_Click` 的控制項返回。</span><span class="sxs-lookup"><span data-stu-id="3ce0c-203">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>  
  
 <span data-ttu-id="3ce0c-204">![步驟六](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span><span class="sxs-lookup"><span data-stu-id="3ce0c-204">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ce0c-205">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ce0c-205">See Also</span></span>  
 [<span data-ttu-id="3ce0c-206">使用 Async 和 Await 進行非同步程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ce0c-206">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="3ce0c-207">非同步方法的傳回型別 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ce0c-207">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="3ce0c-208">逐步解說：使用 Async 和 Await 存取 Web (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ce0c-208">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 <span data-ttu-id="3ce0c-209">[Async Sample: Control Flow in Async Programs (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0) (非同步範例：非同步程式中的控制流程 (C# 和 Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="3ce0c-209">[Async Sample: Control Flow in Async Programs (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)</span></span>
