---
title: "stackalloc (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
dev_langs:
- CSharp
helpviewer_keywords:
- stackalloc keyword [C#]
ms.assetid: adc04c28-3ed2-4326-807a-7545df92b852
caps.latest.revision: 27
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
ms.openlocfilehash: 53d61cfdcf4d356a28881c57ad923017c2b479ae
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="025c2-102">stackalloc (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="025c2-102">stackalloc (C# Reference)</span></span>
<span data-ttu-id="025c2-103">unsafe 程式碼內容中使用 `stackalloc` 關鍵字來配置堆疊上的記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="025c2-103">The `stackalloc` keyword is used in an unsafe code context to allocate a block of memory on the stack.</span></span>  
  
```  
int* block = stackalloc int[100];  
```  
  
## <a name="remarks"></a><span data-ttu-id="025c2-104">備註</span><span class="sxs-lookup"><span data-stu-id="025c2-104">Remarks</span></span>  
 <span data-ttu-id="025c2-105">關鍵字只適用於區域變數初始設定式。</span><span class="sxs-lookup"><span data-stu-id="025c2-105">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="025c2-106">下列程式碼會導致編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="025c2-106">The following code causes compiler errors.</span></span>  
  
```  
int* block;  
// The following assignment statement causes compiler errors. You  
// can use stackalloc only when declaring and initializing a local   
// variable.  
block = stackalloc int[100];  
```  
  
 <span data-ttu-id="025c2-107">因為涉及指標類型，所以 `stackalloc` 需要 [unsafe](../../../csharp/language-reference/keywords/unsafe.md) 內容。</span><span class="sxs-lookup"><span data-stu-id="025c2-107">Because pointer types are involved, `stackalloc` requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context.</span></span> <span data-ttu-id="025c2-108">如需詳細資訊，請參閱 [Unsafe 程式碼和指標](../../../csharp/programming-guide/unsafe-code-pointers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="025c2-108">For more information, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
 <span data-ttu-id="025c2-109">`stackalloc` 就像 C 執行階段程式庫中的 [_alloca](/cpp/c-runtime-library/reference/alloca)。</span><span class="sxs-lookup"><span data-stu-id="025c2-109">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>  
  
 <span data-ttu-id="025c2-110">下列範例會計算並顯示 Fibonacci 序列中的前 20 個數字。</span><span class="sxs-lookup"><span data-stu-id="025c2-110">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="025c2-111">每個數字都是前兩個數字的總和。</span><span class="sxs-lookup"><span data-stu-id="025c2-111">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="025c2-112">在程式碼中，大小足以包含 20 個類型 `int` 的項目的記憶體區塊會配置於堆疊上，而不是堆積。</span><span class="sxs-lookup"><span data-stu-id="025c2-112">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="025c2-113">區塊的位址會儲存在指標 `fib` 中。</span><span class="sxs-lookup"><span data-stu-id="025c2-113">The address of the block is stored in the pointer `fib`.</span></span> <span data-ttu-id="025c2-114">這個記憶體不會進行記憶體回收，因此不需要固定 (使用 [fixed](../../../csharp/language-reference/keywords/fixed-statement.md))。</span><span class="sxs-lookup"><span data-stu-id="025c2-114">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](../../../csharp/language-reference/keywords/fixed-statement.md)).</span></span> <span data-ttu-id="025c2-115">記憶體區塊的存留期只限於定義它的方法的存留期。</span><span class="sxs-lookup"><span data-stu-id="025c2-115">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="025c2-116">傳回方法之前，無法釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="025c2-116">You cannot free the memory before the method returns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="025c2-117">範例</span><span class="sxs-lookup"><span data-stu-id="025c2-117">Example</span></span>  
 <span data-ttu-id="025c2-118">[!code-cs[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="025c2-118">[!code-cs[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]</span></span>  
  
## <a name="security"></a><span data-ttu-id="025c2-119">安全性</span><span class="sxs-lookup"><span data-stu-id="025c2-119">Security</span></span>  
 <span data-ttu-id="025c2-120">不安全程式碼比安全替代項目不安全。</span><span class="sxs-lookup"><span data-stu-id="025c2-120">Unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="025c2-121">不過，使用 `stackalloc` 會自動啟用 Common Language Runtime (CLR) 中的緩衝區滿溢偵測功能。</span><span class="sxs-lookup"><span data-stu-id="025c2-121">However, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="025c2-122">如果偵測到緩衝區滿溢，會盡快終止處理序，將執行惡意程式碼的機會降到最低。</span><span class="sxs-lookup"><span data-stu-id="025c2-122">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="025c2-123">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="025c2-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="025c2-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="025c2-124">See Also</span></span>  
 <span data-ttu-id="025c2-125">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="025c2-125">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="025c2-126">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="025c2-126">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="025c2-127">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="025c2-127">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 <span data-ttu-id="025c2-128">[運算子關鍵字](../../../csharp/language-reference/keywords/operator-keywords.md) </span><span class="sxs-lookup"><span data-stu-id="025c2-128">[Operator Keywords](../../../csharp/language-reference/keywords/operator-keywords.md) </span></span>  
 [<span data-ttu-id="025c2-129">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="025c2-129">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)

