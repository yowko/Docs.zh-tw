---
title: 指標的算術運算 (C# 程式設計手冊)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 54c439aab8b6cd34a796db8d31f9eabeefddf9f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a><span data-ttu-id="f5fdf-102">指標的算術運算 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="f5fdf-102">Arithmetic Operations on Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="f5fdf-103">本主題討論如何使用 `+` 和 **-** 算術運算子來操作指標。</span><span class="sxs-lookup"><span data-stu-id="f5fdf-103">This topic discusses using the arithmetic operators `+` and **-** to manipulate pointers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5fdf-104">您無法對 void 指標執行任何算術運算。</span><span class="sxs-lookup"><span data-stu-id="f5fdf-104">You cannot perform any arithmetic operations on void pointers.</span></span>  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a><span data-ttu-id="f5fdf-105">加入和減去指標的數值</span><span class="sxs-lookup"><span data-stu-id="f5fdf-105">Adding and Subtracting Numeric Values to or From Pointers</span></span>  
 <span data-ttu-id="f5fdf-106">您可以將 [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md) 或 [ulong](../../../csharp/language-reference/keywords/ulong.md) 類型的 `n` 值新增至任何類型的 `p` 指標，但 `void*` 除外。</span><span class="sxs-lookup"><span data-stu-id="f5fdf-106">You can add a value `n` of type [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md) to a pointer, `p`,of any type except `void*`.</span></span> <span data-ttu-id="f5fdf-107">結果 `p+n` 是新增 `n * sizeof(p) to the address of p` 所產生的指標。</span><span class="sxs-lookup"><span data-stu-id="f5fdf-107">The result `p+n` is the pointer resulting from adding `n * sizeof(p) to the address of p`.</span></span> <span data-ttu-id="f5fdf-108">同樣地，`p-n` 是將 `p` 位址減去 `n * sizeof(p)` 所產生的指標。</span><span class="sxs-lookup"><span data-stu-id="f5fdf-108">Similarly, `p-n` is the pointer resulting from subtracting `n * sizeof(p)` from the address of `p`.</span></span>  
  
## <a name="subtracting-pointers"></a><span data-ttu-id="f5fdf-109">減去指標</span><span class="sxs-lookup"><span data-stu-id="f5fdf-109">Subtracting Pointers</span></span>  
 <span data-ttu-id="f5fdf-110">您也可以減去相同類型的指標。</span><span class="sxs-lookup"><span data-stu-id="f5fdf-110">You can also subtract pointers of the same type.</span></span> <span data-ttu-id="f5fdf-111">結果的類型一律是 `long`。</span><span class="sxs-lookup"><span data-stu-id="f5fdf-111">The result is always of the type `long`.</span></span> <span data-ttu-id="f5fdf-112">例如，如果 `p1` 和 `p2` 是 `pointer-type*` 類型的指標，則 `p1-p2` 運算式會導致：</span><span class="sxs-lookup"><span data-stu-id="f5fdf-112">For example, if `p1` and `p2` are pointers of the type `pointer-type*`, then the expression `p1-p2` results in:</span></span>  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 <span data-ttu-id="f5fdf-113">如果算術運算讓指標的定義域溢位，而且結果取決於實作，則不會產生任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="f5fdf-113">No exceptions are generated when the arithmetic operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5fdf-114">範例</span><span class="sxs-lookup"><span data-stu-id="f5fdf-114">Example</span></span>  
 [!code-csharp[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="f5fdf-115">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f5fdf-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f5fdf-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5fdf-116">See Also</span></span>  
 [<span data-ttu-id="f5fdf-117">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f5fdf-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="f5fdf-118">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="f5fdf-118">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="f5fdf-119">指標運算式</span><span class="sxs-lookup"><span data-stu-id="f5fdf-119">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="f5fdf-120">C# 運算子</span><span class="sxs-lookup"><span data-stu-id="f5fdf-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="f5fdf-121">指標操作</span><span class="sxs-lookup"><span data-stu-id="f5fdf-121">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [<span data-ttu-id="f5fdf-122">指標型別</span><span class="sxs-lookup"><span data-stu-id="f5fdf-122">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="f5fdf-123">型別</span><span class="sxs-lookup"><span data-stu-id="f5fdf-123">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="f5fdf-124">Unsafe.DangerousAPI</span><span class="sxs-lookup"><span data-stu-id="f5fdf-124">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="f5fdf-125">fixed 陳述式</span><span class="sxs-lookup"><span data-stu-id="f5fdf-125">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="f5fdf-126">stackalloc</span><span class="sxs-lookup"><span data-stu-id="f5fdf-126">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
