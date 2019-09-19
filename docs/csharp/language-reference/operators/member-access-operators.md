---
title: 成員存取運算子 - C# 參考
description: 了解可用於存取類型成員的 C# 運算子。
ms.date: 09/18/2019
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
- ^_CSharpKeyword
- .._CSharpKeyword
helpviewer_keywords:
- member access operators [C#]
- member access operator [C#]
- dot operator [C#]
- . operator [C#]
- subscript operator [C#]
- square brackets [] operator [C#]
- indexer operator [C#]
- '[] operator [C#]'
- null-conditional operators [C#]
- Elvis operator [C#]
- ?. operator [C#]
- ?[] operator [C#]
- invocation operator [C#]
- method call [C#]
- method invocation [C#]
- delegate invocation [C#]
- () operator [C#]
- ^ operator [C#]
- index from end operator [C#]
- hat operator [C#]
- .. operator [C#]
- range operator [C#]
ms.openlocfilehash: 45af31d10d77f4c63b27b34595b97fdd11ef95a1
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116137"
---
# <a name="member-access-operators-c-reference"></a><span data-ttu-id="d3513-103">成員存取運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="d3513-103">Member access operators (C# reference)</span></span>

<span data-ttu-id="d3513-104">當您存取類型成員時，可以使用下列運算子：</span><span class="sxs-lookup"><span data-stu-id="d3513-104">You might use the following operators when you access a type member:</span></span>

- <span data-ttu-id="d3513-105">[`.` (成員存取)](#member-access-operator-)：可存取命名空間或類型的成員</span><span class="sxs-lookup"><span data-stu-id="d3513-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="d3513-106">[`[]` (陣列項目或索引子存取)](#indexer-operator-)：可存取陣列項目或類型索引子</span><span class="sxs-lookup"><span data-stu-id="d3513-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="d3513-107">[`?.` 和 `?[]` (Null 條件運算子)](#null-conditional-operators--and-)：只有在運算元為非 Null 時，才可執行成員或項目存取作業</span><span class="sxs-lookup"><span data-stu-id="d3513-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="d3513-108">[`()` (引動流程)](#invocation-operator-)：可呼叫存取的方法或叫用委派</span><span class="sxs-lookup"><span data-stu-id="d3513-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="d3513-109">[（從 end 開始的索引）：表示元素位置是從序列結尾`^` ](#index-from-end-operator-)</span><span class="sxs-lookup"><span data-stu-id="d3513-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="d3513-110">（範圍）：指定可用於取得序列元素範圍的索引範圍[ `..` ](#range-operator-)</span><span class="sxs-lookup"><span data-stu-id="d3513-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="d3513-111">成員存取運算子 .</span><span class="sxs-lookup"><span data-stu-id="d3513-111">Member access operator .</span></span>

<span data-ttu-id="d3513-112">您會使用 `.` 語彙基元來存取命名空間或類型的成員，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="d3513-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="d3513-113">使用 `.` 來存取命名空間內的巢狀命名空間，如下列 [`using` 指示詞](../keywords/using-directive.md)的範例所示：</span><span class="sxs-lookup"><span data-stu-id="d3513-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="d3513-114">使用 `.` 來形成「限定名稱」以存取命名空間內的類型，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="d3513-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="d3513-115">使用 [`using` 指示詞](../keywords/using-directive.md)來使限定名稱的使用為選擇性。</span><span class="sxs-lookup"><span data-stu-id="d3513-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="d3513-116">使用 `.` 來存取[類型成員](../../programming-guide/classes-and-structs/index.md#members) (靜態及非靜態)，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="d3513-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="d3513-117">您也可以使用 `.` 來存取[擴充方法](../../programming-guide/classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="d3513-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="d3513-118">索引子運算子 []</span><span class="sxs-lookup"><span data-stu-id="d3513-118">Indexer operator []</span></span>

<span data-ttu-id="d3513-119">中括弧 (`[]`) 通常用於陣列、索引子或指標元素存取。</span><span class="sxs-lookup"><span data-stu-id="d3513-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="d3513-120">陣列存取</span><span class="sxs-lookup"><span data-stu-id="d3513-120">Array access</span></span>

<span data-ttu-id="d3513-121">以下範例將示範如何存取陣列元素：</span><span class="sxs-lookup"><span data-stu-id="d3513-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="d3513-122">如果陣列索引超出陣列的對應維度界限，就會擲回 <xref:System.IndexOutOfRangeException>。</span><span class="sxs-lookup"><span data-stu-id="d3513-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="d3513-123">如上述範例所示，您也會在宣告陣列類型或將陣列執行個體具現化時使用方括弧。</span><span class="sxs-lookup"><span data-stu-id="d3513-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="d3513-124">如需陣列的詳細資訊，請參閱[陣列](../../programming-guide/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d3513-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="d3513-125">索引子存取</span><span class="sxs-lookup"><span data-stu-id="d3513-125">Indexer access</span></span>

<span data-ttu-id="d3513-126">下列範例使用 .NET<xref:System.Collections.Generic.Dictionary%602> 類型示範索引子存取：</span><span class="sxs-lookup"><span data-stu-id="d3513-126">The following example uses .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="d3513-127">索引子可讓您透過與陣列編製索引類似的方式，為使用者定義型別的執行個體編製索引。</span><span class="sxs-lookup"><span data-stu-id="d3513-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="d3513-128">與必須是整數的陣列索引不同，索引子引數可以宣告為任何類型。</span><span class="sxs-lookup"><span data-stu-id="d3513-128">Unlike array indices, which must be integer, the indexer arguments can be declared to be of any type.</span></span>

<span data-ttu-id="d3513-129">如需索引子的詳細資訊，請參閱[索引子](../../programming-guide/indexers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d3513-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="d3513-130">[] 的其他用法</span><span class="sxs-lookup"><span data-stu-id="d3513-130">Other usages of []</span></span>

<span data-ttu-id="d3513-131">如需有關指標元素存取的相關資訊，請參閱[指標相關運算子](pointer-related-operators.md)一文的[指標元素存取運算子 []](pointer-related-operators.md#pointer-element-access-operator-) 一節。</span><span class="sxs-lookup"><span data-stu-id="d3513-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="d3513-132">您也可以使用中括弧來指定[屬性](../../programming-guide/concepts/attributes/index.md)：</span><span class="sxs-lookup"><span data-stu-id="d3513-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="d3513-133">Null 條件運算子 ?.</span><span class="sxs-lookup"><span data-stu-id="d3513-133">Null-conditional operators ?.</span></span> <span data-ttu-id="d3513-134">和 ?[]</span><span class="sxs-lookup"><span data-stu-id="d3513-134">and ?[]</span></span>

<span data-ttu-id="d3513-135">適用於 C# 6 和更新版本，Null 條件運算子只有在其運算元評估為非 Null 時，才會將成員存取 `?.` 或項目存取 `?[]` 作業套用至該運算元。</span><span class="sxs-lookup"><span data-stu-id="d3513-135">Available in C# 6 and later, a null-conditional operator applies a member access, `?.`, or element access, `?[]`, operation to its operand only if that operand evaluates to non-null.</span></span> <span data-ttu-id="d3513-136">如果運算元評估為 `null`，則套用運算子的結果會是 `null`。</span><span class="sxs-lookup"><span data-stu-id="d3513-136">If the operand evaluates to `null`, the result of applying the operator is `null`.</span></span> <span data-ttu-id="d3513-137">Null 條件成員存取運算子 `?.` 也被稱為 Elvis 運算子。</span><span class="sxs-lookup"><span data-stu-id="d3513-137">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

<span data-ttu-id="d3513-138">Null 條件運算子會執行最少運算。</span><span class="sxs-lookup"><span data-stu-id="d3513-138">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="d3513-139">換句話說，如果條件式成員或項目存取作業鏈結中的一個作業傳回 `null`，則鏈結的其餘部分不會執行。</span><span class="sxs-lookup"><span data-stu-id="d3513-139">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="d3513-140">在下列範例中，如果 `A` 評估為 `null`，則不會評估 `B`；如果 `A` 或 `B` 評估為 `null`，則不會評估 `C`：</span><span class="sxs-lookup"><span data-stu-id="d3513-140">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="d3513-141">下列範例示範 `?.` 和 `?[]` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="d3513-141">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="d3513-142">上述範例也示範 [Null 聯合運算子](null-coalescing-operator.md)的用法。</span><span class="sxs-lookup"><span data-stu-id="d3513-142">The preceding example also shows the usage of the [null-coalescing operator](null-coalescing-operator.md).</span></span> <span data-ttu-id="d3513-143">您可以使用 Null 聯合運算子，在 Null 條件運算的結果為 `null` 時提供用於評估的替代運算式。</span><span class="sxs-lookup"><span data-stu-id="d3513-143">You might use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the null-conditional operation is `null`.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="d3513-144">安全執行緒委派引動流程</span><span class="sxs-lookup"><span data-stu-id="d3513-144">Thread-safe delegate invocation</span></span>

<span data-ttu-id="d3513-145">使用 `?.` 運算子來檢查委派是否為非 Null，然後以安全執行緒方式叫用它 (例如當您[引發事件](../../../standard/events/how-to-raise-and-consume-events.md)時)，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="d3513-145">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="d3513-146">該程式碼等同於您用於 C# 5 或舊版的下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="d3513-146">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="d3513-147">引動過程運算子 ()</span><span class="sxs-lookup"><span data-stu-id="d3513-147">Invocation operator ()</span></span>

<span data-ttu-id="d3513-148">使用括弧 `()` 來呼叫[方法](../../programming-guide/classes-and-structs/methods.md)或叫用[委派](../../programming-guide/delegates/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d3513-148">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="d3513-149">下列範例示範如何呼叫方法 (使用或不使用引數)，以及叫用委派：</span><span class="sxs-lookup"><span data-stu-id="d3513-149">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="d3513-150">當您使用 [`new`](new-operator.md) 運算子叫用[建構函式](../../programming-guide/classes-and-structs/constructors.md)時，您也會使用括號。</span><span class="sxs-lookup"><span data-stu-id="d3513-150">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="d3513-151">() 的其他用法</span><span class="sxs-lookup"><span data-stu-id="d3513-151">Other usages of ()</span></span>

<span data-ttu-id="d3513-152">您也可以使用括弧來調整評估運算式中作業的順序。</span><span class="sxs-lookup"><span data-stu-id="d3513-152">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="d3513-153">如需詳細資訊，請參閱 [C# 運算子](index.md)。</span><span class="sxs-lookup"><span data-stu-id="d3513-153">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="d3513-154">[Cast 運算式](type-testing-and-cast.md#cast-operator-) \(其能執行明確類型轉換\) 也會使用括號。</span><span class="sxs-lookup"><span data-stu-id="d3513-154">[Cast expressions](type-testing-and-cast.md#cast-operator-), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="d3513-155">來自 end 運算子 ^ 的索引</span><span class="sxs-lookup"><span data-stu-id="d3513-155">Index from end operator ^</span></span>

<span data-ttu-id="d3513-156">在 8.0 C#和更新版本中提供`^` ，運算子表示從序列結尾處的元素位置。</span><span class="sxs-lookup"><span data-stu-id="d3513-156">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="d3513-157">針對長度`length`的序列， `^n`會指向具有從序列開頭位移`length - n`的元素。</span><span class="sxs-lookup"><span data-stu-id="d3513-157">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="d3513-158">例如， `^1`指向序列的最後一個專案，並`^length`指向序列的第一個元素。</span><span class="sxs-lookup"><span data-stu-id="d3513-158">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="d3513-159">如上述範例所示，expression `^e` <xref:System.Index?displayProperty=nameWithType>的類型為。</span><span class="sxs-lookup"><span data-stu-id="d3513-159">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="d3513-160">在 expression `^e`中，的`e`結果必須可以隱含地轉換`int`為。</span><span class="sxs-lookup"><span data-stu-id="d3513-160">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="d3513-161">您也可以搭配使用`^`運算子與[範圍運算子](#range-operator-)來建立索引的範圍。</span><span class="sxs-lookup"><span data-stu-id="d3513-161">You also can use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="d3513-162">如需詳細資訊，請參閱[索引和範圍](../../tutorials/ranges-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="d3513-162">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="d3513-163">範圍運算子.。</span><span class="sxs-lookup"><span data-stu-id="d3513-163">Range operator ..</span></span>

<span data-ttu-id="d3513-164">在 8.0 C#和更新版本中提供`..` ，運算子會將索引範圍的開始和結束指定為其運算元。</span><span class="sxs-lookup"><span data-stu-id="d3513-164">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="d3513-165">左側運算元是範圍的*內含*開頭。</span><span class="sxs-lookup"><span data-stu-id="d3513-165">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="d3513-166">右運算元是範圍的*獨佔*結束。</span><span class="sxs-lookup"><span data-stu-id="d3513-166">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="d3513-167">其中一個運算元可以是從序列開頭或結尾的索引，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="d3513-167">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="d3513-168">如上述範例所示，expression `a..b` <xref:System.Range?displayProperty=nameWithType>的類型為。</span><span class="sxs-lookup"><span data-stu-id="d3513-168">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="d3513-169">在 expression `a..b`中， `a`和`b`的結果必須可以隱含地轉換`int`為<xref:System.Index>或。</span><span class="sxs-lookup"><span data-stu-id="d3513-169">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="d3513-170">您可以省略`..`運算子的任何運算元，以取得開放式結束範圍：</span><span class="sxs-lookup"><span data-stu-id="d3513-170">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="d3513-171">`a..`相當於`a..^0`</span><span class="sxs-lookup"><span data-stu-id="d3513-171">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="d3513-172">`..b`相當於`0..b`</span><span class="sxs-lookup"><span data-stu-id="d3513-172">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="d3513-173">`..`相當於`0..^0`</span><span class="sxs-lookup"><span data-stu-id="d3513-173">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="d3513-174">如需詳細資訊，請參閱[索引和範圍](../../tutorials/ranges-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="d3513-174">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="d3513-175">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="d3513-175">Operator overloadability</span></span>

<span data-ttu-id="d3513-176">`.` 、`^`、和運算子`..`無法多載。 `()`</span><span class="sxs-lookup"><span data-stu-id="d3513-176">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="d3513-177">`[]` 運算子也會視為不可多載的運算子。</span><span class="sxs-lookup"><span data-stu-id="d3513-177">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="d3513-178">請使用[索引子](../../programming-guide/indexers/index.md)以支援使用使用者定義型別編製索引。</span><span class="sxs-lookup"><span data-stu-id="d3513-178">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="d3513-179">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="d3513-179">C# language specification</span></span>

<span data-ttu-id="d3513-180">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="d3513-180">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="d3513-181">成員存取</span><span class="sxs-lookup"><span data-stu-id="d3513-181">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="d3513-182">項目存取</span><span class="sxs-lookup"><span data-stu-id="d3513-182">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="d3513-183">Null 條件運算子</span><span class="sxs-lookup"><span data-stu-id="d3513-183">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="d3513-184">引動流程運算式</span><span class="sxs-lookup"><span data-stu-id="d3513-184">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a><span data-ttu-id="d3513-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3513-185">See also</span></span>

- [<span data-ttu-id="d3513-186">C# 參考</span><span class="sxs-lookup"><span data-stu-id="d3513-186">C# reference</span></span>](../index.md)
- [<span data-ttu-id="d3513-187">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="d3513-187">C# operators</span></span>](index.md)
- [<span data-ttu-id="d3513-188">?? (Null 聯合運算子)</span><span class="sxs-lookup"><span data-stu-id="d3513-188">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="d3513-189">:: 運算子</span><span class="sxs-lookup"><span data-stu-id="d3513-189">:: operator</span></span>](namespace-alias-qualifier.md)
