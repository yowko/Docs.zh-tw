---
title: 遞迴函式：rec 關鍵字 (F#)
description: "了解如何 F # 'rec' 關鍵字使用 'let' 關鍵字來定義遞迴函式。"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 1f5302c125605d2186deab0bbeaf2e84cc51edc3
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="recursive-functions-the-rec-keyword"></a><span data-ttu-id="87b44-103">遞迴函式：rec 關鍵字</span><span class="sxs-lookup"><span data-stu-id="87b44-103">Recursive Functions: The rec Keyword</span></span>

<span data-ttu-id="87b44-104">`rec`關鍵字會搭配`let`關鍵字來定義遞迴函式。</span><span class="sxs-lookup"><span data-stu-id="87b44-104">The `rec` keyword is used together with the `let` keyword to define a recursive function.</span></span>


## <a name="syntax"></a><span data-ttu-id="87b44-105">語法</span><span class="sxs-lookup"><span data-stu-id="87b44-105">Syntax</span></span>

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

## <a name="remarks"></a><span data-ttu-id="87b44-106">備註</span><span class="sxs-lookup"><span data-stu-id="87b44-106">Remarks</span></span>
<span data-ttu-id="87b44-107">遞迴函式，呼叫本身，函式會明確地識別在 F # 語言中。</span><span class="sxs-lookup"><span data-stu-id="87b44-107">Recursive functions, functions that call themselves, are identified explicitly in the F# language.</span></span> <span data-ttu-id="87b44-108">這讓正在定義的識別項使用的函式範圍中。</span><span class="sxs-lookup"><span data-stu-id="87b44-108">This makes the identifer that is being defined available in the scope of the function.</span></span>

<span data-ttu-id="87b44-109">下列程式碼說明遞迴函式，會計算*n*個 Fibonacci 數字。</span><span class="sxs-lookup"><span data-stu-id="87b44-109">The following code illustrates a recursive function that computes the *n*th Fibonacci number.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4001.fs)]

>[!NOTE]
<span data-ttu-id="87b44-110">在實務上，類似的上述程式碼是不必要的記憶體和處理器時間，因為它牽涉到先前的計算值的重新計算。</span><span class="sxs-lookup"><span data-stu-id="87b44-110">In practice, code like that above is wasteful of memory and processor time because it involves the recomputation of previously computed values.</span></span>


<span data-ttu-id="87b44-111">方法都是隱含遞迴的類型; 內不需要新增`rec`關鍵字。</span><span class="sxs-lookup"><span data-stu-id="87b44-111">Methods are implicitly recursive within the type; there is no need to add the `rec` keyword.</span></span> <span data-ttu-id="87b44-112">在類別中的 let 繫結沒有隱含地遞迴。</span><span class="sxs-lookup"><span data-stu-id="87b44-112">Let bindings within classes are not implicitly recursive.</span></span>


## <a name="mutually-recursive-functions"></a><span data-ttu-id="87b44-113">相互遞迴函式</span><span class="sxs-lookup"><span data-stu-id="87b44-113">Mutually Recursive Functions</span></span>
<span data-ttu-id="87b44-114">函式有時候是*相互遞迴*，這表示呼叫表單的其中一個函式呼叫另一個也就會呼叫第一個與任何數目的呼叫之間的圓形。</span><span class="sxs-lookup"><span data-stu-id="87b44-114">Sometimes functions are *mutually recursive*, meaning that calls form a circle, where one function calls another which in turn calls the first, with any number of calls in between.</span></span> <span data-ttu-id="87b44-115">您必須同時定義這類函式，在一個`let`繫結，請使用`and`關鍵字來連結在一起。</span><span class="sxs-lookup"><span data-stu-id="87b44-115">You must define such functions together in the one `let` binding, using the `and` keyword to link them together.</span></span>

<span data-ttu-id="87b44-116">下列範例示範兩個相互遞迴函式。</span><span class="sxs-lookup"><span data-stu-id="87b44-116">The following example shows two mutually recursive functions.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet4002.fs)]

## <a name="see-also"></a><span data-ttu-id="87b44-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87b44-117">See Also</span></span>
[<span data-ttu-id="87b44-118">函式</span><span class="sxs-lookup"><span data-stu-id="87b44-118">Functions</span></span>](index.md)
