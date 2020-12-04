---
title: 使用 Visual Studio 建立 .NET 類別庫
description: 瞭解如何使用 Visual Studio 建立 .NET 類別庫。
ms.date: 08/07/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet,contperfq1
ms.openlocfilehash: 6a3f61525ca86afc9ee71d56cbc9450862760ba4
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599508"
---
# <a name="tutorial-create-a-net-class-library-using-visual-studio"></a><span data-ttu-id="2ed6d-103">教學課程：使用 Visual Studio 建立 .NET 類別庫</span><span class="sxs-lookup"><span data-stu-id="2ed6d-103">Tutorial: Create a .NET class library using Visual Studio</span></span>

<span data-ttu-id="2ed6d-104">在本教學課程中，您會建立簡單的類別庫，其中包含單一字串處理方法。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-104">In this tutorial, you create a simple class library that contains a single string-handling method.</span></span>

<span data-ttu-id="2ed6d-105">「類別庫」會定義應用程式所呼叫的類型和方法。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="2ed6d-106">如果程式庫以 .NET Standard 2.0 為目標，則可以由任何 .NET 執行 (，包括支援 .NET Standard 2.0 的 .NET Framework) 。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-106">If the library targets .NET Standard 2.0, it can be called by any .NET implementation (including .NET Framework) that supports .NET Standard 2.0.</span></span> <span data-ttu-id="2ed6d-107">如果程式庫以 .NET 5 為目標，則可由任何目標為 .NET 5 的應用程式呼叫。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-107">If the library targets .NET 5, it can be called by any application that targets .NET 5.</span></span> <span data-ttu-id="2ed6d-108">本教學課程說明如何以 .NET 5 為目標。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-108">This tutorial shows how to target .NET 5.</span></span>

<span data-ttu-id="2ed6d-109">當您建立類別庫時，可以將它發佈為 NuGet 套件，或作為與使用它之應用程式配套的元件。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-109">When you create a class library, you can distribute it as a NuGet package or as a component bundled with the application that uses it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2ed6d-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="2ed6d-110">Prerequisites</span></span>

- <span data-ttu-id="2ed6d-111">已安裝 **.Net Core 跨平臺開發** 工作負載的 [Visual Studio 2019 16.8 版或更新版本](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019)。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-111">[Visual Studio 2019 version 16.8 or a later version](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) with the **.NET Core cross-platform development** workload installed.</span></span> <span data-ttu-id="2ed6d-112">當您選取此工作負載時，會自動安裝 .NET 5.0 SDK。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-112">The .NET 5.0 SDK is automatically installed when you select this workload.</span></span> <span data-ttu-id="2ed6d-113">本教學課程假設您已啟用在 **新的專案中顯示所有 .Net Core 範本**，如 [教學課程：使用 Visual Studio 建立 .net 主控台應用程式](with-visual-studio.md)中所示。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-113">This tutorial assumes you have enabled **Show all .NET Core templates in the New project**, as shown in [Tutorial: Create a .NET console application using Visual Studio](with-visual-studio.md).</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="2ed6d-114">建立方案</span><span class="sxs-lookup"><span data-stu-id="2ed6d-114">Create a solution</span></span>

<span data-ttu-id="2ed6d-115">首先，建立空白的方案，將類別庫專案放置在中。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-115">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="2ed6d-116">Visual Studio 方案可作為一或多個專案的容器。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-116">A Visual Studio solution serves as a container for one or more projects.</span></span> <span data-ttu-id="2ed6d-117">您會將其他相關的專案新增至相同的方案。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-117">You'll add additional, related projects to the same solution.</span></span>

<span data-ttu-id="2ed6d-118">若要建立空白的方案：</span><span class="sxs-lookup"><span data-stu-id="2ed6d-118">To create the blank solution:</span></span>

1. <span data-ttu-id="2ed6d-119">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-119">Start Visual Studio.</span></span>

2. <span data-ttu-id="2ed6d-120">在 [開始] 視窗中，選擇 [ **建立新專案**]。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-120">On the start window, choose **Create a new project**.</span></span>

3. <span data-ttu-id="2ed6d-121">在 [ **建立新專案** ] 頁面的 [搜尋] 方塊中，輸入 [ **方案** ]。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-121">On the **Create a new project** page, enter **solution** in the search box.</span></span> <span data-ttu-id="2ed6d-122">選擇 [ **空白方案** ] 範本，然後選擇 [ **下一步]**。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-122">Choose the **Blank Solution** template, and then choose **Next**.</span></span>

   :::image type="content" source="media/library-with-visual-studio/blank-solution.png" alt-text="Visual Studio 中的空白方案範本":::

4. <span data-ttu-id="2ed6d-124">在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入 **>classlibraryprojects** 。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-124">On the **Configure your new project** page, enter **ClassLibraryProjects** in the **Project name** box.</span></span> <span data-ttu-id="2ed6d-125">接著，選擇 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-125">Then choose **Create**.</span></span>

## <a name="create-a-class-library-project"></a><span data-ttu-id="2ed6d-126">建立類別庫專案</span><span class="sxs-lookup"><span data-stu-id="2ed6d-126">Create a class library project</span></span>

1. <span data-ttu-id="2ed6d-127">將名為 "StringLibrary" 的新 .NET 類別庫專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-127">Add a new .NET class library project named "StringLibrary" to the solution.</span></span>

   1. <span data-ttu-id="2ed6d-128">以滑鼠右鍵按一下 **方案總管** 中的方案，然後選取 [**加入**  >  **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-128">Right-click on the solution in **Solution Explorer** and select **Add** > **New Project**.</span></span>

   1. <span data-ttu-id="2ed6d-129">在 [ **加入新的專案** ] 頁面上，于 [搜尋] 方塊中輸入 **library** 。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-129">On the **Add a new project** page, enter **library** in the search box.</span></span> <span data-ttu-id="2ed6d-130">從 [語言] 清單中選擇 [ **c #** ] 或 [ **Visual Basic** ，然後從 [平臺] 清單中選擇 [ **所有平臺** ]。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-130">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="2ed6d-131">選擇 [ **類別庫** ] 範本，然後選擇 [ **下一步]**。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-131">Choose the **Class Library** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="2ed6d-132">在 [**設定您的新專案**] 頁面的 [**專案名稱**] 方塊中，輸入 **StringLibrary** ，然後選擇 [**下一步]**。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-132">On the **Configure your new project** page, enter **StringLibrary** in the **Project name** box, and then choose **Next**.</span></span>

   1. <span data-ttu-id="2ed6d-133">在 [ **其他資訊** ] 頁面上，選取 [ **.Net 5.0 (目前的)**]，然後選擇 [ **建立**]。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-133">On the **Additional information** page, select **.NET 5.0 (Current)**, and then choose **Create**.</span></span>

1. <span data-ttu-id="2ed6d-134">請檢查以確定程式庫以正確的 .NET 版本為目標。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-134">Check to make sure that the library targets the correct version of .NET.</span></span> <span data-ttu-id="2ed6d-135">以滑鼠右鍵按一下 **方案總管** 中的程式庫專案，然後選取 [ **屬性**]。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-135">Right-click on the library project in **Solution Explorer**, and then select **Properties**.</span></span> <span data-ttu-id="2ed6d-136">[ **目標 Framework** ] 文字方塊會顯示專案的目標為 .net 5.0。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-136">The **Target Framework** text box shows that the project targets .NET 5.0.</span></span>

1. <span data-ttu-id="2ed6d-137">如果您是使用 Visual Basic，請清除 [ **根命名空間** ] 文字方塊中的文字。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-137">If you're using Visual Basic, clear the text in the **Root namespace** text box.</span></span>

   :::image type="content" source="./media/library-with-visual-studio/vb/library-project-properties.png" alt-text="類別庫的專案屬性":::

   <span data-ttu-id="2ed6d-139">Visual Basic 會針對每個專案自動建立對應至專案名稱的命名空間。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-139">For each project, Visual Basic automatically creates a namespace that corresponds to the project name.</span></span> <span data-ttu-id="2ed6d-140">在本教學課程中，您會使用程式碼檔案中的關鍵字來定義最上層命名空間 [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) 。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-140">In this tutorial, you define a top-level namespace by using the [`namespace`](../../visual-basic/language-reference/statements/namespace-statement.md) keyword in the code file.</span></span>

1. <span data-ttu-id="2ed6d-141">以下列程式碼取代 *Class1.cs*  或 *Class1* 程式碼視窗中的程式碼，然後儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-141">Replace the code in the code window for *Class1.cs*  or *Class1.vb* with the following code, and save the file.</span></span> <span data-ttu-id="2ed6d-142">如果未顯示您想要使用的語言，請變更頁面頂端的語言選取器。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-142">If the language you want to use is not shown, change the language selector at the top of the page.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/StringLibrary/Class1.vb":::

   <span data-ttu-id="2ed6d-143">類別庫（class library） `UtilityLibraries.StringLibrary` 包含名為的方法 `StartsWithUpper` 。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-143">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="2ed6d-144">這個方法會傳回 <xref:System.Boolean> 值，指出目前字串實例的開頭是否為大寫字元。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-144">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="2ed6d-145">Unicode 標準會區別大寫和小寫字元。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-145">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="2ed6d-146">如果是大寫字元，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-146">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

   <span data-ttu-id="2ed6d-147">`StartsWithUpper` 會實作為 [擴充方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md) ，如此您就可以呼叫它，就如同它是類別的成員一樣 <xref:System.String> 。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-147">`StartsWithUpper` is implemented as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

1. <span data-ttu-id="2ed6d-148">在功能表列上，選取 [**組建**  >  **組建方案**] 或按 <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>B</kbd> ，確認專案編譯時沒有發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-148">On the menu bar, select **Build** > **Build Solution** or press <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>B</kbd> to verify that the project compiles without error.</span></span>

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="2ed6d-149">將主控台應用程式新增至解決方案</span><span class="sxs-lookup"><span data-stu-id="2ed6d-149">Add a console app to the solution</span></span>

<span data-ttu-id="2ed6d-150">加入使用類別庫的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-150">Add a console application that uses the class library.</span></span> <span data-ttu-id="2ed6d-151">應用程式會提示使用者輸入字串，並報告字串是否以大寫字元開頭。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-151">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="2ed6d-152">將名為 "展示" 的新 .NET 主控台應用程式加入至方案。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-152">Add a new .NET console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="2ed6d-153">以滑鼠右鍵按一下 **方案總管** 中的方案，然後選取 [**加入**  >  **新專案**]。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-153">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="2ed6d-154">在 [ **新增專案** ] 頁面的 [搜尋] 方塊中，輸入 **主控台** 。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-154">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="2ed6d-155">從 [語言] 清單中選擇 [ **c #** ] 或 [ **Visual Basic** ，然後從 [平臺] 清單中選擇 [ **所有平臺** ]。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-155">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span>

   1. <span data-ttu-id="2ed6d-156">選擇 [ **主控台應用程式** ] 範本，然後選擇 [ **下一步]**。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-156">Choose the **Console Application** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="2ed6d-157">在 [**設定您的新專案**] 頁面上，于 [**專案名稱**] 方塊中輸入 **展示**。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-157">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="2ed6d-158">然後選擇 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-158">Then choose **Next**.</span></span>

   1. <span data-ttu-id="2ed6d-159">在 [**其他資訊**] 頁面上，選取 [**目標 Framework** ] 方塊中的 [ **.net 5.0 (目前)** 。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-159">On the **Additional information** page, select **.NET 5.0 (Current)** in the **Target Framework** box.</span></span> <span data-ttu-id="2ed6d-160">接著，選擇 [建立]  。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-160">Then choose **Create**.</span></span>

1. <span data-ttu-id="2ed6d-161">在 *Program.cs* 或 .vb 檔案的 *程式* 代碼視窗中，以下列程式碼取代所有程式碼。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-161">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::
   :::code language="vb" source="./snippets/library-with-visual-studio/vb/ShowCase/Program.vb":::

   <span data-ttu-id="2ed6d-162">該程式碼會使用 `row` 變數來維護寫入至主控台視窗的資料列數目計數。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-162">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="2ed6d-163">只要超過或等於25，程式碼就會清除主控台視窗，並向使用者顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-163">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="2ed6d-164">此程式會提示使用者輸入字串。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-164">The program prompts the user to enter a string.</span></span> <span data-ttu-id="2ed6d-165">它會指出該字串開頭是否為大寫字元。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-165">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="2ed6d-166">如果使用者按下 <kbd>Enter</kbd> 鍵但未輸入字串，則應用程式會結束，且主控台視窗會關閉。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-166">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="2ed6d-167">新增專案參考</span><span class="sxs-lookup"><span data-stu-id="2ed6d-167">Add a project reference</span></span>

<span data-ttu-id="2ed6d-168">一開始，新的主控台應用程式專案沒有類別庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-168">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="2ed6d-169">若要允許它呼叫類別庫中的方法，請建立類別庫專案的專案參考。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-169">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="2ed6d-170">在 **方案總管** 中，以滑鼠右鍵按一下專案的 [相依性 `ShowCase` ] 節點，然後選取 [**加入專案參考** **]** 。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-170">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node, and select **Add Project Reference**.</span></span>

   :::image type="content" source="media/library-with-visual-studio/add-reference-context-menu.png" alt-text="在 Visual Studio 中新增參考內容功能表":::

1. <span data-ttu-id="2ed6d-172">在 [ **參考管理員** ] 對話方塊中，選取 [ **StringLibrary** ] 專案，然後選取 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-172">In the **Reference Manager** dialog, select the **StringLibrary** project, and select **OK**.</span></span>

   :::image type="content" source="media/library-with-visual-studio/manage-project-references.png" alt-text="已選取 StringLibrary 的 [參考管理員] 對話方塊":::

## <a name="run-the-app"></a><span data-ttu-id="2ed6d-174">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="2ed6d-174">Run the app</span></span>

1. <span data-ttu-id="2ed6d-175">在方案總管 中，以滑鼠右鍵按一下 **ShowCase** 專案，然後在內容功能表中選取 [設定為啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-175">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   :::image type="content" source="media/library-with-visual-studio/set-startup-project-context-menu.png" alt-text="用來設定啟始專案的 Visual Studio 專案內容功能表":::

1. <span data-ttu-id="2ed6d-177">按下<kbd>Ctrl</kbd> + <kbd>F5</kbd>以編譯並執行程式，而不需進行任何偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-177">Press <kbd>Ctrl</kbd>+<kbd>F5</kbd> to compile and run the program without debugging.</span></span>

   :::image type="content" source="media/library-with-visual-studio/visual-studio-project-toolbar.png" alt-text="顯示 [調試] 按鈕 Visual Studio 專案工具列":::

1. <span data-ttu-id="2ed6d-179">輸入字串並按 <kbd>enter</kbd>鍵以嘗試程式，然後按 <kbd>enter</kbd> 鍵結束。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-179">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   :::image type="content" source="media/library-with-visual-studio/run-showcase.png" alt-text="具有正在執行展示的主控台視窗":::

## <a name="additional-resources"></a><span data-ttu-id="2ed6d-181">其他資源</span><span class="sxs-lookup"><span data-stu-id="2ed6d-181">Additional resources</span></span>

* [<span data-ttu-id="2ed6d-182">使用 .NET CLI 開發程式庫</span><span class="sxs-lookup"><span data-stu-id="2ed6d-182">Develop libraries with the .NET CLI</span></span>](libraries.md)
* <span data-ttu-id="2ed6d-183">[.NET Standard 支援的版本和平臺](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-183">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="2ed6d-184">後續步驟</span><span class="sxs-lookup"><span data-stu-id="2ed6d-184">Next steps</span></span>

<span data-ttu-id="2ed6d-185">在本教學課程中，您已建立類別庫。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-185">In this tutorial, you created a class library.</span></span> <span data-ttu-id="2ed6d-186">在下一個教學課程中，您將瞭解如何對類別庫進行單元測試。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-186">In the next tutorial, you learn how to unit test the class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2ed6d-187">使用 Visual Studio 對 .NET 類別庫進行單元測試</span><span class="sxs-lookup"><span data-stu-id="2ed6d-187">Unit test a .NET class library using Visual Studio</span></span>](testing-library-with-visual-studio.md)

<span data-ttu-id="2ed6d-188">或者，您可以略過自動化單元測試，並瞭解如何藉由建立 NuGet 套件來共用程式庫：</span><span class="sxs-lookup"><span data-stu-id="2ed6d-188">Or you can skip automated unit testing and learn how to share the library by creating a NuGet package:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2ed6d-189">使用 Visual Studio 建立及發行套件</span><span class="sxs-lookup"><span data-stu-id="2ed6d-189">Create and publish a package using Visual Studio</span></span>](/nuget/quickstart/create-and-publish-a-package-using-visual-studio)

<span data-ttu-id="2ed6d-190">或瞭解如何發佈主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-190">Or learn how to publish a console app.</span></span> <span data-ttu-id="2ed6d-191">如果您從本教學課程所建立的方案發佈主控台應用程式，類別庫會將它當作 *.dll* 檔來使用。</span><span class="sxs-lookup"><span data-stu-id="2ed6d-191">If you publish the console app from the solution you created in this tutorial, the class library goes with it as a *.dll* file.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2ed6d-192">使用 Visual Studio 發佈 .NET 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="2ed6d-192">Publish a .NET console application using Visual Studio</span></span>](publishing-with-visual-studio.md)
