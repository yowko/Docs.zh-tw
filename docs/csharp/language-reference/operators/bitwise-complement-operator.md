---
title: ~ 運算子 (C# 參考)
ms.date: 11/05/2018
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
ms.openlocfilehash: 1bcb07c5639a098e3a8c566e92083ca0d48efb81
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153211"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="4e848-102">~ 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="4e848-102">~ Operator (C# Reference)</span></span>

<span data-ttu-id="4e848-103">位元補數運算子 `~` 是一元運算子，會藉由反轉每個位元來產生其運算元的位元補數。</span><span class="sxs-lookup"><span data-stu-id="4e848-103">The bitwise complement operator `~` is a unary operator that produces a bitwise complement of its operand by reversing each bit.</span></span> <span data-ttu-id="4e848-104">所有整數型別都支援 `~` 運算子。</span><span class="sxs-lookup"><span data-stu-id="4e848-104">All integer types support the `~` operator.</span></span>

> [!NOTE]
> <span data-ttu-id="4e848-105">`~` 符號也可用來宣告完成項。</span><span class="sxs-lookup"><span data-stu-id="4e848-105">The `~` symbol is also used to declare finalizers.</span></span> <span data-ttu-id="4e848-106">如需詳細資訊，請參閱[完成項](../../programming-guide/classes-and-structs/destructors.md)。</span><span class="sxs-lookup"><span data-stu-id="4e848-106">For more information, see [Finalizers](../../programming-guide/classes-and-structs/destructors.md).</span></span>

<span data-ttu-id="4e848-107">下列範例示範 `~` 運算子的用法：</span><span class="sxs-lookup"><span data-stu-id="4e848-107">The following example demonstrates the usage of the `~` operator:</span></span>

[!code-csharp-interactive[bitwise NOT](~/samples/snippets/csharp/language-reference/operators/BitwiseComplementExamples.cs#Example)]

> [!NOTE]
> <span data-ttu-id="4e848-108">上述範例使用[在 C# 7.0 中導入](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements)並[在 C# 7.2 中增強的](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals)二進位常值。</span><span class="sxs-lookup"><span data-stu-id="4e848-108">The preceding example uses the binary literals [introduced in C# 7.0](../../whats-new/csharp-7.md#numeric-literal-syntax-improvements) and [enhanced  in C# 7.2](../../whats-new/csharp-7-2.md#leading-underscores-in-numeric-literals).</span></span>

## <a name="operator-overloadability"></a><span data-ttu-id="4e848-109">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="4e848-109">Operator overloadability</span></span>

<span data-ttu-id="4e848-110">使用者定義型別可以[多載](../keywords/operator.md) `~` 運算子。</span><span class="sxs-lookup"><span data-stu-id="4e848-110">User-defined types can [overload](../keywords/operator.md) the `~` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4e848-111">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="4e848-111">C# language specification</span></span>

<span data-ttu-id="4e848-112">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[位元補數運算子](~/_csharplang/spec/expressions.md#bitwise-complement-operator)一節。</span><span class="sxs-lookup"><span data-stu-id="4e848-112">For more information, see the [Bitwise complement operator](~/_csharplang/spec/expressions.md#bitwise-complement-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4e848-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e848-113">See also</span></span>

- [<span data-ttu-id="4e848-114">C# 參考</span><span class="sxs-lookup"><span data-stu-id="4e848-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4e848-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="4e848-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4e848-116">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="4e848-116">C# Operators</span></span>](index.md)
- [<span data-ttu-id="4e848-117">完成項</span><span class="sxs-lookup"><span data-stu-id="4e848-117">Finalizers</span></span>](../../programming-guide/classes-and-structs/destructors.md)
- [<span data-ttu-id="4e848-118">& 運算子</span><span class="sxs-lookup"><span data-stu-id="4e848-118">& operator</span></span>](and-operator.md)
- [<span data-ttu-id="4e848-119">| 運算子</span><span class="sxs-lookup"><span data-stu-id="4e848-119">| operator</span></span>](or-operator.md)
- [<span data-ttu-id="4e848-120">^ 運算子</span><span class="sxs-lookup"><span data-stu-id="4e848-120">^ operator</span></span>](xor-operator.md)
