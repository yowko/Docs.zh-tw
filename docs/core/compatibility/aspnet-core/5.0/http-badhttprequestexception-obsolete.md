---
title: 中斷性變更： HTTP： Kestrel 和 IIS BadHttpRequestException 類型標示為已淘汰和已取代
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為 HTTP： Kestrel，以及標示為已淘汰和已取代的 IIS BadHttpRequestException 類型
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: c51b1dd9d708c04bc1bbcfb65ea2e9daea5330b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760657"
---
# <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a>HTTP： Kestrel 和 IIS BadHttpRequestException 類型標示為已淘汰和已取代

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` 和已 `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` 標示為已淘汰，且已變更為衍生自 `Microsoft.AspNetCore.Http.BadHttpRequestException` 。 Kestrel 和 IIS 伺服器仍會擲回舊的例外狀況類型，以提供回溯相容性。 未來的版本將移除過時的類型。

如需討論，請參閱 [dotnet/aspnetcore # 20614](https://github.com/dotnet/aspnetcore/issues/20614)。

## <a name="version-introduced"></a>引進的版本

5.0 Preview 4

## <a name="old-behavior"></a>舊的行為

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException``Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`衍生自 <xref:System.IO.IOException?displayProperty=nameWithType> 。

## <a name="new-behavior"></a>新的行為

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` 和 `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` 已淘汰。 型別也衍生自 `Microsoft.AspNetCore.Http.BadHttpRequestException` ，而衍生自 `System.IO.IOException` 。

## <a name="reason-for-change"></a>變更的原因

已進行變更：

* 合併重複的類型。
* 統一跨伺服器執行的行為。

應用程式現在可以 `Microsoft.AspNetCore.Http.BadHttpRequestException` 在使用 Kestrel 或 IIS 時攔截基底例外狀況。

## <a name="recommended-action"></a>建議的動作

取代和的 `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` 使用 `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` 方式 `Microsoft.AspNetCore.Http.BadHttpRequestException` 。

## <a name="affected-apis"></a>受影響的 API

- [AspNetCore. BadHttpRequestException。](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [AspNetCore. Kestrel. BadHttpRequestException](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->
