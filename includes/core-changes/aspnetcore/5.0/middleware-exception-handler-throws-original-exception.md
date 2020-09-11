---
ms.openlocfilehash: 26e521a86b504824f035ad5d40e4a04d2ea26abc
ms.sourcegitcommit: 6d4ee46871deb9ea1e45bb5f3784474e240bbc26
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2020
ms.locfileid: "90022959"
---
### <a name="middleware-exception-handler-middleware-throws-original-exception-if-handler-not-found"></a>中介軟體：如果找不到處理程式，中介軟體會擲回原始例外狀況

在 ASP.NET Core 5.0 之前， [例外狀況處理常式中介軟體](xref:Microsoft.AspNetCore.Builder.ExceptionHandlerExtensions.UseExceptionHandler%2A) 會在發生例外狀況時，執行已設定的例外狀況處理常式。 如果找不到透過設定的例外狀況處理常式， <xref:Microsoft.AspNetCore.Builder.ExceptionHandlerOptions.ExceptionHandlingPath> 則會產生 HTTP 404 回應。 回應會誤導它：

* 似乎是使用者錯誤。
* 模糊伺服器上發生例外狀況的事實。

為了解決 ASP.NET Core 5.0 中誤導的錯誤，如果找不到例外狀況處理常式，則會擲回 `ExceptionHandlerMiddleware` 原始例外狀況。 因此，伺服器會產生 HTTP 500 回應。 當偵測到發生的錯誤時，回應將會比較容易在伺服器記錄檔中進行檢查。

如需相關討論，請參閱 GitHub issue [dotnet/aspnetcore # 25288](https://github.com/dotnet/aspnetcore/issues/25288)。

#### <a name="version-introduced"></a>引進的版本

5.0 RC 1

#### <a name="old-behavior"></a>舊的行為

如果找不到設定的例外狀況處理常式，例外狀況處理常式中介軟體會產生 HTTP 404 回應。

#### <a name="new-behavior"></a>新的行為

如果找不到設定的例外狀況處理常式，例外狀況處理常式中介軟體會擲回原始例外狀況。

#### <a name="reason-for-change"></a>變更的原因

HTTP 404 錯誤無法明確指出伺服器上發生例外狀況。 這種變更會產生 HTTP 500 錯誤，讓它顯而易見：

* 問題不是由使用者錯誤所造成。
* 在伺服器上發生例外狀況。

#### <a name="recommended-action"></a>建議的動作

沒有任何 API 變更。 所有現有的應用程式都會繼續編譯和執行。 擲回的例外狀況是由伺服器處理。 例如，例外狀況會透過 [Kestrel](/aspnet/core/fundamentals/servers/kestrel) 或 [HTTP.sys](/aspnet/core/fundamentals/servers/httpsys)轉換成 HTTP 500 錯誤回應。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!--

#### Affected APIs

Not detectable via API analysis

-->
