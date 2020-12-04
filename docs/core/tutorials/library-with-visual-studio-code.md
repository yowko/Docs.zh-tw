---
title: 使用 Visual Studio Code 建立 .NET 類別庫
description: 瞭解如何使用 Visual Studio Code 建立 .NET 類別庫。
ms.date: 11/18/2020
ms.openlocfilehash: 4473163b76060623b364d7dabf7366c3575e3dcd
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599495"
---
# <a name="tutorial-create-a-net-class-library-using-visual-studio-code"></a><span data-ttu-id="851c2-103">教學課程：使用 Visual Studio Code 建立 .NET 類別庫</span><span class="sxs-lookup"><span data-stu-id="851c2-103">Tutorial: Create a .NET class library using Visual Studio Code</span></span>

<span data-ttu-id="851c2-104">在本教學課程中，您會建立包含單一字串處理方法的簡單公用程式程式庫。</span><span class="sxs-lookup"><span data-stu-id="851c2-104">In this tutorial, you create a simple utility library that contains a single string-handling method.</span></span>

<span data-ttu-id="851c2-105">「類別庫」會定義應用程式所呼叫的類型和方法。</span><span class="sxs-lookup"><span data-stu-id="851c2-105">A *class library* defines types and methods that are called by an application.</span></span> <span data-ttu-id="851c2-106">如果程式庫以 .NET Standard 2.0 為目標，則可以由任何 .NET 執行 (，包括支援 .NET Standard 2.0 的 .NET Framework) 。</span><span class="sxs-lookup"><span data-stu-id="851c2-106">If the library targets .NET Standard 2.0, it can be called by any .NET implementation (including .NET Framework) that supports .NET Standard 2.0.</span></span> <span data-ttu-id="851c2-107">如果程式庫以 .NET 5 為目標，則可由任何目標為 .NET 5 的應用程式呼叫。</span><span class="sxs-lookup"><span data-stu-id="851c2-107">If the library targets .NET 5, it can be called by any application that targets .NET 5.</span></span> <span data-ttu-id="851c2-108">本教學課程說明如何以 .NET 5 為目標。</span><span class="sxs-lookup"><span data-stu-id="851c2-108">This tutorial shows how to target .NET 5.</span></span>

<span data-ttu-id="851c2-109">當您建立類別庫時，可以將它散發為協力廠商元件，或做為配套的元件，以及一或多個應用程式。</span><span class="sxs-lookup"><span data-stu-id="851c2-109">When you create a class library, you can distribute it as a third-party component or as a bundled component with one or more applications.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="851c2-110">必要條件</span><span class="sxs-lookup"><span data-stu-id="851c2-110">Prerequisites</span></span>

1. <span data-ttu-id="851c2-111">已安裝[c # 擴充](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp)功能的[Visual Studio Code](https://code.visualstudio.com/) 。</span><span class="sxs-lookup"><span data-stu-id="851c2-111">[Visual Studio Code](https://code.visualstudio.com/) with the [C# extension](https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp) installed.</span></span> <span data-ttu-id="851c2-112">如需有關如何在 Visual Studio Code 上安裝擴充功能的詳細資訊，請參閱 [VS Code 擴充功能 Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery)。</span><span class="sxs-lookup"><span data-stu-id="851c2-112">For information about how to install extensions on Visual Studio Code, see [VS Code Extension Marketplace](https://code.visualstudio.com/docs/editor/extension-gallery).</span></span>
2. <span data-ttu-id="851c2-113">[.Net 5.0 SDK 或更新版本](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="851c2-113">The [.NET 5.0 SDK or later](https://dotnet.microsoft.com/download)</span></span>

## <a name="create-a-solution"></a><span data-ttu-id="851c2-114">建立方案</span><span class="sxs-lookup"><span data-stu-id="851c2-114">Create a solution</span></span>

<span data-ttu-id="851c2-115">首先，建立空白的方案，將類別庫專案放置在中。</span><span class="sxs-lookup"><span data-stu-id="851c2-115">Start by creating a blank solution to put the class library project in.</span></span> <span data-ttu-id="851c2-116">方案可作為一或多個專案的容器。</span><span class="sxs-lookup"><span data-stu-id="851c2-116">A solution serves as a container for one or more projects.</span></span> <span data-ttu-id="851c2-117">您會將其他相關的專案新增至相同的方案。</span><span class="sxs-lookup"><span data-stu-id="851c2-117">You'll add additional, related projects to the same solution.</span></span>

1. <span data-ttu-id="851c2-118">啟動 Visual Studio Code。</span><span class="sxs-lookup"><span data-stu-id="851c2-118">Start Visual Studio Code.</span></span>

1. <span data-ttu-id="851c2-119">**File**  >  從主功能表選取 [macOS) 上的 [開啟 **資料夾**] (**開啟 ...**</span><span class="sxs-lookup"><span data-stu-id="851c2-119">Select **File** > **Open Folder** (**Open...** on macOS) from the main menu</span></span>

1. <span data-ttu-id="851c2-120">在 [ **開啟資料夾** ] 對話方塊中，建立 *>classlibraryprojects* 資料夾，然後按一下 [ **選取資料夾** (在 macOS) **開啟** ]。</span><span class="sxs-lookup"><span data-stu-id="851c2-120">In the **Open Folder** dialog, create a *ClassLibraryProjects* folder and click **Select Folder** (**Open** on macOS).</span></span>

1. <span data-ttu-id="851c2-121">從主功能表中選取 [ **View** terminal]，以在 Visual Studio Code 中開啟 **終端** 機  >  **Terminal** 。</span><span class="sxs-lookup"><span data-stu-id="851c2-121">Open the **Terminal** in Visual Studio Code by selecting **View** > **Terminal** from the main menu.</span></span>

   <span data-ttu-id="851c2-122">**終端** 機會在 *>classlibraryprojects* 資料夾中使用命令提示字元開啟。</span><span class="sxs-lookup"><span data-stu-id="851c2-122">The **Terminal** opens with the command prompt in the *ClassLibraryProjects* folder.</span></span>

1. <span data-ttu-id="851c2-123">在 **終端** 機中，輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="851c2-123">In the **Terminal**, enter the following command:</span></span>

   ```dotnetcli
   dotnet new sln
   ```

   <span data-ttu-id="851c2-124">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="851c2-124">The terminal output looks like the following example:</span></span>

   ```output
   The template "Solution File" was created successfully.
   ```

## <a name="create-a-class-library-project"></a><span data-ttu-id="851c2-125">建立類別庫專案</span><span class="sxs-lookup"><span data-stu-id="851c2-125">Create a class library project</span></span>

<span data-ttu-id="851c2-126">將名為 "StringLibrary" 的新 .NET 類別庫專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="851c2-126">Add a new .NET class library project named "StringLibrary" to the solution.</span></span>

1. <span data-ttu-id="851c2-127">在終端機中執行下列命令，以建立程式庫專案：</span><span class="sxs-lookup"><span data-stu-id="851c2-127">In the terminal, run the following command to create the library project:</span></span>

   ```dotnetcli
   dotnet new classlib -o StringLibrary
   ```

   <span data-ttu-id="851c2-128">`-o`或 `--output` 命令指定要放置所產生輸出的位置。</span><span class="sxs-lookup"><span data-stu-id="851c2-128">The `-o` or `--output` command specifies the location to place the generated output.</span></span>

   <span data-ttu-id="851c2-129">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="851c2-129">The terminal output looks like the following example:</span></span>

   ```output
   The template "Class library" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on StringLibrary\StringLibrary.csproj...
     Determining projects to restore...
     Restored C:\Projects\ClassLibraryProjects\StringLibrary\StringLibrary.csproj (in 328 ms).
   Restore succeeded.
   ```

1. <span data-ttu-id="851c2-130">執行下列命令，以將程式庫專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="851c2-130">Run the following command to add the library project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="851c2-131">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="851c2-131">The terminal output looks like the following example:</span></span>

   ```output
   Project `StringLibrary\StringLibrary.csproj` added to the solution.
   ```

1. <span data-ttu-id="851c2-132">請檢查以確定程式庫以 .NET 5 為目標。</span><span class="sxs-lookup"><span data-stu-id="851c2-132">Check to make sure that the library targets .NET 5.</span></span> <span data-ttu-id="851c2-133">在 [ **Explorer**] 中，開啟 [ *StringLibrary]/[StringLibrary*]。</span><span class="sxs-lookup"><span data-stu-id="851c2-133">In **Explorer**, open *StringLibrary/StringLibrary.csproj*.</span></span>

   <span data-ttu-id="851c2-134">`TargetFramework`元素會顯示專案的目標為 .net 5.0。</span><span class="sxs-lookup"><span data-stu-id="851c2-134">The `TargetFramework` element shows that the project targets .NET 5.0.</span></span>

   ```xml
   <Project Sdk="Microsoft.NET.Sdk">

     <PropertyGroup>
       <TargetFramework>net5.0</TargetFramework>
     </PropertyGroup>

   </Project>
   ```

1. <span data-ttu-id="851c2-135">開啟 *Class1.cs* ，並將程式碼取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="851c2-135">Open *Class1.cs* and replace the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/StringLibrary/Class1.cs":::

   <span data-ttu-id="851c2-136">類別庫（class library） `UtilityLibraries.StringLibrary` 包含名為的方法 `StartsWithUpper` 。</span><span class="sxs-lookup"><span data-stu-id="851c2-136">The class library, `UtilityLibraries.StringLibrary`, contains a method named `StartsWithUpper`.</span></span> <span data-ttu-id="851c2-137">這個方法會傳回 <xref:System.Boolean> 值，指出目前字串實例的開頭是否為大寫字元。</span><span class="sxs-lookup"><span data-stu-id="851c2-137">This method returns a <xref:System.Boolean> value that indicates whether the current string instance begins with an uppercase character.</span></span> <span data-ttu-id="851c2-138">Unicode 標準會區別大寫和小寫字元。</span><span class="sxs-lookup"><span data-stu-id="851c2-138">The Unicode standard distinguishes uppercase characters from lowercase characters.</span></span> <span data-ttu-id="851c2-139">如果是大寫字元，<xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> 方法會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="851c2-139">The <xref:System.Char.IsUpper(System.Char)?displayProperty=nameWithType> method returns `true` if a character is uppercase.</span></span>

1. <span data-ttu-id="851c2-140">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="851c2-140">Save the file.</span></span>

1. <span data-ttu-id="851c2-141">執行下列命令以建立方案，並確認專案編譯時沒有錯誤。</span><span class="sxs-lookup"><span data-stu-id="851c2-141">Run the following command to build the solution and verify that the project compiles without error.</span></span>

   ```dotnetcli
   dotnet build
   ```

   <span data-ttu-id="851c2-142">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="851c2-142">The terminal output looks like the following example:</span></span>

   ```output
   Microsoft (R) Build Engine version 16.7.0+b89cb5fde for .NET
   Copyright (C) Microsoft Corporation. All rights reserved.
     Determining projects to restore...
     All projects are up-to-date for restore.
     StringLibrary -> C:\Projects\ClassLibraryProjects\StringLibrary\bin\Debug\net5.0\StringLibrary.dll
   Build succeeded.
       0 Warning(s)
       0 Error(s)
   Time Elapsed 00:00:02.78
   ```

## <a name="add-a-console-app-to-the-solution"></a><span data-ttu-id="851c2-143">將主控台應用程式新增至解決方案</span><span class="sxs-lookup"><span data-stu-id="851c2-143">Add a console app to the solution</span></span>

<span data-ttu-id="851c2-144">加入使用類別庫的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="851c2-144">Add a console application that uses the class library.</span></span> <span data-ttu-id="851c2-145">應用程式會提示使用者輸入字串，並報告字串是否以大寫字元開頭。</span><span class="sxs-lookup"><span data-stu-id="851c2-145">The app will prompt the user to enter a string and report whether the string begins with an uppercase character.</span></span>

1. <span data-ttu-id="851c2-146">在終端機中執行下列命令，以建立主控台應用程式專案：</span><span class="sxs-lookup"><span data-stu-id="851c2-146">In the terminal, run the following command to create the console app project:</span></span>

   ```dotnetcli
   dotnet new console -o ShowCase
   ```

   <span data-ttu-id="851c2-147">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="851c2-147">The terminal output looks like the following example:</span></span>

   ```output
   The template "Console Application" was created successfully.
   Processing post-creation actions...
   Running 'dotnet restore' on ShowCase\ShowCase.csproj...  
     Determining projects to restore...
     Restored C:\Projects\ClassLibraryProjects\ShowCase\ShowCase.csproj (in 210 ms).
   Restore succeeded.
   ```

1. <span data-ttu-id="851c2-148">執行下列命令，以將主控台應用程式專案新增至方案：</span><span class="sxs-lookup"><span data-stu-id="851c2-148">Run the following command to add the console app project to the solution:</span></span>

   ```dotnetcli
   dotnet sln add ShowCase/ShowCase.csproj
   ```

   <span data-ttu-id="851c2-149">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="851c2-149">The terminal output looks like the following example:</span></span>

   ```output
   Project `ShowCase\ShowCase.csproj` added to the solution.
   ```

1. <span data-ttu-id="851c2-150">開啟 [ *展示]/[Program* ]，並將所有程式碼取代為下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="851c2-150">Open *ShowCase/Program.cs* and replace all of the code with the following code.</span></span>

   :::code language="csharp" source="./snippets/library-with-visual-studio/csharp/ShowCase/Program.cs":::

   <span data-ttu-id="851c2-151">該程式碼會使用 `row` 變數來維護寫入至主控台視窗的資料列數目計數。</span><span class="sxs-lookup"><span data-stu-id="851c2-151">The code uses the `row` variable to maintain a count of the number of rows of data written to the console window.</span></span> <span data-ttu-id="851c2-152">只要超過或等於25，程式碼就會清除主控台視窗，並向使用者顯示訊息。</span><span class="sxs-lookup"><span data-stu-id="851c2-152">Whenever it's greater than or equal to 25, the code clears the console window and displays a message to the user.</span></span>

   <span data-ttu-id="851c2-153">此程式會提示使用者輸入字串。</span><span class="sxs-lookup"><span data-stu-id="851c2-153">The program prompts the user to enter a string.</span></span> <span data-ttu-id="851c2-154">它會指出該字串開頭是否為大寫字元。</span><span class="sxs-lookup"><span data-stu-id="851c2-154">It indicates whether the string starts with an uppercase character.</span></span> <span data-ttu-id="851c2-155">如果使用者按下 <kbd>Enter</kbd> 鍵但未輸入字串，則應用程式會結束，且主控台視窗會關閉。</span><span class="sxs-lookup"><span data-stu-id="851c2-155">If the user presses the <kbd>Enter</kbd> key without entering a string, the application ends, and the console window closes.</span></span>

1. <span data-ttu-id="851c2-156">儲存您的變更。</span><span class="sxs-lookup"><span data-stu-id="851c2-156">Save your changes.</span></span>

## <a name="add-a-project-reference"></a><span data-ttu-id="851c2-157">新增專案參考</span><span class="sxs-lookup"><span data-stu-id="851c2-157">Add a project reference</span></span>

<span data-ttu-id="851c2-158">一開始，新的主控台應用程式專案沒有類別庫的存取權。</span><span class="sxs-lookup"><span data-stu-id="851c2-158">Initially, the new console app project doesn't have access to the class library.</span></span> <span data-ttu-id="851c2-159">若要允許它呼叫類別庫中的方法，請建立類別庫專案的專案參考。</span><span class="sxs-lookup"><span data-stu-id="851c2-159">To allow it to call methods in the class library, create a project reference to the class library project.</span></span>

1. <span data-ttu-id="851c2-160">執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="851c2-160">Run the following command:</span></span>

   ```dotnetcli
   dotnet add ShowCase/ShowCase.csproj reference StringLibrary/StringLibrary.csproj
   ```

   <span data-ttu-id="851c2-161">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="851c2-161">The terminal output looks like the following example:</span></span>

   ```output
   Reference `..\StringLibrary\StringLibrary.csproj` added to the project.
   ```

## <a name="run-the-app"></a><span data-ttu-id="851c2-162">執行應用程式</span><span class="sxs-lookup"><span data-stu-id="851c2-162">Run the app</span></span>

1. <span data-ttu-id="851c2-163">在終端中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="851c2-163">Run the following command in the terminal:</span></span>

   ```dotnetcli
   dotnet run --project ShowCase/ShowCase.csproj
   ```

1. <span data-ttu-id="851c2-164">輸入字串並按 <kbd>enter</kbd>鍵以嘗試程式，然後按 <kbd>enter</kbd> 鍵結束。</span><span class="sxs-lookup"><span data-stu-id="851c2-164">Try out the program by entering strings and pressing <kbd>Enter</kbd>, then press <kbd>Enter</kbd> to exit.</span></span>

   <span data-ttu-id="851c2-165">終端機輸出如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="851c2-165">The terminal output looks like the following example:</span></span>

   ```output
   Press <Enter> only to exit; otherwise, enter a string and press <Enter>:

   A string that starts with an uppercase letter
   Input: A string that starts with an uppercase letter
   Begins with uppercase? : Yes

   a string that starts with a lowercase letter
   Input: a string that starts with a lowercase letter
   Begins with uppercase? : No
   ```

## <a name="additional-resources"></a><span data-ttu-id="851c2-166">其他資源</span><span class="sxs-lookup"><span data-stu-id="851c2-166">Additional resources</span></span>

* [<span data-ttu-id="851c2-167">使用 .NET CLI 開發程式庫</span><span class="sxs-lookup"><span data-stu-id="851c2-167">Develop libraries with the .NET CLI</span></span>](libraries.md)
* <span data-ttu-id="851c2-168">[.NET Standard 支援的版本和平臺](../../standard/net-standard.md)。</span><span class="sxs-lookup"><span data-stu-id="851c2-168">[.NET Standard versions and the platforms they support](../../standard/net-standard.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="851c2-169">後續步驟</span><span class="sxs-lookup"><span data-stu-id="851c2-169">Next steps</span></span>

<span data-ttu-id="851c2-170">在本教學課程中，您已建立解決方案、新增程式庫專案，並加入使用該程式庫的主控台應用程式專案。</span><span class="sxs-lookup"><span data-stu-id="851c2-170">In this tutorial, you created a solution, added a library project, and added a console app project that uses the library.</span></span> <span data-ttu-id="851c2-171">在下一個教學課程中，您會將單元測試專案加入至方案。</span><span class="sxs-lookup"><span data-stu-id="851c2-171">In the next tutorial, you add a unit test project to the solution.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="851c2-172">使用 Visual Studio Code 以 .NET 測試 .NET 類別庫</span><span class="sxs-lookup"><span data-stu-id="851c2-172">Test a .NET class library with .NET using Visual Studio Code</span></span>](testing-library-with-visual-studio-code.md)
