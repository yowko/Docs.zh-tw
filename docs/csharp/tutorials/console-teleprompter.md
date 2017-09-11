---
title: "主控台應用程式"
description: "本教學課程會教導您一些 .NET Core 和 C# 語言中的功能。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.translationtype: Human Translation
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 360e93af03e00547116d1af1816c2b9b29524881
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---

# <a name="console-application"></a><span data-ttu-id="d8a46-104">主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="d8a46-104">Console Application</span></span>

## <a name="introduction"></a><span data-ttu-id="d8a46-105">簡介</span><span class="sxs-lookup"><span data-stu-id="d8a46-105">Introduction</span></span>
<span data-ttu-id="d8a46-106">本教學課程會教導您一些 .NET Core 和 C# 語言中的功能。</span><span class="sxs-lookup"><span data-stu-id="d8a46-106">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="d8a46-107">您將了解：</span><span class="sxs-lookup"><span data-stu-id="d8a46-107">You’ll learn:</span></span>
*   <span data-ttu-id="d8a46-108">「.NET Core 命令列介面」(CLI) 的基本概念</span><span class="sxs-lookup"><span data-stu-id="d8a46-108">The basics of the .NET Core Command Line Interface (CLI)</span></span>
*   <span data-ttu-id="d8a46-109">「C# 主控台應用程式」的結構</span><span class="sxs-lookup"><span data-stu-id="d8a46-109">The structure of a C# Console Application</span></span>
*   <span data-ttu-id="d8a46-110">主控台 I/O</span><span class="sxs-lookup"><span data-stu-id="d8a46-110">Console I/O</span></span>
*   <span data-ttu-id="d8a46-111">.NET Core 中「檔案 I/O API」的基本概念</span><span class="sxs-lookup"><span data-stu-id="d8a46-111">The basics of File I/O APIs in .NET Core</span></span>
*   <span data-ttu-id="d8a46-112">.NET Core 中「工作非同步程式設計模型」的基本概念</span><span class="sxs-lookup"><span data-stu-id="d8a46-112">The basics of the Task Asynchronous Programming Model in .NET Core</span></span>

<span data-ttu-id="d8a46-113">您將建置一個應用程式，此應用程式會讀取文字檔，並將該文字檔的內容回應至主控台。</span><span class="sxs-lookup"><span data-stu-id="d8a46-113">You’ll build an application that reads a text file, and echoes the contents of that text file to the console.</span></span> <span data-ttu-id="d8a46-114">對主控台之輸出的步調將會符合可大聲朗讀它的步調。</span><span class="sxs-lookup"><span data-stu-id="d8a46-114">The output to the console will be paced to match reading it aloud.</span></span> <span data-ttu-id="d8a46-115">您可以按 ‘<’ 或 ‘>’ 鍵來將該步調調快或調慢。</span><span class="sxs-lookup"><span data-stu-id="d8a46-115">You can speed up or slow down the pace by pressing the ‘<’ or ‘>’ keys.</span></span>

<span data-ttu-id="d8a46-116">本教學課程中有許多功能。</span><span class="sxs-lookup"><span data-stu-id="d8a46-116">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="d8a46-117">讓我們來逐一建置它們。</span><span class="sxs-lookup"><span data-stu-id="d8a46-117">Let’s build them one by one.</span></span> 
## <a name="prerequisites"></a><span data-ttu-id="d8a46-118">必要條件</span><span class="sxs-lookup"><span data-stu-id="d8a46-118">Prerequisites</span></span>
<span data-ttu-id="d8a46-119">您必須設定電腦以執行 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="d8a46-119">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="d8a46-120">您可以在 [.NET Core (英文)](https://www.microsoft.com/net/core) 頁面找到安裝指示。</span><span class="sxs-lookup"><span data-stu-id="d8a46-120">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="d8a46-121">您可以在 Windows、Linux、macOS 或是 Docker 容器中執行此應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8a46-121">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="d8a46-122">您將必須安裝慣用的程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="d8a46-122">You’ll need to install your favorite code editor.</span></span> 
## <a name="create-the-application"></a><span data-ttu-id="d8a46-123">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="d8a46-123">Create the Application</span></span>
<span data-ttu-id="d8a46-124">第一個步驟是建立新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8a46-124">The first step is to create a new application.</span></span> <span data-ttu-id="d8a46-125">請開啟命令提示字元，然後為您的應用程式建立新目錄。</span><span class="sxs-lookup"><span data-stu-id="d8a46-125">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="d8a46-126">使該目錄成為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="d8a46-126">Make that the current directory.</span></span> <span data-ttu-id="d8a46-127">在命令提示字元處輸入命令 `dotnet new console`。</span><span class="sxs-lookup"><span data-stu-id="d8a46-127">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="d8a46-128">這會建立基本 "Hello World" 應用程式的起始檔案。</span><span class="sxs-lookup"><span data-stu-id="d8a46-128">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="d8a46-129">在您開始進行修改之前，讓我們先將執行簡單 Hello World 應用程式的所有步驟執行一遍。</span><span class="sxs-lookup"><span data-stu-id="d8a46-129">Before you start making modifications, let’s go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="d8a46-130">在建立應用程式之後，請在命令提示字元處輸入 `dotnet restore`。</span><span class="sxs-lookup"><span data-stu-id="d8a46-130">After creating the application, type `dotnet restore` at the command prompt.</span></span> <span data-ttu-id="d8a46-131">此命令會執行 NuGet 套件還原程序。</span><span class="sxs-lookup"><span data-stu-id="d8a46-131">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="d8a46-132">NuGet 是一個 .NET 套件管理員。</span><span class="sxs-lookup"><span data-stu-id="d8a46-132">NuGet is a .NET package manager.</span></span> <span data-ttu-id="d8a46-133">此命令會為您的專案下載任何遺漏的相依性。</span><span class="sxs-lookup"><span data-stu-id="d8a46-133">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="d8a46-134">由於這是一個新專案，因此沒有任何現有的相依性，所以第一次執行時將會下載 .NET Core 架構。</span><span class="sxs-lookup"><span data-stu-id="d8a46-134">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="d8a46-135">在這個初始步驟之後，當您新增新的相依套件或更新任何相依性的版本時，將只需要執行 `dotnet restore`。</span><span class="sxs-lookup"><span data-stu-id="d8a46-135">After this initial step, you will only need to run `dotnet restore` when you add new dependent packages, or update the versions of any of your dependencies.</span></span> <span data-ttu-id="d8a46-136">此程序也會在您的專案目錄中建立專案鎖定檔 (project.lock.json)。</span><span class="sxs-lookup"><span data-stu-id="d8a46-136">This process also creates the project lock file (project.lock.json) in your project directory.</span></span> <span data-ttu-id="d8a46-137">此檔案可協助管理專案相依性。</span><span class="sxs-lookup"><span data-stu-id="d8a46-137">This file helps to manage the project dependencies.</span></span> <span data-ttu-id="d8a46-138">它包含所有專案相依性的本機位置。</span><span class="sxs-lookup"><span data-stu-id="d8a46-138">It contains the local location of all the project dependencies.</span></span> <span data-ttu-id="d8a46-139">您不需要將此檔案放在原始檔控制中；當您執行 `dotnet restore` 時，就會建立它。</span><span class="sxs-lookup"><span data-stu-id="d8a46-139">You do not need to put the file in source control; it will be generated when you run `dotnet restore`.</span></span> 

<span data-ttu-id="d8a46-140">還原套件之後，您需執行 `dotnet build`。</span><span class="sxs-lookup"><span data-stu-id="d8a46-140">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="d8a46-141">這會執行建置引擎並建立您的應用程式可執行檔。</span><span class="sxs-lookup"><span data-stu-id="d8a46-141">This executes the build engine and creates your application executable.</span></span> <span data-ttu-id="d8a46-142">最後，您需執行 `dotnet run` 來執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d8a46-142">Finally, you execute `dotnet run` to run your application.</span></span>  

<span data-ttu-id="d8a46-143">簡單的 Hello World 應用程式程式碼全部都在 Program.cs 中。</span><span class="sxs-lookup"><span data-stu-id="d8a46-143">The simple Hello World application code is all in Program.cs.</span></span> <span data-ttu-id="d8a46-144">請使用您慣用的文字編輯器來開啟該檔案。</span><span class="sxs-lookup"><span data-stu-id="d8a46-144">Open that file with your favorite text editor.</span></span> <span data-ttu-id="d8a46-145">我們即將進行我們的最初始變更。</span><span class="sxs-lookup"><span data-stu-id="d8a46-145">We’re about to make our first changes.</span></span>
<span data-ttu-id="d8a46-146">在該檔案的開頭，您會看到 using 陳述式：</span><span class="sxs-lookup"><span data-stu-id="d8a46-146">At the top of the file, see a using statement:</span></span>

```csharp
using System;
```

<span data-ttu-id="d8a46-147">此陳述式會告訴編譯器任何來自 `System` 命名空間的型別都在範圍內。</span><span class="sxs-lookup"><span data-stu-id="d8a46-147">This statement tells the compiler that any types from the `System` namespace are in scope.</span></span> <span data-ttu-id="d8a46-148">與您可能已使用的其他「物件導向」語言相同，C# 也使用命名空間來組織型別。</span><span class="sxs-lookup"><span data-stu-id="d8a46-148">Like other Object Oriented languages you may have used, C# uses namespaces to organize types.</span></span> <span data-ttu-id="d8a46-149">這個 Hello World 程式並無不同。</span><span class="sxs-lookup"><span data-stu-id="d8a46-149">This hello world program is no different.</span></span> <span data-ttu-id="d8a46-150">您可以看到此程式是包含在 `ConsoleApplication` 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="d8a46-150">You can see that the program is enclosed in the `ConsoleApplication` namespace.</span></span> <span data-ttu-id="d8a46-151">這不是一個非常具描述性的名稱，因此請將它變更為 `TeleprompterConsole`：</span><span class="sxs-lookup"><span data-stu-id="d8a46-151">That’s not a very descriptive name, so change it to `TeleprompterConsole`:</span></span>

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a><span data-ttu-id="d8a46-152">讀取及回應檔案</span><span class="sxs-lookup"><span data-stu-id="d8a46-152">Reading and Echoing the File</span></span>
<span data-ttu-id="d8a46-153">要新增的第一個功能是能夠讀取文字檔，並對主控台顯示該全部文字。</span><span class="sxs-lookup"><span data-stu-id="d8a46-153">The first feature to add is the ability to read a text file and display all that text to the console.</span></span> <span data-ttu-id="d8a46-154">首先，讓我們新增一個文字檔。</span><span class="sxs-lookup"><span data-stu-id="d8a46-154">First, let’s add a text file.</span></span> <span data-ttu-id="d8a46-155">請從 GitHub 儲存機制將此[範例](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-teleprompter)的 [sampleQuotes.txt](https://raw.githubusercontent.com/dotnet/docs/master/samples/csharp/getting-started/console-teleprompter/sampleQuotes.txt) 檔案複製到您的專案目錄中。</span><span class="sxs-lookup"><span data-stu-id="d8a46-155">Copy the [sampleQuotes.txt](https://raw.githubusercontent.com/dotnet/docs/master/samples/csharp/getting-started/console-teleprompter/sampleQuotes.txt) file from the GitHub repository for this [sample](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-teleprompter) into your project directory.</span></span> <span data-ttu-id="d8a46-156">這將作為您應用程式的指令碼。</span><span class="sxs-lookup"><span data-stu-id="d8a46-156">This will serve as the script for your application.</span></span> <span data-ttu-id="d8a46-157">如果您想要如何下載本主題之範例應用程式的資訊，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)主題中的指示。</span><span class="sxs-lookup"><span data-stu-id="d8a46-157">If you would like information on how to download the sample app for this topic, see the instructions in the [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) topic.</span></span>

<span data-ttu-id="d8a46-158">接著，在您的 Program 類別 (就在 `Main` 方法下方) 中新增下列方法：</span><span class="sxs-lookup"><span data-stu-id="d8a46-158">Next, add the following method in your Program class (right below the `Main` method):</span></span>

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

<span data-ttu-id="d8a46-159">此方法會使用來自兩個新命名空間的型別。</span><span class="sxs-lookup"><span data-stu-id="d8a46-159">This method uses types from two new namespaces.</span></span> <span data-ttu-id="d8a46-160">若要讓此檔案進行編譯，您將必須把下列兩行新增到檔案開頭：</span><span class="sxs-lookup"><span data-stu-id="d8a46-160">For this to compile you’ll need to add the following two lines to the top of the file:</span></span>

```csharp
using System.Collections.Generic;
using System.IO;
```

<span data-ttu-id="d8a46-161">`IEnumerable<T>` 介面是在 `System.Collections.Generic` 命名空間中定義。</span><span class="sxs-lookup"><span data-stu-id="d8a46-161">The `IEnumerable<T>` interface is defined in the `System.Collections.Generic` namespace.</span></span> <span data-ttu-id="d8a46-162">@System.IO.File 類別是在 `System.IO` 命名空間中定義。</span><span class="sxs-lookup"><span data-stu-id="d8a46-162">The @System.IO.File class is defined in the `System.IO` namespace.</span></span>

<span data-ttu-id="d8a46-163">此方法是 C# 方法的特殊型別，稱為「列舉程式方法」。</span><span class="sxs-lookup"><span data-stu-id="d8a46-163">This method is a special type of C# method called an *Enumerator method*.</span></span> <span data-ttu-id="d8a46-164">列舉程式方法會傳回延遲評估的序列。</span><span class="sxs-lookup"><span data-stu-id="d8a46-164">Enumerator methods return sequences that are evaluated lazily.</span></span> <span data-ttu-id="d8a46-165">這意謂著序列中的每個項目會在取用序列的程式碼要求該項目時產生。</span><span class="sxs-lookup"><span data-stu-id="d8a46-165">That means each item in the sequence is generated as it is requested by the code consuming the sequence.</span></span> <span data-ttu-id="d8a46-166">列舉程式方法是包含一或多個 `yield return` 陳述式的方法。</span><span class="sxs-lookup"><span data-stu-id="d8a46-166">Enumerator methods are methods that contain one or more `yield return` statements.</span></span> <span data-ttu-id="d8a46-167">`ReadFrom` 方法所傳回的物件包含用來產生序列中每個項目的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d8a46-167">The object returned by the `ReadFrom` method contains the code to generate each item in the sequence.</span></span> <span data-ttu-id="d8a46-168">在此範例中，這牽涉到從原始程式檔讀取下一行文字，並傳回該字串。</span><span class="sxs-lookup"><span data-stu-id="d8a46-168">In this example, that involves reading the next line of text from the source file, and returning that string.</span></span> <span data-ttu-id="d8a46-169">每次呼叫程式碼要求序列中的下一個項目時，程式碼都會從檔案讀取下一行文字，並傳回該文字。</span><span class="sxs-lookup"><span data-stu-id="d8a46-169">Each time the calling code requests the next item from the sequence, the code reads the next line of text from the file and returns it.</span></span> <span data-ttu-id="d8a46-170">當已完全讀取檔案時，序列會指出已沒有任何其他項目。</span><span class="sxs-lookup"><span data-stu-id="d8a46-170">When the file has been completely read, the sequence indicates that there are no more items.</span></span>

<span data-ttu-id="d8a46-171">有兩個其他 C# 語法元素可能是您不熟悉的。</span><span class="sxs-lookup"><span data-stu-id="d8a46-171">There are two other C# syntax elements that may be new to you.</span></span> <span data-ttu-id="d8a46-172">此方法中的 `using` 陳述式會管理資源清除。</span><span class="sxs-lookup"><span data-stu-id="d8a46-172">The `using` statement in this method manages resource cleanup.</span></span> <span data-ttu-id="d8a46-173">在 `using` 陳述式中初始化的變數 (在此範例中為 `reader`) 必須實作 `IDisposable` 介面。</span><span class="sxs-lookup"><span data-stu-id="d8a46-173">The variable that is initialized in the `using` statement (`reader`, in this example) must implement the `IDisposable` interface.</span></span> <span data-ttu-id="d8a46-174">@System.IDisposable 介面會定義單一方法 `Dispose`，在應該釋出資源時，便應該呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="d8a46-174">The @System.IDisposable interface defines a single method, `Dispose`, that should be called when the resource should be released.</span></span> <span data-ttu-id="d8a46-175">編譯器會在執行到達 `using` 陳述式的結尾大括號時產生該呼叫。</span><span class="sxs-lookup"><span data-stu-id="d8a46-175">The compiler generates that call when execution reaches the closing brace of the `using` statement.</span></span> <span data-ttu-id="d8a46-176">編譯器產生的程式碼會確保即使 using 陳述式所定義區塊中的程式碼擲回例外狀況，也會釋出資源。</span><span class="sxs-lookup"><span data-stu-id="d8a46-176">The compiler-generated code ensures that the resource is released even if an exception is thrown from the code in the block defined by the using statement.</span></span>

<span data-ttu-id="d8a46-177">定義 `reader` 變數時，是使用 `var` 關鍵字來定義。</span><span class="sxs-lookup"><span data-stu-id="d8a46-177">The `reader` variable is defined using the `var` keyword.</span></span> <span data-ttu-id="d8a46-178">`var` 會定義一個「隱含型別區域變數」。</span><span class="sxs-lookup"><span data-stu-id="d8a46-178">`var` defines an *implicitly typed local variable*.</span></span> <span data-ttu-id="d8a46-179">這意謂著變數的型別取決於指派給該變數之物件的編譯階段型別。</span><span class="sxs-lookup"><span data-stu-id="d8a46-179">That means the type of the variable is determined by the compile time type of the object assigned to the variable.</span></span> <span data-ttu-id="d8a46-180">在這裡，這是來自 @System.IO.File.OpenText 的傳回值，是一個 @System.IO.StreamReader 物件。</span><span class="sxs-lookup"><span data-stu-id="d8a46-180">Here, that is the return value from @System.IO.File.OpenText, which is a @System.IO.StreamReader object.</span></span>
 
<span data-ttu-id="d8a46-181">現在，讓我們在 `Main` 方法中填入可讀取檔案的程式碼：</span><span class="sxs-lookup"><span data-stu-id="d8a46-181">Now, let’s fill in the code to read the file in the `Main` method:</span></span> 

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line); 
}
```

<span data-ttu-id="d8a46-182">請執行程式 (使用 `dotnet run`，然後您便可以看到每一行顯示在主控台中)。</span><span class="sxs-lookup"><span data-stu-id="d8a46-182">Run the program (using `dotnet run` and you can see every line printed out to the console).</span></span>  

## <a name="adding-delays-and-formatting-output"></a><span data-ttu-id="d8a46-183">新增延遲及設定輸出格式</span><span class="sxs-lookup"><span data-stu-id="d8a46-183">Adding Delays and Formatting output</span></span>
<span data-ttu-id="d8a46-184">您的內容顯示速度太快，無法大聲朗讀。</span><span class="sxs-lookup"><span data-stu-id="d8a46-184">What you have is being displayed far too fast to read aloud.</span></span> <span data-ttu-id="d8a46-185">現在您必須在輸出中新增延遲。</span><span class="sxs-lookup"><span data-stu-id="d8a46-185">Now you need to add the delays in the output.</span></span> <span data-ttu-id="d8a46-186">開始時，您將建置能夠進行非同步處理的部分核心程式碼。</span><span class="sxs-lookup"><span data-stu-id="d8a46-186">As you start, you’ll be building some of the core code that enables asynchronous processing.</span></span> <span data-ttu-id="d8a46-187">不過，這些開頭的步驟會依循一些反模式。</span><span class="sxs-lookup"><span data-stu-id="d8a46-187">However, these first steps will follow a few anti-patterns.</span></span> <span data-ttu-id="d8a46-188">在您新增程式碼時，註解中會指出這些反模式，然後在稍後的步驟中將會更新此程式碼。</span><span class="sxs-lookup"><span data-stu-id="d8a46-188">The anti-patterns are pointed out in comments as you add the code, and the code will be updated in later steps.</span></span>

<span data-ttu-id="d8a46-189">這個部分有兩個步驟。</span><span class="sxs-lookup"><span data-stu-id="d8a46-189">There are two steps to this section.</span></span> <span data-ttu-id="d8a46-190">首先，您將更新迭代器方法以傳回單一文字而不是整行。</span><span class="sxs-lookup"><span data-stu-id="d8a46-190">First, you’ll update the iterator method to return single words instead of entire lines.</span></span> <span data-ttu-id="d8a46-191">這是藉由下列修改來完成。</span><span class="sxs-lookup"><span data-stu-id="d8a46-191">That’s done with these modifications.</span></span> <span data-ttu-id="d8a46-192">請以下列程式碼取代 `yield return line;` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="d8a46-192">Replace the `yield return line;` statement with the following code:</span></span>

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

<span data-ttu-id="d8a46-193">接著，您必須修改取用檔案行的方式，然後在寫入每個字之後新增延遲。</span><span class="sxs-lookup"><span data-stu-id="d8a46-193">Next, you need to modify how you consume the lines of the file, and add a delay after writing each word.</span></span> <span data-ttu-id="d8a46-194">請以下列區塊取代 `Main` 方法中的 `Console.WriteLine(line)` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="d8a46-194">Replace the `Console.WriteLine(line)` statement in the `Main` method with the following block:</span></span>

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

<span data-ttu-id="d8a46-195">`Task` 類別是在 `System.Threading.Tasks` 命名空間中，因此您必須在檔案開頭新增該 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="d8a46-195">The `Task` class is in the `System.Threading.Tasks` namespace, so you need to add that `using` statement at the top of file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="d8a46-196">請執行範例並檢查輸出。</span><span class="sxs-lookup"><span data-stu-id="d8a46-196">Run the sample, and check the output.</span></span> <span data-ttu-id="d8a46-197">現在會顯示每個單字，後面接著 200 毫秒的延遲。</span><span class="sxs-lookup"><span data-stu-id="d8a46-197">Now, each single word is printed, followed by a 200 ms delay.</span></span> <span data-ttu-id="d8a46-198">不過，顯示的輸出出現一些問題，因為來源文字檔有數行超過 80 個字元且沒有分行符號。</span><span class="sxs-lookup"><span data-stu-id="d8a46-198">However, the displayed output shows some issues because the source text file has several lines that have more than 80 characters without a line break.</span></span> <span data-ttu-id="d8a46-199">這在捲動時會相當難以閱讀。</span><span class="sxs-lookup"><span data-stu-id="d8a46-199">That can be hard to read while it's scrolling by.</span></span> <span data-ttu-id="d8a46-200">這個問題很容易修正。</span><span class="sxs-lookup"><span data-stu-id="d8a46-200">That’s easy to fix.</span></span> <span data-ttu-id="d8a46-201">您只需記錄每一行的長度，並在每次一行達到特定臨界值時就進行換行。</span><span class="sxs-lookup"><span data-stu-id="d8a46-201">You’ll just keep track of the length of each line, and generate a new line whenever the line length reaches a certain threshold.</span></span> <span data-ttu-id="d8a46-202">請在保存行長度的 `words` 宣告之後宣告區域變數：</span><span class="sxs-lookup"><span data-stu-id="d8a46-202">Declare a local variable after the declaration of `words` that holds the line length:</span></span>

```csharp
var lineLength = 0;
```
 
<span data-ttu-id="d8a46-203">接著，在 `yield return word + " ";` 陳述式之後 (在結尾大括號之前) 新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="d8a46-203">Then, add the following code after the `yield return word + " ";` statement (before the closing brace):</span></span>

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```
 
<span data-ttu-id="d8a46-204">請執行範例，然後您將能夠以其預先設定的步調大聲朗讀。</span><span class="sxs-lookup"><span data-stu-id="d8a46-204">Run the sample, and you’ll be able to read aloud at its pre-configured pace.</span></span>

## <a name="async-tasks"></a><span data-ttu-id="d8a46-205">非同步工作</span><span class="sxs-lookup"><span data-stu-id="d8a46-205">Async Tasks</span></span>
<span data-ttu-id="d8a46-206">在這最後一個步驟中，您將新增程式碼以在一個工作中以非同步方式寫入輸出，同時也執行另一個工作以讀取來自使用者的輸入 (如果他們想要加速或減緩文字顯示)。</span><span class="sxs-lookup"><span data-stu-id="d8a46-206">In this final step, you’ll add the code to write the output asynchronously in one task, while also running another task to read input from the user if they want to speed up or slow down the text display.</span></span> <span data-ttu-id="d8a46-207">這包括幾個步驟，而最後，您將會擁有您所需的一切更新。</span><span class="sxs-lookup"><span data-stu-id="d8a46-207">This has a few steps in it and by the end, you’ll have all the updates that you need.</span></span>
<span data-ttu-id="d8a46-208">第一個步驟是建立傳回方法的非同步 @System.Threading.Tasks.Task，該方法代表您到目前為止已建立來讀取和顯示檔案的程式碼。</span><span class="sxs-lookup"><span data-stu-id="d8a46-208">The first step is to create an asynchronous @System.Threading.Tasks.Task returning method that represents the code you’ve created so far to read and display the file.</span></span>

<span data-ttu-id="d8a46-209">請將下列方法新增到您的 `Program` 類別 (這是取自您 `Main` 方法的主體)：</span><span class="sxs-lookup"><span data-stu-id="d8a46-209">Add this method to your `Program` class (it’s taken from the body of your `Main` method):</span></span>

```csharp
private static async Task ShowTeleprompter()
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var line in words)
    {
        Console.Write(line);
        if (!string.IsNullOrWhiteSpace(line))
        {
            await Task.Delay(200);
        }
    }
}
```

<span data-ttu-id="d8a46-210">您將會注意到兩項變更。</span><span class="sxs-lookup"><span data-stu-id="d8a46-210">You’ll notice two changes.</span></span> <span data-ttu-id="d8a46-211">首先，在方法的主體中，此版本使用 `await` 關鍵字，而不是呼叫 @System.Threading.Tasks.Task.Wait 來同步等候工作完成。</span><span class="sxs-lookup"><span data-stu-id="d8a46-211">First, in the body of the method, instead of calling @System.Threading.Tasks.Task.Wait to synchronously wait for a task to finish, this version uses the `await` keyword.</span></span> <span data-ttu-id="d8a46-212">為了這麼做，您必須將 `async` 修飾詞新增到方法簽章。</span><span class="sxs-lookup"><span data-stu-id="d8a46-212">In order to do that, you need to add the `async` modifier to the method signature.</span></span> <span data-ttu-id="d8a46-213">此方法會傳回 `Task`。</span><span class="sxs-lookup"><span data-stu-id="d8a46-213">This method returns a `Task`.</span></span> <span data-ttu-id="d8a46-214">請注意，並沒有會傳回 `Task` 物件的傳回陳述式。</span><span class="sxs-lookup"><span data-stu-id="d8a46-214">Notice that there are no return statements that return a `Task` object.</span></span> <span data-ttu-id="d8a46-215">取而代之的是，會由編譯器在您使用 `await` 運算子時產生的程式碼建立 `Task` 物件。</span><span class="sxs-lookup"><span data-stu-id="d8a46-215">Instead, that `Task` object is created by code the compiler generates when you use the `await` operator.</span></span> <span data-ttu-id="d8a46-216">您可以想像這個方法會在到達 `await` 時返回。</span><span class="sxs-lookup"><span data-stu-id="d8a46-216">You can imagine that this method returns when it reaches an `await`.</span></span> <span data-ttu-id="d8a46-217">傳回的 `Task` 指出工作尚未完成。</span><span class="sxs-lookup"><span data-stu-id="d8a46-217">The returned `Task` indicates that the work has not completed.</span></span>
<span data-ttu-id="d8a46-218">方法會在所等候的工作完成時繼續執行。</span><span class="sxs-lookup"><span data-stu-id="d8a46-218">The method resumes when the awaited task completes.</span></span> <span data-ttu-id="d8a46-219">當它執行到完成時，傳回的 `Task` 會指出它已完成。</span><span class="sxs-lookup"><span data-stu-id="d8a46-219">When it has executed to completion, the returned `Task` indicates that it is complete.</span></span>
<span data-ttu-id="d8a46-220">呼叫程式碼可以監視傳回的 `Task` 以判斷它何時完成。</span><span class="sxs-lookup"><span data-stu-id="d8a46-220">Calling code can monitor that returned `Task` to determine when it has completed.</span></span>

<span data-ttu-id="d8a46-221">您可以在 `Main` 方法中呼叫這個新方法：</span><span class="sxs-lookup"><span data-stu-id="d8a46-221">You can call this new method in your `Main` method:</span></span>

```csharp
ShowTeleprompter().Wait();
```

<span data-ttu-id="d8a46-222">在這裡，`Main` 中的程式碼會執行同步等候。</span><span class="sxs-lookup"><span data-stu-id="d8a46-222">Here, in `Main`, the code does synchronously wait.</span></span> <span data-ttu-id="d8a46-223">您應該儘可能使用 `await` 運算子而不是同步等候。</span><span class="sxs-lookup"><span data-stu-id="d8a46-223">You should use the `await` operator instead of synchronously waiting whenever possible.</span></span> <span data-ttu-id="d8a46-224">但是，在主控台應用程式的 `Main` 方法中，您無法使用 `await` 運算子。</span><span class="sxs-lookup"><span data-stu-id="d8a46-224">But, in a console application’s `Main` method, you cannot use the `await` operator.</span></span> <span data-ttu-id="d8a46-225">那會導致應用程式在所有工作完成之前即結束。</span><span class="sxs-lookup"><span data-stu-id="d8a46-225">That would result in the application exiting before all tasks have completed.</span></span>

<span data-ttu-id="d8a46-226">接著，您必須撰寫第二個非同步方法，以從主控台進行讀取並監視 ‘<’ 和 ‘>’ 鍵。</span><span class="sxs-lookup"><span data-stu-id="d8a46-226">Next, you need to write the second asynchronous method to read from the Console and watch for the ‘<’ and ‘>’ keys.</span></span> <span data-ttu-id="d8a46-227">以下是您針對該工作新增的方法：</span><span class="sxs-lookup"><span data-stu-id="d8a46-227">Here’s the method you add for that task:</span></span>

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
        } while (true);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="d8a46-228">這會建立 lambda 運算式來代表 @System.Action 委派，此委派會從主控台讀取機碼，並修改代表使用者按 ‘<’ 或 ‘>’ 鍵時之延遲的區域變數。</span><span class="sxs-lookup"><span data-stu-id="d8a46-228">This creates a lambda expression to represent an @System.Action delegate that reads a key from the Console and modifies a local variable representing the delay when the user presses the ‘<’ or ‘>’ keys.</span></span> <span data-ttu-id="d8a46-229">此方法會使用 @System.Console.ReadKey 來封鎖並等候使用者按下按鍵。</span><span class="sxs-lookup"><span data-stu-id="d8a46-229">This method uses @System.Console.ReadKey to block and wait for the user to press a key.</span></span>

<span data-ttu-id="d8a46-230">若要完成此功能，您必須建立一個會傳回方法的新 `async Task`，該方法既會啟動這兩項工作 (`GetInput` 和 `ShowTeleprompter`)，也會管理這兩項工作之間的共用資料。</span><span class="sxs-lookup"><span data-stu-id="d8a46-230">To finish this feature, you need to create a new `async Task` returning method that starts both of these tasks (`GetInput` and `ShowTeleprompter`), and also manages the shared data between these two tasks.</span></span>
 
<span data-ttu-id="d8a46-231">現在即可建立可處理這兩項工作間之共用資料的類別。</span><span class="sxs-lookup"><span data-stu-id="d8a46-231">It’s time to create a class that can handle the shared data between these two tasks.</span></span> <span data-ttu-id="d8a46-232">此類別包含兩個公用屬性：延遲和一個指出已完全讀取檔案的旗標：</span><span class="sxs-lookup"><span data-stu-id="d8a46-232">This class contains two public properties: the delay, and a flag to indicate that the file has been completely read:</span></span>

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        private object lockHandle = new object();
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            lock (lockHandle)
            {
                DelayInMilliseconds = newDelay;
            }
        }
    }
}
```

<span data-ttu-id="d8a46-233">請將該類別放在新檔案中，然後如以上所示，將該類別包含在 `TeleprompterConsole` 命名空間中。</span><span class="sxs-lookup"><span data-stu-id="d8a46-233">Put that class in a new file, and enclose that class in the `TeleprompterConsole` namespace as shown above.</span></span> <span data-ttu-id="d8a46-234">您還必須新增 `using static` 陳述式，如此您才能在不使用封入類別或命名空間名稱的情況下參考 `Min` 和 `Max` 方法。</span><span class="sxs-lookup"><span data-stu-id="d8a46-234">You’ll also need to add a `using static` statement so that you can reference the `Min` and `Max` method without the enclosing class or namespace names.</span></span> <span data-ttu-id="d8a46-235">`using static` 陳述式會從一個類別匯入方法。</span><span class="sxs-lookup"><span data-stu-id="d8a46-235">A `using static` statement imports the methods from one class.</span></span> <span data-ttu-id="d8a46-236">這與到目前為止所使用的 `using` 陳述式形成對比，該陳述式會從命名空間匯入所有類別。</span><span class="sxs-lookup"><span data-stu-id="d8a46-236">This is in contrast with the `using` statements used up to this point that have imported all classes from a namespace.</span></span>

```csharp
using static System.Math;
```

<span data-ttu-id="d8a46-237">另一個新的語言功能是 `lock` 陳述式。</span><span class="sxs-lookup"><span data-stu-id="d8a46-237">The other language feature that’s new is the `lock` statement.</span></span> <span data-ttu-id="d8a46-238">此陳述式可確保在任何指定的時間點，該程式碼中都只能有單一執行緒。</span><span class="sxs-lookup"><span data-stu-id="d8a46-238">This statement ensures that only a single thread can be in that code at any given time.</span></span> <span data-ttu-id="d8a46-239">如果有一個執行緒處於鎖定的區段，其他執行緒就必須等候第一個執行緒結束該區段。</span><span class="sxs-lookup"><span data-stu-id="d8a46-239">If one thread is in the locked section, other threads must wait for the first thread to exit that section.</span></span> <span data-ttu-id="d8a46-240">`lock` 陳述式會使用一個保護鎖定區段的物件。</span><span class="sxs-lookup"><span data-stu-id="d8a46-240">The `lock` statement uses an object that guards the lock section.</span></span> <span data-ttu-id="d8a46-241">此類別會依循標準慣用語來鎖定類別中的私用物件。</span><span class="sxs-lookup"><span data-stu-id="d8a46-241">This class follows a standard idiom to lock a private object in the class.</span></span>

<span data-ttu-id="d8a46-242">接著，您必須更新 `ShowTeleprompter` 和 `GetInput` 方法以使用新的 `config` 物件。</span><span class="sxs-lookup"><span data-stu-id="d8a46-242">Next, you need to update the `ShowTeleprompter` and `GetInput` methods to use the new `config` object.</span></span> <span data-ttu-id="d8a46-243">請撰寫一個最後的 `Task` 來傳回 `async` 方法，以啟動兩項工作並在第一個工作完成時結束：</span><span class="sxs-lookup"><span data-stu-id="d8a46-243">Write one final `Task` returning `async` method to start both tasks and exit when the first task finishes:</span></span>

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

<span data-ttu-id="d8a46-244">這裡的一個新方法是 @System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[]) 呼叫。</span><span class="sxs-lookup"><span data-stu-id="d8a46-244">The one new method here is the @System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[]) call.</span></span> <span data-ttu-id="d8a46-245">此方法會建立一個 `Task`，它會在其引數清單中的任何工作完成時便結束。</span><span class="sxs-lookup"><span data-stu-id="d8a46-245">That creates a `Task` that finishes as soon as any of the tasks in its argument list completes.</span></span>

<span data-ttu-id="d8a46-246">接著，您必須更新 `ShowTeleprompter` 和 `GetInput` 方法以使用 `config` 物件來設定延遲：</span><span class="sxs-lookup"><span data-stu-id="d8a46-246">Next, you need to update both the `ShowTeleprompter` and `GetInput` methods to use the `config` object for the delay:</span></span>

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var line in words)
    {
        Console.Write(line);
        if (!string.IsNullOrWhiteSpace(line))
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
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="d8a46-247">這個新版本的 `ShowTeleprompter` 會呼叫 `TeleprompterConfig` 類別中的新方法。</span><span class="sxs-lookup"><span data-stu-id="d8a46-247">This new version of `ShowTeleprompter` calls a new method in the `TeleprompterConfig` class.</span></span> <span data-ttu-id="d8a46-248">現在，您必須更新 `Main` 以呼叫 `RunTeleprompter` 而不是 `ShowTeleprompter`：</span><span class="sxs-lookup"><span data-stu-id="d8a46-248">Now, you need to update `Main` to call `RunTeleprompter` instead of `ShowTeleprompter`:</span></span>

```csharp
RunTeleprompter().Wait();
```

<span data-ttu-id="d8a46-249">若要完成，您將必須將 `SetDone` 方法和 `Done` 屬性新增到 `TelePrompterConfig` 類別：</span><span class="sxs-lookup"><span data-stu-id="d8a46-249">To finish, you'll need to add the `SetDone` method, and the `Done` property to the `TelePrompterConfig` class:</span></span>

```csharp
public bool Done => done;

private bool done;

public void SetDone()
{
    done = true;    
}
```

## <a name="conclusion"></a><span data-ttu-id="d8a46-250">結論</span><span class="sxs-lookup"><span data-stu-id="d8a46-250">Conclusion</span></span>
<span data-ttu-id="d8a46-251">本教學課程示範一些與在主控台應用程式中工作有關的 C# 語言和 .NET Core 程式庫相關功能。</span><span class="sxs-lookup"><span data-stu-id="d8a46-251">This tutorial showed you a number of the features around the C# language and the .NET Core libraries related to working in Console applications.</span></span>
<span data-ttu-id="d8a46-252">您可以利用這項知識作為基礎，進一步探索這裡介紹的語言和類別。</span><span class="sxs-lookup"><span data-stu-id="d8a46-252">You can build on this knowledge to explore more about the language, and the classes introduced here.</span></span> <span data-ttu-id="d8a46-253">您已經了解檔案和主控台 I/O 的基本概念、工作型非同步程式設計模型的封鎖和非封鎖用法、C# 語言和 C# 程式組織方式的教學課程，以及「.NET Core 命令列介面」與工具。</span><span class="sxs-lookup"><span data-stu-id="d8a46-253">You’ve seen the basics of File and Console I/O, blocking and non-blocking use of the Task based Asynchronous programming model, a tour of the C# language and how C# programs are organized and the .NET Core Command Line Interface and tools.</span></span>
 

