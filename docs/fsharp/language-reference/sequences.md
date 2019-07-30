---
title: 序列
description: 當您有大量F# 、已排序的資料集合, 但不一定會使用所有元素時, 瞭解如何使用序列。
ms.date: 02/19/2019
ms.openlocfilehash: a57142c5d07455cff02b0b691ebccb9cb9f347fd
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627174"
---
# <a name="sequences"></a><span data-ttu-id="a698f-103">序列</span><span class="sxs-lookup"><span data-stu-id="a698f-103">Sequences</span></span>

> [!NOTE]
> <span data-ttu-id="a698f-104">本文中的 API 參考連結將帶您前往 MSDN。</span><span class="sxs-lookup"><span data-stu-id="a698f-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="a698f-105">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="a698f-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="a698f-106">「*序列*」是一種專案的邏輯數列, 全都屬於一個型別。</span><span class="sxs-lookup"><span data-stu-id="a698f-106">A *sequence* is a logical series of elements all of one type.</span></span> <span data-ttu-id="a698f-107">當您有大量、已排序的資料集合, 但不一定會使用所有的元素時, 序列會特別有用。</span><span class="sxs-lookup"><span data-stu-id="a698f-107">Sequences are particularly useful when you have a large, ordered collection of data but do not necessarily expect to use all of the elements.</span></span> <span data-ttu-id="a698f-108">個別序列元素只會視需要計算, 因此在不使用所有元素的情況下, 序列可以提供比清單更好的效能。</span><span class="sxs-lookup"><span data-stu-id="a698f-108">Individual sequence elements are computed only as required, so a sequence can provide better performance than a list in situations in which not all the elements are used.</span></span> <span data-ttu-id="a698f-109">序列是以`seq<'T>`型別表示, 這是的`System.Collections.Generic.IEnumerable`別名。</span><span class="sxs-lookup"><span data-stu-id="a698f-109">Sequences are represented by the `seq<'T>` type, which is an alias for `System.Collections.Generic.IEnumerable`.</span></span> <span data-ttu-id="a698f-110">因此, 任何執行的`System.IEnumerable` .NET Framework 類型都可以當做序列使用。</span><span class="sxs-lookup"><span data-stu-id="a698f-110">Therefore, any .NET Framework type that implements `System.IEnumerable` can be used as a sequence.</span></span> <span data-ttu-id="a698f-111">[Seq 模組](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)可支援涉及序列的操作。</span><span class="sxs-lookup"><span data-stu-id="a698f-111">The [Seq module](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) provides support for manipulations involving sequences.</span></span>

## <a name="sequence-expressions"></a><span data-ttu-id="a698f-112">順序運算式</span><span class="sxs-lookup"><span data-stu-id="a698f-112">Sequence Expressions</span></span>

<span data-ttu-id="a698f-113">*序列運算式*是評估為序列的運算式。</span><span class="sxs-lookup"><span data-stu-id="a698f-113">A *sequence expression* is an expression that evaluates to a sequence.</span></span> <span data-ttu-id="a698f-114">順序運算式可以採用數種形式。</span><span class="sxs-lookup"><span data-stu-id="a698f-114">Sequence expressions can take a number of forms.</span></span> <span data-ttu-id="a698f-115">最簡單的形式就是指定範圍。</span><span class="sxs-lookup"><span data-stu-id="a698f-115">The simplest form specifies a range.</span></span> <span data-ttu-id="a698f-116">例如, `seq { 1 . 5 }`會建立包含五個元素的序列, 包括端點1和5。</span><span class="sxs-lookup"><span data-stu-id="a698f-116">For example, `seq { 1 .. 5 }` creates a sequence that contains five elements, including the endpoints 1 and 5.</span></span> <span data-ttu-id="a698f-117">您也可以指定兩個雙句點之間的遞增 (或遞減)。</span><span class="sxs-lookup"><span data-stu-id="a698f-117">You can also specify an increment (or decrement) between two double periods.</span></span> <span data-ttu-id="a698f-118">例如, 下列程式碼會建立10的倍數序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-118">For example, the following code creates the sequence of multiples of 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

<span data-ttu-id="a698f-119">序列運算式是由產生序列F#值的運算式所組成。</span><span class="sxs-lookup"><span data-stu-id="a698f-119">Sequence expressions are made up of F# expressions that produce values of the sequence.</span></span> <span data-ttu-id="a698f-120">它們可以使用`yield`關鍵字來產生會成為序列一部分的值。</span><span class="sxs-lookup"><span data-stu-id="a698f-120">They can use the `yield` keyword to produce values that become part of the sequence.</span></span>

<span data-ttu-id="a698f-121">以下是範例。</span><span class="sxs-lookup"><span data-stu-id="a698f-121">Following is an example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

<span data-ttu-id="a698f-122">您可以使用`->`運算子`yield`, 而不是, 在此`do`情況下, 您可以省略關鍵字, 如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a698f-122">You can use the `->` operator instead of `yield`, in which case you can omit the `do` keyword, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

<span data-ttu-id="a698f-123">下列程式碼會在代表方格的陣列中, 產生座標配對的清單, 以及一個索引。</span><span class="sxs-lookup"><span data-stu-id="a698f-123">The following code generates a list of coordinate pairs along with an index into an array that represents the grid.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

<span data-ttu-id="a698f-124">序列中使用的運算式是篩選準則。`if`</span><span class="sxs-lookup"><span data-stu-id="a698f-124">An `if` expression used in a sequence is a filter.</span></span> <span data-ttu-id="a698f-125">例如, 若只要產生一個質數的序列, 假設您有`isprime`類型`int -> bool`的函式, 請依照下列方式來結構化序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-125">For example, to generate a sequence of only prime numbers, assuming that you have a function `isprime` of type `int -> bool`, construct the sequence as follows.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

<span data-ttu-id="a698f-126">當您在`yield`反復`->`專案中使用或時, 每個反復專案都應該產生序列的單一元素。</span><span class="sxs-lookup"><span data-stu-id="a698f-126">When you use `yield` or `->` in an iteration, each iteration is expected to generate a single element of the sequence.</span></span> <span data-ttu-id="a698f-127">如果每個反復專案都會產生一系列的`yield!`專案, 請使用。</span><span class="sxs-lookup"><span data-stu-id="a698f-127">If each iteration produces a sequence of elements, use `yield!`.</span></span> <span data-ttu-id="a698f-128">在此情況下, 會串連每個反復專案上產生的元素, 以產生最終的序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-128">In that case, the elements generated on each iteration are concatenated to produce the final sequence.</span></span>

<span data-ttu-id="a698f-129">您可以在序列運算式中結合多個運算式。</span><span class="sxs-lookup"><span data-stu-id="a698f-129">You can combine multiple expressions together in a sequence expression.</span></span> <span data-ttu-id="a698f-130">每個運算式所產生的元素會串連在一起。</span><span class="sxs-lookup"><span data-stu-id="a698f-130">The elements generated by each expression are concatenated together.</span></span> <span data-ttu-id="a698f-131">如需範例, 請參閱本主題的「範例」一節。</span><span class="sxs-lookup"><span data-stu-id="a698f-131">For an example, see the "Examples" section of this topic.</span></span>

## <a name="examples"></a><span data-ttu-id="a698f-132">範例</span><span class="sxs-lookup"><span data-stu-id="a698f-132">Examples</span></span>

<span data-ttu-id="a698f-133">第一個範例會使用包含反復專案、篩選和 yield 的序列運算式來產生陣列。</span><span class="sxs-lookup"><span data-stu-id="a698f-133">The first example uses a sequence expression that contains an iteration, a filter, and a yield to generate an array.</span></span> <span data-ttu-id="a698f-134">此程式碼會將1到100之間的質數序列列印到主控台。</span><span class="sxs-lookup"><span data-stu-id="a698f-134">This code prints a sequence of prime numbers between 1 and 100 to the console.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

<span data-ttu-id="a698f-135">下列程式碼會`yield`使用來建立由三個元素的元組組成的乘法資料表, 每個專案都包含兩個因素和產品。</span><span class="sxs-lookup"><span data-stu-id="a698f-135">The following code uses `yield` to create a multiplication table that consists of tuples of three elements, each consisting of two factors and the product.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

<span data-ttu-id="a698f-136">下列範例示範`yield!`如何使用將個別序列結合成單一最終序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-136">The following example demonstrates the use of `yield!` to combine individual sequences into a single final sequence.</span></span> <span data-ttu-id="a698f-137">在此情況下, 二進位樹狀目錄中每個子樹的序列都會在遞迴函式中串連, 以產生最終的序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-137">In this case, the sequences for each subtree in a binary tree are concatenated in a recursive function to produce the final sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]

## <a name="using-sequences"></a><span data-ttu-id="a698f-138">使用順序</span><span class="sxs-lookup"><span data-stu-id="a698f-138">Using Sequences</span></span>

<span data-ttu-id="a698f-139">序列支援許多與[清單](lists.md)相同的功能。</span><span class="sxs-lookup"><span data-stu-id="a698f-139">Sequences support many of the same functions as [lists](lists.md).</span></span> <span data-ttu-id="a698f-140">序列也支援使用索引鍵產生函式的分組和計算之類的作業。</span><span class="sxs-lookup"><span data-stu-id="a698f-140">Sequences also support operations such as grouping and counting by using key-generating functions.</span></span> <span data-ttu-id="a698f-141">序列也支援更多樣化的函式來解壓縮個子序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-141">Sequences also support more diverse functions for extracting subsequences.</span></span>

<span data-ttu-id="a698f-142">許多資料類型 (例如清單、陣列、集合和對應) 都是隱含的序列, 因為它們是可列舉的集合。</span><span class="sxs-lookup"><span data-stu-id="a698f-142">Many data types, such as lists, arrays, sets, and maps are implicitly sequences because they are enumerable collections.</span></span> <span data-ttu-id="a698f-143">將序列當做引數使用的函式, 除了任何可執行檔F# .NET Framework 資料類型`System.Collections.Generic.IEnumerable<'T>`之外, 也適用于任何常見的資料類型。</span><span class="sxs-lookup"><span data-stu-id="a698f-143">A function that takes a sequence as an argument works with any of the common F# data types, in addition to any .NET Framework data type that implements `System.Collections.Generic.IEnumerable<'T>`.</span></span> <span data-ttu-id="a698f-144">相較于接受清單做為引數的函式, 它只能接受清單。</span><span class="sxs-lookup"><span data-stu-id="a698f-144">Contrast this to a function that takes a list as an argument, which can only take lists.</span></span> <span data-ttu-id="a698f-145">類型`seq<'T>`是的`IEnumerable<'T>`類型縮寫。</span><span class="sxs-lookup"><span data-stu-id="a698f-145">The type `seq<'T>` is a type abbreviation for `IEnumerable<'T>`.</span></span> <span data-ttu-id="a698f-146">這表示任何實作為泛型`System.Collections.Generic.IEnumerable<'T>`的型別 (其中包括中F#的陣列、清單、集合和對應, 以及大部分 .NET Framework 的集合型別) `seq`都與類型相容, 而且可以在預期序列的任何位置使用.</span><span class="sxs-lookup"><span data-stu-id="a698f-146">This means that any type that implements the generic `System.Collections.Generic.IEnumerable<'T>`, which includes arrays, lists, sets, and maps in F#, and also most .NET Framework collection types, is compatible with the `seq` type and can be used wherever a sequence is expected.</span></span>

## <a name="module-functions"></a><span data-ttu-id="a698f-147">模組函式</span><span class="sxs-lookup"><span data-stu-id="a698f-147">Module Functions</span></span>

<span data-ttu-id="a698f-148">[Fsharp.core 命名空間](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f)中的[Seq 模組](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)包含處理序列的函式。</span><span class="sxs-lookup"><span data-stu-id="a698f-148">The [Seq module](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) in the [Microsoft.FSharp.Collections namespace](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f) contains functions for working with sequences.</span></span> <span data-ttu-id="a698f-149">這些函式也會使用清單、陣列、對應和集合, 因為所有這些類型都是可列舉的, 因此可以視為序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-149">These functions work with lists, arrays, maps, and sets as well, because all of those types are enumerable, and therefore can be treated as sequences.</span></span>

## <a name="creating-sequences"></a><span data-ttu-id="a698f-150">建立序列</span><span class="sxs-lookup"><span data-stu-id="a698f-150">Creating Sequences</span></span>

<span data-ttu-id="a698f-151">如先前所述, 或使用特定函數, 您可以使用順序運算式來建立序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-151">You can create sequences by using sequence expressions, as described previously, or by using certain functions.</span></span>

<span data-ttu-id="a698f-152">您可以使用 [ [seq](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59)] 建立空的序列, 或使用 [ [seq](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7)] 建立只有一個指定元素的序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-152">You can create an empty sequence by using [Seq.empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59), or you can create a sequence of just one specified element by using [Seq.singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet9.fs)]

<span data-ttu-id="a698f-153">您可以使用 [Seq], 建立使用您所提供的函式來建立元素的序列[。](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576)</span><span class="sxs-lookup"><span data-stu-id="a698f-153">You can use [Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576) to create a sequence for which the elements are created by using a function that you provide.</span></span> <span data-ttu-id="a698f-154">您也可以為序列提供大小。</span><span class="sxs-lookup"><span data-stu-id="a698f-154">You also provide a size for the sequence.</span></span> <span data-ttu-id="a698f-155">此函式就像[List. init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83)一樣, 只是在您逐一查看序列之前, 不會建立元素。</span><span class="sxs-lookup"><span data-stu-id="a698f-155">This function is just like [List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83), except that the elements are not created until you iterate through the sequence.</span></span> <span data-ttu-id="a698f-156">下列程式碼說明的用法`Seq.init`。</span><span class="sxs-lookup"><span data-stu-id="a698f-156">The following code illustrates the use of `Seq.init`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet10.fs)]

<span data-ttu-id="a698f-157">輸出為</span><span class="sxs-lookup"><span data-stu-id="a698f-157">The output is</span></span>

```
0 10 20 30 40
```

<span data-ttu-id="a698f-158">藉由使用[list.ofarray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99)和[array.oflist&#60; &#62;函數](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d), 您可以從陣列和清單建立序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-158">By using [Seq.ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99) and [Seq.ofList&#60;'T&#62; Function](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d), you can create sequences from arrays and lists.</span></span> <span data-ttu-id="a698f-159">不過, 您也可以使用 cast 運算子, 將陣列和清單轉換成序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-159">However, you can also convert arrays and lists to sequences by using a cast operator.</span></span> <span data-ttu-id="a698f-160">下列程式碼會顯示這兩種技術。</span><span class="sxs-lookup"><span data-stu-id="a698f-160">Both techniques are shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet11.fs)]

<span data-ttu-id="a698f-161">藉由使用[Seq](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334), 您可以從弱型別集合 (例如中`System.Collections`定義的型別) 建立序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-161">By using [Seq.cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334), you can create a sequence from a weakly typed collection, such as those defined in `System.Collections`.</span></span> <span data-ttu-id="a698f-162">這類弱式類型集合具有元素`System.Object`類型, 而且是使用非泛型`System.Collections.Generic.IEnumerable&#96;1`類型來列舉。</span><span class="sxs-lookup"><span data-stu-id="a698f-162">Such weakly typed collections have the element type `System.Object` and are enumerated by using the non-generic `System.Collections.Generic.IEnumerable&#96;1` type.</span></span> <span data-ttu-id="a698f-163">下列程式碼說明`Seq.cast`如何使用將`System.Collections.ArrayList`轉換成序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-163">The following code illustrates the use of `Seq.cast` to convert an `System.Collections.ArrayList` into a sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet12.fs)]

<span data-ttu-id="a698f-164">您可以使用[seq.initinfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef)函數來定義無限序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-164">You can define infinite sequences by using the [Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef) function.</span></span> <span data-ttu-id="a698f-165">針對這類順序, 您會提供函式, 從專案的索引產生每個元素。</span><span class="sxs-lookup"><span data-stu-id="a698f-165">For such a sequence, you provide a function that generates each element from the index of the element.</span></span> <span data-ttu-id="a698f-166">無限序列是可能的, 因為延遲評估;專案會視需要藉由呼叫您指定的函式來建立。</span><span class="sxs-lookup"><span data-stu-id="a698f-166">Infinite sequences are possible because of lazy evaluation; elements are created as needed by calling the function that you specify.</span></span> <span data-ttu-id="a698f-167">下列程式碼範例會產生無限的浮點數序列, 在此案例中為連續整數的一系列 reciprocals。</span><span class="sxs-lookup"><span data-stu-id="a698f-167">The following code example produces an infinite sequence of floating point numbers, in this case the alternating series of reciprocals of squares of successive integers.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet13.fs)]

<span data-ttu-id="a698f-168">[[展開](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21)] 會從接受狀態的計算函式產生序列, 並加以轉換, 以產生序列中的每個後續元素。</span><span class="sxs-lookup"><span data-stu-id="a698f-168">[Seq.unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21) generates a sequence from a computation function that takes a state and transforms it to produce each subsequent element in the sequence.</span></span> <span data-ttu-id="a698f-169">此狀態只是用來計算每個元素的值, 而且可以隨著每個元素的計算而變更。</span><span class="sxs-lookup"><span data-stu-id="a698f-169">The state is just a value that is used to compute each element, and can change as each element is computed.</span></span> <span data-ttu-id="a698f-170">的第二個`Seq.unfold`引數是用來啟動序列的起始值。</span><span class="sxs-lookup"><span data-stu-id="a698f-170">The second argument to `Seq.unfold` is the initial value that is used to start the sequence.</span></span> <span data-ttu-id="a698f-171">`Seq.unfold`使用狀態的選項類型, 可讓您藉由`None`傳回值來終止序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-171">`Seq.unfold` uses an option type for the state, which enables you to terminate the sequence by returning the `None` value.</span></span> <span data-ttu-id="a698f-172">下列`seq1` 程式碼`fib`顯示兩個由作業所產生之序列和的範例。`unfold`</span><span class="sxs-lookup"><span data-stu-id="a698f-172">The following code shows two examples of sequences, `seq1` and `fib`, that are generated by an `unfold` operation.</span></span> <span data-ttu-id="a698f-173">第一`seq1`種是一個簡單的序列, 最高可達20個數字。</span><span class="sxs-lookup"><span data-stu-id="a698f-173">The first, `seq1`, is just a simple sequence with numbers up to 20.</span></span> <span data-ttu-id="a698f-174">第二個`fib`會使用`unfold`來計算斐波和數列序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-174">The second, `fib`, uses `unfold` to compute the Fibonacci sequence.</span></span> <span data-ttu-id="a698f-175">由於每個數列序列中的元素都是前兩個斐報數位的總和, 因此 state 值是由序列中前兩個數字組成的元組。</span><span class="sxs-lookup"><span data-stu-id="a698f-175">Because each element in the Fibonacci sequence is the sum of the previous two Fibonacci numbers, the state value is a tuple that consists of the previous two numbers in the sequence.</span></span> <span data-ttu-id="a698f-176">初始值是`(1,1)`, 序列中的前兩個數字。</span><span class="sxs-lookup"><span data-stu-id="a698f-176">The initial value is `(1,1)`, the first two numbers in the sequence.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet14.fs)]

<span data-ttu-id="a698f-177">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="a698f-177">The output is as follows:</span></span>

```
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

<span data-ttu-id="a698f-178">下列程式碼範例會使用此處所述的許多順序模組函數來產生和計算無限序列的值。</span><span class="sxs-lookup"><span data-stu-id="a698f-178">The following code is an example that uses many of the sequence module functions described here to generate and compute the values of infinite sequences.</span></span> <span data-ttu-id="a698f-179">程式碼可能需要幾分鐘的時間才能執行。</span><span class="sxs-lookup"><span data-stu-id="a698f-179">The code might take a few minutes to run.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet15.fs)]

## <a name="searching-and-finding-elements"></a><span data-ttu-id="a698f-180">搜尋和尋找元素</span><span class="sxs-lookup"><span data-stu-id="a698f-180">Searching and Finding Elements</span></span>

<span data-ttu-id="a698f-181">序列支援清單所提供的功能:[Seq. exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1)、 [seq. list.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565)、 [seq. find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8)、 [seq. findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3)、 [seq. pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d)、 [tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47)和[seq. array.tryfindindex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a)。</span><span class="sxs-lookup"><span data-stu-id="a698f-181">Sequences support functionality available with lists: [Seq.exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1), [Seq.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565), [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8), [Seq.findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3), [Seq.pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d), [Seq.tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47), and [Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a).</span></span> <span data-ttu-id="a698f-182">這些可用於序列的函式版本, 只會將序列評估為要搜尋的專案。</span><span class="sxs-lookup"><span data-stu-id="a698f-182">The versions of these functions that are available for sequences evaluate the sequence only up to the element that is being searched for.</span></span> <span data-ttu-id="a698f-183">如需範例, 請參閱[清單](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)。</span><span class="sxs-lookup"><span data-stu-id="a698f-183">For examples, see [Lists](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).</span></span>

## <a name="obtaining-subsequences"></a><span data-ttu-id="a698f-184">取得個子序列</span><span class="sxs-lookup"><span data-stu-id="a698f-184">Obtaining Subsequences</span></span>

<span data-ttu-id="a698f-185">[Seq. filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770)和[Seq。選擇](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395)與可用於清單的對應函式相似, 不同之處在于在評估序列元素之前, 不會進行篩選和選擇。</span><span class="sxs-lookup"><span data-stu-id="a698f-185">[Seq.filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770) and [Seq.choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395) are like the corresponding functions that are available for lists, except that the filtering and choosing does not occur until the sequence elements are evaluated.</span></span>

<span data-ttu-id="a698f-186">[[截斷](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244)] 會從另一個序列建立順序, 但會將序列限制為指定數目的專案。</span><span class="sxs-lookup"><span data-stu-id="a698f-186">[Seq.truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244) creates a sequence from another sequence, but limits the sequence to a specified number of elements.</span></span> <span data-ttu-id="a698f-187">[Seq. take 會](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596)建立新的序列, 其中只包含序列開頭的指定元素數目。</span><span class="sxs-lookup"><span data-stu-id="a698f-187">[Seq.take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596) creates a new sequence that contains only a specified number of elements from the start of a sequence.</span></span> <span data-ttu-id="a698f-188">如果序列中的元素數目比您指定要採用的專案少`Seq.take` , `System.InvalidOperationException`會擲回。</span><span class="sxs-lookup"><span data-stu-id="a698f-188">If there are fewer elements in the sequence than you specify to take, `Seq.take` throws a `System.InvalidOperationException`.</span></span> <span data-ttu-id="a698f-189">和`Seq.take` `Seq.truncate`之間的差異在於, 如果元素數目少於您指定的數目, 就不會產生錯誤。 `Seq.truncate`</span><span class="sxs-lookup"><span data-stu-id="a698f-189">The difference between `Seq.take` and `Seq.truncate` is that `Seq.truncate` does not produce an error if the number of elements is fewer than the number you specify.</span></span>

<span data-ttu-id="a698f-190">下列程式碼顯示和`Seq.truncate` `Seq.take`之間的行為差異。</span><span class="sxs-lookup"><span data-stu-id="a698f-190">The following code shows the behavior of and differences between `Seq.truncate` and `Seq.take`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet16.fs)]

<span data-ttu-id="a698f-191">發生錯誤之前的輸出會如下所示。</span><span class="sxs-lookup"><span data-stu-id="a698f-191">The output, before the error occurs, is as follows.</span></span>

```
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100 
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100
```

<span data-ttu-id="a698f-192">藉由使用[takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92), 您可以指定述詞函式 (布林函式), 並根據原始序列之專案的其他序列來建立順序, 但此順序是`true`由該專案組成, 但在第一個元素之前停止述詞傳回的。 `false`</span><span class="sxs-lookup"><span data-stu-id="a698f-192">By using [Seq.takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92), you can specify a predicate function (a Boolean function) and create a sequence from another sequence made up of those elements of the original sequence for which the predicate is `true`, but stop before the first element for which the predicate returns `false`.</span></span> <span data-ttu-id="a698f-193">[Seq. skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1)傳回的序列會略過另一個序列中第一個專案的指定數目, 並傳回剩餘的元素。</span><span class="sxs-lookup"><span data-stu-id="a698f-193">[Seq.skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1) returns a sequence that skips a specified number of the first elements of another sequence and returns the remaining elements.</span></span> <span data-ttu-id="a698f-194">[SkipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16)傳回的序列會略過另一個序列的第一個專案`true`(只要述詞傳回), 然後傳回其餘的專案, 從該述詞傳回的第一個元素開始。 `false`.</span><span class="sxs-lookup"><span data-stu-id="a698f-194">[Seq.skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16) returns a sequence that skips the first elements of another sequence as long as the predicate returns `true`, and then returns the remaining elements, starting with the first element for which the predicate returns `false`.</span></span>

<span data-ttu-id="a698f-195">下列程式碼範例說明、 `Seq.takeWhile` `Seq.skip` `Seq.skipWhile`和之間的行為和差異。</span><span class="sxs-lookup"><span data-stu-id="a698f-195">The following code example illustrates the behavior of and differences between `Seq.takeWhile`, `Seq.skip`, and `Seq.skipWhile`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet17.fs)]

<span data-ttu-id="a698f-196">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="a698f-196">The output is as follows.</span></span>

```
1 4 9 
36 49 64 81 100 
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a><span data-ttu-id="a698f-197">轉換序列</span><span class="sxs-lookup"><span data-stu-id="a698f-197">Transforming Sequences</span></span>

<span data-ttu-id="a698f-198">[Seq](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1)會建立新的序列, 其中輸入序列的後續元素會分組為元組。</span><span class="sxs-lookup"><span data-stu-id="a698f-198">[Seq.pairwise](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1) creates a new sequence in which successive elements of the input sequence are grouped into tuples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet18.fs)]

<span data-ttu-id="a698f-199">[Seq. 視窗](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744)化類似`Seq.pairwise`, 不同的是, 它不會產生一系列的元組, 而是會產生一系列陣列, 其中包含序列中相鄰元素 (*視窗*) 的複本。</span><span class="sxs-lookup"><span data-stu-id="a698f-199">[Seq.windowed](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744) is like `Seq.pairwise`, except that instead of producing a sequence of tuples, it produces a sequence of arrays that contain copies of adjacent elements (a *window*) from the sequence.</span></span> <span data-ttu-id="a698f-200">您可以在每個陣列中指定您想要的相鄰元素數目。</span><span class="sxs-lookup"><span data-stu-id="a698f-200">You specify the number of adjacent elements you want in each array.</span></span>

<span data-ttu-id="a698f-201">下列程式碼範例示範 `Seq.windowed` 的用法。</span><span class="sxs-lookup"><span data-stu-id="a698f-201">The following code example demonstrates the use of `Seq.windowed`.</span></span> <span data-ttu-id="a698f-202">在此情況下, 視窗中的元素數目是3。</span><span class="sxs-lookup"><span data-stu-id="a698f-202">In this case the number of elements in the window is 3.</span></span> <span data-ttu-id="a698f-203">此範例會`printSeq`使用, 這是在先前的程式碼範例中定義的。</span><span class="sxs-lookup"><span data-stu-id="a698f-203">The example uses `printSeq`, which is defined in the previous code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet180.fs)]

<span data-ttu-id="a698f-204">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="a698f-204">The output is as follows.</span></span>

<span data-ttu-id="a698f-205">初始順序:</span><span class="sxs-lookup"><span data-stu-id="a698f-205">Initial sequence:</span></span>

```
1.0 1.5 2.0 1.5 1.0 1.5 

Windows of length 3: 
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|] 

Moving average: 
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a><span data-ttu-id="a698f-206">具有多個序列的作業</span><span class="sxs-lookup"><span data-stu-id="a698f-206">Operations with Multiple Sequences</span></span>

<span data-ttu-id="a698f-207">[Seq](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4)和[list.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16)接受兩個或三個序列, 並產生一系列的元組。</span><span class="sxs-lookup"><span data-stu-id="a698f-207">[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4) and [Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) take two or three sequences and produce a sequence of tuples.</span></span> <span data-ttu-id="a698f-208">這些函式就像是適用于[清單](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)的對應函數。</span><span class="sxs-lookup"><span data-stu-id="a698f-208">These functions are like the corresponding functions available for [lists](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).</span></span> <span data-ttu-id="a698f-209">沒有對應的功能可將一個序列分隔成兩個或多個序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-209">There is no corresponding functionality to separate one sequence into two or more sequences.</span></span> <span data-ttu-id="a698f-210">如果您需要序列的這種功能, 請將序列轉換為清單, 並使用[list. 解壓縮](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)。</span><span class="sxs-lookup"><span data-stu-id="a698f-210">If you need this functionality for a sequence, convert the sequence to a list and use [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>

## <a name="sorting-comparing-and-grouping"></a><span data-ttu-id="a698f-211">排序、比較和群組</span><span class="sxs-lookup"><span data-stu-id="a698f-211">Sorting, Comparing, and Grouping</span></span>

<span data-ttu-id="a698f-212">清單支援的排序函數也適用于順序。</span><span class="sxs-lookup"><span data-stu-id="a698f-212">The sorting functions supported for lists also work with sequences.</span></span> <span data-ttu-id="a698f-213">這包括[seq. sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e)和[sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f)。</span><span class="sxs-lookup"><span data-stu-id="a698f-213">This includes [Seq.sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) and [Seq.sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f).</span></span> <span data-ttu-id="a698f-214">這些函式會逐一查看整個序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-214">These functions iterate through the whole sequence.</span></span>

<span data-ttu-id="a698f-215">您可以使用[seq.comparewith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f)函數來比較兩個序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-215">You compare two sequences by using the [Seq.compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f) function.</span></span> <span data-ttu-id="a698f-216">函式會輪流比較後續的元素, 並在遇到第一個不相等的配對時停止。</span><span class="sxs-lookup"><span data-stu-id="a698f-216">The function compares successive elements in turn, and stops when it encounters the first unequal pair.</span></span> <span data-ttu-id="a698f-217">任何其他元素都不會參與比較。</span><span class="sxs-lookup"><span data-stu-id="a698f-217">Any additional elements do not contribute to the comparison.</span></span>

<span data-ttu-id="a698f-218">下列程式碼示範 `Seq.compareWith` 的用法。</span><span class="sxs-lookup"><span data-stu-id="a698f-218">The following code shows the use of `Seq.compareWith`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet19.fs)]

<span data-ttu-id="a698f-219">在先前的程式碼中, 只會計算並檢查第一個元素, 而結果為-1。</span><span class="sxs-lookup"><span data-stu-id="a698f-219">In the previous code, only the first element is computed and examined, and the result is -1.</span></span>

<span data-ttu-id="a698f-220">[Seq.countby](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f)接受一個函式, 此函式會針對每個專案產生稱為索引*鍵*的值。</span><span class="sxs-lookup"><span data-stu-id="a698f-220">[Seq.countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f) takes a function that generates a value called a *key* for each element.</span></span> <span data-ttu-id="a698f-221">在每個專案上呼叫此函式, 即可為每個元素產生索引鍵。</span><span class="sxs-lookup"><span data-stu-id="a698f-221">A key is generated for each element by calling this function on each element.</span></span> <span data-ttu-id="a698f-222">`Seq.countBy`然後傳回包含索引鍵值的序列, 以及產生每個索引鍵值的元素計數。</span><span class="sxs-lookup"><span data-stu-id="a698f-222">`Seq.countBy` then returns a sequence that contains the key values, and a count of the number of elements that generated each value of the key.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet201.fs)]

<span data-ttu-id="a698f-223">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="a698f-223">The output is as follows.</span></span>

```
(1, 34) (2, 33) (0, 33)
```

<span data-ttu-id="a698f-224">先前的輸出顯示, 原始序列中有34個元素產生金鑰1、33值產生金鑰 2, 以及33產生金鑰0的值。</span><span class="sxs-lookup"><span data-stu-id="a698f-224">The previous output shows that there were 34 elements of the original sequence that produced the key 1, 33 values that produced the key 2, and 33 values that produced the key 0.</span></span>

<span data-ttu-id="a698f-225">您可以藉由呼叫[Seq. groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd)來分組序列的元素。</span><span class="sxs-lookup"><span data-stu-id="a698f-225">You can group elements of a sequence by calling [Seq.groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd).</span></span> <span data-ttu-id="a698f-226">`Seq.groupBy`接受從專案產生索引鍵的序列和函式。</span><span class="sxs-lookup"><span data-stu-id="a698f-226">`Seq.groupBy` takes a sequence and a function that generates a key from an element.</span></span> <span data-ttu-id="a698f-227">函式會在序列的每個元素上執行。</span><span class="sxs-lookup"><span data-stu-id="a698f-227">The function is executed on each element of the sequence.</span></span> <span data-ttu-id="a698f-228">`Seq.groupBy`傳回一系列的元組, 其中每個元組的第一個元素都是索引鍵, 而第二個是產生該金鑰的專案序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-228">`Seq.groupBy` returns a sequence of tuples, where the first element of each tuple is the key and the second is a sequence of elements that produce that key.</span></span>

<span data-ttu-id="a698f-229">下列程式碼範例示範`Seq.groupBy`如何使用將數位序列從1到100分割成三個群組, 其中有相異索引鍵值0、1和2。</span><span class="sxs-lookup"><span data-stu-id="a698f-229">The following code example shows the use of `Seq.groupBy` to partition the sequence of numbers from 1 to 100 into three groups that have the distinct key values 0, 1, and 2.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet202.fs)]

<span data-ttu-id="a698f-230">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="a698f-230">The output is as follows.</span></span>

```
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

<span data-ttu-id="a698f-231">您可以藉由呼叫[Seq. distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401)來建立刪除重複元素的序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-231">You can create a sequence that eliminates duplicate elements by calling [Seq.distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401).</span></span> <span data-ttu-id="a698f-232">或者, 您可以使用[seq.distinctby](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75), 它會取得要在每個元素上呼叫的索引鍵產生函式。</span><span class="sxs-lookup"><span data-stu-id="a698f-232">Or you can use [Seq.distinctBy](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75), which takes a key-generating function to be called on each element.</span></span> <span data-ttu-id="a698f-233">產生的序列包含具有唯一索引鍵之原始序列的元素。之後, 會捨棄為較早的專案產生重複索引鍵的元素。</span><span class="sxs-lookup"><span data-stu-id="a698f-233">The resulting sequence contains elements of the original sequence that have unique keys; later elements that produce a duplicate key to an earlier element are discarded.</span></span>

<span data-ttu-id="a698f-234">下列程式碼範例說明的用法`Seq.distinct`。</span><span class="sxs-lookup"><span data-stu-id="a698f-234">The following code example illustrates the use of `Seq.distinct`.</span></span> <span data-ttu-id="a698f-235">`Seq.distinct`會藉由產生代表二進位數的序列來示範, 然後顯示唯一不同的元素為0和1。</span><span class="sxs-lookup"><span data-stu-id="a698f-235">`Seq.distinct` is demonstrated by generating sequences that represent binary numbers, and then showing that the only distinct elements are 0 and 1.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet22.fs)]

<span data-ttu-id="a698f-236">下列程式碼會`Seq.distinctBy`以包含負數和正數的序列開始示範, 並使用絕對值函數做為索引鍵產生函數。</span><span class="sxs-lookup"><span data-stu-id="a698f-236">The following code demonstrates `Seq.distinctBy` by starting with a sequence that contains negative and positive numbers and using the absolute value function as the key-generating function.</span></span> <span data-ttu-id="a698f-237">產生的序列遺漏了對應于序列中負數的所有正數, 因為負數會出現在序列中的前面, 因此會選取, 而不是具有相同絕對值的正數value 或 key。</span><span class="sxs-lookup"><span data-stu-id="a698f-237">The resulting sequence is missing all the positive numbers that correspond to the negative numbers in the sequence, because the negative numbers appear earlier in the sequence and therefore are selected instead of the positive numbers that have the same absolute value, or key.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet23.fs)]

## <a name="readonly-and-cached-sequences"></a><span data-ttu-id="a698f-238">Readonly 和快取的序列</span><span class="sxs-lookup"><span data-stu-id="a698f-238">Readonly and Cached Sequences</span></span>

<span data-ttu-id="a698f-239">[Seq。 readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7)會建立序列的唯讀複本。</span><span class="sxs-lookup"><span data-stu-id="a698f-239">[Seq.readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7) creates a read-only copy of a sequence.</span></span> <span data-ttu-id="a698f-240">`Seq.readonly`當您有讀寫集合 (例如陣列), 而且不想修改原創組合時, 會很有用。</span><span class="sxs-lookup"><span data-stu-id="a698f-240">`Seq.readonly` is useful when you have a read-write collection, such as an array, and you do not want to modify the original collection.</span></span> <span data-ttu-id="a698f-241">此函式可以用來保留資料封裝。</span><span class="sxs-lookup"><span data-stu-id="a698f-241">This function can be used to preserve data encapsulation.</span></span> <span data-ttu-id="a698f-242">在下列程式碼範例中, 會建立包含陣列的類型。</span><span class="sxs-lookup"><span data-stu-id="a698f-242">In the following code example, a type that contains an array is created.</span></span> <span data-ttu-id="a698f-243">屬性會公開陣列, 但不會傳回陣列, 它會傳回從陣列使用`Seq.readonly`所建立的序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-243">A property exposes the array, but instead of returning an array, it returns a sequence that is created from the array by using `Seq.readonly`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/fssequences/snippet24.fs)]

<span data-ttu-id="a698f-244">[Seq. cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0)會建立序列的預存版本。</span><span class="sxs-lookup"><span data-stu-id="a698f-244">[Seq.cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0) creates a stored version of a sequence.</span></span> <span data-ttu-id="a698f-245">使用`Seq.cache`來避免重新評估序列, 或當您有多個使用序列的執行緒時, 您必須確定每個元素只會在一次的情況下進行動作。</span><span class="sxs-lookup"><span data-stu-id="a698f-245">Use `Seq.cache` to avoid reevaluation of a sequence, or when you have multiple threads that use a sequence, but you must make sure that each element is acted upon only one time.</span></span> <span data-ttu-id="a698f-246">當您有多個執行緒正在使用的序列時, 您可以有一個執行緒會列舉並計算原始序列的值, 而其餘執行緒可以使用快取的序列。</span><span class="sxs-lookup"><span data-stu-id="a698f-246">When you have a sequence that is being used by multiple threads, you can have one thread that enumerates and computes the values for the original sequence, and remaining threads can use the cached sequence.</span></span>

## <a name="performing-computations-on-sequences"></a><span data-ttu-id="a698f-247">在序列上執行計算</span><span class="sxs-lookup"><span data-stu-id="a698f-247">Performing Computations on Sequences</span></span>

<span data-ttu-id="a698f-248">簡單的算數運算與清單相似, 例如[seq. average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8)、 [seq. sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a)、 [averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8)、 [seq. sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)等等。</span><span class="sxs-lookup"><span data-stu-id="a698f-248">Simple arithmetic operations are like those of lists, such as [Seq.average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8), [Seq.sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a), [Seq.averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8), [Seq.sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1), and so on.</span></span>

<span data-ttu-id="a698f-249">[ [Seq](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3)]、[ [seq](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9)] 和 [ [seq]。 scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e)就像是可用於清單的對應函數。</span><span class="sxs-lookup"><span data-stu-id="a698f-249">[Seq.fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3), [Seq.reduce](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9), and [Seq.scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e) are like the corresponding functions that are available for lists.</span></span> <span data-ttu-id="a698f-250">序列支援這些函式的完整變數的子集, 這些函式會列出支援。</span><span class="sxs-lookup"><span data-stu-id="a698f-250">Sequences support a subset of the full variations of these functions that lists support.</span></span> <span data-ttu-id="a698f-251">如需詳細資訊和範例, 請參閱[清單](lists.md)。</span><span class="sxs-lookup"><span data-stu-id="a698f-251">For more information and examples, see [Lists](lists.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a698f-252">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a698f-252">See also</span></span>

- [<span data-ttu-id="a698f-253">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="a698f-253">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="a698f-254">F# 類型</span><span class="sxs-lookup"><span data-stu-id="a698f-254">F# Types</span></span>](fsharp-types.md)
