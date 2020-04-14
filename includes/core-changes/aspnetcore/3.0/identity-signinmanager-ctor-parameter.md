---
ms.openlocfilehash: ed5a90063b8963d79f412ec1c5c0b9030f980f83
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/13/2020
ms.locfileid: "81275035"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>識別:SignInManager 建構函數接受新參數

從 ASP.NET Core`IUserConfirmation<TUser>`3.0`SignInManager`開始,向構造函數添加了一個新參數。 有關詳細資訊,請參閱[點網/阿斯平核心#8356](https://github.com/dotnet/aspnetcore/issues/8356)。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="reason-for-change"></a>變更原因

更改的動機是在標識中添加新的電子郵件/確認流。

#### <a name="recommended-action"></a>建議的動作

如果手動構造`SignInManager`,`IUserConfirmation`提供 或 從依賴項注入中獲取實現或抓取一個來提供。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
