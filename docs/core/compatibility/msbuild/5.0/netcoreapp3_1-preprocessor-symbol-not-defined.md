---
title: 重大變更：以 .NET 5 為目標時，未定義 NETCOREAPP3_1 預處理器符號
description: 瞭解 .NET 5.0 中的重大變更，其中專案不再定義舊版的預處理器符號。
ms.date: 09/17/2020
ms.openlocfilehash: 61a5e4fce258d2be3d584318e154bb752b88ebe1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760637"
---
# <a name="netcoreapp3_1-preprocessor-symbol-is-not-defined-when-targeting-net-5"></a><span data-ttu-id="438ca-103">以 .NET 5 為目標時，未定義 NETCOREAPP3_1 預處理器符號</span><span class="sxs-lookup"><span data-stu-id="438ca-103">NETCOREAPP3_1 preprocessor symbol is not defined when targeting .NET 5</span></span>

<span data-ttu-id="438ca-104">在 .NET 5.0 RC2 和更新版本中，專案不再定義舊版的預處理器符號，而是僅針對其目標版本。</span><span class="sxs-lookup"><span data-stu-id="438ca-104">In .NET 5.0 RC2 and later versions, projects no longer define preprocessor symbols for earlier versions, but only for the version that they target.</span></span> <span data-ttu-id="438ca-105">這與 .NET Core 1.0-3.1 的行為相同。</span><span class="sxs-lookup"><span data-stu-id="438ca-105">This is the same behavior as .NET Core 1.0 - 3.1.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="438ca-106">引進的版本</span><span class="sxs-lookup"><span data-stu-id="438ca-106">Version introduced</span></span>

<span data-ttu-id="438ca-107">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="438ca-107">5.0 RC2</span></span>

## <a name="change-description"></a><span data-ttu-id="438ca-108">變更描述</span><span class="sxs-lookup"><span data-stu-id="438ca-108">Change description</span></span>

<span data-ttu-id="438ca-109">在 .NET 5.0 preview 7 到 RC1 中，目標專案會 `net5.0` 定義 `NETCOREAPP3_1` 和 `NET5_0` 預處理器符號。</span><span class="sxs-lookup"><span data-stu-id="438ca-109">In .NET 5.0 preview 7 through RC1, projects that target `net5.0` define both `NETCOREAPP3_1` and `NET5_0` preprocessor symbols.</span></span> <span data-ttu-id="438ca-110">此行為變更背後的目的在於從 .NET 5.0 開始，條件式編譯 [符號會是累計](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md#preprocessor-symbols)的。</span><span class="sxs-lookup"><span data-stu-id="438ca-110">The intent behind this behavior change was that starting with .NET 5.0, conditional compilation [symbols would be cumulative](https://github.com/dotnet/designs/blob/main/accepted/2020/net5/net5.md#preprocessor-symbols).</span></span>

<span data-ttu-id="438ca-111">在 .NET 5.0 RC2 和更新版本中，專案只會定義目標 framework 標記的符號 (TFM 它的目標) ，而不是任何較早的版本。</span><span class="sxs-lookup"><span data-stu-id="438ca-111">In .NET 5.0 RC2 and later, projects only define symbols for the target framework monikers (TFM) that it targets and not for any earlier versions.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="438ca-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="438ca-112">Reason for change</span></span>

<span data-ttu-id="438ca-113">因為客戶的意見反應，已還原 preview 7 的變更。</span><span class="sxs-lookup"><span data-stu-id="438ca-113">The change from preview 7 was reverted due to customer feedback.</span></span> <span data-ttu-id="438ca-114">針對較舊的版本定義符號，讓客戶感到驚訝及混淆，並假設它是 c # 編譯器中的 bug。</span><span class="sxs-lookup"><span data-stu-id="438ca-114">Defining symbols for earlier versions surprised and confused customers, and some assumed it was a bug in the C# compiler.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="438ca-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="438ca-115">Recommended action</span></span>

<span data-ttu-id="438ca-116">請確定您的 `#if` 邏輯不會假設在 `NETCOREAPP3_1` 專案目標 `net5.0` 或更高版本時定義。</span><span class="sxs-lookup"><span data-stu-id="438ca-116">Make sure that your `#if` logic doesn't assume that `NETCOREAPP3_1` is defined when the project targets `net5.0` or higher.</span></span> <span data-ttu-id="438ca-117">相反地，假設 `NETCOREAPP3_1` 只有在專案明確設定為目標時才會定義 `netcoreapp3.1` 。</span><span class="sxs-lookup"><span data-stu-id="438ca-117">Instead, assume that `NETCOREAPP3_1` is only defined when the project explicitly targets `netcoreapp3.1`.</span></span>

<span data-ttu-id="438ca-118">例如，如果您的專案是針對 .NET core 2.1 和 .NET Core 3.1 所 multitargets，而且您呼叫 .NET Core 3.1 中引進的 Api，則您的 `#if` 邏輯看起來應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="438ca-118">For example, if your project multitargets for .NET Core 2.1 and .NET Core 3.1 and you call APIs that were introduced in .NET Core 3.1, your `#if` logic should look as follows:</span></span>

```csharp
#if NETCOREAPP2_1 || NETCOREAPP3_0
    // Fallback behavior for old versions.
#elif NETCOREAPP
    // Behavior for .NET Core 3.1 and later.
#endif
```

## <a name="affected-apis"></a><span data-ttu-id="438ca-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="438ca-119">Affected APIs</span></span>

<span data-ttu-id="438ca-120">N/A</span><span class="sxs-lookup"><span data-stu-id="438ca-120">N/A</span></span>

<!--

### Affected APIs

Not detectable via API analysis.

### Category

MSBuild

-->
