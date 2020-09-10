---
ms.openlocfilehash: 975e331ad3e7bd7e0e8f49b62795c6acc7031ca9
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656328"
---
### <a name="winforms-and-wpf-apps-use-microsoftnetsdk"></a>WinForms 和 WPF 應用程式使用 Microsoft .NET Sdk

Windows Forms 和 Windows Presentation Framework (WPF) 應用程式現在會使用 .NET SDK (`Microsoft.NET.Sdk`) ，而不是 .Net Core WinForms 和 WPF SDK (`Microsoft.NET.Sdk.WindowsDesktop`) 。

#### <a name="change-description"></a>變更描述

在舊版的 .NET Core 中，WinForms 和 WPF 應用程式使用個別的 [專案 SDK](../../../../docs/core/project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`) 。 從 .NET 5.0 開始，WinForms 和 WPF SDK 已與 .NET SDK (`Microsoft.NET.Sdk`) 整合。 此外，新的 [目標 framework 標記 (TFM) ](../../../../docs/standard/frameworks.md) 取代 `netcoreapp` 和 `netstandard` .net 5。 下列範例顯示覆位目標至 .NET 5.0 或更新版本時，您需要對 WPF 專案檔進行的變更。

在先前的 .NET Core 版本中：

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

在 .NET 5.0 和更新版本中：

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

#### <a name="version-introduced"></a>引進的版本

.NET 5.0 Preview 8

#### <a name="recommended-action"></a>建議的動作

在您的 WPF 或 Windows Forms 專案檔中：

- 將 `Sdk` 屬性更新為 `Microsoft.NET.Sdk` 。
- 將 `TargetFramework` 屬性更新為 `net5.0-windows` 。

#### <a name="category"></a>類別

- Windows Forms
- Windows Presentation Framework (WPF)

#### <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
