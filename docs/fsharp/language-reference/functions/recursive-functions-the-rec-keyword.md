---
title: 遞迴函式:Rec 關鍵字
description: 瞭解 ' rec F# ' 關鍵字如何與 ' let ' 關鍵字搭配使用, 以定義遞迴函數。
ms.date: 05/16/2016
ms.openlocfilehash: 7edaa7206b2109c7b1a405624b9b2330968f9c52
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630647"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="fad13-103">遞迴函式:Rec 關鍵字</span><span class="sxs-lookup"><span data-stu-id="fad13-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="fad13-104">`rec`關鍵字會`let`與關鍵字搭配使用, 以定義遞迴函數。</span><span class="sxs-lookup"><span data-stu-id="fad13-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="fad13-105">語法</span><span class="sxs-lookup"><span data-stu-id="fad13-105">Syntax</span></span>

```fsharp
// Recursive function:
let rec function-nameparameter-list =
function-body

// Mutually recursive functions:
let rec function1-nameparameter-list =
function1-body
and function2-nameparameter-list =
function2-body
...
```

## <a name="remarks"></a><span data-ttu-id="fad13-106">備註</span><span class="sxs-lookup"><span data-stu-id="fad13-106">Remarks</span></span>

<span data-ttu-id="fad13-107">遞迴函式, 呼叫本身的函數會在F#語言中明確識別。</span><span class="sxs-lookup"><span data-stu-id="fad13-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="fad13-108">這會讓在函式的範圍中定義的識別碼可供使用。</span><span class="sxs-lookup"><span data-stu-id="fad13-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="fad13-109">下列程式碼說明一個遞迴函式, 它會計算<sup>第</sup> *n*個斐的量值。</span><span class="sxs-lookup"><span data-stu-id="fad13-109">The following code illustrates a recursive function that computes the *n*<sup>th</sup> Fibonacci number.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> <span data-ttu-id="fad13-110">實際上, 上述程式碼不會浪費記憶體和處理器時間, 因為它牽涉到先前計算值的重新計算。</span><span class="sxs-lookup"><span data-stu-id="fad13-110">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>

<span data-ttu-id="fad13-111">方法在型別內隱含遞迴;不需要新增`rec`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="fad13-111">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="fad13-112">類別內的 Let 系結不會隱含遞迴。</span><span class="sxs-lookup"><span data-stu-id="fad13-112">Let bindings within classes are not implicitly recursive.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="fad13-113">相互遞迴函式</span><span class="sxs-lookup"><span data-stu-id="fad13-113">Mutually Recursive Functions</span></span>

<span data-ttu-id="fad13-114">有時候函式是*互斥*的, 這表示呼叫會形成圓形, 其中一個函式會呼叫另一個函式, 然後呼叫第一個函式, 而其間的呼叫數目則為。</span><span class="sxs-lookup"><span data-stu-id="fad13-114">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="fad13-115">您必須在一個`let`系結中定義這類函式, 並`and`使用關鍵字將它們連結在一起。</span><span class="sxs-lookup"><span data-stu-id="fad13-115">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="fad13-116">下列範例顯示兩個相互遞迴的函式。</span><span class="sxs-lookup"><span data-stu-id="fad13-116">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="fad13-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fad13-117">See also</span></span>

- [<span data-ttu-id="fad13-118">函式</span><span class="sxs-lookup"><span data-stu-id="fad13-118">Functions</span></span>](index.md)
