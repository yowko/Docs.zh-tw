---
ms.openlocfilehash: 53d2c989120c92f4e2d18f50ce4b364bd4c9b604
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032365"
---
### <a name="http-synchronous-io-disabled-in-all-servers"></a>HTTP：所有伺服器中的同步 IO 已停用

從 ASP.NET Core 3.0 開始，預設會停用同步伺服器作業。

#### <a name="change-description"></a>變更描述

`AllowSynchronousIO` 是每部伺服器中的選項，可啟用或停用同步 IO Api `HttpRequest.Body.Read` ，例如、 `HttpResponse.Body.Write` 和 `Stream.Flush` 。 這些 Api 很久就是執行緒耗盡的來源，而應用程式會停止回應。 從 ASP.NET Core 3.0 Preview 3 開始，預設會停用這些同步作業。

受影響的伺服器：

- Kestrel
- HttpSys
- IIS 同進程
- TestServer

預期的錯誤如下：

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

每一部伺服器都有一個 `AllowSynchronousIO` 選項，可控制這個行為，而所有的預設值都是 `false` 。

也可以根據每個要求覆寫此行為，以暫時降低風險。 例如：

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

如果您 `TextWriter` 在中有或另一個呼叫同步 API 的資料流程遇到問題 `Dispose` ，請改為呼叫新的 `DisposeAsync` api。

如需討論，請參閱 [dotnet/aspnetcore # 7644](https://github.com/dotnet/aspnetcore/issues/7644)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`HttpRequest.Body.Read``HttpResponse.Body.Write` `Stream.Flush` 預設允許、和。

#### <a name="new-behavior"></a>新的行為

預設不允許這些同步的 Api：

預期的錯誤如下：

- `Synchronous operations are disallowed. Call ReadAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call WriteAsync or set AllowSynchronousIO to true instead.`
- `Synchronous operations are disallowed. Call FlushAsync or set AllowSynchronousIO to true instead.`

#### <a name="reason-for-change"></a>變更的原因

這些同步 Api 很久就是執行緒耗盡的來源，而應用程式會停止回應。 從 ASP.NET Core 3.0 Preview 3 開始，同步作業預設為停用。

#### <a name="recommended-action"></a>建議的動作

使用方法的非同步版本。 也可以根據每個要求覆寫此行為，以暫時降低風險。

```csharp
var syncIOFeature = HttpContext.Features.Get<IHttpBodyControlFeature>();
if (syncIOFeature != null)
{
    syncIOFeature.AllowSynchronousIO = true;
}
```

#### <a name="category"></a>類別

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
