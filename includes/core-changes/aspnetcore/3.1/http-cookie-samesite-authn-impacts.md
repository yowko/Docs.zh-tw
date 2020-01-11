---
ms.openlocfilehash: 02602c70689a6d2729e03d3d7230cda5ae7a4994
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901735"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a>HTTP：瀏覽器 SameSite 變更影響驗證

某些瀏覽器（例如 Chrome 和 Firefox）對其 cookie 的 `SameSite` 進行了重大變更。 這些變更會影響遠端驗證案例，例如 OpenID Connect 和 WS-同盟，這必須藉由傳送 `SameSite=None`來退出宣告。 不過，`SameSite=None` 會在 iOS 12 和一些較舊版本的其他瀏覽器上中斷。 應用程式必須探查這些版本，並省略 `SameSite`。

如需此問題的討論，請參閱[dotnet/aspnetcore # 14996](https://github.com/dotnet/aspnetcore/issues/14996)。

#### <a name="version-introduced"></a>引進的版本

3.1 Preview 1

#### <a name="old-behavior"></a>舊的行為

`SameSite` 是 HTTP cookie 的2016草稿標準延伸模組。 其目的是要減少跨網站偽造要求（CSRF）。 這原本是設計成伺服器透過新增新參數來加入宣告的功能。 ASP.NET Core 2.0 已新增 `SameSite`的初始支援。

#### <a name="new-behavior"></a>新的行為

Google 提議的新草稿標準不相容。 標準會將預設模式變更為 `Lax`，並加入 `None` 退出宣告的新專案。針對大部分的應用程式 cookie `Lax` 尾碼;不過，它會中斷類似 OpenID Connect 和 WS-同盟登入的跨網站案例。 大部分的 OAuth 登入不會受到影響，因為要求的流動方式有所差異。 新的 `None` 參數會導致用戶端的相容性問題，而此標準會實作為先前的草稿標準（例如 iOS 12）。 Chrome 80 將包含變更。 請參閱 Chrome 產品啟動時程表的[SameSite 更新](https://www.chromium.org/updates/same-site)。

ASP.NET Core 3.1 已更新，可執行新的 `SameSite` 行為。 更新會重新定義發出 `SameSite=None` `SameSiteMode.None` 的行為，並加入新的值 `SameSiteMode.Unspecified` 以省略 `SameSite` 屬性。 所有的 cookie Api 現在都預設為 `Unspecified`，不過，某些使用 cookie 的元件會針對其案例（例如 OpenID Connect 相互關聯和 nonce cookie）設定更具體的值。

如需此區域中其他最近的變更，請參閱[HTTP：有些 Cookie SameSite 預設值已變更為 None](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none)。 在 ASP.NET Core 3.0 中，大部分的預設值已從 <xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType> 變更為 <xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType> （但仍使用先前的標準）。

#### <a name="reason-for-change"></a>變更的原因

瀏覽器和規格的變更如先前文字中所述。

#### <a name="recommended-action"></a>建議的動作

與遠端網站互動的應用程式（例如透過協力廠商登入）必須：

* 在多個瀏覽器上測試這些案例。
* 套用[支援舊版瀏覽器](#support-older-browsers)中所討論的 cookie 原則瀏覽器探查緩和措施。

如需測試和瀏覽器探查的指示，請參閱下一節。

##### <a name="determine-if-youre-affected"></a>判斷您是否受影響

使用可選擇新行為的用戶端版本，測試您的 web 應用程式。 Chrome、Firefox 和 Microsoft Edge Chromium 都有新的加入宣告功能旗標，可用於測試。 在套用修補程式之後，請確認您的應用程式與舊版用戶端版本相容，特別是 Safari。 如需詳細資訊，請參閱[支援舊版瀏覽器](#support-older-browsers)。

##### <a name="chrome"></a>Chrome

Chrome 78 和更新版本會產生誤導的測試結果。 這些版本具有暫時的緩和措施，並允許不到兩分鐘的 cookie。 啟用適當的測試旗標後，Chrome 76 和77會產生更精確的結果。 若要測試新的行為，請將 `chrome://flags/#same-site-by-default-cookies` 切換為 [已啟用]。 Chrome 75 和更早版本會回報為失敗，並出現新的 `None` 設定。 如需詳細資訊，請參閱[支援舊版瀏覽器](#support-older-browsers)。

Google 不會提供舊版的 Chrome 版本。 不過，您可以下載較舊版本的 Chromium，這樣就足以進行測試。 遵循[下載 Chromium](https://www.chromium.org/getting-involved/download-chromium)中的指示進行。

* [Chromium 76 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [Chromium 74 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a>Safari

Safari 12 已嚴格執行先前的草稿，如果它在 cookie 中看到新的 `None` 值，則會失敗。 這必須透過[支援舊版流覽](#support-older-browsers)器中顯示的瀏覽器探查程式碼來避免。 請確定您使用 Microsoft Authentication Library （MSAL）、Active Directory 驗證程式庫（ADAL）或您使用的任何程式庫，測試 Safari 12 和13以及 WebKit 型 OS 樣式的登入。 問題取決於基礎作業系統版本。 已知 OSX Mojave 10.14 和 iOS 12 與新行為有相容性問題。 升級至 OSX Catalina 10.15 或 iOS 13 會修正問題。 Safari 目前沒有加入宣告旗標來測試新的規格行為。

##### <a name="firefox"></a>Firefox

新標準的 Firefox 支援可以在68版和更新版本上進行測試，方法是在 [`about:config`] 頁面上選擇 [`network.cookie.sameSite.laxByDefault`] 功能旗標。 舊版 Firefox 未回報任何相容性問題。

##### <a name="microsoft-edge"></a>Microsoft Edge

雖然 Microsoft Edge 支援舊版的 `SameSite` 標準，但從44版起，新的標準不會有任何相容性問題。

##### <a name="microsoft-edge-chromium"></a>Microsoft Edge Chromium

功能旗標為 `edge://flags/#same-site-by-default-cookies`。 使用 Microsoft Edge Chromium 78 進行測試時，未發現相容性問題。

##### <a name="electron"></a>Electron

Electron 的版本包含舊版的 Chromium。 例如，Microsoft 團隊所使用的 Electron 版本是 Chromium 66，這會展現較舊的行為。 使用您的產品所使用的 Electron 版本，執行您自己的相容性測試。 如需詳細資訊，請參閱[支援舊版瀏覽器](#support-older-browsers)。

##### <a name="support-older-browsers"></a>支援舊版瀏覽器

2016 `SameSite` 標準規定將未知的值視為 `SameSite=Strict` 值。 因此，任何支援原始標準的舊版瀏覽器可能會在看到值為 `None`的 `SameSite` 屬性時中斷。 如果 Web 應用程式想要支援這些舊的瀏覽器，則必須執行瀏覽器探查。 ASP.NET Core 不會為您執行瀏覽器探查，因為 `User-Agent` 的要求標頭值高度不穩定，並每週變更一次。 相反地，cookie 原則中的擴充點可讓您新增 `User-Agent`特定的邏輯。

在*Startup.cs*中，新增下列程式碼：

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

`Microsoft.AspNetCore.SuppressSameSiteNone` 相容性參數可讓您暫時退出新的 ASP.NET Core cookie 行為。 將下列 JSON 新增至您專案中的 *.runtimeconfig.json json*檔案：

```json
{ 
  "configProperties": { 
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true" 
  } 
}
```

##### <a name="other-versions"></a>其他版本

即將推出的相關 `SameSite` 修補程式如下：

* ASP.NET Core 2.1、2.2 和3.0
* `Microsoft.Owin` 4.1
* `System.Web` （適用于 .NET Framework 4.7.2 和更新版本）

#### <a name="category"></a>分類

[ASP.NET]

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
