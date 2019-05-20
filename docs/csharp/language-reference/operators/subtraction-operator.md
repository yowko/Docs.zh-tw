---
title: '- 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -_CSharpKeyword
helpviewer_keywords:
- '- operator [C#]'
- subtraction operator (-) [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: 920981addd5c779c9ad1c666ef45e1de5cd23408
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633008"
---
# <a name="--operator-c-reference"></a><span data-ttu-id="23d43-102">- 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="23d43-102">- operator (C# Reference)</span></span>

<span data-ttu-id="23d43-103">`-` 運算子可以作為一元或二元運算子。</span><span class="sxs-lookup"><span data-stu-id="23d43-103">The `-` operator can function as either a unary or a binary operator.</span></span>

## <a name="remarks"></a><span data-ttu-id="23d43-104">備註</span><span class="sxs-lookup"><span data-stu-id="23d43-104">Remarks</span></span>

<span data-ttu-id="23d43-105">會預先定義所有數字類型的一元 `-` 運算子。</span><span class="sxs-lookup"><span data-stu-id="23d43-105">Unary `-` operators are predefined for all numeric types.</span></span> <span data-ttu-id="23d43-106">對數值類型執行一元 `-` 運算的結果就是運算元的負數值。</span><span class="sxs-lookup"><span data-stu-id="23d43-106">The result of a unary `-` operation on a numeric type is the numeric negation of the operand.</span></span>

<span data-ttu-id="23d43-107">針對所有數值和列舉類型預先定義二元 `-` 運算子，以將第一個運算元減去第一個運算元。</span><span class="sxs-lookup"><span data-stu-id="23d43-107">Binary `-` operators are predefined for all numeric and enumeration types to subtract the second operand from the first.</span></span>

<span data-ttu-id="23d43-108">委派類型也會提供可執行委派移除的二元 `-` 運算子。</span><span class="sxs-lookup"><span data-stu-id="23d43-108">Delegate types also provide a binary `-` operator, which performs delegate removal.</span></span>

<span data-ttu-id="23d43-109">使用者定義型別可以多載一元 `-` 和二元 `-` 運算子。</span><span class="sxs-lookup"><span data-stu-id="23d43-109">User-defined types can overload the unary `-` and binary `-` operators.</span></span> <span data-ttu-id="23d43-110">如需詳細資訊，請參閱 [operator 關鍵字](../keywords/operator.md)。</span><span class="sxs-lookup"><span data-stu-id="23d43-110">For more information, see [operator keyword](../keywords/operator.md).</span></span>

## <a name="example"></a><span data-ttu-id="23d43-111">範例</span><span class="sxs-lookup"><span data-stu-id="23d43-111">Example</span></span>

[!code-csharp[csRefOperators#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#40)]

## <a name="see-also"></a><span data-ttu-id="23d43-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23d43-112">See also</span></span>

- [<span data-ttu-id="23d43-113">C# 參考</span><span class="sxs-lookup"><span data-stu-id="23d43-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="23d43-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="23d43-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="23d43-115">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="23d43-115">C# operators</span></span>](index.md)
