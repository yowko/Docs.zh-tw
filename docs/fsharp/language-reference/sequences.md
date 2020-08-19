---
title: 序列
description: '瞭解如何使用 F # 序列（當您有大量、依序排列的資料集合，但不一定會預期使用所有元素）。'
ms.date: 08/13/2020
ms.openlocfilehash: c84e0aebcc79a595c0ae3b9075648fb629bdd65c
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559033"
---
# <a name="sequences"></a><span data-ttu-id="26f7d-103">序列</span><span class="sxs-lookup"><span data-stu-id="26f7d-103">Sequences</span></span>

<span data-ttu-id="26f7d-104">「 *序列* 」（sequence）是一種元素的邏輯系列，全都是一種類型。</span><span class="sxs-lookup"><span data-stu-id="26f7d-104">A *sequence* is a logical series of elements all of one type.</span></span> <span data-ttu-id="26f7d-105">當您有大量的資料收集，但不一定會預期使用所有元素時，序列特別有用。</span><span class="sxs-lookup"><span data-stu-id="26f7d-105">Sequences are particularly useful when you have a large, ordered collection of data but do not necessarily expect to use all of the elements.</span></span> <span data-ttu-id="26f7d-106">個別順序元素只會在必要時計算，因此在不使用所有元素的情況下，序列可以提供比清單更佳的效能。</span><span class="sxs-lookup"><span data-stu-id="26f7d-106">Individual sequence elements are computed only as required, so a sequence can provide better performance than a list in situations in which not all the elements are used.</span></span> <span data-ttu-id="26f7d-107">順序是以類型表示 `seq<'T>` ，這是的別名 <xref:System.Collections.Generic.IEnumerable%601> 。</span><span class="sxs-lookup"><span data-stu-id="26f7d-107">Sequences are represented by the `seq<'T>` type, which is an alias for <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="26f7d-108">因此，任何實介面的 .NET 型別都 <xref:System.Collections.Generic.IEnumerable%601> 可以用來做為序列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-108">Therefore, any .NET type that implements <xref:System.Collections.Generic.IEnumerable%601> interface can be used as a sequence.</span></span> <span data-ttu-id="26f7d-109">[Seq 模組](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html)可支援涉及序列的操作。</span><span class="sxs-lookup"><span data-stu-id="26f7d-109">The [Seq module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html) provides support for manipulations involving sequences.</span></span>

## <a name="sequence-expressions"></a><span data-ttu-id="26f7d-110">序列運算式</span><span class="sxs-lookup"><span data-stu-id="26f7d-110">Sequence Expressions</span></span>

<span data-ttu-id="26f7d-111">*順序運算式*是評估為序列的運算式。</span><span class="sxs-lookup"><span data-stu-id="26f7d-111">A *sequence expression* is an expression that evaluates to a sequence.</span></span> <span data-ttu-id="26f7d-112">順序運算式可採用許多形式。</span><span class="sxs-lookup"><span data-stu-id="26f7d-112">Sequence expressions can take a number of forms.</span></span> <span data-ttu-id="26f7d-113">最簡單的形式會指定範圍。</span><span class="sxs-lookup"><span data-stu-id="26f7d-113">The simplest form specifies a range.</span></span> <span data-ttu-id="26f7d-114">例如， `seq { 1 .. 5 }` 建立包含五個元素的序列，包括端點1和5。</span><span class="sxs-lookup"><span data-stu-id="26f7d-114">For example, `seq { 1 .. 5 }` creates a sequence that contains five elements, including the endpoints 1 and 5.</span></span> <span data-ttu-id="26f7d-115">您也可以指定遞增 (，或在兩個雙句點之間遞減) 。</span><span class="sxs-lookup"><span data-stu-id="26f7d-115">You can also specify an increment (or decrement) between two double periods.</span></span> <span data-ttu-id="26f7d-116">例如，下列程式碼會建立10的倍數序列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-116">For example, the following code creates the sequence of multiples of 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

<span data-ttu-id="26f7d-117">順序運算式是由產生序列值的 F # 運算式所組成。</span><span class="sxs-lookup"><span data-stu-id="26f7d-117">Sequence expressions are made up of F# expressions that produce values of the sequence.</span></span> <span data-ttu-id="26f7d-118">您也可以透過程式設計的方式產生值：</span><span class="sxs-lookup"><span data-stu-id="26f7d-118">You can also generate values programmatically:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

<span data-ttu-id="26f7d-119">先前的範例使用 `->` 運算子，可讓您指定其值將成為序列一部分的運算式。</span><span class="sxs-lookup"><span data-stu-id="26f7d-119">The previous sample uses the `->` operator, which allows you to specify an expression whose value will become a part of the sequence.</span></span> <span data-ttu-id="26f7d-120">您只能使用 `->` （如果其後的程式碼的每個部分都傳回值）。</span><span class="sxs-lookup"><span data-stu-id="26f7d-120">You can only use `->` if every part of the code that follows it returns a value.</span></span>

<span data-ttu-id="26f7d-121">或者，您也可以指定 `do` 關鍵字，並選擇性 `yield` 的方法如下：</span><span class="sxs-lookup"><span data-stu-id="26f7d-121">Alternatively, you can specify the `do` keyword, with an optional `yield` that follows:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

<span data-ttu-id="26f7d-122">下列程式碼會產生一份座標組清單，以及代表方格的陣列中的索引。</span><span class="sxs-lookup"><span data-stu-id="26f7d-122">The following code generates a list of coordinate pairs along with an index into an array that represents the grid.</span></span> <span data-ttu-id="26f7d-123">請注意，第一個 `for` 運算式需要 `do` 指定。</span><span class="sxs-lookup"><span data-stu-id="26f7d-123">Note that the first `for` expression requires a `do` to be specified.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

<span data-ttu-id="26f7d-124">`if`序列中使用的運算式是篩選準則。</span><span class="sxs-lookup"><span data-stu-id="26f7d-124">An `if` expression used in a sequence is a filter.</span></span> <span data-ttu-id="26f7d-125">例如，若要產生只有一個質數的序列，假設您有一個 `isprime` 類型的函式 `int -> bool` ，請依照下列方式來建立順序。</span><span class="sxs-lookup"><span data-stu-id="26f7d-125">For example, to generate a sequence of only prime numbers, assuming that you have a function `isprime` of type `int -> bool`, construct the sequence as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

<span data-ttu-id="26f7d-126">如先前所述，在 `do` 這裡是必要的，因為沒有 `else` 與搭配使用的分支 `if` 。</span><span class="sxs-lookup"><span data-stu-id="26f7d-126">As mentioned previously, `do` is required here because there is no `else` branch that goes with the `if`.</span></span> <span data-ttu-id="26f7d-127">如果您嘗試使用 `->` ，您會收到錯誤，指出並非所有分支都會傳回值。</span><span class="sxs-lookup"><span data-stu-id="26f7d-127">If you try to use `->`, you'll get an error saying that not all branches return a value.</span></span>

## <a name="the-yield-keyword"></a><span data-ttu-id="26f7d-128">`yield!` 關鍵字</span><span class="sxs-lookup"><span data-stu-id="26f7d-128">The `yield!` keyword</span></span>

<span data-ttu-id="26f7d-129">有時，您可能會想要在另一個序列中包含一系列的元素。</span><span class="sxs-lookup"><span data-stu-id="26f7d-129">Sometimes, you may wish to include a sequence of elements into another sequence.</span></span> <span data-ttu-id="26f7d-130">若要在另一個序列內包含序列，您必須使用 `yield!` 關鍵字：</span><span class="sxs-lookup"><span data-stu-id="26f7d-130">To include a sequence within another sequence, you'll need to use the `yield!` keyword:</span></span>

```fsharp
// Repeats '1 2 3 4 5' ten times
seq {
    for _ in 1..10 do
        yield! seq { 1; 2; 3; 4; 5}
}
```

<span data-ttu-id="26f7d-131">另一種思考方式 `yield!` 是將內部序列壓平合併，然後將它包含在包含順序中。</span><span class="sxs-lookup"><span data-stu-id="26f7d-131">Another way of thinking of `yield!` is that it flattens an inner sequence and then includes that in the containing sequence.</span></span>

<span data-ttu-id="26f7d-132">`yield!`在運算式中使用時，所有其他的單一值都必須使用 `yield` 關鍵字：</span><span class="sxs-lookup"><span data-stu-id="26f7d-132">When `yield!` is used in an expression, all other single values must use the `yield` keyword:</span></span>

```fsharp
// Combine repeated values with their values
seq {
    for x in 1..10 do
        yield x
        yield! seq { for i in 1..x -> i}
}
```

<span data-ttu-id="26f7d-133">上述範例會產生的值， `x` 以及每個的所有值 `1` `x` `x` 。</span><span class="sxs-lookup"><span data-stu-id="26f7d-133">The previous example will produce the value of `x` in addition to all values from `1` to `x` for each `x`.</span></span>

## <a name="examples"></a><span data-ttu-id="26f7d-134">範例</span><span class="sxs-lookup"><span data-stu-id="26f7d-134">Examples</span></span>

<span data-ttu-id="26f7d-135">第一個範例會使用包含反復專案、篩選和 yield 的序列運算式來產生陣列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-135">The first example uses a sequence expression that contains an iteration, a filter, and a yield to generate an array.</span></span> <span data-ttu-id="26f7d-136">此程式碼會將1和100之間的質數序列列印到主控台。</span><span class="sxs-lookup"><span data-stu-id="26f7d-136">This code prints a sequence of prime numbers between 1 and 100 to the console.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

<span data-ttu-id="26f7d-137">下列範例會建立一個由三個元素的元組組成的乘法資料表，其中每個專案都包含兩個因素和產品：</span><span class="sxs-lookup"><span data-stu-id="26f7d-137">The following example creates a multiplication table that consists of tuples of three elements, each consisting of two factors and the product:</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

<span data-ttu-id="26f7d-138">下列範例示範如何使用，將 `yield!` 個別序列合併成單一的最終順序。</span><span class="sxs-lookup"><span data-stu-id="26f7d-138">The following example demonstrates the use of `yield!` to combine individual sequences into a single final sequence.</span></span> <span data-ttu-id="26f7d-139">在此情況下，二進位樹狀結構中的每個子樹的序列會串連在遞迴函式中，以產生最終的順序。</span><span class="sxs-lookup"><span data-stu-id="26f7d-139">In this case, the sequences for each subtree in a binary tree are concatenated in a recursive function to produce the final sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]

## <a name="using-sequences"></a><span data-ttu-id="26f7d-140">使用順序</span><span class="sxs-lookup"><span data-stu-id="26f7d-140">Using Sequences</span></span>

<span data-ttu-id="26f7d-141">序列支援許多與 [清單](lists.md)相同的功能。</span><span class="sxs-lookup"><span data-stu-id="26f7d-141">Sequences support many of the same functions as [lists](lists.md).</span></span> <span data-ttu-id="26f7d-142">序列也支援使用按鍵產生函數進行分組和計算等作業。</span><span class="sxs-lookup"><span data-stu-id="26f7d-142">Sequences also support operations such as grouping and counting by using key-generating functions.</span></span> <span data-ttu-id="26f7d-143">序列也支援更多樣化的函式來解壓縮個子序列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-143">Sequences also support more diverse functions for extracting subsequences.</span></span>

<span data-ttu-id="26f7d-144">許多資料類型（例如清單、陣列、集合和地圖）都是可列舉的集合，因此是隱含的序列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-144">Many data types, such as lists, arrays, sets, and maps are implicitly sequences because they are enumerable collections.</span></span> <span data-ttu-id="26f7d-145">接受序列做為引數的函式可搭配任何一般 F # 資料型別使用，除了任何執行的 .NET 資料類型之外 `System.Collections.Generic.IEnumerable<'T>` 。</span><span class="sxs-lookup"><span data-stu-id="26f7d-145">A function that takes a sequence as an argument works with any of the common F# data types, in addition to any .NET data type that implements `System.Collections.Generic.IEnumerable<'T>`.</span></span> <span data-ttu-id="26f7d-146">將其與接受清單作為引數的函式相比較，該函式只能接受清單。</span><span class="sxs-lookup"><span data-stu-id="26f7d-146">Contrast this to a function that takes a list as an argument, which can only take lists.</span></span> <span data-ttu-id="26f7d-147">此類型 `seq<'T>` 是的類型縮寫 `IEnumerable<'T>` 。</span><span class="sxs-lookup"><span data-stu-id="26f7d-147">The type `seq<'T>` is a type abbreviation for `IEnumerable<'T>`.</span></span> <span data-ttu-id="26f7d-148">這表示任何實作為泛型的型別（ `System.Collections.Generic.IEnumerable<'T>` 包括 F # 中的陣列、清單、集合和對應，以及大部分的 .net 集合型別）都與型別相容， `seq` 而且可以在預期順序的任何地方使用。</span><span class="sxs-lookup"><span data-stu-id="26f7d-148">This means that any type that implements the generic `System.Collections.Generic.IEnumerable<'T>`, which includes arrays, lists, sets, and maps in F#, and also most .NET collection types, is compatible with the `seq` type and can be used wherever a sequence is expected.</span></span>

## <a name="module-functions"></a><span data-ttu-id="26f7d-149">模組函式</span><span class="sxs-lookup"><span data-stu-id="26f7d-149">Module Functions</span></span>

<span data-ttu-id="26f7d-150">[Fsharp.core 命名空間](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections.html)中的[Seq 模組](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html)包含使用順序的函式。</span><span class="sxs-lookup"><span data-stu-id="26f7d-150">The [Seq module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html) in the [FSharp.Collections namespace](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections.html) contains functions for working with sequences.</span></span> <span data-ttu-id="26f7d-151">這些函式也適用于清單、陣列、對應和集合，因為所有這些類型都是可列舉的，因此可視為序列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-151">These functions work with lists, arrays, maps, and sets as well, because all of those types are enumerable, and therefore can be treated as sequences.</span></span>

## <a name="creating-sequences"></a><span data-ttu-id="26f7d-152">建立序列</span><span class="sxs-lookup"><span data-stu-id="26f7d-152">Creating Sequences</span></span>

<span data-ttu-id="26f7d-153">您可以使用順序運算式（如先前所述），或使用特定函數來建立順序。</span><span class="sxs-lookup"><span data-stu-id="26f7d-153">You can create sequences by using sequence expressions, as described previously, or by using certain functions.</span></span>

<span data-ttu-id="26f7d-154">您可以使用 [seq. 空白](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#empty)來建立空的序列，也可以使用 [seq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#singleton)來建立只有一個指定元素的序列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-154">You can create an empty sequence by using [Seq.empty](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#empty), or you can create a sequence of just one specified element by using [Seq.singleton](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#singleton).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet9.fs)]

<span data-ttu-id="26f7d-155">您可以使用 [Seq.init](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#init) 來建立使用您提供的函式來建立元素的序列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-155">You can use [Seq.init](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#init) to create a sequence for which the elements are created by using a function that you provide.</span></span> <span data-ttu-id="26f7d-156">您也會提供序列的大小。</span><span class="sxs-lookup"><span data-stu-id="26f7d-156">You also provide a size for the sequence.</span></span> <span data-ttu-id="26f7d-157">此函式就像 [List.init](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#init)一樣，不同的是在您逐一查看序列之前，不會建立元素。</span><span class="sxs-lookup"><span data-stu-id="26f7d-157">This function is just like [List.init](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#init), except that the elements are not created until you iterate through the sequence.</span></span> <span data-ttu-id="26f7d-158">下列程式碼說明如何使用 `Seq.init` 。</span><span class="sxs-lookup"><span data-stu-id="26f7d-158">The following code illustrates the use of `Seq.init`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet10.fs)]

<span data-ttu-id="26f7d-159">輸出為</span><span class="sxs-lookup"><span data-stu-id="26f7d-159">The output is</span></span>

```console
0 10 20 30 40
```

<span data-ttu-id="26f7d-160">您可以使用 [list.ofarray](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#ofArray) 和 [seq. ofList&#60; t&#62; 函數](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#ofList)，從陣列和清單建立序列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-160">By using [Seq.ofArray](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#ofArray) and [Seq.ofList&#60;'T&#62; Function](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#ofList), you can create sequences from arrays and lists.</span></span> <span data-ttu-id="26f7d-161">不過，您也可以使用轉換運算子，將陣列和清單轉換成序列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-161">However, you can also convert arrays and lists to sequences by using a cast operator.</span></span> <span data-ttu-id="26f7d-162">下列程式碼中會顯示這兩種技術。</span><span class="sxs-lookup"><span data-stu-id="26f7d-162">Both techniques are shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet11.fs)]

<span data-ttu-id="26f7d-163">藉由使用 [Seq 轉換](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#cast)，您可以從弱型別集合中建立序列，例如中定義的序列 `System.Collections` 。</span><span class="sxs-lookup"><span data-stu-id="26f7d-163">By using [Seq.cast](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#cast), you can create a sequence from a weakly typed collection, such as those defined in `System.Collections`.</span></span> <span data-ttu-id="26f7d-164">這類弱型別集合具有元素類型 `System.Object` ，而且是使用非泛型型別來列舉 `System.Collections.Generic.IEnumerable&#96;1` 。</span><span class="sxs-lookup"><span data-stu-id="26f7d-164">Such weakly typed collections have the element type `System.Object` and are enumerated by using the non-generic `System.Collections.Generic.IEnumerable&#96;1` type.</span></span> <span data-ttu-id="26f7d-165">下列程式碼說明如何使用將 `Seq.cast` 轉換 `System.Collections.ArrayList` 成序列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-165">The following code illustrates the use of `Seq.cast` to convert an `System.Collections.ArrayList` into a sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet12.fs)]

<span data-ttu-id="26f7d-166">您可以使用 [Seq.initInfinite](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#initInfinite) 函數來定義無限序列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-166">You can define infinite sequences by using the [Seq.initInfinite](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#initInfinite) function.</span></span> <span data-ttu-id="26f7d-167">針對這類序列，您會提供一個函式，以從專案的索引產生每個元素。</span><span class="sxs-lookup"><span data-stu-id="26f7d-167">For such a sequence, you provide a function that generates each element from the index of the element.</span></span> <span data-ttu-id="26f7d-168">由於延遲評估，因此可能會有無限的順序;您可以藉由呼叫您指定的函式，視需要建立元素。</span><span class="sxs-lookup"><span data-stu-id="26f7d-168">Infinite sequences are possible because of lazy evaluation; elements are created as needed by calling the function that you specify.</span></span> <span data-ttu-id="26f7d-169">下列程式碼範例會產生無限的浮點數序列，在此案例中為連續整數平方的 reciprocals 序列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-169">The following code example produces an infinite sequence of floating point numbers, in this case the alternating series of reciprocals of squares of successive integers.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet13.fs)]

<span data-ttu-id="26f7d-170">[Seq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#unfold) 會從計算函式產生順序，此函式會接受狀態並將其轉換為產生序列中的每個後續元素。</span><span class="sxs-lookup"><span data-stu-id="26f7d-170">[Seq.unfold](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#unfold) generates a sequence from a computation function that takes a state and transforms it to produce each subsequent element in the sequence.</span></span> <span data-ttu-id="26f7d-171">此狀態只是用來計算每個專案的值，而且可在每個元素計算時變更。</span><span class="sxs-lookup"><span data-stu-id="26f7d-171">The state is just a value that is used to compute each element, and can change as each element is computed.</span></span> <span data-ttu-id="26f7d-172">的第二個引數 `Seq.unfold` 是用來啟動序列的起始值。</span><span class="sxs-lookup"><span data-stu-id="26f7d-172">The second argument to `Seq.unfold` is the initial value that is used to start the sequence.</span></span> <span data-ttu-id="26f7d-173">`Seq.unfold` 使用狀態的選項類型，可讓您藉由傳回值來終止序列 `None` 。</span><span class="sxs-lookup"><span data-stu-id="26f7d-173">`Seq.unfold` uses an option type for the state, which enables you to terminate the sequence by returning the `None` value.</span></span> <span data-ttu-id="26f7d-174">下列程式碼顯示兩個序列範例， `seq1` 以及 `fib` 由作業產生的 `unfold` 。</span><span class="sxs-lookup"><span data-stu-id="26f7d-174">The following code shows two examples of sequences, `seq1` and `fib`, that are generated by an `unfold` operation.</span></span> <span data-ttu-id="26f7d-175">第一個， `seq1` 是最多20個數字的簡單序列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-175">The first, `seq1`, is just a simple sequence with numbers up to 20.</span></span> <span data-ttu-id="26f7d-176">第二個會 `fib` 使用 `unfold` 來計算斐波里的序列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-176">The second, `fib`, uses `unfold` to compute the Fibonacci sequence.</span></span> <span data-ttu-id="26f7d-177">因為量值序列中的每個元素都是前兩個斐的兩個量值的總和，所以狀態值是由序列中前兩個數字組成的元組。</span><span class="sxs-lookup"><span data-stu-id="26f7d-177">Because each element in the Fibonacci sequence is the sum of the previous two Fibonacci numbers, the state value is a tuple that consists of the previous two numbers in the sequence.</span></span> <span data-ttu-id="26f7d-178">初始值是 `(1,1)` 序列中的前兩個數字。</span><span class="sxs-lookup"><span data-stu-id="26f7d-178">The initial value is `(1,1)`, the first two numbers in the sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet14.fs)]

<span data-ttu-id="26f7d-179">輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="26f7d-179">The output is as follows:</span></span>

```console
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

<span data-ttu-id="26f7d-180">下列程式碼範例會使用此處所述的許多序列模組函式來產生和計算無限序列的值。</span><span class="sxs-lookup"><span data-stu-id="26f7d-180">The following code is an example that uses many of the sequence module functions described here to generate and compute the values of infinite sequences.</span></span> <span data-ttu-id="26f7d-181">程式碼可能需要幾分鐘的時間來執行。</span><span class="sxs-lookup"><span data-stu-id="26f7d-181">The code might take a few minutes to run.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet15.fs)]

## <a name="searching-and-finding-elements"></a><span data-ttu-id="26f7d-182">搜尋和尋找元素</span><span class="sxs-lookup"><span data-stu-id="26f7d-182">Searching and Finding Elements</span></span>

<span data-ttu-id="26f7d-183">序列支援清單的可用功能： [Seq. exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#exists)、 [array.exists2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#exists)、 [seq. find](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#find)、 [findIndex](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#findIndex)、 [Seq. pick](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#pick)、 [tryFind](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#tryFind)和 [array.tryfindindex](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#tryFindIndex)。</span><span class="sxs-lookup"><span data-stu-id="26f7d-183">Sequences support functionality available with lists: [Seq.exists](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#exists), [Seq.exists2](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#exists), [Seq.find](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#find), [Seq.findIndex](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#findIndex), [Seq.pick](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#pick), [Seq.tryFind](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#tryFind), and [Seq.tryFindIndex](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#tryFindIndex).</span></span> <span data-ttu-id="26f7d-184">這些可用於序列的函式版本，只會評估序列到所搜尋的專案。</span><span class="sxs-lookup"><span data-stu-id="26f7d-184">The versions of these functions that are available for sequences evaluate the sequence only up to the element that is being searched for.</span></span> <span data-ttu-id="26f7d-185">如需範例，請參閱 [清單](lists.md)。</span><span class="sxs-lookup"><span data-stu-id="26f7d-185">For examples, see [Lists](lists.md).</span></span>

## <a name="obtaining-subsequences"></a><span data-ttu-id="26f7d-186">取得個子序列</span><span class="sxs-lookup"><span data-stu-id="26f7d-186">Obtaining Subsequences</span></span>

<span data-ttu-id="26f7d-187">[Seq. filter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#filter) 和 [seq。 choose](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#choose) 如同可用於清單的對應函式，不同的是，在評估 sequence 元素之前，不會發生篩選和選擇。</span><span class="sxs-lookup"><span data-stu-id="26f7d-187">[Seq.filter](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#filter) and [Seq.choose](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#choose) are like the corresponding functions that are available for lists, except that the filtering and choosing does not occur until the sequence elements are evaluated.</span></span>

<span data-ttu-id="26f7d-188">[Seq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#truncate) 會從另一個序列建立序列，但會將序列限制為指定的元素數目。</span><span class="sxs-lookup"><span data-stu-id="26f7d-188">[Seq.truncate](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#truncate) creates a sequence from another sequence, but limits the sequence to a specified number of elements.</span></span> <span data-ttu-id="26f7d-189">[Seq： take 會](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#take) 建立新的序列，其中只包含序列開頭的指定元素數目。</span><span class="sxs-lookup"><span data-stu-id="26f7d-189">[Seq.take](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#take) creates a new sequence that contains only a specified number of elements from the start of a sequence.</span></span> <span data-ttu-id="26f7d-190">如果序列中的專案數少於您所指定的時間，則會擲回 `Seq.take` `System.InvalidOperationException` 。</span><span class="sxs-lookup"><span data-stu-id="26f7d-190">If there are fewer elements in the sequence than you specify to take, `Seq.take` throws a `System.InvalidOperationException`.</span></span> <span data-ttu-id="26f7d-191">和之間的差異在於， `Seq.take` `Seq.truncate` `Seq.truncate` 如果元素數目少於您指定的數目，則不會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="26f7d-191">The difference between `Seq.take` and `Seq.truncate` is that `Seq.truncate` does not produce an error if the number of elements is fewer than the number you specify.</span></span>

<span data-ttu-id="26f7d-192">下列程式碼顯示和之間的行為和差異 `Seq.truncate` `Seq.take` 。</span><span class="sxs-lookup"><span data-stu-id="26f7d-192">The following code shows the behavior of and differences between `Seq.truncate` and `Seq.take`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet16.fs)]

<span data-ttu-id="26f7d-193">發生錯誤之前的輸出會如下所示。</span><span class="sxs-lookup"><span data-stu-id="26f7d-193">The output, before the error occurs, is as follows.</span></span>

```console
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
1 4 9 16 25
1 4 9 16 25 36 49 64 81 100
```

<span data-ttu-id="26f7d-194">藉由使用 [takeWhile](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#takeWhile)，您可以將述詞函式指定 (布耳函數) ，然後根據述詞為原始序列的這些元素所組成的另一個序列建立序列，但在述詞傳回 `true` 的第一個專案之前停止 `false` 。</span><span class="sxs-lookup"><span data-stu-id="26f7d-194">By using [Seq.takeWhile](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#takeWhile), you can specify a predicate function (a Boolean function) and create a sequence from another sequence made up of those elements of the original sequence for which the predicate is `true`, but stop before the first element for which the predicate returns `false`.</span></span> <span data-ttu-id="26f7d-195">[Seq. skip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#skip) 會傳回序列，以略過另一個序列的第一個專案，並傳回其餘專案的指定數目。</span><span class="sxs-lookup"><span data-stu-id="26f7d-195">[Seq.skip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#skip) returns a sequence that skips a specified number of the first elements of another sequence and returns the remaining elements.</span></span> <span data-ttu-id="26f7d-196">[SkipWhile](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#skipWhile) 會傳回一個序列，只要述詞傳回，就會略過另一個序列的第一個元素 `true` ，然後傳回其餘的元素，從述詞傳回的第一個專案開始 `false` 。</span><span class="sxs-lookup"><span data-stu-id="26f7d-196">[Seq.skipWhile](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#skipWhile) returns a sequence that skips the first elements of another sequence as long as the predicate returns `true`, and then returns the remaining elements, starting with the first element for which the predicate returns `false`.</span></span>

<span data-ttu-id="26f7d-197">下列程式碼範例說明、和之間的行為和 `Seq.takeWhile` 差異 `Seq.skip` `Seq.skipWhile` 。</span><span class="sxs-lookup"><span data-stu-id="26f7d-197">The following code example illustrates the behavior of and differences between `Seq.takeWhile`, `Seq.skip`, and `Seq.skipWhile`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet17.fs)]

<span data-ttu-id="26f7d-198">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="26f7d-198">The output is as follows.</span></span>

```console
1 4 9
36 49 64 81 100
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a><span data-ttu-id="26f7d-199">轉換序列</span><span class="sxs-lookup"><span data-stu-id="26f7d-199">Transforming Sequences</span></span>

<span data-ttu-id="26f7d-200">[Seq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#pairwise) 會建立新的序列，以將輸入序列的後續元素分組到元組中。</span><span class="sxs-lookup"><span data-stu-id="26f7d-200">[Seq.pairwise](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#pairwise) creates a new sequence in which successive elements of the input sequence are grouped into tuples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet18.fs)]

<span data-ttu-id="26f7d-201">[Seq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#windowed) 就像這樣，不同的是， `Seq.pairwise` 除了產生一系列的元組之外，它也會產生一連串陣列，其中包含從序列 (*視窗*) 的相鄰元素複本。</span><span class="sxs-lookup"><span data-stu-id="26f7d-201">[Seq.windowed](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#windowed) is like `Seq.pairwise`, except that instead of producing a sequence of tuples, it produces a sequence of arrays that contain copies of adjacent elements (a *window*) from the sequence.</span></span> <span data-ttu-id="26f7d-202">您可以指定每個陣列中所需的相鄰元素數目。</span><span class="sxs-lookup"><span data-stu-id="26f7d-202">You specify the number of adjacent elements you want in each array.</span></span>

<span data-ttu-id="26f7d-203">下列程式碼範例示範 `Seq.windowed` 的用法。</span><span class="sxs-lookup"><span data-stu-id="26f7d-203">The following code example demonstrates the use of `Seq.windowed`.</span></span> <span data-ttu-id="26f7d-204">在此情況下，視窗中的元素數目為3。</span><span class="sxs-lookup"><span data-stu-id="26f7d-204">In this case the number of elements in the window is 3.</span></span> <span data-ttu-id="26f7d-205">此範例會使用在 `printSeq` 上一個程式碼範例中定義的。</span><span class="sxs-lookup"><span data-stu-id="26f7d-205">The example uses `printSeq`, which is defined in the previous code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet180.fs)]

<span data-ttu-id="26f7d-206">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="26f7d-206">The output is as follows.</span></span>

<span data-ttu-id="26f7d-207">初始順序：</span><span class="sxs-lookup"><span data-stu-id="26f7d-207">Initial sequence:</span></span>

```console
1.0 1.5 2.0 1.5 1.0 1.5

Windows of length 3:
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|]

Moving average:
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a><span data-ttu-id="26f7d-208">具有多個序列的作業</span><span class="sxs-lookup"><span data-stu-id="26f7d-208">Operations with Multiple Sequences</span></span>

<span data-ttu-id="26f7d-209">[Seq.zip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#zip) 和 [Seq.zip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#zip3) 採用兩個或三個序列，並產生一系列的元組。</span><span class="sxs-lookup"><span data-stu-id="26f7d-209">[Seq.zip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#zip) and [Seq.zip3](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#zip3) take two or three sequences and produce a sequence of tuples.</span></span> <span data-ttu-id="26f7d-210">這些函式就像是適用于 [清單](lists.md)的對應函數。</span><span class="sxs-lookup"><span data-stu-id="26f7d-210">These functions are like the corresponding functions available for [lists](lists.md).</span></span> <span data-ttu-id="26f7d-211">沒有對應的功能可將一個序列分隔為兩個或多個序列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-211">There is no corresponding functionality to separate one sequence into two or more sequences.</span></span> <span data-ttu-id="26f7d-212">如果您需要順序的此功能，請將序列轉換為清單，並使用 [ [解壓縮](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip)]。</span><span class="sxs-lookup"><span data-stu-id="26f7d-212">If you need this functionality for a sequence, convert the sequence to a list and use [List.unzip](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html#unzip).</span></span>

## <a name="sorting-comparing-and-grouping"></a><span data-ttu-id="26f7d-213">排序、比較和分組</span><span class="sxs-lookup"><span data-stu-id="26f7d-213">Sorting, Comparing, and Grouping</span></span>

<span data-ttu-id="26f7d-214">清單支援的排序函式也適用于序列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-214">The sorting functions supported for lists also work with sequences.</span></span> <span data-ttu-id="26f7d-215">這包括 [Seq. sort](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sort) 和 [seq. sortBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sortBy)。</span><span class="sxs-lookup"><span data-stu-id="26f7d-215">This includes [Seq.sort](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sort) and [Seq.sortBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sortBy).</span></span> <span data-ttu-id="26f7d-216">這些函數會逐一查看整個序列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-216">These functions iterate through the whole sequence.</span></span>

<span data-ttu-id="26f7d-217">您可以使用 [seq.comparewith](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#compareWith) 函數來比較兩個序列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-217">You compare two sequences by using the [Seq.compareWith](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#compareWith) function.</span></span> <span data-ttu-id="26f7d-218">函式會輪流比較後續的專案，並在遇到第一個不相等的配對時停止。</span><span class="sxs-lookup"><span data-stu-id="26f7d-218">The function compares successive elements in turn, and stops when it encounters the first unequal pair.</span></span> <span data-ttu-id="26f7d-219">任何額外的元素都不會影響到比較。</span><span class="sxs-lookup"><span data-stu-id="26f7d-219">Any additional elements do not contribute to the comparison.</span></span>

<span data-ttu-id="26f7d-220">下列程式碼示範 `Seq.compareWith` 的用法。</span><span class="sxs-lookup"><span data-stu-id="26f7d-220">The following code shows the use of `Seq.compareWith`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet19.fs)]

<span data-ttu-id="26f7d-221">在先前的程式碼中，只會計算和檢查第一個元素，而結果為-1。</span><span class="sxs-lookup"><span data-stu-id="26f7d-221">In the previous code, only the first element is computed and examined, and the result is -1.</span></span>

<span data-ttu-id="26f7d-222">[Seq.countby](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#countBy) 所採用的函式會為每個專案產生一個稱為索引 *鍵* 的值。</span><span class="sxs-lookup"><span data-stu-id="26f7d-222">[Seq.countBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#countBy) takes a function that generates a value called a *key* for each element.</span></span> <span data-ttu-id="26f7d-223">藉由在每個專案上呼叫此函式來產生每個專案的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="26f7d-223">A key is generated for each element by calling this function on each element.</span></span> <span data-ttu-id="26f7d-224">`Seq.countBy` 然後傳回包含索引鍵值的序列，以及產生每個索引鍵值的元素數目計數。</span><span class="sxs-lookup"><span data-stu-id="26f7d-224">`Seq.countBy` then returns a sequence that contains the key values, and a count of the number of elements that generated each value of the key.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet201.fs)]

<span data-ttu-id="26f7d-225">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="26f7d-225">The output is as follows.</span></span>

```console
(1, 34) (2, 33) (0, 33)
```

<span data-ttu-id="26f7d-226">先前的輸出顯示，產生金鑰1、33值產生金鑰2的原始序列有34個元素，以及產生金鑰0的33值。</span><span class="sxs-lookup"><span data-stu-id="26f7d-226">The previous output shows that there were 34 elements of the original sequence that produced the key 1, 33 values that produced the key 2, and 33 values that produced the key 0.</span></span>

<span data-ttu-id="26f7d-227">您可以藉由呼叫 [Seq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#groupBy)，來群組序列的元素。</span><span class="sxs-lookup"><span data-stu-id="26f7d-227">You can group elements of a sequence by calling [Seq.groupBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#groupBy).</span></span> <span data-ttu-id="26f7d-228">`Seq.groupBy` 接受從專案產生索引鍵的序列和函式。</span><span class="sxs-lookup"><span data-stu-id="26f7d-228">`Seq.groupBy` takes a sequence and a function that generates a key from an element.</span></span> <span data-ttu-id="26f7d-229">函數會在序列的每個專案上執行。</span><span class="sxs-lookup"><span data-stu-id="26f7d-229">The function is executed on each element of the sequence.</span></span> <span data-ttu-id="26f7d-230">`Seq.groupBy` 傳回一系列的元組，其中每個元組的第一個元素是索引鍵，而第二個專案是產生該索引鍵的元素序列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-230">`Seq.groupBy` returns a sequence of tuples, where the first element of each tuple is the key and the second is a sequence of elements that produce that key.</span></span>

<span data-ttu-id="26f7d-231">下列程式碼範例示範 `Seq.groupBy` 如何使用將數位序列從1到100分割成具有相異索引鍵值0、1和2的三個群組。</span><span class="sxs-lookup"><span data-stu-id="26f7d-231">The following code example shows the use of `Seq.groupBy` to partition the sequence of numbers from 1 to 100 into three groups that have the distinct key values 0, 1, and 2.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet202.fs)]

<span data-ttu-id="26f7d-232">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="26f7d-232">The output is as follows.</span></span>

```console
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

<span data-ttu-id="26f7d-233">您可以藉由呼叫 [Seq. distinct](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#distinct)來建立可消除重複專案的序列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-233">You can create a sequence that eliminates duplicate elements by calling [Seq.distinct](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#distinct).</span></span> <span data-ttu-id="26f7d-234">或者，您可以使用 [Seq. seq.distinctby](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#distinctBy)，它會接受在每個專案上呼叫按鍵產生函數。</span><span class="sxs-lookup"><span data-stu-id="26f7d-234">Or you can use [Seq.distinctBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#distinctBy), which takes a key-generating function to be called on each element.</span></span> <span data-ttu-id="26f7d-235">產生的序列包含原始序列中具有唯一索引鍵的元素;稍後會捨棄產生重複索引鍵的元素給先前的元素。</span><span class="sxs-lookup"><span data-stu-id="26f7d-235">The resulting sequence contains elements of the original sequence that have unique keys; later elements that produce a duplicate key to an earlier element are discarded.</span></span>

<span data-ttu-id="26f7d-236">下列程式碼範例說明如何使用 `Seq.distinct` 。</span><span class="sxs-lookup"><span data-stu-id="26f7d-236">The following code example illustrates the use of `Seq.distinct`.</span></span> <span data-ttu-id="26f7d-237">`Seq.distinct` 是藉由產生代表二進位數的序列來示範，然後顯示唯一的相異元素為0和1。</span><span class="sxs-lookup"><span data-stu-id="26f7d-237">`Seq.distinct` is demonstrated by generating sequences that represent binary numbers, and then showing that the only distinct elements are 0 and 1.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet22.fs)]

<span data-ttu-id="26f7d-238">下列程式碼示範如何 `Seq.distinctBy` 從包含負數和正數的序列開始，並使用絕對值函式作為索引鍵產生函數。</span><span class="sxs-lookup"><span data-stu-id="26f7d-238">The following code demonstrates `Seq.distinctBy` by starting with a sequence that contains negative and positive numbers and using the absolute value function as the key-generating function.</span></span> <span data-ttu-id="26f7d-239">產生的序列遺漏了對應到序列中之負數的所有正數，因為負數會出現在序列中，因此會被選取，而不是具有相同絕對值或索引鍵的正數。</span><span class="sxs-lookup"><span data-stu-id="26f7d-239">The resulting sequence is missing all the positive numbers that correspond to the negative numbers in the sequence, because the negative numbers appear earlier in the sequence and therefore are selected instead of the positive numbers that have the same absolute value, or key.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet23.fs)]

## <a name="readonly-and-cached-sequences"></a><span data-ttu-id="26f7d-240">Readonly 和快取順序</span><span class="sxs-lookup"><span data-stu-id="26f7d-240">Readonly and Cached Sequences</span></span>

<span data-ttu-id="26f7d-241">[Seq. readonly](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#readonly) 會建立序列的唯讀複本。</span><span class="sxs-lookup"><span data-stu-id="26f7d-241">[Seq.readonly](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#readonly) creates a read-only copy of a sequence.</span></span> <span data-ttu-id="26f7d-242">`Seq.readonly` 當您有讀寫集合（例如陣列），而且您不想要修改原創組合時，會很有用。</span><span class="sxs-lookup"><span data-stu-id="26f7d-242">`Seq.readonly` is useful when you have a read-write collection, such as an array, and you do not want to modify the original collection.</span></span> <span data-ttu-id="26f7d-243">此函數可以用來保留資料封裝。</span><span class="sxs-lookup"><span data-stu-id="26f7d-243">This function can be used to preserve data encapsulation.</span></span> <span data-ttu-id="26f7d-244">在下列程式碼範例中，會建立包含陣列的型別。</span><span class="sxs-lookup"><span data-stu-id="26f7d-244">In the following code example, a type that contains an array is created.</span></span> <span data-ttu-id="26f7d-245">屬性會公開陣列，而不是傳回陣列，而是使用來傳回從陣列建立的序列 `Seq.readonly` 。</span><span class="sxs-lookup"><span data-stu-id="26f7d-245">A property exposes the array, but instead of returning an array, it returns a sequence that is created from the array by using `Seq.readonly`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet24.fs)]

<span data-ttu-id="26f7d-246">[Seq. cache](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#cache) 會建立序列的儲存版本。</span><span class="sxs-lookup"><span data-stu-id="26f7d-246">[Seq.cache](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#cache) creates a stored version of a sequence.</span></span> <span data-ttu-id="26f7d-247">使用 `Seq.cache` 可避免重新評估序列，或當您有多個使用序列的執行緒時，但您必須確定每個專案只會在一次時採取動作。</span><span class="sxs-lookup"><span data-stu-id="26f7d-247">Use `Seq.cache` to avoid reevaluation of a sequence, or when you have multiple threads that use a sequence, but you must make sure that each element is acted upon only one time.</span></span> <span data-ttu-id="26f7d-248">當您有多個執行緒正在使用的序列時，您可以有一個執行緒來列舉和計算原始序列的值，而其餘的執行緒可以使用快取的序列。</span><span class="sxs-lookup"><span data-stu-id="26f7d-248">When you have a sequence that is being used by multiple threads, you can have one thread that enumerates and computes the values for the original sequence, and remaining threads can use the cached sequence.</span></span>

## <a name="performing-computations-on-sequences"></a><span data-ttu-id="26f7d-249">在序列上執行計算</span><span class="sxs-lookup"><span data-stu-id="26f7d-249">Performing Computations on Sequences</span></span>

<span data-ttu-id="26f7d-250">簡單的算數運算和清單類似，例如 [seq. average](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#average)、 [seq. sum](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sum)、 [averageBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#averageBy)、 [seq. sumBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sumBy)等等。</span><span class="sxs-lookup"><span data-stu-id="26f7d-250">Simple arithmetic operations are like those of lists, such as [Seq.average](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#average), [Seq.sum](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sum), [Seq.averageBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#averageBy), [Seq.sumBy](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#sumBy), and so on.</span></span>

<span data-ttu-id="26f7d-251">[Seq](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#fold)、 [seq. 減低](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#reduce)和 [seq. scan](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#scan) 就像是可用於清單的對應函式。</span><span class="sxs-lookup"><span data-stu-id="26f7d-251">[Seq.fold](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#fold), [Seq.reduce](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#reduce), and [Seq.scan](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-seqmodule.html#scan) are like the corresponding functions that are available for lists.</span></span> <span data-ttu-id="26f7d-252">序列支援這些函式的完整變化子集，這些功能會列出支援。</span><span class="sxs-lookup"><span data-stu-id="26f7d-252">Sequences support a subset of the full variations of these functions that lists support.</span></span> <span data-ttu-id="26f7d-253">如需詳細資訊和範例，請參閱 [清單](lists.md)。</span><span class="sxs-lookup"><span data-stu-id="26f7d-253">For more information and examples, see [Lists](lists.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="26f7d-254">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26f7d-254">See also</span></span>

- [<span data-ttu-id="26f7d-255">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="26f7d-255">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="26f7d-256">F# 類型</span><span class="sxs-lookup"><span data-stu-id="26f7d-256">F# Types</span></span>](fsharp-types.md)
