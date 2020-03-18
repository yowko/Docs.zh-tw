---
title: 在 Visual Studio 中取用 .NET Standard 程式庫
description: 使用 Visual Studio 2019 構建一個 .NET Core 應用程式，調用另一個類庫的成員。
ms.date: 12/20/2019
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 4eb75f23359334ea483cba1498f1804c4b24c80c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920462"
---
# <a name="consume-a-net-standard-library-in-visual-studio"></a><span data-ttu-id="96470-103">在 Visual Studio 中取用 .NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="96470-103">Consume a .NET Standard library in Visual Studio</span></span>

<span data-ttu-id="96470-104">創建 .NET 標準類庫、測試並生成庫發佈版本後，下一步是使其可供調用方使用。</span><span class="sxs-lookup"><span data-stu-id="96470-104">Once you've created a .NET Standard class library, tested it, and built a release version of the library, the next step is to make it available to callers.</span></span> <span data-ttu-id="96470-105">您可以使用兩種方式執行此動作：</span><span class="sxs-lookup"><span data-stu-id="96470-105">You can do this in two ways:</span></span>

- <span data-ttu-id="96470-106">如果該類別庫將供單一方案使用 (例如，如果它是單一大型應用程式中的元件)，您可以直接將它以專案的形式包含在您的方案中。</span><span class="sxs-lookup"><span data-stu-id="96470-106">If the library will be used by a single solution (for example, if it's a component in a single large application), you can include it as a project in your solution.</span></span>
- <span data-ttu-id="96470-107">如果庫將公開提供，則可以將其分發為 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="96470-107">If the library will be publicly available, you can distribute it as a NuGet package.</span></span>

<span data-ttu-id="96470-108">在本教學課程中，您會了解如何：</span><span class="sxs-lookup"><span data-stu-id="96470-108">In this tutorial, you learn how to:</span></span>
> [!div class="checklist"]
>
> - <span data-ttu-id="96470-109">將主控台應用添加到引用 .NET 標準庫專案的解決方案。</span><span class="sxs-lookup"><span data-stu-id="96470-109">Add a console app to your solution that references a .NET Standard library project.</span></span>
> - <span data-ttu-id="96470-110">創建包含 .NET 標準庫專案的 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="96470-110">Create a NuGet package that contains a .NET Standard library project.</span></span>

## <a name="add-a-console-app-to-your-solution"></a><span data-ttu-id="96470-111">將主控台應用添加到解決方案</span><span class="sxs-lookup"><span data-stu-id="96470-111">Add a console app to your solution</span></span>

<span data-ttu-id="96470-112">正如在[Visual Studio 中的測試 .NET 標準庫](testing-library-with-visual-studio.md)中將單元測試包含在與類庫相同的解決方案中一樣，您可以將應用程式包含在該解決方案中。</span><span class="sxs-lookup"><span data-stu-id="96470-112">Just as you included unit tests in the same solution as your class library in [Test a .NET Standard library in Visual Studio](testing-library-with-visual-studio.md), you can include your application as part of that solution.</span></span> <span data-ttu-id="96470-113">例如，您可以在提示使用者輸入字串並回報其第一個字元是否為大寫的主控台應用程式中，使用您的類別庫：</span><span class="sxs-lookup"><span data-stu-id="96470-113">For example, you can use your class library in a console application that prompts the user to enter a string and reports whether its first character is uppercase:</span></span>

1. <span data-ttu-id="96470-114">打開在`ClassLibraryProjects`Visual Studio 文章中[生成 .NET 標準庫中](library-with-visual-studio.md)創建的解決方案。</span><span class="sxs-lookup"><span data-stu-id="96470-114">Open the `ClassLibraryProjects` solution you created in the [Build a .NET Standard library in Visual Studio](library-with-visual-studio.md) article.</span></span>

1. <span data-ttu-id="96470-115">向解決方案添加新的 .NET 核心主控台應用程式，名為"ShowCase"。</span><span class="sxs-lookup"><span data-stu-id="96470-115">Add a new .NET Core console application named "ShowCase" to the solution.</span></span>

   1. <span data-ttu-id="96470-116">按右鍵**解決方案資源管理器**中的解決方案，然後選擇"**添加新** > **專案**"。</span><span class="sxs-lookup"><span data-stu-id="96470-116">Right-click on the solution in **Solution Explorer** and select **Add** > **New project**.</span></span>

   1. <span data-ttu-id="96470-117">在"**添加新專案**"頁上，在搜索框中輸入**主控台**。</span><span class="sxs-lookup"><span data-stu-id="96470-117">On the **Add a new project** page, enter **console** in the search box.</span></span> <span data-ttu-id="96470-118">從"語言"清單中選擇**C#** 或**視覺化基本，** 然後從"平臺"清單中選擇 **"所有平臺**"。</span><span class="sxs-lookup"><span data-stu-id="96470-118">Choose **C#** or **Visual Basic** from the Language list, and then choose **All platforms** from the Platform list.</span></span> <span data-ttu-id="96470-119">選擇**主控台應用 （.NET 核心）** 範本，然後選擇 **"下一步**"。</span><span class="sxs-lookup"><span data-stu-id="96470-119">Choose the **Console App (.NET Core)** template, and then choose **Next**.</span></span>

   1. <span data-ttu-id="96470-120">在"**配置新專案**"頁上，在 **"專案名稱**"框中輸入 **"顯示案例**"。</span><span class="sxs-lookup"><span data-stu-id="96470-120">On the **Configure your new project** page, enter **ShowCase** in the **Project name** box.</span></span> <span data-ttu-id="96470-121">然後，選擇 **"創建**"。</span><span class="sxs-lookup"><span data-stu-id="96470-121">Then, choose **Create**.</span></span>

1. <span data-ttu-id="96470-122">在方案總管\*\*\*\* 中，以滑鼠右鍵按一下 **ShowCase** 專案，然後在內容功能表中選取 [設定為啟始專案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96470-122">In **Solution Explorer**, right-click the **ShowCase** project and select **Set as StartUp Project** in the context menu.</span></span>

   ![視覺化工作室專案內容功能表，用於設置啟動專案](./media/consuming-library-with-visual-studio/set-startup-project-context-menu.png)

1. <span data-ttu-id="96470-124">一開始，您的專案並無法存取類別庫。</span><span class="sxs-lookup"><span data-stu-id="96470-124">Initially, your project doesn't have access to your class library.</span></span> <span data-ttu-id="96470-125">若要讓它在您的類別庫中呼叫方法，您可以建立類別庫的參考。</span><span class="sxs-lookup"><span data-stu-id="96470-125">To allow it to call methods in your class library, you create a reference to the class library.</span></span> <span data-ttu-id="96470-126">在方案總管\*\*\*\* 中，以滑鼠右鍵按一下 `ShowCase` 專案的 [相依性]\*\*\*\* 節點，然後選取 [新增參考]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="96470-126">In **Solution Explorer**, right-click the `ShowCase` project's **Dependencies** node and select **Add Reference**.</span></span>

   ![在視覺化工作室中添加參考內容功能表](./media/consuming-library-with-visual-studio/add-reference-context-menu.png)

1. <span data-ttu-id="96470-128">在 [參考管理員]\*\*\*\* 對話方塊中，選取**StringLibrary**、您的類別庫專案，然後選取 [確定]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="96470-128">In the **Reference Manager** dialog, select **StringLibrary**, your class library project, and select the **OK** button.</span></span>

   ![選定字串庫的參考管理器對話方塊](./media/consuming-library-with-visual-studio/manage-project-references.png)

1. <span data-ttu-id="96470-130">在*Program.cs*或*程式.vb*檔的代碼視窗中，將所有代碼替換為以下代碼：</span><span class="sxs-lookup"><span data-stu-id="96470-130">In the code window for the *Program.cs* or *Program.vb* file, replace all of the code with the following code:</span></span>

   [!code-csharp[UsingClassLib#1](~/samples/snippets/csharp/getting_started/with_visual_studio_2017/showcase.cs)]
   [!code-vb[UsingClassLib#1](~/samples/snippets/core/tutorials/vb-library-with-visual-studio/showcase.vb)]

   <span data-ttu-id="96470-131">該程式碼會使用 `row` 變數來維護寫入至主控台視窗的資料列數目計數。</span><span class="sxs-lookup"><span data-stu-id="96470-131">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="96470-132">每當它大於或等於 25 時，代碼都會清除主控台視窗並顯示給使用者的消息。</span><span class="sxs-lookup"><span data-stu-id="96470-132">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="96470-133">此程式會提示使用者輸入字串。</span><span class="sxs-lookup"><span data-stu-id="96470-133">The program prompts the user to enter a string.</span></span> <span data-ttu-id="96470-134">它會指出該字串開頭是否為大寫字元。</span><span class="sxs-lookup"><span data-stu-id="96470-134">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="96470-135">如果使用者在不輸入字串的情況下按下 Enter 鍵，應用程式將結束，主控台視窗將關閉。</span><span class="sxs-lookup"><span data-stu-id="96470-135">If the user presses the Enter key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="96470-136">必要時，變更工具列以編譯 `ShowCase` 專案的 [偵錯]\*\*\*\* 版本。</span><span class="sxs-lookup"><span data-stu-id="96470-136">If necessary, change the toolbar to compile the **Debug** release of the `ShowCase` project.</span></span> <span data-ttu-id="96470-137">選取 **ShowCase** 按鈕上的綠色箭號，以編譯並執行程式。</span><span class="sxs-lookup"><span data-stu-id="96470-137">Compile and run the program by selecting the green arrow on the **ShowCase** button.</span></span>

   ![視覺化工作室專案工具列顯示調試按鈕](./media/consuming-library-with-visual-studio/visual-studio-project-toolbar.png)

<span data-ttu-id="96470-139">您可以使用 Visual Studio 調試和發佈使用此庫的應用程式，按照調試[C# 或 Visual Basic .NET 核心 Hello World 應用程式](debugging-with-visual-studio.md)的步驟，並使用 Visual Studio[發佈您的 .NET Core Hello World 應用程式](publishing-with-visual-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="96470-139">You can debug and publish the application that uses this library by following the steps in [Debug your C# or Visual Basic .NET Core Hello World application using Visual Studio](debugging-with-visual-studio.md) and [Publish your .NET Core Hello World application with Visual Studio](publishing-with-visual-studio.md).</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="96470-140">建立 NuGet 套件</span><span class="sxs-lookup"><span data-stu-id="96470-140">Create a NuGet package</span></span>

<span data-ttu-id="96470-141">您可以藉由 NuGet 套件的形式發行類別庫，讓您的類別庫可供廣泛使用。</span><span class="sxs-lookup"><span data-stu-id="96470-141">You can make your class library widely available by publishing it as a NuGet package.</span></span> <span data-ttu-id="96470-142">視覺化工作室不支援創建 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="96470-142">Visual Studio doesn't support the creation of NuGet packages.</span></span> <span data-ttu-id="96470-143">要創建一個，您需要使用 .NET 核心 CLI 命令：</span><span class="sxs-lookup"><span data-stu-id="96470-143">To create one, you need to use the .NET Core CLI commands:</span></span>

1. <span data-ttu-id="96470-144">開啟主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="96470-144">Open a console window.</span></span>

   <span data-ttu-id="96470-145">例如，在 Windows 工作列上的搜索框中輸入**命令提示符**。</span><span class="sxs-lookup"><span data-stu-id="96470-145">For example, enter **Command Prompt** in the search box on the Windows task bar.</span></span> <span data-ttu-id="96470-146">選擇**命令提示**桌面應用，或按**Enter，** 如果它已在搜尋結果中選擇。</span><span class="sxs-lookup"><span data-stu-id="96470-146">Select the **Command Prompt** desktop app or press **Enter** if it's already selected in the search results.</span></span>

1. <span data-ttu-id="96470-147">瀏覽至您類別庫的專案目錄。</span><span class="sxs-lookup"><span data-stu-id="96470-147">Navigate to your library's project directory.</span></span> <span data-ttu-id="96470-148">該目錄包含您的原始程式碼和專案檔案 *，StringLibrary.csproj*或*StringLibrary.vbproj*。</span><span class="sxs-lookup"><span data-stu-id="96470-148">The directory contains your source code and a project file, *StringLibrary.csproj* or *StringLibrary.vbproj*.</span></span>

1. <span data-ttu-id="96470-149">運行[dotnet pack](../tools/dotnet-pack.md)命令以生成具有 *.nupkg*副檔名的包：</span><span class="sxs-lookup"><span data-stu-id="96470-149">Run the [dotnet pack](../tools/dotnet-pack.md) command to generate a package with a *.nupkg* extension:</span></span>

   ```dotnetcli
   dotnet pack --no-build
   ```

   > [!TIP]
   > <span data-ttu-id="96470-150">如果包含 *dotnet.exe* 的目錄不在您的 PATH 中，則您可以在主控台視窗中輸入 `where dotnet.exe` 來尋找其位置。</span><span class="sxs-lookup"><span data-stu-id="96470-150">If the directory that contains *dotnet.exe* is not in your PATH, you can find its location by entering `where dotnet.exe` in the console window.</span></span>

<span data-ttu-id="96470-151">有關創建 NuGet 包的詳細資訊，請參閱[如何使用 .NET 核心 CLI 創建 NuGet 包](../deploying/creating-nuget-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="96470-151">For more information on creating NuGet packages, see [How to create a NuGet package with the .NET Core CLI](../deploying/creating-nuget-packages.md).</span></span>
