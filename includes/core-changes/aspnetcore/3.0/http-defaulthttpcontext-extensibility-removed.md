---
ms.openlocfilehash: 7b5ae84d02b83a10a4b9e002fc2ed4ee0833b84c
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2019
ms.locfileid: "73198386"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a>HTTP： DefaultHttpCoNtext 擴充性已移除

在 ASP.NET Core 3.0 效能改進的過程中，已移除 `DefaultHttpContext` 的擴充性。 類別現在 `sealed`。 如需詳細資訊，請參閱[aspnet/AspNetCore # 6504](https://github.com/aspnet/AspNetCore/pull/6504)。

如果您的單元測試使用 `Mock<DefaultHttpContext>`，請改用 `Mock<HttpContext>`。

如需討論，請參閱[aspnet/AspNetCore # 6534](https://github.com/aspnet/AspNetCore/issues/6534)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

類別可以衍生自 `DefaultHttpContext`。

#### <a name="new-behavior"></a>新的行為

類別無法衍生自 `DefaultHttpContext`。

#### <a name="reason-for-change"></a>變更的原因

最初提供的擴充性是為了允許 `HttpContext` 的集區，但它引進了不必要的複雜性並阻礙其他優化。

#### <a name="recommended-action"></a>建議的動作

如果您是在單元測試中使用 `Mock<DefaultHttpContext>`，請改為開始使用 `Mock<HttpContext>`。

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
