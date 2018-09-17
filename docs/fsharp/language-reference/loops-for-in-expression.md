---
title: 迴圈：for...in 運算式 (F#)
description: '請參閱如何 F # for...in...在運算式中迴圈建構來逐一查看的可列舉集合中的模式的相符項目。'
ms.date: 05/16/2016
ms.openlocfilehash: c4fba1f1dea3993cafa2e37ad0f32d9fb2eed85a
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45746257"
---
# <a name="loops-forin-expression"></a><span data-ttu-id="c663d-103">迴圈：for...in 運算式</span><span class="sxs-lookup"><span data-stu-id="c663d-103">Loops: for...in Expression</span></span>

<span data-ttu-id="c663d-104">這個迴圈建構來逐一查看的可列舉的集合，例如範圍運算式、 序列、 清單、 陣列或其他支援列舉的建構中模式的相符項目。</span><span class="sxs-lookup"><span data-stu-id="c663d-104">This looping construct is used to iterate over the matches of a pattern in an enumerable collection such as a range expression, sequence, list, array, or other construct that supports enumeration.</span></span>

## <a name="syntax"></a><span data-ttu-id="c663d-105">語法</span><span class="sxs-lookup"><span data-stu-id="c663d-105">Syntax</span></span>

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="c663d-106">備註</span><span class="sxs-lookup"><span data-stu-id="c663d-106">Remarks</span></span>

<span data-ttu-id="c663d-107">`for...in`運算式可以相較於`for each`其他.NET 語言中的陳述式因為它用來使用迴圈處理的可列舉集合中的值。</span><span class="sxs-lookup"><span data-stu-id="c663d-107">The `for...in` expression can be compared to the `for each` statement in other .NET languages because it is used to loop over the values in an enumerable collection.</span></span> <span data-ttu-id="c663d-108">不過，`for...in`也支援模式比對的集合，而不只是反覆項目，是透過對整個集合。</span><span class="sxs-lookup"><span data-stu-id="c663d-108">However, `for...in` also supports pattern matching over the collection instead of just iteration over the whole collection.</span></span>

<span data-ttu-id="c663d-109">可以指定的可列舉的運算式，為的可列舉集合，或使用`..`運算子，為整數型別上的範圍。</span><span class="sxs-lookup"><span data-stu-id="c663d-109">The enumerable expression can be specified as an enumerable collection or, by using the `..` operator, as a range on an integral type.</span></span> <span data-ttu-id="c663d-110">可列舉的集合包含清單、 序列、 陣列、 集、 對應等等。</span><span class="sxs-lookup"><span data-stu-id="c663d-110">Enumerable collections include lists, sequences, arrays, sets, maps, and so on.</span></span> <span data-ttu-id="c663d-111">可實作任何型別`System.Collections.IEnumerable`可用。</span><span class="sxs-lookup"><span data-stu-id="c663d-111">Any type that implements `System.Collections.IEnumerable` can be used.</span></span>

<span data-ttu-id="c663d-112">當您使用，表示範圍`..`運算子，您可以使用下列語法。</span><span class="sxs-lookup"><span data-stu-id="c663d-112">When you express a range by using the `..` operator, you can use the following syntax.</span></span>

<span data-ttu-id="c663d-113">*啟動*...</span><span class="sxs-lookup"><span data-stu-id="c663d-113">*start* ..</span></span> <span data-ttu-id="c663d-114">*[完成]*</span><span class="sxs-lookup"><span data-stu-id="c663d-114">*finish*</span></span>

<span data-ttu-id="c663d-115">您也可以使用的版本，包括呼叫遞增值*略過*，如下列程式碼。</span><span class="sxs-lookup"><span data-stu-id="c663d-115">You can also use a version that includes an increment called the *skip*, as in the following code.</span></span>

<span data-ttu-id="c663d-116">*啟動*...</span><span class="sxs-lookup"><span data-stu-id="c663d-116">*start* ..</span></span> <span data-ttu-id="c663d-117">*略過*...</span><span class="sxs-lookup"><span data-stu-id="c663d-117">*skip* ..</span></span> <span data-ttu-id="c663d-118">*[完成]*</span><span class="sxs-lookup"><span data-stu-id="c663d-118">*finish*</span></span>

<span data-ttu-id="c663d-119">當您使用整數類資料的範圍和簡單的計數器變數模式時，問題通常是在每個反覆項目，以 1 遞增計數器變數，但如果範圍包含略過值，此計數器會遞增所略過值改為。</span><span class="sxs-lookup"><span data-stu-id="c663d-119">When you use integral ranges and a simple counter variable as a pattern, the typical behavior is to increment the counter variable by 1 on each iteration, but if the range includes a skip value, the counter is incremented by the skip value instead.</span></span>

<span data-ttu-id="c663d-120">在模式比對的值也可用在主體的運算式。</span><span class="sxs-lookup"><span data-stu-id="c663d-120">Values matched in the pattern can also be used in the body expression.</span></span>

<span data-ttu-id="c663d-121">下列程式碼範例說明使用`for...in`運算式。</span><span class="sxs-lookup"><span data-stu-id="c663d-121">The following code examples illustrate the use of the `for...in` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

<span data-ttu-id="c663d-122">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="c663d-122">The output is as follows.</span></span>

```
1
5
100
450
788
```

<span data-ttu-id="c663d-123">下列範例會示範如何使用迴圈處理的順序，以及如何使用 tuple 模式，而不是簡單的變數。</span><span class="sxs-lookup"><span data-stu-id="c663d-123">The following example shows how to loop over a sequence, and how to use a tuple pattern instead of a simple variable.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

<span data-ttu-id="c663d-124">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="c663d-124">The output is as follows.</span></span>

```
1 squared is 1
2 squared is 4
3 squared is 9
4 squared is 16
5 squared is 25
6 squared is 36
7 squared is 49
8 squared is 64
9 squared is 81
10 squared is 100
```

<span data-ttu-id="c663d-125">下列範例示範如何使用迴圈處理簡單的整數範圍。</span><span class="sxs-lookup"><span data-stu-id="c663d-125">The following example shows how to loop over a simple integer range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

<span data-ttu-id="c663d-126">Function1 的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="c663d-126">The output of function1 is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
```

<span data-ttu-id="c663d-127">下列範例示範如何使用迴圈處理的範圍與略過為 2，其中包含之範圍的項目。</span><span class="sxs-lookup"><span data-stu-id="c663d-127">The following example shows how to loop over a range with a skip of 2, which includes every other element of the range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

<span data-ttu-id="c663d-128">輸出`function2`如下所示。</span><span class="sxs-lookup"><span data-stu-id="c663d-128">The output of `function2` is as follows.</span></span>

```
1 3 5 7 9
```

<span data-ttu-id="c663d-129">下列範例示範如何使用的字元範圍。</span><span class="sxs-lookup"><span data-stu-id="c663d-129">The following example shows how to use a character range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

<span data-ttu-id="c663d-130">輸出`function3`如下所示。</span><span class="sxs-lookup"><span data-stu-id="c663d-130">The output of `function3` is as follows.</span></span>

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

<span data-ttu-id="c663d-131">下列範例示範如何使用的負略過值反向反覆項目。</span><span class="sxs-lookup"><span data-stu-id="c663d-131">The following example shows how to use a negative skip value for a reverse iteration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

<span data-ttu-id="c663d-132">輸出`function4`如下所示。</span><span class="sxs-lookup"><span data-stu-id="c663d-132">The output of `function4` is as follows.</span></span>

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

<span data-ttu-id="c663d-133">開頭和結尾也可以是範圍的運算式，例如函式，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="c663d-133">The beginning and ending of the range can also be expressions, such as functions, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

<span data-ttu-id="c663d-134">輸出`function5`與這個輸入如下所示。</span><span class="sxs-lookup"><span data-stu-id="c663d-134">The output of `function5` with this input is as follows.</span></span>

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

<span data-ttu-id="c663d-135">下一個範例示範如何使用萬用字元 (\_) 迴圈中有不需要的項目。</span><span class="sxs-lookup"><span data-stu-id="c663d-135">The next example shows the use of a wildcard character (\_) when the element is not needed in the loop.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

<span data-ttu-id="c663d-136">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="c663d-136">The output is as follows.</span></span>

```
Number of elements in list1: 5
```

<span data-ttu-id="c663d-137">`Note` 您可以使用`for...in`循序項運算式和其他計算的運算式，在此情況下的自訂的版本`for...in`運算式的使用方式。</span><span class="sxs-lookup"><span data-stu-id="c663d-137">`Note` You can use `for...in` in sequence expressions and other computation expressions, in which case a customized version of the `for...in` expression is used.</span></span> <span data-ttu-id="c663d-138">如需詳細資訊，請參閱 <<c0> [ 序列](sequences.md)，[非同步工作流程](asynchronous-workflows.md)，並[計算運算式](computation-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="c663d-138">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c663d-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c663d-139">See also</span></span>

- [<span data-ttu-id="c663d-140">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="c663d-140">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="c663d-141">迴圈：`for...to` 運算式</span><span class="sxs-lookup"><span data-stu-id="c663d-141">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
- [<span data-ttu-id="c663d-142">迴圈：`while...do` 運算式</span><span class="sxs-lookup"><span data-stu-id="c663d-142">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
