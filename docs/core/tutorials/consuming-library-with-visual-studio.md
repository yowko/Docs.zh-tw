---
title: "在 Visual Studio 2017 中透過 .NET Core 使用類別庫"
description: "了解如何使用 Visual Studio 2017 來呼叫類別庫中的成員。"
author: BillWagner
ms.author: wiwagn
ms.date: 08/07/2017
ms.topic: article
ms.prod: .net-core
dev_langs:
- csharp
- vb
ms.workload: dotnetcore
ms.openlocfilehash: 1525bd3f9d249fe39fd65b53bc8d1e8eddb09ab9
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="consuming-a-class-library-with-net-core-in-visual-studio-2017"></a><span data-ttu-id="5d3e7-103">在 Visual Studio 2017 中透過 .NET Core 使用類別庫</span><span class="sxs-lookup"><span data-stu-id="5d3e7-103">Consuming a class library with .NET Core in Visual Studio 2017</span></span>

<span data-ttu-id="5d3e7-104">一旦遵循[在 Visual Studio 2017 中使用 .NET Core 建置 C# 類別庫](./library-with-visual-studio.md)或[在 Visual Studio 2017 中使用 .NET Core 建置 Visual Basic 類別庫](vb-library-with-visual-studio.md)中的步驟建立了類別庫，也[在 Visual Studio 2017 中使用 .NET Core 測試類別庫](testing-library-with-visual-studio.md)中測試了類別庫，並建置了類別庫的發行版本，下一個步驟就是把它提供給呼叫端使用。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-104">Once you've created a class library by following the steps in [Building a C# class library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) or [Building a Visual Basic class library with .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md), tested it in [Testing a class library with .NET Core in Visual Studio 2017](testing-library-with-visual-studio.md), and built a Release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="5d3e7-105">執行這項作業的方法有兩種：</span><span class="sxs-lookup"><span data-stu-id="5d3e7-105">You can do this in two ways:</span></span>

* <span data-ttu-id="5d3e7-106">如果該類別庫將供單一方案使用 (例如，如果它是單一大型應用程式中的元件)，您可以直接將它以專案的形式包含在您的方案中。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>

* <span data-ttu-id="5d3e7-107">如果該類別庫將可供一般存取，則可藉由 NuGet 套件的形式來散發它。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-107">If the library will be generally accessible, you can distribute it as a NuGet package.</span></span>

## <a name="including-a-library-as-a-project-in-a-solution"></a><span data-ttu-id="5d3e7-108">將類別庫以專案形式包含在方案中</span><span class="sxs-lookup"><span data-stu-id="5d3e7-108">Including a library as a project in a solution</span></span>

<span data-ttu-id="5d3e7-109">就像您將單元測試包含在與類別庫相同的方案中一樣，您也可以將應用程式包含在該方案中。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-109">Just as you included unit tests in the same solution as your class library, you can include your application as part of that solution.</span></span> <span data-ttu-id="5d3e7-110">例如，您可以在提示使用者輸入字串並回報其第一個字元是否為大寫的主控台應用程式中，使用您的類別庫：</span><span class="sxs-lookup"><span data-stu-id="5d3e7-110">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="5d3e7-111">C#</span><span class="sxs-lookup"><span data-stu-id="5d3e7-111">C#</span></span>](#tab/csharp)
1. <span data-ttu-id="5d3e7-112">開啟您[在 Visual Studio 2017 中使用 .NET Core 組置 C# 類別庫](./library-with-visual-studio.md)主題中建立的 `ClassLibraryProjects` 方案。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-112">Open the `ClassLibraryProjects` solution you created in the [Building a C# Class Library with .NET Core in Visual Studio 2017](./library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="5d3e7-113">在方案總管 中，以滑鼠右鍵按一下 **ClassLibraryProjects** 方案，然後從內容功能表中，選取 [新增]  >  [新增專案]。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-113">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="5d3e7-114">在 [新增專案] 對話方塊中，展開 [Visual C#] 節點，選取後面跟著 [主控台應用程式 (.NET Core)] 專案範本的 [.NET Core] 節點。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-114">In the **Add New Project** dialog, expand the **Visual C#** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="5d3e7-115">在 **[名稱]** 文字方塊中，輸入 "ShowCase"，然後選取 **[確定]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-115">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![[新增專案] 對話方塊](./media/consuming-library-with-visual-studio/addnewproject.png)

1. <span data-ttu-id="5d3e7-117">在方案總管 中，以滑鼠右鍵按一下 **ShowCase** 專案，然後在內容功能表中選取 [設定為啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-117">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span> 

   ![ShowCase 內容功能表](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. <span data-ttu-id="5d3e7-119">一開始，您的專案並無法存取類別庫。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-119">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="5d3e7-120">若要讓它在您的類別庫中呼叫方法，您可以建立類別庫的參考。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-120">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="5d3e7-121">在方案總管 中，以滑鼠右鍵按一下 `ShowCase` 專案的 [相依性] 節點，然後選取 [新增參考]。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-121">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![ShowCase 相依性內容功能表](./media/consuming-library-with-visual-studio/addreference.png)

1. <span data-ttu-id="5d3e7-123">在 [參考管理員] 對話方塊中，選取**StringLibrary**、您的類別庫專案，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-123">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![參考管理員](./media/consuming-library-with-visual-studio/referencemanager.png)

1. <span data-ttu-id="5d3e7-125">在 *Program.cs* 檔案的程式碼視窗中，以下列程式碼取代所有程式碼：</span><span class="sxs-lookup"><span data-stu-id="5d3e7-125">In the code window for the *Program.cs* file, replace all of the code with the following code:</span></span>

   [!CODE-csharp[UsingClassLib#1](../../../samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]

   <span data-ttu-id="5d3e7-126">此程式碼會使用 [Console.WindowHeight](xref:System.Console.WindowHeight) 屬性來判斷主控台視窗有多少資料列。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-126">The code uses the [Console.WindowHeight](xref:System.Console.WindowHeight) property to determine the number of rows in the console window.</span></span> <span data-ttu-id="5d3e7-127">每當 [Console.CursorTop](xref:System.Console.CursorTop) 屬性大於或等於主控台視窗中的資料列數目時，程式碼都會清除主控台視窗並向使用者顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-127">Whenever the [Console.CursorTop](xref:System.Console.CursorTop) property is greater than or equal to the number of rows in the console window, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="5d3e7-128">此程式會提示使用者輸入字串。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-128">The program prompts the user to enter a string.</span></span> <span data-ttu-id="5d3e7-129">它會指出該字串開頭是否為大寫字元。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-129">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="5d3e7-130">如果使用者沒有輸入字串就按 Enter 鍵，應用程式就會終止且主控台視窗會關閉。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-130">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="5d3e7-131">必要時，變更工具列以編譯 `ShowCase` 專案的 [偵錯] 版本。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-131">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="5d3e7-132">選取 **ShowCase** 按鈕上的綠色箭號，以編譯並執行程式。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-132">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Image](./media/consuming-library-with-visual-studio/toolbar.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="5d3e7-134">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5d3e7-134">Visual Basic</span></span>](#tab/visual-basic)
1. <span data-ttu-id="5d3e7-135">開啟您[在 Visual Studio 2017 中使用 .NET Core 建置類別庫](vb-library-with-visual-studio.md)主題中建立的 `ClassLibraryProjects` 解決方案。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-135">Open the `ClassLibraryProjects` solution you created in the [Building a class Library with Visual Basic and .NET Core in Visual Studio 2017](vb-library-with-visual-studio.md) topic.</span></span> <span data-ttu-id="5d3e7-136">在方案總管 中，以滑鼠右鍵按一下 **ClassLibraryProjects** 方案，然後從內容功能表中，選取 [新增]  >  [新增專案]。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-136">In **Solution Explorer**, right-click the **ClassLibraryProjects** solution and select **Add** > **New Project** from the context menu.</span></span>

1. <span data-ttu-id="5d3e7-137">在 [新增專案] 對話方塊中，展開 [Visual Basic] 節點，選取後面跟著 [主控台應用程式 (.NET Core)] 專案範本的 [.NET Core] 節點。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-137">In the **Add New Project** dialog, expand the **Visual Basic** node and select the **.NET Core** node followed by the **Console App (.NET Core)** project template.</span></span> <span data-ttu-id="5d3e7-138">在 [名稱] 文字方塊中，輸入 "ShowCase"，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-138">In the **Name** text box, type "ShowCase", and select the **OK** button.</span></span>

   ![[新增專案] 對話方塊](./media/consuming-library-with-visual-studio/vb-addnewproject.png)

1. <span data-ttu-id="5d3e7-140">在方案總管 中，以滑鼠右鍵按一下 **ShowCase** 專案，然後在內容功能表中選取 [設定為啟始專案]。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-140">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span> 

   ![ShowCase 內容功能表](./media/consuming-library-with-visual-studio/setstartupproject.png)

1. <span data-ttu-id="5d3e7-142">一開始，您的專案並無法存取類別庫。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-142">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="5d3e7-143">若要讓它在您的類別庫中呼叫方法，您可以建立類別庫的參考。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-143">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="5d3e7-144">在方案總管 中，以滑鼠右鍵按一下 `ShowCase` 專案的 [相依性] 節點，然後選取 [新增參考]。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-144">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![ShowCase 相依性內容功能表](./media/consuming-library-with-visual-studio/addreference.png)

1. <span data-ttu-id="5d3e7-146">在 [參考管理員] 對話方塊中，選取**StringLibrary**、您的類別庫專案，然後選取 [確定] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-146">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![參考管理員](./media/consuming-library-with-visual-studio/referencemanager.png)

1. <span data-ttu-id="5d3e7-148">在 *Program.vb* 檔案的程式碼視窗中，以下列程式碼取代所有程式碼：</span><span class="sxs-lookup"><span data-stu-id="5d3e7-148">In the code window for the *Program.vb* file, replace all of the code with the following code:</span></span>

    [!CODE-vb[UsingClassLib#1](../../../samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="5d3e7-149">此程式碼會使用 [Console.WindowHeight](xref:System.Console.WindowHeight) 屬性來判斷主控台視窗有多少資料列。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-149">The code uses the [Console.WindowHeight](xref:System.Console.WindowHeight) property to determine the number of rows in the console window.</span></span> <span data-ttu-id="5d3e7-150">每當 [Console.CursorTop](xref:System.Console.CursorTop) 屬性大於或等於主控台視窗中的資料列數目時，程式碼都會清除主控台視窗並向使用者顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-150">Whenever the [Console.CursorTop](xref:System.Console.CursorTop) property is greater than or equal to the number of rows in the console window, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="5d3e7-151">此程式會提示使用者輸入字串。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-151">The program prompts the user to enter a string.</span></span> <span data-ttu-id="5d3e7-152">它會指出該字串開頭是否為大寫字元。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-152">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="5d3e7-153">如果使用者沒有輸入字串就按 Enter 鍵，應用程式就會終止且主控台視窗會關閉。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-153">If the user presses the Enter key without entering a string, the application terminates, and the console window closes.</span></span>

1. <span data-ttu-id="5d3e7-154">必要時，變更工具列以編譯 `ShowCase` 專案的 [偵錯] 版本。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-154">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="5d3e7-155">選取 **ShowCase** 按鈕上的綠色箭號，以編譯並執行程式。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-155">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![Image](./media/consuming-library-with-visual-studio/toolbar.png)
---

<span data-ttu-id="5d3e7-157">您可以遵循[使用 Visual Studio 2017 針對 Hello World 應用程式進行偵錯](debugging-with-visual-studio.md)和[使用 Visual Studio 2017 發行 Hello World 應用程式](publishing-with-visual-studio.md)中的步驟操作，對使用此類別庫的應用程式進行偵錯並加以發行。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-157">You can debug and publish the application that uses this library by following the steps in [Debugging your Hello World application with Visual Studio 2017](debugging-with-visual-studio.md) and [Publishing your Hello World Application with Visual Studio 2017](publishing-with-visual-studio.md).</span></span>

## <a name="distributing-the-library-in-a-nuget-package"></a><span data-ttu-id="5d3e7-158">以 NuGet 套件散發類別庫</span><span class="sxs-lookup"><span data-stu-id="5d3e7-158">Distributing the library in a NuGet package</span></span>

<span data-ttu-id="5d3e7-159">您可以藉由 NuGet 套件的形式發行類別庫，讓您的類別庫可供廣泛使用。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-159">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="5d3e7-160">Visual Studio 不支援建立 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-160">Visual Studio does not support the creation of NuGet packages.</span></span> <span data-ttu-id="5d3e7-161">若要建立該套件，您需使用 [`dotnet` 命令列公用程式](../../core/tools/dotnet.md)：</span><span class="sxs-lookup"><span data-stu-id="5d3e7-161">To create one, you use the [`dotnet` command line utility](../../core/tools/dotnet.md):</span></span>

1. <span data-ttu-id="5d3e7-162">開啟主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-162">Open a console window.</span></span> <span data-ttu-id="5d3e7-163">例如，在 Windows 工作列的 [請隨意提出問題] 文字方塊中，輸入`Command Prompt` (或 `cmd` 簡稱)，然後選取 [命令提示字元] 桌面應用程式，或按 Enter 鍵 (如果已在搜尋結果中選取該應用程式) 來開啟主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-163">For example in the **Ask me anything** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="5d3e7-164">瀏覽至您類別庫的專案目錄。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-164">Navigate to your library's project directory.</span></span> <span data-ttu-id="5d3e7-165">除非您已重新設定一般檔案位置，否則該位置會是 *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* 目錄。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-165">Unless you've reconfigured the typical file location, it's in the *Documents\Visual Studio 2017\Projects\ClassLibraryProjects\StringLibrary* directory.</span></span> <span data-ttu-id="5d3e7-166">此目錄包含您的原始程式碼和專案檔 *StringLibrary.csproj*。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-166">The directory contains your source code and a project file, *StringLibrary.csproj*.</span></span>

1. <span data-ttu-id="5d3e7-167">發出命令 `dotnet pack --no-build`。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-167">Issue the command `dotnet pack --no-build`.</span></span> <span data-ttu-id="5d3e7-168">`dotnet` 公用程式會產生一個副檔名為 *.nupkg* 的套件。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-168">The `dotnet` utility generates a package with a *.nupkg* extension.</span></span>

   > [!TIP]
   > <span data-ttu-id="5d3e7-169">如果包含 *dotnet.exe* 的目錄不在您的 PATH 中，則您可以在主控台視窗中輸入 `where dotnet.exe` 來尋找其位置。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-169">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="5d3e7-170">如需有關建立 NuGet 套件的詳細資訊，請參閱[如何使用跨平台工具建立 NuGet 套件](../../core/deploying/creating-nuget-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="5d3e7-170">For more information on creating NuGet packages, see [How to Create a NuGet Package with Cross Platform Tools](../../core/deploying/creating-nuget-packages.md).</span></span>
