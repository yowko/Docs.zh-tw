---
title: '! 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 02/14/2019
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- '! operator [C#]'
- logical negation operator (!) [C#]
- NOT operator [C#]
ms.assetid: f5ae133f-8f64-4560-b34f-cd9cd5eed4ad
ms.openlocfilehash: 464bd658c9bf430191d84d3d5ad8d57173ab87c5
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/15/2019
ms.locfileid: "56303708"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="5ef60-103">!</span><span class="sxs-lookup"><span data-stu-id="5ef60-103">!</span></span> <span data-ttu-id="5ef60-104">operator (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="5ef60-104">operator (C# Reference)</span></span>

<span data-ttu-id="5ef60-105">邏輯負運算子 `!` 是一元運算子，它會計算其 [bool](../keywords/bool.md) 運算元的邏輯負值。</span><span class="sxs-lookup"><span data-stu-id="5ef60-105">The logical negation operator `!` is a unary operator that computes logical negation of its [bool](../keywords/bool.md) operand.</span></span> <span data-ttu-id="5ef60-106">也就是說，它會產生 `true` (若運算元是 `false`) 與 `false` (若運算元是 `true`)：</span><span class="sxs-lookup"><span data-stu-id="5ef60-106">That is, it produces `true`, if the operand is `false`, and `false`, if the operand is `true`:</span></span>

[!code-csharp-interactive[logical negation](~/samples/snippets/csharp/language-reference/operators/LogicalNegationExamples.cs#Example)]

## <a name="operator-overloadability"></a><span data-ttu-id="5ef60-107">運算子是否可多載</span><span class="sxs-lookup"><span data-stu-id="5ef60-107">Operator overloadability</span></span>

<span data-ttu-id="5ef60-108">使用者定義型別可以[多載](../keywords/operator.md) `!` 運算子。</span><span class="sxs-lookup"><span data-stu-id="5ef60-108">User-defined types can [overload](../keywords/operator.md) the `!` operator.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5ef60-109">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="5ef60-109">C# language specification</span></span>

<span data-ttu-id="5ef60-110">如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[邏輯負值運算子](~/_csharplang/spec/expressions.md#logical-negation-operator)一節。</span><span class="sxs-lookup"><span data-stu-id="5ef60-110">For more information, see the [Logical negation operator](~/_csharplang/spec/expressions.md#logical-negation-operator) section of the [C# language specification](../language-specification/index.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5ef60-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ef60-111">See also</span></span>

- [<span data-ttu-id="5ef60-112">C# 參考</span><span class="sxs-lookup"><span data-stu-id="5ef60-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5ef60-113">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5ef60-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5ef60-114">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="5ef60-114">C# Operators</span></span>](index.md)