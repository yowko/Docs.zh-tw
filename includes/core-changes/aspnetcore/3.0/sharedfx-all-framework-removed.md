---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394177"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a><span data-ttu-id="c621f-101">共用框架：刪除微軟.AspNetCore.所有</span><span class="sxs-lookup"><span data-stu-id="c621f-101">Shared framework: Removed Microsoft.AspNetCore.All</span></span>

<span data-ttu-id="c621f-102">從 ASP.NET 酷 3.0`Microsoft.AspNetCore.All`開始，不再生成`Microsoft.AspNetCore.All`元包和匹配的共用框架。</span><span class="sxs-lookup"><span data-stu-id="c621f-102">Starting in ASP.NET Core 3.0, the `Microsoft.AspNetCore.All` metapackage and the matching `Microsoft.AspNetCore.All` shared framework are no longer produced.</span></span> <span data-ttu-id="c621f-103">此包在 ASP.NET 酷 2.2 中可用，並將繼續在 ASP.NET 酷 2.1 中接收服務更新。</span><span class="sxs-lookup"><span data-stu-id="c621f-103">This package is available in ASP.NET Core 2.2 and will continue to receive servicing updates in ASP.NET Core 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="c621f-104">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="c621f-104">Version introduced</span></span>

<span data-ttu-id="c621f-105">3.0</span><span class="sxs-lookup"><span data-stu-id="c621f-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="c621f-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="c621f-106">Old behavior</span></span>

<span data-ttu-id="c621f-107">應用可以使用`Microsoft.AspNetCore.All`元包在 .NET `Microsoft.AspNetCore.All` Core 上定位共用框架。</span><span class="sxs-lookup"><span data-stu-id="c621f-107">Apps could use the `Microsoft.AspNetCore.All` metapackage to target the `Microsoft.AspNetCore.All` shared framework on .NET Core.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="c621f-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="c621f-108">New behavior</span></span>

<span data-ttu-id="c621f-109">.NET Core 3.0 不包括`Microsoft.AspNetCore.All`共用框架。</span><span class="sxs-lookup"><span data-stu-id="c621f-109">.NET Core 3.0 doesn't include a `Microsoft.AspNetCore.All` shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="c621f-110">更改原因</span><span class="sxs-lookup"><span data-stu-id="c621f-110">Reason for change</span></span>

<span data-ttu-id="c621f-111">元`Microsoft.AspNetCore.All`包包含大量外部依賴項。</span><span class="sxs-lookup"><span data-stu-id="c621f-111">The `Microsoft.AspNetCore.All` metapackage included a large number of external dependencies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="c621f-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="c621f-112">Recommended action</span></span>

<span data-ttu-id="c621f-113">遷移專案以使用`Microsoft.AspNetCore.App`框架。</span><span class="sxs-lookup"><span data-stu-id="c621f-113">Migrate your project to use the `Microsoft.AspNetCore.App` framework.</span></span> <span data-ttu-id="c621f-114">以前可用的元件`Microsoft.AspNetCore.All`在 NuGet 上仍然可用。</span><span class="sxs-lookup"><span data-stu-id="c621f-114">Components that were previously available in `Microsoft.AspNetCore.All` are still available on NuGet.</span></span> <span data-ttu-id="c621f-115">這些元件現在隨應用一起部署，而不是包含在共用框架中。</span><span class="sxs-lookup"><span data-stu-id="c621f-115">Those components are now deployed with your app instead of being included in the shared framework.</span></span>

#### <a name="category"></a><span data-ttu-id="c621f-116">類別</span><span class="sxs-lookup"><span data-stu-id="c621f-116">Category</span></span>

<span data-ttu-id="c621f-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="c621f-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="c621f-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c621f-118">Affected APIs</span></span>

<span data-ttu-id="c621f-119">None</span><span class="sxs-lookup"><span data-stu-id="c621f-119">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
