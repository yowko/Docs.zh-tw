---
title: "使用 Visual Studio for Mac 在 macOS 上建置完整的 .NET Core 解決方案"
description: "本主題會逐步引導您建置一個包含可重複使用之程式庫和單元測試的 .NET Core 解決方案。"
keywords: .NET, .NET Core, macOS, Mac
author: guardrex
ms.author: mairaw
ms.date: 06/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 6945bedf-5bf3-4955-8588-83fb87511b79
ms.workload:
- dotnetcore
ms.openlocfilehash: 0db67593340ea3bae00a45b845a0effe0c1fcab1
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2018
---
# <a name="building-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="bf420-104">使用 Visual Studio for Mac 在 macOS 上建置完整的 .NET Core 解決方案</span><span class="sxs-lookup"><span data-stu-id="bf420-104">Building a complete .NET Core solution on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="bf420-105">Visual Studio for Mac 針對開發 .NET Core 應用程式，提供功能完整的整合式開發環境 (IDE)。</span><span class="sxs-lookup"><span data-stu-id="bf420-105">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="bf420-106">本主題會逐步引導您建置一個包含可重複使用之程式庫和單元測試的 .NET Core 解決方案。</span><span class="sxs-lookup"><span data-stu-id="bf420-106">This topic walks you through building a .NET Core solution that includes a reusable library and unit testing.</span></span>

<span data-ttu-id="bf420-107">本教學課程會示範如何建立能接受來自使用者的搜尋文字和文字字串、使用類別庫中的方法計算搜尋文字出現在字串中的次數，並將結果傳回給使用者的應用程式。</span><span class="sxs-lookup"><span data-stu-id="bf420-107">This tutorial shows you how to create an application that accepts a search word and a string of text from the user, counts the number of times the search word appears in the string using a method in a class library, and returns the result to the user.</span></span> <span data-ttu-id="bf420-108">解決方案也會包含針對類別庫的單元測試，做為測試驅動開發 (TDD) 概念的簡介。</span><span class="sxs-lookup"><span data-stu-id="bf420-108">The solution also includes unit testing for the class library as an introduction to test-driven development (TDD) concepts.</span></span> <span data-ttu-id="bf420-109">如果您偏好使用完整範例來進行教學課程，請下載[範例解決方案 (英文)](https://github.com/dotnet/docs/blob/master/samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter)。</span><span class="sxs-lookup"><span data-stu-id="bf420-109">If you prefer to proceed through the tutorial with a complete sample, download the [sample solution](https://github.com/dotnet/docs/blob/master/samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter).</span></span> <span data-ttu-id="bf420-110">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="bf420-110">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

> [!NOTE]
> <span data-ttu-id="bf420-111">我們非常重視您的意見反應。</span><span class="sxs-lookup"><span data-stu-id="bf420-111">Your feedback is highly valued.</span></span> <span data-ttu-id="bf420-112">您有兩種方式可以提供意見反應給 Visual Studio for Mac 開發小組：</span><span class="sxs-lookup"><span data-stu-id="bf420-112">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
> * <span data-ttu-id="bf420-113">在 Visual Studio for Mac 中，從功能表選取 [說明] > [回報問題]，或從歡迎畫面選取 [回報問題]，這會開啟用來提出錯誤報告的視窗。</span><span class="sxs-lookup"><span data-stu-id="bf420-113">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which opens a window for filing a bug report.</span></span> <span data-ttu-id="bf420-114">您可在[開發人員社群](https://developercommunity.visualstudio.com/spaces/41/index.html)入口網站追蹤您的意見反應。</span><span class="sxs-lookup"><span data-stu-id="bf420-114">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/41/index.html) portal.</span></span>
> * <span data-ttu-id="bf420-115">若要提出建議，請從功能表選取 [說明] > [提供建議]，或從歡迎畫面選取 [提供建議]，這會帶您前往 [Visual Studio for Mac UserVoice 網頁](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="bf420-115">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which takes you to the [Visual Studio for Mac UserVoice webpage](https://visualstudio.uservoice.com/forums/563332-visual-studio-for-mac).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bf420-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="bf420-116">Prerequisites</span></span>

- <span data-ttu-id="bf420-117">OpenSSL (如果執行 .NET Core 1.1)：請參閱 [Mac 上 .NET Core 的先決條件](../macos-prerequisites.md)主題。</span><span class="sxs-lookup"><span data-stu-id="bf420-117">OpenSSL (if running .NET Core 1.1): See the [Prerequisites for .NET Core on Mac](../macos-prerequisites.md) topic.</span></span>
- [<span data-ttu-id="bf420-118">.NET Core SDK 1.1 或更新版本</span><span class="sxs-lookup"><span data-stu-id="bf420-118">.NET Core SDK 1.1 or later</span></span>](https://www.microsoft.com/net/core#macos)
- [<span data-ttu-id="bf420-119">Visual Studio 2017 for Mac</span><span class="sxs-lookup"><span data-stu-id="bf420-119">Visual Studio 2017 for Mac</span></span>](https://www.visualstudio.com/vs/visual-studio-mac/)

<span data-ttu-id="bf420-120">如需必要條件的詳細資訊，請參閱 [Mac 上 .NET Core 的先決條件](../../core/macos-prerequisites.md)。</span><span class="sxs-lookup"><span data-stu-id="bf420-120">For more information on prerequisites, see the [Prerequisites for .NET Core on Mac](../../core/macos-prerequisites.md).</span></span> <span data-ttu-id="bf420-121">如需 Visual Studio 2017 for Mac 的完整系統需求，請參閱 [Visual Studio 2017 for Mac 產品系列系統需求](/visualstudio/productinfo/vs2017-system-requirements-mac)。</span><span class="sxs-lookup"><span data-stu-id="bf420-121">For the full system requirements of Visual Studio 2017 for Mac, see [Visual Studio 2017 for Mac Product Family System Requirements](/visualstudio/productinfo/vs2017-system-requirements-mac).</span></span>

## <a name="building-a-library"></a><span data-ttu-id="bf420-122">建置程式庫</span><span class="sxs-lookup"><span data-stu-id="bf420-122">Building a library</span></span>

1. <span data-ttu-id="bf420-123">選取歡迎畫面上的 [新增專案]。</span><span class="sxs-lookup"><span data-stu-id="bf420-123">On the Welcome screen, select **New Project**.</span></span> <span data-ttu-id="bf420-124">在 [多平台] 節點下的 [新增專案] 對話方塊中，選取 [.NET 標準程式庫] 範本。</span><span class="sxs-lookup"><span data-stu-id="bf420-124">In the **New Project** dialog under the **Multiplatform** node, select the **.NET Standard Library** template.</span></span> <span data-ttu-id="bf420-125">選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="bf420-125">Select **Next**.</span></span>

   ![[新增專案] 對話方塊](./media/using-on-mac-vs-full-solution/vsmacfull01.png)

1. <span data-ttu-id="bf420-127">將專案命名為 "TextUtils" (「文字公用程式」的簡短名稱)，並將解決方案命名為 "WordCounter"。</span><span class="sxs-lookup"><span data-stu-id="bf420-127">Name the project "TextUtils" (a short name for "Text Utilities") and the solution "WordCounter".</span></span> <span data-ttu-id="bf420-128">保持選取 [在解決方案目錄中建立專案目錄]。</span><span class="sxs-lookup"><span data-stu-id="bf420-128">Leave **Create a project directory within the solution directory** checked.</span></span> <span data-ttu-id="bf420-129">選取 [建立]。</span><span class="sxs-lookup"><span data-stu-id="bf420-129">Select **Create**.</span></span>

   ![[新增專案] 對話方塊](./media/using-on-mac-vs-full-solution/vsmacfull02.png)

1. <span data-ttu-id="bf420-131">在 [解決方案] 提要欄位中，展開 `TextUtils` 節點以顯示範本所提供的類別檔案 *Class1.cs*。</span><span class="sxs-lookup"><span data-stu-id="bf420-131">In the **Solution** sidebar, expand the `TextUtils` node to reveal the class file provided by the template, *Class1.cs*.</span></span> <span data-ttu-id="bf420-132">以滑鼠右鍵按一下該檔案，從操作功能表選取 [重新命名]，並將檔案重新命名為 *WordCount.cs*。</span><span class="sxs-lookup"><span data-stu-id="bf420-132">Right-click the file, select **Rename** from the context menu, and rename the file to *WordCount.cs*.</span></span> <span data-ttu-id="bf420-133">開啟檔案，並以下列程式碼取代內容：</span><span class="sxs-lookup"><span data-stu-id="bf420-133">Open the file and replace the contents with the following code:</span></span>

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. <span data-ttu-id="bf420-134">使用下列三種方法之一來儲存檔案：使用鍵盤快速鍵 <kbd>&#8984;</kbd>+<kbd>s</kbd>、從功能表選取 [檔案] > [儲存]，或以滑鼠右鍵按一下檔案的索引標籤，並從操作功能表選取 [儲存]。</span><span class="sxs-lookup"><span data-stu-id="bf420-134">Save the file by using any of three different methods: use the keyboard shortcut <kbd>&#8984;</kbd>+<kbd>s</kbd>, select **File** > **Save** from the menu, or right-click on the file's tab and select **Save** from the contextual menu.</span></span> <span data-ttu-id="bf420-135">下圖顯示 IDE 視窗︰</span><span class="sxs-lookup"><span data-stu-id="bf420-135">The following image shows the IDE window:</span></span>

   ![顯示 TextUtils 類別庫、WordCount 類別檔案、靜態類別 WordCount，以及 GetWordCount 方法的 IDE 視窗](./media/using-on-mac-vs-full-solution/vsmacfull03.png)

1. <span data-ttu-id="bf420-137">選取 IDE 視窗下邊界中的 [錯誤]，以開啟 [錯誤] 面板。</span><span class="sxs-lookup"><span data-stu-id="bf420-137">Select **Errors** in the margin at the bottom of the IDE window to open the **Errors** panel.</span></span> <span data-ttu-id="bf420-138">選取 [建置輸出] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="bf420-138">Select the **Build Output** button.</span></span>

   ![IDE 的下邊界，顯示 [錯誤] 按鈕](./media/using-on-mac-vs-full-solution/vsmacfull03b.png)

1. <span data-ttu-id="bf420-140">從功能表選取 [建置] > [全部建置]。</span><span class="sxs-lookup"><span data-stu-id="bf420-140">Select **Build** > **Build All** from the menu.</span></span>

   <span data-ttu-id="bf420-141">解決方案隨即建置。</span><span class="sxs-lookup"><span data-stu-id="bf420-141">The solution builds.</span></span> <span data-ttu-id="bf420-142">建置輸出面板會顯示建置成功。</span><span class="sxs-lookup"><span data-stu-id="bf420-142">The build output panel shows that the build is successful.</span></span>

   ![[錯誤] 面板的 [建置輸出] 窗格，顯示「建置成功」訊息](./media/using-on-mac-vs-full-solution/vsmacfull04.png)

## <a name="creating-a-test-project"></a><span data-ttu-id="bf420-144">建立測試專案</span><span class="sxs-lookup"><span data-stu-id="bf420-144">Creating a test project</span></span>

<span data-ttu-id="bf420-145">單元測試能在開發與發佈期間提供自動化的軟體測試。</span><span class="sxs-lookup"><span data-stu-id="bf420-145">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="bf420-146">您在本教學課程中使用的測試架構是 [xUnit (版本 2.2.0 或更新版本)](https://xunit.github.io/)，這會在下列步驟中 xUnit 測試專案加入解決方案時自動安裝：</span><span class="sxs-lookup"><span data-stu-id="bf420-146">The testing framework that you use in this tutorial is [xUnit (version 2.2.0 or later)](https://xunit.github.io/), which is installed automatically when the xUnit test project is added to the solution in the following steps:</span></span>

1. <span data-ttu-id="bf420-147">在 [解決方案] 提要欄位中，以滑鼠右鍵按一下 `WordCounter` 解決方案，並選取 [新增] > [新增專案]。</span><span class="sxs-lookup"><span data-stu-id="bf420-147">In the **Solution** sidebar, right-click the `WordCounter` solution and select **Add** > **Add New Project**.</span></span>

1. <span data-ttu-id="bf420-148">在 [新增專案] 對話方塊中，從 [.NET Core] 節點選取 [測試]。</span><span class="sxs-lookup"><span data-stu-id="bf420-148">In the **New Project** dialog, select **Tests** from the **.NET Core** node.</span></span> <span data-ttu-id="bf420-149">選取 [xUnit 測試專案]，接著選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="bf420-149">Select the **xUnit Test Project** followed by **Next**.</span></span>

   ![建立 xUnit 測試專案的 [新增專案] 對話方塊](./media/using-on-mac-vs-full-solution/vsmacfull05.png)

1. <span data-ttu-id="bf420-151">將新專案命名為 "TestLibrary"，並選取 [建立]。</span><span class="sxs-lookup"><span data-stu-id="bf420-151">Name the new project "TestLibrary" and select **Create**.</span></span>

   ![提供專案名稱的 [新增專案] 對話方塊](./media/using-on-mac-vs-full-solution/vsmacfull06.png)

1. <span data-ttu-id="bf420-153">為了讓測試程式庫能搭配 `WordCount` 類別使用，請將參考加入 `TextUtils` 專案。</span><span class="sxs-lookup"><span data-stu-id="bf420-153">In order for the test library to work with the `WordCount` class, add a reference to the `TextUtils` project.</span></span> <span data-ttu-id="bf420-154">在 [解決方案] 提要欄位中，以滑鼠右鍵按一下 [TestLibrary] 底下的 [相依性]。</span><span class="sxs-lookup"><span data-stu-id="bf420-154">In the **Solution** sidebar, right-click **Dependencies** under **TestLibrary**.</span></span> <span data-ttu-id="bf420-155">從操作功能表選取 [編輯參考]。</span><span class="sxs-lookup"><span data-stu-id="bf420-155">Select **Edit References** from the context menu.</span></span>

1. <span data-ttu-id="bf420-156">在 [編輯參考] 對話方塊中，選取 [專案] 索引標籤上的 [TextUtils] 專案。選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="bf420-156">In the **Edit References** dialog, select the **TextUtils** project on the **Projects** tab. Select **OK**.</span></span>

   ![[編輯參考] 對話方塊](./media/using-on-mac-vs-full-solution/vsmacfull07.png)

1. <span data-ttu-id="bf420-158">在 [TestLibrary] 專案中，將 *UnitTest1.cs* 檔案重新命名為 *TextUtilsTests.cs*。</span><span class="sxs-lookup"><span data-stu-id="bf420-158">In the **TestLibrary** project, rename the *UnitTest1.cs* file to *TextUtilsTests.cs*.</span></span>

1. <span data-ttu-id="bf420-159">開啟檔案，並以下列內容取代程式碼：</span><span class="sxs-lookup"><span data-stu-id="bf420-159">Open the file and replace the code with the following:</span></span>

   ```csharp
   using Xunit;
   using TextUtils;
   using System.Diagnostics;

   namespace TestLibrary
   {
       public class TextUtils_GetWordCountShould
       {
           [Fact]
           public void IgnoreCasing()
           {
               var wordCount = WordCount.GetWordCount("Jack", "Jack jack");
   
               Assert.NotEqual(2, wordCount);
           }
       }
   }
   ```

   <span data-ttu-id="bf420-160">下圖顯示具有單元測試程式碼的 IDE。</span><span class="sxs-lookup"><span data-stu-id="bf420-160">The following image shows the IDE with the unit test code in place.</span></span> <span data-ttu-id="bf420-161">請留意 `Assert.NotEqual` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bf420-161">Pay attention to the `Assert.NotEqual` statement.</span></span>

   ![IDE 主視窗中用來檢查 GetWordCount 的初始單元測試](./media/using-on-mac-vs-full-solution/vsmacfull08.png)

   <span data-ttu-id="bf420-163">使用 TDD 時，請務必使新的測試失敗一次，以確認其測試邏輯是正確的。</span><span class="sxs-lookup"><span data-stu-id="bf420-163">Using TDD, it's important to make a new test fail once to confirm its testing logic is correct.</span></span> <span data-ttu-id="bf420-164">該方法會傳入 "Jack" (大寫) 這個名字，以及具有 "Jack" 和 "jack" (大寫與小寫) 的字串。</span><span class="sxs-lookup"><span data-stu-id="bf420-164">The method passes in the name "Jack" (uppercase) and a string with "Jack" and "jack" (uppercase and lowercase).</span></span> <span data-ttu-id="bf420-165">如果 `GetWordCount` 方法能正常運作，它會針對搜尋文字傳回兩個實例計數。</span><span class="sxs-lookup"><span data-stu-id="bf420-165">If the `GetWordCount` method is working properly, it returns a count of two instances of the search word.</span></span> <span data-ttu-id="bf420-166">為了刻意讓此測試失敗，您會先實作測試，以判斷提示 `GetWordCount` 方法沒有傳回搜尋文字 "Jack" 的兩個實例。</span><span class="sxs-lookup"><span data-stu-id="bf420-166">In order to fail this test on purpose, you first implement the test asserting that two instances of the search word "Jack" aren't returned by the `GetWordCount` method.</span></span> <span data-ttu-id="bf420-167">繼續進行下一個步驟以刻意讓測試失敗。</span><span class="sxs-lookup"><span data-stu-id="bf420-167">Continue to the next step to fail the test on purpose.</span></span>

1. <span data-ttu-id="bf420-168">開啟螢幕右側的 [單元測試] 面板。</span><span class="sxs-lookup"><span data-stu-id="bf420-168">Open the **Unit Tests** panel on the right side of the screen.</span></span>

![單元測試面板](./media/using-on-mac-vs-full-solution/vsmacfull_UnitTestPanel.png)

1. <span data-ttu-id="bf420-170">按一下**固定**圖示維持面板開啟。</span><span class="sxs-lookup"><span data-stu-id="bf420-170">Click the **Dock** icon to keep the panel open.</span></span>

![單元測試面板固定圖示](./media/using-on-mac-vs-full-solution/vsmacfull_UnitTestPanelDockIcon.png)

1. <span data-ttu-id="bf420-172">按一下 [全部執行] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="bf420-172">Click the **Run All** button.</span></span>
   
   <span data-ttu-id="bf420-173">測試會失敗，這是正確的結果。</span><span class="sxs-lookup"><span data-stu-id="bf420-173">The test fails, which is the correct result.</span></span> <span data-ttu-id="bf420-174">測試方法會判斷提示 `inputString` 的兩個實例 ("Jack") 沒有從提供給 `GetWordCount` 方法的字串 "Jack jack" 傳回。</span><span class="sxs-lookup"><span data-stu-id="bf420-174">The test method asserts that two instances of the `inputString`, "Jack," aren't returned from the string "Jack jack" provided to the `GetWordCount` method.</span></span> <span data-ttu-id="bf420-175">由於文字大小寫的因素已經在 `GetWordCount` 方法中排除，因此會傳回兩個實例。</span><span class="sxs-lookup"><span data-stu-id="bf420-175">Since word casing was factored out in the `GetWordCount` method, two instances are returned.</span></span> <span data-ttu-id="bf420-176">2「不等於」2 的判斷提示將會失敗。</span><span class="sxs-lookup"><span data-stu-id="bf420-176">The assertion that 2 *is not equal to* 2 fails.</span></span> <span data-ttu-id="bf420-177">這是正確的結果，並證明測試的邏輯是良好的。</span><span class="sxs-lookup"><span data-stu-id="bf420-177">This is the correct outcome, and the logic of our test is good.</span></span>

   ![測試失敗](./media/using-on-mac-vs-full-solution/vsmacfull09.png)

1. <span data-ttu-id="bf420-179">將 `Assert.NotEqual` 變更為 `Assert.Equal` 來修改 `IgnoreCasing` 測試方法。</span><span class="sxs-lookup"><span data-stu-id="bf420-179">Modify the `IgnoreCasing` test method by changing `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="bf420-180">使用鍵盤快速鍵 <kbd>&#8984;</kbd>+<kbd>s</kbd>、功能表的 [檔案] > [儲存]，或是以滑鼠右鍵按一下檔案的索引標籤，並從操作功能表選取 [儲存] 來儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="bf420-180">Save the file by using the keyboard shortcut <kbd>&#8984;</kbd>+<kbd>s</kbd>, **File** > **Save** from the menu, or right-clicking on the file's tab and selecting **Save** from the context menu.</span></span>

   <span data-ttu-id="bf420-181">藉由將 `inputString` "Jack jack" 傳入 `GetWordCount`，您預期 `searchWord` "Jack" 會傳回兩個實例。</span><span class="sxs-lookup"><span data-stu-id="bf420-181">You expect that the `searchWord` "Jack" returns two instances with `inputString` "Jack jack" passed into `GetWordCount`.</span></span> <span data-ttu-id="bf420-182">按一下螢幕底部 [單元測試] 面板中的 [執行測試] 按鈕或 [測試結果] 面板中的 [重新執行測試] 按鈕來重新執行測試。</span><span class="sxs-lookup"><span data-stu-id="bf420-182">Run the test again by clicking the **Run Tests** button in the **Unit Tests** panel or the **Rerun Tests** button in the **Test Results** panel at the bottom of the screen.</span></span> <span data-ttu-id="bf420-183">測試就會成功。</span><span class="sxs-lookup"><span data-stu-id="bf420-183">The test passes.</span></span> <span data-ttu-id="bf420-184">字串 "Jack jack" 中有兩個 "Jack" 實例 (忽略大小寫)，且測試判斷提示為 `true`。</span><span class="sxs-lookup"><span data-stu-id="bf420-184">There are two instances of "Jack" in the string "Jack jack" (ignoring casing), and the test assertion is `true`.</span></span>

   ![測試成功](./media/using-on-mac-vs-full-solution/vsmacfull10.png)

1. <span data-ttu-id="bf420-186">使用 `Fact` 測試個別的傳回值，只是單元測試的初步用途。</span><span class="sxs-lookup"><span data-stu-id="bf420-186">Testing individual return values with a `Fact` is only the beginning of what you can do with unit testing.</span></span> <span data-ttu-id="bf420-187">另一個強大的技術，是使用 `Theory` 一次測試數個值。</span><span class="sxs-lookup"><span data-stu-id="bf420-187">Another powerful technique allows you to test several values at once using a `Theory`.</span></span> <span data-ttu-id="bf420-188">將下列方法加入至 `TextUtils_GetWordCountShould` 類別。</span><span class="sxs-lookup"><span data-stu-id="bf420-188">Add the following method to your `TextUtils_GetWordCountShould` class.</span></span> <span data-ttu-id="bf420-189">在您加入此方法後，您在類別中會有兩個方法：</span><span class="sxs-lookup"><span data-stu-id="bf420-189">You have two methods in the class after you add this method:</span></span>

   ```csharp
   [Theory]
   [InlineData(0, "Ting", "Does not appear in the string.")]
   [InlineData(1, "Ting", "Ting appears once.")]
   [InlineData(2, "Ting", "Ting appears twice with Ting.")]
   public void CountInstancesCorrectly(int count, 
                                       string searchWord, 
                                       string inputString)
   {
       Assert.NotEqual(count, WordCount.GetWordCount(searchWord,
                                                  inputString));
   }
   ```

   <span data-ttu-id="bf420-190">`CountInstancesCorrectly` 會檢查 `GetWordCount` 方法是否能正確計數。</span><span class="sxs-lookup"><span data-stu-id="bf420-190">The `CountInstancesCorrectly` checks that the `GetWordCount` method counts correctly.</span></span> <span data-ttu-id="bf420-191">`InlineData` 提供要檢查的計數、搜尋文字，以及輸入字串。</span><span class="sxs-lookup"><span data-stu-id="bf420-191">The `InlineData` provides a count, a search word, and an input string to check.</span></span> <span data-ttu-id="bf420-192">測試方法會針對每一行資料各執行一次。</span><span class="sxs-lookup"><span data-stu-id="bf420-192">The test method runs once for each line of data.</span></span> <span data-ttu-id="bf420-193">請注意，即使您知道資料中的計數是正確的，且值符合 `GetWordCount` 方法所傳回的計數，仍然要再次先使用 `Assert.NotEqual` 來判斷提示出錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf420-193">Note once again that you're asserting a failure first by using `Assert.NotEqual`, even when you know that the counts in the data are correct and that the values match the counts returned by the `GetWordCount` method.</span></span> <span data-ttu-id="bf420-194">執行刻意讓測試失敗的步驟，起初看起來似乎有點浪費時間，但是先透過讓測試失敗以檢查測試的邏輯，是一項對測試邏輯很重要的檢查。</span><span class="sxs-lookup"><span data-stu-id="bf420-194">Performing the step of failing the test on purpose might seem like a waste of time at first, but checking the logic of the test by failing it first is an important check on the logic of your tests.</span></span> <span data-ttu-id="bf420-195">當您遇到預期會失敗卻成功的測試方法時，代表測試邏輯中有錯誤。</span><span class="sxs-lookup"><span data-stu-id="bf420-195">When you come across a test method that passes when you expect it to fail, you've found a bug in the logic of the test.</span></span> <span data-ttu-id="bf420-196">每次當您建立測試方法時，都值得採取此步驟。</span><span class="sxs-lookup"><span data-stu-id="bf420-196">It's worth the effort to take this step every time you create a test method.</span></span>
   
1. <span data-ttu-id="bf420-197">儲存檔案，然後再次執行測試。</span><span class="sxs-lookup"><span data-stu-id="bf420-197">Save the file and run the tests again.</span></span> <span data-ttu-id="bf420-198">大小寫的測試會通過，但是三個計數測試會失敗。</span><span class="sxs-lookup"><span data-stu-id="bf420-198">The casing test passes but the three count tests fail.</span></span> <span data-ttu-id="bf420-199">這正是您預期會發生的情況。</span><span class="sxs-lookup"><span data-stu-id="bf420-199">This is exactly what you expect to happen.</span></span>

   ![測試失敗](./media/using-on-mac-vs-full-solution/vsmacfull11.png)

1. <span data-ttu-id="bf420-201">將 `Assert.NotEqual` 變更為 `Assert.Equal` 來修改 `CountInstancesCorrectly` 測試方法。</span><span class="sxs-lookup"><span data-stu-id="bf420-201">Modify the `CountInstancesCorrectly` test method by changing `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="bf420-202">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="bf420-202">Save the file.</span></span> <span data-ttu-id="bf420-203">再次執行測試。</span><span class="sxs-lookup"><span data-stu-id="bf420-203">Run the tests again.</span></span> <span data-ttu-id="bf420-204">所有測試皆通過。</span><span class="sxs-lookup"><span data-stu-id="bf420-204">All tests pass.</span></span>

   ![測試成功](./media/using-on-mac-vs-full-solution/vsmacfull12.png)

## <a name="adding-a-console-app"></a><span data-ttu-id="bf420-206">新增主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="bf420-206">Adding a console app</span></span>

1. <span data-ttu-id="bf420-207">在 [解決方案] 提要欄位中，以滑鼠右鍵按一下 `WordCounter` 解決方案。</span><span class="sxs-lookup"><span data-stu-id="bf420-207">In the **Solution** sidebar, right-click the `WordCounter` solution.</span></span> <span data-ttu-id="bf420-208">從 [.NET Core] > [應用程式] 範本中選取範本，來新增 [主控台應用程式] 專案。</span><span class="sxs-lookup"><span data-stu-id="bf420-208">Add a new **Console Application** project by selecting the template from the **.NET Core** > **App** templates.</span></span> <span data-ttu-id="bf420-209">選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="bf420-209">Select **Next**.</span></span> <span data-ttu-id="bf420-210">將專案命名為 **WordCounterApp**。</span><span class="sxs-lookup"><span data-stu-id="bf420-210">Name the project **WordCounterApp**.</span></span> <span data-ttu-id="bf420-211">選取 [建立] 以在解決方案中建立專案。</span><span class="sxs-lookup"><span data-stu-id="bf420-211">Select **Create** to create the project in the solution.</span></span>

1. <span data-ttu-id="bf420-212">在 [解決方案] 提要欄位中，以滑鼠右鍵按一下新的 [WordCounterApp] 專案的 [相依性] 節點。</span><span class="sxs-lookup"><span data-stu-id="bf420-212">In the **Solutions** sidebar, right-click the **Dependencies** node of the new **WordCounterApp** project.</span></span> <span data-ttu-id="bf420-213">在 [編輯參考] 對話方塊中，選取 [TextUtils] 並選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="bf420-213">In the **Edit References** dialog, check **TextUtils** and select **OK**.</span></span>

1. <span data-ttu-id="bf420-214">開啟 *Program.cs* 檔案。</span><span class="sxs-lookup"><span data-stu-id="bf420-214">Open the *Program.cs* file.</span></span> <span data-ttu-id="bf420-215">使用下列內容取代程式碼：</span><span class="sxs-lookup"><span data-stu-id="bf420-215">Replace the code with the following:</span></span>

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. <span data-ttu-id="bf420-216">若要在主控台視窗而非 IDE 中執行應用程式，請以滑鼠右鍵按一下 `WordCounterApp` 專案，選取 [選項]，並開啟 [組態] 底下的 [預設] 節點。</span><span class="sxs-lookup"><span data-stu-id="bf420-216">To run the app in a console window instead of the IDE, right-click the `WordCounterApp` project, select **Options**, and open the **Default** node under **Configurations**.</span></span> <span data-ttu-id="bf420-217">選取 [在外部主控台上執行] 方塊。</span><span class="sxs-lookup"><span data-stu-id="bf420-217">Check the box for **Run on external console**.</span></span> <span data-ttu-id="bf420-218">保持選取 [暫停主控台輸出] 選項。</span><span class="sxs-lookup"><span data-stu-id="bf420-218">Leave the **Pause console output** option checked.</span></span> <span data-ttu-id="bf420-219">此設定會造成應用程式在主控台視窗中繁衍，讓您可以輸入 `Console.ReadLine` 陳述式的輸入。</span><span class="sxs-lookup"><span data-stu-id="bf420-219">This setting causes the app to spawn in a console window so that you can type input for the `Console.ReadLine` statements.</span></span> <span data-ttu-id="bf420-220">如果您讓應用程式在 IDE 中執行，便只能看見 `Console.WriteLine` 陳述式的輸出。</span><span class="sxs-lookup"><span data-stu-id="bf420-220">If you leave the app to run in the IDE, you can only see the output of `Console.WriteLine` statements.</span></span> <span data-ttu-id="bf420-221">`Console.ReadLine` 陳述式不能在 IDE 的 [應用程式輸出] 面板中運作。</span><span class="sxs-lookup"><span data-stu-id="bf420-221">`Console.ReadLine` statements do not work in the IDE's **Application Output** panel.</span></span>

   ![[專案選項] 視窗](./media/using-on-mac-vs-full-solution/vsmacfull13.png)

1. <span data-ttu-id="bf420-223">由於目前版本的 Visual Studio for Mac 無法在解決方案執行時執行測試，您必須直接執行主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="bf420-223">Because the current version of Visual Studio for Mac cannot run the tests when the solution is run, you run the console app directly.</span></span> <span data-ttu-id="bf420-224">以滑鼠右鍵按一下 `WordCounterApp` 專案，並從操作功能表中選取 [執行項目]。</span><span class="sxs-lookup"><span data-stu-id="bf420-224">Right-click on the `WordCounterApp` project and select **Run item** from the context menu.</span></span> <span data-ttu-id="bf420-225">如果您嘗試使用 [播放] 按鈕執行應用程式，測試執行器和應用程式會無法執行。</span><span class="sxs-lookup"><span data-stu-id="bf420-225">If you attempt to run the app with the Play button, the test runner and app fail to run.</span></span> <span data-ttu-id="bf420-226">如需此問題工作狀態的詳細資訊，請參閱 [xunit/xamarinstudio.xunit (#60) (英文)](https://github.com/xunit/xamarinstudio.xunit/issues/60)。</span><span class="sxs-lookup"><span data-stu-id="bf420-226">For more information on the status of the work on this issue, see [xunit/xamarinstudio.xunit (#60)](https://github.com/xunit/xamarinstudio.xunit/issues/60).</span></span> <span data-ttu-id="bf420-227">當您執行應用程式時，請根據主控台視窗中的提示，提供搜尋文字和輸入字串的值。</span><span class="sxs-lookup"><span data-stu-id="bf420-227">When you run the app, provide values for the search word and input string at the prompts in the console window.</span></span> <span data-ttu-id="bf420-228">應用程式會指出搜尋文字在字串中出現的次數。</span><span class="sxs-lookup"><span data-stu-id="bf420-228">The app indicates the number of times the search word appears in the string.</span></span>

   ![主控台視窗，顯示字串 'Iro ate olives by the lake, and the olives were wonderful' 中搜尋文字 olives。](./media/using-on-mac-vs-full-solution/vsmacfull14.png)

1. <span data-ttu-id="bf420-231">最後一個要探索的功能，是使用 Visual Studio for Mac 進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="bf420-231">The last feature to explore is debugging with Visual Studio for Mac.</span></span> <span data-ttu-id="bf420-232">在 `Console.WriteLine` 陳述式上設定中斷點：選取行 23 的左邊界，您會在程式碼行旁邊看見一個紅色圓圈。</span><span class="sxs-lookup"><span data-stu-id="bf420-232">Set a breakpoint on the `Console.WriteLine` statement: Select in the left margin of line 23, and you see a red circle appear next to the line of code.</span></span> <span data-ttu-id="bf420-233">或者，選取程式碼行上的任何位置，並從功能表選取 [執行] > [切換中斷點]。</span><span class="sxs-lookup"><span data-stu-id="bf420-233">Alternatively, select anywhere on the line of code and select **Run** > **Toggle Breakpoint** from the menu.</span></span>

   ![行 23 (Console.WriteLine 陳述式) 上已設定中斷點](./media/using-on-mac-vs-full-solution/vsmacfull15.png)

1. <span data-ttu-id="bf420-235">以滑鼠右鍵按一下 `WordCounterApp` 專案。</span><span class="sxs-lookup"><span data-stu-id="bf420-235">Right-click the `WordCounterApp` project.</span></span> <span data-ttu-id="bf420-236">從操作功能表選取 [開始偵錯項目]。</span><span class="sxs-lookup"><span data-stu-id="bf420-236">Select **Start Debugging item** from the context menu.</span></span> <span data-ttu-id="bf420-237">當應用程式執行時，輸入搜尋的文字 "cat"，以及</span><span class="sxs-lookup"><span data-stu-id="bf420-237">When the app runs, enter the search word "cat" and "The dog chased the cat, but the cat escaped."</span></span> <span data-ttu-id="bf420-238">要搜尋的字串 "The dog chased the cat, but the cat escaped"。</span><span class="sxs-lookup"><span data-stu-id="bf420-238">for the string to search.</span></span> <span data-ttu-id="bf420-239">當到達 `Console.WriteLine` 陳述式時，程式執行會在執行該陳述式之前中止。</span><span class="sxs-lookup"><span data-stu-id="bf420-239">When the `Console.WriteLine` statement is reached, program execution halts before the statement is executed.</span></span> <span data-ttu-id="bf420-240">在 [區域變數] 索引標籤中，您可以看到 `searchWord`、`inputString`、`wordCount` 及 `pluralChar` 值。</span><span class="sxs-lookup"><span data-stu-id="bf420-240">In the **Locals** tab, you can see the `searchWord`, `inputString`, `wordCount`, and `pluralChar` values.</span></span>

   ![程式執行於 Console.WriteLine 陳述式停止，[區域變數] 視窗顯示執行 Console.WriteLine 陳述式之前的值。](./media/using-on-mac-vs-full-solution/vsmacfull16.png)

1. <span data-ttu-id="bf420-242">在 [即時運算] 窗格中，輸入 "wordCount = 999"，並按 Enter。</span><span class="sxs-lookup"><span data-stu-id="bf420-242">In the **Immediate** pane, type "wordCount = 999;" and press Enter.</span></span> <span data-ttu-id="bf420-243">這會將無意義值 999 指派給 `wordCount` 變數，顯示您可以在進行偵錯時取代變數值。</span><span class="sxs-lookup"><span data-stu-id="bf420-243">This assigns a nonsense value of 999 to the `wordCount` variable showing that you can replace variable values while debugging.</span></span>

   ![已叫用中斷點。](./media/using-on-mac-vs-full-solution/vsmacfull17.png)

1. <span data-ttu-id="bf420-246">在工具列中，按一下 [繼續] 箭號。</span><span class="sxs-lookup"><span data-stu-id="bf420-246">In the toolbar, click the *continue* arrow.</span></span> <span data-ttu-id="bf420-247">查看主控台視窗中的輸出。</span><span class="sxs-lookup"><span data-stu-id="bf420-247">Look at the output in the console window.</span></span> <span data-ttu-id="bf420-248">它會報告您在對應用程式進行偵錯時所設定的不正確值，999。</span><span class="sxs-lookup"><span data-stu-id="bf420-248">It reports the incorrect value of 999 that you set when you were debugging the app.</span></span>

   ![工具列中的 [繼續] 按鈕](./media/using-on-mac-vs-full-solution/vsmacfull18.png)

   ![應用程式輸出中的搜尋文字計數已變更為 999 的值](./media/using-on-mac-vs-full-solution/vsmacfull19.png)

## <a name="see-also"></a><span data-ttu-id="bf420-251">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bf420-251">See also</span></span>

[<span data-ttu-id="bf420-252">Visual Studio 2017 for Mac 版本資訊</span><span class="sxs-lookup"><span data-stu-id="bf420-252">Visual Studio 2017 for Mac Release Notes</span></span>](/visualstudio/releasenotes/vs2017-mac-relnotes)
