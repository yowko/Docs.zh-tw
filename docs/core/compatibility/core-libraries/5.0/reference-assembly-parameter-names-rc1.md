---
title: 重大變更： RC2 中的參數名稱已變更
description: 瞭解核心 .NET 程式庫中的 .NET 5.0 重大變更，其中某些參考元件參數名稱已從預覽和發行候選版本的 .NET 5.0 變更。
ms.date: 11/01/2020
ms.openlocfilehash: 554a4fa9e08fdb504f380465496d7e7e9df85814
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760686"
---
# <a name="parameter-names-changed-in-rc2"></a><span data-ttu-id="c2bf2-103">RC2 中的參數名稱已變更</span><span class="sxs-lookup"><span data-stu-id="c2bf2-103">Parameter names changed in RC2</span></span>

<span data-ttu-id="c2bf2-104">某些參考元件參數名稱已變更，以符合實元件中的參數名稱。</span><span class="sxs-lookup"><span data-stu-id="c2bf2-104">Some reference assembly parameter names have changed to match parameter names in the implementation assemblies.</span></span>

## <a name="change-description"></a><span data-ttu-id="c2bf2-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="c2bf2-105">Change description</span></span>

<span data-ttu-id="c2bf2-106">在舊版的 .NET 5.0 preview 和 RC 版本中，某些 [參考元件](../../../../standard/assembly/reference-assemblies.md) 參數名稱與其在執行元件中的對應參數不同。</span><span class="sxs-lookup"><span data-stu-id="c2bf2-106">In previous .NET 5.0 preview and RC versions, some [reference assembly](../../../../standard/assembly/reference-assemblies.md) parameter names are different to their corresponding parameters in the implementation assembly.</span></span> <span data-ttu-id="c2bf2-107">這可能會在使用具名引數和反映時造成問題。</span><span class="sxs-lookup"><span data-stu-id="c2bf2-107">This can cause problems while using named arguments and reflection.</span></span>

<span data-ttu-id="c2bf2-108">在 .NET 5.0 RC2 中，這些不相符的參數名稱已在參考元件中更新，以完全符合執行元件中的對應參數名稱。</span><span class="sxs-lookup"><span data-stu-id="c2bf2-108">In .NET 5.0 RC2, these mismatched parameter names were updated in the reference assemblies to exactly match the corresponding parameter names in the implementation assemblies.</span></span>

<span data-ttu-id="c2bf2-109">下表顯示變更的 Api 和參數名稱。</span><span class="sxs-lookup"><span data-stu-id="c2bf2-109">The following table shows the APIs and parameter names that changed.</span></span>

| <span data-ttu-id="c2bf2-110">API</span><span class="sxs-lookup"><span data-stu-id="c2bf2-110">API</span></span> | <span data-ttu-id="c2bf2-111">舊的參數名稱</span><span class="sxs-lookup"><span data-stu-id="c2bf2-111">Old parameter name</span></span> | <span data-ttu-id="c2bf2-112">新參數名稱</span><span class="sxs-lookup"><span data-stu-id="c2bf2-112">New parameter name</span></span> |
| - | - | - |
| <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)> | `traceOptions` | `traceFlags` |
| <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=nameWithType> | `suffix` | `prefix` |

## <a name="reason-for-change"></a><span data-ttu-id="c2bf2-113">變更的原因</span><span class="sxs-lookup"><span data-stu-id="c2bf2-113">Reason for change</span></span>

<span data-ttu-id="c2bf2-114">變更參數名稱的一致性，並避免在使用具名引數和反映時失敗。</span><span class="sxs-lookup"><span data-stu-id="c2bf2-114">The parameter names were changed for consistency and to avoid failures when using named arguments and reflection.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="c2bf2-115">引進的版本</span><span class="sxs-lookup"><span data-stu-id="c2bf2-115">Version introduced</span></span>

<span data-ttu-id="c2bf2-116">5.0 RC2</span><span class="sxs-lookup"><span data-stu-id="c2bf2-116">5.0 RC2</span></span>

## <a name="recommended-action"></a><span data-ttu-id="c2bf2-117">建議的動作</span><span class="sxs-lookup"><span data-stu-id="c2bf2-117">Recommended action</span></span>

<span data-ttu-id="c2bf2-118">如果您因為參數名稱變更而發生編譯器錯誤，請據以更新參數名稱。</span><span class="sxs-lookup"><span data-stu-id="c2bf2-118">If you encounter a compiler error due to a parameter name change, update the parameter name accordingly.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="c2bf2-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="c2bf2-119">Affected APIs</span></span>

- <xref:System.Diagnostics.ActivityContext.%23ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)>
- <xref:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.Diagnostics.ActivityContext.#ctor(System.Diagnostics.ActivityTraceId,System.Diagnostics.ActivitySpanId,System.Diagnostics.ActivityTraceFlags,System.String,System.Boolean)`
- `M:System.Globalization.CompareInfo.IsPrefix(System.ReadOnlySpan{System.Char},System.ReadOnlySpan{System.Char},System.Globalization.CompareOptions,System.Int32@)`

-->
