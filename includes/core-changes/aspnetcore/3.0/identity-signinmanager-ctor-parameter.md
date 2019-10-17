---
ms.openlocfilehash: 56b394c4698f60baeb70d3c17d1abee5d867deb7
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394364"
---
### <a name="identity-signinmanager-constructor-accepts-new-parameter"></a>身分識別：使用的函式接受新的參數

從 ASP.NET Core 3.0 開始，新的 `IUserConfirmation<TUser>` 參數已加入至 @no__t 1 的函式。 如需詳細資訊，請參閱[aspnet/AspNetCore # 8356](https://github.com/aspnet/AspNetCore/issues/8356)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="reason-for-change"></a>變更的原因

這項變更的動機是在身分識別中新增新電子郵件/確認流程的支援。

#### <a name="recommended-action"></a>建議的動作

如果手動建立 `SignInManager`，請提供 `IUserConfirmation` 的執行，或從相依性插入中抓取一個，以提供。

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Identity.SignInManager%601.%23ctor%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.AspNetCore.Identity.SignInManager`1.#ctor`

-->
