---
ms.openlocfilehash: 3cc07eef109b9096bc5a5fbcd1ea098a23b2155f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78968356"
---
### <a name="http-browser-samesite-changes-impact-authentication"></a>HTTP： 瀏覽器同網站更改影響身份驗證

某些瀏覽器（如 Chrome 和 Firefox）對其`SameSite`Cookie 的實現進行了重大更改。 這些更改會影響遠端身份驗證方案，如 OpenID 連接和 WS-聯合，它們必須通過發送`SameSite=None`退出宣告。 但是，`SameSite=None`在 iOS 12 和其他瀏覽器的一些舊版本上會中斷。 該應用程式需要嗅探這些版本，並省略`SameSite`。

有關此問題的討論，請參閱[dotnet/aspnetcore_14996](https://github.com/dotnet/aspnetcore/issues/14996)。

#### <a name="version-introduced"></a>介紹的版本

3.1 預覽 1

#### <a name="old-behavior"></a>舊的行為

`SameSite`是 2016 年 HTTP Cookie 標準擴展草案。 它旨在緩解跨網站請求偽造 （CSRF）。 這最初設計為伺服器通過添加新參數而選擇的功能。 ASP.NET 核心 2.0 添加了`SameSite`對 的初始支援。

#### <a name="new-behavior"></a>新的行為

谷歌提出了一個不向後相容的新標準草案。 標準將預設模式更改為`Lax`，並添加新條目`None`以退出宣告。`Lax`足以滿足大多數應用程式 Cookie;但是，它打破了跨網站方案，如 OpenID 連接和 WS-聯合登錄。 大多數 OAuth 登錄不會受到影響，因為請求流的方式不同。 新`None`參數導致與實現先前標準草案的用戶端的相容性問題（例如 iOS 12）。 Chrome 80 將包括更改。 有關 Chrome 產品發佈時程表，請參閱[同一網站更新](https://www.chromium.org/updates/same-site)。

ASP.NET核心 3.1 已更新以實現新`SameSite`行為。 `SameSiteMode.None`更新重新定義了發出`SameSite=None`的行為，並添加了一個新值`SameSiteMode.Unspecified`來省略屬性。 `SameSite` 所有 Cookie API 現在都`Unspecified`預設為 ，儘管某些使用 Cookie 的元件會設置更特定于其方案的值，如 OpenID 連接關聯和 nonce Cookie。

有關此區域中其他最近更改，請參閱[HTTP：某些 Cookie SameSite 預設值更改為"無](/dotnet/core/compatibility/2.2-3.0#http-some-cookie-samesite-defaults-changed-to-none)"。 在 ASP.NET 酷 3.0 中，大多數<xref:Microsoft.AspNetCore.Http.SameSiteMode.Lax?displayProperty=nameWithType>預設值<xref:Microsoft.AspNetCore.Http.SameSiteMode.None?displayProperty=nameWithType>已更改為 （但仍使用以前的標準）。

#### <a name="reason-for-change"></a>更改原因

瀏覽器和規範更改，如前面的文本中概述。

#### <a name="recommended-action"></a>建議的動作

與遠端站台交互的應用（如通過協力廠商登錄）需要：

* 在多個瀏覽器上測試這些方案。
* 應用[支援舊瀏覽器](#support-older-browsers)中討論的 Cookie 策略瀏覽器嗅探緩解。

有關測試和瀏覽器嗅探說明，請參閱以下部分。

##### <a name="determine-if-youre-affected"></a>確定您是否受到影響

使用可以加入宣告新行為的用戶端版本測試 Web 應用。 Chrome、Firefox 和 Microsoft 邊緣鉻都具有可用於測試的新加入宣告功能標誌。 應用修補程式（尤其是 Safari）後，驗證你的應用是否與較舊的用戶端版本相容。 有關詳細資訊，請參閱[支援較舊的瀏覽器](#support-older-browsers)。

##### <a name="chrome"></a>Chrome

Chrome 78 及更高版本會產生誤導性測試結果。 這些版本有一個臨時緩解到位，並允許餅乾不到兩分鐘。 啟用了相應的測試標誌後，Chrome 76 和 77 可生成更準確的結果。 要測試新行為，要切換`chrome://flags/#same-site-by-default-cookies`為已啟用。 據報導，Chrome 75 和更早版本的新`None`設置出現故障。 有關詳細資訊，請參閱[支援較舊的瀏覽器](#support-older-browsers)。

谷歌沒有提供較舊的Chrome版本。 但是，您可以下載舊版本的鉻，這足以進行測試。 按照[下載鉻](https://www.chromium.org/getting-involved/download-chromium)的說明。

* [鉻 76 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/664998/)
* [鉻 74 Win64](https://commondatastorage.googleapis.com/chromium-browser-snapshots/index.html?prefix=Win_x64/638880/)

##### <a name="safari"></a>Safari

Safari 12 嚴格執行以前的草稿，如果看到 Cookie 中`None`的新價值，則失敗。 這必須通過瀏覽器嗅探代碼在[支援舊瀏覽器](#support-older-browsers)中顯示的避免。 請確保使用 Microsoft 身份驗證庫 （MSAL）、活動目錄身份驗證庫 （ADAL） 或您正在使用哪個庫測試 Safari 12 和 13 以及基於 WebKit 的作業系統樣式登錄。 問題取決於基礎作業系統版本。 OSX Mojave 10.14 和 iOS 12 已知與新行為存在相容性問題。 升級到 OSX Catalina 10.15 或 iOS 13 解決了問題。 Safari 當前沒有用於測試新規範行為的加入標誌。

##### <a name="firefox"></a>Firefox

Firefox 支援新標準可以在版本 68 上進行測試，稍後在帶有功能標誌`about:config``network.cookie.sameSite.laxByDefault`的頁面上加入宣告。 沒有報告舊版本的 Firefox 的相容性問題。

##### <a name="microsoft-edge"></a>Microsoft Edge

雖然 Microsoft Edge`SameSite`支援舊標準，但截至版本 44，它與新標準沒有任何相容性問題。

##### <a name="microsoft-edge-chromium"></a>微軟邊緣鉻

要素標誌為`edge://flags/#same-site-by-default-cookies`。 使用 Microsoft 邊緣鉻 78 進行測試時未觀察到相容性問題。

##### <a name="electron"></a>電子

電子版本包括舊版本的鉻。 例如，微軟團隊使用的電子版本是鉻66，它顯示了舊的行為。 使用產品使用的 Electron 版本執行您自己的相容性測試。 有關詳細資訊，請參閱[支援較舊的瀏覽器](#support-older-browsers)。

##### <a name="support-older-browsers"></a>支援較舊的瀏覽器

2016`SameSite`年標準規定，未知值應視為`SameSite=Strict`值。 因此，任何支援原始標準的較舊的瀏覽器在看到`SameSite`值 為 的屬性`None`時可能會中斷。 如果 Web 應用打算支援這些舊瀏覽器，則必須實現瀏覽器嗅探。 ASP.NET Core 不會為您實現瀏覽器嗅探，因為`User-Agent`請求標頭值極不穩定，並且每週更改一次。 相反，Cookie 策略中的擴充點允許您添加`User-Agent`特定于的邏輯。

在*Startup.cs*中，添加以下代碼：

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

##### <a name="opt-out-switches"></a>退出宣告開關

相容性`Microsoft.AspNetCore.SuppressSameSiteNone`開關使您能夠暫時退出宣告新的ASP.NET核心 Cookie 行為。 將以下 JSON 添加到專案中的*運行時 config.template.json*檔中：

```json
{
  "configProperties": {
    "Microsoft.AspNetCore.SuppressSameSiteNone": "true"
  }
}
```

##### <a name="other-versions"></a>其他版本

相關`SameSite`修補程式即將用於：

* ASP.NET核心 2.1、2.2 和 3.0
* `Microsoft.Owin`4.1
* `System.Web`（對於 .NET 框架 4.7.2 及更高版本）

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
