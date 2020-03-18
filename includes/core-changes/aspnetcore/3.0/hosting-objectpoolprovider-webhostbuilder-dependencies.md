---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901641"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a><span data-ttu-id="b825d-101">託管：從 WebHostBuilder 依賴項中刪除物件集區提供程式</span><span class="sxs-lookup"><span data-stu-id="b825d-101">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>

<span data-ttu-id="b825d-102">作為使ASP.NET核心遊戲支付更多費用的一部分，`ObjectPoolProvider`從主依賴項集中刪除了 。</span><span class="sxs-lookup"><span data-stu-id="b825d-102">As part of making ASP.NET Core more pay for play, the `ObjectPoolProvider` was removed from the main set of dependencies.</span></span> <span data-ttu-id="b825d-103">依賴于特定元件`ObjectPoolProvider`現在自行添加。</span><span class="sxs-lookup"><span data-stu-id="b825d-103">Specific components relying on `ObjectPoolProvider` now add it themselves.</span></span>

<span data-ttu-id="b825d-104">有關討論，請參閱[點網/阿斯平核心#5944](https://github.com/dotnet/aspnetcore/issues/5944)。</span><span class="sxs-lookup"><span data-stu-id="b825d-104">For discussion, see [dotnet/aspnetcore#5944](https://github.com/dotnet/aspnetcore/issues/5944).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="b825d-105">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="b825d-105">Version introduced</span></span>

<span data-ttu-id="b825d-106">3.0</span><span class="sxs-lookup"><span data-stu-id="b825d-106">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="b825d-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="b825d-107">Old behavior</span></span>

<span data-ttu-id="b825d-108">`WebHostBuilder`預設情況下`ObjectPoolProvider`在 DI 容器中提供。</span><span class="sxs-lookup"><span data-stu-id="b825d-108">`WebHostBuilder` provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="b825d-109">新的行為</span><span class="sxs-lookup"><span data-stu-id="b825d-109">New behavior</span></span>

<span data-ttu-id="b825d-110">`WebHostBuilder`預設情況下，DI`ObjectPoolProvider`容器中不再提供。</span><span class="sxs-lookup"><span data-stu-id="b825d-110">`WebHostBuilder` no longer provides `ObjectPoolProvider` by default in the DI container.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="b825d-111">更改原因</span><span class="sxs-lookup"><span data-stu-id="b825d-111">Reason for change</span></span>

<span data-ttu-id="b825d-112">這一改變是為了使ASP.NET核心公司為遊戲支付更多報酬。</span><span class="sxs-lookup"><span data-stu-id="b825d-112">This change was made to make ASP.NET Core more pay for play.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="b825d-113">建議的動作</span><span class="sxs-lookup"><span data-stu-id="b825d-113">Recommended action</span></span>

<span data-ttu-id="b825d-114">如果需要`ObjectPoolProvider`，則需要通過 將其添加到依賴項中`IServiceCollection`。</span><span class="sxs-lookup"><span data-stu-id="b825d-114">If your component requires `ObjectPoolProvider`, it needs to be added to your dependencies via the `IServiceCollection`.</span></span>

#### <a name="category"></a><span data-ttu-id="b825d-115">類別</span><span class="sxs-lookup"><span data-stu-id="b825d-115">Category</span></span>

<span data-ttu-id="b825d-116">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b825d-116">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="b825d-117">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="b825d-117">Affected APIs</span></span>

<span data-ttu-id="b825d-118">None</span><span class="sxs-lookup"><span data-stu-id="b825d-118">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
