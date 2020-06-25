---
ms.openlocfilehash: 9a747d8fc15ca8fa2b915f89291f118d7344d172
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325248"
---
### <a name="httpsys-client-certificate-renegotiation-disabled-by-default"></a>HttpSys：預設會停用用戶端憑證重新協商

預設會停用重新協商連接和要求用戶端憑證的選項。 如需討論，請參閱 issue [dotnet/aspnetcore # 23181](https://github.com/dotnet/aspnetcore/issues/23181)。

#### <a name="version-introduced"></a>引進的版本

ASP.NET Core 5。0

#### <a name="old-behavior"></a>舊的行為

連接可以重新協商以要求用戶端憑證。

#### <a name="new-behavior"></a>新的行為

只有在初始連線交握期間，才可要求用戶端憑證。 如需詳細資訊，請參閱 pull request [dotnet/aspnetcore # 23162](https://github.com/dotnet/aspnetcore/pull/23162)。

#### <a name="reason-for-change"></a>變更的原因

重新協商會造成一些效能和鎖死問題。 HTTP/2 也不支援。 如需控制此行為的選項在 ASP.NET Core 3.1 中引進的其他內容，請參閱 issue [dotnet/aspnetcore # 14806](https://github.com/dotnet/aspnetcore/issues/14806)。

#### <a name="recommended-action"></a>建議的動作

需要用戶端憑證的應用程式應該使用*netsh.exe*將 `clientcertnegotiation` 選項設定為 `enabled` 。 如需詳細資訊，請參閱[netsh HTTP 命令](/windows-server/networking/technologies/netsh/netsh-http)。

如果您只想針對應用程式的某些部分啟用用戶端憑證，請參閱[選用用戶端憑證](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates)的指引。

如果您需要舊的重新協商行為，請將設定 `HttpSysOptions.ClientCertificateMethod` 為舊的值 `ClientCertificateMethod.AllowRenegotiate` 。 這不建議用於上述和連結的指引中所述的原因。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate`
- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync`
- `Overload:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod`

-->
