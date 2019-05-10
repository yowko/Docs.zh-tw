---
title: Azure Functions-無伺服器應用程式
description: Azure functions 提供無伺服器的功能 （C#、 JavaScript、 Java） 的多種語言，並立即提供事件驅動的平台擴充程式碼。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 4febcc01eebf3efce3fc1eb42e19c2ec6c0baa52
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64754228"
---
# <a name="azure-functions"></a><span data-ttu-id="e01c1-103">Azure Functions</span><span class="sxs-lookup"><span data-stu-id="e01c1-103">Azure Functions</span></span>

<span data-ttu-id="e01c1-104">Azure functions 提供無伺服器計算體驗。</span><span class="sxs-lookup"><span data-stu-id="e01c1-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="e01c1-105">函式會叫用*觸發程序*（例如存取 HTTP 端點或計時器），並執行的程式碼或商務邏輯區塊。</span><span class="sxs-lookup"><span data-stu-id="e01c1-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="e01c1-106">函式也支援特製化*繫結*，連接到儲存體和佇列等資源。</span><span class="sxs-lookup"><span data-stu-id="e01c1-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Azure functions 標誌](./media/azure-functions-logo.png)

<span data-ttu-id="e01c1-108">有兩個版本的 Azure Functions 架構。</span><span class="sxs-lookup"><span data-stu-id="e01c1-108">There are two versions of the Azure Functions framework.</span></span> <span data-ttu-id="e01c1-109">舊版的版本可支援完整的.NET Framework，新的執行階段支援跨平台.NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e01c1-109">The legacy version supports the full .NET Framework and the new runtime supports cross-platform .NET Core applications.</span></span> <span data-ttu-id="e01c1-110">以外的其他語言C#JavaScript 等F#，並支援 Java。</span><span class="sxs-lookup"><span data-stu-id="e01c1-110">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="e01c1-111">在入口網站中建立的函式提供豐富的指令碼語法。</span><span class="sxs-lookup"><span data-stu-id="e01c1-111">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="e01c1-112">做為獨立專案所建立的函式可以部署與完整的平台支援和功能。</span><span class="sxs-lookup"><span data-stu-id="e01c1-112">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="e01c1-113">如需詳細資訊，請參閱 < [Azure Functions 文件](https://docs.microsoft.com/azure/azure-functions)。</span><span class="sxs-lookup"><span data-stu-id="e01c1-113">For more information, see [Azure Functions documentation](https://docs.microsoft.com/azure/azure-functions).</span></span>

## <a name="functions-v1-vs-v2"></a><span data-ttu-id="e01c1-114">函式 v1 與 v2</span><span class="sxs-lookup"><span data-stu-id="e01c1-114">Functions v1 vs. v2</span></span>

<span data-ttu-id="e01c1-115">有兩個 Azure Functions 執行階段版本：1.x 和 2.x。</span><span class="sxs-lookup"><span data-stu-id="e01c1-115">There are two versions of the Azure Functions runtime: 1.x and 2.x.</span></span> <span data-ttu-id="e01c1-116">版本 1.x 已正式推出 (GA)。</span><span class="sxs-lookup"><span data-stu-id="e01c1-116">Version 1.x is generally available (GA).</span></span> <span data-ttu-id="e01c1-117">它支援從入口網站或 Windows 電腦的.NET 開發，並使用.NET Framework。</span><span class="sxs-lookup"><span data-stu-id="e01c1-117">It supports .NET development from the portal or Windows machines and uses the .NET Framework.</span></span> <span data-ttu-id="e01c1-118">1.x 支援C#，JavaScript，和F#，使用 Python、 PHP、 TypeScript、 Batch、 Bash、 和 PowerShell 的實驗性支援。</span><span class="sxs-lookup"><span data-stu-id="e01c1-118">1.x supports C#, JavaScript, and F#, with experimental support for Python, PHP, TypeScript, Batch, Bash, and PowerShell.</span></span>

<span data-ttu-id="e01c1-119">[版本 2.x 現也正式](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/)。</span><span class="sxs-lookup"><span data-stu-id="e01c1-119">[Version 2.x is also generally available now](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span></span> <span data-ttu-id="e01c1-120">它會利用.NET Core，而且支援在 Windows、 macOS 和 Linux 機器上跨平台開發。</span><span class="sxs-lookup"><span data-stu-id="e01c1-120">It leverages .NET Core and supports cross-platform development on Windows, macOS, and Linux machines.</span></span> <span data-ttu-id="e01c1-121">2.x 新增適用於 Java 的頂級支援，但尚不直接支援的任何實驗性語言。</span><span class="sxs-lookup"><span data-stu-id="e01c1-121">2.x adds first-class support for Java but doesn't yet directly support any of the experimental languages.</span></span> <span data-ttu-id="e01c1-122">版本 2.x 使用新的繫結擴充性模型，可讓協力廠商擴充功能的平台獨立的版本設定的繫結，並更精簡的執行環境。</span><span class="sxs-lookup"><span data-stu-id="e01c1-122">Version 2.x uses a new binding extensibility model that enables third-party extensions to the platform, independent versioning of bindings, and a more streamlined execution environment.</span></span>

> <span data-ttu-id="e01c1-123">**與 1.x 中沒有已知的問題[繫結重新導向支援](https://github.com/Azure/azure-functions-host/issues/992)。**</span><span class="sxs-lookup"><span data-stu-id="e01c1-123">**There is a known issue in 1.x with [binding redirect support](https://github.com/Azure/azure-functions-host/issues/992).**</span></span> <span data-ttu-id="e01c1-124">問題在於專用的.NET 開發。</span><span class="sxs-lookup"><span data-stu-id="e01c1-124">The issue is specific to .NET development.</span></span> <span data-ttu-id="e01c1-125">受影響的相依性會包含在執行階段程式庫中的不同版本的程式庫的專案。</span><span class="sxs-lookup"><span data-stu-id="e01c1-125">Projects with dependencies on libraries that are a different version from the libraries included in the runtime are impacted.</span></span> <span data-ttu-id="e01c1-126">Functions 小組已致力於問題的具體進度。</span><span class="sxs-lookup"><span data-stu-id="e01c1-126">The functions team has committed to making concrete progress on the problem.</span></span> <span data-ttu-id="e01c1-127">小組會在它進入正式運作之前解決在 2.x 中的繫結重新導向。</span><span class="sxs-lookup"><span data-stu-id="e01c1-127">The team will address binding redirects in 2.x before it goes into general availability.</span></span> <span data-ttu-id="e01c1-128">這裡有建議的修正和因應措施的官方團隊陳述式：[在 Azure Functions 中的組件解析](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions)。</span><span class="sxs-lookup"><span data-stu-id="e01c1-128">The official team statement with suggested fixes and workarounds is available here: [Assembly resolution in Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span></span>

<span data-ttu-id="e01c1-129">如需詳細資訊，請參閱 <<c0> [ 比較 1.x 和 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions)。</span><span class="sxs-lookup"><span data-stu-id="e01c1-129">For more information, see [Compare 1.x and 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="e01c1-130">程式設計語言支援</span><span class="sxs-lookup"><span data-stu-id="e01c1-130">Programming language support</span></span>

<span data-ttu-id="e01c1-131">支援下列語言版本可能是一般情況下運作 (GA)，預覽，或實驗性。</span><span class="sxs-lookup"><span data-stu-id="e01c1-131">The following languages are supported either in general availability (GA), preview, or experimental.</span></span>

|<span data-ttu-id="e01c1-132">語言</span><span class="sxs-lookup"><span data-stu-id="e01c1-132">Language</span></span>      |<span data-ttu-id="e01c1-133">1.x</span><span class="sxs-lookup"><span data-stu-id="e01c1-133">1.x</span></span>         |<span data-ttu-id="e01c1-134">2.x</span><span class="sxs-lookup"><span data-stu-id="e01c1-134">2.x</span></span>      |
|--------------|------------|---------|
|<span data-ttu-id="e01c1-135">**C#**</span><span class="sxs-lookup"><span data-stu-id="e01c1-135">**C#**</span></span>        |<span data-ttu-id="e01c1-136">GA</span><span class="sxs-lookup"><span data-stu-id="e01c1-136">GA</span></span>          |<span data-ttu-id="e01c1-137">預覽</span><span class="sxs-lookup"><span data-stu-id="e01c1-137">Preview</span></span>  |
|<span data-ttu-id="e01c1-138">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="e01c1-138">**JavaScript**</span></span>|<span data-ttu-id="e01c1-139">GA</span><span class="sxs-lookup"><span data-stu-id="e01c1-139">GA</span></span>          |<span data-ttu-id="e01c1-140">預覽</span><span class="sxs-lookup"><span data-stu-id="e01c1-140">Preview</span></span>  |
|<span data-ttu-id="e01c1-141">**F#**</span><span class="sxs-lookup"><span data-stu-id="e01c1-141">**F#**</span></span>        |<span data-ttu-id="e01c1-142">GA</span><span class="sxs-lookup"><span data-stu-id="e01c1-142">GA</span></span>          |         |
|<span data-ttu-id="e01c1-143">**Java**</span><span class="sxs-lookup"><span data-stu-id="e01c1-143">**Java**</span></span>      |            |<span data-ttu-id="e01c1-144">預覽</span><span class="sxs-lookup"><span data-stu-id="e01c1-144">Preview</span></span>  |
|<span data-ttu-id="e01c1-145">**Python**</span><span class="sxs-lookup"><span data-stu-id="e01c1-145">**Python**</span></span>    |<span data-ttu-id="e01c1-146">實驗</span><span class="sxs-lookup"><span data-stu-id="e01c1-146">Experimental</span></span>|         |
|<span data-ttu-id="e01c1-147">**PHP**</span><span class="sxs-lookup"><span data-stu-id="e01c1-147">**PHP**</span></span>       |<span data-ttu-id="e01c1-148">實驗</span><span class="sxs-lookup"><span data-stu-id="e01c1-148">Experimental</span></span>|         |
|<span data-ttu-id="e01c1-149">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="e01c1-149">**TypeScript**</span></span>|<span data-ttu-id="e01c1-150">實驗</span><span class="sxs-lookup"><span data-stu-id="e01c1-150">Experimental</span></span>|         |
|<span data-ttu-id="e01c1-151">**Batch**</span><span class="sxs-lookup"><span data-stu-id="e01c1-151">**Batch**</span></span>     |<span data-ttu-id="e01c1-152">實驗</span><span class="sxs-lookup"><span data-stu-id="e01c1-152">Experimental</span></span>|         |
|<span data-ttu-id="e01c1-153">**Bash**</span><span class="sxs-lookup"><span data-stu-id="e01c1-153">**Bash**</span></span>      |<span data-ttu-id="e01c1-154">實驗</span><span class="sxs-lookup"><span data-stu-id="e01c1-154">Experimental</span></span>|         |
|<span data-ttu-id="e01c1-155">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="e01c1-155">**PowerShell**</span></span>|<span data-ttu-id="e01c1-156">實驗</span><span class="sxs-lookup"><span data-stu-id="e01c1-156">Experimental</span></span>|         |

<span data-ttu-id="e01c1-157">如需詳細資訊，請參閱 <<c0> [ 支援的語言](https://docs.microsoft.com/azure/azure-functions/supported-languages)。</span><span class="sxs-lookup"><span data-stu-id="e01c1-157">For more information, see [Supported languages](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="e01c1-158">App service 方案</span><span class="sxs-lookup"><span data-stu-id="e01c1-158">App service plans</span></span>

<span data-ttu-id="e01c1-159">函式都會受到*app service 方案*。</span><span class="sxs-lookup"><span data-stu-id="e01c1-159">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="e01c1-160">方案會定義函式應用程式所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="e01c1-160">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="e01c1-161">您可以指派至區域的計劃，決定大小和數目，將會使用，並選擇定價層的虛擬機器。</span><span class="sxs-lookup"><span data-stu-id="e01c1-161">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="e01c1-162">函式應用程式可能使用真正的無伺服器方法，如**耗用量**計劃。</span><span class="sxs-lookup"><span data-stu-id="e01c1-162">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="e01c1-163">取用方案會調整後端會自動根據負載。</span><span class="sxs-lookup"><span data-stu-id="e01c1-163">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="e01c1-164">如需詳細資訊，請參閱 < [App service 方案](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)。</span><span class="sxs-lookup"><span data-stu-id="e01c1-164">For more information, see [App service plans](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="e01c1-165">建立您的第一個函式</span><span class="sxs-lookup"><span data-stu-id="e01c1-165">Create your first function</span></span>

<span data-ttu-id="e01c1-166">有三種常見的方式，您可以建立函式應用程式。</span><span class="sxs-lookup"><span data-stu-id="e01c1-166">There are three common ways you can create function apps.</span></span>

* <span data-ttu-id="e01c1-167">在入口網站中的指令碼函式。</span><span class="sxs-lookup"><span data-stu-id="e01c1-167">Script functions in the portal.</span></span>
* <span data-ttu-id="e01c1-168">建立所需的資源使用 Azure 命令列介面 (CLI)。</span><span class="sxs-lookup"><span data-stu-id="e01c1-168">Create the necessary resources using the Azure Command Line Interface (CLI).</span></span>
* <span data-ttu-id="e01c1-169">建立使用您最喜愛的 IDE，在本機的函式，並將其發行至 Azure。</span><span class="sxs-lookup"><span data-stu-id="e01c1-169">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="e01c1-170">如需有關如何在入口網站中建立的指令碼式的函式的詳細資訊，請參閱[在 Azure 入口網站中建立您的第一個函式](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)。</span><span class="sxs-lookup"><span data-stu-id="e01c1-170">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="e01c1-171">若要建立從 Azure CLI，請參閱[建立第一個函式中，使用 Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)。</span><span class="sxs-lookup"><span data-stu-id="e01c1-171">To build from the Azure CLI, see [Create your first function using the Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="e01c1-172">若要從 Visual Studio 中建立函式，請參閱[建立第一個函式使用 Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="e01c1-172">To create a function from Visual Studio, see [Create your first function using Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="e01c1-173">了解觸發程序和繫結</span><span class="sxs-lookup"><span data-stu-id="e01c1-173">Understand triggers and bindings</span></span>

<span data-ttu-id="e01c1-174">函式會叫用*觸發程序*，而且可以有一個。</span><span class="sxs-lookup"><span data-stu-id="e01c1-174">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="e01c1-175">除了叫用函數，特定觸發程序也做為繫結。</span><span class="sxs-lookup"><span data-stu-id="e01c1-175">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="e01c1-176">您也可以定義多個繫結，除了觸發程序。</span><span class="sxs-lookup"><span data-stu-id="e01c1-176">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="e01c1-177">*繫結*以宣告方式將資料連接至您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e01c1-177">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="e01c1-178">它們可以傳入 （輸入），或接收資料 （輸出）。</span><span class="sxs-lookup"><span data-stu-id="e01c1-178">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="e01c1-179">觸發程序和繫結都函式讓您輕鬆地使用。</span><span class="sxs-lookup"><span data-stu-id="e01c1-179">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="e01c1-180">繫結移除以手動方式建立資料庫或檔案系統連線的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="e01c1-180">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="e01c1-181">所有的繫結所需的資訊都包含在特殊*functions.json*指令碼檔案，或使用程式碼中的屬性宣告。</span><span class="sxs-lookup"><span data-stu-id="e01c1-181">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="e01c1-182">某些常見的觸發程序包括：</span><span class="sxs-lookup"><span data-stu-id="e01c1-182">Some common triggers include:</span></span>

* <span data-ttu-id="e01c1-183">上傳或儲存體中變更檔案或資料夾時，blob 儲存體： 叫用您的函式。</span><span class="sxs-lookup"><span data-stu-id="e01c1-183">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
* <span data-ttu-id="e01c1-184">HTTP： 叫用您的函式，例如 REST API。</span><span class="sxs-lookup"><span data-stu-id="e01c1-184">HTTP: invoke your function like a REST API.</span></span>
* <span data-ttu-id="e01c1-185">當佇列中的項目存在，佇列： 叫用您的函式。</span><span class="sxs-lookup"><span data-stu-id="e01c1-185">Queue: invoke your function when items exist in a queue.</span></span>
* <span data-ttu-id="e01c1-186">計時器： 叫用您的函式，在一般的頻率。</span><span class="sxs-lookup"><span data-stu-id="e01c1-186">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="e01c1-187">繫結的範例包括：</span><span class="sxs-lookup"><span data-stu-id="e01c1-187">Examples of bindings include:</span></span>

* <span data-ttu-id="e01c1-188">CosmosDB： 輕鬆地連接至資料庫以載入或儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="e01c1-188">CosmosDB: easily connect to the database to load or save files.</span></span>
* <span data-ttu-id="e01c1-189">資料表儲存體： 使用您的函式應用程式中的索引鍵/值儲存體。</span><span class="sxs-lookup"><span data-stu-id="e01c1-189">Table Storage: work with key/value storage from your function app.</span></span>
* <span data-ttu-id="e01c1-190">佇列儲存體： 輕鬆地從佇列擷取項目，或將新的項目放在佇列上。</span><span class="sxs-lookup"><span data-stu-id="e01c1-190">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="e01c1-191">下例*functions.json*檔案會定義觸發程序和繫結：</span><span class="sxs-lookup"><span data-stu-id="e01c1-191">The following example *functions.json* file defines a trigger and a binding:</span></span>

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

<span data-ttu-id="e01c1-192">在此範例中，變更至 blob 儲存體所觸發的函式`images`容器。</span><span class="sxs-lookup"><span data-stu-id="e01c1-192">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="e01c1-193">檔案的資訊會傳入，因此觸發程序也可以當做繫結。</span><span class="sxs-lookup"><span data-stu-id="e01c1-193">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="e01c1-194">另一個繫結存在，將資訊放入佇列，名為`images`。</span><span class="sxs-lookup"><span data-stu-id="e01c1-194">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="e01c1-195">以下是 C# 指令碼函式：</span><span class="sxs-lookup"><span data-stu-id="e01c1-195">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="e01c1-196">範例是檔案的簡單的函式可接受名稱已修改或上傳至 blob 儲存體，且將它放入佇列，以供稍後處理。</span><span class="sxs-lookup"><span data-stu-id="e01c1-196">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="e01c1-197">如需觸發程序和繫結的完整清單，請參閱 < [Azure Functions 觸發程序和繫結概念](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)。</span><span class="sxs-lookup"><span data-stu-id="e01c1-197">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span></span>

## <a name="proxies"></a><span data-ttu-id="e01c1-198">Proxy</span><span class="sxs-lookup"><span data-stu-id="e01c1-198">Proxies</span></span>

<span data-ttu-id="e01c1-199">Proxy 提供您的應用程式重新導向功能。</span><span class="sxs-lookup"><span data-stu-id="e01c1-199">Proxies provide redirect functionality for your application.</span></span> <span data-ttu-id="e01c1-200">Proxy 公開的端點，並將該端點對應至另一個資源。</span><span class="sxs-lookup"><span data-stu-id="e01c1-200">Proxies expose an endpoint and map that endpoint to another resource.</span></span> <span data-ttu-id="e01c1-201">使用 proxy，您可以：</span><span class="sxs-lookup"><span data-stu-id="e01c1-201">With proxies, you can:</span></span>

* <span data-ttu-id="e01c1-202">重新路由傳送至另一個端點的連入要求。</span><span class="sxs-lookup"><span data-stu-id="e01c1-202">Reroute an incoming request to another endpoint.</span></span>
* <span data-ttu-id="e01c1-203">它會傳遞之前，請修改連入要求。</span><span class="sxs-lookup"><span data-stu-id="e01c1-203">Modify the incoming request before it's passed along.</span></span>
* <span data-ttu-id="e01c1-204">修改或提供回應。</span><span class="sxs-lookup"><span data-stu-id="e01c1-204">Modify or provide a response.</span></span>

<span data-ttu-id="e01c1-205">是這類情況下使用 proxy:</span><span class="sxs-lookup"><span data-stu-id="e01c1-205">Proxies are used for scenarios such as:</span></span>

* <span data-ttu-id="e01c1-206">簡化、 縮短兩次，或變更 URL。</span><span class="sxs-lookup"><span data-stu-id="e01c1-206">Simplifying, shortening, or changing the URL.</span></span>
* <span data-ttu-id="e01c1-207">提供一致的 API 前置詞，多個後端服務。</span><span class="sxs-lookup"><span data-stu-id="e01c1-207">Providing a consistent API prefix to multiple back-end services.</span></span>
* <span data-ttu-id="e01c1-208">模擬正在開發的端點的回應。</span><span class="sxs-lookup"><span data-stu-id="e01c1-208">Mocking a response to an endpoint being developed.</span></span>
* <span data-ttu-id="e01c1-209">提供已知端點的靜態回應。</span><span class="sxs-lookup"><span data-stu-id="e01c1-209">Providing a static response to a well-known endpoint.</span></span>
* <span data-ttu-id="e01c1-210">後端正在移動或移轉時，讓 API 端點為一致的。</span><span class="sxs-lookup"><span data-stu-id="e01c1-210">Keeping an API endpoint consistent while the back end is moved or migrated.</span></span>

<span data-ttu-id="e01c1-211">Proxy 會儲存為 JSON 定義中。</span><span class="sxs-lookup"><span data-stu-id="e01c1-211">Proxies are stored as JSON definitions.</span></span> <span data-ttu-id="e01c1-212">請看以下範例：</span><span class="sxs-lookup"><span data-stu-id="e01c1-212">Here is an example:</span></span>

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

<span data-ttu-id="e01c1-213">`Domain Redirect` Proxy 會縮短的路由，並將其對應至較長的函式資源。</span><span class="sxs-lookup"><span data-stu-id="e01c1-213">The `Domain Redirect` proxy takes a shortened route and maps it to the longer function resource.</span></span> <span data-ttu-id="e01c1-214">轉換看起來像：</span><span class="sxs-lookup"><span data-stu-id="e01c1-214">The transformation looks like:</span></span>

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

<span data-ttu-id="e01c1-215">`Root` Proxy 會傳送至根 URL 的任何項目 (`https://--shorturl--/`) 並將它重新導向的文件網站。</span><span class="sxs-lookup"><span data-stu-id="e01c1-215">The `Root` proxy takes anything sent to the root URL (`https://--shorturl--/`) and redirects it to the documentation site.</span></span>

<span data-ttu-id="e01c1-216">使用 proxy 的範例所示影片[Azure:將應用程式帶至雲端，無伺服器 Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102)。</span><span class="sxs-lookup"><span data-stu-id="e01c1-216">An example of using proxies is shown in the video [Azure: Bring your app to the cloud with serverless Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102).</span></span> <span data-ttu-id="e01c1-217">即時本機 SQL Server 上執行的 ASP.NET Core 應用程式移轉到 Azure 雲端。</span><span class="sxs-lookup"><span data-stu-id="e01c1-217">In real time, an ASP.NET Core application running on local SQL Server is migrated to the Azure Cloud.</span></span> <span data-ttu-id="e01c1-218">為了重構傳統的 Web API 專案，使用函式會使用 proxy。</span><span class="sxs-lookup"><span data-stu-id="e01c1-218">Proxies are used to help refactor a traditional Web API project to use functions.</span></span>

<span data-ttu-id="e01c1-219">如需 Proxy 的詳細資訊，請參閱[使用 Azure Functions Proxy](https://docs.microsoft.com/azure/azure-functions/functions-proxies)。</span><span class="sxs-lookup"><span data-stu-id="e01c1-219">For more information about Proxies, see [Work with Azure Functions Proxies](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e01c1-220">[上一頁](azure-serverless-platform.md)
>[下一頁](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="e01c1-220">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
