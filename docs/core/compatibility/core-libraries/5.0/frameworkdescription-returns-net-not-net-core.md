---
title: 重大變更： FrameworkDescription 的值為 .NET 而非 .NET Core
description: 瞭解核心 .NET 程式庫中的 .NET 5.0 重大變更，其中 >runtimeinformation. FrameworkDescription 現在會傳回 ".NET" 而非 ".NET Core"。
ms.date: 11/01/2020
ms.openlocfilehash: 3925fb092135c26291e1e60b99f359974d21553c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760721"
---
# <a name="frameworkdescriptions-value-is-net-instead-of-net-core"></a><span data-ttu-id="46f14-103">FrameworkDescription 的值是 .NET 而不是 .NET Core</span><span class="sxs-lookup"><span data-stu-id="46f14-103">FrameworkDescription's value is .NET instead of .NET Core</span></span>

<span data-ttu-id="46f14-104"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> 現在會傳回 ".NET" 而不是 ".NET Core"。</span><span class="sxs-lookup"><span data-stu-id="46f14-104"><xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> now returns ".NET" instead of ".NET Core".</span></span>

## <a name="change-description"></a><span data-ttu-id="46f14-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="46f14-105">Change description</span></span>

<span data-ttu-id="46f14-106">在先前的 .NET 版本中，會傳回 <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> ".Net Core" 做為描述字串的一部分，例如， `.NET Core 3.1.1` 。</span><span class="sxs-lookup"><span data-stu-id="46f14-106">In previous .NET versions, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> returns ".NET Core" as part of the description string, for example, `.NET Core 3.1.1`.</span></span>

<span data-ttu-id="46f14-107">從 .NET 5.0 開始，會傳回 <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> ".net" 做為描述字串的一部分，例如， `.NET 5.0.0` 。</span><span class="sxs-lookup"><span data-stu-id="46f14-107">Starting in .NET 5.0, <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> returns ".NET" as part of the description string, for example, `.NET 5.0.0`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="46f14-108">變更的原因</span><span class="sxs-lookup"><span data-stu-id="46f14-108">Reason for change</span></span>

<span data-ttu-id="46f14-109">使用 .NET 5 `netcoreapp` 時，會將取代 `net` 為簡短的目標架構名字。</span><span class="sxs-lookup"><span data-stu-id="46f14-109">With .NET 5, `netcoreapp` is replaced by `net` as the short target-framework moniker.</span></span> <span data-ttu-id="46f14-110">為了保持一致性，也更新了架構的描述。</span><span class="sxs-lookup"><span data-stu-id="46f14-110">For consistency, the framework's description has also been updated.</span></span> <span data-ttu-id="46f14-111">這項變更是表面，因為 `FrameworkName` 未編碼于屬性中的任何其他位置 <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="46f14-111">The change is cosmetic, as the `FrameworkName` isn't encoded anywhere else than in the <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=nameWithType> property.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="46f14-112">引進的版本</span><span class="sxs-lookup"><span data-stu-id="46f14-112">Version introduced</span></span>

<span data-ttu-id="46f14-113">5.0</span><span class="sxs-lookup"><span data-stu-id="46f14-113">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="46f14-114">建議的動作</span><span class="sxs-lookup"><span data-stu-id="46f14-114">Recommended action</span></span>

<span data-ttu-id="46f14-115">更新在傳回的字串中搜尋 ".NET Core" 的任何程式碼 <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription> 。</span><span class="sxs-lookup"><span data-stu-id="46f14-115">Update any code that searches for ".NET Core" in the string returned by <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription>.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="46f14-116">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="46f14-116">Affected APIs</span></span>

- <xref:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription`

-->
