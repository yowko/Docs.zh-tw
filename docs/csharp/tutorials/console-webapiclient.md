---
title: 使用 .NET Core 來建立 REST 用戶端
description: 本教學課程會教導您一些 .NET Core 和 C# 語言中的功能。
ms.date: 01/09/2020
ms.assetid: 51033ce2-7a53-4cdd-966d-9da15c8204d2
ms.openlocfilehash: c7b7e9803b0c05f4956f5c007bca8aa4b200cfca
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83208016"
---
# <a name="rest-client"></a><span data-ttu-id="5c8e1-103">REST 用戶端</span><span class="sxs-lookup"><span data-stu-id="5c8e1-103">REST client</span></span>

<span data-ttu-id="5c8e1-104">本教學課程會教導您一些 .NET Core 和 C# 語言中的功能。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="5c8e1-105">您將了解：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-105">You’ll learn:</span></span>

* <span data-ttu-id="5c8e1-106">.NET Core CLI 的基本概念。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-106">The basics of the .NET Core CLI.</span></span>
* <span data-ttu-id="5c8e1-107">「C# 語言」功能的概觀。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-107">An overview of C# Language features.</span></span>
* <span data-ttu-id="5c8e1-108">使用 NuGet 來管理相依性</span><span class="sxs-lookup"><span data-stu-id="5c8e1-108">Managing dependencies with NuGet</span></span>
* <span data-ttu-id="5c8e1-109">HTTP 通訊</span><span class="sxs-lookup"><span data-stu-id="5c8e1-109">HTTP Communications</span></span>
* <span data-ttu-id="5c8e1-110">處理 JSON 資訊</span><span class="sxs-lookup"><span data-stu-id="5c8e1-110">Processing JSON information</span></span>
* <span data-ttu-id="5c8e1-111">使用「屬性」來管理組態。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-111">Managing configuration with Attributes.</span></span>

<span data-ttu-id="5c8e1-112">您將建置一個對 GitHub 上的 REST 服務發出「HTTP 要求」的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-112">You’ll build an application that issues HTTP Requests to a REST service on GitHub.</span></span> <span data-ttu-id="5c8e1-113">您將讀取 JSON 格式的資訊，並將該 JSON 封包轉換成 C# 物件。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-113">You'll read information in JSON format, and convert that JSON packet into C# objects.</span></span> <span data-ttu-id="5c8e1-114">最後，您將了解如何使用 C# 物件。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-114">Finally, you'll see how to work with C# objects.</span></span>

<span data-ttu-id="5c8e1-115">本教學課程中有許多功能。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-115">There are many features in this tutorial.</span></span> <span data-ttu-id="5c8e1-116">讓我們來逐一建置它們。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-116">Let’s build them one by one.</span></span>

<span data-ttu-id="5c8e1-117">如果您偏好追蹤本主題的[最終範例](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient)，則可以下載它。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-117">If you prefer to follow along with the [final sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient) for this topic, you can download it.</span></span> <span data-ttu-id="5c8e1-118">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-118">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5c8e1-119">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="5c8e1-119">Prerequisites</span></span>

<span data-ttu-id="5c8e1-120">您將必須設定電腦以執行 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-120">You’ll need to set up your machine to run .NET core.</span></span> <span data-ttu-id="5c8e1-121">您可以在[.Net Core 下載](https://dotnet.microsoft.com/download)頁面上找到安裝指示。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-121">You can find the installation instructions on the [.NET Core Downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="5c8e1-122">您可以在 Windows、Linux、macOS 或是 Docker 容器中執行此應用程式。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-122">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="5c8e1-123">您將必須安裝慣用的程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-123">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="5c8e1-124">下列說明使用[Visual Studio Code](https://code.visualstudio.com/)，這是一個開放原始碼的跨平臺編輯器。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-124">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/), which is an open source, cross platform editor.</span></span> <span data-ttu-id="5c8e1-125">不過，您可以使用您熟悉的任何工具。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-125">However, you can use whatever tools you are comfortable with.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="5c8e1-126">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="5c8e1-126">Create the Application</span></span>

<span data-ttu-id="5c8e1-127">第一個步驟是建立新的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-127">The first step is to create a new application.</span></span> <span data-ttu-id="5c8e1-128">請開啟命令提示字元，然後為您的應用程式建立新目錄。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-128">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="5c8e1-129">使該目錄成為目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-129">Make that the current directory.</span></span> <span data-ttu-id="5c8e1-130">在主控台視窗中輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-130">Enter the following command in a console window:</span></span>

```dotnetcli
dotnet new console --name WebApiClient
```

<span data-ttu-id="5c8e1-131">這會建立基本 "Hello World" 應用程式的起始檔案。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-131">This creates the starter files for a basic "Hello World" application.</span></span> <span data-ttu-id="5c8e1-132">專案名稱為 "WebApiClient"。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-132">The project name is "WebApiClient".</span></span> <span data-ttu-id="5c8e1-133">因為這是新的專案，所以沒有任何相依性。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-133">As this is a new project, none of the dependencies are in place.</span></span> <span data-ttu-id="5c8e1-134">第一次執行時，會下載 .NET Core framework、安裝開發憑證，以及執行 NuGet 套件管理員，以還原遺失的相依性。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-134">The first run will download the .NET Core framework, install a development certificate, and run the NuGet package manager to restore missing dependencies.</span></span>

<span data-ttu-id="5c8e1-135">在您開始建立修改前，請先在命令提示字元中鍵入 `dotnet run` ([請參閱附註](#dotnet-restore-note))，執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-135">Before you start making modifications, type `dotnet run` ([see note](#dotnet-restore-note)) at the command prompt to run your application.</span></span> <span data-ttu-id="5c8e1-136">如果您的環境缺少相依性，`dotnet run` 會自動執行 `dotnet restore`。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-136">`dotnet run` automatically performs `dotnet restore` if your environment is missing dependencies.</span></span> <span data-ttu-id="5c8e1-137">如果您的應用程式需要重建，它也會執行 `dotnet build`。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-137">It also performs `dotnet build` if your application needs to be rebuilt.</span></span>
<span data-ttu-id="5c8e1-138">在初始安裝之後，當它對您的專案有意義時，您只需要執行 `dotnet restore` 或 `dotnet build`。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-138">After your initial setup, you will only need to run `dotnet restore` or `dotnet build` when it makes sense for your project.</span></span>

## <a name="adding-new-dependencies"></a><span data-ttu-id="5c8e1-139">新增新的相依性</span><span class="sxs-lookup"><span data-stu-id="5c8e1-139">Adding New Dependencies</span></span>

<span data-ttu-id="5c8e1-140">.NET Core 的其中一個主要設計目標就是將 .NET 安裝大小縮減到最小。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-140">One of the key design goals for .NET Core is to minimize the size of the .NET installation.</span></span> <span data-ttu-id="5c8e1-141">如果應用程式的某些功能需要額外的程式庫，您可以將這些相依性新增到 C# 專案檔 (\*.csproj) 中。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-141">If an application needs additional libraries for some of its features, you add those dependencies into your C# project (\*.csproj) file.</span></span> <span data-ttu-id="5c8e1-142">在我們的範例中，您必須新增 `System.Runtime.Serialization.Json` 套件，讓您的應用程式可以處理 JSON 回應。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-142">For our example, you'll need to add the `System.Runtime.Serialization.Json` package, so your application can process JSON responses.</span></span>

<span data-ttu-id="5c8e1-143">您將需要 `System.Runtime.Serialization.Json` 此應用程式的套件。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-143">You'll need the `System.Runtime.Serialization.Json` package for this application.</span></span> <span data-ttu-id="5c8e1-144">執行下列[.NET CLI](../../core/tools/dotnet-add-package.md)命令，將它新增至您的專案：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-144">Add it to your project by running the following [.NET CLI](../../core/tools/dotnet-add-package.md) command:</span></span>

```dotnetcli
dotnet add package System.Text.Json
```

## <a name="making-web-requests"></a><span data-ttu-id="5c8e1-145">提出 Web 要求</span><span class="sxs-lookup"><span data-stu-id="5c8e1-145">Making Web Requests</span></span>

<span data-ttu-id="5c8e1-146">現在您已經準備好開始從 Web 接收資料。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-146">Now you're ready to start retrieving data from the web.</span></span> <span data-ttu-id="5c8e1-147">在此應用程式中，您將從 [GitHub API](https://developer.github.com/v3/) 讀取資訊。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-147">In this application, you'll read information from the [GitHub API](https://developer.github.com/v3/).</span></span> <span data-ttu-id="5c8e1-148">讓我們在 [.NET Foundation](https://www.dotnetfoundation.org/) 的庇護下讀取專案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-148">Let's read information about the projects under the [.NET Foundation](https://www.dotnetfoundation.org/) umbrella.</span></span> <span data-ttu-id="5c8e1-149">您將從對 GitHub API 提出要求以擷取專案相關資訊著手。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-149">You'll start by making the request to the GitHub API to retrieve information on the projects.</span></span> <span data-ttu-id="5c8e1-150">您將使用的端點是：<https://api.github.com/orgs/dotnet/repos>。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-150">The endpoint you'll use is: <https://api.github.com/orgs/dotnet/repos>.</span></span> <span data-ttu-id="5c8e1-151">您想要擷取這些專案的所有相關資訊，因此您將使用 HTTP GET 要求。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-151">You want to retrieve all the information about these projects, so you'll use an HTTP GET request.</span></span>
<span data-ttu-id="5c8e1-152">您的瀏覽器也會使用 HTTP GET 要求，因此您可以將該 URL 貼到瀏覽器中，以查看您將接收和處理的資訊。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-152">Your browser also uses HTTP GET requests, so you can paste that URL into your browser to see what information you'll be receiving and processing.</span></span>

<span data-ttu-id="5c8e1-153">您需使用 <xref:System.Net.Http.HttpClient> 類別來提出 Web 要求。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-153">You use the <xref:System.Net.Http.HttpClient> class to make web requests.</span></span> <span data-ttu-id="5c8e1-154">與所有新式 .NET API 相同，<xref:System.Net.Http.HttpClient> 針對它的長時間執行 API 只支援非同步方法。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-154">Like all modern .NET APIs, <xref:System.Net.Http.HttpClient> supports only async methods for its long-running APIs.</span></span>
<span data-ttu-id="5c8e1-155">請從建立非同步方法著手。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-155">Start by making an async method.</span></span> <span data-ttu-id="5c8e1-156">您將在建置應用程式的功能時填入實作。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-156">You'll fill in the implementation as you build the functionality of the application.</span></span> <span data-ttu-id="5c8e1-157">請從開啟您專案目錄中的 `program.cs` 檔案並將下列方法新增到 `Program` 類別著手：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-157">Start by opening the `program.cs` file in your project directory and adding the following method to the `Program` class:</span></span>

```csharp
private static async Task ProcessRepositories()
{
}
```

<span data-ttu-id="5c8e1-158">您必須 `using` 在方法的頂端加入指示詞， `Main` 讓 c # 編譯器能夠辨識 <xref:System.Threading.Tasks.Task> 類型：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-158">You'll need to add a `using` directive at the top of your `Main` method so that the C# compiler recognizes the <xref:System.Threading.Tasks.Task> type:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="5c8e1-159">如果您在此時建置專案，您將會收到針對此方法產生的警告，因為它不包含任何 `await` 運算子，所以將會以同步方式執行。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-159">If you build your project at this point, you'll get a warning generated for this method, because it does not contain any `await` operators and will run synchronously.</span></span> <span data-ttu-id="5c8e1-160">目前請先忽略該警告；您將在填入方法時新增 `await` 運算子。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-160">Ignore that for now; you'll add `await` operators as you fill in the method.</span></span>

<span data-ttu-id="5c8e1-161">接下來，更新 `Main` 方法以呼叫 `ProcessRepositories` 方法。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-161">Next, update the `Main` method to call the `ProcessRepositories` method.</span></span> <span data-ttu-id="5c8e1-162">`ProcessRepositories`方法會傳回工作，而且您不應該在該工作完成之前結束程式。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-162">The `ProcessRepositories` method returns a task, and you shouldn't exit the program before that task finishes.</span></span> <span data-ttu-id="5c8e1-163">因此，您必須變更的簽章 `Main` 。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-163">Therefore, you must change the signature of `Main`.</span></span> <span data-ttu-id="5c8e1-164">新增 `async` 修飾詞，並將傳回類型變更為 `Task` 。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-164">Add the `async` modifier, and change the return type to `Task`.</span></span> <span data-ttu-id="5c8e1-165">然後，在方法的主體中，新增對的呼叫 `ProcessRepositories` 。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-165">Then, in the body of the method, add a call to `ProcessRepositories`.</span></span> <span data-ttu-id="5c8e1-166">將 `await` 關鍵字新增至該方法呼叫：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-166">Add the `await` keyword to that method call:</span></span>

```csharp
static async Task Main(string[] args)
{
    await ProcessRepositories();
}
```

<span data-ttu-id="5c8e1-167">現在，您擁有一個不會執行任何動作但會以非同步方式執行的程式。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-167">Now, you have a program that does nothing, but does it asynchronously.</span></span> <span data-ttu-id="5c8e1-168">來加以改善吧。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-168">Let's improve it.</span></span>

<span data-ttu-id="5c8e1-169">首先，您需要一個能夠從網路擷取資料的物件；使用 <xref:System.Net.Http.HttpClient> 即可達成。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-169">First you need an object that is capable to retrieve data from the web; you can use a <xref:System.Net.Http.HttpClient> to do that.</span></span> <span data-ttu-id="5c8e1-170">此物件會處理要求和回應。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-170">This object handles the request and the responses.</span></span> <span data-ttu-id="5c8e1-171">在 Program.cs 檔案內，將類別中該類型的單一實例具現化 `Program` 。 *Program.cs*</span><span class="sxs-lookup"><span data-stu-id="5c8e1-171">Instantiate a single instance of that type in the `Program` class inside the *Program.cs* file.</span></span>

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

<span data-ttu-id="5c8e1-172">讓我們回到 `ProcessRepositories` 方法並填入其第一個版本：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-172">Let's go back to the `ProcessRepositories` method and fill in a first version of it:</span></span>

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

<span data-ttu-id="5c8e1-173">您也必須在檔案頂端加入兩個新的指示詞，以 `using` 進行編譯：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-173">You'll need to also add two new `using` directives at the top of the file for this to compile:</span></span>

```csharp
using System.Net.Http;
using System.Net.Http.Headers;
```

<span data-ttu-id="5c8e1-174">第一個版本會提出 Web 要求來讀取 dotnet foundation 組織底下的所有儲存機制清單。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-174">This first version makes a web request to read the list of all repositories under the dotnet foundation organization.</span></span> <span data-ttu-id="5c8e1-175">(.NET Foundation 的 gitHub 識別碼是 'dotnet')。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-175">(The gitHub ID for the .NET Foundation is 'dotnet').</span></span> <span data-ttu-id="5c8e1-176">前幾行會為這個要求設定 <xref:System.Net.Http.HttpClient>。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-176">The first few lines set up the <xref:System.Net.Http.HttpClient> for this request.</span></span> <span data-ttu-id="5c8e1-177">首先，會將它設定為接受 GitHub JSON 回應。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-177">First, it is configured to accept the GitHub JSON responses.</span></span>
<span data-ttu-id="5c8e1-178">此格式就是 JSON。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-178">This format is simply JSON.</span></span> <span data-ttu-id="5c8e1-179">下一行會將「使用者代理程式」標頭新增到來自此物件的所有要求。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-179">The next line adds a User Agent header to all requests from this object.</span></span> <span data-ttu-id="5c8e1-180">這兩個標頭會受到 GitHub 伺服器程式碼檢查，並且是從 GitHub 擷取資訊的必要標頭。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-180">These two headers are checked by the GitHub server code, and are necessary to retrieve information from GitHub.</span></span>

<span data-ttu-id="5c8e1-181">設定 <xref:System.Net.Http.HttpClient> 之後，您需提出 Web 要求並擷取回應。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-181">After you've configured the <xref:System.Net.Http.HttpClient>, you make a web request and retrieve the response.</span></span> <span data-ttu-id="5c8e1-182">在這個第一版中，您會使用 <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> 便利方法。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-182">In this first version, you use the <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)?displayProperty=nameWithType> convenience method.</span></span> <span data-ttu-id="5c8e1-183">這個便利方法會啟動一個提出 Web 要求的工作，然後當要求返回時，它會讀取回應資料流並從該資料流擷取內容。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-183">This convenience method starts a task that makes the web request, and then when the request returns, it reads the response stream and extracts the content from the stream.</span></span> <span data-ttu-id="5c8e1-184">回應本文會以 <xref:System.String> 的形式傳回。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-184">The body of the response is returned as a <xref:System.String>.</span></span> <span data-ttu-id="5c8e1-185">當工作完成時，就會提供該字串。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-185">The string is available when the task completes.</span></span>

<span data-ttu-id="5c8e1-186">此方法的最後兩行會等候該工作，然後將回應顯示在主控台中。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-186">The final two lines of this method await that task, and then print the response to the console.</span></span>
<span data-ttu-id="5c8e1-187">請建置應用程式並執行它。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-187">Build the app, and run it.</span></span> <span data-ttu-id="5c8e1-188">建置警告現在已消失，因為 `ProcessRepositories` 現在確實包含 `await` 運算子。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-188">The build warning is gone now, because the `ProcessRepositories` now does contain an `await` operator.</span></span> <span data-ttu-id="5c8e1-189">您將會看到一長串顯示的 JSON 格式文字。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-189">You'll see a long display of JSON formatted text.</span></span>

## <a name="processing-the-json-result"></a><span data-ttu-id="5c8e1-190">處理 JSON 結果</span><span class="sxs-lookup"><span data-stu-id="5c8e1-190">Processing the JSON Result</span></span>

<span data-ttu-id="5c8e1-191">此時，您已撰寫程式碼來從 Web 伺服器擷取回應，並顯示包含在該回應中的文字。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-191">At this point, you've written the code to retrieve a response from a web server, and display the text that is contained in that response.</span></span> <span data-ttu-id="5c8e1-192">接著，讓我們將該 JSON 回應轉換成 C# 物件。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-192">Next, let's convert that JSON response into C# objects.</span></span>

<span data-ttu-id="5c8e1-193">類別會將 <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> 物件序列化為 json，並將 json 還原序列化為物件。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-193">The <xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> class serializes objects to JSON and deserializes JSON into objects.</span></span> <span data-ttu-id="5c8e1-194">一開始請先定義類別，以代表 `repo` 從 GITHUB API 傳回的 JSON 物件：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-194">Start by defining a class to represent the `repo` JSON object returned from the GitHub API:</span></span>

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

<span data-ttu-id="5c8e1-195">請將上述程式碼放在名為 'repo.cs' 的新檔案中。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-195">Put the above code in a new file called 'repo.cs'.</span></span> <span data-ttu-id="5c8e1-196">這個類別版本代表處理 JSON 資料的最簡單路徑。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-196">This version of the class represents the simplest path to process JSON data.</span></span> <span data-ttu-id="5c8e1-197">類別名稱和成員名稱會符合 JSON 封包中使用的名稱，而不是符合下列 C# 慣例。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-197">The class name and the member name match the names used in the JSON packet, instead of following C# conventions.</span></span> <span data-ttu-id="5c8e1-198">您將在稍後藉由提供一些其他組態屬性來修正此問題。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-198">You'll fix that by providing some configuration attributes later.</span></span> <span data-ttu-id="5c8e1-199">此類別示範了 JSON 序列化和還原序列化的另一個重要功能：並非 JSON 封包中的所有欄位都屬於此類別。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-199">This class demonstrates another important feature of JSON serialization and deserialization: Not all the fields in the JSON packet are part of this class.</span></span>
<span data-ttu-id="5c8e1-200">JSON 序列化程式將會忽略未包含在所要使用之類別型別中的資訊。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-200">The JSON serializer will ignore information that is not included in the class type being used.</span></span>
<span data-ttu-id="5c8e1-201">這個功能可讓您更容易建立只對 JSON 封包中的欄位子集有作用的型別。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-201">This feature makes it easier to create types that work with only a subset of the fields in the JSON packet.</span></span>

<span data-ttu-id="5c8e1-202">現在您已經建立型別，讓我們來將它還原序列化。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-202">Now that you've created the type, let's deserialize it.</span></span>

<span data-ttu-id="5c8e1-203">接著，您將使用序列化程式將 JSON 轉換成 C# 物件。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-203">Next, you'll use the serializer to convert JSON into C# objects.</span></span> <span data-ttu-id="5c8e1-204">將您方法中的呼叫取代為 <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> `ProcessRepositories` 下列幾行：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-204">Replace the call to <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)> in your `ProcessRepositories` method with the following lines:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
```

<span data-ttu-id="5c8e1-205">您使用的是新的命名空間，因此您也必須將它新增至檔案頂端：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-205">You're using a new namespace, so you'll need to add it at the top of the file as well:</span></span>

```csharp
using System.Text.Json;
```

<span data-ttu-id="5c8e1-206">請注意，您現在使用的是 <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> 而不是 <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-206">Notice that you're now using <xref:System.Net.Http.HttpClient.GetStreamAsync(System.String)> instead of <xref:System.Net.Http.HttpClient.GetStringAsync(System.String)>.</span></span> <span data-ttu-id="5c8e1-207">序列化程式會使用資料流 (而不是字串) 作為其來源。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-207">The serializer uses a stream instead of a string as its source.</span></span> <span data-ttu-id="5c8e1-208">讓我們來說明上述程式碼片段第二行中所使用的一些 c # 語言功能。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-208">Let's explain a couple features of the C# language that are being used in the second line of the preceding code snippet.</span></span> <span data-ttu-id="5c8e1-209">的第一個引數 <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> 是 `await` 運算式。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-209">The first argument to <xref:System.Text.Json.JsonSerializer.DeserializeAsync%60%601(System.IO.Stream,System.Text.Json.JsonSerializerOptions,System.Threading.CancellationToken)?displayProperty=nameWithType> is an `await` expression.</span></span> <span data-ttu-id="5c8e1-210">（其他兩個參數是選擇性的，而且會在程式碼片段中省略）。Await 運算式可以出現在您程式碼中的任何位置，雖然目前為止，您只會看到它們是指派語句的一部分。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-210">(The other two parameters are optional and are omitted in the code snippet.) Await expressions can appear almost anywhere in your code, even though up to now, you've only seen them as part of an assignment statement.</span></span> <span data-ttu-id="5c8e1-211">`Deserialize`方法是*泛型*，這表示您必須提供類型引數，以供應從 JSON 文字建立的物件種類。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-211">The `Deserialize` method is *generic*, which means you must supply type arguments for what kind of objects should be created from the JSON text.</span></span> <span data-ttu-id="5c8e1-212">在此範例中，您要還原序列化至 `List<Repository>` ，也就是另一個泛型物件，也就是 <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-212">In this example, you're deserializing to a `List<Repository>`, which is another generic object, the <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5c8e1-213">`List<>`類別會儲存物件的集合。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-213">The `List<>` class stores a collection of objects.</span></span> <span data-ttu-id="5c8e1-214">型別引數會宣告儲存在中的物件類型 `List<>` 。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-214">The type argument declares the type of objects stored in the `List<>`.</span></span> <span data-ttu-id="5c8e1-215">JSON 文字代表存放庫物件的集合，因此類型引數為 `Repository` 。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-215">The JSON text represents a collection of repo objects, so the type argument is `Repository`.</span></span>

<span data-ttu-id="5c8e1-216">您差不多已經完成這個部分。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-216">You're almost done with this section.</span></span> <span data-ttu-id="5c8e1-217">現在您已將 JSON 轉換成 C# 物件，讓我們來顯示每個儲存機制的名稱。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-217">Now that you've converted the JSON to C# objects, let's display the name of each repository.</span></span> <span data-ttu-id="5c8e1-218">將下列幾行：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-218">Replace the lines that read:</span></span>

```csharp
var msg = await stringTask;   //**Deleted this
Console.Write(msg);
```

<span data-ttu-id="5c8e1-219">取代為：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-219">with the following:</span></span>

```csharp
foreach (var repo in repositories)
    Console.WriteLine(repo.name);
```

<span data-ttu-id="5c8e1-220">編譯並執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-220">Compile and run the application.</span></span> <span data-ttu-id="5c8e1-221">它將會列印出隸屬於 .NET Foundation 的儲存機制名稱。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-221">It will print out the names of the repositories that are part of the .NET Foundation.</span></span>

## <a name="controlling-serialization"></a><span data-ttu-id="5c8e1-222">控制序列化</span><span class="sxs-lookup"><span data-stu-id="5c8e1-222">Controlling Serialization</span></span>

<span data-ttu-id="5c8e1-223">在您新增更多功能之前，讓我們 `name` 使用屬性來定址屬性 `[JsonPropertyName]` 。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-223">Before you add more features, let's address the `name` property by using the `[JsonPropertyName]` attribute.</span></span> <span data-ttu-id="5c8e1-224">請對 repo.cs 中 `name` 欄位的宣告進行下列變更：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-224">Make the following changes to the declaration of the `name` field in repo.cs:</span></span>

```csharp
[JsonPropertyName("name")]
public string Name { get; set; }
```

<span data-ttu-id="5c8e1-225">若要使用 `[JsonPropertyName]` 屬性，您必須將 <xref:System.Text.Json.Serialization> 命名空間新增至指示詞 `using` ：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-225">To use `[JsonPropertyName]` attribute, you will need to add the <xref:System.Text.Json.Serialization> namespace to the `using` directives:</span></span>

```csharp
using System.Text.Json.Serialization;
```

<span data-ttu-id="5c8e1-226">這項變更意謂著您必須變更 program.cs 中寫入每個儲存機制名稱的程式碼：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-226">This change means you need to change the code that writes the name of each repository in program.cs:</span></span>

```csharp
Console.WriteLine(repo.Name);
```

<span data-ttu-id="5c8e1-227">執行 `dotnet run` 以確定您的對應正確。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-227">Execute `dotnet run` to make sure you've got the mappings correct.</span></span> <span data-ttu-id="5c8e1-228">您應該會看到與之前相同的輸出。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-228">You should see the same output as before.</span></span>

<span data-ttu-id="5c8e1-229">讓我們在新增新功能之前，再多進行一項變更。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-229">Let's make one more change before adding new features.</span></span> <span data-ttu-id="5c8e1-230">`ProcessRepositories` 方法可以執行非同步工作，然後傳回儲存機制的集合。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-230">The `ProcessRepositories` method can do the async work and return a collection of the repositories.</span></span> <span data-ttu-id="5c8e1-231">讓我們從該方法傳回 `List<Repository>`，並將寫入資訊的程式碼移到 `Main` 方法中。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-231">Let's return the `List<Repository>` from that method, and move the code that writes the information into the `Main` method.</span></span>

<span data-ttu-id="5c8e1-232">請變更 `ProcessRepositories` 的簽章以傳回其結果為 `Repository` 物件清單的工作：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-232">Change the signature of `ProcessRepositories` to return a task whose result is a list of `Repository` objects:</span></span>

```csharp
private static async Task<List<Repository>> ProcessRepositories()
```

<span data-ttu-id="5c8e1-233">接著，在處理 JSON 回應後，直接傳回儲存機制：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-233">Then, just return the repositories after processing the JSON response:</span></span>

```csharp
var streamTask = client.GetStreamAsync("https://api.github.com/orgs/dotnet/repos");
var repositories = await JsonSerializer.DeserializeAsync<List<Repository>>(await streamTask);
return repositories;
```

<span data-ttu-id="5c8e1-234">編譯器會產生用於傳回的 `Task<T>` 物件，因為您已將此方法標示為 `async`。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-234">The compiler generates the `Task<T>` object for the return because you've marked this method as `async`.</span></span>
<span data-ttu-id="5c8e1-235">接著，讓我們來修改 `Main` 方法，使它擷取那些結果並將每個儲存機制名稱寫入到主控台。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-235">Then, let's modify the `Main` method so that it captures those results and writes each repository name to the console.</span></span> <span data-ttu-id="5c8e1-236">您的 `Main` 方法現在看起來會像這樣：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-236">Your `Main` method now looks like this:</span></span>

```csharp
public static async Task Main(string[] args)
{
    var repositories = await ProcessRepositories();

    foreach (var repo in repositories)
        Console.WriteLine(repo.Name);
}
```

## <a name="reading-more-information"></a><span data-ttu-id="5c8e1-237">讀取更多資訊</span><span class="sxs-lookup"><span data-stu-id="5c8e1-237">Reading More Information</span></span>

<span data-ttu-id="5c8e1-238">讓我們再多處理 GitHub API 所傳送之 JSON 封包中的幾個屬性，來結束這個部分。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-238">Let's finish this by processing a few more of the properties in the JSON packet that gets sent from the GitHub API.</span></span> <span data-ttu-id="5c8e1-239">您不會想要全盤了解，但新增幾個屬性將可示範更多一些的 C# 語言功能。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-239">You won't want to grab everything, but adding a few properties will demonstrate a few more features of the C# language.</span></span>

<span data-ttu-id="5c8e1-240">讓我們從再多將幾個簡單型別新增到 `Repository` 類別定義著手。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-240">Let's start by adding a few more simple types to the `Repository` class definition.</span></span> <span data-ttu-id="5c8e1-241">請將下列屬性新增到該類別：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-241">Add these properties to that class:</span></span>

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

<span data-ttu-id="5c8e1-242">這些屬性具有從字串型別 (JSON 封包所包含的型別) 轉換成目標型別的內建轉換。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-242">These properties have built-in conversions from the string type (which is what the JSON packets contain) to the target type.</span></span> <span data-ttu-id="5c8e1-243">您可能不熟悉 <xref:System.Uri> 型別。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-243">The <xref:System.Uri> type may be new to you.</span></span> <span data-ttu-id="5c8e1-244">它代表 URI，或在此案例中是代表 URL。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-244">It represents a URI, or in this case, a URL.</span></span> <span data-ttu-id="5c8e1-245">在 `Uri` 和 `int` 型別的案例中，如果 JSON 封包包含不會轉換成目標型別的資料，序列化動作將會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-245">In the case of the `Uri` and `int` types, if the JSON packet contains data that does not convert to the target type, the serialization action will throw an exception.</span></span>

<span data-ttu-id="5c8e1-246">在您新增這些屬性之後，請更新 `Main` 方法以顯示下列元素：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-246">Once you've added these, update the `Main` method to display those elements:</span></span>

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

<span data-ttu-id="5c8e1-247">在最後一個步驟中，讓我們新增最後一個推送作業的資訊。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-247">As a final step, let's add the information for the last push operation.</span></span> <span data-ttu-id="5c8e1-248">此資訊會在 JSON 回應中採用下列形式的格式：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-248">This information is formatted in this fashion in the JSON response:</span></span>

```json
2016-02-08T21:27:00Z
```

<span data-ttu-id="5c8e1-249">該格式為國際標準時間（UTC），因此您將取得 <xref:System.DateTime> 其 <xref:System.DateTime.Kind%2A> 屬性為的值 <xref:System.DateTimeKind.Utc> 。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-249">That format is in Coordinated Universal Time (UTC) so you'll get a <xref:System.DateTime> value whose <xref:System.DateTime.Kind%2A> property is <xref:System.DateTimeKind.Utc>.</span></span> <span data-ttu-id="5c8e1-250">如果您偏好以時區表示的日期，則需要撰寫自訂轉換方法。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-250">If you prefer a date represented in your time zone, you'll need to write a custom conversion method.</span></span> <span data-ttu-id="5c8e1-251">首先，定義 `public` 屬性，以保存類別中日期和時間的 UTC 標記法 `Repository` ，以及傳回轉換成 `LastPush` `readonly` 當地時間之日期的屬性：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-251">First, define a `public` property that will hold the UTC representation of the date and time in your `Repository` class and a `LastPush` `readonly` property that returns the date converted to local time:</span></span>

```csharp
[JsonPropertyName("pushed_at")]
public DateTime LastPushUtc { get; set; }

public DateTime LastPush => LastPushUtc.ToLocalTime();
```

<span data-ttu-id="5c8e1-252">讓我們來看一下我們剛才定義的新結構。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-252">Let's go over the new constructs we just defined.</span></span> <span data-ttu-id="5c8e1-253">`LastPush`屬性是使用存取子的*運算式主體成員*所定義 `get` 。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-253">The `LastPush` property is defined using an *expression-bodied member* for the `get` accessor.</span></span> <span data-ttu-id="5c8e1-254">沒有 `set` 存取子。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-254">There is no `set` accessor.</span></span> <span data-ttu-id="5c8e1-255">省略 `set` 存取子是您在 c # 中定義*唯讀*屬性的方式。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-255">Omitting the `set` accessor is how you define a *read-only* property in C#.</span></span> <span data-ttu-id="5c8e1-256">(是的，您可以用 C# 來建立「唯寫」\*\* 屬性，但其值會受到限制)。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-256">(Yes, you can create *write-only* properties in C#, but their value is limited.)</span></span>

<span data-ttu-id="5c8e1-257">最後，請在主控台中再多新增一個輸出陳述式，這樣您便已準備好來重新建置及執行此應用程式：</span><span class="sxs-lookup"><span data-stu-id="5c8e1-257">Finally, add one more output statement in the console, and you're ready to build and run this app again:</span></span>

```csharp
Console.WriteLine(repo.LastPush);
```

<span data-ttu-id="5c8e1-258">您的版本現在應該與[完成範例](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient)相符。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-258">Your version should now match the [finished sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-webapiclient).</span></span>

## <a name="conclusion"></a><span data-ttu-id="5c8e1-259">結論</span><span class="sxs-lookup"><span data-stu-id="5c8e1-259">Conclusion</span></span>

<span data-ttu-id="5c8e1-260">本教學課程示範了如何提出 Web 要求、剖析結果，以及顯示這些結果的屬性。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-260">This tutorial showed you how to make web requests, parse the result, and display properties of those results.</span></span> <span data-ttu-id="5c8e1-261">您也在專案中新增了新的套件作為相依性。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-261">You've also added new packages as dependencies in your project.</span></span> <span data-ttu-id="5c8e1-262">您已了解一些支援物件導向技術的 C# 語言功能。</span><span class="sxs-lookup"><span data-stu-id="5c8e1-262">You've seen some of the features of the C# language that support object-oriented techniques.</span></span>

<a name="dotnet-restore-note"></a>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
