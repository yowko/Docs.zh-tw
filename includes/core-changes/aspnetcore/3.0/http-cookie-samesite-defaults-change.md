---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74282509"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a><span data-ttu-id="1a0dc-101">HTTP：某些 cookie SameSite 預設值已變更為 None</span><span class="sxs-lookup"><span data-stu-id="1a0dc-101">HTTP: Some cookie SameSite defaults changed to None</span></span>

<span data-ttu-id="1a0dc-102">`SameSite` 是 cookie 的選項，可協助降低某些跨網站偽造要求（CSRF）攻擊。</span><span class="sxs-lookup"><span data-stu-id="1a0dc-102">`SameSite` is an option for cookies that can help mitigate some Cross-Site Request Forgery (CSRF) attacks.</span></span> <span data-ttu-id="1a0dc-103">一開始引進此選項時，會跨各種 ASP.NET Core Api 使用不一致的預設值。</span><span class="sxs-lookup"><span data-stu-id="1a0dc-103">When this option was initially introduced, inconsistent defaults were used across various ASP.NET Core APIs.</span></span> <span data-ttu-id="1a0dc-104">不一致的結果會導致混淆。</span><span class="sxs-lookup"><span data-stu-id="1a0dc-104">The inconsistency has led to confusing results.</span></span> <span data-ttu-id="1a0dc-105">從 ASP.NET Core 3.0，這些預設值是較佳的對齊方式。</span><span class="sxs-lookup"><span data-stu-id="1a0dc-105">As of ASP.NET Core 3.0, these defaults are better aligned.</span></span> <span data-ttu-id="1a0dc-106">您必須針對每個元件加入宣告這項功能。</span><span class="sxs-lookup"><span data-stu-id="1a0dc-106">You must opt in to this feature on a per-component basis.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1a0dc-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="1a0dc-107">Version introduced</span></span>

<span data-ttu-id="1a0dc-108">3.0</span><span class="sxs-lookup"><span data-stu-id="1a0dc-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="1a0dc-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="1a0dc-109">Old behavior</span></span>

<span data-ttu-id="1a0dc-110">類似的 ASP.NET Core Api 使用不同的預設 <xref:Microsoft.AspNetCore.Http.SameSiteMode> 值。</span><span class="sxs-lookup"><span data-stu-id="1a0dc-110">Similar ASP.NET Core APIs used different default <xref:Microsoft.AspNetCore.Http.SameSiteMode> values.</span></span> <span data-ttu-id="1a0dc-111">`HttpResponse.Cookies.Append(String, String)` 和 `HttpResponse.Cookies.Append(String, String, CookieOptions)`中會出現不一致的範例，分別預設為 `SameSiteMode.None` 和 `SameSiteMode.Lax`。</span><span class="sxs-lookup"><span data-stu-id="1a0dc-111">An example of the inconsistency is seen in `HttpResponse.Cookies.Append(String, String)` and `HttpResponse.Cookies.Append(String, String, CookieOptions)`, which defaulted to `SameSiteMode.None` and `SameSiteMode.Lax`, respectively.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="1a0dc-112">新的行為</span><span class="sxs-lookup"><span data-stu-id="1a0dc-112">New behavior</span></span>

<span data-ttu-id="1a0dc-113">所有受影響的 Api 都會預設為 `SameSiteMode.None`。</span><span class="sxs-lookup"><span data-stu-id="1a0dc-113">All the affected APIs default to `SameSiteMode.None`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="1a0dc-114">變更的原因</span><span class="sxs-lookup"><span data-stu-id="1a0dc-114">Reason for change</span></span>

<span data-ttu-id="1a0dc-115">預設值已變更，使 `SameSite` 加入宣告功能。</span><span class="sxs-lookup"><span data-stu-id="1a0dc-115">The default value was changed to make `SameSite` an opt-in feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1a0dc-116">建議的動作</span><span class="sxs-lookup"><span data-stu-id="1a0dc-116">Recommended action</span></span>

<span data-ttu-id="1a0dc-117">發出 cookie 的每個元件都必須決定 `SameSite` 是否適用于其案例。</span><span class="sxs-lookup"><span data-stu-id="1a0dc-117">Each component that emits cookies needs to decide if `SameSite` is appropriate for its scenarios.</span></span> <span data-ttu-id="1a0dc-118">檢查受影響 Api 的使用方式，並視需要重新設定 `SameSite`。</span><span class="sxs-lookup"><span data-stu-id="1a0dc-118">Review your usage of the affected APIs and reconfigure `SameSite` as needed.</span></span>

#### <a name="category"></a><span data-ttu-id="1a0dc-119">類別</span><span class="sxs-lookup"><span data-stu-id="1a0dc-119">Category</span></span>

<span data-ttu-id="1a0dc-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="1a0dc-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1a0dc-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1a0dc-121">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)`
- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`

-->
