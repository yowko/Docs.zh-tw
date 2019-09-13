---
title: = 運算子 - C# 參考
ms.custom: seodec18
ms.date: 09/10/2019
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: a450a55524f33f4f06ed077aba864e8f641a458d
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924663"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ee2ea-102">= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ee2ea-102">= operator (C# reference)</span></span>

<span data-ttu-id="ee2ea-103">指派運算子 `=` 會將其右方運算元的值指派給其左方運算元所指定的變數、[屬性](../../programming-guide/classes-and-structs/properties.md)或[索引子](../../programming-guide/indexers/index.md)元素。</span><span class="sxs-lookup"><span data-stu-id="ee2ea-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="ee2ea-104">指派運算式的結果是指派給左方運算元的值。</span><span class="sxs-lookup"><span data-stu-id="ee2ea-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="ee2ea-105">右方運算元的型別必須與左方運算元的型別相同，或是會隱含地轉換成該型別。</span><span class="sxs-lookup"><span data-stu-id="ee2ea-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="ee2ea-106">指派運算子是右向關聯運算子，亦即，以下形式的運算式</span><span class="sxs-lookup"><span data-stu-id="ee2ea-106">The assignment operator is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="ee2ea-107">評估為</span><span class="sxs-lookup"><span data-stu-id="ee2ea-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="ee2ea-108">下列範例示範將區域變數、屬性及索引子元素作為指派運算子左運算元的用法：</span><span class="sxs-lookup"><span data-stu-id="ee2ea-108">The following example demonstrates the usage of the assignment operator with a local variable, a property, and an indexer element as its left-hand operand:</span></span>

[!code-csharp-interactive[simple assignment](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#Simple)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="ee2ea-109">ref 指派運算子</span><span class="sxs-lookup"><span data-stu-id="ee2ea-109">ref assignment operator</span></span>

<span data-ttu-id="ee2ea-110">從 C# 7.3 開始，您可以使用 ref 指派運算子 `= ref` 來重新指派 [ref 區域變數](../keywords/ref.md#ref-locals)或[ref readonly 區域變數](../keywords/ref.md#ref-readonly-locals)。</span><span class="sxs-lookup"><span data-stu-id="ee2ea-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="ee2ea-111">下列範例示範 ref 指派運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="ee2ea-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](~/samples/csharp/language-reference/operators/AssignmentOperator.cs#RefAssignment)]

<span data-ttu-id="ee2ea-112">就 ref 指派運算子而言，兩個運算元的型別必須相同。</span><span class="sxs-lookup"><span data-stu-id="ee2ea-112">In the case of the ref assignment operator, the type of both its operands must be the same.</span></span>

<span data-ttu-id="ee2ea-113">如需詳細資訊，請參閱[功能提案注意事項](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="ee2ea-113">For more information, see the [feature proposal note](~/_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="compound-assignment"></a><span data-ttu-id="ee2ea-114">複合指派</span><span class="sxs-lookup"><span data-stu-id="ee2ea-114">Compound assignment</span></span>

<span data-ttu-id="ee2ea-115">若是二元運算子 `op`，表單的複合指派運算式</span><span class="sxs-lookup"><span data-stu-id="ee2ea-115">For a binary operator `op`, a compound assignment expression of the form</span></span>

```csharp
x op= y
```

<span data-ttu-id="ee2ea-116">相當於</span><span class="sxs-lookup"><span data-stu-id="ee2ea-116">is equivalent to</span></span>

```csharp
x = x op y
```

<span data-ttu-id="ee2ea-117">但只會評估 `x` 一次。</span><span class="sxs-lookup"><span data-stu-id="ee2ea-117">except that `x` is only evaluated once.</span></span>

<span data-ttu-id="ee2ea-118">[算數](arithmetic-operators.md#compound-assignment)、[布林邏輯](boolean-logical-operators.md#compound-assignment)和[位元邏輯與位移](bitwise-and-shift-operators.md#compound-assignment)運算子支援複合指派。</span><span class="sxs-lookup"><span data-stu-id="ee2ea-118">Compound assignment is supported by [arithmetic](arithmetic-operators.md#compound-assignment), [Boolean logical](boolean-logical-operators.md#compound-assignment), and [bitwise logical and shift](bitwise-and-shift-operators.md#compound-assignment) operators.</span></span>

## <a name="null-coalescing-assignment"></a><span data-ttu-id="ee2ea-119">Null 聯合指派</span><span class="sxs-lookup"><span data-stu-id="ee2ea-119">Null-coalescing assignment</span></span>

<span data-ttu-id="ee2ea-120">從C# 8.0 開始，您可以使用 null 聯合指派運算子`??=` ，只有在左側運算元評估為`null`時，才將其右運算元的值指派給其左邊的運算元。</span><span class="sxs-lookup"><span data-stu-id="ee2ea-120">Beginning with C# 8.0, you can use the null-coalescing assignment operator `??=` to assign the value of its right-hand operand to its left-hand operand only if the left-hand operand evaluates to `null`.</span></span> <span data-ttu-id="ee2ea-121">如需詳細資訊，請參閱[？？和？= 運算子](null-coalescing-operator.md)一文。</span><span class="sxs-lookup"><span data-stu-id="ee2ea-121">For more information, see the [?? and ??= operators](null-coalescing-operator.md) article.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="ee2ea-122">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="ee2ea-122">Operator overloadability</span></span>

<span data-ttu-id="ee2ea-123">使用者定義型別無法多載指派運算子。</span><span class="sxs-lookup"><span data-stu-id="ee2ea-123">A user-defined type cannot overload the assignment operator.</span></span> <span data-ttu-id="ee2ea-124">不過，使用者定義型別可以定義會轉換成另一型別的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="ee2ea-124">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="ee2ea-125">如此一來，便可將使用者定義型別的值指派給另一型別的變數、屬性或索引子元素。</span><span class="sxs-lookup"><span data-stu-id="ee2ea-125">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="ee2ea-126">如需詳細資訊，請參閱[使用者定義轉換運算子](user-defined-conversion-operators.md)。</span><span class="sxs-lookup"><span data-stu-id="ee2ea-126">For more information, see [User-defined conversion operators](user-defined-conversion-operators.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="ee2ea-127">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ee2ea-127">C# language specification</span></span>

<span data-ttu-id="ee2ea-128">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[指派運算子](~/_csharplang/spec/expressions.md#assignment-operators)一節。</span><span class="sxs-lookup"><span data-stu-id="ee2ea-128">For more information, see the [Assignment operators](~/_csharplang/spec/expressions.md#assignment-operators) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ee2ea-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ee2ea-129">See also</span></span>

- [<span data-ttu-id="ee2ea-130">C# 參考</span><span class="sxs-lookup"><span data-stu-id="ee2ea-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="ee2ea-131">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="ee2ea-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="ee2ea-132">ref 關鍵字</span><span class="sxs-lookup"><span data-stu-id="ee2ea-132">ref keyword</span></span>](../keywords/ref.md)
