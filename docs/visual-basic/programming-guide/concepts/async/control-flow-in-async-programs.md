---
title: "控制流程中非同步程式 (Visual Basic) |Microsoft 文件"
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
ms.assetid: b0443af7-c586-4cb0-b476-742ae4098a96
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
ms.openlocfilehash: 15e02fbc023db9ae2f3ee9f40598faa7c9c027a0
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="control-flow-in-async-programs-visual-basic"></a><span data-ttu-id="7270e-102">非同步程式 (Visual Basic) 中的控制流程</span><span class="sxs-lookup"><span data-stu-id="7270e-102">Control Flow in Async Programs (Visual Basic)</span></span>
<span data-ttu-id="7270e-103">您可以撰寫並使用更輕鬆地維護非同步程式`Async`和`Await`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="7270e-103">You can write and maintain asynchronous programs more easily by using the `Async` and `Await` keywords.</span></span> <span data-ttu-id="7270e-104">不過，結果可能會讓您大吃一驚如果您不了解您的程式的運作方式。</span><span class="sxs-lookup"><span data-stu-id="7270e-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="7270e-105">透過簡單的非同步程式以顯示其中一種方法從控制項移到另一個與哪些資訊時的控制流程的每次傳送這個主題追蹤。</span><span class="sxs-lookup"><span data-stu-id="7270e-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7270e-106">`Async` 和 `Await` 關鍵字是在 Visual Studio 2012 中引入。</span><span class="sxs-lookup"><span data-stu-id="7270e-106">The `Async` and `Await` keywords were introduced in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="7270e-107">一般情況下，您將標記包含與非同步程式碼的方法[非同步](../../../../visual-basic/language-reference/modifiers/async.md)修飾詞。</span><span class="sxs-lookup"><span data-stu-id="7270e-107">In general, you mark methods that contain asynchronous code with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="7270e-108">在加上 async 修飾詞的方法，您可以使用[Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md)運算子來指定位置的方法會暫停等候呼叫的非同步處理序完成。</span><span class="sxs-lookup"><span data-stu-id="7270e-108">In a method that's marked with an async modifier, you can use an [Await (Visual Basic)](../../../../visual-basic/language-reference/operators/await-operator.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="7270e-109">如需詳細資訊，請參閱[使用 Async 和 Await (Visual Basic) 進行非同步程式設計](../../../../visual-basic/programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="7270e-109">For more information, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="7270e-110">下列範例會使用非同步方法，以指定的網站，做為字串的內容下載並顯示字串的長度。</span><span class="sxs-lookup"><span data-stu-id="7270e-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="7270e-111">這個範例包含下列兩種方法。</span><span class="sxs-lookup"><span data-stu-id="7270e-111">The example contains the following two methods.</span></span>  
  
-   <span data-ttu-id="7270e-112">`startButton_Click`其呼叫`AccessTheWebAsync`，並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="7270e-112">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>  
  
-   <span data-ttu-id="7270e-113">`AccessTheWebAsync`因為它會下載網站，以做為字串的內容，並傳回字串的長度。</span><span class="sxs-lookup"><span data-stu-id="7270e-113">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="7270e-114">`AccessTheWebAsync`使用非同步<xref:System.Net.Http.HttpClient>方法， <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>、 內容下載。</xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> </xref:System.Net.Http.HttpClient></span><span class="sxs-lookup"><span data-stu-id="7270e-114">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>  
  
 <span data-ttu-id="7270e-115">編號線出現在整個程式，協助您了解如何在程式執行，並且說明會標示每個點會發生什麼情況的策略點的顯示。</span><span class="sxs-lookup"><span data-stu-id="7270e-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="7270e-116">顯示程式碼行標示為 「 一 」 到 「 六個。 」</span><span class="sxs-lookup"><span data-stu-id="7270e-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="7270e-117">標籤表示程式達到這行程式碼的順序。</span><span class="sxs-lookup"><span data-stu-id="7270e-117">The labels represent the order in which the program reaches these lines of code.</span></span>  
  
 <span data-ttu-id="7270e-118">下列程式碼顯示大綱的程式。</span><span class="sxs-lookup"><span data-stu-id="7270e-118">The following code shows an outline of the program.</span></span>  
  
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
            client.GetStringAsync("http://msdn.microsoft.com")  
  
        ' THREE  
        Dim urlContents As String = Await getStringTask  
  
        ' FIVE  
        Return urlContents.Length  
    End Function  
  
End Class  
  
```  
  
 <span data-ttu-id="7270e-119">每個標記的位置，「 一 」 到 「&6;，"會顯示程式的目前狀態的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="7270e-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="7270e-120">會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="7270e-120">The following output is produced.</span></span>  
  
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
  
## <a name="set-up-the-program"></a><span data-ttu-id="7270e-121">將程式設定</span><span class="sxs-lookup"><span data-stu-id="7270e-121">Set Up the Program</span></span>  
 <span data-ttu-id="7270e-122">您可以從 MSDN 下載本主題所使用的程式碼，或它可以自行建立。</span><span class="sxs-lookup"><span data-stu-id="7270e-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7270e-123">若要執行此範例，您必須擁有 Visual Studio 2012 或較新和.NET Framework 4.5 或更新版本安裝在電腦上。</span><span class="sxs-lookup"><span data-stu-id="7270e-123">To run the example, you must have Visual Studio 2012 or newer and  the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
### <a name="download-the-program"></a><span data-ttu-id="7270e-124">下載程式</span><span class="sxs-lookup"><span data-stu-id="7270e-124">Download the Program</span></span>  
 <span data-ttu-id="7270e-125">您可以下載的應用程式的相關主題的[非同步範例︰ 非同步程式中的控制流程](http://go.microsoft.com/fwlink/?LinkId=255285)。</span><span class="sxs-lookup"><span data-stu-id="7270e-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](http://go.microsoft.com/fwlink/?LinkId=255285).</span></span> <span data-ttu-id="7270e-126">下列步驟會開啟並執行程式。</span><span class="sxs-lookup"><span data-stu-id="7270e-126">The following steps open and run the program.</span></span>  
  
1.  <span data-ttu-id="7270e-127">解壓縮下載的檔案，然後再啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="7270e-127">Unzip the downloaded file, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="7270e-128">在功能表列上，依序選擇 [檔案] ****、[開啟舊檔] ****及 [專案/方案] ****。</span><span class="sxs-lookup"><span data-stu-id="7270e-128">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="7270e-129">瀏覽至解壓縮的範例程式碼所在的資料夾，開啟方案 (.sln) 檔，然後選擇 F5 鍵以建置並執行專案。</span><span class="sxs-lookup"><span data-stu-id="7270e-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the F5 key to build and run the project.</span></span>  
  
### <a name="build-the-program-yourself"></a><span data-ttu-id="7270e-130">自行建立程式</span><span class="sxs-lookup"><span data-stu-id="7270e-130">Build the Program Yourself</span></span>  
 <span data-ttu-id="7270e-131">下列 Windows Presentation Foundation (WPF) 專案包含本主題的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="7270e-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>  
  
 <span data-ttu-id="7270e-132">若要執行專案，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="7270e-132">To run the project, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="7270e-133">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="7270e-133">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="7270e-134">在功能表列上，選擇 [檔案] ****、[新增] ****、[專案] ****。</span><span class="sxs-lookup"><span data-stu-id="7270e-134">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="7270e-135">[ **新增專案** ] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="7270e-135">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="7270e-136">在**已安裝的範本** 窗格中，選擇  **Visual Basic**，然後選擇  **WPF 應用程式**從專案類型清單。</span><span class="sxs-lookup"><span data-stu-id="7270e-136">In the **Installed Templates** pane, choose **Visual Basic**, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="7270e-137">輸入`AsyncTracer`做為專案名稱，然後選擇 [**確定**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7270e-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="7270e-138">新的專案會出現在**方案總管 中**。</span><span class="sxs-lookup"><span data-stu-id="7270e-138">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="7270e-139">在 Visual Studio 程式碼編輯器中，選擇 [ **MainWindow.xaml** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7270e-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="7270e-140">如果看不到索引標籤上，開啟捷徑功能表中的 mainwindow.xaml**方案總管] 中**，然後選擇 [**檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="7270e-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6.  <span data-ttu-id="7270e-141">在**XAML** MainWindow.xaml 的檢視，請以下列程式碼取代程式碼。</span><span class="sxs-lookup"><span data-stu-id="7270e-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
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
  
     <span data-ttu-id="7270e-142">包含文字方塊和按鈕的簡單視窗會出現在**設計**MainWindow.xaml 的檢視。</span><span class="sxs-lookup"><span data-stu-id="7270e-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
7.  <span data-ttu-id="7270e-143">加入<xref:System.Net.Http>.</xref:System.Net.Http>的參考</span><span class="sxs-lookup"><span data-stu-id="7270e-143">Add a reference for <xref:System.Net.Http>.</span></span>  
  
8.  <span data-ttu-id="7270e-144">在**方案總管] 中**MainWindow.xaml.vb，開啟捷徑功能表，然後選擇 [**檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="7270e-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
9. <span data-ttu-id="7270e-145">在 MainWindow.xaml.vb，取代下列程式碼中的程式碼。</span><span class="sxs-lookup"><span data-stu-id="7270e-145">In MainWindow.xaml.vb , replace the code with the following code.</span></span>  
  
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
            Dim getStringTask As Task(Of String) = client.GetStringAsync("http://msdn.microsoft.com")  
  
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
  
10. <span data-ttu-id="7270e-146">選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7270e-146">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="7270e-147">應該出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="7270e-147">The following output should appear.</span></span>  
  
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
  
## <a name="trace-the-program"></a><span data-ttu-id="7270e-148">追蹤程式</span><span class="sxs-lookup"><span data-stu-id="7270e-148">Trace the Program</span></span>  
  
### <a name="steps-one-and-two"></a><span data-ttu-id="7270e-149">步驟一和二</span><span class="sxs-lookup"><span data-stu-id="7270e-149">Steps ONE and TWO</span></span>  
 <span data-ttu-id="7270e-150">前兩個顯示線條追蹤做為路徑`startButton_Click`呼叫`AccessTheWebAsync`，和`AccessTheWebAsync`呼叫非同步<xref:System.Net.Http.HttpClient>方法<xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> </xref:System.Net.Http.HttpClient></span><span class="sxs-lookup"><span data-stu-id="7270e-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="7270e-151">下圖概述在方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="7270e-151">The following image outlines the calls from method to method.</span></span>  
  
 <span data-ttu-id="7270e-152">![步驟&1; 和&2;](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace ONETWO")</span><span class="sxs-lookup"><span data-stu-id="7270e-152">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>  
  
 <span data-ttu-id="7270e-153">兩者的傳回型別`AccessTheWebAsync`和`client.GetStringAsync`為<xref:System.Threading.Tasks.Task%601>.</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="7270e-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="7270e-154">如`AccessTheWebAsync`，TResult 是一個整數。</span><span class="sxs-lookup"><span data-stu-id="7270e-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="7270e-155">如`GetStringAsync`，TResult 是字串。</span><span class="sxs-lookup"><span data-stu-id="7270e-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="7270e-156">如需非同步方法的傳回類型的詳細資訊，請參閱[非同步傳回類型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="7270e-156">For more information about async method return types, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
 <span data-ttu-id="7270e-157">切換回呼叫端的控制時的工作傳回非同步方法會傳回工作執行個體。</span><span class="sxs-lookup"><span data-stu-id="7270e-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="7270e-158">控制從非同步方法傳回至呼叫端時`Await`運算子中被呼叫的方法或被呼叫的方法結束時出現。</span><span class="sxs-lookup"><span data-stu-id="7270e-158">Control returns from an async method to its caller either when an `Await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="7270e-159">顯示程式碼行標記為"3"透過 「&6; 」 會追蹤此程序的一部分。</span><span class="sxs-lookup"><span data-stu-id="7270e-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>  
  
### <a name="step-three"></a><span data-ttu-id="7270e-160">步驟三</span><span class="sxs-lookup"><span data-stu-id="7270e-160">Step THREE</span></span>  
 <span data-ttu-id="7270e-161">在`AccessTheWebAsync`，非同步方法<xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>稱為目標網頁的內容下載。</xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29></span><span class="sxs-lookup"><span data-stu-id="7270e-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="7270e-162">控制權會傳回從`client.GetStringAsync`至`AccessTheWebAsync`時`client.GetStringAsync`傳回。</span><span class="sxs-lookup"><span data-stu-id="7270e-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>  
  
 <span data-ttu-id="7270e-163">`client.GetStringAsync`方法傳回的字串指派給工作`getStringTask`變數中`AccessTheWebAsync`。</span><span class="sxs-lookup"><span data-stu-id="7270e-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="7270e-164">下列行中的範例程式示範如何呼叫`client.GetStringAsync`和指派。</span><span class="sxs-lookup"><span data-stu-id="7270e-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>  
  
<span data-ttu-id="7270e-165"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="7270e-165"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="7270e-166">您可以將工作的一項承諾所視為`client.GetStringAsync`最後會產生實際的字串。</span><span class="sxs-lookup"><span data-stu-id="7270e-166">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="7270e-167">在此同時，如果`AccessTheWebAsync`有工作来做的承諾字串不依賴`client.GetStringAsync`，可以繼續工作時`client.GetStringAsync`等待。</span><span class="sxs-lookup"><span data-stu-id="7270e-167">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="7270e-168">在範例中，下列幾行的輸出，會標示為 「&3; 」，代表有機會進行獨立的工作</span><span class="sxs-lookup"><span data-stu-id="7270e-168">In the example, the following lines of output, which are labeled "THREE,” represent the opportunity to do independent work</span></span>  
  
<span data-ttu-id="7270e-169"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="7270e-169"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="7270e-170">下列陳述式會暫止中的進度`AccessTheWebAsync`時`getStringTask`會等候。</span><span class="sxs-lookup"><span data-stu-id="7270e-170">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>  
  
<span data-ttu-id="7270e-171"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="7270e-171"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="7270e-172">下圖顯示從控制流程`client.GetStringAsync`要指派給`getStringTask`和從建立`getStringTask`Await 運算子的應用程式。</span><span class="sxs-lookup"><span data-stu-id="7270e-172">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an Await operator.</span></span>  
  
 <span data-ttu-id="7270e-173">![步驟三](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace 三")</span><span class="sxs-lookup"><span data-stu-id="7270e-173">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>  
  
 <span data-ttu-id="7270e-174">Await 運算式會暫止`AccessTheWebAsync`直到`client.GetStringAsync`傳回。</span><span class="sxs-lookup"><span data-stu-id="7270e-174">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="7270e-175">在此同時，控制項會返回至呼叫端的`AccessTheWebAsync`， `startButton_Click`。</span><span class="sxs-lookup"><span data-stu-id="7270e-175">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7270e-176">一般而言，您呼叫非同步方法立即等候。</span><span class="sxs-lookup"><span data-stu-id="7270e-176">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="7270e-177">例如，下列指派可以取代先前的程式碼會建立並再等候`getStringTask`:`Dim urlContents As String = Await client.GetStringAsync("http://msdn.microsoft.com")`</span><span class="sxs-lookup"><span data-stu-id="7270e-177">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `Dim urlContents As String = Await client.GetStringAsync("http://msdn.microsoft.com")`</span></span>  
>   
>  <span data-ttu-id="7270e-178">本主題中，await 運算子會更新版本才能容納標記透過計劃的控制流程的輸出行套用。</span><span class="sxs-lookup"><span data-stu-id="7270e-178">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>  
  
### <a name="step-four"></a><span data-ttu-id="7270e-179">步驟四</span><span class="sxs-lookup"><span data-stu-id="7270e-179">Step FOUR</span></span>  
 <span data-ttu-id="7270e-180">宣告的傳回型別`AccessTheWebAsync`是`Task(Of Integer)`。</span><span class="sxs-lookup"><span data-stu-id="7270e-180">The declared return type of `AccessTheWebAsync` is `Task(Of Integer)`.</span></span> <span data-ttu-id="7270e-181">因此，當`AccessTheWebAsync`是暫止，它會傳回工作的整數到`startButton_Click`。</span><span class="sxs-lookup"><span data-stu-id="7270e-181">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="7270e-182">您應該了解傳回的工作不是`getStringTask`。</span><span class="sxs-lookup"><span data-stu-id="7270e-182">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="7270e-183">傳回的工作是一項新工作的整數，表示還保留在已暫停方法中， `AccessTheWebAsync`。</span><span class="sxs-lookup"><span data-stu-id="7270e-183">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="7270e-184">工作可保證一定會從`AccessTheWebAsync`工作完成時產生的整數。</span><span class="sxs-lookup"><span data-stu-id="7270e-184">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>  
  
 <span data-ttu-id="7270e-185">下列陳述式會指派此工作以`getLengthTask`變數。</span><span class="sxs-lookup"><span data-stu-id="7270e-185">The following statement assigns this task to the `getLengthTask` variable.</span></span>  
  
<span data-ttu-id="7270e-186"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="7270e-186"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="7270e-187">如同`AccessTheWebAsync`，`startButton_Click`非同步工作的結果不相依的工作可以繼續 (`getLengthTask`) 之前會等候工作。</span><span class="sxs-lookup"><span data-stu-id="7270e-187">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="7270e-188">下列的輸出行代表該工作。</span><span class="sxs-lookup"><span data-stu-id="7270e-188">The following output lines represent that work.</span></span>  
  
<span data-ttu-id="7270e-189"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="7270e-189"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="7270e-190">在`startButton_Click`時暫止`getLengthTask`會等候。</span><span class="sxs-lookup"><span data-stu-id="7270e-190">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="7270e-191">下列設定陳述式會暫停`startButton_Click`直到`AccessTheWebAsync`已完成。</span><span class="sxs-lookup"><span data-stu-id="7270e-191">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>  
  
<span data-ttu-id="7270e-192"><CodeContentPlaceHolder>10</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="7270e-192"><CodeContentPlaceHolder>10</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="7270e-193">在下圖中，箭頭會顯示從 await 運算式中的控制流程`AccessTheWebAsync`之值的指派`getLengthTask`，後面接著在正常處理`startButton_Click`直到`getLengthTask`會等候。</span><span class="sxs-lookup"><span data-stu-id="7270e-193">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>  
  
 <span data-ttu-id="7270e-194">![步驟四](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace 四")</span><span class="sxs-lookup"><span data-stu-id="7270e-194">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>  
  
### <a name="step-five"></a><span data-ttu-id="7270e-195">步驟五</span><span class="sxs-lookup"><span data-stu-id="7270e-195">Step FIVE</span></span>  
 <span data-ttu-id="7270e-196">當`client.GetStringAsync`訊號已完成作業，以處理`AccessTheWebAsync`發行從擱置，而且可以繼續過去的 await 陳述式。</span><span class="sxs-lookup"><span data-stu-id="7270e-196">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="7270e-197">下列程式行輸出表示繼續處理。</span><span class="sxs-lookup"><span data-stu-id="7270e-197">The following lines of output represent the resumption of processing.</span></span>  
  
<span data-ttu-id="7270e-198"><CodeContentPlaceHolder>11</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="7270e-198"><CodeContentPlaceHolder>11</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="7270e-199">Return 陳述式中，運算元`urlContents.Length`，儲存在工作的`AccessTheWebAsync`傳回。</span><span class="sxs-lookup"><span data-stu-id="7270e-199">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="7270e-200">Await 運算式會擷取此值`getLengthTask`中`startButton_Click`。</span><span class="sxs-lookup"><span data-stu-id="7270e-200">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>  
  
 <span data-ttu-id="7270e-201">下圖顯示的控制項之後傳送`client.GetStringAsync`(和`getStringTask`) 都已完成。</span><span class="sxs-lookup"><span data-stu-id="7270e-201">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>  
  
 <span data-ttu-id="7270e-202">![步驟五](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace 五")</span><span class="sxs-lookup"><span data-stu-id="7270e-202">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>  
  
 <span data-ttu-id="7270e-203">`AccessTheWebAsync`執行到完成和控制項傳回給`startButton_Click`，它正在等待完成。</span><span class="sxs-lookup"><span data-stu-id="7270e-203">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>  
  
### <a name="step-six"></a><span data-ttu-id="7270e-204">步驟六</span><span class="sxs-lookup"><span data-stu-id="7270e-204">Step SIX</span></span>  
 <span data-ttu-id="7270e-205">當`AccessTheWebAsync`await 陳述式中可以繼續完成處理的訊號`startButton_Async`。</span><span class="sxs-lookup"><span data-stu-id="7270e-205">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="7270e-206">事實上，程式有多個不需採取行動。</span><span class="sxs-lookup"><span data-stu-id="7270e-206">In fact, the program has nothing more to do.</span></span>  
  
 <span data-ttu-id="7270e-207">下列程式行輸出代表繼續中處理`startButton_Async`:</span><span class="sxs-lookup"><span data-stu-id="7270e-207">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>  
  
<span data-ttu-id="7270e-208"><CodeContentPlaceHolder>12</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="7270e-208"><CodeContentPlaceHolder>12</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="7270e-209">Await 運算式擷取`getLengthTask`是 return 陳述式中運算元的整數值`AccessTheWebAsync`。</span><span class="sxs-lookup"><span data-stu-id="7270e-209">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="7270e-210">下列陳述式，將值指派至`contentLength`變數。</span><span class="sxs-lookup"><span data-stu-id="7270e-210">The following statement assigns that value to the `contentLength` variable.</span></span>  
  
<span data-ttu-id="7270e-211"><CodeContentPlaceHolder>13</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="7270e-211"><CodeContentPlaceHolder>13</CodeContentPlaceHolder></span></span>  
 <span data-ttu-id="7270e-212">下圖顯示從控制項傳回`AccessTheWebAsync`到`startButton_Click`。</span><span class="sxs-lookup"><span data-stu-id="7270e-212">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>  
  
 <span data-ttu-id="7270e-213">![步驟六](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace 六")</span><span class="sxs-lookup"><span data-stu-id="7270e-213">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7270e-214">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7270e-214">See Also</span></span>  
 <span data-ttu-id="7270e-215">[非同步程式設計使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="7270e-215">[Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="7270e-216"> [非同步方法的傳回類型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span><span class="sxs-lookup"><span data-stu-id="7270e-216"> [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span></span>  
<span data-ttu-id="7270e-217"> [逐步解說︰ 存取 Web 使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span><span class="sxs-lookup"><span data-stu-id="7270e-217"> [Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md) </span></span>  
<span data-ttu-id="7270e-218"> [非同步範例︰ 非同步程式 （C# 和 Visual Basic） 中的控制流程](http://go.microsoft.com/fwlink/?LinkId=255285)</span><span class="sxs-lookup"><span data-stu-id="7270e-218"> [Async Sample: Control Flow in Async Programs (C# and Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255285)</span></span>
