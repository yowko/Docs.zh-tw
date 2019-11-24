---
ms.openlocfilehash: 7a55641b3673dc4d8d9b328f0de99b7247ca51d4
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450881"
---

<span data-ttu-id="97b87-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span><span class="sxs-lookup"><span data-stu-id="97b87-101">The packages added to the package manager feeds are named in a hackable format: `{product}-{type}-{version}`.</span></span>

- <span data-ttu-id="97b87-102">**product**</span><span class="sxs-lookup"><span data-stu-id="97b87-102">**product**</span></span>\
<span data-ttu-id="97b87-103">The type of .NET product to install.</span><span class="sxs-lookup"><span data-stu-id="97b87-103">The type of .NET product to install.</span></span> <span data-ttu-id="97b87-104">有效的選項為：</span><span class="sxs-lookup"><span data-stu-id="97b87-104">Valid options are:</span></span>

  - <span data-ttu-id="97b87-105">dotnet</span><span class="sxs-lookup"><span data-stu-id="97b87-105">dotnet</span></span>
  - <span data-ttu-id="97b87-106">aspnetcore</span><span class="sxs-lookup"><span data-stu-id="97b87-106">aspnetcore</span></span>

- <span data-ttu-id="97b87-107">**type**</span><span class="sxs-lookup"><span data-stu-id="97b87-107">**type**</span></span>\
<span data-ttu-id="97b87-108">Chooses the SDK or the runtime.</span><span class="sxs-lookup"><span data-stu-id="97b87-108">Chooses the SDK or the runtime.</span></span> <span data-ttu-id="97b87-109">有效的選項為：</span><span class="sxs-lookup"><span data-stu-id="97b87-109">Valid options are:</span></span>

  - <span data-ttu-id="97b87-110">SDK</span><span class="sxs-lookup"><span data-stu-id="97b87-110">sdk</span></span>
  - <span data-ttu-id="97b87-111">runtime</span><span class="sxs-lookup"><span data-stu-id="97b87-111">runtime</span></span>

- <span data-ttu-id="97b87-112">**version**</span><span class="sxs-lookup"><span data-stu-id="97b87-112">**version**</span></span>\
<span data-ttu-id="97b87-113">The version of the SDK or runtime to install.</span><span class="sxs-lookup"><span data-stu-id="97b87-113">The version of the SDK or runtime to install.</span></span> <span data-ttu-id="97b87-114">This article will always give the instructions for the latest supported version.</span><span class="sxs-lookup"><span data-stu-id="97b87-114">This article will always give the instructions for the latest supported version.</span></span> <span data-ttu-id="97b87-115">Valid options are any released version, such as:</span><span class="sxs-lookup"><span data-stu-id="97b87-115">Valid options are any released version, such as:</span></span>

  - <span data-ttu-id="97b87-116">3.0</span><span class="sxs-lookup"><span data-stu-id="97b87-116">3.0</span></span>
  - <span data-ttu-id="97b87-117">2.2</span><span class="sxs-lookup"><span data-stu-id="97b87-117">2.2</span></span>
  - <span data-ttu-id="97b87-118">2.1</span><span class="sxs-lookup"><span data-stu-id="97b87-118">2.1</span></span>

### <a name="examples"></a><span data-ttu-id="97b87-119">範例</span><span class="sxs-lookup"><span data-stu-id="97b87-119">Examples</span></span>

- <span data-ttu-id="97b87-120">Install the .NET Core 2.2 SDK: `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="97b87-120">Install the .NET Core 2.2 SDK: `dotnet-sdk-2.2`</span></span>
- <span data-ttu-id="97b87-121">Install the ASP.NET Core 3.0 runtime: `aspnetcore-runtime-3.0`</span><span class="sxs-lookup"><span data-stu-id="97b87-121">Install the ASP.NET Core 3.0 runtime: `aspnetcore-runtime-3.0`</span></span>
- <span data-ttu-id="97b87-122">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span><span class="sxs-lookup"><span data-stu-id="97b87-122">Install the .NET Core 2.1 runtime: `dotnet-runtime-2.1`</span></span>

### <a name="troubleshoot"></a><span data-ttu-id="97b87-123">疑難排解</span><span class="sxs-lookup"><span data-stu-id="97b87-123">Troubleshoot</span></span>

<span data-ttu-id="97b87-124">If the package combination doesn't work, it's not available.</span><span class="sxs-lookup"><span data-stu-id="97b87-124">If the package combination doesn't work, it's not available.</span></span> <span data-ttu-id="97b87-125">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="97b87-125">For example, there isn't an ASP.NET Core SDK, the SDK components are included with the .NET Core SDK.</span></span> <span data-ttu-id="97b87-126">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`</span><span class="sxs-lookup"><span data-stu-id="97b87-126">The value `aspnetcore-sdk-2.2` is incorrect and should be `dotnet-sdk-2.2`</span></span>
