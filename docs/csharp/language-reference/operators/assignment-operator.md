---
description: '指派運算子-c # 參考'
title: '指派運算子-c # 參考'
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 3df118143b692cc8655de31cce23af41f7da125c
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/30/2020
ms.locfileid: "89117879"
---
# <a name="assignment-operators-c-reference"></a><span data-ttu-id="17f45-103">指派運算子 (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="17f45-103">Assignment operators (C# reference)</span></span>

<span data-ttu-id="17f45-104">指派運算子 `=` 會將其右方運算元的值指派給其左方運算元所指定的變數、[屬性](../../programming-guide/classes-and-structs/properties.md)或[索引子](../../programming-guide/indexers/index.md)元素。</span><span class="sxs-lookup"><span data-stu-id="17f45-104">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="17f45-105">指派運算式的結果是指派給左方運算元的值。</span><span class="sxs-lookup"><span data-stu-id="17f45-105">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="17f45-106">右方運算元的型別必須與左方運算元的型別相同，或是會隱含地轉換成該型別。</span><span class="sxs-lookup"><span data-stu-id="17f45-106">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="17f45-107">指派運算子 `=` 是右向關聯，也就是表單的運算式</span><span class="sxs-lookup"><span data-stu-id="17f45-107">The assignment operator `=` is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="17f45-108">會評估為</span><span class="sxs-lookup"><span data-stu-id="17f45-108">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="17f45-109">下列範例示範將區域變數、屬性及索引子元素作為指派運算子左運算元的用法：</span><span class="sxs-lookup"><span data-stu-id="17f45-109">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](snippets/shared/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="17f45-110">ref 指派運算子</span><span class="sxs-lookup"><span data-stu-id="17f45-110">ref assignment operator</span></span>

<span data-ttu-id="17f45-111">從 C# 7.3 開始，您可以使用 ref 指派運算子 `= ref` 來重新指派 [ref 區域變數](../keywords/ref.md#ref-locals)或[ref readonly 區域變數](../keywords/ref.md#ref-readonly-locals)。</span><span class="sxs-lookup"><span data-stu-id="17f45-111">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="17f45-112">下列範例示範 ref 指派運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="17f45-112">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](snippets/shared/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="17f45-113">在 ref 指派運算子的案例中，它的兩個運算元都必須是相同的類型。</span><span class="sxs-lookup"><span data-stu-id="17f45-113">In the case of the ref assignment operator, the both of its operands must be of the same type.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="17f45-114">複合指派</span><span class="sxs-lookup"><span data-stu-id="17f45-114">Compound assignment</span></span>

<span data-ttu-id="17f45-115">若是二元運算子 `op`，表單的複合指派運算式</span><span class="sxs-lookup"><span data-stu-id="17f45-115">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="17f45-116">相當於</span><span class="sxs-lookup"><span data-stu-id="17f45-116">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="17f45-117">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="17f45-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="17f45-118">[算數](arithmetic-operators.md#compound-assignment)、[布林邏輯](boolean-logical-operators.md#compound-assignment)和[位元邏輯與位移](bitwise-and-shift-operators.md#compound-assignment)運算子支援複合指派。</span><span class="sxs-lookup"><span data-stu-id="17f45-118">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="17f45-119">Null 聯合指派</span><span class="sxs-lookup"><span data-stu-id="17f45-119">Null-coalescing assignment</span></span>

<span data-ttu-id="17f45-120">從 c # 8.0 開始，您可以使用 null 聯合指派運算子，將右邊運算元的值指派給左邊的運算元（ `??=` 如果左邊運算元評估為） `null` 。</span><span class="sxs-lookup"><span data-stu-id="17f45-120">Beginning with C# 8.0, you can use the null-coalescing assignment operator `??=` to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="17f45-121">如需詳細資訊，請參閱 [？？和？= 運算子](null-coalescing-operator.md) 文章。</span><span class="sxs-lookup"><span data-stu-id="17f45-121">For more information, see the [?? and ??= operators](null-coalescing-operator.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="17f45-122">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="17f45-122">Operator overloadability</span></span>

<span data-ttu-id="17f45-123">使用者定義型 [別無法多](operator-overloading.md) 載指派運算子。</span><span class="sxs-lookup"><span data-stu-id="17f45-123">A user-defined type cannot [overload](operator-overloading.md) the assignment operator.</span></span> <span data-ttu-id="17f45-124">不過，使用者定義型別可以定義會轉換成另一型別的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="17f45-124">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="17f45-125">如此一來，便可將使用者定義型別的值指派給另一型別的變數、屬性或索引子元素。</span><span class="sxs-lookup"><span data-stu-id="17f45-125">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="17f45-126">如需詳細資訊，請參閱[使用者定義轉換運算子](user-defined-conversion-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="17f45-126">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

<span data-ttu-id="17f45-127">使用者定義型別無法明確地多載複合指派運算子。</span><span class="sxs-lookup"><span data-stu-id="17f45-127">A user-defined type cannot explicitly overload a compound assignment operator.</span></span> <span data-ttu-id="17f45-128">不過，如果使用者定義型別多載二元運算子 `op` ， `op=` 運算子（如果存在的話）也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="17f45-128">However, if a user-defined type overloads a binary operator `op`, the `op=` operator, if it exists, is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="17f45-129">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="17f45-129">C# language specification</span></span>

<span data-ttu-id="17f45-130">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[指派運算子](~/_csharplang/spec/expressions.md#assignment-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="17f45-130">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="17f45-131">如需 ref 指派運算子的詳細資訊 `= ref` ，請參閱 [功能提案注意事項](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md)。</span><span class="sxs-lookup"><span data-stu-id="17f45-131">For more information about the ref assignment operator `= ref`, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="17f45-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17f45-132">See also</span></span>

- [<span data-ttu-id="17f45-133">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="17f45-133">C# reference</span></span>](../index.md)
- [<span data-ttu-id="17f45-134">C# 運算子與運算式</span><span class="sxs-lookup"><span data-stu-id="17f45-134">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="17f45-135">ref 關鍵字</span><span class="sxs-lookup"><span data-stu-id="17f45-135">ref keyword</span></span>](../keywords/ref.md)
