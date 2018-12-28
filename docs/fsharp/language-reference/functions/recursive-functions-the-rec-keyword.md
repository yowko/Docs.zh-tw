---
title: 遞迴函式：Rec 關鍵字
description: 了解如何F#'rec' 關鍵字用以與 'let' 關鍵字定義遞迴函式。
ms.date: 05/16/2016
ms.openlocfilehash: 9f9c7e1a4468de9551b3852d0e7b4381025b2699
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/19/2018
ms.locfileid: "53612903"
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="985db-103">遞迴函式：Rec 關鍵字</span><span class="sxs-lookup"><span data-stu-id="985db-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="985db-104">`rec`關鍵字可搭配使用`let`關鍵字來定義遞迴函式。</span><span class="sxs-lookup"><span data-stu-id="985db-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>

## <a name="syntax"></a><span data-ttu-id="985db-105">語法</span><span class="sxs-lookup"><span data-stu-id="985db-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="985db-106">備註</span><span class="sxs-lookup"><span data-stu-id="985db-106">Remarks</span></span>

<span data-ttu-id="985db-107">遞迴函式，呼叫本身的函式中明確地識別F#語言。</span><span class="sxs-lookup"><span data-stu-id="985db-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="985db-108">如此所定義的識別項可以在函式的範圍內。</span><span class="sxs-lookup"><span data-stu-id="985db-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="985db-109">下列程式碼說明遞迴函式來計算*n*<sup>th</sup> Fibonacci 數字。</span><span class="sxs-lookup"><span data-stu-id="985db-109">The following code illustrates a recursive function that computes the *n*<sup>th</sup> Fibonacci number.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

> [!NOTE]
> <span data-ttu-id="985db-110">在實務上，類似上述程式碼是浪費資源的記憶體和處理器時間，因為它牽涉到先前的計算值的重新計算。</span><span class="sxs-lookup"><span data-stu-id="985db-110">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>

<span data-ttu-id="985db-111">方法為隱含型別; 中的遞迴不需要將`rec`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="985db-111">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="985db-112">在類別中的 let 繫結不會隱含地遞迴。</span><span class="sxs-lookup"><span data-stu-id="985db-112">Let bindings within classes are not implicitly recursive.</span></span>

## <a name="mutually-recursive-functions"></a><span data-ttu-id="985db-113">相互遞迴函式</span><span class="sxs-lookup"><span data-stu-id="985db-113">Mutually Recursive Functions</span></span>

<span data-ttu-id="985db-114">函式的是有時*相互遞迴*，這表示呼叫表單的其中一個函式呼叫另一個會接著呼叫第一，使用任意多個呼叫之間的圓形。</span><span class="sxs-lookup"><span data-stu-id="985db-114">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="985db-115">您必須同時定義這類函式，在一個`let`繫結，使用`and`而連結在一起的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="985db-115">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="985db-116">下列範例示範兩個相互遞迴函式。</span><span class="sxs-lookup"><span data-stu-id="985db-116">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="985db-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="985db-117">See also</span></span>

- [<span data-ttu-id="985db-118">函式</span><span class="sxs-lookup"><span data-stu-id="985db-118">Functions</span></span>](index.md)