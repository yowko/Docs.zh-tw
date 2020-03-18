---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74282509"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a><span data-ttu-id="2f363-101">HTTP： 某些 Cookie 同網站預設值更改為"無"</span><span class="sxs-lookup"><span data-stu-id="2f363-101">HTTP: Some cookie SameSite defaults changed to None</span></span>

<span data-ttu-id="2f363-102">`SameSite`是 Cookie 的一個選項，可説明緩解某些跨網站請求偽造 （CSRF） 攻擊。</span><span class="sxs-lookup"><span data-stu-id="2f363-102">`SameSite` is an option for cookies that can help mitigate some Cross-Site Request Forgery (CSRF) attacks.</span></span> <span data-ttu-id="2f363-103">最初引入此選項時，在各種ASP.NET核心 API 中使用了不一致的預設值。</span><span class="sxs-lookup"><span data-stu-id="2f363-103">When this option was initially introduced, inconsistent defaults were used across various ASP.NET Core APIs.</span></span> <span data-ttu-id="2f363-104">這種不一致導致了混亂的結果。</span><span class="sxs-lookup"><span data-stu-id="2f363-104">The inconsistency has led to confusing results.</span></span> <span data-ttu-id="2f363-105">從 ASP.NET Core 3.0 起，這些預設值可以更好地對齊。</span><span class="sxs-lookup"><span data-stu-id="2f363-105">As of ASP.NET Core 3.0, these defaults are better aligned.</span></span> <span data-ttu-id="2f363-106">您必須根據每個元件加入宣告此功能。</span><span class="sxs-lookup"><span data-stu-id="2f363-106">You must opt in to this feature on a per-component basis.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="2f363-107">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="2f363-107">Version introduced</span></span>

<span data-ttu-id="2f363-108">3.0</span><span class="sxs-lookup"><span data-stu-id="2f363-108">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="2f363-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="2f363-109">Old behavior</span></span>

<span data-ttu-id="2f363-110">類似的ASP.NET核心 API 使用不同的預設值<xref:Microsoft.AspNetCore.Http.SameSiteMode>。</span><span class="sxs-lookup"><span data-stu-id="2f363-110">Similar ASP.NET Core APIs used different default <xref:Microsoft.AspNetCore.Http.SameSiteMode> values.</span></span> <span data-ttu-id="2f363-111">不一致的示例分別`HttpResponse.Cookies.Append(String, String)`出現在 和`HttpResponse.Cookies.Append(String, String, CookieOptions)`中，後者分別預設為`SameSiteMode.None``SameSiteMode.Lax`和 。</span><span class="sxs-lookup"><span data-stu-id="2f363-111">An example of the inconsistency is seen in `HttpResponse.Cookies.Append(String, String)` and `HttpResponse.Cookies.Append(String, String, CookieOptions)`, which defaulted to `SameSiteMode.None` and `SameSiteMode.Lax`, respectively.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="2f363-112">新的行為</span><span class="sxs-lookup"><span data-stu-id="2f363-112">New behavior</span></span>

<span data-ttu-id="2f363-113">所有受影響的 API 預設為`SameSiteMode.None`。</span><span class="sxs-lookup"><span data-stu-id="2f363-113">All the affected APIs default to `SameSiteMode.None`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="2f363-114">更改原因</span><span class="sxs-lookup"><span data-stu-id="2f363-114">Reason for change</span></span>

<span data-ttu-id="2f363-115">預設值已更改，以進行`SameSite`加入宣告功能。</span><span class="sxs-lookup"><span data-stu-id="2f363-115">The default value was changed to make `SameSite` an opt-in feature.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="2f363-116">建議的動作</span><span class="sxs-lookup"><span data-stu-id="2f363-116">Recommended action</span></span>

<span data-ttu-id="2f363-117">發出 Cookie 的每個元件都需要決定是否適合`SameSite`其方案。</span><span class="sxs-lookup"><span data-stu-id="2f363-117">Each component that emits cookies needs to decide if `SameSite` is appropriate for its scenarios.</span></span> <span data-ttu-id="2f363-118">查看受影響 API 的使用方式，並根據需要重新`SameSite`配置。</span><span class="sxs-lookup"><span data-stu-id="2f363-118">Review your usage of the affected APIs and reconfigure `SameSite` as needed.</span></span>

#### <a name="category"></a><span data-ttu-id="2f363-119">類別</span><span class="sxs-lookup"><span data-stu-id="2f363-119">Category</span></span>

<span data-ttu-id="2f363-120">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="2f363-120">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="2f363-121">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="2f363-121">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)`
- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`

-->
