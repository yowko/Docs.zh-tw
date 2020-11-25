---
title: 重大變更：已從 .NET 中移除適用于 WinRT 的內建支援
description: 瞭解 .NET 5.0 中的 interop 重大變更，其中內建的 WinRT 支援已從 .NET 中移除。
ms.date: 10/13/2020
ms.openlocfilehash: 61d8e26d06c232a7bfa1891a2159f5232f747b8a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760718"
---
# <a name="built-in-support-for-winrt-is-removed-from-net"></a><span data-ttu-id="1704e-103">WinRT 的內建支援已從 .NET 移除</span><span class="sxs-lookup"><span data-stu-id="1704e-103">Built-in support for WinRT is removed from .NET</span></span>

<span data-ttu-id="1704e-104">已移除在 .NET 中使用 [Windows 執行時間 (WinRT) ](/uwp/winrt-cref/winrt-type-system) api 的內建支援。</span><span class="sxs-lookup"><span data-stu-id="1704e-104">Built-in support for consumption of [Windows runtime (WinRT)](/uwp/winrt-cref/winrt-type-system) APIs in .NET is removed.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="1704e-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="1704e-105">Version introduced</span></span>

<span data-ttu-id="1704e-106">5.0</span><span class="sxs-lookup"><span data-stu-id="1704e-106">5.0</span></span>

## <a name="change-description"></a><span data-ttu-id="1704e-107">變更描述</span><span class="sxs-lookup"><span data-stu-id="1704e-107">Change description</span></span>

<span data-ttu-id="1704e-108">先前，CoreCLR 可以使用 [ (WinMD) 檔案的 Windows 中繼資料](/uwp/winrt-cref/winmd-files) ，並使用 WinRT 類型。</span><span class="sxs-lookup"><span data-stu-id="1704e-108">Previously, CoreCLR could consume [Windows metadata (WinMD) files](/uwp/winrt-cref/winmd-files) to active and consume WinRT types.</span></span> <span data-ttu-id="1704e-109">從 .NET 5.0 開始，CoreCLR 無法再直接使用 WinMD 檔案。</span><span class="sxs-lookup"><span data-stu-id="1704e-109">Starting in .NET 5.0, CoreCLR can no longer consume WinMD files directly.</span></span>

<span data-ttu-id="1704e-110">如果您嘗試參考不支援的元件，您會收到 <xref:System.IO.FileNotFoundException> 。</span><span class="sxs-lookup"><span data-stu-id="1704e-110">If you attempt to reference an unsupported assembly, you'll get a <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="1704e-111">如果您啟用 WinRT 類別，您將會收到 <xref:System.PlatformNotSupportedException> 。</span><span class="sxs-lookup"><span data-stu-id="1704e-111">If you activate a WinRT class, you'll get a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="1704e-112">這項重大變更的原因如下：</span><span class="sxs-lookup"><span data-stu-id="1704e-112">This breaking change was made for the following reasons:</span></span>

- <span data-ttu-id="1704e-113">因此 WinRT 可以與 .NET 執行時間分開開發和改進。</span><span class="sxs-lookup"><span data-stu-id="1704e-113">So WinRT can be developed and improved separately from the .NET runtime.</span></span>
- <span data-ttu-id="1704e-114">針對其他作業系統（例如 iOS 和 Android）所提供的 interop 系統進行對稱。</span><span class="sxs-lookup"><span data-stu-id="1704e-114">For symmetry with interop systems provided for other operating systems, such as iOS and Android.</span></span>
- <span data-ttu-id="1704e-115">若要利用其他 .NET 功能，例如 c # 功能、中繼語言 (IL) 連結，以及預先 (的 AOT) 編譯。</span><span class="sxs-lookup"><span data-stu-id="1704e-115">To take advantage of other .NET features, such as C# features, intermediate language (IL) linking, and ahead-of-time (AOT) compilation.</span></span>
- <span data-ttu-id="1704e-116">以簡化 .NET 執行時間程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="1704e-116">To simplify the .NET runtime codebase.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="1704e-117">建議的動作</span><span class="sxs-lookup"><span data-stu-id="1704e-117">Recommended action</span></span>

- <span data-ttu-id="1704e-118">移除對 node.js [封裝](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts)的參考。</span><span class="sxs-lookup"><span data-stu-id="1704e-118">Remove references to the [Microsoft.Windows.SDK.Contracts package](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts).</span></span>  <span data-ttu-id="1704e-119">相反地，請透過專案的屬性，指定您想要存取的 Windows Api 版本 `TargetFramework` 。</span><span class="sxs-lookup"><span data-stu-id="1704e-119">Instead, specify the version of the Windows APIs that you want to access via the `TargetFramework` property of the project.</span></span>  <span data-ttu-id="1704e-120">例如：</span><span class="sxs-lookup"><span data-stu-id="1704e-120">For example:</span></span>

  ```xml
  <TargetFramework>net5.0-windows10.0.19041</TargetFramework>
  ```

- <span data-ttu-id="1704e-121">使用 [c #/WinRT](/windows/uwp/csharp-winrt/) 工具鏈來產生或自訂 .net 5.0 和更新版本的 WinRT api 和類型。</span><span class="sxs-lookup"><span data-stu-id="1704e-121">Use the [C#/WinRT](/windows/uwp/csharp-winrt/) tool chain to generate or customize WinRT APIs and types for .NET 5.0 and later versions.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="1704e-122">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1704e-122">Affected APIs</span></span>

- <xref:System.IO.WindowsRuntimeStorageExtensions?displayProperty=fullName>
- <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.WindowsRuntime?displayProperty=fullName>
- <xref:System.WindowsRuntimeSystemExtensions?displayProperty=fullName>
- <xref:Windows.Foundation.Point?displayProperty=fullName>
- <xref:Windows.Foundation.Size?displayProperty=fullName>
- <xref:Windows.UI.Color?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.IO.WindowsRuntimeStorageExtensions`
- `T: System.IO.WindowsRuntimeStreamExtensions`
- `N:System.Runtime.InteropServices.WindowsRuntime`
- `T:System.WindowsRuntimeSystemExtensions`
- `T:Windows.Foundation.Point`
- `T:Windows.Foundation.Size`
- `T:Windows.UI.Color`

### Category

Interop

-->
