---
title: Azure 功能 - 無伺服器應用
description: Azure 函數提供跨多種語言（C#、JavaScript、JAVA）和平臺的無伺服器功能，以提供事件驅動的即時縮放代碼。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 8764e6a33f3fdd53e60fa767d0fb584a9c07de7e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401610"
---
# <a name="azure-functions"></a><span data-ttu-id="518a3-103">Azure Functions</span><span class="sxs-lookup"><span data-stu-id="518a3-103">Azure Functions</span></span>

<span data-ttu-id="518a3-104">Azure 函數提供無伺服器計算體驗。</span><span class="sxs-lookup"><span data-stu-id="518a3-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="518a3-105">函數由*觸發器*調用（例如訪問 HTTP 終結點或計時器），並執行代碼或業務邏輯塊。</span><span class="sxs-lookup"><span data-stu-id="518a3-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="518a3-106">函數還支援連接到存儲和佇列等資源的專用*綁定*。</span><span class="sxs-lookup"><span data-stu-id="518a3-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Azure 函數徽標](./media/azure-functions-logo.png)

<span data-ttu-id="518a3-108">Azure 函數框架有兩個版本。</span><span class="sxs-lookup"><span data-stu-id="518a3-108">There are two versions of the Azure Functions framework.</span></span> <span data-ttu-id="518a3-109">舊版本支援完整的 .NET 框架，新的運行時支援跨平臺 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="518a3-109">The legacy version supports the full .NET Framework and the new runtime supports cross-platform .NET Core applications.</span></span> <span data-ttu-id="518a3-110">除了 C# 之外，還支援其他語言，如 JavaScript、F# 和 JAVA。</span><span class="sxs-lookup"><span data-stu-id="518a3-110">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="518a3-111">在門戶中創建的函數提供了豐富的腳本語法。</span><span class="sxs-lookup"><span data-stu-id="518a3-111">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="518a3-112">作為獨立專案創建的函數可以使用完整的平臺支援和功能進行部署。</span><span class="sxs-lookup"><span data-stu-id="518a3-112">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="518a3-113">有關詳細資訊，請參閱[Azure 函數文檔](https://docs.microsoft.com/azure/azure-functions)。</span><span class="sxs-lookup"><span data-stu-id="518a3-113">For more information, see [Azure Functions documentation](https://docs.microsoft.com/azure/azure-functions).</span></span>

## <a name="functions-v1-vs-v2"></a><span data-ttu-id="518a3-114">功能 v1 vs. v2</span><span class="sxs-lookup"><span data-stu-id="518a3-114">Functions v1 vs. v2</span></span>

<span data-ttu-id="518a3-115">Azure 函數運行時有兩個版本：1.x 和 2.x。</span><span class="sxs-lookup"><span data-stu-id="518a3-115">There are two versions of the Azure Functions runtime: 1.x and 2.x.</span></span> <span data-ttu-id="518a3-116">版本 1.x 通常可用 （GA）。</span><span class="sxs-lookup"><span data-stu-id="518a3-116">Version 1.x is generally available (GA).</span></span> <span data-ttu-id="518a3-117">它支援來自門戶或 Windows 電腦的 .NET 開發，並使用 .NET 框架。</span><span class="sxs-lookup"><span data-stu-id="518a3-117">It supports .NET development from the portal or Windows machines and uses the .NET Framework.</span></span> <span data-ttu-id="518a3-118">1.x 支援 C#、JavaScript 和 F#，支援 Python、PHP、TypeScript、批次處理、Bash 和 PowerShell 的實驗支援。</span><span class="sxs-lookup"><span data-stu-id="518a3-118">1.x supports C#, JavaScript, and F#, with experimental support for Python, PHP, TypeScript, Batch, Bash, and PowerShell.</span></span>

<span data-ttu-id="518a3-119">[版本 2.x 現在也通常可用](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/)。</span><span class="sxs-lookup"><span data-stu-id="518a3-119">[Version 2.x is also generally available now](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span></span> <span data-ttu-id="518a3-120">它利用 .NET Core 並支援 Windows、macOS 和 Linux 電腦上跨平臺開發。</span><span class="sxs-lookup"><span data-stu-id="518a3-120">It leverages .NET Core and supports cross-platform development on Windows, macOS, and Linux machines.</span></span> <span data-ttu-id="518a3-121">2.x 增加了對 JAVA 的一流支援，但尚未直接支援任何實驗語言。</span><span class="sxs-lookup"><span data-stu-id="518a3-121">2.x adds first-class support for Java but doesn't yet directly support any of the experimental languages.</span></span> <span data-ttu-id="518a3-122">版本 2.x 使用新的綁定擴充性模型，支援平臺的協力廠商擴展、綁定的獨立版本控制以及更簡化的執行環境。</span><span class="sxs-lookup"><span data-stu-id="518a3-122">Version 2.x uses a new binding extensibility model that enables third-party extensions to the platform, independent versioning of bindings, and a more streamlined execution environment.</span></span>

> <span data-ttu-id="518a3-123">**1.x 中存在[具有綁定重定向支援的](https://github.com/Azure/azure-functions-host/issues/992)已知問題。**</span><span class="sxs-lookup"><span data-stu-id="518a3-123">**There is a known issue in 1.x with [binding redirect support](https://github.com/Azure/azure-functions-host/issues/992).**</span></span> <span data-ttu-id="518a3-124">此問題特定于 .NET 開發。</span><span class="sxs-lookup"><span data-stu-id="518a3-124">The issue is specific to .NET development.</span></span> <span data-ttu-id="518a3-125">對庫的依賴項與運行時中包含的庫不同的專案將受到影響。</span><span class="sxs-lookup"><span data-stu-id="518a3-125">Projects with dependencies on libraries that are a different version from the libraries included in the runtime are impacted.</span></span> <span data-ttu-id="518a3-126">職能小組已承諾在問題上取得具體進展。</span><span class="sxs-lookup"><span data-stu-id="518a3-126">The functions team has committed to making concrete progress on the problem.</span></span> <span data-ttu-id="518a3-127">團隊將在 2.x 中處理綁定重定向，然後再進入常規可用性。</span><span class="sxs-lookup"><span data-stu-id="518a3-127">The team will address binding redirects in 2.x before it goes into general availability.</span></span> <span data-ttu-id="518a3-128">此處提供了包含建議的修補程式和解決方法的官方團隊聲明[：Azure 函數中的程式集解析](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions)。</span><span class="sxs-lookup"><span data-stu-id="518a3-128">The official team statement with suggested fixes and workarounds is available here: [Assembly resolution in Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span></span>

<span data-ttu-id="518a3-129">有關詳細資訊，請參閱比較[1.x 和 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions)。</span><span class="sxs-lookup"><span data-stu-id="518a3-129">For more information, see [Compare 1.x and 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="518a3-130">程式設計語言支援</span><span class="sxs-lookup"><span data-stu-id="518a3-130">Programming language support</span></span>

<span data-ttu-id="518a3-131">以下語言在通用 （GA）、預覽版或實驗版中支援。</span><span class="sxs-lookup"><span data-stu-id="518a3-131">The following languages are supported either in general availability (GA), preview, or experimental.</span></span>

|<span data-ttu-id="518a3-132">Language</span><span class="sxs-lookup"><span data-stu-id="518a3-132">Language</span></span>      |<span data-ttu-id="518a3-133">1.x</span><span class="sxs-lookup"><span data-stu-id="518a3-133">1.x</span></span>         |<span data-ttu-id="518a3-134">2.x</span><span class="sxs-lookup"><span data-stu-id="518a3-134">2.x</span></span>      |
|--------------|------------|---------|
|<span data-ttu-id="518a3-135">**C#**</span><span class="sxs-lookup"><span data-stu-id="518a3-135">**C#**</span></span>        |<span data-ttu-id="518a3-136">GA</span><span class="sxs-lookup"><span data-stu-id="518a3-136">GA</span></span>          |<span data-ttu-id="518a3-137">預覽</span><span class="sxs-lookup"><span data-stu-id="518a3-137">Preview</span></span>  |
|<span data-ttu-id="518a3-138">**JAVAscript**</span><span class="sxs-lookup"><span data-stu-id="518a3-138">**JavaScript**</span></span>|<span data-ttu-id="518a3-139">GA</span><span class="sxs-lookup"><span data-stu-id="518a3-139">GA</span></span>          |<span data-ttu-id="518a3-140">預覽</span><span class="sxs-lookup"><span data-stu-id="518a3-140">Preview</span></span>  |
|<span data-ttu-id="518a3-141">**F#**</span><span class="sxs-lookup"><span data-stu-id="518a3-141">**F#**</span></span>        |<span data-ttu-id="518a3-142">GA</span><span class="sxs-lookup"><span data-stu-id="518a3-142">GA</span></span>          |         |
|<span data-ttu-id="518a3-143">**JAVA**</span><span class="sxs-lookup"><span data-stu-id="518a3-143">**Java**</span></span>      |            |<span data-ttu-id="518a3-144">預覽</span><span class="sxs-lookup"><span data-stu-id="518a3-144">Preview</span></span>  |
|<span data-ttu-id="518a3-145">**Python**</span><span class="sxs-lookup"><span data-stu-id="518a3-145">**Python**</span></span>    |<span data-ttu-id="518a3-146">Experimental</span><span class="sxs-lookup"><span data-stu-id="518a3-146">Experimental</span></span>|         |
|<span data-ttu-id="518a3-147">**Php**</span><span class="sxs-lookup"><span data-stu-id="518a3-147">**PHP**</span></span>       |<span data-ttu-id="518a3-148">Experimental</span><span class="sxs-lookup"><span data-stu-id="518a3-148">Experimental</span></span>|         |
|<span data-ttu-id="518a3-149">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="518a3-149">**TypeScript**</span></span>|<span data-ttu-id="518a3-150">Experimental</span><span class="sxs-lookup"><span data-stu-id="518a3-150">Experimental</span></span>|         |
|<span data-ttu-id="518a3-151">**批**</span><span class="sxs-lookup"><span data-stu-id="518a3-151">**Batch**</span></span>     |<span data-ttu-id="518a3-152">Experimental</span><span class="sxs-lookup"><span data-stu-id="518a3-152">Experimental</span></span>|         |
|<span data-ttu-id="518a3-153">**Bash**</span><span class="sxs-lookup"><span data-stu-id="518a3-153">**Bash**</span></span>      |<span data-ttu-id="518a3-154">Experimental</span><span class="sxs-lookup"><span data-stu-id="518a3-154">Experimental</span></span>|         |
|<span data-ttu-id="518a3-155">**電源外殼**</span><span class="sxs-lookup"><span data-stu-id="518a3-155">**PowerShell**</span></span>|<span data-ttu-id="518a3-156">Experimental</span><span class="sxs-lookup"><span data-stu-id="518a3-156">Experimental</span></span>|         |

<span data-ttu-id="518a3-157">有關詳細資訊，請參閱[支援的語言](https://docs.microsoft.com/azure/azure-functions/supported-languages)。</span><span class="sxs-lookup"><span data-stu-id="518a3-157">For more information, see [Supported languages](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="518a3-158">應用服務方案</span><span class="sxs-lookup"><span data-stu-id="518a3-158">App service plans</span></span>

<span data-ttu-id="518a3-159">函數由*應用服務方案*支援。</span><span class="sxs-lookup"><span data-stu-id="518a3-159">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="518a3-160">計畫定義函數應用使用的資源。</span><span class="sxs-lookup"><span data-stu-id="518a3-160">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="518a3-161">您可以將計畫分配給區域、確定將使用的虛擬機器的大小和數量，並選擇定價層。</span><span class="sxs-lookup"><span data-stu-id="518a3-161">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="518a3-162">對於真正的無伺服器方法，函數應用可以使用**消耗**計畫。</span><span class="sxs-lookup"><span data-stu-id="518a3-162">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="518a3-163">消耗計畫將根據負載自動縮放後端。</span><span class="sxs-lookup"><span data-stu-id="518a3-163">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="518a3-164">有關詳細資訊，請參閱[應用服務方案](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)。</span><span class="sxs-lookup"><span data-stu-id="518a3-164">For more information, see [App service plans](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="518a3-165">建立您的第一個函式</span><span class="sxs-lookup"><span data-stu-id="518a3-165">Create your first function</span></span>

<span data-ttu-id="518a3-166">有三種常見方法可以創建函數應用。</span><span class="sxs-lookup"><span data-stu-id="518a3-166">There are three common ways you can create function apps.</span></span>

- <span data-ttu-id="518a3-167">腳本在門戶中功能。</span><span class="sxs-lookup"><span data-stu-id="518a3-167">Script functions in the portal.</span></span>
- <span data-ttu-id="518a3-168">使用 Azure CLI 創建必要的資源。</span><span class="sxs-lookup"><span data-stu-id="518a3-168">Create the necessary resources using the Azure CLI.</span></span>
- <span data-ttu-id="518a3-169">使用您最喜愛的 IDE 在本地生成函數，並將它們發佈到 Azure。</span><span class="sxs-lookup"><span data-stu-id="518a3-169">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="518a3-170">有關在門戶中創建腳本化函數的詳細資訊，請參閱[在 Azure 門戶中創建第一個函數](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)。</span><span class="sxs-lookup"><span data-stu-id="518a3-170">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="518a3-171">要從 Azure CLI 生成，請參閱[使用 Azure CLI 創建第一個函數](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)。</span><span class="sxs-lookup"><span data-stu-id="518a3-171">To build from the Azure CLI, see [Create your first function using the Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="518a3-172">要從視覺化工作室創建函數，請參閱[使用 Visual Studio 創建第一個函數](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="518a3-172">To create a function from Visual Studio, see [Create your first function using Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="518a3-173">瞭解觸發器和綁定</span><span class="sxs-lookup"><span data-stu-id="518a3-173">Understand triggers and bindings</span></span>

<span data-ttu-id="518a3-174">函數由*觸發器*調用，並且可以有一個。</span><span class="sxs-lookup"><span data-stu-id="518a3-174">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="518a3-175">除了調用函數之外，某些觸發器還用作綁定。</span><span class="sxs-lookup"><span data-stu-id="518a3-175">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="518a3-176">除了觸發器之外，您還可以定義多個綁定。</span><span class="sxs-lookup"><span data-stu-id="518a3-176">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="518a3-177">*綁定*提供了將資料連線到代碼的聲明性方法。</span><span class="sxs-lookup"><span data-stu-id="518a3-177">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="518a3-178">它們可以傳入（輸入）或接收資料（輸出）。</span><span class="sxs-lookup"><span data-stu-id="518a3-178">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="518a3-179">觸發器和綁定使功能便於使用。</span><span class="sxs-lookup"><span data-stu-id="518a3-179">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="518a3-180">綁定消除了手動創建資料庫或檔案系統連接的開銷。</span><span class="sxs-lookup"><span data-stu-id="518a3-180">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="518a3-181">綁定所需的所有資訊都包含在腳本的特殊*函數.json*檔中，或者使用代碼中的屬性聲明。</span><span class="sxs-lookup"><span data-stu-id="518a3-181">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="518a3-182">一些常見的觸發器包括：</span><span class="sxs-lookup"><span data-stu-id="518a3-182">Some common triggers include:</span></span>

- <span data-ttu-id="518a3-183">Blob 存儲：在存儲中上載或更改檔或資料夾時調用函數。</span><span class="sxs-lookup"><span data-stu-id="518a3-183">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
- <span data-ttu-id="518a3-184">HTTP：像 REST API 一樣調用函數。</span><span class="sxs-lookup"><span data-stu-id="518a3-184">HTTP: invoke your function like a REST API.</span></span>
- <span data-ttu-id="518a3-185">佇列：當佇列中存在項時調用函數。</span><span class="sxs-lookup"><span data-stu-id="518a3-185">Queue: invoke your function when items exist in a queue.</span></span>
- <span data-ttu-id="518a3-186">計時器：在常規節奏上調用函數。</span><span class="sxs-lookup"><span data-stu-id="518a3-186">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="518a3-187">綁定的示例包括：</span><span class="sxs-lookup"><span data-stu-id="518a3-187">Examples of bindings include:</span></span>

- <span data-ttu-id="518a3-188">CosmosDB：輕鬆連接到資料庫以載入或保存檔。</span><span class="sxs-lookup"><span data-stu-id="518a3-188">CosmosDB: easily connect to the database to load or save files.</span></span>
- <span data-ttu-id="518a3-189">表存儲：使用函數應用中的金鑰/值存儲。</span><span class="sxs-lookup"><span data-stu-id="518a3-189">Table Storage: work with key/value storage from your function app.</span></span>
- <span data-ttu-id="518a3-190">佇列存儲：輕鬆從佇列中檢索項，或將新專案放在佇列中。</span><span class="sxs-lookup"><span data-stu-id="518a3-190">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="518a3-191">以下示例*函數.json*檔定義了觸發器和綁定：</span><span class="sxs-lookup"><span data-stu-id="518a3-191">The following example *functions.json* file defines a trigger and a binding:</span></span>

```json
{
  "bindings": [
    {
      "name": "myBlob",
      "type": "blobTrigger",
      "direction": "in",
      "path": "images/{name}",
      "connection": "AzureWebJobsStorage"
    },
    {
      "name": "$return",
      "type": "queue",
      "direction": "out",
      "queueName": "images",
      "connection": "AzureWebJobsStorage"
    }
  ],
  "disabled": false
}
```

<span data-ttu-id="518a3-192">在此示例中，函數由容器中 blob 存儲的`images`更改觸發。</span><span class="sxs-lookup"><span data-stu-id="518a3-192">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="518a3-193">檔的資訊傳入，因此觸發器也充當綁定。</span><span class="sxs-lookup"><span data-stu-id="518a3-193">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="518a3-194">存在另一個綁定，用於將資訊放到名為`images`的佇列中。</span><span class="sxs-lookup"><span data-stu-id="518a3-194">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="518a3-195">下面是函數的 C# 腳本：</span><span class="sxs-lookup"><span data-stu-id="518a3-195">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="518a3-196">該示例是一個簡單的函數，該函數獲取已修改或上載到 Blob 存儲的檔的名稱，並將其放在佇列中，以便以後處理。</span><span class="sxs-lookup"><span data-stu-id="518a3-196">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="518a3-197">有關觸發器和綁定的完整清單，請參閱[Azure 函數觸發器和綁定概念](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)。</span><span class="sxs-lookup"><span data-stu-id="518a3-197">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span></span>

## <a name="proxies"></a><span data-ttu-id="518a3-198">Proxy</span><span class="sxs-lookup"><span data-stu-id="518a3-198">Proxies</span></span>

<span data-ttu-id="518a3-199">代理為您的應用程式提供重定向功能。</span><span class="sxs-lookup"><span data-stu-id="518a3-199">Proxies provide redirect functionality for your application.</span></span> <span data-ttu-id="518a3-200">代理公開終結點並將該終結點映射到其他資源。</span><span class="sxs-lookup"><span data-stu-id="518a3-200">Proxies expose an endpoint and map that endpoint to another resource.</span></span> <span data-ttu-id="518a3-201">使用代理，您可以：</span><span class="sxs-lookup"><span data-stu-id="518a3-201">With proxies, you can:</span></span>

- <span data-ttu-id="518a3-202">將傳入請求重新路由到另一個終結點。</span><span class="sxs-lookup"><span data-stu-id="518a3-202">Reroute an incoming request to another endpoint.</span></span>
- <span data-ttu-id="518a3-203">在傳入請求傳遞之前對其進行修改。</span><span class="sxs-lookup"><span data-stu-id="518a3-203">Modify the incoming request before it's passed along.</span></span>
- <span data-ttu-id="518a3-204">修改或提供回應。</span><span class="sxs-lookup"><span data-stu-id="518a3-204">Modify or provide a response.</span></span>

<span data-ttu-id="518a3-205">代理用於以下方案：</span><span class="sxs-lookup"><span data-stu-id="518a3-205">Proxies are used for scenarios such as:</span></span>

- <span data-ttu-id="518a3-206">簡化、縮短或更改 URL。</span><span class="sxs-lookup"><span data-stu-id="518a3-206">Simplifying, shortening, or changing the URL.</span></span>
- <span data-ttu-id="518a3-207">為多個後端服務提供一致的 API 首碼。</span><span class="sxs-lookup"><span data-stu-id="518a3-207">Providing a consistent API prefix to multiple back-end services.</span></span>
- <span data-ttu-id="518a3-208">類比對正在開發的終結點的回應。</span><span class="sxs-lookup"><span data-stu-id="518a3-208">Mocking a response to an endpoint being developed.</span></span>
- <span data-ttu-id="518a3-209">向已知終結點提供靜態回應。</span><span class="sxs-lookup"><span data-stu-id="518a3-209">Providing a static response to a well-known endpoint.</span></span>
- <span data-ttu-id="518a3-210">在移動或遷移後端時保持 API 終結點的一致性。</span><span class="sxs-lookup"><span data-stu-id="518a3-210">Keeping an API endpoint consistent while the back end is moved or migrated.</span></span>

<span data-ttu-id="518a3-211">代理存儲為 JSON 定義。</span><span class="sxs-lookup"><span data-stu-id="518a3-211">Proxies are stored as JSON definitions.</span></span> <span data-ttu-id="518a3-212">範例如下：</span><span class="sxs-lookup"><span data-stu-id="518a3-212">Here is an example:</span></span>

```json
{
  "$schema": "http://json.schemastore.org/proxies",
  "proxies": {
    "Domain Redirect": {
      "matchCondition": {
        "route": "/{shortUrl}"
      },
      "backendUri": "http://%WEBSITE_HOSTNAME%/api/UrlRedirect/{shortUrl}"
    },
    "Root": {
      "matchCondition": {
        "route": "/"
      },
      "responseOverrides": {
        "response.statusCode": "301",
        "response.statusReason": "Moved Permanently",
        "response.headers.location": "https://docs.microsoft.com/"
      }
    }
  }
}
```

<span data-ttu-id="518a3-213">代理`Domain Redirect`採用縮短的路由並將其映射到較長的函數資源。</span><span class="sxs-lookup"><span data-stu-id="518a3-213">The `Domain Redirect` proxy takes a shortened route and maps it to the longer function resource.</span></span> <span data-ttu-id="518a3-214">轉換如下所示：</span><span class="sxs-lookup"><span data-stu-id="518a3-214">The transformation looks like:</span></span>

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

<span data-ttu-id="518a3-215">代理`Root`會獲取發送到根 URL （`https://--shorturl--/`） 的任何內容，並將其重定向到文檔網站。</span><span class="sxs-lookup"><span data-stu-id="518a3-215">The `Root` proxy takes anything sent to the root URL (`https://--shorturl--/`) and redirects it to the documentation site.</span></span>

<span data-ttu-id="518a3-216">使用代理的示例顯示在視頻[Azure 中：使用無伺服器 Azure 函數將應用帶到雲](https://channel9.msdn.com/events/Connect/2017/E102)中。</span><span class="sxs-lookup"><span data-stu-id="518a3-216">An example of using proxies is shown in the video [Azure: Bring your app to the cloud with serverless Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102).</span></span> <span data-ttu-id="518a3-217">即時，在本地 SQL 伺服器上運行ASP.NET核心應用程式將遷移到 Azure 雲。</span><span class="sxs-lookup"><span data-stu-id="518a3-217">In real time, an ASP.NET Core application running on local SQL Server is migrated to the Azure Cloud.</span></span> <span data-ttu-id="518a3-218">代理用於説明重構傳統的 Web API 專案以使用函數。</span><span class="sxs-lookup"><span data-stu-id="518a3-218">Proxies are used to help refactor a traditional Web API project to use functions.</span></span>

<span data-ttu-id="518a3-219">有關代理的詳細資訊，請參閱使用 Azure[函數代理](https://docs.microsoft.com/azure/azure-functions/functions-proxies)。</span><span class="sxs-lookup"><span data-stu-id="518a3-219">For more information about Proxies, see [Work with Azure Functions Proxies](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="518a3-220">[上一個](azure-serverless-platform.md)
>[下一個](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="518a3-220">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
