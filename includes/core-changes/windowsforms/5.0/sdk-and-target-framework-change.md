---
ms.openlocfilehash: 975e331ad3e7bd7e0e8f49b62795c6acc7031ca9
ms.sourcegitcommit: 1e8382d0ce8b5515864f8fbb178b9fd692a7503f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2020
ms.locfileid: "89656328"
---
### <a name="winforms-and-wpf-apps-use-microsoftnetsdk"></a><span data-ttu-id="3704d-101">WinForms 和 WPF 應用程式使用 Microsoft .NET Sdk</span><span class="sxs-lookup"><span data-stu-id="3704d-101">WinForms and WPF apps use Microsoft.NET.Sdk</span></span>

<span data-ttu-id="3704d-102">Windows Forms 和 Windows Presentation Framework (WPF) 應用程式現在會使用 .NET SDK (`Microsoft.NET.Sdk`) ，而不是 .Net Core WinForms 和 WPF SDK (`Microsoft.NET.Sdk.WindowsDesktop`) 。</span><span class="sxs-lookup"><span data-stu-id="3704d-102">Windows Forms and Windows Presentation Framework (WPF) apps now use the .NET SDK (`Microsoft.NET.Sdk`) instead of the .NET Core WinForms and WPF SDK (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span>

#### <a name="change-description"></a><span data-ttu-id="3704d-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="3704d-103">Change description</span></span>

<span data-ttu-id="3704d-104">在舊版的 .NET Core 中，WinForms 和 WPF 應用程式使用個別的 [專案 SDK](../../../../docs/core/project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`) 。</span><span class="sxs-lookup"><span data-stu-id="3704d-104">In previous .NET Core versions, WinForms and WPF apps used a separate [project SDK](../../../../docs/core/project-sdk/overview.md) (`Microsoft.NET.Sdk.WindowsDesktop`).</span></span> <span data-ttu-id="3704d-105">從 .NET 5.0 開始，WinForms 和 WPF SDK 已與 .NET SDK (`Microsoft.NET.Sdk`) 整合。</span><span class="sxs-lookup"><span data-stu-id="3704d-105">Starting in .NET 5.0, the WinForms and WPF SDK has been unified with the .NET SDK (`Microsoft.NET.Sdk`).</span></span> <span data-ttu-id="3704d-106">此外，新的 [目標 framework 標記 (TFM) ](../../../../docs/standard/frameworks.md) 取代 `netcoreapp` 和 `netstandard` .net 5。</span><span class="sxs-lookup"><span data-stu-id="3704d-106">In addition, new [target framework monikers (TFM)](../../../../docs/standard/frameworks.md) replace `netcoreapp` and `netstandard` in .NET 5.</span></span> <span data-ttu-id="3704d-107">下列範例顯示覆位目標至 .NET 5.0 或更新版本時，您需要對 WPF 專案檔進行的變更。</span><span class="sxs-lookup"><span data-stu-id="3704d-107">The following example shows the changes you'd need to make for a WPF project file when retargeting to .NET 5.0 or later.</span></span>

<span data-ttu-id="3704d-108">在先前的 .NET Core 版本中：</span><span class="sxs-lookup"><span data-stu-id="3704d-108">In previous .NET Core versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="3704d-109">在 .NET 5.0 和更新版本中：</span><span class="sxs-lookup"><span data-stu-id="3704d-109">In .NET 5.0 and later versions:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>WinExe</OutputType>
    <TargetFramework>net5.0-windows</TargetFramework>
    <UseWPF>true</UseWPF>
  </PropertyGroup>

</Project>
```

#### <a name="version-introduced"></a><span data-ttu-id="3704d-110">引進的版本</span><span class="sxs-lookup"><span data-stu-id="3704d-110">Version introduced</span></span>

<span data-ttu-id="3704d-111">.NET 5.0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="3704d-111">.NET 5.0 Preview 8</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="3704d-112">建議的動作</span><span class="sxs-lookup"><span data-stu-id="3704d-112">Recommended action</span></span>

<span data-ttu-id="3704d-113">在您的 WPF 或 Windows Forms 專案檔中：</span><span class="sxs-lookup"><span data-stu-id="3704d-113">In your WPF or Windows Forms project file:</span></span>

- <span data-ttu-id="3704d-114">將 `Sdk` 屬性更新為 `Microsoft.NET.Sdk` 。</span><span class="sxs-lookup"><span data-stu-id="3704d-114">Update the `Sdk` attribute  to `Microsoft.NET.Sdk`.</span></span>
- <span data-ttu-id="3704d-115">將 `TargetFramework` 屬性更新為 `net5.0-windows` 。</span><span class="sxs-lookup"><span data-stu-id="3704d-115">Update the `TargetFramework` property to `net5.0-windows`.</span></span>

#### <a name="category"></a><span data-ttu-id="3704d-116">類別</span><span class="sxs-lookup"><span data-stu-id="3704d-116">Category</span></span>

- <span data-ttu-id="3704d-117">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3704d-117">Windows Forms</span></span>
- <span data-ttu-id="3704d-118">Windows Presentation Framework (WPF)</span><span class="sxs-lookup"><span data-stu-id="3704d-118">Windows Presentation Framework (WPF)</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="3704d-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="3704d-119">Affected APIs</span></span>

<span data-ttu-id="3704d-120">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="3704d-120">Not detectable via API analysis.</span></span>

<!-- 

#### Affected APIs

Not detectable via API analysis.

-->
