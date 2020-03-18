---
title: volatile - C# 參考
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: c7a6c442c33ac2b41f652805837f455a957819de
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712841"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="adffd-102">volatile (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="adffd-102">volatile (C# Reference)</span></span>

<span data-ttu-id="adffd-103">`volatile` 關鍵字指出某個欄位可能是由同時執行的多個執行緒所修改。</span><span class="sxs-lookup"><span data-stu-id="adffd-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="adffd-104">編譯器、執行階段系統，甚至硬體都有可能基於效能因素，而重新排列對記憶體位置的讀取和寫入。</span><span class="sxs-lookup"><span data-stu-id="adffd-104">The compiler, the runtime system, and even hardware may rearrange reads and writes to memory locations for performance reasons.</span></span> <span data-ttu-id="adffd-105">宣告為 `volatile` 的欄位不受限於這些最佳化考量。</span><span class="sxs-lookup"><span data-stu-id="adffd-105">Fields that are declared `volatile` are not subject to these optimizations.</span></span> <span data-ttu-id="adffd-106">加入 `volatile` 修飾詞可確保所有的執行緒都會依執行寫入的順序，觀察任何其他執行緒所執行的暫時性寫入。</span><span class="sxs-lookup"><span data-stu-id="adffd-106">Adding the `volatile` modifier ensures that all threads will observe volatile writes performed by any other thread in the order in which they were performed.</span></span> <span data-ttu-id="adffd-107">不保證 volatile 寫入的單一總排序如所有執行緒的執行中所示。</span><span class="sxs-lookup"><span data-stu-id="adffd-107">There is no guarantee of a single total ordering of volatile writes as seen from all threads of execution.</span></span>

<span data-ttu-id="adffd-108">`volatile` 關鍵字可以套用至下列類型的欄位：</span><span class="sxs-lookup"><span data-stu-id="adffd-108">The `volatile` keyword can be applied to fields of these types:</span></span>

- <span data-ttu-id="adffd-109">參考型別。</span><span class="sxs-lookup"><span data-stu-id="adffd-109">Reference types.</span></span>
- <span data-ttu-id="adffd-110">指標類型 (在不安全的內容中)。</span><span class="sxs-lookup"><span data-stu-id="adffd-110">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="adffd-111">請注意，雖然指標本身可為 volatile，但它所指向的物件不得為 volatile。</span><span class="sxs-lookup"><span data-stu-id="adffd-111">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="adffd-112">換句話說，您無法將指標宣告為 volatile。</span><span class="sxs-lookup"><span data-stu-id="adffd-112">In other words, you cannot declare a "pointer to volatile."</span></span>
- <span data-ttu-id="adffd-113">簡單型別，例如 `sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`char`、`float` 與 `bool`。</span><span class="sxs-lookup"><span data-stu-id="adffd-113">Simple types such as `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`, and `bool`.</span></span>
- <span data-ttu-id="adffd-114">使用下列其中一個基底類型的 `enum` 型別：`byte`、`sbyte`、`short`、`ushort`、`int` 或 `uint`。</span><span class="sxs-lookup"><span data-stu-id="adffd-114">An `enum` type with one of the following base types: `byte`, `sbyte`, `short`, `ushort`, `int`, or `uint`.</span></span>
- <span data-ttu-id="adffd-115">已知為參考型別的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="adffd-115">Generic type parameters known to be reference types.</span></span>
- <span data-ttu-id="adffd-116"><xref:System.IntPtr> 和 <xref:System.UIntPtr>。</span><span class="sxs-lookup"><span data-stu-id="adffd-116"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>

<span data-ttu-id="adffd-117">其他型別，包括 `double` 與 `long`，不能標示為 `volatile`，因為對這些型別之欄位的讀取和寫入不保證是不可部分完成。</span><span class="sxs-lookup"><span data-stu-id="adffd-117">Other types, including `double` and `long`, cannot be marked `volatile` because reads and writes to fields of those types cannot be guaranteed to be atomic.</span></span> <span data-ttu-id="adffd-118">要保護對這些類型的欄位的多執行緒訪問，請使用<xref:System.Threading.Interlocked>類成員或使用 語句[`lock`](lock-statement.md)保護訪問。</span><span class="sxs-lookup"><span data-stu-id="adffd-118">To protect multi-threaded access to those types of fields, use the <xref:System.Threading.Interlocked> class members or protect access using the [`lock`](lock-statement.md) statement.</span></span>

<span data-ttu-id="adffd-119">`volatile` 關鍵字只能套用至 `class` 或 `struct` 的欄位。</span><span class="sxs-lookup"><span data-stu-id="adffd-119">The `volatile` keyword can only be applied to fields of a `class` or `struct`.</span></span> <span data-ttu-id="adffd-120">區域變數不可以宣告為 `volatile`。</span><span class="sxs-lookup"><span data-stu-id="adffd-120">Local variables cannot be declared `volatile`.</span></span>

## <a name="example"></a><span data-ttu-id="adffd-121">範例</span><span class="sxs-lookup"><span data-stu-id="adffd-121">Example</span></span>

<span data-ttu-id="adffd-122">下列範例示範如何將公用欄位變數宣告為 `volatile`。</span><span class="sxs-lookup"><span data-stu-id="adffd-122">The following example shows how to declare a public field variable as `volatile`.</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

<span data-ttu-id="adffd-123">下列範例示範如何建立和使用輔助或背景工作執行緒，以運用主執行緒的輔助或背景工作執行緒來執行平行處理。</span><span class="sxs-lookup"><span data-stu-id="adffd-123">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="adffd-124">如需有關多執行緒的詳細資訊，請參閱 [Managed 執行緒處理](../../../standard/threading/index.md)。</span><span class="sxs-lookup"><span data-stu-id="adffd-124">For more information about multithreading, see [Managed Threading](../../../standard/threading/index.md).</span></span>

[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

<span data-ttu-id="adffd-125">將 `volatile` 修飾詞新增到 `_shouldStop` 的宣告之後，您將會一律取得相同的結果 (類似上述程式碼顯示的摘要)。</span><span class="sxs-lookup"><span data-stu-id="adffd-125">With the `volatile` modifier added to the declaration of `_shouldStop` in place, you'll always get the same results (similar to the excerpt shown in the preceding code).</span></span> <span data-ttu-id="adffd-126">不過，如果 `_shouldStop` 成員上沒有修飾詞，則行為是無法預測的。</span><span class="sxs-lookup"><span data-stu-id="adffd-126">However, without that modifier on the `_shouldStop` member, the behavior is unpredictable.</span></span> <span data-ttu-id="adffd-127">`DoWork` 方法可能會將成員存取最佳化，導致讀取過時的資料。</span><span class="sxs-lookup"><span data-stu-id="adffd-127">The `DoWork` method may optimize the member access, resulting in reading stale data.</span></span> <span data-ttu-id="adffd-128">由於多執行緒程式設計的特性，過時讀取的數目是無法預測的。</span><span class="sxs-lookup"><span data-stu-id="adffd-128">Because of the nature of multi-threaded programming, the number of stale reads is unpredictable.</span></span> <span data-ttu-id="adffd-129">程式不同次的執行會產生不同的結果。</span><span class="sxs-lookup"><span data-stu-id="adffd-129">Different runs of the program will produce somewhat different results.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="adffd-130">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="adffd-130">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="adffd-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adffd-131">See also</span></span>

- [<span data-ttu-id="adffd-132">C# 語言規格：volatile 關鍵字</span><span class="sxs-lookup"><span data-stu-id="adffd-132">C# language specification: volatile keyword</span></span>](../../../../_csharplang/spec/classes.md#volatile-fields)
- [<span data-ttu-id="adffd-133">C# 參考</span><span class="sxs-lookup"><span data-stu-id="adffd-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="adffd-134">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="adffd-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="adffd-135">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="adffd-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="adffd-136">修飾詞</span><span class="sxs-lookup"><span data-stu-id="adffd-136">Modifiers</span></span>](index.md)
- [<span data-ttu-id="adffd-137">鎖語句</span><span class="sxs-lookup"><span data-stu-id="adffd-137">lock statement</span></span>](lock-statement.md)
- <xref:System.Threading.Interlocked>
