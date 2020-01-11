---
ms.openlocfilehash: 6f8e6d2786d20e055c9bef63891db4d6f88bc64b
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901889"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>身分識別：使用的函式接受新的參數

從 ASP.NET Core 3.0 開始，新的 `IUserConfirmation<TUser>` 參數已加入至 `SignInManager` 的函式。 如需詳細資訊，請參閱[dotnet/aspnetcore # 8356](https://github.com/dotnet/aspnetcore/issues/8356)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="reason-for-change"></a>變更的原因

這項變更的動機是在身分識別中新增新電子郵件/確認流程的支援。

#### <a name="recommended-action"></a>建議的動作

如果手動建立 `SignInManager`，請提供 `IUserConfirmation` 的執行，或從要提供的相依性插入抓取一個。

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
