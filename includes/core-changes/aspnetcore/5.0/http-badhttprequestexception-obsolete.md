---
ms.openlocfilehash: c4e7864262a11aafa4b7f1f4bdf632fbf084c560
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507070"
---
### <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a>HTTP： Kestrel 和 IIS BadHttpRequestException 類型已標記為過時並被取代

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`和已 `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` 標示為過時，並已變更為衍生自 `Microsoft.AspNetCore.Http.BadHttpRequestException` 。 Kestrel 和 IIS 伺服器仍然會擲回舊的例外狀況類型，以提供回溯相容性。 未來的版本將移除過時的類型。

如需討論，請參閱[dotnet/aspnetcore # 20614](https://github.com/dotnet/aspnetcore/issues/20614)。

#### <a name="version-introduced"></a>引進的版本

5.0 Preview 4

#### <a name="old-behavior"></a>舊的行為

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`和 `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` 衍生自 <xref:System.IO.IOException?displayProperty=nameWithType> 。

#### <a name="new-behavior"></a>新的行為

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`和 `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` 已經過時。 類型也衍生自 `Microsoft.AspNetCore.Http.BadHttpRequestException` ，其衍生自 `System.IO.IOException` 。

#### <a name="reason-for-change"></a>變更的原因

已進行變更：

* 合併重複的類型。
* 跨伺服器的整合行為。

應用程式現在可以 `Microsoft.AspNetCore.Http.BadHttpRequestException` 在使用 Kestrel 或 IIS 時攔截基底例外狀況。

#### <a name="recommended-action"></a>建議的動作

以取代和的使用 `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` 方式 `Microsoft.AspNetCore.Http.BadHttpRequestException` 。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

- [AspNetCore. IIS. BadHttpRequestException](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [AspNetCore. Kestrel. BadHttpRequestException](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->
