---
ms.openlocfilehash: 6f8e6d2786d20e055c9bef63891db4d6f88bc64b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901889"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>標識：SignInManager 建構函式接受新參數

從 ASP.NET Core 3.0`IUserConfirmation<TUser>`開始，向`SignInManager`建構函式添加了一個新參數。 有關詳細資訊，請參閱[點網/阿斯平核心#8356](https://github.com/dotnet/aspnetcore/issues/8356)。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="reason-for-change"></a>更改原因

更改的動機是在標識中添加新的電子郵件/確認流。

#### <a name="recommended-action"></a>建議的動作

如果手動構造 ，`SignInManager`提供`IUserConfirmation`或 從依賴項注入中獲取實現或抓取一個來提供。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
