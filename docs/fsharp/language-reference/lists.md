---
title: 清單 (F#)
description: '深入了解 F # 清單、 排序、 不可變的數列相同型別的項目。'
ms.date: 05/16/2016
ms.openlocfilehash: ea86b3ca94c6414bf5ab60406452f3604838075a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33566624"
---
# <a name="lists"></a><span data-ttu-id="4da49-103">清單</span><span class="sxs-lookup"><span data-stu-id="4da49-103">Lists</span></span>

> [!NOTE]
<span data-ttu-id="4da49-104">本文中的 API 參考連結將帶您前往 MSDN。</span><span class="sxs-lookup"><span data-stu-id="4da49-104">The API reference links in this article will take you to MSDN.</span></span>  <span data-ttu-id="4da49-105">docs.microsoft.com API 參考不完整。</span><span class="sxs-lookup"><span data-stu-id="4da49-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="4da49-106">在 F# 中，list 是包含一系列經過排序且類型相同的固定元素。</span><span class="sxs-lookup"><span data-stu-id="4da49-106">A list in F# is an ordered, immutable series of elements of the same type.</span></span> <span data-ttu-id="4da49-107">若要執行 list 的基本運算，使用中的函式[List 模組](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)。</span><span class="sxs-lookup"><span data-stu-id="4da49-107">To perform basic operations on lists, use the functions in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>


## <a name="creating-and-initializing-lists"></a><span data-ttu-id="4da49-108">建立及初始化 list</span><span class="sxs-lookup"><span data-stu-id="4da49-108">Creating and Initializing Lists</span></span>
<span data-ttu-id="4da49-109">您可以藉由明確列出元素 (以逗號分隔並括以方括號) 來定義 list，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="4da49-109">You can define a list by explicitly listing out the elements, separated by semicolons and enclosed in square brackets, as shown in the following line of code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1301.fs)]

<span data-ttu-id="4da49-110">您也可以在元素之間加入分行符號；若您選擇加入分行符號，就不一定需要使用分號。</span><span class="sxs-lookup"><span data-stu-id="4da49-110">You can also put line breaks between elements, in which case the semicolons are optional.</span></span> <span data-ttu-id="4da49-111">當元素初始化運算式比較長，或當您想要為每個元素加入逗號時，以後一種語法編寫的程式碼會比較容易閱讀。</span><span class="sxs-lookup"><span data-stu-id="4da49-111">The latter syntax can result in more readable code when the element initialization expressions are longer, or when you want to include a comment for each element.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13011.fs)]

<span data-ttu-id="4da49-112">通常 list 的所有元素都應必須是同一類型。</span><span class="sxs-lookup"><span data-stu-id="4da49-112">Normally, all list elements must be the same type.</span></span> <span data-ttu-id="4da49-113">但當 list 指定的元素具有衍生類型的基底類型時，就不在此限。</span><span class="sxs-lookup"><span data-stu-id="4da49-113">An exception is that a list in which the elements are specified to be a base type can have elements that are derived types.</span></span> <span data-ttu-id="4da49-114">下列的 `Button` 與 `CheckBox` 因為都是從 `Control` 衍生而來，所以可接受。</span><span class="sxs-lookup"><span data-stu-id="4da49-114">Thus the following is acceptable, because both `Button` and `CheckBox` derive from `Control`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13012.fs)]

<span data-ttu-id="4da49-115">如下列程式碼所示，您也可以使用以整數指定的範圍 (以範圍運算子 `..` 分隔) 來定義 list 元素。</span><span class="sxs-lookup"><span data-stu-id="4da49-115">You can also define list elements by using a range indicated by integers separated by the range operator (`..`), as shown in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1302.fs)]

<span data-ttu-id="4da49-116">空 list 由不含任何內容的一對方括號指定。</span><span class="sxs-lookup"><span data-stu-id="4da49-116">An empty list is specified by a pair of square brackets with nothing in between them.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1304.fs)]

<span data-ttu-id="4da49-117">您也可以使用順序運算式建立 list。</span><span class="sxs-lookup"><span data-stu-id="4da49-117">You can also use a sequence expression to create a list.</span></span> <span data-ttu-id="4da49-118">請參閱[循序項運算式](sequences.md#sequence-expressions)如需詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="4da49-118">See [Sequence Expressions](sequences.md#sequence-expressions) for more information.</span></span> <span data-ttu-id="4da49-119">例如下列程式碼會建立從 1 到 10 之整數平方的 list。</span><span class="sxs-lookup"><span data-stu-id="4da49-119">For example, the following code creates a list of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1303.fs)]

## <a name="operators-for-working-with-lists"></a><span data-ttu-id="4da49-120">使用 list 的運算子</span><span class="sxs-lookup"><span data-stu-id="4da49-120">Operators for Working with Lists</span></span>
<span data-ttu-id="4da49-121">您可以使用 `::` (cons) 運算子。</span><span class="sxs-lookup"><span data-stu-id="4da49-121">You can attach elements to a list by using the `::` (cons) operator.</span></span> <span data-ttu-id="4da49-122">若 `list1` 為 `[2; 3; 4]`，下列程式碼將 `list2` 建立為 `[100; 2; 3; 4]`。</span><span class="sxs-lookup"><span data-stu-id="4da49-122">If `list1` is `[2; 3; 4]`, the following code creates `list2` as `[100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1305.fs)]

<span data-ttu-id="4da49-123">您可以使用 `@` 運算子串流具有相容類型的 list，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="4da49-123">You can concatenate lists that have compatible types by using the `@` operator, as in the following code.</span></span> <span data-ttu-id="4da49-124">當 `list1` 為 `[2; 3; 4]` 及 `list2` 為 `[100; 2; 3; 4 ]` 時，此程式碼會將 `list3` 建立為 `[2; 3; 4; 100; 2; 3; 4]`。</span><span class="sxs-lookup"><span data-stu-id="4da49-124">If `list1` is `[2; 3; 4]` and `list2` is `[100; 2; 3; 4 ]`, this code creates `list3` as `[2; 3; 4; 100; 2; 3; 4]`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1306.fs)]

<span data-ttu-id="4da49-125">中可用的執行 list 運算的函式[List 模組](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)。</span><span class="sxs-lookup"><span data-stu-id="4da49-125">Functions for performing operations on lists are available in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span>

<span data-ttu-id="4da49-126">由於 F# 中的 list 為固定，因此任何修改作業都會產生新的 list，而不會修改現有的 list。</span><span class="sxs-lookup"><span data-stu-id="4da49-126">Because lists in F# are immutable, any modifying operations generate new lists instead of modifying existing lists.</span></span>

<span data-ttu-id="4da49-127">F # 中的清單都會實作為單向連結清單，這表示存取清單的開頭的作業為 o （1），而且項目存取為 O (*n*)。</span><span class="sxs-lookup"><span data-stu-id="4da49-127">Lists in F# are implemented as singly linked lists, which means that operations that access only the head of the list are O(1), and element access is O(*n*).</span></span>


## <a name="properties"></a><span data-ttu-id="4da49-128">屬性</span><span class="sxs-lookup"><span data-stu-id="4da49-128">Properties</span></span>
<span data-ttu-id="4da49-129">list 類型支援下列屬性：</span><span class="sxs-lookup"><span data-stu-id="4da49-129">The list type supports the following properties:</span></span>

|<span data-ttu-id="4da49-130">屬性</span><span class="sxs-lookup"><span data-stu-id="4da49-130">Property</span></span>|<span data-ttu-id="4da49-131">類型</span><span class="sxs-lookup"><span data-stu-id="4da49-131">Type</span></span>|<span data-ttu-id="4da49-132">描述</span><span class="sxs-lookup"><span data-stu-id="4da49-132">Description</span></span>|
|--------|----|-----------|
|[<span data-ttu-id="4da49-133">標頭</span><span class="sxs-lookup"><span data-stu-id="4da49-133">Head</span></span>](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)|`'T`|<span data-ttu-id="4da49-134">第一個元素。</span><span class="sxs-lookup"><span data-stu-id="4da49-134">The first element.</span></span>|
|[<span data-ttu-id="4da49-135">空白</span><span class="sxs-lookup"><span data-stu-id="4da49-135">Empty</span></span>](https://msdn.microsoft.com/library/44406ecb-1918-4d32-b32a-ca1f69840386)|`'T list`|<span data-ttu-id="4da49-136">此為靜態屬性，會傳回適當類型的空 list。</span><span class="sxs-lookup"><span data-stu-id="4da49-136">A static property that returns an empty list of the appropriate type.</span></span>|
|[<span data-ttu-id="4da49-137">IsEmpty</span><span class="sxs-lookup"><span data-stu-id="4da49-137">IsEmpty</span></span>](https://msdn.microsoft.com/library/3ba087b2-2fc2-406d-b10a-cff6a19322da)|`bool`|<span data-ttu-id="4da49-138">`true` 表示 list 不含任何元素。</span><span class="sxs-lookup"><span data-stu-id="4da49-138">`true` if the list has no elements.</span></span>|
|[<span data-ttu-id="4da49-139">Item</span><span class="sxs-lookup"><span data-stu-id="4da49-139">Item</span></span>](https://msdn.microsoft.com/library/bdb2553a-0e54-4ff8-baed-ab1aac8f5dae)|`'T`|<span data-ttu-id="4da49-140">使用位於指定索引的元素 (以零為基底)。</span><span class="sxs-lookup"><span data-stu-id="4da49-140">The element at the specified index (zero-based).</span></span>|
|[<span data-ttu-id="4da49-141">長度</span><span class="sxs-lookup"><span data-stu-id="4da49-141">Length</span></span>](https://msdn.microsoft.com/library/25f715c8-9daa-4c4d-a6c7-26772f9dab4d)|`int`|<span data-ttu-id="4da49-142">元素數。</span><span class="sxs-lookup"><span data-stu-id="4da49-142">The number of elements.</span></span>|
|[<span data-ttu-id="4da49-143">結尾</span><span class="sxs-lookup"><span data-stu-id="4da49-143">Tail</span></span>](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)|`'T list`|<span data-ttu-id="4da49-144">list 沒有第一個元素。</span><span class="sxs-lookup"><span data-stu-id="4da49-144">The list without the first element.</span></span>|
<span data-ttu-id="4da49-145">下列是使用這些屬性的一些範例。</span><span class="sxs-lookup"><span data-stu-id="4da49-145">Following are some examples of using these properties.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1307.fs)]
    
## <a name="using-lists"></a><span data-ttu-id="4da49-146">使用 list</span><span class="sxs-lookup"><span data-stu-id="4da49-146">Using Lists</span></span>
<span data-ttu-id="4da49-147">使用 list 編寫程式讓您只需要編寫小量的程式碼，就可以執行複雜的運算。</span><span class="sxs-lookup"><span data-stu-id="4da49-147">Programming with lists enables you to perform complex operations with a small amount of code.</span></span> <span data-ttu-id="4da49-148">本節說明一些使用函式編寫程式時不可或缺的常用 list 運算。</span><span class="sxs-lookup"><span data-stu-id="4da49-148">This section describes common operations on lists that are important to functional programming.</span></span>


### <a name="recursion-with-lists"></a><span data-ttu-id="4da49-149">list 的遞迴功能</span><span class="sxs-lookup"><span data-stu-id="4da49-149">Recursion with Lists</span></span>
<span data-ttu-id="4da49-150">list 是唯一適合遞迴程式設計技巧的函式。</span><span class="sxs-lookup"><span data-stu-id="4da49-150">Lists are uniquely suited to recursive programming techniques.</span></span> <span data-ttu-id="4da49-151">假設有一項作業必須對 list 的每個元素執行。</span><span class="sxs-lookup"><span data-stu-id="4da49-151">Consider an operation that must be performed on every element of a list.</span></span> <span data-ttu-id="4da49-152">您可以利用遞迴方式執行此作業，方法是先對 list 的 head 執行運算，再傳遞 list 的 tail (此 list 只含原始 list，而不含第一個元素，所以比較小)，然後再執行下一個遞迴層級的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4da49-152">You can do this recursively by operating on the head of the list and then passing the tail of the list, which is a smaller list that consists of the original list without the first element, back again to the next level of recursion.</span></span>

<span data-ttu-id="4da49-153">若要編寫這類遞迴函式，可以在模式比對中使用 cons 運算子 (`::`)，以區分 list 的 head 與 tail。</span><span class="sxs-lookup"><span data-stu-id="4da49-153">To write such a recursive function, you use the cons operator (`::`) in pattern matching, which enables you to separate the head of a list from the tail.</span></span>

<span data-ttu-id="4da49-154">下列程式碼範例示範如何使用模式比對，實作執行 list 運算的遞迴函式。</span><span class="sxs-lookup"><span data-stu-id="4da49-154">The following code example shows how to use pattern matching to implement a recursive function that performs operations on a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13071.fs)]

<span data-ttu-id="4da49-155">前述程式碼對於小型 list 的效果很好，但對於大型的 list，可能會發生堆疊溢位。</span><span class="sxs-lookup"><span data-stu-id="4da49-155">The previous code works well for small lists, but for larger lists, it could overflow the stack.</span></span> <span data-ttu-id="4da49-156">下列程式碼是前述程式碼的改良版，運用了遞迴函式標準技巧中的 accumulator 引數。</span><span class="sxs-lookup"><span data-stu-id="4da49-156">The following code improves on this code by using an accumulator argument, a standard technique for working with recursive functions.</span></span> <span data-ttu-id="4da49-157">使用 accumulator 引數可以遞迴函式的 tail，進而達到節省空間的目的。</span><span class="sxs-lookup"><span data-stu-id="4da49-157">The use of the accumulator argument makes the function tail recursive, which saves stack space.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet13072.fs)]

<span data-ttu-id="4da49-158">函式 `RemoveAllMultiples` 為遞迴函式，可接受兩個 list。</span><span class="sxs-lookup"><span data-stu-id="4da49-158">The function `RemoveAllMultiples` is a recursive function that takes two lists.</span></span> <span data-ttu-id="4da49-159">第一個 list 包含倍數要移除的數字；第二個 list 是數字要移除的 list。</span><span class="sxs-lookup"><span data-stu-id="4da49-159">The first list contains the numbers whose multiples will be removed, and the second list is the list from which to remove the numbers.</span></span> <span data-ttu-id="4da49-160">下列範例會使用此遞迴函式消除 list 中的所有非質數，而只保留質數。</span><span class="sxs-lookup"><span data-stu-id="4da49-160">The code in the following example uses this recursive function to eliminate all the non-prime numbers from a list, leaving a list of prime numbers as the result.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet1308.fs)]

<span data-ttu-id="4da49-161">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-161">The output is as follows:</span></span>

```
Primes Up To 100:
[2; 3; 5; 7; 11; 13; 17; 19; 23; 29; 31; 37; 41; 43; 47; 53; 59; 61; 67; 71; 73; 79; 83; 89; 97]
```

## <a name="module-functions"></a><span data-ttu-id="4da49-162">模組函式</span><span class="sxs-lookup"><span data-stu-id="4da49-162">Module Functions</span></span>
<span data-ttu-id="4da49-163">[List 模組](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)提供可存取的項目清單的函式。</span><span class="sxs-lookup"><span data-stu-id="4da49-163">The [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788) provides functions that access the elements of a list.</span></span> <span data-ttu-id="4da49-164">head 元素是最方便存取的元素。</span><span class="sxs-lookup"><span data-stu-id="4da49-164">The head element is the fastest and easiest to access.</span></span> <span data-ttu-id="4da49-165">使用屬性[Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740)或模組函式[List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2)。</span><span class="sxs-lookup"><span data-stu-id="4da49-165">Use the property [Head](https://msdn.microsoft.com/library/5f9414fd-6bdb-470a-8b72-40016db30740) or the module function [List.head](https://msdn.microsoft.com/library/22514cc5-0511-498b-a2cc-837b688a6da2).</span></span> <span data-ttu-id="4da49-166">您可以使用來存取清單的結尾[結尾](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91)屬性或[List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601)函式。</span><span class="sxs-lookup"><span data-stu-id="4da49-166">You can access the tail of a list by using the [Tail](https://msdn.microsoft.com/library/2a6f8eb9-dc32-41aa-8b62-2baffaface91) property or the [List.tail](https://msdn.microsoft.com/library/da0a0638-4420-4571-84b6-d09ae601f601) function.</span></span> <span data-ttu-id="4da49-167">若要尋找索引項目，使用[List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1)函式。</span><span class="sxs-lookup"><span data-stu-id="4da49-167">To find an element by index, use the [List.nth](https://msdn.microsoft.com/library/1f717d57-89be-4007-a971-9cf5a28d83b1) function.</span></span> <span data-ttu-id="4da49-168">`List.nth` 會周遊 list。</span><span class="sxs-lookup"><span data-stu-id="4da49-168">`List.nth` traverses the list.</span></span> <span data-ttu-id="4da49-169">因此，它是 O (*n*)。</span><span class="sxs-lookup"><span data-stu-id="4da49-169">Therefore, it is O(*n*).</span></span> <span data-ttu-id="4da49-170">若您的程式碼需要頻繁地使用 `List.nth`，您或可改用 array，而不要使用 list。</span><span class="sxs-lookup"><span data-stu-id="4da49-170">If your code uses `List.nth` frequently, you might want to consider using an array instead of a list.</span></span> <span data-ttu-id="4da49-171">array 中的元素存取為 O(1)。</span><span class="sxs-lookup"><span data-stu-id="4da49-171">Element access in arrays is O(1).</span></span>


### <a name="boolean-operations-on-lists"></a><span data-ttu-id="4da49-172">List 的布林運算</span><span class="sxs-lookup"><span data-stu-id="4da49-172">Boolean Operations on Lists</span></span>
<span data-ttu-id="4da49-173">[List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107)函式可讓您決定清單是否有任何項目。</span><span class="sxs-lookup"><span data-stu-id="4da49-173">The [List.isEmpty](https://msdn.microsoft.com/library/a7941d44-9e92-427c-b806-c378f4558107) function determines whether a list has any elements.</span></span>

<span data-ttu-id="4da49-174">[List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8)函式套用布林測試，以傳回與清單的項目`true`沒有任何項目符合測試。</span><span class="sxs-lookup"><span data-stu-id="4da49-174">The [List.exists](https://msdn.microsoft.com/library/15a3ebd5-98f0-44c0-8220-7dedec3e68a8) function applies a Boolean test to elements of a list and returns `true` if any element satisfies the test.</span></span> <span data-ttu-id="4da49-175">[List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e)類似，但會在兩個清單中項目的後續配對。</span><span class="sxs-lookup"><span data-stu-id="4da49-175">[List.exists2](https://msdn.microsoft.com/library/7532b39e-3f4f-4534-a60b-d7721dc6fa7e) is similar but operates on successive pairs of elements in two lists.</span></span>

<span data-ttu-id="4da49-176">下列程式碼示範 `List.exists` 的用法。</span><span class="sxs-lookup"><span data-stu-id="4da49-176">The following code demonstrates the use of `List.exists`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet1.fs)]

<span data-ttu-id="4da49-177">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-177">The output is as follows:</span></span>

```
For list [0; 1; 2; 3], contains zero is true
```

<span data-ttu-id="4da49-178">下列範例示範 `List.exists2` 的用法。</span><span class="sxs-lookup"><span data-stu-id="4da49-178">The following example demonstrates the use of `List.exists2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet2.fs)]

<span data-ttu-id="4da49-179">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-179">The output is as follows:</span></span>

```
Lists [1; 2; 3; 4; 5] and [5; 4; 3; 2; 1] have at least one equal element at the same position.
```

<span data-ttu-id="4da49-180">您可以使用[List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7)如果您想要測試是否為清單的所有項目符合條件。</span><span class="sxs-lookup"><span data-stu-id="4da49-180">You can use [List.forall](https://msdn.microsoft.com/library/e11a5233-d612-40ac-833b-d5cf496900b7) if you want to test whether all the elements of a list meet a condition.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet3.fs)]

<span data-ttu-id="4da49-181">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-181">The output is as follows:</span></span>

```
true
false
```

<span data-ttu-id="4da49-182">同樣地， [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e)判斷兩個 list 中的對應位置中的所有元素是否都符合牽涉到的每對元素的布林運算式。</span><span class="sxs-lookup"><span data-stu-id="4da49-182">Similarly, [List.forall2](https://msdn.microsoft.com/library/bb611f02-8277-48f5-9af3-6194ae27d07e) determines whether all elements in the corresponding positions in two lists satisfy a Boolean expression that involves each pair of elements.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet4.fs)]

<span data-ttu-id="4da49-183">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-183">The output is as follows:</span></span>

```
true
false
```

### <a name="sort-operations-on-lists"></a><span data-ttu-id="4da49-184">List 的排序運算</span><span class="sxs-lookup"><span data-stu-id="4da49-184">Sort Operations on Lists</span></span>
<span data-ttu-id="4da49-185">[List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d)， [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359)，和[List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7)函式會排序清單。</span><span class="sxs-lookup"><span data-stu-id="4da49-185">The [List.sort](https://msdn.microsoft.com/library/17f1030e-aa7e-41dd-94ea-72cb6c04fd3d), [List.sortBy](https://msdn.microsoft.com/library/955bfc5f-ad9c-4f2d-a7ab-91e43eb21359), and [List.sortWith](https://msdn.microsoft.com/library/1d806a54-9166-4198-906d-15101f7916c7) functions sort lists.</span></span> <span data-ttu-id="4da49-186">排序函式可指定要使用這三個函式中的哪一個函式。</span><span class="sxs-lookup"><span data-stu-id="4da49-186">The sorting function determines which of these three functions to use.</span></span> <span data-ttu-id="4da49-187">`List.sort` 會使用預設的泛型比較。</span><span class="sxs-lookup"><span data-stu-id="4da49-187">`List.sort` uses default generic comparison.</span></span> <span data-ttu-id="4da49-188">泛型比較會依不同的泛型比較函式而使用不同的全域運算子來比較值。</span><span class="sxs-lookup"><span data-stu-id="4da49-188">Generic comparison uses global operators based on the generic compare function to compare values.</span></span> <span data-ttu-id="4da49-189">其可與多種元素類型搭配使用，例如簡單的數值類型、tuple、記錄、差別聯集、list、array 及所有實作 `System.IComparable` 的類型。</span><span class="sxs-lookup"><span data-stu-id="4da49-189">It works efficiently with a wide variety of element types, such as simple numeric types, tuples, records, discriminated unions, lists, arrays, and any type that implements `System.IComparable`.</span></span> <span data-ttu-id="4da49-190">對於實作 `System.IComparable` 的類型，泛型比較會使用 `System.IComparable.CompareTo()` 函式。</span><span class="sxs-lookup"><span data-stu-id="4da49-190">For types that implement `System.IComparable`, generic comparison uses the `System.IComparable.CompareTo()` function.</span></span> <span data-ttu-id="4da49-191">泛型比較也會搭配字串，但會使用不涉及文化的排序順序。</span><span class="sxs-lookup"><span data-stu-id="4da49-191">Generic comparison also works with strings, but uses a culture-independent sorting order.</span></span> <span data-ttu-id="4da49-192">請勿對不支援的類型 (例如函式類型) 使用泛型比較。</span><span class="sxs-lookup"><span data-stu-id="4da49-192">Generic comparison should not be used on unsupported types, such as function types.</span></span> <span data-ttu-id="4da49-193">此外，預設泛型比較對小型結構類型的效能最好；若需要經常比較及排序比較大的結構類型，可考慮實作 `System.IComparable` 及佈建成效更好的 `System.IComparable.CompareTo()` 方法實作。</span><span class="sxs-lookup"><span data-stu-id="4da49-193">Also, the performance of the default generic comparison is best for small structured types; for larger structured types that need to be compared and sorted frequently, consider implementing `System.IComparable` and providing an efficient implementation of the `System.IComparable.CompareTo()` method.</span></span>

<span data-ttu-id="4da49-194">`List.sortBy` 可接受函式傳回的值做為排序準則；而 `List.sortWith` 可接受比較函式做為引數。</span><span class="sxs-lookup"><span data-stu-id="4da49-194">`List.sortBy` takes a function that returns a value that is used as the sort criterion, and `List.sortWith` takes a comparison function as an argument.</span></span> <span data-ttu-id="4da49-195">當您要使用的類型不支援比較時，或比較需要更複雜的比較語意 (例如使用涉及文化的字串) 時，即可使用後兩個函式。</span><span class="sxs-lookup"><span data-stu-id="4da49-195">These latter two functions are useful when you are working with types that do not support comparison, or when the comparison requires more complex comparison semantics, as in the case of culture-aware strings.</span></span>

<span data-ttu-id="4da49-196">下列範例示範 `List.sort` 的用法。</span><span class="sxs-lookup"><span data-stu-id="4da49-196">The following example demonstrates the use of `List.sort`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet5.fs)]

<span data-ttu-id="4da49-197">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-197">The output is as follows:</span></span>

```
[-2; 1; 4; 5; 8]
```

<span data-ttu-id="4da49-198">下列範例示範 `List.sortBy` 的用法。</span><span class="sxs-lookup"><span data-stu-id="4da49-198">The following example demonstrates the use of `List.sortBy`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet6.fs)]

<span data-ttu-id="4da49-199">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-199">The output is as follows:</span></span>

```
[1; -2; 4; 5; 8]
```

<span data-ttu-id="4da49-200">下列範例示範 `List.sortWith` 的用法。</span><span class="sxs-lookup"><span data-stu-id="4da49-200">The next example demonstrates the use of `List.sortWith`.</span></span> <span data-ttu-id="4da49-201">此範例會使用自訂比較函式 `compareWidgets` 先比較自訂類型的第一個欄位，當第一個欄位的值相等時，再比較其他欄位。</span><span class="sxs-lookup"><span data-stu-id="4da49-201">In this example, the custom comparison function `compareWidgets` is used to first compare one field of a custom type, and then another when the values of the first field are equal.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet7.fs)]

<span data-ttu-id="4da49-202">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-202">The output is as follows:</span></span>

```
[{ID = 92;
Rev = 1;}; {ID = 92;
Rev = 1;}; {ID = 100;
Rev = 2;}; {ID = 100;
Rev = 5;}; {ID = 110;
Rev = 1;}]
```

### <a name="search-operations-on-lists"></a><span data-ttu-id="4da49-203">List 的搜尋運算</span><span class="sxs-lookup"><span data-stu-id="4da49-203">Search Operations on Lists</span></span>
<span data-ttu-id="4da49-204">list 支援多種搜尋運算。</span><span class="sxs-lookup"><span data-stu-id="4da49-204">Numerous search operations are supported for lists.</span></span> <span data-ttu-id="4da49-205">最簡單的[List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06)，可讓您尋找符合指定的條件的第一個項目。</span><span class="sxs-lookup"><span data-stu-id="4da49-205">The simplest, [List.find](https://msdn.microsoft.com/library/0594593e-9c75-44c1-8f5a-a37b2e561c06), enables you to find the first element that matches a given condition.</span></span>

<span data-ttu-id="4da49-206">下列程式碼範例示範如何使用 `List.find` 從 list 中尋找第一個可以被 5 整除的數字。</span><span class="sxs-lookup"><span data-stu-id="4da49-206">The following code example demonstrates the use of `List.find` to find the first number that is divisible by 5 in a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet8.fs)]

<span data-ttu-id="4da49-207">The result is 5.</span><span class="sxs-lookup"><span data-stu-id="4da49-207">The result is 5.</span></span>

<span data-ttu-id="4da49-208">如果項目必須先經過轉換，呼叫[List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2); 其可接受函式會傳回選項，然後尋找第一個選項值是`Some(x)`。</span><span class="sxs-lookup"><span data-stu-id="4da49-208">If the elements must be transformed first, call [List.pick](https://msdn.microsoft.com/library/0430b515-7fe4-49a1-a616-d2286d8b08b2), which takes a function that returns an option, and looks for the first option value that is `Some(x)`.</span></span> <span data-ttu-id="4da49-209">`List.pick` 不會傳回元素，而會傳回結果 `x`。</span><span class="sxs-lookup"><span data-stu-id="4da49-209">Instead of returning the element, `List.pick` returns the result `x`.</span></span> <span data-ttu-id="4da49-210">若找不到相符的元素，`List.pick` 會擲出 `System.Collections.Generic.KeyNotFoundException`。</span><span class="sxs-lookup"><span data-stu-id="4da49-210">If no matching element is found, `List.pick` throws `System.Collections.Generic.KeyNotFoundException`.</span></span> <span data-ttu-id="4da49-211">下列程式碼示範 `List.pick` 的用法。</span><span class="sxs-lookup"><span data-stu-id="4da49-211">The following code shows the use of `List.pick`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet9.fs)]

<span data-ttu-id="4da49-212">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-212">The output is as follows:</span></span>

```
"b"
```

<span data-ttu-id="4da49-213">搜尋作業，另一個群組[List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d)和相關的函數，會傳回選項值。</span><span class="sxs-lookup"><span data-stu-id="4da49-213">Another group of search operations, [List.tryFind](https://msdn.microsoft.com/library/37f4532e-9fd0-4802-8bbd-e1aa2380287d) and related functions, return an option value.</span></span> <span data-ttu-id="4da49-214">`List.tryFind` 函式會傳回 list 中第一個滿足條件的元素 (如其存在)；若找不到，即會傳回選項值 `None`。</span><span class="sxs-lookup"><span data-stu-id="4da49-214">The `List.tryFind` function returns the first element of a list that satisfies a condition if such an element exists, but the option value `None` if not.</span></span> <span data-ttu-id="4da49-215">變化[List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec)傳回項目的索引; 如果找到一個物件，而不是項目本身。</span><span class="sxs-lookup"><span data-stu-id="4da49-215">The variation [List.tryFindIndex](https://msdn.microsoft.com/library/5e31968c-c3d3-43d2-859a-0526825895ec) returns the index of the element, if one is found, rather than the element itself.</span></span> <span data-ttu-id="4da49-216">下列程式碼是這些函式的示範。</span><span class="sxs-lookup"><span data-stu-id="4da49-216">These functions are illustrated in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet10.fs)]

<span data-ttu-id="4da49-217">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-217">The output is as follows:</span></span>

```
The first even value is 22.
The first even value is at position 8.
```

### <a name="arithmetic-operations-on-lists"></a><span data-ttu-id="4da49-218">List 的算術運算</span><span class="sxs-lookup"><span data-stu-id="4da49-218">Arithmetic Operations on Lists</span></span>
<span data-ttu-id="4da49-219">內建常用的算術運算，例如 sum 及 average [List 模組](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788)。</span><span class="sxs-lookup"><span data-stu-id="4da49-219">Common arithmetic operations such as sum and average are built into the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="4da49-220">若要使用[List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9)，list 的元素類型必須支援`+`運算子，且具有零值。</span><span class="sxs-lookup"><span data-stu-id="4da49-220">To work with [List.sum](https://msdn.microsoft.com/library/54d47fe3-5ecf-4883-beb5-e915342a17f9), the list element type must support the `+` operator and have a zero value.</span></span> <span data-ttu-id="4da49-221">所有內建算術類型皆滿足這些條件。</span><span class="sxs-lookup"><span data-stu-id="4da49-221">All built-in arithmetic types satisfy these conditions.</span></span> <span data-ttu-id="4da49-222">若要使用[List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1)，項目類型必須支援的其餘部分，其中不包含整數類資料類型，但允許浮點數型別。</span><span class="sxs-lookup"><span data-stu-id="4da49-222">To work with [List.average](https://msdn.microsoft.com/library/2b9a627b-106d-4548-8c4c-ab5058b8f8e1), the element type must support division without a remainder, which excludes integral types but allows for floating point types.</span></span> <span data-ttu-id="4da49-223">[List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d)和[List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403)函式可接受函式做為參數，且此函式的結果用來計算出的總和或平均的值。</span><span class="sxs-lookup"><span data-stu-id="4da49-223">The [List.sumBy](https://msdn.microsoft.com/library/b7623389-0fe1-4762-9c67-51079903ab7d) and [List.averageBy](https://msdn.microsoft.com/library/936cc9ec-62af-464d-8726-7999c2f48403) functions take a function as a parameter, and this function's results are used to calculate the values for the sum or average.</span></span>

<span data-ttu-id="4da49-224">下列程式碼示範 `List.sum`、`List.sumBy` 及 `List.average` 的用法。</span><span class="sxs-lookup"><span data-stu-id="4da49-224">The following code demonstrates the use of `List.sum`, `List.sumBy`, and `List.average`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet11.fs)]

<span data-ttu-id="4da49-225">輸出為 `1.000000`。</span><span class="sxs-lookup"><span data-stu-id="4da49-225">The output is `1.000000`.</span></span>

<span data-ttu-id="4da49-226">下列程式碼示範 `List.averageBy` 的用法。</span><span class="sxs-lookup"><span data-stu-id="4da49-226">The following code shows the use of `List.averageBy`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet12.fs)]

<span data-ttu-id="4da49-227">輸出為 `5.5`。</span><span class="sxs-lookup"><span data-stu-id="4da49-227">The output is `5.5`.</span></span>


### <a name="lists-and-tuples"></a><span data-ttu-id="4da49-228">List 與 Tuple</span><span class="sxs-lookup"><span data-stu-id="4da49-228">Lists and Tuples</span></span>
<span data-ttu-id="4da49-229">zip 及 unzip 函式可以操作包含 tuple 的 list。</span><span class="sxs-lookup"><span data-stu-id="4da49-229">Lists that contain tuples can be manipulated by zip and unzip functions.</span></span> <span data-ttu-id="4da49-230">這些函式會將各自包含一個值的兩個 list 合併成一份元組清單，或將一份元組清單分割成兩個只含單一值的 list。</span><span class="sxs-lookup"><span data-stu-id="4da49-230">These functions combine two lists of single values into one list of tuples or separate one list of tuples into two lists of single values.</span></span> <span data-ttu-id="4da49-231">最簡單[List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c)函式接受兩個 list 的單一項目，並產生一份 tuple 配對。</span><span class="sxs-lookup"><span data-stu-id="4da49-231">The simplest [List.zip](https://msdn.microsoft.com/library/3028d790-8f48-4c94-bf08-b058bec3689c) function takes two lists of single elements and produces a single list of tuple pairs.</span></span> <span data-ttu-id="4da49-232">另一個版本[List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b)會接受三個清單的單一項目，並產生一份有三個元素的 tuple 集合。</span><span class="sxs-lookup"><span data-stu-id="4da49-232">Another version, [List.zip3](https://msdn.microsoft.com/library/003cc28e-0de3-4d99-89ed-cb19028e3c5b), takes three lists of single elements and produces a single list of tuples that have three elements.</span></span> <span data-ttu-id="4da49-233">下列程式碼範例示範 `List.zip` 的用法。</span><span class="sxs-lookup"><span data-stu-id="4da49-233">The following code example demonstrates the use of `List.zip`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet13.fs)]

<span data-ttu-id="4da49-234">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-234">The output is as follows:</span></span>

```
[(1, -1); (2, -2); (3; -3)]
```

<span data-ttu-id="4da49-235">下列程式碼範例示範 `List.zip3` 的用法。</span><span class="sxs-lookup"><span data-stu-id="4da49-235">The following code example demonstrates the use of `List.zip3`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet14.fs)]

<span data-ttu-id="4da49-236">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-236">The output is as follows:</span></span>

```
[(1, -1, 0); (2, -2, 0); (3, -3, 0)]
```

<span data-ttu-id="4da49-237">對應的 unzip 版本[List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)和[List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4)、 接受 tuple 清單，並傳回 tuple，其中第一個清單中會包含每個 tuple 中第一次的所有項目，清單和第二個清單包含每個 tuple 和等等的第二個項目。</span><span class="sxs-lookup"><span data-stu-id="4da49-237">The corresponding unzip versions, [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21) and [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4), take lists of tuples and return lists in a tuple, where the first list contains all the elements that were first in each tuple, and the second list contains the second element of each tuple, and so on.</span></span>

<span data-ttu-id="4da49-238">下列程式碼範例示範如何使用[List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21)。</span><span class="sxs-lookup"><span data-stu-id="4da49-238">The following code example demonstrates the use of [List.unzip](https://msdn.microsoft.com/library/639db80c-41b5-45bb-a6b4-1eaa04d61d21).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet15.fs)]

<span data-ttu-id="4da49-239">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-239">The output is as follows:</span></span>

```
([1; 3], [2; 4])
[1; 3] [2; 4]
```

<span data-ttu-id="4da49-240">下列程式碼範例示範如何使用[List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4)。</span><span class="sxs-lookup"><span data-stu-id="4da49-240">The following code example demonstrates the use of [List.unzip3](https://msdn.microsoft.com/library/43078c77-32ec-4342-85b3-c31ccf984db4).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet16.fs)]

<span data-ttu-id="4da49-241">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-241">The output is as follows:</span></span>

```
([1; 4], [2; 5], [3; 6])
```

### <a name="operating-on-list-elements"></a><span data-ttu-id="4da49-242">List 元素的運算</span><span class="sxs-lookup"><span data-stu-id="4da49-242">Operating on List Elements</span></span>
<span data-ttu-id="4da49-243">F# 支援多種 list 元素運算。</span><span class="sxs-lookup"><span data-stu-id="4da49-243">F# supports a variety of operations on list elements.</span></span> <span data-ttu-id="4da49-244">最簡單的是[List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f)，可讓您在清單的每個項目上呼叫的函式。</span><span class="sxs-lookup"><span data-stu-id="4da49-244">The simplest is [List.iter](https://msdn.microsoft.com/library/f778d075-81a9-4994-af60-cddcc53a201f), which enables you to call a function on every element of a list.</span></span> <span data-ttu-id="4da49-245">包含變化[List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40)，可讓您執行的兩個清單項目上操作[List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60)，就像一樣`List.iter`不同之處在於每個項目的索引做為傳遞針對每個項目，呼叫函式引數和[List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c)，這是結合的功能`List.iter2`和`List.iteri`。</span><span class="sxs-lookup"><span data-stu-id="4da49-245">Variations include [List.iter2](https://msdn.microsoft.com/library/ea3b7761-916c-4016-9bd8-651124c98b40), which enables you to perform an operation on elements of two lists, [List.iteri](https://msdn.microsoft.com/library/6dd21ae6-5c00-41cd-8306-821e513d8f60), which is like `List.iter` except that the index of each element is passed as an argument to the function that is called for each element, and [List.iteri2](https://msdn.microsoft.com/library/9658d740-9be5-4bf7-b663-c8ab2b3e196c), which is a combination of the functionality of `List.iter2` and `List.iteri`.</span></span> <span data-ttu-id="4da49-246">下列程式碼範例會示範這些函數。</span><span class="sxs-lookup"><span data-stu-id="4da49-246">The following code example illustrates these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet17.fs)]

<span data-ttu-id="4da49-247">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-247">The output is as follows:</span></span>

```
List.iter: element is 1
List.iter: element is 2
List.iter: element is 3
List.iteri: element 0 is 1
List.iteri: element 1 is 2
List.iteri: element 2 is 3
List.iter2: elements are 1 4
List.iter2: elements are 2 5
List.iter2: elements are 3 6
List.iteri2: element 0 of list1 is 1; element 0 of list2 is 4
List.iteri2: element 1 of list1 is 2; element 1 of list2 is 5
List.iteri2: element 2 of list1 is 3; element 2 of list2 is 6
```

<span data-ttu-id="4da49-248">另一個轉換 list 元素的常用函式是[List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6)，可讓您將函數套用至清單的每個項目，並將所有結果都放入新的 list。</span><span class="sxs-lookup"><span data-stu-id="4da49-248">Another frequently used function that transforms list elements is [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6), which enables you to apply a function to each element of a list and put all the results into a new list.</span></span> <span data-ttu-id="4da49-249">[List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57)和[List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8)接受多個 list 的變化。</span><span class="sxs-lookup"><span data-stu-id="4da49-249">[List.map2](https://msdn.microsoft.com/library/5f48cce7-6eaf-4e54-8996-2b04d3c31e57) and [List.map3](https://msdn.microsoft.com/library/dd9fb190-6980-4537-be96-5645a64908f8) are variations that take multiple lists.</span></span> <span data-ttu-id="4da49-250">您也可以使用[List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14)和[List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49)，如果項目，除了函式需要傳遞每個項目的索引。</span><span class="sxs-lookup"><span data-stu-id="4da49-250">You can also use [List.mapi](https://msdn.microsoft.com/library/284b9234-3d26-409b-b328-ac79638d9e14) and [List.mapi2](https://msdn.microsoft.com/library/680643af-233c-40a3-82f2-43d5af27ec49), if, in addition to the element, the function needs to be passed the index of each element.</span></span> <span data-ttu-id="4da49-251">`List.mapi2` 與 `List.mapi` 的唯一差別在於 `List.mapi2` 可與兩個 list 搭配使用。</span><span class="sxs-lookup"><span data-stu-id="4da49-251">The only difference between `List.mapi2` and `List.mapi` is that `List.mapi2` works with two lists.</span></span> <span data-ttu-id="4da49-252">下列範例說明[List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6)。</span><span class="sxs-lookup"><span data-stu-id="4da49-252">The following example illustrates [List.map](https://msdn.microsoft.com/library/c6b49c99-d4f3-4ba3-b1d0-85a312683dc6).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet18.fs)]

<span data-ttu-id="4da49-253">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-253">The output is as follows:</span></span>

```
[2; 3; 4]
```

<span data-ttu-id="4da49-254">下列範例示範 `List.map2` 的用法。</span><span class="sxs-lookup"><span data-stu-id="4da49-254">The following example shows the use of `List.map2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet19.fs)]

<span data-ttu-id="4da49-255">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-255">The output is as follows:</span></span>

```
[5; 7; 9]
```

<span data-ttu-id="4da49-256">下列範例示範 `List.map3` 的用法。</span><span class="sxs-lookup"><span data-stu-id="4da49-256">The following example shows the use of `List.map3`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet20.fs)]

<span data-ttu-id="4da49-257">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-257">The output is as follows:</span></span>

```
[7; 10; 13]
```

<span data-ttu-id="4da49-258">下列範例示範 `List.mapi` 的用法。</span><span class="sxs-lookup"><span data-stu-id="4da49-258">The following example shows the use of `List.mapi`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet21.fs)]

<span data-ttu-id="4da49-259">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-259">The output is as follows:</span></span>

```
[1; 3; 5]
```

<span data-ttu-id="4da49-260">下列範例示範 `List.mapi2` 的用法。</span><span class="sxs-lookup"><span data-stu-id="4da49-260">The following example shows the use of `List.mapi2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet22.fs)]

<span data-ttu-id="4da49-261">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-261">The output is as follows:</span></span>

```
[0; 7; 18]
```

<span data-ttu-id="4da49-262">[List.collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f)就像是`List.map`，不同之處在於每個項目會產生的清單和所有 list 會都串連成最終的 list。</span><span class="sxs-lookup"><span data-stu-id="4da49-262">[List.collect](https://msdn.microsoft.com/library/cd08bbc7-a3b9-40ab-8c20-4e85ec84664f) is like `List.map`, except that each element produces a list and all these lists are concatenated into a final list.</span></span> <span data-ttu-id="4da49-263">在下列程式碼中，list 的每個元素都會產生三個數字。</span><span class="sxs-lookup"><span data-stu-id="4da49-263">In the following code, each element of the list generates three numbers.</span></span> <span data-ttu-id="4da49-264">所有數字都會收集到一個 list 中。</span><span class="sxs-lookup"><span data-stu-id="4da49-264">These are all collected into one list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet23.fs)]

<span data-ttu-id="4da49-265">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-265">The output is as follows:</span></span>

```
[1; 2; 3; 2; 4; 6; 3; 6; 9]
```

<span data-ttu-id="4da49-266">您也可以使用[List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248)，這會採用布林條件，並產生新清單，其中只包含符合指定的條件的項目。</span><span class="sxs-lookup"><span data-stu-id="4da49-266">You can also use [List.filter](https://msdn.microsoft.com/library/11a8c926-547b-44dd-bbae-98d44f3dd248), which takes a Boolean condition and produces a new list that consists only of elements that satisfy the given condition.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet24.fs)]

<span data-ttu-id="4da49-267">所得 list 為 `[2; 4; 6]`。</span><span class="sxs-lookup"><span data-stu-id="4da49-267">The resulting list is `[2; 4; 6]`.</span></span>

<span data-ttu-id="4da49-268">一組對應與篩選， [List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d)可讓您同時轉換及選取項目在相同的時間。</span><span class="sxs-lookup"><span data-stu-id="4da49-268">A combination of map and filter, [List.choose](https://msdn.microsoft.com/library/2e21d3fb-ce35-4824-8a57-c4404616093d) enables you to transform and select elements at the same time.</span></span> <span data-ttu-id="4da49-269">`List.choose` 會套用可以傳回選項給每個 list 元素的函式，並會在函式傳回選項值 `Some` 時，為元素傳回新的結果清單。</span><span class="sxs-lookup"><span data-stu-id="4da49-269">`List.choose` applies a function that returns an option to each element of a list, and returns a new list of the results for elements when the function returns the option value `Some`.</span></span>

<span data-ttu-id="4da49-270">下列程式碼示範如何使用 `List.choose` 選取不在單字清單內的大寫單字。</span><span class="sxs-lookup"><span data-stu-id="4da49-270">The following code demonstrates the use of `List.choose` to select capitalized words out of a list of words.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet25.fs)]

<span data-ttu-id="4da49-271">其輸出如下：</span><span class="sxs-lookup"><span data-stu-id="4da49-271">The output is as follows:</span></span>

```
["Rome's"; "Bob's"]
```

### <a name="operating-on-multiple-lists"></a><span data-ttu-id="4da49-272">多個 List 的運算</span><span class="sxs-lookup"><span data-stu-id="4da49-272">Operating on Multiple Lists</span></span>
<span data-ttu-id="4da49-273">多個 list 可以相互結合。</span><span class="sxs-lookup"><span data-stu-id="4da49-273">Lists can be joined together.</span></span> <span data-ttu-id="4da49-274">若要將兩個 list 合而為一，使用[List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426)。</span><span class="sxs-lookup"><span data-stu-id="4da49-274">To join two lists into one, use [List.append](https://msdn.microsoft.com/library/2954da80-3f4a-4a4b-9371-794645c03426).</span></span> <span data-ttu-id="4da49-275">若要加入兩個以上的清單，請使用[List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c)。</span><span class="sxs-lookup"><span data-stu-id="4da49-275">To join more than two lists, use [List.concat](https://msdn.microsoft.com/library/c5afd433-8764-4ea8-a6a8-937fb4d77c4c).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet26.fs)]
    
### <a name="fold-and-scan-operations"></a><span data-ttu-id="4da49-276">Fold 與 Scan 運算</span><span class="sxs-lookup"><span data-stu-id="4da49-276">Fold and Scan Operations</span></span>
<span data-ttu-id="4da49-277">有些 list 運算涉及所有 list 元素間彼此的相依性。</span><span class="sxs-lookup"><span data-stu-id="4da49-277">Some list operations involve interdependencies between all of the list elements.</span></span> <span data-ttu-id="4da49-278">Fold 與 scan 運算就像是`List.iter`和`List.map`您叫用每個元素上的函式，但這些作業會提供額外的參數呼叫在所*accumulator*的通訊進行的資訊計算。</span><span class="sxs-lookup"><span data-stu-id="4da49-278">The fold and scan operations are like `List.iter` and `List.map` in that you invoke a function on each element, but these operations provide an additional parameter called the *accumulator* that carries information through the computation.</span></span>

<span data-ttu-id="4da49-279">使用 `List.fold` 對 list 執行運算。</span><span class="sxs-lookup"><span data-stu-id="4da49-279">Use `List.fold` to perform a calculation on a list.</span></span>

<span data-ttu-id="4da49-280">下列程式碼範例示範如何使用[List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0)執行各種作業。</span><span class="sxs-lookup"><span data-stu-id="4da49-280">The following code example demonstrates the use of [List.fold](https://msdn.microsoft.com/library/c272779e-bae7-4983-8d7f-16b345bb33a0) to perform various operations.</span></span>

<span data-ttu-id="4da49-281">清單會經過周遊；accumulator `acc` 一值會隨著運算進行而傳遞。</span><span class="sxs-lookup"><span data-stu-id="4da49-281">The list is traversed; the accumulator `acc` is a value that is passed along as the calculation proceeds.</span></span> <span data-ttu-id="4da49-282">第一個引數在接受 accumulator 及 list 元素之後，會傳回 list 元素的暫時結果。</span><span class="sxs-lookup"><span data-stu-id="4da49-282">The first argument takes the accumulator and the list element, and returns the interim result of the calculation for that list element.</span></span> <span data-ttu-id="4da49-283">第二個引數是 accumulator 的初始值。</span><span class="sxs-lookup"><span data-stu-id="4da49-283">The second argument is the initial value of the accumulator.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet27.fs)]

<span data-ttu-id="4da49-284">這些函式若對多個 list 執行，函式名稱中會有一位數字記錄其版本。</span><span class="sxs-lookup"><span data-stu-id="4da49-284">The versions of these functions that have a digit in the function name operate on more than one list.</span></span> <span data-ttu-id="4da49-285">例如， [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343)對兩個 list 執行運算。</span><span class="sxs-lookup"><span data-stu-id="4da49-285">For example, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) performs computations on two lists.</span></span>

<span data-ttu-id="4da49-286">下列範例示範 `List.fold2` 的用法。</span><span class="sxs-lookup"><span data-stu-id="4da49-286">The following example demonstrates the use of `List.fold2`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet28.fs)]

<span data-ttu-id="4da49-287">`List.fold` 和[List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8)差別在於`List.fold`傳回此額外的參數，最終的值，但`List.scan`傳回此額外參數 （與最終值） 的中間值的清單。</span><span class="sxs-lookup"><span data-stu-id="4da49-287">`List.fold` and [List.scan](https://msdn.microsoft.com/library/21f636db-885c-4a72-970e-e3841f33a1b8) differ in that `List.fold` returns the final value of the extra parameter, but `List.scan` returns the list of the intermediate values (along with the final value) of the extra parameter.</span></span>

<span data-ttu-id="4da49-288">所有這些函式包含一個反向的變化，例如[List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7)，其中的順序在不同的周遊和引數的順序。</span><span class="sxs-lookup"><span data-stu-id="4da49-288">Each of these functions includes a reverse variation, for example, [List.foldBack](https://msdn.microsoft.com/library/b9a58e66-efe1-445f-a90c-ac9ffb9d40c7), which differs in the order in which the list is traversed and the order of the arguments.</span></span> <span data-ttu-id="4da49-289">此外，`List.fold`和`List.foldBack`有變化[List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343)和[List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2)，可接受兩個等長的清單。</span><span class="sxs-lookup"><span data-stu-id="4da49-289">Also, `List.fold` and `List.foldBack` have variations, [List.fold2](https://msdn.microsoft.com/library/6cfcd043-a65d-4423-805a-2ab234cb5343) and [List.foldBack2](https://msdn.microsoft.com/library/56371d3e-5271-4183-9e8c-15a02eda9aa2), that take two lists of equal length.</span></span> <span data-ttu-id="4da49-290">對每個元素執行的函式，皆可使用兩個 list 的對應元素執行特定動作。</span><span class="sxs-lookup"><span data-stu-id="4da49-290">The function that executes on each element can use corresponding elements of both lists to perform some action.</span></span> <span data-ttu-id="4da49-291">如下列範例所示，兩個 list 的元素類型可以不同，其中一個 list 包含銀行帳戶的交易金額，另一個 list 則包含交易的類型 (存款或提款)。</span><span class="sxs-lookup"><span data-stu-id="4da49-291">The element types of the two lists can be different, as in the following example, in which one list contains transaction amounts for a bank account, and the other list contains the type of transaction: deposit or withdrawal.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet29.fs)]

<span data-ttu-id="4da49-292">對於加總這類運算，因為 `List.fold` 與 `List.foldBack` 的結果與周遊順序無關，所以兩者的效果相同。</span><span class="sxs-lookup"><span data-stu-id="4da49-292">For a calculation like summation, `List.fold` and `List.foldBack` have the same effect because the result does not depend on the order of traversal.</span></span> <span data-ttu-id="4da49-293">在下列範例中，`List.foldBack` 會用於新增 list 中的元素。</span><span class="sxs-lookup"><span data-stu-id="4da49-293">In the following example, `List.foldBack` is used to add the elements in a list.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet30.fs)]

<span data-ttu-id="4da49-294">下列範例會回到銀行帳戶範例。</span><span class="sxs-lookup"><span data-stu-id="4da49-294">The following example returns to the bank account example.</span></span> <span data-ttu-id="4da49-295">這次會新增「利息運算」交易類型。</span><span class="sxs-lookup"><span data-stu-id="4da49-295">This time a new transaction type is added: an interest calculation.</span></span> <span data-ttu-id="4da49-296">最終結餘取決於異動的順序。</span><span class="sxs-lookup"><span data-stu-id="4da49-296">The ending balance now depends on the order of transactions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet34.fs)]

<span data-ttu-id="4da49-297">函式[List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b)有點像`List.fold`和`List.scan`不同之處在於，而不是個別的 accumulator，`List.reduce`會採用兩個引數的項目類型，而不是將函式只一個，而這些引數的另一個做為 accumulator，亦即會儲存計算的中繼結果。</span><span class="sxs-lookup"><span data-stu-id="4da49-297">The function [List.reduce](https://msdn.microsoft.com/library/048e1f95-691b-49cb-bb99-fb85f68f3d8b) is somewhat like `List.fold` and `List.scan`, except that instead of passing around a separate accumulator, `List.reduce` takes a function that takes two arguments of the element type instead of just one, and one of those arguments acts as the accumulator, meaning that it stores the intermediate result of the computation.</span></span> <span data-ttu-id="4da49-298">`List.reduce` 會從運算頭兩個 list 元素開始，然後再並用運算結果與下一個元素。</span><span class="sxs-lookup"><span data-stu-id="4da49-298">`List.reduce` starts by operating on the first two list elements, and then uses the result of the operation along with the next element.</span></span> <span data-ttu-id="4da49-299">因為沒有任何具有專屬類型的 accumulator，所以可以使用 `List.reduce` 取代 `List.fold`，但前提是 accumulator 與元素類型必須屬於相同類型。</span><span class="sxs-lookup"><span data-stu-id="4da49-299">Because there is not a separate accumulator that has its own type, `List.reduce` can be used in place of `List.fold` only when the accumulator and the element type have the same type.</span></span> <span data-ttu-id="4da49-300">下列程式碼示範 `List.reduce` 的用法。</span><span class="sxs-lookup"><span data-stu-id="4da49-300">The following code demonstrates the use of `List.reduce`.</span></span> <span data-ttu-id="4da49-301">若提供的 list 不含任何元素，`List.reduce` 會擲出例外狀況。</span><span class="sxs-lookup"><span data-stu-id="4da49-301">`List.reduce` throws an exception if the list provided has no elements.</span></span>

<span data-ttu-id="4da49-302">在下列程式碼中，第一個 Lambda 運算式呼叫的引數設定為 2 與 4，並傳回 6；下一個呼叫的引數設定為 6 與 10，所以結果為 16。</span><span class="sxs-lookup"><span data-stu-id="4da49-302">In the following code, the first call to the lambda expression is given the arguments 2 and 4, and returns 6, and the next call is given the arguments 6 and 10, so the result is 16.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lists/snippet33.fs)]
    
### <a name="converting-between-lists-and-other-collection-types"></a><span data-ttu-id="4da49-303">List 與其他收集類型的相互轉換</span><span class="sxs-lookup"><span data-stu-id="4da49-303">Converting Between Lists and Other Collection Types</span></span>
<span data-ttu-id="4da49-304">`List` 模組提供可以讓 sequence 與 array 相互轉換的函式。</span><span class="sxs-lookup"><span data-stu-id="4da49-304">The `List` module provides functions for converting to and from both sequences and arrays.</span></span> <span data-ttu-id="4da49-305">若要轉換的序列，使用[List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0)或[List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0)。</span><span class="sxs-lookup"><span data-stu-id="4da49-305">To convert to or from a sequence, use [List.toSeq](https://msdn.microsoft.com/library/7024be4b-ee70-43cc-8d0a-e6564a4ff7c0) or [List.ofSeq](https://msdn.microsoft.com/library/74ab9289-4a59-4433-92eb-3f662d7f7db0).</span></span> <span data-ttu-id="4da49-306">若要轉換的陣列，使用[List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547)或[List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032)。</span><span class="sxs-lookup"><span data-stu-id="4da49-306">To convert to or from an array, use [List.toArray](https://msdn.microsoft.com/library/ac87dd82-a0cd-40b3-b1fa-dd3168134547) or [List.ofArray](https://msdn.microsoft.com/library/f4bddc26-8c8f-4307-a6d7-a49dceb97032).</span></span>


### <a name="additional-operations"></a><span data-ttu-id="4da49-307">其他運算</span><span class="sxs-lookup"><span data-stu-id="4da49-307">Additional Operations</span></span>
<span data-ttu-id="4da49-308">在清單上的其他作業的相關資訊，請參閱程式庫參考主題[Collections.List 模組](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d)。</span><span class="sxs-lookup"><span data-stu-id="4da49-308">For information about additional operations on lists, see the library reference topic [Collections.List Module](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.list-module-%5bfsharp%5d).</span></span>


## <a name="see-also"></a><span data-ttu-id="4da49-309">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4da49-309">See Also</span></span>
[<span data-ttu-id="4da49-310">F# 語言參考</span><span class="sxs-lookup"><span data-stu-id="4da49-310">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="4da49-311">F# 類型</span><span class="sxs-lookup"><span data-stu-id="4da49-311">F# Types</span></span>](fsharp-types.md)

[<span data-ttu-id="4da49-312">序列</span><span class="sxs-lookup"><span data-stu-id="4da49-312">Sequences</span></span>](sequences.md)

[<span data-ttu-id="4da49-313">陣列</span><span class="sxs-lookup"><span data-stu-id="4da49-313">Arrays</span></span>](arrays.md)

[<span data-ttu-id="4da49-314">選項</span><span class="sxs-lookup"><span data-stu-id="4da49-314">Options</span></span>](options.md)
