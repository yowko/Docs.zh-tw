---
title: "迴圈：for...in 運算式 (F#)"
description: "請參閱如何 F # for...in..運算式中迴圈建構用來反覆查看的可列舉集合中的模式比對。"
keywords: "Visual F#, F#, 函式程式設計"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: f54e3228-4aec-4d0a-ae37-bc3376508284
ms.openlocfilehash: d86aeb3bdd975261e59004d636354a740bd95c47
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="loops-forin-expression"></a><span data-ttu-id="347e6-104">迴圈：for...in 運算式</span><span class="sxs-lookup"><span data-stu-id="347e6-104">Loops: for...in Expression</span></span>

<span data-ttu-id="347e6-105">此迴圈建構用來反覆查看的可列舉集合，例如範圍運算式、 序列、 清單、 陣列或其他支援列舉的建構中的某個模式的相符項目。</span><span class="sxs-lookup"><span data-stu-id="347e6-105">This looping construct is used to iterate over the matches of a pattern in an enumerable collection such as a range expression, sequence, list, array, or other construct that supports enumeration.</span></span>


## <a name="syntax"></a><span data-ttu-id="347e6-106">語法</span><span class="sxs-lookup"><span data-stu-id="347e6-106">Syntax</span></span>

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="347e6-107">備註</span><span class="sxs-lookup"><span data-stu-id="347e6-107">Remarks</span></span>
<span data-ttu-id="347e6-108">`for...in`運算式可以相較於`for each`其他.NET 語言中的陳述式因為它用來循環的可列舉集合中的值。</span><span class="sxs-lookup"><span data-stu-id="347e6-108">The `for...in` expression can be compared to the `for each` statement in other .NET languages because it is used to loop over the values in an enumerable collection.</span></span> <span data-ttu-id="347e6-109">不過，`for...in`也支援整個集合，而不是只是反覆項目集合上比對的模式。</span><span class="sxs-lookup"><span data-stu-id="347e6-109">However, `for...in` also supports pattern matching over the collection instead of just iteration over the whole collection.</span></span>

<span data-ttu-id="347e6-110">可列舉的運算式可以指定成可列舉集合，或使用`..`運算子，為整數類型的範圍。</span><span class="sxs-lookup"><span data-stu-id="347e6-110">The enumerable expression can be specified as an enumerable collection or, by using the `..` operator, as a range on an integral type.</span></span> <span data-ttu-id="347e6-111">可列舉集合包括清單、 序列、 陣列、 集合、 對應等等。</span><span class="sxs-lookup"><span data-stu-id="347e6-111">Enumerable collections include lists, sequences, arrays, sets, maps, and so on.</span></span> <span data-ttu-id="347e6-112">實作的任何類型`System.Collections.IEnumerable`可用。</span><span class="sxs-lookup"><span data-stu-id="347e6-112">Any type that implements `System.Collections.IEnumerable` can be used.</span></span>

<span data-ttu-id="347e6-113">當您使用 express 範圍`..`運算子，您可以使用下列語法。</span><span class="sxs-lookup"><span data-stu-id="347e6-113">When you express a range by using the `..` operator, you can use the following syntax.</span></span>

<span data-ttu-id="347e6-114">*啟動*...</span><span class="sxs-lookup"><span data-stu-id="347e6-114">*start* ..</span></span> <span data-ttu-id="347e6-115">*[完成]*</span><span class="sxs-lookup"><span data-stu-id="347e6-115">*finish*</span></span>

<span data-ttu-id="347e6-116">您也可以使用包含呼叫遞增值的版本*略過*，在下列程式碼中。</span><span class="sxs-lookup"><span data-stu-id="347e6-116">You can also use a version that includes an increment called the *skip*, as in the following code.</span></span>

<span data-ttu-id="347e6-117">*啟動*...</span><span class="sxs-lookup"><span data-stu-id="347e6-117">*start* ..</span></span> <span data-ttu-id="347e6-118">*略過*...</span><span class="sxs-lookup"><span data-stu-id="347e6-118">*skip* ..</span></span> <span data-ttu-id="347e6-119">*[完成]*</span><span class="sxs-lookup"><span data-stu-id="347e6-119">*finish*</span></span>

<span data-ttu-id="347e6-120">當您使用整數類資料的範圍和簡單的計數器變數作為模式時，問題通常是在每個反覆項目，以 1 遞增計數器變數，但如果範圍包含略過值時，此計數器會遞增略過值改為。</span><span class="sxs-lookup"><span data-stu-id="347e6-120">When you use integral ranges and a simple counter variable as a pattern, the typical behavior is to increment the counter variable by 1 on each iteration, but if the range includes a skip value, the counter is incremented by the skip value instead.</span></span>

<span data-ttu-id="347e6-121">在模式比對的值也可用在本文的運算式。</span><span class="sxs-lookup"><span data-stu-id="347e6-121">Values matched in the pattern can also be used in the body expression.</span></span>

<span data-ttu-id="347e6-122">下列程式碼範例說明使用`for...in`運算式。</span><span class="sxs-lookup"><span data-stu-id="347e6-122">The following code examples illustrate the use of the `for...in` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

<span data-ttu-id="347e6-123">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="347e6-123">The output is as follows.</span></span>

```
1
5
100
450
788
```

<span data-ttu-id="347e6-124">下列範例示範如何迴圈時的順序，以及如何使用 tuple 模式，而不是簡單的變數。</span><span class="sxs-lookup"><span data-stu-id="347e6-124">The following example shows how to loop over a sequence, and how to use a tuple pattern instead of a simple variable.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

<span data-ttu-id="347e6-125">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="347e6-125">The output is as follows.</span></span>

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

<span data-ttu-id="347e6-126">下列範例會示範如何在迴圈的一個簡單的整數範圍內。</span><span class="sxs-lookup"><span data-stu-id="347e6-126">The following example shows how to loop over a simple integer range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

<span data-ttu-id="347e6-127">Function1 的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="347e6-127">The output of function1 is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
```

<span data-ttu-id="347e6-128">下列範例會示範如何使用 skip 2，其中包含的範圍的項目範圍內執行迴圈。</span><span class="sxs-lookup"><span data-stu-id="347e6-128">The following example shows how to loop over a range with a skip of 2, which includes every other element of the range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

<span data-ttu-id="347e6-129">輸出`function2`如下所示。</span><span class="sxs-lookup"><span data-stu-id="347e6-129">The output of `function2` is as follows.</span></span>

```
1 3 5 7 9
```

<span data-ttu-id="347e6-130">下列範例會示範如何使用的字元範圍。</span><span class="sxs-lookup"><span data-stu-id="347e6-130">The following example shows how to use a character range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

<span data-ttu-id="347e6-131">輸出`function3`如下所示。</span><span class="sxs-lookup"><span data-stu-id="347e6-131">The output of `function3` is as follows.</span></span>

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

<span data-ttu-id="347e6-132">下列範例會示範如何使用反向反覆項目中的負 skip 值。</span><span class="sxs-lookup"><span data-stu-id="347e6-132">The following example shows how to use a negative skip value for a reverse iteration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

<span data-ttu-id="347e6-133">輸出`function4`如下所示。</span><span class="sxs-lookup"><span data-stu-id="347e6-133">The output of `function4` is as follows.</span></span>

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

<span data-ttu-id="347e6-134">開頭和結尾範圍也可以是運算式，例如函式，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="347e6-134">The beginning and ending of the range can also be expressions, such as functions, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

<span data-ttu-id="347e6-135">輸出`function5`與這個輸入如下所示。</span><span class="sxs-lookup"><span data-stu-id="347e6-135">The output of `function5` with this input is as follows.</span></span>

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

<span data-ttu-id="347e6-136">項目不需要在迴圈中時下, 一個範例顯示使用萬用字元字元 (_)。</span><span class="sxs-lookup"><span data-stu-id="347e6-136">The next example shows the use of a wildcard character (_) when the element is not needed in the loop.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

<span data-ttu-id="347e6-137">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="347e6-137">The output is as follows.</span></span>

```
Number of elements in list1: 5
```

<span data-ttu-id="347e6-138">`Note`您可以使用`for...in`在循序項運算式和其他計算的運算式，在此情況下的自訂的版本`for...in`運算式使用。</span><span class="sxs-lookup"><span data-stu-id="347e6-138">`Note` You can use `for...in` in sequence expressions and other computation expressions, in which case a customized version of the `for...in` expression is used.</span></span> <span data-ttu-id="347e6-139">如需詳細資訊，請參閱[序列](sequences.md)，[非同步工作流程](asynchronous-workflows.md)，和[計算運算式](computation-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="347e6-139">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="347e6-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="347e6-140">See Also</span></span>
[<span data-ttu-id="347e6-141">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="347e6-141">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="347e6-142">迴圈：`for...to` 運算式</span><span class="sxs-lookup"><span data-stu-id="347e6-142">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)

[<span data-ttu-id="347e6-143">迴圈：`while...do` 運算式</span><span class="sxs-lookup"><span data-stu-id="347e6-143">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
