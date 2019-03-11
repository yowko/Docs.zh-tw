---
title: = 運算子 - C# 參考
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 40dc844f2a4b6411ea82aa2f029b36d7dd8f6e5a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716307"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c6dc3-102">= 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="c6dc3-102">= Operator (C# Reference)</span></span>

<span data-ttu-id="c6dc3-103">指派運算子 `=` 會將其右方運算元的值指派給其左方運算元所指定的變數、[屬性](../../programming-guide/classes-and-structs/properties.md)或[索引子](../../../csharp/programming-guide/indexers/index.md)元素。</span><span class="sxs-lookup"><span data-stu-id="c6dc3-103">The assignment operator `=` assigns the value of its right-hand operand to a variable, a [property](../../programming-guide/classes-and-structs/properties.md), or an [indexer](../../../csharp/programming-guide/indexers/index.md) element given by its left-hand operand.</span></span> <span data-ttu-id="c6dc3-104">指派運算式的結果是指派給左方運算元的值。</span><span class="sxs-lookup"><span data-stu-id="c6dc3-104">The result of an assignment expression is the value assigned to the left-hand operand.</span></span> <span data-ttu-id="c6dc3-105">右方運算元的型別必須與左方運算元的型別相同，或是會隱含地轉換成該型別。</span><span class="sxs-lookup"><span data-stu-id="c6dc3-105">The type of the right-hand operand must be the same as the type of the left-hand operand or implicitly convertible to it.</span></span>

<span data-ttu-id="c6dc3-106">指派運算子是右向關聯運算子，亦即，以下形式的運算式</span><span class="sxs-lookup"><span data-stu-id="c6dc3-106">The assignment operator is right-associative, that is, an expression of the form</span></span>

```csharp
a = b = c
```

<span data-ttu-id="c6dc3-107">評估為</span><span class="sxs-lookup"><span data-stu-id="c6dc3-107">is evaluated as</span></span>

```csharp
a = (b = c)
```

<span data-ttu-id="c6dc3-108">下列範例示範如何使用指派運算子將值指派給區域變數、屬性及索引子元素：</span><span class="sxs-lookup"><span data-stu-id="c6dc3-108">The following example demonstrates the usage of the assignment operator to assign values to a local variable, a property, and an indexer element:</span></span>

[!code-csharp-interactive[assignment operator](~/samples/snippets/csharp/language-reference/operators/AssignmentExamples.cs#Assignments)]

## <a name="ref-assignment-operator"></a><span data-ttu-id="c6dc3-109">ref 指派運算子</span><span class="sxs-lookup"><span data-stu-id="c6dc3-109">ref assignment operator</span></span>

<span data-ttu-id="c6dc3-110">從 C# 7.3 開始，您可以使用 ref 指派運算子 `= ref` 來重新指派 [ref 區域變數](../keywords/ref.md#ref-locals)或[ref readonly 區域變數](../keywords/ref.md#ref-readonly-locals)。</span><span class="sxs-lookup"><span data-stu-id="c6dc3-110">Beginning with C# 7.3, you can use the ref assignment operator `= ref` to reassign a [ref local](../keywords/ref.md#ref-locals) or [ref readonly local](../keywords/ref.md#ref-readonly-locals) variable.</span></span> <span data-ttu-id="c6dc3-111">下列範例示範 ref 指派運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="c6dc3-111">The following example demonstrates the usage of the ref assignment operator:</span></span>

[!code-csharp[ref assignment operator](~/samples/snippets/csharp/language-reference/operators/AssignmentExamples.cs#RefAssignment)]

<span data-ttu-id="c6dc3-112">就 ref 指派運算子而言，左方運算元與右方運算元的型別必須相同。</span><span class="sxs-lookup"><span data-stu-id="c6dc3-112">In the case of the ref assignment operator, the type of the left operand and the right operand must be the same.</span></span>

<span data-ttu-id="c6dc3-113">如需詳細資訊，請參閱[功能提案注意事項](../../../../_csharplang/proposals/csharp-7.3/ref-local-reassignment.md) \(英文\)。</span><span class="sxs-lookup"><span data-stu-id="c6dc3-113">For more information, see the [feature proposal note](../../../../_csharplang/proposals/csharp-7.3/ref-local-reassignment.md).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="c6dc3-114">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="c6dc3-114">Operator overloadability</span></span>

<span data-ttu-id="c6dc3-115">使用者定義型別無法多載指派運算子。</span><span class="sxs-lookup"><span data-stu-id="c6dc3-115">A user-defined type cannot overload the assignment operator.</span></span> <span data-ttu-id="c6dc3-116">不過，使用者定義型別可以定義會轉換成另一型別的隱含轉換。</span><span class="sxs-lookup"><span data-stu-id="c6dc3-116">However, a user-defined type can define an implicit conversion to another type.</span></span> <span data-ttu-id="c6dc3-117">如此一來，便可將使用者定義型別的值指派給另一型別的變數、屬性或索引子元素。</span><span class="sxs-lookup"><span data-stu-id="c6dc3-117">That way, the value of a user-defined type can be assigned to a variable, a property, or an indexer element of another type.</span></span> <span data-ttu-id="c6dc3-118">如需詳細資訊，請參閱 [implicit](../keywords/implicit.md) 關鍵字一文。</span><span class="sxs-lookup"><span data-stu-id="c6dc3-118">For more information, see the [implicit](../keywords/implicit.md) keyword article.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c6dc3-119">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="c6dc3-119">C# language specification</span></span>

<span data-ttu-id="c6dc3-120">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[簡單指派](~/_csharplang/spec/expressions.md#simple-assignment)一節。</span><span class="sxs-lookup"><span data-stu-id="c6dc3-120">For more information, see the [Simple assignment](~/_csharplang/spec/expressions.md#simple-assignment) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c6dc3-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6dc3-121">See also</span></span>

- [<span data-ttu-id="c6dc3-122">C# 參考</span><span class="sxs-lookup"><span data-stu-id="c6dc3-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c6dc3-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c6dc3-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c6dc3-124">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="c6dc3-124">C# Operators</span></span>](index.md)
- [<span data-ttu-id="c6dc3-125">ref 關鍵字</span><span class="sxs-lookup"><span data-stu-id="c6dc3-125">ref keyword</span></span>](../keywords/ref.md)
