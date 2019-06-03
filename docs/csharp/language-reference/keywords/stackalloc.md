---
title: stackalloc 關鍵字 - C# 參考
ms.custom: seodec18
ms.date: 04/10/2019
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: c72daa58d2fceb05d9cc9c388a9d2e5dbe062796
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422434"
---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="731e6-102">stackalloc (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="731e6-102">stackalloc (C# Reference)</span></span>

<span data-ttu-id="731e6-103">`stackalloc` 關鍵字是用來在堆疊上配置記憶體區塊。</span><span class="sxs-lookup"><span data-stu-id="731e6-103">The `stackalloc` keyword is used to allocate a block of memory on the stack.</span></span>

```csharp
Span<int> block = stackalloc int[100];
```

<span data-ttu-id="731e6-104">將已配置的區塊指派至 <xref:System.Span%601?displayName=nameWithType> (而非 `int*`) 可允許在安全區塊中進行堆疊配置。</span><span class="sxs-lookup"><span data-stu-id="731e6-104">Assigning the allocated block to a <xref:System.Span%601?displayName=nameWithType> instead of an `int*` allows stack allocations in a safe block.</span></span> <span data-ttu-id="731e6-105">不需要 `unsafe` 內容。</span><span class="sxs-lookup"><span data-stu-id="731e6-105">The `unsafe` context is not required.</span></span>

## <a name="remarks"></a><span data-ttu-id="731e6-106">備註</span><span class="sxs-lookup"><span data-stu-id="731e6-106">Remarks</span></span>

<span data-ttu-id="731e6-107">關鍵字只適用於區域變數初始設定式。</span><span class="sxs-lookup"><span data-stu-id="731e6-107">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="731e6-108">下列程式碼會導致編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="731e6-108">The following code causes compiler errors.</span></span>

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
Span<int> span;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
span = stackalloc int[100];
```

<span data-ttu-id="731e6-109">從 C# 7.3 開始，您可以使用 `stackalloc` 陣列的陣列初始設定式語法。</span><span class="sxs-lookup"><span data-stu-id="731e6-109">Beginning with C# 7.3, you can use array initializer syntax for `stackalloc` arrays.</span></span> <span data-ttu-id="731e6-110">所有下列宣告都會宣告包含三個元素的陣列，且元素的值是整數 `1`、`2` 和 `3`。</span><span class="sxs-lookup"><span data-stu-id="731e6-110">All the following declarations declare an array with three elements whose values are the integers `1`, `2`, and `3`.</span></span> <span data-ttu-id="731e6-111">第二個初始化會將記憶體指派至 <xref:System.ReadOnlySpan%601>，指出該記憶體無法被修改。</span><span class="sxs-lookup"><span data-stu-id="731e6-111">The second initialization assigns the memory to a <xref:System.ReadOnlySpan%601>, indicating that the memory cannot be modified.</span></span>

```csharp
// Valid starting with C# 7.3
Span<int> first = stackalloc int[3] { 1, 2, 3 };
ReadOnlySpan<int> second = stackalloc int[] { 1, 2, 3 };
Span<int> third = stackalloc[] { 1, 2, 3 };
```

<span data-ttu-id="731e6-112">涉及指標類型時，`stackalloc` 需要 [unsafe](unsafe.md) 內容。</span><span class="sxs-lookup"><span data-stu-id="731e6-112">When pointer types are involved, `stackalloc` requires an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="731e6-113">如需詳細資訊，請參閱[不安全的程式碼和指標](../../programming-guide/unsafe-code-pointers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="731e6-113">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="731e6-114">`stackalloc` 就像 C 執行階段程式庫中的 [_alloca](/cpp/c-runtime-library/reference/alloca)。</span><span class="sxs-lookup"><span data-stu-id="731e6-114">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>

## <a name="examples"></a><span data-ttu-id="731e6-115">範例</span><span class="sxs-lookup"><span data-stu-id="731e6-115">Examples</span></span>

<span data-ttu-id="731e6-116">下列範例會計算並顯示 Fibonacci 序列中的前 20 個數字。</span><span class="sxs-lookup"><span data-stu-id="731e6-116">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="731e6-117">每個數字都是前兩個數字的總和。</span><span class="sxs-lookup"><span data-stu-id="731e6-117">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="731e6-118">在程式碼中，大小足以包含 20 個類型 `int` 的項目的記憶體區塊會配置於堆疊上，而不是堆積。</span><span class="sxs-lookup"><span data-stu-id="731e6-118">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="731e6-119">區塊的位址會儲存在 `Span``fib` 中。</span><span class="sxs-lookup"><span data-stu-id="731e6-119">The address of the block is stored in the `Span` `fib`.</span></span> <span data-ttu-id="731e6-120">這個記憶體不會進行記憶體回收，因此不需要固定 (使用 [fixed](fixed-statement.md))。</span><span class="sxs-lookup"><span data-stu-id="731e6-120">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](fixed-statement.md)).</span></span> <span data-ttu-id="731e6-121">記憶體區塊的存留期只限於定義它的方法的存留期。</span><span class="sxs-lookup"><span data-stu-id="731e6-121">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="731e6-122">傳回方法之前，無法釋放記憶體。</span><span class="sxs-lookup"><span data-stu-id="731e6-122">You cannot free the memory before the method returns.</span></span>

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

<span data-ttu-id="731e6-123">下列範例會將 `stackalloc` 整數陣列初始化為位元遮罩，而且每個項目中設定一個位元。</span><span class="sxs-lookup"><span data-stu-id="731e6-123">The following example initializes a `stackalloc` array of integers to a bit mask with one bit set in each element.</span></span> <span data-ttu-id="731e6-124">這示範從 C# 7.3 開始提供的新初始設定式語法：</span><span class="sxs-lookup"><span data-stu-id="731e6-124">This demonstrates the new initializer syntax available starting in C# 7.3:</span></span>

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a><span data-ttu-id="731e6-125">安全性</span><span class="sxs-lookup"><span data-stu-id="731e6-125">Security</span></span>

<span data-ttu-id="731e6-126">您應該盡可能使用 <xref:System.Span%601> 或 <xref:System.ReadOnlySpan%601>，因為 unsafe 程式碼比起其他安全的替代內容來說較不安全。</span><span class="sxs-lookup"><span data-stu-id="731e6-126">You should use <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> when possible because unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="731e6-127">就算在搭配指標使用的情況下，使用 `stackalloc` 會自動啟用通用語言執行平台 (CLR) 中的緩衝區溢位偵測功能。</span><span class="sxs-lookup"><span data-stu-id="731e6-127">Even when used with pointers, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="731e6-128">如果偵測到緩衝區滿溢，會盡快終止處理序，將執行惡意程式碼的機會降到最低。</span><span class="sxs-lookup"><span data-stu-id="731e6-128">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="731e6-129">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="731e6-129">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="731e6-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="731e6-130">See also</span></span>

- [<span data-ttu-id="731e6-131">C# 參考</span><span class="sxs-lookup"><span data-stu-id="731e6-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="731e6-132">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="731e6-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="731e6-133">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="731e6-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="731e6-134">Unsafe 程式碼和指標</span><span class="sxs-lookup"><span data-stu-id="731e6-134">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
