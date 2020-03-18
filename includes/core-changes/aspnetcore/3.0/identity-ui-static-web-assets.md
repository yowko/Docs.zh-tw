---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "73041655"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a>標識：UI 使用靜態 Web 資產功能

ASP.NET Core 3.0 引入了靜態 Web 資產功能，而標識 UI 已採用此功能。

#### <a name="change-description"></a>變更描述

由於標識 UI 採用了靜態 Web 資產功能：

- 框架選擇通過使用專案檔案中的屬性`IdentityUIFrameworkVersion`來完成。
- 引導 4 是標識 UI 的預設 UI 框架。 引導 3 已達到生命週期結束，應考慮遷移到受支援的版本。

#### <a name="version-introduced"></a>介紹的版本

3.0

#### <a name="old-behavior"></a>舊的行為

標識 UI 的預設 UI 框架為**引導 3**。 可以使用 參數對 中的`AddDefaultUI``Startup.ConfigureServices`方法調用配置 UI 框架。

#### <a name="new-behavior"></a>新的行為

標識 UI 的預設 UI 框架是**引導 4**。 必須在專案檔案中而不是`AddDefaultUI`方法調用中配置 UI 框架。

#### <a name="reason-for-change"></a>更改原因

採用靜態 Web 資產功能要求 UI 框架配置遷移到 MSBuild。 要嵌入哪個框架的決定是生成時間決策，而不是運行時決策。

#### <a name="recommended-action"></a>建議的動作

查看網站 UI 以確保新的 Bootstrap 4 元件相容。 如有必要，`IdentityUIFrameworkVersion`請使用 MSBuild 屬性還原到引導 3。 將屬性添加到專案檔案中`<PropertyGroup>`的元素：

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a>類別

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
