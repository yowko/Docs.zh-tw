---
title: 迴圈：for...in 運算式
description: F#查看 .。。在運算式迴圈結構中，是用來反復查看可列舉集合中的模式相符專案。
ms.date: 05/16/2016
ms.openlocfilehash: 5a2ca59ca4199ece5d78010ff780e86ae2b25181
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216455"
---
# <a name="loops-forin-expression"></a><span data-ttu-id="0f2ed-103">迴圈：for...in 運算式</span><span class="sxs-lookup"><span data-stu-id="0f2ed-103">Loops: for...in Expression</span></span>

<span data-ttu-id="0f2ed-104">這個迴圈結構是用來反復查看可列舉集合中的模式相符專案，例如範圍運算式、序列、清單、陣列或其他支援列舉的結構。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-104">This looping construct is used to iterate over the matches of a pattern in an enumerable collection such as a range expression, sequence, list, array, or other construct that supports enumeration.</span></span>

## <a name="syntax"></a><span data-ttu-id="0f2ed-105">語法</span><span class="sxs-lookup"><span data-stu-id="0f2ed-105">Syntax</span></span>

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="0f2ed-106">備註</span><span class="sxs-lookup"><span data-stu-id="0f2ed-106">Remarks</span></span>

<span data-ttu-id="0f2ed-107">運算式可以與其他 .net 語言中`for each`的語句比較，因為它是用來對可列舉集合中的值進行迴圈處理。 `for...in`</span><span class="sxs-lookup"><span data-stu-id="0f2ed-107">The `for...in` expression can be compared to the `for each` statement in other .NET languages because it is used to loop over the values in an enumerable collection.</span></span> <span data-ttu-id="0f2ed-108">不過， `for...in`也支援在集合上進行模式比對，而不只是在整個集合上反覆運算。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-108">However, `for...in` also supports pattern matching over the collection instead of just iteration over the whole collection.</span></span>

<span data-ttu-id="0f2ed-109">可列舉的運算式可以指定為可列舉集合，或使用`..`運算子做為整數類型的範圍。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-109">The enumerable expression can be specified as an enumerable collection or, by using the `..` operator, as a range on an integral type.</span></span> <span data-ttu-id="0f2ed-110">可列舉集合包含清單、序列、陣列、集合、對應等等。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-110">Enumerable collections include lists, sequences, arrays, sets, maps, and so on.</span></span> <span data-ttu-id="0f2ed-111">`System.Collections.IEnumerable`可以使用任何可執行檔型別。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-111">Any type that implements `System.Collections.IEnumerable` can be used.</span></span>

<span data-ttu-id="0f2ed-112">當您使用`..`運算子來表示範圍時，您可以使用下列語法。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-112">When you express a range by using the `..` operator, you can use the following syntax.</span></span>

<span data-ttu-id="0f2ed-113">*啟動*。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-113">*start* ..</span></span> <span data-ttu-id="0f2ed-114">*finish*</span><span class="sxs-lookup"><span data-stu-id="0f2ed-114">*finish*</span></span>

<span data-ttu-id="0f2ed-115">您也可以使用包含名為*skip*之遞增值的版本，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-115">You can also use a version that includes an increment called the *skip*, as in the following code.</span></span>

<span data-ttu-id="0f2ed-116">*啟動*。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-116">*start* ..</span></span> <span data-ttu-id="0f2ed-117">*略過*。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-117">*skip* ..</span></span> <span data-ttu-id="0f2ed-118">*finish*</span><span class="sxs-lookup"><span data-stu-id="0f2ed-118">*finish*</span></span>

<span data-ttu-id="0f2ed-119">當您使用整數範圍和簡單計數器變數做為模式時，一般的行為是在每個反復專案上將計數器變數遞增1，但如果範圍包含 skip 值，則會改由 skip 值來遞增計數器。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-119">When you use integral ranges and a simple counter variable as a pattern, the typical behavior is to increment the counter variable by 1 on each iteration, but if the range includes a skip value, the counter is incremented by the skip value instead.</span></span>

<span data-ttu-id="0f2ed-120">在此模式中符合的值也可以在主體運算式中使用。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-120">Values matched in the pattern can also be used in the body expression.</span></span>

<span data-ttu-id="0f2ed-121">下列程式碼範例說明`for...in`運算式的用法。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-121">The following code examples illustrate the use of the `for...in` expression.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

<span data-ttu-id="0f2ed-122">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-122">The output is as follows.</span></span>

```console
1
5
100
450
788
```

<span data-ttu-id="0f2ed-123">下列範例顯示如何在序列上執行迴圈，以及如何使用元組模式，而不是簡單變數。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-123">The following example shows how to loop over a sequence, and how to use a tuple pattern instead of a simple variable.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

<span data-ttu-id="0f2ed-124">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-124">The output is as follows.</span></span>

```console
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

<span data-ttu-id="0f2ed-125">下列範例示範如何在簡單的整數範圍內執行迴圈。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-125">The following example shows how to loop over a simple integer range.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

<span data-ttu-id="0f2ed-126">Function1 的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-126">The output of function1 is as follows.</span></span>

```console
1 2 3 4 5 6 7 8 9 10
```

<span data-ttu-id="0f2ed-127">下列範例示範如何使用略過2的範圍來迴圈，其中包括範圍的每個其他元素。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-127">The following example shows how to loop over a range with a skip of 2, which includes every other element of the range.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

<span data-ttu-id="0f2ed-128">的輸出`function2`如下所示。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-128">The output of `function2` is as follows.</span></span>

```console
1 3 5 7 9
```

<span data-ttu-id="0f2ed-129">下列範例顯示如何使用字元範圍。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-129">The following example shows how to use a character range.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

<span data-ttu-id="0f2ed-130">的輸出`function3`如下所示。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-130">The output of `function3` is as follows.</span></span>

```console
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

<span data-ttu-id="0f2ed-131">下列範例顯示如何使用反向反覆運算的負略過值。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-131">The following example shows how to use a negative skip value for a reverse iteration.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

<span data-ttu-id="0f2ed-132">的輸出`function4`如下所示。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-132">The output of `function4` is as follows.</span></span>

```console
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

<span data-ttu-id="0f2ed-133">範圍的開始和結束也可以是運算式，例如函式，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-133">The beginning and ending of the range can also be expressions, such as functions, as in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

<span data-ttu-id="0f2ed-134">`function5`具有此輸入的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-134">The output of `function5` with this input is as follows.</span></span>

```console
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

<span data-ttu-id="0f2ed-135">下一個範例顯示當迴圈中不需要元素時\_，使用萬用字元（）。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-135">The next example shows the use of a wildcard character (\_) when the element is not needed in the loop.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

<span data-ttu-id="0f2ed-136">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-136">The output is as follows.</span></span>

```console
Number of elements in list1: 5
```

<span data-ttu-id="0f2ed-137">`Note`您可以在`for...in`序列運算式和其他計算運算式中使用，在此情況下會使用自`for...in`定義版本的運算式。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-137">`Note` You can use `for...in` in sequence expressions and other computation expressions, in which case a customized version of the `for...in` expression is used.</span></span> <span data-ttu-id="0f2ed-138">如需詳細資訊，請參閱[序列](sequences.md)、[非同步工作流程](asynchronous-workflows.md)和[計算運算式](computation-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="0f2ed-138">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0f2ed-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f2ed-139">See also</span></span>

- [<span data-ttu-id="0f2ed-140">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="0f2ed-140">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="0f2ed-141">環回`for...to`運算式</span><span class="sxs-lookup"><span data-stu-id="0f2ed-141">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)
- [<span data-ttu-id="0f2ed-142">環回`while...do`運算式</span><span class="sxs-lookup"><span data-stu-id="0f2ed-142">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
