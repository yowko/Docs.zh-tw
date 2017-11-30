---
title: "如何：取得指標變數值 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8065c10bec737789f13dcbafe147b50eedb9da36
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a><span data-ttu-id="89ce3-102">如何：取得指標變數值 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="89ce3-102">How to: Obtain the Value of a Pointer Variable (C# Programming Guide)</span></span>
<span data-ttu-id="89ce3-103">您可以使用指標間接運算子來取得指標所指向位置的變數。</span><span class="sxs-lookup"><span data-stu-id="89ce3-103">Use the pointer indirection operator to obtain the variable at the location pointed to by a pointer.</span></span> <span data-ttu-id="89ce3-104">運算式會採用下列格式，其中 `p` 是指標類型：</span><span class="sxs-lookup"><span data-stu-id="89ce3-104">The expression takes the following form, where `p` is a pointer type:</span></span>  
  
```  
*p;  
```  
  
 <span data-ttu-id="89ce3-105">您無法在非指標類型之任何類型的運算式上使用一元間接運算子。</span><span class="sxs-lookup"><span data-stu-id="89ce3-105">You cannot use the unary indirection operator on an expression of any type other than the pointer type.</span></span> <span data-ttu-id="89ce3-106">此外，也無法將它套用至 [void](../../../csharp/language-reference/keywords/void.md) 指標。</span><span class="sxs-lookup"><span data-stu-id="89ce3-106">Also, you cannot apply it to a [void](../../../csharp/language-reference/keywords/void.md) pointer.</span></span>  
  
 <span data-ttu-id="89ce3-107">當您將間接運算子套用至 [null](../../../csharp/language-reference/keywords/null.md) 指標時，結果會取決於實作。</span><span class="sxs-lookup"><span data-stu-id="89ce3-107">When you apply the indirection operator to a [null](../../../csharp/language-reference/keywords/null.md) pointer, the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="89ce3-108">範例</span><span class="sxs-lookup"><span data-stu-id="89ce3-108">Example</span></span>  
 <span data-ttu-id="89ce3-109">在下列範例中，`char` 類型的變數會使用不同類型的指標來存取。</span><span class="sxs-lookup"><span data-stu-id="89ce3-109">In the following example, a variable of the type `char` is accessed by using pointers of different types.</span></span> <span data-ttu-id="89ce3-110">請注意，`theChar` 的位址會因執行而異，原因是配置給變數的實體位址可能會變更。</span><span class="sxs-lookup"><span data-stu-id="89ce3-110">Note that the address of `theChar` will vary from run to run, because the physical address allocated to a variable can change.</span></span>  
  
 [!code-csharp[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
 <span data-ttu-id="89ce3-111">**值為 theChar = Z**</span><span class="sxs-lookup"><span data-stu-id="89ce3-111">**Value of theChar = Z**</span></span>  
<span data-ttu-id="89ce3-112">**位址為 theChar = 12F718**</span><span class="sxs-lookup"><span data-stu-id="89ce3-112">**Address of theChar = 12F718**</span></span>  
<span data-ttu-id="89ce3-113">**值為 pChar = Z** </span><span class="sxs-lookup"><span data-stu-id="89ce3-113">**Value of pChar = Z** </span></span>  
<span data-ttu-id="89ce3-114">**值為 pInt = 90**</span><span class="sxs-lookup"><span data-stu-id="89ce3-114">**Value of pInt = 90**</span></span>    
## <a name="see-also"></a><span data-ttu-id="89ce3-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89ce3-115">See Also</span></span>  
 [<span data-ttu-id="89ce3-116">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="89ce3-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="89ce3-117">指標運算式</span><span class="sxs-lookup"><span data-stu-id="89ce3-117">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="89ce3-118">指標型別</span><span class="sxs-lookup"><span data-stu-id="89ce3-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="89ce3-119">型別</span><span class="sxs-lookup"><span data-stu-id="89ce3-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="89ce3-120">Unsafe.DangerousAPI</span><span class="sxs-lookup"><span data-stu-id="89ce3-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="89ce3-121">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="89ce3-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="89ce3-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="89ce3-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
