---
title: Azure Functions-無伺服器應用程式
description: Azure 函式提供跨多種語言 (C#、JavaScript、JAVA) 和平臺的無伺服器功能, 以提供事件驅動的立即調整程式碼。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 06/26/2018
ms.openlocfilehash: 4febcc01eebf3efce3fc1eb42e19c2ec6c0baa52
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "69577601"
---
# <a name="azure-functions"></a><span data-ttu-id="9611c-103">Azure Functions</span><span class="sxs-lookup"><span data-stu-id="9611c-103">Azure Functions</span></span>

<span data-ttu-id="9611c-104">Azure 函式提供無伺服器計算體驗。</span><span class="sxs-lookup"><span data-stu-id="9611c-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="9611c-105">函式是由*觸發*程式 (例如存取 HTTP 端點或計時器) 所叫用, 並執行程式碼區塊或商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="9611c-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="9611c-106">函式也支援特定的系結, 這些系結會連接到儲存體和佇列之類的資源。</span><span class="sxs-lookup"><span data-stu-id="9611c-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Azure 函數標誌](./media/azure-functions-logo.png)

<span data-ttu-id="9611c-108">Azure Functions framework 有兩個版本。</span><span class="sxs-lookup"><span data-stu-id="9611c-108">There are two versions of the Azure Functions framework.</span></span> <span data-ttu-id="9611c-109">舊版支援完整的 .NET Framework, 而新的執行時間支援跨平臺 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9611c-109">The legacy version supports the full .NET Framework and the new runtime supports cross-platform .NET Core applications.</span></span> <span data-ttu-id="9611c-110">除了 JavaScript、 C# F#和 JAVA 以外, 還支援其他語言。</span><span class="sxs-lookup"><span data-stu-id="9611c-110">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="9611c-111">在入口網站中建立的函數會提供豐富的腳本語法。</span><span class="sxs-lookup"><span data-stu-id="9611c-111">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="9611c-112">建立為獨立專案的函式可以使用完整的平臺支援和功能進行部署。</span><span class="sxs-lookup"><span data-stu-id="9611c-112">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="9611c-113">如需詳細資訊, 請參閱[Azure Functions 檔](https://docs.microsoft.com/azure/azure-functions)。</span><span class="sxs-lookup"><span data-stu-id="9611c-113">For more information, see [Azure Functions documentation](https://docs.microsoft.com/azure/azure-functions).</span></span>

## <a name="functions-v1-vs-v2"></a><span data-ttu-id="9611c-114">函數 v1 與 v2 的比較</span><span class="sxs-lookup"><span data-stu-id="9611c-114">Functions v1 vs. v2</span></span>

<span data-ttu-id="9611c-115">Azure Functions 執行時間有兩個版本:1.x 和2.x。</span><span class="sxs-lookup"><span data-stu-id="9611c-115">There are two versions of the Azure Functions runtime: 1.x and 2.x.</span></span> <span data-ttu-id="9611c-116">1\.x 版正式推出 (GA)。</span><span class="sxs-lookup"><span data-stu-id="9611c-116">Version 1.x is generally available (GA).</span></span> <span data-ttu-id="9611c-117">它支援從入口網站或 Windows 電腦進行 .NET 開發, 並使用 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="9611c-117">It supports .NET development from the portal or Windows machines and uses the .NET Framework.</span></span> <span data-ttu-id="9611c-118">1.x 支援C#PYTHON、PHP、TypeScript、 F#Batch、Bash 和 PowerShell 的實驗性支援、JavaScript 和。</span><span class="sxs-lookup"><span data-stu-id="9611c-118">1.x supports C#, JavaScript, and F#, with experimental support for Python, PHP, TypeScript, Batch, Bash, and PowerShell.</span></span>

<span data-ttu-id="9611c-119">2\.x[版現在也已正式推出](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/)。</span><span class="sxs-lookup"><span data-stu-id="9611c-119">[Version 2.x is also generally available now](https://azure.microsoft.com/blog/introducing-azure-functions-2-0/).</span></span> <span data-ttu-id="9611c-120">它會利用 .NET Core, 並在 Windows、macOS 和 Linux 電腦上支援跨平臺開發。</span><span class="sxs-lookup"><span data-stu-id="9611c-120">It leverages .NET Core and supports cross-platform development on Windows, macOS, and Linux machines.</span></span> <span data-ttu-id="9611c-121">2.x 新增了 JAVA 的第一級支援, 但尚未直接支援任何實驗語言。</span><span class="sxs-lookup"><span data-stu-id="9611c-121">2.x adds first-class support for Java but doesn't yet directly support any of the experimental languages.</span></span> <span data-ttu-id="9611c-122">2\.x 版使用新的系結擴充性模型, 可啟用平臺的協力廠商延伸、系結的獨立版本控制, 以及更簡化的執行環境。</span><span class="sxs-lookup"><span data-stu-id="9611c-122">Version 2.x uses a new binding extensibility model that enables third-party extensions to the platform, independent versioning of bindings, and a more streamlined execution environment.</span></span>

> <span data-ttu-id="9611c-123">**1.x 具有系結重新[導向支援](https://github.com/Azure/azure-functions-host/issues/992)的已知問題。**</span><span class="sxs-lookup"><span data-stu-id="9611c-123">**There is a known issue in 1.x with [binding redirect support](https://github.com/Azure/azure-functions-host/issues/992).**</span></span> <span data-ttu-id="9611c-124">問題僅適用于 .NET 開發。</span><span class="sxs-lookup"><span data-stu-id="9611c-124">The issue is specific to .NET development.</span></span> <span data-ttu-id="9611c-125">具有相依性的專案, 與執行時間中包含的程式庫不同版本會受到影響。</span><span class="sxs-lookup"><span data-stu-id="9611c-125">Projects with dependencies on libraries that are a different version from the libraries included in the runtime are impacted.</span></span> <span data-ttu-id="9611c-126">函數小組致力於對問題做出具體的進度。</span><span class="sxs-lookup"><span data-stu-id="9611c-126">The functions team has committed to making concrete progress on the problem.</span></span> <span data-ttu-id="9611c-127">小組會先解決2.x 中的系結重新導向, 再進入正式運作狀態。</span><span class="sxs-lookup"><span data-stu-id="9611c-127">The team will address binding redirects in 2.x before it goes into general availability.</span></span> <span data-ttu-id="9611c-128">如有建議的修正和因應措施, 請參閱此官方小組聲明:[Azure Functions 中的元件解析](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions)。</span><span class="sxs-lookup"><span data-stu-id="9611c-128">The official team statement with suggested fixes and workarounds is available here: [Assembly resolution in Azure Functions](https://github.com/Azure/azure-functions-host/wiki/Assembly-Resolution-in-Azure-Functions).</span></span>

<span data-ttu-id="9611c-129">如需詳細資訊, 請參閱[比較1.x 和](https://docs.microsoft.com/azure/azure-functions/functions-versions)2.x。</span><span class="sxs-lookup"><span data-stu-id="9611c-129">For more information, see [Compare 1.x and 2.x](https://docs.microsoft.com/azure/azure-functions/functions-versions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="9611c-130">程式設計語言支援</span><span class="sxs-lookup"><span data-stu-id="9611c-130">Programming language support</span></span>

<span data-ttu-id="9611c-131">公開上市 (GA)、預覽或實驗性都支援下列語言。</span><span class="sxs-lookup"><span data-stu-id="9611c-131">The following languages are supported either in general availability (GA), preview, or experimental.</span></span>

|<span data-ttu-id="9611c-132">語言</span><span class="sxs-lookup"><span data-stu-id="9611c-132">Language</span></span>      |<span data-ttu-id="9611c-133">1.x</span><span class="sxs-lookup"><span data-stu-id="9611c-133">1.x</span></span>         |<span data-ttu-id="9611c-134">2.x</span><span class="sxs-lookup"><span data-stu-id="9611c-134">2.x</span></span>      |
|--------------|------------|---------|
|<span data-ttu-id="9611c-135">**C#**</span><span class="sxs-lookup"><span data-stu-id="9611c-135">**C#**</span></span>        |<span data-ttu-id="9611c-136">GA</span><span class="sxs-lookup"><span data-stu-id="9611c-136">GA</span></span>          |<span data-ttu-id="9611c-137">預覽</span><span class="sxs-lookup"><span data-stu-id="9611c-137">Preview</span></span>  |
|<span data-ttu-id="9611c-138">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="9611c-138">**JavaScript**</span></span>|<span data-ttu-id="9611c-139">GA</span><span class="sxs-lookup"><span data-stu-id="9611c-139">GA</span></span>          |<span data-ttu-id="9611c-140">預覽</span><span class="sxs-lookup"><span data-stu-id="9611c-140">Preview</span></span>  |
|<span data-ttu-id="9611c-141">**F#**</span><span class="sxs-lookup"><span data-stu-id="9611c-141">**F#**</span></span>        |<span data-ttu-id="9611c-142">GA</span><span class="sxs-lookup"><span data-stu-id="9611c-142">GA</span></span>          |         |
|<span data-ttu-id="9611c-143">**Java**</span><span class="sxs-lookup"><span data-stu-id="9611c-143">**Java**</span></span>      |            |<span data-ttu-id="9611c-144">預覽</span><span class="sxs-lookup"><span data-stu-id="9611c-144">Preview</span></span>  |
|<span data-ttu-id="9611c-145">**Python**</span><span class="sxs-lookup"><span data-stu-id="9611c-145">**Python**</span></span>    |<span data-ttu-id="9611c-146">實驗</span><span class="sxs-lookup"><span data-stu-id="9611c-146">Experimental</span></span>|         |
|<span data-ttu-id="9611c-147">**PHP**</span><span class="sxs-lookup"><span data-stu-id="9611c-147">**PHP**</span></span>       |<span data-ttu-id="9611c-148">實驗</span><span class="sxs-lookup"><span data-stu-id="9611c-148">Experimental</span></span>|         |
|<span data-ttu-id="9611c-149">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="9611c-149">**TypeScript**</span></span>|<span data-ttu-id="9611c-150">實驗</span><span class="sxs-lookup"><span data-stu-id="9611c-150">Experimental</span></span>|         |
|<span data-ttu-id="9611c-151">**Batch**</span><span class="sxs-lookup"><span data-stu-id="9611c-151">**Batch**</span></span>     |<span data-ttu-id="9611c-152">實驗</span><span class="sxs-lookup"><span data-stu-id="9611c-152">Experimental</span></span>|         |
|<span data-ttu-id="9611c-153">**狂歡**</span><span class="sxs-lookup"><span data-stu-id="9611c-153">**Bash**</span></span>      |<span data-ttu-id="9611c-154">實驗</span><span class="sxs-lookup"><span data-stu-id="9611c-154">Experimental</span></span>|         |
|<span data-ttu-id="9611c-155">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="9611c-155">**PowerShell**</span></span>|<span data-ttu-id="9611c-156">實驗</span><span class="sxs-lookup"><span data-stu-id="9611c-156">Experimental</span></span>|         |

<span data-ttu-id="9611c-157">如需詳細資訊, 請參閱[支援的語言](https://docs.microsoft.com/azure/azure-functions/supported-languages)。</span><span class="sxs-lookup"><span data-stu-id="9611c-157">For more information, see [Supported languages](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="9611c-158">App service 方案</span><span class="sxs-lookup"><span data-stu-id="9611c-158">App service plans</span></span>

<span data-ttu-id="9611c-159">函數是由*app service 方案*支援。</span><span class="sxs-lookup"><span data-stu-id="9611c-159">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="9611c-160">此方案會定義函數應用程式所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="9611c-160">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="9611c-161">您可以將方案指派給區域、判斷將使用的虛擬機器大小和數量, 以及挑選定價層。</span><span class="sxs-lookup"><span data-stu-id="9611c-161">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="9611c-162">針對真正的無伺服器方法, 函數應用程式可能會使用取用方案。</span><span class="sxs-lookup"><span data-stu-id="9611c-162">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="9611c-163">取用方案會根據負載自動調整後端。</span><span class="sxs-lookup"><span data-stu-id="9611c-163">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="9611c-164">如需詳細資訊, 請參閱[App service 方案](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)。</span><span class="sxs-lookup"><span data-stu-id="9611c-164">For more information, see [App service plans](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="9611c-165">建立您的第一個函式</span><span class="sxs-lookup"><span data-stu-id="9611c-165">Create your first function</span></span>

<span data-ttu-id="9611c-166">有三種常見的方式可供您建立函數應用程式。</span><span class="sxs-lookup"><span data-stu-id="9611c-166">There are three common ways you can create function apps.</span></span>

* <span data-ttu-id="9611c-167">在入口網站中編寫函式的腳本。</span><span class="sxs-lookup"><span data-stu-id="9611c-167">Script functions in the portal.</span></span>
* <span data-ttu-id="9611c-168">使用 Azure 命令列介面 (CLI) 來建立必要的資源。</span><span class="sxs-lookup"><span data-stu-id="9611c-168">Create the necessary resources using the Azure Command Line Interface (CLI).</span></span>
* <span data-ttu-id="9611c-169">使用您最愛的 IDE 在本機建立函式, 並將其發佈至 Azure。</span><span class="sxs-lookup"><span data-stu-id="9611c-169">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="9611c-170">如需在入口網站中建立腳本函式的詳細資訊, 請參閱在[Azure 入口網站中建立您的第一個函數](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)。</span><span class="sxs-lookup"><span data-stu-id="9611c-170">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="9611c-171">若要從 Azure CLI 建立, 請參閱[使用 Azure CLI 建立您的第一個](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)函式。</span><span class="sxs-lookup"><span data-stu-id="9611c-171">To build from the Azure CLI, see [Create your first function using the Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="9611c-172">若要從 Visual Studio 建立函數, 請參閱[使用 Visual Studio 建立您的第一個](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)函式。</span><span class="sxs-lookup"><span data-stu-id="9611c-172">To create a function from Visual Studio, see [Create your first function using Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="9611c-173">瞭解觸發程式和系結</span><span class="sxs-lookup"><span data-stu-id="9611c-173">Understand triggers and bindings</span></span>

<span data-ttu-id="9611c-174">函式是由*觸發*程式叫用, 而且可以只有一個。</span><span class="sxs-lookup"><span data-stu-id="9611c-174">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="9611c-175">除了叫用函式, 某些觸發程式也會做為系結。</span><span class="sxs-lookup"><span data-stu-id="9611c-175">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="9611c-176">除了觸發程式之外, 您也可以定義多個系結。</span><span class="sxs-lookup"><span data-stu-id="9611c-176">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="9611c-177">系結會提供宣告式方式, 將資料連線到您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="9611c-177">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="9611c-178">它們可以傳入 (輸入) 或接收資料 (輸出)。</span><span class="sxs-lookup"><span data-stu-id="9611c-178">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="9611c-179">觸發程式和系結可讓函式便於使用。</span><span class="sxs-lookup"><span data-stu-id="9611c-179">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="9611c-180">系結會移除手動建立資料庫或檔案系統連接的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="9611c-180">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="9611c-181">系結所需的所有資訊都包含在腳本的特殊函式*json*檔案中, 或以程式碼中的屬性宣告。</span><span class="sxs-lookup"><span data-stu-id="9611c-181">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="9611c-182">一些常見的觸發套裝程式括:</span><span class="sxs-lookup"><span data-stu-id="9611c-182">Some common triggers include:</span></span>

* <span data-ttu-id="9611c-183">Blob 儲存體: 在儲存體中上傳或變更檔案或資料夾時, 叫用您的函式。</span><span class="sxs-lookup"><span data-stu-id="9611c-183">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
* <span data-ttu-id="9611c-184">HTTP: 叫用您的函式, 例如 REST API。</span><span class="sxs-lookup"><span data-stu-id="9611c-184">HTTP: invoke your function like a REST API.</span></span>
* <span data-ttu-id="9611c-185">Queue: 當專案存在於佇列中時, 叫用您的函式。</span><span class="sxs-lookup"><span data-stu-id="9611c-185">Queue: invoke your function when items exist in a queue.</span></span>
* <span data-ttu-id="9611c-186">計時器: 定期叫用您的函式。</span><span class="sxs-lookup"><span data-stu-id="9611c-186">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="9611c-187">系結的範例包括:</span><span class="sxs-lookup"><span data-stu-id="9611c-187">Examples of bindings include:</span></span>

* <span data-ttu-id="9611c-188">CosmosDB: 輕鬆地連接到資料庫以載入或儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="9611c-188">CosmosDB: easily connect to the database to load or save files.</span></span>
* <span data-ttu-id="9611c-189">表格儲存體: 使用函數應用程式中的索引鍵/值儲存體。</span><span class="sxs-lookup"><span data-stu-id="9611c-189">Table Storage: work with key/value storage from your function app.</span></span>
* <span data-ttu-id="9611c-190">佇列儲存體: 輕鬆地從佇列取出專案, 或將新專案放在佇列上。</span><span class="sxs-lookup"><span data-stu-id="9611c-190">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="9611c-191">下列範例*函數. json*檔案會定義觸發程式和系結:</span><span class="sxs-lookup"><span data-stu-id="9611c-191">The following example *functions.json* file defines a trigger and a binding:</span></span>

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

<span data-ttu-id="9611c-192">在此範例中, 函式是由`images`容器中的 blob 儲存體變更所觸發。</span><span class="sxs-lookup"><span data-stu-id="9611c-192">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="9611c-193">檔案的資訊會傳入, 因此觸發程式也會做為系結。</span><span class="sxs-lookup"><span data-stu-id="9611c-193">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="9611c-194">有另一個系結可將資訊放在`images`名為的佇列上。</span><span class="sxs-lookup"><span data-stu-id="9611c-194">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="9611c-195">以下是函數C#的腳本:</span><span class="sxs-lookup"><span data-stu-id="9611c-195">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="9611c-196">此範例是一個簡單的函式, 會採用已修改或上傳至 blob 儲存體的檔案名稱, 並將它放在佇列上以供稍後處理。</span><span class="sxs-lookup"><span data-stu-id="9611c-196">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="9611c-197">如需觸發程式和系結的完整清單, 請參閱[Azure Functions 觸發程式和](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)系結概念。</span><span class="sxs-lookup"><span data-stu-id="9611c-197">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span></span>

## <a name="proxies"></a><span data-ttu-id="9611c-198">Proxy</span><span class="sxs-lookup"><span data-stu-id="9611c-198">Proxies</span></span>

<span data-ttu-id="9611c-199">Proxy 會為您的應用程式提供重新導向功能。</span><span class="sxs-lookup"><span data-stu-id="9611c-199">Proxies provide redirect functionality for your application.</span></span> <span data-ttu-id="9611c-200">Proxy 會公開端點, 並將該端點對應至另一個資源。</span><span class="sxs-lookup"><span data-stu-id="9611c-200">Proxies expose an endpoint and map that endpoint to another resource.</span></span> <span data-ttu-id="9611c-201">使用 proxy, 您可以:</span><span class="sxs-lookup"><span data-stu-id="9611c-201">With proxies, you can:</span></span>

* <span data-ttu-id="9611c-202">將連入要求重新路由至另一個端點。</span><span class="sxs-lookup"><span data-stu-id="9611c-202">Reroute an incoming request to another endpoint.</span></span>
* <span data-ttu-id="9611c-203">在傳入要求傳遞之前進行修改。</span><span class="sxs-lookup"><span data-stu-id="9611c-203">Modify the incoming request before it's passed along.</span></span>
* <span data-ttu-id="9611c-204">修改或提供回應。</span><span class="sxs-lookup"><span data-stu-id="9611c-204">Modify or provide a response.</span></span>

<span data-ttu-id="9611c-205">Proxy 用於下列案例:</span><span class="sxs-lookup"><span data-stu-id="9611c-205">Proxies are used for scenarios such as:</span></span>

* <span data-ttu-id="9611c-206">簡化、縮短或變更 URL。</span><span class="sxs-lookup"><span data-stu-id="9611c-206">Simplifying, shortening, or changing the URL.</span></span>
* <span data-ttu-id="9611c-207">提供一致的 API 前置詞給多個後端服務。</span><span class="sxs-lookup"><span data-stu-id="9611c-207">Providing a consistent API prefix to multiple back-end services.</span></span>
* <span data-ttu-id="9611c-208">模擬正在開發之端點的回應。</span><span class="sxs-lookup"><span data-stu-id="9611c-208">Mocking a response to an endpoint being developed.</span></span>
* <span data-ttu-id="9611c-209">提供對知名端點的靜態回應。</span><span class="sxs-lookup"><span data-stu-id="9611c-209">Providing a static response to a well-known endpoint.</span></span>
* <span data-ttu-id="9611c-210">移動或遷移後端時, 讓 API 端點保持一致。</span><span class="sxs-lookup"><span data-stu-id="9611c-210">Keeping an API endpoint consistent while the back end is moved or migrated.</span></span>

<span data-ttu-id="9611c-211">Proxy 會儲存為 JSON 定義。</span><span class="sxs-lookup"><span data-stu-id="9611c-211">Proxies are stored as JSON definitions.</span></span> <span data-ttu-id="9611c-212">請看以下範例：</span><span class="sxs-lookup"><span data-stu-id="9611c-212">Here is an example:</span></span>

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

<span data-ttu-id="9611c-213">`Domain Redirect` Proxy 會使用較短的路由, 並將其對應至較長的函式資源。</span><span class="sxs-lookup"><span data-stu-id="9611c-213">The `Domain Redirect` proxy takes a shortened route and maps it to the longer function resource.</span></span> <span data-ttu-id="9611c-214">轉換看起來像這樣:</span><span class="sxs-lookup"><span data-stu-id="9611c-214">The transformation looks like:</span></span>

`https://--shorturl--/123` -> `https://--longurl--.azurewebsites.net/api/UrlRedirect/123`

<span data-ttu-id="9611c-215">Proxy 會接受傳送至根 URL (`https://--shorturl--/`) 的任何專案, 並將其重新導向至檔網站。 `Root`</span><span class="sxs-lookup"><span data-stu-id="9611c-215">The `Root` proxy takes anything sent to the root URL (`https://--shorturl--/`) and redirects it to the documentation site.</span></span>

<span data-ttu-id="9611c-216">如需使用 proxy 的範例, 請觀看[Azure:透過無伺服器 Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102)將您的應用程式帶入雲端。</span><span class="sxs-lookup"><span data-stu-id="9611c-216">An example of using proxies is shown in the video [Azure: Bring your app to the cloud with serverless Azure Functions](https://channel9.msdn.com/events/Connect/2017/E102).</span></span> <span data-ttu-id="9611c-217">在本機 SQL Server 上執行的 ASP.NET Core 應用程式會即時移轉至 Azure 雲端。</span><span class="sxs-lookup"><span data-stu-id="9611c-217">In real time, an ASP.NET Core application running on local SQL Server is migrated to the Azure Cloud.</span></span> <span data-ttu-id="9611c-218">Proxy 是用來協助重構傳統的 Web API 專案以使用函式。</span><span class="sxs-lookup"><span data-stu-id="9611c-218">Proxies are used to help refactor a traditional Web API project to use functions.</span></span>

<span data-ttu-id="9611c-219">如需 proxy 的詳細資訊, 請參閱使用[Azure Functions Proxy](https://docs.microsoft.com/azure/azure-functions/functions-proxies)。</span><span class="sxs-lookup"><span data-stu-id="9611c-219">For more information about Proxies, see [Work with Azure Functions Proxies](https://docs.microsoft.com/azure/azure-functions/functions-proxies).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="9611c-220">[上一頁](azure-serverless-platform.md)
>[下一頁](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="9611c-220">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
