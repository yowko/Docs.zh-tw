---
ms.openlocfilehash: 02602c70689a6d2729e03d3d7230cda5ae7a4994
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901735"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a><span data-ttu-id="ad9bf-101">HTTP：瀏覽器 SameSite 變更影響驗證</span><span class="sxs-lookup"><span data-stu-id="ad9bf-101">HTTP: Browser SameSite changes impact authentication</span></span>

<span data-ttu-id="ad9bf-102">某些瀏覽器（例如 Chrome 和 Firefox）對其 cookie 的 `SameSite` 進行了重大變更。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-102">Some browsers, such as Chrome and Firefox, made breaking changes to their implementations of `SameSite` for cookies.</span></span> <span data-ttu-id="ad9bf-103">這些變更會影響遠端驗證案例，例如 OpenID Connect 和 WS-同盟，這必須藉由傳送 `SameSite=None`來退出宣告。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-103">The changes impact remote authentication scenarios, such as OpenID Connect and WS-Federation, which must opt out by sending `SameSite=None`.</span></span> <span data-ttu-id="ad9bf-104">不過，`SameSite=None` 會在 iOS 12 和一些較舊版本的其他瀏覽器上中斷。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-104">However, `SameSite=None` breaks on iOS 12 and some older versions of other browsers.</span></span> <span data-ttu-id="ad9bf-105">應用程式必須探查這些版本，並省略 `SameSite`。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-105">The app needs to sniff these versions and omit `SameSite`.</span></span>

<span data-ttu-id="ad9bf-106">如需此問題的討論，請參閱[dotnet/aspnetcore # 14996](https://github.com/dotnet/aspnetcore/issues/14996)。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-106">For discussion on this issue, see [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ad9bf-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="ad9bf-107">Version introduced</span></span>

<span data-ttu-id="ad9bf-108">3.1 Preview 1</span><span class="sxs-lookup"><span data-stu-id="ad9bf-108">3.1 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ad9bf-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="ad9bf-109">Old behavior</span></span>

<span data-ttu-id="ad9bf-110">`SameSite` 是 HTTP cookie 的2016草稿標準延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-110">`SameSite` is a 2016 draft standard extension to HTTP cookies.</span></span> <span data-ttu-id="ad9bf-111">其目的是要減少跨網站偽造要求（CSRF）。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-111">It's intended to mitigate Cross-Site Request Forgery (CSRF).</span></span> <span data-ttu-id="ad9bf-112">這原本是設計成伺服器透過新增新參數來加入宣告的功能。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-112">This was originally designed as a feature the servers would opt into by adding the new parameters.</span></span> <span data-ttu-id="ad9bf-113">ASP.NET Core 2.0 已新增 `SameSite`的初始支援。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-113">ASP.NET Core 2.0 added initial support for `SameSite`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ad9bf-114">新的行為</span><span class="sxs-lookup"><span data-stu-id="ad9bf-114">New behavior</span></span>

<span data-ttu-id="ad9bf-115">Google 提議的新草稿標準不相容。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-115">Google proposed a new draft standard that isn't backwards compatible.</span></span> <span data-ttu-id="ad9bf-116">標準會將預設模式變更為 `Lax`，並加入 `None` 退出宣告的新專案。針對大部分的應用程式 cookie `Lax` 尾碼;不過，它會中斷類似 OpenID Connect 和 WS-同盟登入的跨網站案例。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-116">The standard changes the default mode to `Lax` and adds a new entry `None` to opt out. `Lax` suffices for most app cookies; however, it breaks cross-site scenarios like OpenID Connect and WS-Federation login.</span></span> <span data-ttu-id="ad9bf-117">大部分的 OAuth 登入不會受到影響，因為要求的流動方式有所差異。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-117">Most OAuth logins aren't affected because of differences in how the request flows.</span></span> <span data-ttu-id="ad9bf-118">新的 `None` 參數會導致用戶端的相容性問題，而此標準會實作為先前的草稿標準（例如 iOS 12）。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-118">The new `None` parameter causes compatibility problems with clients that implemented the prior draft standard (for example, iOS 12).</span></span> <span data-ttu-id="ad9bf-119">Chrome 80 將包含變更。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-119">Chrome 80 will include the changes.</span></span> <span data-ttu-id="ad9bf-120">請參閱 Chrome 產品啟動時程表的[SameSite 更新](https://www.chromium.org/updates/same-site)。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-120">See [SameSite Updates](https://www.chromium.org/updates/same-site) for the Chrome product launch timeline.</span></span>

<span data-ttu-id="ad9bf-121">ASP.NET Core 3.1 已更新，可執行新的 `SameSite` 行為。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-121">ASP.NET Core 3.1 has been updated to implement the new `SameSite` behavior.</span></span> <span data-ttu-id="ad9bf-122">更新會重新定義發出 `SameSite=None` `SameSiteMode.None` 的行為，並加入新的值 `SameSiteMode.Unspecified` 以省略 `SameSite` 屬性。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-122">The update redefines the behavior of `SameSiteMode.None` to emit `SameSite=None` and adds a new value `SameSiteMode.Unspecified` to omit the `SameSite` attribute.</span></span> <span data-ttu-id="ad9bf-123">所有的 cookie Api 現在都預設為 `Unspecified`，不過，某些使用 cookie 的元件會針對其案例（例如 OpenID Connect 相互關聯和 nonce cookie）設定更具體的值。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-123">All cookie APIs now default to `Unspecified`, though some components that use cookies set values more specific to their scenarios such as the OpenID Connect correlation and nonce cookies.</span></span>

<span data-ttu-id="ad9bf-124">如需此區域中其他最近的變更，請參閱[HTTP：有些 Cookie SameSite 預設值已變更為 None](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none)。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-124">For other recent changes in this area, see [HTTP: Some cookie SameSite defaults changed to None](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none).</span></span> <span data-ttu-id="ad9bf-125">在 ASP.NET Core 3.0 中，大部分的預設值已從 <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> 變更為 <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> （但仍使用先前的標準）。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-125">In ASP.NET Core 3.0, most defaults were changed from <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> to <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (but still using the prior standard).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ad9bf-126">變更的原因</span><span class="sxs-lookup"><span data-stu-id="ad9bf-126">Reason for change</span></span>

<span data-ttu-id="ad9bf-127">瀏覽器和規格的變更如先前文字中所述。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-127">Browser and specification changes as outlined in the preceding text.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ad9bf-128">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ad9bf-128">Recommended action</span></span>

<span data-ttu-id="ad9bf-129">與遠端網站互動的應用程式（例如透過協力廠商登入）必須：</span><span class="sxs-lookup"><span data-stu-id="ad9bf-129">Apps that interact with remote sites, such as through third-party login, need to:</span></span>

* <span data-ttu-id="ad9bf-130">在多個瀏覽器上測試這些案例。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-130">Test those scenarios on multiple browsers.</span></span>
* <span data-ttu-id="ad9bf-131">套用[支援舊版瀏覽器](#support-older-browsers)中所討論的 cookie 原則瀏覽器探查緩和措施。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-131">Apply the cookie policy browser sniffing mitigation discussed in [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="ad9bf-132">如需測試和瀏覽器探查的指示，請參閱下一節。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-132">For testing and browser sniffing instructions, see the following section.</span></span>

##### <a name="determine-if-youre-affected"></a><span data-ttu-id="ad9bf-133">判斷您是否受影響</span><span class="sxs-lookup"><span data-stu-id="ad9bf-133">Determine if you're affected</span></span>

<span data-ttu-id="ad9bf-134">使用可選擇新行為的用戶端版本，測試您的 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-134">Test your web app using a client version that can opt into the new behavior.</span></span> <span data-ttu-id="ad9bf-135">Chrome、Firefox 和 Microsoft Edge Chromium 都有新的加入宣告功能旗標，可用於測試。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-135">Chrome, Firefox, and Microsoft Edge Chromium all have new opt-in feature flags that can be used for testing.</span></span> <span data-ttu-id="ad9bf-136">在套用修補程式之後，請確認您的應用程式與舊版用戶端版本相容，特別是 Safari。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-136">Verify that your app is compatible with older client versions after you've applied the patches, especially Safari.</span></span> <span data-ttu-id="ad9bf-137">如需詳細資訊，請參閱[支援舊版瀏覽器](#support-older-browsers)。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-137">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="chrome"></a><span data-ttu-id="ad9bf-138">Chrome</span><span class="sxs-lookup"><span data-stu-id="ad9bf-138">Chrome</span></span>

<span data-ttu-id="ad9bf-139">Chrome 78 和更新版本會產生誤導的測試結果。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-139">Chrome 78 and later yield misleading test results.</span></span> <span data-ttu-id="ad9bf-140">這些版本具有暫時的緩和措施，並允許不到兩分鐘的 cookie。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-140">Those versions have a temporary mitigation in place and allow cookies less than two minutes old.</span></span> <span data-ttu-id="ad9bf-141">啟用適當的測試旗標後，Chrome 76 和77會產生更精確的結果。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-141">With the appropriate test flags enabled, Chrome 76 and 77 yield more accurate results.</span></span> <span data-ttu-id="ad9bf-142">若要測試新的行為，請將 `chrome://flags/#same-site-by-default-cookies` 切換為 [已啟用]。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-142">To test the new behavior, toggle `chrome://flags/#same-site-by-default-cookies` to enabled.</span></span> <span data-ttu-id="ad9bf-143">Chrome 75 和更早版本會回報為失敗，並出現新的 `None` 設定。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-143">Chrome 75 and earlier are reported to fail with the new `None` setting.</span></span> <span data-ttu-id="ad9bf-144">如需詳細資訊，請參閱[支援舊版瀏覽器](#support-older-browsers)。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-144">For more information, see [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="ad9bf-145">Google 不會提供舊版的 Chrome 版本。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-145">Google doesn't make older Chrome versions available.</span></span> <span data-ttu-id="ad9bf-146">不過，您可以下載較舊版本的 Chromium，這樣就足以進行測試。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-146">You can, however, download older versions of Chromium, which will suffice for testing.</span></span> <span data-ttu-id="ad9bf-147">遵循[下載 Chromium](https://www.chromium.org/getting-involved/download-chromium)中的指示進行。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-147">Follow the instructions at [Download Chromium](https://www.chromium.org/getting-involved/download-chromium).</span></span>

* [<span data-ttu-id="ad9bf-148">Chromium 76 Win64</span><span class="sxs-lookup"><span data-stu-id="ad9bf-148">Chromium 76 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [<span data-ttu-id="ad9bf-149">Chromium 74 Win64</span><span class="sxs-lookup"><span data-stu-id="ad9bf-149">Chromium 74 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a><span data-ttu-id="ad9bf-150">Safari</span><span class="sxs-lookup"><span data-stu-id="ad9bf-150">Safari</span></span>

<span data-ttu-id="ad9bf-151">Safari 12 已嚴格執行先前的草稿，如果它在 cookie 中看到新的 `None` 值，則會失敗。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-151">Safari 12 strictly implemented the prior draft and fails if it sees the new `None` value in cookies.</span></span> <span data-ttu-id="ad9bf-152">這必須透過[支援舊版流覽](#support-older-browsers)器中顯示的瀏覽器探查程式碼來避免。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-152">This must be avoided via the browser sniffing code shown in [Support older browsers](#support-older-browsers).</span></span> <span data-ttu-id="ad9bf-153">請確定您使用 Microsoft Authentication Library （MSAL）、Active Directory 驗證程式庫（ADAL）或您使用的任何程式庫，測試 Safari 12 和13以及 WebKit 型 OS 樣式的登入。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-153">Ensure you test Safari 12 and 13 as well as WebKit-based, OS-style logins using Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL), or whichever library you're using.</span></span> <span data-ttu-id="ad9bf-154">問題取決於基礎作業系統版本。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-154">The problem is dependent on the underlying OS version.</span></span> <span data-ttu-id="ad9bf-155">已知 OSX Mojave 10.14 和 iOS 12 與新行為有相容性問題。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-155">OSX Mojave 10.14 and iOS 12 are known to have compatibility problems with the new behavior.</span></span> <span data-ttu-id="ad9bf-156">升級至 OSX Catalina 10.15 或 iOS 13 會修正問題。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-156">Upgrading to OSX Catalina 10.15 or iOS 13 fixes the problem.</span></span> <span data-ttu-id="ad9bf-157">Safari 目前沒有加入宣告旗標來測試新的規格行為。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-157">Safari doesn't currently have an opt-in flag for testing the new specification behavior.</span></span>

##### <a name="firefox"></a><span data-ttu-id="ad9bf-158">Firefox</span><span class="sxs-lookup"><span data-stu-id="ad9bf-158">Firefox</span></span>

<span data-ttu-id="ad9bf-159">新標準的 Firefox 支援可以在68版和更新版本上進行測試，方法是在 [`about:config`] 頁面上選擇 [`network.cookie.sameSite.laxByDefault`] 功能旗標。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-159">Firefox support for the new standard can be tested on version 68 and later by opting in on the `about:config` page with the feature flag `network.cookie.sameSite.laxByDefault`.</span></span> <span data-ttu-id="ad9bf-160">舊版 Firefox 未回報任何相容性問題。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-160">No compatibility issues have been reported on older versions of Firefox.</span></span>

##### <a name="microsoft-edge"></a><span data-ttu-id="ad9bf-161">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="ad9bf-161">Microsoft Edge</span></span>

<span data-ttu-id="ad9bf-162">雖然 Microsoft Edge 支援舊版的 `SameSite` 標準，但從44版起，新的標準不會有任何相容性問題。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-162">While Microsoft Edge supports the old `SameSite` standard, as of version 44 it didn't have any compatibility problems with the new standard.</span></span>

##### <a name="microsoft-edge-chromium"></a><span data-ttu-id="ad9bf-163">Microsoft Edge Chromium</span><span class="sxs-lookup"><span data-stu-id="ad9bf-163">Microsoft Edge Chromium</span></span>

<span data-ttu-id="ad9bf-164">功能旗標為 `edge://flags/#same-site-by-default-cookies`。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-164">The feature flag is `edge://flags/#same-site-by-default-cookies`.</span></span> <span data-ttu-id="ad9bf-165">使用 Microsoft Edge Chromium 78 進行測試時，未發現相容性問題。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-165">No compatibility issues were observed when testing with Microsoft Edge Chromium 78.</span></span>

##### <a name="electron"></a><span data-ttu-id="ad9bf-166">Electron</span><span class="sxs-lookup"><span data-stu-id="ad9bf-166">Electron</span></span>

<span data-ttu-id="ad9bf-167">Electron 的版本包含舊版的 Chromium。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-167">Versions of Electron include older versions of Chromium.</span></span> <span data-ttu-id="ad9bf-168">例如，Microsoft 團隊所使用的 Electron 版本是 Chromium 66，這會展現較舊的行為。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-168">For example, the version of Electron used by Microsoft Teams is Chromium 66, which exhibits the older behavior.</span></span> <span data-ttu-id="ad9bf-169">使用您的產品所使用的 Electron 版本，執行您自己的相容性測試。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-169">Perform your own compatibility testing with the version of Electron your product uses.</span></span> <span data-ttu-id="ad9bf-170">如需詳細資訊，請參閱[支援舊版瀏覽器](#support-older-browsers)。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-170">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="support-older-browsers"></a><span data-ttu-id="ad9bf-171">支援舊版瀏覽器</span><span class="sxs-lookup"><span data-stu-id="ad9bf-171">Support older browsers</span></span>

<span data-ttu-id="ad9bf-172">2016 `SameSite` 標準規定將未知的值視為 `SameSite=Strict` 值。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-172">The 2016 `SameSite` standard mandated that unknown values be treated as `SameSite=Strict` values.</span></span> <span data-ttu-id="ad9bf-173">因此，任何支援原始標準的舊版瀏覽器可能會在看到值為 `None`的 `SameSite` 屬性時中斷。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-173">Consequently, any older browsers that support the original standard may break when they see a `SameSite` property with a value of `None`.</span></span> <span data-ttu-id="ad9bf-174">如果 Web 應用程式想要支援這些舊的瀏覽器，則必須執行瀏覽器探查。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-174">Web apps must implement browser sniffing if they intend to support these old browsers.</span></span> <span data-ttu-id="ad9bf-175">ASP.NET Core 不會為您執行瀏覽器探查，因為 `User-Agent` 的要求標頭值高度不穩定，並每週變更一次。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-175">ASP.NET Core doesn't implement browser sniffing for you because `User-Agent` request header values are highly unstable and change on a weekly basis.</span></span> <span data-ttu-id="ad9bf-176">相反地，cookie 原則中的擴充點可讓您新增 `User-Agent`特定的邏輯。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-176">Instead, an extension point in the cookie policy allows you to add `User-Agent`-specific logic.</span></span>

<span data-ttu-id="ad9bf-177">在*Startup.cs*中，新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="ad9bf-177">In *Startup.cs*, add the following code:</span></span>

```csharp
private void CheckSameSite(HttpContext httpContext, CookieOptions options)
{
    if (options.SameSite == SameSiteMode.None) 
    { 
        var userAgent = httpContext.Request.Headers["User-Agent"].ToString();
        // TODO: Use your User Agent library of choice here. 
        if (/* UserAgent doesn't support new behavior */) 
        { 
            options.SameSite = SameSiteMode.Unspecified;
        }
    }
}

public void ConfigureServices(IServiceCollection services) 
{ 
    services.Configure<CookiePolicyOptions>(options => 
    { 
        options.MinimumSameSitePolicy = SameSiteMode.Unspecified;
        options.OnAppendCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
        options.OnDeleteCookie = cookieContext =>
            CheckSameSite(cookieContext.Context, cookieContext.CookieOptions);
    }); 
} 

public void Configure(IApplicationBuilder app) 
{ 
    // Before UseAuthentication or anything else that writes cookies.
    app.UseCookiePolicy();

    app.UseAuthentication(); 
    // code omitted for brevity
}
```

##### <a name="opt-out-switches"></a><span data-ttu-id="ad9bf-178">退出參數</span><span class="sxs-lookup"><span data-stu-id="ad9bf-178">Opt-out switches</span></span>

<span data-ttu-id="ad9bf-179">`Microsoft.AspNetCore.SuppressSameSiteNone` 相容性參數可讓您暫時退出新的 ASP.NET Core cookie 行為。</span><span class="sxs-lookup"><span data-stu-id="ad9bf-179">The `Microsoft.AspNetCore.SuppressSameSiteNone` compatibility switch enables you to temporarily opt out of the new ASP.NET Core cookie behavior.</span></span> <span data-ttu-id="ad9bf-180">將下列 JSON 新增至您專案中的 *.runtimeconfig.json json*檔案：</span><span class="sxs-lookup"><span data-stu-id="ad9bf-180">Add the following JSON to a *runtimeconfig.template.json* file in your project:</span></span>

```json
{ 
  "configProperties": { 
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true" 
  } 
}
```

##### <a name="other-versions"></a><span data-ttu-id="ad9bf-181">其他版本</span><span class="sxs-lookup"><span data-stu-id="ad9bf-181">Other Versions</span></span>

<span data-ttu-id="ad9bf-182">即將推出的相關 `SameSite` 修補程式如下：</span><span class="sxs-lookup"><span data-stu-id="ad9bf-182">Related `SameSite` patches are forthcoming for:</span></span>

* <span data-ttu-id="ad9bf-183">ASP.NET Core 2.1、2.2 和3.0</span><span class="sxs-lookup"><span data-stu-id="ad9bf-183">ASP.NET Core 2.1, 2.2, and 3.0</span></span>
* <span data-ttu-id="ad9bf-184">`Microsoft.Owin` 4.1</span><span class="sxs-lookup"><span data-stu-id="ad9bf-184">`Microsoft.Owin` 4.1</span></span>
* <span data-ttu-id="ad9bf-185">`System.Web` （適用于 .NET Framework 4.7.2 和更新版本）</span><span class="sxs-lookup"><span data-stu-id="ad9bf-185">`System.Web` (for .NET Framework 4.7.2 and later)</span></span>

#### <a name="category"></a><span data-ttu-id="ad9bf-186">分類</span><span class="sxs-lookup"><span data-stu-id="ad9bf-186">Category</span></span>

<span data-ttu-id="ad9bf-187">[ASP.NET]</span><span class="sxs-lookup"><span data-stu-id="ad9bf-187">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ad9bf-188">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ad9bf-188">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieBuilder.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.CookieOptions.SameSite%2A?displayProperty=fullName>
- <xref:Microsoft.AspNetCore.Http.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SameSiteMode?displayProperty=fullName>
- <xref:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite%2A?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`
- `Overload:Microsoft.AspNetCore.Http.CookieBuilder.SameSite`
- `Overload:Microsoft.AspNetCore.Http.CookieOptions.SameSite`
- `T:Microsoft.AspNetCore.Http.SameSiteMode`
- `T:Microsoft.Net.Http.Headers.SameSiteMode`
- `Overload:Microsoft.Net.Http.Headers.SetCookieHeaderValue.SameSite`

-->
