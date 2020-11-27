---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032412"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a><span data-ttu-id="795a4-101">共用架構：已移除 AspNetCore</span><span class="sxs-lookup"><span data-stu-id="795a4-101">Shared framework: Removed Microsoft.AspNetCore.All</span></span>

<span data-ttu-id="795a4-102">從 ASP.NET Core 3.0 開始， `Microsoft.AspNetCore.All` `Microsoft.AspNetCore.All` 就不會再產生中繼套件和相符的共用架構。</span><span class="sxs-lookup"><span data-stu-id="795a4-102">Starting in ASP.NET Core 3.0, the `Microsoft.AspNetCore.All` metapackage and the matching `Microsoft.AspNetCore.All` shared framework are no longer produced.</span></span> <span data-ttu-id="795a4-103">此封裝可在 ASP.NET Core 2.2 中取得，並將繼續在 ASP.NET Core 2.1 中接收服務更新。</span><span class="sxs-lookup"><span data-stu-id="795a4-103">This package is available in ASP.NET Core 2.2 and will continue to receive servicing updates in ASP.NET Core 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="795a4-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="795a4-104">Version introduced</span></span>

<span data-ttu-id="795a4-105">3.0</span><span class="sxs-lookup"><span data-stu-id="795a4-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="795a4-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="795a4-106">Old behavior</span></span>

<span data-ttu-id="795a4-107">應用程式可以使用 `Microsoft.AspNetCore.All` 中繼套件將目標設為 `Microsoft.AspNetCore.All` .net Core 上的共用架構。</span><span class="sxs-lookup"><span data-stu-id="795a4-107">Apps could use the `Microsoft.AspNetCore.All` metapackage to target the `Microsoft.AspNetCore.All` shared framework on .NET Core.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="795a4-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="795a4-108">New behavior</span></span>

<span data-ttu-id="795a4-109">.NET Core 3.0 不包含 `Microsoft.AspNetCore.All` 共用架構。</span><span class="sxs-lookup"><span data-stu-id="795a4-109">.NET Core 3.0 doesn't include a `Microsoft.AspNetCore.All` shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="795a4-110">變更的原因</span><span class="sxs-lookup"><span data-stu-id="795a4-110">Reason for change</span></span>

<span data-ttu-id="795a4-111">`Microsoft.AspNetCore.All`中繼套件包含許多外部相依性。</span><span class="sxs-lookup"><span data-stu-id="795a4-111">The `Microsoft.AspNetCore.All` metapackage included a large number of external dependencies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="795a4-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="795a4-112">Recommended action</span></span>

<span data-ttu-id="795a4-113">遷移您的專案以使用 `Microsoft.AspNetCore.App` 架構。</span><span class="sxs-lookup"><span data-stu-id="795a4-113">Migrate your project to use the `Microsoft.AspNetCore.App` framework.</span></span> <span data-ttu-id="795a4-114">先前可用的元件 `Microsoft.AspNetCore.All` 仍可在 NuGet 上取得。</span><span class="sxs-lookup"><span data-stu-id="795a4-114">Components that were previously available in `Microsoft.AspNetCore.All` are still available on NuGet.</span></span> <span data-ttu-id="795a4-115">這些元件現在會與您的應用程式一起部署，而不會包含在共用架構中。</span><span class="sxs-lookup"><span data-stu-id="795a4-115">Those components are now deployed with your app instead of being included in the shared framework.</span></span>

#### <a name="category"></a><span data-ttu-id="795a4-116">類別</span><span class="sxs-lookup"><span data-stu-id="795a4-116">Category</span></span>

<span data-ttu-id="795a4-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="795a4-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="795a4-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="795a4-118">Affected APIs</span></span>

<span data-ttu-id="795a4-119">無</span><span class="sxs-lookup"><span data-stu-id="795a4-119">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
