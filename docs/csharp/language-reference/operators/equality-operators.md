---
title: 等號比較運算子 - C# 參考
description: 深入了解 C# 等號比較運算子與 C# 型別等號。
ms.date: 10/30/2020
author: pkulikov
f1_keywords:
- ==_CSharpKeyword
- '!=_CSharpKeyword'
helpviewer_keywords:
- comparison operators [C#]
- relational operators [C#]
- equality operator [C#]
- equals operator [C#]
- == operator [C#]
- inequality operator [C#]
- not equals operator [C#]
- '!= operator [C#]'
ms.openlocfilehash: 39461157c33fea0effb5c8808ded1c9981900e17
ms.sourcegitcommit: b1442669f1982d3a1cb18ea35b5acfb0fc7d93e4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/30/2020
ms.locfileid: "93063211"
---
# <a name="equality-operators-c-reference"></a><span data-ttu-id="b79d6-103">等號比較運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="b79d6-103">Equality operators (C# reference)</span></span>

<span data-ttu-id="b79d6-104">[ `==` (相等) ](#equality-operator-)和[ `!=` (不相等) ](#inequality-operator-)運算子會檢查其運算元是否相等。</span><span class="sxs-lookup"><span data-stu-id="b79d6-104">The [`==` (equality)](#equality-operator-) and [`!=` (inequality)](#inequality-operator-) operators check if their operands are equal or not.</span></span>

## <a name="equality-operator-"></a><span data-ttu-id="b79d6-105">等號比較運算子 ==</span><span class="sxs-lookup"><span data-stu-id="b79d6-105">Equality operator ==</span></span>

<span data-ttu-id="b79d6-106">等號比較運算子 `==` 會在其運算元相等時傳回 `true`，否則傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="b79d6-106">The equality operator `==` returns `true` if its operands are equal, `false` otherwise.</span></span>

### <a name="value-types-equality"></a><span data-ttu-id="b79d6-107">實值型別相等</span><span class="sxs-lookup"><span data-stu-id="b79d6-107">Value types equality</span></span>

<span data-ttu-id="b79d6-108">若他們的值相等時，[內建實值型別](../builtin-types/value-types.md#built-in-value-types)的運算元就會相等：</span><span class="sxs-lookup"><span data-stu-id="b79d6-108">Operands of the [built-in value types](../builtin-types/value-types.md#built-in-value-types) are equal if their values are equal:</span></span>

[!code-csharp-interactive[value types equality](snippets/shared/EqualityOperators.cs#ValueTypesEquality)]

> [!NOTE]
> <span data-ttu-id="b79d6-109">針對 `==` 、、 [ `<` `>` 、 `<=` 和 `>=` ](comparison-operators.md)運算子，如果任何運算元不是數位 (<xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType>) ，則運算的結果為 `false` 。</span><span class="sxs-lookup"><span data-stu-id="b79d6-109">For the `==`, [`<`, `>`, `<=`, and `>=`](comparison-operators.md) operators, if any of the operands is not a number (<xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType>), the result of operation is `false`.</span></span> <span data-ttu-id="b79d6-110">這代表 `NaN` 的值皆不會大於、小於或等於任何其他 `double` (或 `float`) 的值，包括 `NaN`。</span><span class="sxs-lookup"><span data-stu-id="b79d6-110">That means that the `NaN` value is neither greater than, less than, nor equal to any other `double` (or `float`) value, including `NaN`.</span></span> <span data-ttu-id="b79d6-111">如需詳細資訊和範例，請參閱 <xref:System.Double.NaN?displayProperty=nameWithType> 或 <xref:System.Single.NaN?displayProperty=nameWithType> 參考文章。</span><span class="sxs-lookup"><span data-stu-id="b79d6-111">For more information and examples, see the <xref:System.Double.NaN?displayProperty=nameWithType> or <xref:System.Single.NaN?displayProperty=nameWithType> reference article.</span></span>

<span data-ttu-id="b79d6-112">若基礎整數型別的對應值相等時，相同[列舉](../builtin-types/enum.md)類型的兩個運算元就會相等。</span><span class="sxs-lookup"><span data-stu-id="b79d6-112">Two operands of the same [enum](../builtin-types/enum.md) type are equal if the corresponding values of the underlying integral type are equal.</span></span>

<span data-ttu-id="b79d6-113">使用者定義[結構](../builtin-types/struct.md)型別預設不支援 `==` 運算子。</span><span class="sxs-lookup"><span data-stu-id="b79d6-113">User-defined [struct](../builtin-types/struct.md) types don't support the `==` operator by default.</span></span> <span data-ttu-id="b79d6-114">若要支援 `==` 運算子，使用者定義結構必須[多載](operator-overloading.md)它。</span><span class="sxs-lookup"><span data-stu-id="b79d6-114">To support the `==` operator, a user-defined struct must [overload](operator-overloading.md) it.</span></span>

<span data-ttu-id="b79d6-115">從 C# 7.3 說起，`==` 及 `!=` 運算子是由 C# [tuples](../builtin-types/value-tuples.md) 所支援。</span><span class="sxs-lookup"><span data-stu-id="b79d6-115">Beginning with C# 7.3, the `==` and `!=` operators are supported by C# [tuples](../builtin-types/value-tuples.md).</span></span> <span data-ttu-id="b79d6-116">如需詳細資訊，請參閱[元組類型](../builtin-types/value-tuples.md)一文的[元組相等](../builtin-types/value-tuples.md#tuple-equality)區段。</span><span class="sxs-lookup"><span data-stu-id="b79d6-116">For more information, see the [Tuple equality](../builtin-types/value-tuples.md#tuple-equality) section of the [Tuple types](../builtin-types/value-tuples.md) article.</span></span>

### <a name="reference-types-equality"></a><span data-ttu-id="b79d6-117">參考型別相等</span><span class="sxs-lookup"><span data-stu-id="b79d6-117">Reference types equality</span></span>

<span data-ttu-id="b79d6-118">根據預設，如果兩個非記錄的參考型別運算元參考相同的物件，就會相等：</span><span class="sxs-lookup"><span data-stu-id="b79d6-118">By default, two non-record reference-type operands are equal if they refer to the same object:</span></span>

[!code-csharp[reference type equality](snippets/shared/EqualityOperators.cs#ReferenceTypesEquality)]

<span data-ttu-id="b79d6-119">如範例所示，使用者定義參考型別預設支援 `==` 運算子。</span><span class="sxs-lookup"><span data-stu-id="b79d6-119">As the example shows, user-defined reference types support the `==` operator by default.</span></span> <span data-ttu-id="b79d6-120">不過，參考型別可以多載 `==` 運算子。</span><span class="sxs-lookup"><span data-stu-id="b79d6-120">However, a reference type can overload the `==` operator.</span></span> <span data-ttu-id="b79d6-121">若參考型別多載 `==` 運算子，請使用 <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> 方法檢查兩個該類型的參考是否參考相同的物件。</span><span class="sxs-lookup"><span data-stu-id="b79d6-121">If a reference type overloads the `==` operator, use the <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType> method to check if two references of that type refer to the same object.</span></span>

### <a name="record-types-equality"></a><span data-ttu-id="b79d6-122">記錄類型相等</span><span class="sxs-lookup"><span data-stu-id="b79d6-122">Record types equality</span></span>

<span data-ttu-id="b79d6-123">在 c # 9.0 和更新版本中提供， [記錄類型](../../whats-new/csharp-9.md#record-types) 支援 `==` 和 `!=` 運算子，這些運算子預設會提供值相等的語法。</span><span class="sxs-lookup"><span data-stu-id="b79d6-123">Available in C# 9.0 and later, [record types](../../whats-new/csharp-9.md#record-types) support the `==` and `!=` operators that by default provide value equality semantics.</span></span> <span data-ttu-id="b79d6-124">也就是說，當兩個記錄運算元都是 `null` 或所有欄位的對應值，且自動執行的屬性相等時，兩個記錄運算元相等。</span><span class="sxs-lookup"><span data-stu-id="b79d6-124">That is, two record operands are equal when both of them are `null` or corresponding values of all fields and auto-implemented properties are equal.</span></span>

:::code language="csharp" source="snippets/shared/EqualityOperators.cs" id="RecordTypesEquality":::

<span data-ttu-id="b79d6-125">如先前的範例所示，如果是非記錄的參考型別成員，則會比較其參考值，而不是參考的實例。</span><span class="sxs-lookup"><span data-stu-id="b79d6-125">As the preceding example shows, in case of non-record reference-type members their reference values are compared, not the referenced instances.</span></span>

### <a name="string-equality"></a><span data-ttu-id="b79d6-126">字串相等</span><span class="sxs-lookup"><span data-stu-id="b79d6-126">String equality</span></span>

<span data-ttu-id="b79d6-127">當兩個 [string](../builtin-types/reference-types.md#the-string-type) 運算元皆為 `null`，或兩個 string 執行個體的長度相同且在各字元位置擁有完全相同的字元，兩者就會相等：</span><span class="sxs-lookup"><span data-stu-id="b79d6-127">Two [string](../builtin-types/reference-types.md#the-string-type) operands are equal when both of them are `null` or both string instances are of the same length and have identical characters in each character position:</span></span>

[!code-csharp-interactive[string equality](snippets/shared/EqualityOperators.cs#StringEquality)]

<span data-ttu-id="b79d6-128">這是區分大小寫的序數比較。</span><span class="sxs-lookup"><span data-stu-id="b79d6-128">That is a case-sensitive ordinal comparison.</span></span> <span data-ttu-id="b79d6-129">如需有關字串比較的詳細資訊，請參閱[如何在 C# 中比較字串](../../how-to/compare-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="b79d6-129">For more information about string comparison, see [How to compare strings in C#](../../how-to/compare-strings.md).</span></span>

### <a name="delegate-equality"></a><span data-ttu-id="b79d6-130">委派等號</span><span class="sxs-lookup"><span data-stu-id="b79d6-130">Delegate equality</span></span>

<span data-ttu-id="b79d6-131">相同執行階段型別的兩個[委派](../../programming-guide/delegates/index.md)運算元都是 `null` 或其引動過程清單長度相同且每個位置都有相等的項目時，那兩個運算元相等：</span><span class="sxs-lookup"><span data-stu-id="b79d6-131">Two [delegate](../../programming-guide/delegates/index.md) operands of the same runtime type are equal when both of them are `null` or their invocation lists are of the same length and have equal entries in each position:</span></span>

[!code-csharp-interactive[delegate equality](snippets/shared/EqualityOperators.cs#DelegateEquality)]

<span data-ttu-id="b79d6-132">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[委派相等運算子](~/_csharplang/spec/expressions.md#delegate-equality-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="b79d6-132">For more information, see the [Delegate equality operators](~/_csharplang/spec/expressions.md#delegate-equality-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="b79d6-133">從語意相同之 [lambda 運算式](lambda-expressions.md)之評估產生的委派不相等，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b79d6-133">Delegates that are produced from evaluation of semantically identical [lambda expressions](lambda-expressions.md) are not equal, as the following example shows:</span></span>

[!code-csharp-interactive[from identical lambdas](snippets/shared/EqualityOperators.cs#IdenticalLambdas)]

## <a name="inequality-operator-"></a><span data-ttu-id="b79d6-134">不等比較運算子 !=</span><span class="sxs-lookup"><span data-stu-id="b79d6-134">Inequality operator !=</span></span>

<span data-ttu-id="b79d6-135">不等比較運算子 `!=` 會在其運算元不相等時傳回 `true`，否則傳回 `false`。</span><span class="sxs-lookup"><span data-stu-id="b79d6-135">The inequality operator `!=` returns `true` if its operands are not equal, `false` otherwise.</span></span> <span data-ttu-id="b79d6-136">對於[內建類型](../builtin-types/built-in-types.md)的運算元，運算式 `x != y` 會產生與運算式 `!(x == y)` 相同的結果。</span><span class="sxs-lookup"><span data-stu-id="b79d6-136">For the operands of the [built-in types](../builtin-types/built-in-types.md), the expression `x != y` produces the same result as the expression `!(x == y)`.</span></span> <span data-ttu-id="b79d6-137">如需有關型別等號的詳細資訊，請參閱[等號比較運算子](#equality-operator-)一節。</span><span class="sxs-lookup"><span data-stu-id="b79d6-137">For more information about type equality, see the [Equality operator](#equality-operator-) section.</span></span>

<span data-ttu-id="b79d6-138">下列範例示範 `!=` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="b79d6-138">The following example demonstrates the usage of the `!=` operator:</span></span>

[!code-csharp-interactive[non-equality examples](snippets/shared/EqualityOperators.cs#NonEquality)]

## <a name="operator-overloadability"></a><span data-ttu-id="b79d6-139">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="b79d6-139">Operator overloadability</span></span>

<span data-ttu-id="b79d6-140">使用者定義類型可以[多載](operator-overloading.md)`==` 和 `!=` 運算子。</span><span class="sxs-lookup"><span data-stu-id="b79d6-140">A user-defined type can [overload](operator-overloading.md) the `==` and `!=` operators.</span></span> <span data-ttu-id="b79d6-141">如果類型多載這兩個運算子之一，它也必須多載另一個運算子。</span><span class="sxs-lookup"><span data-stu-id="b79d6-141">If a type overloads one of the two operators, it must also overload the other one.</span></span>

<span data-ttu-id="b79d6-142">記錄類型無法明確地多載 `==` and `!=` 運算子。</span><span class="sxs-lookup"><span data-stu-id="b79d6-142">A record type cannot explicitly overload the `==` and `!=` operators.</span></span> <span data-ttu-id="b79d6-143">如果您需要變更 `==` 記錄類型之和運算子的行為 `!=` `T` ，請使用下列簽章來執行 <xref:System.IEquatable%601.Equals%2A?displayProperty=nameWithType> 方法：</span><span class="sxs-lookup"><span data-stu-id="b79d6-143">If you need to change the behavior of the `==` and `!=` operators for record type `T`, implement the <xref:System.IEquatable%601.Equals%2A?displayProperty=nameWithType> method with the following signature:</span></span>

```csharp
public virtual bool Equals(T? other);
```

## <a name="c-language-specification"></a><span data-ttu-id="b79d6-144">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="b79d6-144">C# language specification</span></span>

<span data-ttu-id="b79d6-145">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[關係及類型測試運算子](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="b79d6-145">For more information, see the [Relational and type-testing operators](~/_csharplang/spec/expressions.md#relational-and-type-testing-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="b79d6-146">如需記錄類型是否相等的詳細資訊，請參閱[記錄功能提案附注](~/_csharplang/proposals/csharp-9.0/records.md)的[相等成員](~/_csharplang/proposals/csharp-9.0/records.md#equality-members)一節。</span><span class="sxs-lookup"><span data-stu-id="b79d6-146">For more information about equality of record types, see the [Equality members](~/_csharplang/proposals/csharp-9.0/records.md#equality-members) section of the [records feature proposal note](~/_csharplang/proposals/csharp-9.0/records.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b79d6-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b79d6-147">See also</span></span>

- [<span data-ttu-id="b79d6-148">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="b79d6-148">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b79d6-149">C# 運算子與運算式</span><span class="sxs-lookup"><span data-stu-id="b79d6-149">C# operators and expressions</span></span>](index.md)
- <xref:System.IEquatable%601?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- <xref:System.Object.ReferenceEquals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="b79d6-150">相等比較</span><span class="sxs-lookup"><span data-stu-id="b79d6-150">Equality comparisons</span></span>](../../programming-guide/statements-expressions-operators/equality-comparisons.md)
- [<span data-ttu-id="b79d6-151">比較運算子</span><span class="sxs-lookup"><span data-stu-id="b79d6-151">Comparison operators</span></span>](comparison-operators.md)
