---
title: 重大變更： WPF 和 WinForms 應用程式的 OutputType 設定為 WinExe
description: 瞭解 .NET 5.0 中的重大變更，其中的 OutputType 會自動設定為 WinExe，以供 Windows Forms apps 之用。
ms.date: 09/18/2020
ms.openlocfilehash: 7b2c7a76983c9e7958808e3cc4716be7792841c6
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/15/2020
ms.locfileid: "97513181"
---
# <a name="outputtype-set-to-winexe-for-wpf-and-winforms-apps"></a><span data-ttu-id="e4d89-103">適用于 WPF 和 WinForms 應用程式的 OutputType 設定為 WinExe</span><span class="sxs-lookup"><span data-stu-id="e4d89-103">OutputType set to WinExe for WPF and WinForms apps</span></span>

<span data-ttu-id="e4d89-104">`OutputType` 會自動設為， `WinExe` Windows Presentation Foundation (WPF) 和 Windows Forms 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e4d89-104">`OutputType` is automatically set to `WinExe` for Windows Presentation Foundation (WPF) and Windows Forms apps.</span></span> <span data-ttu-id="e4d89-105">當 `OutputType` 設定為時 `WinExe` ，在執行應用程式時，不會開啟主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="e4d89-105">When `OutputType` is set to `WinExe`, a console window doesn't open when the app is executed.</span></span>

## <a name="change-description"></a><span data-ttu-id="e4d89-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="e4d89-106">Change description</span></span>

<span data-ttu-id="e4d89-107">在舊版的 .NET SDK 中， `OutputType` 會使用在專案檔中所指定的值。</span><span class="sxs-lookup"><span data-stu-id="e4d89-107">In previous versions of the .NET SDK, the value that's specified for `OutputType` in the project file is used.</span></span> <span data-ttu-id="e4d89-108">例如︰</span><span class="sxs-lookup"><span data-stu-id="e4d89-108">For example:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="e4d89-109">從 .NET SDK 的5.0.1 版開始， `OutputType` 會 `WinExe` 針對 WPF 以及以任何 framework 版本為目標的 Windows Forms 應用程式自動設定為，包括 .NET Framework。</span><span class="sxs-lookup"><span data-stu-id="e4d89-109">Starting in the 5.0.1 version of the .NET SDK, `OutputType` is automatically set to `WinExe` for WPF and Windows Forms apps that target any framework version, including .NET Framework.</span></span> <span data-ttu-id="e4d89-110">例如︰</span><span class="sxs-lookup"><span data-stu-id="e4d89-110">For example:</span></span>

```xml
<PropertyGroup>
  <OutputType>WinExe</OutputType>
</PropertyGroup>
```

## <a name="reason-for-change"></a><span data-ttu-id="e4d89-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="e4d89-111">Reason for change</span></span>

<span data-ttu-id="e4d89-112">假設在執行 WPF 或 Windows Forms 應用程式時，大部分的使用者不希望主控台視窗開啟。</span><span class="sxs-lookup"><span data-stu-id="e4d89-112">It's assumed that most users don't want a console window to open when a WPF or Windows Forms app is executed.</span></span> <span data-ttu-id="e4d89-113">此外， [現在這些應用程式類型會使用 .NET sdk](sdk-and-target-framework-change.md) ，而不是使用 WINDOWS 桌面 sdk，因此會設定正確的預設值。</span><span class="sxs-lookup"><span data-stu-id="e4d89-113">In addition, [now that these application types use the .NET SDK](sdk-and-target-framework-change.md) instead of the Windows Desktop SDK, the correct default will be set.</span></span> <span data-ttu-id="e4d89-114">此外，當新增以 iOS 和 Android 為目標的支援時，如果在多個平臺上都使用相同的輸出類型，就會比較容易使用多個平臺。</span><span class="sxs-lookup"><span data-stu-id="e4d89-114">Further, when support for targeting iOS and Android is added, it will be easier to multi-target between multiple platforms if they all use the same output type.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="e4d89-115">引進的版本</span><span class="sxs-lookup"><span data-stu-id="e4d89-115">Version introduced</span></span>

<span data-ttu-id="e4d89-116">.NET 5.0。1</span><span class="sxs-lookup"><span data-stu-id="e4d89-116">.NET 5.0.1</span></span>

## <a name="recommended-action"></a><span data-ttu-id="e4d89-117">建議的動作</span><span class="sxs-lookup"><span data-stu-id="e4d89-117">Recommended action</span></span>

<span data-ttu-id="e4d89-118">在您的部分中不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="e4d89-118">No action is required in your part.</span></span> <span data-ttu-id="e4d89-119">但是，如果您想要還原為舊的行為，請 `DisableWinExeOutputInference` 在專案檔中將屬性設為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="e4d89-119">However, if you want to revert to the old behavior, set the `DisableWinExeOutputInference` property to `true` in your project file.</span></span>

```xml
<DisableWinExeOutputInference>true</DisableWinExeOutputInference>
```

## <a name="affected-apis"></a><span data-ttu-id="e4d89-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e4d89-120">Affected APIs</span></span>

<span data-ttu-id="e4d89-121">無法透過 API 分析偵測。</span><span class="sxs-lookup"><span data-stu-id="e4d89-121">Not detectable via API analysis.</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

- Windows Forms
- Windows Presentation Framework (WPF)

-->
