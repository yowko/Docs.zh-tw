---
title: Azure Functions-無伺服器應用程式
description: 'Azure 函式提供跨多種語言（c #、JavaScript、JAVA）和平臺的無伺服器功能，以提供事件驅動的立即調整程式碼。'
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/06/2020
ms.openlocfilehash: 2dee60e3635be94a55ee26a7f04942bc59cb8dec
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135720"
---
# <a name="azure-functions"></a><span data-ttu-id="ae58c-103">Azure Functions</span><span class="sxs-lookup"><span data-stu-id="ae58c-103">Azure Functions</span></span>

<span data-ttu-id="ae58c-104">Azure 函式提供無伺服器計算體驗。</span><span class="sxs-lookup"><span data-stu-id="ae58c-104">Azure functions provide a serverless compute experience.</span></span> <span data-ttu-id="ae58c-105">函式是由*觸發*程式（例如存取 HTTP 端點或計時器）所叫用，並執行程式碼區塊或商務邏輯。</span><span class="sxs-lookup"><span data-stu-id="ae58c-105">A function is invoked by a *trigger* (such as access to an HTTP endpoint or a timer) and executes a block of code or business logic.</span></span> <span data-ttu-id="ae58c-106">函式也支援*特定的*系結，這些系結會連接到儲存體和佇列之類的資源。</span><span class="sxs-lookup"><span data-stu-id="ae58c-106">Functions also support specialized *bindings* that connect to resources like storage and queues.</span></span>

![Azure 函數標誌](./media/azure-functions-logo.png)

<span data-ttu-id="ae58c-108">目前的執行階段版本3.0 支援跨平臺 .NET Core 3.1 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ae58c-108">The current runtime version 3.0 supports cross-platform .NET Core 3.1 applications.</span></span> <span data-ttu-id="ae58c-109">支援 c # 以外的其他語言，例如 JavaScript、F # 和 JAVA。</span><span class="sxs-lookup"><span data-stu-id="ae58c-109">Additional languages besides C# such as JavaScript, F#, and Java are supported.</span></span> <span data-ttu-id="ae58c-110">在入口網站中建立的函數會提供豐富的腳本語法。</span><span class="sxs-lookup"><span data-stu-id="ae58c-110">Functions created in the portal provide a rich scripting syntax.</span></span> <span data-ttu-id="ae58c-111">建立為獨立專案的函式可以使用完整的平臺支援和功能進行部署。</span><span class="sxs-lookup"><span data-stu-id="ae58c-111">Functions created as standalone projects can be deployed with full platform support and capabilities.</span></span>

<span data-ttu-id="ae58c-112">如需詳細資訊，請參閱[Azure Functions 檔](https://docs.microsoft.com/azure/azure-functions)。</span><span class="sxs-lookup"><span data-stu-id="ae58c-112">For more information, see [Azure Functions documentation](https://docs.microsoft.com/azure/azure-functions).</span></span>

## <a name="programming-language-support"></a><span data-ttu-id="ae58c-113">程式設計語言支援</span><span class="sxs-lookup"><span data-stu-id="ae58c-113">Programming language support</span></span>

<span data-ttu-id="ae58c-114">公開上市（GA）支援下列語言。</span><span class="sxs-lookup"><span data-stu-id="ae58c-114">The following languages are all supported in general availability (GA).</span></span>

|<span data-ttu-id="ae58c-115">Language</span><span class="sxs-lookup"><span data-stu-id="ae58c-115">Language</span></span>      |<span data-ttu-id="ae58c-116">支援的執行時間</span><span class="sxs-lookup"><span data-stu-id="ae58c-116">Supported runtimes</span></span>|
|--------------|------------------|
|<span data-ttu-id="ae58c-117">**C#**</span><span class="sxs-lookup"><span data-stu-id="ae58c-117">**C#**</span></span>        |<span data-ttu-id="ae58c-118">.NET Core 3。1</span><span class="sxs-lookup"><span data-stu-id="ae58c-118">.NET Core 3.1</span></span>     |
|<span data-ttu-id="ae58c-119">**JavaScript**</span><span class="sxs-lookup"><span data-stu-id="ae58c-119">**JavaScript**</span></span>|<span data-ttu-id="ae58c-120">節點 10 & 12</span><span class="sxs-lookup"><span data-stu-id="ae58c-120">Node 10 & 12</span></span>      |
|<span data-ttu-id="ae58c-121">**F#**</span><span class="sxs-lookup"><span data-stu-id="ae58c-121">**F#**</span></span>        |<span data-ttu-id="ae58c-122">.NET Core 3。1</span><span class="sxs-lookup"><span data-stu-id="ae58c-122">.NET Core 3.1</span></span>     |
|<span data-ttu-id="ae58c-123">**Java**</span><span class="sxs-lookup"><span data-stu-id="ae58c-123">**Java**</span></span>      |<span data-ttu-id="ae58c-124">Java 8</span><span class="sxs-lookup"><span data-stu-id="ae58c-124">Java 8</span></span>            |
|<span data-ttu-id="ae58c-125">**Python**</span><span class="sxs-lookup"><span data-stu-id="ae58c-125">**Python**</span></span>    |<span data-ttu-id="ae58c-126">Python 3.6、3.7、& 3。8</span><span class="sxs-lookup"><span data-stu-id="ae58c-126">Python 3.6, 3.7, & 3.8</span></span>|
|<span data-ttu-id="ae58c-127">**TypeScript**</span><span class="sxs-lookup"><span data-stu-id="ae58c-127">**TypeScript**</span></span>|<span data-ttu-id="ae58c-128">節點 10 & 12 （透過 JavaScript）</span><span class="sxs-lookup"><span data-stu-id="ae58c-128">Node 10 & 12 (via JavaScript)</span></span>|
|<span data-ttu-id="ae58c-129">**PowerShell**</span><span class="sxs-lookup"><span data-stu-id="ae58c-129">**PowerShell**</span></span>|<span data-ttu-id="ae58c-130">PowerShell Core 6</span><span class="sxs-lookup"><span data-stu-id="ae58c-130">PowerShell Core 6</span></span>|

<span data-ttu-id="ae58c-131">如需詳細資訊，請參閱[支援的語言](https://docs.microsoft.com/azure/azure-functions/supported-languages)。</span><span class="sxs-lookup"><span data-stu-id="ae58c-131">For more information, see [Supported languages](https://docs.microsoft.com/azure/azure-functions/supported-languages).</span></span>

## <a name="app-service-plans"></a><span data-ttu-id="ae58c-132">App service 方案</span><span class="sxs-lookup"><span data-stu-id="ae58c-132">App service plans</span></span>

<span data-ttu-id="ae58c-133">函數是由*app service 方案*支援。</span><span class="sxs-lookup"><span data-stu-id="ae58c-133">Functions are backed by an *app service plan*.</span></span> <span data-ttu-id="ae58c-134">此方案會定義函數應用程式所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="ae58c-134">The plan defines the resources used by the functions app.</span></span> <span data-ttu-id="ae58c-135">您可以將方案指派給區域、判斷將使用的虛擬機器大小和數量，以及挑選定價層。</span><span class="sxs-lookup"><span data-stu-id="ae58c-135">You can assign plans to a region, determine the size and number of virtual machines that will be used, and pick a pricing tier.</span></span> <span data-ttu-id="ae58c-136">針對真正的無伺服器方法，函數應用程式可能會使用**取用方案。**</span><span class="sxs-lookup"><span data-stu-id="ae58c-136">For a true serverless approach, function apps may use the **consumption** plan.</span></span> <span data-ttu-id="ae58c-137">取用方案會根據負載自動調整後端。</span><span class="sxs-lookup"><span data-stu-id="ae58c-137">The consumption plan will scale the back end automatically based on load.</span></span>

<span data-ttu-id="ae58c-138">函數應用程式的另一個裝載選項是高階[計畫](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan)。</span><span class="sxs-lookup"><span data-stu-id="ae58c-138">Another hosting option for function apps is the [Premium plan](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan).</span></span> <span data-ttu-id="ae58c-139">此方案提供「永遠開啟」實例，以避免冷啟動、支援 VNet 連線能力之類的先進功能，並可在高階硬體上執行。</span><span class="sxs-lookup"><span data-stu-id="ae58c-139">This plan provides an "always on" instance to avoid cold start, supports advanced features like VNet connectivity, and runs on premium hardware.</span></span>

<span data-ttu-id="ae58c-140">如需詳細資訊，請參閱[App service 方案](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview)。</span><span class="sxs-lookup"><span data-stu-id="ae58c-140">For more information, see [App service plans](https://docs.microsoft.com/azure/app-service/azure-web-sites-web-hosting-plans-in-depth-overview).</span></span>

## <a name="create-your-first-function"></a><span data-ttu-id="ae58c-141">建立您的第一個函式</span><span class="sxs-lookup"><span data-stu-id="ae58c-141">Create your first function</span></span>

<span data-ttu-id="ae58c-142">有三種常見的方式可供您建立函數應用程式。</span><span class="sxs-lookup"><span data-stu-id="ae58c-142">There are three common ways you can create function apps.</span></span>

- <span data-ttu-id="ae58c-143">在入口網站中編寫函式的腳本。</span><span class="sxs-lookup"><span data-stu-id="ae58c-143">Script functions in the portal.</span></span>
- <span data-ttu-id="ae58c-144">使用 Azure CLI 建立必要的資源。</span><span class="sxs-lookup"><span data-stu-id="ae58c-144">Create the necessary resources using the Azure CLI.</span></span>
- <span data-ttu-id="ae58c-145">使用您最愛的 IDE 在本機建立函式，並將其發佈至 Azure。</span><span class="sxs-lookup"><span data-stu-id="ae58c-145">Build functions locally using your favorite IDE and publish them to Azure.</span></span>

<span data-ttu-id="ae58c-146">如需在入口網站中建立腳本函式的詳細資訊，請參閱在[Azure 入口網站中建立您的第一個函數](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function)。</span><span class="sxs-lookup"><span data-stu-id="ae58c-146">For more information on creating a scripted function in the portal, see [Create your first function in the Azure portal](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function).</span></span>

<span data-ttu-id="ae58c-147">若要從 Azure CLI 建立，請參閱[使用 Azure CLI 建立您的第一個](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli)函式。</span><span class="sxs-lookup"><span data-stu-id="ae58c-147">To build from the Azure CLI, see [Create your first function using the Azure CLI](https://docs.microsoft.com/azure/azure-functions/functions-create-first-azure-function-azure-cli).</span></span>

<span data-ttu-id="ae58c-148">若要從 Visual Studio 建立函數，請參閱[使用 Visual Studio 建立您的第一個](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio)函式。</span><span class="sxs-lookup"><span data-stu-id="ae58c-148">To create a function from Visual Studio, see [Create your first function using Visual Studio](https://docs.microsoft.com/azure/azure-functions/functions-create-your-first-function-visual-studio).</span></span>

## <a name="understand-triggers-and-bindings"></a><span data-ttu-id="ae58c-149">瞭解觸發程式和系結</span><span class="sxs-lookup"><span data-stu-id="ae58c-149">Understand triggers and bindings</span></span>

<span data-ttu-id="ae58c-150">函式是由*觸發*程式叫用，而且可以只有一個。</span><span class="sxs-lookup"><span data-stu-id="ae58c-150">Functions are invoked by a *trigger* and can have exactly one.</span></span> <span data-ttu-id="ae58c-151">除了叫用函式，某些觸發程式也會做為系結。</span><span class="sxs-lookup"><span data-stu-id="ae58c-151">In addition to invoking the function, certain triggers also serve as bindings.</span></span> <span data-ttu-id="ae58c-152">除了觸發程式之外，您也可以定義多個系結。</span><span class="sxs-lookup"><span data-stu-id="ae58c-152">You may also define multiple bindings in addition to the trigger.</span></span> <span data-ttu-id="ae58c-153">系結*會提供宣告*式方式，將資料連線到您的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ae58c-153">*Bindings* provide a declarative way to connect data to your code.</span></span> <span data-ttu-id="ae58c-154">它們可以傳入（輸入）或接收資料（輸出）。</span><span class="sxs-lookup"><span data-stu-id="ae58c-154">They can be passed in (input) or receive data (output).</span></span> <span data-ttu-id="ae58c-155">觸發程式和系結可讓函式便於使用。</span><span class="sxs-lookup"><span data-stu-id="ae58c-155">Triggers and bindings make functions easy to work with.</span></span> <span data-ttu-id="ae58c-156">系結會移除手動建立資料庫或檔案系統連接的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="ae58c-156">Bindings remove the overhead of manually creating database or file system connections.</span></span> <span data-ttu-id="ae58c-157">系結所需的所有資訊都包含在腳本的特殊函式*json*檔案中，或以程式碼中的屬性宣告。</span><span class="sxs-lookup"><span data-stu-id="ae58c-157">All of the information needed for the bindings is contained in a special *functions.json* file for scripts or declared with attributes in code.</span></span>

<span data-ttu-id="ae58c-158">一些常見的觸發套裝程式括：</span><span class="sxs-lookup"><span data-stu-id="ae58c-158">Some common triggers include:</span></span>

- <span data-ttu-id="ae58c-159">Blob 儲存體：在儲存體中上傳或變更檔案或資料夾時，叫用您的函式。</span><span class="sxs-lookup"><span data-stu-id="ae58c-159">Blob Storage: invoke your function when a file or folder is uploaded or changed in storage.</span></span>
- <span data-ttu-id="ae58c-160">HTTP：叫用您的函式，例如 REST API。</span><span class="sxs-lookup"><span data-stu-id="ae58c-160">HTTP: invoke your function like a REST API.</span></span>
- <span data-ttu-id="ae58c-161">Queue：當專案存在於佇列中時，叫用您的函式。</span><span class="sxs-lookup"><span data-stu-id="ae58c-161">Queue: invoke your function when items exist in a queue.</span></span>
- <span data-ttu-id="ae58c-162">計時器：定期叫用您的函式。</span><span class="sxs-lookup"><span data-stu-id="ae58c-162">Timer: invoke your function on a regular cadence.</span></span>

<span data-ttu-id="ae58c-163">系結的範例包括：</span><span class="sxs-lookup"><span data-stu-id="ae58c-163">Examples of bindings include:</span></span>

- <span data-ttu-id="ae58c-164">CosmosDB：輕鬆地連接到資料庫以載入或儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="ae58c-164">CosmosDB: easily connect to the database to load or save files.</span></span>
- <span data-ttu-id="ae58c-165">表格儲存體：使用函數應用程式中的索引鍵/值儲存體。</span><span class="sxs-lookup"><span data-stu-id="ae58c-165">Table Storage: work with key/value storage from your function app.</span></span>
- <span data-ttu-id="ae58c-166">佇列儲存體：輕鬆地從佇列取出專案，或將新專案放在佇列上。</span><span class="sxs-lookup"><span data-stu-id="ae58c-166">Queue Storage: easily retrieve items from a queue, or place new items on the queue.</span></span>

<span data-ttu-id="ae58c-167">下列範例*函數. json*檔案會定義觸發程式和系結：</span><span class="sxs-lookup"><span data-stu-id="ae58c-167">The following example *functions.json* file defines a trigger and a binding:</span></span>

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

<span data-ttu-id="ae58c-168">在此範例中，函式是由`images`容器中的 blob 儲存體變更所觸發。</span><span class="sxs-lookup"><span data-stu-id="ae58c-168">In this example, the function is triggered by a change to blob storage in the `images` container.</span></span> <span data-ttu-id="ae58c-169">檔案的資訊會傳入，因此觸發程式也會做為系結。</span><span class="sxs-lookup"><span data-stu-id="ae58c-169">The information for the file is passed in, so the trigger also acts as a binding.</span></span> <span data-ttu-id="ae58c-170">有另一個系結可將資訊放在`images`名為的佇列上。</span><span class="sxs-lookup"><span data-stu-id="ae58c-170">Another binding exists to put information onto a queue named `images`.</span></span>

<span data-ttu-id="ae58c-171">以下是函式的 c # 腳本：</span><span class="sxs-lookup"><span data-stu-id="ae58c-171">Here is the C# script for the function:</span></span>

```csharp
public static string Run(Stream myBlob, string name, TraceWriter log)
{
    log.Info($"C# Blob trigger function Processed blob\n Name:{name} \n Size: {myBlob.Length} Bytes");
    return name;
}
```

<span data-ttu-id="ae58c-172">此範例是一個簡單的函式，會採用已修改或上傳至 blob 儲存體的檔案名稱，並將它放在佇列上以供稍後處理。</span><span class="sxs-lookup"><span data-stu-id="ae58c-172">The example is a simple function that takes the name of the file that was modified or uploaded to blob storage, and places it on a queue for later processing.</span></span>

<span data-ttu-id="ae58c-173">如需觸發程式和系結的完整清單，請參閱[Azure Functions 觸發程式和](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings)系結概念。</span><span class="sxs-lookup"><span data-stu-id="ae58c-173">For a full list of triggers and bindings, see [Azure Functions triggers and bindings concepts](https://docs.microsoft.com/azure/azure-functions/functions-triggers-bindings).</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ae58c-174">[上一頁](azure-serverless-platform.md)
>[下一頁](application-insights.md)</span><span class="sxs-lookup"><span data-stu-id="ae58c-174">[Previous](azure-serverless-platform.md)
[Next](application-insights.md)</span></span>
