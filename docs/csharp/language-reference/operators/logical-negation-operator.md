---
title: '! 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- '! operator [C#]'
- logical negation operator (!) [C#]
- NOT operator [C#]
ms.assetid: f5ae133f-8f64-4560-b34f-cd9cd5eed4ad
ms.openlocfilehash: 6b6d1796032f536aac0be49d4f101c1380b4e98f
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333222"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="dcc2e-103">!</span><span class="sxs-lookup"><span data-stu-id="dcc2e-103">!</span></span> <span data-ttu-id="dcc2e-104">operator (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="dcc2e-104">operator (C# Reference)</span></span>

<span data-ttu-id="dcc2e-105">邏輯負運算子 (`!`) 是將運算元變成負值的一元運算子。</span><span class="sxs-lookup"><span data-stu-id="dcc2e-105">The logical negation operator (`!`) is a unary operator that negates its operand.</span></span> <span data-ttu-id="dcc2e-106">它是針對 `bool` 所定義，並且只有在其運算元為 `false` 時，才會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="dcc2e-106">It is defined for `bool` and returns `true` if and only if its operand is `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="dcc2e-107">備註</span><span class="sxs-lookup"><span data-stu-id="dcc2e-107">Remarks</span></span>

<span data-ttu-id="dcc2e-108">使用者定義型別可以多載 `!` 運算子 (請參閱 [operator](../keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="dcc2e-108">User-defined types can overload the `!` operator (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="dcc2e-109">範例</span><span class="sxs-lookup"><span data-stu-id="dcc2e-109">Example</span></span>

[!code-csharp[csRefOperators#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#7)]

## <a name="see-also"></a><span data-ttu-id="dcc2e-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dcc2e-110">See also</span></span>

- [<span data-ttu-id="dcc2e-111">C# 參考</span><span class="sxs-lookup"><span data-stu-id="dcc2e-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="dcc2e-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="dcc2e-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="dcc2e-113">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="dcc2e-113">C# Operators</span></span>](index.md)