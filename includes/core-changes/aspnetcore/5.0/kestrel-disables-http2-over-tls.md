---
ms.openlocfilehash: 92210f6becb5a5a43893ee0fd51ef51e2ddd7f8d
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325228"
---
### <a name="kestrel-http2-disabled-over-tls-on-incompatible-windows-versions"></a>Kestrel：在不相容的 Windows 版本上，透過 TLS 停用 HTTP/2

若要在 Windows 上啟用透過傳輸層安全性（TLS）的 HTTP/2，必須符合兩個需求：

- 從 Windows 8.1 和 Windows Server 2012 R2 開始提供的應用層通訊協定協商（ALPN）支援。
- 一組與 HTTP/2 相容的密碼，從 Windows 10 和 Windows Server 2016 開始提供。

因此，在設定 HTTP/2 over TLS 時，Kestrel 的行為已變更為：

- `Http1` `Information` 當[listenoptions 來. HttpProtocols](/dotnet/api/microsoft.aspnetcore.server.kestrel.core.httpprotocols)設定為時，降級為，並在層級記錄訊息 `Http1AndHttp2` 。 `Http1AndHttp2` 是 `ListenOptions.HttpProtocols` 的預設值。
- `NotSupportedException`當設定為時，擲回 `ListenOptions.HttpProtocols` `Http2` 。

如需討論，請參閱 issue [dotnet/aspnetcore # 23068](https://github.com/dotnet/aspnetcore/issues/23068)。

#### <a name="version-introduced"></a>引進的版本

ASP.NET Core 5.0 Preview 7

#### <a name="old-behavior"></a>舊的行為

下表概述透過 TLS 設定 HTTP/2 時的行為。

| 通訊協定 | Windows 7、<br />Windows Server 2008 R2、<br />或更早版本 | Windows 8、<br />Windows Server 2012 | Windows 8.1<br />Windows Server 2012 R2 | Windows 10、<br />Windows Server 2016、<br />或更新版本 |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | 放棄`NotSupportedException`                   | TLS 交握期間發生錯誤     | TLS 交握期間發生錯誤&ast;     | 沒有錯誤 |
| `Http1AndHttp2` | 降級為`Http1`                    | 降級為`Http1`     | TLS 交握期間發生錯誤&ast;     | 沒有錯誤 |

&ast;設定相容的加密套件以啟用這些案例。

#### <a name="new-behavior"></a>新的行為

下表概述透過 TLS 設定 HTTP/2 時的行為。

| 通訊協定 | Windows 7、<br />Windows Server 2008 R2、<br />或更早版本 | Windows 8、<br />Windows Server 2012 | Windows 8.1<br />Windows Server 2012 R2 | Windows 10、<br />Windows Server 2016、<br />或更新版本 |
|---------------|-----------------------------------------------|--------------------------------|-------------------------------------|------------------------------------------|
| `Http2`         | 放棄`NotSupportedException`                   | 放棄`NotSupportedException`     | Throw `NotSupportedException`&ast;&ast;     | 沒有錯誤 |
| `Http1AndHttp2` | 降級為`Http1`                    | 降級為`Http1`     | 降級為 `Http1`&ast;&ast;     | 沒有錯誤 |

&ast;&ast;設定相容的加密套件，並將應用程式內容切換 `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` 為， `true` 以啟用這些案例。

#### <a name="reason-for-change"></a>變更的原因

這種變更可確保較舊的 Windows 版本上 HTTP/2 over TLS 的相容性錯誤，會儘早且清楚地呈現。

#### <a name="recommended-action"></a>建議的動作

請確定在不相容的 Windows 版本上停用 HTTP/2 over TLS。 Windows 8.1 和 Windows Server 2012 R2 不相容，因為預設不會有必要的密碼。 不過，您可以將電腦設定值更新為使用 HTTP/2 相容的密碼。 如需詳細資訊，請參閱[Windows 8.1 中的 TLS 加密套件](/windows/win32/secauthn/tls-cipher-suites-in-windows-8-1)。 設定好之後，您必須透過設定應用程式內容切換來啟用 Kestrel 上的 HTTP/2 over TLS `Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2` 。 例如：

```csharp
AppContext.SetSwitch("Microsoft.AspNetCore.Server.Kestrel.EnableWindows81Http2", true);
```

未變更任何基礎支援。 例如，透過 TLS 的 HTTP/2 從未在 Windows 8 或 Windows Server 2012 上運作。 這項變更會修改這些不支援案例中的錯誤呈現方式。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

無

<!--

#### Affected APIs

Not detectable via API analysis

-->
