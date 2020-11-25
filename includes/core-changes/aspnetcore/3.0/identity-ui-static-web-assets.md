---
ms.openlocfilehash: c5e4b5619394f99a419fe48aee190ad741ea8c0d
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032376"
---
### <a name="identity-ui-uses-static-web-assets-feature"></a>身分識別： UI 使用靜態 web 資產功能

ASP.NET Core 3.0 引進了靜態 web 資產功能，而身分識別 UI 已採用。

#### <a name="change-description"></a>變更描述

由於身分識別 UI 採用靜態 web 資產功能，因此：

- 您可以使用專案檔中的屬性來完成架構選擇 `IdentityUIFrameworkVersion` 。
- 啟動程式4是身分識別 UI 的預設 UI 架構。 啟動程式3已達生命週期結束，您應該考慮遷移至支援的版本。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="old-behavior"></a>舊的行為

身分識別 UI 的預設 UI 架構是 **啟動程式 3**。 UI 架構可以使用參數 `AddDefaultUI` 在中的方法呼叫來設定 `Startup.ConfigureServices` 。

#### <a name="new-behavior"></a>新的行為

身分識別 UI 的預設 UI 架構是 **啟動程式 4**。 您必須在專案檔中設定 UI 架構，而不是在 `AddDefaultUI` 方法呼叫中設定。

#### <a name="reason-for-change"></a>變更的原因

採用靜態 web 資產功能需要將 UI 架構設定移至 MSBuild。 決定要內嵌的架構是組建階段決策，而不是執行時間決策。

#### <a name="recommended-action"></a>建議的動作

請檢查您的網站 UI，以確保新的啟動載入器4元件相容。 如有必要，請使用 `IdentityUIFrameworkVersion` MSBuild 屬性還原為啟動程式3。 將屬性新增至 `<PropertyGroup>` 專案檔中的元素：

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
