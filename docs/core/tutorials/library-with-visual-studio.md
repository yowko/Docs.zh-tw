---
title: 使用 Visual Studio 建立 .NET Standard 類別庫
description: 瞭解如何使用 Visual Studio 建立 .NET Standard 類別庫。
ms.date: 08/07/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 07cc1bd7b9892f7cbee7a82998093718cd311b92
ms.sourcegitcommit: 7476c20d2f911a834a00b8a7f5e8926bae6804d9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/11/2020
ms.locfileid: "88062661"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio"></a><span data-ttu-id="23be6-103">教學課程：使用 Visual Studio 建立 .NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="23be6-103">Tutorial: Create a .NET Standard library using Visual Studio</span></span>

<span data-ttu-id="23be6-104">在本教學課程中，您會建立包含單一字串處理方法的簡單類別庫。</span><span class="sxs-lookup"><span data-stu-id="23be6-104">In this tutorial, you create a simple class library that contains a single string-handling method.</span></span>

<span data-ttu-id="23be6-105">「類別庫」\*\* 會定義應用程式所呼叫的類型和方法。</span><span class="sxs-lookup"><span data-stu-id="23be6-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="23be6-106">以 .NET Standard 2.0 為目標的類別庫，可讓任何支援該版本 .NET Standard 的 .NET 部署呼叫您的程式庫。</span><span class="sxs-lookup"><span data-stu-id="23be6-106">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span>

<span data-ttu-id="23be6-107">當您完成類別庫時，您可以將它散發為 NuGet 套件，或做為使用它的應用程式所配套的元件。</span><span class="sxs-lookup"><span data-stu-id="23be6-107">When you finish your class library, you can distribute it as a NuGet package or as a component bundled with the application that uses it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="23be6-108">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="23be6-108">Prerequisites</span></span>

- <span data-ttu-id="23be6-109">已安裝 **.Net Core 跨平臺開發**工作負載的[Visual Studio 2019 16.6 版或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="23be6-109">[Visual Studio 2019 version 16.6 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="23be6-110">當您選取此工作負載時，會自動安裝 .NET Core 3.1 SDK。</span><span class="sxs-lookup"><span data-stu-id="23be6-110">.NET Core 3.1 SDK is automatically installed when you select this workload.</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="23be6-111">建立方案</span><span class="sxs-lookup"><span data-stu-id="23be6-111">Create a solution</span></span>

<span data-ttu-id="23be6-112">一開始先建立一個空白的方案，將類別庫專案放入中。</span><span class="sxs-lookup"><span data-stu-id="23be6-112">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="23be6-113">Visual Studio 方案會當做一個或多個專案的容器。</span><span class="sxs-lookup"><span data-stu-id="23be6-113">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="23be6-114">您會在相同的方案中加入其他相關的專案。</span><span class="sxs-lookup"><span data-stu-id="23be6-114">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="23be6-115">若要建立空白解決方案：</span><span class="sxs-lookup"><span data-stu-id="23be6-115">To create the blank solution:</span></span>

1. <span data-ttu-id="23be6-116">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="23be6-116">Start Visual Studio.</span></span>

2. <span data-ttu-id="23be6-117">在 [開始] 視窗中，選擇 [**建立新專案**]。</span><span class="sxs-lookup"><span data-stu-id="23be6-117">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="23be6-118">在 [**建立新專案**] 頁面的 [搜尋] 方塊中，輸入 [**方案**]。</span><span class="sxs-lookup"><span data-stu-id="23be6-118">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="23be6-119">選擇 [**空白解決方案**] 範本，然後選擇 [**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="23be6-119">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   ![Visual Studio 中的空白方案範本](media/library-with-visual-studio/blank-solution.png)

4. <span data-ttu-id="23be6-121">在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**ClassLibraryProjects** 。</span><span class="sxs-lookup"><span data-stu-id="23be6-121">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="23be6-122">接著，選擇 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="23be6-122">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="23be6-123">建立類別庫專案</span><span class="sxs-lookup"><span data-stu-id="23be6-123">Create a class library project</span></span>

1. <span data-ttu-id="23be6-124">將名為 "StringLibrary" 的新 .NET Standard 類別庫專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="23be6-124">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="23be6-125">以滑鼠右鍵按一下**方案總管**中的方案，然後選取 [**加入**  >  **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="23be6-125">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="23be6-126">在 [**加入新專案**] 頁面的 [搜尋] 方塊中，輸入 [連結**庫**]。</span><span class="sxs-lookup"><span data-stu-id="23be6-126">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="23be6-127">選擇 [語言] 清單中的 [ **c #** ] 或 [ **Visual Basic** ，然後從 [平臺] 清單中選擇 [**所有平臺**]。</span><span class="sxs-lookup"><span data-stu-id="23be6-127">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="23be6-128">選擇 [\*\*類別庫] ( .NET Standard) \*\* ] 範本，然後選擇 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="23be6-128">Choose the **Class Library (.NET Standard)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="23be6-129">在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**StringLibrary** 。</span><span class="sxs-lookup"><span data-stu-id="23be6-129">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box.</span></span> <span data-ttu-id="23be6-130">然後選擇 [**建立**]。</span><span class="sxs-lookup"><span data-stu-id="23be6-130">Then, choose **Create**.</span></span>

1. <span data-ttu-id="23be6-131">請檢查並確定程式庫的目標是正確的 .NET Standard 版本。</span><span class="sxs-lookup"><span data-stu-id="23be6-131">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="23be6-132">以滑鼠右鍵按一下**方案總管**中的 [程式庫] 專案，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="23be6-132">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="23be6-133">[**目標 Framework** ] 文字方塊會顯示專案的目標為 .NET Standard 2.0。</span><span class="sxs-lookup"><span data-stu-id="23be6-133">The **Target Framework** text box shows that the project targets .NET Standard 2.0.</span></span>

   ![類別庫的專案屬性](./media/library-with-visual-studio/library-project-properties.png)

1. <span data-ttu-id="23be6-135">如果您使用的是 Visual Basic，請清除 [**根命名空間**] 文字方塊中的文字。</span><span class="sxs-lookup"><span data-stu-id="23be6-135">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   ![類別庫的專案屬性](./media/library-with-visual-studio/vb/library-project-properties.png)

   <span data-ttu-id="23be6-137">針對每個專案，Visual Basic 會自動建立對應至專案名稱的命名空間。</span><span class="sxs-lookup"><span data-stu-id="23be6-137">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="23be6-138">在本教學課程中，您會使用程式碼檔案中的關鍵字來定義最上層命名空間 [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) 。</span><span class="sxs-lookup"><span data-stu-id="23be6-138">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="23be6-139">使用下列程式碼取代*Class1.cs*或*Class1*的程式碼視窗中的程式碼，並儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="23be6-139">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="23be6-140">如果未顯示您想要使用的語言，請變更頁面頂端的 [語言選取器]。</span><span class="sxs-lookup"><span data-stu-id="23be6-140">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   <span data-ttu-id="23be6-141">類別庫 `UtilityLibraries.StringLibrary` 包含名為的方法 `StartsWithUpper` 。</span><span class="sxs-lookup"><span data-stu-id="23be6-141">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="23be6-142">這個方法會傳回 <xref:System.Boolean> 值，指出目前的字串實例是否以大寫字元開頭。</span><span class="sxs-lookup"><span data-stu-id="23be6-142">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="23be6-143">Unicode 標準會區別大寫和小寫字元。</span><span class="sxs-lookup"><span data-stu-id="23be6-143">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="23be6-144">如果是大寫字元，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="23be6-144">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

   <span data-ttu-id="23be6-145">`StartsWithUpper`會實作為[擴充方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)，讓您可以如同類別的成員一樣呼叫它 <xref:System.String> 。</span><span class="sxs-lookup"><span data-stu-id="23be6-145">`StartsWithUpper` is implemented as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

1. <span data-ttu-id="23be6-146">在功能表列上，選取 [**組建**] [組建  >  **方案**] 以確認專案編譯無誤。</span><span class="sxs-lookup"><span data-stu-id="23be6-146">On the menu bar, select **Build** > **Build Solution** to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="23be6-147">將主控台應用程式新增至解決方案</span><span class="sxs-lookup"><span data-stu-id="23be6-147">Add a console app to the solution</span></span>

<span data-ttu-id="23be6-148">新增使用類別庫的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="23be6-148">Add a console application that uses the class library.</span></span> <span data-ttu-id="23be6-149">應用程式會提示使用者輸入字串，並報告字串是否以大寫字元開頭。</span><span class="sxs-lookup"><span data-stu-id="23be6-149">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="23be6-150">將名為 "展示" 的新 .NET Core 主控台應用程式加入至方案。</span><span class="sxs-lookup"><span data-stu-id="23be6-150">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="23be6-151">以滑鼠右鍵按一下**方案總管**中的方案，然後選取 [**加入**  >  **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="23be6-151">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="23be6-152">在 [**加入新專案**] 頁面的 [搜尋] 方塊中，輸入**主控台**。</span><span class="sxs-lookup"><span data-stu-id="23be6-152">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="23be6-153">選擇 [語言] 清單中的 [ **c #** ] 或 [ **Visual Basic** ，然後從 [平臺] 清單中選擇 [**所有平臺**]。</span><span class="sxs-lookup"><span data-stu-id="23be6-153">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="23be6-154">選擇 [ \*\* ( .Net Core) ] 範本的主控台應用程式**，然後選擇 [**下一步]\*\*。</span><span class="sxs-lookup"><span data-stu-id="23be6-154">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="23be6-155">在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入**展示**。</span><span class="sxs-lookup"><span data-stu-id="23be6-155">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="23be6-156">接著，選擇 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="23be6-156">Then choose **Create**.</span></span>

1. <span data-ttu-id="23be6-157">在*Program.cs*或*Program .Vb*檔案的程式碼視窗中，將所有程式碼取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="23be6-157">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   <span data-ttu-id="23be6-158">該程式碼會使用 `row` 變數來維護寫入至主控台視窗的資料列數目計數。</span><span class="sxs-lookup"><span data-stu-id="23be6-158">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="23be6-159">當它大於或等於25時，程式碼就會清除主控台視窗，並向使用者顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="23be6-159">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="23be6-160">此程式會提示使用者輸入字串。</span><span class="sxs-lookup"><span data-stu-id="23be6-160">The program prompts the user to enter a string.</span></span> <span data-ttu-id="23be6-161">它會指出該字串開頭是否為大寫字元。</span><span class="sxs-lookup"><span data-stu-id="23be6-161">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="23be6-162">如果使用者在未輸入字串的情況下按<kbd>Enter</kbd>鍵，應用程式就會結束，而且主控台視窗會關閉。</span><span class="sxs-lookup"><span data-stu-id="23be6-162">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="23be6-163">新增專案參考</span><span class="sxs-lookup"><span data-stu-id="23be6-163">Add a project reference</span></span>

<span data-ttu-id="23be6-164">一開始，新的主控台應用程式專案無法存取類別庫。</span><span class="sxs-lookup"><span data-stu-id="23be6-164">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="23be6-165">若要讓它能夠呼叫類別庫中的方法，請建立類別庫專案的專案參考。</span><span class="sxs-lookup"><span data-stu-id="23be6-165">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="23be6-166">在**方案總管**中，以滑鼠右鍵按一下專案的 [相依性 `ShowCase` ] 節點，然後選取 [**加入專案參考** **]** 。</span><span class="sxs-lookup"><span data-stu-id="23be6-166">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   ![Visual Studio 中的 [新增參考] 內容功能表](media/library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="23be6-168">在 [**參考管理員**] 對話方塊中，選取 [ **StringLibrary** ] 專案，然後選取 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="23be6-168">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   ![已選取 StringLibrary 的參考管理員對話方塊](media/library-with-visual-studio/manage-project-references.png)

## <a name="run-the-app"></a><span data-ttu-id="23be6-170">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="23be6-170">Run the app</span></span>

1. <span data-ttu-id="23be6-171">在方案總管\*\*\*\* 中，以滑鼠右鍵按一下 **ShowCase** 專案，然後在內容功能表中選取 [設定為啟始專案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="23be6-171">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Visual Studio 專案操作功能表來設定啟始專案](media/library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="23be6-173">按<kbd>Ctrl</kbd> + <kbd>F5</kbd>以編譯並執行程式，而不進行任何調試。</span><span class="sxs-lookup"><span data-stu-id="23be6-173">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to compile and run the program without debugging.</span></span>

   ![顯示調試按鈕的 Visual Studio 專案工具列](media/library-with-visual-studio/visual-studio-project-toolbar.png)

1. <span data-ttu-id="23be6-175">輸入字串並按<kbd>enter</kbd>鍵以嘗試程式，然後按<kbd>enter</kbd>結束。</span><span class="sxs-lookup"><span data-stu-id="23be6-175">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="展示執行中的主控台視窗":::

## <a name="additional-resources"></a><span data-ttu-id="23be6-177">其他資源</span><span class="sxs-lookup"><span data-stu-id="23be6-177">Additional resources</span></span>

* [<span data-ttu-id="23be6-178">使用 .NET Core CLI 開發程式庫</span><span class="sxs-lookup"><span data-stu-id="23be6-178">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="23be6-179">[.NET Standard 版本和支援的平臺](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="23be6-179">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="23be6-180">後續步驟</span><span class="sxs-lookup"><span data-stu-id="23be6-180">Next steps</span></span>

<span data-ttu-id="23be6-181">在本教學課程中，您已建立類別庫。</span><span class="sxs-lookup"><span data-stu-id="23be6-181">In this tutorial, you created a class library.</span></span> <span data-ttu-id="23be6-182">在下一個教學課程中，您將瞭解如何對類別庫進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="23be6-182">In the next tutorial, you learn how to unit test the class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="23be6-183">使用 Visual Studio 對 .NET Standard 程式庫進行單元測試</span><span class="sxs-lookup"><span data-stu-id="23be6-183">Unit test a .NET Standard library using Visual Studio</span></span>](testing-library-with-visual-studio.md)

<span data-ttu-id="23be6-184">或者，您可以略過自動化單元測試，並瞭解如何藉由建立 NuGet 套件來共用程式庫：</span><span class="sxs-lookup"><span data-stu-id="23be6-184">Or you can skip automated unit testing and learn how to share the library by creating a NuGet package:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="23be6-185">使用 Visual Studio 建立及發行套件</span><span class="sxs-lookup"><span data-stu-id="23be6-185">Create and publish a package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio)

<span data-ttu-id="23be6-186">或瞭解如何發佈主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="23be6-186">Or learn how to publish a console app.</span></span> <span data-ttu-id="23be6-187">如果您從在本教學課程中建立的解決方案發佈主控台應用程式，類別庫會將它當做 *.dll*檔案。</span><span class="sxs-lookup"><span data-stu-id="23be6-187">If you publish the console app from the solution you created in this tutorial, the class library goes with it as a *.dll* file.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="23be6-188">使用 Visual Studio 發行 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="23be6-188">Publish a .NET Core console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
