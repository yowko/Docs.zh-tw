---
title: '指派運算子-c # 參考'
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 7b4f3b3f4d6b697903461f08435552f2df36bfe4
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916935"
---
# <a name="assignment-operators-c-reference"></a><span data-ttu-id="57f3d-102">指派運算子 (c # 參考) </span><span class="sxs-lookup"><span data-stu-id="57f3d-102">Assignment operators (C# reference)</span></span>

<span data-ttu-id="57f3d-103">指派運算子 `=` 會將其右方運算元的值指派給其左方運算元所指定的變數、[屬性](../../programming-guide/classes-and-structs/properties.md)或[索引子](../../programming-guide/indexers/index.md)元素。</span><span class="sxs-lookup"><span data-stu-id="57f3d-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="57f3d-104">指派運算式的結果是指派給左方運算元的值。</span><span class="sxs-lookup"><span data-stu-id="57f3d-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="57f3d-105">右方運算元的型別必須與左方運算元的型別相同，或是會隱含地轉換成該型別。</span><span class="sxs-lookup"><span data-stu-id="57f3d-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="57f3d-106">指派運算子 `=` 是右向關聯，也就是表單的運算式</span><span class="sxs-lookup"><span data-stu-id="57f3d-106">The assignment operator `=` is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="57f3d-107">會評估為</span><span class="sxs-lookup"><span data-stu-id="57f3d-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="57f3d-108">下列範例示範將區域變數、屬性及索引子元素作為指派運算子左運算元的用法：</span><span class="sxs-lookup"><span data-stu-id="57f3d-108">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](snippets/shared/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="57f3d-109">ref 指派運算子</span><span class="sxs-lookup"><span data-stu-id="57f3d-109">ref assignment operator</span></span>

<span data-ttu-id="57f3d-110">從 C# 7.3 開始，您可以使用 ref 指派運算子 `= ref` 來重新指派 [ref 區域變數](../keywords/ref.md#ref-locals)或[ref readonly 區域變數](../keywords/ref.md#ref-readonly-locals)。</span><span class="sxs-lookup"><span data-stu-id="57f3d-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="57f3d-111">下列範例示範 ref 指派運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="57f3d-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](snippets/shared/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="57f3d-112">在 ref 指派運算子的情況下，它的兩個運算元都必須是相同的類型。</span><span class="sxs-lookup"><span data-stu-id="57f3d-112">In the case of the ref assignment operator, the both of its operands must be of the same type.</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="57f3d-113">複合指派</span><span class="sxs-lookup"><span data-stu-id="57f3d-113">Compound assignment</span></span>

<span data-ttu-id="57f3d-114">若是二元運算子 `op`，表單的複合指派運算式</span><span class="sxs-lookup"><span data-stu-id="57f3d-114">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="57f3d-115">相當於</span><span class="sxs-lookup"><span data-stu-id="57f3d-115">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="57f3d-116">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="57f3d-116">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="57f3d-117">[算數](arithmetic-operators.md#compound-assignment)、[布林邏輯](boolean-logical-operators.md#compound-assignment)和[位元邏輯與位移](bitwise-and-shift-operators.md#compound-assignment)運算子支援複合指派。</span><span class="sxs-lookup"><span data-stu-id="57f3d-117">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="57f3d-118">Null 聯合指派</span><span class="sxs-lookup"><span data-stu-id="57f3d-118">Null-coalescing assignment</span></span>

<span data-ttu-id="57f3d-119">從 c # 8.0 開始，您可以使用 null 聯合指派運算子， `??=` 只有在左側運算元評估為時，才將其右運算元的值指派給其左邊的運算元 `null` 。</span><span class="sxs-lookup"><span data-stu-id="57f3d-119">Beginning with C# 8.0, you can use the null-coalescing assignment operator `??=` to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="57f3d-120">如需詳細資訊，請參閱[？？和？= 運算子](null-coalescing-operator.md)一文。</span><span class="sxs-lookup"><span data-stu-id="57f3d-120">For more information, see the [?? and ??= operators](null-coalescing-operator.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="57f3d-121">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="57f3d-121">Operator overloadability</span></span>

<span data-ttu-id="57f3d-122">使用者定義型[別無法多](operator-overloading.md)載指派運算子。</span><span class="sxs-lookup"><span data-stu-id="57f3d-122">A user-defined type cannot [overload](operator-overloading.md) the assignment operator.</span></span> <span data-ttu-id="57f3d-123">不過，使用者定義型別可以定義會轉換成另一型別的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="57f3d-123">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="57f3d-124">如此一來，便可將使用者定義型別的值指派給另一型別的變數、屬性或索引子元素。</span><span class="sxs-lookup"><span data-stu-id="57f3d-124">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="57f3d-125">如需詳細資訊，請參閱[使用者定義轉換運算子](user-defined-conversion-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="57f3d-125">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

<span data-ttu-id="57f3d-126">使用者定義型別無法明確地多載複合指派運算子。</span><span class="sxs-lookup"><span data-stu-id="57f3d-126">A user-defined type cannot explicitly overload a compound assignment operator.</span></span> <span data-ttu-id="57f3d-127">不過，如果使用者定義型別多載二元運算子 `op` ，則 `op=` 運算子（如果存在的話）也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="57f3d-127">However, if a user-defined type overloads a binary operator `op`, the `op=` operator, if it exists, is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="57f3d-128">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="57f3d-128">C# language specification</span></span>

<span data-ttu-id="57f3d-129">如需詳細資訊，請參閱 [C# 語言規格](~/_csharplang/spec/introduction.md)的[指派運算子](~/_csharplang/spec/expressions.md#assignment-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="57f3d-129">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

<span data-ttu-id="57f3d-130">如需 ref 指派運算子的詳細資訊 `= ref` ，請參閱[功能提案注意事項](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md)。</span><span class="sxs-lookup"><span data-stu-id="57f3d-130">For more information about the ref assignment operator `= ref`, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="57f3d-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="57f3d-131">See also</span></span>

- [<span data-ttu-id="57f3d-132">C# 參考資料</span><span class="sxs-lookup"><span data-stu-id="57f3d-132">C# reference</span></span>](../index.md)
- [<span data-ttu-id="57f3d-133">C# 運算子與運算式</span><span class="sxs-lookup"><span data-stu-id="57f3d-133">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="57f3d-134">ref 關鍵字</span><span class="sxs-lookup"><span data-stu-id="57f3d-134">ref keyword</span></span>](../keywords/ref.md)
