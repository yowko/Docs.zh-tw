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
# <a name="winforms-and-wpf-apps-use-microsoftnetsdk"></a><span data-ttu-id="6f0b3-103">WinForms 和 WPF 應用程式使用 Microsoft .NET Sdk</span><span class="sxs-lookup"><span data-stu-id="6f0b3-103">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>

<span data-ttu-id="6f0b3-104">Windows Forms 和 Windows Presentation Framework (WPF) 應用程式現在會使用 .NET SDK (`Microsoft.NET.Sdk`) ，而不是 .Net Core WinForms 和 WPF SDK (`Microsoft.NET.Sdk.WindowsDesktop`) 。</span><span class="sxs-lookup"><span data-stu-id="6f0b3-104">Windows Forms and Windows Presentation Framework (WPF) apps now use the .NET SDK (`Microsoft.NET.Sdk`) instead of the .NET Core WinForms and WPF SDK (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span>

## <a name="change-description"></a><span data-ttu-id="6f0b3-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="6f0b3-105">Change description</span></span>

<span data-ttu-id="6f0b3-106">在舊版的 .NET Core 中，WinForms 和 WPF 應用程式使用個別的 [專案 SDK](../../../project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`) 。</span><span class="sxs-lookup"><span data-stu-id="6f0b3-106">In previous .NET Core versions, WinForms and WPF apps used a separate [project SDK](../../../project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span> <span data-ttu-id="6f0b3-107">從 .NET 5.0 開始，WinForms 和 WPF SDK 已與 .NET SDK (`Microsoft.NET.Sdk`) 整合。</span><span class="sxs-lookup"><span data-stu-id="6f0b3-107">Starting in .NET 5.0, the WinForms and WPF SDK has been unified with the .NET SDK (`Microsoft.NET.Sdk`).</span></span> <span data-ttu-id="6f0b3-108">此外，新的 [目標 framework 標記 (TFM) ](../../../../standard/frameworks.md) 取代 `netcoreapp` 和 `netstandard` .net 5。</span><span class="sxs-lookup"><span data-stu-id="6f0b3-108">In addition, new [target framework monikers (TFM)](../../../../standard/frameworks.md) replace `netcoreapp` and `netstandard` in .NET 5.</span></span> <span data-ttu-id="6f0b3-109">下列範例顯示覆位目標至 .NET 5.0 或更新版本時，您需要對 WPF 專案檔進行的變更。</span><span class="sxs-lookup"><span data-stu-id="6f0b3-109">The following example shows the changes you'd need to make for a WPF project file when retargeting to .NET 5.0 or later.</span></span>

<span data-ttu-id="6f0b3-110">在先前的 .NET Core 版本中：</span><span class="sxs-lookup"><span data-stu-id="6f0b3-110">In previous .NET Core versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="6f0b3-111">在 .NET 5.0 和更新版本中：</span><span class="sxs-lookup"><span data-stu-id="6f0b3-111">In .NET 5.0 and later versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

## <a name="version-introduced"></a><span data-ttu-id="6f0b3-112">引進的版本</span><span class="sxs-lookup"><span data-stu-id="6f0b3-112">Version introduced</span></span>

<span data-ttu-id="6f0b3-113">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="6f0b3-113">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="6f0b3-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="6f0b3-114">Recommended action</span></span>

<span data-ttu-id="6f0b3-115">在您的 WPF 或 Windows Forms 專案檔中：</span><span class="sxs-lookup"><span data-stu-id="6f0b3-115">In your WPF or Windows Forms project file:</span></span>

- <span data-ttu-id="6f0b3-116">將 `Sdk` 屬性更新為 `Microsoft.NET.Sdk` 。</span><span class="sxs-lookup"><span data-stu-id="6f0b3-116">Update the `Sdk` attribute  to `Microsoft.NET.Sdk`.</span></span>
- <span data-ttu-id="6f0b3-117">將 `TargetFramework` 屬性更新為 `net5.0-windows` 。</span><span class="sxs-lookup"><span data-stu-id="6f0b3-117">Update the `TargetFramework` property to `net5.0-windows`.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="6f0b3-118">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="6f0b3-118">Affected APIs</span></span>

<span data-ttu-id="6f0b3-119">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="6f0b3-119">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
