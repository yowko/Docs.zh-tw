---
title: 逐步解說：使用 Async 和 Await 存取 Web （Visual Basic）
ms.date: 07/20/2015
ms.assetid: 84fd047f-fab8-4d89-8ced-104fb7310a91
ms.openlocfilehash: 2d9d3ea3d55fcd3a59039f4b8b93f37df35bf86d
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/27/2019
ms.locfileid: "71351915"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-visual-basic"></a><span data-ttu-id="a06f3-102">逐步解說：使用 Async 和 Await 存取 Web （Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="a06f3-102">Walkthrough: Accessing the Web by Using Async and Await (Visual Basic)</span></span>

<span data-ttu-id="a06f3-103">您可以使用 async/await 功能，以更容易且直觀的方式撰寫非同步程式。</span><span class="sxs-lookup"><span data-stu-id="a06f3-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="a06f3-104">您可以撰寫非同步程式碼，使其看起來像是同步程式碼，讓編譯器處理困難的回呼函式和非同步程式碼通常需要的接續。</span><span class="sxs-lookup"><span data-stu-id="a06f3-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>

<span data-ttu-id="a06f3-105">如需非同步功能的詳細資訊，請參閱[使用 async 和 Await 進行非同步程式設計（Visual Basic）](../../../../visual-basic/programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="a06f3-105">For more information about the Async feature, see [Asynchronous Programming with Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="a06f3-106">本逐步解說從同步化 Windows Presentation Foundation (WPF) 應用程式開始，該應用程式會加總網站清單中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="a06f3-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="a06f3-107">然後逐步解說會藉由使用新功能，將應用程式轉換為非同步解決方案。</span><span class="sxs-lookup"><span data-stu-id="a06f3-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>

<span data-ttu-id="a06f3-108">如果您不想要自行建立應用程式，您可以下載「非同步範例：從C# [開發人員程式碼範例](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)存取 Web 逐步解說（和 Visual Basic）。</span><span class="sxs-lookup"><span data-stu-id="a06f3-108">If you don't want to build the applications yourself, you can download "Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)" from [Developer Code Samples](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

<span data-ttu-id="a06f3-109">在這個逐步解說中，您將完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="a06f3-109">In this walkthrough, you complete the following tasks:</span></span>

> [!div class="checklist"]
>
> - [<span data-ttu-id="a06f3-110">建立 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="a06f3-110">Create a WPF application</span></span>](#create-a-wpf-application)
> - [<span data-ttu-id="a06f3-111">設計簡單的 WPF Mainwindow.xaml</span><span class="sxs-lookup"><span data-stu-id="a06f3-111">Design a simple WPF MainWindow</span></span>](#design-a-simple-wpf-mainwindow)
> - [<span data-ttu-id="a06f3-112">新增參考</span><span class="sxs-lookup"><span data-stu-id="a06f3-112">Add a reference</span></span>](#add-a-reference)
> - [<span data-ttu-id="a06f3-113">新增必要的 Imports 語句</span><span class="sxs-lookup"><span data-stu-id="a06f3-113">Add necessary Imports statements</span></span>](#add-necessary-imports-statements)
> - [<span data-ttu-id="a06f3-114">建立同步應用程式</span><span class="sxs-lookup"><span data-stu-id="a06f3-114">Create a synchronous application</span></span>](#create-a-synchronous-application)
> - [<span data-ttu-id="a06f3-115">測試同步解決方案</span><span class="sxs-lookup"><span data-stu-id="a06f3-115">Test the synchronous solution</span></span>](#test-the-synchronous-solution)
> - [<span data-ttu-id="a06f3-116">將 Geturlcontents 轉換轉換為非同步方法</span><span class="sxs-lookup"><span data-stu-id="a06f3-116">Convert GetURLContents to an asynchronous method</span></span>](#convert-geturlcontents-to-an-asynchronous-method)
> - [<span data-ttu-id="a06f3-117">將 Sumpagesizes 轉換轉換為非同步方法</span><span class="sxs-lookup"><span data-stu-id="a06f3-117">Convert SumPageSizes to an asynchronous method</span></span>](#convert-sumpagesizes-to-an-asynchronous-method)
> - [<span data-ttu-id="a06f3-118">將 startButton_Click 轉換為非同步方法</span><span class="sxs-lookup"><span data-stu-id="a06f3-118">Convert startButton_Click to an asynchronous method</span></span>](#convert-startbutton_click-to-an-asynchronous-method)
> - [<span data-ttu-id="a06f3-119">測試非同步方案</span><span class="sxs-lookup"><span data-stu-id="a06f3-119">Test the asynchronous solution</span></span>](#test-the-asynchronous-solution)
> - [<span data-ttu-id="a06f3-120">將 Geturlcontentsasync 為方法取代為 .NET Framework 方法</span><span class="sxs-lookup"><span data-stu-id="a06f3-120">Replace the GetURLContentsAsync method with a .NET Framework method</span></span>](#replace-the-geturlcontentsasync-method-with-a-net-framework-method)

<span data-ttu-id="a06f3-121">如需完整的非同步範例，請參閱[範例](#example)一節。</span><span class="sxs-lookup"><span data-stu-id="a06f3-121">See the [Example](#example) section for the complete asynchronous example.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a06f3-122">必要條件</span><span class="sxs-lookup"><span data-stu-id="a06f3-122">Prerequisites</span></span>

<span data-ttu-id="a06f3-123">您的電腦上必須安裝 Visual Studio 2012 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="a06f3-123">Visual Studio 2012 or later must be installed on your computer.</span></span> <span data-ttu-id="a06f3-124">如需詳細資訊，請參閱 Visual Studio[下載](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)頁面。</span><span class="sxs-lookup"><span data-stu-id="a06f3-124">For more information, see the Visual Studio [Downloads](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) page.</span></span>

## <a name="create-a-wpf-application"></a><span data-ttu-id="a06f3-125">建立 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="a06f3-125">Create a WPF application</span></span>

1. <span data-ttu-id="a06f3-126">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="a06f3-126">Start Visual Studio.</span></span>

2. <span data-ttu-id="a06f3-127">在功能表列上，選擇 [檔案]、[新增]、[專案]。</span><span class="sxs-lookup"><span data-stu-id="a06f3-127">On the menu bar, choose **File**, **New**, **Project**.</span></span>

    <span data-ttu-id="a06f3-128">[ **新增專案** ] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="a06f3-128">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="a06f3-129">在 [**已安裝的範本**] 窗格中，選擇 [Visual Basic]，然後從專案類型清單中選擇 [ **WPF 應用程式**]。</span><span class="sxs-lookup"><span data-stu-id="a06f3-129">In the **Installed Templates** pane, choose Visual Basic, and then choose **WPF Application** from the list of project types.</span></span>

4. <span data-ttu-id="a06f3-130">在 [名稱] 文字方塊中，輸入 `AsyncExampleWPF`，然後選擇 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="a06f3-130">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>

    <span data-ttu-id="a06f3-131">新的專案隨即會出現在方案總管中。</span><span class="sxs-lookup"><span data-stu-id="a06f3-131">The new project appears in **Solution Explorer**.</span></span>

## <a name="design-a-simple-wpf-mainwindow"></a><span data-ttu-id="a06f3-132">設計簡單的 WPF MainWindow</span><span class="sxs-lookup"><span data-stu-id="a06f3-132">Design a simple WPF MainWindow</span></span>

1. <span data-ttu-id="a06f3-133">在 Visual Studio 程式碼編輯器中，選擇 [ **MainWindow.xaml** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a06f3-133">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

2. <span data-ttu-id="a06f3-134">如果未顯示 [工具箱] 視窗，請選擇 [檢視] 功能表，然後選擇 [工具箱]。</span><span class="sxs-lookup"><span data-stu-id="a06f3-134">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>

3. <span data-ttu-id="a06f3-135">將 **Button** 控制項和 **TextBox** 控制項加入 [MainWindow] 視窗。</span><span class="sxs-lookup"><span data-stu-id="a06f3-135">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>

4. <span data-ttu-id="a06f3-136">反白顯示 **TextBox** 控制項，並在 [屬性] 視窗中，設定下列值：</span><span class="sxs-lookup"><span data-stu-id="a06f3-136">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="a06f3-137">將 [名稱] 屬性設定為 `resultsTextBox`。</span><span class="sxs-lookup"><span data-stu-id="a06f3-137">Set the **Name** property to `resultsTextBox`.</span></span>

    - <span data-ttu-id="a06f3-138">將 [高度] 屬性設為 250。</span><span class="sxs-lookup"><span data-stu-id="a06f3-138">Set the **Height** property to 250.</span></span>

    - <span data-ttu-id="a06f3-139">將 [寬度] 屬性設為 500。</span><span class="sxs-lookup"><span data-stu-id="a06f3-139">Set the **Width** property to 500.</span></span>

    - <span data-ttu-id="a06f3-140">在 [文字] 索引標籤上，指定等寬字型，例如 Lucida Console 或全域等寬。</span><span class="sxs-lookup"><span data-stu-id="a06f3-140">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>

5. <span data-ttu-id="a06f3-141">反白顯示 **Button** 控制項，並在 [屬性] 視窗中，設定下列值：</span><span class="sxs-lookup"><span data-stu-id="a06f3-141">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>

    - <span data-ttu-id="a06f3-142">將 [名稱] 屬性設定為 `startButton`。</span><span class="sxs-lookup"><span data-stu-id="a06f3-142">Set the **Name** property to `startButton`.</span></span>

    - <span data-ttu-id="a06f3-143">將 [內容] 屬性的值從 **Button** 變更為 **Start**。</span><span class="sxs-lookup"><span data-stu-id="a06f3-143">Change the value of the **Content** property from **Button** to **Start**.</span></span>

6. <span data-ttu-id="a06f3-144">放置文字方塊和按鈕，使兩者都出現在 [MainWindow] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="a06f3-144">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>

    <span data-ttu-id="a06f3-145">如需 WPF XAML 設計工具的詳細資訊，請參閱[使用 XAML 設計工具建立 UI](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="a06f3-145">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>

## <a name="add-a-reference"></a><span data-ttu-id="a06f3-146">加入參考</span><span class="sxs-lookup"><span data-stu-id="a06f3-146">Add a reference</span></span>

1. <span data-ttu-id="a06f3-147">在方案總管中，反白顯示您的專案名稱。</span><span class="sxs-lookup"><span data-stu-id="a06f3-147">In **Solution Explorer**, highlight your project's name.</span></span>

2. <span data-ttu-id="a06f3-148">在功能表列上，依序選擇 [專案] 和 [加入參考]。</span><span class="sxs-lookup"><span data-stu-id="a06f3-148">On the menu bar, choose **Project**, **Add Reference**.</span></span>

    <span data-ttu-id="a06f3-149">[參考管理員] 對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="a06f3-149">The **Reference Manager** dialog box appears.</span></span>

3. <span data-ttu-id="a06f3-150">在對話方塊上方，請確認專案的目標是 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="a06f3-150">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>

4. <span data-ttu-id="a06f3-151">在 [組件] 區域中，選擇 [Framework] (如果尚未選擇)。</span><span class="sxs-lookup"><span data-stu-id="a06f3-151">In the **Assemblies** area, choose **Framework** if it isn’t already chosen.</span></span>

5. <span data-ttu-id="a06f3-152">在名稱清單中，選取 [System.Net.Http] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="a06f3-152">In the list of names, select the **System.Net.Http** check box.</span></span>

6. <span data-ttu-id="a06f3-153">選擇 [確定] 按鈕以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="a06f3-153">Choose the **OK** button to close the dialog box.</span></span>

## <a name="add-necessary-imports-statements"></a><span data-ttu-id="a06f3-154">新增必要的 Imports 語句</span><span class="sxs-lookup"><span data-stu-id="a06f3-154">Add necessary Imports statements</span></span>

1. <span data-ttu-id="a06f3-155">在**方案總管**中，開啟 mainwindow.xaml 的快捷方式功能表，然後選擇 [ **View Code**]。</span><span class="sxs-lookup"><span data-stu-id="a06f3-155">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.vb, and then choose **View Code**.</span></span>

2. <span data-ttu-id="a06f3-156">在程式碼`Imports`檔案頂端新增下列語句（如果尚未存在的話）。</span><span class="sxs-lookup"><span data-stu-id="a06f3-156">Add the following `Imports` statements at the top of the code file if they’re not already present.</span></span>

    ```vb
    Imports System.Net.Http
    Imports System.Net
    Imports System.IO
    ```

## <a name="create-a-synchronous-application"></a><span data-ttu-id="a06f3-157">建立同步應用程式</span><span class="sxs-lookup"><span data-stu-id="a06f3-157">Create a synchronous application</span></span>

1. <span data-ttu-id="a06f3-158">在設計視窗 mainwindow.xaml 中，按兩下 [**開始**] 按鈕，以在 mainwindow.xaml 中建立`startButton_Click`事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="a06f3-158">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.vb.</span></span>

2. <span data-ttu-id="a06f3-159">在 Mainwindow.xaml 中，將下列程式碼複製到的主體`startButton_Click`中：</span><span class="sxs-lookup"><span data-stu-id="a06f3-159">In MainWindow.xaml.vb, copy the following code into the body of `startButton_Click`:</span></span>

    ```vb
    resultsTextBox.Clear()
    SumPageSizes()
    resultsTextBox.Text &= vbCrLf & "Control returned to startButton_Click."
    ```

    <span data-ttu-id="a06f3-160">程式碼會呼叫方法，該方法會驅動應用程式 `SumPageSizes`，並且在控制項返回 `startButton_Click` 時顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="a06f3-160">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>

3. <span data-ttu-id="a06f3-161">同步方案的程式碼包含下列四種方法：</span><span class="sxs-lookup"><span data-stu-id="a06f3-161">The code for the synchronous solution contains the following four methods:</span></span>

    - <span data-ttu-id="a06f3-162">`SumPageSizes`，會從 `SetUpURLList` 取得網頁 URL 的清單，然後呼叫 `GetURLContents` 和 `DisplayResults` 以處理每個 URL。</span><span class="sxs-lookup"><span data-stu-id="a06f3-162">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>

    - <span data-ttu-id="a06f3-163">`SetUpURLList`，會製作並傳回網址清單。</span><span class="sxs-lookup"><span data-stu-id="a06f3-163">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>

    - <span data-ttu-id="a06f3-164">`GetURLContents`，會下載每個網站的內容，並傳回內容做為位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="a06f3-164">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>

    - <span data-ttu-id="a06f3-165">`DisplayResults`，會顯示每個 URL 的位元組陣列中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="a06f3-165">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>

    <span data-ttu-id="a06f3-166">複製下列四種方法，然後將它們貼在 mainwindow.xaml `startButton_Click`的事件處理常式底下：</span><span class="sxs-lookup"><span data-stu-id="a06f3-166">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.vb:</span></span>

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
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
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
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub
    ```

## <a name="test-the-synchronous-solution"></a><span data-ttu-id="a06f3-167">測試同步解決方案</span><span class="sxs-lookup"><span data-stu-id="a06f3-167">Test the synchronous solution</span></span>

1. <span data-ttu-id="a06f3-168">選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="a06f3-168">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="a06f3-169">應該會顯示如下列清單的輸出：</span><span class="sxs-lookup"><span data-stu-id="a06f3-169">Output that resembles the following list should appear:</span></span>

    ```console
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

    <span data-ttu-id="a06f3-170">請注意，需要花費幾秒鐘以顯示計數。</span><span class="sxs-lookup"><span data-stu-id="a06f3-170">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="a06f3-171">在這段期間，在等候下載要求資源的同時，會封鎖 UI 執行緒。</span><span class="sxs-lookup"><span data-stu-id="a06f3-171">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="a06f3-172">如此一來，您就無法在選擇 [開始] 按鈕之後，移動、最大化、最小化，或甚至關閉顯示視窗。</span><span class="sxs-lookup"><span data-stu-id="a06f3-172">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="a06f3-173">這些努力會失敗，直到位元組計數開始出現為止。</span><span class="sxs-lookup"><span data-stu-id="a06f3-173">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="a06f3-174">如果網站沒有回應，也不會指出失敗的站台。</span><span class="sxs-lookup"><span data-stu-id="a06f3-174">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="a06f3-175">甚至難以停止等候以及關閉程式。</span><span class="sxs-lookup"><span data-stu-id="a06f3-175">It is difficult even to stop waiting and close the program.</span></span>

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a><span data-ttu-id="a06f3-176">將 GetURLContents 轉換為非同步方法</span><span class="sxs-lookup"><span data-stu-id="a06f3-176">Convert GetURLContents to an asynchronous method</span></span>

1. <span data-ttu-id="a06f3-177">若要將同步方案轉換成非同步方案，最佳的起點是在`GetURLContents` ，因為呼叫<xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType>方法及<xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType>方法是應用程式存取 web 的位置。</span><span class="sxs-lookup"><span data-stu-id="a06f3-177">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest.GetResponse%2A?displayProperty=nameWithType> method and to the <xref:System.IO.Stream.CopyTo%2A?displayProperty=nameWithType> method are where the application accesses the web.</span></span> <span data-ttu-id="a06f3-178">.NET Framework 會讓轉換變得簡單，方法是提供這兩種方法的非同步版本。</span><span class="sxs-lookup"><span data-stu-id="a06f3-178">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>

    <span data-ttu-id="a06f3-179">如需 `GetURLContents` 中所用之方法的詳細資訊，請參閱 <xref:System.Net.WebRequest>。</span><span class="sxs-lookup"><span data-stu-id="a06f3-179">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a06f3-180">當您依照本逐步解說中的步驟時，會出現數個編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="a06f3-180">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="a06f3-181">您可以略過它們，並繼續進行本逐步解說。</span><span class="sxs-lookup"><span data-stu-id="a06f3-181">You can ignore them and continue with the walkthrough.</span></span>

    <span data-ttu-id="a06f3-182">將在 `GetURLContents` 的第三行呼叫的方法從 `GetResponse` 變更為非同步、以工作為基礎的 <xref:System.Net.WebRequest.GetResponseAsync%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="a06f3-182">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>

    ```vb
    Using response As WebResponse = webReq.GetResponseAsync()
    ```

2. <span data-ttu-id="a06f3-183">`GetResponseAsync` 會傳回 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="a06f3-183">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="a06f3-184">在此情況下，工作傳回變數 `TResult` 具有類型 <xref:System.Net.WebResponse>。</span><span class="sxs-lookup"><span data-stu-id="a06f3-184">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="a06f3-185">工作承諾會在已下載要求的資料及工作執行完成之後，產生實際 `WebResponse` 物件。</span><span class="sxs-lookup"><span data-stu-id="a06f3-185">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>

    <span data-ttu-id="a06f3-186">若要從`WebResponse`工作中取出值，請將[Await](../../../../visual-basic/language-reference/operators/await-operator.md)運算子套用`GetResponseAsync`至的呼叫，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="a06f3-186">To retrieve the `WebResponse` value from the task, apply an [Await](../../../../visual-basic/language-reference/operators/await-operator.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>

    ```vb
    Using response As WebResponse = Await webReq.GetResponseAsync()
    ```

    <span data-ttu-id="a06f3-187">`Await` 運算子會暫停執行目前的 `GetURLContents` 方法，直到等候的工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="a06f3-187">The `Await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="a06f3-188">同時，控制項會返回非同步方法的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="a06f3-188">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="a06f3-189">在此範例中，目前方法是 `GetURLContents`，呼叫端是 `SumPageSizes`。</span><span class="sxs-lookup"><span data-stu-id="a06f3-189">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="a06f3-190">當工作完成時，承諾的 `WebResponse` 物件會以等候工作之值的形式產生，而且會指派給變數 `response`。</span><span class="sxs-lookup"><span data-stu-id="a06f3-190">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>

    <span data-ttu-id="a06f3-191">前一個陳述式可分成下列兩個陳述式，以釐清會發生什麼情況。</span><span class="sxs-lookup"><span data-stu-id="a06f3-191">The previous statement can be separated into the following two statements to clarify what happens.</span></span>

    ```vb
    Dim responseTask As Task(Of WebResponse) = webReq.GetResponseAsync()
    Using response As WebResponse = Await responseTask
    ```

    <span data-ttu-id="a06f3-192">對 `webReq.GetResponseAsync` 的呼叫會傳回 `Task(Of WebResponse)` 或 `Task<WebResponse>`。</span><span class="sxs-lookup"><span data-stu-id="a06f3-192">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="a06f3-193">然後，會將`WebResponse` 運算子套用至工作以抓取值。`Await`</span><span class="sxs-lookup"><span data-stu-id="a06f3-193">Then an `Await` operator is applied to the task to retrieve the `WebResponse` value.</span></span>

    <span data-ttu-id="a06f3-194">如果非同步方法有不需要依賴工作完成的工作要執行，此方法可以在呼叫非同步方法之後，以及套用 await 運算子之前，繼續這兩個陳述式之間的工作。</span><span class="sxs-lookup"><span data-stu-id="a06f3-194">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the await operator is applied.</span></span> <span data-ttu-id="a06f3-195">如需範例，請參閱[如何：使用 Async 和 Await （Visual Basic）](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) ，同時發出多個 Web 要求，以及[如何：使用 System.threading.tasks.task.whenall （Visual Basic）](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)擴充非同步逐步解說。</span><span class="sxs-lookup"><span data-stu-id="a06f3-195">For examples, see [How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

3. <span data-ttu-id="a06f3-196">由於您在上一個步驟中加入 `Await` 運算子，所以發生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="a06f3-196">Because you added the `Await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="a06f3-197">運算子只能用在以[Async](../../../../visual-basic/language-reference/modifiers/async.md)修飾詞標示的方法中。</span><span class="sxs-lookup"><span data-stu-id="a06f3-197">The operator can be used only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="a06f3-198">當您重複轉換步驟以將對 `CopyTo` 的呼叫取代為對 `CopyToAsync` 的呼叫時，略過錯誤。</span><span class="sxs-lookup"><span data-stu-id="a06f3-198">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>

    - <span data-ttu-id="a06f3-199">變更方法的名稱，該方法會呼叫 <xref:System.IO.Stream.CopyToAsync%2A>。</span><span class="sxs-lookup"><span data-stu-id="a06f3-199">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>

    - <span data-ttu-id="a06f3-200">`CopyTo` 或 `CopyToAsync` 方法會將位元組複製到其引數，`content`，並不會傳回有意義的值。</span><span class="sxs-lookup"><span data-stu-id="a06f3-200">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="a06f3-201">在同步版本中，呼叫 `CopyTo` 是簡單的陳述式，不會傳回值。</span><span class="sxs-lookup"><span data-stu-id="a06f3-201">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="a06f3-202">非同步版本，`CopyToAsync`，傳回 <xref:System.Threading.Tasks.Task>。</span><span class="sxs-lookup"><span data-stu-id="a06f3-202">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="a06f3-203">工作函式，例如 "Task(void)"，讓方法等候。</span><span class="sxs-lookup"><span data-stu-id="a06f3-203">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="a06f3-204">將 `Await` 或 `await` 套用至對 `CopyToAsync` 的呼叫，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="a06f3-204">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>

        ```vb
        Await responseStream.CopyToAsync(content)
        ```

         <span data-ttu-id="a06f3-205">前一個陳述式縮寫下列兩行程式碼。</span><span class="sxs-lookup"><span data-stu-id="a06f3-205">The previous statement abbreviates the following two lines of code.</span></span>

        ```vb
        ' CopyToAsync returns a Task, not a Task<T>.
        Dim copyTask As Task = responseStream.CopyToAsync(content)

        ' When copyTask is completed, content contains a copy of
        ' responseStream.
        Await copyTask
        ```

4. <span data-ttu-id="a06f3-206">`GetURLContents` 中還需要完成的工作是調整方法簽章。</span><span class="sxs-lookup"><span data-stu-id="a06f3-206">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="a06f3-207">您只能在以`Await` [Async](../../../../visual-basic/language-reference/modifiers/async.md)修飾詞標示的方法中使用運算子。</span><span class="sxs-lookup"><span data-stu-id="a06f3-207">You can use the `Await` operator only in methods that are marked with the [Async](../../../../visual-basic/language-reference/modifiers/async.md) modifier.</span></span> <span data-ttu-id="a06f3-208">新增修飾詞以將方法標示為「非同步方法」，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="a06f3-208">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>

    ```vb
    Private Async Function GetURLContents(url As String) As Byte()
    ```

5. <span data-ttu-id="a06f3-209">非同步方法的傳回型別只能是<xref:System.Threading.Tasks.Task>、。 <xref:System.Threading.Tasks.Task%601></span><span class="sxs-lookup"><span data-stu-id="a06f3-209">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="a06f3-210">在 Visual Basic 中，方法必須是 `Function`，會傳回 `Task` 或 `Task(Of T)`，或者方法必須是 `Sub`。</span><span class="sxs-lookup"><span data-stu-id="a06f3-210">In Visual Basic, the method must be a `Function` that returns a `Task` or a `Task(Of T)`, or the method must be a `Sub`.</span></span> <span data-ttu-id="a06f3-211">通常， `Sub`方法只會用於非同步事件處理常式，其中`Sub`是必要的。</span><span class="sxs-lookup"><span data-stu-id="a06f3-211">Typically, a `Sub` method  is used only in an async event handler, where `Sub` is required.</span></span> <span data-ttu-id="a06f3-212">在其他情況下，如果`Task(T)`完成的方法有傳回類型 T 之值的[Return](../../../../visual-basic/language-reference/statements/return-statement.md)語句，而且您使用`Task` （如果完成的方法不會傳回有意義的值），則會使用。</span><span class="sxs-lookup"><span data-stu-id="a06f3-212">In other cases, you use `Task(T)` if the completed method has a [Return](../../../../visual-basic/language-reference/statements/return-statement.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span>

    <span data-ttu-id="a06f3-213">如需詳細資訊，請參閱[非同步傳回類型（Visual Basic）](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="a06f3-213">For more information, see [Async Return Types (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md).</span></span>

    <span data-ttu-id="a06f3-214">方法 `GetURLContents` 有 return 陳述式，陳述式會傳回位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="a06f3-214">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="a06f3-215">因此，非同步版本的傳回類型是 Task(T)，其中 T 是位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="a06f3-215">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="a06f3-216">在方法簽章中進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="a06f3-216">Make the following changes in the method signature:</span></span>

    - <span data-ttu-id="a06f3-217">將傳回型別變更為 `Task(Of Byte())`。</span><span class="sxs-lookup"><span data-stu-id="a06f3-217">Change the return type to `Task(Of Byte())`.</span></span>

    - <span data-ttu-id="a06f3-218">依照慣例，非同步方法的名稱會以 "Async" 結尾，所以重新命名方法 `GetURLContentsAsync`。</span><span class="sxs-lookup"><span data-stu-id="a06f3-218">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>

    <span data-ttu-id="a06f3-219">下列程式碼會顯示這些變更。</span><span class="sxs-lookup"><span data-stu-id="a06f3-219">The following code shows these changes.</span></span>

    ```vb
    Private Async Function GetURLContentsAsync(url As String) As Task(Of Byte())
    ```

    <span data-ttu-id="a06f3-220">只要這幾個變更，`GetURLContents` 至非同步方法的轉換就能完成。</span><span class="sxs-lookup"><span data-stu-id="a06f3-220">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a><span data-ttu-id="a06f3-221">將 SumPageSizes 轉換為非同步方法</span><span class="sxs-lookup"><span data-stu-id="a06f3-221">Convert SumPageSizes to an asynchronous method</span></span>

1. <span data-ttu-id="a06f3-222">針對 `SumPageSizes` 重複上述程序的步驟。</span><span class="sxs-lookup"><span data-stu-id="a06f3-222">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="a06f3-223">首先，將對 `GetURLContents` 的呼叫變更為非同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="a06f3-223">First, change the call to `GetURLContents` to an asynchronous call.</span></span>

    - <span data-ttu-id="a06f3-224">如果您尚未這麼做，請變更方法的名稱，該方法是從 `GetURLContents` 呼叫至 `GetURLContentsAsync`。</span><span class="sxs-lookup"><span data-stu-id="a06f3-224">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>

    - <span data-ttu-id="a06f3-225">將 `Await` 套用至工作，`GetURLContentsAsync` 會傳回該工作以取得位元組陣列值。</span><span class="sxs-lookup"><span data-stu-id="a06f3-225">Apply `Await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>

    <span data-ttu-id="a06f3-226">下列程式碼會顯示這些變更。</span><span class="sxs-lookup"><span data-stu-id="a06f3-226">The following code shows these changes.</span></span>

    ```vb
    Dim urlContents As Byte() = Await GetURLContentsAsync(url)
    ```

    <span data-ttu-id="a06f3-227">前一個指派縮寫下列兩行程式碼。</span><span class="sxs-lookup"><span data-stu-id="a06f3-227">The previous assignment abbreviates the following two lines of code.</span></span>

    ```vb
    ' GetURLContentsAsync returns a task. At completion, the task
    ' produces a byte array.
    Dim getContentsTask As Task(Of Byte()) = GetURLContentsAsync(url)
    Dim urlContents As Byte() = Await getContentsTask
    ```

2. <span data-ttu-id="a06f3-228">在方法簽章中進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="a06f3-228">Make the following changes in the method's signature:</span></span>

    - <span data-ttu-id="a06f3-229">以 `Async` 修飾詞來標示方法。</span><span class="sxs-lookup"><span data-stu-id="a06f3-229">Mark the method with the `Async` modifier.</span></span>

    - <span data-ttu-id="a06f3-230">將 "Async" 加入至方法名稱。</span><span class="sxs-lookup"><span data-stu-id="a06f3-230">Add "Async" to the method name.</span></span>

    - <span data-ttu-id="a06f3-231">這次沒有任何工作傳回變數，T，因為 `SumPageSizesAsync` 並未傳回 T 的值。(這個方法沒有任何 `Return` 陳述式)。不過，方法必須傳回 `Task` 才可以等候。</span><span class="sxs-lookup"><span data-stu-id="a06f3-231">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `Return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="a06f3-232">因此，請將方法類型從`Sub`變更`Function`為。</span><span class="sxs-lookup"><span data-stu-id="a06f3-232">Therefore, change the method type from `Sub` to `Function`.</span></span> <span data-ttu-id="a06f3-233">函式的傳回類型是 `Task`。</span><span class="sxs-lookup"><span data-stu-id="a06f3-233">The return type of the function is `Task`.</span></span>

    <span data-ttu-id="a06f3-234">下列程式碼會顯示這些變更。</span><span class="sxs-lookup"><span data-stu-id="a06f3-234">The following code shows these changes.</span></span>

    ```vb
    Private Async Function SumPageSizesAsync() As Task
    ```

    <span data-ttu-id="a06f3-235">`SumPageSizes` 至 `SumPageSizesAsync` 的轉換完成。</span><span class="sxs-lookup"><span data-stu-id="a06f3-235">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>

## <a name="convert-startbutton_click-to-an-asynchronous-method"></a><span data-ttu-id="a06f3-236">將 startButton_Click 轉換為非同步方法</span><span class="sxs-lookup"><span data-stu-id="a06f3-236">Convert startButton_Click to an asynchronous method</span></span>

1. <span data-ttu-id="a06f3-237">如果您尚未這麼做，請在事件處理常式中，將呼叫方法的名稱從 `SumPageSizes` 變更為 `SumPageSizesAsync`。</span><span class="sxs-lookup"><span data-stu-id="a06f3-237">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>

2. <span data-ttu-id="a06f3-238">因為 `SumPageSizesAsync` 是非同步方法，在事件處理常式中變更程式碼以等候結果。</span><span class="sxs-lookup"><span data-stu-id="a06f3-238">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>

    <span data-ttu-id="a06f3-239">對 `SumPageSizesAsync` 的呼叫會鏡射 `GetURLContentsAsync` 中對 `CopyToAsync` 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a06f3-239">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="a06f3-240">呼叫會傳回 `Task`，而不是 `Task(T)`。</span><span class="sxs-lookup"><span data-stu-id="a06f3-240">The call returns a `Task`, not a `Task(T)`.</span></span>

    <span data-ttu-id="a06f3-241">如同先前的程序，您可以使用一個陳述式或兩個陳述式轉換呼叫。</span><span class="sxs-lookup"><span data-stu-id="a06f3-241">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="a06f3-242">下列程式碼會顯示這些變更。</span><span class="sxs-lookup"><span data-stu-id="a06f3-242">The following code shows these changes.</span></span>

    ```vb
    ' One-step async call.
    Await SumPageSizesAsync()

    ' Two-step async call.
    Dim sumTask As Task = SumPageSizesAsync()
    Await sumTask
    ```

3. <span data-ttu-id="a06f3-243">若要避免不小心重新進入作業，請在 `startButton_Click` 頂端加入下列陳述式以停用 [開始] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="a06f3-243">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>

    ```vb
    ' Disable the button until the operation is complete.
    startButton.IsEnabled = False
    ```

    <span data-ttu-id="a06f3-244">您可以在事件處理常式結尾重新啟用按鈕。</span><span class="sxs-lookup"><span data-stu-id="a06f3-244">You can reenable the button at the end of the event handler.</span></span>

    ```vb
    ' Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = True
    ```

    <span data-ttu-id="a06f3-245">如需重新進入的詳細資訊，請參閱[處理非同步應用程式中的重新進入（Visual Basic）](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="a06f3-245">For more information about reentrancy, see [Handling Reentrancy in Async Apps (Visual Basic)](../../../../visual-basic/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>

4. <span data-ttu-id="a06f3-246">最後，將 `Async` 修飾詞加入宣告，讓事件處理常式可以等候 `SumPagSizesAsync`。</span><span class="sxs-lookup"><span data-stu-id="a06f3-246">Finally, add the `Async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>

    ```vb
    Async Sub startButton_Click(sender As Object, e As RoutedEventArgs) Handles startButton.Click
    ```

    <span data-ttu-id="a06f3-247">一般而言，事件處理常式的名稱並沒有改變。</span><span class="sxs-lookup"><span data-stu-id="a06f3-247">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="a06f3-248">傳回型別不會變更`Task`為，因為事件處理`Sub`程式必須是 Visual Basic 中的程式。</span><span class="sxs-lookup"><span data-stu-id="a06f3-248">The return type isn’t changed to `Task` because event handlers must be `Sub` procedures in Visual Basic.</span></span>

    <span data-ttu-id="a06f3-249">專案從同步到非同步處理的轉換已完成。</span><span class="sxs-lookup"><span data-stu-id="a06f3-249">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>

## <a name="test-the-asynchronous-solution"></a><span data-ttu-id="a06f3-250">測試非同步解決方案</span><span class="sxs-lookup"><span data-stu-id="a06f3-250">Test the asynchronous solution</span></span>

1. <span data-ttu-id="a06f3-251">選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="a06f3-251">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

2. <span data-ttu-id="a06f3-252">類似同步方案的輸出應該會顯示。</span><span class="sxs-lookup"><span data-stu-id="a06f3-252">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="a06f3-253">但是，請注意下列差異。</span><span class="sxs-lookup"><span data-stu-id="a06f3-253">However, notice the following differences.</span></span>

    - <span data-ttu-id="a06f3-254">處理完成之後，結果不會同時發生。</span><span class="sxs-lookup"><span data-stu-id="a06f3-254">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="a06f3-255">例如，這兩個程式在 `startButton_Click` 中都包含程式碼行，會清除文字方塊。</span><span class="sxs-lookup"><span data-stu-id="a06f3-255">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="a06f3-256">此用意是在顯示一個結果集之後、二度選擇 [開始] 按鈕時，清除執行之間的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="a06f3-256">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="a06f3-257">在同步版本中，當下載完成且 UI 執行緒可以執行其他工作時，會在第二次顯示計數之前，清除文字方塊。</span><span class="sxs-lookup"><span data-stu-id="a06f3-257">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="a06f3-258">在非同步版本中，會在您選擇 [開始] 按鈕之後，立即清除文字方塊。</span><span class="sxs-lookup"><span data-stu-id="a06f3-258">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>

    - <span data-ttu-id="a06f3-259">最重要的是，不會在下載期間封鎖 UI 執行緒。</span><span class="sxs-lookup"><span data-stu-id="a06f3-259">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="a06f3-260">您可以移動視窗或調整其大小，同時下載、計算及顯示 Web 資源。</span><span class="sxs-lookup"><span data-stu-id="a06f3-260">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="a06f3-261">如果其中一個網站變慢或沒有回應，您可以選擇 [關閉] 按鈕 (右上角紅色欄位中的 x)，取消作業。</span><span class="sxs-lookup"><span data-stu-id="a06f3-261">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>

## <a name="replace-the-geturlcontentsasync-method-with-a-net-framework-method"></a><span data-ttu-id="a06f3-262">將 Geturlcontentsasync 為方法取代為 .NET Framework 方法</span><span class="sxs-lookup"><span data-stu-id="a06f3-262">Replace the GetURLContentsAsync method with a .NET Framework method</span></span>

1. <span data-ttu-id="a06f3-263">.NET Framework 提供許多您可以使用的非同步方法。</span><span class="sxs-lookup"><span data-stu-id="a06f3-263">The .NET Framework provides many async methods that you can use.</span></span> <span data-ttu-id="a06f3-264">其中一個<xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType>方法，就是這個逐步解說所需的功能。</span><span class="sxs-lookup"><span data-stu-id="a06f3-264">One of them, the <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29?displayProperty=nameWithType> method, does just what you need for this walkthrough.</span></span> <span data-ttu-id="a06f3-265">您可以使用這個方法，而不是 `GetURLContentsAsync` 方法，這是您在先前的程序中建立的方法。</span><span class="sxs-lookup"><span data-stu-id="a06f3-265">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>

    <span data-ttu-id="a06f3-266">第一個步驟是<xref:System.Net.Http.HttpClient> `SumPageSizesAsync`在方法中建立物件。</span><span class="sxs-lookup"><span data-stu-id="a06f3-266">The first step is to create an <xref:System.Net.Http.HttpClient> object in the `SumPageSizesAsync` method.</span></span> <span data-ttu-id="a06f3-267">在方法的開頭，加入下列宣告。</span><span class="sxs-lookup"><span data-stu-id="a06f3-267">Add the following declaration at the start of the method.</span></span>

    ```vb
    ' Declare an HttpClient object and increase the buffer size. The
    ' default buffer size is 65,536.
    Dim client As HttpClient =
        New HttpClient() With {.MaxResponseContentBufferSize = 1000000}
    ```

2. <span data-ttu-id="a06f3-268">在 `SumPageSizesAsync,` 中將對 `GetURLContentsAsync` 方法的呼叫取代為對 `HttpClient` 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="a06f3-268">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>

    ```vb
    Dim urlContents As Byte() = Await client.GetByteArrayAsync(url)
    ```

3. <span data-ttu-id="a06f3-269">移除或取消註解您撰寫的 `GetURLContentsAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="a06f3-269">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>

4. <span data-ttu-id="a06f3-270">選擇 F5 鍵以執行程式，然後選擇 [ **開始** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="a06f3-270">Choose the F5 key to run the program, and then choose the **Start** button.</span></span>

    <span data-ttu-id="a06f3-271">此版本之專案的行為應該符合「測試非同步方案」程序描述的行為，而且您只需要投入較少的精力。</span><span class="sxs-lookup"><span data-stu-id="a06f3-271">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>

## <a name="example"></a><span data-ttu-id="a06f3-272">範例</span><span class="sxs-lookup"><span data-stu-id="a06f3-272">Example</span></span>

<span data-ttu-id="a06f3-273">以下是使用非同步`GetURLContentsAsync`方法之已轉換非同步方案的完整範例。</span><span class="sxs-lookup"><span data-stu-id="a06f3-273">The following is the full example of the converted asynchronous solution that uses the asynchronous `GetURLContentsAsync` method.</span></span> <span data-ttu-id="a06f3-274">請注意，它極為類似原始的同步方案。</span><span class="sxs-lookup"><span data-stu-id="a06f3-274">Notice that it strongly resembles the original, synchronous solution.</span></span>

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
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
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
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

<span data-ttu-id="a06f3-275">下列程式碼包含使用 `HttpClient` 方法 `GetByteArrayAsync` 之方案的完整範例。</span><span class="sxs-lookup"><span data-stu-id="a06f3-275">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>

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

        ' Two-step async call.
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
                "https://msdn.microsoft.com/library/windows/apps/br211380.aspx",
                "https://msdn.microsoft.com",
                "https://msdn.microsoft.com/library/hh290136.aspx",
                "https://msdn.microsoft.com/library/ee256749.aspx",
                "https://msdn.microsoft.com/library/hh290138.aspx",
                "https://msdn.microsoft.com/library/hh290140.aspx",
                "https://msdn.microsoft.com/library/dd470362.aspx",
                "https://msdn.microsoft.com/library/aa578028.aspx",
                "https://msdn.microsoft.com/library/ms404677.aspx",
                "https://msdn.microsoft.com/library/ff730837.aspx"
            }
        Return urls
    End Function

    Private Sub DisplayResults(url As String, content As Byte())

        ' Display the length of each website. The string format
        ' is designed to be used with a monospaced font, such as
        ' Lucida Console or Global Monospace.
        Dim bytes = content.Length
        ' Strip off the "https://".
        Dim displayURL = url.Replace("https://", "")
        resultsTextBox.Text &= String.Format(vbCrLf & "{0,-58} {1,8}", displayURL, bytes)
    End Sub

End Class
```

## <a name="see-also"></a><span data-ttu-id="a06f3-276">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a06f3-276">See also</span></span>

- [<span data-ttu-id="a06f3-277">非同步範例：存取 Web 逐步解說 (C# 和 Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a06f3-277">Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)</span></span>](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)
- [<span data-ttu-id="a06f3-278">Await 運算子</span><span class="sxs-lookup"><span data-stu-id="a06f3-278">Await Operator</span></span>](../../../../visual-basic/language-reference/operators/await-operator.md)
- [<span data-ttu-id="a06f3-279">Async</span><span class="sxs-lookup"><span data-stu-id="a06f3-279">Async</span></span>](../../../../visual-basic/language-reference/modifiers/async.md)
- [<span data-ttu-id="a06f3-280">使用 Async 和 Await 進行非同步程式設計 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a06f3-280">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="a06f3-281">非同步方法的傳回型別 (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a06f3-281">Async Return Types (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/async-return-types.md)
- <span data-ttu-id="a06f3-282">[Task-based Asynchronous Programming (TAP)](https://go.microsoft.com/fwlink/?LinkId=204847) (以工作為基礎的非同步程式設計 (TAP))</span><span class="sxs-lookup"><span data-stu-id="a06f3-282">[Task-based Asynchronous Programming (TAP)](https://go.microsoft.com/fwlink/?LinkId=204847)</span></span>
- [<span data-ttu-id="a06f3-283">如何：使用 System.threading.tasks.task.whenall （Visual Basic）擴充非同步逐步解說</span><span class="sxs-lookup"><span data-stu-id="a06f3-283">How to: Extend the Async Walkthrough by Using Task.WhenAll (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="a06f3-284">如何：使用 Async 和 Await，同時發出多個 Web 要求（Visual Basic）</span><span class="sxs-lookup"><span data-stu-id="a06f3-284">How to: Make Multiple Web Requests in Parallel by Using Async and Await (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
