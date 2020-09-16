---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901641"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a><span data-ttu-id="6cec5-101">裝載： ObjectPoolProvider 已從 >webhostbuilder 相依性中移除</span><span class="sxs-lookup"><span data-stu-id="6cec5-101">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>

<span data-ttu-id="6cec5-102">在讓 ASP.NET Core 更多付費的情況下， `ObjectPoolProvider` 已從主要的相依性集合中移除。</span><span class="sxs-lookup"><span data-stu-id="6cec5-102">As part of making ASP.NET Core more pay for play, the `ObjectPoolProvider` was removed from the main set of dependencies.</span></span> <span data-ttu-id="6cec5-103">依賴的特定元件 `ObjectPoolProvider` 現在會自行新增。</span><span class="sxs-lookup"><span data-stu-id="6cec5-103">Specific components relying on `ObjectPoolProvider` now add it themselves.</span></span>

<span data-ttu-id="6cec5-104">如需討論，請參閱 [dotnet/aspnetcore # 5944](https://github.com/dotnet/aspnetcore/issues/5944)。</span><span class="sxs-lookup"><span data-stu-id="6cec5-104">For discussion, see [dotnet/aspnetcore#5944](https://github.com/dotnet/aspnetcore/issues/5944).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6cec5-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="6cec5-105">Version introduced</span></span>

<span data-ttu-id="6cec5-106">3.0</span><span class="sxs-lookup"><span data-stu-id="6cec5-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="6cec5-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="6cec5-107">Old behavior</span></span>

<span data-ttu-id="6cec5-108">`WebHostBuilder``ObjectPoolProvider`預設會在 DI 容器中提供。</span><span class="sxs-lookup"><span data-stu-id="6cec5-108">`WebHostBuilder` provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="6cec5-109">新的行為</span><span class="sxs-lookup"><span data-stu-id="6cec5-109">New behavior</span></span>

<span data-ttu-id="6cec5-110">`WebHostBuilder``ObjectPoolProvider`在 DI 容器中，預設不再提供。</span><span class="sxs-lookup"><span data-stu-id="6cec5-110">`WebHostBuilder` no longer provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6cec5-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="6cec5-111">Reason for change</span></span>

<span data-ttu-id="6cec5-112">這是為了讓 ASP.NET Core 更多的播放付費所做的變更。</span><span class="sxs-lookup"><span data-stu-id="6cec5-112">This change was made to make ASP.NET Core more pay for play.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6cec5-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="6cec5-113">Recommended action</span></span>

<span data-ttu-id="6cec5-114">如果您的元件需要 `ObjectPoolProvider` ，則必須透過將其新增至您的相依性 `IServiceCollection` 。</span><span class="sxs-lookup"><span data-stu-id="6cec5-114">If your component requires `ObjectPoolProvider`, it needs to be added to your dependencies via the `IServiceCollection`.</span></span>

#### <a name="category"></a><span data-ttu-id="6cec5-115">類別</span><span class="sxs-lookup"><span data-stu-id="6cec5-115">Category</span></span>

<span data-ttu-id="6cec5-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6cec5-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6cec5-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="6cec5-117">Affected APIs</span></span>

<span data-ttu-id="6cec5-118">無</span><span class="sxs-lookup"><span data-stu-id="6cec5-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
