---
title: "指標比較 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0b45b9152272244b9a0c9d0fa3787973f8f8182a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="00da5-102">指標比較 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="00da5-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="00da5-103">您可以套用下列運算子來比較任何類型的指標：</span><span class="sxs-lookup"><span data-stu-id="00da5-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="00da5-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="00da5-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="00da5-105">比較運算子會比較兩個運算元的位址，就像它們是不帶正負號的整數一樣。</span><span class="sxs-lookup"><span data-stu-id="00da5-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="00da5-106">範例</span><span class="sxs-lookup"><span data-stu-id="00da5-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#17](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_2.cs)]  
  
## <a name="sample-output"></a><span data-ttu-id="00da5-107">範例輸出</span><span class="sxs-lookup"><span data-stu-id="00da5-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="00da5-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00da5-108">See Also</span></span>  
 [<span data-ttu-id="00da5-109">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="00da5-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="00da5-110">指標運算式</span><span class="sxs-lookup"><span data-stu-id="00da5-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="00da5-111">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="00da5-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="00da5-112">指標操作</span><span class="sxs-lookup"><span data-stu-id="00da5-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [<span data-ttu-id="00da5-113">指標型別</span><span class="sxs-lookup"><span data-stu-id="00da5-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="00da5-114">型別</span><span class="sxs-lookup"><span data-stu-id="00da5-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="00da5-115">Unsafe.DangerousAPI</span><span class="sxs-lookup"><span data-stu-id="00da5-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="00da5-116">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="00da5-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="00da5-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="00da5-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
