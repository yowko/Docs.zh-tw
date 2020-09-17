---
ms.openlocfilehash: 760c9ce2427bc1f5e9276e66ecb6d2cf2ed83c16
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738812"
---
### <a name="parameter-names-changed-in-rc1"></a><span data-ttu-id="21721-101">RC1 中的參數名稱已變更</span><span class="sxs-lookup"><span data-stu-id="21721-101">Parameter names changed in RC1</span></span>

<span data-ttu-id="21721-102">某些參考元件參數名稱已變更，以符合實元件中的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="21721-102">Some reference assembly parameter names have changed to match parameter names in the implementation assemblies.</span></span>

#### <a name="change-description"></a><span data-ttu-id="21721-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="21721-103">Change description</span></span>

<span data-ttu-id="21721-104">在舊版的 .NET 5.0 preview 和 RC 版本中，某些 [參考元件](../../../../docs/standard/assembly/reference-assemblies.md) 參數名稱與其在執行元件中的對應參數不同。</span><span class="sxs-lookup"><span data-stu-id="21721-104">In previous .NET 5.0 preview and RC versions, some [reference assembly](../../../../docs/standard/assembly/reference-assemblies.md) parameter names are different to their corresponding parameters in the implementation assembly.</span></span> <span data-ttu-id="21721-105">這可能會在使用具名引數和反映時造成問題。</span><span class="sxs-lookup"><span data-stu-id="21721-105">This can cause problems while using named arguments and reflection.</span></span>

<span data-ttu-id="21721-106">在 .NET 5.0 RC2 中，這些不相符的參數名稱已在參考元件中更新，以完全符合執行元件中的對應參數名稱。</span><span class="sxs-lookup"><span data-stu-id="21721-106">In .NET 5.0 RC2, these mismatched parameter names were updated in the reference assemblies to exactly match the corresponding parameter names in the implementation assemblies.</span></span>

<span data-ttu-id="21721-107">下表顯示變更的 Api 和參數名稱。</span><span class="sxs-lookup"><span data-stu-id="21721-107">The following table shows the APIs and parameter names that changed.</span></span>

| <span data-ttu-id="21721-108">API</span><span class="sxs-lookup"><span data-stu-id="21721-108">API</span></span> | <span data-ttu-id="21721-109">舊的參數名稱</span><span class="sxs-lookup"><span data-stu-id="21721-109">Old parameter name</span></span> | <span data-ttu-id="21721-110">新參數名稱</span><span class="sxs-lookup"><span data-stu-id="21721-110">New parameter name</span></span> |
| - | - | - |
| <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)> | `traceOptions` | `traceFlags` |
| <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=nameWithType> | `suffix` | `prefix` |

#### <a name="reason-for-change"></a><span data-ttu-id="21721-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="21721-111">Reason for change</span></span>

<span data-ttu-id="21721-112">變更參數名稱的一致性，並避免在使用具名引數和反映時失敗。</span><span class="sxs-lookup"><span data-stu-id="21721-112">The parameter names were changed for consistency and to avoid failures when using named arguments and reflection.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="21721-113">引進的版本</span><span class="sxs-lookup"><span data-stu-id="21721-113">Version introduced</span></span>

<span data-ttu-id="21721-114">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="21721-114">5.0 RC2</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="21721-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="21721-115">Recommended action</span></span>

<span data-ttu-id="21721-116">如果您因為參數名稱變更而發生編譯器錯誤，請據以更新參數名稱。</span><span class="sxs-lookup"><span data-stu-id="21721-116">If you encounter a compiler error due to a parameter name change, update the parameter name accordingly.</span></span>

#### <a name="category"></a><span data-ttu-id="21721-117">類別</span><span class="sxs-lookup"><span data-stu-id="21721-117">Category</span></span>

<span data-ttu-id="21721-118">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="21721-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="21721-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="21721-119">Affected APIs</span></span>

- <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)>
- <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=fullName>

<!--

#### Affected APIs

- `M:System.Diagnostics.ActivityContext.#ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)`
- `M:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)`

-->
