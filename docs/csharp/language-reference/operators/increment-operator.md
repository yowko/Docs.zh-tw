---
title: ++ 運算子 - C# 參考
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: db716f0d8cfe252462abeee9c80baaab880e212b
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235640"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="bfe8e-102">++ 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="bfe8e-102">++ Operator (C# Reference)</span></span>

<span data-ttu-id="bfe8e-103">一元遞增運算子 `++` 的運算元遞增量為 1。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-103">The unary increment operator `++` increments its operand by 1.</span></span> <span data-ttu-id="bfe8e-104">其支援兩種形式：後置遞增運算子 `x++` 和前置遞增運算子 `++x`。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-104">It's supported in two forms: the postfix increment operator, `x++`, and the prefix increment operator, `++x`.</span></span>

## <a name="postfix-increment-operator"></a><span data-ttu-id="bfe8e-105">後置遞增運算子</span><span class="sxs-lookup"><span data-stu-id="bfe8e-105">Postfix increment operator</span></span>

<span data-ttu-id="bfe8e-106">`x++` 的結果為運算「之前」的 `x` 值，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="bfe8e-106">The result of `x++` is the value of `x` *before* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[postfix increment](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PostfixIncrement)]

## <a name="prefix-increment-operator"></a><span data-ttu-id="bfe8e-107">前置遞增運算子</span><span class="sxs-lookup"><span data-stu-id="bfe8e-107">Prefix increment operator</span></span>

<span data-ttu-id="bfe8e-108">`++x` 的結果為運算「之後」的 `x` 值，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="bfe8e-108">The result of `++x` is the value of `x` *after* the operation, as the following example shows:</span></span>

[!code-csharp-interactive[prefix increment](~/samples/snippets/csharp/language-reference/operators/DecrementAndIncrementExamples.cs#PrefixIncrement)]

## <a name="remarks"></a><span data-ttu-id="bfe8e-109">備註</span><span class="sxs-lookup"><span data-stu-id="bfe8e-109">Remarks</span></span>

<span data-ttu-id="bfe8e-110">遞增運算子已針對所有[整數型別](../keywords/integral-types-table.md) (包 括 [char](../keywords/char.md) 型別)、[浮點型別](../keywords/floating-point-types-table.md)及任何[列舉](../keywords/enum.md)型別進行預先定義。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-110">The increment operator is predefined for all [integral types](../keywords/integral-types-table.md) (including the [char](../keywords/char.md) type), [floating-point types](../keywords/floating-point-types-table.md), and any [enum](../keywords/enum.md) type.</span></span>

<span data-ttu-id="bfe8e-111">遞增運算子的運算元必須是變數、[屬性](../../programming-guide/classes-and-structs/properties.md)存取或[索引子](../../../csharp/programming-guide/indexers/index.md)存取。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-111">An operand of the increment operator must be a variable, a [property](../../programming-guide/classes-and-structs/properties.md) access, or an [indexer](../../../csharp/programming-guide/indexers/index.md) access.</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="bfe8e-112">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="bfe8e-112">Operator overloadability</span></span>

<span data-ttu-id="bfe8e-113">使用者定義型別可以[多載](../keywords/operator.md) `++` 運算子。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-113">User-defined types can [overload](../keywords/operator.md) the `++` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="bfe8e-114">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="bfe8e-114">C# language specification</span></span>

<span data-ttu-id="bfe8e-115">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[後置遞增和遞減運算子](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators)與[前置遞增和遞減運算子](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators)小節。</span><span class="sxs-lookup"><span data-stu-id="bfe8e-115">For more information, see the [Postfix increment and decrement operators](~/_csharplang/spec/expressions.md#postfix-increment-and-decrement-operators) and [Prefix increment and decrement operators](~/_csharplang/spec/expressions.md#prefix-increment-and-decrement-operators) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bfe8e-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bfe8e-116">See also</span></span>

- [<span data-ttu-id="bfe8e-117">C# 參考</span><span class="sxs-lookup"><span data-stu-id="bfe8e-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bfe8e-118">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="bfe8e-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bfe8e-119">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="bfe8e-119">C# Operators</span></span>](index.md)
- [<span data-ttu-id="bfe8e-120">-- 運算子</span><span class="sxs-lookup"><span data-stu-id="bfe8e-120">-- Operator</span></span>](decrement-operator.md)
- [<span data-ttu-id="bfe8e-121">操作說明：遞增和遞減指標</span><span class="sxs-lookup"><span data-stu-id="bfe8e-121">How to: increment and decrement pointers</span></span>](../../programming-guide/unsafe-code-pointers/how-to-increment-and-decrement-pointers.md)
