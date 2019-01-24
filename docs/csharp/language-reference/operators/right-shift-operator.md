---
title: '&gt;&gt; 運算子 - C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: 80e38d8e75b9ad573b635d544d6381950f107583
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333679"
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="cd88c-102">&gt;&gt; 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="cd88c-102">&gt;&gt; operator (C# Reference)</span></span>

<span data-ttu-id="cd88c-103">右移運算子 (`>>`) 會向其第一個運算元右移第二個運算元所指定的位元數。</span><span class="sxs-lookup"><span data-stu-id="cd88c-103">The right-shift operator (`>>`) shifts its first operand right by the number of bits specified by its second operand.</span></span>

## <a name="remarks"></a><span data-ttu-id="cd88c-104">備註</span><span class="sxs-lookup"><span data-stu-id="cd88c-104">Remarks</span></span>

<span data-ttu-id="cd88c-105">如果第一個運算元是 [int](../keywords/int.md) 或 [uint](../keywords/uint.md) (32 位元數量)，則是由第二個運算元的低序位五位元指定移位計數 (第二個運算元 & 0x1f)。</span><span class="sxs-lookup"><span data-stu-id="cd88c-105">If the first operand is an [int](../keywords/int.md) or [uint](../keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand (second operand & 0x1f).</span></span>

<span data-ttu-id="cd88c-106">如果第一個運算元是 [long](../keywords/long.md) 或 [ulong](../keywords/ulong.md) (64 位元數量)，則是由第二個運算元的低序位六位元指定移位計數 (第二個運算元 & 0x3f)。</span><span class="sxs-lookup"><span data-stu-id="cd88c-106">If the first operand is a [long](../keywords/long.md) or [ulong](../keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand (second operand & 0x3f).</span></span>

<span data-ttu-id="cd88c-107">如果第一個運算元是 [int](../keywords/int.md) 或 [long](../keywords/long.md)，則右移是算術移位 (高序位空位元會設定為正負號位元)。</span><span class="sxs-lookup"><span data-stu-id="cd88c-107">If the first operand is an [int](../keywords/int.md) or [long](../keywords/long.md), the right-shift is an arithmetic shift (high-order empty bits are set to the sign bit).</span></span> <span data-ttu-id="cd88c-108">如果第一個運算元的類型為 [uint](../keywords/uint.md) 或 [ulong](../keywords/ulong.md)，則右移是邏輯移位 (高序位位元會填上零)。</span><span class="sxs-lookup"><span data-stu-id="cd88c-108">If the first operand is of type [uint](../keywords/uint.md) or [ulong](../keywords/ulong.md), the right-shift is a logical shift (high-order bits are zero-filled).</span></span>

<span data-ttu-id="cd88c-109">使用者定義型別可以多載 `>>` 運算子；第一個運算元的類型必須是使用者定義型別，而第二個運算元的類型必須是 [int](../keywords/int.md)。如需詳細資訊，請參閱[運算子](../keywords/operator.md)。</span><span class="sxs-lookup"><span data-stu-id="cd88c-109">User-defined types can overload the `>>` operator; the type of the first operand must be the user-defined type, and the type of the second operand must be [int](../keywords/int.md). For more information, see [operator](../keywords/operator.md).</span></span> <span data-ttu-id="cd88c-110">二元運算子多載時，對應的指派運算子 (若有) 也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="cd88c-110">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>

## <a name="example"></a><span data-ttu-id="cd88c-111">範例</span><span class="sxs-lookup"><span data-stu-id="cd88c-111">Example</span></span>

[!code-csharp[csRefOperators#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#26)]

## <a name="see-also"></a><span data-ttu-id="cd88c-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="cd88c-112">See Also</span></span>

- [<span data-ttu-id="cd88c-113">C# 參考</span><span class="sxs-lookup"><span data-stu-id="cd88c-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cd88c-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cd88c-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cd88c-115">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="cd88c-115">C# operators</span></span>](index.md)