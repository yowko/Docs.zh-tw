---
ms.openlocfilehash: 7723892a33bf7dd8e475b2f696db5d9ab287e182
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84602989"
---

<span data-ttu-id="e76d2-101">新增至套件管理員摘要的封裝會以 hackable 格式命名： `{product}-{type}-{version}` 。</span><span class="sxs-lookup"><span data-stu-id="e76d2-101">The packages added to package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="e76d2-102">**基礎**</span><span class="sxs-lookup"><span data-stu-id="e76d2-102">**product**</span></span>\
<span data-ttu-id="e76d2-103">要安裝的 .NET 產品類型。</span><span class="sxs-lookup"><span data-stu-id="e76d2-103">The type of .NET product to install.</span></span> <span data-ttu-id="e76d2-104">有效的選項包括：</span><span class="sxs-lookup"><span data-stu-id="e76d2-104">Valid options are:</span></span>

  - <span data-ttu-id="e76d2-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="e76d2-105">dotnet</span></span>
  - <span data-ttu-id="e76d2-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="e76d2-106">aspnetcore</span></span>

- <span data-ttu-id="e76d2-107">**型**</span><span class="sxs-lookup"><span data-stu-id="e76d2-107">**type**</span></span>\
<span data-ttu-id="e76d2-108">選擇 SDK 或執行時間。</span><span class="sxs-lookup"><span data-stu-id="e76d2-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="e76d2-109">有效的選項包括：</span><span class="sxs-lookup"><span data-stu-id="e76d2-109">Valid options are:</span></span>

  - <span data-ttu-id="e76d2-110">sdk</span><span class="sxs-lookup"><span data-stu-id="e76d2-110">sdk</span></span>
  - <span data-ttu-id="e76d2-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="e76d2-111">runtime</span></span>

- <span data-ttu-id="e76d2-112">**版本**</span><span class="sxs-lookup"><span data-stu-id="e76d2-112">**version**</span></span>\
<span data-ttu-id="e76d2-113">要安裝的 SDK 或執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="e76d2-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="e76d2-114">本文一律會提供最新支援版本的指示。</span><span class="sxs-lookup"><span data-stu-id="e76d2-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="e76d2-115">有效的選項為任何已發行的版本，例如：</span><span class="sxs-lookup"><span data-stu-id="e76d2-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="e76d2-116">3.1</span><span class="sxs-lookup"><span data-stu-id="e76d2-116">3.1</span></span>
  - <span data-ttu-id="e76d2-117">3.0</span><span class="sxs-lookup"><span data-stu-id="e76d2-117">3.0</span></span>
  - <span data-ttu-id="e76d2-118">2.1</span><span class="sxs-lookup"><span data-stu-id="e76d2-118">2.1</span></span>

  <span data-ttu-id="e76d2-119">您嘗試下載的 SDK/執行時間可能不適用於您的 Linux 散發套件。</span><span class="sxs-lookup"><span data-stu-id="e76d2-119">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="e76d2-120">如需支援的發行版本清單，請參閱[.Net Core 相依性和需求](../linux.md)。</span><span class="sxs-lookup"><span data-stu-id="e76d2-120">For a list of supported distributions, see [.NET Core dependencies and requirements](../linux.md).</span></span>

### <a name="examples"></a><span data-ttu-id="e76d2-121">範例</span><span class="sxs-lookup"><span data-stu-id="e76d2-121">Examples</span></span>

- <span data-ttu-id="e76d2-122">安裝 ASP.NET Core 3.1 執行時間：`aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="e76d2-122">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="e76d2-123">安裝 .NET Core 2.1 執行時間：`dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="e76d2-123">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="e76d2-124">安裝 .NET Core 3.1 SDK：`dotnet-sdk-3.1`</span><span class="sxs-lookup"><span data-stu-id="e76d2-124">Install the .NET Core 3.1 SDK: `dotnet-sdk-3.1`</span></span>

### <a name="package-missing"></a><span data-ttu-id="e76d2-125">套件遺失</span><span class="sxs-lookup"><span data-stu-id="e76d2-125">Package missing</span></span>

<span data-ttu-id="e76d2-126">如果封裝版本組合無效，則無法使用。</span><span class="sxs-lookup"><span data-stu-id="e76d2-126">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="e76d2-127">例如，沒有 ASP.NET Core SDK，SDK 元件會包含在 .NET Core SDK 中。</span><span class="sxs-lookup"><span data-stu-id="e76d2-127">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="e76d2-128">值 `aspnetcore-sdk-2.2` 不正確，應該是 `dotnet-sdk-2.2` 。</span><span class="sxs-lookup"><span data-stu-id="e76d2-128">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="e76d2-129">如需 .NET Core 支援的 Linux 發行版本清單，請參閱[.Net core 相依性和需求](../linux.md)。</span><span class="sxs-lookup"><span data-stu-id="e76d2-129">For a list of Linux distributions supported by .NET Core, see [.NET Core dependencies and requirements](../linux.md).</span></span>
