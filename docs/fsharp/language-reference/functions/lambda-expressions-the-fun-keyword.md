---
title: Lambda 運算式:有趣的關鍵字
description: 瞭解如何使用F# ' 趣味 ' 關鍵字來定義 lambda 運算式, 這是匿名函式。
ms.date: 05/16/2016
ms.openlocfilehash: 9818724686dd83a7e352fb36819289fa19b002df
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630671"
---
# <a name="lambda-expressions-the-fun-keyword-f"></a><span data-ttu-id="2a41a-103">Lambda 運算式:有趣的關鍵字 (F#)</span><span class="sxs-lookup"><span data-stu-id="2a41a-103">Lambda Expressions: The fun Keyword (F#)</span></span>

<span data-ttu-id="2a41a-104">`fun`關鍵字是用來定義 lambda 運算式, 也就是匿名函式。</span><span class="sxs-lookup"><span data-stu-id="2a41a-104">The `fun` keyword is used to define a lambda expression, that is, an anonymous function.</span></span>

## <a name="syntax"></a><span data-ttu-id="2a41a-105">語法</span><span class="sxs-lookup"><span data-stu-id="2a41a-105">Syntax</span></span>

```fsharp
fun parameter-list -> expression
```

## <a name="remarks"></a><span data-ttu-id="2a41a-106">備註</span><span class="sxs-lookup"><span data-stu-id="2a41a-106">Remarks</span></span>

<span data-ttu-id="2a41a-107">*參數清單*通常包含名稱和選擇性的參數類型。</span><span class="sxs-lookup"><span data-stu-id="2a41a-107">The *parameter-list* typically consists of names and, optionally, types of parameters.</span></span> <span data-ttu-id="2a41a-108">更常見的情況是,*參數清單*可以由任何F#模式組成。</span><span class="sxs-lookup"><span data-stu-id="2a41a-108">More generally, the *parameter-list* can be composed of any F# patterns.</span></span> <span data-ttu-id="2a41a-109">如需可能模式的完整清單, 請參閱[模式](../pattern-matching.md)比對。</span><span class="sxs-lookup"><span data-stu-id="2a41a-109">For a full list of possible patterns, see [Pattern Matching](../pattern-matching.md).</span></span> <span data-ttu-id="2a41a-110">有效參數的清單包含下列範例。</span><span class="sxs-lookup"><span data-stu-id="2a41a-110">Lists of valid parameters include the following examples.</span></span>

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

<span data-ttu-id="2a41a-111">*運算式*是函式的主體, 最後一個運算式會產生傳回值。</span><span class="sxs-lookup"><span data-stu-id="2a41a-111">The *expression* is the body of the function, the last expression of which generates a return value.</span></span> <span data-ttu-id="2a41a-112">有效 lambda 運算式的範例包括下列各項:</span><span class="sxs-lookup"><span data-stu-id="2a41a-112">Examples of valid lambda expressions include the following:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet301.fs)]

## <a name="using-lambda-expressions"></a><span data-ttu-id="2a41a-113">使用 Lambda 運算式</span><span class="sxs-lookup"><span data-stu-id="2a41a-113">Using Lambda Expressions</span></span>

<span data-ttu-id="2a41a-114">當您想要對清單或其他集合執行作業, 而且想要避免定義函數的額外工作時, Lambda 運算式特別有用。</span><span class="sxs-lookup"><span data-stu-id="2a41a-114">Lambda expressions are especially useful when you want to perform operations on a list or other collection and want to avoid the extra work of defining a function.</span></span> <span data-ttu-id="2a41a-115">許多F#程式庫函式會採用函式值做為引數, 在這些情況下使用 lambda 運算式會特別方便。</span><span class="sxs-lookup"><span data-stu-id="2a41a-115">Many F# library functions take function values as arguments, and it can be especially convenient to use a lambda expression in those cases.</span></span> <span data-ttu-id="2a41a-116">下列程式碼會將 lambda 運算式套用至清單的元素。</span><span class="sxs-lookup"><span data-stu-id="2a41a-116">The following code applies a lambda expression to elements of a list.</span></span> <span data-ttu-id="2a41a-117">在此情況下, 匿名函式會將1新增至清單的每個元素。</span><span class="sxs-lookup"><span data-stu-id="2a41a-117">In this case, the anonymous function adds 1 to every element of a list.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet302.fs)]

## <a name="see-also"></a><span data-ttu-id="2a41a-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a41a-118">See also</span></span>

- [<span data-ttu-id="2a41a-119">函式</span><span class="sxs-lookup"><span data-stu-id="2a41a-119">Functions</span></span>](index.md)
