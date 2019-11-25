---
ms.openlocfilehash: 15ba678431b97e7c961c119d83546569bdf9bad2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2019
ms.locfileid: "74282509"
---
### <a name="http-some-cookie-samesite-defaults-changed-to-none"></a>HTTP：某些 cookie SameSite 預設值已變更為 None

`SameSite` 是 cookie 的選項，可協助降低某些跨網站偽造要求（CSRF）攻擊。 一開始引進此選項時，會跨各種 ASP.NET Core Api 使用不一致的預設值。 不一致的結果會導致混淆。 從 ASP.NET Core 3.0，這些預設值是較佳的對齊方式。 您必須針對每個元件加入宣告這項功能。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

類似的 ASP.NET Core Api 使用不同的預設 <xref:Microsoft.AspNetCore.Http.SameSiteMode> 值。 `HttpResponse.Cookies.Append(String, String)` 和 `HttpResponse.Cookies.Append(String, String, CookieOptions)`中會出現不一致的範例，分別預設為 `SameSiteMode.None` 和 `SameSiteMode.Lax`。

#### <a name="new-behavior"></a>新的行為

所有受影響的 Api 都會預設為 `SameSiteMode.None`。

#### <a name="reason-for-change"></a>變更的原因

預設值已變更，使 `SameSite` 加入宣告功能。

#### <a name="recommended-action"></a>建議的動作

發出 cookie 的每個元件都必須決定 `SameSite` 是否適用于其案例。 檢查受影響 Api 的使用方式，並視需要重新設定 `SameSite`。

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
