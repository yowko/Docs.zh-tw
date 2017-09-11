---
title: "指標的算術運算 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
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
ms.openlocfilehash: d40d44f8be590a909ff059b0fa84efb598fcf263
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a><span data-ttu-id="aaf92-102">指標的算術運算 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="aaf92-102">Arithmetic Operations on Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="aaf92-103">本主題討論如何使用 `+` 和 **-** 算術運算子來操作指標。</span><span class="sxs-lookup"><span data-stu-id="aaf92-103">This topic discusses using the arithmetic operators `+` and **-** to manipulate pointers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aaf92-104">您無法對 void 指標執行任何算術運算。</span><span class="sxs-lookup"><span data-stu-id="aaf92-104">You cannot perform any arithmetic operations on void pointers.</span></span>  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a><span data-ttu-id="aaf92-105">加入和減去指標的數值</span><span class="sxs-lookup"><span data-stu-id="aaf92-105">Adding and Subtracting Numeric Values to or From Pointers</span></span>  
 <span data-ttu-id="aaf92-106">您可以將 [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md) 或 [ulong](../../../csharp/language-reference/keywords/ulong.md) 類型的 `n` 值新增至任何類型的 `p` 指標，但 `void*` 除外。</span><span class="sxs-lookup"><span data-stu-id="aaf92-106">You can add a value `n` of type [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md) to a pointer, `p`,of any type except `void*`.</span></span> <span data-ttu-id="aaf92-107">結果 `p+n` 是新增 `n * sizeof(p) to the address of p` 所產生的指標。</span><span class="sxs-lookup"><span data-stu-id="aaf92-107">The result `p+n` is the pointer resulting from adding `n * sizeof(p) to the address of p`.</span></span> <span data-ttu-id="aaf92-108">同樣地，`p-n` 是將 `p` 位址減去 `n * sizeof(p)` 所產生的指標。</span><span class="sxs-lookup"><span data-stu-id="aaf92-108">Similarly, `p-n` is the pointer resulting from subtracting `n * sizeof(p)` from the address of `p`.</span></span>  
  
## <a name="subtracting-pointers"></a><span data-ttu-id="aaf92-109">減去指標</span><span class="sxs-lookup"><span data-stu-id="aaf92-109">Subtracting Pointers</span></span>  
 <span data-ttu-id="aaf92-110">您也可以減去相同類型的指標。</span><span class="sxs-lookup"><span data-stu-id="aaf92-110">You can also subtract pointers of the same type.</span></span> <span data-ttu-id="aaf92-111">結果的類型一律是 `long`。</span><span class="sxs-lookup"><span data-stu-id="aaf92-111">The result is always of the type `long`.</span></span> <span data-ttu-id="aaf92-112">例如，如果 `p1` 和 `p2` 是 `pointer-type*` 類型的指標，則 `p1-p2` 運算式會導致：</span><span class="sxs-lookup"><span data-stu-id="aaf92-112">For example, if `p1` and `p2` are pointers of the type `pointer-type*`, then the expression `p1-p2` results in:</span></span>  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 <span data-ttu-id="aaf92-113">如果算術運算讓指標的定義域溢位，而且結果取決於實作，則不會產生任何例外狀況。</span><span class="sxs-lookup"><span data-stu-id="aaf92-113">No exceptions are generated when the arithmetic operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aaf92-114">範例</span><span class="sxs-lookup"><span data-stu-id="aaf92-114">Example</span></span>  
 <span data-ttu-id="aaf92-115">[!code-cs[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="aaf92-115">[!code-cs[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]</span></span>  
  
 <span data-ttu-id="aaf92-116">[!code-cs[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="aaf92-116">[!code-cs[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="aaf92-117">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="aaf92-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="aaf92-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aaf92-118">See Also</span></span>  
 <span data-ttu-id="aaf92-119">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="aaf92-119">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="aaf92-120">[unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="aaf92-120">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 <span data-ttu-id="aaf92-121">[指標運算式](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="aaf92-121">[Pointer Expressions](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md) </span></span>  
 <span data-ttu-id="aaf92-122">[C# 運算子](../../../csharp/language-reference/operators/index.md) </span><span class="sxs-lookup"><span data-stu-id="aaf92-122">[C# Operators](../../../csharp/language-reference/operators/index.md) </span></span>  
 <span data-ttu-id="aaf92-123">[指標操作](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md) </span><span class="sxs-lookup"><span data-stu-id="aaf92-123">[Manipulating Pointers](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md) </span></span>  
 <span data-ttu-id="aaf92-124">[指標類型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span><span class="sxs-lookup"><span data-stu-id="aaf92-124">[Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md) </span></span>  
 <span data-ttu-id="aaf92-125">[類型](../../../csharp/language-reference/keywords/types.md) </span><span class="sxs-lookup"><span data-stu-id="aaf92-125">[Types](../../../csharp/language-reference/keywords/types.md) </span></span>  
 <span data-ttu-id="aaf92-126">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span><span class="sxs-lookup"><span data-stu-id="aaf92-126">[unsafe](../../../csharp/language-reference/keywords/unsafe.md) </span></span>  
 <span data-ttu-id="aaf92-127">[fixed 陳述式](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="aaf92-127">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 [<span data-ttu-id="aaf92-128">stackalloc</span><span class="sxs-lookup"><span data-stu-id="aaf92-128">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)

