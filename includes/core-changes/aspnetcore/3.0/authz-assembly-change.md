---
ms.openlocfilehash: b91cdc7a0d2e4258662155a840500ce21ab35760
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74100760"
---
### <a name="authorization-addauthorization-overload-moved-to-different-assembly"></a>授權：將授權重載移動到不同的程式集

過去駐`AddAuthorization`留在 中`Microsoft.AspNetCore.Authorization`的核心方法重命名為`AddAuthorizationCore`。 舊`AddAuthorization`方法仍然存在，但位於程式集中`Microsoft.AspNetCore.Authorization.Policy`。 使用這兩種方法的應用不應看到任何影響。 請注意，`Microsoft.AspNetCore.Authorization.Policy`現在在共用框架中發貨，而不是共用框架中討論的獨立包[：從 Microsoft 中刪除的程式集](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為
`AddAuthorization`方法存在於`Microsoft.AspNetCore.Authorization`中。

#### <a name="new-behavior"></a>新的行為

`AddAuthorization`方法存在於`Microsoft.AspNetCore.Authorization.Policy`中。 `AddAuthorizationCore`是舊方法的新名稱。

#### <a name="reason-for-change"></a>更改原因

`AddAuthorization`是添加授權所需的所有公共服務的更好方法名稱。

#### <a name="recommended-action"></a>建議的動作

增加參考`Microsoft.AspNetCore.Authorization.Policy`或改用引用`AddAuthorizationCore`。

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})?displayProperty=fullName>

<!--

#### Affected APIs

`M:Microsoft.Extensions.DependencyInjection.AuthorizationServiceCollectionExtensions.AddAuthorization(Microsoft.Extensions.DependencyInjection.IServiceCollection,System.Action{Microsoft.AspNetCore.Authorization.AuthorizationOptions})`

-->
