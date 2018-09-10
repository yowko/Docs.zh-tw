---
title: stackalloc (C# 參考)
ms.date: 04/12/2018
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: 5926550eea1f5a2f8fb74645f22ca54c2bed3136
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508576"
---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="76c06-102">stackalloc (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="76c06-102">stackalloc (C# Reference)</span></span>
<span data-ttu-id="76c06-103">unsafe 程式碼內容中使用 `stackalloc` 關鍵字來配置堆疊上的記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="76c06-103">The `stackalloc` keyword is used in an unsafe code context to allocate a block of memory on the stack.</span></span>

```csharp
int* block = stackalloc int[100];
```

## <a name="remarks"></a><span data-ttu-id="76c06-104">備註</span><span class="sxs-lookup"><span data-stu-id="76c06-104">Remarks</span></span>

<span data-ttu-id="76c06-105">關鍵字只適用於區域變數初始設定式。</span><span class="sxs-lookup"><span data-stu-id="76c06-105">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="76c06-106">下列程式碼會導致編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="76c06-106">The following code causes compiler errors.</span></span>

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
```

<span data-ttu-id="76c06-107">從 C# 7.3 開始，您可以使用 `stackalloc` 陣列的陣列初始設定式語法。</span><span class="sxs-lookup"><span data-stu-id="76c06-107">Beginning with C# 7.3, you can use array initializer syntax for `stackalloc` arrays.</span></span> <span data-ttu-id="76c06-108">所有下列宣告都會宣告包含三個項目的陣列，而且項目的值是整數 `1`、`2` 和 `3`：</span><span class="sxs-lookup"><span data-stu-id="76c06-108">All the following declarations declare an array with three elements whose values are the integers `1`, `2`, and `3`:</span></span>

```csharp
// Valid starting with C# 7.3
int* first = stackalloc int[3] { 1, 2, 3 };
int* second = stackalloc int[] { 1, 2, 3 };
int* third = stackalloc[] { 1, 2, 3 };
```

<span data-ttu-id="76c06-109">因為涉及指標類型，所以 `stackalloc` 需要 [unsafe](unsafe.md) 內容。</span><span class="sxs-lookup"><span data-stu-id="76c06-109">Because pointer types are involved, `stackalloc` requires an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="76c06-110">如需詳細資訊，請參閱 [Unsafe 程式碼和指標](../../programming-guide/unsafe-code-pointers/index.md)</span><span class="sxs-lookup"><span data-stu-id="76c06-110">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md)</span></span> 

<span data-ttu-id="76c06-111">`stackalloc` 就像 C 執行階段程式庫中的 [_alloca](/cpp/c-runtime-library/reference/alloca)。</span><span class="sxs-lookup"><span data-stu-id="76c06-111">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>

## <a name="examples"></a><span data-ttu-id="76c06-112">範例</span><span class="sxs-lookup"><span data-stu-id="76c06-112">Examples</span></span>

<span data-ttu-id="76c06-113">下列範例會計算並顯示 Fibonacci 序列中的前 20 個數字。</span><span class="sxs-lookup"><span data-stu-id="76c06-113">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="76c06-114">每個數字都是前兩個數字的總和。</span><span class="sxs-lookup"><span data-stu-id="76c06-114">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="76c06-115">在程式碼中，大小足以包含 20 個類型 `int` 的項目的記憶體區塊會配置於堆疊上，而不是堆積。</span><span class="sxs-lookup"><span data-stu-id="76c06-115">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="76c06-116">區塊的位址會儲存在指標 `fib` 中。</span><span class="sxs-lookup"><span data-stu-id="76c06-116">The address of the block is stored in the pointer `fib`.</span></span> <span data-ttu-id="76c06-117">這個記憶體不會進行記憶體回收，因此不需要固定 (使用 [fixed](fixed-statement.md))。</span><span class="sxs-lookup"><span data-stu-id="76c06-117">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](fixed-statement.md)).</span></span> <span data-ttu-id="76c06-118">記憶體區塊的存留期只限於定義它的方法的存留期。</span><span class="sxs-lookup"><span data-stu-id="76c06-118">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="76c06-119">傳回方法之前，無法釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="76c06-119">You cannot free the memory before the method returns.</span></span>

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

<span data-ttu-id="76c06-120">下列範例會將 `stackalloc` 整數陣列初始化為位元遮罩，而且每個項目中設定一個位元。</span><span class="sxs-lookup"><span data-stu-id="76c06-120">The following example initializes a `stackalloc` array of integers to a bit mask with one bit set in each element.</span></span> <span data-ttu-id="76c06-121">這示範從 C# 7.3 開始提供的新初始設定式語法：</span><span class="sxs-lookup"><span data-stu-id="76c06-121">This demonstrates the new initializer syntax available starting in C# 7.3:</span></span>

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a><span data-ttu-id="76c06-122">安全性</span><span class="sxs-lookup"><span data-stu-id="76c06-122">Security</span></span>

<span data-ttu-id="76c06-123">不安全程式碼比安全替代項目不安全。</span><span class="sxs-lookup"><span data-stu-id="76c06-123">Unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="76c06-124">不過，使用 `stackalloc` 會自動啟用 Common Language Runtime (CLR) 中的緩衝區滿溢偵測功能。</span><span class="sxs-lookup"><span data-stu-id="76c06-124">However, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="76c06-125">如果偵測到緩衝區滿溢，會盡快終止處理序，將執行惡意程式碼的機會降到最低。</span><span class="sxs-lookup"><span data-stu-id="76c06-125">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="76c06-126">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="76c06-126">C# Language Specification</span></span>
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="76c06-127">請參閱</span><span class="sxs-lookup"><span data-stu-id="76c06-127">See Also</span></span>

- [<span data-ttu-id="76c06-128">C# 參考</span><span class="sxs-lookup"><span data-stu-id="76c06-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="76c06-129">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="76c06-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="76c06-130">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="76c06-130">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="76c06-131">運算子關鍵字</span><span class="sxs-lookup"><span data-stu-id="76c06-131">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
- [<span data-ttu-id="76c06-132">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="76c06-132">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
