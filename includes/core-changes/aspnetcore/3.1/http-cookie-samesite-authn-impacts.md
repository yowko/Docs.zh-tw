---
ms.openlocfilehash: 8b6d334677991382d235fd53cd3c98e3a77d650d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539575"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a><span data-ttu-id="ecf3b-101">HTTP：瀏覽器 SameSite 變更會影響驗證</span><span class="sxs-lookup"><span data-stu-id="ecf3b-101">HTTP: Browser SameSite changes impact authentication</span></span>

<span data-ttu-id="ecf3b-102">某些瀏覽器（例如 Chrome 和 Firefox）會對其 cookie 的執行進行中斷性變更 `SameSite` 。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-102">Some browsers, such as Chrome and Firefox, made breaking changes to their implementations of `SameSite` for cookies.</span></span> <span data-ttu-id="ecf3b-103">這些變更會影響遠端驗證案例，例如 OpenID Connect 和 WS-同盟，必須透過傳送來退出 `SameSite=None` 。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-103">The changes impact remote authentication scenarios, such as OpenID Connect and WS-Federation, which must opt out by sending `SameSite=None`.</span></span> <span data-ttu-id="ecf3b-104">但是，會 `SameSite=None` 在 iOS 12 和某些舊版的其他瀏覽器上中斷。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-104">However, `SameSite=None` breaks on iOS 12 and some older versions of other browsers.</span></span> <span data-ttu-id="ecf3b-105">應用程式必須探查這些版本並省略 `SameSite` 。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-105">The app needs to sniff these versions and omit `SameSite`.</span></span>

<span data-ttu-id="ecf3b-106">如需此問題的討論，請參閱 [dotnet/aspnetcore # 14996](https://github.com/dotnet/aspnetcore/issues/14996)。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-106">For discussion on this issue, see [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ecf3b-107">引進的版本</span><span class="sxs-lookup"><span data-stu-id="ecf3b-107">Version introduced</span></span>

<span data-ttu-id="ecf3b-108">3.1 Preview 1</span><span class="sxs-lookup"><span data-stu-id="ecf3b-108">3.1 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="ecf3b-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="ecf3b-109">Old behavior</span></span>

<span data-ttu-id="ecf3b-110">`SameSite` 是 HTTP cookie 的2016草稿標準延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-110">`SameSite` is a 2016 draft standard extension to HTTP cookies.</span></span> <span data-ttu-id="ecf3b-111">其目的是要降低跨網站偽造要求 (CSRF) 。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-111">It's intended to mitigate Cross-Site Request Forgery (CSRF).</span></span> <span data-ttu-id="ecf3b-112">這原本是設計為伺服器在加入新參數時加入宣告的功能。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-112">This was originally designed as a feature the servers would opt into by adding the new parameters.</span></span> <span data-ttu-id="ecf3b-113">ASP.NET Core 2.0 已新增的初始支援 `SameSite` 。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-113">ASP.NET Core 2.0 added initial support for `SameSite`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="ecf3b-114">新的行為</span><span class="sxs-lookup"><span data-stu-id="ecf3b-114">New behavior</span></span>

<span data-ttu-id="ecf3b-115">Google 提議新的草稿標準，但無法回溯相容。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-115">Google proposed a new draft standard that isn't backwards compatible.</span></span> <span data-ttu-id="ecf3b-116">標準會將預設模式變更為 `Lax` ，並加入新的專案 `None` 以退出宣告。 `Lax` 尾碼大部分的應用程式 cookie，不過它會破壞跨網站案例，例如 OpenID Connect 和 WS-同盟登入。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-116">The standard changes the default mode to `Lax` and adds a new entry `None` to opt out. `Lax` suffices for most app cookies; however, it breaks cross-site scenarios like OpenID Connect and WS-Federation login.</span></span> <span data-ttu-id="ecf3b-117">大部分的 OAuth 登入不會受到影響，因為要求流程的不同之處。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-117">Most OAuth logins aren't affected because of differences in how the request flows.</span></span> <span data-ttu-id="ecf3b-118">新的 `None` 參數會造成與先前 draft 標準 (的用戶端相容性問題，例如 iOS 12) 。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-118">The new `None` parameter causes compatibility problems with clients that implemented the prior draft standard (for example, iOS 12).</span></span> <span data-ttu-id="ecf3b-119">Chrome 80 將包含這些變更。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-119">Chrome 80 will include the changes.</span></span> <span data-ttu-id="ecf3b-120">請參閱 Chrome 產品啟動時間軸的 [SameSite 更新](https://www.chromium.org/updates/same-site) 。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-120">See [SameSite Updates](https://www.chromium.org/updates/same-site) for the Chrome product launch timeline.</span></span>

<span data-ttu-id="ecf3b-121">ASP.NET Core 3.1 已更新為可執行新的 `SameSite` 行為。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-121">ASP.NET Core 3.1 has been updated to implement the new `SameSite` behavior.</span></span> <span data-ttu-id="ecf3b-122">更新會重新定義發出的行為 `SameSiteMode.None` `SameSite=None` ，並新增值 `SameSiteMode.Unspecified` 以省略 `SameSite` 屬性。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-122">The update redefines the behavior of `SameSiteMode.None` to emit `SameSite=None` and adds a new value `SameSiteMode.Unspecified` to omit the `SameSite` attribute.</span></span> <span data-ttu-id="ecf3b-123">所有 cookie Api 現在都會預設為 `Unspecified` ，不過，某些使用 cookie 的元件會針對其案例（例如 OpenID Connect 相互關聯和 nonce cookie）更明確地設定值。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-123">All cookie APIs now default to `Unspecified`, though some components that use cookies set values more specific to their scenarios such as the OpenID Connect correlation and nonce cookies.</span></span>

<span data-ttu-id="ecf3b-124">如需此區域中最近的變更，請參閱 [HTTP：某些 Cookie SameSite 預設值已變更為 None](../../../../docs/core/compatibility/2.2-3.0.md#http-some-cookie-samesite-defaults-changed-to-none)。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-124">For other recent changes in this area, see [HTTP: Some cookie SameSite defaults changed to None](../../../../docs/core/compatibility/2.2-3.0.md#http-some-cookie-samesite-defaults-changed-to-none).</span></span> <span data-ttu-id="ecf3b-125">在 ASP.NET Core 3.0 中，大部分的預設值已從變更 <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> 為 <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (但是仍在使用先前的標準) 。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-125">In ASP.NET Core 3.0, most defaults were changed from <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> to <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (but still using the prior standard).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="ecf3b-126">變更的原因</span><span class="sxs-lookup"><span data-stu-id="ecf3b-126">Reason for change</span></span>

<span data-ttu-id="ecf3b-127">瀏覽器和規格變更，如上述文字所述。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-127">Browser and specification changes as outlined in the preceding text.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ecf3b-128">建議的動作</span><span class="sxs-lookup"><span data-stu-id="ecf3b-128">Recommended action</span></span>

<span data-ttu-id="ecf3b-129">與遠端網站互動的應用程式（例如透過協力廠商登入）必須：</span><span class="sxs-lookup"><span data-stu-id="ecf3b-129">Apps that interact with remote sites, such as through third-party login, need to:</span></span>

* <span data-ttu-id="ecf3b-130">在多個瀏覽器上測試這些案例。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-130">Test those scenarios on multiple browsers.</span></span>
* <span data-ttu-id="ecf3b-131">在 [支援舊版瀏覽器](#support-older-browsers)中，套用討論的 cookie 原則瀏覽器探查緩和措施。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-131">Apply the cookie policy browser sniffing mitigation discussed in [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="ecf3b-132">如需測試和瀏覽器探查的指示，請參閱下一節。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-132">For testing and browser sniffing instructions, see the following section.</span></span>

##### <a name="determine-if-youre-affected"></a><span data-ttu-id="ecf3b-133">判斷您是否受影響</span><span class="sxs-lookup"><span data-stu-id="ecf3b-133">Determine if you're affected</span></span>

<span data-ttu-id="ecf3b-134">使用可加入宣告新行為的用戶端版本，測試您的 web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-134">Test your web app using a client version that can opt into the new behavior.</span></span> <span data-ttu-id="ecf3b-135">Chrome、Firefox 和 Microsoft Edge Chromium 都有新的加入宣告功能旗標，可用於測試。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-135">Chrome, Firefox, and Microsoft Edge Chromium all have new opt-in feature flags that can be used for testing.</span></span> <span data-ttu-id="ecf3b-136">在套用修補程式之後，請確認您的應用程式與較舊的用戶端版本相容（尤其是 Safari）。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-136">Verify that your app is compatible with older client versions after you've applied the patches, especially Safari.</span></span> <span data-ttu-id="ecf3b-137">如需詳細資訊，請參閱 [支援較舊的瀏覽器](#support-older-browsers)。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-137">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="chrome"></a><span data-ttu-id="ecf3b-138">Chrome</span><span class="sxs-lookup"><span data-stu-id="ecf3b-138">Chrome</span></span>

<span data-ttu-id="ecf3b-139">Chrome 78 和更新版本會產生誤導的測試結果。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-139">Chrome 78 and later yield misleading test results.</span></span> <span data-ttu-id="ecf3b-140">這些版本有暫時的緩和措施，讓 cookie 的時間不超過兩分鐘。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-140">Those versions have a temporary mitigation in place and allow cookies less than two minutes old.</span></span> <span data-ttu-id="ecf3b-141">啟用適當的測試旗標之後，Chrome 76 和77會產生更精確的結果。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-141">With the appropriate test flags enabled, Chrome 76 and 77 yield more accurate results.</span></span> <span data-ttu-id="ecf3b-142">若要測試新的行為，請切換 `chrome://flags/#same-site-by-default-cookies` 為 [已啟用]。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-142">To test the new behavior, toggle `chrome://flags/#same-site-by-default-cookies` to enabled.</span></span> <span data-ttu-id="ecf3b-143">系統會報告 Chrome 75 及更早的版本，並出現新的 `None` 設定。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-143">Chrome 75 and earlier are reported to fail with the new `None` setting.</span></span> <span data-ttu-id="ecf3b-144">如需詳細資訊，請參閱 [支援較舊的瀏覽器](#support-older-browsers)。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-144">For more information, see [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="ecf3b-145">Google 未提供較舊的 Chrome 版本。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-145">Google doesn't make older Chrome versions available.</span></span> <span data-ttu-id="ecf3b-146">不過，您可以下載較舊版本的 Chromium，這將足以進行測試。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-146">You can, however, download older versions of Chromium, which will suffice for testing.</span></span> <span data-ttu-id="ecf3b-147">遵循 [下載 Chromium](https://www.chromium.org/getting-involved/download-chromium)中的指示進行。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-147">Follow the instructions at [Download Chromium](https://www.chromium.org/getting-involved/download-chromium).</span></span>

* [<span data-ttu-id="ecf3b-148">Chromium 76 Win64</span><span class="sxs-lookup"><span data-stu-id="ecf3b-148">Chromium 76 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [<span data-ttu-id="ecf3b-149">Chromium 74 Win64</span><span class="sxs-lookup"><span data-stu-id="ecf3b-149">Chromium 74 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a><span data-ttu-id="ecf3b-150">Safari</span><span class="sxs-lookup"><span data-stu-id="ecf3b-150">Safari</span></span>

<span data-ttu-id="ecf3b-151">Safari 12 會嚴格地實行先前的草稿，如果在 cookie 中看到新的值，就會失敗 `None` 。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-151">Safari 12 strictly implemented the prior draft and fails if it sees the new `None` value in cookies.</span></span> <span data-ttu-id="ecf3b-152">您必須透過 [支援舊版流覽](#support-older-browsers)器中顯示的瀏覽器探查程式碼來避免這種情況。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-152">This must be avoided via the browser sniffing code shown in [Support older browsers](#support-older-browsers).</span></span> <span data-ttu-id="ecf3b-153">請務必使用 Microsoft 驗證程式庫 (MSAL) 、Active Directory 驗證程式庫 (ADAL) 或您所使用的任何程式庫，來測試 Safari 12 和13以及以 WebKit 為基礎的 OS 樣式登入。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-153">Ensure you test Safari 12 and 13 as well as WebKit-based, OS-style logins using Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL), or whichever library you're using.</span></span> <span data-ttu-id="ecf3b-154">問題取決於基礎作業系統版本。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-154">The problem is dependent on the underlying OS version.</span></span> <span data-ttu-id="ecf3b-155">已知 OSX Mojave 10.14 和 iOS 12 具有新行為的相容性問題。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-155">OSX Mojave 10.14 and iOS 12 are known to have compatibility problems with the new behavior.</span></span> <span data-ttu-id="ecf3b-156">升級至 OSX Catalina 10.15 或 iOS 13 可修正問題。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-156">Upgrading to OSX Catalina 10.15 or iOS 13 fixes the problem.</span></span> <span data-ttu-id="ecf3b-157">Safari 目前沒有可用於測試新規格行為的加入宣告旗標。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-157">Safari doesn't currently have an opt-in flag for testing the new specification behavior.</span></span>

##### <a name="firefox"></a><span data-ttu-id="ecf3b-158">Firefox</span><span class="sxs-lookup"><span data-stu-id="ecf3b-158">Firefox</span></span>

<span data-ttu-id="ecf3b-159">您可以在頁面上選擇功能旗標，以在68版和更新版本上測試新標準的 Firefox 支援 `about:config` `network.cookie.sameSite.laxByDefault` 。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-159">Firefox support for the new standard can be tested on version 68 and later by opting in on the `about:config` page with the feature flag `network.cookie.sameSite.laxByDefault`.</span></span> <span data-ttu-id="ecf3b-160">較舊版本的 Firefox 未回報任何相容性問題。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-160">No compatibility issues have been reported on older versions of Firefox.</span></span>

##### <a name="microsoft-edge"></a><span data-ttu-id="ecf3b-161">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="ecf3b-161">Microsoft Edge</span></span>

<span data-ttu-id="ecf3b-162">Microsoft Edge 支援舊的 `SameSite` 標準，從44版開始，它沒有與新標準的任何相容性問題。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-162">While Microsoft Edge supports the old `SameSite` standard, as of version 44 it didn't have any compatibility problems with the new standard.</span></span>

##### <a name="microsoft-edge-chromium"></a><span data-ttu-id="ecf3b-163">Microsoft Edge Chromium</span><span class="sxs-lookup"><span data-stu-id="ecf3b-163">Microsoft Edge Chromium</span></span>

<span data-ttu-id="ecf3b-164">功能旗標為 `edge://flags/#same-site-by-default-cookies` 。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-164">The feature flag is `edge://flags/#same-site-by-default-cookies`.</span></span> <span data-ttu-id="ecf3b-165">使用 Microsoft Edge Chromium 78 進行測試時，找不到相容性問題。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-165">No compatibility issues were observed when testing with Microsoft Edge Chromium 78.</span></span>

##### <a name="electron"></a><span data-ttu-id="ecf3b-166">電子</span><span class="sxs-lookup"><span data-stu-id="ecf3b-166">Electron</span></span>

<span data-ttu-id="ecf3b-167">Electron 的版本包括舊版的 Chromium。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-167">Versions of Electron include older versions of Chromium.</span></span> <span data-ttu-id="ecf3b-168">例如，Microsoft 小組所使用的 Electron 版本為 Chromium 66，表示較舊的行為。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-168">For example, the version of Electron used by Microsoft Teams is Chromium 66, which exhibits the older behavior.</span></span> <span data-ttu-id="ecf3b-169">使用您的產品所使用的 Electron 版本來執行您自己的相容性測試。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-169">Perform your own compatibility testing with the version of Electron your product uses.</span></span> <span data-ttu-id="ecf3b-170">如需詳細資訊，請參閱 [支援較舊的瀏覽器](#support-older-browsers)。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-170">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="support-older-browsers"></a><span data-ttu-id="ecf3b-171">支援較舊的瀏覽器</span><span class="sxs-lookup"><span data-stu-id="ecf3b-171">Support older browsers</span></span>

<span data-ttu-id="ecf3b-172">2016 `SameSite` 標準規定將未知值視為 `SameSite=Strict` 值。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-172">The 2016 `SameSite` standard mandated that unknown values be treated as `SameSite=Strict` values.</span></span> <span data-ttu-id="ecf3b-173">因此，當任何支援原始標準的舊版瀏覽器看到 `SameSite` 具有值的屬性時，都可能會中斷 `None` 。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-173">Consequently, any older browsers that support the original standard may break when they see a `SameSite` property with a value of `None`.</span></span> <span data-ttu-id="ecf3b-174">如果 Web 應用程式想要支援這些舊的瀏覽器，則必須執行瀏覽器探查。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-174">Web apps must implement browser sniffing if they intend to support these old browsers.</span></span> <span data-ttu-id="ecf3b-175">ASP.NET Core 不會為您執行瀏覽器探查，因為 `User-Agent` 要求標頭值的高度不穩定，而且每週都有變更。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-175">ASP.NET Core doesn't implement browser sniffing for you because `User-Agent` request header values are highly unstable and change on a weekly basis.</span></span> <span data-ttu-id="ecf3b-176">相反地，cookie 原則中的擴充點可讓您新增 `User-Agent` 特定的邏輯。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-176">Instead, an extension point in the cookie policy allows you to add `User-Agent`-specific logic.</span></span>

<span data-ttu-id="ecf3b-177">在 *Startup.cs*中，新增下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="ecf3b-177">In *Startup.cs*, add the following code:</span></span>

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

##### <a name="opt-out-switches"></a><span data-ttu-id="ecf3b-178">退出參數</span><span class="sxs-lookup"><span data-stu-id="ecf3b-178">Opt-out switches</span></span>

<span data-ttu-id="ecf3b-179">`Microsoft.AspNetCore.SuppressSameSiteNone`相容性參數可讓您暫時退出新的 ASP.NET Core cookie 行為。</span><span class="sxs-lookup"><span data-stu-id="ecf3b-179">The `Microsoft.AspNetCore.SuppressSameSiteNone` compatibility switch enables you to temporarily opt out of the new ASP.NET Core cookie behavior.</span></span> <span data-ttu-id="ecf3b-180">將下列 JSON 新增至您專案中的檔案 *runtimeconfig.template.js* ：</span><span class="sxs-lookup"><span data-stu-id="ecf3b-180">Add the following JSON to a *runtimeconfig.template.json* file in your project:</span></span>

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a><span data-ttu-id="ecf3b-181">其他版本</span><span class="sxs-lookup"><span data-stu-id="ecf3b-181">Other Versions</span></span>

<span data-ttu-id="ecf3b-182">相關 `SameSite` 的修補程式即將推出：</span><span class="sxs-lookup"><span data-stu-id="ecf3b-182">Related `SameSite` patches are forthcoming for:</span></span>

* <span data-ttu-id="ecf3b-183">ASP.NET Core 2.1、2.2 和3。0</span><span class="sxs-lookup"><span data-stu-id="ecf3b-183">ASP.NET Core 2.1, 2.2, and 3.0</span></span>
* <span data-ttu-id="ecf3b-184">`Microsoft.Owin` 4.1</span><span class="sxs-lookup"><span data-stu-id="ecf3b-184">`Microsoft.Owin` 4.1</span></span>
* <span data-ttu-id="ecf3b-185">`System.Web` 適用于 .NET Framework 4.7.2 和更新版本的 () </span><span class="sxs-lookup"><span data-stu-id="ecf3b-185">`System.Web` (for .NET Framework 4.7.2 and later)</span></span>

#### <a name="category"></a><span data-ttu-id="ecf3b-186">類別</span><span class="sxs-lookup"><span data-stu-id="ecf3b-186">Category</span></span>

<span data-ttu-id="ecf3b-187">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ecf3b-187">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ecf3b-188">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="ecf3b-188">Affected APIs</span></span>

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
