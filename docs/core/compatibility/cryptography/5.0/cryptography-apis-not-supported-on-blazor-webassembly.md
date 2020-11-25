---
title: 重大變更： Blazor WebAssembly 不支援密碼編譯 Api
description: 瞭解 .NET 5.0 中的重大變更，也就是在瀏覽器上執行密碼編譯 Api 時，會擲回例外狀況。
ms.date: 09/16/2020
ms.openlocfilehash: ec10fa777e91f641b5582378830536a0cfa8dd72
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760463"
---
# <a name="systemsecuritycryptography-apis-not-supported-on-blazor-webassembly"></a><span data-ttu-id="dcfaa-103">Blazor WebAssembly 不支援的密碼編譯 Api</span><span class="sxs-lookup"><span data-stu-id="dcfaa-103">System.Security.Cryptography APIs not supported on Blazor WebAssembly</span></span>

<span data-ttu-id="dcfaa-104"><xref:System.Security.Cryptography> Api 會在 <xref:System.PlatformNotSupportedException> 執行時間于瀏覽器上執行時擲回。</span><span class="sxs-lookup"><span data-stu-id="dcfaa-104"><xref:System.Security.Cryptography> APIs throw a <xref:System.PlatformNotSupportedException> at run time when run on a browser.</span></span>

## <a name="change-description"></a><span data-ttu-id="dcfaa-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="dcfaa-105">Change description</span></span>

<span data-ttu-id="dcfaa-106">在舊版的 .NET 中，大部分的 <xref:System.Security.Cryptography> api 無法用來 Blazor WebAssembly 應用程式。</span><span class="sxs-lookup"><span data-stu-id="dcfaa-106">In previous .NET versions, most of the <xref:System.Security.Cryptography> APIs aren't available to Blazor WebAssembly apps.</span></span> <span data-ttu-id="dcfaa-107">從 .NET 5.0 開始，Blazor WebAssembly apps 會以完整的 .NET 5 API 介面區為目標，不過，由於瀏覽器沙箱條件約束，不支援所有的 .NET 5 Api。</span><span class="sxs-lookup"><span data-stu-id="dcfaa-107">Starting in .NET 5.0, Blazor WebAssembly apps target the full .NET 5 API surface area, however, not all .NET 5 APIs are supported due to browser sandbox constraints.</span></span> <span data-ttu-id="dcfaa-108">在 .NET 5.0 和更新版本中，不支援的 api 會在 <xref:System.Security.Cryptography> <xref:System.PlatformNotSupportedException> WebAssembly 上執行時擲回。</span><span class="sxs-lookup"><span data-stu-id="dcfaa-108">In .NET 5.0 and later versions, the unsupported <xref:System.Security.Cryptography> APIs throw a <xref:System.PlatformNotSupportedException> when running on WebAssembly.</span></span>

> [!TIP]
> <span data-ttu-id="dcfaa-109">當您建立支援瀏覽器平臺的專案時， [平臺相容性分析器](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md) 會將任何對受影響 api 的呼叫加上旗標。</span><span class="sxs-lookup"><span data-stu-id="dcfaa-109">The [Platform compatibility analyzer](../../code-analysis/5.0/ca1416-platform-compatibility-analyzer.md) will flag any calls to the affected APIs when you build a project that supports the browser platform.</span></span> <span data-ttu-id="dcfaa-110">此分析器預設會在 .NET 5.0 和更新版本的應用程式中執行。</span><span class="sxs-lookup"><span data-stu-id="dcfaa-110">This analyzer runs by default in .NET 5.0 and later apps.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="dcfaa-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="dcfaa-111">Reason for change</span></span>

<span data-ttu-id="dcfaa-112">Microsoft 無法以 Blazor WebAssembly 設定中的相依性來傳送 OpenSSL。</span><span class="sxs-lookup"><span data-stu-id="dcfaa-112">Microsoft is unable to ship OpenSSL as a dependency in the Blazor WebAssembly configuration.</span></span> <span data-ttu-id="dcfaa-113">我們嘗試與瀏覽器的 API 整合來解決此問題 `SubtleCrypto` 。</span><span class="sxs-lookup"><span data-stu-id="dcfaa-113">We attempted to work around this by trying to integrate with the browser's `SubtleCrypto` API.</span></span> <span data-ttu-id="dcfaa-114">可惜的是，它需要大量的 API 變更，使其難以整合。</span><span class="sxs-lookup"><span data-stu-id="dcfaa-114">Unfortunately, it required significant API changes that made it too hard to integrate.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="dcfaa-115">引進的版本</span><span class="sxs-lookup"><span data-stu-id="dcfaa-115">Version introduced</span></span>

<span data-ttu-id="dcfaa-116">5.0</span><span class="sxs-lookup"><span data-stu-id="dcfaa-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="dcfaa-117">建議的動作</span><span class="sxs-lookup"><span data-stu-id="dcfaa-117">Recommended action</span></span>

<span data-ttu-id="dcfaa-118">目前沒有建議的好方法可提供建議。</span><span class="sxs-lookup"><span data-stu-id="dcfaa-118">There are no good workarounds to suggest at this time.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="dcfaa-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="dcfaa-119">Affected APIs</span></span>

<span data-ttu-id="dcfaa-120"><xref:System.Security.Cryptography?displayProperty=fullName>除了下列以外的所有 api：</span><span class="sxs-lookup"><span data-stu-id="dcfaa-120">All <xref:System.Security.Cryptography?displayProperty=fullName> APIs except the following:</span></span>

- `System.Security.Cryptography.RandomNumberGenerator`
- `System.Security.Cryptography.IncrementalHash`
- `System.Security.Cryptography.SHA1`
- `System.Security.Cryptography.SHA256`
- `System.Security.Cryptography.SHA384`
- `System.Security.Cryptography.SHA512`
- `System.Security.Cryptography.SHA1Managed`
- `System.Security.Cryptography.SHA256Managed`
- `System.Security.Cryptography.SHA384Managed`
- `System.Security.Cryptography.SHA512Managed`

<!--

### Affected APIs

- `T:System.Security.Cryptography`

### Category

- ASP.NET Core
- Cryptography

-->
