---
title: 使用 Visual Studio for Mac 建立 .NET Standard 類別庫
description: 瞭解如何使用 Visual Studio for Mac 建立 .NET Standard 類別庫。
ms.date: 06/08/2020
ms.openlocfilehash: 3a107fff2fd6aef5e06d9af3eac334fbf5688fa5
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2020
ms.locfileid: "84713739"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-for-mac"></a><span data-ttu-id="b7360-103">教學課程：使用 Visual Studio for Mac 建立 .NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="b7360-103">Tutorial: Create a .NET Standard library using Visual Studio for Mac</span></span>

<span data-ttu-id="b7360-104">在本教學課程中，您會建立包含單一字串處理方法的簡單類別庫。</span><span class="sxs-lookup"><span data-stu-id="b7360-104">In this tutorial, you create a simple class library that contains a single string-handling method.</span></span> <span data-ttu-id="b7360-105">您可以將它實作為[擴充方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)，讓您可以如同類別的成員一樣呼叫它 <xref:System.String> 。</span><span class="sxs-lookup"><span data-stu-id="b7360-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="b7360-106">「類別庫」\*\* 會定義應用程式所呼叫的類型和方法。</span><span class="sxs-lookup"><span data-stu-id="b7360-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="b7360-107">以 .NET Standard 2.1 為目標的類別庫可供以任何支援2.1 版 .NET Standard 的 .NET 實作為目標的應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="b7360-107">A class library that targets .NET Standard 2.1 can be used by an application that targets any .NET implementation that supports version 2.1 of .NET Standard.</span></span> <span data-ttu-id="b7360-108">當您完成類別庫時，您可以將它散發為協力廠商元件，或作為一或多個應用程式的配套元件。</span><span class="sxs-lookup"><span data-stu-id="b7360-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="b7360-109">我們非常重視您的意見反應。</span><span class="sxs-lookup"><span data-stu-id="b7360-109">Your feedback is highly valued.</span></span> <span data-ttu-id="b7360-110">您有兩種方式可以提供意見反應給 Visual Studio for Mac 開發小組：</span><span class="sxs-lookup"><span data-stu-id="b7360-110">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> - <span data-ttu-id="b7360-111">在 Visual Studio for Mac 中，從功能表**選取**  >  [說明] [回報**問題**]，或從 [歡迎使用] 畫面中選取 [**回報問題**]，這會開啟用來提出錯誤報表的視窗。</span><span class="sxs-lookup"><span data-stu-id="b7360-111">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which opens a window for filing a bug report.</span></span> <span data-ttu-id="b7360-112">您可在[開發人員社群](https://developercommunity.visualstudio.com/spaces/41/index.html)入口網站追蹤您的意見反應。</span><span class="sxs-lookup"><span data-stu-id="b7360-112">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/41/index.html) portal.</span></span>
> - <span data-ttu-id="b7360-113">若要提出建議，請從功能表**選取 [** 說明]  >  [**提供建議**] 或從 [歡迎使用] 畫面中**提供建議**，這會帶您前往[Visual Studio for Mac 的開發人員社區網頁](https://developercommunity.visualstudio.com/content/idea/post.html?space=41)。</span><span class="sxs-lookup"><span data-stu-id="b7360-113">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which takes you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b7360-114">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="b7360-114">Prerequisites</span></span>

* <span data-ttu-id="b7360-115">[安裝 Visual Studio for Mac 8.6 版或更新](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)版本。</span><span class="sxs-lookup"><span data-stu-id="b7360-115">[Install Visual Studio for Mac version 8.6 or later](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="b7360-116">選取 [安裝 .NET Core] 選項。</span><span class="sxs-lookup"><span data-stu-id="b7360-116">Select the option to install .NET Core.</span></span> <span data-ttu-id="b7360-117">安裝 Xamarin 對於 .NET Core 開發而言是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="b7360-117">Installing Xamarin is optional for .NET Core development.</span></span> <span data-ttu-id="b7360-118">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="b7360-118">For more information, see the following resources:</span></span>

  * <span data-ttu-id="b7360-119">[教學課程：安裝 Visual Studio for Mac](/visualstudio/mac/installation)。</span><span class="sxs-lookup"><span data-stu-id="b7360-119">[Tutorial: Install Visual Studio for Mac](/visualstudio/mac/installation).</span></span>
  * <span data-ttu-id="b7360-120">[支援的 macOS 版本](../install/dependencies.md?pivots=os-macos)。</span><span class="sxs-lookup"><span data-stu-id="b7360-120">[Supported macOS versions](../install/dependencies.md?pivots=os-macos).</span></span>
  * <span data-ttu-id="b7360-121">[Visual Studio for Mac 支援的 .Net Core 版本](/visualstudio/mac/net-core-support)。</span><span class="sxs-lookup"><span data-stu-id="b7360-121">[.NET Core versions supported by Visual Studio for Mac](/visualstudio/mac/net-core-support).</span></span>

## <a name="create-a-solution-with-a-class-library-project"></a><span data-ttu-id="b7360-122">使用類別庫專案建立解決方案</span><span class="sxs-lookup"><span data-stu-id="b7360-122">Create a solution with a class library project</span></span>

<span data-ttu-id="b7360-123">Visual Studio 方案會當做一個或多個專案的容器。</span><span class="sxs-lookup"><span data-stu-id="b7360-123">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="b7360-124">在方案中建立方案和類別庫專案。</span><span class="sxs-lookup"><span data-stu-id="b7360-124">Create a solution and a class library project in the solution.</span></span> <span data-ttu-id="b7360-125">您稍後會將其他相關的專案新增至相同的方案。</span><span class="sxs-lookup"><span data-stu-id="b7360-125">You'll add additional, related projects to the same solution later.</span></span>

1. <span data-ttu-id="b7360-126">啟動 Visual Studio for Mac。</span><span class="sxs-lookup"><span data-stu-id="b7360-126">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="b7360-127">在 [開始] 視窗中，選取 [**新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="b7360-127">In the start window, select **New Project**.</span></span>

1. <span data-ttu-id="b7360-128">在 [**新增專案**] 對話方塊的 [**多平臺**] 節點下，選取 [連結**庫**]，然後選取 [ **.NET Standard 程式庫**] 範本，然後選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="b7360-128">In the **New Project** dialog under the **Multi-Platform** node, select **Library**, then select the **.NET Standard Library** template, and select **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="[新增專案] 對話方塊":::

1. <span data-ttu-id="b7360-130">在 [**設定新的 .NET Standard 程式庫**] 對話方塊中，選擇 [.NET Standard 2.1]，然後選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="b7360-130">In the **Configure your new .NET Standard Library** dialog, choose ".NET Standard 2.1", and select **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/choose-net-std-21.png" alt-text="選擇 .NET Standard 2。1":::

1. <span data-ttu-id="b7360-132">將專案命名為 "StringLibrary" 和方案 "ClassLibraryProjects"。</span><span class="sxs-lookup"><span data-stu-id="b7360-132">Name the project "StringLibrary" and the solution "ClassLibraryProjects".</span></span> <span data-ttu-id="b7360-133">在選取**的方案目錄中，保留 [建立專案目錄**]。</span><span class="sxs-lookup"><span data-stu-id="b7360-133">Leave **Create a project directory within the solution directory** selected.</span></span> <span data-ttu-id="b7360-134">選取 [建立]。</span><span class="sxs-lookup"><span data-stu-id="b7360-134">Select **Create**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project-options.png" alt-text="Visual Studio for Mac [新增專案] 對話方塊選項":::

1. <span data-ttu-id="b7360-136">從主功能表中，選取 [ **View**  >  **pad**  >  **Solution**]，然後選取 [dock] 圖示以讓 pad 保持開啟。</span><span class="sxs-lookup"><span data-stu-id="b7360-136">From the main menu, select **View** > **Pads** > **Solution**, and select the dock icon to keep the pad open.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/solution-dock-icon.png" alt-text="Solution pad 的停駐圖示":::

1. <span data-ttu-id="b7360-138">在 [ **Solution** pad] 中，展開 `StringLibrary` 節點以顯示範本所提供的類別檔案*Class1.cs*。</span><span class="sxs-lookup"><span data-stu-id="b7360-138">In the **Solution** pad, expand the `StringLibrary` node to reveal the class file provided by the template, *Class1.cs*.</span></span> <span data-ttu-id="b7360-139">在檔案上按一下<kbd>ctrl 鍵</kbd>，從內容功能表中選取 [**重新命名**]，然後將檔案重新命名為*StringLibrary.cs*。</span><span class="sxs-lookup"><span data-stu-id="b7360-139"><kbd>ctrl</kbd>-click the file, select **Rename** from the context menu, and rename the file to *StringLibrary.cs*.</span></span> <span data-ttu-id="b7360-140">開啟檔案，並以下列程式碼取代內容：</span><span class="sxs-lookup"><span data-stu-id="b7360-140">Open the file and replace the contents with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

1. <span data-ttu-id="b7360-141">按<kbd>則是⌘</kbd><kbd>S</kbd> （<kbd>命令</kbd> + <kbd>s</kbd>）以儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="b7360-141">Press <kbd>⌘</kbd><kbd>S</kbd> (<kbd>command</kbd>+<kbd>S</kbd>) to save the file.</span></span>

1. <span data-ttu-id="b7360-142">選取 IDE 視窗下邊界中的 [錯誤]\*\*\*\*，以開啟 [錯誤]\*\*\*\* 面板。</span><span class="sxs-lookup"><span data-stu-id="b7360-142">Select **Errors** in the margin at the bottom of the IDE window to open the **Errors** panel.</span></span> <span data-ttu-id="b7360-143">選取 [建置輸出]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b7360-143">Select the **Build Output** button.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-error-button.png" alt-text="Visual Studio Mac IDE 的下邊界，顯示 [錯誤] 按鈕":::

1. <span data-ttu-id="b7360-145">**Build**  >  從功能表中選取 [組建**組建全部**]。</span><span class="sxs-lookup"><span data-stu-id="b7360-145">Select **Build** > **Build All** from the menu.</span></span>

   <span data-ttu-id="b7360-146">解決方案隨即建置。</span><span class="sxs-lookup"><span data-stu-id="b7360-146">The solution builds.</span></span> <span data-ttu-id="b7360-147">建置輸出面板會顯示建置成功。</span><span class="sxs-lookup"><span data-stu-id="b7360-147">The build output panel shows that the build is successful.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-build-panel.png" alt-text="[錯誤] 面板的 Visual Studio Mac [建置輸出] 窗格，其中包含「建置成功」訊息":::

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="b7360-149">將主控台應用程式新增至解決方案</span><span class="sxs-lookup"><span data-stu-id="b7360-149">Add a console app to the solution</span></span>

<span data-ttu-id="b7360-150">新增使用類別庫的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="b7360-150">Add a console application that uses the class library.</span></span> <span data-ttu-id="b7360-151">應用程式會提示使用者輸入字串，並報告字串是否以大寫字元開頭。</span><span class="sxs-lookup"><span data-stu-id="b7360-151">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="b7360-152">在 [ **solution** pad] 中，按<kbd>ctrl</kbd>-按一下 `ClassLibraryProjects` 解決方案。</span><span class="sxs-lookup"><span data-stu-id="b7360-152">In the **Solution** pad, <kbd>ctrl</kbd>-click the `ClassLibraryProjects` solution.</span></span> <span data-ttu-id="b7360-153">從**Web 和主控台**應用程式範本選取範本，以加入新的**主控台應用程式**專案  >  **App** ，然後選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="b7360-153">Add a new **Console Application** project by selecting the template from the **Web and Console** > **App** templates, and select **Next**.</span></span>

1. <span data-ttu-id="b7360-154">選取 [ **.Net Core 3.1** ] 做為**目標架構**，然後選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="b7360-154">Select **.NET Core 3.1** as the **Target Framework** and select **Next**.</span></span>

1. <span data-ttu-id="b7360-155">為專案**展示**命名。</span><span class="sxs-lookup"><span data-stu-id="b7360-155">Name the project **ShowCase**.</span></span> <span data-ttu-id="b7360-156">選取 [建立]\*\*\*\* 以在解決方案中建立專案。</span><span class="sxs-lookup"><span data-stu-id="b7360-156">Select **Create** to create the project in the solution.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/add-showcase-project.png" alt-text="新增展示專案":::

1. <span data-ttu-id="b7360-158">開啟*Program.cs*檔案。</span><span class="sxs-lookup"><span data-stu-id="b7360-158">Open the *Program.cs* file.</span></span> <span data-ttu-id="b7360-159">將程式碼取代為下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="b7360-159">Replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="b7360-160">此程式會提示使用者輸入字串。</span><span class="sxs-lookup"><span data-stu-id="b7360-160">The program prompts the user to enter a string.</span></span> <span data-ttu-id="b7360-161">它會指出該字串開頭是否為大寫字元。</span><span class="sxs-lookup"><span data-stu-id="b7360-161">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="b7360-162">如果使用者在未輸入字串的情況下按<kbd>enter</kbd>鍵，應用程式就會結束，而且主控台視窗會關閉。</span><span class="sxs-lookup"><span data-stu-id="b7360-162">If the user presses the <kbd>enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

   <span data-ttu-id="b7360-163">該程式碼會使用 `row` 變數來維護寫入至主控台視窗的資料列數目計數。</span><span class="sxs-lookup"><span data-stu-id="b7360-163">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="b7360-164">當它大於或等於25時，程式碼就會清除主控台視窗，並向使用者顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="b7360-164">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="b7360-165">新增專案參考</span><span class="sxs-lookup"><span data-stu-id="b7360-165">Add a project reference</span></span>

<span data-ttu-id="b7360-166">一開始，新的主控台應用程式專案無法存取類別庫。</span><span class="sxs-lookup"><span data-stu-id="b7360-166">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="b7360-167">若要讓它能夠呼叫類別庫中的方法，請建立類別庫專案的專案參考。</span><span class="sxs-lookup"><span data-stu-id="b7360-167">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="b7360-168">在 [**解決方案**] 面板中，以<kbd>ctrl 鍵</kbd>按一下新**展示**專案的 [相依性 **]** 節點。</span><span class="sxs-lookup"><span data-stu-id="b7360-168">In the **Solutions** pad, <kbd>ctrl</kbd>-click the **Dependencies** node of the new **ShowCase** project.</span></span> <span data-ttu-id="b7360-169">在內容功能表中，選取 [**加入參考**]。</span><span class="sxs-lookup"><span data-stu-id="b7360-169">In the context menu, select **Add Reference**.</span></span>

1. <span data-ttu-id="b7360-170">在 [**參考**] 對話方塊中，選取 [ **StringLibrary** ]，然後選取 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="b7360-170">In the **References** dialog, select **StringLibrary** and select **OK**.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="b7360-171">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="b7360-171">Run the app</span></span>

1. <span data-ttu-id="b7360-172"><kbd>ctrl</kbd>-按一下展示專案，然後從內容功能表中選取 [**執行專案**]。</span><span class="sxs-lookup"><span data-stu-id="b7360-172"><kbd>ctrl</kbd>-click on the ShowCase project and select **Run project** from the context menu.</span></span>

1. <span data-ttu-id="b7360-173">輸入字串並按<kbd>enter</kbd>鍵以嘗試程式，然後按<kbd>enter</kbd>結束。</span><span class="sxs-lookup"><span data-stu-id="b7360-173">Try out the program by entering strings and pressing <kbd>enter</kbd>, then press <kbd>enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-console-window.png" alt-text="Visual Studio for Mac 主控台視窗，顯示您的應用程式正在執行":::

## <a name="additional-resources"></a><span data-ttu-id="b7360-175">其他資源</span><span class="sxs-lookup"><span data-stu-id="b7360-175">Additional resources</span></span>

* [<span data-ttu-id="b7360-176">使用 .NET Core CLI 開發程式庫</span><span class="sxs-lookup"><span data-stu-id="b7360-176">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="b7360-177">[.NET Standard 版本和支援的平臺](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="b7360-177">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>
* [<span data-ttu-id="b7360-178">Visual Studio 2019 for Mac 版本資訊</span><span class="sxs-lookup"><span data-stu-id="b7360-178">Visual Studio 2019 for Mac Release Notes</span></span>](/visualstudio/releasenotes/vs2019-mac-relnotes)

## <a name="next-steps"></a><span data-ttu-id="b7360-179">後續步驟</span><span class="sxs-lookup"><span data-stu-id="b7360-179">Next steps</span></span>

<span data-ttu-id="b7360-180">在本教學課程中，您已建立解決方案和程式庫專案，並加入了使用該程式庫的主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="b7360-180">In this tutorial, you created a solution and a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="b7360-181">在下一個教學課程中，您會將單元測試專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="b7360-181">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b7360-182">使用 Visual Studio for Mac 測試具有 .NET Core 的 .NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="b7360-182">Test a .NET Standard library with .NET Core using Visual Studio for Mac</span></span>](testing-library-with-visual-studio-mac.md)
