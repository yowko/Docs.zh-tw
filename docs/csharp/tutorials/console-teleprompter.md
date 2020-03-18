---
title: 主控台應用程式
description: 本教學課程會教導您一些 .NET Core 和 C# 語言中的功能。
ms.date: 03/06/2017
ms.technology: csharp-fundamentals
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 09ce36e7a61f576dc4449976ce676701dc57c9cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "76921126"
---
# <a name="console-app"></a><span data-ttu-id="1ed1c-103">主控台應用</span><span class="sxs-lookup"><span data-stu-id="1ed1c-103">Console app</span></span>

<span data-ttu-id="1ed1c-104">本教學課程會教導您一些 .NET Core 和 C# 語言中的功能。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="1ed1c-105">您將了解：</span><span class="sxs-lookup"><span data-stu-id="1ed1c-105">You'll learn:</span></span>

- <span data-ttu-id="1ed1c-106">.NET 核心 CLI 的基礎知識</span><span class="sxs-lookup"><span data-stu-id="1ed1c-106">The basics of the .NET Core CLI</span></span>
- <span data-ttu-id="1ed1c-107">「C# 主控台應用程式」的結構</span><span class="sxs-lookup"><span data-stu-id="1ed1c-107">The structure of a C# Console Application</span></span>
- <span data-ttu-id="1ed1c-108">主控台 I/O</span><span class="sxs-lookup"><span data-stu-id="1ed1c-108">Console I/O</span></span>
- <span data-ttu-id="1ed1c-109">.NET 中檔案 I/O API 的基本概念</span><span class="sxs-lookup"><span data-stu-id="1ed1c-109">The basics of File I/O APIs in .NET</span></span>
- <span data-ttu-id="1ed1c-110">.NET 中以工作為基礎的非同步程式設計的基本概念</span><span class="sxs-lookup"><span data-stu-id="1ed1c-110">The basics of the Task-based Asynchronous Programming in .NET</span></span>

<span data-ttu-id="1ed1c-111">您將構建一個應用程式，該應用程式讀取文字檔，並將該文字檔的內容回顯到主控台。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-111">You'll build an application that reads a text file, and echoes the contents of that text file to the console.</span></span> <span data-ttu-id="1ed1c-112">對主控台之輸出的步調會符合可大聲朗讀它的步調。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-112">The output to the console is paced to match reading it aloud.</span></span> <span data-ttu-id="1ed1c-113">您可以通過按"<"（小於）或">"（大於）鍵來加快或減慢速度。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-113">You can speed up or slow down the pace by pressing the '<' (less than) or '>' (greater than) keys.</span></span>

<span data-ttu-id="1ed1c-114">本教學課程中有許多功能。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-114">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="1ed1c-115">讓我們逐個構建它們。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-115">Let's build them one by one.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1ed1c-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="1ed1c-116">Prerequisites</span></span>

- <span data-ttu-id="1ed1c-117">將電腦設置為運行 .NET 核心。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-117">Set up your machine to run .NET Core.</span></span> <span data-ttu-id="1ed1c-118">您可以在[.NET Core 下載](https://dotnet.microsoft.com/download)頁面上找到安裝說明。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-118">You can find the installation instructions on the [.NET Core downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="1ed1c-119">您可以在 Windows、Linux、macOS 或 Docker 容器中運行此應用程式。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-119">You can run this application on Windows, Linux, macOS, or in a Docker container.</span></span>

- <span data-ttu-id="1ed1c-120">安裝您最喜愛的代碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-120">Install your favorite code editor.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="1ed1c-121">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="1ed1c-121">Create the app</span></span>

<span data-ttu-id="1ed1c-122">第一個步驟是建立新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-122">The first step is to create a new application.</span></span> <span data-ttu-id="1ed1c-123">請開啟命令提示字元，然後為您的應用程式建立新目錄。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-123">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="1ed1c-124">使該目錄成為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-124">Make that the current directory.</span></span> <span data-ttu-id="1ed1c-125">在命令提示字元處輸入命令 `dotnet new console`。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-125">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="1ed1c-126">這會建立基本 "Hello World" 應用程式的起始檔案。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-126">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="1ed1c-127">在開始修改之前，讓我們完成運行簡單 Hello World 應用程式的步驟。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-127">Before you start making modifications, let's go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="1ed1c-128">在建立應用程式之後，請在命令提示字元處輸入 `dotnet restore`。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-128">After creating the application, type `dotnet restore` at the command prompt.</span></span> <span data-ttu-id="1ed1c-129">此命令會執行 NuGet 套件還原程序。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-129">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="1ed1c-130">NuGet 是一個 .NET 套件管理員。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-130">NuGet is a .NET package manager.</span></span> <span data-ttu-id="1ed1c-131">此命令會為您的專案下載任何遺漏的相依性。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-131">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="1ed1c-132">由於這是一個新專案，因此沒有任何現有的相依性，所以第一次執行時將會下載 .NET Core 架構。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-132">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="1ed1c-133">在這個初始步驟之後，當您新增新的相依套件或更新任何相依性的版本時，將只需要執行 `dotnet restore`。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-133">After this initial step, you will only need to run `dotnet restore` when you add new dependent packages, or update the versions of any of your dependencies.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="1ed1c-134">還原套件之後，您需執行 `dotnet build`。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-134">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="1ed1c-135">這會執行建置引擎並建立您的應用程式可執行檔。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-135">This executes the build engine and creates your application executable.</span></span> <span data-ttu-id="1ed1c-136">最後，您需執行 `dotnet run` 來執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-136">Finally, you execute `dotnet run` to run your application.</span></span>

<span data-ttu-id="1ed1c-137">簡單的 Hello World 應用程式程式碼全部都在 Program.cs 中。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-137">The simple Hello World application code is all in Program.cs.</span></span> <span data-ttu-id="1ed1c-138">請使用您慣用的文字編輯器來開啟該檔案。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-138">Open that file with your favorite text editor.</span></span> <span data-ttu-id="1ed1c-139">我們即將做出第一次改變。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-139">We're about to make our first changes.</span></span> <span data-ttu-id="1ed1c-140">在該檔案的開頭，您會看到 using 陳述式：</span><span class="sxs-lookup"><span data-stu-id="1ed1c-140">At the top of the file, see a using statement:</span></span>

```csharp
using System;
```

<span data-ttu-id="1ed1c-141">此陳述式會告訴編譯器任何來自 `System` 命名空間的型別都在範圍內。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-141">This statement tells the compiler that any types from the `System` namespace are in scope.</span></span> <span data-ttu-id="1ed1c-142">與您可能已使用的其他「物件導向」語言相同，C# 也使用命名空間來組織型別。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-142">Like other Object Oriented languages you may have used, C# uses namespaces to organize types.</span></span> <span data-ttu-id="1ed1c-143">這個 Hello World 程式並無不同。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-143">This Hello World program is no different.</span></span> <span data-ttu-id="1ed1c-144">您可以看到命名空間中所包含的程式，而命名空間的名稱是根據目前目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-144">You can see that the program is enclosed in the namespace with the name based on the name of the current directory.</span></span> <span data-ttu-id="1ed1c-145">在本教學課程中，將命名空間的名稱變更為 `TeleprompterConsole`：</span><span class="sxs-lookup"><span data-stu-id="1ed1c-145">For this tutorial, let's change the name of the namespace to `TeleprompterConsole`:</span></span>

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a><span data-ttu-id="1ed1c-146">讀取及回應檔案</span><span class="sxs-lookup"><span data-stu-id="1ed1c-146">Reading and Echoing the File</span></span>

<span data-ttu-id="1ed1c-147">要新增的第一個功能是能夠讀取文字檔，並對主控台顯示該全部文字。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-147">The first feature to add is the ability to read a text file and display all that text to the console.</span></span> <span data-ttu-id="1ed1c-148">首先，讓我們添加一個文字檔。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-148">First, let's add a text file.</span></span> <span data-ttu-id="1ed1c-149">請從 GitHub 儲存機制將此[範例](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter)的 [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) 檔案複製到您的專案目錄中。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-149">Copy the [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) file from the GitHub repository for this [sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) into your project directory.</span></span> <span data-ttu-id="1ed1c-150">這將作為您應用程式的指令碼。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-150">This will serve as the script for your application.</span></span> <span data-ttu-id="1ed1c-151">如果您想要如何下載本主題之範例應用程式的資訊，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)主題中的指示。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-151">If you would like information on how to download the sample app for this topic, see the instructions in the [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) topic.</span></span>

<span data-ttu-id="1ed1c-152">接著，在您的 `Program` 類別 (就在 `Main` 方法下方) 中新增下列方法：</span><span class="sxs-lookup"><span data-stu-id="1ed1c-152">Next, add the following method in your `Program` class (right below the `Main` method):</span></span>

```csharp
static IEnumerable<string> ReadFrom(string file)
{
    string line;
    using (var reader = File.OpenText(file))
    {
        while ((line = reader.ReadLine()) != null)
        {
            yield return line;
        }
    }
}
```

<span data-ttu-id="1ed1c-153">此方法會使用來自兩個新命名空間的型別。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-153">This method uses types from two new namespaces.</span></span> <span data-ttu-id="1ed1c-154">要編譯此，您需要將以下兩行添加到檔頂部：</span><span class="sxs-lookup"><span data-stu-id="1ed1c-154">For this to compile you'll need to add the following two lines to the top of the file:</span></span>

```csharp
using System.Collections.Generic;
using System.IO;
```

<span data-ttu-id="1ed1c-155"><xref:System.Collections.Generic.IEnumerable%601> 介面是在 <xref:System.Collections.Generic> 命名空間中定義。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-155">The <xref:System.Collections.Generic.IEnumerable%601> interface is defined in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="1ed1c-156"><xref:System.IO.File> 類別是在 <xref:System.IO> 命名空間中定義。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-156">The <xref:System.IO.File> class is defined in the <xref:System.IO> namespace.</span></span>

<span data-ttu-id="1ed1c-157">此方法是 C# 方法的特殊型別，稱為「Iterator 方法」\*\*。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-157">This method is a special type of C# method called an *Iterator method*.</span></span> <span data-ttu-id="1ed1c-158">列舉程式方法會傳回延遲評估的序列。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-158">Enumerator methods return sequences that are evaluated lazily.</span></span> <span data-ttu-id="1ed1c-159">這意謂著序列中的每個項目會在取用序列的程式碼要求該項目時產生。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-159">That means each item in the sequence is generated as it is requested by the code consuming the sequence.</span></span> <span data-ttu-id="1ed1c-160">枚舉器方法是包含一個或多個[`yield return`](../language-reference/keywords/yield.md)語句的方法。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-160">Enumerator methods are methods that contain one or more [`yield return`](../language-reference/keywords/yield.md) statements.</span></span> <span data-ttu-id="1ed1c-161">`ReadFrom` 方法所傳回的物件包含用來產生序列中每個項目的程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-161">The object returned by the `ReadFrom` method contains the code to generate each item in the sequence.</span></span> <span data-ttu-id="1ed1c-162">在此範例中，這牽涉到從原始程式檔讀取下一行文字，並傳回該字串。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-162">In this example, that involves reading the next line of text from the source file, and returning that string.</span></span> <span data-ttu-id="1ed1c-163">每次呼叫程式碼要求序列中的下一個項目時，程式碼都會從檔案讀取下一行文字，並傳回該文字。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-163">Each time the calling code requests the next item from the sequence, the code reads the next line of text from the file and returns it.</span></span> <span data-ttu-id="1ed1c-164">完全讀取檔案後，序列會指出已沒有任何其他項目。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-164">When the file is completely read, the sequence indicates that there are no more items.</span></span>

<span data-ttu-id="1ed1c-165">有兩個其他 C# 語法元素可能是您不熟悉的。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-165">There are two other C# syntax elements that may be new to you.</span></span> <span data-ttu-id="1ed1c-166">此方法[`using`](../language-reference/keywords/using-statement.md)中的語句管理資源清理。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-166">The [`using`](../language-reference/keywords/using-statement.md) statement in this method manages resource cleanup.</span></span> <span data-ttu-id="1ed1c-167">在 `using` 陳述式中初始化的變數 (在此範例中為 `reader`) 必須實作 <xref:System.IDisposable> 介面。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-167">The variable that is initialized in the `using` statement (`reader`, in this example) must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="1ed1c-168">該介面會定義單一方法 `Dispose`，而在應該釋出資源時應該呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-168">That interface defines a single method, `Dispose`, that should be called when the resource should be released.</span></span> <span data-ttu-id="1ed1c-169">編譯器會在執行到達 `using` 陳述式的結尾大括號時產生該呼叫。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-169">The compiler generates that call when execution reaches the closing brace of the `using` statement.</span></span> <span data-ttu-id="1ed1c-170">編譯器產生的程式碼會確保即使 using 陳述式所定義區塊中的程式碼擲回例外狀況，也會釋出資源。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-170">The compiler-generated code ensures that the resource is released even if an exception is thrown from the code in the block defined by the using statement.</span></span>

<span data-ttu-id="1ed1c-171">定義 `reader` 變數時，是使用 `var` 關鍵字來定義。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-171">The `reader` variable is defined using the `var` keyword.</span></span> <span data-ttu-id="1ed1c-172">[`var`](../language-reference/keywords/var.md)定義*隱式類型區域變數*。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-172">[`var`](../language-reference/keywords/var.md) defines an *implicitly typed local variable*.</span></span> <span data-ttu-id="1ed1c-173">這意謂著變數的型別取決於指派給該變數之物件的編譯階段型別。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-173">That means the type of the variable is determined by the compile-time type of the object assigned to the variable.</span></span> <span data-ttu-id="1ed1c-174">在這裡，這是來自 <xref:System.IO.File.OpenText(System.String)> 方法的傳回值，是一個 <xref:System.IO.StreamReader> 物件。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-174">Here, that is the return value from the <xref:System.IO.File.OpenText(System.String)> method, which is a <xref:System.IO.StreamReader> object.</span></span>

<span data-ttu-id="1ed1c-175">現在，讓我們填寫代碼以讀取`Main`方法中的檔：</span><span class="sxs-lookup"><span data-stu-id="1ed1c-175">Now, let's fill in the code to read the file in the `Main` method:</span></span>

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

<span data-ttu-id="1ed1c-176">請執行程式 (使用 `dotnet run`)，然後您便可以看到每一行顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-176">Run the program (using `dotnet run`) and you can see every line printed out to the console.</span></span>

## <a name="adding-delays-and-formatting-output"></a><span data-ttu-id="1ed1c-177">新增延遲及設定輸出格式</span><span class="sxs-lookup"><span data-stu-id="1ed1c-177">Adding Delays and Formatting output</span></span>

<span data-ttu-id="1ed1c-178">您的內容顯示速度太快，無法大聲朗讀。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-178">What you have is being displayed far too fast to read aloud.</span></span> <span data-ttu-id="1ed1c-179">現在您必須在輸出中新增延遲。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-179">Now you need to add the delays in the output.</span></span> <span data-ttu-id="1ed1c-180">開始，您將構建一些支援非同步處理的核心代碼。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-180">As you start, you'll be building some of the core code that enables asynchronous processing.</span></span> <span data-ttu-id="1ed1c-181">不過，這些開頭的步驟會依循一些反模式。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-181">However, these first steps will follow a few anti-patterns.</span></span> <span data-ttu-id="1ed1c-182">在您新增程式碼時，註解中會指出這些反模式，然後在稍後的步驟中將會更新此程式碼。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-182">The anti-patterns are pointed out in comments as you add the code, and the code will be updated in later steps.</span></span>

<span data-ttu-id="1ed1c-183">這個部分有兩個步驟。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-183">There are two steps to this section.</span></span> <span data-ttu-id="1ed1c-184">首先，您將更新反覆運算器方法以返回單個單詞而不是整行。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-184">First, you'll update the iterator method to return single words instead of entire lines.</span></span> <span data-ttu-id="1ed1c-185">這些修改就完成了。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-185">That's done with these modifications.</span></span> <span data-ttu-id="1ed1c-186">請以下列程式碼取代 `yield return line;` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="1ed1c-186">Replace the `yield return line;` statement with the following code:</span></span>

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

<span data-ttu-id="1ed1c-187">接著，您必須修改取用檔案行的方式，然後在寫入每個字之後新增延遲。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-187">Next, you need to modify how you consume the lines of the file, and add a delay after writing each word.</span></span> <span data-ttu-id="1ed1c-188">請以下列區塊取代 `Main` 方法中的 `Console.WriteLine(line)` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="1ed1c-188">Replace the `Console.WriteLine(line)` statement in the `Main` method with the following block:</span></span>

```csharp
Console.Write(line);
if (!string.IsNullOrWhiteSpace(line))
{
    var pause = Task.Delay(200);
    // Synchronously waiting on a task is an
    // anti-pattern. This will get fixed in later
    // steps.
    pause.Wait();
}
```

<span data-ttu-id="1ed1c-189"><xref:System.Threading.Tasks.Task> 類別是在 <xref:System.Threading.Tasks> 命名空間中，因此您必須在檔案開頭新增該 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="1ed1c-189">The <xref:System.Threading.Tasks.Task> class is in the <xref:System.Threading.Tasks> namespace, so you need to add that `using` statement at the top of file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="1ed1c-190">請執行範例並檢查輸出。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-190">Run the sample, and check the output.</span></span> <span data-ttu-id="1ed1c-191">現在會顯示每個單字，後面接著 200 毫秒的延遲。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-191">Now, each single word is printed, followed by a 200 ms delay.</span></span> <span data-ttu-id="1ed1c-192">不過，顯示的輸出出現一些問題，因為來源文字檔有數行超過 80 個字元且沒有分行符號。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-192">However, the displayed output shows some issues because the source text file has several lines that have more than 80 characters without a line break.</span></span> <span data-ttu-id="1ed1c-193">這在捲動時會相當難以閱讀。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-193">That can be hard to read while it's scrolling by.</span></span> <span data-ttu-id="1ed1c-194">這很容易修復。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-194">That's easy to fix.</span></span> <span data-ttu-id="1ed1c-195">您將只跟蹤每行的長度，並在直線長度達到特定閾值時生成新線。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-195">You'll just keep track of the length of each line, and generate a new line whenever the line length reaches a certain threshold.</span></span> <span data-ttu-id="1ed1c-196">請在保存行長度的 `ReadFrom` 方法中 `words` 的宣告之後宣告區域變數：</span><span class="sxs-lookup"><span data-stu-id="1ed1c-196">Declare a local variable after the declaration of `words` in the `ReadFrom` method that holds the line length:</span></span>

```csharp
var lineLength = 0;
```

<span data-ttu-id="1ed1c-197">接著，在 `yield return word + " ";` 陳述式之後 (在結尾大括號之前) 新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="1ed1c-197">Then, add the following code after the `yield return word + " ";` statement (before the closing brace):</span></span>

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

<span data-ttu-id="1ed1c-198">運行示例，您將能夠按照預配置的速度大聲朗讀。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-198">Run the sample, and you'll be able to read aloud at its pre-configured pace.</span></span>

## <a name="async-tasks"></a><span data-ttu-id="1ed1c-199">非同步工作</span><span class="sxs-lookup"><span data-stu-id="1ed1c-199">Async Tasks</span></span>

<span data-ttu-id="1ed1c-200">在最後一步中，您將添加代碼以非同步方式在一個任務中寫入輸出，同時運行另一個任務，以讀取使用者輸入（如果使用者想要加快或減慢文本顯示速度，或完全停止文本顯示）。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-200">In this final step, you'll add the code to write the output asynchronously in one task, while also running another task to read input from the user if they want to speed up or slow down the text display, or stop the text display altogether.</span></span> <span data-ttu-id="1ed1c-201">這有幾個步驟，到最後，您將擁有所需的所有更新。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-201">This has a few steps in it and by the end, you'll have all the updates that you need.</span></span> <span data-ttu-id="1ed1c-202">第一步是創建一個非同步<xref:System.Threading.Tasks.Task>返回方法，該方法表示到目前為止為讀取和顯示檔而創建的代碼。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-202">The first step is to create an asynchronous <xref:System.Threading.Tasks.Task> returning method that represents the code you've created so far to read and display the file.</span></span>

<span data-ttu-id="1ed1c-203">將此方法添加到類`Program`（取自方法`Main`正文）：</span><span class="sxs-lookup"><span data-stu-id="1ed1c-203">Add this method to your `Program` class (it's taken from the body of your `Main` method):</span></span>

```csharp
private static async Task ShowTeleprompter()
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(200);
        }
    }
}
```

<span data-ttu-id="1ed1c-204">您會注意到兩個更改。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-204">You'll notice two changes.</span></span> <span data-ttu-id="1ed1c-205">首先，在方法的主體中，此版本使用 `await` 關鍵字，而不是呼叫 <xref:System.Threading.Tasks.Task.Wait> 來同步等候工作完成。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-205">First, in the body of the method, instead of calling <xref:System.Threading.Tasks.Task.Wait> to synchronously wait for a task to finish, this version uses the `await` keyword.</span></span> <span data-ttu-id="1ed1c-206">為了這麼做，您必須將 `async` 修飾詞新增到方法簽章。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-206">In order to do that, you need to add the `async` modifier to the method signature.</span></span> <span data-ttu-id="1ed1c-207">此方法會傳回 `Task`。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-207">This method returns a `Task`.</span></span> <span data-ttu-id="1ed1c-208">請注意，並沒有會傳回 `Task` 物件的傳回陳述式。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-208">Notice that there are no return statements that return a `Task` object.</span></span> <span data-ttu-id="1ed1c-209">取而代之的是，會由編譯器在您使用 `await` 運算子時產生的程式碼建立 `Task` 物件。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-209">Instead, that `Task` object is created by code the compiler generates when you use the `await` operator.</span></span> <span data-ttu-id="1ed1c-210">您可以想像這個方法會在到達 `await` 時返回。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-210">You can imagine that this method returns when it reaches an `await`.</span></span> <span data-ttu-id="1ed1c-211">傳回的 `Task` 指出工作尚未完成。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-211">The returned `Task` indicates that the work has not completed.</span></span> <span data-ttu-id="1ed1c-212">方法會在所等候的工作完成時繼續執行。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-212">The method resumes when the awaited task completes.</span></span> <span data-ttu-id="1ed1c-213">當它執行到完成時，傳回的 `Task` 會指出它已完成。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-213">When it has executed to completion, the returned `Task` indicates that it is complete.</span></span>
<span data-ttu-id="1ed1c-214">呼叫程式碼可以監視傳回的 `Task` 以判斷它何時完成。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-214">Calling code can monitor that returned `Task` to determine when it has completed.</span></span>

<span data-ttu-id="1ed1c-215">您可以在 `Main` 方法中呼叫這個新方法：</span><span class="sxs-lookup"><span data-stu-id="1ed1c-215">You can call this new method in your `Main` method:</span></span>

```csharp
ShowTeleprompter().Wait();
```

<span data-ttu-id="1ed1c-216">在這裡，`Main` 中的程式碼會執行同步等候。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-216">Here, in `Main`, the code does synchronously wait.</span></span> <span data-ttu-id="1ed1c-217">您應該儘可能使用 `await` 運算子而不是同步等候。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-217">You should use the `await` operator instead of synchronously waiting whenever possible.</span></span> <span data-ttu-id="1ed1c-218">但是，在主控台應用程式`Main`的方法中，不能使用`await`運算子。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-218">But, in a console application's `Main` method, you cannot use the `await` operator.</span></span> <span data-ttu-id="1ed1c-219">那會導致應用程式在所有工作完成之前即結束。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-219">That would result in the application exiting before all tasks have completed.</span></span>

> [!NOTE]
> <span data-ttu-id="1ed1c-220">如果您使用 C# 7.1 或更新版本，則可以使用 [`async` `Main` 方法](../whats-new/csharp-7-1.md#async-main)建立主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-220">If you use C# 7.1 or later, you can create console applications with [`async` `Main` method](../whats-new/csharp-7-1.md#async-main).</span></span>

<span data-ttu-id="1ed1c-221">接下來，您需要編寫第二個非同步方法，以便從主控台讀取，並監視"<"（小於）、">"（大於）和"X"或"x"鍵。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-221">Next, you need to write the second asynchronous method to read from the Console and watch for the '<' (less than), '>' (greater than) and 'X' or 'x' keys.</span></span> <span data-ttu-id="1ed1c-222">以下是為該任務添加的方法：</span><span class="sxs-lookup"><span data-stu-id="1ed1c-222">Here's the method you add for that task:</span></span>

```csharp
private static async Task GetInput()
{
    var delay = 200;
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
            {
                delay -= 10;
            }
            else if (key.KeyChar == '<')
            {
                delay += 10;
            }
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
            {
                break;
            }
        } while (true);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="1ed1c-223">這將創建一個 lambda 運算式<xref:System.Action>來表示從主控台讀取鍵的委託，並修改表示使用者按"<"（小於）或">"（大於）鍵時的延遲的區域變數。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-223">This creates a lambda expression to represent an <xref:System.Action> delegate that reads a key from the Console and modifies a local variable representing the delay when the user presses the '<' (less than) or '>' (greater than) keys.</span></span> <span data-ttu-id="1ed1c-224">當使用者按下"X"或"x"鍵時，委託方法將結束，這允許使用者隨時停止文本顯示。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-224">The delegate method finishes when user presses the 'X' or 'x'  keys, which allow the user to stop the text display at any time.</span></span> <span data-ttu-id="1ed1c-225">此方法會使用 <xref:System.Console.ReadKey> 來封鎖並等候使用者按下按鍵。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-225">This method uses <xref:System.Console.ReadKey> to block and wait for the user to press a key.</span></span>

<span data-ttu-id="1ed1c-226">若要完成此功能，您必須建立一個會傳回方法的新 `async Task`，該方法既會啟動這兩項工作 (`GetInput` 和 `ShowTeleprompter`)，也會管理這兩項工作之間的共用資料。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-226">To finish this feature, you need to create a new `async Task` returning method that starts both of these tasks (`GetInput` and `ShowTeleprompter`), and also manages the shared data between these two tasks.</span></span>

<span data-ttu-id="1ed1c-227">是時候創建一個類來處理這兩個任務之間的共用資料了。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-227">It's time to create a class that can handle the shared data between these two tasks.</span></span> <span data-ttu-id="1ed1c-228">此類別包含兩個公用屬性：延遲和一個指出已完全讀取檔案的 `Done` 旗標：</span><span class="sxs-lookup"><span data-stu-id="1ed1c-228">This class contains two public properties: the delay, and a flag `Done` to indicate that the file has been completely read:</span></span>

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            DelayInMilliseconds = newDelay;
        }

        public bool Done { get; private set; }

        public void SetDone()
        {
            Done = true;
        }
    }
}
```

<span data-ttu-id="1ed1c-229">請將該類別放在新檔案中，然後如以上所示，將該類別包含在 `TeleprompterConsole` 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-229">Put that class in a new file, and enclose that class in the `TeleprompterConsole` namespace as shown above.</span></span> <span data-ttu-id="1ed1c-230">您還需要添加一個`using static`語句，以便可以引用`Min`和`Max`方法，而無需封閉類或命名空間名稱。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-230">You'll also need to add a `using static` statement so that you can reference the `Min` and `Max` methods without the enclosing class or namespace names.</span></span> <span data-ttu-id="1ed1c-231">語句[`using static`](../language-reference/keywords/using-static.md)從一個類導入方法。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-231">A [`using static`](../language-reference/keywords/using-static.md) statement imports the methods from one class.</span></span> <span data-ttu-id="1ed1c-232">這與到目前為止所使用的 `using` 陳述式形成對比，該陳述式會從命名空間匯入所有類別。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-232">This is in contrast with the `using` statements used up to this point that have imported all classes from a namespace.</span></span>

```csharp
using static System.Math;
```

<span data-ttu-id="1ed1c-233">接著，您必須更新 `ShowTeleprompter` 和 `GetInput` 方法以使用新的 `config` 物件。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-233">Next, you need to update the `ShowTeleprompter` and `GetInput` methods to use the new `config` object.</span></span> <span data-ttu-id="1ed1c-234">請撰寫一個最後的 `Task` 來傳回 `async` 方法，以啟動兩項工作並在第一個工作完成時結束：</span><span class="sxs-lookup"><span data-stu-id="1ed1c-234">Write one final `Task` returning `async` method to start both tasks and exit when the first task finishes:</span></span>

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

<span data-ttu-id="1ed1c-235">這裡的新方法是 <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> 呼叫。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-235">The one new method here is the <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> call.</span></span> <span data-ttu-id="1ed1c-236">此方法會建立一個 `Task`，它會在其引數清單中的任何工作完成時便結束。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-236">That creates a `Task` that finishes as soon as any of the tasks in its argument list completes.</span></span>

<span data-ttu-id="1ed1c-237">接著，您必須更新 `ShowTeleprompter` 和 `GetInput` 方法以使用 `config` 物件來設定延遲：</span><span class="sxs-lookup"><span data-stu-id="1ed1c-237">Next, you need to update both the `ShowTeleprompter` and `GetInput` methods to use the `config` object for the delay:</span></span>

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(config.DelayInMilliseconds);
        }
    }
    config.SetDone();
}

private static async Task GetInput(TelePrompterConfig config)
{
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
                config.UpdateDelay(-10);
            else if (key.KeyChar == '<')
                config.UpdateDelay(10);
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
                config.SetDone();
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="1ed1c-238">這個新版本的 `ShowTeleprompter` 會呼叫 `TeleprompterConfig` 類別中的新方法。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-238">This new version of `ShowTeleprompter` calls a new method in the `TeleprompterConfig` class.</span></span> <span data-ttu-id="1ed1c-239">現在，您必須更新 `Main` 以呼叫 `RunTeleprompter` 而不是 `ShowTeleprompter`：</span><span class="sxs-lookup"><span data-stu-id="1ed1c-239">Now, you need to update `Main` to call `RunTeleprompter` instead of `ShowTeleprompter`:</span></span>

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a><span data-ttu-id="1ed1c-240">結論</span><span class="sxs-lookup"><span data-stu-id="1ed1c-240">Conclusion</span></span>

<span data-ttu-id="1ed1c-241">本教學課程示範一些與在主控台應用程式中工作有關的 C# 語言和 .NET Core 程式庫相關功能。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-241">This tutorial showed you a number of the features around the C# language and the .NET Core libraries related to working in Console applications.</span></span> <span data-ttu-id="1ed1c-242">您可以利用這項知識作為基礎，進一步探索這裡介紹的語言和類別。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-242">You can build on this knowledge to explore more about the language, and the classes introduced here.</span></span> <span data-ttu-id="1ed1c-243">您已經看到了檔和主控台 I/O、基於任務的非同步程式設計的阻止和非阻止使用、C# 語言的教程以及 C# 程式的組織方式以及 .NET Core CLI。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-243">You've seen the basics of File and Console I/O, blocking and non-blocking use of the Task-based asynchronous programming, a tour of the C# language and how C# programs are organized, and the .NET Core CLI.</span></span>

<span data-ttu-id="1ed1c-244">如需檔案 I/O 的詳細資訊，請參閱[檔案和資料流 I/O](../../standard/io/index.md) 主題。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-244">For more information about File I/O, see the [File and Stream I/O](../../standard/io/index.md) topic.</span></span> <span data-ttu-id="1ed1c-245">如需本教學課程中所使用非同步程式設計模型的詳細資訊，請參閱[以工作為基礎的非同步程式設計](../..//standard/parallel-programming/task-based-asynchronous-programming.md)主題和[非同步程式設計](../async.md)主題。</span><span class="sxs-lookup"><span data-stu-id="1ed1c-245">For more information about asynchronous programming model used in this tutorial, see the [Task-based Asynchronous Programming](../..//standard/parallel-programming/task-based-asynchronous-programming.md) topic and the [Asynchronous programming](../async.md) topic.</span></span>
