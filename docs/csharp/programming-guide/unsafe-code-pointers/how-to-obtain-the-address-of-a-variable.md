---
title: "如何：取得變數位址 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- variables [C#], address of
- pointers [C#], & operator
- pointer expressions [C#], address-of operator
ms.assetid: 44fe2cd9-a64f-4ef5-be2a-09ce807c0182
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3d0969f7e62864c682660f08cd4198aa4032e0e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-the-address-of-a-variable-c-programming-guide"></a><span data-ttu-id="05af4-102">如何：取得變數位址 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="05af4-102">How to: Obtain the Address of a Variable (C# Programming Guide)</span></span>
<span data-ttu-id="05af4-103">若要取得評估為固定變數之一元運算式的位址，請使用傳址運算子：</span><span class="sxs-lookup"><span data-stu-id="05af4-103">To obtain the address of a unary expression, which evaluates to a fixed variable, use the address-of operator:</span></span>  
  
```  
int number;  
int* p = &number; //address-of operator &  
```  
  
 <span data-ttu-id="05af4-104">傳址運算子只能套用至變數。</span><span class="sxs-lookup"><span data-stu-id="05af4-104">The address-of operator can only be applied to a variable.</span></span> <span data-ttu-id="05af4-105">如果變數是可移動的變數，您可以使用 [fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md)暫時修正變數，然後再取得其位址。</span><span class="sxs-lookup"><span data-stu-id="05af4-105">If the variable is a moveable variable, you can use the [fixed statement](../../../csharp/language-reference/keywords/fixed-statement.md) to temporarily fix the variable before obtaining its address.</span></span>  
  
 <span data-ttu-id="05af4-106">您必須負責確保變數已初始化。</span><span class="sxs-lookup"><span data-stu-id="05af4-106">It is your responsibility to ensure that the variable is initialized.</span></span> <span data-ttu-id="05af4-107">如果變數未初始化，編譯器不會發出錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="05af4-107">The compiler will not issue an error message if the variable is not initialized.</span></span>  
  
 <span data-ttu-id="05af4-108">您無法取得常數或值的位址。</span><span class="sxs-lookup"><span data-stu-id="05af4-108">You cannot get the address of a constant or a value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="05af4-109">範例</span><span class="sxs-lookup"><span data-stu-id="05af4-109">Example</span></span>  
 <span data-ttu-id="05af4-110">在此範例中，`int`、`p` 的指標會宣告並指派 `number` 整數變數的位址。</span><span class="sxs-lookup"><span data-stu-id="05af4-110">In this example, a pointer to `int`, `p`, is declared and assigned the address of an integer variable, `number`.</span></span> <span data-ttu-id="05af4-111">`number` 變數會初始化，作為指派給 * p 的結果。</span><span class="sxs-lookup"><span data-stu-id="05af4-111">The variable `number` is initialized as a result of the assignment to *p.</span></span> <span data-ttu-id="05af4-112">如果您讓這個指派陳述式成為註解，即會移除 `number` 變數的初始化，而不會發出任何編譯時錯誤。</span><span class="sxs-lookup"><span data-stu-id="05af4-112">If you make this assignment statement a comment, the initialization of the variable `number` will be removed, but no compile-time error is issued.</span></span> <span data-ttu-id="05af4-113">請注意，使用[成員存取](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md)運算子`->`以取得和顯示儲存在指標中的位址。</span><span class="sxs-lookup"><span data-stu-id="05af4-113">Notice the use of the [Member Access](../../../csharp/programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md) operator `->` to obtain and display the address stored in the pointer.</span></span>  
  
 [!code-csharp[csProgGuidePointers#7](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#8](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-address-of-a-variable_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="05af4-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="05af4-114">See Also</span></span>  
 [<span data-ttu-id="05af4-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="05af4-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="05af4-116">指標運算式</span><span class="sxs-lookup"><span data-stu-id="05af4-116">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="05af4-117">指標型別</span><span class="sxs-lookup"><span data-stu-id="05af4-117">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="05af4-118">型別</span><span class="sxs-lookup"><span data-stu-id="05af4-118">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="05af4-119">Unsafe.DangerousAPI</span><span class="sxs-lookup"><span data-stu-id="05af4-119">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="05af4-120">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="05af4-120">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="05af4-121">stackalloc</span><span class="sxs-lookup"><span data-stu-id="05af4-121">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
