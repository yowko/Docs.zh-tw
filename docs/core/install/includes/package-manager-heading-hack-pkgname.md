---
ms.openlocfilehash: 7a55641b3673dc4d8d9b328f0de99b7247ca51d4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450881"
---

<span data-ttu-id="0cc93-101">新增至套件管理員摘要的封裝會以 hackable 格式命名： `{product}-{type}-{version}`。</span><span class="sxs-lookup"><span data-stu-id="0cc93-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="0cc93-102">**產品**</span><span class="sxs-lookup"><span data-stu-id="0cc93-102">**product**</span></span>\
<span data-ttu-id="0cc93-103">要安裝的 .NET 產品類型。</span><span class="sxs-lookup"><span data-stu-id="0cc93-103">The type of .NET product to install.</span></span> <span data-ttu-id="0cc93-104">有效的選項包括：</span><span class="sxs-lookup"><span data-stu-id="0cc93-104">Valid options are:</span></span>

  - <span data-ttu-id="0cc93-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="0cc93-105">dotnet</span></span>
  - <span data-ttu-id="0cc93-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="0cc93-106">aspnetcore</span></span>

- <span data-ttu-id="0cc93-107">**類型**</span><span class="sxs-lookup"><span data-stu-id="0cc93-107">**type**</span></span>\
<span data-ttu-id="0cc93-108">選擇 SDK 或執行時間。</span><span class="sxs-lookup"><span data-stu-id="0cc93-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="0cc93-109">有效的選項包括：</span><span class="sxs-lookup"><span data-stu-id="0cc93-109">Valid options are:</span></span>

  - <span data-ttu-id="0cc93-110">sdk</span><span class="sxs-lookup"><span data-stu-id="0cc93-110">sdk</span></span>
  - <span data-ttu-id="0cc93-111">執行階段</span><span class="sxs-lookup"><span data-stu-id="0cc93-111">runtime</span></span>

- <span data-ttu-id="0cc93-112">**版本**</span><span class="sxs-lookup"><span data-stu-id="0cc93-112">**version**</span></span>\
<span data-ttu-id="0cc93-113">要安裝的 SDK 或執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="0cc93-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="0cc93-114">本文一律會提供最新支援版本的指示。</span><span class="sxs-lookup"><span data-stu-id="0cc93-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="0cc93-115">有效的選項為任何已發行的版本，例如：</span><span class="sxs-lookup"><span data-stu-id="0cc93-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="0cc93-116">3.0</span><span class="sxs-lookup"><span data-stu-id="0cc93-116">3.0</span></span>
  - <span data-ttu-id="0cc93-117">2.2</span><span class="sxs-lookup"><span data-stu-id="0cc93-117">2.2</span></span>
  - <span data-ttu-id="0cc93-118">2.1</span><span class="sxs-lookup"><span data-stu-id="0cc93-118">2.1</span></span>

### <a name="examples"></a><span data-ttu-id="0cc93-119">範例</span><span class="sxs-lookup"><span data-stu-id="0cc93-119">Examples</span></span>

- <span data-ttu-id="0cc93-120">安裝 .NET Core 2.2 SDK： `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="0cc93-120">Install the .NET Core 2.2 SDK: `dotnet-sdk-2.2`</span></span>
- <span data-ttu-id="0cc93-121">安裝 ASP.NET Core 3.0 執行時間： `aspnetcore-runtime-3.0`</span><span class="sxs-lookup"><span data-stu-id="0cc93-121">Install the ASP.NET Core 3.0 runtime: `aspnetcore-runtime-3.0`</span></span>
- <span data-ttu-id="0cc93-122">安裝 .NET Core 2.1 執行時間： `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="0cc93-122">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>

### <a name="troubleshoot"></a><span data-ttu-id="0cc93-123">疑難排解</span><span class="sxs-lookup"><span data-stu-id="0cc93-123">Troubleshoot</span></span>

<span data-ttu-id="0cc93-124">如果封裝組合無法運作，就無法使用。</span><span class="sxs-lookup"><span data-stu-id="0cc93-124">If the package combination doesn't work, it's not available.</span></span> <span data-ttu-id="0cc93-125">例如，沒有 ASP.NET Core SDK，SDK 元件會包含在 .NET Core SDK 中。</span><span class="sxs-lookup"><span data-stu-id="0cc93-125">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="0cc93-126">`aspnetcore-sdk-2.2` 的值不正確，應為 `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="0cc93-126">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`</span></span>
