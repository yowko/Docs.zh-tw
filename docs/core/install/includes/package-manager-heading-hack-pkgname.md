---
ms.openlocfilehash: ab1006f706439bcf5129854da3d14538e5b690a2
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506848"
---

<span data-ttu-id="7d30f-101">加入封裝管理員摘要的封裝會以 hackable 格式命名： `{product}-{type}-{version}` 。</span><span class="sxs-lookup"><span data-stu-id="7d30f-101">The packages added to package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="7d30f-102">**產品**</span><span class="sxs-lookup"><span data-stu-id="7d30f-102">**product**</span></span>\
<span data-ttu-id="7d30f-103">要安裝的 .NET 產品類型。</span><span class="sxs-lookup"><span data-stu-id="7d30f-103">The type of .NET product to install.</span></span> <span data-ttu-id="7d30f-104">有效的選項包括：</span><span class="sxs-lookup"><span data-stu-id="7d30f-104">Valid options are:</span></span>

  - <span data-ttu-id="7d30f-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="7d30f-105">dotnet</span></span>
  - <span data-ttu-id="7d30f-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="7d30f-106">aspnetcore</span></span>

- <span data-ttu-id="7d30f-107">**類型**</span><span class="sxs-lookup"><span data-stu-id="7d30f-107">**type**</span></span>\
<span data-ttu-id="7d30f-108">選擇 SDK 或執行時間。</span><span class="sxs-lookup"><span data-stu-id="7d30f-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="7d30f-109">有效的選項包括：</span><span class="sxs-lookup"><span data-stu-id="7d30f-109">Valid options are:</span></span>

  - <span data-ttu-id="7d30f-110">sdk</span><span class="sxs-lookup"><span data-stu-id="7d30f-110">sdk</span></span>
  - <span data-ttu-id="7d30f-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="7d30f-111">runtime</span></span>

- <span data-ttu-id="7d30f-112">**版本**</span><span class="sxs-lookup"><span data-stu-id="7d30f-112">**version**</span></span>\
<span data-ttu-id="7d30f-113">要安裝的 SDK 或執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="7d30f-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="7d30f-114">本文一律會提供最新支援版本的指示。</span><span class="sxs-lookup"><span data-stu-id="7d30f-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="7d30f-115">有效的選項為任何已發行的版本，例如：</span><span class="sxs-lookup"><span data-stu-id="7d30f-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="7d30f-116">5.0</span><span class="sxs-lookup"><span data-stu-id="7d30f-116">5.0</span></span>
  - <span data-ttu-id="7d30f-117">3.1</span><span class="sxs-lookup"><span data-stu-id="7d30f-117">3.1</span></span>
  - <span data-ttu-id="7d30f-118">3.0</span><span class="sxs-lookup"><span data-stu-id="7d30f-118">3.0</span></span>
  - <span data-ttu-id="7d30f-119">2.1</span><span class="sxs-lookup"><span data-stu-id="7d30f-119">2.1</span></span>

  <span data-ttu-id="7d30f-120">您嘗試下載的 SDK/執行時間可能無法用於您的 Linux 散發套件。</span><span class="sxs-lookup"><span data-stu-id="7d30f-120">It's possible the SDK/runtime you're trying to download is not available for your Linux distribution.</span></span> <span data-ttu-id="7d30f-121">如需支援的發行版本清單，請參閱 [.Net Core 相依性和需求](../linux.md)。</span><span class="sxs-lookup"><span data-stu-id="7d30f-121">For a list of supported distributions, see [.NET Core dependencies and requirements](../linux.md).</span></span>

### <a name="examples"></a><span data-ttu-id="7d30f-122">範例</span><span class="sxs-lookup"><span data-stu-id="7d30f-122">Examples</span></span>

- <span data-ttu-id="7d30f-123">安裝 ASP.NET Core 5.0 執行時間： `aspnetcore-runtime-5.0`</span><span class="sxs-lookup"><span data-stu-id="7d30f-123">Install the ASP.NET Core 5.0 runtime: `aspnetcore-runtime-5.0`</span></span>
- <span data-ttu-id="7d30f-124">安裝 .NET Core 2.1 執行時間： `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="7d30f-124">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>
- <span data-ttu-id="7d30f-125">安裝 .NET 5.0 SDK： `dotnet-sdk-5.0`</span><span class="sxs-lookup"><span data-stu-id="7d30f-125">Install the .NET 5.0 SDK: `dotnet-sdk-5.0`</span></span>
- <span data-ttu-id="7d30f-126">安裝 .NET Core 3.1 SDK： `dotnet-sdk-3.1`</span><span class="sxs-lookup"><span data-stu-id="7d30f-126">Install the .NET Core 3.1 SDK: `dotnet-sdk-3.1`</span></span>

### <a name="package-missing"></a><span data-ttu-id="7d30f-127">封裝遺失</span><span class="sxs-lookup"><span data-stu-id="7d30f-127">Package missing</span></span>

<span data-ttu-id="7d30f-128">如果封裝版本組合無法運作，則無法使用。</span><span class="sxs-lookup"><span data-stu-id="7d30f-128">If the package-version combination doesn't work, it's not available.</span></span> <span data-ttu-id="7d30f-129">例如，沒有 ASP.NET Core SDK，SDK 元件隨附于 .NET SDK。</span><span class="sxs-lookup"><span data-stu-id="7d30f-129">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET SDK.</span></span> <span data-ttu-id="7d30f-130">值 `aspnetcore-sdk-2.2` 不正確，應該是 `dotnet-sdk-2.2` 。</span><span class="sxs-lookup"><span data-stu-id="7d30f-130">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`.</span></span> <span data-ttu-id="7d30f-131">如需 .NET Core 所支援的 Linux 發行版本清單，請參閱 .Net 相依性 [和需求](../linux.md)。</span><span class="sxs-lookup"><span data-stu-id="7d30f-131">For a list of Linux distributions supported by .NET Core, see [.NET dependencies and requirements](../linux.md).</span></span>
