---
title: ~ 運算子 (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
ms.openlocfilehash: 25b157fafde7d2b75cd8b112848a01e9b3fb0db2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="02dc9-102">~ 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="02dc9-102">~ Operator (C# Reference)</span></span>
<span data-ttu-id="02dc9-103">`~` 運算子會對其運算元執行位元補數運算，其有反轉每個位元的效果。</span><span class="sxs-lookup"><span data-stu-id="02dc9-103">The `~` operator performs a bitwise complement operation on its operand, which has the effect of reversing each bit.</span></span> <span data-ttu-id="02dc9-104">位元補數運算子會針對 [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md) 和[ulong](../../../csharp/language-reference/keywords/ulong.md) 預先定義。</span><span class="sxs-lookup"><span data-stu-id="02dc9-104">Bitwise complement operators are predefined for [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), and [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="02dc9-105">`~` 符號也用來宣告完成項。</span><span class="sxs-lookup"><span data-stu-id="02dc9-105">The `~` symbol also is used to declare finalizers.</span></span> <span data-ttu-id="02dc9-106">如需詳細資訊，請參閱[完成項](../../../csharp/programming-guide/classes-and-structs/destructors.md)。</span><span class="sxs-lookup"><span data-stu-id="02dc9-106">For more information, see [Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02dc9-107">備註</span><span class="sxs-lookup"><span data-stu-id="02dc9-107">Remarks</span></span>  
 <span data-ttu-id="02dc9-108">使用者定義型別可以多載 `~` 運算子。</span><span class="sxs-lookup"><span data-stu-id="02dc9-108">User-defined types can overload the `~` operator.</span></span> <span data-ttu-id="02dc9-109">如需詳細資訊，請參閱[運算子](../../../csharp/language-reference/keywords/operator.md)。</span><span class="sxs-lookup"><span data-stu-id="02dc9-109">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="02dc9-110">整數類資料類型上的作業通常允許用於列舉型別。</span><span class="sxs-lookup"><span data-stu-id="02dc9-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02dc9-111">範例</span><span class="sxs-lookup"><span data-stu-id="02dc9-111">Example</span></span>  
 [!code-csharp[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="02dc9-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="02dc9-112">See Also</span></span>  
 [<span data-ttu-id="02dc9-113">C# 參考</span><span class="sxs-lookup"><span data-stu-id="02dc9-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="02dc9-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="02dc9-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="02dc9-115">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="02dc9-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="02dc9-116">完成項</span><span class="sxs-lookup"><span data-stu-id="02dc9-116">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)
