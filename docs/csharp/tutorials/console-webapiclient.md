---
title: 使用 .NET Core 來建立 REST 用戶端
description: 本教學課程會教導您一些 .NET Core 和 C# 語言中的功能。
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 9478966598a9aaa1e9f592b72afce8f878a38abf
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964413"
---
# <a name="rest-client"></a><span data-ttu-id="69c4b-103">REST 用戶端</span><span class="sxs-lookup"><span data-stu-id="69c4b-103">REST client</span></span>

## <a name="introduction"></a><span data-ttu-id="69c4b-104">簡介</span><span class="sxs-lookup"><span data-stu-id="69c4b-104">Introduction</span></span>

<span data-ttu-id="69c4b-105">本教學課程會教導您一些 .NET Core 和 C# 語言中的功能。</span><span class="sxs-lookup"><span data-stu-id="69c4b-105">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="69c4b-106">您將了解：</span><span class="sxs-lookup"><span data-stu-id="69c4b-106">You’ll learn:</span></span>

* <span data-ttu-id="69c4b-107">「.NET Core 命令列介面」(CLI) 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="69c4b-107">The basics of the .NET Core Command Line Interface (CLI).</span></span>
* <span data-ttu-id="69c4b-108">「C# 語言」功能的概觀。</span><span class="sxs-lookup"><span data-stu-id="69c4b-108">An overview of C# Language features.</span></span>
* <span data-ttu-id="69c4b-109">使用 NuGet 來管理相依性</span><span class="sxs-lookup"><span data-stu-id="69c4b-109">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="69c4b-110">HTTP 通訊</span><span class="sxs-lookup"><span data-stu-id="69c4b-110">HTTP Communications</span></span>
* <span data-ttu-id="69c4b-111">處理 JSON 資訊</span><span class="sxs-lookup"><span data-stu-id="69c4b-111">Processing JSON information</span></span>
* <span data-ttu-id="69c4b-112">使用「屬性」來管理組態。</span><span class="sxs-lookup"><span data-stu-id="69c4b-112">Managing configuration with Attributes.</span></span>

<span data-ttu-id="69c4b-113">您將建置一個對 GitHub 上的 REST 服務發出「HTTP 要求」的應用程式。</span><span class="sxs-lookup"><span data-stu-id="69c4b-113">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="69c4b-114">您將讀取 JSON 格式的資訊，並將該 JSON 封包轉換成 C# 物件。</span><span class="sxs-lookup"><span data-stu-id="69c4b-114">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="69c4b-115">最後，您將了解如何使用 C# 物件。</span><span class="sxs-lookup"><span data-stu-id="69c4b-115">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="69c4b-116">本教學課程中有許多功能。</span><span class="sxs-lookup"><span data-stu-id="69c4b-116">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="69c4b-117">讓我們來逐一建置它們。</span><span class="sxs-lookup"><span data-stu-id="69c4b-117">Let’s build them one by one.</span></span>

<span data-ttu-id="69c4b-118">如果您偏好追蹤本主題的[最終範例](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient)，則可以下載它。</span><span class="sxs-lookup"><span data-stu-id="69c4b-118">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="69c4b-119">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="69c4b-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="69c4b-120">必要條件：</span><span class="sxs-lookup"><span data-stu-id="69c4b-120">Prerequisites</span></span>

<span data-ttu-id="69c4b-121">您將必須設定電腦以執行 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="69c4b-121">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="69c4b-122">您可以在[.Net Core 下載](https://dotnet.microsoft.com/download)頁面上找到安裝指示。</span><span class="sxs-lookup"><span data-stu-id="69c4b-122">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="69c4b-123">您可以在 Windows、Linux、macOS 或是 Docker 容器中執行此應用程式。</span><span class="sxs-lookup"><span data-stu-id="69c4b-123">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="69c4b-124">您將必須安裝慣用的程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="69c4b-124">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="69c4b-125">以下說明使用 [Visual Studio Code (英文)](https://code.visualstudio.com/)，這是開放原始碼的跨平台編輯器。</span><span class="sxs-lookup"><span data-stu-id="69c4b-125">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="69c4b-126">不過，您可以使用您熟悉的任何工具。</span><span class="sxs-lookup"><span data-stu-id="69c4b-126">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="69c4b-127">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="69c4b-127">Create the Application</span></span>

<span data-ttu-id="69c4b-128">第一個步驟是建立新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="69c4b-128">The first step is to create a new application.</span></span> <span data-ttu-id="69c4b-129">請開啟命令提示字元，然後為您的應用程式建立新目錄。</span><span class="sxs-lookup"><span data-stu-id="69c4b-129">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="69c4b-130">使該目錄成為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="69c4b-130">Make that the current directory.</span></span> <span data-ttu-id="69c4b-131">在主控台視窗中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="69c4b-131">Enter the following command in a console window:</span></span>

```dotnetcli
dotnet new console --name WebApiClient
```

<span data-ttu-id="69c4b-132">這會建立基本 "Hello World" 應用程式的起始檔案。</span><span class="sxs-lookup"><span data-stu-id="69c4b-132">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="69c4b-133">專案名稱為 "WebApiClient"。</span><span class="sxs-lookup"><span data-stu-id="69c4b-133">The project name is "WebApiClient".</span></span> <span data-ttu-id="69c4b-134">由於這是新的專案，目前沒有任何相依性，因此第一次執行時會下載 .NET Core Framework、安裝開發憑證並執行 NuGet 套件管理員，以還原缺少的相依性。</span><span class="sxs-lookup"><span data-stu-id="69c4b-134">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework, install a development certificate and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="69c4b-135">在您開始建立修改前，請先在命令提示字元中鍵入 `dotnet run` ([請參閱附註](#dotnet-restore-note))，執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="69c4b-135">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="69c4b-136">如果您的環境缺少相依性，`dotnet run` 會自動執行 `dotnet restore`。</span><span class="sxs-lookup"><span data-stu-id="69c4b-136">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="69c4b-137">如果您的應用程式需要重建，它也會執行 `dotnet build`。</span><span class="sxs-lookup"><span data-stu-id="69c4b-137">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="69c4b-138">在初始安裝之後，當它對您的專案有意義時，您只需要執行 `dotnet restore` 或 `dotnet build`。</span><span class="sxs-lookup"><span data-stu-id="69c4b-138">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="69c4b-139">新增新的相依性</span><span class="sxs-lookup"><span data-stu-id="69c4b-139">Adding New Dependencies</span></span>

<span data-ttu-id="69c4b-140">.NET Core 的其中一個主要設計目標就是將 .NET 安裝大小縮減到最小。</span><span class="sxs-lookup"><span data-stu-id="69c4b-140">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="69c4b-141">如果應用程式的某些功能需要額外的程式庫，您可以將這些相依性新增到 C# 專案檔 (\*.csproj) 中。</span><span class="sxs-lookup"><span data-stu-id="69c4b-141">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="69c4b-142">在我們的範例中，您必須新增 `System.Runtime.Serialization.Json` 套件，讓您的應用程式可以處理 JSON 回應。</span><span class="sxs-lookup"><span data-stu-id="69c4b-142">For our example, you'll need to add the `System.Runtime.Serialization.Json` package, so your application can process JSON responses.</span></span>

<span data-ttu-id="69c4b-143">您將需要此應用程式的 `System.Runtime.Serialization.Json` 套件。</span><span class="sxs-lookup"><span data-stu-id="69c4b-143">You'll need the `System.Runtime.Serialization.Json` package for this application.</span></span> <span data-ttu-id="69c4b-144">執行下列[.NET CLI](../../core/tools/dotnet-add-package.md)命令，將它新增至您的專案：</span><span class="sxs-lookup"><span data-stu-id="69c4b-144">Add it to your project by running the following [.NET CLI](../../core/tools/dotnet-add-package.md) command:</span></span>

```console
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a><span data-ttu-id="69c4b-145">提出 Web 要求</span><span class="sxs-lookup"><span data-stu-id="69c4b-145">Making Web Requests</span></span>

<span data-ttu-id="69c4b-146">現在您已經準備好開始從 Web 接收資料。</span><span class="sxs-lookup"><span data-stu-id="69c4b-146">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="69c4b-147">在此應用程式中，您將從 [GitHub API](https://developer.github.com/v3/) 讀取資訊。</span><span class="sxs-lookup"><span data-stu-id="69c4b-147">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="69c4b-148">讓我們在 [.NET Foundation](https://www.dotnetfoundation.org/) 的庇護下讀取專案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="69c4b-148">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="69c4b-149">您將從對 GitHub API 提出要求以擷取專案相關資訊著手。</span><span class="sxs-lookup"><span data-stu-id="69c4b-149">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="69c4b-150">您將使用的端點是：<https://api.github.com/orgs/dotnet/repos>。</span><span class="sxs-lookup"><span data-stu-id="69c4b-150">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="69c4b-151">您想要擷取這些專案的所有相關資訊，因此您將使用 HTTP GET 要求。</span><span class="sxs-lookup"><span data-stu-id="69c4b-151">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="69c4b-152">您的瀏覽器也會使用 HTTP GET 要求，因此您可以將該 URL 貼到瀏覽器中，以查看您將接收和處理的資訊。</span><span class="sxs-lookup"><span data-stu-id="69c4b-152">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="69c4b-153">您需使用 <xref:System.Net.Http.HttpClient> 類別來提出 Web 要求。</span><span class="sxs-lookup"><span data-stu-id="69c4b-153">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="69c4b-154">與所有新式 .NET API 相同，<xref:System.Net.Http.HttpClient> 針對它的長時間執行 API 只支援非同步方法。</span><span class="sxs-lookup"><span data-stu-id="69c4b-154">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="69c4b-155">請從建立非同步方法著手。</span><span class="sxs-lookup"><span data-stu-id="69c4b-155">Start by making an async method.</span></span> <span data-ttu-id="69c4b-156">您將在建置應用程式的功能時填入實作。</span><span class="sxs-lookup"><span data-stu-id="69c4b-156">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="69c4b-157">請從開啟您專案目錄中的 `program.cs` 檔案並將下列方法新增到 `Program` 類別著手：</span><span class="sxs-lookup"><span data-stu-id="69c4b-157">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="69c4b-158">您將必須在 `Main` 方法上面新增 `using` 陳述式，如此 C# 編譯器才能夠辨識 <xref:System.Threading.Tasks.Task> 型別：</span><span class="sxs-lookup"><span data-stu-id="69c4b-158">You'll need to add a `using` statement at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="69c4b-159">如果您在此時建置專案，您將會收到針對此方法產生的警告，因為它不包含任何 `await` 運算子，所以將會以同步方式執行。</span><span class="sxs-lookup"><span data-stu-id="69c4b-159">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="69c4b-160">目前請先忽略該警告；您將在填入方法時新增 `await` 運算子。</span><span class="sxs-lookup"><span data-stu-id="69c4b-160">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="69c4b-161">接著，請將 `namespace` 陳述式中定義的命名空間從其預設值 `ConsoleApp` 重新命名為 `WebAPIClient`。</span><span class="sxs-lookup"><span data-stu-id="69c4b-161">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="69c4b-162">我們稍後將會在此命名空間中定義 `repo` 類別。</span><span class="sxs-lookup"><span data-stu-id="69c4b-162">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="69c4b-163">接著，請將 `Main` 方法更新成呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="69c4b-163">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="69c4b-164">`ProcessRepositories` 方法會傳回一個工作，而在該工作完成之前，您不應該結束程式。</span><span class="sxs-lookup"><span data-stu-id="69c4b-164">The `ProcessRepositories` method returns a Task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="69c4b-165">因此，您必須變更 `Main`的簽章。</span><span class="sxs-lookup"><span data-stu-id="69c4b-165">Therefore, you must change the signature of `Main`.</span></span> <span data-ttu-id="69c4b-166">新增 `async` 修飾詞，並將傳回類型變更為 `Task`。</span><span class="sxs-lookup"><span data-stu-id="69c4b-166">Add the `async` modifier, and change the return type to `Task`.</span></span> <span data-ttu-id="69c4b-167">然後，在方法的主體中，新增對 `ProcessRepositories`的呼叫。</span><span class="sxs-lookup"><span data-stu-id="69c4b-167">Then, in the body of the method, add a call to `ProcessRepositories`.</span></span> <span data-ttu-id="69c4b-168">將 `await` 關鍵字新增至該方法呼叫：</span><span class="sxs-lookup"><span data-stu-id="69c4b-168">Add the `await` keyword when to that method call:</span></span>

```csharp
static Task Main(string[] args)
{
    await ProcessRepositories();
}
```

<span data-ttu-id="69c4b-169">現在，您擁有一個不會執行任何動作但會以非同步方式執行的程式。</span><span class="sxs-lookup"><span data-stu-id="69c4b-169">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="69c4b-170">來加以改善吧。</span><span class="sxs-lookup"><span data-stu-id="69c4b-170">Let's improve it.</span></span>

<span data-ttu-id="69c4b-171">首先，您需要一個能夠從網路擷取資料的物件；使用 <xref:System.Net.Http.HttpClient> 即可達成。</span><span class="sxs-lookup"><span data-stu-id="69c4b-171">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="69c4b-172">此物件會處理要求和回應。</span><span class="sxs-lookup"><span data-stu-id="69c4b-172">This object handles the request and the responses.</span></span> <span data-ttu-id="69c4b-173">在 Program.cs 檔案內，將 `Program` 類別中該類型的單一執行個體具現化。</span><span class="sxs-lookup"><span data-stu-id="69c4b-173">Instantiate a single instance of that type in the `Program` class inside the Program.cs file.</span></span>

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static Task Main(string[] args)
        {
            //...
        }
    }
}
```

<span data-ttu-id="69c4b-174">讓我們回到 `ProcessRepositories` 方法並填入其第一個版本：</span><span class="sxs-lookup"><span data-stu-id="69c4b-174">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="69c4b-175">您將必須在檔案開頭一併新增兩個新的 using 陳述式以讓此檔案進行編譯：</span><span class="sxs-lookup"><span data-stu-id="69c4b-175">You'll need to also add two new using statements at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="69c4b-176">第一個版本會提出 Web 要求來讀取 dotnet foundation 組織底下的所有儲存機制清單。</span><span class="sxs-lookup"><span data-stu-id="69c4b-176">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="69c4b-177">(.NET Foundation 的 gitHub 識別碼是 'dotnet')。</span><span class="sxs-lookup"><span data-stu-id="69c4b-177">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="69c4b-178">前幾行會為這個要求設定 <xref:System.Net.Http.HttpClient>。</span><span class="sxs-lookup"><span data-stu-id="69c4b-178">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="69c4b-179">首先，會將它設定為接受 GitHub JSON 回應。</span><span class="sxs-lookup"><span data-stu-id="69c4b-179">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="69c4b-180">此格式就是 JSON。</span><span class="sxs-lookup"><span data-stu-id="69c4b-180">This format is simply JSON.</span></span> <span data-ttu-id="69c4b-181">下一行會將「使用者代理程式」標頭新增到來自此物件的所有要求。</span><span class="sxs-lookup"><span data-stu-id="69c4b-181">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="69c4b-182">這兩個標頭會受到 GitHub 伺服器程式碼檢查，並且是從 GitHub 擷取資訊的必要標頭。</span><span class="sxs-lookup"><span data-stu-id="69c4b-182">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="69c4b-183">設定 <xref:System.Net.Http.HttpClient> 之後，您需提出 Web 要求並擷取回應。</span><span class="sxs-lookup"><span data-stu-id="69c4b-183">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="69c4b-184">在這個第一版中，您會使用 <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> 便利方法。</span><span class="sxs-lookup"><span data-stu-id="69c4b-184">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="69c4b-185">這個便利方法會啟動一個提出 Web 要求的工作，然後當要求返回時，它會讀取回應資料流並從該資料流擷取內容。</span><span class="sxs-lookup"><span data-stu-id="69c4b-185">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="69c4b-186">回應本文會以 <xref:System.String> 的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="69c4b-186">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="69c4b-187">當工作完成時，就會提供該字串。</span><span class="sxs-lookup"><span data-stu-id="69c4b-187">The string is available when the task completes.</span></span>

<span data-ttu-id="69c4b-188">此方法的最後兩行會等候該工作，然後將回應顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="69c4b-188">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="69c4b-189">請建置應用程式並執行它。</span><span class="sxs-lookup"><span data-stu-id="69c4b-189">Build the app, and run it.</span></span> <span data-ttu-id="69c4b-190">建置警告現在已消失，因為 `ProcessRepositories` 現在確實包含 `await` 運算子。</span><span class="sxs-lookup"><span data-stu-id="69c4b-190">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="69c4b-191">您將會看到一長串顯示的 JSON 格式文字。</span><span class="sxs-lookup"><span data-stu-id="69c4b-191">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="69c4b-192">處理 JSON 結果</span><span class="sxs-lookup"><span data-stu-id="69c4b-192">Processing the JSON Result</span></span>

<span data-ttu-id="69c4b-193">此時，您已撰寫程式碼來從 Web 伺服器擷取回應，並顯示包含在該回應中的文字。</span><span class="sxs-lookup"><span data-stu-id="69c4b-193">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="69c4b-194">接著，讓我們將該 JSON 回應轉換成 C# 物件。</span><span class="sxs-lookup"><span data-stu-id="69c4b-194">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="69c4b-195"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> 類別會將物件序列化為 JSON，並將 JSON 還原序列化為物件。</span><span class="sxs-lookup"><span data-stu-id="69c4b-195">The <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> class serializes objects to JSON and deserializes JSON into objects.</span></span> <span data-ttu-id="69c4b-196">一開始請先定義類別，以代表從 GitHub API 傳回的 `repo` JSON 物件：</span><span class="sxs-lookup"><span data-stu-id="69c4b-196">Start by defining a class to represent the `repo` JSON object returned from the GitHub API:</span></span>

```csharp
using System;

namespace WebAPIClient
{
    public class Repository
    {
        public string name { get; set; };
    }
}
```

<span data-ttu-id="69c4b-197">請將上述程式碼放在名為 'repo.cs' 的新檔案中。</span><span class="sxs-lookup"><span data-stu-id="69c4b-197">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="69c4b-198">這個類別版本代表處理 JSON 資料的最簡單路徑。</span><span class="sxs-lookup"><span data-stu-id="69c4b-198">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="69c4b-199">類別名稱和成員名稱會符合 JSON 封包中使用的名稱，而不是符合下列 C# 慣例。</span><span class="sxs-lookup"><span data-stu-id="69c4b-199">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="69c4b-200">您將在稍後藉由提供一些其他組態屬性來修正此問題。</span><span class="sxs-lookup"><span data-stu-id="69c4b-200">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="69c4b-201">此類別示範了 JSON 序列化和還原序列化的另一個重要功能：並非 JSON 封包中的所有欄位都屬於此類別。</span><span class="sxs-lookup"><span data-stu-id="69c4b-201">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="69c4b-202">JSON 序列化程式將會忽略未包含在所要使用之類別型別中的資訊。</span><span class="sxs-lookup"><span data-stu-id="69c4b-202">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="69c4b-203">這個功能可讓您更容易建立只對 JSON 封包中的欄位子集有作用的型別。</span><span class="sxs-lookup"><span data-stu-id="69c4b-203">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="69c4b-204">現在您已經建立型別，讓我們來將它還原序列化。</span><span class="sxs-lookup"><span data-stu-id="69c4b-204">Now that you've created the type, let's deserialize it.</span></span> 

<span data-ttu-id="69c4b-205">接著，您將使用序列化程式將 JSON 轉換成 C# 物件。</span><span class="sxs-lookup"><span data-stu-id="69c4b-205">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="69c4b-206">將您 `ProcessRepositories` 方法中 <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> 的呼叫取代為下列三行：</span><span class="sxs-lookup"><span data-stu-id="69c4b-206">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following three lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

<span data-ttu-id="69c4b-207">您使用的是新的命名空間，因此您也必須將它新增至檔案頂端：</span><span class="sxs-lookup"><span data-stu-id="69c4b-207">You're using a new namespace, so you'll need to add it at the top of the file as well:</span></span>

```csharp
using System.Text.Json;
```

<span data-ttu-id="69c4b-208">請注意，您現在使用的是 <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> 而不是 <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>。</span><span class="sxs-lookup"><span data-stu-id="69c4b-208">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="69c4b-209">序列化程式會使用資料流 (而不是字串) 作為其來源。</span><span class="sxs-lookup"><span data-stu-id="69c4b-209">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="69c4b-210">讓我們來說明上述程式碼片段第C#二行中所使用的一些語言功能。</span><span class="sxs-lookup"><span data-stu-id="69c4b-210">Let's explain a couple features of the C# language that are being used in the second line of the preceding code snippet.</span></span> <span data-ttu-id="69c4b-211"><xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> 的第一個引數是 `await` 運算式。</span><span class="sxs-lookup"><span data-stu-id="69c4b-211">The first argument to <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> is an `await` expression.</span></span> <span data-ttu-id="69c4b-212">（其他兩個參數是選擇性的，而且會在程式碼片段中省略）。Await 運算式可以出現在您程式碼中的任何位置，雖然目前為止，您只會看到它們是指派語句的一部分。</span><span class="sxs-lookup"><span data-stu-id="69c4b-212">(The other two parameters are optional and are omitted in the code snippet.) Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span> <span data-ttu-id="69c4b-213">`Deserialize` 方法是*泛型*，這表示您必須提供類型引數，以供應該從 JSON 文字建立的物件種類。</span><span class="sxs-lookup"><span data-stu-id="69c4b-213">The `Deserialize` method is *generic*, which means you must supply type arguments for what kind of objects should be created from the JSON text.</span></span> <span data-ttu-id="69c4b-214">在此範例中，您要還原序列化為 `List<Repository>`，也就是另一個泛型物件，也就是 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="69c4b-214">In this example, you're deserializing to a `List<Repository>`, which is another generic object, the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="69c4b-215">`List<>` 類別會儲存物件的集合。</span><span class="sxs-lookup"><span data-stu-id="69c4b-215">The `List<>` class stores a collection of objects.</span></span> <span data-ttu-id="69c4b-216">型別引數會宣告儲存在 `List<>`中的物件類型。</span><span class="sxs-lookup"><span data-stu-id="69c4b-216">The type argument declares the type of objects stored in the `List<>`.</span></span> <span data-ttu-id="69c4b-217">JSON 文字代表存放庫物件的集合，因此 `Repository`類型引數。</span><span class="sxs-lookup"><span data-stu-id="69c4b-217">The JSON text represents a collection of repo objects, so the type argument is `Repository`.</span></span>

<span data-ttu-id="69c4b-218">您差不多已經完成這個部分。</span><span class="sxs-lookup"><span data-stu-id="69c4b-218">You're almost done with this section.</span></span> <span data-ttu-id="69c4b-219">現在您已將 JSON 轉換成 C# 物件，讓我們來顯示每個儲存機制的名稱。</span><span class="sxs-lookup"><span data-stu-id="69c4b-219">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="69c4b-220">將下列幾行：</span><span class="sxs-lookup"><span data-stu-id="69c4b-220">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="69c4b-221">取代為：</span><span class="sxs-lookup"><span data-stu-id="69c4b-221">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="69c4b-222">編譯並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="69c4b-222">Compile and run the application.</span></span> <span data-ttu-id="69c4b-223">它將會列印出隸屬於 .NET Foundation 的儲存機制名稱。</span><span class="sxs-lookup"><span data-stu-id="69c4b-223">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="69c4b-224">控制序列化</span><span class="sxs-lookup"><span data-stu-id="69c4b-224">Controlling Serialization</span></span>

<span data-ttu-id="69c4b-225">在您新增更多功能之前，讓我們先使用 `[JsonPropertyName]` 屬性來處理 `name` 屬性。</span><span class="sxs-lookup"><span data-stu-id="69c4b-225">Before you add more features, let's address the `name` property by using the `[JsonPropertyName]` attribute.</span></span> <span data-ttu-id="69c4b-226">請對 repo.cs 中 `name` 欄位的宣告進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="69c4b-226">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

<span data-ttu-id="69c4b-227">這項變更意謂著您必須變更 program.cs 中寫入每個儲存機制名稱的程式碼：</span><span class="sxs-lookup"><span data-stu-id="69c4b-227">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="69c4b-228">執行 `dotnet run` 以確定對應正確。</span><span class="sxs-lookup"><span data-stu-id="69c4b-228">Execute `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="69c4b-229">您應該會看到與之前相同的輸出。</span><span class="sxs-lookup"><span data-stu-id="69c4b-229">You should see the same output as before.</span></span>

<span data-ttu-id="69c4b-230">讓我們在新增新功能之前，再多進行一項變更。</span><span class="sxs-lookup"><span data-stu-id="69c4b-230">Let's make one more change before adding new features.</span></span> <span data-ttu-id="69c4b-231">`ProcessRepositories` 方法可以執行非同步工作，然後傳回儲存機制的集合。</span><span class="sxs-lookup"><span data-stu-id="69c4b-231">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="69c4b-232">讓我們從該方法傳回 `List<Repository>`，並將寫入資訊的程式碼移到 `Main` 方法中。</span><span class="sxs-lookup"><span data-stu-id="69c4b-232">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="69c4b-233">請變更 `ProcessRepositories` 的簽章以傳回其結果為 `Repository` 物件清單的工作：</span><span class="sxs-lookup"><span data-stu-id="69c4b-233">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="69c4b-234">接著，在處理 JSON 回應後，直接傳回儲存機制：</span><span class="sxs-lookup"><span data-stu-id="69c4b-234">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var repositories = serializer.ReadObject(await streamTask) as List<Repository>;
return repositories;
```

<span data-ttu-id="69c4b-235">編譯器會產生用於傳回的 `Task<T>` 物件，因為您已將此方法標示為 `async`。</span><span class="sxs-lookup"><span data-stu-id="69c4b-235">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="69c4b-236">接著，讓我們來修改 `Main` 方法，使它擷取那些結果並將每個儲存機制名稱寫入到主控台。</span><span class="sxs-lookup"><span data-stu-id="69c4b-236">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="69c4b-237">您的 `Main` 方法現在看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="69c4b-237">Your `Main` method now looks like this:</span></span>

```csharp
public static Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a><span data-ttu-id="69c4b-238">讀取更多資訊</span><span class="sxs-lookup"><span data-stu-id="69c4b-238">Reading More Information</span></span>

<span data-ttu-id="69c4b-239">讓我們再多處理 GitHub API 所傳送之 JSON 封包中的幾個屬性，來結束這個部分。</span><span class="sxs-lookup"><span data-stu-id="69c4b-239">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="69c4b-240">您不會想要全盤了解，但新增幾個屬性將可示範更多一些的 C# 語言功能。</span><span class="sxs-lookup"><span data-stu-id="69c4b-240">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="69c4b-241">讓我們從再多將幾個簡單型別新增到 `Repository` 類別定義著手。</span><span class="sxs-lookup"><span data-stu-id="69c4b-241">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="69c4b-242">請將下列屬性新增到該類別：</span><span class="sxs-lookup"><span data-stu-id="69c4b-242">Add these properties to that class:</span></span>

```csharp
[JsonPropertyName(Name="description")]
public string Description { get; set; }

[JsonPropertyName(Name="html_url")]
public Uri GitHubHomeUrl { get; set; }

[JsonPropertyName(Name="homepage")]
public Uri Homepage { get; set; }

[JsonPropertyName(Name="watchers")]
public int Watchers { get; set; }
```

<span data-ttu-id="69c4b-243">這些屬性具有從字串型別 (JSON 封包所包含的型別) 轉換成目標型別的內建轉換。</span><span class="sxs-lookup"><span data-stu-id="69c4b-243">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="69c4b-244">您可能不熟悉 <xref:System.Uri> 型別。</span><span class="sxs-lookup"><span data-stu-id="69c4b-244">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="69c4b-245">它代表 URI，或在此案例中是代表 URL。</span><span class="sxs-lookup"><span data-stu-id="69c4b-245">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="69c4b-246">在 `Uri` 和 `int` 型別的案例中，如果 JSON 封包包含不會轉換成目標型別的資料，序列化動作將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="69c4b-246">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="69c4b-247">在您新增這些屬性之後，請更新 `Main` 方法以顯示下列元素：</span><span class="sxs-lookup"><span data-stu-id="69c4b-247">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="69c4b-248">在最後一個步驟中，讓我們新增最後一個推送作業的資訊。</span><span class="sxs-lookup"><span data-stu-id="69c4b-248">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="69c4b-249">此資訊會在 JSON 回應中採用下列形式的格式：</span><span class="sxs-lookup"><span data-stu-id="69c4b-249">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="69c4b-250">該格式並不符合任何標準 .NET <xref:System.DateTime> 格式。</span><span class="sxs-lookup"><span data-stu-id="69c4b-250">That format does not follow any of the standard .NET <xref:System.DateTime> formats.</span></span> <span data-ttu-id="69c4b-251">因此，您將需要撰寫一個自訂的轉換方法。</span><span class="sxs-lookup"><span data-stu-id="69c4b-251">Because of that, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="69c4b-252">您可能也不會想要對 `Repository` 類別的使用者公開原始字串。</span><span class="sxs-lookup"><span data-stu-id="69c4b-252">You also probably don't want the raw string exposed to users of the `Repository` class.</span></span> <span data-ttu-id="69c4b-253">屬性也可以幫助控制該行為。</span><span class="sxs-lookup"><span data-stu-id="69c4b-253">Attributes can help control that as well.</span></span> <span data-ttu-id="69c4b-254">首先，定義一個 `public` 屬性，以保存您 `Repository` 類別中日期和時間的字串表示，以及一個會傳回格式字串的 `LastPush` `readonly` 屬性，該字串代表所傳回的日期：</span><span class="sxs-lookup"><span data-stu-id="69c4b-254">First, define a `public` property that will hold the string representation of the date and time in your `Repository` class and a `LastPush` `readonly` property that returns a formatted string that represents the returned date:</span></span>

```csharp
[JsonPropertyName(Name="pushed_at")]
public string JsonDate { get; set; }

public DateTime LastPush =>
    DateTime.ParseExact(JsonDate, "yyyy-MM-ddTHH:mm:ssZ", CultureInfo.InvariantCulture);
```

<span data-ttu-id="69c4b-255">讓我們來看一下我們剛才定義的新結構。</span><span class="sxs-lookup"><span data-stu-id="69c4b-255">Let's go over the new constructs we just defined.</span></span> <span data-ttu-id="69c4b-256">`LastPush` 屬性是使用 `get` 存取子的*運算式主體成員*所定義。</span><span class="sxs-lookup"><span data-stu-id="69c4b-256">The `LastPush` property is defined using an *expression-bodied member* for the `get` accessor.</span></span> <span data-ttu-id="69c4b-257">沒有 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="69c4b-257">There is no `set` accessor.</span></span> <span data-ttu-id="69c4b-258">省略 `set` 存取子是您在中C#定義*唯讀*屬性的方式。</span><span class="sxs-lookup"><span data-stu-id="69c4b-258">Omitting the `set` accessor is how you define a *read-only* property in C#.</span></span> <span data-ttu-id="69c4b-259">（是的，您可以在中C#建立*僅限寫入的*屬性，但其值有限）。<xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> 方法會剖析字串並使用提供的日期格式來建立 <xref:System.DateTime> 物件，並使用 `CultureInfo` 物件將額外的中繼資料新增至 `DateTime`。</span><span class="sxs-lookup"><span data-stu-id="69c4b-259">(Yes, you can create *write-only* properties in C#, but their value is limited.) The <xref:System.DateTime.ParseExact(System.String,System.String,System.IFormatProvider)> method parses a string and creates a <xref:System.DateTime> object using a provided date format, and adds additional metadata to the `DateTime` using a `CultureInfo` object.</span></span> <span data-ttu-id="69c4b-260">如果剖析作業失敗，屬性存取子就會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="69c4b-260">If the parse operation fails, the property accessor throws an exception.</span></span>

<span data-ttu-id="69c4b-261">若要使用 <xref:System.Globalization.CultureInfo.InvariantCulture> ，您將必須把 <xref:System.Globalization> 命名空間新增到 `repo.cs` 中的 `using` 陳述式：</span><span class="sxs-lookup"><span data-stu-id="69c4b-261">To use <xref:System.Globalization.CultureInfo.InvariantCulture>, you will need to add the <xref:System.Globalization> namespace to the `using` statements in `repo.cs`:</span></span>

```csharp
using System.Globalization;
```

<span data-ttu-id="69c4b-262">最後，請在主控台中再多新增一個輸出陳述式，這樣您便已準備好來重新建置及執行此應用程式：</span><span class="sxs-lookup"><span data-stu-id="69c4b-262">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="69c4b-263">您的版本現在應該與[完成範例](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient)相符。</span><span class="sxs-lookup"><span data-stu-id="69c4b-263">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="69c4b-264">結論</span><span class="sxs-lookup"><span data-stu-id="69c4b-264">Conclusion</span></span>

<span data-ttu-id="69c4b-265">本教學課程示範了如何提出 Web 要求、剖析結果，以及顯示這些結果的屬性。</span><span class="sxs-lookup"><span data-stu-id="69c4b-265">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="69c4b-266">您也在專案中新增了新的套件作為相依性。</span><span class="sxs-lookup"><span data-stu-id="69c4b-266">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="69c4b-267">您已了解一些支援物件導向技術的 C# 語言功能。</span><span class="sxs-lookup"><span data-stu-id="69c4b-267">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
