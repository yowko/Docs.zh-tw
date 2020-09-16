---
ms.openlocfilehash: 492d3e61acff31d3d6858a1c27cf353b04a05e36
ms.sourcegitcommit: d4f7ba08f2a45a9dbef53be597eed6d4a9410f29
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/15/2020
ms.locfileid: "86401974"
---
### <a name="security-cookie-name-encoding-removed"></a>安全性：已移除 Cookie 名稱編碼

[HTTP cookie 標準](https://tools.ietf.org/html/rfc6265#section-4.1.1)只允許 cookie 名稱和值中的特定字元。 若要支援不允許的字元，ASP.NET Core：

* 建立回應 cookie 時進行編碼。
* 在讀取要求 cookie 時解碼。

在 ASP.NET Core 5.0 中，此編碼行為會因安全性考慮而改變。

如需相關討論，請參閱 GitHub issue [dotnet/aspnetcore # 23578](https://github.com/dotnet/aspnetcore/issues/23578)。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 8

#### <a name="old-behavior"></a>舊的行為

回應 cookie 名稱會經過編碼。 要求 cookie 名稱已解碼。

#### <a name="new-behavior"></a>新的行為

已移除 cookie 名稱的編碼和解碼。 針對先前 [支援](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) 的 ASP.NET Core 版本，小組計畫就地減輕解碼問題。 此外， <xref:Microsoft.AspNetCore.Http.IResponseCookies.Append%2A?displayProperty=nameWithType> 使用無效 cookie 名稱呼叫會擲回類型的例外狀況 <xref:System.ArgumentException> 。 Cookie 值的編碼和解碼會維持不變。

#### <a name="reason-for-change"></a>變更的原因

在 [多個 web](https://github.com/advisories/GHSA-j6w9-fv6q-3q52)架構中發現問題。 編碼和解碼可能會讓攻擊者透過詐騙保留的前置詞（例如的編碼值）來略過安全性功能，稱為 [cookie 首碼](https://tools.ietf.org/html/draft-ietf-httpbis-cookie-prefixes-00) `__Host-` `__%48ost-` 。 攻擊需要次要惡意探索，才能在網站中插入詐騙的 cookie，例如跨網站腳本 (XSS) 弱點。 ASP.NET Core 或程式庫或範本中預設不會使用這些前置詞 `Microsoft.Owin` 。

#### <a name="recommended-action"></a>建議的動作

如果您要將專案移至 ASP.NET Core 5.0 或更新版本，請確定其 cookie 名稱符合 [權杖規格需求](https://tools.ietf.org/html/rfc2616#section-2.2)：不包括控制項和分隔符號的 ASCII 字元 `"(" | ")" | "<" | ">" | "@" | "," | ";" | ":" | "\" | <"> | "/" | "[" | "]" | "?" | "=" | "{" | "}" | SP | HT` 。 在 cookie 名稱或其他 HTTP 標頭中使用非 ASCII 字元，可能會導致伺服器發生例外狀況，或用戶端不正確地進行錯誤的往返。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.AspNetCore.Http.HttpRequest.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.HttpResponse.Cookies%2A?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinRequest.Cookies?displayProperty=nameWithType>
- <xref:Microsoft.Owin.IOwinResponse.Cookies?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.HttpRequest.Cookies`
- `Overload:Microsoft.AspNetCore.Http.HttpResponse.Cookies`
- `P:Microsoft.Owin.IOwinRequest.Cookies`
- `P:Microsoft.Owin.IOwinResponse.Cookies`

-->
