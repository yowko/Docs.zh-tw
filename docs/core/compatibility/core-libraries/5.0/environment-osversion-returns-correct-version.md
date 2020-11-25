---
title: 重大變更：環境。 OSVersion 傳回正確的作業系統版本
description: 瞭解核心 .NET 程式庫中的 .NET 5.0 重大變更，其中的環境會傳回作業系統的實際版本，而不是（例如，針對應用程式相容性所選取的作業系統）。
ms.date: 11/01/2020
ms.openlocfilehash: b78ca1c7be50f76b99b5558a976d8f00e2f560c3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760802"
---
# <a name="environmentosversion-returns-the-correct-operating-system-version"></a><span data-ttu-id="62d15-103">環境。 OSVersion 傳回正確的作業系統版本</span><span class="sxs-lookup"><span data-stu-id="62d15-103">Environment.OSVersion returns the correct operating system version</span></span>

<span data-ttu-id="62d15-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> 傳回作業系統 (OS) 的實際版本，例如針對應用程式相容性選取的作業系統。</span><span class="sxs-lookup"><span data-stu-id="62d15-104"><xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system (OS) instead of, for example, the OS that's selected for application compatibility.</span></span>

## <a name="change-description"></a><span data-ttu-id="62d15-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="62d15-105">Change description</span></span>

<span data-ttu-id="62d15-106">在舊版的 .NET 中， <xref:System.Environment.OSVersion?displayProperty=nameWithType> 當應用程式在 Windows 相容性模式下執行時，會傳回不正確的 OS 版本。</span><span class="sxs-lookup"><span data-stu-id="62d15-106">In previous .NET versions, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns an OS version that may be incorrect when an application runs under Windows compatibility mode.</span></span> <span data-ttu-id="62d15-107">如需詳細資訊，請參閱 [GetVersionExA 函數備註](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks)。</span><span class="sxs-lookup"><span data-stu-id="62d15-107">For more information, see [GetVersionExA function remarks](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getversionexa#remarks).</span></span>

<span data-ttu-id="62d15-108">從 .NET 5.0 開始，會傳回 <xref:System.Environment.OSVersion?displayProperty=nameWithType> 作業系統的實際版本。</span><span class="sxs-lookup"><span data-stu-id="62d15-108">Starting in .NET 5.0, <xref:System.Environment.OSVersion?displayProperty=nameWithType> returns the actual version of the operating system.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="62d15-109">變更的原因</span><span class="sxs-lookup"><span data-stu-id="62d15-109">Reason for change</span></span>

<span data-ttu-id="62d15-110">這個屬性的使用者預期會傳回作業系統的實際版本。</span><span class="sxs-lookup"><span data-stu-id="62d15-110">Users of this property expect it to return the actual version of the operating system.</span></span> <span data-ttu-id="62d15-111">大部分的 .NET 應用程式不會在其應用程式資訊清單中指定其支援的版本，因此會從 dotnet 主機取得預設支援的版本。</span><span class="sxs-lookup"><span data-stu-id="62d15-111">Most .NET apps don't specify their supported version in their application manifest, and thus get the default supported version from the dotnet host.</span></span> <span data-ttu-id="62d15-112">因此，相容性填充碼對執行中的應用程式很有意義。</span><span class="sxs-lookup"><span data-stu-id="62d15-112">As a result, the compatibility shim is rarely meaningful for the app that's running.</span></span> <span data-ttu-id="62d15-113">當 Windows 發行新版本，而較舊的 dotnet 主機仍在使用中時，這些應用程式可能會得到不正確的 OS 版本。</span><span class="sxs-lookup"><span data-stu-id="62d15-113">When Windows releases a new version and an older dotnet host is still in use, these apps may get an incorrect OS version.</span></span> <span data-ttu-id="62d15-114">傳回實際版本與開發人員對此 API 的期望更具內嵌。</span><span class="sxs-lookup"><span data-stu-id="62d15-114">Returning the actual version is more inline with developers' expectations of this API.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="62d15-115">引進的版本</span><span class="sxs-lookup"><span data-stu-id="62d15-115">Version introduced</span></span>

<span data-ttu-id="62d15-116">5.0</span><span class="sxs-lookup"><span data-stu-id="62d15-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="62d15-117">建議的動作</span><span class="sxs-lookup"><span data-stu-id="62d15-117">Recommended action</span></span>

<span data-ttu-id="62d15-118">請檢查並測試任何使用的程式碼， <xref:System.Environment.OSVersion?displayProperty=nameWithType> 以確保它會如預期運作。</span><span class="sxs-lookup"><span data-stu-id="62d15-118">Review and test any code that uses <xref:System.Environment.OSVersion?displayProperty=nameWithType> to ensure it behaves as desired.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="62d15-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="62d15-119">Affected APIs</span></span>

- <xref:System.Environment.OSVersion?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Environment.OSVersion`

-->
