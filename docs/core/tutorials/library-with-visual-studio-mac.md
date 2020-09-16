---
title: 使用 Visual Studio for Mac 建立 .NET Standard 類別庫
description: 瞭解如何使用 Visual Studio for Mac 建立 .NET Standard 類別庫。
ms.date: 06/08/2020
ms.openlocfilehash: 433f6e0e2d784878c9a1616139b39ec56d695bcf
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537635"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-for-mac"></a><span data-ttu-id="eff53-103">教學課程：使用 Visual Studio for Mac 建立 .NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="eff53-103">Tutorial: Create a .NET Standard library using Visual Studio for Mac</span></span>

<span data-ttu-id="eff53-104">在本教學課程中，您會建立包含單一字串處理方法的類別庫。</span><span class="sxs-lookup"><span data-stu-id="eff53-104">In this tutorial, you create a class library that contains a single string-handling method.</span></span> <span data-ttu-id="eff53-105">您可以將它實作為 [擴充方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md) ，讓您可以如同類別的成員一樣呼叫它 <xref:System.String> 。</span><span class="sxs-lookup"><span data-stu-id="eff53-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="eff53-106">「類別庫」\*\* 會定義應用程式所呼叫的類型和方法。</span><span class="sxs-lookup"><span data-stu-id="eff53-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="eff53-107">以 .NET Standard 2.1 為目標的類別庫可供以支援 2.1 .NET Standard 版的任何 .NET 執行為目標的應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="eff53-107">A class library that targets .NET Standard 2.1 can be used by an application that targets any .NET implementation that supports version 2.1 of .NET Standard.</span></span> <span data-ttu-id="eff53-108">當您完成類別庫時，可以將它散發為協力廠商元件，或做為配套的元件，以及一或多個應用程式。</span><span class="sxs-lookup"><span data-stu-id="eff53-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="eff53-109">我們非常重視您的意見反應。</span><span class="sxs-lookup"><span data-stu-id="eff53-109">Your feedback is highly valued.</span></span> <span data-ttu-id="eff53-110">您有兩種方式可以提供意見反應給 Visual Studio for Mac 開發小組：</span><span class="sxs-lookup"><span data-stu-id="eff53-110">There are two ways you can provide feedback to the development team on Visual Studio for Mac:</span></span>
>
> - <span data-ttu-id="eff53-111">在 Visual Studio for Mac 中， **Help**  >  **Report a Problem**從功能表中選取 [說明]，或從歡迎畫面回報**問題**，這會開啟用來提出錯誤報表的視窗。</span><span class="sxs-lookup"><span data-stu-id="eff53-111">In Visual Studio for Mac, select **Help** > **Report a Problem** from the menu or **Report a Problem** from the Welcome screen, which opens a window for filing a bug report.</span></span> <span data-ttu-id="eff53-112">您可在[開發人員社群](https://developercommunity.visualstudio.com/spaces/41/index.html)入口網站追蹤您的意見反應。</span><span class="sxs-lookup"><span data-stu-id="eff53-112">You can track your feedback in the [Developer Community](https://developercommunity.visualstudio.com/spaces/41/index.html) portal.</span></span>
> - <span data-ttu-id="eff53-113">若要提出建議，請從功能表中**選取 [** 說明]  >  **提供建議**，或從歡迎畫面**提供**建議，這會帶您前往[Visual Studio for Mac 開發人員社群網頁](https://developercommunity.visualstudio.com/content/idea/post.html?space=41)。</span><span class="sxs-lookup"><span data-stu-id="eff53-113">To make a suggestion, select **Help** > **Provide a Suggestion** from the menu or **Provide a Suggestion** from the Welcome screen, which takes you to the [Visual Studio for Mac Developer Community webpage](https://developercommunity.visualstudio.com/content/idea/post.html?space=41).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eff53-114">必要條件</span><span class="sxs-lookup"><span data-stu-id="eff53-114">Prerequisites</span></span>

* <span data-ttu-id="eff53-115">[安裝 Visual Studio for Mac 8.6 版或更新版本](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)。</span><span class="sxs-lookup"><span data-stu-id="eff53-115">[Install Visual Studio for Mac version 8.6 or later](https://visualstudio.microsoft.com/vs/mac/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link).</span></span> <span data-ttu-id="eff53-116">選取安裝 .NET Core 的選項。</span><span class="sxs-lookup"><span data-stu-id="eff53-116">Select the option to install .NET Core.</span></span> <span data-ttu-id="eff53-117">安裝 Xamarin 是 .NET Core 開發的選擇性選項。</span><span class="sxs-lookup"><span data-stu-id="eff53-117">Installing Xamarin is optional for .NET Core development.</span></span> <span data-ttu-id="eff53-118">如需詳細資訊，請參閱下列資源：</span><span class="sxs-lookup"><span data-stu-id="eff53-118">For more information, see the following resources:</span></span>

  * <span data-ttu-id="eff53-119">[教學課程：安裝 Visual Studio for Mac](/visualstudio/mac/installation)。</span><span class="sxs-lookup"><span data-stu-id="eff53-119">[Tutorial: Install Visual Studio for Mac](/visualstudio/mac/installation).</span></span>
  * <span data-ttu-id="eff53-120">[支援的 macOS 版本](../install/macos.md)。</span><span class="sxs-lookup"><span data-stu-id="eff53-120">[Supported macOS versions](../install/macos.md).</span></span>
  * <span data-ttu-id="eff53-121">[Visual Studio for Mac 支援的 .Net Core 版本](/visualstudio/mac/net-core-support)。</span><span class="sxs-lookup"><span data-stu-id="eff53-121">[.NET Core versions supported by Visual Studio for Mac](/visualstudio/mac/net-core-support).</span></span>

## <a name="create-a-solution-with-a-class-library-project"></a><span data-ttu-id="eff53-122">使用類別庫專案建立方案</span><span class="sxs-lookup"><span data-stu-id="eff53-122">Create a solution with a class library project</span></span>

<span data-ttu-id="eff53-123">Visual Studio 方案可作為一或多個專案的容器。</span><span class="sxs-lookup"><span data-stu-id="eff53-123">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="eff53-124">在方案中建立方案和類別庫專案。</span><span class="sxs-lookup"><span data-stu-id="eff53-124">Create a solution and a class library project in the solution.</span></span> <span data-ttu-id="eff53-125">您稍後會將其他相關的專案加入至相同的方案。</span><span class="sxs-lookup"><span data-stu-id="eff53-125">You'll add additional, related projects to the same solution later.</span></span>

1. <span data-ttu-id="eff53-126">開始 Visual Studio for Mac。</span><span class="sxs-lookup"><span data-stu-id="eff53-126">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="eff53-127">在 [開始] 視窗中，選取 [ **新增專案**]。</span><span class="sxs-lookup"><span data-stu-id="eff53-127">In the start window, select **New Project**.</span></span>

1. <span data-ttu-id="eff53-128">在 [ **新增專案** ] 對話方塊的 [ **多平臺** ] 節點底下，選取 [連結 **庫**]，然後選取 [ **.NET Standard 程式庫** ] 範本，再選取 [ **下一步]**。</span><span class="sxs-lookup"><span data-stu-id="eff53-128">In the **New Project** dialog under the **Multi-Platform** node, select **Library**, then select the **.NET Standard Library** template, and select **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project.png" alt-text="[新增專案] 對話方塊":::

1. <span data-ttu-id="eff53-130">在 [ **設定新的 .NET Standard 程式庫** ] 對話方塊中，選擇 [.NET Standard 2.1]，然後選取 **[下一步**]。</span><span class="sxs-lookup"><span data-stu-id="eff53-130">In the **Configure your new .NET Standard Library** dialog, choose ".NET Standard 2.1", and select **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/choose-net-std-21.png" alt-text="選擇 .NET Standard 2。1":::

1. <span data-ttu-id="eff53-132">將專案命名為 "StringLibrary"，並將方案命名為 ">classlibraryprojects"。</span><span class="sxs-lookup"><span data-stu-id="eff53-132">Name the project "StringLibrary" and the solution "ClassLibraryProjects".</span></span> <span data-ttu-id="eff53-133">在選取 **的方案目錄內保持建立專案目錄** 。</span><span class="sxs-lookup"><span data-stu-id="eff53-133">Leave **Create a project directory within the solution directory** selected.</span></span> <span data-ttu-id="eff53-134">選取 [建立]。</span><span class="sxs-lookup"><span data-stu-id="eff53-134">Select **Create**.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-new-project-options.png" alt-text="Visual Studio for Mac [新增專案] 對話方塊選項":::

1. <span data-ttu-id="eff53-136">從主功能表中，選取 [ **View**  >  **pad**  >  **Solution**]，然後選取 [dock] 圖示，讓板保持開啟狀態。</span><span class="sxs-lookup"><span data-stu-id="eff53-136">From the main menu, select **View** > **Pads** > **Solution**, and select the dock icon to keep the pad open.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/solution-dock-icon.png" alt-text="Solution pad 的停駐圖示":::

1. <span data-ttu-id="eff53-138">在 **Solution** pad 中，展開 `StringLibrary` 節點以顯示範本 *Class1.cs*所提供的類別檔案。</span><span class="sxs-lookup"><span data-stu-id="eff53-138">In the **Solution** pad, expand the `StringLibrary` node to reveal the class file provided by the template, *Class1.cs*.</span></span> <span data-ttu-id="eff53-139"><kbd>ctrl</kbd>-按一下該檔案，從內容功能表中選取 [ **重新命名** ]，然後將檔案重新命名為 *StringLibrary.cs*。</span><span class="sxs-lookup"><span data-stu-id="eff53-139"><kbd>ctrl</kbd>-click the file, select **Rename** from the context menu, and rename the file to *StringLibrary.cs*.</span></span> <span data-ttu-id="eff53-140">開啟檔案，並以下列程式碼取代內容：</span><span class="sxs-lookup"><span data-stu-id="eff53-140">Open the file and replace the contents with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

1. <span data-ttu-id="eff53-141">按<kbd>⌘</kbd><kbd> (</kbd> <kbd>命令</kbd> + <kbd>S</kbd>) 來儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="eff53-141">Press <kbd>⌘</kbd><kbd>S</kbd> (<kbd>command</kbd>+<kbd>S</kbd>) to save the file.</span></span>

1. <span data-ttu-id="eff53-142">選取 IDE 視窗下邊界中的 [錯誤]\*\*\*\*，以開啟 [錯誤]\*\*\*\* 面板。</span><span class="sxs-lookup"><span data-stu-id="eff53-142">Select **Errors** in the margin at the bottom of the IDE window to open the **Errors** panel.</span></span> <span data-ttu-id="eff53-143">選取 [建置輸出]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="eff53-143">Select the **Build Output** button.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-error-button.png" alt-text="Visual Studio Mac IDE 的下邊界，顯示 [錯誤] 按鈕":::

1. <span data-ttu-id="eff53-145">**Build**  >  從功能表選取 [**全部組建組建**]。</span><span class="sxs-lookup"><span data-stu-id="eff53-145">Select **Build** > **Build All** from the menu.</span></span>

   <span data-ttu-id="eff53-146">解決方案隨即建置。</span><span class="sxs-lookup"><span data-stu-id="eff53-146">The solution builds.</span></span> <span data-ttu-id="eff53-147">建置輸出面板會顯示建置成功。</span><span class="sxs-lookup"><span data-stu-id="eff53-147">The build output panel shows that the build is successful.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-build-panel.png" alt-text="[錯誤] 面板的 Visual Studio Mac [建置輸出] 窗格，其中包含「建置成功」訊息":::

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="eff53-149">將主控台應用程式新增至解決方案</span><span class="sxs-lookup"><span data-stu-id="eff53-149">Add a console app to the solution</span></span>

<span data-ttu-id="eff53-150">加入使用類別庫的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="eff53-150">Add a console application that uses the class library.</span></span> <span data-ttu-id="eff53-151">應用程式會提示使用者輸入字串，並報告字串是否以大寫字元開頭。</span><span class="sxs-lookup"><span data-stu-id="eff53-151">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="eff53-152">在 **solution** pad 中， <kbd>ctrl +</kbd>按一下 `ClassLibraryProjects` 方案。</span><span class="sxs-lookup"><span data-stu-id="eff53-152">In the **Solution** pad, <kbd>ctrl</kbd>-click the `ClassLibraryProjects` solution.</span></span> <span data-ttu-id="eff53-153">從**Web 和主控台** **Console Application**  >  **應用程式**範本選取範本，然後選取 [**下一步]**，以新增主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="eff53-153">Add a new **Console Application** project by selecting the template from the **Web and Console** > **App** templates, and select **Next**.</span></span>

1. <span data-ttu-id="eff53-154">選取 [ **.Net Core 3.1** ] 作為 **目標架構** ，然後選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="eff53-154">Select **.NET Core 3.1** as the **Target Framework** and select **Next**.</span></span>

1. <span data-ttu-id="eff53-155">命名專案 **展示**。</span><span class="sxs-lookup"><span data-stu-id="eff53-155">Name the project **ShowCase**.</span></span> <span data-ttu-id="eff53-156">選取 [建立]\*\*\*\* 以在解決方案中建立專案。</span><span class="sxs-lookup"><span data-stu-id="eff53-156">Select **Create** to create the project in the solution.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/add-showcase-project.png" alt-text="新增展示專案":::

1. <span data-ttu-id="eff53-158">開啟 *Program.cs* 檔案。</span><span class="sxs-lookup"><span data-stu-id="eff53-158">Open the *Program.cs* file.</span></span> <span data-ttu-id="eff53-159">以下列程式碼取代程式碼：</span><span class="sxs-lookup"><span data-stu-id="eff53-159">Replace the code with the following code:</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="eff53-160">此程式會提示使用者輸入字串。</span><span class="sxs-lookup"><span data-stu-id="eff53-160">The program prompts the user to enter a string.</span></span> <span data-ttu-id="eff53-161">它會指出該字串開頭是否為大寫字元。</span><span class="sxs-lookup"><span data-stu-id="eff53-161">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="eff53-162">如果使用者按下 <kbd>enter</kbd> 鍵但未輸入字串，則應用程式會結束，且主控台視窗會關閉。</span><span class="sxs-lookup"><span data-stu-id="eff53-162">If the user presses the <kbd>enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

   <span data-ttu-id="eff53-163">該程式碼會使用 `row` 變數來維護寫入至主控台視窗的資料列數目計數。</span><span class="sxs-lookup"><span data-stu-id="eff53-163">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="eff53-164">只要超過或等於25，程式碼就會清除主控台視窗，並向使用者顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="eff53-164">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="eff53-165">新增專案參考</span><span class="sxs-lookup"><span data-stu-id="eff53-165">Add a project reference</span></span>

<span data-ttu-id="eff53-166">一開始，新的主控台應用程式專案沒有類別庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="eff53-166">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="eff53-167">若要允許它呼叫類別庫中的方法，請建立類別庫專案的專案參考。</span><span class="sxs-lookup"><span data-stu-id="eff53-167">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="eff53-168">在 [**方案**] 面板中， <kbd>ctrl +</kbd>按一下新**展示**專案的 [相依性 **]** 節點。</span><span class="sxs-lookup"><span data-stu-id="eff53-168">In the **Solutions** pad, <kbd>ctrl</kbd>-click the **Dependencies** node of the new **ShowCase** project.</span></span> <span data-ttu-id="eff53-169">在內容功能表中，選取 [ **加入參考**]。</span><span class="sxs-lookup"><span data-stu-id="eff53-169">In the context menu, select **Add Reference**.</span></span>

1. <span data-ttu-id="eff53-170">在 [ **參考** ] 對話方塊中，選取 [ **StringLibrary** ]，然後選取 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="eff53-170">In the **References** dialog, select **StringLibrary** and select **OK**.</span></span>

## <a name="run-the-app"></a><span data-ttu-id="eff53-171">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="eff53-171">Run the app</span></span>

1. <span data-ttu-id="eff53-172"><kbd>ctrl</kbd>-按一下展示專案，然後從內容功能表中選取 [ **執行專案** ]。</span><span class="sxs-lookup"><span data-stu-id="eff53-172"><kbd>ctrl</kbd>-click on the ShowCase project and select **Run project** from the context menu.</span></span>

1. <span data-ttu-id="eff53-173">輸入字串並按 <kbd>enter</kbd>鍵以嘗試程式，然後按 <kbd>enter</kbd> 鍵結束。</span><span class="sxs-lookup"><span data-stu-id="eff53-173">Try out the program by entering strings and pressing <kbd>enter</kbd>, then press <kbd>enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio-mac/visual-studio-mac-console-window.png" alt-text="Visual Studio for Mac 主控台視窗，顯示您的應用程式正在執行":::

## <a name="additional-resources"></a><span data-ttu-id="eff53-175">其他資源</span><span class="sxs-lookup"><span data-stu-id="eff53-175">Additional resources</span></span>

* [<span data-ttu-id="eff53-176">使用 .NET Core CLI 開發程式庫</span><span class="sxs-lookup"><span data-stu-id="eff53-176">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="eff53-177">[.NET Standard 支援的版本和平臺](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="eff53-177">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>
* [<span data-ttu-id="eff53-178">Visual Studio 2019 for Mac 版本資訊</span><span class="sxs-lookup"><span data-stu-id="eff53-178">Visual Studio 2019 for Mac Release Notes</span></span>](/visualstudio/releasenotes/vs2019-mac-relnotes)

## <a name="next-steps"></a><span data-ttu-id="eff53-179">後續步驟</span><span class="sxs-lookup"><span data-stu-id="eff53-179">Next steps</span></span>

<span data-ttu-id="eff53-180">在本教學課程中，您已建立方案和程式庫專案，並新增了使用該程式庫的主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="eff53-180">In this tutorial, you created a solution and a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="eff53-181">在下一個教學課程中，您會將單元測試專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="eff53-181">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="eff53-182">使用 Visual Studio for Mac 測試具有 .NET Core 的 .NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="eff53-182">Test a .NET Standard library with .NET Core using Visual Studio for Mac</span></span>](testing-library-with-visual-studio-mac.md)
