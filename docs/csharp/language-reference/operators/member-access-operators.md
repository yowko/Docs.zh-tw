---
title: 成員存取運算子與表示式 - C# 引用
description: 了解可用於存取類型成員的 C# 運算子。
ms.date: 03/31/2020
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
ms.openlocfilehash: 90066b1e9c219f66fc0c76423679e81aa3fa6770
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/11/2020
ms.locfileid: "81120987"
---
# <a name="member-access-operators-and-expressions-c-reference"></a><span data-ttu-id="89b41-103">成員存取運算子與表示式(C# 引用)</span><span class="sxs-lookup"><span data-stu-id="89b41-103">Member access operators and expressions (C# reference)</span></span>

<span data-ttu-id="89b41-104">存取類型成員時,可以使用以下運算子和表示式:</span><span class="sxs-lookup"><span data-stu-id="89b41-104">You can use the following operators and expressions when you access a type member:</span></span>

- <span data-ttu-id="89b41-105">(成員存取):存取命名空間或類型[`.`](#member-access-expression-)的成員</span><span class="sxs-lookup"><span data-stu-id="89b41-105">[`.` (member access)](#member-access-expression-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="89b41-106">[(陣列元素或索引器存取): 存取陣列元素或類型`[]`索引器](#indexer-operator-)</span><span class="sxs-lookup"><span data-stu-id="89b41-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="89b41-107">[與`?[]`條件運算子:僅在操作數為非空時執行成員或元素`?.`](#null-conditional-operators--and-)存取操作</span><span class="sxs-lookup"><span data-stu-id="89b41-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="89b41-108">(呼叫) :呼叫被存取的方法或呼[`()`](#invocation-expression-)叫委託</span><span class="sxs-lookup"><span data-stu-id="89b41-108">[`()` (invocation)](#invocation-expression-): to call an accessed method or invoke a delegate</span></span>
- <span data-ttu-id="89b41-109">[(索引從末尾):指示元素位置來自序列的末尾`^`](#index-from-end-operator-)</span><span class="sxs-lookup"><span data-stu-id="89b41-109">[`^` (index from end)](#index-from-end-operator-): to indicate that the element position is from the end of a sequence</span></span>
- <span data-ttu-id="89b41-110">(範圍):指定可用於取得序列元素範圍的索引範圍[`..`](#range-operator-)</span><span class="sxs-lookup"><span data-stu-id="89b41-110">[`..` (range)](#range-operator-): to specify a range of indices that you can use to obtain a range of sequence elements</span></span>

## <a name="member-access-expression-"></a><span data-ttu-id="89b41-111">成員存取式 .</span><span class="sxs-lookup"><span data-stu-id="89b41-111">Member access expression .</span></span>

<span data-ttu-id="89b41-112">您會使用 `.` 語彙基元來存取命名空間或類型的成員，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="89b41-112">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="89b41-113">使用`.`命名空間中的嵌套命名空間,例如[`using`以下指令](../keywords/using-directive.md)範例的範例 :</span><span class="sxs-lookup"><span data-stu-id="89b41-113">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](snippets/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="89b41-114">使用 `.` 來形成「限定名稱」\*\* 以存取命名空間內的類型，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="89b41-114">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](snippets/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="89b41-115">使用[`using`指令](../keywords/using-directive.md)使限定名稱的使用成為可選名稱。</span><span class="sxs-lookup"><span data-stu-id="89b41-115">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="89b41-116">使用 `.` 來存取[類型成員](../../programming-guide/classes-and-structs/index.md#members) (靜態及非靜態)，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="89b41-116">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](snippets/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="89b41-117">您也可以使用 `.` 來存取[擴充方法](../../programming-guide/classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="89b41-117">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="89b41-118">索引子運算子 []</span><span class="sxs-lookup"><span data-stu-id="89b41-118">Indexer operator []</span></span>

<span data-ttu-id="89b41-119">中括弧 (`[]`) 通常用於陣列、索引子或指標元素存取。</span><span class="sxs-lookup"><span data-stu-id="89b41-119">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="89b41-120">陣列存取</span><span class="sxs-lookup"><span data-stu-id="89b41-120">Array access</span></span>

<span data-ttu-id="89b41-121">以下範例將示範如何存取陣列元素：</span><span class="sxs-lookup"><span data-stu-id="89b41-121">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](snippets/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="89b41-122">如果陣列索引超出陣列的對應維度界限，就會擲回 <xref:System.IndexOutOfRangeException>。</span><span class="sxs-lookup"><span data-stu-id="89b41-122">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="89b41-123">如上述範例所示，您也會在宣告陣列類型或將陣列執行個體具現化時使用方括弧。</span><span class="sxs-lookup"><span data-stu-id="89b41-123">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="89b41-124">如需陣列的詳細資訊，請參閱[陣列](../../programming-guide/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="89b41-124">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="89b41-125">索引子存取</span><span class="sxs-lookup"><span data-stu-id="89b41-125">Indexer access</span></span>

<span data-ttu-id="89b41-126">下面的範例使用 .NET<xref:System.Collections.Generic.Dictionary%602>類型來展示索引器存取:</span><span class="sxs-lookup"><span data-stu-id="89b41-126">The following example uses the .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](snippets/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="89b41-127">索引子可讓您透過與陣列編製索引類似的方式，為使用者定義型別的執行個體編製索引。</span><span class="sxs-lookup"><span data-stu-id="89b41-127">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="89b41-128">與陣列索引(必須整數)不同,索引器參數可以聲明為任何類型的索引器參數。</span><span class="sxs-lookup"><span data-stu-id="89b41-128">Unlike array indices, which must be integer, the indexer parameters can be declared to be of any type.</span></span>

<span data-ttu-id="89b41-129">如需索引子的詳細資訊，請參閱[索引子](../../programming-guide/indexers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="89b41-129">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="89b41-130">[] 的其他用法</span><span class="sxs-lookup"><span data-stu-id="89b41-130">Other usages of []</span></span>

<span data-ttu-id="89b41-131">如需有關指標元素存取的相關資訊，請參閱[指標相關運算子](pointer-related-operators.md)一文的[指標元素存取運算子 []](pointer-related-operators.md#pointer-element-access-operator-) 一節。</span><span class="sxs-lookup"><span data-stu-id="89b41-131">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="89b41-132">您也可以使用中括弧來指定[屬性](../../programming-guide/concepts/attributes/index.md)：</span><span class="sxs-lookup"><span data-stu-id="89b41-132">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="89b41-133">Null 條件運算子 ?.</span><span class="sxs-lookup"><span data-stu-id="89b41-133">Null-conditional operators ?.</span></span> <span data-ttu-id="89b41-134">和 ?[]</span><span class="sxs-lookup"><span data-stu-id="89b41-134">and ?[]</span></span>

<span data-ttu-id="89b41-135">在 C# 6 和更高版本中可用,null 條件運算元`?.`僅當該 操作`?[]`數計算為非 null 時,才會將[成員訪問](#member-access-expression-)、或[元素存取](#indexer-operator-)操作應用於其操作數;否則,它將返回`null`。</span><span class="sxs-lookup"><span data-stu-id="89b41-135">Available in C# 6 and later, a null-conditional operator applies a [member access](#member-access-expression-), `?.`, or [element access](#indexer-operator-), `?[]`, operation to its operand only if that operand evaluates to non-null; otherwise, it returns `null`.</span></span> <span data-ttu-id="89b41-136">那是</span><span class="sxs-lookup"><span data-stu-id="89b41-136">That is,</span></span>

- <span data-ttu-id="89b41-137">如果`a`計算到`null`,`a?.x``a?[x]`結果`null`為 。</span><span class="sxs-lookup"><span data-stu-id="89b41-137">If `a` evaluates to `null`, the result of `a?.x` or `a?[x]` is `null`.</span></span>
- <span data-ttu-id="89b41-138">如果`a`計算為`a?.x`非空,則`a?[x]`或的結果`a.x`與`a[x]`或的結果相同。</span><span class="sxs-lookup"><span data-stu-id="89b41-138">If `a` evaluates to non-null, the result of `a?.x` or `a?[x]` is the same as the result of `a.x` or `a[x]`, respectively.</span></span>

  > [!NOTE]
  > <span data-ttu-id="89b41-139">如果`a.x``a[x]`或引發異常`a?.x`,`a?[x]`或將為非`a`null 引發相同的異常。</span><span class="sxs-lookup"><span data-stu-id="89b41-139">If `a.x` or `a[x]` throws an exception, `a?.x` or `a?[x]` would throw the same exception for non-null `a`.</span></span> <span data-ttu-id="89b41-140">例如,`a`如果是非空陣列實體,並且`x`超出的邊界`a`,`a?[x]`則將引發<xref:System.IndexOutOfRangeException>。</span><span class="sxs-lookup"><span data-stu-id="89b41-140">For example, if `a` is a non-null array instance and `x` is outside the bounds of `a`, `a?[x]` would throw an <xref:System.IndexOutOfRangeException>.</span></span>

<span data-ttu-id="89b41-141">Null 條件運算子會執行最少運算。</span><span class="sxs-lookup"><span data-stu-id="89b41-141">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="89b41-142">換句話說，如果條件式成員或項目存取作業鏈結中的一個作業傳回 `null`，則鏈結的其餘部分不會執行。</span><span class="sxs-lookup"><span data-stu-id="89b41-142">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="89b41-143">在下列範例中，如果 `A` 評估為 `null`，則不會評估 `B`；如果 `A` 或 `B` 評估為 `null`，則不會評估 `C`：</span><span class="sxs-lookup"><span data-stu-id="89b41-143">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="89b41-144">下列範例示範 `?.` 和 `?[]` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="89b41-144">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](snippets/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="89b41-145">前面的範例還使用[null 合併運算`??`符](null-coalescing-operator.md)指定一個替代運算式,以計算 null`null`條件操作的結果為 時計算的運算式。</span><span class="sxs-lookup"><span data-stu-id="89b41-145">The preceding example also uses the [null-coalescing operator `??`](null-coalescing-operator.md) to specify an alternative expression to evaluate in case the result of a null-conditional operation is `null`.</span></span>

<span data-ttu-id="89b41-146">如果`a.x``a[x]`或非空數型態`T``a?.x`,`a?[x]`或是一個[非空白型態 。](../builtin-types/nullable-value-types.md)`T?`</span><span class="sxs-lookup"><span data-stu-id="89b41-146">If `a.x` or `a[x]` is of a non-nullable value type `T`, `a?.x` or `a?[x]` is of the corresponding [nullable value type](../builtin-types/nullable-value-types.md) `T?`.</span></span> <span data-ttu-id="89b41-147">如果需要類型`T`表示式,請將空合併運算子`??`應用於 null 條件表示式,如下例所示:</span><span class="sxs-lookup"><span data-stu-id="89b41-147">If you need an expression of type `T`, apply the null-coalescing operator `??` to a null-conditional expression, as the following example shows:</span></span>

[!code-csharp-interactive[null-conditional with null-coalescing](snippets/MemberAccessOperators.cs#NullConditionalWithNullCoalescing)]

<span data-ttu-id="89b41-148">在`??`前面的範例中,如果不使用運算子,請`numbers?.Length < 2`計算到`false`時`numbers`為`null`。</span><span class="sxs-lookup"><span data-stu-id="89b41-148">In the preceding example, if you don't use the `??` operator, `numbers?.Length < 2` evaluates to `false` when `numbers` is `null`.</span></span>

<span data-ttu-id="89b41-149">Null 條件成員存取運算子 `?.` 也被稱為 Elvis 運算子。</span><span class="sxs-lookup"><span data-stu-id="89b41-149">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="89b41-150">安全執行緒委派引動流程</span><span class="sxs-lookup"><span data-stu-id="89b41-150">Thread-safe delegate invocation</span></span>

<span data-ttu-id="89b41-151">使用 `?.` 運算子來檢查委派是否為非 Null，然後以安全執行緒方式叫用它 (例如當您[引發事件](../../../standard/events/how-to-raise-and-consume-events.md)時)，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="89b41-151">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="89b41-152">該程式碼等同於您用於 C# 5 或舊版的下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="89b41-152">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-expression-"></a><span data-ttu-id="89b41-153">呼叫表示式 ()</span><span class="sxs-lookup"><span data-stu-id="89b41-153">Invocation expression ()</span></span>

<span data-ttu-id="89b41-154">使用括弧 `()` 來呼叫[方法](../../programming-guide/classes-and-structs/methods.md)或叫用[委派](../../programming-guide/delegates/index.md)。</span><span class="sxs-lookup"><span data-stu-id="89b41-154">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="89b41-155">下列範例示範如何呼叫方法 (使用或不使用引數)，以及叫用委派：</span><span class="sxs-lookup"><span data-stu-id="89b41-155">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](snippets/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="89b41-156">當您使用 [`new`](new-operator.md) 運算子叫用[建構函式](../../programming-guide/classes-and-structs/constructors.md)時，您也會使用括號。</span><span class="sxs-lookup"><span data-stu-id="89b41-156">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="89b41-157">() 的其他用法</span><span class="sxs-lookup"><span data-stu-id="89b41-157">Other usages of ()</span></span>

<span data-ttu-id="89b41-158">您也可以使用括弧來調整評估運算式中作業的順序。</span><span class="sxs-lookup"><span data-stu-id="89b41-158">You also use parentheses to adjust the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="89b41-159">如需詳細資訊，請參閱 [C# 運算子](index.md)。</span><span class="sxs-lookup"><span data-stu-id="89b41-159">For more information, see [C# operators](index.md).</span></span>

<span data-ttu-id="89b41-160">[Cast 運算式](type-testing-and-cast.md#cast-expression) \(其能執行明確類型轉換\) 也會使用括號。</span><span class="sxs-lookup"><span data-stu-id="89b41-160">[Cast expressions](type-testing-and-cast.md#cast-expression), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="index-from-end-operator-"></a><span data-ttu-id="89b41-161">來自終端運算子索引 |</span><span class="sxs-lookup"><span data-stu-id="89b41-161">Index from end operator ^</span></span>

<span data-ttu-id="89b41-162">在 C# 8.0`^`及更高 版本中可用,運算符指示序列末尾的元素位置。</span><span class="sxs-lookup"><span data-stu-id="89b41-162">Available in C# 8.0 and later, the `^` operator indicates the element position from the end of a sequence.</span></span> <span data-ttu-id="89b41-163">對於長度`length`序列`^n`, 指向具有序列開頭`length - n`偏移 的元素。</span><span class="sxs-lookup"><span data-stu-id="89b41-163">For a sequence of length `length`, `^n` points to the element with offset `length - n` from the start of a sequence.</span></span> <span data-ttu-id="89b41-164">例如,`^1`指向序列的最後一個元素,`^length`並指向序列的第一個元素。</span><span class="sxs-lookup"><span data-stu-id="89b41-164">For example, `^1` points to the last element of a sequence and `^length` points to the first element of a sequence.</span></span>

[!code-csharp[index from end](snippets/MemberAccessOperators.cs#IndexFromEnd)]

<span data-ttu-id="89b41-165">如前面的示例所示,表達式`^e`是類型<xref:System.Index?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="89b41-165">As the preceding example shows, expression `^e` is of the <xref:System.Index?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="89b41-166">在表示式`^e`中,必須`e`將的結果隱式轉換`int`為 。</span><span class="sxs-lookup"><span data-stu-id="89b41-166">In expression `^e`, the result of `e` must be implicitly convertible to `int`.</span></span>

<span data-ttu-id="89b41-167">您還可以使用運算子`^`與[範圍運算子](#range-operator-)一起建立一系列索引。</span><span class="sxs-lookup"><span data-stu-id="89b41-167">You also can use the `^` operator with the [range operator](#range-operator-) to create a range of indices.</span></span> <span data-ttu-id="89b41-168">有關詳細資訊,請參閱[索引和範圍](../../tutorials/ranges-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="89b41-168">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="range-operator-"></a><span data-ttu-id="89b41-169">範圍運算子 ..</span><span class="sxs-lookup"><span data-stu-id="89b41-169">Range operator ..</span></span>

<span data-ttu-id="89b41-170">在 C# 8.0`..`及更高 版本中提供,運算符指定一系列索引的開始和結束作為其操作數。</span><span class="sxs-lookup"><span data-stu-id="89b41-170">Available in C# 8.0 and later, the `..` operator specifies the start and end of a range of indices as its operands.</span></span> <span data-ttu-id="89b41-171">左側操作數是範圍的*包容性*開始。</span><span class="sxs-lookup"><span data-stu-id="89b41-171">The left-hand operand is an *inclusive* start of a range.</span></span> <span data-ttu-id="89b41-172">右側操作數是範圍的*獨佔*端。</span><span class="sxs-lookup"><span data-stu-id="89b41-172">The right-hand operand is an *exclusive* end of a range.</span></span> <span data-ttu-id="89b41-173">其中任一操作數可以是序列開頭或末尾的索引,如下例所示:</span><span class="sxs-lookup"><span data-stu-id="89b41-173">Either of operands can be an index from the start or from the end of a sequence, as the following example shows:</span></span>

[!code-csharp[range examples](snippets/MemberAccessOperators.cs#Ranges)]

<span data-ttu-id="89b41-174">如前面的示例所示,表達式`a..b`是類型<xref:System.Range?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="89b41-174">As the preceding example shows, expression `a..b` is of the <xref:System.Range?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="89b41-175">在表示式`a..b`中,`a``b`與 的結果必須隱式`int`<xref:System.Index>轉換為 或 。</span><span class="sxs-lookup"><span data-stu-id="89b41-175">In expression `a..b`, the results of `a` and `b` must be implicitly convertible to `int` or <xref:System.Index>.</span></span>

<span data-ttu-id="89b41-176">您可以省略`..`運算子的任何操作數以取得開放式範圍:</span><span class="sxs-lookup"><span data-stu-id="89b41-176">You can omit any of the operands of the `..` operator to obtain an open-ended range:</span></span>

- <span data-ttu-id="89b41-177">`a..`等效於`a..^0`</span><span class="sxs-lookup"><span data-stu-id="89b41-177">`a..` is equivalent to `a..^0`</span></span>
- <span data-ttu-id="89b41-178">`..b`等效於`0..b`</span><span class="sxs-lookup"><span data-stu-id="89b41-178">`..b` is equivalent to `0..b`</span></span>
- <span data-ttu-id="89b41-179">`..`等效於`0..^0`</span><span class="sxs-lookup"><span data-stu-id="89b41-179">`..` is equivalent to `0..^0`</span></span>

[!code-csharp[ranges with omitted operands](snippets/MemberAccessOperators.cs#RangesOptional)]

<span data-ttu-id="89b41-180">有關詳細資訊,請參閱[索引和範圍](../../tutorials/ranges-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="89b41-180">For more information, see [Indices and ranges](../../tutorials/ranges-indexes.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="89b41-181">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="89b41-181">Operator overloadability</span></span>

<span data-ttu-id="89b41-182">不能`.``()`重`^`載`..`、 和運算子。</span><span class="sxs-lookup"><span data-stu-id="89b41-182">The `.`, `()`, `^`, and `..` operators cannot be overloaded.</span></span> <span data-ttu-id="89b41-183">`[]` 運算子也會視為不可多載的運算子。</span><span class="sxs-lookup"><span data-stu-id="89b41-183">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="89b41-184">請使用[索引子](../../programming-guide/indexers/index.md)以支援使用使用者定義型別編製索引。</span><span class="sxs-lookup"><span data-stu-id="89b41-184">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="89b41-185">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="89b41-185">C# language specification</span></span>

<span data-ttu-id="89b41-186">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="89b41-186">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="89b41-187">成員存取</span><span class="sxs-lookup"><span data-stu-id="89b41-187">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="89b41-188">項目存取</span><span class="sxs-lookup"><span data-stu-id="89b41-188">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="89b41-189">Null 條件運算子</span><span class="sxs-lookup"><span data-stu-id="89b41-189">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="89b41-190">引動流程運算式</span><span class="sxs-lookup"><span data-stu-id="89b41-190">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

<span data-ttu-id="89b41-191">有關索引和範圍的詳細資訊,請參閱[功能建議註釋](~/_csharplang/proposals/csharp-8.0/ranges.md)。</span><span class="sxs-lookup"><span data-stu-id="89b41-191">For more information about indices and ranges, see the [feature proposal note](~/_csharplang/proposals/csharp-8.0/ranges.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="89b41-192">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89b41-192">See also</span></span>

- [<span data-ttu-id="89b41-193">C# 參考</span><span class="sxs-lookup"><span data-stu-id="89b41-193">C# reference</span></span>](../index.md)
- [<span data-ttu-id="89b41-194">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="89b41-194">C# operators</span></span>](index.md)
- [<span data-ttu-id="89b41-195">?? (Null 聯合運算子)</span><span class="sxs-lookup"><span data-stu-id="89b41-195">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
- [<span data-ttu-id="89b41-196">:: 運算子</span><span class="sxs-lookup"><span data-stu-id="89b41-196">:: operator</span></span>](namespace-alias-qualifier.md)
