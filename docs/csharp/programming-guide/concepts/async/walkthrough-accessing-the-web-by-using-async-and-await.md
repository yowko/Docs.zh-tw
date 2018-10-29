---
title: 逐步解說：使用 async 和 await 存取 Web (C#)
ms.date: 07/20/2015
ms.assetid: c95d8d71-5a98-4bf0-aaf4-45fed2ebbacd
ms.openlocfilehash: 8a97521bae7f5f16841aa4c8e4a157384739ee61
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/19/2018
ms.locfileid: "49453277"
---
# <a name="walkthrough-accessing-the-web-by-using-async-and-await-c"></a><span data-ttu-id="c4c00-102">逐步解說：使用 async 和 await 存取 Web (C#)</span><span class="sxs-lookup"><span data-stu-id="c4c00-102">Walkthrough: Accessing the Web by Using async and await (C#)</span></span>

<span data-ttu-id="c4c00-103">您可以使用 async/await 功能，以更容易且直觀的方式撰寫非同步程式。</span><span class="sxs-lookup"><span data-stu-id="c4c00-103">You can write asynchronous programs more easily and intuitively by using async/await features.</span></span> <span data-ttu-id="c4c00-104">您可以撰寫非同步程式碼，使其看起來像是同步程式碼，讓編譯器處理困難的回呼函式和非同步程式碼通常需要的接續。</span><span class="sxs-lookup"><span data-stu-id="c4c00-104">You can write asynchronous code that looks like synchronous code and let the compiler handle the difficult callback functions and continuations that asynchronous code usually entails.</span></span>

<span data-ttu-id="c4c00-105">如需非同步功能的詳細資訊，請參閱[使用 async 和 await 進行非同步程式設計 (C#)](../../../../csharp/programming-guide/concepts/async/index.md)。</span><span class="sxs-lookup"><span data-stu-id="c4c00-105">For more information about the Async feature, see [Asynchronous Programming with async and await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).</span></span>

<span data-ttu-id="c4c00-106">本逐步解說從同步化 Windows Presentation Foundation (WPF) 應用程式開始，該應用程式會加總網站清單中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="c4c00-106">This walkthrough starts with a synchronous Windows Presentation Foundation (WPF) application that sums the number of bytes in a list of websites.</span></span> <span data-ttu-id="c4c00-107">然後逐步解說會藉由使用新功能，將應用程式轉換為非同步解決方案。</span><span class="sxs-lookup"><span data-stu-id="c4c00-107">The walkthrough then converts the application to an asynchronous solution by using the new features.</span></span>

<span data-ttu-id="c4c00-108">如果您不想要自行建置應用程式，可以下載 [Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) (非同步範例：存取 Web 逐步解說 (C# 和 Visual Basic))。</span><span class="sxs-lookup"><span data-stu-id="c4c00-108">If you don't want to build the applications yourself, you can download [Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f).</span></span>

> [!NOTE]
> <span data-ttu-id="c4c00-109">若要執行範例，您必須在電腦上安裝 Visual Studio 2012 或更新版本以及 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="c4c00-109">To run the examples, you must have Visual Studio 2012 or newer and the .NET Framework 4.5 or newer installed on your computer.</span></span>

## <a name="create-a-wpf-application"></a><span data-ttu-id="c4c00-110">建立 WPF 應用程式</span><span class="sxs-lookup"><span data-stu-id="c4c00-110">Create a WPF application</span></span>

1.  <span data-ttu-id="c4c00-111">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="c4c00-111">Start Visual Studio.</span></span>

2.  <span data-ttu-id="c4c00-112">在功能表列上，選擇 [檔案] > [新增] > [專案]。</span><span class="sxs-lookup"><span data-stu-id="c4c00-112">On the menu bar, choose **File** > **New** > **Project**.</span></span>

     <span data-ttu-id="c4c00-113">[ **新增專案** ] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="c4c00-113">The **New Project** dialog box opens.</span></span>

3.  <span data-ttu-id="c4c00-114">在 [已安裝的範本] 窗格中，選擇 [Visual C#]，然後從專案類型清單中選擇 [WPF 應用程式]。</span><span class="sxs-lookup"><span data-stu-id="c4c00-114">In the **Installed Templates** pane, choose Visual C#, and then choose **WPF Application** from the list of project types.</span></span>

4.  <span data-ttu-id="c4c00-115">在 [名稱] 文字方塊中，輸入 `AsyncExampleWPF`，然後選擇 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c4c00-115">In the **Name** text box, enter `AsyncExampleWPF`, and then choose the **OK** button.</span></span>

     <span data-ttu-id="c4c00-116">新的專案隨即會出現在方案總管中。</span><span class="sxs-lookup"><span data-stu-id="c4c00-116">The new project appears in **Solution Explorer**.</span></span>

## <a name="design-a-simple-wpf-mainwindow"></a><span data-ttu-id="c4c00-117">設計簡單的 WPF MainWindow</span><span class="sxs-lookup"><span data-stu-id="c4c00-117">Design a simple WPF MainWindow</span></span>

1.  <span data-ttu-id="c4c00-118">在 Visual Studio 程式碼編輯器中，選擇 [ **MainWindow.xaml** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c4c00-118">In the Visual Studio Code Editor, choose the **MainWindow.xaml** tab.</span></span>

2.  <span data-ttu-id="c4c00-119">如果未顯示 [工具箱] 視窗，請選擇 [檢視] 功能表，然後選擇 [工具箱]。</span><span class="sxs-lookup"><span data-stu-id="c4c00-119">If the **Toolbox** window isn’t visible, open the **View** menu, and then choose **Toolbox**.</span></span>

3.  <span data-ttu-id="c4c00-120">將 **Button** 控制項和 **TextBox** 控制項加入 [MainWindow] 視窗。</span><span class="sxs-lookup"><span data-stu-id="c4c00-120">Add a **Button** control and a **TextBox** control to the **MainWindow** window.</span></span>

4.  <span data-ttu-id="c4c00-121">反白顯示 **TextBox** 控制項，並在 [屬性] 視窗中，設定下列值：</span><span class="sxs-lookup"><span data-stu-id="c4c00-121">Highlight the **TextBox** control and, in the **Properties** window, set the following values:</span></span>

    -   <span data-ttu-id="c4c00-122">將 [名稱] 屬性設定為 `resultsTextBox`。</span><span class="sxs-lookup"><span data-stu-id="c4c00-122">Set the **Name** property to `resultsTextBox`.</span></span>

    -   <span data-ttu-id="c4c00-123">將 [高度] 屬性設為 250。</span><span class="sxs-lookup"><span data-stu-id="c4c00-123">Set the **Height** property to 250.</span></span>

    -   <span data-ttu-id="c4c00-124">將 [寬度] 屬性設為 500。</span><span class="sxs-lookup"><span data-stu-id="c4c00-124">Set the **Width** property to 500.</span></span>

    -   <span data-ttu-id="c4c00-125">在 [文字] 索引標籤上，指定等寬字型，例如 Lucida Console 或全域等寬。</span><span class="sxs-lookup"><span data-stu-id="c4c00-125">On the **Text** tab, specify a monospaced font, such as Lucida Console or Global Monospace.</span></span>

5.  <span data-ttu-id="c4c00-126">反白顯示 **Button** 控制項，並在 [屬性] 視窗中，設定下列值：</span><span class="sxs-lookup"><span data-stu-id="c4c00-126">Highlight the **Button** control and, in the **Properties** window, set the following values:</span></span>

    -   <span data-ttu-id="c4c00-127">將 [名稱] 屬性設定為 `startButton`。</span><span class="sxs-lookup"><span data-stu-id="c4c00-127">Set the **Name** property to `startButton`.</span></span>

    -   <span data-ttu-id="c4c00-128">將 [內容] 屬性的值從 **Button** 變更為 **Start**。</span><span class="sxs-lookup"><span data-stu-id="c4c00-128">Change the value of the **Content** property from **Button** to **Start**.</span></span>

6.  <span data-ttu-id="c4c00-129">放置文字方塊和按鈕，使兩者都出現在 [MainWindow] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="c4c00-129">Position the text box and the button so that both appear in the **MainWindow** window.</span></span>

     <span data-ttu-id="c4c00-130">如需 WPF XAML 設計工具的詳細資訊，請參閱[使用 XAML 設計工具建立 UI](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="c4c00-130">For more information about the WPF XAML Designer, see [Creating a UI by using XAML Designer](/visualstudio/designers/creating-a-ui-by-using-xaml-designer-in-visual-studio).</span></span>

## <a name="add-a-reference"></a><span data-ttu-id="c4c00-131">加入參考</span><span class="sxs-lookup"><span data-stu-id="c4c00-131">Add a reference</span></span>

1.  <span data-ttu-id="c4c00-132">在方案總管中，反白顯示您的專案名稱。</span><span class="sxs-lookup"><span data-stu-id="c4c00-132">In **Solution Explorer**, highlight your project's name.</span></span>

2.  <span data-ttu-id="c4c00-133">在功能表列上，選擇 [專案]  >  [加入參考]。</span><span class="sxs-lookup"><span data-stu-id="c4c00-133">On the menu bar, choose **Project** > **Add Reference**.</span></span>

     <span data-ttu-id="c4c00-134">[參考管理員] 對話方塊隨即顯示。</span><span class="sxs-lookup"><span data-stu-id="c4c00-134">The **Reference Manager** dialog box appears.</span></span>

3.  <span data-ttu-id="c4c00-135">在對話方塊上方，請確認專案的目標是 .NET Framework 4.5 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="c4c00-135">At the top of the dialog box, verify that your project is targeting the .NET Framework 4.5 or higher.</span></span>

4.  <span data-ttu-id="c4c00-136">在 [組件] 分類中，選擇 [Framework] (如果尚未選擇)。</span><span class="sxs-lookup"><span data-stu-id="c4c00-136">In the **Assemblies** category, choose **Framework** if it isn’t already chosen.</span></span>

5.  <span data-ttu-id="c4c00-137">在名稱清單中，選取 [System.Net.Http] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="c4c00-137">In the list of names, select the **System.Net.Http** check box.</span></span>

6.  <span data-ttu-id="c4c00-138">選擇 [確定] 按鈕以關閉對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c4c00-138">Choose the **OK** button to close the dialog box.</span></span>

## <a name="add-necessary-using-directives"></a><span data-ttu-id="c4c00-139">加入必要的 using 指示詞</span><span class="sxs-lookup"><span data-stu-id="c4c00-139">Add necessary using directives</span></span>

1.  <span data-ttu-id="c4c00-140">在方案總管中，開啟 MainWindow.xaml.cs 的捷徑功能表，然後選擇 [檢視程式碼]。</span><span class="sxs-lookup"><span data-stu-id="c4c00-140">In **Solution Explorer**, open the shortcut menu for MainWindow.xaml.cs, and then choose **View Code**.</span></span>

2.  <span data-ttu-id="c4c00-141">如果尚未顯示，請將下列 `using` 指示詞加入程式碼檔案頂端。</span><span class="sxs-lookup"><span data-stu-id="c4c00-141">Add the following `using` directives at the top of the code file if they’re not already present.</span></span>

    ```csharp
    using System.Net.Http;
    using System.Net;
    using System.IO;
    ```

## <a name="create-a-synchronous-app"></a><span data-ttu-id="c4c00-142">建立同步應用程式</span><span class="sxs-lookup"><span data-stu-id="c4c00-142">Create a synchronous app</span></span>

1.  <span data-ttu-id="c4c00-143">在設計視窗 MainWindow.xaml 中，按兩下 [開始] 按鈕，以在 MainWindow.xaml.cs 中建立 `startButton_Click` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="c4c00-143">In the design window, MainWindow.xaml, double-click the **Start** button to create the `startButton_Click` event handler in MainWindow.xaml.cs.</span></span>

2.  <span data-ttu-id="c4c00-144">在 MainWindow.xaml.cs 中，將下列程式碼複製到 `startButton_Click` 的內文：</span><span class="sxs-lookup"><span data-stu-id="c4c00-144">In MainWindow.xaml.cs, copy the following code into the body of `startButton_Click`:</span></span>

    ```csharp
    resultsTextBox.Clear();
    SumPageSizes();
    resultsTextBox.Text += "\r\nControl returned to startButton_Click.";
    ```

    <span data-ttu-id="c4c00-145">程式碼會呼叫方法，該方法會驅動應用程式 `SumPageSizes`，並且在控制項返回 `startButton_Click` 時顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="c4c00-145">The code calls the method that drives the application, `SumPageSizes`, and displays a message when control returns to `startButton_Click`.</span></span>

3.  <span data-ttu-id="c4c00-146">同步方案的程式碼包含下列四種方法：</span><span class="sxs-lookup"><span data-stu-id="c4c00-146">The code for the synchronous solution contains the following four methods:</span></span>

    -   <span data-ttu-id="c4c00-147">`SumPageSizes`，會從 `SetUpURLList` 取得網頁 URL 的清單，然後呼叫 `GetURLContents` 和 `DisplayResults` 以處理每個 URL。</span><span class="sxs-lookup"><span data-stu-id="c4c00-147">`SumPageSizes`, which gets a list of webpage URLs from `SetUpURLList` and then calls `GetURLContents` and `DisplayResults` to process each URL.</span></span>

    -   <span data-ttu-id="c4c00-148">`SetUpURLList`，會製作並傳回網址清單。</span><span class="sxs-lookup"><span data-stu-id="c4c00-148">`SetUpURLList`, which makes and returns a list of web addresses.</span></span>

    -   <span data-ttu-id="c4c00-149">`GetURLContents`，會下載每個網站的內容，並傳回內容做為位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="c4c00-149">`GetURLContents`, which downloads the contents of each website and returns the contents as a byte array.</span></span>

    -   <span data-ttu-id="c4c00-150">`DisplayResults`，會顯示每個 URL 的位元組陣列中的位元組數目。</span><span class="sxs-lookup"><span data-stu-id="c4c00-150">`DisplayResults`, which displays  the number of bytes in the byte array for each URL.</span></span>

    <span data-ttu-id="c4c00-151">複製下列四種方法，然後貼在 MainWindow.xaml.cs 的 `startButton_Click` 事件處理常式下方：</span><span class="sxs-lookup"><span data-stu-id="c4c00-151">Copy the following four methods, and then paste them under the `startButton_Click` event handler in MainWindow.xaml.cs:</span></span>

    ```csharp
    private void SumPageSizes()
    {
        // Make a list of web addresses.
        List<string> urlList = SetUpURLList();

        var total = 0;
        foreach (var url in urlList)
        {
            // GetURLContents returns the contents of url as a byte array.
            byte[] urlContents = GetURLContents(url);

            DisplayResults(url, urlContents);

            // Update the total.
            total += urlContents.Length;
        }

        // Display the total count for all of the web addresses.
        resultsTextBox.Text +=
            string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);
    }

    private List<string> SetUpURLList()
    {
        var urls = new List<string>
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
        };
        return urls;
    }

    private byte[] GetURLContents(string url)
    {
        // The downloaded resource ends up in the variable named content.
        var content = new MemoryStream();

        // Initialize an HttpWebRequest for the current URL.
        var webReq = (HttpWebRequest)WebRequest.Create(url);

        // Send the request to the Internet resource and wait for
        // the response.
        // Note: you can't use HttpWebRequest.GetResponse in a Windows Store app.
        using (WebResponse response = webReq.GetResponse())
        {
            // Get the data stream that is associated with the specified URL.
            using (Stream responseStream = response.GetResponseStream())
            {
                // Read the bytes in responseStream and copy them to content.
                responseStream.CopyTo(content);
            }
        }

        // Return the result as a byte array.
        return content.ToArray();
    }

    private void DisplayResults(string url, byte[] content)
    {
        // Display the length of each website. The string format
        // is designed to be used with a monospaced font, such as
        // Lucida Console or Global Monospace.
        var bytes = content.Length;
        // Strip off the "https://".
        var displayURL = url.Replace("https://", "");
        resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);
    }
    ```

## <a name="test-the-synchronous-solution"></a><span data-ttu-id="c4c00-152">測試同步解決方案</span><span class="sxs-lookup"><span data-stu-id="c4c00-152">Test the synchronous solution</span></span>

<span data-ttu-id="c4c00-153">選擇 **F5** 鍵以執行程式，然後選擇 [開始] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c4c00-153">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

<span data-ttu-id="c4c00-154">應該會顯示如下列清單的輸出：</span><span class="sxs-lookup"><span data-stu-id="c4c00-154">Output that resembles the following list should appear:</span></span>

```text
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

<span data-ttu-id="c4c00-155">請注意，需要花費幾秒鐘以顯示計數。</span><span class="sxs-lookup"><span data-stu-id="c4c00-155">Notice that it takes a few seconds to display the counts.</span></span> <span data-ttu-id="c4c00-156">在這段期間，在等候下載要求資源的同時，會封鎖 UI 執行緒。</span><span class="sxs-lookup"><span data-stu-id="c4c00-156">During that time, the UI thread is blocked while it waits for requested resources to download.</span></span> <span data-ttu-id="c4c00-157">如此一來，您就無法在選擇 [開始] 按鈕之後，移動、最大化、最小化，或甚至關閉顯示視窗。</span><span class="sxs-lookup"><span data-stu-id="c4c00-157">As a result, you can't move, maximize, minimize, or even close the display window after you choose the  **Start** button.</span></span> <span data-ttu-id="c4c00-158">這些努力會失敗，直到位元組計數開始出現為止。</span><span class="sxs-lookup"><span data-stu-id="c4c00-158">These efforts fail until the byte counts start to appear.</span></span> <span data-ttu-id="c4c00-159">如果網站沒有回應，也不會指出失敗的站台。</span><span class="sxs-lookup"><span data-stu-id="c4c00-159">If a website isn’t responding, you have no indication of which site failed.</span></span> <span data-ttu-id="c4c00-160">甚至難以停止等候以及關閉程式。</span><span class="sxs-lookup"><span data-stu-id="c4c00-160">It is difficult even to stop waiting and close the program.</span></span>

## <a name="convert-geturlcontents-to-an-asynchronous-method"></a><span data-ttu-id="c4c00-161">將 GetURLContents 轉換為非同步方法</span><span class="sxs-lookup"><span data-stu-id="c4c00-161">Convert GetURLContents to an asynchronous method</span></span>

1.  <span data-ttu-id="c4c00-162">若要將同步方案轉換成非同步方案，最佳的起點是在 `GetURLContents`，因為呼叫 <xref:System.Net.HttpWebRequest> 方法 <xref:System.Net.HttpWebRequest.GetResponse%2A> 及 <xref:System.IO.Stream> 方法 <xref:System.IO.Stream.CopyTo%2A> 是應用程式存取 Web 的位置。</span><span class="sxs-lookup"><span data-stu-id="c4c00-162">To convert the synchronous solution to an asynchronous solution, the best place to start is in `GetURLContents` because the calls to the <xref:System.Net.HttpWebRequest> method <xref:System.Net.HttpWebRequest.GetResponse%2A> and to the <xref:System.IO.Stream> method <xref:System.IO.Stream.CopyTo%2A> are where the application accesses the web.</span></span> <span data-ttu-id="c4c00-163">.NET Framework 會讓轉換變得簡單，方法是提供這兩種方法的非同步版本。</span><span class="sxs-lookup"><span data-stu-id="c4c00-163">The .NET Framework makes the conversion easy by supplying asynchronous versions of both methods.</span></span>

     <span data-ttu-id="c4c00-164">如需 `GetURLContents` 中所用之方法的詳細資訊，請參閱 <xref:System.Net.WebRequest>。</span><span class="sxs-lookup"><span data-stu-id="c4c00-164">For more information about the methods that are used in `GetURLContents`, see <xref:System.Net.WebRequest>.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c4c00-165">當您依照本逐步解說中的步驟時，會出現數個編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="c4c00-165">As you follow the steps in this walkthrough, several compiler errors appear.</span></span> <span data-ttu-id="c4c00-166">您可以略過它們，並繼續進行本逐步解說。</span><span class="sxs-lookup"><span data-stu-id="c4c00-166">You can ignore them and continue with the walkthrough.</span></span>

     <span data-ttu-id="c4c00-167">將在 `GetURLContents` 的第三行呼叫的方法從 `GetResponse` 變更為非同步、以工作為基礎的 <xref:System.Net.WebRequest.GetResponseAsync%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="c4c00-167">Change the method that's called in the third line of `GetURLContents` from `GetResponse` to the asynchronous, task-based <xref:System.Net.WebRequest.GetResponseAsync%2A> method.</span></span>

    ```csharp
    using (WebResponse response = webReq.GetResponseAsync())
    ```

2.  <span data-ttu-id="c4c00-168">`GetResponseAsync` 會傳回 <xref:System.Threading.Tasks.Task%601>。</span><span class="sxs-lookup"><span data-stu-id="c4c00-168">`GetResponseAsync` returns a <xref:System.Threading.Tasks.Task%601>.</span></span> <span data-ttu-id="c4c00-169">在此情況下，工作傳回變數 `TResult` 具有類型 <xref:System.Net.WebResponse>。</span><span class="sxs-lookup"><span data-stu-id="c4c00-169">In this case, the *task return variable*, `TResult`, has type <xref:System.Net.WebResponse>.</span></span> <span data-ttu-id="c4c00-170">工作承諾會在已下載要求的資料及工作執行完成之後，產生實際 `WebResponse` 物件。</span><span class="sxs-lookup"><span data-stu-id="c4c00-170">The task is a promise to produce an actual `WebResponse` object after the requested data has been downloaded and the task has run to completion.</span></span>

     <span data-ttu-id="c4c00-171">若要從工作擷取 `WebResponse` 值，請將 [await](../../../../csharp/language-reference/keywords/await.md) 運算子套用至 `GetResponseAsync` 的呼叫，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="c4c00-171">To retrieve the `WebResponse` value from the task, apply an [await](../../../../csharp/language-reference/keywords/await.md) operator to the call to `GetResponseAsync`, as the following code shows.</span></span>

    ```csharp
    using (WebResponse response = await webReq.GetResponseAsync())
    ```

     <span data-ttu-id="c4c00-172">`await` 運算子會暫停執行目前的 `GetURLContents` 方法，直到等候的工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="c4c00-172">The `await` operator suspends the execution of the current method, `GetURLContents`, until the awaited task is complete.</span></span> <span data-ttu-id="c4c00-173">同時，控制項會返回非同步方法的呼叫端。</span><span class="sxs-lookup"><span data-stu-id="c4c00-173">In the meantime, control returns to the caller of the current method.</span></span> <span data-ttu-id="c4c00-174">在此範例中，目前方法是 `GetURLContents`，呼叫端是 `SumPageSizes`。</span><span class="sxs-lookup"><span data-stu-id="c4c00-174">In this example, the current method is `GetURLContents`, and the caller is `SumPageSizes`.</span></span> <span data-ttu-id="c4c00-175">當工作完成時，承諾的 `WebResponse` 物件會以等候工作之值的形式產生，而且會指派給變數 `response`。</span><span class="sxs-lookup"><span data-stu-id="c4c00-175">When the task is finished, the promised `WebResponse` object is produced as the value of the awaited task and assigned to the variable `response`.</span></span>

     <span data-ttu-id="c4c00-176">前一個陳述式可分成下列兩個陳述式，以釐清會發生什麼情況。</span><span class="sxs-lookup"><span data-stu-id="c4c00-176">The previous statement can be separated into the following two statements to clarify what happens.</span></span>

    ```csharp
    //Task<WebResponse> responseTask = webReq.GetResponseAsync();
    //using (WebResponse response = await responseTask)
    ```

     <span data-ttu-id="c4c00-177">對 `webReq.GetResponseAsync` 的呼叫會傳回 `Task(Of WebResponse)` 或 `Task<WebResponse>`。</span><span class="sxs-lookup"><span data-stu-id="c4c00-177">The call to `webReq.GetResponseAsync` returns a `Task(Of WebResponse)` or `Task<WebResponse>`.</span></span> <span data-ttu-id="c4c00-178">await 運算子會套用至工作以擷取 `WebResponse` 值。</span><span class="sxs-lookup"><span data-stu-id="c4c00-178">Then an await operator is applied to the task to retrieve the `WebResponse` value.</span></span>

     <span data-ttu-id="c4c00-179">如果非同步方法有不需要依賴工作完成的工作要執行，此方法可以在呼叫非同步方法之後，以及套用 `await` 運算子之前，繼續這兩個陳述式之間的工作。</span><span class="sxs-lookup"><span data-stu-id="c4c00-179">If your async method has work to do that doesn’t depend on the completion of the task, the method can continue with that work between these two statements, after the call to the async method and before the `await` operator is applied.</span></span> <span data-ttu-id="c4c00-180">如需範例，請參閱[如何：使用 Async 和 Await，同時發出多個 Web 要求 (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) 以及[如何：使用 Task.WhenAll 擴充非同步逐步解說的內容 (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)。</span><span class="sxs-lookup"><span data-stu-id="c4c00-180">For examples, see [How to: Make Multiple Web Requests in Parallel by Using async and await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md) and [How to: Extend the async Walkthrough by Using Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md).</span></span>

3.  <span data-ttu-id="c4c00-181">由於您在上一個步驟中加入 `await` 運算子，所以發生編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="c4c00-181">Because you added the `await` operator in the previous step, a compiler error occurs.</span></span> <span data-ttu-id="c4c00-182">此運算子只能用於以 [async](../../../../csharp/language-reference/keywords/async.md) 修飾詞標示的方法。</span><span class="sxs-lookup"><span data-stu-id="c4c00-182">The operator can be used only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="c4c00-183">當您重複轉換步驟以將對 `CopyTo` 的呼叫取代為對 `CopyToAsync` 的呼叫時，略過錯誤。</span><span class="sxs-lookup"><span data-stu-id="c4c00-183">Ignore the error while you repeat the conversion steps to replace the call to `CopyTo` with a call to `CopyToAsync`.</span></span>

    -   <span data-ttu-id="c4c00-184">變更方法的名稱，該方法會呼叫 <xref:System.IO.Stream.CopyToAsync%2A>。</span><span class="sxs-lookup"><span data-stu-id="c4c00-184">Change the name of the method that’s called to <xref:System.IO.Stream.CopyToAsync%2A>.</span></span>

    -   <span data-ttu-id="c4c00-185">`CopyTo` 或 `CopyToAsync` 方法會將位元組複製到其引數，`content`，並不會傳回有意義的值。</span><span class="sxs-lookup"><span data-stu-id="c4c00-185">The `CopyTo` or `CopyToAsync` method copies bytes to its argument, `content`, and doesn’t return a meaningful value.</span></span> <span data-ttu-id="c4c00-186">在同步版本中，呼叫 `CopyTo` 是簡單的陳述式，不會傳回值。</span><span class="sxs-lookup"><span data-stu-id="c4c00-186">In the synchronous version, the call to `CopyTo` is a simple statement that doesn't return a value.</span></span> <span data-ttu-id="c4c00-187">非同步版本，`CopyToAsync`，傳回 <xref:System.Threading.Tasks.Task>。</span><span class="sxs-lookup"><span data-stu-id="c4c00-187">The asynchronous version, `CopyToAsync`, returns a <xref:System.Threading.Tasks.Task>.</span></span> <span data-ttu-id="c4c00-188">工作函式，例如 "Task(void)"，讓方法等候。</span><span class="sxs-lookup"><span data-stu-id="c4c00-188">The task functions like "Task(void)" and enables the method to be awaited.</span></span> <span data-ttu-id="c4c00-189">將 `Await` 或 `await` 套用至對 `CopyToAsync` 的呼叫，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="c4c00-189">Apply `Await` or `await` to the call to `CopyToAsync`, as the following code shows.</span></span>

        ```csharp
        await responseStream.CopyToAsync(content);
        ```

         <span data-ttu-id="c4c00-190">前一個陳述式縮寫下列兩行程式碼。</span><span class="sxs-lookup"><span data-stu-id="c4c00-190">The previous statement abbreviates the following two lines of code.</span></span>

        ```csharp
        // CopyToAsync returns a Task, not a Task<T>.
        //Task copyTask = responseStream.CopyToAsync(content);

        // When copyTask is completed, content contains a copy of
        // responseStream.
        //await copyTask;
        ```

4.  <span data-ttu-id="c4c00-191">`GetURLContents` 中還需要完成的工作是調整方法簽章。</span><span class="sxs-lookup"><span data-stu-id="c4c00-191">All that remains to be done in `GetURLContents` is to adjust the method signature.</span></span> <span data-ttu-id="c4c00-192">您只能在以 [async](../../../../csharp/language-reference/keywords/async.md) 修飾詞標示的方法中使用 `await` 運算子。</span><span class="sxs-lookup"><span data-stu-id="c4c00-192">You can use the `await` operator only in methods that are marked with the [async](../../../../csharp/language-reference/keywords/async.md) modifier.</span></span> <span data-ttu-id="c4c00-193">新增修飾詞以將方法標示為「非同步方法」，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="c4c00-193">Add the modifier to mark the method as an *async method*, as the following code shows.</span></span>

    ```csharp
    private async byte[] GetURLContents(string url)
    ```

5.  <span data-ttu-id="c4c00-194">非同步方法的傳回型別在 C# 中只能是 <xref:System.Threading.Tasks.Task>、<xref:System.Threading.Tasks.Task%601> 或 `void`。</span><span class="sxs-lookup"><span data-stu-id="c4c00-194">The return type of an async method can only be <xref:System.Threading.Tasks.Task>, <xref:System.Threading.Tasks.Task%601>, or `void` in C#.</span></span> <span data-ttu-id="c4c00-195">一般而言，`void` 的傳回型別只適用於非同步事件處理常式，其中 `void` 為必要項目。</span><span class="sxs-lookup"><span data-stu-id="c4c00-195">Typically, a return type of `void` is used only in an async event handler, where `void` is required.</span></span> <span data-ttu-id="c4c00-196">在其他情況下，如果完成的方法有 [return](../../../../csharp/language-reference/keywords/return.md) 陳述式，則會傳回類型 T 的值，請使用 `Task(T)`；如果完成的方法不會傳回有意義的值，則使用 `Task`。</span><span class="sxs-lookup"><span data-stu-id="c4c00-196">In other cases, you use `Task(T)` if the completed method has a [return](../../../../csharp/language-reference/keywords/return.md) statement that returns a value of type T, and you use `Task` if the completed method doesn’t return a meaningful value.</span></span> <span data-ttu-id="c4c00-197">您可以將 `Task` 傳回類型想成是有意義的 "Task(void)"。</span><span class="sxs-lookup"><span data-stu-id="c4c00-197">You can think of the `Task` return type as meaning "Task(void)."</span></span>

     <span data-ttu-id="c4c00-198">如需詳細資訊，請參閱[非同步方法的傳回型別 (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)。</span><span class="sxs-lookup"><span data-stu-id="c4c00-198">For more information, see [Async Return Types (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>

     <span data-ttu-id="c4c00-199">方法 `GetURLContents` 有 return 陳述式，陳述式會傳回位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="c4c00-199">Method `GetURLContents` has a return statement, and the statement returns a byte array.</span></span> <span data-ttu-id="c4c00-200">因此，非同步版本的傳回類型是 Task(T)，其中 T 是位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="c4c00-200">Therefore, the return type of the async version is Task(T), where T is a byte array.</span></span> <span data-ttu-id="c4c00-201">在方法簽章中進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="c4c00-201">Make the following changes in the method signature:</span></span>

    -   <span data-ttu-id="c4c00-202">將傳回型別變更為 `Task<byte[]>`。</span><span class="sxs-lookup"><span data-stu-id="c4c00-202">Change the return type to `Task<byte[]>`.</span></span>

    -   <span data-ttu-id="c4c00-203">依照慣例，非同步方法的名稱會以 "Async" 結尾，所以重新命名方法 `GetURLContentsAsync`。</span><span class="sxs-lookup"><span data-stu-id="c4c00-203">By convention, asynchronous methods have names that end in "Async," so rename the method `GetURLContentsAsync`.</span></span>

     <span data-ttu-id="c4c00-204">下列程式碼會顯示這些變更。</span><span class="sxs-lookup"><span data-stu-id="c4c00-204">The following code shows these changes.</span></span>

    ```csharp
    private async Task<byte[]> GetURLContentsAsync(string url)
    ```

     <span data-ttu-id="c4c00-205">只要這幾個變更，`GetURLContents` 至非同步方法的轉換就能完成。</span><span class="sxs-lookup"><span data-stu-id="c4c00-205">With those few changes, the conversion of `GetURLContents` to an asynchronous method is complete.</span></span>

## <a name="convert-sumpagesizes-to-an-asynchronous-method"></a><span data-ttu-id="c4c00-206">將 SumPageSizes 轉換為非同步方法</span><span class="sxs-lookup"><span data-stu-id="c4c00-206">Convert SumPageSizes to an asynchronous method</span></span>

1.  <span data-ttu-id="c4c00-207">針對 `SumPageSizes` 重複上述程序的步驟。</span><span class="sxs-lookup"><span data-stu-id="c4c00-207">Repeat the steps from the previous procedure for `SumPageSizes`.</span></span> <span data-ttu-id="c4c00-208">首先，將對 `GetURLContents` 的呼叫變更為非同步呼叫。</span><span class="sxs-lookup"><span data-stu-id="c4c00-208">First, change the call to `GetURLContents` to an asynchronous call.</span></span>

    -   <span data-ttu-id="c4c00-209">如果您尚未這麼做，請變更方法的名稱，該方法是從 `GetURLContents` 呼叫至 `GetURLContentsAsync`。</span><span class="sxs-lookup"><span data-stu-id="c4c00-209">Change the name of the method that’s called from `GetURLContents` to `GetURLContentsAsync`, if you haven't already done so.</span></span>

    -   <span data-ttu-id="c4c00-210">將 `await` 套用至工作，`GetURLContentsAsync` 會傳回該工作以取得位元組陣列值。</span><span class="sxs-lookup"><span data-stu-id="c4c00-210">Apply `await` to the task that `GetURLContentsAsync` returns to obtain the byte array value.</span></span>

     <span data-ttu-id="c4c00-211">下列程式碼會顯示這些變更。</span><span class="sxs-lookup"><span data-stu-id="c4c00-211">The following code shows these changes.</span></span>

    ```csharp
    byte[] urlContents = await GetURLContentsAsync(url);
    ```

     <span data-ttu-id="c4c00-212">前一個指派縮寫下列兩行程式碼。</span><span class="sxs-lookup"><span data-stu-id="c4c00-212">The previous assignment abbreviates the following two lines of code.</span></span>

    ```csharp
    // GetURLContentsAsync returns a Task<T>. At completion, the task
    // produces a byte array.
    //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
    //byte[] urlContents = await getContentsTask;
    ```

2.  <span data-ttu-id="c4c00-213">在方法簽章中進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="c4c00-213">Make the following changes in the method's signature:</span></span>

    -   <span data-ttu-id="c4c00-214">以 `async` 修飾詞來標示方法。</span><span class="sxs-lookup"><span data-stu-id="c4c00-214">Mark the method with the `async` modifier.</span></span>

    -   <span data-ttu-id="c4c00-215">將 "Async" 加入至方法名稱。</span><span class="sxs-lookup"><span data-stu-id="c4c00-215">Add "Async" to the method name.</span></span>

    -   <span data-ttu-id="c4c00-216">這次沒有任何工作傳回變數，T，因為 `SumPageSizesAsync` 並未傳回 T 的值。(這個方法沒有任何 `return` 陳述式)。不過，方法必須傳回 `Task` 才可以等候。</span><span class="sxs-lookup"><span data-stu-id="c4c00-216">There is no task return variable, T, this time because `SumPageSizesAsync` doesn’t return a value for T. (The method has no `return` statement.) However, the method must return a `Task` to be awaitable.</span></span> <span data-ttu-id="c4c00-217">因此，請將方法的傳回型別從 `void` 變更為 `Task`。</span><span class="sxs-lookup"><span data-stu-id="c4c00-217">Therefore, change the return type of the method from `void` to `Task`.</span></span>

    <span data-ttu-id="c4c00-218">下列程式碼會顯示這些變更。</span><span class="sxs-lookup"><span data-stu-id="c4c00-218">The following code shows these changes.</span></span>

    ```csharp
    private async Task SumPageSizesAsync()
    ```

     <span data-ttu-id="c4c00-219">`SumPageSizes` 至 `SumPageSizesAsync` 的轉換完成。</span><span class="sxs-lookup"><span data-stu-id="c4c00-219">The conversion of `SumPageSizes` to `SumPageSizesAsync` is complete.</span></span>

## <a name="convert-startbuttonclick-to-an-asynchronous-method"></a><span data-ttu-id="c4c00-220">將 startButton_Click 轉換為非同步方法</span><span class="sxs-lookup"><span data-stu-id="c4c00-220">Convert startButton_Click to an asynchronous method</span></span>

1.  <span data-ttu-id="c4c00-221">如果您尚未這麼做，請在事件處理常式中，將呼叫方法的名稱從 `SumPageSizes` 變更為 `SumPageSizesAsync`。</span><span class="sxs-lookup"><span data-stu-id="c4c00-221">In the event handler, change the name of the called method from `SumPageSizes` to `SumPageSizesAsync`, if you haven’t already done so.</span></span>

2.  <span data-ttu-id="c4c00-222">因為 `SumPageSizesAsync` 是非同步方法，在事件處理常式中變更程式碼以等候結果。</span><span class="sxs-lookup"><span data-stu-id="c4c00-222">Because `SumPageSizesAsync` is an async method, change the code in the event handler to await the result.</span></span>

     <span data-ttu-id="c4c00-223">對 `SumPageSizesAsync` 的呼叫會鏡射 `GetURLContentsAsync` 中對 `CopyToAsync` 的呼叫。</span><span class="sxs-lookup"><span data-stu-id="c4c00-223">The call to `SumPageSizesAsync` mirrors the call to `CopyToAsync` in `GetURLContentsAsync`.</span></span> <span data-ttu-id="c4c00-224">呼叫會傳回 `Task`，而不是 `Task(T)`。</span><span class="sxs-lookup"><span data-stu-id="c4c00-224">The call returns a `Task`, not a `Task(T)`.</span></span>

     <span data-ttu-id="c4c00-225">如同先前的程序，您可以使用一個陳述式或兩個陳述式轉換呼叫。</span><span class="sxs-lookup"><span data-stu-id="c4c00-225">As in previous procedures, you can convert the call by using one statement or two statements.</span></span> <span data-ttu-id="c4c00-226">下列程式碼會顯示這些變更。</span><span class="sxs-lookup"><span data-stu-id="c4c00-226">The following code shows these changes.</span></span>

    ```csharp
    // One-step async call.
    await SumPageSizesAsync();

    // Two-step async call.
    //Task sumTask = SumPageSizesAsync();
    //await sumTask;
    ```

3.  <span data-ttu-id="c4c00-227">若要避免不小心重新進入作業，請在 `startButton_Click` 頂端加入下列陳述式以停用 [開始] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c4c00-227">To prevent accidentally reentering the operation, add the following statement at the top of `startButton_Click` to disable the **Start** button.</span></span>

    ```csharp
    // Disable the button until the operation is complete.
    startButton.IsEnabled = false;
    ```

     <span data-ttu-id="c4c00-228">您可以在事件處理常式結尾重新啟用按鈕。</span><span class="sxs-lookup"><span data-stu-id="c4c00-228">You can reenable the button at the end of the event handler.</span></span>

    ```csharp
    // Reenable the button in case you want to run the operation again.
    startButton.IsEnabled = true;
    ```

     <span data-ttu-id="c4c00-229">如需重新進入的詳細資訊，請參閱[處理非同步應用程式中的重新進入 (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)。</span><span class="sxs-lookup"><span data-stu-id="c4c00-229">For more information about reentrancy, see [Handling Reentrancy in Async Apps (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md).</span></span>

4.  <span data-ttu-id="c4c00-230">最後，將 `async` 修飾詞加入宣告，讓事件處理常式可以等候 `SumPagSizesAsync`。</span><span class="sxs-lookup"><span data-stu-id="c4c00-230">Finally, add the `async` modifier to the declaration so that the event handler can await `SumPagSizesAsync`.</span></span>

    ```csharp
    private async void startButton_Click(object sender, RoutedEventArgs e)
    ```

     <span data-ttu-id="c4c00-231">一般而言，事件處理常式的名稱並沒有改變。</span><span class="sxs-lookup"><span data-stu-id="c4c00-231">Typically, the names of event handlers aren’t changed.</span></span> <span data-ttu-id="c4c00-232">因為事件處理常式必須傳回 `void`，所以傳回型別不會變更為 `Task`。</span><span class="sxs-lookup"><span data-stu-id="c4c00-232">The return type isn’t changed to `Task` because event handlers must return `void`.</span></span>

     <span data-ttu-id="c4c00-233">專案從同步到非同步處理的轉換已完成。</span><span class="sxs-lookup"><span data-stu-id="c4c00-233">The conversion of the project from synchronous to asynchronous processing is complete.</span></span>

## <a name="test-the-asynchronous-solution"></a><span data-ttu-id="c4c00-234">測試非同步解決方案</span><span class="sxs-lookup"><span data-stu-id="c4c00-234">Test the asynchronous solution</span></span>

1.  <span data-ttu-id="c4c00-235">選擇 **F5** 鍵以執行程式，然後選擇 [開始] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c4c00-235">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

2.  <span data-ttu-id="c4c00-236">類似同步方案的輸出應該會顯示。</span><span class="sxs-lookup"><span data-stu-id="c4c00-236">Output that resembles the output of the synchronous solution should appear.</span></span> <span data-ttu-id="c4c00-237">但是，請注意下列差異。</span><span class="sxs-lookup"><span data-stu-id="c4c00-237">However, notice the following differences.</span></span>

    -   <span data-ttu-id="c4c00-238">處理完成之後，結果不會同時發生。</span><span class="sxs-lookup"><span data-stu-id="c4c00-238">The results don’t all occur at the same time, after the processing is complete.</span></span> <span data-ttu-id="c4c00-239">例如，這兩個程式在 `startButton_Click` 中都包含程式碼行，會清除文字方塊。</span><span class="sxs-lookup"><span data-stu-id="c4c00-239">For example, both programs contain a line in `startButton_Click` that clears the text box.</span></span> <span data-ttu-id="c4c00-240">此用意是在顯示一個結果集之後、二度選擇 [開始] 按鈕時，清除執行之間的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="c4c00-240">The intent is to clear the text box between runs if you choose the **Start** button for a second time, after one set of results has appeared.</span></span> <span data-ttu-id="c4c00-241">在同步版本中，當下載完成且 UI 執行緒可以執行其他工作時，會在第二次顯示計數之前，清除文字方塊。</span><span class="sxs-lookup"><span data-stu-id="c4c00-241">In the synchronous version, the text box is cleared just before the counts appear for the second time, when the downloads are completed and the UI thread is free to do other work.</span></span> <span data-ttu-id="c4c00-242">在非同步版本中，會在您選擇 [開始] 按鈕之後，立即清除文字方塊。</span><span class="sxs-lookup"><span data-stu-id="c4c00-242">In the asynchronous version, the text box clears immediately after you choose the **Start** button.</span></span>

    -   <span data-ttu-id="c4c00-243">最重要的是，不會在下載期間封鎖 UI 執行緒。</span><span class="sxs-lookup"><span data-stu-id="c4c00-243">Most importantly, the UI thread isn’t blocked during the downloads.</span></span> <span data-ttu-id="c4c00-244">您可以移動視窗或調整其大小，同時下載、計算及顯示 Web 資源。</span><span class="sxs-lookup"><span data-stu-id="c4c00-244">You can move or resize the window while the web resources are being downloaded, counted, and displayed.</span></span> <span data-ttu-id="c4c00-245">如果其中一個網站變慢或沒有回應，您可以選擇 [關閉] 按鈕 (右上角紅色欄位中的 x)，取消作業。</span><span class="sxs-lookup"><span data-stu-id="c4c00-245">If one of the websites is slow or not responding, you can cancel the operation by choosing the **Close** button (the x in the red field in the upper-right corner).</span></span>

## <a name="replace-method-geturlcontentsasync-with-a-net-framework-method"></a><span data-ttu-id="c4c00-246">將方法 GetURLContentsAsync 取代為 .NET Framework 方法</span><span class="sxs-lookup"><span data-stu-id="c4c00-246">Replace method GetURLContentsAsync with a .NET Framework method</span></span>

1.  <span data-ttu-id="c4c00-247">.NET Framework 4.5 提供許多您可以使用的非同步方法。</span><span class="sxs-lookup"><span data-stu-id="c4c00-247">The .NET Framework 4.5 provides many async methods that you can use.</span></span> <span data-ttu-id="c4c00-248">其中一個方法 (<xref:System.Net.Http.HttpClient> 方法 <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>) 會執行這個逐步解說所需的工作。</span><span class="sxs-lookup"><span data-stu-id="c4c00-248">One of them, the <xref:System.Net.Http.HttpClient> method <xref:System.Net.Http.HttpClient.GetByteArrayAsync%28System.String%29>, does just what you need for this walkthrough.</span></span> <span data-ttu-id="c4c00-249">您可以使用這個方法，而不是 `GetURLContentsAsync` 方法，這是您在先前的程序中建立的方法。</span><span class="sxs-lookup"><span data-stu-id="c4c00-249">You can use it instead of the `GetURLContentsAsync` method that you created in an earlier procedure.</span></span>

     <span data-ttu-id="c4c00-250">第一個步驟是在方法 `SumPageSizesAsync` 中建立 `HttpClient` 物件。</span><span class="sxs-lookup"><span data-stu-id="c4c00-250">The first step is to create an `HttpClient` object in method `SumPageSizesAsync`.</span></span> <span data-ttu-id="c4c00-251">在方法的開頭，加入下列宣告。</span><span class="sxs-lookup"><span data-stu-id="c4c00-251">Add the following declaration at the start of the method.</span></span>

    ```csharp
    // Declare an HttpClient object and increase the buffer size. The
    // default buffer size is 65,536.
    HttpClient client =
        new HttpClient() { MaxResponseContentBufferSize = 1000000 };
    ```

2.  <span data-ttu-id="c4c00-252">在 `SumPageSizesAsync,` 中將對 `GetURLContentsAsync` 方法的呼叫取代為對 `HttpClient` 方法的呼叫。</span><span class="sxs-lookup"><span data-stu-id="c4c00-252">In `SumPageSizesAsync,` replace the call to your `GetURLContentsAsync` method with a call to the `HttpClient` method.</span></span>

    ```csharp
    byte[] urlContents = await client.GetByteArrayAsync(url);
    ```

3.  <span data-ttu-id="c4c00-253">移除或取消註解您撰寫的 `GetURLContentsAsync` 方法。</span><span class="sxs-lookup"><span data-stu-id="c4c00-253">Remove or comment out the `GetURLContentsAsync` method that you wrote.</span></span>

4.  <span data-ttu-id="c4c00-254">選擇 **F5** 鍵以執行程式，然後選擇 [開始] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="c4c00-254">Choose the **F5** key to run the program, and then choose the **Start** button.</span></span>

     <span data-ttu-id="c4c00-255">此版本之專案的行為應該符合「測試非同步方案」程序描述的行為，而且您只需要投入較少的精力。</span><span class="sxs-lookup"><span data-stu-id="c4c00-255">The behavior of this version of the project should match the behavior that the "To test the asynchronous solution" procedure describes but with even less effort from you.</span></span>

## <a name="example-code"></a><span data-ttu-id="c4c00-256">範例程式碼</span><span class="sxs-lookup"><span data-stu-id="c4c00-256">Example code</span></span>

<span data-ttu-id="c4c00-257">下列程式碼包含使用您撰寫的 `GetURLContentsAsync` 方法，從同步轉換為非同步方案的完整範例。</span><span class="sxs-lookup"><span data-stu-id="c4c00-257">The following code contains the full example of the conversion from a synchronous to an asynchronous solution by using the asynchronous `GetURLContentsAsync` method that you wrote.</span></span> <span data-ttu-id="c4c00-258">請注意，它極為類似原始的同步方案。</span><span class="sxs-lookup"><span data-stu-id="c4c00-258">Notice that it strongly resembles the original, synchronous solution.</span></span>

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

// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            // Disable the button until the operation is complete.
            startButton.IsEnabled = false;

            resultsTextBox.Clear();

            // One-step async call.
            await SumPageSizesAsync();

            // Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";

            // Reenable the button in case you want to run the operation again.
            startButton.IsEnabled = true;
        }

        private async Task SumPageSizesAsync()
        {
            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            var total = 0;

            foreach (var url in urlList)
            {
                byte[] urlContents = await GetURLContentsAsync(url);

                // The previous line abbreviates the following two assignment statements.

                // GetURLContentsAsync returns a Task<T>. At completion, the task
                // produces a byte array.
                //Task<byte[]> getContentsTask = GetURLContentsAsync(url);
                //byte[] urlContents = await getContentsTask;

                DisplayResults(url, urlContents);

                // Update the total.
                total += urlContents.Length;
            }
            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
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
            };
            return urls;
        }

        private async Task<byte[]> GetURLContentsAsync(string url)
        {
            // The downloaded resource ends up in the variable named content.
            var content = new MemoryStream();

            // Initialize an HttpWebRequest for the current URL.
            var webReq = (HttpWebRequest)WebRequest.Create(url);

            // Send the request to the Internet resource and wait for
            // the response.
            using (WebResponse response = await webReq.GetResponseAsync())

            // The previous statement abbreviates the following two statements.

            //Task<WebResponse> responseTask = webReq.GetResponseAsync();
            //using (WebResponse response = await responseTask)
            {
                // Get the data stream that is associated with the specified url.
                using (Stream responseStream = response.GetResponseStream())
                {
                    // Read the bytes in responseStream and copy them to content.
                    await responseStream.CopyToAsync(content);

                    // The previous statement abbreviates the following two statements.

                    // CopyToAsync returns a Task, not a Task<T>.
                    //Task copyTask = responseStream.CopyToAsync(content);

                    // When copyTask is completed, content contains a copy of
                    // responseStream.
                    //await copyTask;
                }
            }
            // Return the result as a byte array.
            return content.ToArray();
        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);
        }
    }
}
```

<span data-ttu-id="c4c00-259">下列程式碼包含使用 `HttpClient` 方法 `GetByteArrayAsync` 之方案的完整範例。</span><span class="sxs-lookup"><span data-stu-id="c4c00-259">The following code contains the full example of the solution that uses the `HttpClient` method, `GetByteArrayAsync`.</span></span>

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

// Add the following using directives, and add a reference for System.Net.Http.
using System.Net.Http;
using System.IO;
using System.Net;

namespace AsyncExampleWPF
{
    public partial class MainWindow : Window
    {
        public MainWindow()
        {
            InitializeComponent();
        }

        private async void startButton_Click(object sender, RoutedEventArgs e)
        {
            resultsTextBox.Clear();

            // Disable the button until the operation is complete.
            startButton.IsEnabled = false;

            // One-step async call.
            await SumPageSizesAsync();

            //// Two-step async call.
            //Task sumTask = SumPageSizesAsync();
            //await sumTask;

            resultsTextBox.Text += "\r\nControl returned to startButton_Click.\r\n";

            // Reenable the button in case you want to run the operation again.
            startButton.IsEnabled = true;
        }

        private async Task SumPageSizesAsync()
        {
            // Declare an HttpClient object and increase the buffer size. The
            // default buffer size is 65,536.
            HttpClient client =
                new HttpClient() { MaxResponseContentBufferSize = 1000000 };

            // Make a list of web addresses.
            List<string> urlList = SetUpURLList();

            var total = 0;

            foreach (var url in urlList)
            {
                // GetByteArrayAsync returns a task. At completion, the task
                // produces a byte array.
                byte[] urlContents = await client.GetByteArrayAsync(url);

                // The following two lines can replace the previous assignment statement.
                //Task<byte[]> getContentsTask = client.GetByteArrayAsync(url);
                //byte[] urlContents = await getContentsTask;

                DisplayResults(url, urlContents);

                // Update the total.
                total += urlContents.Length;
            }

            // Display the total count for all of the websites.
            resultsTextBox.Text +=
                string.Format("\r\n\r\nTotal bytes returned:  {0}\r\n", total);
        }

        private List<string> SetUpURLList()
        {
            List<string> urls = new List<string>
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
            };
            return urls;
        }

        private void DisplayResults(string url, byte[] content)
        {
            // Display the length of each website. The string format
            // is designed to be used with a monospaced font, such as
            // Lucida Console or Global Monospace.
            var bytes = content.Length;
            // Strip off the "https://".
            var displayURL = url.Replace("https://", "");
            resultsTextBox.Text += string.Format("\n{0,-58} {1,8}", displayURL, bytes);
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="c4c00-260">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c4c00-260">See also</span></span>

- <span data-ttu-id="c4c00-261">[Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f) (非同步範例：存取 Web 逐步解說 (C# 和 Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="c4c00-261">[Async Sample: Accessing the Web Walkthrough (C# and Visual Basic)](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)</span></span>
- [<span data-ttu-id="c4c00-262">async</span><span class="sxs-lookup"><span data-stu-id="c4c00-262">async</span></span>](../../../../csharp/language-reference/keywords/async.md)
- [<span data-ttu-id="c4c00-263">await</span><span class="sxs-lookup"><span data-stu-id="c4c00-263">await</span></span>](../../../../csharp/language-reference/keywords/await.md)
- [<span data-ttu-id="c4c00-264">使用 async 和 await 進行非同步程式設計 (C#)</span><span class="sxs-lookup"><span data-stu-id="c4c00-264">Asynchronous Programming with async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/index.md)
- [<span data-ttu-id="c4c00-265">非同步方法的傳回型別 (C#)</span><span class="sxs-lookup"><span data-stu-id="c4c00-265">Async Return Types (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/async-return-types.md)
- <span data-ttu-id="c4c00-266">[Task-based Asynchronous Programming (TAP)](https://www.microsoft.com/en-us/download/details.aspx?id=19957) (以工作為基礎的非同步程式設計 (TAP))</span><span class="sxs-lookup"><span data-stu-id="c4c00-266">[Task-based Asynchronous Programming (TAP)](https://www.microsoft.com/en-us/download/details.aspx?id=19957)</span></span>
- [<span data-ttu-id="c4c00-267">如何：使用 Task.WhenAll 擴充非同步逐步解說的內容 (C#)</span><span class="sxs-lookup"><span data-stu-id="c4c00-267">How to: Extend the async Walkthrough by Using Task.WhenAll (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)
- [<span data-ttu-id="c4c00-268">如何：使用 async 和 await，同時發出多個 Web 要求 (C#)</span><span class="sxs-lookup"><span data-stu-id="c4c00-268">How to: Make Multiple Web Requests in Parallel by Using async and await (C#)</span></span>](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)
