---
title: 重大變更： Blazor： JSObjectReference 和 JSInProcessObjectReference 類型已變更為內部
description: 瞭解 ASP.NET Core 5.0 的重大變更，標題為 Blazor： JSObjectReference，JSInProcessObjectReference 類型已變更為內部
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 43a66d204f8309dc5afc57d099b2201c477cc3ad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760666"
---
# <a name="blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal"></a><span data-ttu-id="bc455-103">Blazor： JSObjectReference 和 JSInProcessObjectReference 類型已變更為內部</span><span class="sxs-lookup"><span data-stu-id="bc455-103">Blazor: JSObjectReference and JSInProcessObjectReference types changed to internal</span></span>

<span data-ttu-id="bc455-104">`Microsoft.JSInterop.JSObjectReference` `Microsoft.JSInterop.JSInProcessObjectReference` ASP.NET CORE 5.0 RC1 中引進的新和類型已標示為 `internal` 。</span><span class="sxs-lookup"><span data-stu-id="bc455-104">The new `Microsoft.JSInterop.JSObjectReference` and `Microsoft.JSInterop.JSInProcessObjectReference` types introduced in ASP.NET Core 5.0 RC1 have been marked as `internal`.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="bc455-105">引進的版本</span><span class="sxs-lookup"><span data-stu-id="bc455-105">Version introduced</span></span>

<span data-ttu-id="bc455-106">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="bc455-106">5.0 RC2</span></span>

## <a name="old-behavior"></a><span data-ttu-id="bc455-107">舊的行為</span><span class="sxs-lookup"><span data-stu-id="bc455-107">Old behavior</span></span>

<span data-ttu-id="bc455-108">`JSObjectReference`可以透過 JavaScript interop 呼叫來取得 `IJSRuntime` 。</span><span class="sxs-lookup"><span data-stu-id="bc455-108">A `JSObjectReference` can be obtained from a JavaScript interop call via `IJSRuntime`.</span></span> <span data-ttu-id="bc455-109">例如：</span><span class="sxs-lookup"><span data-stu-id="bc455-109">For example:</span></span>

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<JSObjectReference>(...);
```

## <a name="new-behavior"></a><span data-ttu-id="bc455-110">新的行為</span><span class="sxs-lookup"><span data-stu-id="bc455-110">New behavior</span></span>

<span data-ttu-id="bc455-111">`JSObjectReference` 使用 [內部](../../../../csharp/language-reference/keywords/internal.md) 存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="bc455-111">`JSObjectReference` uses the [internal](../../../../csharp/language-reference/keywords/internal.md) access modifier.</span></span> <span data-ttu-id="bc455-112">您 `public` `IJSObjectReference` 必須改為使用介面。</span><span class="sxs-lookup"><span data-stu-id="bc455-112">The `public` `IJSObjectReference` interface must be used instead.</span></span> <span data-ttu-id="bc455-113">例如：</span><span class="sxs-lookup"><span data-stu-id="bc455-113">For example:</span></span>

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<IJSObjectReference>(...);
```

<span data-ttu-id="bc455-114">`JSInProcessObjectReference` 也標記為 `internal` ，並取代為 `IJSInProcessObjectReference` 。</span><span class="sxs-lookup"><span data-stu-id="bc455-114">`JSInProcessObjectReference` was also marked as `internal` and was replaced by `IJSInProcessObjectReference`.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="bc455-115">變更的原因</span><span class="sxs-lookup"><span data-stu-id="bc455-115">Reason for change</span></span>

<span data-ttu-id="bc455-116">這項變更讓 JavaScript interop 功能與 Blazor 中的其他模式更一致。</span><span class="sxs-lookup"><span data-stu-id="bc455-116">The change makes the JavaScript interop feature more consistent with other patterns within Blazor.</span></span> <span data-ttu-id="bc455-117">`IJSObjectReference` 類似于 `IJSRuntime` ，因為它的用途類似，而且具有類似的方法和延伸模組。</span><span class="sxs-lookup"><span data-stu-id="bc455-117">`IJSObjectReference` is analogous to `IJSRuntime` in that it serves a similar purpose and has similar methods and extensions.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="bc455-118">建議的動作</span><span class="sxs-lookup"><span data-stu-id="bc455-118">Recommended action</span></span>

<span data-ttu-id="bc455-119">`JSObjectReference`分別以和取代 and 的出現次數 `JSInProcessObjectReference` `IJSObjectReference` `IJSInProcessObjectReference` 。</span><span class="sxs-lookup"><span data-stu-id="bc455-119">Replace occurrences of `JSObjectReference` and `JSInProcessObjectReference` with `IJSObjectReference` and `IJSInProcessObjectReference`, respectively.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="bc455-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="bc455-120">Affected APIs</span></span>

- `Microsoft.JSInterop.JSObjectReference`
- `Microsoft.JSInterop.JSInProcessObjectReference`

<!--

### Category

ASP.NET Core

### Affected APIs

- `T:Microsoft.JSInterop.JSObjectReference`
- `T:Microsoft.JSInterop.JSInProcessObjectReference`

-->
