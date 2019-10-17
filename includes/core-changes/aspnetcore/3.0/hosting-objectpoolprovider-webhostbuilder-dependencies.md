---
ms.openlocfilehash: 16b9fde49f513643a37f65f3e926a34fc991c55a
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394315"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a><span data-ttu-id="52dc6-101">裝載：已從 WebHostBuilder 相依性移除 ObjectPoolProvider</span><span class="sxs-lookup"><span data-stu-id="52dc6-101">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>

<span data-ttu-id="52dc6-102">為了讓 ASP.NET Core 擁有更多的播放費用，`ObjectPoolProvider` 已從主要的相依性集合中移除。</span><span class="sxs-lookup"><span data-stu-id="52dc6-102">As part of making ASP.NET Core more pay for play, the `ObjectPoolProvider` was removed from the main set of dependencies.</span></span> <span data-ttu-id="52dc6-103">依賴 `ObjectPoolProvider` 的特定元件現在會自行新增。</span><span class="sxs-lookup"><span data-stu-id="52dc6-103">Specific components relying on `ObjectPoolProvider` now add it themselves.</span></span>

<span data-ttu-id="52dc6-104">如需討論，請參閱[aspnet/AspNetCore # 5944](https://github.com/aspnet/AspNetCore/issues/5944)。</span><span class="sxs-lookup"><span data-stu-id="52dc6-104">For discussion, see [aspnet/AspNetCore#5944](https://github.com/aspnet/AspNetCore/issues/5944).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="52dc6-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="52dc6-105">Version introduced</span></span>

<span data-ttu-id="52dc6-106">3.0</span><span class="sxs-lookup"><span data-stu-id="52dc6-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="52dc6-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="52dc6-107">Old behavior</span></span>

<span data-ttu-id="52dc6-108">`WebHostBuilder` 預設會在 DI 容器中提供 `ObjectPoolProvider`。</span><span class="sxs-lookup"><span data-stu-id="52dc6-108">`WebHostBuilder` provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="52dc6-109">新的行為</span><span class="sxs-lookup"><span data-stu-id="52dc6-109">New behavior</span></span>

<span data-ttu-id="52dc6-110">`WebHostBuilder` 不再于 DI 容器中提供 `ObjectPoolProvider`。</span><span class="sxs-lookup"><span data-stu-id="52dc6-110">`WebHostBuilder` no longer provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="52dc6-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="52dc6-111">Reason for change</span></span>

<span data-ttu-id="52dc6-112">進行這種變更是為了讓 ASP.NET Core 更多的播放費用。</span><span class="sxs-lookup"><span data-stu-id="52dc6-112">This change was made to make ASP.NET Core more pay for play.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="52dc6-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="52dc6-113">Recommended action</span></span>

<span data-ttu-id="52dc6-114">如果您的元件需要 `ObjectPoolProvider`，則必須透過 `IServiceCollection` 將其新增至您的相依性。</span><span class="sxs-lookup"><span data-stu-id="52dc6-114">If your component requires `ObjectPoolProvider`, it needs to be added to your dependencies via the `IServiceCollection`.</span></span>

#### <a name="category"></a><span data-ttu-id="52dc6-115">分類</span><span class="sxs-lookup"><span data-stu-id="52dc6-115">Category</span></span>

<span data-ttu-id="52dc6-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="52dc6-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="52dc6-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="52dc6-117">Affected APIs</span></span>

<span data-ttu-id="52dc6-118">無</span><span class="sxs-lookup"><span data-stu-id="52dc6-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
