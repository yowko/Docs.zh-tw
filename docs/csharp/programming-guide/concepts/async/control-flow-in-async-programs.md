---
title: "非同步程式中的控制流程 (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: fc92b08b-fe1d-4d07-84ab-5192fafe06bb
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7a13763b2eeec93e7db7ca770c4d52b4a2ba768c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="control-flow-in-async-programs-c"></a><span data-ttu-id="21ba3-102">非同步程式中的控制流程 (C#)</span><span class="sxs-lookup"><span data-stu-id="21ba3-102">Control Flow in Async Programs (C#)</span></span>
<span data-ttu-id="21ba3-103">您可以使用 `async` 和 `await` 關鍵字更輕鬆地撰寫和維護非同步程式。</span><span class="sxs-lookup"><span data-stu-id="21ba3-103">You can write and maintain asynchronous programs more easily by using the `async` and `await` keywords.</span></span> <span data-ttu-id="21ba3-104">不過，如果您不了解程式的運作方式，則結果可能會讓您大吃一驚。</span><span class="sxs-lookup"><span data-stu-id="21ba3-104">However, the results might surprise you if you don't understand how your program operates.</span></span> <span data-ttu-id="21ba3-105">本主題透過簡單非同步程式來追蹤控制流程，以顯示控制何時從某個方法移至另一個方法以及每次傳輸的資訊。</span><span class="sxs-lookup"><span data-stu-id="21ba3-105">This topic traces the flow of control through a simple async program to show you when control moves from one method to another and what information is transferred each time.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21ba3-106">`async` 和 `await` 關鍵字是在 Visual Studio 2012 中引入。</span><span class="sxs-lookup"><span data-stu-id="21ba3-106">The `async` and `await` keywords were introduced in Visual Studio 2012.</span></span>  
  
 <span data-ttu-id="21ba3-107">一般而言，您可以使用 [async (C#)](../../../../csharp/language-reference/keywords/async.md) 修飾詞來標記包含非同步程式碼的方法。</span><span class="sxs-lookup"><span data-stu-id="21ba3-107">In general, you mark methods that contain asynchronous code with the [async (C#)](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="21ba3-108">在使用 async 修飾詞所標記的方法中，您可以使用 [await (C#)](../../../../csharp/language-reference/keywords/await.md) 運算子來指定方法會暫停以等候被呼叫的非同步處理程序完成的位置。</span><span class="sxs-lookup"><span data-stu-id="21ba3-108">In a method that's marked with an async modifier, you can use an [await (C#)](../../../../csharp/language-reference/keywords/await.md) operator to specify where the method pauses to wait for a called asynchronous process to complete.</span></span> <span data-ttu-id="21ba3-109">如需詳細資訊，請參閱[使用 async 和 await 進行非同步程式設計 (C#)](../../../../csharp/programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="21ba3-109">For more information, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="21ba3-110">下列範例會使用非同步方法，將所指定網站的內容下載為字串，以及顯示字串的長度。</span><span class="sxs-lookup"><span data-stu-id="21ba3-110">The following example uses async methods to download the contents of a specified website as a string and to display the length of the string.</span></span> <span data-ttu-id="21ba3-111">這個範例包含下列兩個方法。</span><span class="sxs-lookup"><span data-stu-id="21ba3-111">The example contains the following two methods.</span></span>  
  
-   <span data-ttu-id="21ba3-112">`startButton_Click`，其呼叫 `AccessTheWebAsync` 並顯示結果。</span><span class="sxs-lookup"><span data-stu-id="21ba3-112">`startButton_Click`, which calls `AccessTheWebAsync` and displays the result.</span></span>  
  
-   <span data-ttu-id="21ba3-113">`AccessTheWebAsync`，會將網站的內容下載為字串，並傳回字串的長度。</span><span class="sxs-lookup"><span data-stu-id="21ba3-113">`AccessTheWebAsync`, which downloads the contents of a website as a string and returns the length of the string.</span></span> <span data-ttu-id="21ba3-114">`AccessTheWebAsync`使用非同步的 <xref:System.Net.Http.HttpClient> 方法 <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> 來下載內容。</span><span class="sxs-lookup"><span data-stu-id="21ba3-114">`AccessTheWebAsync` uses an asynchronous <xref:System.Net.Http.HttpClient> method, <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>, to download the contents.</span></span>  
  
 <span data-ttu-id="21ba3-115">編號的顯示行會出現在程式中的策略點，協助您了解程式的執行方式，以及說明每個標記點所發生的情況。</span><span class="sxs-lookup"><span data-stu-id="21ba3-115">Numbered display lines appear at strategic points throughout the program to help you understand how the program runs and to explain what happens at each point that is marked.</span></span> <span data-ttu-id="21ba3-116">顯示行會標上 "ONE" 到 "SIX"。</span><span class="sxs-lookup"><span data-stu-id="21ba3-116">The display lines are labeled "ONE" through "SIX."</span></span> <span data-ttu-id="21ba3-117">標籤代表程式到達這些程式碼行的順序。</span><span class="sxs-lookup"><span data-stu-id="21ba3-117">The labels represent the order in which the program reaches these lines of code.</span></span>  
  
 <span data-ttu-id="21ba3-118">下列程式碼示範程式的大綱。</span><span class="sxs-lookup"><span data-stu-id="21ba3-118">The following code shows an outline of the program.</span></span>  
  
```csharp  
public partial class MainWindow : Window  
{  
    // . . .  
    private async void startButton_Click(object sender, RoutedEventArgs e)  
    {  
        // ONE  
        Task<int> getLengthTask = AccessTheWebAsync();  
  
        // FOUR  
        int contentLength = await getLengthTask;  
  
        // SIX  
        resultsTextBox.Text +=  
            String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
    }  
  
    async Task<int> AccessTheWebAsync()  
    {  
        // TWO  
        HttpClient client = new HttpClient();  
        Task<string> getStringTask =  
            client.GetStringAsync("http://msdn.microsoft.com");  
  
        // THREE                   
        string urlContents = await getStringTask;  
  
        // FIVE  
        return urlContents.Length;  
    }  
}  
```  
  
 <span data-ttu-id="21ba3-119">每個標記位置 "ONE" 到 "SIX" 都會顯示程式目前狀態的資訊。</span><span class="sxs-lookup"><span data-stu-id="21ba3-119">Each of the labeled locations, "ONE" through "SIX," displays information about the current state of the program.</span></span> <span data-ttu-id="21ba3-120">會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="21ba3-120">The following output is produced.</span></span>  
  
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
  
## <a name="set-up-the-program"></a><span data-ttu-id="21ba3-121">設定程式</span><span class="sxs-lookup"><span data-stu-id="21ba3-121">Set Up the Program</span></span>  
 <span data-ttu-id="21ba3-122">您可以從 MSDN 下載本主題所使用的程式碼，也可以自行建置。</span><span class="sxs-lookup"><span data-stu-id="21ba3-122">You can download the code that this topic uses from MSDN, or you can build it yourself.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21ba3-123">若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="21ba3-123">To run the example, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>  
  
### <a name="download-the-program"></a><span data-ttu-id="21ba3-124">下載程式</span><span class="sxs-lookup"><span data-stu-id="21ba3-124">Download the Program</span></span>  
 <span data-ttu-id="21ba3-125">您可以從 [Async Sample: Control Flow in Async Programs](http://go.microsoft.com/fwlink/?LinkId=255285) (非同步範例：非同步程式中的控制流程) 下載本主題的應用程式。</span><span class="sxs-lookup"><span data-stu-id="21ba3-125">You can download the application for this topic from [Async Sample: Control Flow in Async Programs](http://go.microsoft.com/fwlink/?LinkId=255285).</span></span> <span data-ttu-id="21ba3-126">下列步驟會開啟和執行程式。</span><span class="sxs-lookup"><span data-stu-id="21ba3-126">The following steps open and run the program.</span></span>  
  
1.  <span data-ttu-id="21ba3-127">解壓縮下載的檔案，然後啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="21ba3-127">Unzip the downloaded file, and then start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="21ba3-128">在功能表列上，依序選擇 [檔案] 、[開啟舊檔] 及 [專案/方案] 。</span><span class="sxs-lookup"><span data-stu-id="21ba3-128">On the menu bar, choose **File**, **Open**, **Project/Solution**.</span></span>  
  
3.  <span data-ttu-id="21ba3-129">巡覽至保存解壓縮之範例程式碼的資料夾，並開啟方案 (.sln) 檔案，然後選擇 F5 鍵來建置和執行專案。</span><span class="sxs-lookup"><span data-stu-id="21ba3-129">Navigate to the folder that holds the unzipped sample code, open the solution (.sln) file, and then choose the F5 key to build and run the project.</span></span>  
  
### <a name="build-the-program-yourself"></a><span data-ttu-id="21ba3-130">自行建立程式</span><span class="sxs-lookup"><span data-stu-id="21ba3-130">Build the Program Yourself</span></span>  
 <span data-ttu-id="21ba3-131">下列 Windows Presentation Foundation (WPF) 專案包含本主題的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="21ba3-131">The following Windows Presentation Foundation (WPF) project contains the code example for this topic.</span></span>  
  
 <span data-ttu-id="21ba3-132">若要執行專案，請執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="21ba3-132">To run the project, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="21ba3-133">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="21ba3-133">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="21ba3-134">在功能表列上，選擇 [檔案] 、[新增] 、[專案] 。</span><span class="sxs-lookup"><span data-stu-id="21ba3-134">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="21ba3-135">[ **新增專案** ] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="21ba3-135">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="21ba3-136">在 [已安裝的範本] 窗格中，選擇 [Visual C#]，然後從專案類型清單中選擇 [WPF 應用程式]。</span><span class="sxs-lookup"><span data-stu-id="21ba3-136">In the **Installed Templates** pane, choose **Visual C#**, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="21ba3-137">輸入 `AsyncTracer` 作為專案的名稱，然後選擇 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="21ba3-137">Enter `AsyncTracer` as the name of the project, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="21ba3-138">新的專案隨即出現在方案總管中。</span><span class="sxs-lookup"><span data-stu-id="21ba3-138">The new project appears in **Solution Explorer**.</span></span>  
  
5.  <span data-ttu-id="21ba3-139">在 Visual Studio 程式碼編輯器中，選擇 [ **MainWindow.xaml** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="21ba3-139">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
     <span data-ttu-id="21ba3-140">如未顯示索引標籤，請在方案總管中開啟 MainWindow.xaml 的捷徑功能表，然後選擇 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="21ba3-140">If the tab isn’t visible, open the shortcut menu for MainWindow.xaml in **Solution Explorer**, and then choose **View Code**.</span></span>  
  
6.  <span data-ttu-id="21ba3-141">在 MainWindow.xaml 的 [XAML] 檢視中，以下列程式碼取代程式碼。</span><span class="sxs-lookup"><span data-stu-id="21ba3-141">In the **XAML** view of MainWindow.xaml, replace the code with the following code.</span></span>  
  
    ```csharp  
    <Window  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            xmlns:d="http://schemas.microsoft.com/expression/blend/2008" xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006" mc:Ignorable="d" x:Class="AsyncTracer.MainWindow"  
            Title="Control Flow Trace" Height="350" Width="592">  
        <Grid>  
            <Button x:Name="startButton" Content="Start  
    " HorizontalAlignment="Left" Margin="250,10,0,0" VerticalAlignment="Top" Width="75" Height="24"  Click="startButton_Click" d:LayoutOverrides="GridBox"/>  
            <TextBox x:Name="resultsTextBox" HorizontalAlignment="Left" TextWrapping="Wrap" VerticalAlignment="Bottom" Width="576" Height="265" FontFamily="Lucida Console" FontSize="10" VerticalScrollBarVisibility="Visible" Grid.ColumnSpan="3"/>  
        </Grid>  
    </Window>  
    ```  
  
     <span data-ttu-id="21ba3-142">包含文字方塊和按鈕的簡易視窗會出現在 MainWindow.xaml 的 [設計] 檢視中。</span><span class="sxs-lookup"><span data-stu-id="21ba3-142">A simple window that contains a text box and a button appears in the **Design** view of MainWindow.xaml.</span></span>  
  
7.  <span data-ttu-id="21ba3-143">加入 <xref:System.Net.Http> 的參考。</span><span class="sxs-lookup"><span data-stu-id="21ba3-143">Add a reference for <xref:System.Net.Http>.</span></span>  
  
8.  <span data-ttu-id="21ba3-144">在方案總管中開啟 MainWindow.xaml.cs 的捷徑功能表，然後選擇 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="21ba3-144">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>  
  
9. <span data-ttu-id="21ba3-145">在 MainWindow.xaml.cs 中，將程式碼取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="21ba3-145">In MainWindow.xaml.cs, replace the code with the following code.</span></span>  
  
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
  
    // Add a using directive and a reference for System.Net.Http;  
    using System.Net.Http;  
  
    namespace AsyncTracer  
    {  
        public partial class MainWindow : Window  
        {  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
  
            private async void startButton_Click(object sender, RoutedEventArgs e)  
            {  
                // The display lines in the example lead you through the control shifts.  
                resultsTextBox.Text += "ONE:   Entering startButton_Click.\r\n" +  
                    "           Calling AccessTheWebAsync.\r\n";  
  
                Task<int> getLengthTask = AccessTheWebAsync();  
  
                resultsTextBox.Text += "\r\nFOUR:  Back in startButton_Click.\r\n" +  
                    "           Task getLengthTask is started.\r\n" +  
                    "           About to await getLengthTask -- no caller to return to.\r\n";  
  
                int contentLength = await getLengthTask;  
  
                resultsTextBox.Text += "\r\nSIX:   Back in startButton_Click.\r\n" +  
                    "           Task getLengthTask is finished.\r\n" +  
                    "           Result from AccessTheWebAsync is stored in contentLength.\r\n" +  
                    "           About to display contentLength and exit.\r\n";  
  
                resultsTextBox.Text +=  
                    String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
            }  
  
            async Task<int> AccessTheWebAsync()  
            {  
                resultsTextBox.Text += "\r\nTWO:   Entering AccessTheWebAsync.";  
  
                // Declare an HttpClient object.  
                HttpClient client = new HttpClient();  
  
                resultsTextBox.Text += "\r\n           Calling HttpClient.GetStringAsync.\r\n";  
  
                // GetStringAsync returns a Task<string>.   
                Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
  
                resultsTextBox.Text += "\r\nTHREE: Back in AccessTheWebAsync.\r\n" +  
                    "           Task getStringTask is started.";  
  
                // AccessTheWebAsync can continue to work until getStringTask is awaited.  
  
                resultsTextBox.Text +=  
                    "\r\n           About to await getStringTask and return a Task<int> to startButton_Click.\r\n";  
  
                // Retrieve the website contents when task is complete.  
                string urlContents = await getStringTask;  
  
                resultsTextBox.Text += "\r\nFIVE:  Back in AccessTheWebAsync." +  
                    "\r\n           Task getStringTask is complete." +  
                    "\r\n           Processing the return statement." +  
                    "\r\n           Exiting from AccessTheWebAsync.\r\n";  
  
                return urlContents.Length;  
            }  
        }  
    }  
    ```  
  
10. <span data-ttu-id="21ba3-146">選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="21ba3-146">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="21ba3-147">應該出現下列輸出。</span><span class="sxs-lookup"><span data-stu-id="21ba3-147">The following output should appear.</span></span>  
  
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
  
## <a name="trace-the-program"></a><span data-ttu-id="21ba3-148">追蹤程式</span><span class="sxs-lookup"><span data-stu-id="21ba3-148">Trace the Program</span></span>  
  
### <a name="steps-one-and-two"></a><span data-ttu-id="21ba3-149">步驟一和二</span><span class="sxs-lookup"><span data-stu-id="21ba3-149">Steps ONE and TWO</span></span>  
 <span data-ttu-id="21ba3-150">前兩個顯示當 `startButton_Click` 呼叫 `AccessTheWebAsync`，以及 `AccessTheWebAsync` 呼叫非同步 <xref:System.Net.Http.HttpClient> 方法 <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> 時，追蹤路徑的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="21ba3-150">The first two display lines trace the path as `startButton_Click` calls `AccessTheWebAsync`, and `AccessTheWebAsync` calls the asynchronous <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29>.</span></span> <span data-ttu-id="21ba3-151">下圖概述不同方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="21ba3-151">The following image outlines the calls from method to method.</span></span>  
  
 <span data-ttu-id="21ba3-152">![步驟一和二](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span><span class="sxs-lookup"><span data-stu-id="21ba3-152">![Steps ONE and TWO](../../../../csharp/programming-guide/concepts/async/media/asynctrace-onetwo.png "AsyncTrace-ONETWO")</span></span>  
  
 <span data-ttu-id="21ba3-153">`AccessTheWebAsync` 和 `client.GetStringAsync` 傳回的類型都是 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="21ba3-153">The return type of both `AccessTheWebAsync` and `client.GetStringAsync` is <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="21ba3-154">針對 `AccessTheWebAsync`，TResult 是整數。</span><span class="sxs-lookup"><span data-stu-id="21ba3-154">For `AccessTheWebAsync`, TResult is an integer.</span></span> <span data-ttu-id="21ba3-155">針對 `GetStringAsync`，TResult 是字串。</span><span class="sxs-lookup"><span data-stu-id="21ba3-155">For `GetStringAsync`, TResult is a string.</span></span> <span data-ttu-id="21ba3-156">如需非同步方法傳回型別的詳細資訊，請參閱[非同步方法的傳回型別 (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="21ba3-156">For more information about async method return types, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
 <span data-ttu-id="21ba3-157">控制權返回呼叫端時，工作傳回非同步方法會傳回工作執行個體。</span><span class="sxs-lookup"><span data-stu-id="21ba3-157">A task-returning async method returns a task instance when control shifts back to the caller.</span></span> <span data-ttu-id="21ba3-158">在被呼叫的方法中發現 `await` 運算子時，或被呼叫的方法結束時，控制權會從非同步方法返回其呼叫端。</span><span class="sxs-lookup"><span data-stu-id="21ba3-158">Control returns from an async method to its caller either when an `await` operator is encountered in the called method or when the called method ends.</span></span> <span data-ttu-id="21ba3-159">標上 "THREE" 到 "SIX" 的顯示行會追蹤處理程序的這個部分。</span><span class="sxs-lookup"><span data-stu-id="21ba3-159">The display lines that are labeled "THREE" through "SIX" trace this part of the process.</span></span>  
  
### <a name="step-three"></a><span data-ttu-id="21ba3-160">步驟三</span><span class="sxs-lookup"><span data-stu-id="21ba3-160">Step THREE</span></span>  
 <span data-ttu-id="21ba3-161">在 `AccessTheWebAsync` 中，呼叫非同步方法 <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> 以下載目標網頁的內容。</span><span class="sxs-lookup"><span data-stu-id="21ba3-161">In `AccessTheWebAsync`, the asynchronous method <xref:System.Net.Http.HttpClient.GetStringAsync%28System.String%29> is called to download the contents of the target webpage.</span></span> <span data-ttu-id="21ba3-162">傳回 `client.GetStringAsync` 時，控制項會從 `client.GetStringAsync` 返回 `AccessTheWebAsync`。</span><span class="sxs-lookup"><span data-stu-id="21ba3-162">Control returns from `client.GetStringAsync` to `AccessTheWebAsync` when `client.GetStringAsync` returns.</span></span>  
  
 <span data-ttu-id="21ba3-163">`client.GetStringAsync` 方法會傳回指派給 `AccessTheWebAsync` 中 `getStringTask` 變數的字串工作。</span><span class="sxs-lookup"><span data-stu-id="21ba3-163">The `client.GetStringAsync` method returns a task of string that’s assigned to the `getStringTask` variable in `AccessTheWebAsync`.</span></span> <span data-ttu-id="21ba3-164">範例程式中的下行示範 `client.GetStringAsync` 呼叫和指派。</span><span class="sxs-lookup"><span data-stu-id="21ba3-164">The following line in the example program shows the call to `client.GetStringAsync` and the assignment.</span></span>  
  
```csharp  
Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
```  
  
 <span data-ttu-id="21ba3-165">您可以透過 `client.GetStringAsync` 將工作視為承諾，最後產生實際字串。</span><span class="sxs-lookup"><span data-stu-id="21ba3-165">You can think of the task as a promise by `client.GetStringAsync` to produce an actual string eventually.</span></span> <span data-ttu-id="21ba3-166">同時，如果 `AccessTheWebAsync` 的工作未依存於來自 `client.GetStringAsync` 的承諾字串，則該工作可以在 `client.GetStringAsync` 等候時繼續進行。</span><span class="sxs-lookup"><span data-stu-id="21ba3-166">In the meantime, if `AccessTheWebAsync` has work to do that doesn't depend on the promised string from `client.GetStringAsync`, that work can continue while  `client.GetStringAsync` waits.</span></span> <span data-ttu-id="21ba3-167">在此範例中，下列數行的輸出 (標上 "THREE”) 代表執行獨立工作的機會。</span><span class="sxs-lookup"><span data-stu-id="21ba3-167">In the example, the following lines of output, which are labeled "THREE," represent the opportunity to do independent work</span></span>  
  
```  
THREE: Back in AccessTheWebAsync.  
           Task getStringTask is started.  
           About to await getStringTask & return a Task<int> to startButton_Click.  
```  
  
 <span data-ttu-id="21ba3-168">下列陳述式會在等候 `getStringTask` 時暫止 `AccessTheWebAsync` 中的進度。</span><span class="sxs-lookup"><span data-stu-id="21ba3-168">The following statement suspends progress in `AccessTheWebAsync` when `getStringTask` is awaited.</span></span>  
  
```csharp  
string urlContents = await getStringTask;  
```  
  
 <span data-ttu-id="21ba3-169">下圖顯示從 `client.GetStringAsync` 到指派給 `getStringTask` 以及從建立 `getStringTask` 到套用 await 運算子的控制流程。</span><span class="sxs-lookup"><span data-stu-id="21ba3-169">The following image shows the flow of control from `client.GetStringAsync` to the assignment to `getStringTask` and from the creation of `getStringTask` to the application of an await operator.</span></span>  
  
 <span data-ttu-id="21ba3-170">![步驟三](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span><span class="sxs-lookup"><span data-stu-id="21ba3-170">![Step THREE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-three.png "AsyncTrace-Three")</span></span>  
  
 <span data-ttu-id="21ba3-171">除非傳回 `client.GetStringAsync`，否則 await 運算式會暫止 `AccessTheWebAsync`。</span><span class="sxs-lookup"><span data-stu-id="21ba3-171">The await expression suspends `AccessTheWebAsync` until `client.GetStringAsync` returns.</span></span> <span data-ttu-id="21ba3-172">同時，控制項會返回 `AccessTheWebAsync` 的呼叫端 `startButton_Click`。</span><span class="sxs-lookup"><span data-stu-id="21ba3-172">In the meantime, control returns to the caller of `AccessTheWebAsync`, `startButton_Click`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21ba3-173">一般而言，您會立即等候非同步方法呼叫。</span><span class="sxs-lookup"><span data-stu-id="21ba3-173">Typically, you await the call to an asynchronous method immediately.</span></span> <span data-ttu-id="21ba3-174">例如，下列指派可以取代可建立後等候 `getStringTask` 的先前程式碼：`string urlContents = await client.GetStringAsync("http://msdn.microsoft.com");`</span><span class="sxs-lookup"><span data-stu-id="21ba3-174">For example, the following assignment could replace the previous code that creates and then awaits `getStringTask`: `string urlContents = await client.GetStringAsync("http://msdn.microsoft.com");`</span></span>  
>   
>  <span data-ttu-id="21ba3-175">在本主題中，稍後會套用 await 運算子，以容納透過程式標記控制流程的輸出行。</span><span class="sxs-lookup"><span data-stu-id="21ba3-175">In this topic, the await operator is applied later to accommodate the output lines that mark the flow of control through the program.</span></span>  
  
### <a name="step-four"></a><span data-ttu-id="21ba3-176">步驟四</span><span class="sxs-lookup"><span data-stu-id="21ba3-176">Step FOUR</span></span>  
 <span data-ttu-id="21ba3-177">`AccessTheWebAsync` 的已宣告傳回型別為 `Task<int>`。</span><span class="sxs-lookup"><span data-stu-id="21ba3-177">The declared return type of `AccessTheWebAsync` is `Task<int>`.</span></span> <span data-ttu-id="21ba3-178">因此，暫止 `AccessTheWebAsync` 時，會將整數工作傳回給 `startButton_Click`。</span><span class="sxs-lookup"><span data-stu-id="21ba3-178">Therefore, when `AccessTheWebAsync` is suspended, it returns a task of integer to `startButton_Click`.</span></span> <span data-ttu-id="21ba3-179">您應該了解所傳回的工作不是 `getStringTask`。</span><span class="sxs-lookup"><span data-stu-id="21ba3-179">You should understand that the returned task isn’t `getStringTask`.</span></span> <span data-ttu-id="21ba3-180">傳回的工作是新整數工作，代表仍要在已暫止方法 `AccessTheWebAsync` 中執行的作業。</span><span class="sxs-lookup"><span data-stu-id="21ba3-180">The returned task is a new task of integer that represents what remains to be done in the suspended method, `AccessTheWebAsync`.</span></span> <span data-ttu-id="21ba3-181">這個工作是來自 `AccessTheWebAsync` 的承諾，可在工作完成時產生整數。</span><span class="sxs-lookup"><span data-stu-id="21ba3-181">The task is a promise from `AccessTheWebAsync` to produce an integer when the task is complete.</span></span>  
  
 <span data-ttu-id="21ba3-182">下列陳述式會將這個工作指派給 `getLengthTask` 變數。</span><span class="sxs-lookup"><span data-stu-id="21ba3-182">The following statement assigns this task to the `getLengthTask` variable.</span></span>  
  
```csharp  
Task<int> getLengthTask = AccessTheWebAsync();  
```  
  
 <span data-ttu-id="21ba3-183">如同 `AccessTheWebAsync`，除非等候非同步工作 (`getLengthTask`)，否則 `startButton_Click` 可以繼續執行未依存於該工作結果的工作。</span><span class="sxs-lookup"><span data-stu-id="21ba3-183">As in `AccessTheWebAsync`, `startButton_Click` can continue with work that doesn’t depend on the results of the asynchronous task (`getLengthTask`) until the task is awaited.</span></span> <span data-ttu-id="21ba3-184">下列輸出行代表該工作。</span><span class="sxs-lookup"><span data-stu-id="21ba3-184">The following output lines represent that work.</span></span>  
  
```  
FOUR:  Back in startButton_Click.  
           Task getLengthTask is started.  
           About to await getLengthTask -- no caller to return to.  
```  
  
 <span data-ttu-id="21ba3-185">等候 `getLengthTask` 時，會暫止 `startButton_Click` 中的進度。</span><span class="sxs-lookup"><span data-stu-id="21ba3-185">Progress in `startButton_Click` is suspended when `getLengthTask` is awaited.</span></span> <span data-ttu-id="21ba3-186">除非 `AccessTheWebAsync` 完成，否則下列指派陳述式會暫止 `startButton_Click`。</span><span class="sxs-lookup"><span data-stu-id="21ba3-186">The following assignment statement suspends `startButton_Click` until `AccessTheWebAsync` is complete.</span></span>  
  
```csharp  
int contentLength = await getLengthTask;  
```  
  
 <span data-ttu-id="21ba3-187">在下圖中，除非等候 `getLengthTask`，否則箭頭會顯示從 `AccessTheWebAsync` 中的 await 運算式到將值指派給 `getLengthTask` (後接 `startButton_Click` 中的正常處理) 的控制流程。</span><span class="sxs-lookup"><span data-stu-id="21ba3-187">In the following illustration, the arrows show the flow of control from the await expression in `AccessTheWebAsync` to the assignment of a value to `getLengthTask`, followed by normal processing in `startButton_Click` until `getLengthTask` is awaited.</span></span>  
  
 <span data-ttu-id="21ba3-188">![步驟四](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span><span class="sxs-lookup"><span data-stu-id="21ba3-188">![Step FOUR](../../../../csharp/programming-guide/concepts/async/media/asynctrace-four.png "AsyncTrace-FOUR")</span></span>  
  
### <a name="step-five"></a><span data-ttu-id="21ba3-189">步驟五</span><span class="sxs-lookup"><span data-stu-id="21ba3-189">Step FIVE</span></span>  
 <span data-ttu-id="21ba3-190">`client.GetStringAsync` 指出完成時，會取消暫止 `AccessTheWebAsync` 中的處理，而且可以繼續略過 await 陳述式。</span><span class="sxs-lookup"><span data-stu-id="21ba3-190">When `client.GetStringAsync` signals that it’s complete, processing in `AccessTheWebAsync` is released from suspension and can continue past the await statement.</span></span> <span data-ttu-id="21ba3-191">下列數行的輸出代表繼續處理。</span><span class="sxs-lookup"><span data-stu-id="21ba3-191">The following lines of output represent the resumption of processing.</span></span>  
  
```  
FIVE:  Back in AccessTheWebAsync.  
           Task getStringTask is complete.  
           Processing the return statement.  
           Exiting from AccessTheWebAsync.  
```  
  
 <span data-ttu-id="21ba3-192">return 陳述式的運算元 `urlContents.Length` 儲存在 `AccessTheWebAsync` 所傳回的工作中。</span><span class="sxs-lookup"><span data-stu-id="21ba3-192">The operand of the return statement, `urlContents.Length`, is stored in the task that  `AccessTheWebAsync` returns.</span></span> <span data-ttu-id="21ba3-193">await 運算式會從 `startButton_Click` 中的 `getLengthTask` 擷取該值。</span><span class="sxs-lookup"><span data-stu-id="21ba3-193">The await expression retrieves that value from `getLengthTask` in `startButton_Click`.</span></span>  
  
 <span data-ttu-id="21ba3-194">下圖顯示 `client.GetStringAsync` (和 `getStringTask`) 完成後的控制權轉移。</span><span class="sxs-lookup"><span data-stu-id="21ba3-194">The following image shows the transfer of control after `client.GetStringAsync` (and `getStringTask`) are complete.</span></span>  
  
 <span data-ttu-id="21ba3-195">![步驟五](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span><span class="sxs-lookup"><span data-stu-id="21ba3-195">![Step FIVE](../../../../csharp/programming-guide/concepts/async/media/asynctrace-five.png "AsyncTrace-FIVE")</span></span>  
  
 <span data-ttu-id="21ba3-196">`AccessTheWebAsync` 會執行直到完成，而且控制項會返回正在等待完成的 `startButton_Click`。</span><span class="sxs-lookup"><span data-stu-id="21ba3-196">`AccessTheWebAsync` runs to completion, and control returns to `startButton_Click`, which is awaiting the completion.</span></span>  
  
### <a name="step-six"></a><span data-ttu-id="21ba3-197">步驟六</span><span class="sxs-lookup"><span data-stu-id="21ba3-197">Step SIX</span></span>  
 <span data-ttu-id="21ba3-198">`AccessTheWebAsync` 指出完成時，會繼續略過 `startButton_Async` 中 await 陳述式的處理。</span><span class="sxs-lookup"><span data-stu-id="21ba3-198">When `AccessTheWebAsync` signals that it’s complete, processing can continue past the await statement in `startButton_Async`.</span></span> <span data-ttu-id="21ba3-199">事實上，程式不需要再執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="21ba3-199">In fact, the program has nothing more to do.</span></span>  
  
 <span data-ttu-id="21ba3-200">下列數行的輸出代表在 `startButton_Async` 中繼續處理：</span><span class="sxs-lookup"><span data-stu-id="21ba3-200">The following lines of output represent the resumption of processing in `startButton_Async`:</span></span>  
  
```  
SIX:   Back in startButton_Click.  
           Task getLengthTask is finished.  
           Result from AccessTheWebAsync is stored in contentLength.  
           About to display contentLength and exit.  
```  
  
 <span data-ttu-id="21ba3-201">await 運算式會從 `getLengthTask` 擷取整數值，而整數值是 `AccessTheWebAsync` 中 return 陳述式的運算元。</span><span class="sxs-lookup"><span data-stu-id="21ba3-201">The await expression retrieves from `getLengthTask` the integer value that’s the operand of the return statement in `AccessTheWebAsync`.</span></span> <span data-ttu-id="21ba3-202">下列陳述式會將該值指派給 `contentLength` 變數。</span><span class="sxs-lookup"><span data-stu-id="21ba3-202">The following statement assigns that value to the `contentLength` variable.</span></span>  
  
```csharp  
int contentLength = await getLengthTask;  
```  
  
 <span data-ttu-id="21ba3-203">下圖顯示從 `AccessTheWebAsync` 到 `startButton_Click` 的控制項返回。</span><span class="sxs-lookup"><span data-stu-id="21ba3-203">The following image shows the return of control from `AccessTheWebAsync` to `startButton_Click`.</span></span>  
  
 <span data-ttu-id="21ba3-204">![步驟六](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span><span class="sxs-lookup"><span data-stu-id="21ba3-204">![Step SIX](../../../../csharp/programming-guide/concepts/async/media/asynctrace-six.png "AsyncTrace-SIX")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21ba3-205">另請參閱</span><span class="sxs-lookup"><span data-stu-id="21ba3-205">See Also</span></span>  
 [<span data-ttu-id="21ba3-206">使用 async 和 await 進行非同步程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="21ba3-206">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)  
 [<span data-ttu-id="21ba3-207">非同步方法的傳回型別 (C#)</span><span class="sxs-lookup"><span data-stu-id="21ba3-207">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)  
 [<span data-ttu-id="21ba3-208">逐步解說：使用 async 和 await 存取 Web (C#)</span><span class="sxs-lookup"><span data-stu-id="21ba3-208">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
 <span data-ttu-id="21ba3-209">[Async Sample: Control Flow in Async Programs (C# and Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255285) (非同步範例：非同步程式中的控制流程 (C# 和 Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="21ba3-209">[Async Sample: Control Flow in Async Programs (C# and Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255285)</span></span>
