---
ms.openlocfilehash: 51b3c1b3e3d61b23a0511ca807afef0269ac9ee4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "77465977"
---

<span data-ttu-id="071b0-101">添加到包管理器源的包以可破解的格式命名： `{product}-{type}-{version}`。</span><span class="sxs-lookup"><span data-stu-id="071b0-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="071b0-102">**產品**</span><span class="sxs-lookup"><span data-stu-id="071b0-102">**product**</span></span>\
<span data-ttu-id="071b0-103">要安裝的 .NET 產品的類型。</span><span class="sxs-lookup"><span data-stu-id="071b0-103">The type of .NET product to install.</span></span> <span data-ttu-id="071b0-104">有效的選項包括：</span><span class="sxs-lookup"><span data-stu-id="071b0-104">Valid options are:</span></span>

  - <span data-ttu-id="071b0-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="071b0-105">dotnet</span></span>
  - <span data-ttu-id="071b0-106">阿斯普內科</span><span class="sxs-lookup"><span data-stu-id="071b0-106">aspnetcore</span></span>

- <span data-ttu-id="071b0-107">**類型**</span><span class="sxs-lookup"><span data-stu-id="071b0-107">**type**</span></span>\
<span data-ttu-id="071b0-108">選擇 SDK 或運行時。</span><span class="sxs-lookup"><span data-stu-id="071b0-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="071b0-109">有效的選項包括：</span><span class="sxs-lookup"><span data-stu-id="071b0-109">Valid options are:</span></span>

  - <span data-ttu-id="071b0-110">sdk</span><span class="sxs-lookup"><span data-stu-id="071b0-110">sdk</span></span>
  - <span data-ttu-id="071b0-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="071b0-111">runtime</span></span>

- <span data-ttu-id="071b0-112">**版本**</span><span class="sxs-lookup"><span data-stu-id="071b0-112">**version**</span></span>\
<span data-ttu-id="071b0-113">要安裝的 SDK 或運行時的版本。</span><span class="sxs-lookup"><span data-stu-id="071b0-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="071b0-114">本文將始終提供最新受支援版本的說明。</span><span class="sxs-lookup"><span data-stu-id="071b0-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="071b0-115">有效選項是任何發佈的版本，例如：</span><span class="sxs-lookup"><span data-stu-id="071b0-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="071b0-116">3.1</span><span class="sxs-lookup"><span data-stu-id="071b0-116">3.1</span></span>
  - <span data-ttu-id="071b0-117">3.0</span><span class="sxs-lookup"><span data-stu-id="071b0-117">3.0</span></span>
  - <span data-ttu-id="071b0-118">2.1</span><span class="sxs-lookup"><span data-stu-id="071b0-118">2.1</span></span>

  <span data-ttu-id="071b0-119">您嘗試下載的 SDK/運行時可能不適用於 Linux 發行版本。</span><span class="sxs-lookup"><span data-stu-id="071b0-119">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="071b0-120">有關受支援的分發的清單，請參閱[.NET Core 依賴項和要求](../dependencies.md?pivots=os-linux)。</span><span class="sxs-lookup"><span data-stu-id="071b0-120">For a list of supported distributions, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>

### <a name="examples"></a><span data-ttu-id="071b0-121">範例</span><span class="sxs-lookup"><span data-stu-id="071b0-121">Examples</span></span>

- <span data-ttu-id="071b0-122">安裝ASP.NET核心 3.1 運行時：`aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="071b0-122">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="071b0-123">安裝 .NET 核心 2.1 運行時：`dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="071b0-123">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="071b0-124">安裝 .NET 核心 3.0 SDK：`dotnet-sdk-3.0`</span><span class="sxs-lookup"><span data-stu-id="071b0-124">Install the .NET Core 3.0 SDK: `dotnet-sdk-3.0`</span></span>

### <a name="package-missing"></a><span data-ttu-id="071b0-125">缺少包</span><span class="sxs-lookup"><span data-stu-id="071b0-125">Package missing</span></span>

<span data-ttu-id="071b0-126">如果包版本組合不起作用，則不可用。</span><span class="sxs-lookup"><span data-stu-id="071b0-126">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="071b0-127">例如，沒有ASP.NET核心 SDK，SDK 元件包含在 .NET 核心 SDK 中。</span><span class="sxs-lookup"><span data-stu-id="071b0-127">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="071b0-128">該值`aspnetcore-sdk-2.2`不正確，應為`dotnet-sdk-2.2`。</span><span class="sxs-lookup"><span data-stu-id="071b0-128">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="071b0-129">有關 .NET Core 支援的 Linux 發行版本的清單，請參閱[.NET Core 依賴項和要求](../dependencies.md?pivots=os-linux)。</span><span class="sxs-lookup"><span data-stu-id="071b0-129">For a list of Linux distributions supported by .NET Core, see [.NET Core dependencies and requirements](../dependencies.md?pivots=os-linux).</span></span>
