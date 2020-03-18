---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74282509"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a>HTTP： 某些 Cookie 同網站預設值更改為"無"

`SameSite`是 Cookie 的一個選項，可説明緩解某些跨網站請求偽造 （CSRF） 攻擊。 最初引入此選項時，在各種ASP.NET核心 API 中使用了不一致的預設值。 這種不一致導致了混亂的結果。 從 ASP.NET Core 3.0 起，這些預設值可以更好地對齊。 您必須根據每個元件加入宣告此功能。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

類似的ASP.NET核心 API 使用不同的預設值<xref:Microsoft.AspNetCore.Http.SameSiteMode>。 不一致的示例分別`HttpResponse.Cookies.Append(String, String)`出現在 和`HttpResponse.Cookies.Append(String, String, CookieOptions)`中，後者分別預設為`SameSiteMode.None``SameSiteMode.Lax`和 。

#### <a name="new-behavior"></a>新的行為

所有受影響的 API 預設為`SameSiteMode.None`。

#### <a name="reason-for-change"></a>更改原因

預設值已更改，以進行`SameSite`加入宣告功能。

#### <a name="recommended-action"></a>建議的動作

發出 Cookie 的每個元件都需要決定是否適合`SameSite`其方案。 查看受影響 API 的使用方式，並根據需要重新`SameSite`配置。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:Microsoft.AspNetCore.Http.IResponseCookies.Append(System.String,System.String,Microsoft.AspNetCore.Http.CookieOptions)`
- `Overload:Microsoft.AspNetCore.Builder.CookiePolicyOptions.MinimumSameSitePolicy`

-->
