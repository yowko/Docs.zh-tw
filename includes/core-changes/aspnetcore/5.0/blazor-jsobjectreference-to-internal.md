---
ms.openlocfilehash: 46f6f77a543dfcf2073063d8ec200ef7d71e6b1f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91077588"
---
### <a name="blazor-jsobjectreference-and-jsinprocessobjectreference-types-changed-to-internal"></a><span data-ttu-id="12902-101">Blazor： JSObjectReference 和 JSInProcessObjectReference 類型已變更為內部</span><span class="sxs-lookup"><span data-stu-id="12902-101">Blazor: JSObjectReference and JSInProcessObjectReference types changed to internal</span></span>

<span data-ttu-id="12902-102">`Microsoft.JSInterop.JSObjectReference` `Microsoft.JSInterop.JSInProcessObjectReference` ASP.NET CORE 5.0 RC1 中引進的新和類型已標示為 `internal` 。</span><span class="sxs-lookup"><span data-stu-id="12902-102">The new `Microsoft.JSInterop.JSObjectReference` and `Microsoft.JSInterop.JSInProcessObjectReference` types introduced in ASP.NET Core 5.0 RC1 have been marked as `internal`.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="12902-103">引進的版本</span><span class="sxs-lookup"><span data-stu-id="12902-103">Version introduced</span></span>

<span data-ttu-id="12902-104">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="12902-104">5.0 RC2</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="12902-105">舊的行為</span><span class="sxs-lookup"><span data-stu-id="12902-105">Old behavior</span></span>

<span data-ttu-id="12902-106">`JSObjectReference`可以透過 JavaScript interop 呼叫來取得 `IJSRuntime` 。</span><span class="sxs-lookup"><span data-stu-id="12902-106">A `JSObjectReference` can be obtained from a JavaScript interop call via `IJSRuntime`.</span></span> <span data-ttu-id="12902-107">例如：</span><span class="sxs-lookup"><span data-stu-id="12902-107">For example:</span></span>

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<JSObjectReference>(...);
```

#### <a name="new-behavior"></a><span data-ttu-id="12902-108">新的行為</span><span class="sxs-lookup"><span data-stu-id="12902-108">New behavior</span></span>

<span data-ttu-id="12902-109">`JSObjectReference` 使用 [內部](../../../../docs/csharp/language-reference/keywords/internal.md) 存取修飾詞。</span><span class="sxs-lookup"><span data-stu-id="12902-109">`JSObjectReference` uses the [internal](../../../../docs/csharp/language-reference/keywords/internal.md) access modifier.</span></span> <span data-ttu-id="12902-110">您 `public` `IJSObjectReference` 必須改為使用介面。</span><span class="sxs-lookup"><span data-stu-id="12902-110">The `public` `IJSObjectReference` interface must be used instead.</span></span> <span data-ttu-id="12902-111">例如：</span><span class="sxs-lookup"><span data-stu-id="12902-111">For example:</span></span>

```csharp
var jsObjectReference = await JSRuntime.InvokeAsync<IJSObjectReference>(...);
```

<span data-ttu-id="12902-112">`JSInProcessObjectReference` 也標記為 `internal` ，並取代為 `IJSInProcessObjectReference` 。</span><span class="sxs-lookup"><span data-stu-id="12902-112">`JSInProcessObjectReference` was also marked as `internal` and was replaced by `IJSInProcessObjectReference`.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="12902-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="12902-113">Reason for change</span></span>

<span data-ttu-id="12902-114">這項變更讓 JavaScript interop 功能與 Blazor 中的其他模式更一致。</span><span class="sxs-lookup"><span data-stu-id="12902-114">The change makes the JavaScript interop feature more consistent with other patterns within Blazor.</span></span> <span data-ttu-id="12902-115">`IJSObjectReference` 類似于 `IJSRuntime` ，因為它的用途類似，而且具有類似的方法和延伸模組。</span><span class="sxs-lookup"><span data-stu-id="12902-115">`IJSObjectReference` is analogous to `IJSRuntime` in that it serves a similar purpose and has similar methods and extensions.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="12902-116">建議的動作</span><span class="sxs-lookup"><span data-stu-id="12902-116">Recommended action</span></span>

<span data-ttu-id="12902-117">`JSObjectReference`分別以和取代 and 的出現次數 `JSInProcessObjectReference` `IJSObjectReference` `IJSInProcessObjectReference` 。</span><span class="sxs-lookup"><span data-stu-id="12902-117">Replace occurrences of `JSObjectReference` and `JSInProcessObjectReference` with `IJSObjectReference` and `IJSInProcessObjectReference`, respectively.</span></span>

#### <a name="category"></a><span data-ttu-id="12902-118">類別</span><span class="sxs-lookup"><span data-stu-id="12902-118">Category</span></span>

<span data-ttu-id="12902-119">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="12902-119">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="12902-120">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="12902-120">Affected APIs</span></span>

- `Microsoft.JSInterop.JSObjectReference`
- `Microsoft.JSInterop.JSInProcessObjectReference`

<!--

#### Affected APIs

- `T:Microsoft.JSInterop.JSObjectReference`
- `T:Microsoft.JSInterop.JSInProcessObjectReference`

-->
