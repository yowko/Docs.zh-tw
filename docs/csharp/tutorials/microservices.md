---
title: 在 Docker 中裝載的微服務 - C#
description: 了解如何建立在 Docker 容器中執行的 ASP.NET Core 服務
ms.date: 06/08/2017
ms.assetid: 87e93838-a363-4813-b859-7356023d98ed
ms.openlocfilehash: b043b0109bcf8a67867d2c73a5ab22e43a4963cf
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207918"
---
# <a name="microservices-hosted-in-docker"></a><span data-ttu-id="78899-103">在 Docker 中裝載的微服務</span><span class="sxs-lookup"><span data-stu-id="78899-103">Microservices hosted in Docker</span></span>

<span data-ttu-id="78899-104">本教學課程詳細說明在 Docker 容器中建置和部署 ASP.NET Core 微服務所需的工作。</span><span class="sxs-lookup"><span data-stu-id="78899-104">This tutorial details the tasks necessary to build and deploy an ASP.NET Core microservice in a Docker container.</span></span> <span data-ttu-id="78899-105">您將在本教學課程中了解︰</span><span class="sxs-lookup"><span data-stu-id="78899-105">During the course of this tutorial, you'll learn:</span></span>

* <span data-ttu-id="78899-106">如何產生 ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="78899-106">How to generate an ASP.NET Core application.</span></span>
* <span data-ttu-id="78899-107">如何建立開發 Docker 環境。</span><span class="sxs-lookup"><span data-stu-id="78899-107">How to create a development Docker environment.</span></span>
* <span data-ttu-id="78899-108">如何根據現有的映像來建立 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="78899-108">How to build a Docker image based on an existing image.</span></span>
* <span data-ttu-id="78899-109">如何將您的服務部署到 Docker 容器中。</span><span class="sxs-lookup"><span data-stu-id="78899-109">How to deploy your service into a Docker container.</span></span>

<span data-ttu-id="78899-110">您也會在本教學課程當中看到一些 C# 語言功能︰</span><span class="sxs-lookup"><span data-stu-id="78899-110">Along the way, you'll also see some C# language features:</span></span>

* <span data-ttu-id="78899-111">如何將 C# 物件轉換成 JSON 裝載。</span><span class="sxs-lookup"><span data-stu-id="78899-111">How to convert C# objects into JSON payloads.</span></span>
* <span data-ttu-id="78899-112">如何建置不可變的資料傳輸物件。</span><span class="sxs-lookup"><span data-stu-id="78899-112">How to build immutable Data Transfer Objects.</span></span>
* <span data-ttu-id="78899-113">如何處理傳入 HTTP 要求和產生 HTTP 回應。</span><span class="sxs-lookup"><span data-stu-id="78899-113">How to process incoming HTTP Requests and generate the HTTP Response.</span></span>
* <span data-ttu-id="78899-114">如何使用可為 Null 的實值型別。</span><span class="sxs-lookup"><span data-stu-id="78899-114">How to work with nullable value types.</span></span>

<span data-ttu-id="78899-115">您可以[檢視或下載本主題的範例應用程式 (英文)](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice)。</span><span class="sxs-lookup"><span data-stu-id="78899-115">You can [view or download the sample app](https://github.com/dotnet/samples/tree/master/csharp/getting-started/WeatherMicroservice) for this topic.</span></span> <span data-ttu-id="78899-116">如需下載指示，請參閱[範例和教學課程](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)。</span><span class="sxs-lookup"><span data-stu-id="78899-116">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

## <a name="why-docker"></a><span data-ttu-id="78899-117">為何要使用 Docker？</span><span class="sxs-lookup"><span data-stu-id="78899-117">Why Docker?</span></span>

<span data-ttu-id="78899-118">Docker 可讓您輕鬆地建立標準的機器映像，在資料中心或公用雲端裝載您的服務。</span><span class="sxs-lookup"><span data-stu-id="78899-118">Docker makes it easy to create standard machine images to host your services in a data center, or the public cloud.</span></span> <span data-ttu-id="78899-119">Docker 可讓您設定映像，並視需要複製來調整應用程式的安裝。</span><span class="sxs-lookup"><span data-stu-id="78899-119">Docker enables you to configure the image, and replicate it as needed to scale the installation of your application.</span></span>

<span data-ttu-id="78899-120">本教學課程中的所有程式碼可在任何 .NET Core 環境中運作。</span><span class="sxs-lookup"><span data-stu-id="78899-120">All the code in this tutorial will work in any .NET Core environment.</span></span>
<span data-ttu-id="78899-121">Docker 安裝的其他工作均適用於 ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="78899-121">The additional tasks for a Docker installation will work for an ASP.NET Core application.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="78899-122">必要條件</span><span class="sxs-lookup"><span data-stu-id="78899-122">Prerequisites</span></span>

<span data-ttu-id="78899-123">您必須設定電腦以執行 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="78899-123">You’ll need to setup your machine to run .NET Core.</span></span> <span data-ttu-id="78899-124">您可以在 [.NET Core (英文)](https://www.microsoft.com/net/core) 頁面找到安裝指示。</span><span class="sxs-lookup"><span data-stu-id="78899-124">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span>
<span data-ttu-id="78899-125">您可以在 Windows、Linux、macOS 或是 Docker 容器中執行此應用程式。</span><span class="sxs-lookup"><span data-stu-id="78899-125">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="78899-126">您將必須安裝慣用的程式碼編輯器。</span><span class="sxs-lookup"><span data-stu-id="78899-126">You’ll need to install your favorite code editor.</span></span> <span data-ttu-id="78899-127">以下說明使用 [Visual Studio Code (英文)](https://code.visualstudio.com/)，這是開放原始碼的跨平台編輯器。</span><span class="sxs-lookup"><span data-stu-id="78899-127">The descriptions below use [Visual Studio Code](https://code.visualstudio.com/) which is an open source, cross platform editor.</span></span> <span data-ttu-id="78899-128">不過，您可以使用您熟悉的任何工具。</span><span class="sxs-lookup"><span data-stu-id="78899-128">However, you can use whatever tools you are comfortable with.</span></span>

<span data-ttu-id="78899-129">您也需要安裝 Docker 引擎。</span><span class="sxs-lookup"><span data-stu-id="78899-129">You'll also need to install the Docker engine.</span></span> <span data-ttu-id="78899-130">如需適用於您平台的指示，請參閱 [Docker 安裝頁面 (英文)](http://www.docker.com/products/docker)。</span><span class="sxs-lookup"><span data-stu-id="78899-130">See the [Docker Installation page](http://www.docker.com/products/docker) for instructions for your platform.</span></span>
<span data-ttu-id="78899-131">Docker 可以安裝在許多 Linux 發行版本、macOS 或 Windows。</span><span class="sxs-lookup"><span data-stu-id="78899-131">Docker can be installed in many Linux distributions, macOS, or Windows.</span></span> <span data-ttu-id="78899-132">上述的參考頁面包含每個可用安裝的相關章節。</span><span class="sxs-lookup"><span data-stu-id="78899-132">The page referenced above contains sections to each of the available installations.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="78899-133">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="78899-133">Create the Application</span></span>

<span data-ttu-id="78899-134">現在您已安裝完所有工具，請建立新的 ASP.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="78899-134">Now that you've installed all the tools, create a new ASP.NET Core application.</span></span> <span data-ttu-id="78899-135">若要這樣做，請建立稱為 "WeatherMicroservice" 的新目錄，並以您最愛的 Shell 在該目錄中執行下列命令：</span><span class="sxs-lookup"><span data-stu-id="78899-135">To do that, create a new directory called "WeatherMicroservice" and execute the following command in that directory in your favorite shell:</span></span>

```console
dotnet new web
```

<span data-ttu-id="78899-136">`dotnet` 命令會執行 .NET 開發所需的工具。</span><span class="sxs-lookup"><span data-stu-id="78899-136">The `dotnet` command runs the tools necessary for .NET development.</span></span> <span data-ttu-id="78899-137">每個動詞都會執行不同的命令。</span><span class="sxs-lookup"><span data-stu-id="78899-137">Each verb executes a different command.</span></span>

<span data-ttu-id="78899-138">`dotnet new` 命令用來建立 .Net Core 專案。</span><span class="sxs-lookup"><span data-stu-id="78899-138">The `dotnet new` command is used to create .Net Core projects.</span></span>

<span data-ttu-id="78899-139">針對此微服務，我們想要最簡單且最輕量的 Web 應用程式，因此使用了「空的 ASP.NET Core」範本，方法是指定其簡短名稱：`web`。</span><span class="sxs-lookup"><span data-stu-id="78899-139">For this microservice, we want the simplest, most lightweight web application possible, so we used the "ASP.NET Core Empty" template, by specifying its short name, `web`.</span></span>

<span data-ttu-id="78899-140">這個範本會為您建立四個檔案︰</span><span class="sxs-lookup"><span data-stu-id="78899-140">The template creates four files for you:</span></span>

* <span data-ttu-id="78899-141">Startup.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="78899-141">A Startup.cs file.</span></span> <span data-ttu-id="78899-142">這當中包含應用程式的基礎。</span><span class="sxs-lookup"><span data-stu-id="78899-142">This contains the basis of the application.</span></span>
* <span data-ttu-id="78899-143">Program.cs 檔案。</span><span class="sxs-lookup"><span data-stu-id="78899-143">A Program.cs file.</span></span> <span data-ttu-id="78899-144">這當中包含應用程式的進入點。</span><span class="sxs-lookup"><span data-stu-id="78899-144">This contains the entry point of the application.</span></span>
* <span data-ttu-id="78899-145">WeatherMicroservice.csproj 檔案。</span><span class="sxs-lookup"><span data-stu-id="78899-145">A WeatherMicroservice.csproj file.</span></span> <span data-ttu-id="78899-146">這是應用程式的組建檔案。</span><span class="sxs-lookup"><span data-stu-id="78899-146">This is the build file for the application.</span></span>
* <span data-ttu-id="78899-147">Properties/launchSettings.json 檔案。</span><span class="sxs-lookup"><span data-stu-id="78899-147">A Properties/launchSettings.json file.</span></span> <span data-ttu-id="78899-148">這包含 IDE 所使用的偵錯設定。</span><span class="sxs-lookup"><span data-stu-id="78899-148">This contains debugging settings used by IDEs.</span></span>

<span data-ttu-id="78899-149">現在，您可以執行範本產生的應用程式：</span><span class="sxs-lookup"><span data-stu-id="78899-149">Now you can run the template generated application:</span></span>

```console
dotnet run
```

<span data-ttu-id="78899-150">此命令會先還原建置應用程式所需的相依性，然後它會建置應用程式。</span><span class="sxs-lookup"><span data-stu-id="78899-150">This command will first restore dependencies required to build the application and then it will build the application.</span></span>

<span data-ttu-id="78899-151">預設組態會接聽 `http://localhost:5000`。</span><span class="sxs-lookup"><span data-stu-id="78899-151">The default configuration listens to `http://localhost:5000`.</span></span> <span data-ttu-id="78899-152">您可以開啟瀏覽器，然後瀏覽至該頁面，就會看到「Hello World!」</span><span class="sxs-lookup"><span data-stu-id="78899-152">You can open a browser and navigate to that page and see a "Hello World!"</span></span> <span data-ttu-id="78899-153">訊息。</span><span class="sxs-lookup"><span data-stu-id="78899-153">message.</span></span>

<span data-ttu-id="78899-154">當您完成時，您可以按 <kbd>Ctrl</kbd>+<kbd>C</kbd> 關閉應用程式。</span><span class="sxs-lookup"><span data-stu-id="78899-154">When you're done, you can shut down the application by pressing <kbd>Ctrl</kbd>+<kbd>C</kbd>.</span></span>

### <a name="anatomy-of-an-aspnet-core-application"></a><span data-ttu-id="78899-155">ASP.NET Core 應用程式的結構</span><span class="sxs-lookup"><span data-stu-id="78899-155">Anatomy of an ASP.NET Core application</span></span>

<span data-ttu-id="78899-156">既然您已經建置應用程式，現在讓我們來看看如何實作這項功能。</span><span class="sxs-lookup"><span data-stu-id="78899-156">Now that you've built the application, let's look at how this functionality is implemented.</span></span> <span data-ttu-id="78899-157">此時，產生的檔案當中有兩個特別有趣︰WeatherMicroservice.csproj 和 Startup.cs。</span><span class="sxs-lookup"><span data-stu-id="78899-157">There are two of the generated files that are particularly interesting at this point: WeatherMicroservice.csproj and Startup.cs.</span></span> 

<span data-ttu-id="78899-158">.csproj 檔包含該專案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="78899-158">The .csproj file contains information about the project.</span></span>
<span data-ttu-id="78899-159">最令人關注的兩個節點是 `<TargetFramework>` 和 `<PackageReference>`。</span><span class="sxs-lookup"><span data-stu-id="78899-159">The two nodes that are most interesting are `<TargetFramework>` and `<PackageReference>`.</span></span>

<span data-ttu-id="78899-160">`<TargetFramework>` 節點指定會執行此應用程式的 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="78899-160">The `<TargetFramework>` node specifies the version of .NET that will run this application.</span></span>

<span data-ttu-id="78899-161">每個 `<PackageReference>` 節點是用來指定此應用程式所需的套件。</span><span class="sxs-lookup"><span data-stu-id="78899-161">Each `<PackageReference>` node is used to specify a package that is needed for this application.</span></span>

<span data-ttu-id="78899-162">在 Startup.cs 中實作應用程式。</span><span class="sxs-lookup"><span data-stu-id="78899-162">The application is implemented in Startup.cs.</span></span> <span data-ttu-id="78899-163">此檔案包含啟動類別。</span><span class="sxs-lookup"><span data-stu-id="78899-163">This file contains the startup class.</span></span>

<span data-ttu-id="78899-164">ASP.NET Core 基礎結構會呼叫這兩個方法，來設定和執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="78899-164">The two methods are called by the ASP.NET Core infrastructure to configure and run the application.</span></span> <span data-ttu-id="78899-165">`ConfigureServices` 方法描述此應用程式所需的服務。</span><span class="sxs-lookup"><span data-stu-id="78899-165">The `ConfigureServices` method describes the services that are necessary for this application.</span></span> <span data-ttu-id="78899-166">您正在建置精簡的微服務，因此它不需要設定任何相依性。</span><span class="sxs-lookup"><span data-stu-id="78899-166">You're building a lean microservice, so it doesn't need to configure any dependencies.</span></span> <span data-ttu-id="78899-167">`Configure` 方法會設定傳入 HTTP 要求的處理常式。</span><span class="sxs-lookup"><span data-stu-id="78899-167">The `Configure` method configures the handlers for incoming HTTP Requests.</span></span> <span data-ttu-id="78899-168">範本會產生能以「Hello World!」文字回應任何要求的簡單處理常式。</span><span class="sxs-lookup"><span data-stu-id="78899-168">The template generates a simple handler that responds to any request with the text 'Hello World!'.</span></span>

## <a name="build-a-microservice"></a><span data-ttu-id="78899-169">建置微服務</span><span class="sxs-lookup"><span data-stu-id="78899-169">Build a microservice</span></span>

<span data-ttu-id="78899-170">您即將建置的服務可提供世界上任何地方的氣象報告。</span><span class="sxs-lookup"><span data-stu-id="78899-170">The service you're going to build will deliver weather reports from anywhere around the globe.</span></span> <span data-ttu-id="78899-171">在實際執行應用程式中，您會呼叫某些服務來擷取氣象資料。</span><span class="sxs-lookup"><span data-stu-id="78899-171">In a production application, you'd call some service to retrieve weather data.</span></span> <span data-ttu-id="78899-172">對我們的範例而言，則將會產生隨機的氣象預報。</span><span class="sxs-lookup"><span data-stu-id="78899-172">For our sample, we'll generate a random weather forecast.</span></span> 

<span data-ttu-id="78899-173">您必須執行數項工作，才能實作隨機的氣象服務︰</span><span class="sxs-lookup"><span data-stu-id="78899-173">There are a number of tasks you'll need to perform in order to implement our random weather service:</span></span>

* <span data-ttu-id="78899-174">剖析傳入要求以讀取緯度和經度。</span><span class="sxs-lookup"><span data-stu-id="78899-174">Parse the incoming request to read the latitude and longitude.</span></span>
* <span data-ttu-id="78899-175">產生一些隨機的預測資料。</span><span class="sxs-lookup"><span data-stu-id="78899-175">Generate some random forecast data.</span></span>
* <span data-ttu-id="78899-176">將隨機的預測資料從 C# 物件轉換為 JSON 封包。</span><span class="sxs-lookup"><span data-stu-id="78899-176">Convert that random forecast data from C# objects into JSON packets.</span></span>
* <span data-ttu-id="78899-177">設定回應標頭，指出您的服務會傳送回 JSON。</span><span class="sxs-lookup"><span data-stu-id="78899-177">Set the response header to indicate that your service sends back JSON.</span></span>
* <span data-ttu-id="78899-178">撰寫回應。</span><span class="sxs-lookup"><span data-stu-id="78899-178">Write the response.</span></span>

<span data-ttu-id="78899-179">下一節將逐步說明每一個步驟。</span><span class="sxs-lookup"><span data-stu-id="78899-179">The next sections walk you through each of these steps.</span></span>

### <a name="parsing-the-query-string"></a><span data-ttu-id="78899-180">剖析查詢字串</span><span class="sxs-lookup"><span data-stu-id="78899-180">Parsing the Query String</span></span>

<span data-ttu-id="78899-181">一開始要先剖析查詢字串。</span><span class="sxs-lookup"><span data-stu-id="78899-181">You'll begin by parsing the query string.</span></span> <span data-ttu-id="78899-182">服務會接受下列格式查詢字串的 'lat' 和 'long' 引數：</span><span class="sxs-lookup"><span data-stu-id="78899-182">The service will accept 'lat' and 'long' arguments on the query string in this form:</span></span>

```
http://localhost:5000/?lat=-35.55&long=-12.35
```

<span data-ttu-id="78899-183">您需要的所有變更都是針對啟動類別中的 `app.Run` 定義為引數的 Lambda 運算式中進行。</span><span class="sxs-lookup"><span data-stu-id="78899-183">All the changes you need to make are in the lambda expression defined as the argument to `app.Run` in your startup class.</span></span>

<span data-ttu-id="78899-184">Lambda 運算式中的引數就是要求的 `HttpContext`。</span><span class="sxs-lookup"><span data-stu-id="78899-184">The argument on the lambda expression is the `HttpContext` for the request.</span></span> <span data-ttu-id="78899-185">它的其中一個屬性是 `Request` 物件。</span><span class="sxs-lookup"><span data-stu-id="78899-185">One of its properties is the `Request` object.</span></span> <span data-ttu-id="78899-186">`Request` 物件具有 `Query` 屬性，其中包含要求的查詢字串上所有值的字典。</span><span class="sxs-lookup"><span data-stu-id="78899-186">The `Request` object has a `Query` property that contains a dictionary of all the values on the query string for the request.</span></span> <span data-ttu-id="78899-187">首先要加入的內容是尋找緯度和經度值︰</span><span class="sxs-lookup"><span data-stu-id="78899-187">The first addition is to find the latitude and longitude values:</span></span>

[!code-csharp[ReadQueryString](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ReadQueryString "read variables from the query string")]

<span data-ttu-id="78899-188">`Query` 字典值為 `StringValue` 型別。</span><span class="sxs-lookup"><span data-stu-id="78899-188">The `Query` dictionary values are `StringValue` type.</span></span> <span data-ttu-id="78899-189">該型別可以包含字串集合。</span><span class="sxs-lookup"><span data-stu-id="78899-189">That type can contain a collection of strings.</span></span> <span data-ttu-id="78899-190">對於氣象服務而言，每個值都是單一字串。</span><span class="sxs-lookup"><span data-stu-id="78899-190">For your weather service, each value is a single string.</span></span> <span data-ttu-id="78899-191">這就是在上述程式碼中呼叫 `FirstOrDefault()` 的原因。</span><span class="sxs-lookup"><span data-stu-id="78899-191">That's why there's the call to `FirstOrDefault()` in the code above.</span></span> 

<span data-ttu-id="78899-192">接著，您必須將字串轉換為雙精度浮點數。</span><span class="sxs-lookup"><span data-stu-id="78899-192">Next, you need to convert the strings to doubles.</span></span> <span data-ttu-id="78899-193">您用來將字串轉換為雙精度浮點數的方法是 `double.TryParse()`：</span><span class="sxs-lookup"><span data-stu-id="78899-193">The method you'll use to convert the string to a double is `double.TryParse()`:</span></span>

```csharp
bool TryParse(string s, out double result);
```

<span data-ttu-id="78899-194">此方法會利用 C# 的輸出參數，指出該輸入字串是否能轉換為雙精度浮點數。</span><span class="sxs-lookup"><span data-stu-id="78899-194">This method leverages C# out parameters to indicate if the input string can be converted to a double.</span></span> <span data-ttu-id="78899-195">如果字串的確是有效的雙精度浮點數表示法，該方法會傳回 true，`result` 引數也會包含值。</span><span class="sxs-lookup"><span data-stu-id="78899-195">If the string does represent a valid representation for a double, the method returns true, and the `result` argument contains the value.</span></span> <span data-ttu-id="78899-196">如果字串不代表有效的雙精度浮點數，則該方法會傳回 false。</span><span class="sxs-lookup"><span data-stu-id="78899-196">If the string does not represent a valid double, the method returns false.</span></span>

<span data-ttu-id="78899-197">您可以採用該 API 搭配使用「擴充方法」，來傳回「可為 Null 的雙精度浮點數」。</span><span class="sxs-lookup"><span data-stu-id="78899-197">You can adapt that API with the use of an *extension method* that returns a *nullable double*.</span></span> <span data-ttu-id="78899-198">「可為 Null 的實值型別」是代表一些實值型別的一種型別，它也可以保留遺漏值或 Null 值。</span><span class="sxs-lookup"><span data-stu-id="78899-198">A *nullable value type* is a type that represents some value type, and can also hold a missing, or null value.</span></span> <span data-ttu-id="78899-199">在型別宣告附加 `?` 字元，即表示它是可為 Null 的型別。</span><span class="sxs-lookup"><span data-stu-id="78899-199">A nullable type is represented by appending the `?` character to the type declaration.</span></span> 

<span data-ttu-id="78899-200">擴充方法是指定義為靜態方法，但在第一個參數加上 `this` 修飾詞的方法，可以如同是該類別的成員一般來呼叫。</span><span class="sxs-lookup"><span data-stu-id="78899-200">Extension methods are methods that are defined as static methods, but by adding the `this` modifier on the first parameter, can be called as though they are members of that class.</span></span> <span data-ttu-id="78899-201">擴充方法只能在靜態類別中定義。</span><span class="sxs-lookup"><span data-stu-id="78899-201">Extension methods may only be defined in static classes.</span></span> <span data-ttu-id="78899-202">以下的類別定義包含可用於剖析的擴充方法：</span><span class="sxs-lookup"><span data-stu-id="78899-202">Here's the definition of the class containing the extension method for parse:</span></span>

[!code-csharp[TryParseExtension](../../../samples/csharp/getting-started/WeatherMicroservice/Extensions.cs#TryParseExtension "try parse to a nullable")]

<span data-ttu-id="78899-203">在呼叫擴充方法之前，請先將目前的文化特性 (Culture) 變更為不區分：</span><span class="sxs-lookup"><span data-stu-id="78899-203">Before calling the extension method, change the current culture to invariant:</span></span>

[!code-csharp[SetCulture](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#SetCulture "set current culture to invariant")]

<span data-ttu-id="78899-204">這可以確保應用程式剖析數字的方式在任何伺服器上都相同，而不論它的預設文化特性。</span><span class="sxs-lookup"><span data-stu-id="78899-204">This ensures that your application parses numbers the same on any server, regardless of its default culture.</span></span>

<span data-ttu-id="78899-205">現在您可以使用擴充方法，將查詢字串引數轉換成 double 類型︰</span><span class="sxs-lookup"><span data-stu-id="78899-205">Now you can use the extension method to convert the query string arguments into the double type:</span></span>

[!code-csharp[UseTryParse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#UseTryParse "Use the try parse extension method")]

<span data-ttu-id="78899-206">更新回應以包含該引數的值，即可輕鬆地測試剖析程式碼︰</span><span class="sxs-lookup"><span data-stu-id="78899-206">To easily test the parsing code, update the response to include the values of the arguments:</span></span>

[!code-csharp[WriteResponse](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#WriteResponse "Write the output response")]

<span data-ttu-id="78899-207">此時，您可以執行 Web 應用程式，並查看您的剖析程式碼是否可以正常運作。</span><span class="sxs-lookup"><span data-stu-id="78899-207">At this point, you can run the web application and see if your parsing code is working.</span></span> <span data-ttu-id="78899-208">將值加入至瀏覽器中的 Web 要求後，您應該會看到更新的結果。</span><span class="sxs-lookup"><span data-stu-id="78899-208">Add values to the web request in a browser, and you should see the updated results.</span></span>

### <a name="build-a-random-weather-forecast"></a><span data-ttu-id="78899-209">建立隨機的氣象預報</span><span class="sxs-lookup"><span data-stu-id="78899-209">Build a random weather forecast</span></span>

<span data-ttu-id="78899-210">您的下一個工作是建立隨機的氣象預報。</span><span class="sxs-lookup"><span data-stu-id="78899-210">Your next task is to build a random weather forecast.</span></span> <span data-ttu-id="78899-211">讓我們從保存您所想要氣象預報值的資料容器開始︰</span><span class="sxs-lookup"><span data-stu-id="78899-211">Let's start with a data container that holds the values you'd want for a weather forecast:</span></span>

```csharp
public class WeatherReport
{
    private static readonly string[] PossibleConditions =
    {
        "Sunny",
        "Mostly Sunny",
        "Partly Sunny",
        "Partly Cloudy",
        "Mostly Cloudy",
        "Rain"
    };

    public int HighTemperatureFahrenheit { get; }
    public int LowTemperatureFahrenheit { get; }
    public int AverageWindSpeedMph { get; }
    public string Condition { get; }
}
```

<span data-ttu-id="78899-212">接下來，建置會隨機設定這些值的建構函式。</span><span class="sxs-lookup"><span data-stu-id="78899-212">Next, build a constructor that randomly sets those values.</span></span> <span data-ttu-id="78899-213">此建構函式會使用經度和緯度的值來植入 `Random` 數字產生器。</span><span class="sxs-lookup"><span data-stu-id="78899-213">This constructor uses the values for the latitude and longitude to seed the `Random` number generator.</span></span> <span data-ttu-id="78899-214">這表示相同位置會有相同的預報。</span><span class="sxs-lookup"><span data-stu-id="78899-214">That means the forecast for the same location is the same.</span></span> <span data-ttu-id="78899-215">如果您變更緯度和經度的引數，您會得到不同的預報 (因為您從不同的種子開始)。</span><span class="sxs-lookup"><span data-stu-id="78899-215">If you change the arguments for the latitude and longitude, you'll get a different forecast (because you start with a different seed).</span></span>

[!code-csharp[WeatherReportConstructor](../../../samples/csharp/getting-started/WeatherMicroservice/WeatherReport.cs#WeatherReportConstructor "Weather Report Constructor")]

<span data-ttu-id="78899-216">您現在能以您的回應方法產生 5 天的預報︰</span><span class="sxs-lookup"><span data-stu-id="78899-216">You can now generate the 5-day forecast in your response method:</span></span>

```csharp
if (latitude.HasValue && longitude.HasValue)
{
    var forecast = new List<WeatherReport>();
    for (var days = 1; days <= 5; days++)
    {
        forecast.Add(new WeatherReport(latitude.Value, longitude.Value, days));
    }
}
```

### <a name="build-the-json-response"></a><span data-ttu-id="78899-217">建立 JSON 回應</span><span class="sxs-lookup"><span data-stu-id="78899-217">Build the JSON response</span></span>

<span data-ttu-id="78899-218">伺服器上最後的程式碼工作是將 `WeatherReport` 清單轉換為 JSON 文件，並傳送回用戶端。</span><span class="sxs-lookup"><span data-stu-id="78899-218">The final code task on the server is to convert the `WeatherReport` list into JSON document, and send that back to the client.</span></span> <span data-ttu-id="78899-219">現在就開始建立 JSON 文件。</span><span class="sxs-lookup"><span data-stu-id="78899-219">Let's start by creating the JSON document.</span></span> <span data-ttu-id="78899-220">您要將 Newtonsoft JSON 序列化程式新增至相依性清單。</span><span class="sxs-lookup"><span data-stu-id="78899-220">You'll add the Newtonsoft JSON serializer to the list of dependencies.</span></span> <span data-ttu-id="78899-221">您可以使用下列 `dotnet` 命令來完成：</span><span class="sxs-lookup"><span data-stu-id="78899-221">You can do that using the following `dotnet` command:</span></span>

```console
dotnet add package Newtonsoft.Json
```

<span data-ttu-id="78899-222">然後，您可以使用 `JsonConvert` 類別來將該物件撰寫為字串︰</span><span class="sxs-lookup"><span data-stu-id="78899-222">Then, you can use the `JsonConvert` class to write the object to a string:</span></span>

[!code-csharp[ConvertToJson](../../../samples/csharp/getting-started/WeatherMicroservice/Startup.cs#ConvertToJSON "Convert objects to JSON")]

<span data-ttu-id="78899-223">上述程式碼會將預測物件 (`WeatherForecast` 物件清單) 轉換為 JSON 文件。</span><span class="sxs-lookup"><span data-stu-id="78899-223">The code above converts the forecast object (a list of `WeatherForecast` objects) into a JSON document.</span></span> <span data-ttu-id="78899-224">在您完成建構回應文件之後，您可以將內容類型設定為 `application/json`，然後撰寫字串。</span><span class="sxs-lookup"><span data-stu-id="78899-224">After you've constructed the response document, you set the content type to `application/json`, and write the string.</span></span>

<span data-ttu-id="78899-225">應用程式現在會執行，並傳回隨機的預測。</span><span class="sxs-lookup"><span data-stu-id="78899-225">The application now runs and returns random forecasts.</span></span>

## <a name="build-a-docker-image"></a><span data-ttu-id="78899-226">建置 Docker 映像</span><span class="sxs-lookup"><span data-stu-id="78899-226">Build a Docker image</span></span>

<span data-ttu-id="78899-227">最後一項工作是在 Docker 中執行應用程式。</span><span class="sxs-lookup"><span data-stu-id="78899-227">Our final task is to run the application in Docker.</span></span> <span data-ttu-id="78899-228">我們會建立 Docker 容器，執行代表應用程式的 Docker 映像。</span><span class="sxs-lookup"><span data-stu-id="78899-228">We'll create a Docker container that runs a Docker image that represents our application.</span></span>

<span data-ttu-id="78899-229">「Docker 映像」這個檔案會定義用來執行應用程式的環境。</span><span class="sxs-lookup"><span data-stu-id="78899-229">A ***Docker Image*** is a file that defines the environment for running the application.</span></span>

<span data-ttu-id="78899-230">「Docker 容器」代表 Docker 映像的執行中執行個體。</span><span class="sxs-lookup"><span data-stu-id="78899-230">A ***Docker Container*** represents a running instance of a Docker Image.</span></span>

<span data-ttu-id="78899-231">比方說，您可以將「Docker 映像」視為「類別」，而將「Docker 容器」視為物件，或該類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="78899-231">By analogy, you can think of the *Docker Image* as a *class*, and the *Docker Container* as an object, or an instance of that class.</span></span>  

<span data-ttu-id="78899-232">下列 Dockerfile 會滿足我們的目的：</span><span class="sxs-lookup"><span data-stu-id="78899-232">The following Dockerfile will serve for our purposes:</span></span>

```
FROM microsoft/dotnet:2.1-sdk AS build
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out

# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

<span data-ttu-id="78899-233">讓我們來看看它的內容。</span><span class="sxs-lookup"><span data-stu-id="78899-233">Let's go over its contents.</span></span>

<span data-ttu-id="78899-234">第一行指定用來建置應用程式的來源映像：</span><span class="sxs-lookup"><span data-stu-id="78899-234">The first line specifies the source image used for building the application:</span></span>

```
FROM microsoft/dotnet:2.1-sdk AS build
```

<span data-ttu-id="78899-235">Docker 可讓您根據來源範本來設定機器映像。</span><span class="sxs-lookup"><span data-stu-id="78899-235">Docker allows you to configure a machine image based on a source template.</span></span> <span data-ttu-id="78899-236">這表示當您啟動時，不需要提供所有的機器參數，您只需要提供所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="78899-236">That means you don't have to supply all the machine parameters when you start, you only need to supply any changes.</span></span> <span data-ttu-id="78899-237">此處的變更會包含在我們的應用程式中。</span><span class="sxs-lookup"><span data-stu-id="78899-237">The changes here will be to include our application.</span></span>

<span data-ttu-id="78899-238">在這個範例中，我們將使用 `2.1-sdk` 版本的 `dotnet` 映像。</span><span class="sxs-lookup"><span data-stu-id="78899-238">In this sample, we'll use the `2.1-sdk` version of the `dotnet` image.</span></span> <span data-ttu-id="78899-239">這是建立 Docker 工作環境的最簡單方式。</span><span class="sxs-lookup"><span data-stu-id="78899-239">This is the easiest way to create a working Docker environment.</span></span> <span data-ttu-id="78899-240">此映像包含 .NET Core 執行階段和 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="78899-240">This image includes the .NET Core runtime, and the .NET Core SDK.</span></span>
<span data-ttu-id="78899-241">那可讓您更輕鬆地開始使用和建置，但是會建立較大的映像，因此我們將使用此映像來建置應用程式並使用不同的映像來執行它。</span><span class="sxs-lookup"><span data-stu-id="78899-241">That makes it easier to get started and build, but does create a larger image, so we'll use this image for building the application and a different image to run it.</span></span>

<span data-ttu-id="78899-242">接下來的幾行會安裝並建置您的應用程式︰</span><span class="sxs-lookup"><span data-stu-id="78899-242">The next lines setup and build your application:</span></span>

```
WORKDIR /app

# Copy csproj and restore as distinct layers
COPY *.csproj ./
RUN dotnet restore

# Copy everything else and build
COPY . ./
RUN dotnet publish -c Release -o out
```

<span data-ttu-id="78899-243">這會將目前目錄中的專案檔案複製到 Docker VM，並還原所有套件。</span><span class="sxs-lookup"><span data-stu-id="78899-243">This will copy the project file from the  current directory to the Docker VM, and restore all the packages.</span></span> <span data-ttu-id="78899-244">使用 DotNet CLI，表示 Docker 映像必須包含 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="78899-244">Using the dotnet CLI means that the Docker image must include the .NET Core SDK.</span></span> <span data-ttu-id="78899-245">之後，會複製您應用程式的其餘部分，然後 `dotnet
publish` 命令會建置和封裝您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="78899-245">After that, the rest of your application gets copied, and the `dotnet
publish` command builds and packages your application.</span></span>

<span data-ttu-id="78899-246">最後，我們會建立執行應用程式的第二個 Docker 映像：</span><span class="sxs-lookup"><span data-stu-id="78899-246">Finally, we create a second Docker image that runs the application:</span></span>

```
# Build runtime image
FROM microsoft/dotnet:2.1-aspnetcore-runtime
WORKDIR /app
COPY --from=build /app/out .
ENTRYPOINT ["dotnet", "WeatherMicroservice.dll"]
```

<span data-ttu-id="78899-247">此映像會使用 `2.1-aspnetcore-runtime` 版本的 `dotnet` 映像，這包含執行 ASP.NET Core 應用程式所需的所有項目，但不包含 .NET Core SDK。</span><span class="sxs-lookup"><span data-stu-id="78899-247">This image uses the `2.1-aspnetcore-runtime` version of the `dotnet` image, which contains everything necessary to run ASP.NET Core applications, but does not include the .NET Core SDK.</span></span> <span data-ttu-id="78899-248">這表示此映像不能用來建置 .NET Core 應用程式，但同時也讓最終的映像變小。</span><span class="sxs-lookup"><span data-stu-id="78899-248">This means this image can't be used to build .NET Core applications, but it also makes the final image smaller.</span></span>

<span data-ttu-id="78899-249">為了讓此能夠運作，我們從第一個映像複製已建置的應用程式到第二個映像。</span><span class="sxs-lookup"><span data-stu-id="78899-249">To make this work, we copy the built application from the first image to the second one.</span></span>

<span data-ttu-id="78899-250">`ENTRYPOINT` 命令會通知 Docker 哪個命令啟動服務。</span><span class="sxs-lookup"><span data-stu-id="78899-250">The `ENTRYPOINT` command informs Docker what command starts the service.</span></span>

## <a name="building-and-running-the-image-in-a-container"></a><span data-ttu-id="78899-251">在容器中建置和執行映像</span><span class="sxs-lookup"><span data-stu-id="78899-251">Building and running the image in a container</span></span>

<span data-ttu-id="78899-252">讓我們在 Docker 容器內建置映像並執行服務。</span><span class="sxs-lookup"><span data-stu-id="78899-252">Let's build an image and run the service inside a Docker container.</span></span> <span data-ttu-id="78899-253">不建議將本機目錄中的所有檔案複製到映像中。</span><span class="sxs-lookup"><span data-stu-id="78899-253">You don't want all the files from your local directory copied into the image.</span></span> <span data-ttu-id="78899-254">相反地，您要在容器中建置應用程式。</span><span class="sxs-lookup"><span data-stu-id="78899-254">Instead, you'll build the application in the container.</span></span> <span data-ttu-id="78899-255">您會建立 `.dockerignore` 檔案，以指定不要複製到映像中的目錄。</span><span class="sxs-lookup"><span data-stu-id="78899-255">You'll create a `.dockerignore` file to specify the directories that are not copied into the image.</span></span> <span data-ttu-id="78899-256">不建議複製任何的組建資產。</span><span class="sxs-lookup"><span data-stu-id="78899-256">You don't want any of the build assets copied.</span></span> <span data-ttu-id="78899-257">請在 `.dockerignore` 檔案中指定組建和發行目錄：</span><span class="sxs-lookup"><span data-stu-id="78899-257">Specify the build and publish directories in the `.dockerignore` file:</span></span>

```
bin/*
obj/*
out/*
```

<span data-ttu-id="78899-258">您會使用 `docker build` 命令來建置映像。</span><span class="sxs-lookup"><span data-stu-id="78899-258">You build the image using the `docker build` command.</span></span> <span data-ttu-id="78899-259">從包含您程式碼的目錄執行下列命令。</span><span class="sxs-lookup"><span data-stu-id="78899-259">Run the following command from the directory containing your code.</span></span>

```console
docker build -t weather-microservice .
```

<span data-ttu-id="78899-260">此命令會根據 Dockerfile 中的所有資訊來建置容器映像。</span><span class="sxs-lookup"><span data-stu-id="78899-260">This command builds the container image based on all the information in your Dockerfile.</span></span> <span data-ttu-id="78899-261">`-t` 引數會提供此容器映像的標籤或名稱。</span><span class="sxs-lookup"><span data-stu-id="78899-261">The `-t` argument provides a tag, or name, for this container image.</span></span> <span data-ttu-id="78899-262">在上述命令列中，Docker 容器所使用的標籤是 `weather-microservice`。</span><span class="sxs-lookup"><span data-stu-id="78899-262">In the command line above, the tag used for the Docker container is `weather-microservice`.</span></span> <span data-ttu-id="78899-263">此命令完成時，容器已準備好可以執行新的服務。</span><span class="sxs-lookup"><span data-stu-id="78899-263">When this command completes, you have a container ready to run your new service.</span></span> 

<span data-ttu-id="78899-264">執行下列命令以啟動容器並啟動您的服務︰</span><span class="sxs-lookup"><span data-stu-id="78899-264">Run the following command to start the container and launch your service:</span></span>

```console
docker run -d -p 80:80 --name hello-docker weather-microservice
```

<span data-ttu-id="78899-265">`-d` 選項表示要執行和目前終端機中斷連結的容器。</span><span class="sxs-lookup"><span data-stu-id="78899-265">The `-d` option means to run the container detached from the current terminal.</span></span> <span data-ttu-id="78899-266">這表示您不會在終端機看到命令輸出。</span><span class="sxs-lookup"><span data-stu-id="78899-266">That means you won't see the command output in your terminal.</span></span> <span data-ttu-id="78899-267">`-p` 選項會指出服務和主機之間的連接埠對應。</span><span class="sxs-lookup"><span data-stu-id="78899-267">The `-p` option indicates the port mapping between the service and the host.</span></span> <span data-ttu-id="78899-268">這裡指出連接埠 80 上的任何傳入要求都應該轉送到容器上的連接埠 80。</span><span class="sxs-lookup"><span data-stu-id="78899-268">Here it says that any incoming request on port 80 should be forwarded to port 80 on the container.</span></span> <span data-ttu-id="78899-269">使用 80 會符合您的服務正在接聽的連接埠，也就是實際執行應用程式的預設通訊埠。</span><span class="sxs-lookup"><span data-stu-id="78899-269">Using 80 matches the port your service is listening on, which is the default port for production applications.</span></span> <span data-ttu-id="78899-270">`--name` 引數會命名執行中的容器。</span><span class="sxs-lookup"><span data-stu-id="78899-270">The `--name` argument names your running container.</span></span> <span data-ttu-id="78899-271">該名稱可方便您使用該容器。</span><span class="sxs-lookup"><span data-stu-id="78899-271">It's a convenient name you can use to work with that container.</span></span>

<span data-ttu-id="78899-272">您可以透過檢查以下命令，來查看映像是否正在執行︰</span><span class="sxs-lookup"><span data-stu-id="78899-272">You can see if the image is running by checking the command:</span></span>

```console
docker ps
```

<span data-ttu-id="78899-273">如果您的容器正在執行中，您會在執行中處理序看到當中有一行將它列出。</span><span class="sxs-lookup"><span data-stu-id="78899-273">If your container is running, you'll see a line that lists it in the running processes.</span></span> <span data-ttu-id="78899-274">(它可能是唯一的一行。)</span><span class="sxs-lookup"><span data-stu-id="78899-274">(It may be the only one.)</span></span>

<span data-ttu-id="78899-275">開啟瀏覽器並瀏覽到 localhost，然後指定緯度和經度來測試您的服務︰</span><span class="sxs-lookup"><span data-stu-id="78899-275">You can test your service by opening a browser and navigating to localhost, and specifying a latitude and longitude:</span></span>

```
http://localhost/?lat=35.5&long=40.75
```

## <a name="attaching-to-a-running-container"></a><span data-ttu-id="78899-276">附加至執行中的容器</span><span class="sxs-lookup"><span data-stu-id="78899-276">Attaching to a running container</span></span>

<span data-ttu-id="78899-277">當您在命令視窗中執行服務時，您可以看到為每個要求印出的診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="78899-277">When you ran your service in a command window, you could see diagnostic information printed for each request.</span></span> <span data-ttu-id="78899-278">當您的容器在中斷連結模式中執行時，您看不到該資訊。</span><span class="sxs-lookup"><span data-stu-id="78899-278">You don't see that information when your container is running in detached mode.</span></span> <span data-ttu-id="78899-279">Docker attach 命令可讓您附加至執行中的容器，以便查看記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="78899-279">The Docker attach command enables you to attach to a running container so that you can see the log information.</span></span>  <span data-ttu-id="78899-280">請從命令視窗執行這個命令︰</span><span class="sxs-lookup"><span data-stu-id="78899-280">Run this command from a command window:</span></span>

```console
docker attach --sig-proxy=false hello-docker
```

<span data-ttu-id="78899-281">`--sig-proxy=false` 引數表示不會將 <kbd>Ctrl</kbd>+<kbd>C</kbd> 命令傳送到此容器處理序，而是會停止 `docker attach` 命令。</span><span class="sxs-lookup"><span data-stu-id="78899-281">The `--sig-proxy=false` argument means that <kbd>Ctrl</kbd>+<kbd>C</kbd> commands do not get sent to the container process, but rather stop the `docker attach` command.</span></span> <span data-ttu-id="78899-282">最後一個引數是要在 `docker run` 命令中提供給容器的名稱。</span><span class="sxs-lookup"><span data-stu-id="78899-282">The final argument is the name given to the container in the `docker run` command.</span></span> 

> [!NOTE]
> <span data-ttu-id="78899-283">您也可以使用 Docker 指派的容器識別碼來參考任何容器。</span><span class="sxs-lookup"><span data-stu-id="78899-283">You can also use the Docker assigned container ID to refer to any container.</span></span> <span data-ttu-id="78899-284">如果您並未在 `docker run` 中為您的容器指定名稱 ，您必須使用容器識別碼。</span><span class="sxs-lookup"><span data-stu-id="78899-284">If you didn't specify a name for your container in `docker run` you must use the container ID.</span></span>

<span data-ttu-id="78899-285">開啟瀏覽器，並瀏覽到您的服務。</span><span class="sxs-lookup"><span data-stu-id="78899-285">Open a browser and navigate to your service.</span></span> <span data-ttu-id="78899-286">您會在命令視窗中看到來自所附加執行中容器的診斷訊息。</span><span class="sxs-lookup"><span data-stu-id="78899-286">You'll see the diagnostic messages in the command windows from the attached running container.</span></span>

<span data-ttu-id="78899-287">按下 <kbd>Ctrl</kbd>+<kbd>C</kbd> 可停止附加處理序。</span><span class="sxs-lookup"><span data-stu-id="78899-287">Press <kbd>Ctrl</kbd>+<kbd>C</kbd> to stop the attach process.</span></span>

<span data-ttu-id="78899-288">當您完成使用容器，可以將它停止︰</span><span class="sxs-lookup"><span data-stu-id="78899-288">When you are done working with your container, you can stop it:</span></span>

```console
docker stop hello-docker
```

<span data-ttu-id="78899-289">您仍然可以重新啟動該容器和映像。</span><span class="sxs-lookup"><span data-stu-id="78899-289">The container and image is still available for you to restart.</span></span>  <span data-ttu-id="78899-290">如果您想要從機器中移除該容器，您可以使用此命令︰</span><span class="sxs-lookup"><span data-stu-id="78899-290">If you want to remove the container from your machine, you use this command:</span></span>

```console
docker rm hello-docker
```

<span data-ttu-id="78899-291">如果您想要從機器中移除未使用的映像，您可以使用此命令︰</span><span class="sxs-lookup"><span data-stu-id="78899-291">If you want to remove unused images from your machine, you use this command:</span></span>

```console
docker rmi weather-microservice
```

## <a name="conclusion"></a><span data-ttu-id="78899-292">結論</span><span class="sxs-lookup"><span data-stu-id="78899-292">Conclusion</span></span> 

<span data-ttu-id="78899-293">在本教學課程中，您已建置 ASP.NET Core 微服務，並新增一些簡單的功能。</span><span class="sxs-lookup"><span data-stu-id="78899-293">In this tutorial, you built an ASP.NET Core microservice, and added a few simple features.</span></span>

<span data-ttu-id="78899-294">您為該服務建置了 Docker 容器映像，並在您的機器上執行該容器。</span><span class="sxs-lookup"><span data-stu-id="78899-294">You built a Docker container image for that service, and ran that container on your machine.</span></span> <span data-ttu-id="78899-295">您將終端機視窗附加至該服務，並看到來自您服務的診斷訊息。</span><span class="sxs-lookup"><span data-stu-id="78899-295">You attached a terminal window to the service, and saw the diagnostic messages from your service.</span></span>

<span data-ttu-id="78899-296">過程中，您也看到一些 C# 語言功能的實際運作。</span><span class="sxs-lookup"><span data-stu-id="78899-296">Along the way, you saw several features of the C# language in action.</span></span>
