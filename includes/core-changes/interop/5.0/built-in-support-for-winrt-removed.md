---
ms.openlocfilehash: 47c676122df4f0990949a7bfbcd7af8c6144d870
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160529"
---
### <a name="built-in-support-for-winrt-is-removed-from-net"></a><span data-ttu-id="31a64-101">WinRT 的內建支援已從 .NET 移除</span><span class="sxs-lookup"><span data-stu-id="31a64-101">Built-in support for WinRT is removed from .NET</span></span>

<span data-ttu-id="31a64-102">已移除在 .NET 中使用 [Windows 執行時間 (WinRT) ](/uwp/winrt-cref/winrt-type-system) api 的內建支援。</span><span class="sxs-lookup"><span data-stu-id="31a64-102">Built-in support for consumption of [Windows runtime (WinRT)](/uwp/winrt-cref/winrt-type-system) APIs in .NET is removed.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="31a64-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="31a64-103">Version introduced</span></span>

<span data-ttu-id="31a64-104">5.0 Preview 6</span><span class="sxs-lookup"><span data-stu-id="31a64-104">5.0 Preview 6</span></span>

#### <a name="change-description"></a><span data-ttu-id="31a64-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="31a64-105">Change description</span></span>

<span data-ttu-id="31a64-106">先前，CoreCLR 可以使用 [ (WinMD) 檔案的 Windows 中繼資料](/uwp/winrt-cref/winmd-files) ，並使用 WinRT 類型。</span><span class="sxs-lookup"><span data-stu-id="31a64-106">Previously, CoreCLR could consume [Windows metadata (WinMD) files](/uwp/winrt-cref/winmd-files) to active and consume WinRT types.</span></span> <span data-ttu-id="31a64-107">從 .NET 5.0 開始，CoreCLR 無法再直接使用 WinMD 檔案。</span><span class="sxs-lookup"><span data-stu-id="31a64-107">Starting in .NET 5.0, CoreCLR can no longer consume WinMD files directly.</span></span>

<span data-ttu-id="31a64-108">如果您嘗試參考不支援的元件，您會收到 <xref:System.IO.FileNotFoundException> 。</span><span class="sxs-lookup"><span data-stu-id="31a64-108">If you attempt to reference an unsupported assembly, you'll get a <xref:System.IO.FileNotFoundException>.</span></span> <span data-ttu-id="31a64-109">如果您啟用 WinRT 類別，您將會收到 <xref:System.PlatformNotSupportedException> 。</span><span class="sxs-lookup"><span data-stu-id="31a64-109">If you activate a WinRT class, you'll get a <xref:System.PlatformNotSupportedException>.</span></span>

<span data-ttu-id="31a64-110">這項重大變更的原因如下：</span><span class="sxs-lookup"><span data-stu-id="31a64-110">This breaking change was made for the following reasons:</span></span>

- <span data-ttu-id="31a64-111">因此 WinRT 可以與 .NET 執行時間分開開發和改進。</span><span class="sxs-lookup"><span data-stu-id="31a64-111">So WinRT can be developed and improved separately from the .NET runtime.</span></span>
- <span data-ttu-id="31a64-112">針對其他作業系統（例如 iOS 和 Android）所提供的 interop 系統進行對稱。</span><span class="sxs-lookup"><span data-stu-id="31a64-112">For symmetry with interop systems provided for other operating systems, such as iOS and Android.</span></span>
- <span data-ttu-id="31a64-113">若要利用其他 .NET 功能，例如 c # 功能、中繼語言 (IL) 連結，以及預先 (的 AOT) 編譯。</span><span class="sxs-lookup"><span data-stu-id="31a64-113">To take advantage of other .NET features, such as C# features, intermediate language (IL) linking, and ahead-of-time (AOT) compilation.</span></span>
- <span data-ttu-id="31a64-114">以簡化 .NET 執行時間程式碼基底。</span><span class="sxs-lookup"><span data-stu-id="31a64-114">To simplify the .NET runtime codebase.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="31a64-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="31a64-115">Recommended action</span></span>

- <span data-ttu-id="31a64-116">移除對 node.js [封裝](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts)的參考。</span><span class="sxs-lookup"><span data-stu-id="31a64-116">Remove references to the [Microsoft.Windows.SDK.Contracts package](https://www.nuget.org/packages/Microsoft.Windows.SDK.Contracts).</span></span>  <span data-ttu-id="31a64-117">相反地，請透過專案的屬性，指定您想要存取的 Windows Api 版本 `TargetFramework` 。</span><span class="sxs-lookup"><span data-stu-id="31a64-117">Instead, specify the version of the Windows APIs that you want to access via the `TargetFramework` property of the project.</span></span>  <span data-ttu-id="31a64-118">例如：</span><span class="sxs-lookup"><span data-stu-id="31a64-118">For example:</span></span>

  ```xml
  <TargetFramework>net5.0-windows10.0.19041</TargetFramework>
  ```

- <span data-ttu-id="31a64-119">使用 [c #/WinRT](/windows/uwp/csharp-winrt/) 工具鏈來產生或自訂 .net 5.0 和更新版本的 WinRT api 和類型。</span><span class="sxs-lookup"><span data-stu-id="31a64-119">Use the [C#/WinRT](/windows/uwp/csharp-winrt/) tool chain to generate or customize WinRT APIs and types for .NET 5.0 and later versions.</span></span>

#### <a name="category"></a><span data-ttu-id="31a64-120">類別</span><span class="sxs-lookup"><span data-stu-id="31a64-120">Category</span></span>

<span data-ttu-id="31a64-121">Interop</span><span class="sxs-lookup"><span data-stu-id="31a64-121">Interop</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="31a64-122">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="31a64-122">Affected APIs</span></span>

- <xref:System.IO.WindowsRuntimeStorageExtensions?displayProperty=fullName>
- <xref:System.IO.WindowsRuntimeStreamExtensions?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.WindowsRuntime?displayProperty=fullName>
- <xref:System.WindowsRuntimeSystemExtensions?displayProperty=fullName>
- <xref:Windows.Foundation.Point?displayProperty=fullName>
- <xref:Windows.Foundation.Size?displayProperty=fullName>
- <xref:Windows.UI.Color?displayProperty=fullName>

<!--

#### Affected APIs

- `T:System.IO.WindowsRuntimeStorageExtensions`
- `T: System.IO.WindowsRuntimeStreamExtensions`
- `N:System.Runtime.InteropServices.WindowsRuntime`
- `T:System.WindowsRuntimeSystemExtensions`
- `T:Windows.Foundation.Point`
- `T:Windows.Foundation.Size`
- `T:Windows.UI.Color`

-->
