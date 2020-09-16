---
ms.openlocfilehash: 9d138f79fcede4acac837f8d7793aa343ced737c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78290767"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a>HTTP：已移除 DefaultHttpCoNtext 擴充性

在 ASP.NET Core 3.0 效能改進的過程中，已移除的擴充性 `DefaultHttpContext` 。 類別現在是 `sealed` 。 如需詳細資訊，請參閱 [dotnet/aspnetcore # 6504](https://github.com/dotnet/aspnetcore/pull/6504)。

如果您的單元測試使用 `Mock<DefaultHttpContext>` ，請改用 `Mock<HttpContext>` 或 `new DefaultHttpContext()` 。

如需討論，請參閱 [dotnet/aspnetcore # 6534](https://github.com/dotnet/aspnetcore/issues/6534)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

類別可以衍生自 `DefaultHttpContext` 。

#### <a name="new-behavior"></a>新的行為

類別無法衍生自 `DefaultHttpContext` 。

#### <a name="reason-for-change"></a>變更的原因

最初提供的擴充性是為了允許共用 `HttpContext` ，但它引進了不必要的複雜度，並阻礙其他優化。

#### <a name="recommended-action"></a>建議的動作

如果您要 `Mock<DefaultHttpContext>` 在單元測試中使用，請改為開始使用 `Mock<HttpContext>` 。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
