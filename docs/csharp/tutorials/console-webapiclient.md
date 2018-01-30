---
title: "使用 .NET Core 來建立 REST 用戶端"
description: "本教學課程會教導您一些 .NET Core 和 C# 語言中的功能。"
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 6b0f3acc3a6dbed4f44497d92d3c518ee5a5d2a7
ms.sourcegitcommit: dd6ea7f0e581ac84e0a90d9b23c463fcf1ec3ce7
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2018
---
# <a name="rest-client"></a><span data-ttu-id="da927-104">REST 用戶端</span><span class="sxs-lookup"><span data-stu-id="da927-104">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="da927-105">簡介</span><span class="sxs-lookup"><span data-stu-id="da927-105">Introduction</span></span>
<span data-ttu-id="da927-106">本教學課程會教導您一些 .NET Core 和 C# 語言中的功能。</span><span class="sxs-lookup"><span data-stu-id="da927-106">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="da927-107">您將了解：</span><span class="sxs-lookup"><span data-stu-id="da927-107">You’ll learn:</span></span>
*   <span data-ttu-id="da927-108">「.NET Core 命令列介面」(CLI) 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="da927-108">The basics of the .NET Core Command Line Interface (CLI).</span></span>
*   <span data-ttu-id="da927-109">「C# 語言」功能的概觀。</span><span class="sxs-lookup"><span data-stu-id="da927-109">An overview of C# Language features.</span></span>
*   <span data-ttu-id="da927-110">使用 NuGet 來管理相依性</span><span class="sxs-lookup"><span data-stu-id="da927-110">Managing dependencies with NuGet</span></span>
*   <span data-ttu-id="da927-111">HTTP 通訊</span><span class="sxs-lookup"><span data-stu-id="da927-111">HTTP Communications</span></span>
*   <span data-ttu-id="da927-112">處理 JSON 資訊</span><span class="sxs-lookup"><span data-stu-id="da927-112">Processing JSON information</span></span>
*   <span data-ttu-id="da927-113">使用「屬性」來管理組態。</span><span class="sxs-lookup"><span data-stu-id="da927-113">Managing configuration with Attributes.</span></span> 

<span data-ttu-id="da927-114">您將建置一個對 GitHub 上的 REST 服務發出「HTTP 要求」的應用程式。</span><span class="sxs-lookup"><span data-stu-id="da927-114">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="da927-115">您將讀取 JSON 格式的資訊，並將該 JSON 封包轉換成 C# 物件。</span><span class="sxs-lookup"><span data-stu-id="da927-115">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="da927-116">最後，您將了解如何使用 C# 物件。</span><span class="sxs-lookup"><span data-stu-id="da927-116">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="da927-117">本教學課程中有許多功能。</span><span class="sxs-lookup"><span data-stu-id="da927-117">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="da927-118">讓我們來逐一建置它們。</span><span class="sxs-lookup"><span data-stu-id="da927-118">Let’s build them one by one.</span></span>

<span data-ttu-id="da927-119">如果您偏好追蹤本主題的[最終範例](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient)，則可以下載它。</span><span class="sxs-lookup"><span data-stu-id="da927-119">If you prefer to follow along with the [final sample](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="da927-120">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="da927-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="da927-121">必要條件</span><span class="sxs-lookup"><span data-stu-id="da927-121">Prerequisites</span></span>
<span data-ttu-id="da927-122">您將必須設定電腦以執行 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="da927-122">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="da927-123">您可以在 [.NET Core (英文)](https://www.microsoft.com/net/core) 頁面找到安裝指示。</span><span class="sxs-lookup"><span data-stu-id="da927-123">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="da927-124">您可以在 Windows、Linux、macOS 或是 Docker 容器中執行此應用程式。</span><span class="sxs-lookup"><span data-stu-id="da927-124">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="da927-125">您將必須安裝慣用的程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="da927-125">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="da927-126">以下說明使用 [Visual Studio Code (英文)](https://code.visualstudio.com/)，這是開放原始碼的跨平台編輯器。</span><span class="sxs-lookup"><span data-stu-id="da927-126">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="da927-127">不過，您可以使用您熟悉的任何工具。</span><span class="sxs-lookup"><span data-stu-id="da927-127">However, you can use whatever tools you are comfortable with.</span></span>
## <a name="create-the-application"></a><span data-ttu-id="da927-128">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="da927-128">Create the Application</span></span>
<span data-ttu-id="da927-129">第一個步驟是建立新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="da927-129">The first step is to create a new application.</span></span> <span data-ttu-id="da927-130">請開啟命令提示字元，然後為您的應用程式建立新目錄。</span><span class="sxs-lookup"><span data-stu-id="da927-130">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="da927-131">使該目錄成為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="da927-131">Make that the current directory.</span></span> <span data-ttu-id="da927-132">在命令提示字元處輸入命令 `dotnet new console`。</span><span class="sxs-lookup"><span data-stu-id="da927-132">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="da927-133">這會建立基本 "Hello World" 應用程式的起始檔案。</span><span class="sxs-lookup"><span data-stu-id="da927-133">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="da927-134">在您開始進行修改之前，讓我們先將執行簡單 Hello World 應用程式的所有步驟執行一遍。</span><span class="sxs-lookup"><span data-stu-id="da927-134">Before you start making modifications, let’s go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="da927-135">在建立應用程式之後，在命令提示字元鍵入 `dotnet restore` ([參閱附註](#dotnet-restore-note))。</span><span class="sxs-lookup"><span data-stu-id="da927-135">After creating the application, type `dotnet restore` ([see note](#dotnet-restore-note)) at the command prompt.</span></span> <span data-ttu-id="da927-136">此命令會執行 NuGet 套件還原程序。</span><span class="sxs-lookup"><span data-stu-id="da927-136">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="da927-137">NuGet 是一個 .NET 套件管理員。</span><span class="sxs-lookup"><span data-stu-id="da927-137">NuGet is a .NET package manager.</span></span> <span data-ttu-id="da927-138">此命令會為您的專案下載任何遺漏的相依性。</span><span class="sxs-lookup"><span data-stu-id="da927-138">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="da927-139">由於這是一個新專案，因此沒有任何現有的相依性，所以第一次執行時將會下載 .NET Core 架構。</span><span class="sxs-lookup"><span data-stu-id="da927-139">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="da927-140">在這個初始步驟之後，當您新增新的相依套件或更新任何相依性的版本時，將只需要執行 `dotnet restore` ([參閱附註](#dotnet-restore-note))。</span><span class="sxs-lookup"><span data-stu-id="da927-140">After this initial step, you will only need to run `dotnet restore` ([see note](#dotnet-restore-note)) when you add new dependent packages, or update the versions of any of your dependencies.</span></span>  

<span data-ttu-id="da927-141">還原套件之後，您需執行 `dotnet build`。</span><span class="sxs-lookup"><span data-stu-id="da927-141">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="da927-142">這會執行建置引擎並建立您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="da927-142">This executes the build engine and creates your application.</span></span> <span data-ttu-id="da927-143">最後，您需執行 `dotnet run` 來執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="da927-143">Finally, you execute `dotnet run` to run your application.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="da927-144">新增新的相依性</span><span class="sxs-lookup"><span data-stu-id="da927-144">Adding New Dependencies</span></span>
<span data-ttu-id="da927-145">.NET Core 的其中一個主要設計目標就是將 .NET Framework 安裝大小縮減到最小。</span><span class="sxs-lookup"><span data-stu-id="da927-145">One of the key design goals for .NET Core is to minimize the size of the .NET framework installation.</span></span> <span data-ttu-id="da927-146">.NET Core 應用程式架構只包含 .NET 完整架構的最常見元素。</span><span class="sxs-lookup"><span data-stu-id="da927-146">The .NET Core Application framework contains only the most common elements of the .NET full framework.</span></span> <span data-ttu-id="da927-147">如果應用程式的某些功能需要額外的程式庫，您可以將這些相依性新增到 C# 專案檔 (\*.csproj) 中。</span><span class="sxs-lookup"><span data-stu-id="da927-147">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="da927-148">就我們的範例而言，您將必須新增 `System.Runtime.Serialization.Json` 套件，以便讓您的應用程式能夠處理 JSON 回應。</span><span class="sxs-lookup"><span data-stu-id="da927-148">For our example, you'll need to add the `System.Runtime.Serialization.Json` package so your application can process JSON responses.</span></span>

<span data-ttu-id="da927-149">請開啟您的 `csproj` 專案檔。</span><span class="sxs-lookup"><span data-stu-id="da927-149">Open your `csproj` project file.</span></span> <span data-ttu-id="da927-150">檔案的第一行程應該顯示如下：</span><span class="sxs-lookup"><span data-stu-id="da927-150">The first line of the file should appear as:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
```

<span data-ttu-id="da927-151">在此行之後，緊接著新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="da927-151">Add the following immediately after this line:</span></span> 

```xml
   <ItemGroup>
      <PackageReference Include="System.Runtime.Serialization.Json" Version="4.3.0" />
   </ItemGroup> 
```
<span data-ttu-id="da927-152">大多數程式碼編輯器都有為這些程式庫的不同版本提供完成功能。</span><span class="sxs-lookup"><span data-stu-id="da927-152">Most code editors will provide completion for different versions of these libraries.</span></span> <span data-ttu-id="da927-153">您通常會想要使用所新增之任何套件的最新版本。</span><span class="sxs-lookup"><span data-stu-id="da927-153">You'll usually want to use the latest version of any package that you add.</span></span> <span data-ttu-id="da927-154">不過，請務必確保所有套件的版本都相符，此外，也與 .NET Core 應用程式架構的版本相符。</span><span class="sxs-lookup"><span data-stu-id="da927-154">However, it is important to make sure that the versions of all packages match, and that they also match the version of the .NET Core Application framework.</span></span>

<span data-ttu-id="da927-155">在您進行這些變更之後，應該重新執行 `dotnet restore` ([參閱附註](#dotnet-restore-note))，讓套件安裝在您的系統上。</span><span class="sxs-lookup"><span data-stu-id="da927-155">After you've made these changes, you should run `dotnet restore` ([see note](#dotnet-restore-note)) again so that the package is installed on your system.</span></span>

## <a name="making-web-requests"></a><span data-ttu-id="da927-156">提出 Web 要求</span><span class="sxs-lookup"><span data-stu-id="da927-156">Making Web Requests</span></span>
<span data-ttu-id="da927-157">現在您已經準備好開始從 Web 接收資料。</span><span class="sxs-lookup"><span data-stu-id="da927-157">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="da927-158">在此應用程式中，您將從 [GitHub API](https://developer.github.com/v3/) 讀取資訊。</span><span class="sxs-lookup"><span data-stu-id="da927-158">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="da927-159">讓我們在 [.NET Foundation](http://www.dotnetfoundation.org/) 的庇護下讀取專案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="da927-159">Let's read information about the projects under the [.NET Foundation](http://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="da927-160">您將從對 GitHub API 提出要求以擷取專案相關資訊著手。</span><span class="sxs-lookup"><span data-stu-id="da927-160">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="da927-161">您將使用的端點為：[https://api.github.com/orgs/dotnet/repos](https://api.github.com/orgs/dotnet/repos)。</span><span class="sxs-lookup"><span data-stu-id="da927-161">The endpoint you'll use is: [https://api.github.com/orgs/dotnet/repos](https://api.github.com/orgs/dotnet/repos).</span></span> <span data-ttu-id="da927-162">您想要擷取這些專案的所有相關資訊，因此您將使用 HTTP GET 要求。</span><span class="sxs-lookup"><span data-stu-id="da927-162">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="da927-163">您的瀏覽器也會使用 HTTP GET 要求，因此您可以將該 URL 貼到瀏覽器中，以查看您將接收和處理的資訊。</span><span class="sxs-lookup"><span data-stu-id="da927-163">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="da927-164">您需使用 <xref:System.Net.Http.HttpClient> 類別來提出 Web 要求。</span><span class="sxs-lookup"><span data-stu-id="da927-164">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="da927-165">與所有新式 .NET API 相同，<xref:System.Net.Http.HttpClient> 針對它的長時間執行 API 只支援非同步方法。</span><span class="sxs-lookup"><span data-stu-id="da927-165">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="da927-166">請從建立非同步方法著手。</span><span class="sxs-lookup"><span data-stu-id="da927-166">Start by making an async method.</span></span> <span data-ttu-id="da927-167">您將在建置應用程式的功能時填入實作。</span><span class="sxs-lookup"><span data-stu-id="da927-167">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="da927-168">請從開啟您專案目錄中的 `program.cs` 檔案並將下列方法新增到 `Program` 類別著手：</span><span class="sxs-lookup"><span data-stu-id="da927-168">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
    
}
```

<span data-ttu-id="da927-169">您將必須在 `Main` 方法上面新增 `using` 陳述式，如此 C# 編譯器才能夠辨識 <xref:System.Threading.Tasks.Task> 型別：</span><span class="sxs-lookup"><span data-stu-id="da927-169">You'll need to add a `using` statement at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="da927-170">如果您在此時建置專案，您將會收到針對此方法產生的警告，因為它不包含任何 `await` 運算子，所以將會以同步方式執行。</span><span class="sxs-lookup"><span data-stu-id="da927-170">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="da927-171">目前請先忽略該警告；您將在填入方法時新增 `await` 運算子。</span><span class="sxs-lookup"><span data-stu-id="da927-171">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="da927-172">接著，請將 `namespace` 陳述式中定義的命名空間從其預設值 `ConsoleApp` 重新命名為 `WebAPIClient`。</span><span class="sxs-lookup"><span data-stu-id="da927-172">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="da927-173">我們稍後將會在此命名空間中定義 `repo` 類別。</span><span class="sxs-lookup"><span data-stu-id="da927-173">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="da927-174">接著，請將 `Main` 方法更新成呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="da927-174">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="da927-175">`ProcessRepositories` 方法會傳回一個工作，而在該工作完成之前，您不應該結束程式。</span><span class="sxs-lookup"><span data-stu-id="da927-175">The `ProcessRepositories` method returns a Task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="da927-176">因此，您必須使用 `Wait` 方法來封鎖並等候工作完成：</span><span class="sxs-lookup"><span data-stu-id="da927-176">Therefore, you must use the `Wait` method to block and wait for the task to finish:</span></span>

```csharp
public static void Main(string[] args)
{
    ProcessRepositories().Wait();
}
```

<span data-ttu-id="da927-177">現在，您擁有一個不會執行任何動作但會以非同步方式執行的程式。</span><span class="sxs-lookup"><span data-stu-id="da927-177">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="da927-178">來加以改善吧。</span><span class="sxs-lookup"><span data-stu-id="da927-178">Let's improve it.</span></span>

<span data-ttu-id="da927-179">首先，您需要一個能夠從網路擷取資料的物件；使用 <xref:System.Net.Http.HttpClient> 即可達成。</span><span class="sxs-lookup"><span data-stu-id="da927-179">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="da927-180">此物件會處理要求和回應。</span><span class="sxs-lookup"><span data-stu-id="da927-180">This object handles the request and the responses.</span></span> <span data-ttu-id="da927-181">在 Program.cs 檔案內，將 `Program` 類別中該類型的單一執行個體具現化。</span><span class="sxs-lookup"><span data-stu-id="da927-181">Instantiate a single instance of that type in the `Program` class inside the Program.cs file.</span></span>

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static void Main(string[] args)
        {
            //...
        }
    }
}
```

 <span data-ttu-id="da927-182">讓我們回到 `ProcessRepositories` 方法並填入其第一個版本：</span><span class="sxs-lookup"><span data-stu-id="da927-182">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

```csharp
private static async Task ProcessRepositories()
{
    client.DefaultRequestHeaders.Accept.Clear();
    client.DefaultRequestHeaders.Accept.Add(
        new MediaTypeWithQualityHeaderValue("application/vnd.github.v3+json"));
    client.DefaultRequestHeaders.Add("User-Agent", ".NET Foundation Repository Reporter");

    var stringTask = client.GetStringAsync("https://api.github.com/orgs/dotnet/repos");

    var msg = await stringTask;
    Console.Write(msg);
}
```

<span data-ttu-id="da927-183">您將必須在檔案開頭一併新增兩個新的 using 陳述式以讓此檔案進行編譯：</span><span class="sxs-lookup"><span data-stu-id="da927-183">You'll need to also add two new using statements at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="da927-184">第一個版本會提出 Web 要求來讀取 dotnet foundation 組織底下的所有儲存機制清單。</span><span class="sxs-lookup"><span data-stu-id="da927-184">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="da927-185">(.NET Foundation 的 gitHub 識別碼是 'dotnet')。</span><span class="sxs-lookup"><span data-stu-id="da927-185">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="da927-186">前幾行會為這個要求設定 <xref:System.Net.Http.HttpClient>。</span><span class="sxs-lookup"><span data-stu-id="da927-186">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="da927-187">首先，會將它設定為接受 GitHub JSON 回應。</span><span class="sxs-lookup"><span data-stu-id="da927-187">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="da927-188">此格式就是 JSON。</span><span class="sxs-lookup"><span data-stu-id="da927-188">This format is simply JSON.</span></span> <span data-ttu-id="da927-189">下一行會將「使用者代理程式」標頭新增到來自此物件的所有要求。</span><span class="sxs-lookup"><span data-stu-id="da927-189">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="da927-190">這兩個標頭會受到 GitHub 伺服器程式碼檢查，並且是從 GitHub 擷取資訊的必要標頭。</span><span class="sxs-lookup"><span data-stu-id="da927-190">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="da927-191">設定 <xref:System.Net.Http.HttpClient> 之後，您需提出 Web 要求並擷取回應。</span><span class="sxs-lookup"><span data-stu-id="da927-191">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="da927-192">在這個第一版中，您會使用 <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> 便利方法。</span><span class="sxs-lookup"><span data-stu-id="da927-192">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="da927-193">這個便利方法會啟動一個提出 Web 要求的工作，然後當要求返回時，它會讀取回應資料流並從該資料流擷取內容。</span><span class="sxs-lookup"><span data-stu-id="da927-193">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="da927-194">回應本文會以 <xref:System.String> 的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="da927-194">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="da927-195">當工作完成時，就會提供該字串。</span><span class="sxs-lookup"><span data-stu-id="da927-195">The string is available when the task completes.</span></span> 

<span data-ttu-id="da927-196">此方法的最後兩行會等候該工作，然後將回應顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="da927-196">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="da927-197">請建置應用程式並執行它。</span><span class="sxs-lookup"><span data-stu-id="da927-197">Build the app, and run it.</span></span> <span data-ttu-id="da927-198">建置警告現在已消失，因為 `ProcessRepositories` 現在確實包含 `await` 運算子。</span><span class="sxs-lookup"><span data-stu-id="da927-198">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="da927-199">您將會看到一長串顯示的 JSON 格式文字。</span><span class="sxs-lookup"><span data-stu-id="da927-199">You'll see a long display of JSON formatted text.</span></span>   

## <a name="processing-the-json-result"></a><span data-ttu-id="da927-200">處理 JSON 結果</span><span class="sxs-lookup"><span data-stu-id="da927-200">Processing the JSON Result</span></span>

<span data-ttu-id="da927-201">此時，您已撰寫程式碼來從 Web 伺服器擷取回應，並顯示包含在該回應中的文字。</span><span class="sxs-lookup"><span data-stu-id="da927-201">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="da927-202">接著，讓我們將該 JSON 回應轉換成 C# 物件。</span><span class="sxs-lookup"><span data-stu-id="da927-202">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="da927-203">「JSON 序列化程式」會將 JSON 資料轉匯成「C# 物件」。</span><span class="sxs-lookup"><span data-stu-id="da927-203">The JSON Serializer converts JSON data into C# Objects.</span></span> <span data-ttu-id="da927-204">您的第一個工作是定義 C# 類別型別，以包含所使用來自這個回應的資訊。</span><span class="sxs-lookup"><span data-stu-id="da927-204">Your first task is to define a C# class type to contain the information you use from this response.</span></span> <span data-ttu-id="da927-205">讓我們慢慢地進行建置，因此，請從包含儲存機制名稱的簡單 C# 型別著手：</span><span class="sxs-lookup"><span data-stu-id="da927-205">Let's build this slowly, so start with a simple C# type that contains the name of the repository:</span></span>

```csharp
using System;

namespace WebAPIClient
{
    public class repo
    {
        public string name;
    }
}
``` 

<span data-ttu-id="da927-206">請將上述程式碼放在名為 'repo.cs' 的新檔案中。</span><span class="sxs-lookup"><span data-stu-id="da927-206">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="da927-207">這個類別版本代表處理 JSON 資料的最簡單路徑。</span><span class="sxs-lookup"><span data-stu-id="da927-207">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="da927-208">類別名稱和成員名稱會符合 JSON 封包中使用的名稱，而不是符合下列 C# 慣例。</span><span class="sxs-lookup"><span data-stu-id="da927-208">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="da927-209">您將在稍後藉由提供一些其他組態屬性來修正此問題。</span><span class="sxs-lookup"><span data-stu-id="da927-209">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="da927-210">此類別示範了 JSON 序列化和還原序列化的另一個重要功能：並非 JSON 封包中的所有欄位都屬於此類別。</span><span class="sxs-lookup"><span data-stu-id="da927-210">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="da927-211">JSON 序列化程式將會忽略未包含在所要使用之類別型別中的資訊。</span><span class="sxs-lookup"><span data-stu-id="da927-211">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="da927-212">這個功能可讓您更容易建立只對 JSON 封包中的欄位子集有作用的型別。</span><span class="sxs-lookup"><span data-stu-id="da927-212">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="da927-213">現在您已經建立型別，讓我們來將它還原序列化。</span><span class="sxs-lookup"><span data-stu-id="da927-213">Now that you've created the type, let's deserialize it.</span></span> <span data-ttu-id="da927-214">您將必須建立 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> 物件。</span><span class="sxs-lookup"><span data-stu-id="da927-214">You'll need to create a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object.</span></span> <span data-ttu-id="da927-215">此物件必須知道針對其擷取的 JSON 封包預期的 CLR 型別。</span><span class="sxs-lookup"><span data-stu-id="da927-215">This object must know the CLR type expected for the JSON packet it retrieves.</span></span> <span data-ttu-id="da927-216">來自 GitHub 的封包會包含一個儲存機制序列，因此 `List<repo>` 是正確的型別。</span><span class="sxs-lookup"><span data-stu-id="da927-216">The packet from GitHub contains a sequence of repositories, so a `List<repo>` is the correct type.</span></span> <span data-ttu-id="da927-217">請將下列這一行新增到您的 `ProcessRepositories` 方法：</span><span class="sxs-lookup"><span data-stu-id="da927-217">Add the following line to your `ProcessRepositories` method:</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<repo>));
```

<span data-ttu-id="da927-218">您將使用兩個新的命名空間，因此您將必須一併新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="da927-218">You're using two new namespaces, so you'll need to add those as well:</span></span>

```csharp
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
```

<span data-ttu-id="da927-219">接著，您將使用序列化程式將 JSON 轉換成 C# 物件。</span><span class="sxs-lookup"><span data-stu-id="da927-219">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="da927-220">請使用以下兩行來取代對您 `ProcessRepositories` 方法中 <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> 的呼叫：</span><span class="sxs-lookup"><span data-stu-id="da927-220">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following two lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = serializer.ReadObject(await streamTask) as List<repo>;
```

<span data-ttu-id="da927-221">請注意，您現在使用的是 <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> 而不是 <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>。</span><span class="sxs-lookup"><span data-stu-id="da927-221">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="da927-222">序列化程式會使用資料流 (而不是字串) 作為其來源。</span><span class="sxs-lookup"><span data-stu-id="da927-222">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="da927-223">讓我們來說明上述第二行中所使用的一些 C# 語言功能。</span><span class="sxs-lookup"><span data-stu-id="da927-223">Let's explain a couple features of the C# language that are being used in the second line above.</span></span> <span data-ttu-id="da927-224"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> 的引數是 `await` 運算式。</span><span class="sxs-lookup"><span data-stu-id="da927-224">The argument to <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> is an `await` expression.</span></span> <span data-ttu-id="da927-225">Await 運算式可以出現在您程式碼中幾乎任何一個地方，雖然到目前為止，您只在指派陳述式中看到它們。</span><span class="sxs-lookup"><span data-stu-id="da927-225">Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span>

<span data-ttu-id="da927-226">其次，`as` 運算子會從編譯階段型別 `object` 轉換成 `List<repo>`。</span><span class="sxs-lookup"><span data-stu-id="da927-226">Secondly, the `as` operator converts from the compile time type of `object` to `List<repo>`.</span></span> <span data-ttu-id="da927-227"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> 的宣告會宣告其傳回 <xref:System.Object?displayProperty=nameWithType> 類型的物件。</span><span class="sxs-lookup"><span data-stu-id="da927-227">The declaration of <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> declares that it returns an object of type <xref:System.Object?displayProperty=nameWithType>.</span></span> <span data-ttu-id="da927-228"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> 會傳回您在加以建構時指定的類型 (在本教學課程中為 `List<repo>`)。</span><span class="sxs-lookup"><span data-stu-id="da927-228"><xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.ReadObject(System.IO.Stream)> will return the type you specified when you constructed it (`List<repo>` in this tutorial).</span></span> <span data-ttu-id="da927-229">如果轉換並未成功，`as` 運算子就會評估為 `null`，而不是擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="da927-229">If the conversion does not succeed, the `as` operator evaluates to `null`, instead of throwing an exception.</span></span>

<span data-ttu-id="da927-230">您差不多已經完成這個部分。</span><span class="sxs-lookup"><span data-stu-id="da927-230">You're almost done with this section.</span></span> <span data-ttu-id="da927-231">現在您已將 JSON 轉換成 C# 物件，讓我們來顯示每個儲存機制的名稱。</span><span class="sxs-lookup"><span data-stu-id="da927-231">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="da927-232">將下列幾行：</span><span class="sxs-lookup"><span data-stu-id="da927-232">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="da927-233">取代為：</span><span class="sxs-lookup"><span data-stu-id="da927-233">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="da927-234">編譯並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="da927-234">Compile and run the application.</span></span> <span data-ttu-id="da927-235">它將會列印出隸屬於 .NET Foundation 的儲存機制名稱。</span><span class="sxs-lookup"><span data-stu-id="da927-235">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="da927-236">控制序列化</span><span class="sxs-lookup"><span data-stu-id="da927-236">Controlling Serialization</span></span>

<span data-ttu-id="da927-237">在您新增更多功能之前，讓我們先處理 `repo` 型別並讓它符合更標準的 C# 慣例。</span><span class="sxs-lookup"><span data-stu-id="da927-237">Before you add more features, let's address the `repo` type and make it follow more standard C# conventions.</span></span> <span data-ttu-id="da927-238">您將透過在 `repo` 型別上加註控制「JSON 序列化程式」運作方式的「屬性」，來進行這項操作。</span><span class="sxs-lookup"><span data-stu-id="da927-238">You'll do this by annotating the `repo` type with *attributes* that control how the JSON Serializer works.</span></span> <span data-ttu-id="da927-239">在您的案例中，您將使用這些屬性來定義 JSON 機碼名稱與 C# 類別及成員名稱之間的對應。</span><span class="sxs-lookup"><span data-stu-id="da927-239">In your case, you'll use these attributes to define a mapping between the JSON key names and the C# class and member names.</span></span> <span data-ttu-id="da927-240">所使用的兩個屬性為 `DataContract` 屬性和 `DataMember` 屬性。</span><span class="sxs-lookup"><span data-stu-id="da927-240">The two attributes used are the `DataContract` attribute and the `DataMember` attribute.</span></span> <span data-ttu-id="da927-241">透過轉換，所有屬性類別都會以後置詞 `Attribute` 結尾。</span><span class="sxs-lookup"><span data-stu-id="da927-241">By convention, all Attribute classes end in the suffix `Attribute`.</span></span> <span data-ttu-id="da927-242">不過，當您套用屬性時，並不需要使用該後置詞。</span><span class="sxs-lookup"><span data-stu-id="da927-242">However, you do not need to use that suffix when you apply an attribute.</span></span> 

<span data-ttu-id="da927-243">`DataContract` 和 `DataMember` 屬性位於不同的程式庫中，因此您將必須把該程式庫新增到 C# 專案檔中作為相依性。</span><span class="sxs-lookup"><span data-stu-id="da927-243">The `DataContract` and `DataMember` attributes are in a different library, so you'll need to add that library to your C# project file as a dependency.</span></span> <span data-ttu-id="da927-244">請將下列行新增到您專案檔中的 `<ItemGroup>` 區段：</span><span class="sxs-lookup"><span data-stu-id="da927-244">Add the following line to the `<ItemGroup>` section of your project file:</span></span>

```xml
<PackageReference Include="System.Runtime.Serialization.Primitives" Version="4.3.0" />
```

<span data-ttu-id="da927-245">在您儲存檔案之後，請執行 `dotnet restore` ([參閱附註](#dotnet-restore-note)) 來擷取此套件。</span><span class="sxs-lookup"><span data-stu-id="da927-245">After you save the file, run `dotnet restore` ([see note](#dotnet-restore-note)) to retrieve this package.</span></span>

<span data-ttu-id="da927-246">接著，開啟 `repo.cs` 檔案。</span><span class="sxs-lookup"><span data-stu-id="da927-246">Next, open the `repo.cs` file.</span></span> <span data-ttu-id="da927-247">讓我們變更名稱以使用「Pascal 命名法的大小寫」，並完整拼出名稱 `Repository`。</span><span class="sxs-lookup"><span data-stu-id="da927-247">Let's change the name to use Pascal Case, and fully spell out the name `Repository`.</span></span> <span data-ttu-id="da927-248">我們仍然想要將 JSON 'repo' 節點對應到這個型別，因此您將必須把 `DataContract` 屬性新增到類別宣告。</span><span class="sxs-lookup"><span data-stu-id="da927-248">We still want to map JSON 'repo' nodes to this type, so you'll need to add the `DataContract` attribute to the class declaration.</span></span> <span data-ttu-id="da927-249">您將把該屬性的 `Name` 屬性設定為與此型別對應之 JSON 節點的名稱：</span><span class="sxs-lookup"><span data-stu-id="da927-249">You'll set the `Name` property of the attribute to the name of the JSON nodes that map to this type:</span></span>

```csharp
[DataContract(Name="repo")]
public class Repository
```

<span data-ttu-id="da927-250"><xref:System.Runtime.Serialization.DataContractAttribute> 是 <xref:System.Runtime.Serialization> 命名空間的成員，因此您將必須在檔案的開頭新增適當的 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="da927-250">The <xref:System.Runtime.Serialization.DataContractAttribute> is a member of the <xref:System.Runtime.Serialization> namespace, so you'll need to add the appropriate `using` statement at the top of the file:</span></span>

```csharp
using System.Runtime.Serialization;
```

<span data-ttu-id="da927-251">您已將 `repo` 類別的名稱變更為 `Repository`，因此您將必須在 Program.cs 中進行相同的名稱變更 (有些編輯器可能支援可自動進行這項變更的重新命名重構功能)：</span><span class="sxs-lookup"><span data-stu-id="da927-251">You changed the name of the `repo` class to `Repository`, so you'll need to make the same name change in Program.cs (some editors may support a rename refactoring that will make this change automatically:)</span></span>

```csharp
var serializer = new DataContractJsonSerializer(typeof(List<Repository>));

// ...

var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
```

<span data-ttu-id="da927-252">接著，讓我們使用 <xref:System.Runtime.Serialization.DataMemberAttribute> 類別來以 `name` 欄位進行相同的變更。</span><span class="sxs-lookup"><span data-stu-id="da927-252">Next, let's make the same change with the `name` field by using the <xref:System.Runtime.Serialization.DataMemberAttribute> class.</span></span> <span data-ttu-id="da927-253">請對 repo.cs 中 `name` 欄位的宣告進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="da927-253">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[DataMember(Name="name")]
public string Name;
```

<span data-ttu-id="da927-254">這項變更意謂著您必須變更 program.cs 中寫入每個儲存機制名稱的程式碼：</span><span class="sxs-lookup"><span data-stu-id="da927-254">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="da927-255">請執行 `dotnet build` 再接著執行 `dotnet run` 以確保您的對應正確。</span><span class="sxs-lookup"><span data-stu-id="da927-255">Do a `dotnet build` followed by a `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="da927-256">您應該會看到與之前相同的輸出。</span><span class="sxs-lookup"><span data-stu-id="da927-256">You should see the same output as before.</span></span> <span data-ttu-id="da927-257">在處理更多來自 Web 伺服器的屬性之前，讓我們先對 `Repository` 類別再多進行一項變更。</span><span class="sxs-lookup"><span data-stu-id="da927-257">Before we process more properties from the web server, let's make one more change to the `Repository` class.</span></span> <span data-ttu-id="da927-258">`Name` 成員是一個可公開存取的欄位。</span><span class="sxs-lookup"><span data-stu-id="da927-258">The `Name` member is a publicly accessible field.</span></span> <span data-ttu-id="da927-259">這並非一個理想的物件導向做法，因此讓我們將它變更成屬性。</span><span class="sxs-lookup"><span data-stu-id="da927-259">That's not a good object-oriented practice, so let's change it to a property.</span></span> <span data-ttu-id="da927-260">就我們的目的而言，當取得或設定該屬性時，我們並不需要執行任何特定的程式碼，但變更成屬性可讓稍後新增這些變更變得更容易，而不會破壞使用 `Repository` 類別的任何程式碼。</span><span class="sxs-lookup"><span data-stu-id="da927-260">For our purposes, we don't need any specific code to run when getting or setting the property, but changing to a property makes it easier to add those changes later without breaking any code that uses the `Repository` class.</span></span>

<span data-ttu-id="da927-261">請移除欄位定義，然後以[自動實作的屬性](../programming-guide/classes-and-structs/auto-implemented-properties.md)來取代它：</span><span class="sxs-lookup"><span data-stu-id="da927-261">Remove the field definition, and replace it with an [auto-implemented property](../programming-guide/classes-and-structs/auto-implemented-properties.md):</span></span>

```csharp
public string Name { get; set; }
```

<span data-ttu-id="da927-262">編譯器除了會產生用來儲存名稱的私用欄位之外，也會產生 `get` 和 `set` 存取子的主體。</span><span class="sxs-lookup"><span data-stu-id="da927-262">The compiler generates the body of the `get` and `set` accessors, as well as a private field to store the name.</span></span> <span data-ttu-id="da927-263">它會類似於以下您可以手動輸入的程式碼：</span><span class="sxs-lookup"><span data-stu-id="da927-263">It would be similar to the following code that you could type by hand:</span></span>

```csharp
public string Name 
{ 
    get { return this._name; }
    set { this._name = value; }
}
private string _name;
```

<span data-ttu-id="da927-264">讓我們在新增新功能之前，再多進行一項變更。</span><span class="sxs-lookup"><span data-stu-id="da927-264">Let's make one more change before adding new features.</span></span> <span data-ttu-id="da927-265">`ProcessRepositories` 方法可以執行非同步工作，然後傳回儲存機制的集合。</span><span class="sxs-lookup"><span data-stu-id="da927-265">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="da927-266">讓我們從該方法傳回 `List<Repository>`，並將寫入資訊的程式碼移到 `Main` 方法中。</span><span class="sxs-lookup"><span data-stu-id="da927-266">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="da927-267">請變更 `ProcessRepositories` 的簽章以傳回其結果為 `Repository` 物件清單的工作：</span><span class="sxs-lookup"><span data-stu-id="da927-267">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="da927-268">接著，在處理 JSON 回應後，直接傳回儲存機制：</span><span class="sxs-lookup"><span data-stu-id="da927-268">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

<span data-ttu-id="da927-269">編譯器會產生用於傳回的 `Task<T>` 物件，因為您已將此方法標示為 `async`。</span><span class="sxs-lookup"><span data-stu-id="da927-269">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="da927-270">接著，讓我們來修改 `Main` 方法，使它擷取那些結果並將每個儲存機制名稱寫入到主控台。</span><span class="sxs-lookup"><span data-stu-id="da927-270">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="da927-271">您的 `Main` 方法現在看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="da927-271">Your `Main` method now looks like this:</span></span>

```csharp
public static void Main(string[] args)
{
    var repositories = ProcessRepositories().Result;

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

<span data-ttu-id="da927-272">系統會封鎖存取工作之 `Result` 屬性的行為，直到工作完成為止。</span><span class="sxs-lookup"><span data-stu-id="da927-272">Accessing the `Result` property of a Task blocks until the task has completed.</span></span> <span data-ttu-id="da927-273">通常，您會偏好 `await` 工作完成，就像在 `ProcessRepositories` 方法中一樣，但在 `Main` 方法中並不允許這樣做。</span><span class="sxs-lookup"><span data-stu-id="da927-273">Normally, you would prefer to `await` the completion of the task, as in the `ProcessRepositories` method, but that isn't allowed in the `Main` method.</span></span>

## <a name="reading-more-information"></a><span data-ttu-id="da927-274">讀取更多資訊</span><span class="sxs-lookup"><span data-stu-id="da927-274">Reading More Information</span></span>

<span data-ttu-id="da927-275">讓我們再多處理 GitHub API 所傳送之 JSON 封包中的幾個屬性，來結束這個部分。</span><span class="sxs-lookup"><span data-stu-id="da927-275">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="da927-276">您不會想要全盤了解，但新增幾個屬性將可示範更多一些的 C# 語言功能。</span><span class="sxs-lookup"><span data-stu-id="da927-276">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="da927-277">讓我們從再多將幾個簡單型別新增到 `Repository` 類別定義著手。</span><span class="sxs-lookup"><span data-stu-id="da927-277">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="da927-278">請將下列屬性新增到該類別：</span><span class="sxs-lookup"><span data-stu-id="da927-278">Add these properties to that class:</span></span>

```csharp
[DataMember(Name="description")]
public string Description { get; set; }

[DataMember(Name="html_url")]
public Uri GitHubHomeUrl { get; set; }

[DataMember(Name="homepage")]
public Uri Homepage { get; set; }

[DataMember(Name="watchers")]
public int Watchers { get; set; }
```

<span data-ttu-id="da927-279">這些屬性具有從字串型別 (JSON 封包所包含的型別) 轉換成目標型別的內建轉換。</span><span class="sxs-lookup"><span data-stu-id="da927-279">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="da927-280">您可能不熟悉 <xref:System.Uri> 型別。</span><span class="sxs-lookup"><span data-stu-id="da927-280">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="da927-281">它代表 URI，或在此案例中是代表 URL。</span><span class="sxs-lookup"><span data-stu-id="da927-281">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="da927-282">在 `Uri` 和 `int` 型別的案例中，如果 JSON 封包包含不會轉換成目標型別的資料，序列化動作將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="da927-282">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="da927-283">在您新增這些屬性之後，請更新 `Main` 方法以顯示下列元素：</span><span class="sxs-lookup"><span data-stu-id="da927-283">Once you've added these, update the `Main` method to display those elements:</span></span>

```csharp
foreach (var repo in repositories)
{
    Console.WriteLine(repo.Name);
    Console.WriteLine(repo.Description);
    Console.WriteLine(repo.GitHubHomeUrl);
    Console.WriteLine(repo.Homepage);
    Console.WriteLine(repo.Watchers);
    Console.WriteLine();
}
```
<span data-ttu-id="da927-284">在最後一個步驟中，讓我們新增最後一個推送作業的資訊。</span><span class="sxs-lookup"><span data-stu-id="da927-284">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="da927-285">此資訊會在 JSON 回應中採用下列形式的格式：</span><span class="sxs-lookup"><span data-stu-id="da927-285">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="da927-286">該格式並不符合任何標準 .NET <xref:System.DateTime> 格式。</span><span class="sxs-lookup"><span data-stu-id="da927-286">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="da927-287">因此，您將需要撰寫一個自訂的轉換方法。</span><span class="sxs-lookup"><span data-stu-id="da927-287">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="da927-288">您可能也不會想要對 `Repository` 類別的使用者公開原始字串。</span><span class="sxs-lookup"><span data-stu-id="da927-288">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="da927-289">屬性也可以幫助控制該行為。</span><span class="sxs-lookup"><span data-stu-id="da927-289">Attributes can help control that as well.</span></span> <span data-ttu-id="da927-290">首先，請定義 `private` 屬性，此屬性將保存您 `Repository` 類別中日期時間的字串表示：</span><span class="sxs-lookup"><span data-stu-id="da927-290">First, define a `private` property that will hold the string representation of the date time in your `Repository` class:</span></span>

```csharp
[DataMember(Name="pushed_at")]
private string JsonDate { get; set; }
```

<span data-ttu-id="da927-291">`DataMember` 屬性會通知序列化程式應該處理此屬性，即使它並非公用成員。</span><span class="sxs-lookup"><span data-stu-id="da927-291">The `DataMember` attribute informs the serializer that this should be processed, even though it is not a public member.</span></span> <span data-ttu-id="da927-292">接著，您需要撰寫一個公用的唯讀屬性來將字串轉換成有效的 <xref:System.DateTime> 物件，並傳回該 <xref:System.DateTime>：</span><span class="sxs-lookup"><span data-stu-id="da927-292">Next, you need to write a public read-only property that converts the string to a valid <xref:System.DateTime> object, and returns that <xref:System.DateTime>:</span></span>

```csharp
[IgnoreDataMember]
public DateTime LastPush
{
    get
    {
        return DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
    }
}
```

<span data-ttu-id="da927-293">讓我們來檢查上述的新建構。</span><span class="sxs-lookup"><span data-stu-id="da927-293">Let's go over the new constructs above.</span></span> <span data-ttu-id="da927-294">`IgnoreDataMember` 屬性會指示序列化程式不應該將此型別讀取到任何 JSON 物件，或從任何 JSON 物件寫入此型別。</span><span class="sxs-lookup"><span data-stu-id="da927-294">The `IgnoreDataMember` attribute instructs the serializer that this type should not be read to or written from any JSON object.</span></span> <span data-ttu-id="da927-295">此屬性只包含 `get` 存取子。</span><span class="sxs-lookup"><span data-stu-id="da927-295">This property contains only a `get` accessor.</span></span> <span data-ttu-id="da927-296">沒有 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="da927-296">There is no `set` accessor.</span></span> <span data-ttu-id="da927-297">這就是您以 C# 定義「唯讀」屬性的方式。</span><span class="sxs-lookup"><span data-stu-id="da927-297">That's how you define a *read-only* property in C#.</span></span> <span data-ttu-id="da927-298">(是的，您可以用 C# 來建立「唯寫」屬性，但其值會受到限制)。<xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> 方法會剖析字串並使用提供的日期格式來建立 <xref:System.DateTime> 物件，然後使用 `CultureInfo` 物件為 `DateTime` 新增額外的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="da927-298">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="da927-299">如果剖析作業失敗，屬性存取子就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="da927-299">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="da927-300">若要使用 <xref:System.Globalization.CultureInfo.InvariantCulture> ，您將必須把 <xref:System.Globalization> 命名空間新增到 `repo.cs` 中的 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="da927-300">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` statements in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="da927-301">最後，請在主控台中再多新增一個輸出陳述式，這樣您便已準備好來重新建置及執行此應用程式：</span><span class="sxs-lookup"><span data-stu-id="da927-301">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="da927-302">您的版本現在應該與[完成範例](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient)相符。</span><span class="sxs-lookup"><span data-stu-id="da927-302">Your version should now match the [finished sample](https://github.com/dotnet/docs/tree/master/samples/csharp/getting-started/console-webapiclient).</span></span>
 
## <a name="conclusion"></a><span data-ttu-id="da927-303">結論</span><span class="sxs-lookup"><span data-stu-id="da927-303">Conclusion</span></span>

<span data-ttu-id="da927-304">本教學課程示範了如何提出 Web 要求、剖析結果，以及顯示這些結果的屬性。</span><span class="sxs-lookup"><span data-stu-id="da927-304">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="da927-305">您也在專案中新增了新的套件作為相依性。</span><span class="sxs-lookup"><span data-stu-id="da927-305">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="da927-306">您已了解一些支援物件導向技術的 C# 語言功能。</span><span class="sxs-lookup"><span data-stu-id="da927-306">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
