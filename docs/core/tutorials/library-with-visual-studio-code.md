---
title: 使用 Visual Studio Code 建立 .NET Standard 類別庫
description: 瞭解如何使用 Visual Studio Code 建立 .NET Standard 類別庫。
ms.date: 06/08/2020
ms.openlocfilehash: d37e3c663146c90f4ae4188b25ea7e501501c93b
ms.sourcegitcommit: e7acba36517134238065e4d50bb4a1cfe47ebd06
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2020
ms.locfileid: "89465282"
---
# <a name="tutorial-create-a-net-standard-library-using-visual-studio-code"></a><span data-ttu-id="e9308-103">教學課程：使用 Visual Studio Code 建立 .NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="e9308-103">Tutorial: Create a .NET Standard library using Visual Studio Code</span></span>

<span data-ttu-id="e9308-104">在本教學課程中，您會建立包含單一字串處理方法的簡單公用程式程式庫。</span><span class="sxs-lookup"><span data-stu-id="e9308-104">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span> <span data-ttu-id="e9308-105">您可以將它實作為 [擴充方法](../../csharp/programming-guide/classes-and-structs/extension-methods.md) ，讓您可以如同類別的成員一樣呼叫它 <xref:System.String> 。</span><span class="sxs-lookup"><span data-stu-id="e9308-105">You implement it as an [extension method](../../csharp/programming-guide/classes-and-structs/extension-methods.md) so that you can call it as if it were a member of the <xref:System.String> class.</span></span>

<span data-ttu-id="e9308-106">「類別庫」\*\* 會定義應用程式所呼叫的類型和方法。</span><span class="sxs-lookup"><span data-stu-id="e9308-106">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="e9308-107">以 .NET Standard 2.0 為目標的類別庫，可讓任何支援該版本 .NET Standard 的 .NET 執行呼叫您的程式庫。</span><span class="sxs-lookup"><span data-stu-id="e9308-107">A class library that targets .NET Standard 2.0 allows your library to be called by any .NET implementation that supports that version of .NET Standard.</span></span> <span data-ttu-id="e9308-108">當您完成類別庫時，可以將它散發為協力廠商元件，或做為配套的元件，以及一或多個應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9308-108">When you finish your class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e9308-109">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="e9308-109">Prerequisites</span></span>

1. <span data-ttu-id="e9308-110">已安裝[c # 擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)功能的[Visual Studio Code](https://code.visualstudio.com/) 。</span><span class="sxs-lookup"><span data-stu-id="e9308-110">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="e9308-111">如需有關如何在 Visual Studio Code 上安裝擴充功能的詳細資訊，請參閱 [VS Code 擴充功能 Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery)。</span><span class="sxs-lookup"><span data-stu-id="e9308-111">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="e9308-112">[.Net Core 3.1 SDK 或更新版本](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="e9308-112">The [.NET Core 3.1 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="e9308-113">建立方案</span><span class="sxs-lookup"><span data-stu-id="e9308-113">Create a solution</span></span>

<span data-ttu-id="e9308-114">首先，建立空白的方案，將類別庫專案放置在中。</span><span class="sxs-lookup"><span data-stu-id="e9308-114">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="e9308-115">方案可作為一或多個專案的容器。</span><span class="sxs-lookup"><span data-stu-id="e9308-115">A solution serves as a container for one or more projects.</span></span> <span data-ttu-id="e9308-116">您會將其他相關的專案新增至相同的方案。</span><span class="sxs-lookup"><span data-stu-id="e9308-116">You'll add additional, related projects to the same solution.</span></span>

1. <span data-ttu-id="e9308-117">啟動 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="e9308-117">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="e9308-118">**File**  >  從主功能表選取 [macOS) 上的 [開啟**資料夾**] (**開啟 ...**</span><span class="sxs-lookup"><span data-stu-id="e9308-118">Select **File** > **Open Folder** (**Open...** on macOS) from the main menu</span></span>

1. <span data-ttu-id="e9308-119">在 [ **開啟資料夾** ] 對話方塊中，建立 *>classlibraryprojects* 資料夾，然後按一下 [ **選取資料夾** (在 macOS) **開啟** ]。</span><span class="sxs-lookup"><span data-stu-id="e9308-119">In the **Open Folder** dialog, create a *ClassLibraryProjects* folder and click **Select Folder** (**Open** on macOS).</span></span>

1. <span data-ttu-id="e9308-120">從主功能表中選取 [ **View**terminal]，以在 Visual Studio Code 中開啟**終端**機  >  **Terminal** 。</span><span class="sxs-lookup"><span data-stu-id="e9308-120">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="e9308-121">**終端**機會在 *>classlibraryprojects*資料夾中使用命令提示字元開啟。</span><span class="sxs-lookup"><span data-stu-id="e9308-121">The **Terminal** opens with the command prompt in the *ClassLibraryProjects* folder.</span></span>

1. <span data-ttu-id="e9308-122">在 **終端**機中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="e9308-122">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new sln
   ```

   <span data-ttu-id="e9308-123">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e9308-123">The terminal output looks like the following example:</span></span>

   ```output
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a><span data-ttu-id="e9308-124">建立類別庫專案</span><span class="sxs-lookup"><span data-stu-id="e9308-124">Create a class library project</span></span>

<span data-ttu-id="e9308-125">將名為 "StringLibrary" 的新 .NET Standard 類別庫專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="e9308-125">Add a new .NET Standard class library project named "StringLibrary" to the solution.</span></span>

1. <span data-ttu-id="e9308-126">在終端機中執行下列命令，以建立程式庫專案：</span><span class="sxs-lookup"><span data-stu-id="e9308-126">In the terminal, run the following command to create the library project:</span></span>

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   <span data-ttu-id="e9308-127">`-o`或 `--output` 命令指定要放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="e9308-127">The `-o` or `--output` command specifies the location to place the generated output.</span></span>

   <span data-ttu-id="e9308-128">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e9308-128">The terminal output looks like the following example:</span></span>

   ```output
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restore completed in 328.13 ms for C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="e9308-129">執行下列命令，以將程式庫專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="e9308-129">Run the following command to add the library project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="e9308-130">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e9308-130">The terminal output looks like the following example:</span></span>

   ```output
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. <span data-ttu-id="e9308-131">請檢查以確定程式庫的目標是正確的 .NET Standard 版本。</span><span class="sxs-lookup"><span data-stu-id="e9308-131">Check to make sure that the library targets the correct version of .NET Standard.</span></span> <span data-ttu-id="e9308-132">在 [ **Explorer**] 中，開啟 [ *StringLibrary]/[StringLibrary*]。</span><span class="sxs-lookup"><span data-stu-id="e9308-132">In **Explorer**, open *StringLibrary/StringLibrary.csproj*.</span></span>

   <span data-ttu-id="e9308-133">`TargetFramework`元素會顯示專案的目標為 .NET Standard 2.0。</span><span class="sxs-lookup"><span data-stu-id="e9308-133">The `TargetFramework` element shows that the project targets .NET Standard 2.0.</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>netstandard2.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="e9308-134">開啟 *Class1.cs* ，並將程式碼取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="e9308-134">Open *Class1.cs* and replace the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   <span data-ttu-id="e9308-135">類別庫（class library） `UtilityLibraries.StringLibrary` 包含名為的方法 `StartsWithUpper` 。</span><span class="sxs-lookup"><span data-stu-id="e9308-135">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="e9308-136">這個方法會傳回 <xref:System.Boolean> 值，指出目前字串實例的開頭是否為大寫字元。</span><span class="sxs-lookup"><span data-stu-id="e9308-136">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="e9308-137">Unicode 標準會區別大寫和小寫字元。</span><span class="sxs-lookup"><span data-stu-id="e9308-137">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="e9308-138">如果是大寫字元，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="e9308-138">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="e9308-139">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="e9308-139">Save the file.</span></span>

1. <span data-ttu-id="e9308-140">執行下列命令以建立方案，並確認專案編譯時沒有錯誤。</span><span class="sxs-lookup"><span data-stu-id="e9308-140">Run the following command to build the solution and verify that the project compiles without error.</span></span>

   ```dotnetcli
   dotnet build
   ```

   <span data-ttu-id="e9308-141">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e9308-141">The terminal output looks like the following example:</span></span>

   ```output
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

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="e9308-142">將主控台應用程式新增至解決方案</span><span class="sxs-lookup"><span data-stu-id="e9308-142">Add a console app to the solution</span></span>

<span data-ttu-id="e9308-143">加入使用類別庫的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9308-143">Add a console application that uses the class library.</span></span> <span data-ttu-id="e9308-144">應用程式會提示使用者輸入字串，並報告字串是否以大寫字元開頭。</span><span class="sxs-lookup"><span data-stu-id="e9308-144">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="e9308-145">在終端機中執行下列命令，以建立主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="e9308-145">In the terminal, run the following command to create the console app project:</span></span>

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   <span data-ttu-id="e9308-146">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e9308-146">The terminal output looks like the following example:</span></span>

   ```output
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restore completed in 210.78 ms for C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj.
   Restore succeeded.
   ```

1. <span data-ttu-id="e9308-147">執行下列命令，以將主控台應用程式專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="e9308-147">Run the following command to add the console app project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   <span data-ttu-id="e9308-148">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e9308-148">The terminal output looks like the following example:</span></span>

   ```output
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. <span data-ttu-id="e9308-149">開啟 [ *展示]/[Program* ]，並將所有程式碼取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="e9308-149">Open *ShowCase/Program.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="e9308-150">該程式碼會使用 `row` 變數來維護寫入至主控台視窗的資料列數目計數。</span><span class="sxs-lookup"><span data-stu-id="e9308-150">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="e9308-151">只要超過或等於25，程式碼就會清除主控台視窗，並向使用者顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="e9308-151">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="e9308-152">此程式會提示使用者輸入字串。</span><span class="sxs-lookup"><span data-stu-id="e9308-152">The program prompts the user to enter a string.</span></span> <span data-ttu-id="e9308-153">它會指出該字串開頭是否為大寫字元。</span><span class="sxs-lookup"><span data-stu-id="e9308-153">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="e9308-154">如果使用者按下 <kbd>Enter</kbd> 鍵但未輸入字串，則應用程式會結束，且主控台視窗會關閉。</span><span class="sxs-lookup"><span data-stu-id="e9308-154">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="e9308-155">儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="e9308-155">Save your changes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="e9308-156">新增專案參考</span><span class="sxs-lookup"><span data-stu-id="e9308-156">Add a project reference</span></span>

<span data-ttu-id="e9308-157">一開始，新的主控台應用程式專案沒有類別庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="e9308-157">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="e9308-158">若要允許它呼叫類別庫中的方法，請建立類別庫專案的專案參考。</span><span class="sxs-lookup"><span data-stu-id="e9308-158">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="e9308-159">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="e9308-159">Run the following command:</span></span>

   ```dotnetcli
   dotnet add ShowCase/ShowCase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="e9308-160">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e9308-160">The terminal output looks like the following example:</span></span>

   ```output
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

## <a name="run-the-app"></a><span data-ttu-id="e9308-161">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="e9308-161">Run the app</span></span>

1. <span data-ttu-id="e9308-162">在終端中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="e9308-162">Run the following command in the terminal:</span></span>

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. <span data-ttu-id="e9308-163">輸入字串並按 <kbd>enter</kbd>鍵以嘗試程式，然後按 <kbd>enter</kbd> 鍵結束。</span><span class="sxs-lookup"><span data-stu-id="e9308-163">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   <span data-ttu-id="e9308-164">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="e9308-164">The terminal output looks like the following example:</span></span>

   ```output
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   a string that starts with a lowercase letter
   Input: a string that starts with a lowercase letter
   Begins with uppercase? : No
   ```

## <a name="additional-resources"></a><span data-ttu-id="e9308-165">其他資源</span><span class="sxs-lookup"><span data-stu-id="e9308-165">Additional resources</span></span>

* [<span data-ttu-id="e9308-166">使用 .NET Core CLI 開發程式庫</span><span class="sxs-lookup"><span data-stu-id="e9308-166">Develop libraries with the .NET Core CLI</span></span>](libraries.md)
* <span data-ttu-id="e9308-167">[.NET Standard 支援的版本和平臺](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="e9308-167">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="e9308-168">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e9308-168">Next steps</span></span>

<span data-ttu-id="e9308-169">在本教學課程中，您已建立解決方案、新增程式庫專案，並加入使用該程式庫的主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="e9308-169">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="e9308-170">在下一個教學課程中，您會將單元測試專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="e9308-170">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e9308-171">使用 Visual Studio Code 測試具有 .NET Core 的 .NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="e9308-171">Test a .NET Standard library with .NET Core using Visual Studio Code</span></span>](testing-library-with-visual-studio-code.md)
