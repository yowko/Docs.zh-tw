---
title: "&lt;&lt; 運算子 (C# 參考)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: <<_CSharpKeyword
helpviewer_keywords:
- left shift operator (<<) [C#]
- << operator [C#]
ms.assetid: a654eb56-1ff7-4bf3-9064-b631be0cdccc
caps.latest.revision: "18"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 400dbc799c68bb9e1bc00695954115f2eb6af7c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="71689-102">&lt;&lt; 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="71689-102">&lt;&lt; Operator (C# Reference)</span></span>
<span data-ttu-id="71689-103">左移運算子 (`<<`) 會向其第一個運算元左移第二個運算元所指定的位元數。</span><span class="sxs-lookup"><span data-stu-id="71689-103">The left-shift operator (`<<`) shifts its first operand left by the number of bits specified by its second operand.</span></span> <span data-ttu-id="71689-104">第二個運算元的類型必須是 [int](../../../csharp/language-reference/keywords/int.md) 或對 `int` 進行預先定義隱含數值轉換的類型。</span><span class="sxs-lookup"><span data-stu-id="71689-104">The type of the second operand must be an [int](../../../csharp/language-reference/keywords/int.md) or a type that has a predefined implicit numeric conversion to `int`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="71689-105">備註</span><span class="sxs-lookup"><span data-stu-id="71689-105">Remarks</span></span>  
 <span data-ttu-id="71689-106">如果第一個運算元是 [int](../../../csharp/language-reference/keywords/int.md) 或 [uint](../../../csharp/language-reference/keywords/uint.md) (32 位元數量)，則是由第二個運算元的低序位五位元指定移位計數。</span><span class="sxs-lookup"><span data-stu-id="71689-106">If the first operand is an [int](../../../csharp/language-reference/keywords/int.md) or [uint](../../../csharp/language-reference/keywords/uint.md) (32-bit quantity), the shift count is given by the low-order five bits of the second operand.</span></span> <span data-ttu-id="71689-107">也就是，實際移位計數是 0 到 31 位元。</span><span class="sxs-lookup"><span data-stu-id="71689-107">That is, the actual shift count is 0 to 31 bits.</span></span>  
  
 <span data-ttu-id="71689-108">如果第一個運算元是 [long](../../../csharp/language-reference/keywords/long.md) 或 [ulong](../../../csharp/language-reference/keywords/ulong.md) (64 位元數量)，則是由第二個運算元的低序位六位元指定移位計數。</span><span class="sxs-lookup"><span data-stu-id="71689-108">If the first operand is a [long](../../../csharp/language-reference/keywords/long.md) or [ulong](../../../csharp/language-reference/keywords/ulong.md) (64-bit quantity), the shift count is given by the low-order six bits of the second operand.</span></span> <span data-ttu-id="71689-109">也就是，實際移位計數是 0 到 63 位元。</span><span class="sxs-lookup"><span data-stu-id="71689-109">That is, the actual shift count is 0 to 63 bits.</span></span>  
  
 <span data-ttu-id="71689-110">會捨棄移位後面不在第一個運算元類型範圍內的任何高序位位元，而且低序位空位元都會填入零。</span><span class="sxs-lookup"><span data-stu-id="71689-110">Any high-order bits that are not within the range of the type of the first operand after the shift are discarded, and the low-order empty bits are zero-filled.</span></span> <span data-ttu-id="71689-111">移位作業絕不會造成溢位。</span><span class="sxs-lookup"><span data-stu-id="71689-111">Shift operations never cause overflows.</span></span>  
  
 <span data-ttu-id="71689-112">使用者定義型別可以多載 `<<` 運算子 (請參閱 [operator](../../../csharp/language-reference/keywords/operator.md))；第一個運算元的類型必須是使用者定義型別，而第二個運算元的類型必須是 `int`。</span><span class="sxs-lookup"><span data-stu-id="71689-112">User-defined types can overload the `<<` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)); the type of the first operand must be the user-defined type, and the type of the second operand must be `int`.</span></span> <span data-ttu-id="71689-113">二元運算子多載時，對應的指派運算子 (若有) 也會隱含地多載。</span><span class="sxs-lookup"><span data-stu-id="71689-113">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71689-114">範例</span><span class="sxs-lookup"><span data-stu-id="71689-114">Example</span></span>  
 [!code-csharp[csRefOperators#14](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-operator_1.cs)]  
  
## <a name="comments"></a><span data-ttu-id="71689-115">註解</span><span class="sxs-lookup"><span data-stu-id="71689-115">Comments</span></span>  
 <span data-ttu-id="71689-116">請注意，`i<<1` 和 `i<<33` 提供相同的結果，因為 1 和 33 有相同的低序位五位元。</span><span class="sxs-lookup"><span data-stu-id="71689-116">Note that `i<<1` and `i<<33` give the same result, because 1 and 33 have the same low-order five bits.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71689-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="71689-117">See Also</span></span>  
 [<span data-ttu-id="71689-118">C# 參考</span><span class="sxs-lookup"><span data-stu-id="71689-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="71689-119">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="71689-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="71689-120">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="71689-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
