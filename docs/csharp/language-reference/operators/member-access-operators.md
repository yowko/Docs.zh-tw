---
title: 成員存取運算子 - C# 參考
description: 了解可用於存取類型成員的 C# 運算子。
ms.date: 05/09/2019
author: pkulikov
f1_keywords:
- ._CSharpKeyword
- '[]_CSharpKeyword'
- ()_CSharpKeyword
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
ms.openlocfilehash: 4f1d79497f255f52a87dce44f1b5b8709adfada7
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67401478"
---
# <a name="member-access-operators-c-reference"></a><span data-ttu-id="06e57-103">成員存取運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="06e57-103">Member access operators (C# reference)</span></span>

<span data-ttu-id="06e57-104">當您存取類型成員時，可以使用下列運算子：</span><span class="sxs-lookup"><span data-stu-id="06e57-104">You might use the following operators when you access a type member:</span></span>

- <span data-ttu-id="06e57-105">[`.` (成員存取)](#member-access-operator-)：可存取命名空間或類型的成員</span><span class="sxs-lookup"><span data-stu-id="06e57-105">[`.` (member access)](#member-access-operator-): to access a member of a namespace or a type</span></span>
- <span data-ttu-id="06e57-106">[`[]` (陣列項目或索引子存取)](#indexer-operator-)：可存取陣列項目或類型索引子</span><span class="sxs-lookup"><span data-stu-id="06e57-106">[`[]` (array element or indexer access)](#indexer-operator-): to access an array element or a type indexer</span></span>
- <span data-ttu-id="06e57-107">[`?.` 和 `?[]` (Null 條件運算子)](#null-conditional-operators--and-)：只有在運算元為非 Null 時，才可執行成員或項目存取作業</span><span class="sxs-lookup"><span data-stu-id="06e57-107">[`?.` and `?[]` (null-conditional operators)](#null-conditional-operators--and-): to perform a member or element access operation only if an operand is non-null</span></span>
- <span data-ttu-id="06e57-108">[`()` (引動流程)](#invocation-operator-)：可呼叫存取的方法或叫用委派</span><span class="sxs-lookup"><span data-stu-id="06e57-108">[`()` (invocation)](#invocation-operator-): to call an accessed method or invoke a delegate</span></span>

## <a name="member-access-operator-"></a><span data-ttu-id="06e57-109">成員存取運算子 .</span><span class="sxs-lookup"><span data-stu-id="06e57-109">Member access operator .</span></span>

<span data-ttu-id="06e57-110">您會使用 `.` 語彙基元來存取命名空間或類型的成員，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="06e57-110">You use the `.` token to access a member of a namespace or a type, as the following examples demonstrate:</span></span>

- <span data-ttu-id="06e57-111">使用 `.` 來存取命名空間內的巢狀命名空間，如下列 [`using` 指示詞](../keywords/using-directive.md)的範例所示：</span><span class="sxs-lookup"><span data-stu-id="06e57-111">Use `.` to access a nested namespace within a namespace, as the following example of a [`using` directive](../keywords/using-directive.md) shows:</span></span>

  [!code-csharp[nested namespaces](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NestedNamespace)]

- <span data-ttu-id="06e57-112">使用 `.` 來形成「限定名稱」  以存取命名空間內的類型，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="06e57-112">Use `.` to form a *qualified name* to access a type within a namespace, as the following code shows:</span></span>

  [!code-csharp[qualified name](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#QualifiedName)]

  <span data-ttu-id="06e57-113">使用 [`using` 指示詞](../keywords/using-directive.md)來使限定名稱的使用為選擇性。</span><span class="sxs-lookup"><span data-stu-id="06e57-113">Use a [`using` directive](../keywords/using-directive.md) to make the use of qualified names optional.</span></span>

- <span data-ttu-id="06e57-114">使用 `.` 來存取[類型成員](../../programming-guide/classes-and-structs/index.md#members) (靜態及非靜態)，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="06e57-114">Use `.` to access [type members](../../programming-guide/classes-and-structs/index.md#members), static and non-static, as the following code shows:</span></span>

  [!code-csharp-interactive[type members](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#TypeMemberAccess)]

<span data-ttu-id="06e57-115">您也可以使用 `.` 來存取[擴充方法](../../programming-guide/classes-and-structs/extension-methods.md)。</span><span class="sxs-lookup"><span data-stu-id="06e57-115">You can also use `.` to access an [extension method](../../programming-guide/classes-and-structs/extension-methods.md).</span></span>

## <a name="indexer-operator-"></a><span data-ttu-id="06e57-116">索引子運算子 []</span><span class="sxs-lookup"><span data-stu-id="06e57-116">Indexer operator []</span></span>

<span data-ttu-id="06e57-117">中括弧 (`[]`) 通常用於陣列、索引子或指標元素存取。</span><span class="sxs-lookup"><span data-stu-id="06e57-117">Square brackets, `[]`, are typically used for array, indexer, or pointer element access.</span></span>

### <a name="array-access"></a><span data-ttu-id="06e57-118">陣列存取</span><span class="sxs-lookup"><span data-stu-id="06e57-118">Array access</span></span>

<span data-ttu-id="06e57-119">以下範例將示範如何存取陣列元素：</span><span class="sxs-lookup"><span data-stu-id="06e57-119">The following example demonstrates how to access array elements:</span></span>

[!code-csharp-interactive[array access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Arrays)]

<span data-ttu-id="06e57-120">如果陣列索引超出陣列的對應維度界限，就會擲回 <xref:System.IndexOutOfRangeException>。</span><span class="sxs-lookup"><span data-stu-id="06e57-120">If an array index is outside the bounds of the corresponding dimension of an array, an <xref:System.IndexOutOfRangeException> is thrown.</span></span>

<span data-ttu-id="06e57-121">如上述範例所示，您也會在宣告陣列類型或將陣列執行個體具現化時使用方括弧。</span><span class="sxs-lookup"><span data-stu-id="06e57-121">As the preceding example shows, you also use square brackets when you declare an array type or instantiate an array instance.</span></span>

<span data-ttu-id="06e57-122">如需陣列的詳細資訊，請參閱[陣列](../../programming-guide/arrays/index.md)。</span><span class="sxs-lookup"><span data-stu-id="06e57-122">For more information about arrays, see [Arrays](../../programming-guide/arrays/index.md).</span></span>

### <a name="indexer-access"></a><span data-ttu-id="06e57-123">索引子存取</span><span class="sxs-lookup"><span data-stu-id="06e57-123">Indexer access</span></span>

<span data-ttu-id="06e57-124">下列範例使用 .NET<xref:System.Collections.Generic.Dictionary%602> 類型示範索引子存取：</span><span class="sxs-lookup"><span data-stu-id="06e57-124">The following example uses .NET <xref:System.Collections.Generic.Dictionary%602> type to demonstrate indexer access:</span></span>

[!code-csharp-interactive[indexer access](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Indexers)]

<span data-ttu-id="06e57-125">索引子可讓您透過與陣列編製索引類似的方式，為使用者定義型別的執行個體編製索引。</span><span class="sxs-lookup"><span data-stu-id="06e57-125">Indexers allow you to index instances of a user-defined type in the similar way as array indexing.</span></span> <span data-ttu-id="06e57-126">與必須是整數的陣列索引不同，索引子引數可以宣告為任何類型。</span><span class="sxs-lookup"><span data-stu-id="06e57-126">Unlike array indices, which must be integer, the indexer arguments can be declared to be of any type.</span></span>

<span data-ttu-id="06e57-127">如需索引子的詳細資訊，請參閱[索引子](../../programming-guide/indexers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="06e57-127">For more information about indexers, see [Indexers](../../programming-guide/indexers/index.md).</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="06e57-128">[] 的其他用法</span><span class="sxs-lookup"><span data-stu-id="06e57-128">Other usages of []</span></span>

<span data-ttu-id="06e57-129">如需有關指標元素存取的相關資訊，請參閱[指標相關運算子](pointer-related-operators.md)一文的[指標元素存取運算子 []](pointer-related-operators.md#pointer-element-access-operator-) 一節。</span><span class="sxs-lookup"><span data-stu-id="06e57-129">For information about pointer element access, see the [Pointer element access operator []](pointer-related-operators.md#pointer-element-access-operator-) section of the [Pointer related operators](pointer-related-operators.md) article.</span></span>

<span data-ttu-id="06e57-130">您也可以使用中括弧來指定[屬性](../../programming-guide/concepts/attributes/index.md)：</span><span class="sxs-lookup"><span data-stu-id="06e57-130">You also use square brackets to specify [attributes](../../programming-guide/concepts/attributes/index.md):</span></span>

```csharp
[System.Diagnostics.Conditional("DEBUG")]
void TraceMethod() {}
```

## <a name="null-conditional-operators--and-"></a><span data-ttu-id="06e57-131">Null 條件運算子 ?.</span><span class="sxs-lookup"><span data-stu-id="06e57-131">Null-conditional operators ?.</span></span> <span data-ttu-id="06e57-132">和 ?[]</span><span class="sxs-lookup"><span data-stu-id="06e57-132">and ?[]</span></span>

<span data-ttu-id="06e57-133">適用於 C# 6 和更新版本，Null 條件運算子只有在其運算元評估為非 Null 時，才會將成員存取 `?.` 或項目存取 `?[]` 作業套用至該運算元。</span><span class="sxs-lookup"><span data-stu-id="06e57-133">Available in C# 6 and later, a null-conditional operator applies a member access, `?.`, or element access, `?[]`, operation to its operand only if that operand evaluates to non-null.</span></span> <span data-ttu-id="06e57-134">如果運算元評估為 `null`，則套用運算子的結果會是 `null`。</span><span class="sxs-lookup"><span data-stu-id="06e57-134">If the operand evaluates to `null`, the result of applying the operator is `null`.</span></span> <span data-ttu-id="06e57-135">Null 條件成員存取運算子 `?.` 也被稱為 Elvis 運算子。</span><span class="sxs-lookup"><span data-stu-id="06e57-135">The null-conditional member access operator `?.` is also known as the Elvis operator.</span></span>

<span data-ttu-id="06e57-136">Null 條件運算子會執行最少運算。</span><span class="sxs-lookup"><span data-stu-id="06e57-136">The null-conditional operators are short-circuiting.</span></span> <span data-ttu-id="06e57-137">換句話說，如果條件式成員或項目存取作業鏈結中的一個作業傳回 `null`，則鏈結的其餘部分不會執行。</span><span class="sxs-lookup"><span data-stu-id="06e57-137">That is, if one operation in a chain of conditional member or element access operations returns `null`, the rest of the chain doesn't execute.</span></span> <span data-ttu-id="06e57-138">在下列範例中，如果 `A` 評估為 `null`，則不會評估 `B`；如果 `A` 或 `B` 評估為 `null`，則不會評估 `C`：</span><span class="sxs-lookup"><span data-stu-id="06e57-138">In the following example, `B` is not evaluated if `A` evaluates to `null` and `C` is not evaluated if `A` or `B` evaluates to `null`:</span></span>

```csharp
A?.B?.Do(C);
A?.B?[C];
```

<span data-ttu-id="06e57-139">下列範例示範 `?.` 和 `?[]` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="06e57-139">The following example demonstrates the usage of the `?.` and `?[]` operators:</span></span>

[!code-csharp-interactive[null-conditional operators](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#NullConditional)]

<span data-ttu-id="06e57-140">上述範例也示範 [Null 聯合運算子](null-coalescing-operator.md)的用法。</span><span class="sxs-lookup"><span data-stu-id="06e57-140">The preceding example also shows the usage of the [null-coalescing operator](null-coalescing-operator.md).</span></span> <span data-ttu-id="06e57-141">您可以使用 Null 聯合運算子，在 Null 條件運算的結果為 `null` 時提供用於評估的替代運算式。</span><span class="sxs-lookup"><span data-stu-id="06e57-141">You might use the null-coalescing operator to provide an alternative expression to evaluate in case the result of the null-conditional operation is `null`.</span></span>

### <a name="thread-safe-delegate-invocation"></a><span data-ttu-id="06e57-142">安全執行緒委派引動流程</span><span class="sxs-lookup"><span data-stu-id="06e57-142">Thread-safe delegate invocation</span></span>

<span data-ttu-id="06e57-143">使用 `?.` 運算子來檢查委派是否為非 Null，然後以安全執行緒方式叫用它 (例如當您[引發事件](../../../standard/events/how-to-raise-and-consume-events.md)時)，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="06e57-143">Use the `?.` operator to check if a delegate is non-null and invoke it in a thread-safe way (for example, when you [raise an event](../../../standard/events/how-to-raise-and-consume-events.md)), as the following code shows:</span></span>

```csharp
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="06e57-144">該程式碼等同於您用於 C# 5 或舊版的下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="06e57-144">That code is equivalent to the following code that you would use in C# 5 or earlier:</span></span>

```csharp
var handler = this.PropertyChanged;
if (handler != null)
{
    handler(…);
}
```

## <a name="invocation-operator-"></a><span data-ttu-id="06e57-145">引動過程運算子 ()</span><span class="sxs-lookup"><span data-stu-id="06e57-145">Invocation operator ()</span></span>

<span data-ttu-id="06e57-146">使用括弧 `()` 來呼叫[方法](../../programming-guide/classes-and-structs/methods.md)或叫用[委派](../../programming-guide/delegates/index.md)。</span><span class="sxs-lookup"><span data-stu-id="06e57-146">Use parentheses, `()`, to call a [method](../../programming-guide/classes-and-structs/methods.md) or invoke a [delegate](../../programming-guide/delegates/index.md).</span></span>

<span data-ttu-id="06e57-147">下列範例示範如何呼叫方法 (使用或不使用引數)，以及叫用委派：</span><span class="sxs-lookup"><span data-stu-id="06e57-147">The following example demonstrates how to call a method, with or without arguments, and invoke a delegate:</span></span>

[!code-csharp-interactive[invocation with ()](~/samples/csharp/language-reference/operators/MemberAccessOperators.cs#Invocation)]

<span data-ttu-id="06e57-148">當您使用 [`new`](new-operator.md) 運算子叫用[建構函式](../../programming-guide/classes-and-structs/constructors.md)時，您也會使用括號。</span><span class="sxs-lookup"><span data-stu-id="06e57-148">You also use parentheses when you invoke a [constructor](../../programming-guide/classes-and-structs/constructors.md) with the [`new`](new-operator.md) operator.</span></span>

### <a name="other-usages-of-"></a><span data-ttu-id="06e57-149">() 的其他用法</span><span class="sxs-lookup"><span data-stu-id="06e57-149">Other usages of ()</span></span>

<span data-ttu-id="06e57-150">您也可以使用括號來指定評估運算式中作業的順序。</span><span class="sxs-lookup"><span data-stu-id="06e57-150">You also use parentheses to specify the order in which to evaluate operations in an expression.</span></span> <span data-ttu-id="06e57-151">如需詳細資訊，請參閱[運算子](../../programming-guide/statements-expressions-operators/operators.md)一文的[新增括號](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses)小節。</span><span class="sxs-lookup"><span data-stu-id="06e57-151">For more information, see the [Adding parentheses](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) section of the [Operators](../../programming-guide/statements-expressions-operators/operators.md) article.</span></span> <span data-ttu-id="06e57-152">對於按優先順序層級排序的運算子清單，請參閱 [C# 運算子](index.md)。</span><span class="sxs-lookup"><span data-stu-id="06e57-152">For the list of operators ordered by precedence level, see [C# operators](index.md).</span></span>

<span data-ttu-id="06e57-153">[Cast 運算式](type-testing-and-conversion-operators.md#cast-operator-) \(其能執行明確類型轉換\) 也會使用括號。</span><span class="sxs-lookup"><span data-stu-id="06e57-153">[Cast expressions](type-testing-and-conversion-operators.md#cast-operator-), which perform explicit type conversions, also use parentheses.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="06e57-154">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="06e57-154">Operator overloadability</span></span>

<span data-ttu-id="06e57-155">`.` 和 `()` 運算子無法多載。</span><span class="sxs-lookup"><span data-stu-id="06e57-155">The `.` and `()` operators cannot be overloaded.</span></span> <span data-ttu-id="06e57-156">`[]` 運算子也會視為不可多載的運算子。</span><span class="sxs-lookup"><span data-stu-id="06e57-156">The `[]` operator is also considered a non-overloadable operator.</span></span> <span data-ttu-id="06e57-157">請使用[索引子](../../programming-guide/indexers/index.md)以支援使用使用者定義型別編製索引。</span><span class="sxs-lookup"><span data-stu-id="06e57-157">Use [indexers](../../programming-guide/indexers/index.md) to support indexing with user-defined types.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="06e57-158">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="06e57-158">C# language specification</span></span>

<span data-ttu-id="06e57-159">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的下列幾節：</span><span class="sxs-lookup"><span data-stu-id="06e57-159">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="06e57-160">成員存取</span><span class="sxs-lookup"><span data-stu-id="06e57-160">Member access</span></span>](~/_csharplang/spec/expressions.md#member-access)
- [<span data-ttu-id="06e57-161">項目存取</span><span class="sxs-lookup"><span data-stu-id="06e57-161">Element access</span></span>](~/_csharplang/spec/expressions.md#element-access)
- [<span data-ttu-id="06e57-162">Null 條件運算子</span><span class="sxs-lookup"><span data-stu-id="06e57-162">Null-conditional operator</span></span>](~/_csharplang/spec/expressions.md#null-conditional-operator)
- [<span data-ttu-id="06e57-163">引動流程運算式</span><span class="sxs-lookup"><span data-stu-id="06e57-163">Invocation expressions</span></span>](~/_csharplang/spec/expressions.md#invocation-expressions)

## <a name="see-also"></a><span data-ttu-id="06e57-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06e57-164">See also</span></span>

- [<span data-ttu-id="06e57-165">C# 參考</span><span class="sxs-lookup"><span data-stu-id="06e57-165">C# reference</span></span>](../index.md)
- [<span data-ttu-id="06e57-166">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="06e57-166">C# operators</span></span>](index.md)
- [<span data-ttu-id="06e57-167">?? (Null 聯合運算子)</span><span class="sxs-lookup"><span data-stu-id="06e57-167">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)
