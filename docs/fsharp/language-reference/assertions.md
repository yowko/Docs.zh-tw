---
title: 判斷提示
description: 瞭解如何使用「判斷提示」運算式做為程式F#設計語言中測試運算式的偵錯工具。
ms.date: 10/22/2019
ms.openlocfilehash: 430db20e5ca307ba43a72e678a0424e03b0ac381
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799069"
---
# <a name="assertions"></a><span data-ttu-id="c2a6a-103">判斷提示</span><span class="sxs-lookup"><span data-stu-id="c2a6a-103">Assertions</span></span>

<span data-ttu-id="c2a6a-104">`assert` 運算式是一個可供您用來測試運算式的偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="c2a6a-104">The `assert` expression is a debugging feature that you can use to test an expression.</span></span> <span data-ttu-id="c2a6a-105">當運算式在偵測模式中發生錯誤時，判斷提示會顯示系統錯誤對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c2a6a-105">Upon failure in Debug mode, an assertion generates a system error dialog box.</span></span>

## <a name="syntax"></a><span data-ttu-id="c2a6a-106">語法</span><span class="sxs-lookup"><span data-stu-id="c2a6a-106">Syntax</span></span>

```fsharp
assert condition
```

## <a name="remarks"></a><span data-ttu-id="c2a6a-107">備註</span><span class="sxs-lookup"><span data-stu-id="c2a6a-107">Remarks</span></span>

<span data-ttu-id="c2a6a-108">`assert` 運算式的類型 `bool -> unit`。</span><span class="sxs-lookup"><span data-stu-id="c2a6a-108">The `assert` expression has type `bool -> unit`.</span></span>

<span data-ttu-id="c2a6a-109">`assert` 函式會解析為 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="c2a6a-109">The `assert` function resolves to <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c2a6a-110">這表示其行為等同于直接呼叫 <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="c2a6a-110">This means its behavior is identical to having called <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> directly.</span></span>

<span data-ttu-id="c2a6a-111">只有當您在 Debug 模式下編譯時，才會啟用判斷提示檢查;也就是，如果已定義常數 `DEBUG`。</span><span class="sxs-lookup"><span data-stu-id="c2a6a-111">Assertion checking is enabled only when you compile in Debug mode; that is, if the constant `DEBUG` is defined.</span></span> <span data-ttu-id="c2a6a-112">在專案系統中，預設會在 [偵錯工具] 設定中定義 `DEBUG` 常數，而不是在 [發行] 設定中。</span><span class="sxs-lookup"><span data-stu-id="c2a6a-112">In the project system, by default, the `DEBUG` constant is defined in the Debug configuration but not in the Release configuration.</span></span>

<span data-ttu-id="c2a6a-113">無法使用F#例外狀況處理來攔截判斷提示失敗錯誤。</span><span class="sxs-lookup"><span data-stu-id="c2a6a-113">The assertion failure error cannot be caught by using F# exception handling.</span></span>

## <a name="example"></a><span data-ttu-id="c2a6a-114">範例</span><span class="sxs-lookup"><span data-stu-id="c2a6a-114">Example</span></span>

<span data-ttu-id="c2a6a-115">下列程式碼範例說明如何使用 `assert` 運算式。</span><span class="sxs-lookup"><span data-stu-id="c2a6a-115">The following code example illustrates the use of the `assert` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5401.fs)]

## <a name="see-also"></a><span data-ttu-id="c2a6a-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="c2a6a-116">See also</span></span>

- [<span data-ttu-id="c2a6a-117">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="c2a6a-117">F# Language Reference</span></span>](index.md)
