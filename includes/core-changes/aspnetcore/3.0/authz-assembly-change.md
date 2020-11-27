---
ms.openlocfilehash: 2819fb3857fa6d40a2b2e42eeaec2d9c6e50eef0
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96299349"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>授權： AddAuthorization 多載移至不同的元件

`AddAuthorization`用來存放的核心方法已重新 `Microsoft.AspNetCore.Authorization` 命名為 `AddAuthorizationCore` 。 舊 `AddAuthorization` 方法仍存在，但仍在元件中 `Microsoft.AspNetCore.Authorization.Policy` 。 使用這兩種方法的應用程式應該看不到任何影響。 請注意， `Microsoft.AspNetCore.Authorization.Policy` 現在會隨附于共用架構，而不是獨立套件，如共用架構中所討論 [：從 AspNetCore 移除的元件](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

`AddAuthorization` 方法存在於中 `Microsoft.AspNetCore.Authorization` 。

#### <a name="new-behavior"></a>新的行為

`AddAuthorization` 方法存在於中 `Microsoft.AspNetCore.Authorization.Policy` 。 `AddAuthorizationCore` 這是舊方法的新名稱。

#### <a name="reason-for-change"></a>變更的原因

`AddAuthorization` 是更好的方法名稱，可新增授權所需的所有一般服務。

#### <a name="recommended-action"></a>建議的動作

請改為加入 `Microsoft.AspNetCore.Authorization.Policy` 或使用的參考 `AddAuthorizationCore` 。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
