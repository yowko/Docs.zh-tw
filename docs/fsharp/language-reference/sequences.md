---
title: 序列 (F#)
description: '了解如何使用 F # 序列，當您使用較大，已排序集合的資料，但不一定要使用的所有項目。'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: a3521037112d40998ed00cd6fed376882c2f2c88
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2018
---
# <a name="sequences"></a><span data-ttu-id="cb995-103">序列</span><span class="sxs-lookup"><span data-stu-id="cb995-103">Sequences</span></span>

> [!NOTE]
<span data-ttu-id="cb995-104">本文中的 API 參考連結將帶您前往 MSDN。</span><span class="sxs-lookup"><span data-stu-id="cb995-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="cb995-105">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="cb995-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="cb995-106">A*順序*邏輯的一連串的項目所有的一種類型。</span><span class="sxs-lookup"><span data-stu-id="cb995-106">A *sequence* is a logical series of elements all of one type.</span></span> <span data-ttu-id="cb995-107">當您使用較大，已排序集合的資料，但不是一定會預期使用的所有項目時，順序會特別有用。</span><span class="sxs-lookup"><span data-stu-id="cb995-107">Sequences are particularly useful when you have a large, ordered collection of data but do not necessarily expect to use all of the elements.</span></span> <span data-ttu-id="cb995-108">個別序列項目會計算只做為必要項，讓序列可以提供較佳的效能比情況中，並非可用所有的項目中的清單。</span><span class="sxs-lookup"><span data-stu-id="cb995-108">Individual sequence elements are computed only as required, so a sequence can provide better performance than a list in situations in which not all the elements are used.</span></span> <span data-ttu-id="cb995-109">順序由`seq<'T>`類型，這是別名的`System.Collections.Generic.IEnumerable`。</span><span class="sxs-lookup"><span data-stu-id="cb995-109">Sequences are represented by the `seq<'T>` type, which is an alias for `System.Collections.Generic.IEnumerable`.</span></span> <span data-ttu-id="cb995-110">因此，任何.NET Framework 型別可實作`System.IEnumerable`可用做為序列。</span><span class="sxs-lookup"><span data-stu-id="cb995-110">Therefore, any .NET Framework type that implements `System.IEnumerable` can be used as a sequence.</span></span> <span data-ttu-id="cb995-111">[Seq 模組](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)提供操作與順序有關的支援。</span><span class="sxs-lookup"><span data-stu-id="cb995-111">The [Seq module](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) provides support for manipulations involving sequences.</span></span>

## <a name="sequence-expressions"></a><span data-ttu-id="cb995-112">循序項運算式</span><span class="sxs-lookup"><span data-stu-id="cb995-112">Sequence Expressions</span></span>
<span data-ttu-id="cb995-113">A*序列運算式*是一個順序評估的運算式。</span><span class="sxs-lookup"><span data-stu-id="cb995-113">A *sequence expression* is an expression that evaluates to a sequence.</span></span> <span data-ttu-id="cb995-114">循序項運算式中可能需要數種格式。</span><span class="sxs-lookup"><span data-stu-id="cb995-114">Sequence expressions can take a number of forms.</span></span> <span data-ttu-id="cb995-115">最簡單的形式指定的範圍。</span><span class="sxs-lookup"><span data-stu-id="cb995-115">The simplest form specifies a range.</span></span> <span data-ttu-id="cb995-116">例如，`seq { 1 .. 5 }`建立序列，其中包含五個項目，包括 1 到 5 的端點。</span><span class="sxs-lookup"><span data-stu-id="cb995-116">For example, `seq { 1 .. 5 }` creates a sequence that contains five elements, including the endpoints 1 and 5.</span></span> <span data-ttu-id="cb995-117">您也可以指定遞增 （或遞減） 之間兩個雙句點。</span><span class="sxs-lookup"><span data-stu-id="cb995-117">You can also specify an increment (or decrement) between two double periods.</span></span> <span data-ttu-id="cb995-118">例如，下列程式碼會建立 10 個倍數的順序。</span><span class="sxs-lookup"><span data-stu-id="cb995-118">For example, the following code creates the sequence of multiples of 10.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1502.fs)]

<span data-ttu-id="cb995-119">F # 運算式會產生序列的值是由循序項運算式所組成。</span><span class="sxs-lookup"><span data-stu-id="cb995-119">Sequence expressions are made up of F# expressions that produce values of the sequence.</span></span> <span data-ttu-id="cb995-120">他們可以使用`yield`關鍵字來產生變成順序一部分的值。</span><span class="sxs-lookup"><span data-stu-id="cb995-120">They can use the `yield` keyword to produce values that become part of the sequence.</span></span>

<span data-ttu-id="cb995-121">以下是範例。</span><span class="sxs-lookup"><span data-stu-id="cb995-121">Following is an example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1503.fs)]

<span data-ttu-id="cb995-122">您可以使用`->`運算子，而不是`yield`，在此情況下，您可以省略`do`關鍵字，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="cb995-122">You can use the `->` operator instead of `yield`, in which case you can omit the `do` keyword, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1504.fs)]

<span data-ttu-id="cb995-123">下列程式碼會產生一份座標組，以及索引到陣列，代表方格。</span><span class="sxs-lookup"><span data-stu-id="cb995-123">The following code generates a list of coordinate pairs along with an index into an array that represents the grid.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1505.fs)]

<span data-ttu-id="cb995-124">`if`序列中使用的運算式是篩選器。</span><span class="sxs-lookup"><span data-stu-id="cb995-124">An `if` expression used in a sequence is a filter.</span></span> <span data-ttu-id="cb995-125">例如，若要產生唯一的質數，假設您有函式的序列`isprime`型別的`int -> bool`，建構的序列，如下所示。</span><span class="sxs-lookup"><span data-stu-id="cb995-125">For example, to generate a sequence of only prime numbers, assuming that you have a function `isprime` of type `int -> bool`, construct the sequence as follows.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1506.fs)]

<span data-ttu-id="cb995-126">當您使用`yield`或`->`反覆項目，在每個反覆項目必須以產生單一項目的序列。</span><span class="sxs-lookup"><span data-stu-id="cb995-126">When you use `yield` or `->` in an iteration, each iteration is expected to generate a single element of the sequence.</span></span> <span data-ttu-id="cb995-127">如果每個反覆項目會產生一連串的項目，使用`yield!`。</span><span class="sxs-lookup"><span data-stu-id="cb995-127">If each iteration produces a sequence of elements, use `yield!`.</span></span> <span data-ttu-id="cb995-128">在此情況下，每個反覆運算上產生的項目會串連來產生最後的序列。</span><span class="sxs-lookup"><span data-stu-id="cb995-128">In that case, the elements generated on each iteration are concatenated to produce the final sequence.</span></span>

<span data-ttu-id="cb995-129">您可以結合在一起在循序項運算式中的多個運算式。</span><span class="sxs-lookup"><span data-stu-id="cb995-129">You can combine multiple expressions together in a sequence expression.</span></span> <span data-ttu-id="cb995-130">每個運算式所產生的項目串連在一起。</span><span class="sxs-lookup"><span data-stu-id="cb995-130">The elements generated by each expression are concatenated together.</span></span> <span data-ttu-id="cb995-131">如需範例，請參閱本主題的 「 範例 」 一節。</span><span class="sxs-lookup"><span data-stu-id="cb995-131">For an example, see the "Examples" section of this topic.</span></span>

## <a name="examples"></a><span data-ttu-id="cb995-132">範例</span><span class="sxs-lookup"><span data-stu-id="cb995-132">Examples</span></span>
<span data-ttu-id="cb995-133">第一個範例會使用循序項運算式包含反覆項目、 篩選和 yield 產生陣列。</span><span class="sxs-lookup"><span data-stu-id="cb995-133">The first example uses a sequence expression that contains an iteration, a filter, and a yield to generate an array.</span></span> <span data-ttu-id="cb995-134">此程式碼會列印一串質數介於 1 到 100 到主控台。</span><span class="sxs-lookup"><span data-stu-id="cb995-134">This code prints a sequence of prime numbers between 1 and 100 to the console.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1507.fs)]

<span data-ttu-id="cb995-135">下列程式碼會使用`yield`建立三個項目，各包含兩個因素與產品的 tuple 所組成的乘法表。</span><span class="sxs-lookup"><span data-stu-id="cb995-135">The following code uses `yield` to create a multiplication table that consists of tuples of three elements, each consisting of two factors and the product.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1508.fs)]

<span data-ttu-id="cb995-136">下列範例示範如何使用`yield!`結合成單一的最後一個序列的個別序列。</span><span class="sxs-lookup"><span data-stu-id="cb995-136">The following example demonstrates the use of `yield!` to combine individual sequences into a single final sequence.</span></span> <span data-ttu-id="cb995-137">在此情況下，在二進位樹狀目錄中的每個樹狀子目錄的序列會在遞迴函式，以產生最終的順序串連。</span><span class="sxs-lookup"><span data-stu-id="cb995-137">In this case, the sequences for each subtree in a binary tree are concatenated in a recursive function to produce the final sequence.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1509.fs)]
    
## <a name="using-sequences"></a><span data-ttu-id="cb995-138">使用順序</span><span class="sxs-lookup"><span data-stu-id="cb995-138">Using Sequences</span></span>
<span data-ttu-id="cb995-139">時序支援許多相同的函式做為[列出](lists.md)。</span><span class="sxs-lookup"><span data-stu-id="cb995-139">Sequences support many of the same functions as [lists](lists.md).</span></span> <span data-ttu-id="cb995-140">序列也支援分組，並且使用索引鍵產生函式計算等作業。</span><span class="sxs-lookup"><span data-stu-id="cb995-140">Sequences also support operations such as grouping and counting by using key-generating functions.</span></span> <span data-ttu-id="cb995-141">序列也支援更多樣化的函式來擷取子。</span><span class="sxs-lookup"><span data-stu-id="cb995-141">Sequences also support more diverse functions for extracting subsequences.</span></span>

<span data-ttu-id="cb995-142">許多資料類型，例如清單、 陣列、 集合和對應是以隱含方式序列，因為它們是可列舉集合。</span><span class="sxs-lookup"><span data-stu-id="cb995-142">Many data types, such as lists, arrays, sets, and maps are implicitly sequences because they are enumerable collections.</span></span> <span data-ttu-id="cb995-143">函式會將序列，當做引數搭配任一常見 F # 資料類型，除了可實作任何.NET Framework 資料型別的`System.Collections.Generic.IEnumerable<'T>`。</span><span class="sxs-lookup"><span data-stu-id="cb995-143">A function that takes a sequence as an argument works with any of the common F# data types, in addition to any .NET Framework data type that implements `System.Collections.Generic.IEnumerable<'T>`.</span></span> <span data-ttu-id="cb995-144">以此對照接受清單做為引數只能接受清單的函式。</span><span class="sxs-lookup"><span data-stu-id="cb995-144">Contrast this to a function that takes a list as an argument, which can only take lists.</span></span> <span data-ttu-id="cb995-145">型別`seq<'T>`是類型縮寫`IEnumerable<'T>`。</span><span class="sxs-lookup"><span data-stu-id="cb995-145">The type `seq<'T>` is a type abbreviation for `IEnumerable<'T>`.</span></span> <span data-ttu-id="cb995-146">這表示任何型別實作泛型`System.Collections.Generic.IEnumerable<'T>`，其中包括陣列、 清單、 設定和 F # 和也大部分.NET Framework 集合型別中的對應相容`seq`輸入，然後就可以使用預期的順序。</span><span class="sxs-lookup"><span data-stu-id="cb995-146">This means that any type that implements the generic `System.Collections.Generic.IEnumerable<'T>`, which includes arrays, lists, sets, and maps in F#, and also most .NET Framework collection types, is compatible with the `seq` type and can be used wherever a sequence is expected.</span></span>


## <a name="module-functions"></a><span data-ttu-id="cb995-147">模組函式</span><span class="sxs-lookup"><span data-stu-id="cb995-147">Module Functions</span></span>
<span data-ttu-id="cb995-148">[Seq 模組](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684)中[Microsoft.FSharp.Collections 命名空間](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f)包含序列所使用的功能。</span><span class="sxs-lookup"><span data-stu-id="cb995-148">The [Seq module](https://msdn.microsoft.com/library/54e8f059-ca52-4632-9ae9-49685ee9b684) in the [Microsoft.FSharp.Collections namespace](https://msdn.microsoft.com/library/24f64e5f-5030-47d0-9759-8d3e398ed13f) contains functions for working with sequences.</span></span> <span data-ttu-id="cb995-149">這些函式使用清單、 陣列、 對應和集合，因為所有這些類型是可列舉的並因此可被視為序列。</span><span class="sxs-lookup"><span data-stu-id="cb995-149">These functions work with lists, arrays, maps, and sets as well, because all of those types are enumerable, and therefore can be treated as sequences.</span></span>


## <a name="creating-sequences"></a><span data-ttu-id="cb995-150">建立順序</span><span class="sxs-lookup"><span data-stu-id="cb995-150">Creating Sequences</span></span>
<span data-ttu-id="cb995-151">您可以建立序列之前所述，使用循序項運算式，或使用某些函式。</span><span class="sxs-lookup"><span data-stu-id="cb995-151">You can create sequences by using sequence expressions, as described previously, or by using certain functions.</span></span>

<span data-ttu-id="cb995-152">您可以使用來建立空的序列[Seq.empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59)，或者您可以建立一連串的只有一個指定的項目使用[Seq.singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7)。</span><span class="sxs-lookup"><span data-stu-id="cb995-152">You can create an empty sequence by using [Seq.empty](https://msdn.microsoft.com/library/3c7f1c69-6117-4782-b2da-0e04d6854f59), or you can create a sequence of just one specified element by using [Seq.singleton](https://msdn.microsoft.com/library/9b8cc460-a282-4ec5-b29a-630ab17e9de7).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet9.fs)]

<span data-ttu-id="cb995-153">您可以使用[Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576)建立項目建立使用您提供的函式的順序。</span><span class="sxs-lookup"><span data-stu-id="cb995-153">You can use [Seq.init](https://msdn.microsoft.com/library/059de69d-812c-4f8e-be86-88aa72101576) to create a sequence for which the elements are created by using a function that you provide.</span></span> <span data-ttu-id="cb995-154">您也會提供用於序列的大小。</span><span class="sxs-lookup"><span data-stu-id="cb995-154">You also provide a size for the sequence.</span></span> <span data-ttu-id="cb995-155">此函式一樣是[List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83)，不同之處在於您逐一查看序列之前不會建立項目。</span><span class="sxs-lookup"><span data-stu-id="cb995-155">This function is just like [List.init](https://msdn.microsoft.com/library/dd38c096-0ea8-4858-be6b-794b90418b83), except that the elements are not created until you iterate through the sequence.</span></span> <span data-ttu-id="cb995-156">下列程式碼說明如何使用`Seq.init`。</span><span class="sxs-lookup"><span data-stu-id="cb995-156">The following code illustrates the use of `Seq.init`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet10.fs)]

<span data-ttu-id="cb995-157">輸出為</span><span class="sxs-lookup"><span data-stu-id="cb995-157">The output is</span></span>

```
0 10 20 30 40
```

<span data-ttu-id="cb995-158">使用[Seq.ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99)和[Seq.ofList&#60;t&#62;函式](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d)，您可以建立從陣列和清單的順序。</span><span class="sxs-lookup"><span data-stu-id="cb995-158">By using [Seq.ofArray](https://msdn.microsoft.com/library/299cd4d9-be72-4511-aac8-089e1ddaac99) and [Seq.ofList&#60;'T&#62; Function](https://msdn.microsoft.com/visualfsharpdocs/conceptual/seq.oflist%5b%27t%5d-function-%5bfsharp%5d), you can create sequences from arrays and lists.</span></span> <span data-ttu-id="cb995-159">不過，您也可以轉換陣列和清單順序使用轉換運算子。</span><span class="sxs-lookup"><span data-stu-id="cb995-159">However, you can also convert arrays and lists to sequences by using a cast operator.</span></span> <span data-ttu-id="cb995-160">這兩種技術是以下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="cb995-160">Both techniques are shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet11.fs)]

<span data-ttu-id="cb995-161">使用[Seq.cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334)，您可以從弱型別的集合，例如所定義的建立順序`System.Collections`。</span><span class="sxs-lookup"><span data-stu-id="cb995-161">By using [Seq.cast](https://msdn.microsoft.com/library/1d087db3-a8b2-41dd-8ddc-227544529334), you can create a sequence from a weakly typed collection, such as those defined in `System.Collections`.</span></span> <span data-ttu-id="cb995-162">這類弱型別的集合都具有項目型別`System.Object`會使用非泛型列舉和`System.Collections.Generic.IEnumerable&#96;1`型別。</span><span class="sxs-lookup"><span data-stu-id="cb995-162">Such weakly typed collections have the element type `System.Object` and are enumerated by using the non-generic `System.Collections.Generic.IEnumerable&#96;1` type.</span></span> <span data-ttu-id="cb995-163">下列程式碼說明如何使用`Seq.cast`轉換`System.Collections.ArrayList`成序列。</span><span class="sxs-lookup"><span data-stu-id="cb995-163">The following code illustrates the use of `Seq.cast` to convert an `System.Collections.ArrayList` into a sequence.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet12.fs)]

<span data-ttu-id="cb995-164">您可以使用，以定義無限序列[Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef)函式。</span><span class="sxs-lookup"><span data-stu-id="cb995-164">You can define infinite sequences by using the [Seq.initInfinite](https://msdn.microsoft.com/library/d1804e53-da92-48ec-8d6e-57eaf4c62bef) function.</span></span> <span data-ttu-id="cb995-165">對於時序，您可以提供函式，並產生的項目索引的每個項目。</span><span class="sxs-lookup"><span data-stu-id="cb995-165">For such a sequence, you provide a function that generates each element from the index of the element.</span></span> <span data-ttu-id="cb995-166">無限期的順序有可能因為延遲評估;視需要透過呼叫您指定的函式，會建立項目。</span><span class="sxs-lookup"><span data-stu-id="cb995-166">Infinite sequences are possible because of lazy evaluation; elements are created as needed by calling the function that you specify.</span></span> <span data-ttu-id="cb995-167">下列程式碼範例會產生浮點數，在此情況下替代倒數連續整數平方的一系列的無限的序列。</span><span class="sxs-lookup"><span data-stu-id="cb995-167">The following code example produces an infinite sequence of floating point numbers, in this case the alternating series of reciprocals of squares of successive integers.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet13.fs)]

<span data-ttu-id="cb995-168">[Seq.unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21)產生一連串的計算函式取用狀態，並將其轉換為產生的序列中每個後續項目。</span><span class="sxs-lookup"><span data-stu-id="cb995-168">[Seq.unfold](https://msdn.microsoft.com/library/7d9232fc-742e-42bc-bdf7-6f130f0eff21) generates a sequence from a computation function that takes a state and transforms it to produce each subsequent element in the sequence.</span></span> <span data-ttu-id="cb995-169">狀態為只是用來計算每個項目，並可隨著每個項目會計算值。</span><span class="sxs-lookup"><span data-stu-id="cb995-169">The state is just a value that is used to compute each element, and can change as each element is computed.</span></span> <span data-ttu-id="cb995-170">第二個引數`Seq.unfold`是用來啟動順序的起始值。</span><span class="sxs-lookup"><span data-stu-id="cb995-170">The second argument to `Seq.unfold` is the initial value that is used to start the sequence.</span></span> <span data-ttu-id="cb995-171">`Seq.unfold` 使用狀態，可讓您藉由傳回終止順序選項的型別`None`值。</span><span class="sxs-lookup"><span data-stu-id="cb995-171">`Seq.unfold` uses an option type for the state, which enables you to terminate the sequence by returning the `None` value.</span></span> <span data-ttu-id="cb995-172">下列程式碼顯示的順序，兩個範例`seq1`和`fib`，由產生`unfold`作業。</span><span class="sxs-lookup"><span data-stu-id="cb995-172">The following code shows two examples of sequences, `seq1` and `fib`, that are generated by an `unfold` operation.</span></span> <span data-ttu-id="cb995-173">首先， `seq1`，是只具有最多 100 的數字的簡單順序。</span><span class="sxs-lookup"><span data-stu-id="cb995-173">The first, `seq1`, is just a simple sequence with numbers up to 100.</span></span> <span data-ttu-id="cb995-174">第二個， `fib`，會使用`unfold`來計算 Fibonacci 順序。</span><span class="sxs-lookup"><span data-stu-id="cb995-174">The second, `fib`, uses `unfold` to compute the Fibonacci sequence.</span></span> <span data-ttu-id="cb995-175">費式數列序列中的每個項目是先前的兩個 Fibonacci 數字的總和，因為狀態值是序列中前兩個數字所組成的 tuple。</span><span class="sxs-lookup"><span data-stu-id="cb995-175">Because each element in the Fibonacci sequence is the sum of the previous two Fibonacci numbers, the state value is a tuple that consists of the previous two numbers in the sequence.</span></span> <span data-ttu-id="cb995-176">初始值是`(1,1)`，序列中的前兩個數字。</span><span class="sxs-lookup"><span data-stu-id="cb995-176">The initial value is `(1,1)`, the first two numbers in the sequence.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet14.fs)]

<span data-ttu-id="cb995-177">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="cb995-177">The output is as follows:</span></span>

```
The sequence seq1 contains numbers from 0 to 20.

0 1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20

The sequence fib contains Fibonacci numbers.

2 3 5 8 13 21 34 55 89 144 233 377 610 987 1597
```

<span data-ttu-id="cb995-178">下列程式碼會使用許多順序模組函式產生，並計算的無限序列值此處所述的範例。</span><span class="sxs-lookup"><span data-stu-id="cb995-178">The following code is an example that uses many of the sequence module functions described here to generate and compute the values of infinite sequences.</span></span> <span data-ttu-id="cb995-179">程式碼可能需要幾分鐘才能完成。</span><span class="sxs-lookup"><span data-stu-id="cb995-179">The code might take a few minutes to run.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet15.fs)]
    
## <a name="searching-and-finding-elements"></a><span data-ttu-id="cb995-180">搜尋和尋找項目</span><span class="sxs-lookup"><span data-stu-id="cb995-180">Searching and Finding Elements</span></span>
<span data-ttu-id="cb995-181">序列支援的功能適用於清單： [Seq.exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1)， [Seq.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565)， [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8)， [Seq.findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3)， [Seq.pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d)， [Seq.tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47)，和[Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a)。</span><span class="sxs-lookup"><span data-stu-id="cb995-181">Sequences support functionality available with lists: [Seq.exists](https://msdn.microsoft.com/library/428c97bf-599d-4c39-a5b9-f8717c198ad1), [Seq.exists2](https://msdn.microsoft.com/library/efdf14a4-27f7-4dc1-9281-52639e66d565), [Seq.find](https://msdn.microsoft.com/library/02c21ecd-97e5-4e99-a4c1-b4d0b730b7d8), [Seq.findIndex](https://msdn.microsoft.com/library/96dfe86b-df15-4d92-8316-7cd6055e09f3), [Seq.pick](https://msdn.microsoft.com/library/a87bc771-55f7-43f9-94f9-33d8f9bf325d), [Seq.tryFind](https://msdn.microsoft.com/library/ac43c6f5-4dc7-4e9a-a222-00b5736aee47), and [Seq.tryFindIndex](https://msdn.microsoft.com/library/c357b221-edf6-4f68-bf40-82a3156d945a).</span></span> <span data-ttu-id="cb995-182">這些函式可供順序的版本會評估順序，只會一直要搜尋的項目。</span><span class="sxs-lookup"><span data-stu-id="cb995-182">The versions of these functions that are available for sequences evaluate the sequence only up to the element that is being searched for.</span></span> <span data-ttu-id="cb995-183">如需範例，請參閱[列出](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)。</span><span class="sxs-lookup"><span data-stu-id="cb995-183">For examples, see [Lists](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).</span></span>


## <a name="obtaining-subsequences"></a><span data-ttu-id="cb995-184">取得子</span><span class="sxs-lookup"><span data-stu-id="cb995-184">Obtaining Subsequences</span></span>
<span data-ttu-id="cb995-185">[Seq.filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770)和[Seq.choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395)是類似的對應函式清單，請使用不同之處在於篩選並選擇，才會進行評估的順序項目。</span><span class="sxs-lookup"><span data-stu-id="cb995-185">[Seq.filter](https://msdn.microsoft.com/library/7f2e9850-a660-460c-9831-3bbff5613770) and [Seq.choose](https://msdn.microsoft.com/library/63b83b06-4b24-4239-bf69-a2c12d891395) are like the corresponding functions that are available for lists, except that the filtering and choosing does not occur until the sequence elements are evaluated.</span></span>

<span data-ttu-id="cb995-186">[Seq.truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244)從另一個序列，會建立序列，但將序列限制為指定的項目數。</span><span class="sxs-lookup"><span data-stu-id="cb995-186">[Seq.truncate](https://msdn.microsoft.com/library/1892dfeb-308e-45e2-857a-3c3405d02244) creates a sequence from another sequence, but limits the sequence to a specified number of elements.</span></span> <span data-ttu-id="cb995-187">[Seq.take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596)會建立新的序列，包含指定數字的序列開頭的項目。</span><span class="sxs-lookup"><span data-stu-id="cb995-187">[Seq.take](https://msdn.microsoft.com/library/6e75f701-640b-4c4a-9d63-4313fc090596) creates a new sequence that contains only a specified number of elements from the start of a sequence.</span></span> <span data-ttu-id="cb995-188">如果有較少序列中的項目比您指定要採取，`Seq.take`會擲回`System.InvalidOperationException`。</span><span class="sxs-lookup"><span data-stu-id="cb995-188">If there are fewer elements in the sequence than you specify to take, `Seq.take` throws a `System.InvalidOperationException`.</span></span> <span data-ttu-id="cb995-189">之間的差異`Seq.take`和`Seq.truncate`在於`Seq.truncate`的元素數目少於的數字就是指定不會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="cb995-189">The difference between `Seq.take` and `Seq.truncate` is that `Seq.truncate` does not produce an error if the number of elements is fewer than the number you specify.</span></span>

<span data-ttu-id="cb995-190">下列程式碼所示的行為和之間的差異`Seq.truncate`和`Seq.take`。</span><span class="sxs-lookup"><span data-stu-id="cb995-190">The following code shows the behavior of and differences between `Seq.truncate` and `Seq.take`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet16.fs)]

<span data-ttu-id="cb995-191">輸出中，會發生此錯誤之前，如下所示。</span><span class="sxs-lookup"><span data-stu-id="cb995-191">The output, before the error occurs, is as follows.</span></span>

```
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100 
1 4 9 16 25 
1 4 9 16 25 36 49 64 81 100
```

<span data-ttu-id="cb995-192">使用[Seq.takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92)，您可以指定述詞的函式 （布林值的函式），並建立另一個原始序列的述詞的這些元素組成的序列中的順序`true`，但停止傳回的述詞的第一個項目之前`false`。</span><span class="sxs-lookup"><span data-stu-id="cb995-192">By using [Seq.takeWhile](https://msdn.microsoft.com/library/19eea4ce-66e0-4353-b015-72eb03421d92), you can specify a predicate function (a Boolean function) and create a sequence from another sequence made up of those elements of the original sequence for which the predicate is `true`, but stop before the first element for which the predicate returns `false`.</span></span> <span data-ttu-id="cb995-193">[Seq.skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1)傳回序列，略過指定的數目的另一個序列的第一個項目，並傳回其餘項目。</span><span class="sxs-lookup"><span data-stu-id="cb995-193">[Seq.skip](https://msdn.microsoft.com/library/b4eb3f08-8594-4d17-8180-852c6c688bf1) returns a sequence that skips a specified number of the first elements of another sequence and returns the remaining elements.</span></span> <span data-ttu-id="cb995-194">[Seq.skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16)傳回略過另一個序列的第一個項目，只要傳回的述詞的序列`true`，然後傳回其餘項目，則述詞傳回的第一個元素開始`false`.</span><span class="sxs-lookup"><span data-stu-id="cb995-194">[Seq.skipWhile](https://msdn.microsoft.com/library/fb729021-2a3c-430f-83c3-0b37526f1a16) returns a sequence that skips the first elements of another sequence as long as the predicate returns `true`, and then returns the remaining elements, starting with the first element for which the predicate returns `false`.</span></span>

<span data-ttu-id="cb995-195">下列程式碼範例說明的行為和之間的差異`Seq.takeWhile`， `Seq.skip`，和`Seq.skipWhile`。</span><span class="sxs-lookup"><span data-stu-id="cb995-195">The following code example illustrates the behavior of and differences between `Seq.takeWhile`, `Seq.skip`, and `Seq.skipWhile`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet17.fs)]

<span data-ttu-id="cb995-196">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="cb995-196">The output is as follows.</span></span>

```
1 4 9 
36 49 64 81 100 
16 25 36 49 64 81 100
```

## <a name="transforming-sequences"></a><span data-ttu-id="cb995-197">轉換順序</span><span class="sxs-lookup"><span data-stu-id="cb995-197">Transforming Sequences</span></span>
<span data-ttu-id="cb995-198">[Seq.pairwise](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1)會建立新的序列，後續的輸入序列的項目會群 tuple。</span><span class="sxs-lookup"><span data-stu-id="cb995-198">[Seq.pairwise](https://msdn.microsoft.com/library/210dcf26-4e24-4d83-af6d-a8288b2ae4b1) creates a new sequence in which successive elements of the input sequence are grouped into tuples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet18.fs)]

<span data-ttu-id="cb995-199">[Seq.windowed](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744)就像是`Seq.pairwise`，不過，而不是產生一連串的 tuple，它會產生一連串的陣列，其中包含的相鄰元素的複本 (*視窗*) 序列。</span><span class="sxs-lookup"><span data-stu-id="cb995-199">[Seq.windowed](https://msdn.microsoft.com/library/8b565b8f-d645-4dba-be22-099075fe4744) is like `Seq.pairwise`, except that instead of producing a sequence of tuples, it produces a sequence of arrays that contain copies of adjacent elements (a *window*) from the sequence.</span></span> <span data-ttu-id="cb995-200">您每個陣列中指定您想要的相鄰項目數目。</span><span class="sxs-lookup"><span data-stu-id="cb995-200">You specify the number of adjacent elements you want in each array.</span></span>

<span data-ttu-id="cb995-201">下列程式碼範例示範 `Seq.windowed` 的用法。</span><span class="sxs-lookup"><span data-stu-id="cb995-201">The following code example demonstrates the use of `Seq.windowed`.</span></span> <span data-ttu-id="cb995-202">在此情況下視窗中的項目數為 3。</span><span class="sxs-lookup"><span data-stu-id="cb995-202">In this case the number of elements in the window is 3.</span></span> <span data-ttu-id="cb995-203">此範例會使用`printSeq`，定義在先前的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="cb995-203">The example uses `printSeq`, which is defined in the previous code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet180.fs)]

<span data-ttu-id="cb995-204">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="cb995-204">The output is as follows.</span></span>

<span data-ttu-id="cb995-205">初始順序：</span><span class="sxs-lookup"><span data-stu-id="cb995-205">Initial sequence:</span></span>

```
1.0 1.5 2.0 1.5 1.0 1.5 

Windows of length 3: 
[|1.0; 1.5; 2.0|] [|1.5; 2.0; 1.5|] [|2.0; 1.5; 1.0|] [|1.5; 1.0; 1.5|] 

Moving average: 
1.5 1.666666667 1.5 1.333333333
```

## <a name="operations-with-multiple-sequences"></a><span data-ttu-id="cb995-206">使用多個序列的作業</span><span class="sxs-lookup"><span data-stu-id="cb995-206">Operations with Multiple Sequences</span></span>
<span data-ttu-id="cb995-207">[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4)和[Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16)採用兩個或三個序列，並產生一連串的 tuple。</span><span class="sxs-lookup"><span data-stu-id="cb995-207">[Seq.zip](https://msdn.microsoft.com/library/0a5df8bf-0d48-44ce-bff4-e8ef1df5bca4) and [Seq.zip3](https://msdn.microsoft.com/library/ef13bebb-22ae-4eb9-873b-87dd29154d16) take two or three sequences and produce a sequence of tuples.</span></span> <span data-ttu-id="cb995-208">這些函式是對應的函式用於像[列出](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d)。</span><span class="sxs-lookup"><span data-stu-id="cb995-208">These functions are like the corresponding functions available for [lists](https://msdn.microsoft.com/library/83102799-f251-42e1-93ef-64232e8c5b1d).</span></span> <span data-ttu-id="cb995-209">沒有任何對應的功能，來分隔一個序列分成兩個或多個序列。</span><span class="sxs-lookup"><span data-stu-id="cb995-209">There is no corresponding functionality to separate one sequence into two or more sequences.</span></span> <span data-ttu-id="cb995-210">如果您需要這項功能的序列，將序列轉換為清單，並使用[List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)。</span><span class="sxs-lookup"><span data-stu-id="cb995-210">If you need this functionality for a sequence, convert the sequence to a list and use [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>


## <a name="sorting-comparing-and-grouping"></a><span data-ttu-id="cb995-211">排序、 比較和群組</span><span class="sxs-lookup"><span data-stu-id="cb995-211">Sorting, Comparing, and Grouping</span></span>
<span data-ttu-id="cb995-212">List 支援排序函式也會使用序列。</span><span class="sxs-lookup"><span data-stu-id="cb995-212">The sorting functions supported for lists also work with sequences.</span></span> <span data-ttu-id="cb995-213">這包括[Seq.sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e)和[Seq.sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f)。</span><span class="sxs-lookup"><span data-stu-id="cb995-213">This includes [Seq.sort](https://msdn.microsoft.com/library/327ea595-e77c-4529-b61e-8c6cbf5ec92e) and [Seq.sortBy](https://msdn.microsoft.com/library/4f8b4fb9-bf20-49d9-b4ee-dcc906c8208f).</span></span> <span data-ttu-id="cb995-214">這些函式逐一查看整個序列。</span><span class="sxs-lookup"><span data-stu-id="cb995-214">These functions iterate through the whole sequence.</span></span>

<span data-ttu-id="cb995-215">使用比較兩個序列[Seq.compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f)函式。</span><span class="sxs-lookup"><span data-stu-id="cb995-215">You compare two sequences by using the [Seq.compareWith](https://msdn.microsoft.com/library/5a740135-0b3a-4545-816f-8f91cc31290f) function.</span></span> <span data-ttu-id="cb995-216">函式接著會比較連續元素，並停止當它遇到第一對不相等。</span><span class="sxs-lookup"><span data-stu-id="cb995-216">The function compares successive elements in turn, and stops when it encounters the first unequal pair.</span></span> <span data-ttu-id="cb995-217">任何其他項目不會構成的比較。</span><span class="sxs-lookup"><span data-stu-id="cb995-217">Any additional elements do not contribute to the comparison.</span></span>

<span data-ttu-id="cb995-218">下列程式碼示範 `Seq.compareWith` 的用法。</span><span class="sxs-lookup"><span data-stu-id="cb995-218">The following code shows the use of `Seq.compareWith`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet19.fs)]

<span data-ttu-id="cb995-219">先前的程式碼中，第一個項目會計算和檢查，且結果為-1。</span><span class="sxs-lookup"><span data-stu-id="cb995-219">In the previous code, only the first element is computed and examined, and the result is -1.</span></span>

<span data-ttu-id="cb995-220">[Seq.countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f)接受函式產生一個值，稱為*金鑰*每個項目。</span><span class="sxs-lookup"><span data-stu-id="cb995-220">[Seq.countBy](https://msdn.microsoft.com/library/721702a5-150e-4fe8-81cd-ffbf8476cc1f) takes a function that generates a value called a *key* for each element.</span></span> <span data-ttu-id="cb995-221">每個項目產生金鑰，在每個項目上呼叫此函式。</span><span class="sxs-lookup"><span data-stu-id="cb995-221">A key is generated for each element by calling this function on each element.</span></span> <span data-ttu-id="cb995-222">`Seq.countBy` 則會傳回序列，其中包含的索引鍵值，以及產生索引鍵的每個值的項目數目的計數。</span><span class="sxs-lookup"><span data-stu-id="cb995-222">`Seq.countBy` then returns a sequence that contains the key values, and a count of the number of elements that generated each value of the key.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet201.fs)]

<span data-ttu-id="cb995-223">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="cb995-223">The output is as follows.</span></span>

```
(1, 34) (2, 33) (0, 33)
```

<span data-ttu-id="cb995-224">上述輸出會顯示已 34 的項目所產生的索引鍵為 1，將原始序列所產生的索引鍵 2 的 33 值和 33 所產生的索引鍵 0 的值。</span><span class="sxs-lookup"><span data-stu-id="cb995-224">The previous output shows that there were 34 elements of the original sequence that produced the key 1, 33 values that produced the key 2, and 33 values that produced the key 0.</span></span>

<span data-ttu-id="cb995-225">您可以藉由呼叫來群組序列的項目[Seq.groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd)。</span><span class="sxs-lookup"><span data-stu-id="cb995-225">You can group elements of a sequence by calling [Seq.groupBy](https://msdn.microsoft.com/library/d46a04df-1a42-40cc-a368-058c9c5806fd).</span></span> <span data-ttu-id="cb995-226">`Seq.groupBy` 會將序列和函式會產生金鑰的項目。</span><span class="sxs-lookup"><span data-stu-id="cb995-226">`Seq.groupBy` takes a sequence and a function that generates a key from an element.</span></span> <span data-ttu-id="cb995-227">此函式順序的每個項目上執行。</span><span class="sxs-lookup"><span data-stu-id="cb995-227">The function is executed on each element of the sequence.</span></span> <span data-ttu-id="cb995-228">`Seq.groupBy` 傳回序列的 tuple，其中每個 tuple 的第一個元素是機碼，而第二個是一串產生該索引鍵的項目。</span><span class="sxs-lookup"><span data-stu-id="cb995-228">`Seq.groupBy` returns a sequence of tuples, where the first element of each tuple is the key and the second is a sequence of elements that produce that key.</span></span>

<span data-ttu-id="cb995-229">下列程式碼範例示範使用`Seq.groupBy`分割成三個群組具有相異索引鍵的值 0、 1 和 2 從 1 到 100 之間的數字的序列。</span><span class="sxs-lookup"><span data-stu-id="cb995-229">The following code example shows the use of `Seq.groupBy` to partition the sequence of numbers from 1 to 100 into three groups that have the distinct key values 0, 1, and 2.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet202.fs)]

<span data-ttu-id="cb995-230">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="cb995-230">The output is as follows.</span></span>

```
(1, seq [1; 4; 7; 10; ...]) (2, seq [2; 5; 8; 11; ...]) (0, seq [3; 6; 9; 12; ...])
```

<span data-ttu-id="cb995-231">您可以建立一連串以消除重複的項目，藉由呼叫[Seq.distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401)。</span><span class="sxs-lookup"><span data-stu-id="cb995-231">You can create a sequence that eliminates duplicate elements by calling [Seq.distinct](https://msdn.microsoft.com/library/99d01014-7e0e-4e7b-9d0a-41a61d93f401).</span></span> <span data-ttu-id="cb995-232">您可以使用或者[Seq.distinctBy](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75)，其採用索引鍵產生函式呼叫的每個項目。</span><span class="sxs-lookup"><span data-stu-id="cb995-232">Or you can use [Seq.distinctBy](https://msdn.microsoft.com/library/9293293b-9420-49c8-848f-401a9cd49b75), which takes a key-generating function to be called on each element.</span></span> <span data-ttu-id="cb995-233">產生的序列包含具有唯一的索引鍵; 原始序列的項目更新產生的較早的項目重複的索引鍵的項目都會被捨棄。</span><span class="sxs-lookup"><span data-stu-id="cb995-233">The resulting sequence contains elements of the original sequence that have unique keys; later elements that produce a duplicate key to an earlier element are discarded.</span></span>

<span data-ttu-id="cb995-234">下列程式碼範例說明使用`Seq.distinct`。</span><span class="sxs-lookup"><span data-stu-id="cb995-234">The following code example illustrates the use of `Seq.distinct`.</span></span> <span data-ttu-id="cb995-235">`Seq.distinct` 示範藉由產生代表二進位數字的順序，然後顯示 僅不同的項目為 0 和 1。</span><span class="sxs-lookup"><span data-stu-id="cb995-235">`Seq.distinct` is demonstrated by generating sequences that represent binary numbers, and then showing that the only distinct elements are 0 and 1.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet22.fs)]

<span data-ttu-id="cb995-236">下列程式碼示範`Seq.distinctBy`開頭包含負數和正數的序列，並為索引鍵產生函式使用絕對值函式。</span><span class="sxs-lookup"><span data-stu-id="cb995-236">The following code demonstrates `Seq.distinctBy` by starting with a sequence that contains negative and positive numbers and using the absolute value function as the key-generating function.</span></span> <span data-ttu-id="cb995-237">遺漏對應到在順序中，負數，因為負數稍早在序列中都會出現，而且因此而不是正數，具有相同的絕對選取所有正數所產生的順序。值或索引鍵。</span><span class="sxs-lookup"><span data-stu-id="cb995-237">The resulting sequence is missing all the positive numbers that correspond to the negative numbers in the sequence, because the negative numbers appear earlier in the sequence and therefore are selected instead of the positive numbers that have the same absolute value, or key.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet23.fs)]
    
## <a name="readonly-and-cached-sequences"></a><span data-ttu-id="cb995-238">在 Readonly 和快取的順序</span><span class="sxs-lookup"><span data-stu-id="cb995-238">Readonly and Cached Sequences</span></span>
<span data-ttu-id="cb995-239">[Seq.readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7)建立序列的唯讀複本。</span><span class="sxs-lookup"><span data-stu-id="cb995-239">[Seq.readonly](https://msdn.microsoft.com/library/88059cb4-3bb0-4126-9448-fbcd48fe13a7) creates a read-only copy of a sequence.</span></span> <span data-ttu-id="cb995-240">`Seq.readonly` 當您具有讀寫集合，例如陣列、 且不想修改原始集合，則會是很有用。</span><span class="sxs-lookup"><span data-stu-id="cb995-240">`Seq.readonly` is useful when you have a read-write collection, such as an array, and you do not want to modify the original collection.</span></span> <span data-ttu-id="cb995-241">此函式可以用來保留資料的封裝。</span><span class="sxs-lookup"><span data-stu-id="cb995-241">This function can be used to preserve data encapsulation.</span></span> <span data-ttu-id="cb995-242">在下列程式碼範例中，會建立包含陣列的類型。</span><span class="sxs-lookup"><span data-stu-id="cb995-242">In the following code example, a type that contains an array is created.</span></span> <span data-ttu-id="cb995-243">屬性會公開的陣列，但是它會使用建立陣列中的順序傳回而不是傳回陣列， `Seq.readonly`。</span><span class="sxs-lookup"><span data-stu-id="cb995-243">A property exposes the array, but instead of returning an array, it returns a sequence that is created from the array by using `Seq.readonly`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/fssequences/snippet24.fs)]

<span data-ttu-id="cb995-244">[Seq.cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0)建立序列的儲存的版本。</span><span class="sxs-lookup"><span data-stu-id="cb995-244">[Seq.cache](https://msdn.microsoft.com/library/d197f9cc-08bf-4986-9869-246e72ca73f0) creates a stored version of a sequence.</span></span> <span data-ttu-id="cb995-245">使用`Seq.cache`以避免重新評估的順序，或當您使用順序的多個執行緒，但您必須確定每個項目會處理一次。</span><span class="sxs-lookup"><span data-stu-id="cb995-245">Use `Seq.cache` to avoid reevaluation of a sequence, or when you have multiple threads that use a sequence, but you must make sure that each element is acted upon only one time.</span></span> <span data-ttu-id="cb995-246">若您正在使用多個執行緒的順序，您可以擁有的列舉，並計算的值將原始序列中，執行緒，而且其餘的執行緒可以使用快取的順序。</span><span class="sxs-lookup"><span data-stu-id="cb995-246">When you have a sequence that is being used by multiple threads, you can have one thread that enumerates and computes the values for the original sequence, and remaining threads can use the cached sequence.</span></span>


## <a name="performing-computations-on-sequences"></a><span data-ttu-id="cb995-247">序列上執行計算</span><span class="sxs-lookup"><span data-stu-id="cb995-247">Performing Computations on Sequences</span></span>
<span data-ttu-id="cb995-248">簡單的算術運算是類似的清單，例如[Seq.average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8)， [Seq.sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a)， [Seq.averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8)， [Seq.sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1)，依此類推。</span><span class="sxs-lookup"><span data-stu-id="cb995-248">Simple arithmetic operations are like those of lists, such as [Seq.average](https://msdn.microsoft.com/library/609d793b-c70f-4e36-9ab4-d928056d65b8), [Seq.sum](https://msdn.microsoft.com/library/01208515-4880-4358-91f5-af34f66dc77a), [Seq.averageBy](https://msdn.microsoft.com/library/47c855c1-2dbd-415a-885e-b909d9d3e4f8), [Seq.sumBy](https://msdn.microsoft.com/library/68cca78c-94ed-4a45-9b8d-34d2c5f2b1b1), and so on.</span></span>

<span data-ttu-id="cb995-249">[Seq.fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3)， [Seq.reduce](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9)，和[Seq.scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e)都和對應函式可用於清單一樣。</span><span class="sxs-lookup"><span data-stu-id="cb995-249">[Seq.fold](https://msdn.microsoft.com/library/30c4c95a-9563-4c96-bbe1-f7aacfd026e3), [Seq.reduce](https://msdn.microsoft.com/library/a2ad4f64-ac69-47d2-92f0-7173d9dfeae9), and [Seq.scan](https://msdn.microsoft.com/library/7e2d23e9-f153-4411-a884-b6d415ff627e) are like the corresponding functions that are available for lists.</span></span> <span data-ttu-id="cb995-250">時序支援列出支援這些函式的完整變化的子集。</span><span class="sxs-lookup"><span data-stu-id="cb995-250">Sequences support a subset of the full variations of these functions that lists support.</span></span> <span data-ttu-id="cb995-251">如需詳細資訊和範例，請參閱[列出](lists.md)。</span><span class="sxs-lookup"><span data-stu-id="cb995-251">For more information and examples, see [Lists](lists.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cb995-252">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb995-252">See Also</span></span>
[<span data-ttu-id="cb995-253">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="cb995-253">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="cb995-254">F# 類型</span><span class="sxs-lookup"><span data-stu-id="cb995-254">F# Types</span></span>](fsharp-types.md)
