---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2019
ms.locfileid: "73041655"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a>身分識別： UI 使用靜態 web 資產功能

ASP.NET Core 3.0 引進了靜態 web 資產功能，且身分識別 UI 已採用它。

#### <a name="change-description"></a>變更描述

由於身分識別使用者介面採用靜態 web 資產功能：

- 您可以使用專案檔中的 `IdentityUIFrameworkVersion` 屬性來完成架構選擇。
- 啟動程式4是身分識別 UI 的預設 UI 架構。 啟動程式3已達到生命週期的結尾，您應該考慮遷移至支援的版本。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

身分識別 UI 的預設 UI 架構是**啟動程式 3**。 您可以使用 `Startup.ConfigureServices`中 `AddDefaultUI` 方法呼叫的參數來設定 UI 架構。

#### <a name="new-behavior"></a>新的行為

身分識別 UI 的預設 UI 架構是**啟動程式 4**。 UI 架構必須在專案檔中設定，而不是在 `AddDefaultUI` 方法呼叫中。

#### <a name="reason-for-change"></a>變更的原因

採用靜態 web 資產功能時，UI 架構設定必須移至 MSBuild。 決定要內嵌的架構是組建時間決策，而不是執行時間決策。

#### <a name="recommended-action"></a>建議的動作

請檢查您的網站 UI，以確保新的啟動程式4元件相容。 如有必要，請使用 `IdentityUIFrameworkVersion` MSBuild 屬性來還原為啟動程式3。 將屬性新增至專案檔中的 `<PropertyGroup>` 元素：

```xml
<IdentityUIFrameworkVersion>Bootstrap3</IdentityUIFrameworkVersion>
```

#### <a name="category"></a>Category

ASP.NET Core

#### <a name="affected-apis"></a>受影響的 API

<xref:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Identity.IdentityBuilderUIExtensions.AddDefaultUI(Microsoft.AspNetCore.Identity.IdentityBuilder,Microsoft.AspNetCore.Identity.UI.UIFramework)`

-->
