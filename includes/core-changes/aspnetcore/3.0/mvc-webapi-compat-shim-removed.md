---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394403"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a><span data-ttu-id="47f65-101">MVC： Web API 相容性填充碼已移除</span><span class="sxs-lookup"><span data-stu-id="47f65-101">MVC: Web API compatibility shim removed</span></span>

<span data-ttu-id="47f65-102">從 ASP.NET Core 3.0 開始，`Microsoft.AspNetCore.Mvc.WebApiCompatShim` 封裝已無法再使用。</span><span class="sxs-lookup"><span data-stu-id="47f65-102">Starting with ASP.NET Core 3.0, the `Microsoft.AspNetCore.Mvc.WebApiCompatShim` package is no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="47f65-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="47f65-103">Change description</span></span>

<span data-ttu-id="47f65-104">@No__t-0 （WebApiCompatShim）套件提供 ASP.NET 4.x Web API 2 ASP.NET Core 的部分相容性，以簡化將現有的 Web API 部署遷移至 ASP.NET Core 的工作。</span><span class="sxs-lookup"><span data-stu-id="47f65-104">The `Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) package provides partial compatibility in ASP.NET Core with ASP.NET 4.x Web API 2 to simplify migrating existing Web API implementations to ASP.NET Core.</span></span> <span data-ttu-id="47f65-105">不過，使用 WebApiCompatShim 的應用程式不會受益于最近 ASP.NET Core 版本中的 API 相關功能隨附。</span><span class="sxs-lookup"><span data-stu-id="47f65-105">However, apps using the WebApiCompatShim don't benefit from the API-related features shipping in recent ASP.NET Core releases.</span></span> <span data-ttu-id="47f65-106">這類功能包括改良的開放式 API 規格產生、標準化的錯誤處理，以及用戶端程式代碼產生。</span><span class="sxs-lookup"><span data-stu-id="47f65-106">Such features include improved Open API specification generation, standardized error handling, and client code generation.</span></span> <span data-ttu-id="47f65-107">為了更專注于3.0 中的 API 工作，已移除 WebApiCompatShim。</span><span class="sxs-lookup"><span data-stu-id="47f65-107">To better focus the API efforts in 3.0, WebApiCompatShim was removed.</span></span> <span data-ttu-id="47f65-108">使用 WebApiCompatShim 的現有應用程式應該遷移至較新的 `[ApiController]` 模型。</span><span class="sxs-lookup"><span data-stu-id="47f65-108">Existing apps using the WebApiCompatShim should migrate to the newer `[ApiController]` model.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="47f65-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="47f65-109">Version introduced</span></span>

<span data-ttu-id="47f65-110">3.0</span><span class="sxs-lookup"><span data-stu-id="47f65-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="47f65-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="47f65-111">Reason for change</span></span>

<span data-ttu-id="47f65-112">Web API 相容性填充碼是一種遷移工具。</span><span class="sxs-lookup"><span data-stu-id="47f65-112">The Web API compatibility shim was a migration tool.</span></span> <span data-ttu-id="47f65-113">它會限制使用者存取 ASP.NET Core 中新增的功能。</span><span class="sxs-lookup"><span data-stu-id="47f65-113">It restricts user access to new functionality added in ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="47f65-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="47f65-114">Recommended action</span></span>

<span data-ttu-id="47f65-115">移除此填充碼的使用方式，並直接遷移至 ASP.NET Core 本身的類似功能。</span><span class="sxs-lookup"><span data-stu-id="47f65-115">Remove usage of this shim and migrate directly to the similar functionality in ASP.NET Core itself.</span></span>

#### <a name="category"></a><span data-ttu-id="47f65-116">分類</span><span class="sxs-lookup"><span data-stu-id="47f65-116">Category</span></span>

<span data-ttu-id="47f65-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="47f65-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="47f65-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="47f65-118">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
