---
title: '* 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 02/26/2019
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: a5e120d26614f1e38cc2f2db02949552140b594e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977340"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="e185c-102">\* 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="e185c-102">\* operator (C# Reference)</span></span>

<span data-ttu-id="e185c-103">`*` 運算子支援兩種形式：一元指標間接運算子或二元乘法運算子。</span><span class="sxs-lookup"><span data-stu-id="e185c-103">The `*` operator is supported in two forms: a unary pointer indirection operator or a binary multiplication operator.</span></span>

## <a name="pointer-indirection-operator"></a><span data-ttu-id="e185c-104">指標間接運算子</span><span class="sxs-lookup"><span data-stu-id="e185c-104">Pointer indirection operator</span></span>

<span data-ttu-id="e185c-105">使用一元 `*` 運算子來取得指標類型的運算元所指向的變數。</span><span class="sxs-lookup"><span data-stu-id="e185c-105">Use the unary `*` operator to obtain the variable to which an operand of a pointer type points.</span></span> <span data-ttu-id="e185c-106">如需詳細資訊，請參閱[如何：取得指標變數值](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-value-of-a-pointer-variable.md)。</span><span class="sxs-lookup"><span data-stu-id="e185c-106">For more information, see [How to: obtain the value of a pointer variable](../../programming-guide/unsafe-code-pointers/how-to-obtain-the-value-of-a-pointer-variable.md).</span></span>

<span data-ttu-id="e185c-107">指標間接運算子 `*` 需要 [unsafe](../keywords/unsafe.md) 內容。</span><span class="sxs-lookup"><span data-stu-id="e185c-107">The pointer indirection operator `*` requires [unsafe](../keywords/unsafe.md) context.</span></span>

## <a name="multiplication-operator"></a><span data-ttu-id="e185c-108">乘法運算子</span><span class="sxs-lookup"><span data-stu-id="e185c-108">Multiplication operator</span></span>

<span data-ttu-id="e185c-109">針對數值類型，`*` 運算子會計算其運算元的乘積：</span><span class="sxs-lookup"><span data-stu-id="e185c-109">For numeric types, the `*` operator computes the product of its operands:</span></span>

[!code-csharp-interactive[multiplication](~/samples/snippets/csharp/language-reference/operators/MultiplicationExamples.cs#Multiply)]

## <a name="operator-overloadability"></a><span data-ttu-id="e185c-110">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="e185c-110">Operator overloadability</span></span>

<span data-ttu-id="e185c-111">使用者定義類型可以[多載](../keywords/operator.md)二元 `*` 運算子。</span><span class="sxs-lookup"><span data-stu-id="e185c-111">User-defined types can [overload](../keywords/operator.md) a binary `*` operator.</span></span> <span data-ttu-id="e185c-112">多載二元 `*` 運算子時，[乘法指派運算子](multiplication-assignment-operator.md) `*=` 也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="e185c-112">When a binary `*` operator is overloaded, the [multiplication assignment operator](multiplication-assignment-operator.md) `*=` is also implicitly overloaded.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="e185c-113">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="e185c-113">C# language specification</span></span>

<span data-ttu-id="e185c-114">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[指標間接](~/_csharplang/spec/unsafe-code.md#pointer-indirection)與[乘法運算子](~/_csharplang/spec/expressions.md#multiplication-operator)小節。</span><span class="sxs-lookup"><span data-stu-id="e185c-114">For more information, see the [Pointer indirection](~/_csharplang/spec/unsafe-code.md#pointer-indirection) and [Multiplication operator](~/_csharplang/spec/expressions.md#multiplication-operator) sections of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e185c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e185c-115">See also</span></span>

- [<span data-ttu-id="e185c-116">C# 參考</span><span class="sxs-lookup"><span data-stu-id="e185c-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e185c-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e185c-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e185c-118">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="e185c-118">C# Operators</span></span>](index.md)
- [<span data-ttu-id="e185c-119">指標型別</span><span class="sxs-lookup"><span data-stu-id="e185c-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)