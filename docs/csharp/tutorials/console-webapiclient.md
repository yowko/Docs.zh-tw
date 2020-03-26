---
title: 使用 .NET Core 來建立 REST 用戶端
description: 本教學課程會教導您一些 .NET Core 和 C# 語言中的功能。
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: 0105db519f7accec6bf8bfbafdc6a67a444b1074
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249164"
---
# <a name="rest-client"></a><span data-ttu-id="fb0f4-103">REST 用戶端</span><span class="sxs-lookup"><span data-stu-id="fb0f4-103">REST client</span></span>

<span data-ttu-id="fb0f4-104">本教學課程會教導您一些 .NET Core 和 C# 語言中的功能。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="fb0f4-105">您將了解：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-105">You’ll learn:</span></span>

* <span data-ttu-id="fb0f4-106">.NET 核心 CLI 的基礎知識。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-106">The basics of the .NET Core CLI.</span></span>
* <span data-ttu-id="fb0f4-107">「C# 語言」功能的概觀。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-107">An overview of C# Language features.</span></span>
* <span data-ttu-id="fb0f4-108">使用 NuGet 來管理相依性</span><span class="sxs-lookup"><span data-stu-id="fb0f4-108">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="fb0f4-109">HTTP 通訊</span><span class="sxs-lookup"><span data-stu-id="fb0f4-109">HTTP Communications</span></span>
* <span data-ttu-id="fb0f4-110">處理 JSON 資訊</span><span class="sxs-lookup"><span data-stu-id="fb0f4-110">Processing JSON information</span></span>
* <span data-ttu-id="fb0f4-111">使用「屬性」來管理組態。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-111">Managing configuration with Attributes.</span></span>

<span data-ttu-id="fb0f4-112">您將建置一個對 GitHub 上的 REST 服務發出「HTTP 要求」的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-112">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="fb0f4-113">您將讀取 JSON 格式的資訊，並將該 JSON 封包轉換成 C# 物件。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-113">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="fb0f4-114">最後，您將了解如何使用 C# 物件。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-114">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="fb0f4-115">本教程中有許多功能。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-115">There are many features in this tutorial.</span></span> <span data-ttu-id="fb0f4-116">讓我們來逐一建置它們。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-116">Let’s build them one by one.</span></span>

<span data-ttu-id="fb0f4-117">如果您偏好追蹤本主題的[最終範例](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient)，則可以下載它。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-117">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="fb0f4-118">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-118">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fb0f4-119">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="fb0f4-119">Prerequisites</span></span>

<span data-ttu-id="fb0f4-120">您將必須設定電腦以執行 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-120">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="fb0f4-121">您可以在[.NET 核心下載](https://dotnet.microsoft.com/download)頁面上找到安裝說明。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-121">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="fb0f4-122">您可以在 Windows、Linux、macOS 或是 Docker 容器中執行此應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-122">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="fb0f4-123">您將必須安裝慣用的程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-123">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="fb0f4-124">下面的描述使用[Visual Studio代碼](https://code.visualstudio.com/)，這是一個開源的跨平臺編輯器。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-124">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="fb0f4-125">不過，您可以使用您熟悉的任何工具。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-125">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="fb0f4-126">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="fb0f4-126">Create the Application</span></span>

<span data-ttu-id="fb0f4-127">第一個步驟是建立新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-127">The first step is to create a new application.</span></span> <span data-ttu-id="fb0f4-128">請開啟命令提示字元，然後為您的應用程式建立新目錄。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-128">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="fb0f4-129">使該目錄成為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-129">Make that the current directory.</span></span> <span data-ttu-id="fb0f4-130">在主控台視窗中輸入以下命令：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-130">Enter the following command in a console window:</span></span>

```dotnetcli
dotnet new console --name WebApiClient
```

<span data-ttu-id="fb0f4-131">這會建立基本 "Hello World" 應用程式的起始檔案。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-131">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="fb0f4-132">專案名稱為"WebApiClient"。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-132">The project name is "WebApiClient".</span></span> <span data-ttu-id="fb0f4-133">由於這是一個新專案，因此沒有任何依賴項都到位。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-133">As this is a new project, none of the dependencies are in place.</span></span> <span data-ttu-id="fb0f4-134">第一次運行將下載 .NET Core 框架、安裝開發證書以及運行 NuGet 包管理器以還原缺少的依賴項。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-134">The first run will download the .NET Core framework, install a development certificate, and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="fb0f4-135">在您開始建立修改前，請先在命令提示字元中鍵入 `dotnet run` ([請參閱附註](#dotnet-restore-note))，執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-135">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="fb0f4-136">如果您的環境缺少相依性，`dotnet run` 會自動執行 `dotnet restore`。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-136">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="fb0f4-137">如果您的應用程式需要重建，它也會執行 `dotnet build`。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-137">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="fb0f4-138">在初始安裝之後，當它對您的專案有意義時，您只需要執行 `dotnet restore` 或 `dotnet build`。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-138">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="fb0f4-139">新增新的相依性</span><span class="sxs-lookup"><span data-stu-id="fb0f4-139">Adding New Dependencies</span></span>

<span data-ttu-id="fb0f4-140">.NET Core 的其中一個主要設計目標就是將 .NET 安裝大小縮減到最小。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-140">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="fb0f4-141">如果應用程式的某些功能需要額外的程式庫，您可以將這些相依性新增到 C# 專案檔 (\*.csproj) 中。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-141">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="fb0f4-142">對於我們的示例，您需要添加`System.Runtime.Serialization.Json`包，以便您的應用程式可以處理 JSON 回應。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-142">For our example, you'll need to add the `System.Runtime.Serialization.Json` package, so your application can process JSON responses.</span></span>

<span data-ttu-id="fb0f4-143">您將需要此應用程式的`System.Runtime.Serialization.Json`包。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-143">You'll need the `System.Runtime.Serialization.Json` package for this application.</span></span> <span data-ttu-id="fb0f4-144">通過運行以下[.NET CLI](../../core/tools/dotnet-add-package.md)命令將其添加到專案中：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-144">Add it to your project by running the following [.NET CLI](../../core/tools/dotnet-add-package.md) command:</span></span>

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a><span data-ttu-id="fb0f4-145">提出 Web 要求</span><span class="sxs-lookup"><span data-stu-id="fb0f4-145">Making Web Requests</span></span>

<span data-ttu-id="fb0f4-146">現在您已經準備好開始從 Web 接收資料。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-146">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="fb0f4-147">在此應用程式中，您將從 [GitHub API](https://developer.github.com/v3/) 讀取資訊。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-147">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="fb0f4-148">讓我們在 [.NET Foundation](https://www.dotnetfoundation.org/) 的庇護下讀取專案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-148">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="fb0f4-149">您將從對 GitHub API 提出要求以擷取專案相關資訊著手。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-149">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="fb0f4-150">您將使用的端點是：<https://api.github.com/orgs/dotnet/repos>。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-150">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="fb0f4-151">您想要擷取這些專案的所有相關資訊，因此您將使用 HTTP GET 要求。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-151">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="fb0f4-152">您的瀏覽器也會使用 HTTP GET 要求，因此您可以將該 URL 貼到瀏覽器中，以查看您將接收和處理的資訊。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-152">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="fb0f4-153">您需使用 <xref:System.Net.Http.HttpClient> 類別來提出 Web 要求。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-153">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="fb0f4-154">與所有新式 .NET API 相同，<xref:System.Net.Http.HttpClient> 針對它的長時間執行 API 只支援非同步方法。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-154">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="fb0f4-155">請從建立非同步方法著手。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-155">Start by making an async method.</span></span> <span data-ttu-id="fb0f4-156">您將在建置應用程式的功能時填入實作。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-156">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="fb0f4-157">請從開啟您專案目錄中的 `program.cs` 檔案並將下列方法新增到 `Program` 類別著手：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-157">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="fb0f4-158">您需要在`using``Main`方法頂部添加一個指令，以便 C# 編譯器識別類型<xref:System.Threading.Tasks.Task>：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-158">You'll need to add a `using` directive at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="fb0f4-159">如果您在此時建置專案，您將會收到針對此方法產生的警告，因為它不包含任何 `await` 運算子，所以將會以同步方式執行。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-159">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="fb0f4-160">目前請先忽略該警告；您將在填入方法時新增 `await` 運算子。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-160">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="fb0f4-161">接著，請將 `namespace` 陳述式中定義的命名空間從其預設值 `ConsoleApp` 重新命名為 `WebAPIClient`。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-161">Next, rename the namespace defined in the `namespace` statement from its default of `ConsoleApp` to `WebAPIClient`.</span></span> <span data-ttu-id="fb0f4-162">我們稍後將會在此命名空間中定義 `repo` 類別。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-162">We'll later define a `repo` class in this namespace.</span></span>

<span data-ttu-id="fb0f4-163">接著，請將 `Main` 方法更新成呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-163">Next, update the `Main` method to call this method.</span></span> <span data-ttu-id="fb0f4-164">該方法`ProcessRepositories`返回任務，並且不應在任務完成之前退出該程式。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-164">The `ProcessRepositories` method returns a task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="fb0f4-165">因此，必須更改 的簽名`Main`。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-165">Therefore, you must change the signature of `Main`.</span></span> <span data-ttu-id="fb0f4-166">添加`async`修改器，並將返回類型更改為`Task`。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-166">Add the `async` modifier, and change the return type to `Task`.</span></span> <span data-ttu-id="fb0f4-167">然後，在 方法的正文中，向`ProcessRepositories`添加調用。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-167">Then, in the body of the method, add a call to `ProcessRepositories`.</span></span> <span data-ttu-id="fb0f4-168">將`await`關鍵字添加到該方法調用：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-168">Add the `await` keyword to that method call:</span></span>

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

<span data-ttu-id="fb0f4-169">現在，您擁有一個不會執行任何動作但會以非同步方式執行的程式。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-169">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="fb0f4-170">來加以改善吧。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-170">Let's improve it.</span></span>

<span data-ttu-id="fb0f4-171">首先，您需要一個能夠從網路擷取資料的物件；使用 <xref:System.Net.Http.HttpClient> 即可達成。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-171">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="fb0f4-172">此物件會處理要求和回應。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-172">This object handles the request and the responses.</span></span> <span data-ttu-id="fb0f4-173">在`Program`*Program.cs*檔中的類中具現化該類型的單個實例。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-173">Instantiate a single instance of that type in the `Program` class inside the *Program.cs* file.</span></span>

```csharp
namespace WebAPIClient
{
    class Program
    {
        private static readonly HttpClient client = new HttpClient();

        static async Task Main(string[] args)
        {
            //...
        }
    }
}
```

<span data-ttu-id="fb0f4-174">讓我們回到 `ProcessRepositories` 方法並填入其第一個版本：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-174">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="fb0f4-175">您還需要在檔頂部添加兩個新`using`指令才能編譯：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-175">You'll need to also add two new `using` directives at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="fb0f4-176">第一個版本會提出 Web 要求來讀取 dotnet foundation 組織底下的所有儲存機制清單。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-176">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="fb0f4-177">(.NET Foundation 的 gitHub 識別碼是 'dotnet')。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-177">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="fb0f4-178">前幾行會為這個要求設定 <xref:System.Net.Http.HttpClient>。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-178">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="fb0f4-179">首先，會將它設定為接受 GitHub JSON 回應。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-179">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="fb0f4-180">此格式就是 JSON。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-180">This format is simply JSON.</span></span> <span data-ttu-id="fb0f4-181">下一行會將「使用者代理程式」標頭新增到來自此物件的所有要求。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-181">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="fb0f4-182">這兩個標頭會受到 GitHub 伺服器程式碼檢查，並且是從 GitHub 擷取資訊的必要標頭。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-182">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="fb0f4-183">設定 <xref:System.Net.Http.HttpClient> 之後，您需提出 Web 要求並擷取回應。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-183">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="fb0f4-184">在這個第一版中，您會使用 <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> 便利方法。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-184">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="fb0f4-185">這個便利方法會啟動一個提出 Web 要求的工作，然後當要求返回時，它會讀取回應資料流並從該資料流擷取內容。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-185">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="fb0f4-186">回應本文會以 <xref:System.String> 的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-186">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="fb0f4-187">當工作完成時，就會提供該字串。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-187">The string is available when the task completes.</span></span>

<span data-ttu-id="fb0f4-188">此方法的最後兩行會等候該工作，然後將回應顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-188">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="fb0f4-189">請建置應用程式並執行它。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-189">Build the app, and run it.</span></span> <span data-ttu-id="fb0f4-190">建置警告現在已消失，因為 `ProcessRepositories` 現在確實包含 `await` 運算子。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-190">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="fb0f4-191">您將會看到一長串顯示的 JSON 格式文字。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-191">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="fb0f4-192">處理 JSON 結果</span><span class="sxs-lookup"><span data-stu-id="fb0f4-192">Processing the JSON Result</span></span>

<span data-ttu-id="fb0f4-193">此時，您已撰寫程式碼來從 Web 伺服器擷取回應，並顯示包含在該回應中的文字。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-193">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="fb0f4-194">接著，讓我們將該 JSON 回應轉換成 C# 物件。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-194">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="fb0f4-195">類<xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType>將物件序列化到 JSON 並將 JSON 反序列化到物件中。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-195">The <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> class serializes objects to JSON and deserializes JSON into objects.</span></span> <span data-ttu-id="fb0f4-196">首先定義一個類來表示從`repo`GitHub API 返回的 JSON 物件：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-196">Start by defining a class to represent the `repo` JSON object returned from the GitHub API:</span></span>

```csharp
using System;

namespace WebAPIClient
{
    public class Repository
    {
        public string name { get; set; }
    }
}
```

<span data-ttu-id="fb0f4-197">請將上述程式碼放在名為 'repo.cs' 的新檔案中。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-197">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="fb0f4-198">這個類別版本代表處理 JSON 資料的最簡單路徑。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-198">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="fb0f4-199">類別名稱和成員名稱會符合 JSON 封包中使用的名稱，而不是符合下列 C# 慣例。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-199">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="fb0f4-200">您將在稍後藉由提供一些其他組態屬性來修正此問題。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-200">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="fb0f4-201">此類別示範了 JSON 序列化和還原序列化的另一個重要功能：並非 JSON 封包中的所有欄位都屬於此類別。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-201">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="fb0f4-202">JSON 序列化程式將會忽略未包含在所要使用之類別型別中的資訊。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-202">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="fb0f4-203">這個功能可讓您更容易建立只對 JSON 封包中的欄位子集有作用的型別。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-203">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="fb0f4-204">現在您已經建立型別，讓我們來將它還原序列化。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-204">Now that you've created the type, let's deserialize it.</span></span>

<span data-ttu-id="fb0f4-205">接著，您將使用序列化程式將 JSON 轉換成 C# 物件。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-205">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="fb0f4-206">將方法<xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>`ProcessRepositories`中的調用替換為以下行：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-206">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

<span data-ttu-id="fb0f4-207">您使用的是新的命名空間，因此還需要將其添加到檔頂部：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-207">You're using a new namespace, so you'll need to add it at the top of the file as well:</span></span>

```csharp
using System.Text.Json;
```

<span data-ttu-id="fb0f4-208">請注意，您現在使用的是 <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> 而不是 <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-208">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="fb0f4-209">序列化程式會使用資料流 (而不是字串) 作為其來源。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-209">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="fb0f4-210">讓我們解釋在前面程式碼片段的第二行中使用的 C# 語言的幾個功能。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-210">Let's explain a couple features of the C# language that are being used in the second line of the preceding code snippet.</span></span> <span data-ttu-id="fb0f4-211">的第一個`await`參數<xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType>是運算式。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-211">The first argument to <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> is an `await` expression.</span></span> <span data-ttu-id="fb0f4-212">（其他兩個參數是可選的，在程式碼片段中省略。Await 運算式幾乎可以出現在代碼中的任意位置，即使到目前為止，您只將它們視為設定陳述式的一部分。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-212">(The other two parameters are optional and are omitted in the code snippet.) Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span> <span data-ttu-id="fb0f4-213">該方法`Deserialize`是*泛型*的，這意味著您必須提供類型參數，用於應從 JSON 文本創建的物件類型。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-213">The `Deserialize` method is *generic*, which means you must supply type arguments for what kind of objects should be created from the JSON text.</span></span> <span data-ttu-id="fb0f4-214">在此示例中，您將反序列化為`List<Repository>`， 這是另一個泛型物件 。 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="fb0f4-214">In this example, you're deserializing to a `List<Repository>`, which is another generic object, the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="fb0f4-215">類`List<>`存儲物件的集合。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-215">The `List<>` class stores a collection of objects.</span></span> <span data-ttu-id="fb0f4-216">類型參數聲明存儲在 中`List<>`的物件的類型。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-216">The type argument declares the type of objects stored in the `List<>`.</span></span> <span data-ttu-id="fb0f4-217">JSON 文本表示回購物件的集合，因此類型參數為`Repository`。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-217">The JSON text represents a collection of repo objects, so the type argument is `Repository`.</span></span>

<span data-ttu-id="fb0f4-218">您差不多已經完成這個部分。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-218">You're almost done with this section.</span></span> <span data-ttu-id="fb0f4-219">現在您已將 JSON 轉換成 C# 物件，讓我們來顯示每個儲存機制的名稱。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-219">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="fb0f4-220">將下列幾行：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-220">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="fb0f4-221">取代為：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-221">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="fb0f4-222">編譯並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-222">Compile and run the application.</span></span> <span data-ttu-id="fb0f4-223">它將會列印出隸屬於 .NET Foundation 的儲存機制名稱。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-223">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="fb0f4-224">控制序列化</span><span class="sxs-lookup"><span data-stu-id="fb0f4-224">Controlling Serialization</span></span>

<span data-ttu-id="fb0f4-225">在添加更多要素之前，讓我們使用 屬性`name``[JsonPropertyName]`解決該屬性。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-225">Before you add more features, let's address the `name` property by using the `[JsonPropertyName]` attribute.</span></span> <span data-ttu-id="fb0f4-226">請對 repo.cs 中 `name` 欄位的宣告進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-226">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

<span data-ttu-id="fb0f4-227">要使用`[JsonPropertyName]`屬性，您需要將<xref:System.Text.Json.Serialization>命名空間添加到指令： `using`</span><span class="sxs-lookup"><span data-stu-id="fb0f4-227">To use `[JsonPropertyName]` attribute, you will need to add the <xref:System.Text.Json.Serialization> namespace to the `using` directives:</span></span>

```csharp
using System.Text.Json.Serialization;
```

<span data-ttu-id="fb0f4-228">這項變更意謂著您必須變更 program.cs 中寫入每個儲存機制名稱的程式碼：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-228">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="fb0f4-229">執行`dotnet run`以確保映射正確。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-229">Execute `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="fb0f4-230">您應該會看到與之前相同的輸出。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-230">You should see the same output as before.</span></span>

<span data-ttu-id="fb0f4-231">讓我們在新增新功能之前，再多進行一項變更。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-231">Let's make one more change before adding new features.</span></span> <span data-ttu-id="fb0f4-232">`ProcessRepositories` 方法可以執行非同步工作，然後傳回儲存機制的集合。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-232">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="fb0f4-233">讓我們從該方法傳回 `List<Repository>`，並將寫入資訊的程式碼移到 `Main` 方法中。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-233">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="fb0f4-234">請變更 `ProcessRepositories` 的簽章以傳回其結果為 `Repository` 物件清單的工作：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-234">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="fb0f4-235">接著，在處理 JSON 回應後，直接傳回儲存機制：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-235">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

<span data-ttu-id="fb0f4-236">編譯器會產生用於傳回的 `Task<T>` 物件，因為您已將此方法標示為 `async`。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-236">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="fb0f4-237">接著，讓我們來修改 `Main` 方法，使它擷取那些結果並將每個儲存機制名稱寫入到主控台。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-237">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="fb0f4-238">您的 `Main` 方法現在看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-238">Your `Main` method now looks like this:</span></span>

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a><span data-ttu-id="fb0f4-239">讀取更多資訊</span><span class="sxs-lookup"><span data-stu-id="fb0f4-239">Reading More Information</span></span>

<span data-ttu-id="fb0f4-240">讓我們再多處理 GitHub API 所傳送之 JSON 封包中的幾個屬性，來結束這個部分。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-240">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="fb0f4-241">您不會想要全盤了解，但新增幾個屬性將可示範更多一些的 C# 語言功能。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-241">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="fb0f4-242">讓我們從再多將幾個簡單型別新增到 `Repository` 類別定義著手。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-242">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="fb0f4-243">請將下列屬性新增到該類別：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-243">Add these properties to that class:</span></span>

```csharp
[JsonPropertyName("description")]
public string Description { get; set; }

[JsonPropertyName("html_url")]
public Uri GitHubHomeUrl { get; set; }

[JsonPropertyName("homepage")]
public Uri Homepage { get; set; }

[JsonPropertyName("watchers")]
public int Watchers { get; set; }
```

<span data-ttu-id="fb0f4-244">這些屬性具有從字串型別 (JSON 封包所包含的型別) 轉換成目標型別的內建轉換。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-244">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="fb0f4-245">您可能不熟悉 <xref:System.Uri> 型別。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-245">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="fb0f4-246">它代表 URI，或在此案例中是代表 URL。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-246">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="fb0f4-247">在 `Uri` 和 `int` 型別的案例中，如果 JSON 封包包含不會轉換成目標型別的資料，序列化動作將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-247">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="fb0f4-248">在您新增這些屬性之後，請更新 `Main` 方法以顯示下列元素：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-248">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="fb0f4-249">在最後一個步驟中，讓我們新增最後一個推送作業的資訊。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-249">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="fb0f4-250">此資訊會在 JSON 回應中採用下列形式的格式：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-250">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="fb0f4-251">該格式在協調通用時間 （UTC） 中，因此您將獲得其<xref:System.DateTime><xref:System.DateTime.Kind%2A>屬性為<xref:System.DateTimeKind.Utc>的值。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-251">That format is in Coordinated Universal Time (UTC) so you'll get a <xref:System.DateTime> value whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Utc>.</span></span> <span data-ttu-id="fb0f4-252">如果您更喜歡在時區中表示的日期，則需要編寫自訂轉換方法。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-252">If you prefer a date represented in your time zone, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="fb0f4-253">首先，定義一`public`個屬性，該屬性將保存`Repository`類中的日期和時間的 UTC 表示形式，`LastPush``readonly`以及返回轉換為本地時間的日期的屬性：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-253">First, define a `public` property that will hold the UTC representation of the date and time in your `Repository` class and a `LastPush` `readonly` property that returns the date converted to local time:</span></span>

```csharp
[JsonPropertyName("pushed_at")]
public DateTime LastPushUtc { get; set; }

public DateTime LastPush => LastPushUtc.ToLocalTime();
```

<span data-ttu-id="fb0f4-254">讓我們來討論一下我們剛剛定義的新構造。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-254">Let's go over the new constructs we just defined.</span></span> <span data-ttu-id="fb0f4-255">屬性`LastPush`使用`get`訪問器的*運算式體成員*定義。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-255">The `LastPush` property is defined using an *expression-bodied member* for the `get` accessor.</span></span> <span data-ttu-id="fb0f4-256">沒有 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-256">There is no `set` accessor.</span></span> <span data-ttu-id="fb0f4-257">省略`set`訪問器是在 C# 中定義*唯讀*屬性的方式。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-257">Omitting the `set` accessor is how you define a *read-only* property in C#.</span></span> <span data-ttu-id="fb0f4-258">(是的，您可以用 C# 來建立「唯寫」\*\* 屬性，但其值會受到限制)。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-258">(Yes, you can create *write-only* properties in C#, but their value is limited.)</span></span>

<span data-ttu-id="fb0f4-259">最後，請在主控台中再多新增一個輸出陳述式，這樣您便已準備好來重新建置及執行此應用程式：</span><span class="sxs-lookup"><span data-stu-id="fb0f4-259">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="fb0f4-260">您的版本現在應該與[完成範例](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient)相符。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-260">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="fb0f4-261">結論</span><span class="sxs-lookup"><span data-stu-id="fb0f4-261">Conclusion</span></span>

<span data-ttu-id="fb0f4-262">本教學課程示範了如何提出 Web 要求、剖析結果，以及顯示這些結果的屬性。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-262">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="fb0f4-263">您也在專案中新增了新的套件作為相依性。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-263">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="fb0f4-264">您已了解一些支援物件導向技術的 C# 語言功能。</span><span class="sxs-lookup"><span data-stu-id="fb0f4-264">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
