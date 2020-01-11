---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901776"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a>HTTP：所有伺服器中的同步 IO 已停用

從 ASP.NET Core 3.0 開始，預設會停用同步伺服器作業。

#### <a name="change-description"></a>變更描述

`AllowSynchronousIO` 是每部伺服器中的選項，可啟用或停用同步 IO Api，如 `HttpRequest.Body.Read`、`HttpResponse.Body.Write`和 `Stream.Flush`。 這些 Api 長期以來都是執行緒耗盡和應用程式停止回應的來源。 從 ASP.NET Core 3.0 Preview 3 開始，預設會停用這些同步作業。

受影響的伺服器：

- Kestrel
- HttpSys
- IIS 同進程
- TestServer

預期的錯誤如下：

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

每一部伺服器都有 `AllowSynchronousIO` 選項可控制此行為，而所有伺服器的預設值現在都會 `false`。

您也可以根據每個要求來覆寫此行為，以做為暫時的緩和措施。 例如：

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

如果您在 `Dispose`中 `TextWriter` 或另一個資料流程呼叫同步 API 時遇到問題，請改為呼叫新的 `DisposeAsync` API。

如需討論，請參閱[dotnet/aspnetcore # 7644](https://github.com/dotnet/aspnetcore/issues/7644)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

預設允許 `HttpRequest.Body.Read`、`HttpResponse.Body.Write`和 `Stream.Flush`。

#### <a name="new-behavior"></a>新的行為

預設不允許這些同步 Api：

預期的錯誤如下：

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a>變更的原因

這些同步 Api 長期以來都是執行緒耗盡和應用程式停止回應的來源。 從 ASP.NET Core 3.0 Preview 3 開始，預設會停用同步作業。

#### <a name="recommended-action"></a>建議的動作

使用方法的非同步版本。 您也可以根據每個要求來覆寫此行為，以做為暫時的緩和措施。

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

- <xref:System.IO.Stream.Flush%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Read%2A?displayProperty=nameWithType>
- <xref:System.IO.Stream.Write%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

- `Overload:System.IO.Stream.Flush`
- `Overload:System.IO.Stream.Read`
- `Overload:System.IO.Stream.Write`

-->
