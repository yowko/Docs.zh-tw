---
title: 使用 Visual Studio Code 建立 .NET Standard 類別庫
description: 瞭解如何使用 Visual Studio Code 建立 .NET Standard 類別庫。
ms.date: 06/08/2020
ms.openlocfilehash: f7d2319bcea58f63ca40e43ba39745bdf1b394ce
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2020
ms.locfileid: "84701795"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-code"></a><span data-ttu-id="ad9e2-103">教學課程：使用 Visual Studio Code 建立 .NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="ad9e2-103">Tutorial: Create a .NET Standard library using Visual Studio Code</span></span>

<span data-ttu-id="ad9e2-104">在本教學課程中，您會建立包含單一字串處理方法的簡單公用程式程式庫。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-104">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="ad9e2-105">您可以將它實作為[擴充方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md)，讓您可以如同類別的成員一樣呼叫它 <xref:System.String> 。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="ad9e2-106">「類別庫」\*\* 會定義應用程式所呼叫的類型和方法。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="ad9e2-107">以 .NET Standard 2.0 為目標的類別庫，可讓任何支援該版本 .NET Standard 的 .NET 部署呼叫您的程式庫。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-107">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="ad9e2-108">當您完成類別庫時，您可以將它散發為協力廠商元件，或作為一或多個應用程式的配套元件。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ad9e2-109">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="ad9e2-109">Prerequisites</span></span>

1. <span data-ttu-id="ad9e2-110">已安裝[c # 擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)功能的[Visual Studio Code](https://code.visualstudio.com/) 。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-110">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="ad9e2-111">如需有關如何在 Visual Studio Code 上安裝延伸模組的詳細資訊，請參閱[VS Code 延伸模組 Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery)。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-111">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="ad9e2-112">[.Net Core 3.1 SDK 或更新版本](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="ad9e2-112">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="ad9e2-113">建立方案</span><span class="sxs-lookup"><span data-stu-id="ad9e2-113">Create a solution</span></span>

<span data-ttu-id="ad9e2-114">一開始先建立一個空白的方案，將類別庫專案放入中。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-114">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="ad9e2-115">解決方案會當做一個或多個專案的容器。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-115">A solution serves as a container for one or more projects.</span></span> <span data-ttu-id="ad9e2-116">您會在相同的方案中加入其他相關的專案。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-116">You'll add additional, related projects to the same solution.</span></span>

1. <span data-ttu-id="ad9e2-117">啟動 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-117">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="ad9e2-118">從**File**主功能表選取 [檔案] [  >  **開啟資料夾**] （**開啟**macOS）</span><span class="sxs-lookup"><span data-stu-id="ad9e2-118">Select **File** > **Open Folder** (**Open...** on macOS) from the main menu</span></span>

1. <span data-ttu-id="ad9e2-119">在 [**開啟資料夾**] 對話方塊中，建立*ClassLibraryProjects*資料夾，然後按一下 [**選取資料夾**] （在 macOS 上**開啟**）。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-119">In the **Open Folder** dialog, create a *ClassLibraryProjects* folder and click **Select Folder** (**Open** on macOS).</span></span>

1. <span data-ttu-id="ad9e2-120">從主功能表選取 [**查看**終端機]，以在 Visual Studio Code 中開啟**終端**機  >  **Terminal** 。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-120">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="ad9e2-121">**終端**機會在*ClassLibraryProjects*資料夾中以命令提示字元開啟。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-121">The **Terminal** opens with the command prompt in the *ClassLibraryProjects* folder.</span></span>

1. <span data-ttu-id="ad9e2-122">在**終端**機中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="ad9e2-122">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new sln
   ```

   <span data-ttu-id="ad9e2-123">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ad9e2-123">The terminal output looks like the following example:</span></span>

   ```
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a><span data-ttu-id="ad9e2-124">建立類別庫專案</span><span class="sxs-lookup"><span data-stu-id="ad9e2-124">Create a class library project</span></span>

<span data-ttu-id="ad9e2-125">將名為 "StringLibrary" 的新 .NET Standard 類別庫專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-125">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

1. <span data-ttu-id="ad9e2-126">在終端機中，執行下列命令以建立程式庫專案：</span><span class="sxs-lookup"><span data-stu-id="ad9e2-126">In the terminal, run the following command to create the library project:</span></span>

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   <span data-ttu-id="ad9e2-127">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ad9e2-127">The terminal output looks like the following example:</span></span>

   ```
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restore completed in 328.13 ms for C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="ad9e2-128">執行下列命令，將程式庫專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="ad9e2-128">Run the following command to add the library project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="ad9e2-129">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ad9e2-129">The terminal output looks like the following example:</span></span>

   ```
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. <span data-ttu-id="ad9e2-130">請檢查並確定程式庫的目標是正確的 .NET Standard 版本。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-130">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="ad9e2-131">在**Explorer**中，開啟*StringLibrary/StringLibrary*。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-131">In **Explorer**, open *StringLibrary/StringLibrary.csproj*.</span></span>

   <span data-ttu-id="ad9e2-132">`TargetFramework`元素會顯示專案的目標為 .NET Standard 2.0。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-132">The `TargetFramework` element shows that the project targets .NET Standard 2.0.</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>netstandard2.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="ad9e2-133">開啟*Class1.cs* ，並將程式碼取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-133">Open *Class1.cs* and replace the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   <span data-ttu-id="ad9e2-134">類別庫 `UtilityLibraries.StringLibrary` 包含名為的方法 `StartsWithUpper` 。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-134">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="ad9e2-135">這個方法會傳回 <xref:System.Boolean> 值，指出目前的字串實例是否以大寫字元開頭。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-135">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="ad9e2-136">Unicode 標準會區別大寫和小寫字元。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-136">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="ad9e2-137">如果是大寫字元，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-137">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="ad9e2-138">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-138">Save the file.</span></span>

1. <span data-ttu-id="ad9e2-139">執行下列命令來建立方案，並確認專案編譯無誤。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-139">Run the following command to build the solution and verify that the project compiles without error.</span></span>

   ```dotnetcli
   dotnet build
   ```

   <span data-ttu-id="ad9e2-140">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ad9e2-140">The terminal output looks like the following example:</span></span>

   ```
   Microsoft (R) Build Engine version 16.6.0 for .NET Core
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     You are using a preview version of .NET Core. See: https://aka.ms/dotnet-core-preview
     StringLibrary -> C:\Projects\ClassLibraryProjects\StringLibrary\bin\Debug\netstandard2.0\StringLibrary.dll
   Build succeeded.
       0 Warning(s)
       0 Error(s)
   Time Elapsed 00:00:02.78
   ```

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="ad9e2-141">將主控台應用程式新增至解決方案</span><span class="sxs-lookup"><span data-stu-id="ad9e2-141">Add a console app to the solution</span></span>

<span data-ttu-id="ad9e2-142">新增使用類別庫的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-142">Add a console application that uses the class library.</span></span> <span data-ttu-id="ad9e2-143">應用程式會提示使用者輸入字串，並報告字串是否以大寫字元開頭。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-143">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="ad9e2-144">在終端機中，執行下列命令來建立主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="ad9e2-144">In the terminal, run the following command to create the console app project:</span></span>

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   <span data-ttu-id="ad9e2-145">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ad9e2-145">The terminal output looks like the following example:</span></span>

   ```
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restore completed in 210.78 ms for C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="ad9e2-146">執行下列命令，將主控台應用程式專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="ad9e2-146">Run the following command to add the console app project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   <span data-ttu-id="ad9e2-147">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ad9e2-147">The terminal output looks like the following example:</span></span>

   ```
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. <span data-ttu-id="ad9e2-148">開啟 [*展示/程式 .cs* ]，並將所有程式碼取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-148">Open *ShowCase/Program.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="ad9e2-149">該程式碼會使用 `row` 變數來維護寫入至主控台視窗的資料列數目計數。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-149">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="ad9e2-150">當它大於或等於25時，程式碼就會清除主控台視窗，並向使用者顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-150">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="ad9e2-151">此程式會提示使用者輸入字串。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-151">The program prompts the user to enter a string.</span></span> <span data-ttu-id="ad9e2-152">它會指出該字串開頭是否為大寫字元。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-152">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="ad9e2-153">如果使用者在未輸入字串的情況下按<kbd>Enter</kbd>鍵，應用程式就會結束，而且主控台視窗會關閉。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-153">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="ad9e2-154">儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-154">Save your changes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="ad9e2-155">新增專案參考</span><span class="sxs-lookup"><span data-stu-id="ad9e2-155">Add a project reference</span></span>

<span data-ttu-id="ad9e2-156">一開始，新的主控台應用程式專案無法存取類別庫。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-156">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="ad9e2-157">若要讓它能夠呼叫類別庫中的方法，請建立類別庫專案的專案參考。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-157">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="ad9e2-158">執行以下命令：</span><span class="sxs-lookup"><span data-stu-id="ad9e2-158">Run the following command:</span></span>

   ```dotnetcli
   dotnet add ShowCase/Showcase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="ad9e2-159">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ad9e2-159">The terminal output looks like the following example:</span></span>

   ```
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

## <a name="run-the-app"></a><span data-ttu-id="ad9e2-160">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="ad9e2-160">Run the app</span></span>

1. <span data-ttu-id="ad9e2-161">在終端機中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="ad9e2-161">Run the following command in the terminal:</span></span>

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. <span data-ttu-id="ad9e2-162">輸入字串並按<kbd>enter</kbd>鍵以嘗試程式，然後按<kbd>enter</kbd>結束。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-162">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   <span data-ttu-id="ad9e2-163">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="ad9e2-163">The terminal output looks like the following example:</span></span>

   ```
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   A string that starts with a lowercase letter
   Input: A string that starts with a lowercase letter
   Begins with uppercase? : Yes
   ```

## <a name="additional-resources"></a><span data-ttu-id="ad9e2-164">其他資源</span><span class="sxs-lookup"><span data-stu-id="ad9e2-164">Additional resources</span></span>

* [<span data-ttu-id="ad9e2-165">使用 .NET Core CLI 開發程式庫</span><span class="sxs-lookup"><span data-stu-id="ad9e2-165">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="ad9e2-166">[.NET Standard 版本和支援的平臺](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-166">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="ad9e2-167">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ad9e2-167">Next steps</span></span>

<span data-ttu-id="ad9e2-168">在本教學課程中，您已建立解決方案、新增程式庫專案，以及加入使用該程式庫的主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-168">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="ad9e2-169">在下一個教學課程中，您會將單元測試專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="ad9e2-169">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ad9e2-170">使用 Visual Studio Code 測試具有 .NET Core 的 .NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="ad9e2-170">Test a .NET Standard library with .NET Core using Visual Studio Code</span></span>](testing-library-with-visual-studio-code.md)
