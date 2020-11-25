---
ms.openlocfilehash: ed5a90063b8963d79f412ec1c5c0b9030f980f83
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032372"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>Identity：使用函式接受新的參數

從 ASP.NET Core 3.0 開始，已將新 `IUserConfirmation<TUser>` 的參數新增至函式 `SignInManager` 。 如需詳細資訊，請參閱 [dotnet/aspnetcore # 8356](https://github.com/dotnet/aspnetcore/issues/8356)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="reason-for-change"></a>變更的原因

變革的動機是要在身分識別中新增電子郵件/確認流程的支援。

#### <a name="recommended-action"></a>建議的動作

如果手動建立 `SignInManager` ，請提供的實作為， `IUserConfirmation` 或從相依性插入中取得一個，以提供。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
