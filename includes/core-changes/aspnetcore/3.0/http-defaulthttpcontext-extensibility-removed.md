---
ms.openlocfilehash: 9d138f79fcede4acac837f8d7793aa343ced737c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78290767"
---
### <a name="http-defaulthttpcontext-extensibility-removed"></a>HTTP： 預設 HttpCoNtext 擴充性已被刪除

作為 ASP.NET Core 3.0 性能改進的一部分，`DefaultHttpContext`已刪除 的擴充性。 該類現在是`sealed`。 有關詳細資訊，請參閱[點網/阿斯平核心#6504](https://github.com/dotnet/aspnetcore/pull/6504)。

如果您的單元測試使用`Mock<DefaultHttpContext>`、使用`Mock<HttpContext>`或`new DefaultHttpContext()`代替。

有關討論，請參閱[點網/阿斯平核心#6534](https://github.com/dotnet/aspnetcore/issues/6534)。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

類可以從`DefaultHttpContext`派生。

#### <a name="new-behavior"></a>新的行為

類無法派生自`DefaultHttpContext`。

#### <a name="reason-for-change"></a>更改原因

擴充性最初是為了允許池化，`HttpContext`但它引入了不必要的複雜性並阻礙了其他優化。

#### <a name="recommended-action"></a>建議的動作

如果您在單元測試中使用`Mock<DefaultHttpContext>`，`Mock<HttpContext>`請改用。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Http.DefaultHttpContext?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.Http.DefaultHttpContext`

-->
