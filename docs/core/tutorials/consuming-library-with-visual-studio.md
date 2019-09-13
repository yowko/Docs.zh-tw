---
title: 在 Visual Studio 2017 中取用 .NET Standard 程式庫
description: 使用 Visual Studio 2017 來建置會呼叫另一個類別庫之成員的 .NET Core 應用程式。
author: BillWagner
ms.author: wiwagn
ms.date: 06/05/2018
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: ff60bb5de403970f432e938cba81ca4e99476e8a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70925979"
---
# <a name="consume-a-net-standard-library-in-visual-studio-2017"></a><span data-ttu-id="b33f1-103">在 Visual Studio 2017 中取用 .NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="b33f1-103">Consume a .NET Standard library in Visual Studio 2017</span></span>

<span data-ttu-id="b33f1-104">在您遵循[在 Visual Studio 2017 中使用 .NET Core 建置 C# 類別庫](./library-with-visual-studio.md)或[在 Visual Studio 2017 中使用 .NET Core 建置 Visual Basic 類別庫](vb-library-with-visual-studio.md)中的步驟建立 .NET Standard 類別庫，並根據[在 Visual Studio 2017 中使用 .NET Core 測試類別庫](testing-library-with-visual-studio.md)中的指示測試該類別庫，然後建置該類別庫的發行版本之後，下一個步驟就是把它提供給呼叫端使用。</span><span class="sxs-lookup"><span data-stu-id="b33f1-104">Once you've created a .NET Standard class library by following the steps in [Building a C# class library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) or [Building a Visual Basic class library with .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md), tested it in [Testing a class library with .NET Core in Visual Studio 2017](testing-library-with-visual-studio.md), and built a Release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="b33f1-105">執行這項作業的方法有兩種：</span><span class="sxs-lookup"><span data-stu-id="b33f1-105">You can do this in two ways:</span></span>

* <span data-ttu-id="b33f1-106">如果該類別庫將供單一方案使用 (例如，如果它是單一大型應用程式中的元件)，您可以直接將它以專案的形式包含在您的方案中。</span><span class="sxs-lookup"><span data-stu-id="b33f1-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>

* <span data-ttu-id="b33f1-107">如果該類別庫將可供一般存取，則可藉由 NuGet 套件的形式來散發它。</span><span class="sxs-lookup"><span data-stu-id="b33f1-107">If the library will be generally accessible, you can distribute it as a NuGet package.</span></span>

## <a name="including-a-library-as-a-project-in-a-solution"></a><span data-ttu-id="b33f1-108">將類別庫以專案形式包含在方案中</span><span class="sxs-lookup"><span data-stu-id="b33f1-108">Including a library as a project in a solution</span></span>

<span data-ttu-id="b33f1-109">就像您將單元測試包含在與類別庫相同的方案中一樣，您也可以將應用程式包含在該方案中。</span><span class="sxs-lookup"><span data-stu-id="b33f1-109">Just as you included unit tests in the same solution as your class library, you can include your application as part of that solution.</span></span> <span data-ttu-id="b33f1-110">例如，您可以在提示使用者輸入字串並回報其第一個字元是否為大寫的主控台應用程式中，使用您的類別庫：</span><span class="sxs-lookup"><span data-stu-id="b33f1-110">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="b33f1-111">C#</span><span class="sxs-lookup"><span data-stu-id="b33f1-111">C#</span></span>](#tab/csharp)

1. <span data-ttu-id="b33f1-112">開啟您[在 Visual Studio 2017 中使用 .NET Core 組置 C# 類別庫](./library-with-visual-studio.md)主題中建立的 `ClassLibraryProjects` 方案。</span><span class="sxs-lookup"><span data-stu-id="b33f1-112">Open the `ClassLibraryProjects` solution you created in the [Building a C# Class Library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="b33f1-113">在方案總管 中，以滑鼠右鍵按一下 **ClassLibraryProjects** 方案，然後從內容功能表中，選取 [新增]  >  [新增專案]。</span><span class="sxs-lookup"><span data-stu-id="b33f1-113">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="b33f1-114">在 [新增專案] 對話方塊中，展開 [Visual C#] 節點，選取後面跟著 [主控台應用程式 (.NET Core)] 專案範本的 [.NET Core] 節點。</span><span class="sxs-lookup"><span data-stu-id="b33f1-114">In the **Add New Project** dialog, expand the **Visual C#** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="b33f1-115">在 **[名稱]** 文字方塊中，輸入 "ShowCase"，然後選取 **[確定]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b33f1-115">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Visual Studio [新增專案] 對話方塊 - C#](./media/consuming-library-with-visual-studio/add-new-project-dialog.png)

1. <span data-ttu-id="b33f1-117">在 **方案總管** 中，以滑鼠右鍵按一下 **ShowCase** 專案，然後在內容功能表中選取 **[設定為啟始專案]** 。</span><span class="sxs-lookup"><span data-stu-id="b33f1-117">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![Visual Studio 專案的設定啟始專案操作功能表 - C#](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="b33f1-119">一開始，您的專案並無法存取類別庫。</span><span class="sxs-lookup"><span data-stu-id="b33f1-119">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="b33f1-120">若要讓它在您的類別庫中呼叫方法，您可以建立類別庫的參考。</span><span class="sxs-lookup"><span data-stu-id="b33f1-120">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="b33f1-121">在方案總管 中，以滑鼠右鍵按一下 `ShowCase` 專案的 [相依性] 節點，然後選取 [新增參考]。</span><span class="sxs-lookup"><span data-stu-id="b33f1-121">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Visual Studio 專案的 [新增參考] 操作功能表 - C#](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="b33f1-123">在 **[參考管理員]** 對話方塊中，選取**StringLibrary**、您的類別庫專案，然後選取 **[確定]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b33f1-123">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Visual Studio [參考管理員] 對話方塊 - C#](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="b33f1-125">在 *Program.cs* 檔案的程式碼視窗中，以下列程式碼取代所有程式碼：</span><span class="sxs-lookup"><span data-stu-id="b33f1-125">In the code window for the *Program.cs* file, replace all of the code with the following code:</span></span>

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   <span data-ttu-id="b33f1-126">該程式碼會使用 `row` 變數來維護寫入至主控台視窗的資料列數目計數。</span><span class="sxs-lookup"><span data-stu-id="b33f1-126">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="b33f1-127">當它大於或等於 25 時，程式碼就會清除主控台視窗，並向使用者顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="b33f1-127">Whenever it is greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="b33f1-128">此程式會提示使用者輸入字串。</span><span class="sxs-lookup"><span data-stu-id="b33f1-128">The program prompts the user to enter a string.</span></span> <span data-ttu-id="b33f1-129">它會指出該字串開頭是否為大寫字元。</span><span class="sxs-lookup"><span data-stu-id="b33f1-129">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="b33f1-130">如果使用者沒有輸入字串就按 Enter 鍵，應用程式就會終止且主控台視窗會關閉。</span><span class="sxs-lookup"><span data-stu-id="b33f1-130">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="b33f1-131">必要時，變更工具列以編譯 `ShowCase` 專案的 [偵錯] 版本。</span><span class="sxs-lookup"><span data-stu-id="b33f1-131">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="b33f1-132">選取 **ShowCase** 按鈕上的綠色箭號，以編譯並執行程式。</span><span class="sxs-lookup"><span data-stu-id="b33f1-132">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![顯示 [偵錯] 按鈕的 Visual Studio 專案工具列 - C#](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

# <a name="visual-basictabvb"></a>[<span data-ttu-id="b33f1-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b33f1-134">Visual Basic</span></span>](#tab/vb)

1. <span data-ttu-id="b33f1-135">開啟您[在 Visual Studio 2017 中使用 .NET Core 建置類別庫](vb-library-with-visual-studio.md)主題中建立的 `ClassLibraryProjects` 解決方案。</span><span class="sxs-lookup"><span data-stu-id="b33f1-135">Open the `ClassLibraryProjects` solution you created in the [Building a class Library with Visual Basic and .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="b33f1-136">在方案總管 中，以滑鼠右鍵按一下 **ClassLibraryProjects** 方案，然後從內容功能表中，選取 [新增]  >  [新增專案]。</span><span class="sxs-lookup"><span data-stu-id="b33f1-136">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="b33f1-137">在 [新增專案] 對話方塊中，展開 [Visual Basic] 節點，選取後面跟著 [主控台應用程式 (.NET Core)] 專案範本的 [.NET Core] 節點。</span><span class="sxs-lookup"><span data-stu-id="b33f1-137">In the **Add New Project** dialog, expand the **Visual Basic** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="b33f1-138">在 **[名稱]** 文字方塊中，輸入 "ShowCase"，然後選取 **[確定]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b33f1-138">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![Visual Studio [新增專案] 對話方塊 - Visual Basic](./media/consuming-library-with-visual-studio/add-new-vb-project-dialog.png)

1. <span data-ttu-id="b33f1-140">在 **方案總管** 中，以滑鼠右鍵按一下 **ShowCase** 專案，然後在內容功能表中選取 **[設定為啟始專案]** 。</span><span class="sxs-lookup"><span data-stu-id="b33f1-140">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span> 

   ![Visual Studio 專案的設定啟始專案操作功能表 - Visual Basic](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="b33f1-142">一開始，您的專案並無法存取類別庫。</span><span class="sxs-lookup"><span data-stu-id="b33f1-142">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="b33f1-143">若要讓它在您的類別庫中呼叫方法，您可以建立類別庫的參考。</span><span class="sxs-lookup"><span data-stu-id="b33f1-143">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="b33f1-144">在方案總管 中，以滑鼠右鍵按一下 `ShowCase` 專案的 [相依性] 節點，然後選取 [新增參考]。</span><span class="sxs-lookup"><span data-stu-id="b33f1-144">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![Visual Studio 專案的 [新增參考] 操作功能表 - Visual Basic](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="b33f1-146">在 **[參考管理員]** 對話方塊中，選取**StringLibrary**、您的類別庫專案，然後選取 **[確定]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="b33f1-146">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![Visual Studio [參考管理員] 對話方塊 - Visual Basic](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="b33f1-148">在 *Program.vb* 檔案的程式碼視窗中，以下列程式碼取代所有程式碼：</span><span class="sxs-lookup"><span data-stu-id="b33f1-148">In the code window for the *Program.vb* file, replace all of the code with the following code:</span></span>

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="b33f1-149">該程式碼會使用 `row` 變數來維護寫入至主控台視窗的資料列數目計數。</span><span class="sxs-lookup"><span data-stu-id="b33f1-149">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="b33f1-150">當它大於或等於 25 時，程式碼就會清除主控台視窗，並向使用者顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="b33f1-150">Whenever it is greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="b33f1-151">此程式會提示使用者輸入字串。</span><span class="sxs-lookup"><span data-stu-id="b33f1-151">The program prompts the user to enter a string.</span></span> <span data-ttu-id="b33f1-152">它會指出該字串開頭是否為大寫字元。</span><span class="sxs-lookup"><span data-stu-id="b33f1-152">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="b33f1-153">如果使用者沒有輸入字串就按 Enter 鍵，應用程式就會終止且主控台視窗會關閉。</span><span class="sxs-lookup"><span data-stu-id="b33f1-153">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="b33f1-154">必要時，變更工具列以編譯 `ShowCase` 專案的 [偵錯] 版本。</span><span class="sxs-lookup"><span data-stu-id="b33f1-154">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="b33f1-155">選取 **ShowCase** 按鈕上的綠色箭號，以編譯並執行程式。</span><span class="sxs-lookup"><span data-stu-id="b33f1-155">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![工具列上的 [偵錯] - Visual Basic](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

---

<span data-ttu-id="b33f1-157">您可以遵循[使用 Visual Studio 2017 針對 Hello World 應用程式進行偵錯](debugging-with-visual-studio.md)和[使用 Visual Studio 2017 發行 Hello World 應用程式](publishing-with-visual-studio.md)中的步驟操作，對使用此類別庫的應用程式進行偵錯並加以發行。</span><span class="sxs-lookup"><span data-stu-id="b33f1-157">You can debug and publish the application that uses this library by following the steps in [Debugging your Hello World application with Visual Studio 2017](debugging-with-visual-studio.md) and [Publishing your Hello World Application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

## <a name="distributing-the-library-in-a-nuget-package"></a><span data-ttu-id="b33f1-158">以 NuGet 套件散發類別庫</span><span class="sxs-lookup"><span data-stu-id="b33f1-158">Distributing the library in a NuGet package</span></span>

<span data-ttu-id="b33f1-159">您可以藉由 NuGet 套件的形式發行類別庫，讓您的類別庫可供廣泛使用。</span><span class="sxs-lookup"><span data-stu-id="b33f1-159">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="b33f1-160">Visual Studio 不支援建立 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="b33f1-160">Visual Studio does not support the creation of NuGet packages.</span></span> <span data-ttu-id="b33f1-161">若要建立該套件，您需使用 [`dotnet` 命令列公用程式](../tools/dotnet.md)：</span><span class="sxs-lookup"><span data-stu-id="b33f1-161">To create one, you use the [`dotnet` command line utility](../tools/dotnet.md):</span></span>

1. <span data-ttu-id="b33f1-162">開啟主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="b33f1-162">Open a console window.</span></span> <span data-ttu-id="b33f1-163">例如，在 Windows 工作列的 [請隨意提出問題] 文字方塊中，輸入`Command Prompt` (或 `cmd` 簡稱)，然後選取 [命令提示字元] 桌面應用程式，或按 Enter 鍵 (如果已在搜尋結果中選取該應用程式) 來開啟主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="b33f1-163">For example in the **Ask me anything** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="b33f1-164">瀏覽至您類別庫的專案目錄。</span><span class="sxs-lookup"><span data-stu-id="b33f1-164">Navigate to your library's project directory.</span></span> <span data-ttu-id="b33f1-165">除非您已重新設定一般檔案位置，否則該位置會是 *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* 目錄。</span><span class="sxs-lookup"><span data-stu-id="b33f1-165">Unless you've reconfigured the typical file location, it's in the *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* directory.</span></span> <span data-ttu-id="b33f1-166">此目錄包含您的原始程式碼和專案檔 *StringLibrary.csproj*。</span><span class="sxs-lookup"><span data-stu-id="b33f1-166">The directory contains your source code and a project file, *StringLibrary.csproj*.</span></span>

1. <span data-ttu-id="b33f1-167">發出命令 `dotnet pack --no-build`。</span><span class="sxs-lookup"><span data-stu-id="b33f1-167">Issue the command `dotnet pack --no-build`.</span></span> <span data-ttu-id="b33f1-168">`dotnet` 公用程式會產生一個副檔名為 *.nupkg* 的套件。</span><span class="sxs-lookup"><span data-stu-id="b33f1-168">The `dotnet` utility generates a package with a *.nupkg* extension.</span></span>

   > [!TIP]
   > <span data-ttu-id="b33f1-169">如果包含 *dotnet.exe* 的目錄不在您的 PATH 中，則您可以在主控台視窗中輸入 `where dotnet.exe` 來尋找其位置。</span><span class="sxs-lookup"><span data-stu-id="b33f1-169">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="b33f1-170">如需有關建立 NuGet 套件的詳細資訊，請參閱[如何使用跨平台工具建立 NuGet 套件](../deploying/creating-nuget-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="b33f1-170">For more information on creating NuGet packages, see [How to Create a NuGet Package with Cross Platform Tools](../deploying/creating-nuget-packages.md).</span></span>
