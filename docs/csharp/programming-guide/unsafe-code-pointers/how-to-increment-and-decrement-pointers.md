---
title: 如何：遞增和遞減指標 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], increment and decrement
- pointer expressions [C#], increment and decrement
ms.assetid: 1b8b9281-44ee-485a-9045-3db38a4b4b89
ms.openlocfilehash: 39cefc5dcebf1331a5e0ac0fadb8284e9041eb27
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44206467"
---
# <a name="how-to-increment-and-decrement-pointers-c-programming-guide"></a><span data-ttu-id="cb392-102">如何：遞增和遞減指標 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="cb392-102">How to: Increment and Decrement Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="cb392-103">使用遞增和遞減運算子 (`++` 和 `--`)，依指標類型的類型指標的 [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) 變更指標位置\*。</span><span class="sxs-lookup"><span data-stu-id="cb392-103">Use the increment and the decrement operators, `++` and `--`, to change the pointer location by [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) for a pointer of type pointer-type\*.</span></span> <span data-ttu-id="cb392-104">遞增和遞減運算式的格式如下：</span><span class="sxs-lookup"><span data-stu-id="cb392-104">The increment and decrement expressions take the following form:</span></span>  
  
```  
++p;  
p++;  
--p;  
p--;  
```  
  
 <span data-ttu-id="cb392-105">遞增和遞減運算子可以套用至任何類型的指標，類型 `void*` 除外。</span><span class="sxs-lookup"><span data-stu-id="cb392-105">The increment and decrement operators can be applied to pointers of any type except the type `void*`.</span></span>  
  
 <span data-ttu-id="cb392-106">將遞增運算子套用至類型 `pointer-type` 指標的效果，是包含在指標變數中的位址加上 [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`)。</span><span class="sxs-lookup"><span data-stu-id="cb392-106">The effect of applying the increment operator to a pointer of the type `pointer-type` is to add [sizeof](../../../csharp/language-reference/keywords/sizeof.md) (`pointer-type`) to the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="cb392-107">將遞減運算子套用至類型 `pointer-type` 指標的效果，是包含在指標變數中的位址減去 `sizeof` (`pointer-type`)。</span><span class="sxs-lookup"><span data-stu-id="cb392-107">The effect of applying the decrement operator to a pointer of the type `pointer-type` is to subtract `sizeof` (`pointer-type`) from the address that is contained in the pointer variable.</span></span>  
  
 <span data-ttu-id="cb392-108">如果運算讓指標的定義域溢位，而且結果取決於實作，則不會產生任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="cb392-108">No exceptions are generated when the operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb392-109">範例</span><span class="sxs-lookup"><span data-stu-id="cb392-109">Example</span></span>  
 <span data-ttu-id="cb392-110">在此範例中，您要按 `int` 大小遞增指標逐步執行陣列。</span><span class="sxs-lookup"><span data-stu-id="cb392-110">In this example, you step through an array by incrementing the pointer by the size of `int`.</span></span> <span data-ttu-id="cb392-111">您會在每個步驟顯示陣列元素的位址和內容。</span><span class="sxs-lookup"><span data-stu-id="cb392-111">With each step, you display the address and the content of the array element.</span></span>  
  
 [!code-csharp[csProgGuidePointers#3](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#13](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-increment-and-decrement-pointers_2.cs)]  
  
<span data-ttu-id="cb392-112">**值：0 @ 位址：12860272**
**值：1 @ 位址：12860276**
**值：2 @ 位址：12860280**
**值：3 @ 位址：12860284**
**值：4 @ 位址：12860288**</span><span class="sxs-lookup"><span data-stu-id="cb392-112">**Value:0 @ Address:12860272**
**Value:1 @ Address:12860276**
**Value:2 @ Address:12860280**
**Value:3 @ Address:12860284**
**Value:4 @ Address:12860288**</span></span>

## <a name="see-also"></a><span data-ttu-id="cb392-113">請參閱</span><span class="sxs-lookup"><span data-stu-id="cb392-113">See Also</span></span>

- [<span data-ttu-id="cb392-114">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cb392-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="cb392-115">指標運算式</span><span class="sxs-lookup"><span data-stu-id="cb392-115">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="cb392-116">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="cb392-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="cb392-117">指標操作</span><span class="sxs-lookup"><span data-stu-id="cb392-117">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
- [<span data-ttu-id="cb392-118">指標型別</span><span class="sxs-lookup"><span data-stu-id="cb392-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="cb392-119">型別</span><span class="sxs-lookup"><span data-stu-id="cb392-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="cb392-120">Unsafe.DangerousAPI</span><span class="sxs-lookup"><span data-stu-id="cb392-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="cb392-121">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="cb392-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="cb392-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="cb392-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
