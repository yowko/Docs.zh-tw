---
ms.openlocfilehash: 75945e7ff26c1c6db891d12cef4c16ed210da6af
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "72394403"
---
### <a name="mvc-web-api-compatibility-shim-removed"></a><span data-ttu-id="737c3-101">MVC：已刪除 Web API 相容性</span><span class="sxs-lookup"><span data-stu-id="737c3-101">MVC: Web API compatibility shim removed</span></span>

<span data-ttu-id="737c3-102">從 ASP.NET 酷 3.0`Microsoft.AspNetCore.Mvc.WebApiCompatShim`開始，該包不再可用。</span><span class="sxs-lookup"><span data-stu-id="737c3-102">Starting with ASP.NET Core 3.0, the `Microsoft.AspNetCore.Mvc.WebApiCompatShim` package is no longer available.</span></span>

#### <a name="change-description"></a><span data-ttu-id="737c3-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="737c3-103">Change description</span></span>

<span data-ttu-id="737c3-104">`Microsoft.AspNetCore.Mvc.WebApiCompatShim` （WebApiCompatShim） 包在ASP.NET酷中提供與ASP.NET 4.x Web API 2 的部分相容性，以簡化將現有 Web API 實現遷移到 ASP.NET Core。</span><span class="sxs-lookup"><span data-stu-id="737c3-104">The `Microsoft.AspNetCore.Mvc.WebApiCompatShim` (WebApiCompatShim) package provides partial compatibility in ASP.NET Core with ASP.NET 4.x Web API 2 to simplify migrating existing Web API implementations to ASP.NET Core.</span></span> <span data-ttu-id="737c3-105">但是，使用 WebApiCompatShim 的應用不會從最近ASP.NET核心版本中發佈的 API 相關功能中受益。</span><span class="sxs-lookup"><span data-stu-id="737c3-105">However, apps using the WebApiCompatShim don't benefit from the API-related features shipping in recent ASP.NET Core releases.</span></span> <span data-ttu-id="737c3-106">這些功能包括改進的 Open API 規範生成、標準化錯誤處理和用戶端代碼生成。</span><span class="sxs-lookup"><span data-stu-id="737c3-106">Such features include improved Open API specification generation, standardized error handling, and client code generation.</span></span> <span data-ttu-id="737c3-107">為了更好地集中 3.0 中的 API 工作，刪除了 WebApiCompatshim。</span><span class="sxs-lookup"><span data-stu-id="737c3-107">To better focus the API efforts in 3.0, WebApiCompatShim was removed.</span></span> <span data-ttu-id="737c3-108">使用 WebApiCompatShim 的現有應用應遷移到較新的`[ApiController]`模型。</span><span class="sxs-lookup"><span data-stu-id="737c3-108">Existing apps using the WebApiCompatShim should migrate to the newer `[ApiController]` model.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="737c3-109">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="737c3-109">Version introduced</span></span>

<span data-ttu-id="737c3-110">3.0</span><span class="sxs-lookup"><span data-stu-id="737c3-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="737c3-111">更改原因</span><span class="sxs-lookup"><span data-stu-id="737c3-111">Reason for change</span></span>

<span data-ttu-id="737c3-112">Web API 相容性是一個遷移工具。</span><span class="sxs-lookup"><span data-stu-id="737c3-112">The Web API compatibility shim was a migration tool.</span></span> <span data-ttu-id="737c3-113">它限制使用者訪問 ASP.NET Core 中添加的新功能。</span><span class="sxs-lookup"><span data-stu-id="737c3-113">It restricts user access to new functionality added in ASP.NET Core.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="737c3-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="737c3-114">Recommended action</span></span>

<span data-ttu-id="737c3-115">刪除此分片的使用，並直接遷移到ASP.NET核心本身的類似功能。</span><span class="sxs-lookup"><span data-stu-id="737c3-115">Remove usage of this shim and migrate directly to the similar functionality in ASP.NET Core itself.</span></span>

#### <a name="category"></a><span data-ttu-id="737c3-116">類別</span><span class="sxs-lookup"><span data-stu-id="737c3-116">Category</span></span>

<span data-ttu-id="737c3-117">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="737c3-117">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="737c3-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="737c3-118">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Mvc.WebApiCompatShim?displayProperty=fullName>

<!--

#### Affected APIs

N:Microsoft.AspNetCore.Mvc.WebApiCompatShim

-->
