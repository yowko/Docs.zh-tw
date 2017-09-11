---
title: "~ 運算子 (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ~_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ffbfc379b7c021ccd8fbed9b796aa9fda6618b55
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="77f07-102">~ 運算子 (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="77f07-102">~ Operator (C# Reference)</span></span>
<span data-ttu-id="77f07-103">`~` 運算子會對其運算元執行位元補數運算，其有反轉每個位元的效果。</span><span class="sxs-lookup"><span data-stu-id="77f07-103">The `~` operator performs a bitwise complement operation on its operand, which has the effect of reversing each bit.</span></span> <span data-ttu-id="77f07-104">位元補數運算子會針對 [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md) 和[ulong](../../../csharp/language-reference/keywords/ulong.md) 預先定義。</span><span class="sxs-lookup"><span data-stu-id="77f07-104">Bitwise complement operators are predefined for [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), and [ulong](../../../csharp/language-reference/keywords/ulong.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="77f07-105">`~` 符號也用來宣告完成項。</span><span class="sxs-lookup"><span data-stu-id="77f07-105">The `~` symbol also is used to declare finalizers.</span></span> <span data-ttu-id="77f07-106">如需詳細資訊，請參閱[完成項](../../../csharp/programming-guide/classes-and-structs/destructors.md)。</span><span class="sxs-lookup"><span data-stu-id="77f07-106">For more information, see [Finalizers](../../../csharp/programming-guide/classes-and-structs/destructors.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="77f07-107">備註</span><span class="sxs-lookup"><span data-stu-id="77f07-107">Remarks</span></span>  
 <span data-ttu-id="77f07-108">使用者定義型別可以多載 `~` 運算子。</span><span class="sxs-lookup"><span data-stu-id="77f07-108">User-defined types can overload the `~` operator.</span></span> <span data-ttu-id="77f07-109">如需詳細資訊，請參閱[運算子](../../../csharp/language-reference/keywords/operator.md)。</span><span class="sxs-lookup"><span data-stu-id="77f07-109">For more information, see [operator](../../../csharp/language-reference/keywords/operator.md).</span></span> <span data-ttu-id="77f07-110">整數類資料類型上的作業通常允許用於列舉型別。</span><span class="sxs-lookup"><span data-stu-id="77f07-110">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77f07-111">範例</span><span class="sxs-lookup"><span data-stu-id="77f07-111">Example</span></span>  
 <span data-ttu-id="77f07-112">[!code-cs[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="77f07-112">[!code-cs[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77f07-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77f07-113">See Also</span></span>  
 <span data-ttu-id="77f07-114">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="77f07-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="77f07-115">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="77f07-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="77f07-116">[C# 運算子](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="77f07-116">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 [<span data-ttu-id="77f07-117">完成項</span><span class="sxs-lookup"><span data-stu-id="77f07-117">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)

