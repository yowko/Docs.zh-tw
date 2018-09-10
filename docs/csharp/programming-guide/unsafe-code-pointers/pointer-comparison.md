---
title: 指標比較 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], comparison
ms.assetid: fcafd514-7405-4deb-8490-cc58efda5495
ms.openlocfilehash: fa980c944159c477c333762ffad569332fba9402
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2018
ms.locfileid: "44086635"
---
# <a name="pointer-comparison-c-programming-guide"></a><span data-ttu-id="5672f-102">指標比較 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="5672f-102">Pointer Comparison (C# Programming Guide)</span></span>
<span data-ttu-id="5672f-103">您可以套用下列運算子來比較任何類型的指標：</span><span class="sxs-lookup"><span data-stu-id="5672f-103">You can apply the following operators to compare pointers of any type:</span></span>  
  
 <span data-ttu-id="5672f-104">**==   !=   \<   >   \<=   >=**</span><span class="sxs-lookup"><span data-stu-id="5672f-104">**==   !=   \<   >   \<=   >=**</span></span>  
  
 <span data-ttu-id="5672f-105">比較運算子會比較兩個運算元的位址，就像它們是不帶正負號的整數一樣。</span><span class="sxs-lookup"><span data-stu-id="5672f-105">The comparison operators compare the addresses of the two operands as if they are unsigned integers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5672f-106">範例</span><span class="sxs-lookup"><span data-stu-id="5672f-106">Example</span></span>  
 [!code-csharp[csProgGuidePointers#16](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#17](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/pointer-comparison_2.cs)]  
  
## <a name="sample-output"></a><span data-ttu-id="5672f-107">範例輸出</span><span class="sxs-lookup"><span data-stu-id="5672f-107">Sample Output</span></span>  
 `True`  
  
 `False`  
  
## <a name="see-also"></a><span data-ttu-id="5672f-108">請參閱</span><span class="sxs-lookup"><span data-stu-id="5672f-108">See Also</span></span>

- [<span data-ttu-id="5672f-109">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5672f-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="5672f-110">指標運算式</span><span class="sxs-lookup"><span data-stu-id="5672f-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="5672f-111">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="5672f-111">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="5672f-112">指標操作</span><span class="sxs-lookup"><span data-stu-id="5672f-112">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [<span data-ttu-id="5672f-113">指標型別</span><span class="sxs-lookup"><span data-stu-id="5672f-113">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="5672f-114">型別</span><span class="sxs-lookup"><span data-stu-id="5672f-114">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="5672f-115">Unsafe.DangerousAPI</span><span class="sxs-lookup"><span data-stu-id="5672f-115">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="5672f-116">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="5672f-116">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="5672f-117">stackalloc</span><span class="sxs-lookup"><span data-stu-id="5672f-117">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
