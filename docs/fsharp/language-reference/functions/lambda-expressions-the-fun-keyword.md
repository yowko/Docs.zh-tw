---
title: Lambda 運算式：fun 關鍵字 (F#)
description: "了解如何使用 F # 'fun' 關鍵字來定義 lambda 運算式，這是匿名函式。"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: f2f15a1b482ce3971d0b3d5ffc4f6dcc9ccf1569
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="8fd90-103">Lambda 運算式：fun 關鍵字 (F#)</span><span class="sxs-lookup"><span data-stu-id="8fd90-103">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="8fd90-104">`fun`關鍵字用來定義 lambda 運算式，也就是匿名函式。</span><span class="sxs-lookup"><span data-stu-id="8fd90-104">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>


## <a name="syntax"></a><span data-ttu-id="8fd90-105">語法</span><span class="sxs-lookup"><span data-stu-id="8fd90-105">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="8fd90-106">備註</span><span class="sxs-lookup"><span data-stu-id="8fd90-106">Remarks</span></span>
<span data-ttu-id="8fd90-107">*參數清單*通常包含名稱和 （選擇性） 參數的型別。</span><span class="sxs-lookup"><span data-stu-id="8fd90-107">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="8fd90-108">較常見地，*參數清單*可以是任何 F # 模式所組成。</span><span class="sxs-lookup"><span data-stu-id="8fd90-108">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="8fd90-109">如需可能模式的完整清單，請參閱[模式比對](../pattern-matching.md)。</span><span class="sxs-lookup"><span data-stu-id="8fd90-109">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="8fd90-110">有效參數清單都包含下列的範例。</span><span class="sxs-lookup"><span data-stu-id="8fd90-110">Lists of valid parameters include the following examples.</span></span>

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

<span data-ttu-id="8fd90-111">*運算式*是函式，其中在最後一個運算式會產生傳回值的主體。</span><span class="sxs-lookup"><span data-stu-id="8fd90-111">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="8fd90-112">有效的 lambda 運算式的範例包括：</span><span class="sxs-lookup"><span data-stu-id="8fd90-112">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet301.fs)]
    
## <a name="using-lambda-expressions"></a><span data-ttu-id="8fd90-113">使用 Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="8fd90-113">Using Lambda Expressions</span></span>
<span data-ttu-id="8fd90-114">當您想要在清單或另一個集合上執行作業，而且想要避免額外的工作定義函式的 lambda 運算式時特別有用的。</span><span class="sxs-lookup"><span data-stu-id="8fd90-114">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="8fd90-115">許多 F # 程式庫函式會接受做為引數，函式值，可以使用 lambda 運算式，在這些情況下特別方便。</span><span class="sxs-lookup"><span data-stu-id="8fd90-115">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="8fd90-116">下列程式碼將 lambda 運算式套用至清單的元素。</span><span class="sxs-lookup"><span data-stu-id="8fd90-116">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="8fd90-117">在此情況下，匿名函式會將 1 加入至清單的每個項目。</span><span class="sxs-lookup"><span data-stu-id="8fd90-117">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet302.fs)]
    
## <a name="see-also"></a><span data-ttu-id="8fd90-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8fd90-118">See Also</span></span>
[<span data-ttu-id="8fd90-119">函式</span><span class="sxs-lookup"><span data-stu-id="8fd90-119">Functions</span></span>](index.md)
