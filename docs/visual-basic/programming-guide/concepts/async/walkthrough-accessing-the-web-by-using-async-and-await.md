---
title: "存取 Web 使用 Async 和 Await (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs:
- VB
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
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
ms.openlocfilehash: 643fff648336c664961ad7956308acbaea262f61
ms.contentlocale: zh-tw
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a><span data-ttu-id="7df00-102">逐步解說：使用 Async 和 Await 存取 Web (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7df00-102">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>
<span data-ttu-id="7df00-103">您可以使用所導入的功能撰寫非同步程式更容易、 更直覺[!INCLUDE[vs_dev11_long](../../../../csharp/includes/vs_dev11_long_md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7df00-103">You can write asynchronous programs more easily and intuitively by using features that were introduced in [!INCLUDE[vs_dev11_long](../../../../csharp/includes/vs_dev11_long_md.md)].</span></span> <span data-ttu-id="7df00-104">您可以撰寫非同步程式碼，使其看起來像是同步程式碼，讓編譯器處理困難的回呼函式和非同步程式碼通常需要的接續。</span><span class="sxs-lookup"><span data-stu-id="7df00-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>  
  
 <span data-ttu-id="7df00-105">如需非同步功能的詳細資訊，請參閱[使用 Async 和 Await (Visual Basic) 進行非同步程式設計](../../../../visual-basic/programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="7df00-105">For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>  
  
 <span data-ttu-id="7df00-106">本逐步解說從同步化 Windows Presentation Foundation (WPF) 應用程式開始，該應用程式會加總網站清單中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="7df00-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="7df00-107">然後逐步解說會藉由使用新功能，將應用程式轉換為非同步解決方案。</span><span class="sxs-lookup"><span data-stu-id="7df00-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>  
  
 <span data-ttu-id="7df00-108">如果您不想要自行建置的應用程式，您可以下載 「 非同步範例︰ 存取 Web 逐步解說 （C# 和 Visual Basic） 」 從[開發人員程式碼範例](http://go.microsoft.com/fwlink/?LinkId=255191)。</span><span class="sxs-lookup"><span data-stu-id="7df00-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](http://go.microsoft.com/fwlink/?LinkId=255191).</span></span>  
  
 <span data-ttu-id="7df00-109">在這個逐步解說中，您將完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="7df00-109">In this walkthrough, you complete the following tasks:</span></span>  
  
-   [<span data-ttu-id="7df00-110">若要建立 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="7df00-110">To create a WPF application</span></span>](#CreateWPFApp)  
  
-   [<span data-ttu-id="7df00-111">若要設計簡單的 WPF MainWindow</span><span class="sxs-lookup"><span data-stu-id="7df00-111">To design a simple WPF MainWindow</span></span>](#MainWindow)  
  
-   [<span data-ttu-id="7df00-112">若要加入的參考</span><span class="sxs-lookup"><span data-stu-id="7df00-112">To add a reference</span></span>](#AddRef)  
  
-   [<span data-ttu-id="7df00-113">加入必要的 Imports 陳述式</span><span class="sxs-lookup"><span data-stu-id="7df00-113">To add necessary Imports statements</span></span>](#ImportsState)  
  
-   [<span data-ttu-id="7df00-114">若要建立同步應用程式</span><span class="sxs-lookup"><span data-stu-id="7df00-114">To create a synchronous application</span></span>](#synchronous)  
  
-   [<span data-ttu-id="7df00-115">若要測試同步方案</span><span class="sxs-lookup"><span data-stu-id="7df00-115">To test the synchronous solution</span></span>](#testSynch)  
  
-   [<span data-ttu-id="7df00-116">若要將 GetURLContents 轉換非同步方法</span><span class="sxs-lookup"><span data-stu-id="7df00-116">To convert GetURLContents to an asynchronous method</span></span>](#GetURLContents)  
  
-   [<span data-ttu-id="7df00-117">若要將 SumPageSizes 轉換非同步方法</span><span class="sxs-lookup"><span data-stu-id="7df00-117">To convert SumPageSizes to an asynchronous method</span></span>](#SumPageSizes)  
  
-   [<span data-ttu-id="7df00-118">若要將 startButton_Click 轉換非同步方法</span><span class="sxs-lookup"><span data-stu-id="7df00-118">To convert startButton_Click to an asynchronous method</span></span>](#startButton)  
  
-   [<span data-ttu-id="7df00-119">若要測試非同步方案</span><span class="sxs-lookup"><span data-stu-id="7df00-119">To test the asynchronous solution</span></span>](#testAsynch)  
  
-   [<span data-ttu-id="7df00-120">若要使用.NET Framework 方法來取代方法 GetURLContentsAsync</span><span class="sxs-lookup"><span data-stu-id="7df00-120">To replace method GetURLContentsAsync with a .NET Framework method</span></span>](#GetURLContentsAsync)  
  
-   [<span data-ttu-id="7df00-121">範例</span><span class="sxs-lookup"><span data-stu-id="7df00-121">Example</span></span>](#BKMK_CompleteCodeExamples)  
  
## <a name="prerequisites"></a><span data-ttu-id="7df00-122">必要條件</span><span class="sxs-lookup"><span data-stu-id="7df00-122">Prerequisites</span></span>  
 <span data-ttu-id="7df00-123">在您的電腦上必須安裝 visual Studio 2012 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="7df00-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="7df00-124">如需詳細資訊，請參閱[Microsoft 網站](http://go.microsoft.com/fwlink/?LinkId=235233)。</span><span class="sxs-lookup"><span data-stu-id="7df00-124">For more information, see the [Microsoft website](http://go.microsoft.com/fwlink/?LinkId=235233).</span></span>  
  
###  <span data-ttu-id="7df00-125"><a name="CreateWPFApp"></a>若要建立 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="7df00-125"><a name="CreateWPFApp"></a> To create a WPF application</span></span>  
  
1.  <span data-ttu-id="7df00-126">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="7df00-126">Start Visual Studio.</span></span>  
  
2.  <span data-ttu-id="7df00-127">在功能表列上，選擇 [檔案] ****、[新增] ****、[專案] ****。</span><span class="sxs-lookup"><span data-stu-id="7df00-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>  
  
     <span data-ttu-id="7df00-128">[ **新增專案** ] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="7df00-128">The **New Project** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="7df00-129">在**已安裝的範本**] 窗格中，選擇 [Visual Basic 中，並選擇**WPF 應用程式**從專案類型清單。</span><span class="sxs-lookup"><span data-stu-id="7df00-129">In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.</span></span>  
  
4.  <span data-ttu-id="7df00-130">在**名稱**文字中，輸入`AsyncExampleWPF`，然後選擇 **確定**按鈕。</span><span class="sxs-lookup"><span data-stu-id="7df00-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>  
  
     <span data-ttu-id="7df00-131">新的專案會出現在**方案總管 中**。</span><span class="sxs-lookup"><span data-stu-id="7df00-131">The new project appears in **Solution Explorer**.</span></span>  
  
##  <a name="BKMK_DesignWPFMainWin"></a>   
###  <span data-ttu-id="7df00-132"><a name="MainWindow"></a>若要設計簡單的 WPF MainWindow</span><span class="sxs-lookup"><span data-stu-id="7df00-132"><a name="MainWindow"></a> To design a simple WPF MainWindow</span></span>  
  
1.  <span data-ttu-id="7df00-133">在 Visual Studio 程式碼編輯器中，選擇 [ **MainWindow.xaml** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="7df00-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>  
  
2.  <span data-ttu-id="7df00-134">如果**工具箱** 視窗未顯示，開啟**檢視** 功能表上，然後選擇 **工具箱**。</span><span class="sxs-lookup"><span data-stu-id="7df00-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>  
  
3.  <span data-ttu-id="7df00-135">新增**按鈕**控制項和**文字方塊**，來控制對**MainWindow**視窗。</span><span class="sxs-lookup"><span data-stu-id="7df00-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>  
  
4.  <span data-ttu-id="7df00-136">反白顯示**文字方塊**控制項並在**屬性** 視窗中，設定下列值︰</span><span class="sxs-lookup"><span data-stu-id="7df00-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="7df00-137">設定**名稱**屬性`resultsTextBox`。</span><span class="sxs-lookup"><span data-stu-id="7df00-137">Set the **Name** property to `resultsTextBox`.</span></span>  
  
    -   <span data-ttu-id="7df00-138">設定**高度**屬性為 250。</span><span class="sxs-lookup"><span data-stu-id="7df00-138">Set the **Height** property to 250.</span></span>  
  
    -   <span data-ttu-id="7df00-139">設定**寬度**500 的屬性。</span><span class="sxs-lookup"><span data-stu-id="7df00-139">Set the **Width** property to 500.</span></span>  
  
    -   <span data-ttu-id="7df00-140">在**文字**索引標籤上，指定等寬字型，例如新細明體或全域等寬。</span><span class="sxs-lookup"><span data-stu-id="7df00-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>  
  
5.  <span data-ttu-id="7df00-141">反白顯示**按鈕**控制項並在**屬性** 視窗中，設定下列值︰</span><span class="sxs-lookup"><span data-stu-id="7df00-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>  
  
    -   <span data-ttu-id="7df00-142">設定**名稱**屬性`startButton`。</span><span class="sxs-lookup"><span data-stu-id="7df00-142">Set the **Name** property to `startButton`.</span></span>  
  
    -   <span data-ttu-id="7df00-143">值變更**內容**屬性從**按鈕**至**啟動**。</span><span class="sxs-lookup"><span data-stu-id="7df00-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>  
  
6.  <span data-ttu-id="7df00-144">將文字方塊和按鈕，同時出現在**MainWindow**視窗。</span><span class="sxs-lookup"><span data-stu-id="7df00-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>  
  
     <span data-ttu-id="7df00-145">如需 WPF 的 XAML 設計工具的詳細資訊，請參閱[使用 XAML 設計工具建立 UI](https://docs.microsoft.com/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="7df00-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](https://docs.microsoft.com/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>  
  
##  <a name="BKMK_AddReference"></a>   
###  <span data-ttu-id="7df00-146"><a name="AddRef"></a>若要加入的參考</span><span class="sxs-lookup"><span data-stu-id="7df00-146"><a name="AddRef"></a> To add a reference</span></span>  
  
1.  <span data-ttu-id="7df00-147">在**方案總管 中**，反白顯示您的專案名稱。</span><span class="sxs-lookup"><span data-stu-id="7df00-147">In **Solution Explorer**, highlight your project's name.</span></span>  
  
2.  <span data-ttu-id="7df00-148">在功能表列上選擇 **專案**，**加入參考**。</span><span class="sxs-lookup"><span data-stu-id="7df00-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>  
  
     <span data-ttu-id="7df00-149">**參考管理員** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="7df00-149">The **Reference Manager** dialog box appears.</span></span>  
  
3.  <span data-ttu-id="7df00-150">在對話方塊頂端，請確認您的專案的目標為.NET Framework 4.5 或更高版本。</span><span class="sxs-lookup"><span data-stu-id="7df00-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>  
  
4.  <span data-ttu-id="7df00-151">在**組件**區域中，選擇  **Framework**如果它已經不選擇。</span><span class="sxs-lookup"><span data-stu-id="7df00-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>  
  
5.  <span data-ttu-id="7df00-152">在名稱的清單中選取**System.Net.Http**核取方塊。</span><span class="sxs-lookup"><span data-stu-id="7df00-152">In the list of names, select the **System.Net.Http** check box.</span></span>  
  
6.  <span data-ttu-id="7df00-153">選擇**確定** 按鈕以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="7df00-153">Choose the **OK** button to close the dialog box.</span></span>  
  
##  <a name="BKMK_AddStatesandDirs"></a>   
###  <span data-ttu-id="7df00-154"><a name="ImportsState"></a>加入必要的 Imports 陳述式</span><span class="sxs-lookup"><span data-stu-id="7df00-154"><a name="ImportsState"></a> To add necessary Imports statements</span></span>  
  
1.  <span data-ttu-id="7df00-155">在**方案總管] 中**MainWindow.xaml.vb，開啟捷徑功能表，然後選擇 [**檢視程式碼**。</span><span class="sxs-lookup"><span data-stu-id="7df00-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>  
  
2.  <span data-ttu-id="7df00-156">新增下列`Imports`尚不存在的程式碼檔案頂端的陳述式。</span><span class="sxs-lookup"><span data-stu-id="7df00-156">Add the following `Imports` statements at the top of the code file if they’re not already present.</span></span>  
  
    ```vb  
    Imports System.Net.Http  
    Imports System.Net  
    Imports System.IO  
    ```  
  
##  <a name="BKMK_CreatSynchApp"></a>   
###  <span data-ttu-id="7df00-157"><a name="synchronous"></a>若要建立同步應用程式</span><span class="sxs-lookup"><span data-stu-id="7df00-157"><a name="synchronous"></a> To create a synchronous application</span></span>  
  
1.  <span data-ttu-id="7df00-158">在 設計 視窗，MainWindow.xaml，連按兩下**啟動** 按鈕以建立`startButton_Click`MainWindow.xaml.vb 中的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="7df00-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>  
  
2.  <span data-ttu-id="7df00-159">在 MainWindow.xaml.vb，將下列程式碼複製到本文`startButton_Click`:</span><span class="sxs-lookup"><span data-stu-id="7df00-159">In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:</span></span>  
  
    ```vb  
    resultsTextBox.Clear()  
    SumPageSizes()  
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."  
    ```  
  
     <span data-ttu-id="7df00-160">程式碼會呼叫方法，該方法會驅動應用程式 `SumPageSizes`，並且在控制項返回 `startButton_Click` 時顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="7df00-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>  
  
3.  <span data-ttu-id="7df00-161">同步方案的程式碼包含下列四種方法：</span><span class="sxs-lookup"><span data-stu-id="7df00-161">The code for the synchronous solution contains the following four methods:</span></span>  
  
    -   <span data-ttu-id="7df00-162">`SumPageSizes`，會從 `SetUpURLList` 取得網頁 URL 的清單，然後呼叫 `GetURLContents` 和 `DisplayResults` 以處理每個 URL。</span><span class="sxs-lookup"><span data-stu-id="7df00-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>  
  
    -   <span data-ttu-id="7df00-163">`SetUpURLList`，會製作並傳回網址清單。</span><span class="sxs-lookup"><span data-stu-id="7df00-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>  
  
    -   <span data-ttu-id="7df00-164">`GetURLContents`，會下載每個網站的內容，並傳回內容做為位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="7df00-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>  
  
    -   <span data-ttu-id="7df00-165">`DisplayResults`，會顯示每個 URL 的位元組陣列中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="7df00-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>  
  
     <span data-ttu-id="7df00-166">複製下列四種方法，然後再貼入下`startButton_Click`MainWindow.xaml.vb 中的事件處理常式︰</span><span class="sxs-lookup"><span data-stu-id="7df00-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:</span></span>  
  
    ```vb  
    Private Sub SumPageSizes()  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            ' GetURLContents returns the contents of url as a byte array.  
            Dim urlContents As Byte() = GetURLContents(url)  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the web addresses.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf & "Total bytes returned:  {0}" & vbCrLf, total)  
    End Sub  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Function GetURLContents(url As String) As Byte()  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        ' Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.  
        Using response As WebResponse = webReq.GetResponse()  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                responseStream.CopyTo(content)  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
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
  
##  <a name="BKMK_TestSynchSol"></a>   
###  <span data-ttu-id="7df00-167"><a name="testSynch"></a>若要測試同步方案</span><span class="sxs-lookup"><span data-stu-id="7df00-167"><a name="testSynch"></a> To test the synchronous solution</span></span>  
  
1.  <span data-ttu-id="7df00-168">選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7df00-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="7df00-169">應該會顯示如下列清單的輸出。</span><span class="sxs-lookup"><span data-stu-id="7df00-169">Output that resembles the following list should appear.</span></span>  
  
    ```  
  
    msdn.microsoft.com/library/windows/apps/br211380.aspx        383832  
    msdn.microsoft.com                                            33964  
    msdn.microsoft.com/library/hh290136.aspx               225793  
    msdn.microsoft.com/library/ee256749.aspx               143577  
    msdn.microsoft.com/library/hh290138.aspx               237372  
    msdn.microsoft.com/library/hh290140.aspx               128279  
    msdn.microsoft.com/library/dd470362.aspx               157649  
    msdn.microsoft.com/library/aa578028.aspx               204457  
    msdn.microsoft.com/library/ms404677.aspx               176405  
    msdn.microsoft.com/library/ff730837.aspx               143474  
  
    Total bytes returned:  1834802  
  
    Control returned to startButton_Click.  
  
    ```  
  
     <span data-ttu-id="7df00-170">請注意，需要花費幾秒鐘以顯示計數。</span><span class="sxs-lookup"><span data-stu-id="7df00-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="7df00-171">在這段期間，在等候下載要求資源的同時，會封鎖 UI 執行緒。</span><span class="sxs-lookup"><span data-stu-id="7df00-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="7df00-172">如此一來，您無法移動、 最大化、 最小化，或甚至關閉顯示在視窗中，選擇之後**啟動** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7df00-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="7df00-173">這些努力會失敗，直到位元組計數開始出現為止。</span><span class="sxs-lookup"><span data-stu-id="7df00-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="7df00-174">如果網站沒有回應，也不會指出失敗的站台。</span><span class="sxs-lookup"><span data-stu-id="7df00-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="7df00-175">甚至難以停止等候以及關閉程式。</span><span class="sxs-lookup"><span data-stu-id="7df00-175">It is difficult even to stop waiting and close the program.</span></span>  
  
##  <a name="BKMK_ConvertGtBtArr"></a>   
###  <span data-ttu-id="7df00-176"><a name="GetURLContents"></a>若要將 GetURLContents 轉換非同步方法</span><span class="sxs-lookup"><span data-stu-id="7df00-176"><a name="GetURLContents"></a> To convert GetURLContents to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="7df00-177">若要轉換為非同步方案同步的方案，開始的最佳位置是在`GetURLContents`因為呼叫<xref:System.Net.HttpWebRequest>方法<xref:System.Net.HttpWebRequest.GetResponse%2A>和<xref:System.IO.Stream>方法<xref:System.IO.Stream.CopyTo%2A>會在應用程式存取 web。</xref:System.IO.Stream.CopyTo%2A> </xref:System.IO.Stream> </xref:System.Net.HttpWebRequest.GetResponse%2A> </xref:System.Net.HttpWebRequest></span><span class="sxs-lookup"><span data-stu-id="7df00-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="7df00-178">.NET Framework 會讓轉換變得簡單，方法是提供這兩種方法的非同步版本。</span><span class="sxs-lookup"><span data-stu-id="7df00-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>  
  
     <span data-ttu-id="7df00-179">如需有關中所使用的方法`GetURLContents`，請參閱<xref:System.Net.WebRequest>。</xref:System.Net.WebRequest></span><span class="sxs-lookup"><span data-stu-id="7df00-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7df00-180">當您依照本逐步解說中的步驟時，會出現數個編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="7df00-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="7df00-181">您可以略過它們，並繼續進行本逐步解說。</span><span class="sxs-lookup"><span data-stu-id="7df00-181">You can ignore them and continue with the walkthrough.</span></span>  
  
     <span data-ttu-id="7df00-182">變更方法呼叫中的第三行`GetURLContents`從`GetResponse`非同步工作基礎<xref:System.Net.WebRequest.GetResponseAsync%2A>方法。</xref:System.Net.WebRequest.GetResponseAsync%2A></span><span class="sxs-lookup"><span data-stu-id="7df00-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>  
  
    ```vb  
    Using response As WebResponse = webReq.GetResponseAsync()  
    ```  
  
2.  <span data-ttu-id="7df00-183">`GetResponseAsync`傳回<xref:System.Threading.Tasks.Task%601>。</xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="7df00-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="7df00-184">在此情況下，*工作傳回變數*， `TResult`，具有類型<xref:System.Net.WebResponse>。</xref:System.Net.WebResponse></span><span class="sxs-lookup"><span data-stu-id="7df00-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="7df00-185">工作承諾會在已下載要求的資料及工作執行完成之後，產生實際 `WebResponse` 物件。</span><span class="sxs-lookup"><span data-stu-id="7df00-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>  
  
     <span data-ttu-id="7df00-186">要擷取`WebResponse`值從工作，請套用[Await](../../../../visual-basic/language-reference/operators/await-operator.md)運算子來呼叫`GetResponseAsync`，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="7df00-186">To retrieve the `WebResponse` value from the task, apply an [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>  
  
<span data-ttu-id="7df00-187"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="7df00-187"><CodeContentPlaceHolder>5</CodeContentPlaceHolder></span></span>  
     <span data-ttu-id="7df00-188">`Await`運算子會暫停目前的方法，執行`GetURLContents`，直到等候的工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="7df00-188">The `Await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="7df00-189">同時，控制項會返回非同步方法的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="7df00-189">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="7df00-190">在此範例中，目前方法是 `GetURLContents`，呼叫端是 `SumPageSizes`。</span><span class="sxs-lookup"><span data-stu-id="7df00-190">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="7df00-191">當工作完成時，承諾的 `WebResponse` 物件會以等候工作之值的形式產生，而且會指派給變數 `response`。</span><span class="sxs-lookup"><span data-stu-id="7df00-191">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>  
  
     The previous statement can be separated into the following two statements to clarify what happens.  
  
<span data-ttu-id="7df00-192"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="7df00-192"><CodeContentPlaceHolder>6</CodeContentPlaceHolder></span></span>  
     <span data-ttu-id="7df00-193">對 `webReq.GetResponseAsync` 的呼叫會傳回 `Task(Of WebResponse)` 或 `Task<WebResponse>`。</span><span class="sxs-lookup"><span data-stu-id="7df00-193">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="7df00-194">然後`Await`運算子會套用至擷取工作`WebResponse`值。</span><span class="sxs-lookup"><span data-stu-id="7df00-194">Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.</span></span>  
  
     If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied. For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).  
  
3.  <span data-ttu-id="7df00-195">因為您將新增`Await`運算子上一個步驟中的，編譯器就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7df00-195">Because you added the `Await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="7df00-196">運算子只能用於與標記的方法，[非同步](../../../../visual-basic/language-reference/modifiers/async.md)修飾詞。</span><span class="sxs-lookup"><span data-stu-id="7df00-196">The operator can be used only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="7df00-197">當您重複轉換步驟以將對 `CopyTo` 的呼叫取代為對 `CopyToAsync` 的呼叫時，略過錯誤。</span><span class="sxs-lookup"><span data-stu-id="7df00-197">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>  
  
    -   <span data-ttu-id="7df00-198">變更至<xref:System.IO.Stream.CopyToAsync%2A>。</xref:System.IO.Stream.CopyToAsync%2A>呼叫的方法名稱</span><span class="sxs-lookup"><span data-stu-id="7df00-198">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>  
  
    -   <span data-ttu-id="7df00-199">`CopyTo` 或 `CopyToAsync` 方法會將位元組複製到其引數，`content`，並不會傳回有意義的值。</span><span class="sxs-lookup"><span data-stu-id="7df00-199">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="7df00-200">在同步版本中，呼叫 `CopyTo` 是簡單的陳述式，不會傳回值。</span><span class="sxs-lookup"><span data-stu-id="7df00-200">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="7df00-201">非同步版本， `CopyToAsync`，傳回<xref:System.Threading.Tasks.Task>。</xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="7df00-201">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="7df00-202">工作函式，例如 "Task(void)"，讓方法等候。</span><span class="sxs-lookup"><span data-stu-id="7df00-202">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="7df00-203">將 `Await` 或 `await` 套用至對 `CopyToAsync` 的呼叫，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="7df00-203">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>  
  
<span data-ttu-id="7df00-204"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="7df00-204"><CodeContentPlaceHolder>7</CodeContentPlaceHolder></span></span>  
         <span data-ttu-id="7df00-205">前一個陳述式縮寫下列兩行程式碼。</span><span class="sxs-lookup"><span data-stu-id="7df00-205">The previous statement abbreviates the following two lines of code.</span></span>  
  
<span data-ttu-id="7df00-206"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="7df00-206"><CodeContentPlaceHolder>8</CodeContentPlaceHolder></span></span>  
4.  <span data-ttu-id="7df00-207">`GetURLContents` 中還需要完成的工作是調整方法簽章。</span><span class="sxs-lookup"><span data-stu-id="7df00-207">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="7df00-208">您可以使用`Await`運算子只能在方法中會標示[非同步](../../../../visual-basic/language-reference/modifiers/async.md)修飾詞。</span><span class="sxs-lookup"><span data-stu-id="7df00-208">You can use the `Await` operator only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="7df00-209">新增修飾詞來標記方法，做為*非同步方法*，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="7df00-209">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>  
  
<span data-ttu-id="7df00-210"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span><span class="sxs-lookup"><span data-stu-id="7df00-210"><CodeContentPlaceHolder>9</CodeContentPlaceHolder></span></span>  
5.  <span data-ttu-id="7df00-211">非同步方法的傳回型別只能<xref:System.Threading.Tasks.Task>， <xref:System.Threading.Tasks.Task%601>。</xref:System.Threading.Tasks.Task%601> </xref:System.Threading.Tasks.Task></span><span class="sxs-lookup"><span data-stu-id="7df00-211">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="7df00-212">在 Visual Basic 中，方法必須是 `Function`，會傳回 `Task` 或 `Task(Of T)`，或者方法必須是 `Sub`。</span><span class="sxs-lookup"><span data-stu-id="7df00-212">In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`.</span></span> <span data-ttu-id="7df00-213">一般而言，`Sub`方法只適用於非同步事件處理常式，其中`Sub`需要。</span><span class="sxs-lookup"><span data-stu-id="7df00-213">Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required.</span></span> <span data-ttu-id="7df00-214">在其他情況下，您會使用`Task(T)`完成的方法有[傳回](../../../../visual-basic/language-reference/statements/return-statement.md)陳述式所傳回的值型別 T，而且您使用`Task`如果完成的方法不會傳回有意義的值。</span><span class="sxs-lookup"><span data-stu-id="7df00-214">In other cases, you use `Task(T)` if the completed method has a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span>  
  
     <span data-ttu-id="7df00-215">如需詳細資訊，請參閱[非同步傳回類型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="7df00-215">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
     <span data-ttu-id="7df00-216">方法 `GetURLContents` 有 return 陳述式，陳述式會傳回位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="7df00-216">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="7df00-217">因此，非同步版本的傳回類型是 Task(T)，其中 T 是位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="7df00-217">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="7df00-218">在方法簽章中進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="7df00-218">Make the following changes in the method signature:</span></span>  
  
    -   <span data-ttu-id="7df00-219">傳回的型別變更`Task(Of Byte())`。</span><span class="sxs-lookup"><span data-stu-id="7df00-219">Change the return type to `Task(Of Byte())`.</span></span>  
  
    -   <span data-ttu-id="7df00-220">依照慣例，非同步方法的名稱會以 "Async" 結尾，所以重新命名方法 `GetURLContentsAsync`。</span><span class="sxs-lookup"><span data-stu-id="7df00-220">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>  
  
     <span data-ttu-id="7df00-221">下列程式碼會顯示這些變更。</span><span class="sxs-lookup"><span data-stu-id="7df00-221">The following code shows these changes.</span></span>  
  
    ```vb  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
    ```  
  
     <span data-ttu-id="7df00-222">只要這幾個變更，`GetURLContents` 至非同步方法的轉換就能完成。</span><span class="sxs-lookup"><span data-stu-id="7df00-222">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>  
  
##  <a name="BKMK_ConvertSumPagSzs"></a>   
###  <span data-ttu-id="7df00-223"><a name="SumPageSizes"></a>若要將 SumPageSizes 轉換非同步方法</span><span class="sxs-lookup"><span data-stu-id="7df00-223"><a name="SumPageSizes"></a> To convert SumPageSizes to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="7df00-224">針對 `SumPageSizes` 重複上述程序的步驟。</span><span class="sxs-lookup"><span data-stu-id="7df00-224">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="7df00-225">首先，將對 `GetURLContents` 的呼叫變更為非同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="7df00-225">First, change the call to `GetURLContents` to an asynchronous call.</span></span>  
  
    -   <span data-ttu-id="7df00-226">如果您尚未這麼做，請變更方法的名稱，該方法是從 `GetURLContents` 呼叫至 `GetURLContentsAsync`。</span><span class="sxs-lookup"><span data-stu-id="7df00-226">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>  
  
    -   <span data-ttu-id="7df00-227">套用`Await`工作，`GetURLContentsAsync`傳回取得位元組陣列值。</span><span class="sxs-lookup"><span data-stu-id="7df00-227">Apply `Await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>  
  
     <span data-ttu-id="7df00-228">下列程式碼會顯示這些變更。</span><span class="sxs-lookup"><span data-stu-id="7df00-228">The following code shows these changes.</span></span>  
  
    ```vb  
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
    ```  
  
     <span data-ttu-id="7df00-229">前一個指派縮寫下列兩行程式碼。</span><span class="sxs-lookup"><span data-stu-id="7df00-229">The previous assignment abbreviates the following two lines of code.</span></span>  
  
    ```vb  
    ' GetURLContentsAsync returns a task. At completion, the task   
    ' produces a byte array.   
    'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)   
    'Dim urlContents As Byte() = Await getContentsTask  
  
    ```  
  
2.  <span data-ttu-id="7df00-230">在方法簽章中進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="7df00-230">Make the following changes in the method's signature:</span></span>  
  
    -   <span data-ttu-id="7df00-231">方法標`Async`修飾詞。</span><span class="sxs-lookup"><span data-stu-id="7df00-231">Mark the method with the `Async` modifier.</span></span>  
  
    -   <span data-ttu-id="7df00-232">將 "Async" 加入至方法名稱。</span><span class="sxs-lookup"><span data-stu-id="7df00-232">Add "Async" to the method name.</span></span>  
  
    -   <span data-ttu-id="7df00-233">這次沒有任何工作傳回變數，T，因為 `SumPageSizesAsync` 並未傳回 T 的值。(此方法沒有任何`Return`陳述式。)不過，方法必須傳回 `Task` 才可以等候。</span><span class="sxs-lookup"><span data-stu-id="7df00-233">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="7df00-234">因此，變更方法型別從`Sub`到`Function`。</span><span class="sxs-lookup"><span data-stu-id="7df00-234">Therefore, change the method type from `Sub` to `Function`.</span></span> <span data-ttu-id="7df00-235">函式的傳回類型是 `Task`。</span><span class="sxs-lookup"><span data-stu-id="7df00-235">The return type of the function is `Task`.</span></span>  
  
     <span data-ttu-id="7df00-236">下列程式碼會顯示這些變更。</span><span class="sxs-lookup"><span data-stu-id="7df00-236">The following code shows these changes.</span></span>  
  
    ```vb  
    Private Async Function SumPageSizesAsync() As Task  
    ```  
  
     <span data-ttu-id="7df00-237">`SumPageSizes` 至 `SumPageSizesAsync` 的轉換完成。</span><span class="sxs-lookup"><span data-stu-id="7df00-237">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>  
  
##  <a name="BKMK_Cnvrtbttn1"></a>   
###  <span data-ttu-id="7df00-238"><a name="startButton"></a>若要將 startButton_Click 轉換非同步方法</span><span class="sxs-lookup"><span data-stu-id="7df00-238"><a name="startButton"></a> To convert startButton_Click to an asynchronous method</span></span>  
  
1.  <span data-ttu-id="7df00-239">如果您尚未這麼做，請在事件處理常式中，將呼叫方法的名稱從 `SumPageSizes` 變更為 `SumPageSizesAsync`。</span><span class="sxs-lookup"><span data-stu-id="7df00-239">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>  
  
2.  <span data-ttu-id="7df00-240">因為 `SumPageSizesAsync` 是非同步方法，在事件處理常式中變更程式碼以等候結果。</span><span class="sxs-lookup"><span data-stu-id="7df00-240">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>  
  
     <span data-ttu-id="7df00-241">對 `SumPageSizesAsync` 的呼叫會鏡射 `GetURLContentsAsync` 中對 `CopyToAsync` 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="7df00-241">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="7df00-242">呼叫會傳回 `Task`，而不是 `Task(T)`。</span><span class="sxs-lookup"><span data-stu-id="7df00-242">The call returns a `Task`, not a `Task(T)`.</span></span>  
  
     <span data-ttu-id="7df00-243">如同先前的程序，您可以使用一個陳述式或兩個陳述式轉換呼叫。</span><span class="sxs-lookup"><span data-stu-id="7df00-243">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="7df00-244">下列程式碼會顯示這些變更。</span><span class="sxs-lookup"><span data-stu-id="7df00-244">The following code shows these changes.</span></span>  
  
    ```vb  
    '' One-step async call.  
    Await SumPageSizesAsync()  
  
    ' Two-step async call.  
    'Dim sumTask As Task = SumPageSizesAsync()  
    'Await sumTask  
    ```  
  
3.  <span data-ttu-id="7df00-245">若要避免不小心重新輸入此作業，將下列陳述式加入頂端`startButton_Click`停用**啟動** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7df00-245">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>  
  
    ```vb  
    ' Disable the button until the operation is complete.  
    startButton.IsEnabled = False  
    ```  
  
     <span data-ttu-id="7df00-246">您可以在事件處理常式結尾重新啟用按鈕。</span><span class="sxs-lookup"><span data-stu-id="7df00-246">You can reenable the button at the end of the event handler.</span></span>  
  
    ```vb  
    ' Reenable the button in case you want to run the operation again.  
    startButton.IsEnabled = True  
    ```  
  
     <span data-ttu-id="7df00-247">如需重新進入的詳細資訊，請參閱[處理非同步應用程式 (Visual Basic) 中的重新進入](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="7df00-247">For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>  
  
4.  <span data-ttu-id="7df00-248">最後，加入`Async`修飾詞新增至宣告，讓事件處理常式可以等候`SumPagSizesAsync`。</span><span class="sxs-lookup"><span data-stu-id="7df00-248">Finally, add the `Async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>  
  
    ```vb  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
    ```  
  
     <span data-ttu-id="7df00-249">一般而言，事件處理常式的名稱並沒有改變。</span><span class="sxs-lookup"><span data-stu-id="7df00-249">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="7df00-250">傳回的型別並不會變更為`Task`因為事件處理常式必須是`Sub`在 Visual Basic 中的程序。</span><span class="sxs-lookup"><span data-stu-id="7df00-250">The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.</span></span>  
  
     <span data-ttu-id="7df00-251">專案從同步到非同步處理的轉換已完成。</span><span class="sxs-lookup"><span data-stu-id="7df00-251">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>  
  
##  <a name="BKMK_testAsynchSolution"></a>   
###  <span data-ttu-id="7df00-252"><a name="testAsynch"></a>若要測試非同步方案</span><span class="sxs-lookup"><span data-stu-id="7df00-252"><a name="testAsynch"></a> To test the asynchronous solution</span></span>  
  
1.  <span data-ttu-id="7df00-253">選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7df00-253">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
2.  <span data-ttu-id="7df00-254">類似同步方案的輸出應該會顯示。</span><span class="sxs-lookup"><span data-stu-id="7df00-254">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="7df00-255">但是，請注意下列差異。</span><span class="sxs-lookup"><span data-stu-id="7df00-255">However, notice the following differences.</span></span>  
  
    -   <span data-ttu-id="7df00-256">處理完成之後，結果不會同時發生。</span><span class="sxs-lookup"><span data-stu-id="7df00-256">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="7df00-257">例如，這兩個程式在 `startButton_Click` 中都包含程式碼行，會清除文字方塊。</span><span class="sxs-lookup"><span data-stu-id="7df00-257">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="7df00-258">目的是要清除文字方塊中，執行之間，如果您選擇**啟動**按鈕後出現結果集中的第二個時間。</span><span class="sxs-lookup"><span data-stu-id="7df00-258">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="7df00-259">在同步版本中，當下載完成且 UI 執行緒可以執行其他工作時，會在第二次顯示計數之前，清除文字方塊。</span><span class="sxs-lookup"><span data-stu-id="7df00-259">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="7df00-260">非同步版本，在文字方塊中會清除您選擇之後，立即**啟動** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7df00-260">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>  
  
    -   <span data-ttu-id="7df00-261">最重要的是，不會在下載期間封鎖 UI 執行緒。</span><span class="sxs-lookup"><span data-stu-id="7df00-261">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="7df00-262">您可以移動視窗或調整其大小，同時下載、計算及顯示 Web 資源。</span><span class="sxs-lookup"><span data-stu-id="7df00-262">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="7df00-263">如果其中一個網站變慢，或沒有回應，您可以取消作業選擇**關閉**按鈕 (在右上角的紅色欄位 x)。</span><span class="sxs-lookup"><span data-stu-id="7df00-263">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>  
  
##  <a name="BKMK_ReplaceGetByteArrayAsync"></a>   
###  <span data-ttu-id="7df00-264"><a name="GetURLContentsAsync"></a>若要使用.NET Framework 方法來取代方法 GetURLContentsAsync</span><span class="sxs-lookup"><span data-stu-id="7df00-264"><a name="GetURLContentsAsync"></a> To replace method GetURLContentsAsync with a .NET Framework method</span></span>  
  
1.  <span data-ttu-id="7df00-265">.NET Framework 4.5 提供許多您可以使用的非同步方法。</span><span class="sxs-lookup"><span data-stu-id="7df00-265">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="7df00-266">其中，<xref:System.Net.Http.HttpClient>方法<xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>，並在這個逐步解說什麼需要。</xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29> </xref:System.Net.Http.HttpClient></span><span class="sxs-lookup"><span data-stu-id="7df00-266">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="7df00-267">您可以使用這個方法，而不是 `GetURLContentsAsync` 方法，這是您在先前的程序中建立的方法。</span><span class="sxs-lookup"><span data-stu-id="7df00-267">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>  
  
     <span data-ttu-id="7df00-268">第一個步驟是在方法 `SumPageSizesAsync` 中建立 `HttpClient` 物件。</span><span class="sxs-lookup"><span data-stu-id="7df00-268">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="7df00-269">在方法的開頭，加入下列宣告。</span><span class="sxs-lookup"><span data-stu-id="7df00-269">Add the following declaration at the start of the method.</span></span>  
  
    ```vb  
    ' Declare an HttpClient object and increase the buffer size. The  
    ' default buffer size is 65,536.  
    Dim client As HttpClient =  
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
    ```  
  
2.  <span data-ttu-id="7df00-270">在 `SumPageSizesAsync,` 中將對 `GetURLContentsAsync` 方法的呼叫取代為對 `HttpClient` 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="7df00-270">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>  
  
    ```vb  
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
    ```  
  
3.  <span data-ttu-id="7df00-271">移除或取消註解您撰寫的 `GetURLContentsAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="7df00-271">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>  
  
4.  <span data-ttu-id="7df00-272">選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="7df00-272">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>  
  
     <span data-ttu-id="7df00-273">此版本之專案的行為應該符合「測試非同步方案」程序描述的行為，而且您只需要投入較少的精力。</span><span class="sxs-lookup"><span data-stu-id="7df00-273">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>  
  
##  <span data-ttu-id="7df00-274"><a name="BKMK_CompleteCodeExamples"></a>範例</span><span class="sxs-lookup"><span data-stu-id="7df00-274"><a name="BKMK_CompleteCodeExamples"></a> Example</span></span>  
 <span data-ttu-id="7df00-275">下列程式碼包含使用您撰寫的 `GetURLContentsAsync` 方法，從同步轉換為非同步方案的完整範例。</span><span class="sxs-lookup"><span data-stu-id="7df00-275">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="7df00-276">請注意，它極為類似原始的同步方案。</span><span class="sxs-lookup"><span data-stu-id="7df00-276">Notice that it strongly resembles the original, synchronous solution.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        ' Disable the button until the operation is complete.  
        startButton.IsEnabled = False  
  
        resultsTextBox.Clear()  
  
        '' One-step async call.  
        Await SumPageSizesAsync()  
  
        ' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
  
        ' Reenable the button in case you want to run the operation again.  
        startButton.IsEnabled = True  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            Dim urlContents As Byte() = Await GetURLContentsAsync(url)  
  
            ' The previous line abbreviates the following two assignment statements.  
  
            '//<snippet21>  
            ' GetURLContentsAsync returns a task. At completion, the task  
            ' produces a byte array.  
            'Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)  
            'Dim urlContents As Byte() = Await getContentsTask  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
    End Function  
  
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())  
  
        ' The downloaded resource ends up in the variable named content.  
        Dim content = New MemoryStream()  
  
        ' Initialize an HttpWebRequest for the current URL.  
        Dim webReq = CType(WebRequest.Create(url), HttpWebRequest)  
  
        ' Send the request to the Internet resource and wait for  
        ' the response.  
        Using response As WebResponse = Await webReq.GetResponseAsync()  
  
            ' The previous statement abbreviates the following two statements.  
  
            'Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()  
            'Using response As WebResponse = Await responseTask  
  
            ' Get the data stream that is associated with the specified URL.  
            Using responseStream As Stream = response.GetResponseStream()  
                ' Read the bytes in responseStream and copy them to content.    
                Await responseStream.CopyToAsync(content)  
  
                ' The previous statement abbreviates the following two statements.  
  
                ' CopyToAsync returns a Task, not a Task<T>.  
                'Dim copyTask As Task = responseStream.CopyToAsync(content)  
  
                ' When copyTask is completed, content contains a copy of  
                ' responseStream.  
                'Await copyTask  
            End Using  
        End Using  
  
        ' Return the result as a byte array.  
        Return content.ToArray()  
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
  
 <span data-ttu-id="7df00-277">下列程式碼包含使用 `HttpClient` 方法 `GetByteArrayAsync` 之方案的完整範例。</span><span class="sxs-lookup"><span data-stu-id="7df00-277">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>  
  
```vb  
' Add the following Imports statements, and add a reference for System.Net.Http.  
Imports System.Net.Http  
Imports System.Net  
Imports System.IO  
  
Class MainWindow  
  
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click  
  
        resultsTextBox.Clear()  
  
        ' Disable the button until the operation is complete.  
        startButton.IsEnabled = False  
  
        ' One-step async call.  
        Await SumPageSizesAsync()  
  
        '' Two-step async call.  
        'Dim sumTask As Task = SumPageSizesAsync()  
        'Await sumTask  
  
        resultsTextBox.Text &= vbCrLf & "Control returned to button1_Click."  
  
        ' Reenable the button in case you want to run the operation again.  
        startButton.IsEnabled = True  
    End Sub  
  
    Private Async Function SumPageSizesAsync() As Task  
  
        ' Declare an HttpClient object and increase the buffer size. The  
        ' default buffer size is 65,536.  
        Dim client As HttpClient =  
            New HttpClient() With {.MaxResponseContentBufferSize = 1000000}  
  
        ' Make a list of web addresses.  
        Dim urlList As List(Of String) = SetUpURLList()  
  
        Dim total = 0  
        For Each url In urlList  
            ' GetByteArrayAsync returns a task. At completion, the task  
            ' produces a byte array.  
            Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)  
  
            ' The following two lines can replace the previous assignment statement.  
            'Dim getContentsTask As Task(Of Byte()) = client.GetByteArrayAsync(url)  
            'Dim urlContents As Byte() = Await getContentsTask  
  
            DisplayResults(url, urlContents)  
  
            ' Update the total.  
            total += urlContents.Length  
        Next  
  
        ' Display the total count for all of the websites.  
        resultsTextBox.Text &= String.Format(vbCrLf & vbCrLf &  
                                             "Total bytes returned:  {0}" & vbCrLf, total)  
    End Function  
  
    Private Function SetUpURLList() As List(Of String)  
  
        Dim urls = New List(Of String) From  
            {  
                "http://msdn.microsoft.com/library/windows/apps/br211380.aspx",  
                "http://msdn.microsoft.com",  
                "http://msdn.microsoft.com/library/hh290136.aspx",  
                "http://msdn.microsoft.com/library/ee256749.aspx",  
                "http://msdn.microsoft.com/library/hh290138.aspx",  
                "http://msdn.microsoft.com/library/hh290140.aspx",  
                "http://msdn.microsoft.com/library/dd470362.aspx",  
                "http://msdn.microsoft.com/library/aa578028.aspx",  
                "http://msdn.microsoft.com/library/ms404677.aspx",  
                "http://msdn.microsoft.com/library/ff730837.aspx"  
            }  
        Return urls  
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
  
## <a name="see-also"></a><span data-ttu-id="7df00-278">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7df00-278">See Also</span></span>  
 <span data-ttu-id="7df00-279">[非同步範例︰ 存取 Web 逐步解說 （C# 和 Visual Basic）](http://go.microsoft.com/fwlink/?LinkId=255191) </span><span class="sxs-lookup"><span data-stu-id="7df00-279">[Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](http://go.microsoft.com/fwlink/?LinkId=255191) </span></span>  
<span data-ttu-id="7df00-280"> [Await 運算子](../../../../visual-basic/language-reference/operators/await-operator.md) </span><span class="sxs-lookup"><span data-stu-id="7df00-280"> [Await Operator](../../../../visual-basic/language-reference/operators/await-operator.md) </span></span>  
<span data-ttu-id="7df00-281"> [非同步處理](../../../../visual-basic/language-reference/modifiers/async.md) </span><span class="sxs-lookup"><span data-stu-id="7df00-281"> [Async](../../../../visual-basic/language-reference/modifiers/async.md) </span></span>  
<span data-ttu-id="7df00-282"> [非同步程式設計使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span><span class="sxs-lookup"><span data-stu-id="7df00-282"> [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md) </span></span>  
<span data-ttu-id="7df00-283"> [非同步方法的傳回類型 (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span><span class="sxs-lookup"><span data-stu-id="7df00-283"> [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md) </span></span>  
<span data-ttu-id="7df00-284"> [工作為基礎的非同步程式設計 (TAP)](http://go.microsoft.com/fwlink/?LinkId=204847) </span><span class="sxs-lookup"><span data-stu-id="7df00-284"> [Task-based Asynchronous Programming (TAP)](http://go.microsoft.com/fwlink/?LinkId=204847) </span></span>  
<span data-ttu-id="7df00-285"> [如何︰ 使用 Task.WhenAll (Visual Basic) 來擴充非同步逐步解說](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md) </span><span class="sxs-lookup"><span data-stu-id="7df00-285"> [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md) </span></span>  
<span data-ttu-id="7df00-286"> [如何︰ 同時發出多個 Web 要求使用 Async 和 Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)</span><span class="sxs-lookup"><span data-stu-id="7df00-286"> [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)</span></span>
