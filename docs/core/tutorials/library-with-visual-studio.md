---
title: 使用 Visual Studio 建立 .NET Standard 類別庫
description: 瞭解如何使用 Visual Studio 建立 .NET Standard 類別庫。
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: ef9c62b0378e1064d8cfd90a8c59aed74ea312b2
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2020
ms.locfileid: "84701561"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio"></a><span data-ttu-id="c8b79-103">教學課程：使用 Visual Studio 建立 .NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="c8b79-103">Tutorial: Create a .NET Standard library using Visual Studio</span></span>

<span data-ttu-id="c8b79-104">在本教學課程中，您會建立包含單一字串處理方法的簡單公用程式程式庫。</span><span class="sxs-lookup"><span data-stu-id="c8b79-104">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="c8b79-105">您可以將它實作為[擴充方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)，讓您可以如同類別的成員一樣呼叫它 <xref:System.String> 。</span><span class="sxs-lookup"><span data-stu-id="c8b79-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="c8b79-106">「類別庫」\*\* 會定義應用程式所呼叫的類型和方法。</span><span class="sxs-lookup"><span data-stu-id="c8b79-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="c8b79-107">以 .NET Standard 2.0 為目標的類別庫，可讓任何支援該版本 .NET Standard 的 .NET 部署呼叫您的程式庫。</span><span class="sxs-lookup"><span data-stu-id="c8b79-107">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="c8b79-108">當您完成類別庫時，您可以將它散發為協力廠商元件，或作為一或多個應用程式的配套元件。</span><span class="sxs-lookup"><span data-stu-id="c8b79-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c8b79-109">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="c8b79-109">Prerequisites</span></span>

- <span data-ttu-id="c8b79-110">已安裝 **.Net Core 跨平臺開發**工作負載的[Visual Studio 2019 16.6 版或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="c8b79-110">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="c8b79-111">當您選取此工作負載時，會自動安裝 .NET Core 3.1 SDK。</span><span class="sxs-lookup"><span data-stu-id="c8b79-111">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

  <span data-ttu-id="c8b79-112">如需詳細資訊，請參閱[安裝 .NET Core SDK](../install/sdk.md?pivots=os-windows)一文中的[install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio)一節。</span><span class="sxs-lookup"><span data-stu-id="c8b79-112">For more information, see the [Install with Visual Studio](../install/sdk.md?pivots=os-windows#install-with-visual-studio) section on the [Install the .NET Core SDK](../install/sdk.md?pivots=os-windows) article.</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="c8b79-113">建立方案</span><span class="sxs-lookup"><span data-stu-id="c8b79-113">Create a solution</span></span>

<span data-ttu-id="c8b79-114">一開始先建立一個空白的方案，將類別庫專案放入中。</span><span class="sxs-lookup"><span data-stu-id="c8b79-114">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="c8b79-115">Visual Studio 方案會當做一個或多個專案的容器。</span><span class="sxs-lookup"><span data-stu-id="c8b79-115">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="c8b79-116">您會在相同的方案中加入其他相關的專案。</span><span class="sxs-lookup"><span data-stu-id="c8b79-116">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="c8b79-117">若要建立空白解決方案：</span><span class="sxs-lookup"><span data-stu-id="c8b79-117">To create the blank solution:</span></span>

1. <span data-ttu-id="c8b79-118">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="c8b79-118">Start Visual Studio.</span></span>

2. <span data-ttu-id="c8b79-119">在 [開始] 視窗中，選擇 [**建立新專案**]。</span><span class="sxs-lookup"><span data-stu-id="c8b79-119">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="c8b79-120">在 [**建立新專案**] 頁面的 [搜尋] 方塊中，輸入 [**方案**]。</span><span class="sxs-lookup"><span data-stu-id="c8b79-120">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="c8b79-121">選擇 [**空白解決方案**] 範本，然後選擇 [**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="c8b79-121">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Visual Studio 中的空白方案範本](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="c8b79-123">在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**ClassLibraryProjects** 。</span><span class="sxs-lookup"><span data-stu-id="c8b79-123">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="c8b79-124">接著，選擇 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="c8b79-124">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="c8b79-125">建立類別庫專案</span><span class="sxs-lookup"><span data-stu-id="c8b79-125">Create a class library project</span></span>

1. <span data-ttu-id="c8b79-126">將名為 "StringLibrary" 的新 .NET Standard 類別庫專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="c8b79-126">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="c8b79-127">以滑鼠右鍵按一下**方案總管**中的方案，然後選取 [**加入**  >  **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="c8b79-127">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="c8b79-128">在 [**加入新專案**] 頁面的 [搜尋] 方塊中，輸入 [連結**庫**]。</span><span class="sxs-lookup"><span data-stu-id="c8b79-128">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="c8b79-129">選擇 [語言] 清單中的 [ **c #** ] 或 [ **Visual Basic** ，然後從 [平臺] 清單中選擇 [**所有平臺**]。</span><span class="sxs-lookup"><span data-stu-id="c8b79-129">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="c8b79-130">選擇 [**類別庫（.NET Standard）** ] 範本，然後選擇 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="c8b79-130">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="c8b79-131">在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**StringLibrary** 。</span><span class="sxs-lookup"><span data-stu-id="c8b79-131">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="c8b79-132">然後選擇 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="c8b79-132">Then, choose **Create**.</span></span>

1. <span data-ttu-id="c8b79-133">請檢查並確定程式庫的目標是正確的 .NET Standard 版本。</span><span class="sxs-lookup"><span data-stu-id="c8b79-133">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="c8b79-134">以滑鼠右鍵按一下**方案總管**中的 [程式庫] 專案，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="c8b79-134">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="c8b79-135">[**目標 Framework** ] 文字方塊會顯示專案的目標為 .NET Standard 2.0。</span><span class="sxs-lookup"><span data-stu-id="c8b79-135">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![類別庫的專案屬性](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="c8b79-137">如果您使用的是 Visual Basic，請清除 [**根命名空間**] 文字方塊中的文字。</span><span class="sxs-lookup"><span data-stu-id="c8b79-137">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   ![類別庫的專案屬性](./media/library-with-visual-studio/vb/library-project-properties.png)

   <span data-ttu-id="c8b79-139">針對每個專案，Visual Basic 會自動建立對應至專案名稱的命名空間。</span><span class="sxs-lookup"><span data-stu-id="c8b79-139">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="c8b79-140">在本教學課程中，您會使用程式碼檔案中的關鍵字來定義最上層命名空間 [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) 。</span><span class="sxs-lookup"><span data-stu-id="c8b79-140">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="c8b79-141">使用下列程式碼取代*Class1.cs*或*Class1*的程式碼視窗中的程式碼，並儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="c8b79-141">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="c8b79-142">如果未顯示您想要使用的語言，請變更頁面頂端的 [語言選取器]。</span><span class="sxs-lookup"><span data-stu-id="c8b79-142">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   <span data-ttu-id="c8b79-143">類別庫 `UtilityLibraries.StringLibrary` 包含名為的方法 `StartsWithUpper` 。</span><span class="sxs-lookup"><span data-stu-id="c8b79-143">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="c8b79-144">這個方法會傳回 <xref:System.Boolean> 值，指出目前的字串實例是否以大寫字元開頭。</span><span class="sxs-lookup"><span data-stu-id="c8b79-144">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="c8b79-145">Unicode 標準會區別大寫和小寫字元。</span><span class="sxs-lookup"><span data-stu-id="c8b79-145">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="c8b79-146">如果是大寫字元，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="c8b79-146">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="c8b79-147">在功能表列上，選取 [**組建**] [組建  >  **方案**] 以確認專案編譯無誤。</span><span class="sxs-lookup"><span data-stu-id="c8b79-147">On the menu bar, select **Build** > **Build Solution** to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="c8b79-148">將主控台應用程式新增至解決方案</span><span class="sxs-lookup"><span data-stu-id="c8b79-148">Add a console app to the solution</span></span>

<span data-ttu-id="c8b79-149">新增使用類別庫的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="c8b79-149">Add a console application that uses the class library.</span></span> <span data-ttu-id="c8b79-150">應用程式會提示使用者輸入字串，並報告字串是否以大寫字元開頭。</span><span class="sxs-lookup"><span data-stu-id="c8b79-150">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="c8b79-151">將名為 "展示" 的新 .NET Core 主控台應用程式加入至方案。</span><span class="sxs-lookup"><span data-stu-id="c8b79-151">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="c8b79-152">以滑鼠右鍵按一下**方案總管**中的方案，然後選取 [**加入**  >  **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="c8b79-152">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="c8b79-153">在 [**加入新專案**] 頁面的 [搜尋] 方塊中，輸入**主控台**。</span><span class="sxs-lookup"><span data-stu-id="c8b79-153">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="c8b79-154">選擇 [語言] 清單中的 [ **c #** ] 或 [ **Visual Basic** ，然後從 [平臺] 清單中選擇 [**所有平臺**]。</span><span class="sxs-lookup"><span data-stu-id="c8b79-154">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="c8b79-155">選擇 [**主控台應用程式（.Net Core）** ] 範本，然後選擇 [**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="c8b79-155">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="c8b79-156">在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**展示**。</span><span class="sxs-lookup"><span data-stu-id="c8b79-156">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="c8b79-157">接著，選擇 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="c8b79-157">Then choose **Create**.</span></span>

1. <span data-ttu-id="c8b79-158">在*Program.cs*或*Program .Vb*檔案的程式碼視窗中，將所有程式碼取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="c8b79-158">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   <span data-ttu-id="c8b79-159">該程式碼會使用 `row` 變數來維護寫入至主控台視窗的資料列數目計數。</span><span class="sxs-lookup"><span data-stu-id="c8b79-159">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="c8b79-160">當它大於或等於25時，程式碼就會清除主控台視窗，並向使用者顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="c8b79-160">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="c8b79-161">此程式會提示使用者輸入字串。</span><span class="sxs-lookup"><span data-stu-id="c8b79-161">The program prompts the user to enter a string.</span></span> <span data-ttu-id="c8b79-162">它會指出該字串開頭是否為大寫字元。</span><span class="sxs-lookup"><span data-stu-id="c8b79-162">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="c8b79-163">如果使用者在未輸入字串的情況下按<kbd>Enter</kbd>鍵，應用程式就會結束，而且主控台視窗會關閉。</span><span class="sxs-lookup"><span data-stu-id="c8b79-163">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="c8b79-164">新增專案參考</span><span class="sxs-lookup"><span data-stu-id="c8b79-164">Add a project reference</span></span>

<span data-ttu-id="c8b79-165">一開始，新的主控台應用程式專案無法存取類別庫。</span><span class="sxs-lookup"><span data-stu-id="c8b79-165">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="c8b79-166">若要讓它能夠呼叫類別庫中的方法，請建立類別庫專案的專案參考。</span><span class="sxs-lookup"><span data-stu-id="c8b79-166">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="c8b79-167">在**方案總管**中，以滑鼠右鍵按一下專案的 [相依性 `ShowCase` ] 節點，然後選取 [**加入專案參考** **]** 。</span><span class="sxs-lookup"><span data-stu-id="c8b79-167">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   ![Visual Studio 中的 [新增參考] 內容功能表](media/library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="c8b79-169">在 [**參考管理員**] 對話方塊中，選取 [ **StringLibrary** ] 專案，然後選取 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="c8b79-169">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   ![已選取 StringLibrary 的參考管理員對話方塊](media/library-with-visual-studio/manage-project-references.png)

## <a name="run-the-app"></a><span data-ttu-id="c8b79-171">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="c8b79-171">Run the app</span></span>

1. <span data-ttu-id="c8b79-172">在方案總管\*\*\*\* 中，以滑鼠右鍵按一下 **ShowCase** 專案，然後在內容功能表中選取 [設定為啟始專案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c8b79-172">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Visual Studio 專案操作功能表來設定啟始專案](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="c8b79-174">按<kbd>Shift</kbd> + <kbd>F5</kbd>以編譯並執行程式，而不進行偵測。</span><span class="sxs-lookup"><span data-stu-id="c8b79-174">Press <kbd>Shift</kbd>+<kbd>F5</kbd> to compile and run the program without debugging.</span></span>

   ![顯示調試按鈕的 Visual Studio 專案工具列](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. <span data-ttu-id="c8b79-176">輸入字串並按<kbd>enter</kbd>鍵以嘗試程式，然後按<kbd>enter</kbd>結束。</span><span class="sxs-lookup"><span data-stu-id="c8b79-176">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="展示執行中的主控台視窗":::

## <a name="additional-resources"></a><span data-ttu-id="c8b79-178">其他資源</span><span class="sxs-lookup"><span data-stu-id="c8b79-178">Additional resources</span></span>

* [<span data-ttu-id="c8b79-179">使用 .NET Core CLI 開發程式庫</span><span class="sxs-lookup"><span data-stu-id="c8b79-179">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="c8b79-180">[.NET Standard 版本和支援的平臺](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="c8b79-180">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="c8b79-181">後續步驟</span><span class="sxs-lookup"><span data-stu-id="c8b79-181">Next steps</span></span>

<span data-ttu-id="c8b79-182">在本教學課程中，您已建立解決方案、新增程式庫專案，以及加入使用該程式庫的主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="c8b79-182">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="c8b79-183">在下一個教學課程中，您會將單元測試專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="c8b79-183">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c8b79-184">使用 Visual Studio 測試具有 .NET Core 的 .NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="c8b79-184">Test a .NET Standard library with .NET Core using Visual Studio</span></span>](testing-library-with-visual-studio.md)
