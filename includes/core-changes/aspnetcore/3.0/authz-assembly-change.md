---
ms.openlocfilehash: 65bac44c84589fb55d2b04c39088c2825c451a6b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394205"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>授權： AddAuthorization 多載已移至不同的元件

用來存放在 `Microsoft.AspNetCore.Authorization` 中的核心 `AddAuthorization` 方法已重新命名為 `AddAuthorizationCore`。 舊的 `AddAuthorization` 方法仍然存在，但卻是在 `Microsoft.AspNetCore.Authorization.Policy` 封裝中。 使用這兩種方法的應用程式應該看不到任何影響。 未使用原則套件的應用程式必須切換為使用 `AddAuthorizationCore`。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`AddAuthorization` 方法存在於 `Microsoft.AspNetCore.Authorization` 中。

#### <a name="new-behavior"></a>新的行為

`AddAuthorization` 方法存在於 `Microsoft.AspNetCore.Authorization.Policy` 中。 `AddAuthorizationCore` 是舊方法的新名稱。

#### <a name="reason-for-change"></a>變更的原因

`AddAuthorization` 是新增授權所需之所有泛型服務的較佳方法名稱。

#### <a name="recommended-action"></a>建議的動作

請將參考新增至 `Microsoft.AspNetCore.Authorization.Policy`，或改為使用 `AddAuthorizationCore`。

#### <a name="category"></a>分類

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
