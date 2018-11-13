---
title: Lambda 運算式：fun 關鍵字 (F#)
description: 了解如何使用 F# '好玩 」 關鍵字來定義 lambda 運算式，這是匿名函式。
ms.date: 05/16/2016
ms.openlocfilehash: a37757f6b7328cd348bbf13f058a6dbc881769cf
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2018
ms.locfileid: "47231017"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="f0ae0-103">Lambda 運算式：fun 關鍵字 (F#)</span><span class="sxs-lookup"><span data-stu-id="f0ae0-103">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="f0ae0-104">`fun`關鍵字用以定義 lambda 運算式，也就是匿名函式。</span><span class="sxs-lookup"><span data-stu-id="f0ae0-104">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>

## <a name="syntax"></a><span data-ttu-id="f0ae0-105">語法</span><span class="sxs-lookup"><span data-stu-id="f0ae0-105">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="f0ae0-106">備註</span><span class="sxs-lookup"><span data-stu-id="f0ae0-106">Remarks</span></span>

<span data-ttu-id="f0ae0-107">*參數清單*通常是由名稱和 （選擇性） 參數的型別所組成。</span><span class="sxs-lookup"><span data-stu-id="f0ae0-107">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="f0ae0-108">更廣泛地*參數清單*可以包含任何的 F# 模式。</span><span class="sxs-lookup"><span data-stu-id="f0ae0-108">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="f0ae0-109">可能的模式的完整清單，請參閱 <<c0> [ 模式比對](../pattern-matching.md)。</span><span class="sxs-lookup"><span data-stu-id="f0ae0-109">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="f0ae0-110">有效的參數清單包含下列的範例。</span><span class="sxs-lookup"><span data-stu-id="f0ae0-110">Lists of valid parameters include the following examples.</span></span>

```fsharp
// Lambda expressions with parameter lists.
fun a b c -> ...
fun (a: int) b c -> ...
fun (a : int) (b : string) (c:float) -> ...

// A lambda expression with a tuple pattern.
fun (a, b) -> …

// A lambda expression with a list pattern.
fun head :: tail -> …
```

<span data-ttu-id="f0ae0-111">*運算式*是函式，其中的最後一個運算式會產生傳回值的主體。</span><span class="sxs-lookup"><span data-stu-id="f0ae0-111">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="f0ae0-112">有效的 lambda 運算式的範例包括：</span><span class="sxs-lookup"><span data-stu-id="f0ae0-112">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a><span data-ttu-id="f0ae0-113">使用 Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="f0ae0-113">Using Lambda Expressions</span></span>

<span data-ttu-id="f0ae0-114">當您想要在清單或另一個集合上執行作業，而且想要避免額外的工作定義的函式，lambda 運算式是特別有用。</span><span class="sxs-lookup"><span data-stu-id="f0ae0-114">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="f0ae0-115">許多 F# 程式庫函式會採用做為引數，函式值，可以使用 lambda 運算式，在這些情況下特別方便。</span><span class="sxs-lookup"><span data-stu-id="f0ae0-115">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="f0ae0-116">下列程式碼將 lambda 運算式套用至項目清單。</span><span class="sxs-lookup"><span data-stu-id="f0ae0-116">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="f0ae0-117">在此情況下，匿名函式會將 1 加入至清單的每個項目。</span><span class="sxs-lookup"><span data-stu-id="f0ae0-117">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a><span data-ttu-id="f0ae0-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0ae0-118">See also</span></span>

- [<span data-ttu-id="f0ae0-119">函式</span><span class="sxs-lookup"><span data-stu-id="f0ae0-119">Functions</span></span>](index.md)
