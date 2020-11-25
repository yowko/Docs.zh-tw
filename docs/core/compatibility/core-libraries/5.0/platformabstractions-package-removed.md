---
title: 重大變更：已移除 DotNet PlatformAbstractions 套件
description: 瞭解已移除 DotNet PlatformAbstractions 封裝的核心 .NET 程式庫中的 .NET 5.0 重大變更。
ms.date: 11/01/2020
ms.openlocfilehash: 38ffe5e592d01c3bae14fc41becb594283b975a3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760704"
---
# <a name="microsoftdotnetplatformabstractions-package-removed"></a><span data-ttu-id="26e76-103">已移除 DotNet PlatformAbstractions 套件</span><span class="sxs-lookup"><span data-stu-id="26e76-103">Microsoft.DotNet.PlatformAbstractions package removed</span></span>

<span data-ttu-id="26e76-104">將不會產生任何新版本的 [DotNet. PlatformAbstractions NuGet 套件](https://www.nuget.org/packages/Microsoft.DotNet.PlatformAbstractions/) 。</span><span class="sxs-lookup"><span data-stu-id="26e76-104">No new versions of the [Microsoft.DotNet.PlatformAbstractions NuGet package](https://www.nuget.org/packages/Microsoft.DotNet.PlatformAbstractions/) will be produced.</span></span>

## <a name="change-description"></a><span data-ttu-id="26e76-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="26e76-105">Change description</span></span>

<span data-ttu-id="26e76-106">先前，新版本的連結 <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> 庫是隨著新版本的 .Net Core 一起產生。</span><span class="sxs-lookup"><span data-stu-id="26e76-106">Previously, new versions of the <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> library were produced alongside new versions of .NET Core.</span></span> <span data-ttu-id="26e76-107">未來，將不會在程式庫中新增任何新功能，也不會發行任何新的主要版本。</span><span class="sxs-lookup"><span data-stu-id="26e76-107">Going forward, no new functionality will be added to the library, and no new major versions will be released.</span></span> <span data-ttu-id="26e76-108">不過，現有的程式庫版本將繼續運作並提供服務。</span><span class="sxs-lookup"><span data-stu-id="26e76-108">However, existing versions of the library will continue to work and be serviced.</span></span>

<span data-ttu-id="26e76-109">連結 <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> 庫與已在 system.string 中建立的 api 重迭 \* 。</span><span class="sxs-lookup"><span data-stu-id="26e76-109">The <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> library overlaps with APIs that are already established in the System.\* namespaces.</span></span> <span data-ttu-id="26e76-110">此外，有些 <xref:Microsoft.DotNet.PlatformAbstractions> api 的設計並不是使用與系統其餘部分相同的審查層級和長期可支援性。 \* Api。</span><span class="sxs-lookup"><span data-stu-id="26e76-110">Also, some <xref:Microsoft.DotNet.PlatformAbstractions> APIs weren't designed with the same level of scrutiny and long-term supportability as the rest of the System.\* APIs.</span></span> <span data-ttu-id="26e76-111">例如，會 <xref:Microsoft.DotNet.PlatformAbstractions> 使用 `Platform` 列舉來描述目前的作業系統平臺。</span><span class="sxs-lookup"><span data-stu-id="26e76-111">For example, <xref:Microsoft.DotNet.PlatformAbstractions> uses the `Platform` enumeration to describe the current operating system platform.</span></span> <span data-ttu-id="26e76-112">設計 API 時，已明確拒絕此列舉設計 <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> ，以允許新的平臺和未來的彈性。</span><span class="sxs-lookup"><span data-stu-id="26e76-112">This enumeration design was explicitly rejected when the <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> API was designed, to allow for new platforms and future flexibility.</span></span>

<span data-ttu-id="26e76-113">程式庫所啟用的案例 <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> 現在可能沒有它。</span><span class="sxs-lookup"><span data-stu-id="26e76-113">The scenarios enabled by the <xref:Microsoft.DotNet.PlatformAbstractions?displayProperty=fullName> library are now possible without it.</span></span> <span data-ttu-id="26e76-114">現有的版本會繼續運作，即使是在 .NET 5.0 和更新版本中，也會隨著舊版的 .NET Core 服務。</span><span class="sxs-lookup"><span data-stu-id="26e76-114">Existing versions will continue to work, even in .NET 5.0 and later, and will be serviced along with previous versions of .NET Core.</span></span> <span data-ttu-id="26e76-115">但是，不會將新功能新增至程式庫。</span><span class="sxs-lookup"><span data-stu-id="26e76-115">However, new functionality won't be added to the library.</span></span> <span data-ttu-id="26e76-116">相反地，會將新功能新增至其他程式庫和 Api。</span><span class="sxs-lookup"><span data-stu-id="26e76-116">Instead, new functionality will be added to other libraries and APIs.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="26e76-117">引進的版本</span><span class="sxs-lookup"><span data-stu-id="26e76-117">Version introduced</span></span>

<span data-ttu-id="26e76-118">5.0</span><span class="sxs-lookup"><span data-stu-id="26e76-118">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="26e76-119">建議的動作</span><span class="sxs-lookup"><span data-stu-id="26e76-119">Recommended action</span></span>

- <span data-ttu-id="26e76-120">如果程式庫符合您的需求，則可以繼續使用較舊版本的程式庫。</span><span class="sxs-lookup"><span data-stu-id="26e76-120">You can continue to use older versions of the library if they meet your requirements.</span></span>

- <span data-ttu-id="26e76-121">如果較舊的版本不符合您的需求，請 `PlatformAbstractions` 使用建議的取代取代 api 的使用方式。</span><span class="sxs-lookup"><span data-stu-id="26e76-121">If the older versions don't meet your requirements, replace usages of the `PlatformAbstractions` APIs with the recommended replacements.</span></span>

  | <span data-ttu-id="26e76-122">`PlatformAbstractions` Api</span><span class="sxs-lookup"><span data-stu-id="26e76-122">`PlatformAbstractions` API</span></span> | <span data-ttu-id="26e76-123">建議取代</span><span class="sxs-lookup"><span data-stu-id="26e76-123">Recommended replacement</span></span> |
  |-|-|
  | `ApplicationEnvironment.ApplicationBasePath` | <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> |
  | <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner> | <xref:System.HashCode?displayProperty=nameWithType> |
  | `RuntimeEnvironment.GetRuntimeIdentifier()` | <xref:System.Runtime.InteropServices.RuntimeInformation.RuntimeIdentifier?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemPlatform` | <xref:System.Runtime.InteropServices.RuntimeInformation.IsOSPlatform(System.Runtime.InteropServices.OSPlatform)?displayProperty=nameWithType> |
  | `RuntimeEnvironment.RuntimeArchitecture` | <xref:System.Runtime.InteropServices.RuntimeInformation.ProcessArchitecture?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystem` | <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> |
  | `RuntimeEnvironment.OperatingSystemVersion` | <span data-ttu-id="26e76-124"><xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> 和 <xref:System.Environment.OSVersion?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="26e76-124"><xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> and <xref:System.Environment.OSVersion?displayProperty=nameWithType></span></span> |

  > [!NOTE]
  > <span data-ttu-id="26e76-125">和的大部分使用 `RuntimeEnvironment.OperatingSystem` 案例 `RuntimeEnvironment.OperatingSystemVersion` 都是基於顯示目的，例如顯示給使用者、記錄和遙測。</span><span class="sxs-lookup"><span data-stu-id="26e76-125">Most use cases for `RuntimeEnvironment.OperatingSystem` and `RuntimeEnvironment.OperatingSystemVersion` are for display purposes, for example, displaying to a user, logging, and telemetry.</span></span> <span data-ttu-id="26e76-126">不建議您根據作業系統) 版本 (作業系統進行執行時間決策。</span><span class="sxs-lookup"><span data-stu-id="26e76-126">It's not recommended to make run-time decisions based on an operating system (OS) version.</span></span> <span data-ttu-id="26e76-127"><xref:System.Environment.OSVersion?displayProperty=nameWithType> 現在會傳回適用于 Windows 和 macOS 作業系統 [的正確版本](environment-osversion-returns-correct-version.md) 。</span><span class="sxs-lookup"><span data-stu-id="26e76-127"><xref:System.Environment.OSVersion?displayProperty=nameWithType> now [returns the correct version](environment-osversion-returns-correct-version.md) for Windows and macOS operating systems.</span></span> <span data-ttu-id="26e76-128">不過，對於大多數的 Unix 散發套件來說，視為「作業系統版本」的內容並不直接。</span><span class="sxs-lookup"><span data-stu-id="26e76-128">However, for most Unix distributions, what is considered to be the "OS version" is not as straightforward.</span></span> <span data-ttu-id="26e76-129">例如，它可以是 Linux 核心版本，也可以是發行版本版本。</span><span class="sxs-lookup"><span data-stu-id="26e76-129">For example, it could be the Linux kernel version, or it could be the distro version.</span></span> <span data-ttu-id="26e76-130">適用于大部分的 Unix 平臺， <xref:System.Environment.OSVersion?displayProperty=nameWithType> 並 <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> 傳回所傳回的版本 `uname` 。</span><span class="sxs-lookup"><span data-stu-id="26e76-130">For most Unix platforms, <xref:System.Environment.OSVersion?displayProperty=nameWithType> and <xref:System.Runtime.InteropServices.RuntimeInformation.OSDescription?displayProperty=nameWithType> return the version that's returned by `uname`.</span></span> <span data-ttu-id="26e76-131">若要取得 Linux 發行版本名稱和版本資訊，建議的方法是讀取 */etc/os-release* 檔案。</span><span class="sxs-lookup"><span data-stu-id="26e76-131">To get the Linux distro name and version information, the recommended approach is to read the */etc/os-release* file.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="26e76-132">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="26e76-132">Affected APIs</span></span>

- `Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- <xref:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner?displayProperty=fullName>
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier()`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:Microsoft.DotNet.PlatformAbstractions.ApplicationEnvironment.ApplicationBasePath`
- `T:Microsoft.DotNet.PlatformAbstractions.HashCodeCombiner`
- `M:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.GetRuntimeIdentifier`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystem`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemPlatform`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.OperatingSystemVersion`
- `P:Microsoft.DotNet.PlatformAbstractions.RuntimeEnvironment.RuntimeArchitecture`

-->
