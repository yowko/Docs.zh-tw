---
ms.openlocfilehash: 3cc07eef109b9096bc5a5fbcd1ea098a23b2155f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78968356"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a><span data-ttu-id="a28cb-101">HTTP： 瀏覽器同網站更改影響身份驗證</span><span class="sxs-lookup"><span data-stu-id="a28cb-101">HTTP: Browser SameSite changes impact authentication</span></span>

<span data-ttu-id="a28cb-102">某些瀏覽器（如 Chrome 和 Firefox）對其`SameSite`Cookie 的實現進行了重大更改。</span><span class="sxs-lookup"><span data-stu-id="a28cb-102">Some browsers, such as Chrome and Firefox, made breaking changes to their implementations of `SameSite` for cookies.</span></span> <span data-ttu-id="a28cb-103">這些更改會影響遠端身份驗證方案，如 OpenID 連接和 WS-聯合，它們必須通過發送`SameSite=None`退出宣告。</span><span class="sxs-lookup"><span data-stu-id="a28cb-103">The changes impact remote authentication scenarios, such as OpenID Connect and WS-Federation, which must opt out by sending `SameSite=None`.</span></span> <span data-ttu-id="a28cb-104">但是，`SameSite=None`在 iOS 12 和其他瀏覽器的一些舊版本上會中斷。</span><span class="sxs-lookup"><span data-stu-id="a28cb-104">However, `SameSite=None` breaks on iOS 12 and some older versions of other browsers.</span></span> <span data-ttu-id="a28cb-105">該應用程式需要嗅探這些版本，並省略`SameSite`。</span><span class="sxs-lookup"><span data-stu-id="a28cb-105">The app needs to sniff these versions and omit `SameSite`.</span></span>

<span data-ttu-id="a28cb-106">有關此問題的討論，請參閱[dotnet/aspnetcore_14996](https://github.com/dotnet/aspnetcore/issues/14996)。</span><span class="sxs-lookup"><span data-stu-id="a28cb-106">For discussion on this issue, see [dotnet/aspnetcore#14996](https://github.com/dotnet/aspnetcore/issues/14996).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="a28cb-107">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="a28cb-107">Version introduced</span></span>

<span data-ttu-id="a28cb-108">3.1 預覽 1</span><span class="sxs-lookup"><span data-stu-id="a28cb-108">3.1 Preview 1</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="a28cb-109">舊的行為</span><span class="sxs-lookup"><span data-stu-id="a28cb-109">Old behavior</span></span>

<span data-ttu-id="a28cb-110">`SameSite`是 2016 年 HTTP Cookie 標準擴展草案。</span><span class="sxs-lookup"><span data-stu-id="a28cb-110">`SameSite` is a 2016 draft standard extension to HTTP cookies.</span></span> <span data-ttu-id="a28cb-111">它旨在緩解跨網站請求偽造 （CSRF）。</span><span class="sxs-lookup"><span data-stu-id="a28cb-111">It's intended to mitigate Cross-Site Request Forgery (CSRF).</span></span> <span data-ttu-id="a28cb-112">這最初設計為伺服器通過添加新參數而選擇的功能。</span><span class="sxs-lookup"><span data-stu-id="a28cb-112">This was originally designed as a feature the servers would opt into by adding the new parameters.</span></span> <span data-ttu-id="a28cb-113">ASP.NET 核心 2.0 添加了`SameSite`對 的初始支援。</span><span class="sxs-lookup"><span data-stu-id="a28cb-113">ASP.NET Core 2.0 added initial support for `SameSite`.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="a28cb-114">新的行為</span><span class="sxs-lookup"><span data-stu-id="a28cb-114">New behavior</span></span>

<span data-ttu-id="a28cb-115">谷歌提出了一個不向後相容的新標準草案。</span><span class="sxs-lookup"><span data-stu-id="a28cb-115">Google proposed a new draft standard that isn't backwards compatible.</span></span> <span data-ttu-id="a28cb-116">標準將預設模式更改為`Lax`，並添加新條目`None`以退出宣告。`Lax`足以滿足大多數應用程式 Cookie;但是，它打破了跨網站方案，如 OpenID 連接和 WS-聯合登錄。</span><span class="sxs-lookup"><span data-stu-id="a28cb-116">The standard changes the default mode to `Lax` and adds a new entry `None` to opt out. `Lax` suffices for most app cookies; however, it breaks cross-site scenarios like OpenID Connect and WS-Federation login.</span></span> <span data-ttu-id="a28cb-117">大多數 OAuth 登錄不會受到影響，因為請求流的方式不同。</span><span class="sxs-lookup"><span data-stu-id="a28cb-117">Most OAuth logins aren't affected because of differences in how the request flows.</span></span> <span data-ttu-id="a28cb-118">新`None`參數導致與實現先前標準草案的用戶端的相容性問題（例如 iOS 12）。</span><span class="sxs-lookup"><span data-stu-id="a28cb-118">The new `None` parameter causes compatibility problems with clients that implemented the prior draft standard (for example, iOS 12).</span></span> <span data-ttu-id="a28cb-119">Chrome 80 將包括更改。</span><span class="sxs-lookup"><span data-stu-id="a28cb-119">Chrome 80 will include the changes.</span></span> <span data-ttu-id="a28cb-120">有關 Chrome 產品發佈時程表，請參閱[同一網站更新](https://www.chromium.org/updates/same-site)。</span><span class="sxs-lookup"><span data-stu-id="a28cb-120">See [SameSite Updates](https://www.chromium.org/updates/same-site) for the Chrome product launch timeline.</span></span>

<span data-ttu-id="a28cb-121">ASP.NET核心 3.1 已更新以實現新`SameSite`行為。</span><span class="sxs-lookup"><span data-stu-id="a28cb-121">ASP.NET Core 3.1 has been updated to implement the new `SameSite` behavior.</span></span> <span data-ttu-id="a28cb-122">`SameSiteMode.None`更新重新定義了發出`SameSite=None`的行為，並添加了一個新值`SameSiteMode.Unspecified`來省略屬性。 `SameSite`</span><span class="sxs-lookup"><span data-stu-id="a28cb-122">The update redefines the behavior of `SameSiteMode.None` to emit `SameSite=None` and adds a new value `SameSiteMode.Unspecified` to omit the `SameSite` attribute.</span></span> <span data-ttu-id="a28cb-123">所有 Cookie API 現在都`Unspecified`預設為 ，儘管某些使用 Cookie 的元件會設置更特定于其方案的值，如 OpenID 連接關聯和 nonce Cookie。</span><span class="sxs-lookup"><span data-stu-id="a28cb-123">All cookie APIs now default to `Unspecified`, though some components that use cookies set values more specific to their scenarios such as the OpenID Connect correlation and nonce cookies.</span></span>

<span data-ttu-id="a28cb-124">有關此區域中其他最近更改，請參閱[HTTP：某些 Cookie SameSite 預設值更改為"無](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none)"。</span><span class="sxs-lookup"><span data-stu-id="a28cb-124">For other recent changes in this area, see [HTTP: Some cookie SameSite defaults changed to None](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none).</span></span> <span data-ttu-id="a28cb-125">在 ASP.NET 酷 3.0 中，大多數<xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType>預設值<xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType>已更改為 （但仍使用以前的標準）。</span><span class="sxs-lookup"><span data-stu-id="a28cb-125">In ASP.NET Core 3.0, most defaults were changed from <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> to <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (but still using the prior standard).</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="a28cb-126">更改原因</span><span class="sxs-lookup"><span data-stu-id="a28cb-126">Reason for change</span></span>

<span data-ttu-id="a28cb-127">瀏覽器和規範更改，如前面的文本中概述。</span><span class="sxs-lookup"><span data-stu-id="a28cb-127">Browser and specification changes as outlined in the preceding text.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="a28cb-128">建議的動作</span><span class="sxs-lookup"><span data-stu-id="a28cb-128">Recommended action</span></span>

<span data-ttu-id="a28cb-129">與遠端站台交互的應用（如通過協力廠商登錄）需要：</span><span class="sxs-lookup"><span data-stu-id="a28cb-129">Apps that interact with remote sites, such as through third-party login, need to:</span></span>

* <span data-ttu-id="a28cb-130">在多個瀏覽器上測試這些方案。</span><span class="sxs-lookup"><span data-stu-id="a28cb-130">Test those scenarios on multiple browsers.</span></span>
* <span data-ttu-id="a28cb-131">應用[支援舊瀏覽器](#support-older-browsers)中討論的 Cookie 策略瀏覽器嗅探緩解。</span><span class="sxs-lookup"><span data-stu-id="a28cb-131">Apply the cookie policy browser sniffing mitigation discussed in [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="a28cb-132">有關測試和瀏覽器嗅探說明，請參閱以下部分。</span><span class="sxs-lookup"><span data-stu-id="a28cb-132">For testing and browser sniffing instructions, see the following section.</span></span>

##### <a name="determine-if-youre-affected"></a><span data-ttu-id="a28cb-133">確定您是否受到影響</span><span class="sxs-lookup"><span data-stu-id="a28cb-133">Determine if you're affected</span></span>

<span data-ttu-id="a28cb-134">使用可以加入宣告新行為的用戶端版本測試 Web 應用。</span><span class="sxs-lookup"><span data-stu-id="a28cb-134">Test your web app using a client version that can opt into the new behavior.</span></span> <span data-ttu-id="a28cb-135">Chrome、Firefox 和 Microsoft 邊緣鉻都具有可用於測試的新加入宣告功能標誌。</span><span class="sxs-lookup"><span data-stu-id="a28cb-135">Chrome, Firefox, and Microsoft Edge Chromium all have new opt-in feature flags that can be used for testing.</span></span> <span data-ttu-id="a28cb-136">應用修補程式（尤其是 Safari）後，驗證你的應用是否與較舊的用戶端版本相容。</span><span class="sxs-lookup"><span data-stu-id="a28cb-136">Verify that your app is compatible with older client versions after you've applied the patches, especially Safari.</span></span> <span data-ttu-id="a28cb-137">有關詳細資訊，請參閱[支援較舊的瀏覽器](#support-older-browsers)。</span><span class="sxs-lookup"><span data-stu-id="a28cb-137">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="chrome"></a><span data-ttu-id="a28cb-138">Chrome</span><span class="sxs-lookup"><span data-stu-id="a28cb-138">Chrome</span></span>

<span data-ttu-id="a28cb-139">Chrome 78 及更高版本會產生誤導性測試結果。</span><span class="sxs-lookup"><span data-stu-id="a28cb-139">Chrome 78 and later yield misleading test results.</span></span> <span data-ttu-id="a28cb-140">這些版本有一個臨時緩解到位，並允許餅乾不到兩分鐘。</span><span class="sxs-lookup"><span data-stu-id="a28cb-140">Those versions have a temporary mitigation in place and allow cookies less than two minutes old.</span></span> <span data-ttu-id="a28cb-141">啟用了相應的測試標誌後，Chrome 76 和 77 可生成更準確的結果。</span><span class="sxs-lookup"><span data-stu-id="a28cb-141">With the appropriate test flags enabled, Chrome 76 and 77 yield more accurate results.</span></span> <span data-ttu-id="a28cb-142">要測試新行為，要切換`chrome://flags/#same-site-by-default-cookies`為已啟用。</span><span class="sxs-lookup"><span data-stu-id="a28cb-142">To test the new behavior, toggle `chrome://flags/#same-site-by-default-cookies` to enabled.</span></span> <span data-ttu-id="a28cb-143">據報導，Chrome 75 和更早版本的新`None`設置出現故障。</span><span class="sxs-lookup"><span data-stu-id="a28cb-143">Chrome 75 and earlier are reported to fail with the new `None` setting.</span></span> <span data-ttu-id="a28cb-144">有關詳細資訊，請參閱[支援較舊的瀏覽器](#support-older-browsers)。</span><span class="sxs-lookup"><span data-stu-id="a28cb-144">For more information, see [Support older browsers](#support-older-browsers).</span></span>

<span data-ttu-id="a28cb-145">谷歌沒有提供較舊的Chrome版本。</span><span class="sxs-lookup"><span data-stu-id="a28cb-145">Google doesn't make older Chrome versions available.</span></span> <span data-ttu-id="a28cb-146">但是，您可以下載舊版本的鉻，這足以進行測試。</span><span class="sxs-lookup"><span data-stu-id="a28cb-146">You can, however, download older versions of Chromium, which will suffice for testing.</span></span> <span data-ttu-id="a28cb-147">按照[下載鉻](https://www.chromium.org/getting-involved/download-chromium)的說明。</span><span class="sxs-lookup"><span data-stu-id="a28cb-147">Follow the instructions at [Download Chromium](https://www.chromium.org/getting-involved/download-chromium).</span></span>

* [<span data-ttu-id="a28cb-148">鉻 76 Win64</span><span class="sxs-lookup"><span data-stu-id="a28cb-148">Chromium 76 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [<span data-ttu-id="a28cb-149">鉻 74 Win64</span><span class="sxs-lookup"><span data-stu-id="a28cb-149">Chromium 74 Win64</span></span>](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a><span data-ttu-id="a28cb-150">Safari</span><span class="sxs-lookup"><span data-stu-id="a28cb-150">Safari</span></span>

<span data-ttu-id="a28cb-151">Safari 12 嚴格執行以前的草稿，如果看到 Cookie 中`None`的新價值，則失敗。</span><span class="sxs-lookup"><span data-stu-id="a28cb-151">Safari 12 strictly implemented the prior draft and fails if it sees the new `None` value in cookies.</span></span> <span data-ttu-id="a28cb-152">這必須通過瀏覽器嗅探代碼在[支援舊瀏覽器](#support-older-browsers)中顯示的避免。</span><span class="sxs-lookup"><span data-stu-id="a28cb-152">This must be avoided via the browser sniffing code shown in [Support older browsers](#support-older-browsers).</span></span> <span data-ttu-id="a28cb-153">請確保使用 Microsoft 身份驗證庫 （MSAL）、活動目錄身份驗證庫 （ADAL） 或您正在使用哪個庫測試 Safari 12 和 13 以及基於 WebKit 的作業系統樣式登錄。</span><span class="sxs-lookup"><span data-stu-id="a28cb-153">Ensure you test Safari 12 and 13 as well as WebKit-based, OS-style logins using Microsoft Authentication Library (MSAL), Active Directory Authentication Library (ADAL), or whichever library you're using.</span></span> <span data-ttu-id="a28cb-154">問題取決於基礎作業系統版本。</span><span class="sxs-lookup"><span data-stu-id="a28cb-154">The problem is dependent on the underlying OS version.</span></span> <span data-ttu-id="a28cb-155">OSX Mojave 10.14 和 iOS 12 已知與新行為存在相容性問題。</span><span class="sxs-lookup"><span data-stu-id="a28cb-155">OSX Mojave 10.14 and iOS 12 are known to have compatibility problems with the new behavior.</span></span> <span data-ttu-id="a28cb-156">升級到 OSX Catalina 10.15 或 iOS 13 解決了問題。</span><span class="sxs-lookup"><span data-stu-id="a28cb-156">Upgrading to OSX Catalina 10.15 or iOS 13 fixes the problem.</span></span> <span data-ttu-id="a28cb-157">Safari 當前沒有用於測試新規範行為的加入標誌。</span><span class="sxs-lookup"><span data-stu-id="a28cb-157">Safari doesn't currently have an opt-in flag for testing the new specification behavior.</span></span>

##### <a name="firefox"></a><span data-ttu-id="a28cb-158">Firefox</span><span class="sxs-lookup"><span data-stu-id="a28cb-158">Firefox</span></span>

<span data-ttu-id="a28cb-159">Firefox 支援新標準可以在版本 68 上進行測試，稍後在帶有功能標誌`about:config``network.cookie.sameSite.laxByDefault`的頁面上加入宣告。</span><span class="sxs-lookup"><span data-stu-id="a28cb-159">Firefox support for the new standard can be tested on version 68 and later by opting in on the `about:config` page with the feature flag `network.cookie.sameSite.laxByDefault`.</span></span> <span data-ttu-id="a28cb-160">沒有報告舊版本的 Firefox 的相容性問題。</span><span class="sxs-lookup"><span data-stu-id="a28cb-160">No compatibility issues have been reported on older versions of Firefox.</span></span>

##### <a name="microsoft-edge"></a><span data-ttu-id="a28cb-161">Microsoft Edge</span><span class="sxs-lookup"><span data-stu-id="a28cb-161">Microsoft Edge</span></span>

<span data-ttu-id="a28cb-162">雖然 Microsoft Edge`SameSite`支援舊標準，但截至版本 44，它與新標準沒有任何相容性問題。</span><span class="sxs-lookup"><span data-stu-id="a28cb-162">While Microsoft Edge supports the old `SameSite` standard, as of version 44 it didn't have any compatibility problems with the new standard.</span></span>

##### <a name="microsoft-edge-chromium"></a><span data-ttu-id="a28cb-163">微軟邊緣鉻</span><span class="sxs-lookup"><span data-stu-id="a28cb-163">Microsoft Edge Chromium</span></span>

<span data-ttu-id="a28cb-164">要素標誌為`edge://flags/#same-site-by-default-cookies`。</span><span class="sxs-lookup"><span data-stu-id="a28cb-164">The feature flag is `edge://flags/#same-site-by-default-cookies`.</span></span> <span data-ttu-id="a28cb-165">使用 Microsoft 邊緣鉻 78 進行測試時未觀察到相容性問題。</span><span class="sxs-lookup"><span data-stu-id="a28cb-165">No compatibility issues were observed when testing with Microsoft Edge Chromium 78.</span></span>

##### <a name="electron"></a><span data-ttu-id="a28cb-166">電子</span><span class="sxs-lookup"><span data-stu-id="a28cb-166">Electron</span></span>

<span data-ttu-id="a28cb-167">電子版本包括舊版本的鉻。</span><span class="sxs-lookup"><span data-stu-id="a28cb-167">Versions of Electron include older versions of Chromium.</span></span> <span data-ttu-id="a28cb-168">例如，微軟團隊使用的電子版本是鉻66，它顯示了舊的行為。</span><span class="sxs-lookup"><span data-stu-id="a28cb-168">For example, the version of Electron used by Microsoft Teams is Chromium 66, which exhibits the older behavior.</span></span> <span data-ttu-id="a28cb-169">使用產品使用的 Electron 版本執行您自己的相容性測試。</span><span class="sxs-lookup"><span data-stu-id="a28cb-169">Perform your own compatibility testing with the version of Electron your product uses.</span></span> <span data-ttu-id="a28cb-170">有關詳細資訊，請參閱[支援較舊的瀏覽器](#support-older-browsers)。</span><span class="sxs-lookup"><span data-stu-id="a28cb-170">For more information, see [Support older browsers](#support-older-browsers).</span></span>

##### <a name="support-older-browsers"></a><span data-ttu-id="a28cb-171">支援較舊的瀏覽器</span><span class="sxs-lookup"><span data-stu-id="a28cb-171">Support older browsers</span></span>

<span data-ttu-id="a28cb-172">2016`SameSite`年標準規定，未知值應視為`SameSite=Strict`值。</span><span class="sxs-lookup"><span data-stu-id="a28cb-172">The 2016 `SameSite` standard mandated that unknown values be treated as `SameSite=Strict` values.</span></span> <span data-ttu-id="a28cb-173">因此，任何支援原始標準的較舊的瀏覽器在看到`SameSite`值 為 的屬性`None`時可能會中斷。</span><span class="sxs-lookup"><span data-stu-id="a28cb-173">Consequently, any older browsers that support the original standard may break when they see a `SameSite` property with a value of `None`.</span></span> <span data-ttu-id="a28cb-174">如果 Web 應用打算支援這些舊瀏覽器，則必須實現瀏覽器嗅探。</span><span class="sxs-lookup"><span data-stu-id="a28cb-174">Web apps must implement browser sniffing if they intend to support these old browsers.</span></span> <span data-ttu-id="a28cb-175">ASP.NET Core 不會為您實現瀏覽器嗅探，因為`User-Agent`請求標頭值極不穩定，並且每週更改一次。</span><span class="sxs-lookup"><span data-stu-id="a28cb-175">ASP.NET Core doesn't implement browser sniffing for you because `User-Agent` request header values are highly unstable and change on a weekly basis.</span></span> <span data-ttu-id="a28cb-176">相反，Cookie 策略中的擴充點允許您添加`User-Agent`特定于的邏輯。</span><span class="sxs-lookup"><span data-stu-id="a28cb-176">Instead, an extension point in the cookie policy allows you to add `User-Agent`-specific logic.</span></span>

<span data-ttu-id="a28cb-177">在*Startup.cs*中，添加以下代碼：</span><span class="sxs-lookup"><span data-stu-id="a28cb-177">In *Startup.cs*, add the following code:</span></span>

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

##### <a name="opt-out-switches"></a><span data-ttu-id="a28cb-178">退出宣告開關</span><span class="sxs-lookup"><span data-stu-id="a28cb-178">Opt-out switches</span></span>

<span data-ttu-id="a28cb-179">相容性`Microsoft.AspNetCore.SuppressSameSiteNone`開關使您能夠暫時退出宣告新的ASP.NET核心 Cookie 行為。</span><span class="sxs-lookup"><span data-stu-id="a28cb-179">The `Microsoft.AspNetCore.SuppressSameSiteNone` compatibility switch enables you to temporarily opt out of the new ASP.NET Core cookie behavior.</span></span> <span data-ttu-id="a28cb-180">將以下 JSON 添加到專案中的*運行時 config.template.json*檔中：</span><span class="sxs-lookup"><span data-stu-id="a28cb-180">Add the following JSON to a *runtimeconfig.template.json* file in your project:</span></span>

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a><span data-ttu-id="a28cb-181">其他版本</span><span class="sxs-lookup"><span data-stu-id="a28cb-181">Other Versions</span></span>

<span data-ttu-id="a28cb-182">相關`SameSite`修補程式即將用於：</span><span class="sxs-lookup"><span data-stu-id="a28cb-182">Related `SameSite` patches are forthcoming for:</span></span>

* <span data-ttu-id="a28cb-183">ASP.NET核心 2.1、2.2 和 3.0</span><span class="sxs-lookup"><span data-stu-id="a28cb-183">ASP.NET Core 2.1, 2.2, and 3.0</span></span>
* <span data-ttu-id="a28cb-184">`Microsoft.Owin`4.1</span><span class="sxs-lookup"><span data-stu-id="a28cb-184">`Microsoft.Owin` 4.1</span></span>
* <span data-ttu-id="a28cb-185">`System.Web`（對於 .NET 框架 4.7.2 及更高版本）</span><span class="sxs-lookup"><span data-stu-id="a28cb-185">`System.Web` (for .NET Framework 4.7.2 and later)</span></span>

#### <a name="category"></a><span data-ttu-id="a28cb-186">類別</span><span class="sxs-lookup"><span data-stu-id="a28cb-186">Category</span></span>

<span data-ttu-id="a28cb-187">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a28cb-187">ASP.NET</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="a28cb-188">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="a28cb-188">Affected APIs</span></span>

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
