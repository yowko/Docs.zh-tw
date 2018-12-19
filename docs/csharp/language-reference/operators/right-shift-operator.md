---
title: '&gt;&gt; 運算子- C# 參考'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>_CSharpKeyword'
helpviewer_keywords:
- '>> operator [C#]'
- right shift operator (>>) [C#]
ms.assetid: a07f8679-d318-4ef8-b38b-65903efb8056
ms.openlocfilehash: fc3d683f212c71620049ec6adee3d20bd5c1437c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239991"
---
# <a name="gtgt-operator-c-reference"></a><span data-ttu-id="6cb29-102">&gt;&gt; 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="6cb29-102">&gt;&gt; Operator (C# Reference)</span></span>
<span data-ttu-id="6cb29-103">右移運算子 (`>>`) 會向其第一個運算元右移第二個運算元所指定的位元數。</span><span class="sxs-lookup"><span data-stu-id="6cb29-103">The right-shift operator (`>>`) shifts its first operand right by the number of bits specified by its second operand.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6cb29-104">備註</span><span class="sxs-lookup"><span data-stu-id="6cb29-104">Remarks</span></span>  
 <span data-ttu-id="6cb29-105">如果第一個運算元是 [int](../../../csharp/language-reference/keywords/int.md) 或 [uint](../../../csharp/language-reference/keywords/uint.md) (32 位元數量)，則是由第二個運算元的低序位五位元指定移位計數 (第二個運算元 & 0x1f)。</span><span class="sxs-lookup"><span data-stu-id="6cb29-105">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand (second operand & 0x1f).</span></span>  
  
 <span data-ttu-id="6cb29-106">如果第一個運算元是 [long](../../../csharp/language-reference/keywords/long.md) 或 [ulong](../../../csharp/language-reference/keywords/ulong.md) (64 位元數量)，則是由第二個運算元的低序位六位元指定移位計數 (第二個運算元 & 0x3f)。</span><span class="sxs-lookup"><span data-stu-id="6cb29-106">If the first operand is a [long](../../../csharp/language-reference/keywords/long.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand (second operand & 0x3f).</span></span>  
  
 <span data-ttu-id="6cb29-107">如果第一個運算元是 [int](../../../csharp/language-reference/keywords/int.md) 或 [long](../../../csharp/language-reference/keywords/long.md)，則右移是算術移位 (高序位空位元會設定為正負號位元)。</span><span class="sxs-lookup"><span data-stu-id="6cb29-107">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [long](../../../csharp/language-reference/keywords/long.md), the right-shift is an arithmetic shift (high-order empty bits are set to the sign bit).</span></span> <span data-ttu-id="6cb29-108">如果第一個運算元的類型為 [uint](../../../csharp/language-reference/keywords/uint.md) 或 [ulong](../../../csharp/language-reference/keywords/ulong.md)，則右移是邏輯移位 (高序位位元會填上零)。</span><span class="sxs-lookup"><span data-stu-id="6cb29-108">If the first operand is of type [uint](../../../csharp/language-reference/keywords/uint.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md), the right-shift is a logical shift (high-order bits are zero-filled).</span></span>  
  
 <span data-ttu-id="6cb29-109">使用者定義型別可以多載 `>>` 運算子；第一個運算元的類型必須是使用者定義型別，而第二個運算元的類型必須是 [int](../../../csharp/language-reference/keywords/int.md)。如需詳細資訊，請參閱[運算子](../../../csharp/language-reference/keywords/operator.md)。</span><span class="sxs-lookup"><span data-stu-id="6cb29-109">User-defined types can overload the `>>` operator; the type of the first operand must be the user-defined type, and the type of the second operand must be [int](../../../csharp/language-reference/keywords/int.md). For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="6cb29-110">二元運算子多載時，對應的指派運算子 (若有) 也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="6cb29-110">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cb29-111">範例</span><span class="sxs-lookup"><span data-stu-id="6cb29-111">Example</span></span>  
 [!code-csharp[csRefOperators#26](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6cb29-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="6cb29-112">See Also</span></span>

- [<span data-ttu-id="6cb29-113">C# 參考</span><span class="sxs-lookup"><span data-stu-id="6cb29-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="6cb29-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6cb29-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="6cb29-115">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="6cb29-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
