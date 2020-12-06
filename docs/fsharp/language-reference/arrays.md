---
title: 陣列
description: '瞭解如何以 F # 程式設計語言建立和使用陣列。'
ms.date: 08/13/2020
ms.openlocfilehash: 96b0d7eaf10d5afcd9a647681d5c2ef2d2fba335
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/05/2020
ms.locfileid: "96739747"
---
# <a name="arrays"></a><span data-ttu-id="c349a-103">陣列</span><span class="sxs-lookup"><span data-stu-id="c349a-103">Arrays</span></span>

<span data-ttu-id="c349a-104">陣列是固定大小、以零為基礎且可變動的連續資料元素集合，這些專案全都屬於相同類型。</span><span class="sxs-lookup"><span data-stu-id="c349a-104">Arrays are fixed-size, zero-based, mutable collections of consecutive data elements that are all of the same type.</span></span>

## <a name="create-arrays"></a><span data-ttu-id="c349a-105">建立陣列</span><span class="sxs-lookup"><span data-stu-id="c349a-105">Create arrays</span></span>

<span data-ttu-id="c349a-106">您可以用數種方式建立陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-106">You can create arrays in several ways.</span></span> <span data-ttu-id="c349a-107">您可以藉由列出介於和之間的連續值 `[|` `|]` ，並以分號分隔來建立小型陣列，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c349a-107">You can create a small array by listing consecutive values between `[|` and `|]` and separated by semicolons, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet1.fs)]

<span data-ttu-id="c349a-108">您也可以將每個專案放在個別的行上，在這種情況下，分號分隔符號是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="c349a-108">You can also put each element on a separate line, in which case the semicolon separator is optional.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet2.fs)]

<span data-ttu-id="c349a-109">陣列元素的型別是從使用的常值推斷而來，而且必須是一致的。</span><span class="sxs-lookup"><span data-stu-id="c349a-109">The type of the array elements is inferred from the literals used and must be consistent.</span></span> <span data-ttu-id="c349a-110">下列程式碼會造成錯誤，因為1.0 是 float，而2和3是整數。</span><span class="sxs-lookup"><span data-stu-id="c349a-110">The following code causes an error because 1.0 is a float and 2 and 3 are integers.</span></span>

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

<span data-ttu-id="c349a-111">您也可以使用順序運算式來建立陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-111">You can also use sequence expressions to create arrays.</span></span> <span data-ttu-id="c349a-112">以下範例會建立從1到10的整數平方陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-112">Following is an example that creates an array of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet3.fs)]

<span data-ttu-id="c349a-113">若要建立陣列，其中所有元素都會初始化為零，請使用 `Array.zeroCreate` 。</span><span class="sxs-lookup"><span data-stu-id="c349a-113">To create an array in which all the elements are initialized to zero, use `Array.zeroCreate`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="access-elements"></a><span data-ttu-id="c349a-114">存取元素</span><span class="sxs-lookup"><span data-stu-id="c349a-114">Access elements</span></span>

<span data-ttu-id="c349a-115">您可以使用點運算子來存取陣列元素 (`.`) 和方括弧 (`[` 和 `]`) 。</span><span class="sxs-lookup"><span data-stu-id="c349a-115">You can access array elements by using a dot operator (`.`) and brackets (`[` and `]`).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet5.fs)]

<span data-ttu-id="c349a-116">陣列索引從0開始。</span><span class="sxs-lookup"><span data-stu-id="c349a-116">Array indexes start at 0.</span></span>

<span data-ttu-id="c349a-117">您也可以使用配量標記法來存取陣列元素，這可讓您指定陣列的子範圍。</span><span class="sxs-lookup"><span data-stu-id="c349a-117">You can also access array elements by using slice notation, which enables you to specify a subrange of the array.</span></span> <span data-ttu-id="c349a-118">配量標記法的範例如下。</span><span class="sxs-lookup"><span data-stu-id="c349a-118">Examples of slice notation follow.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet51.fs)]

<span data-ttu-id="c349a-119">使用配量標記法時，會建立陣列的新複本。</span><span class="sxs-lookup"><span data-stu-id="c349a-119">When slice notation is used, a new copy of the array is created.</span></span>

## <a name="array-types-and-modules"></a><span data-ttu-id="c349a-120">陣列類型和模組</span><span class="sxs-lookup"><span data-stu-id="c349a-120">Array types and modules</span></span>

<span data-ttu-id="c349a-121">所有 F # 陣列的型別都是 .NET Framework 型別 <xref:System.Array?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="c349a-121">The type of all F# arrays is the .NET Framework type <xref:System.Array?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c349a-122">因此，F # 陣列支援中所有可用的功能 <xref:System.Array?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="c349a-122">Therefore, F# arrays support all the functionality available in <xref:System.Array?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="c349a-123">此[ `Array` 模組](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html)支援一維陣列上的作業。</span><span class="sxs-lookup"><span data-stu-id="c349a-123">The [`Array` module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html) supports operations on one-dimensional arrays.</span></span> <span data-ttu-id="c349a-124">模組 `Array2D` 、 `Array3D` 和包含的函式 `Array4D` 分別支援兩個、三個和四個維度的陣列作業。</span><span class="sxs-lookup"><span data-stu-id="c349a-124">The modules `Array2D`, `Array3D`, and `Array4D` contain functions that support operations on arrays of two, three, and four dimensions, respectively.</span></span> <span data-ttu-id="c349a-125">您可以使用來建立順位大於四的陣列 <xref:System.Array?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="c349a-125">You can create arrays of rank greater than four by using <xref:System.Array?displayProperty=nameWithType>.</span></span>

### <a name="simple-functions"></a><span data-ttu-id="c349a-126">簡單函數</span><span class="sxs-lookup"><span data-stu-id="c349a-126">Simple functions</span></span>

<span data-ttu-id="c349a-127">[`Array.get`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#get) 取得專案。</span><span class="sxs-lookup"><span data-stu-id="c349a-127">[`Array.get`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#get) gets an element.</span></span> <span data-ttu-id="c349a-128">[`Array.length`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#length) 提供陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="c349a-128">[`Array.length`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#length) gives the length of an array.</span></span> <span data-ttu-id="c349a-129">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) 將元素設定為指定的值。</span><span class="sxs-lookup"><span data-stu-id="c349a-129">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) sets an element to a specified value.</span></span> <span data-ttu-id="c349a-130">下列程式碼範例說明這些函數的用法。</span><span class="sxs-lookup"><span data-stu-id="c349a-130">The following code example illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet9.fs)]

<span data-ttu-id="c349a-131">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="c349a-131">The output is as follows.</span></span>

```console
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a><span data-ttu-id="c349a-132">建立陣列的函式</span><span class="sxs-lookup"><span data-stu-id="c349a-132">Functions that create arrays</span></span>

<span data-ttu-id="c349a-133">有幾個函式會建立陣列，而不需要現有的陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-133">Several functions create arrays without requiring an existing array.</span></span> <span data-ttu-id="c349a-134">[`Array.empty`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#empty) 建立不包含任何專案的新陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-134">[`Array.empty`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#empty) creates a new array that does not contain any elements.</span></span> <span data-ttu-id="c349a-135">[`Array.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#create) 建立指定大小的陣列，並將所有元素設定為提供的值。</span><span class="sxs-lookup"><span data-stu-id="c349a-135">[`Array.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#create) creates an array of a specified size and sets all the elements to provided values.</span></span> <span data-ttu-id="c349a-136">[`Array.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#init) 建立陣列，並指定維度和函式來產生元素。</span><span class="sxs-lookup"><span data-stu-id="c349a-136">[`Array.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#init) creates an array, given a dimension and a function to generate the elements.</span></span> <span data-ttu-id="c349a-137">[`Array.zeroCreate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate) 建立陣列，其中所有元素都會初始化為數組類型的零值。</span><span class="sxs-lookup"><span data-stu-id="c349a-137">[`Array.zeroCreate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate) creates an array in which all the elements are initialized to the zero value for the array's type.</span></span> <span data-ttu-id="c349a-138">下列程式碼示範這些函數。</span><span class="sxs-lookup"><span data-stu-id="c349a-138">The following code demonstrates these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet91.fs)]

<span data-ttu-id="c349a-139">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="c349a-139">The output is as follows.</span></span>

```console
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

<span data-ttu-id="c349a-140">[`Array.copy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#copy) 建立新的陣列，其中包含從現有陣列複製的元素。</span><span class="sxs-lookup"><span data-stu-id="c349a-140">[`Array.copy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#copy) creates a new array that contains elements that are copied from an existing array.</span></span> <span data-ttu-id="c349a-141">請注意，複製是淺層複製，這表示如果元素類型是參考型別，則只會複製參考，而不會複製基礎物件。</span><span class="sxs-lookup"><span data-stu-id="c349a-141">Note that the copy is a shallow copy, which means that if the element type is a reference type, only the reference is copied, not the underlying object.</span></span> <span data-ttu-id="c349a-142">下列程式碼範例會說明這點。</span><span class="sxs-lookup"><span data-stu-id="c349a-142">The following code example illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet11.fs)]

<span data-ttu-id="c349a-143">上述程式碼的輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="c349a-143">The output of the preceding code is as follows:</span></span>

```console
[|Test1; Test2; |]
[|; Test2; |]
```

<span data-ttu-id="c349a-144">字串 `Test1` 只會出現在第一個陣列中，因為建立新專案的作業會覆寫中的參考， `firstArray` 但不會影響仍然存在於中之空字串的原始參考 `secondArray` 。</span><span class="sxs-lookup"><span data-stu-id="c349a-144">The string `Test1` appears only in the first array because the operation of creating a new element overwrites the reference in `firstArray` but does not affect the original reference to an empty string that is still present in `secondArray`.</span></span> <span data-ttu-id="c349a-145">字串 `Test2` 會出現在這兩個數組中 `Insert` ，因為類型上的作業 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 會影響在 <xref:System.Text.StringBuilder?displayProperty=nameWithType> 這兩個數組中所參考的基礎物件。</span><span class="sxs-lookup"><span data-stu-id="c349a-145">The string `Test2` appears in both arrays because the `Insert` operation on the <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affects the underlying <xref:System.Text.StringBuilder?displayProperty=nameWithType> object, which is referenced in both arrays.</span></span>

<span data-ttu-id="c349a-146">[`Array.sub`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sub) 從陣列的子範圍產生新的陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-146">[`Array.sub`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sub) generates a new array from a subrange of an array.</span></span> <span data-ttu-id="c349a-147">您可以藉由提供開始索引和長度來指定子範圍。</span><span class="sxs-lookup"><span data-stu-id="c349a-147">You specify the subrange by providing the starting index and the length.</span></span> <span data-ttu-id="c349a-148">下列程式碼示範 `Array.sub` 的用法。</span><span class="sxs-lookup"><span data-stu-id="c349a-148">The following code demonstrates the use of `Array.sub`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet12.fs)]

<span data-ttu-id="c349a-149">輸出顯示子陣列在元素5開始，且包含10個元素。</span><span class="sxs-lookup"><span data-stu-id="c349a-149">The output shows that the subarray starts at element 5 and contains 10 elements.</span></span>

```console
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

<span data-ttu-id="c349a-150">[`Array.append`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#append) 藉由結合兩個現有的陣列，建立新的陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-150">[`Array.append`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#append) creates a new array by combining two existing arrays.</span></span>

<span data-ttu-id="c349a-151">下列程式碼示範 **陣列. append**。</span><span class="sxs-lookup"><span data-stu-id="c349a-151">The following code demonstrates **Array.append**.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet13.fs)]

<span data-ttu-id="c349a-152">上述程式碼的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="c349a-152">The output of the preceding code is as follows.</span></span>

```console
[|1; 2; 3; 4; 5; 6|]
```

<span data-ttu-id="c349a-153">[`Array.choose`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#choose) 選取要包含在新陣列中的陣列元素。</span><span class="sxs-lookup"><span data-stu-id="c349a-153">[`Array.choose`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#choose) selects elements of an array to include in a new array.</span></span> <span data-ttu-id="c349a-154">下列程式碼示範 `Array.choose` 。</span><span class="sxs-lookup"><span data-stu-id="c349a-154">The following code demonstrates `Array.choose`.</span></span> <span data-ttu-id="c349a-155">請注意，陣列的元素類型不需要符合選項類型中所傳回值的類型。</span><span class="sxs-lookup"><span data-stu-id="c349a-155">Note that the element type of the array does not have to match the type of the value returned in the option type.</span></span> <span data-ttu-id="c349a-156">在此範例中，元素類型為， `int` 而選項是多項式函式的結果， `elem*elem - 1` 做為浮點數。</span><span class="sxs-lookup"><span data-stu-id="c349a-156">In this example, the element type is `int` and the option is the result of a polynomial function, `elem*elem - 1`, as a floating point number.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet14.fs)]

<span data-ttu-id="c349a-157">上述程式碼的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="c349a-157">The output of the preceding code is as follows.</span></span>

```console
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

<span data-ttu-id="c349a-158">[`Array.collect`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#collect) 在現有陣列的每個陣列元素上執行指定的函式，然後收集函式所產生的元素，並將它們合併成新的陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-158">[`Array.collect`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#collect) runs a specified function on each array element of an existing array and then collects the elements generated by the function and combines them into a new array.</span></span> <span data-ttu-id="c349a-159">下列程式碼示範 `Array.collect` 。</span><span class="sxs-lookup"><span data-stu-id="c349a-159">The following code demonstrates `Array.collect`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet15.fs)]

<span data-ttu-id="c349a-160">上述程式碼的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="c349a-160">The output of the preceding code is as follows.</span></span>

```console
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

<span data-ttu-id="c349a-161">[`Array.concat`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#concat) 接受一連串的陣列，並將它們結合成單一陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-161">[`Array.concat`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#concat) takes a sequence of arrays and combines them into a single array.</span></span> <span data-ttu-id="c349a-162">下列程式碼示範 `Array.concat` 。</span><span class="sxs-lookup"><span data-stu-id="c349a-162">The following code demonstrates `Array.concat`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet16.fs)]

<span data-ttu-id="c349a-163">上述程式碼的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="c349a-163">The output of the preceding code is as follows.</span></span>

```console
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

<span data-ttu-id="c349a-164">[`Array.filter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#filter) 採用布林條件函式，並產生新的陣列，其中只包含輸入陣列中條件為 true 的元素。</span><span class="sxs-lookup"><span data-stu-id="c349a-164">[`Array.filter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#filter) takes a Boolean condition function and generates a new array that contains only those elements from the input array for which the condition is true.</span></span> <span data-ttu-id="c349a-165">下列程式碼示範 `Array.filter` 。</span><span class="sxs-lookup"><span data-stu-id="c349a-165">The following code demonstrates `Array.filter`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet17.fs)]

<span data-ttu-id="c349a-166">上述程式碼的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="c349a-166">The output of the preceding code is as follows.</span></span>

```console
[|2; 4; 6; 8; 10|]
```

<span data-ttu-id="c349a-167">[`Array.rev`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#rev) 藉由反轉現有陣列的順序來產生新的陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-167">[`Array.rev`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#rev) generates a new array by reversing the order of an existing array.</span></span> <span data-ttu-id="c349a-168">下列程式碼示範 `Array.rev` 。</span><span class="sxs-lookup"><span data-stu-id="c349a-168">The following code demonstrates `Array.rev`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet18.fs)]

<span data-ttu-id="c349a-169">上述程式碼的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="c349a-169">The output of the preceding code is as follows.</span></span>

```console
"Hello world!"
```

<span data-ttu-id="c349a-170">您可以輕鬆地結合陣列模組中的函式，使用管線運算子 () 來轉換陣列 `|>` ，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="c349a-170">You can easily combine functions in the array module that transform arrays by using the pipeline operator (`|>`), as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet19.fs)]

<span data-ttu-id="c349a-171">輸出為</span><span class="sxs-lookup"><span data-stu-id="c349a-171">The output is</span></span>

```console
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a><span data-ttu-id="c349a-172">多維陣列</span><span class="sxs-lookup"><span data-stu-id="c349a-172">Multidimensional arrays</span></span>

<span data-ttu-id="c349a-173">您可以建立多維度陣列，但是沒有寫入多維陣列常值的語法。</span><span class="sxs-lookup"><span data-stu-id="c349a-173">A multidimensional array can be created, but there is no syntax for writing a multidimensional array literal.</span></span> <span data-ttu-id="c349a-174">使用運算子 [`array2D`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html) ，從陣列元素序列的序列中建立陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-174">Use the operator [`array2D`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html) to create an array from a sequence of sequences of array elements.</span></span> <span data-ttu-id="c349a-175">序列可以是陣列或清單常值。</span><span class="sxs-lookup"><span data-stu-id="c349a-175">The sequences can be array or list literals.</span></span> <span data-ttu-id="c349a-176">例如，下列程式碼會建立二維陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-176">For example, the following code creates a two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet20.fs)]

<span data-ttu-id="c349a-177">您也可以使用函式 [`Array2D.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#init) 來初始化兩個維度的陣列，而類似的函式可用於三和四個維度的陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-177">You can also use the function [`Array2D.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#init) to initialize arrays of two dimensions, and similar functions are available for arrays of three and four dimensions.</span></span> <span data-ttu-id="c349a-178">這些函式會取得用來建立元素的函式。</span><span class="sxs-lookup"><span data-stu-id="c349a-178">These functions take a function that is used to create the elements.</span></span> <span data-ttu-id="c349a-179">若要建立包含設定為初始值之專案的二維陣列，而不是指定函式，請使用函式 [`Array2D.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#create) ，此函式也適用于最多四個維度的陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-179">To create a two-dimensional array that contains elements set to an initial value instead of specifying a function, use the [`Array2D.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#create) function, which is also available for arrays up to four dimensions.</span></span> <span data-ttu-id="c349a-180">下列程式碼範例會先示範如何建立包含所需元素的陣列陣列，然後使用 `Array2D.init` 來產生所需的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-180">The following code example first shows how to create an array of arrays that contain the desired elements, and then uses `Array2D.init` to generate the desired two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet21.fs)]

<span data-ttu-id="c349a-181">陣列索引和切割語法支援最高排名4的陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-181">Array indexing and slicing syntax is supported for arrays up to rank 4.</span></span> <span data-ttu-id="c349a-182">當您指定多個維度中的索引時，您可以使用逗號來分隔索引，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="c349a-182">When you specify an index in multiple dimensions, you use commas to separate the indexes, as illustrated in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet22.fs)]

<span data-ttu-id="c349a-183">二維陣列的型別會寫出做為 (例如， `<type>[,]` `int[,]` `double[,]`) ，而三維陣列的型別則是撰寫為 `<type>[,,]` ，依此類推，針對較高維度的陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-183">The type of a two-dimensional array is written out as `<type>[,]` (for example, `int[,]`, `double[,]`), and the type of a three-dimensional array is written as `<type>[,,]`, and so on for arrays of higher dimensions.</span></span>

<span data-ttu-id="c349a-184">只有一維陣列的可用函式子集也適用于多維度陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-184">Only a subset of the functions available for one-dimensional arrays is also available for multidimensional arrays.</span></span>

### <a name="array-slicing-and-multidimensional-arrays"></a><span data-ttu-id="c349a-185">陣列切割和多維陣列</span><span class="sxs-lookup"><span data-stu-id="c349a-185">Array slicing and multidimensional arrays</span></span>

<span data-ttu-id="c349a-186">在二維陣列 (矩陣) 中，您可以指定範圍，並使用萬用字元 (`*`) 字元來指定整個資料列或資料行，藉以解壓縮子矩陣。</span><span class="sxs-lookup"><span data-stu-id="c349a-186">In a two-dimensional array (a matrix), you can extract a sub-matrix by specifying ranges and using a wildcard (`*`) character to specify whole rows or columns.</span></span>

```fsharp
// Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

<span data-ttu-id="c349a-187">您可以將多維陣列分解成相同或較低維度的 subarrays。</span><span class="sxs-lookup"><span data-stu-id="c349a-187">You can decompose a multidimensional array into subarrays of the same or lower dimension.</span></span> <span data-ttu-id="c349a-188">例如，您可以藉由指定單一資料列或資料行，從矩陣取得向量。</span><span class="sxs-lookup"><span data-stu-id="c349a-188">For example, you can obtain a vector from a matrix by specifying a single row or column.</span></span>

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

<span data-ttu-id="c349a-189">您可以針對實際引數素存取運算子和多載方法的型別使用此切割語法 `GetSlice` 。</span><span class="sxs-lookup"><span data-stu-id="c349a-189">You can use this slicing syntax for types that implement the element access operators and overloaded `GetSlice` methods.</span></span> <span data-ttu-id="c349a-190">例如，下列程式碼會建立包裝 F # 2D 陣列的矩陣類型、執行專案屬性以提供陣列索引編制的支援，以及執行三個版本的 `GetSlice` 。</span><span class="sxs-lookup"><span data-stu-id="c349a-190">For example, the following code creates a Matrix type that wraps the F# 2D array, implements an Item property to provide support for array indexing, and implements three versions of `GetSlice`.</span></span> <span data-ttu-id="c349a-191">如果您可以使用此程式碼作為矩陣類型的範本，您可以使用本節描述的所有配量作業。</span><span class="sxs-lookup"><span data-stu-id="c349a-191">If you can use this code as a template for your matrix types, you can use all the slicing operations that this section describes.</span></span>

```fsharp
type Matrix<'T>(N: int, M: int) =
    let internalArray = Array2D.zeroCreate<'T> N M

    member this.Item
        with get(a: int, b: int) = internalArray.[a, b]
        and set(a: int, b: int) (value:'T) = internalArray.[a, b] <- value

    member this.GetSlice(rowStart: int option, rowFinish : int option, colStart: int option, colFinish : int option) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[rowStart..rowFinish, colStart..colFinish]

    member this.GetSlice(row: int, colStart: int option, colFinish: int option) =
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[row, colStart..colFinish]

    member this.GetSlice(rowStart: int option, rowFinish: int option, col: int) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        internalArray.[rowStart..rowFinish, col]

module test =
    let generateTestMatrix x y =
        let matrix = new Matrix<float>(3, 3)
        for i in 0..2 do
            for j in 0..2 do
                matrix.[i, j] <- float(i) * x - float(j) * y
        matrix

    let test1 = generateTestMatrix 2.3 1.1
    let submatrix = test1.[0..1, 0..1]
    printfn $"{submatrix}"

    let firstRow = test1.[0,*]
    let secondRow = test1.[1,*]
    let firstCol = test1.[*,0]
    printfn $"{firstCol}"
```

### <a name="boolean-functions-on-arrays"></a><span data-ttu-id="c349a-192">陣列上的布耳函數</span><span class="sxs-lookup"><span data-stu-id="c349a-192">Boolean functions on arrays</span></span>

<span data-ttu-id="c349a-193">[`Array.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists) [`Array.exists2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists2) 一或兩個數組中的函式和測試專案，分別為。</span><span class="sxs-lookup"><span data-stu-id="c349a-193">The functions [`Array.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists) and [`Array.exists2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists2) test elements in either one or two arrays, respectively.</span></span> <span data-ttu-id="c349a-194">`true`如果符合條件的) 有元素 (或元素組，則這些函式會採用測試函式，並傳回 `Array.exists2` 。</span><span class="sxs-lookup"><span data-stu-id="c349a-194">These functions take a test function and return `true` if there is an element (or element pair for `Array.exists2`) that satisfies the condition.</span></span>

<span data-ttu-id="c349a-195">下列程式碼示範如何使用 `Array.exists` 和 `Array.exists2` 。</span><span class="sxs-lookup"><span data-stu-id="c349a-195">The following code demonstrates the use of `Array.exists` and `Array.exists2`.</span></span> <span data-ttu-id="c349a-196">在這些範例中，會藉由只套用其中一個引數（在這些情況下為函式引數）來建立新的函式。</span><span class="sxs-lookup"><span data-stu-id="c349a-196">In these examples, new functions are created by applying only one of the arguments, in these cases, the function argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet23.fs)]

<span data-ttu-id="c349a-197">上述程式碼的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="c349a-197">The output of the preceding code is as follows.</span></span>

```console
true
false
false
true
```

<span data-ttu-id="c349a-198">同樣地，函 [`Array.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall) 式會測試陣列，以判斷每個專案是否符合布林值條件。</span><span class="sxs-lookup"><span data-stu-id="c349a-198">Similarly, the function [`Array.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall) tests an array to determine whether every element satisfies a Boolean condition.</span></span> <span data-ttu-id="c349a-199">變異 [`Array.forall2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall2) 會使用布耳函數來執行相同的動作，此函式牽涉到兩個相等長度陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="c349a-199">The variation [`Array.forall2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall2) does the same thing by using a Boolean function that involves elements of two arrays of equal length.</span></span> <span data-ttu-id="c349a-200">下列程式碼說明如何使用這些函數。</span><span class="sxs-lookup"><span data-stu-id="c349a-200">The following code illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet24.fs)]

<span data-ttu-id="c349a-201">這些範例的輸出如下所示。</span><span class="sxs-lookup"><span data-stu-id="c349a-201">The output for these examples is as follows.</span></span>

```console
false
true
true
false
```

### <a name="search-arrays"></a><span data-ttu-id="c349a-202">搜尋陣列</span><span class="sxs-lookup"><span data-stu-id="c349a-202">Search arrays</span></span>

<span data-ttu-id="c349a-203">[`Array.find`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#find) 採用布林函式，並傳回函式傳回的第一個專案 `true` ， <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> 如果找不到符合條件的專案，則會引發。</span><span class="sxs-lookup"><span data-stu-id="c349a-203">[`Array.find`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#find) takes a Boolean function and returns the first element for which the function returns `true`, or raises a <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> if no element that satisfies the condition is found.</span></span> <span data-ttu-id="c349a-204">[`Array.findIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#findIndex) 類似，不同的是它會傳回專案的 `Array.find` 索引，而不是元素本身。</span><span class="sxs-lookup"><span data-stu-id="c349a-204">[`Array.findIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#findIndex) is like `Array.find`, except that it returns the index of the element instead of the element itself.</span></span>

<span data-ttu-id="c349a-205">下列 `Array.find` 程式碼會使用和 `Array.findIndex` 來找出同時為完美方形和完美 cube 的數位。</span><span class="sxs-lookup"><span data-stu-id="c349a-205">The following code uses `Array.find` and `Array.findIndex` to locate a number that is both a perfect square and perfect cube.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet25.fs)]

<span data-ttu-id="c349a-206">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="c349a-206">The output is as follows.</span></span>

```console
The first element that is both a square and a cube is 64 and its index is 62.
```

<span data-ttu-id="c349a-207">[`Array.tryFind`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFind) 類似 `Array.find` ，不同之處在于它的結果是選項類型， `None` 如果找不到任何元素，則會傳回。</span><span class="sxs-lookup"><span data-stu-id="c349a-207">[`Array.tryFind`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFind) is like `Array.find`, except that its result is an option type, and it returns `None` if no element is found.</span></span> <span data-ttu-id="c349a-208">`Array.tryFind``Array.find`如果您不知道相符的專案是否在陣列中，則應該使用而不是。</span><span class="sxs-lookup"><span data-stu-id="c349a-208">`Array.tryFind` should be used instead of `Array.find` when you do not know whether a matching element is in the array.</span></span> <span data-ttu-id="c349a-209">同樣地，它 [`Array.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFindIndex) 也是一樣， `Array.findIndex` 但選項類型是傳回值。</span><span class="sxs-lookup"><span data-stu-id="c349a-209">Similarly, [`Array.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFindIndex) is like `Array.findIndex` except that the option type is the return value.</span></span> <span data-ttu-id="c349a-210">如果找不到任何元素，則選項為 `None` 。</span><span class="sxs-lookup"><span data-stu-id="c349a-210">If no element is found, the option is `None`.</span></span>

<span data-ttu-id="c349a-211">下列程式碼示範 `Array.tryFind` 的用法。</span><span class="sxs-lookup"><span data-stu-id="c349a-211">The following code demonstrates the use of `Array.tryFind`.</span></span> <span data-ttu-id="c349a-212">此程式碼相依于先前的程式碼。</span><span class="sxs-lookup"><span data-stu-id="c349a-212">This code depends on the previous code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet26.fs)]

<span data-ttu-id="c349a-213">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="c349a-213">The output is as follows.</span></span>

```console
Found an element: 1
Found an element: 729
Failed to find a matching element.
```

<span data-ttu-id="c349a-214">[`Array.tryPick`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryPick)當您需要轉換元素，並加以尋找時，請使用。</span><span class="sxs-lookup"><span data-stu-id="c349a-214">Use [`Array.tryPick`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryPick) when you need to transform an element in addition to finding it.</span></span> <span data-ttu-id="c349a-215">結果為函式傳回已轉換元素做為選項值的第一個專案， `None` 如果找不到這類元素，則為。</span><span class="sxs-lookup"><span data-stu-id="c349a-215">The result is the first element for which the function returns the transformed element as an option value, or `None` if no such element is found.</span></span>

<span data-ttu-id="c349a-216">下列程式碼示範 `Array.tryPick` 的用法。</span><span class="sxs-lookup"><span data-stu-id="c349a-216">The following code shows the use of `Array.tryPick`.</span></span> <span data-ttu-id="c349a-217">在此情況下，不會使用 lambda 運算式，而是定義數個本機 helper 函數來簡化程式碼。</span><span class="sxs-lookup"><span data-stu-id="c349a-217">In this case, instead of a lambda expression, several local helper functions are defined to simplify the code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet27.fs)]

<span data-ttu-id="c349a-218">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="c349a-218">The output is as follows.</span></span>

```console
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
Did not find an element that is both a perfect square and a perfect cube.
```

### <a name="perform-computations-on-arrays"></a><span data-ttu-id="c349a-219">在陣列上執行計算</span><span class="sxs-lookup"><span data-stu-id="c349a-219">Perform computations on arrays</span></span>

<span data-ttu-id="c349a-220">函數會傳回 [`Array.average`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#average) 陣列中每個元素的平均值。</span><span class="sxs-lookup"><span data-stu-id="c349a-220">The [`Array.average`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#average) function returns the average of each element in an array.</span></span> <span data-ttu-id="c349a-221">它受限於支援整數除以整數的專案類型，其中包含浮點數類型，但不包括整數類資料類型。</span><span class="sxs-lookup"><span data-stu-id="c349a-221">It is limited to element types that support exact division by an integer, which includes floating point types but not integral types.</span></span> <span data-ttu-id="c349a-222">函數會傳回在 [`Array.averageBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#averageBy) 每個專案上呼叫函式的結果平均值。</span><span class="sxs-lookup"><span data-stu-id="c349a-222">The [`Array.averageBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#averageBy) function returns the average of the results of calling a function on each element.</span></span> <span data-ttu-id="c349a-223">若為整數類資料類型的陣列，您可以使用 `Array.averageBy` ，並讓函式將每個元素轉換成浮點數類型以進行計算。</span><span class="sxs-lookup"><span data-stu-id="c349a-223">For an array of integral type, you can use `Array.averageBy` and have the function convert each element to a floating point type for the computation.</span></span>

<span data-ttu-id="c349a-224">[`Array.max`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#max)如果專案 [`Array.min`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#min) 類型支援，請使用或來取得最大或最小元素。</span><span class="sxs-lookup"><span data-stu-id="c349a-224">Use [`Array.max`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#max) or [`Array.min`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#min) to get the maximum or minimum element, if the element type supports it.</span></span> <span data-ttu-id="c349a-225">同樣地，也可讓函式 [`Array.maxBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#maxBy) [`Array.minBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#minBy) 先執行，也許可以轉換成支援比較的型別。</span><span class="sxs-lookup"><span data-stu-id="c349a-225">Similarly, [`Array.maxBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#maxBy) and [`Array.minBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#minBy) allow a function to be executed first, perhaps to transform to a type that supports comparison.</span></span>

<span data-ttu-id="c349a-226">[`Array.sum`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sum) 加入陣列的元素，並 [`Array.sumBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sumBy) 在每個專案上呼叫函式，並將結果加在一起。</span><span class="sxs-lookup"><span data-stu-id="c349a-226">[`Array.sum`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sum) adds the elements of an array, and [`Array.sumBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sumBy) calls a function on each element and adds the results together.</span></span>

<span data-ttu-id="c349a-227">若要在陣列中的每個元素上執行函式，而不儲存傳回值，請使用 [`Array.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter) 。</span><span class="sxs-lookup"><span data-stu-id="c349a-227">To execute a function on each element in an array without storing the return values, use [`Array.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter).</span></span> <span data-ttu-id="c349a-228">若為涉及兩個相等長度陣列的函式，請使用 [`Array.iter2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter2) 。</span><span class="sxs-lookup"><span data-stu-id="c349a-228">For a function involving two arrays of equal length, use [`Array.iter2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter2).</span></span> <span data-ttu-id="c349a-229">如果您也需要保留函式結果的陣列，請使用 [`Array.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map) 或 [`Array.map2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map2) ，它會一次在兩個數組上運作。</span><span class="sxs-lookup"><span data-stu-id="c349a-229">If you also need to keep an array of the results of the function, use [`Array.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map) or [`Array.map2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map2), which operates on two arrays at a time.</span></span>

<span data-ttu-id="c349a-230">變數 [`Array.iteri`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri) 和可 [`Array.iteri2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri2) 讓元素的索引參與計算; 和相同的情況也是如此 [`Array.mapi`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi) [`Array.mapi2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi2) 。</span><span class="sxs-lookup"><span data-stu-id="c349a-230">The variations [`Array.iteri`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri) and [`Array.iteri2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri2) allow the index of the element to be involved in the computation; the same is true for [`Array.mapi`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi) and [`Array.mapi2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi2).</span></span>

<span data-ttu-id="c349a-231">[`Array.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold)包含陣列所有元素的函式、、、、 [`Array.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack) [`Array.reduce`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduce) [`Array.reduceBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduceBack) [`Array.scan`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scan) 和 [`Array.scanBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scanBack) 執行演算法。</span><span class="sxs-lookup"><span data-stu-id="c349a-231">The functions [`Array.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold), [`Array.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack), [`Array.reduce`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduce), [`Array.reduceBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduceBack), [`Array.scan`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scan), and [`Array.scanBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scanBack) execute algorithms that involve all the elements of an array.</span></span> <span data-ttu-id="c349a-232">同樣地，變化 [`Array.fold2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold2) 和 [`Array.foldBack2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack2) 在兩個數組上執行計算。</span><span class="sxs-lookup"><span data-stu-id="c349a-232">Similarly, the variations [`Array.fold2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold2) and [`Array.foldBack2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack2) perform computations on two arrays.</span></span>

<span data-ttu-id="c349a-233">這些執行計算的函式會對應到 [清單模組](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html)中相同名稱的函式。</span><span class="sxs-lookup"><span data-stu-id="c349a-233">These functions for performing computations correspond to the functions of the same name in the [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span> <span data-ttu-id="c349a-234">如需使用範例，請參閱 [清單](lists.md)。</span><span class="sxs-lookup"><span data-stu-id="c349a-234">For usage examples, see [Lists](lists.md).</span></span>

### <a name="modify-arrays"></a><span data-ttu-id="c349a-235">修改陣列</span><span class="sxs-lookup"><span data-stu-id="c349a-235">Modify arrays</span></span>

<span data-ttu-id="c349a-236">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) 將元素設定為指定的值。</span><span class="sxs-lookup"><span data-stu-id="c349a-236">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) sets an element to a specified value.</span></span> <span data-ttu-id="c349a-237">[`Array.fill`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fill) 將陣列中的元素範圍設定為指定的值。</span><span class="sxs-lookup"><span data-stu-id="c349a-237">[`Array.fill`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fill) sets a range of elements in an array to a specified value.</span></span> <span data-ttu-id="c349a-238">下列程式碼提供的範例 `Array.fill` 。</span><span class="sxs-lookup"><span data-stu-id="c349a-238">The following code provides an example of `Array.fill`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet28.fs)]

<span data-ttu-id="c349a-239">輸出如下。</span><span class="sxs-lookup"><span data-stu-id="c349a-239">The output is as follows.</span></span>

```console
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

<span data-ttu-id="c349a-240">您可以使用將 [`Array.blit`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#blit) 某個陣列的子區段複製到另一個陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-240">You can use [`Array.blit`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#blit) to copy a subsection of one array to another array.</span></span>

### <a name="convert-to-and-from-other-types"></a><span data-ttu-id="c349a-241">從其他類型轉換</span><span class="sxs-lookup"><span data-stu-id="c349a-241">Convert to and from other types</span></span>

<span data-ttu-id="c349a-242">[`Array.ofList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofList) 從清單建立陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-242">[`Array.ofList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofList) creates an array from a list.</span></span> <span data-ttu-id="c349a-243">[`Array.ofSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofSeq) 從序列建立陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-243">[`Array.ofSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofSeq) creates an array from a sequence.</span></span> <span data-ttu-id="c349a-244">[`Array.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toList) 並 [`Array.toSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toSeq) 從陣列型別轉換為這些其他集合類型。</span><span class="sxs-lookup"><span data-stu-id="c349a-244">[`Array.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toList) and [`Array.toSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toSeq) convert to these other collection types from the array type.</span></span>

### <a name="sort-arrays"></a><span data-ttu-id="c349a-245">排序陣列</span><span class="sxs-lookup"><span data-stu-id="c349a-245">Sort arrays</span></span>

<span data-ttu-id="c349a-246">使用 [`Array.sort`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sort) 來排序陣列，方法是使用泛型比較函數。</span><span class="sxs-lookup"><span data-stu-id="c349a-246">Use [`Array.sort`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sort) to sort an array by using the generic comparison function.</span></span> <span data-ttu-id="c349a-247">使用指定一個函式，此函式 [`Array.sortBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortBy) 會產生值（稱為索引 *鍵*），以在索引鍵上使用泛型比較函數進行排序。</span><span class="sxs-lookup"><span data-stu-id="c349a-247">Use [`Array.sortBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortBy) to specify a function that generates a value, referred to as a *key*, to sort by using the generic comparison function on the key.</span></span> <span data-ttu-id="c349a-248">[`Array.sortWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortWith)如果您想要提供自訂比較函數，請使用。</span><span class="sxs-lookup"><span data-stu-id="c349a-248">Use [`Array.sortWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortWith) if you want to provide a custom comparison function.</span></span> <span data-ttu-id="c349a-249">`Array.sort`、 `Array.sortBy` 和 `Array.sortWith` 全都會以新陣列的形式傳回已排序的陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-249">`Array.sort`, `Array.sortBy`, and `Array.sortWith` all return the sorted array as a new array.</span></span> <span data-ttu-id="c349a-250">變化 [`Array.sortInPlace`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlace) 、 [`Array.sortInPlaceBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceBy) 和會 [`Array.sortInPlaceWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceWith) 修改現有的陣列，而不是傳回新的陣列。</span><span class="sxs-lookup"><span data-stu-id="c349a-250">The variations [`Array.sortInPlace`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlace), [`Array.sortInPlaceBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceBy), and [`Array.sortInPlaceWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceWith) modify the existing array instead of returning a new one.</span></span>

### <a name="arrays-and-tuples"></a><span data-ttu-id="c349a-251">陣列和元組</span><span class="sxs-lookup"><span data-stu-id="c349a-251">Arrays and tuples</span></span>

<span data-ttu-id="c349a-252">函數 [`Array.zip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip) 和會 [`Array.unzip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip) 將元組的陣列轉換成陣列的元組，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="c349a-252">The functions [`Array.zip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip) and [`Array.unzip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip) convert arrays of tuple pairs to tuples of arrays and vice versa.</span></span> <span data-ttu-id="c349a-253">[`Array.zip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip3) 和 [`Array.unzip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip3) 很類似，不同之處在于它們會使用三個元素的元組或三個數組的元組。</span><span class="sxs-lookup"><span data-stu-id="c349a-253">[`Array.zip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip3) and [`Array.unzip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip3) are similar except that they work with tuples of three elements or tuples of three arrays.</span></span>

## <a name="parallel-computations-on-arrays"></a><span data-ttu-id="c349a-254">針對陣列進行平行計算</span><span class="sxs-lookup"><span data-stu-id="c349a-254">Parallel computations on arrays</span></span>

<span data-ttu-id="c349a-255">模組 [`Array.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule-parallel.html) 包含在陣列上執行平行計算的函數。</span><span class="sxs-lookup"><span data-stu-id="c349a-255">The module [`Array.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule-parallel.html) contains functions for performing parallel computations on arrays.</span></span> <span data-ttu-id="c349a-256">在版本4之前，以 .NET Framework 版本為目標的應用程式無法使用此模組。</span><span class="sxs-lookup"><span data-stu-id="c349a-256">This module is not available in applications that target versions of the .NET Framework prior to version 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="c349a-257">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c349a-257">See also</span></span>

- [<span data-ttu-id="c349a-258">F # 語言參考</span><span class="sxs-lookup"><span data-stu-id="c349a-258">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="c349a-259">F# 類型</span><span class="sxs-lookup"><span data-stu-id="c349a-259">F# Types</span></span>](fsharp-types.md)
