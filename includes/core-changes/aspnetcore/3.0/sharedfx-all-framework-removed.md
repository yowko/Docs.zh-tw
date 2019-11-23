---
ms.openlocfilehash: 959f3959c28c7d0159be7a213986345e2865b9a2
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394177"
---
### <a name="shared-framework-removed-microsoftaspnetcoreall"></a><span data-ttu-id="29660-101">共用架構：已移除 AspNetCore。</span><span class="sxs-lookup"><span data-stu-id="29660-101">Shared framework: Removed Microsoft.AspNetCore.All</span></span>

<span data-ttu-id="29660-102">從 ASP.NET Core 3.0 開始，不再產生 `Microsoft.AspNetCore.All` 中繼套件和相符的 `Microsoft.AspNetCore.All` 共用架構。</span><span class="sxs-lookup"><span data-stu-id="29660-102">Starting in ASP.NET Core 3.0, the `Microsoft.AspNetCore.All` metapackage and the matching `Microsoft.AspNetCore.All` shared framework are no longer produced.</span></span> <span data-ttu-id="29660-103">此套件會在 ASP.NET Core 2.2 中提供，並會繼續在 ASP.NET Core 2.1 中接收服務更新。</span><span class="sxs-lookup"><span data-stu-id="29660-103">This package is available in ASP.NET Core 2.2 and will continue to receive servicing updates in ASP.NET Core 2.1.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="29660-104">引進的版本</span><span class="sxs-lookup"><span data-stu-id="29660-104">Version introduced</span></span>

<span data-ttu-id="29660-105">3.0</span><span class="sxs-lookup"><span data-stu-id="29660-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="29660-106">舊的行為</span><span class="sxs-lookup"><span data-stu-id="29660-106">Old behavior</span></span>

<span data-ttu-id="29660-107">應用程式可以使用 `Microsoft.AspNetCore.All` 中繼套件，以 .NET Core 上的 `Microsoft.AspNetCore.All` 共用架構為目標。</span><span class="sxs-lookup"><span data-stu-id="29660-107">Apps could use the `Microsoft.AspNetCore.All` metapackage to target the `Microsoft.AspNetCore.All` shared framework on .NET Core.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="29660-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="29660-108">New behavior</span></span>

<span data-ttu-id="29660-109">.NET Core 3.0 不包含 `Microsoft.AspNetCore.All` 的共用架構。</span><span class="sxs-lookup"><span data-stu-id="29660-109">.NET Core 3.0 doesn't include a `Microsoft.AspNetCore.All` shared framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="29660-110">變更的原因</span><span class="sxs-lookup"><span data-stu-id="29660-110">Reason for change</span></span>

<span data-ttu-id="29660-111">`Microsoft.AspNetCore.All` 中繼套件包含大量的外部相依性。</span><span class="sxs-lookup"><span data-stu-id="29660-111">The `Microsoft.AspNetCore.All` metapackage included a large number of external dependencies.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="29660-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="29660-112">Recommended action</span></span>

<span data-ttu-id="29660-113">遷移您的專案，以使用 `Microsoft.AspNetCore.App` 架構。</span><span class="sxs-lookup"><span data-stu-id="29660-113">Migrate your project to use the `Microsoft.AspNetCore.App` framework.</span></span> <span data-ttu-id="29660-114">先前在 `Microsoft.AspNetCore.All` 中提供的元件仍可在 NuGet 上取得。</span><span class="sxs-lookup"><span data-stu-id="29660-114">Components that were previously available in `Microsoft.AspNetCore.All` are still available on NuGet.</span></span> <span data-ttu-id="29660-115">這些元件現在會與您的應用程式一起部署，而不會包含在共用架構中。</span><span class="sxs-lookup"><span data-stu-id="29660-115">Those components are now deployed with your app instead of being included in the shared framework.</span></span>

#### <a name="category"></a><span data-ttu-id="29660-116">類別</span><span class="sxs-lookup"><span data-stu-id="29660-116">Category</span></span>

<span data-ttu-id="29660-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="29660-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="29660-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="29660-118">Affected APIs</span></span>

<span data-ttu-id="29660-119">無</span><span class="sxs-lookup"><span data-stu-id="29660-119">None</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
