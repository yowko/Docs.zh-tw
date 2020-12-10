---
title: 重大變更：環境。 OSVersion 傳回正確的作業系統版本
description: 瞭解核心 .NET 程式庫中的 .NET 5.0 重大變更，其中的環境會傳回作業系統的實際版本，而不是（例如，針對應用程式相容性所選取的作業系統）。
ms.date: 11/01/2020
ms.openlocfilehash: c810d9a7a028a0c60c30d69e78a9b9c695d933ef
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009517"
---
# <a name="environmentosversion-returns-the-correct-operating-system-version"></a><span data-ttu-id="1d76e-103">環境。 OSVersion 傳回正確的作業系統版本</span><span class="sxs-lookup"><span data-stu-id="1d76e-103">Environment.OSVersion returns the correct operating system version</span></span>

<span data-ttu-id="1d76e-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> 傳回作業系統 (OS) 的實際版本，例如針對應用程式相容性選取的作業系統。</span><span class="sxs-lookup"><span data-stu-id="1d76e-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system (OS) instead of, for example, the OS that's selected for application compatibility.</span></span>

## <a name="change-description"></a><span data-ttu-id="1d76e-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="1d76e-105">Change description</span></span>

<span data-ttu-id="1d76e-106">在舊版的 .NET 中， <xref:System.Environment.OSVersion?displayProperty=nameWithType> 當應用程式在 Windows 相容性模式下執行時，會傳回不正確的 OS 版本。</span><span class="sxs-lookup"><span data-stu-id="1d76e-106">In previous .NET versions, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns an OS version that may be incorrect when an application runs under Windows compatibility mode.</span></span> <span data-ttu-id="1d76e-107">如需詳細資訊，請參閱 [GetVersionExA 函數備註](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks)。</span><span class="sxs-lookup"><span data-stu-id="1d76e-107">For more information, see [GetVersionExA function remarks](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span></span> <span data-ttu-id="1d76e-108">在 macOS 上，傳回 <xref:System.Environment.OSVersion?displayProperty=nameWithType> 基礎 Darwin 核心版本。</span><span class="sxs-lookup"><span data-stu-id="1d76e-108">On macOS, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the underlying Darwin kernel version.</span></span>

<span data-ttu-id="1d76e-109">從 .NET 5.0 開始，會傳回 <xref:System.Environment.OSVersion?displayProperty=nameWithType> Windows 和 macOS 作業系統的實際版本。</span><span class="sxs-lookup"><span data-stu-id="1d76e-109">Starting in .NET 5.0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system for Windows and macOS.</span></span>

<span data-ttu-id="1d76e-110">下表顯示行為差異。</span><span class="sxs-lookup"><span data-stu-id="1d76e-110">The following table shows the difference in behavior.</span></span>

|  | <span data-ttu-id="1d76e-111">先前的 .NET 版本</span><span class="sxs-lookup"><span data-stu-id="1d76e-111">Previous .NET versions</span></span> | <span data-ttu-id="1d76e-112">.NET 5 +</span><span class="sxs-lookup"><span data-stu-id="1d76e-112">.NET 5+</span></span> |
|--|------------------------|---------|
| <span data-ttu-id="1d76e-113">Windows</span><span class="sxs-lookup"><span data-stu-id="1d76e-113">Windows</span></span> | <span data-ttu-id="1d76e-114">6.2.9200.0</span><span class="sxs-lookup"><span data-stu-id="1d76e-114">6.2.9200.0</span></span> | <span data-ttu-id="1d76e-115">10.0.19042.0</span><span class="sxs-lookup"><span data-stu-id="1d76e-115">10.0.19042.0</span></span> |
| <span data-ttu-id="1d76e-116">macOS</span><span class="sxs-lookup"><span data-stu-id="1d76e-116">macOS</span></span> | <span data-ttu-id="1d76e-117">19.6.0.0</span><span class="sxs-lookup"><span data-stu-id="1d76e-117">19.6.0.0</span></span> | <span data-ttu-id="1d76e-118">10.15.7</span><span class="sxs-lookup"><span data-stu-id="1d76e-118">10.15.7</span></span> |

## <a name="reason-for-change"></a><span data-ttu-id="1d76e-119">變更的原因</span><span class="sxs-lookup"><span data-stu-id="1d76e-119">Reason for change</span></span>

<span data-ttu-id="1d76e-120">這個屬性的使用者預期會傳回作業系統的實際版本。</span><span class="sxs-lookup"><span data-stu-id="1d76e-120">Users of this property expect it to return the actual version of the operating system.</span></span> <span data-ttu-id="1d76e-121">大部分的 .NET 應用程式不會在其應用程式資訊清單中指定其支援的版本，因此會從 dotnet 主機取得預設支援的版本。</span><span class="sxs-lookup"><span data-stu-id="1d76e-121">Most .NET apps don't specify their supported version in their application manifest, and thus get the default supported version from the dotnet host.</span></span> <span data-ttu-id="1d76e-122">因此，相容性填充碼對執行中的應用程式很有意義。</span><span class="sxs-lookup"><span data-stu-id="1d76e-122">As a result, the compatibility shim is rarely meaningful for the app that's running.</span></span> <span data-ttu-id="1d76e-123">當 Windows 發行新版本，而較舊的 dotnet 主機仍在使用中時，這些應用程式可能會得到不正確的 OS 版本。</span><span class="sxs-lookup"><span data-stu-id="1d76e-123">When Windows releases a new version and an older dotnet host is still in use, these apps may get an incorrect OS version.</span></span> <span data-ttu-id="1d76e-124">傳回實際版本與開發人員對此 API 的期望更具內嵌。</span><span class="sxs-lookup"><span data-stu-id="1d76e-124">Returning the actual version is more inline with developers' expectations of this API.</span></span>

<span data-ttu-id="1d76e-125">隨著在 <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType> .net 5.0 中引進、 <xref:System.OperatingSystem.IsMacOSVersionAtLeast%2A?displayProperty=nameWithType> 和， <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute?displayProperty=nameWithType> <xref:System.Environment.OSVersion?displayProperty=nameWithType> 已針對 Windows 和 macOS 變更為一致。</span><span class="sxs-lookup"><span data-stu-id="1d76e-125">With the introduction of <xref:System.OperatingSystem.IsWindowsVersionAtLeast%2A?displayProperty=nameWithType>, <xref:System.OperatingSystem.IsMacOSVersionAtLeast%2A?displayProperty=nameWithType>, and <xref:System.Runtime.Versioning.SupportedOSPlatformAttribute?displayProperty=nameWithType> in .NET 5.0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> was changed to be consistent for Windows and macOS.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="1d76e-126">引進的版本</span><span class="sxs-lookup"><span data-stu-id="1d76e-126">Version introduced</span></span>

<span data-ttu-id="1d76e-127">5.0</span><span class="sxs-lookup"><span data-stu-id="1d76e-127">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="1d76e-128">建議的動作</span><span class="sxs-lookup"><span data-stu-id="1d76e-128">Recommended action</span></span>

<span data-ttu-id="1d76e-129">請檢查並測試任何使用的程式碼， <xref:System.Environment.OSVersion?displayProperty=nameWithType> 以確保它會如預期運作。</span><span class="sxs-lookup"><span data-stu-id="1d76e-129">Review and test any code that uses <xref:System.Environment.OSVersion?displayProperty=nameWithType> to ensure it behaves as desired.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="1d76e-130">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="1d76e-130">Affected APIs</span></span>

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Environment.OSVersion`

-->
