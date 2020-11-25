---
title: 重大變更： WinForms 和 WPF 應用程式使用 Microsoft .NET Sdk
description: 瞭解 .NET 5.0 中的重大變更，Windows Forms 和 Windows Presentation Framework 應用程式現在使用 .NET SDK，而不是 .NET Core WinForms 和 WPF SDK。
ms.date: 09/18/2020
ms.openlocfilehash: 5f25be44c390abc173f155351d8cb007a6b370b0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760734"
---
# <a name="winforms-and-wpf-apps-use-microsoftnetsdk"></a>WinForms 和 WPF 應用程式使用 Microsoft .NET Sdk

Windows Forms 和 Windows Presentation Framework (WPF) 應用程式現在會使用 .NET SDK (`Microsoft.NET.Sdk`) ，而不是 .Net Core WinForms 和 WPF SDK (`Microsoft.NET.Sdk.WindowsDesktop`) 。

## <a name="change-description"></a>變更描述

在舊版的 .NET Core 中，WinForms 和 WPF 應用程式使用個別的 [專案 SDK](../../../project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`) 。 從 .NET 5.0 開始，WinForms 和 WPF SDK 已與 .NET SDK (`Microsoft.NET.Sdk`) 整合。 此外，新的 [目標 framework 標記 (TFM) ](../../../../standard/frameworks.md) 取代 `netcoreapp` 和 `netstandard` .net 5。 下列範例顯示覆位目標至 .NET 5.0 或更新版本時，您需要對 WPF 專案檔進行的變更。

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

## <a name="version-introduced"></a>引進的版本

.NET 5。0

## <a name="recommended-action"></a>建議的動作

在您的 WPF 或 Windows Forms 專案檔中：

- 將 `Sdk` 屬性更新為 `Microsoft.NET.Sdk` 。
- 將 `TargetFramework` 屬性更新為 `net5.0-windows` 。

## <a name="affected-apis"></a>受影響的 API

無法透過 API 分析偵測。

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
