---
ms.openlocfilehash: 8b6d334677991382d235fd53cd3c98e3a77d650d
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90539575"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a>HTTP：瀏覽器 SameSite 變更會影響驗證

某些瀏覽器（例如 Chrome 和 Firefox）會對其 cookie 的執行進行中斷性變更 `SameSite` 。 這些變更會影響遠端驗證案例，例如 OpenID Connect 和 WS-同盟，必須透過傳送來退出 `SameSite=None` 。 但是，會 `SameSite=None` 在 iOS 12 和某些舊版的其他瀏覽器上中斷。 應用程式必須探查這些版本並省略 `SameSite` 。

如需此問題的討論，請參閱 [dotnet/aspnetcore # 14996](https://github.com/dotnet/aspnetcore/issues/14996)。

#### <a name="version-introduced"></a>引進的版本

3.1 Preview 1

#### <a name="old-behavior"></a>舊的行為

`SameSite` 是 HTTP cookie 的2016草稿標準延伸模組。 其目的是要降低跨網站偽造要求 (CSRF) 。 這原本是設計為伺服器在加入新參數時加入宣告的功能。 ASP.NET Core 2.0 已新增的初始支援 `SameSite` 。

#### <a name="new-behavior"></a>新的行為

Google 提議新的草稿標準，但無法回溯相容。 標準會將預設模式變更為 `Lax` ，並加入新的專案 `None` 以退出宣告。 `Lax` 尾碼大部分的應用程式 cookie，不過它會破壞跨網站案例，例如 OpenID Connect 和 WS-同盟登入。 大部分的 OAuth 登入不會受到影響，因為要求流程的不同之處。 新的 `None` 參數會造成與先前 draft 標準 (的用戶端相容性問題，例如 iOS 12) 。 Chrome 80 將包含這些變更。 請參閱 Chrome 產品啟動時間軸的 [SameSite 更新](https://www.chromium.org/updates/same-site) 。

ASP.NET Core 3.1 已更新為可執行新的 `SameSite` 行為。 更新會重新定義發出的行為 `SameSiteMode.None` `SameSite=None` ，並新增值 `SameSiteMode.Unspecified` 以省略 `SameSite` 屬性。 所有 cookie Api 現在都會預設為 `Unspecified` ，不過，某些使用 cookie 的元件會針對其案例（例如 OpenID Connect 相互關聯和 nonce cookie）更明確地設定值。

如需此區域中最近的變更，請參閱 [HTTP：某些 Cookie SameSite 預設值已變更為 None](../../../../docs/core/compatibility/2.2-3.0.md#http-some-cookie-samesite-defaults-changed-to-none)。 在 ASP.NET Core 3.0 中，大部分的預設值已從變更 <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> 為 <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> (但是仍在使用先前的標準) 。

#### <a name="reason-for-change"></a>變更的原因

瀏覽器和規格變更，如上述文字所述。

#### <a name="recommended-action"></a>建議的動作

與遠端網站互動的應用程式（例如透過協力廠商登入）必須：

* 在多個瀏覽器上測試這些案例。
* 在 [支援舊版瀏覽器](#support-older-browsers)中，套用討論的 cookie 原則瀏覽器探查緩和措施。

如需測試和瀏覽器探查的指示，請參閱下一節。

##### <a name="determine-if-youre-affected"></a>判斷您是否受影響

使用可加入宣告新行為的用戶端版本，測試您的 web 應用程式。 Chrome、Firefox 和 Microsoft Edge Chromium 都有新的加入宣告功能旗標，可用於測試。 在套用修補程式之後，請確認您的應用程式與較舊的用戶端版本相容（尤其是 Safari）。 如需詳細資訊，請參閱 [支援較舊的瀏覽器](#support-older-browsers)。

##### <a name="chrome"></a>Chrome

Chrome 78 和更新版本會產生誤導的測試結果。 這些版本有暫時的緩和措施，讓 cookie 的時間不超過兩分鐘。 啟用適當的測試旗標之後，Chrome 76 和77會產生更精確的結果。 若要測試新的行為，請切換 `chrome://flags/#same-site-by-default-cookies` 為 [已啟用]。 系統會報告 Chrome 75 及更早的版本，並出現新的 `None` 設定。 如需詳細資訊，請參閱 [支援較舊的瀏覽器](#support-older-browsers)。

Google 未提供較舊的 Chrome 版本。 不過，您可以下載較舊版本的 Chromium，這將足以進行測試。 遵循 [下載 Chromium](https://www.chromium.org/getting-involved/download-chromium)中的指示進行。

* [Chromium 76 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [Chromium 74 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a>Safari

Safari 12 會嚴格地實行先前的草稿，如果在 cookie 中看到新的值，就會失敗 `None` 。 您必須透過 [支援舊版流覽](#support-older-browsers)器中顯示的瀏覽器探查程式碼來避免這種情況。 請務必使用 Microsoft 驗證程式庫 (MSAL) 、Active Directory 驗證程式庫 (ADAL) 或您所使用的任何程式庫，來測試 Safari 12 和13以及以 WebKit 為基礎的 OS 樣式登入。 問題取決於基礎作業系統版本。 已知 OSX Mojave 10.14 和 iOS 12 具有新行為的相容性問題。 升級至 OSX Catalina 10.15 或 iOS 13 可修正問題。 Safari 目前沒有可用於測試新規格行為的加入宣告旗標。

##### <a name="firefox"></a>Firefox

您可以在頁面上選擇功能旗標，以在68版和更新版本上測試新標準的 Firefox 支援 `about:config` `network.cookie.sameSite.laxByDefault` 。 較舊版本的 Firefox 未回報任何相容性問題。

##### <a name="microsoft-edge"></a>Microsoft Edge

Microsoft Edge 支援舊的 `SameSite` 標準，從44版開始，它沒有與新標準的任何相容性問題。

##### <a name="microsoft-edge-chromium"></a>Microsoft Edge Chromium

功能旗標為 `edge://flags/#same-site-by-default-cookies` 。 使用 Microsoft Edge Chromium 78 進行測試時，找不到相容性問題。

##### <a name="electron"></a>電子

Electron 的版本包括舊版的 Chromium。 例如，Microsoft 小組所使用的 Electron 版本為 Chromium 66，表示較舊的行為。 使用您的產品所使用的 Electron 版本來執行您自己的相容性測試。 如需詳細資訊，請參閱 [支援較舊的瀏覽器](#support-older-browsers)。

##### <a name="support-older-browsers"></a>支援較舊的瀏覽器

2016 `SameSite` 標準規定將未知值視為 `SameSite=Strict` 值。 因此，當任何支援原始標準的舊版瀏覽器看到 `SameSite` 具有值的屬性時，都可能會中斷 `None` 。 如果 Web 應用程式想要支援這些舊的瀏覽器，則必須執行瀏覽器探查。 ASP.NET Core 不會為您執行瀏覽器探查，因為 `User-Agent` 要求標頭值的高度不穩定，而且每週都有變更。 相反地，cookie 原則中的擴充點可讓您新增 `User-Agent` 特定的邏輯。

在 *Startup.cs*中，新增下列程式碼：

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

##### <a name="opt-out-switches"></a>退出參數

`Microsoft.AspNetCore.SuppressSameSiteNone`相容性參數可讓您暫時退出新的 ASP.NET Core cookie 行為。 將下列 JSON 新增至您專案中的檔案 *runtimeconfig.template.js* ：

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a>其他版本

相關 `SameSite` 的修補程式即將推出：

* ASP.NET Core 2.1、2.2 和3。0
* `Microsoft.Owin` 4.1
* `System.Web` 適用于 .NET Framework 4.7.2 和更新版本的 () 

#### <a name="category"></a>類別

ASP.NET

#### <a name="affected-apis"></a>受影響的 API

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
