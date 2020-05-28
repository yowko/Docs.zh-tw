---
title: 在 Visual Studio 中建立 .NET Standard 類別庫
description: 瞭解如何使用 Visual Studio 建立 .NET Standard 類別庫。
ms.date: 05/21/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 2afe11ad75fc36a67efed48d56dbafb11bceaf2a
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005227"
---
# <a name="tutorial-create-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="f6b43-103">教學課程：在 Visual Studio 中建立 .NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="f6b43-103">Tutorial: Create a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="f6b43-104">「類別庫」\*\* 會定義應用程式所呼叫的類型和方法。</span><span class="sxs-lookup"><span data-stu-id="f6b43-104">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="f6b43-105">以 .NET Standard 2.0 為目標的類別庫，可讓任何支援該版本 .NET Standard 的 .NET 部署呼叫您的程式庫。</span><span class="sxs-lookup"><span data-stu-id="f6b43-105">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="f6b43-106">當您完成類別庫時，您可以決定要將它散發為協力廠商元件，還是要將它併入作為一或多個應用程式隨附的元件。</span><span class="sxs-lookup"><span data-stu-id="f6b43-106">When you finish your class library, you can decide whether you want to distribute it as a third-party component or whether you want to include it as a bundled component with one or more applications.</span></span>

> [!NOTE]
> <span data-ttu-id="f6b43-107">如需所支援的 .NET Standard 版本和平臺清單，請參閱[.NET Standard](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="f6b43-107">For a list of .NET Standard versions and the platforms they support, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="f6b43-108">在本教學課程中，您會建立包含單一字串處理方法的簡單公用程式程式庫。</span><span class="sxs-lookup"><span data-stu-id="f6b43-108">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="f6b43-109">您可以將它實作為[擴充方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)，讓您可以如同類別的成員一樣呼叫它 <xref:System.String> 。</span><span class="sxs-lookup"><span data-stu-id="f6b43-109">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f6b43-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="f6b43-110">Prerequisites</span></span>

- <span data-ttu-id="f6b43-111">已安裝 **.Net Core 跨平臺開發**工作負載的[Visual Studio 2019 16.6 版或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="f6b43-111">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="f6b43-112">當您選取此工作負載時，會自動安裝 .NET Core 3.1 SDK。</span><span class="sxs-lookup"><span data-stu-id="f6b43-112">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="f6b43-113">如需詳細資訊，請參閱[安裝 .NET Core SDK](../install/sdk.md?pivots=os-windows)一文中的[install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio)一節。</span><span class="sxs-lookup"><span data-stu-id="f6b43-113">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-a-visual-studio-solution"></a><span data-ttu-id="f6b43-114">建立 Visual Studio 解決方案</span><span class="sxs-lookup"><span data-stu-id="f6b43-114">Create a Visual Studio solution</span></span>

<span data-ttu-id="f6b43-115">一開始先建立一個空白的方案，將類別庫專案放入中。</span><span class="sxs-lookup"><span data-stu-id="f6b43-115">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="f6b43-116">Visual Studio 方案會當做一個或多個專案的容器。</span><span class="sxs-lookup"><span data-stu-id="f6b43-116">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="f6b43-117">您會在相同的方案中加入其他相關的專案。</span><span class="sxs-lookup"><span data-stu-id="f6b43-117">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="f6b43-118">若要建立空白解決方案：</span><span class="sxs-lookup"><span data-stu-id="f6b43-118">To create the blank solution:</span></span>

1. <span data-ttu-id="f6b43-119">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="f6b43-119">Open Visual Studio.</span></span>

2. <span data-ttu-id="f6b43-120">在 [開始] 視窗中，選擇 [**建立新專案**]。</span><span class="sxs-lookup"><span data-stu-id="f6b43-120">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="f6b43-121">在 [**建立新專案**] 頁面的 [搜尋] 方塊中，輸入 [**方案**]。</span><span class="sxs-lookup"><span data-stu-id="f6b43-121">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="f6b43-122">選擇 [**空白解決方案**] 範本，然後選擇 [**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="f6b43-122">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Visual Studio 中的空白方案範本](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="f6b43-124">在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**ClassLibraryProjects** 。</span><span class="sxs-lookup"><span data-stu-id="f6b43-124">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="f6b43-125">接著，選擇 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="f6b43-125">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="f6b43-126">建立類別庫專案</span><span class="sxs-lookup"><span data-stu-id="f6b43-126">Create a class library project</span></span>

1. <span data-ttu-id="f6b43-127">將名為 "StringLibrary" 的新 .NET Standard 類別庫專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="f6b43-127">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="f6b43-128">以滑鼠右鍵按一下**方案總管**中的方案，然後選取 [**加入**  >  **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="f6b43-128">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="f6b43-129">在 [**加入新專案**] 頁面的 [搜尋] 方塊中，輸入 [連結**庫**]。</span><span class="sxs-lookup"><span data-stu-id="f6b43-129">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="f6b43-130">選擇 [語言] 清單中的 [ **c #** ] 或 [ **Visual Basic** ，然後從 [平臺] 清單中選擇 [**所有平臺**]。</span><span class="sxs-lookup"><span data-stu-id="f6b43-130">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="f6b43-131">選擇 [**類別庫（.NET Standard）** ] 範本，然後選擇 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="f6b43-131">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="f6b43-132">在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**StringLibrary** 。</span><span class="sxs-lookup"><span data-stu-id="f6b43-132">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="f6b43-133">然後選擇 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="f6b43-133">Then, choose **Create**.</span></span>

1. <span data-ttu-id="f6b43-134">請檢查並確定程式庫的目標是正確的 .NET Standard 版本。</span><span class="sxs-lookup"><span data-stu-id="f6b43-134">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="f6b43-135">以滑鼠右鍵按一下**方案總管**中的 [程式庫] 專案，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="f6b43-135">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="f6b43-136">[**目標 Framework** ] 文字方塊會顯示專案的目標為 .NET Standard 2.0。</span><span class="sxs-lookup"><span data-stu-id="f6b43-136">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![類別庫的專案屬性](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="f6b43-138">如果您使用的是 Visual Basic，請清除 [**根命名空間**] 文字方塊中的文字。</span><span class="sxs-lookup"><span data-stu-id="f6b43-138">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   ![類別庫的專案屬性](./media/library-with-visual-studio/vb/library-project-properties.png)

   <span data-ttu-id="f6b43-140">針對每個專案，Visual Basic 會自動建立對應至專案名稱的命名空間。</span><span class="sxs-lookup"><span data-stu-id="f6b43-140">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="f6b43-141">在本教學課程中，您會使用程式碼檔案中的關鍵字來定義最上層命名空間 [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) 。</span><span class="sxs-lookup"><span data-stu-id="f6b43-141">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="f6b43-142">使用下列程式碼取代*Class1.cs*或*Class1*的程式碼視窗中的程式碼，並儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="f6b43-142">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="f6b43-143">如果未顯示您想要使用的語言，請變更頁面頂端的 [語言選取器]。</span><span class="sxs-lookup"><span data-stu-id="f6b43-143">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   [!code-csharp[](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/classlib.cs)]
   [!code-vb[](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/stringlibrary.vb)]

   <span data-ttu-id="f6b43-144">類別庫 `UtilityLibraries.StringLibrary` 包含名為的方法 `StartsWithUpper` 。</span><span class="sxs-lookup"><span data-stu-id="f6b43-144">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="f6b43-145">這個方法會傳回 <xref:System.Boolean> 值，指出目前的字串實例是否以大寫字元開頭。</span><span class="sxs-lookup"><span data-stu-id="f6b43-145">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="f6b43-146">Unicode 標準會區別大寫和小寫字元。</span><span class="sxs-lookup"><span data-stu-id="f6b43-146">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="f6b43-147">如果是大寫字元，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="f6b43-147">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="f6b43-148">在功能表列上，選取 [**組建**] [組建  >  **方案**] 以確認專案編譯無誤。</span><span class="sxs-lookup"><span data-stu-id="f6b43-148">On the menu bar, select **Build** > **Build Solution** to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="f6b43-149">將主控台應用程式新增至解決方案</span><span class="sxs-lookup"><span data-stu-id="f6b43-149">Add a console app to the solution</span></span>

<span data-ttu-id="f6b43-150">在主控台應用程式中使用類別庫，以提示使用者輸入字串，並報告字串是否以大寫字元開頭。</span><span class="sxs-lookup"><span data-stu-id="f6b43-150">Use the class library in a console application that prompts the user to enter a string and reports whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="f6b43-151">將名為 "展示" 的新 .NET Core 主控台應用程式加入至方案。</span><span class="sxs-lookup"><span data-stu-id="f6b43-151">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="f6b43-152">以滑鼠右鍵按一下**方案總管**中的方案，然後選取 [**加入**  >  **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="f6b43-152">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="f6b43-153">在 [**加入新專案**] 頁面的 [搜尋] 方塊中，輸入**主控台**。</span><span class="sxs-lookup"><span data-stu-id="f6b43-153">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="f6b43-154">選擇 [語言] 清單中的 [ **c #** ] 或 [ **Visual Basic** ，然後從 [平臺] 清單中選擇 [**所有平臺**]。</span><span class="sxs-lookup"><span data-stu-id="f6b43-154">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="f6b43-155">選擇 [**主控台應用程式（.Net Core）** ] 範本，然後選擇 [**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="f6b43-155">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="f6b43-156">在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**展示**。</span><span class="sxs-lookup"><span data-stu-id="f6b43-156">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="f6b43-157">接著，選擇 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="f6b43-157">Then choose **Create**.</span></span>

1. <span data-ttu-id="f6b43-158">在方案總管\*\*\*\* 中，以滑鼠右鍵按一下 **ShowCase** 專案，然後在內容功能表中選取 [設定為啟始專案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f6b43-158">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Visual Studio 專案操作功能表來設定啟始專案](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="f6b43-160">一開始，新的主控台應用程式專案無法存取類別庫。</span><span class="sxs-lookup"><span data-stu-id="f6b43-160">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="f6b43-161">若要讓它能夠呼叫類別庫中的方法，請建立類別庫專案的專案參考。</span><span class="sxs-lookup"><span data-stu-id="f6b43-161">To allow it to call methods in the class library, create a project reference to the class library project.</span></span> <span data-ttu-id="f6b43-162">在**方案總管**中，以滑鼠右鍵按一下專案的 [相依性 `ShowCase` ] 節點，然後選取 [**加入專案參考** **]** 。</span><span class="sxs-lookup"><span data-stu-id="f6b43-162">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   ![Visual Studio 中的 [新增參考] 內容功能表](media/library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="f6b43-164">在 [**參考管理員**] 對話方塊中，選取 [ **StringLibrary** ] 專案，然後選取 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="f6b43-164">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   ![已選取 StringLibrary 的參考管理員對話方塊](media/library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="f6b43-166">在*Program.cs*或*Program .Vb*檔案的程式碼視窗中，將所有程式碼取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="f6b43-166">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="f6b43-167">該程式碼會使用 `row` 變數來維護寫入至主控台視窗的資料列數目計數。</span><span class="sxs-lookup"><span data-stu-id="f6b43-167">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="f6b43-168">當它大於或等於25時，程式碼就會清除主控台視窗，並向使用者顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="f6b43-168">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="f6b43-169">此程式會提示使用者輸入字串。</span><span class="sxs-lookup"><span data-stu-id="f6b43-169">The program prompts the user to enter a string.</span></span> <span data-ttu-id="f6b43-170">它會指出該字串開頭是否為大寫字元。</span><span class="sxs-lookup"><span data-stu-id="f6b43-170">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="f6b43-171">如果使用者在未輸入字串的情況下按 Enter 鍵，應用程式就會結束，而且主控台視窗會關閉。</span><span class="sxs-lookup"><span data-stu-id="f6b43-171">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="f6b43-172">必要時，變更工具列以編譯 `ShowCase` 專案的 [偵錯]\*\*\*\* 版本。</span><span class="sxs-lookup"><span data-stu-id="f6b43-172">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="f6b43-173">選取 **ShowCase** 按鈕上的綠色箭號，以編譯並執行程式。</span><span class="sxs-lookup"><span data-stu-id="f6b43-173">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![顯示調試按鈕的 Visual Studio 專案工具列](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. <span data-ttu-id="f6b43-175">輸入字串並按**enter**鍵以嘗試程式，然後按**enter**結束。</span><span class="sxs-lookup"><span data-stu-id="f6b43-175">Try out the program by entering strings and pressing **Enter**, then press **Enter** to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="展示執行中的主控台視窗":::

## <a name="next-steps"></a><span data-ttu-id="f6b43-177">後續步驟</span><span class="sxs-lookup"><span data-stu-id="f6b43-177">Next steps</span></span>

<span data-ttu-id="f6b43-178">在本教學課程中，您已建立解決方案、新增程式庫專案，以及加入使用該程式庫的主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="f6b43-178">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="f6b43-179">在下一個教學課程中，您會將單元測試專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="f6b43-179">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f6b43-180">在 Visual Studio 中使用 .NET Core 測試 .NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="f6b43-180">Test a .NET Standard library with .NET Core in Visual Studio</span></span>](testing-library-with-visual-studio.md)
