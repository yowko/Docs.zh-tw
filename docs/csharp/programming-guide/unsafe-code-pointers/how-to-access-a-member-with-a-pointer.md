---
title: 如何：使用指標存取成員 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
ms.openlocfilehash: 20f0dd18bb5ca132d05335953958d8f747b6abc4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33332198"
---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a><span data-ttu-id="6243a-102">如何：使用指標存取成員 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="6243a-102">How to: Access a Member with a Pointer (C# Programming Guide)</span></span>
<span data-ttu-id="6243a-103">若要存取在不安全內容中宣告的結構成員，您可以使用下例所示的成員存取運算子，該例的 `p` 是包含成員 `x` 的 [struct](../../../csharp/language-reference/keywords/struct.md) 的指標。</span><span class="sxs-lookup"><span data-stu-id="6243a-103">To access a member of a struct that is declared in an unsafe context, you can use the member access operator as shown in the following example in which `p` is a pointer to a [struct](../../../csharp/language-reference/keywords/struct.md) that contains a member `x`.</span></span>  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a><span data-ttu-id="6243a-104">範例</span><span class="sxs-lookup"><span data-stu-id="6243a-104">Example</span></span>  
 <span data-ttu-id="6243a-105">在本例中，會宣告並具現化包含 `x` 和 `y` 兩個座標的 [struct](../../../csharp/language-reference/keywords/struct.md) (`CoOrds`)。</span><span class="sxs-lookup"><span data-stu-id="6243a-105">In this example, a [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, that contains the two coordinates `x` and `y` is declared and instantiated.</span></span> <span data-ttu-id="6243a-106">藉由使用成員存取運算子 `->` 和執行個體 `home` 的指標，`x` 和 `y` 成為指派的值。</span><span class="sxs-lookup"><span data-stu-id="6243a-106">By using the member access operator `->` and a pointer to the instance `home`, `x` and `y` are assigned values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6243a-107">請注意，運算式 `p->x` 相當於運算式 `(*p).x`，而且您可以使用任一運算式取得相同的結果。</span><span class="sxs-lookup"><span data-stu-id="6243a-107">Notice that the expression `p->x` is equivalent to the expression `(*p).x`, and you can obtain the same result by using either of the two expressions.</span></span>  
  
 [!code-csharp[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6243a-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="6243a-108">See Also</span></span>  
 [<span data-ttu-id="6243a-109">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="6243a-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6243a-110">指標運算式</span><span class="sxs-lookup"><span data-stu-id="6243a-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="6243a-111">指標型別</span><span class="sxs-lookup"><span data-stu-id="6243a-111">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="6243a-112">型別</span><span class="sxs-lookup"><span data-stu-id="6243a-112">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="6243a-113">Unsafe.DangerousAPI</span><span class="sxs-lookup"><span data-stu-id="6243a-113">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="6243a-114">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="6243a-114">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="6243a-115">stackalloc</span><span class="sxs-lookup"><span data-stu-id="6243a-115">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
