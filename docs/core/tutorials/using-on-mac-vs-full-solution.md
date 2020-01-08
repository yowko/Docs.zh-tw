---
title: 使用 Visual Studio for Mac 建立完整的 .NET Core 解決方案
description: 本文會逐步引導您建立 .NET Core 解決方案，其中包含可重複使用的程式庫和單元測試。
author: mairaw
ms.date: 12/19/2019
ms.custom: seodec18
ms.openlocfilehash: 361df77a45f22ae72e50a818cf0e2a5b24c4b67d
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75340263"
---
# <a name="build-a-complete-net-core-solution-on-macos-using-visual-studio-for-mac"></a><span data-ttu-id="efe23-103">使用 Visual Studio for Mac 在 macOS 上建立完整的 .NET Core 解決方案</span><span class="sxs-lookup"><span data-stu-id="efe23-103">Build a complete .NET Core solution on macOS using Visual Studio for Mac</span></span>

<span data-ttu-id="efe23-104">Visual Studio for Mac 針對開發 .NET Core 應用程式，提供功能完整的整合式開發環境 (IDE)。</span><span class="sxs-lookup"><span data-stu-id="efe23-104">Visual Studio for Mac provides a full-featured Integrated Development Environment (IDE) for developing .NET Core applications.</span></span> <span data-ttu-id="efe23-105">本文會逐步引導您建立 .NET Core 解決方案，其中包含可重複使用的程式庫和單元測試。</span><span class="sxs-lookup"><span data-stu-id="efe23-105">This article walks you through building a .NET Core solution that includes a reusable library and unit testing.</span></span>

<span data-ttu-id="efe23-106">本教學課程會示範如何建立能接受來自使用者的搜尋文字和文字字串、使用類別庫中的方法計算搜尋文字出現在字串中的次數，並將結果傳回給使用者的應用程式。</span><span class="sxs-lookup"><span data-stu-id="efe23-106">This tutorial shows you how to create an application that accepts a search word and a string of text from the user, counts the number of times the search word appears in the string using a method in a class library, and returns the result to the user.</span></span> <span data-ttu-id="efe23-107">解決方案也包含類別庫的單元測試，作為單元測試概念的簡介。</span><span class="sxs-lookup"><span data-stu-id="efe23-107">The solution also includes unit testing for the class library as an introduction to unit testing concepts.</span></span> <span data-ttu-id="efe23-108">如果您偏好使用完整範例來進行教學課程，請下載[範例解決方案 (英文)](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter)。</span><span class="sxs-lookup"><span data-stu-id="efe23-108">If you prefer to proceed through the tutorial with a complete sample, download the [sample solution](https://github.com/dotnet/samples/blob/master/core/tutorials/using-on-mac-vs-full-solution/WordCounter).</span></span> <span data-ttu-id="efe23-109">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="efe23-109">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

> [!NOTE]
> <span data-ttu-id="efe23-110">我們非常重視您的意見反應。</span><span class="sxs-lookup"><span data-stu-id="efe23-110">Your feedback is highly valued.</span></span> <span data-ttu-id="efe23-111">您有兩種方式可以提供意見反應給 Visual Studio for Mac 開發小組：</span><span class="sxs-lookup"><span data-stu-id="efe23-111">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> - <span data-ttu-id="efe23-112">在 Visual Studio for Mac 中，從功能表選取 [說明] > [回報問題]，或從歡迎畫面選取 [回報問題]，這會開啟用來提出錯誤報告的視窗。</span><span class="sxs-lookup"><span data-stu-id="efe23-112">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which opens a window for filing a bug report.</span></span> <span data-ttu-id="efe23-113">您可在[開發人員社群](https://developercommunity.visualstudio.com/spaces/41/index.html)入口網站追蹤您的意見反應。</span><span class="sxs-lookup"><span data-stu-id="efe23-113">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/41/index.html) portal.</span></span>
> - <span data-ttu-id="efe23-114">若要提出建議，請從功能表選取 [說明] > [提供建議]，或從歡迎畫面選取 [提供建議]，這會帶您前往 [Visual Studio for Mac 開發人員社群網頁](https://developercommunity.visualstudio.com/content/idea/post.html?space=41) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="efe23-114">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which takes you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="efe23-115">必要條件：</span><span class="sxs-lookup"><span data-stu-id="efe23-115">Prerequisites</span></span>

- [<span data-ttu-id="efe23-116">.NET Core SDK 3.1 或更新版本</span><span class="sxs-lookup"><span data-stu-id="efe23-116">.NET Core SDK 3.1 or later</span></span>](https://dotnet.microsoft.com/download)
- [<span data-ttu-id="efe23-117">適用于 Mac 的 Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="efe23-117">Visual Studio 2019 for Mac</span></span>](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

<span data-ttu-id="efe23-118">如需必要條件的詳細資訊，請參閱[.Net Core 相依性和需求](../install/dependencies.md?pivots=os-macos)。</span><span class="sxs-lookup"><span data-stu-id="efe23-118">For more information on prerequisites, see the [.NET Core dependencies and requirements](../install/dependencies.md?pivots=os-macos).</span></span> <span data-ttu-id="efe23-119">如需 Visual Studio 2019 for Mac 的完整系統需求，請參閱[Visual Studio 2019 For Mac 產品系列系統需求](/visualstudio/productinfo/vs2019-system-requirements-mac)。</span><span class="sxs-lookup"><span data-stu-id="efe23-119">For the full system requirements of Visual Studio 2019 for Mac, see [Visual Studio 2019 for Mac Product Family System Requirements](/visualstudio/productinfo/vs2019-system-requirements-mac).</span></span>

## <a name="building-a-library"></a><span data-ttu-id="efe23-120">建置程式庫</span><span class="sxs-lookup"><span data-stu-id="efe23-120">Building a library</span></span>

1. <span data-ttu-id="efe23-121">在 [開始] 視窗中，選取 [**新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="efe23-121">On the start window, select **New Project**.</span></span> <span data-ttu-id="efe23-122">在 [新增專案] 對話方塊中的 [.NET Core] 節點下，選取 [.NET Standard 程式庫] 範本。</span><span class="sxs-lookup"><span data-stu-id="efe23-122">In the **New Project** dialog under the **.NET Core** node, select the **.NET Standard Library** template.</span></span> <span data-ttu-id="efe23-123">此命令會建立以 .NET Core 為目標的 .NET Standard 程式庫，以及任何其他支援2.1 版[.NET Standard](../../standard/net-standard.md)的 .net 部署。</span><span class="sxs-lookup"><span data-stu-id="efe23-123">This command creates a .NET Standard library that targets .NET Core as well as any other .NET implementation that supports version 2.1 of the [.NET Standard](../../standard/net-standard.md).</span></span> <span data-ttu-id="efe23-124">如果您已安裝多個版本的 .NET Core SDK，可以為您的媒體櫃選擇不同版本的 .NET Standard。</span><span class="sxs-lookup"><span data-stu-id="efe23-124">If you have multiple versions of the .NET Core SDK installed, you can choose different versions of .NET Standard for your library.</span></span> <span data-ttu-id="efe23-125">選擇 [.NET Standard 2.1]，然後選取 **[下一步]** 。</span><span class="sxs-lookup"><span data-stu-id="efe23-125">Choose ".NET Standard 2.1" and select **Next**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="efe23-126">![Visual Studio for Mac 新增專案 對話方塊](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project.png)</span><span class="sxs-lookup"><span data-stu-id="efe23-126">![Visual Studio for Mac New project dialog](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project.png)</span></span>

1. <span data-ttu-id="efe23-127">將專案命名為 "TextUtils" (「文字公用程式」的簡短名稱)，並將解決方案命名為 "WordCounter"。</span><span class="sxs-lookup"><span data-stu-id="efe23-127">Name the project "TextUtils" (a short name for "Text Utilities") and the solution "WordCounter".</span></span> <span data-ttu-id="efe23-128">保持選取 [在解決方案目錄中建立專案目錄]。</span><span class="sxs-lookup"><span data-stu-id="efe23-128">Leave **Create a project directory within the solution directory** checked.</span></span> <span data-ttu-id="efe23-129">選取 [建立]。</span><span class="sxs-lookup"><span data-stu-id="efe23-129">Select **Create**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="efe23-130">![Visual Studio for Mac [新增專案] 對話方塊選項](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-options.png)</span><span class="sxs-lookup"><span data-stu-id="efe23-130">![Visual Studio for Mac New project dialog options](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-options.png)</span></span>

1. <span data-ttu-id="efe23-131">在 [ **Solution** pad] 中，展開 [`TextUtils`] 節點，以顯示範本所提供的類別檔案*Class1.cs*。</span><span class="sxs-lookup"><span data-stu-id="efe23-131">In the **Solution** pad, expand the `TextUtils` node to reveal the class file provided by the template, *Class1.cs*.</span></span> <span data-ttu-id="efe23-132">在檔案上按一下 Ctrl 鍵，從內容功能表中選取 [**重新命名**]，然後將檔案重新命名為*WordCount.cs*。</span><span class="sxs-lookup"><span data-stu-id="efe23-132">Ctrl-click the file, select **Rename** from the context menu, and rename the file to *WordCount.cs*.</span></span> <span data-ttu-id="efe23-133">開啟檔案，並以下列程式碼取代內容：</span><span class="sxs-lookup"><span data-stu-id="efe23-133">Open the file and replace the contents with the following code:</span></span>

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/TextUtils/WordCount.cs)]

1. <span data-ttu-id="efe23-134">使用三種不同的方法來儲存<kbd>盤</kbd>案：使用鍵盤快速鍵<kbd>&#8984;</kbd>+，從功能表**選取** 檔案 > **儲存**，或按 ctrl-按一下檔案的索引標籤，然後從內容功能表中選取 **儲存**。</span><span class="sxs-lookup"><span data-stu-id="efe23-134">Save the file by using any of three different methods: use the keyboard shortcut <kbd>&#8984;</kbd>+<kbd>s</kbd>, select **File** > **Save** from the menu, or ctrl-click on the file's tab and select **Save** from the contextual menu.</span></span> <span data-ttu-id="efe23-135">下圖顯示 IDE 視窗︰</span><span class="sxs-lookup"><span data-stu-id="efe23-135">The following image shows the IDE window:</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="efe23-136">具有類別庫檔案和方法的 ![Visual Studio for Mac IDE 視窗](./media/using-on-mac-vs-full-solution/visual-studio-mac-editor.png)</span><span class="sxs-lookup"><span data-stu-id="efe23-136">![Visual Studio for Mac IDE window with class library file and method](./media/using-on-mac-vs-full-solution/visual-studio-mac-editor.png)</span></span>

1. <span data-ttu-id="efe23-137">選取 IDE 視窗下邊界中的 [錯誤]，以開啟 [錯誤] 面板。</span><span class="sxs-lookup"><span data-stu-id="efe23-137">Select **Errors** in the margin at the bottom of the IDE window to open the **Errors** panel.</span></span> <span data-ttu-id="efe23-138">選取 [建置輸出] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="efe23-138">Select the **Build Output** button.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="efe23-139">![Visual Studio Mac IDE 的下邊界，顯示 [錯誤] 按鈕](./media/using-on-mac-vs-full-solution/visual-studio-mac-error-button.png)</span><span class="sxs-lookup"><span data-stu-id="efe23-139">![Bottom margin of the Visual Studio Mac IDE showing the Errors button](./media/using-on-mac-vs-full-solution/visual-studio-mac-error-button.png)</span></span>

1. <span data-ttu-id="efe23-140">從功能表選取 [建置] > [全部建置]。</span><span class="sxs-lookup"><span data-stu-id="efe23-140">Select **Build** > **Build All** from the menu.</span></span>

   <span data-ttu-id="efe23-141">解決方案隨即建置。</span><span class="sxs-lookup"><span data-stu-id="efe23-141">The solution builds.</span></span> <span data-ttu-id="efe23-142">建置輸出面板會顯示建置成功。</span><span class="sxs-lookup"><span data-stu-id="efe23-142">The build output panel shows that the build is successful.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="efe23-143">![[錯誤] 面板的 [Visual Studio Mac 組建輸出] 窗格，其中包含組建成功訊息](./media/using-on-mac-vs-full-solution/visual-studio-mac-build-panel.png)</span><span class="sxs-lookup"><span data-stu-id="efe23-143">![Visual Studio Mac Build output pane of the Errors panel with Build successful message](./media/using-on-mac-vs-full-solution/visual-studio-mac-build-panel.png)</span></span>

## <a name="creating-a-test-project"></a><span data-ttu-id="efe23-144">建立測試專案</span><span class="sxs-lookup"><span data-stu-id="efe23-144">Creating a test project</span></span>

<span data-ttu-id="efe23-145">單元測試能在開發與發佈期間提供自動化的軟體測試。</span><span class="sxs-lookup"><span data-stu-id="efe23-145">Unit tests provide automated software testing during your development and publishing.</span></span> <span data-ttu-id="efe23-146">您在本教學課程中使用的測試架構是[xUnit （version 2.4.0 或更新版本）](https://xunit.github.io/)，會在下列步驟中將 xUnit 測試專案加入至方案時自動安裝：</span><span class="sxs-lookup"><span data-stu-id="efe23-146">The testing framework that you use in this tutorial is [xUnit (version 2.4.0 or later)](https://xunit.github.io/), which is installed automatically when the xUnit test project is added to the solution in the following steps:</span></span>

1. <span data-ttu-id="efe23-147">在 **方案** 提要欄位中，以 ctrl 按一下 `WordCounter` 方案，**然後選取 新增** > **加入新專案**。</span><span class="sxs-lookup"><span data-stu-id="efe23-147">In the **Solution** sidebar, ctrl-click the `WordCounter` solution and select **Add** > **Add New Project**.</span></span>

1. <span data-ttu-id="efe23-148">在 [新增專案] 對話方塊中，從 [.NET Core] 節點選取 [測試]。</span><span class="sxs-lookup"><span data-stu-id="efe23-148">In the **New Project** dialog, select **Tests** from the **.NET Core** node.</span></span> <span data-ttu-id="efe23-149">選取 [xUnit 測試專案]，接著選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="efe23-149">Select the **xUnit Test Project** followed by **Next**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="efe23-150">![Visual Studio Mac [新增專案] 對話方塊建立 xUnit 測試專案](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-project.png)</span><span class="sxs-lookup"><span data-stu-id="efe23-150">![Visual Studio Mac New Project dialog creating xUnit test project](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-project.png)</span></span>

1. <span data-ttu-id="efe23-151">如果您有多個版本的 .NET Core SDK，則必須選取此專案的版本。</span><span class="sxs-lookup"><span data-stu-id="efe23-151">If you have multiple versions of the .NET Core SDK, you'll need to select the version for this project.</span></span> <span data-ttu-id="efe23-152">選取 [ **.Net Core 3.1**]。</span><span class="sxs-lookup"><span data-stu-id="efe23-152">Select **.NET Core 3.1**.</span></span> <span data-ttu-id="efe23-153">將新專案命名為 "TestLibrary"，並選取 [建立]。</span><span class="sxs-lookup"><span data-stu-id="efe23-153">Name the new project "TestLibrary" and select **Create**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="efe23-154">![Visual Studio Mac [新增專案] 對話方塊，提供專案名稱](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-name.png)</span><span class="sxs-lookup"><span data-stu-id="efe23-154">![Visual Studio Mac New Project dialog providing project name](./media/using-on-mac-vs-full-solution/visual-studio-mac-new-project-name.png)</span></span>

1. <span data-ttu-id="efe23-155">為了讓測試程式庫能搭配 `WordCount` 類別使用，請將參考加入 `TextUtils` 專案。</span><span class="sxs-lookup"><span data-stu-id="efe23-155">In order for the test library to work with the `WordCount` class, add a reference to the `TextUtils` project.</span></span> <span data-ttu-id="efe23-156">在 [**解決方案**] 提要欄位中，按一下 [ **TestLibrary**] 底下的 [相依性 **]** 。</span><span class="sxs-lookup"><span data-stu-id="efe23-156">In the **Solution** sidebar, ctrl-click **Dependencies** under **TestLibrary**.</span></span> <span data-ttu-id="efe23-157">從操作功能表選取 [編輯參考]。</span><span class="sxs-lookup"><span data-stu-id="efe23-157">Select **Edit References** from the context menu.</span></span>

1. <span data-ttu-id="efe23-158">在 [**編輯參考**] 對話方塊中，選取 [**專案**] 索引標籤上的 [ **TextUtils** ] 專案。選取 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="efe23-158">In the **Edit References** dialog, select the **TextUtils** project on the **Projects** tab. Select **OK**.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="efe23-159">![Visual Studio Mac 編輯參考 對話方塊](./media/using-on-mac-vs-full-solution/visual-studio-mac-edit-references.png)</span><span class="sxs-lookup"><span data-stu-id="efe23-159">![Visual Studio Mac Edit References dialog](./media/using-on-mac-vs-full-solution/visual-studio-mac-edit-references.png)</span></span>

1. <span data-ttu-id="efe23-160">在 [TestLibrary] 專案中，將 *UnitTest1.cs* 檔案重新命名為 *TextUtilsTests.cs*。</span><span class="sxs-lookup"><span data-stu-id="efe23-160">In the **TestLibrary** project, rename the *UnitTest1.cs* file to *TextUtilsTests.cs*.</span></span>

1. <span data-ttu-id="efe23-161">開啟檔案，並以下列程式碼取代程式碼：</span><span class="sxs-lookup"><span data-stu-id="efe23-161">Open the file and replace the code with the following code:</span></span>

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

   <span data-ttu-id="efe23-162">下圖顯示具有單元測試程式碼的 IDE。</span><span class="sxs-lookup"><span data-stu-id="efe23-162">The following image shows the IDE with the unit test code in place.</span></span> <span data-ttu-id="efe23-163">請留意 `Assert.NotEqual` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="efe23-163">Pay attention to the `Assert.NotEqual` statement.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="efe23-164">IDE 主視窗中的 ![Visual Studio for Mac 初始單元測試](./media/using-on-mac-vs-full-solution/visual-studio-mac-assert-test.png)</span><span class="sxs-lookup"><span data-stu-id="efe23-164">![Visual Studio for Mac Initial unit test in the IDE main window](./media/using-on-mac-vs-full-solution/visual-studio-mac-assert-test.png)</span></span>

   <span data-ttu-id="efe23-165">請務必讓新的測試失敗一次，以確認其測試邏輯正確。</span><span class="sxs-lookup"><span data-stu-id="efe23-165">It's important to make a new test fail once to confirm its testing logic is correct.</span></span> <span data-ttu-id="efe23-166">該方法會傳入 "Jack" (大寫) 這個名字，以及具有 "Jack" 和 "jack" (大寫與小寫) 的字串。</span><span class="sxs-lookup"><span data-stu-id="efe23-166">The method passes in the name "Jack" (uppercase) and a string with "Jack" and "jack" (uppercase and lowercase).</span></span> <span data-ttu-id="efe23-167">如果 `GetWordCount` 方法能正常運作，它會針對搜尋文字傳回兩個實例計數。</span><span class="sxs-lookup"><span data-stu-id="efe23-167">If the `GetWordCount` method is working properly, it returns a count of two instances of the search word.</span></span> <span data-ttu-id="efe23-168">為了刻意讓此測試失敗，您會先實作測試，以判斷提示 `GetWordCount` 方法沒有傳回搜尋文字 "Jack" 的兩個實例。</span><span class="sxs-lookup"><span data-stu-id="efe23-168">In order to fail this test on purpose, you first implement the test asserting that two instances of the search word "Jack" aren't returned by the `GetWordCount` method.</span></span> <span data-ttu-id="efe23-169">繼續進行下一個步驟以刻意讓測試失敗。</span><span class="sxs-lookup"><span data-stu-id="efe23-169">Continue to the next step to fail the test on purpose.</span></span>

1. <span data-ttu-id="efe23-170">開啟螢幕右側的 [單元測試] 面板。</span><span class="sxs-lookup"><span data-stu-id="efe23-170">Open the **Unit Tests** panel on the right side of the screen.</span></span> <span data-ttu-id="efe23-171">從功能表中選取 [ **View** > **測試**]。</span><span class="sxs-lookup"><span data-stu-id="efe23-171">Select **View** > **Tests** from the menu.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="efe23-172">![Visual Studio for Mac 單元測試 面板](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-panel.png)</span><span class="sxs-lookup"><span data-stu-id="efe23-172">![Visual Studio for Mac Unit Tests panel](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-panel.png)</span></span>

1. <span data-ttu-id="efe23-173">按一下**固定**圖示維持面板開啟。</span><span class="sxs-lookup"><span data-stu-id="efe23-173">Click the **Dock** icon to keep the panel open.</span></span> <span data-ttu-id="efe23-174">（在下圖中反白顯示）。</span><span class="sxs-lookup"><span data-stu-id="efe23-174">(Highlighted in the following image.)</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="efe23-175">![Visual Studio for Mac 單元測試面板停駐圖示](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-dock-icon.png)</span><span class="sxs-lookup"><span data-stu-id="efe23-175">![Visual Studio for Mac Unit Tests panel dock icon](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-dock-icon.png)</span></span>

1. <span data-ttu-id="efe23-176">按一下 [全部執行] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="efe23-176">Click the **Run All** button.</span></span>

   <span data-ttu-id="efe23-177">測試會失敗，這是正確的結果。</span><span class="sxs-lookup"><span data-stu-id="efe23-177">The test fails, which is the correct result.</span></span> <span data-ttu-id="efe23-178">測試方法會判斷提示 `inputString` 的兩個實例 ("Jack") 沒有從提供給 `GetWordCount` 方法的字串 "Jack jack" 傳回。</span><span class="sxs-lookup"><span data-stu-id="efe23-178">The test method asserts that two instances of the `inputString`, "Jack," aren't returned from the string "Jack jack" provided to the `GetWordCount` method.</span></span> <span data-ttu-id="efe23-179">由於文字大小寫的因素已經在 `GetWordCount` 方法中排除，因此會傳回兩個實例。</span><span class="sxs-lookup"><span data-stu-id="efe23-179">Since word casing was factored out in the `GetWordCount` method, two instances are returned.</span></span> <span data-ttu-id="efe23-180">2「不等於」2 的判斷提示將會失敗。</span><span class="sxs-lookup"><span data-stu-id="efe23-180">The assertion that 2 *is not equal to* 2 fails.</span></span> <span data-ttu-id="efe23-181">這個結果是正確的結果，而我們的測試邏輯就是好的。</span><span class="sxs-lookup"><span data-stu-id="efe23-181">This result is the correct outcome, and the logic of our test is good.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="efe23-182">![Visual Studio for Mac 測試失敗顯示](./media/using-on-mac-vs-full-solution/visual-studio-for-mac-unit-test-failure.png)</span><span class="sxs-lookup"><span data-stu-id="efe23-182">![Visual Studio for Mac test failure display](./media/using-on-mac-vs-full-solution/visual-studio-for-mac-unit-test-failure.png)</span></span>

1. <span data-ttu-id="efe23-183">將 `Assert.NotEqual` 變更為 `Assert.Equal` 來修改 `IgnoreCasing` 測試方法。</span><span class="sxs-lookup"><span data-stu-id="efe23-183">Modify the `IgnoreCasing` test method by changing `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="efe23-184">使用鍵盤快速鍵<kbd>Ctrl</kbd>+<kbd>s 儲存檔</kbd>案，然後從功能表中選取 [**檔案 > \*\* **儲存**]，或在檔案的索引標籤上按一下滑鼠右鍵，然後從內容功能表中選取 [**儲存\*\*]。</span><span class="sxs-lookup"><span data-stu-id="efe23-184">Save the file by using the keyboard shortcut <kbd>Ctrl</kbd>+<kbd>s</kbd>, **File** > **Save** from the menu, or ctrl-clicking on the file's tab and selecting **Save** from the context menu.</span></span>

   <span data-ttu-id="efe23-185">藉由將 `inputString` "Jack jack" 傳入 `GetWordCount`，您預期 `searchWord` "Jack" 會傳回兩個實例。</span><span class="sxs-lookup"><span data-stu-id="efe23-185">You expect that the `searchWord` "Jack" returns two instances with `inputString` "Jack jack" passed into `GetWordCount`.</span></span> <span data-ttu-id="efe23-186">按一下螢幕底部 [單元測試] 面板中的 [執行測試] 按鈕或 [測試結果] 面板中的 [重新執行測試] 按鈕來重新執行測試。</span><span class="sxs-lookup"><span data-stu-id="efe23-186">Run the test again by clicking the **Run Tests** button in the **Unit Tests** panel or the **Rerun Tests** button in the **Test Results** panel at the bottom of the screen.</span></span> <span data-ttu-id="efe23-187">測試就會成功。</span><span class="sxs-lookup"><span data-stu-id="efe23-187">The test passes.</span></span> <span data-ttu-id="efe23-188">字串 "Jack jack" 中有兩個 "Jack" 實例 (忽略大小寫)，且測試判斷提示為 `true`。</span><span class="sxs-lookup"><span data-stu-id="efe23-188">There are two instances of "Jack" in the string "Jack jack" (ignoring casing), and the test assertion is `true`.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="efe23-189">![Visual Studio for Mac 測試通過顯示](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)</span><span class="sxs-lookup"><span data-stu-id="efe23-189">![Visual Studio for Mac tests pass display](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)</span></span>

1. <span data-ttu-id="efe23-190">使用 `Fact` 測試個別的傳回值，只是單元測試的初步用途。</span><span class="sxs-lookup"><span data-stu-id="efe23-190">Testing individual return values with a `Fact` is only the beginning of what you can do with unit testing.</span></span> <span data-ttu-id="efe23-191">另一個強大的技術，是使用 `Theory` 一次測試數個值。</span><span class="sxs-lookup"><span data-stu-id="efe23-191">Another powerful technique allows you to test several values at once using a `Theory`.</span></span> <span data-ttu-id="efe23-192">將下列方法加入至 `TextUtils_GetWordCountShould` 類別。</span><span class="sxs-lookup"><span data-stu-id="efe23-192">Add the following method to your `TextUtils_GetWordCountShould` class.</span></span> <span data-ttu-id="efe23-193">在您加入此方法後，您在類別中會有兩個方法：</span><span class="sxs-lookup"><span data-stu-id="efe23-193">You have two methods in the class after you add this method:</span></span>

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

   <span data-ttu-id="efe23-194">`CountInstancesCorrectly` 會檢查 `GetWordCount` 方法是否能正確計數。</span><span class="sxs-lookup"><span data-stu-id="efe23-194">The `CountInstancesCorrectly` checks that the `GetWordCount` method counts correctly.</span></span> <span data-ttu-id="efe23-195">`InlineData` 提供要檢查的計數、搜尋文字，以及輸入字串。</span><span class="sxs-lookup"><span data-stu-id="efe23-195">The `InlineData` provides a count, a search word, and an input string to check.</span></span> <span data-ttu-id="efe23-196">測試方法會針對每一行資料各執行一次。</span><span class="sxs-lookup"><span data-stu-id="efe23-196">The test method runs once for each line of data.</span></span> <span data-ttu-id="efe23-197">請注意，即使您知道資料中的計數是正確的，且值符合 `GetWordCount` 方法所傳回的計數，仍然要再次先使用 `Assert.NotEqual` 來判斷提示出錯誤。</span><span class="sxs-lookup"><span data-stu-id="efe23-197">Note once again that you're asserting a failure first by using `Assert.NotEqual`, even when you know that the counts in the data are correct and that the values match the counts returned by the `GetWordCount` method.</span></span> <span data-ttu-id="efe23-198">執行刻意讓測試失敗的步驟，起初看起來似乎有點浪費時間，但是先透過讓測試失敗以檢查測試的邏輯，是一項對測試邏輯很重要的檢查。</span><span class="sxs-lookup"><span data-stu-id="efe23-198">Performing the step of failing the test on purpose might seem like a waste of time at first, but checking the logic of the test by failing it first is an important check on the logic of your tests.</span></span> <span data-ttu-id="efe23-199">當您遇到預期會失敗卻成功的測試方法時，代表測試邏輯中有錯誤。</span><span class="sxs-lookup"><span data-stu-id="efe23-199">When you come across a test method that passes when you expect it to fail, you've found a bug in the logic of the test.</span></span> <span data-ttu-id="efe23-200">每次當您建立測試方法時，都值得採取此步驟。</span><span class="sxs-lookup"><span data-stu-id="efe23-200">It's worth the effort to take this step every time you create a test method.</span></span>

1. <span data-ttu-id="efe23-201">儲存檔案，然後再次執行測試。</span><span class="sxs-lookup"><span data-stu-id="efe23-201">Save the file and run the tests again.</span></span> <span data-ttu-id="efe23-202">大小寫的測試會通過，但是三個計數測試會失敗。</span><span class="sxs-lookup"><span data-stu-id="efe23-202">The casing test passes but the three count tests fail.</span></span> <span data-ttu-id="efe23-203">這就是您預期會發生的結果。</span><span class="sxs-lookup"><span data-stu-id="efe23-203">This outcome is exactly what you expect to happen.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="efe23-204">![Visual Studio for Mac 預期的測試失敗](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-failure.png)</span><span class="sxs-lookup"><span data-stu-id="efe23-204">![Visual Studio for Mac expected test failure](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-failure.png)</span></span>

1. <span data-ttu-id="efe23-205">將 `Assert.NotEqual` 變更為 `Assert.Equal` 來修改 `CountInstancesCorrectly` 測試方法。</span><span class="sxs-lookup"><span data-stu-id="efe23-205">Modify the `CountInstancesCorrectly` test method by changing `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="efe23-206">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="efe23-206">Save the file.</span></span> <span data-ttu-id="efe23-207">再次執行測試。</span><span class="sxs-lookup"><span data-stu-id="efe23-207">Run the tests again.</span></span> <span data-ttu-id="efe23-208">所有測試皆通過。</span><span class="sxs-lookup"><span data-stu-id="efe23-208">All tests pass.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="efe23-209">![Visual Studio for Mac 預期的測試階段](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)</span><span class="sxs-lookup"><span data-stu-id="efe23-209">![Visual Studio for Mac expected test passes](./media/using-on-mac-vs-full-solution/visual-studio-mac-unit-test-pass.png)</span></span>

## <a name="adding-a-console-app"></a><span data-ttu-id="efe23-210">新增主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="efe23-210">Adding a console app</span></span>

1. <span data-ttu-id="efe23-211">在 [**解決方案**] 提要欄位中，以 ctrl 鍵按一下 [`WordCounter`] 方案。</span><span class="sxs-lookup"><span data-stu-id="efe23-211">In the **Solution** sidebar, ctrl-click the `WordCounter` solution.</span></span> <span data-ttu-id="efe23-212">從 [.NET Core] > [應用程式] 範本中選取範本，來新增 [主控台應用程式] 專案。</span><span class="sxs-lookup"><span data-stu-id="efe23-212">Add a new **Console Application** project by selecting the template from the **.NET Core** > **App** templates.</span></span> <span data-ttu-id="efe23-213">選取 [下一步]。</span><span class="sxs-lookup"><span data-stu-id="efe23-213">Select **Next**.</span></span> <span data-ttu-id="efe23-214">將專案命名為 **WordCounterApp**。</span><span class="sxs-lookup"><span data-stu-id="efe23-214">Name the project **WordCounterApp**.</span></span> <span data-ttu-id="efe23-215">選取 [建立] 以在解決方案中建立專案。</span><span class="sxs-lookup"><span data-stu-id="efe23-215">Select **Create** to create the project in the solution.</span></span>

1. <span data-ttu-id="efe23-216">在 [**方案**] 提要欄位中，以 ctrl 按一下新**WordCounterApp**專案的 [相依性 **]** 節點。</span><span class="sxs-lookup"><span data-stu-id="efe23-216">In the **Solutions** sidebar, ctrl-click the **Dependencies** node of the new **WordCounterApp** project.</span></span> <span data-ttu-id="efe23-217">在 [編輯參考] 對話方塊中，選取 [TextUtils] 並選取 [確定]。</span><span class="sxs-lookup"><span data-stu-id="efe23-217">In the **Edit References** dialog, check **TextUtils** and select **OK**.</span></span>

1. <span data-ttu-id="efe23-218">開啟 *Program.cs* 檔案。</span><span class="sxs-lookup"><span data-stu-id="efe23-218">Open the *Program.cs* file.</span></span> <span data-ttu-id="efe23-219">將程式碼取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="efe23-219">Replace the code with the following code:</span></span>

   [!code-csharp[Main](../../../samples/core/tutorials/using-on-mac-vs-full-solution/WordCounter/WordCounterApp/Program.cs)]

1. <span data-ttu-id="efe23-220">Ctrl-按一下 [`WordCounterApp`] 專案，然後從內容功能表中選取 [**執行專案**]。</span><span class="sxs-lookup"><span data-stu-id="efe23-220">Ctrl-click on the `WordCounterApp` project and select **Run project** from the context menu.</span></span> <span data-ttu-id="efe23-221">當您執行應用程式時，請根據主控台視窗中的提示，提供搜尋文字和輸入字串的值。</span><span class="sxs-lookup"><span data-stu-id="efe23-221">When you run the app, provide values for the search word and input string at the prompts in the console window.</span></span> <span data-ttu-id="efe23-222">應用程式會指出搜尋文字在字串中出現的次數。</span><span class="sxs-lookup"><span data-stu-id="efe23-222">The app indicates the number of times the search word appears in the string.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="efe23-223">![Visual Studio for Mac 主控台視窗，顯示您的應用程式正在執行](./media/using-on-mac-vs-full-solution/visual-studio-mac-console-window.png)</span><span class="sxs-lookup"><span data-stu-id="efe23-223">![Visual Studio for Mac console window showing your app running](./media/using-on-mac-vs-full-solution/visual-studio-mac-console-window.png)</span></span>

1. <span data-ttu-id="efe23-224">最後一個要探索的功能，是使用 Visual Studio for Mac 進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="efe23-224">The last feature to explore is debugging with Visual Studio for Mac.</span></span> <span data-ttu-id="efe23-225">在 `Console.WriteLine` 陳述式上設定中斷點：選取行 23 的左邊界，您會在程式碼行旁邊看見一個紅色圓圈。</span><span class="sxs-lookup"><span data-stu-id="efe23-225">Set a breakpoint on the `Console.WriteLine` statement: Select in the left margin of line 23, and you see a red circle appear next to the line of code.</span></span> <span data-ttu-id="efe23-226">或者，選取程式碼行上的任何位置，並從功能表選取 [執行] > [切換中斷點]。</span><span class="sxs-lookup"><span data-stu-id="efe23-226">Alternatively, select anywhere on the line of code and select **Run** > **Toggle Breakpoint** from the menu.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="efe23-227">![Visual Studio for Mac 中斷點集](./media/using-on-mac-vs-full-solution/visual-studio-mac-breakpoint.png)</span><span class="sxs-lookup"><span data-stu-id="efe23-227">![Visual Studio for Mac breakpoint set](./media/using-on-mac-vs-full-solution/visual-studio-mac-breakpoint.png)</span></span>

1. <span data-ttu-id="efe23-228">按 ctrl-按一下 [`WordCounterApp`] 專案。</span><span class="sxs-lookup"><span data-stu-id="efe23-228">ctrl-click the `WordCounterApp` project.</span></span> <span data-ttu-id="efe23-229">從內容功能表中選取 [**開始調試專案**]。</span><span class="sxs-lookup"><span data-stu-id="efe23-229">Select **Start Debugging Project** from the context menu.</span></span> <span data-ttu-id="efe23-230">當應用程式執行時，輸入搜尋的文字 "cat"，以及</span><span class="sxs-lookup"><span data-stu-id="efe23-230">When the app runs, enter the search word "cat" and "The dog chased the cat, but the cat escaped."</span></span> <span data-ttu-id="efe23-231">要搜尋的字串 "The dog chased the cat, but the cat escaped"。</span><span class="sxs-lookup"><span data-stu-id="efe23-231">for the string to search.</span></span> <span data-ttu-id="efe23-232">當到達 `Console.WriteLine` 陳述式時，程式執行會在執行該陳述式之前中止。</span><span class="sxs-lookup"><span data-stu-id="efe23-232">When the `Console.WriteLine` statement is reached, program execution halts before the statement is executed.</span></span> <span data-ttu-id="efe23-233">在 [區域變數] 索引標籤中，您可以看到 `searchWord`、`inputString`、`wordCount` 及 `pluralChar` 值。</span><span class="sxs-lookup"><span data-stu-id="efe23-233">In the **Locals** tab, you can see the `searchWord`, `inputString`, `wordCount`, and `pluralChar` values.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="efe23-234">![Visual Studio for Mac 偵錯工具執行已停止](./media/using-on-mac-vs-full-solution/visual-studio-mac-debugger.png)</span><span class="sxs-lookup"><span data-stu-id="efe23-234">![Visual Studio for Mac debugger program execution stopped](./media/using-on-mac-vs-full-solution/visual-studio-mac-debugger.png)</span></span>

1. <span data-ttu-id="efe23-235">在 [即時運算] 窗格中，輸入 "wordCount = 999"，並按 Enter。</span><span class="sxs-lookup"><span data-stu-id="efe23-235">In the **Immediate** pane, type "wordCount = 999;" and press Enter.</span></span> <span data-ttu-id="efe23-236">此命令會將沒有意義的值999指派給 `wordCount` 變數，顯示您可以在進行偵錯工具時取代變數值。</span><span class="sxs-lookup"><span data-stu-id="efe23-236">This command assigns a nonsense value of 999 to the `wordCount` variable showing that you can replace variable values while debugging.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="efe23-237">![Visual Studio for Mac 變更 [即時運算] 視窗中的值](./media/using-on-mac-vs-full-solution/visual-studio-mac-immediate-window.png)</span><span class="sxs-lookup"><span data-stu-id="efe23-237">![Visual Studio for Mac changing values in the immediate window](./media/using-on-mac-vs-full-solution/visual-studio-mac-immediate-window.png)</span></span>

1. <span data-ttu-id="efe23-238">在工具列中，按一下 [繼續] 箭號。</span><span class="sxs-lookup"><span data-stu-id="efe23-238">In the toolbar, click the *continue* arrow.</span></span> <span data-ttu-id="efe23-239">查看主控台視窗中的輸出。</span><span class="sxs-lookup"><span data-stu-id="efe23-239">Look at the output in the console window.</span></span> <span data-ttu-id="efe23-240">它會報告您在對應用程式進行偵錯時所設定的不正確值，999。</span><span class="sxs-lookup"><span data-stu-id="efe23-240">It reports the incorrect value of 999 that you set when you were debugging the app.</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="efe23-241">![工具列中 Visual Studio for Mac 繼續 按鈕](./media/using-on-mac-vs-full-solution/visual-studio-mac-toolbar.png)</span><span class="sxs-lookup"><span data-stu-id="efe23-241">![Visual Studio for Mac continue button in the toolbar](./media/using-on-mac-vs-full-solution/visual-studio-mac-toolbar.png)</span></span>

   > [!div class="mx-imgBorder"]
   > <span data-ttu-id="efe23-242">![Visual Studio for Mac 主控台視窗輸出](./media/using-on-mac-vs-full-solution/visual-studio-mac-output.png)</span><span class="sxs-lookup"><span data-stu-id="efe23-242">![Visual Studio for Mac console window output](./media/using-on-mac-vs-full-solution/visual-studio-mac-output.png)</span></span>

<span data-ttu-id="efe23-243">您可以使用相同的程式，以使用您的單元測試專案來偵錯工具代碼。</span><span class="sxs-lookup"><span data-stu-id="efe23-243">You can use the same process to debug code using your unit test project.</span></span> <span data-ttu-id="efe23-244">不要啟動 WordCount 應用程式專案，而是在測試連結**庫**專案上按一下，然後從內容功能表中選取 [**啟動調試**程式]。</span><span class="sxs-lookup"><span data-stu-id="efe23-244">Instead of starting the WordCount app project, ctrl-click the **Test Library** project, and select **Start Debugging Project** from the context menu.</span></span> <span data-ttu-id="efe23-245">Visual Studio for Mac 啟動已附加偵錯工具的測試專案。</span><span class="sxs-lookup"><span data-stu-id="efe23-245">Visual Studio for Mac starts your test project with the debugger attached.</span></span> <span data-ttu-id="efe23-246">執行會在您已加入測試專案或基礎程式庫程式碼的任何中斷點停止。</span><span class="sxs-lookup"><span data-stu-id="efe23-246">Execution will stop at any breakpoint you've added to the test project, or the underlying library code.</span></span>

## <a name="see-also"></a><span data-ttu-id="efe23-247">請參閱</span><span class="sxs-lookup"><span data-stu-id="efe23-247">See also</span></span>

- [<span data-ttu-id="efe23-248">Visual Studio 2019 for Mac 版本資訊</span><span class="sxs-lookup"><span data-stu-id="efe23-248">Visual Studio 2019 for Mac Release Notes</span></span>](/visualstudio/releasenotes/vs2019-mac-relnotes)
