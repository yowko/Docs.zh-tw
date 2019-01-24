---
title: '| 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: 185ea3aabff4794ec08cca541773dbec3574ab4b
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333508"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="a0647-102">| 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="a0647-102">| operator (C# Reference)</span></span>

<span data-ttu-id="a0647-103">整數型別和 `bool` 會預先定義二元 `|` 運算子。</span><span class="sxs-lookup"><span data-stu-id="a0647-103">Binary `|` operators are predefined for the integral types and `bool`.</span></span> <span data-ttu-id="a0647-104">對於整數型別，`|` 會計算其運算元的位元 OR。</span><span class="sxs-lookup"><span data-stu-id="a0647-104">For integral types, `|` computes the bitwise OR of its operands.</span></span> <span data-ttu-id="a0647-105">對於 `bool` 運算元，`|` 會計算其運算元的邏輯 OR；亦即，如果且唯有當其兩個運算元都是 `false` 時，結果會是 `false`。</span><span class="sxs-lookup"><span data-stu-id="a0647-105">For `bool` operands, `|` computes the logical OR of its operands; that is, the result is `false` if and only if both its operands are `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="a0647-106">備註</span><span class="sxs-lookup"><span data-stu-id="a0647-106">Remarks</span></span>

<span data-ttu-id="a0647-107">不同於[條件式 OR 運算子](conditional-or-operator.md) `||`，二元 `|` 運算子會評估兩個運算元，不論第一個運算元的值為何。</span><span class="sxs-lookup"><span data-stu-id="a0647-107">The binary `|` operator evaluates both operands regardless of the first one's value, in contrast to the [conditional-OR operator](conditional-or-operator.md) `||`.</span></span>

<span data-ttu-id="a0647-108">使用者定義型別可以多載 `|` 運算子 (請參閱 [operator](../keywords/operator.md))。</span><span class="sxs-lookup"><span data-stu-id="a0647-108">User-defined types can overload the `|` operator (see [operator](../keywords/operator.md)).</span></span>

## <a name="example"></a><span data-ttu-id="a0647-109">範例</span><span class="sxs-lookup"><span data-stu-id="a0647-109">Example</span></span>

 [!code-csharp[csRefOperators#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#31)]

## <a name="see-also"></a><span data-ttu-id="a0647-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0647-110">See also</span></span>

- [<span data-ttu-id="a0647-111">C# 參考</span><span class="sxs-lookup"><span data-stu-id="a0647-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a0647-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="a0647-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a0647-113">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="a0647-113">C# operators</span></span>](index.md)