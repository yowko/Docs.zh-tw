---
ms.openlocfilehash: 47e8e15a64236d8ade2febb1add81fa4e5c030d9
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116171"
---

<span data-ttu-id="8139f-101">新增至套件管理員摘要的封裝會以 hackable 格式命名： `{product}-{type}-{version}`。</span><span class="sxs-lookup"><span data-stu-id="8139f-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="8139f-102">**產品**</span><span class="sxs-lookup"><span data-stu-id="8139f-102">**product**</span></span>\
<span data-ttu-id="8139f-103">要安裝的 .NET 產品類型。</span><span class="sxs-lookup"><span data-stu-id="8139f-103">The type of .NET product to install.</span></span> <span data-ttu-id="8139f-104">有效的選項為：</span><span class="sxs-lookup"><span data-stu-id="8139f-104">Valid options are:</span></span>

  - <span data-ttu-id="8139f-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="8139f-105">dotnet</span></span>
  - <span data-ttu-id="8139f-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="8139f-106">aspnetcore</span></span>

- <span data-ttu-id="8139f-107">**類型**</span><span class="sxs-lookup"><span data-stu-id="8139f-107">**type**</span></span>\
<span data-ttu-id="8139f-108">選擇 SDK 或執行時間。</span><span class="sxs-lookup"><span data-stu-id="8139f-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="8139f-109">有效的選項為：</span><span class="sxs-lookup"><span data-stu-id="8139f-109">Valid options are:</span></span>

  - <span data-ttu-id="8139f-110">SDK</span><span class="sxs-lookup"><span data-stu-id="8139f-110">sdk</span></span>
  - <span data-ttu-id="8139f-111">執行階段 ( runtime)</span><span class="sxs-lookup"><span data-stu-id="8139f-111">runtime</span></span>

- <span data-ttu-id="8139f-112">**版本**</span><span class="sxs-lookup"><span data-stu-id="8139f-112">**version**</span></span>\
<span data-ttu-id="8139f-113">要安裝的 SDK 或執行階段版本。</span><span class="sxs-lookup"><span data-stu-id="8139f-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="8139f-114">本文一律會提供最新支援版本的指示。</span><span class="sxs-lookup"><span data-stu-id="8139f-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="8139f-115">有效的選項為任何已發行的版本，例如：</span><span class="sxs-lookup"><span data-stu-id="8139f-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="8139f-116">3.0</span><span class="sxs-lookup"><span data-stu-id="8139f-116">3.0</span></span>
  - <span data-ttu-id="8139f-117">2.2</span><span class="sxs-lookup"><span data-stu-id="8139f-117">2.2</span></span>
  - <span data-ttu-id="8139f-118">2.1</span><span class="sxs-lookup"><span data-stu-id="8139f-118">2.1</span></span>

### <a name="examples"></a><span data-ttu-id="8139f-119">範例</span><span class="sxs-lookup"><span data-stu-id="8139f-119">Examples</span></span>

- <span data-ttu-id="8139f-120">安裝 .NET Core 2.2 SDK： `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="8139f-120">Install the .NET Core 2.2 SDK: `dotnet-sdk-2.2`</span></span>
- <span data-ttu-id="8139f-121">安裝 ASP.NET Core 3.1 執行時間： `aspnetcore-runtime-3.1`</span><span class="sxs-lookup"><span data-stu-id="8139f-121">Install the ASP.NET Core 3.1 runtime: `aspnetcore-runtime-3.1`</span></span>
- <span data-ttu-id="8139f-122">安裝 .NET Core 2.1 執行時間： `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="8139f-122">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>

### <a name="troubleshoot"></a><span data-ttu-id="8139f-123">疑難排解</span><span class="sxs-lookup"><span data-stu-id="8139f-123">Troubleshoot</span></span>

<span data-ttu-id="8139f-124">如果封裝組合無法運作，就無法使用。</span><span class="sxs-lookup"><span data-stu-id="8139f-124">If the package combination doesn't work, it's not available.</span></span> <span data-ttu-id="8139f-125">例如，沒有 ASP.NET Core SDK，SDK 元件會包含在 .NET Core SDK 中。</span><span class="sxs-lookup"><span data-stu-id="8139f-125">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="8139f-126">`aspnetcore-sdk-2.2` 的值不正確，應為 `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="8139f-126">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`</span></span>
