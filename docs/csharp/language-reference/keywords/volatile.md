---
title: volatile (C# 參考)
ms.date: 10/24/2018
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: fd81c0c36cb88b971539e843e3e1f2096a73d40e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53152772"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="2f0b7-102">volatile (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="2f0b7-102">volatile (C# Reference)</span></span>

<span data-ttu-id="2f0b7-103">`volatile` 關鍵字指出某個欄位可能是由同時執行的多個執行緒所修改。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="2f0b7-104">編譯器、執行階段系統，甚至硬體都有可能基於效能因素，而重新排列對記憶體位置的讀取和寫入。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-104">The compiler, the runtime system, and even hardware may rearrange reads and writes to memory locations for performance reasons.</span></span> <span data-ttu-id="2f0b7-105">宣告為 `volatile` 的欄位不受限於這些最佳化考量。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-105">Fields that are declared `volatile` are not subject to these optimizations.</span></span> <span data-ttu-id="2f0b7-106">加入 `volatile` 修飾詞可確保所有的執行緒都會依執行寫入的順序，觀察任何其他執行緒所執行的暫時性寫入。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-106">Adding the `volatile` modifier ensures that all threads will observe volatile writes performed by any other thread in the order in which they were performed.</span></span> <span data-ttu-id="2f0b7-107">不保證 volatile 寫入的單一總排序如所有執行緒的執行中所示。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-107">There is no guarantee of a single total ordering of volatile writes as seen from all threads of execution.</span></span>
  
<span data-ttu-id="2f0b7-108">`volatile` 關鍵字可以套用至下列類型的欄位：</span><span class="sxs-lookup"><span data-stu-id="2f0b7-108">The `volatile` keyword can be applied to fields of these types:</span></span>  
  
- <span data-ttu-id="2f0b7-109">參考型別。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-109">Reference types.</span></span>  
- <span data-ttu-id="2f0b7-110">指標類型 (在不安全的內容中)。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-110">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="2f0b7-111">請注意，雖然指標本身可為 volatile，但它所指向的物件不得為 volatile。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-111">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="2f0b7-112">換句話說，您無法將指標宣告為 volatile。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-112">In other words, you cannot declare a "pointer to volatile."</span></span>  
- <span data-ttu-id="2f0b7-113">簡單型別，例如 `sbyte`、`byte`、`short`、`ushort`、`int`、`uint`、`char`、`float` 與 `bool`。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-113">Simple types such as `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `char`, `float`, and `bool`.</span></span>  
- <span data-ttu-id="2f0b7-114">使用下列其中一個基底類型的 `enum` 型別：`byte`、`sbyte`、`short`、`ushort`、`int` 或 `uint`。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-114">An `enum` type with one of the following base types: `byte`, `sbyte`, `short`, `ushort`, `int`, or `uint`.</span></span>  
- <span data-ttu-id="2f0b7-115">已知為參考型別的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-115">Generic type parameters known to be reference types.</span></span>
- <span data-ttu-id="2f0b7-116"><xref:System.IntPtr> 和 <xref:System.UIntPtr>。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-116"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>  

<span data-ttu-id="2f0b7-117">其他型別，包括 `double` 與 `long`，不能標示為 `volatile`，因為對這些型別之欄位的讀取和寫入不保證是不可部分完成。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-117">Other types, including `double` and `long`, cannot be marked `volatile` because reads and writes to fields of those types cannot be guaranteed to be atomic.</span></span> <span data-ttu-id="2f0b7-118">若要保護對這些型別之欄位的多執行緒存取，請使用 <xref:System.Threading.Interlocked> 類別成員，或使用 [`lock` ](lock-statement.md) 陳述式來保護存取。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-118">To protect multi-threaded access to those types of fields, use the <xref:System.Threading.Interlocked> class members or protect access using the [`lock`](lock-statement.md) statement.</span></span>

<span data-ttu-id="2f0b7-119">`volatile` 關鍵字只能套用至 `class` 或 `struct` 的欄位。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-119">The `volatile` keyword can only be applied to fields of a `class` or `struct`.</span></span> <span data-ttu-id="2f0b7-120">區域變數不可以宣告為 `volatile`。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-120">Local variables cannot be declared `volatile`.</span></span>
  
## <a name="example"></a><span data-ttu-id="2f0b7-121">範例</span><span class="sxs-lookup"><span data-stu-id="2f0b7-121">Example</span></span>

<span data-ttu-id="2f0b7-122">下列範例示範如何將公用欄位變數宣告為 `volatile`。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-122">The following example shows how to declare a public field variable as `volatile`.</span></span>  
  
[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Declaration)]

<span data-ttu-id="2f0b7-123">下列範例示範如何建立和使用輔助或背景工作執行緒，以運用主執行緒的輔助或背景工作執行緒來執行平行處理。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-123">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="2f0b7-124">如需有關多執行緒的詳細資訊，請參閱 [Managed 執行緒處理](../../../standard/threading/index.md)。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-124">For more information about multithreading, see [Managed Threading](../../../standard/threading/index.md).</span></span>
  
[!code-csharp[declareVolatile](~/samples/snippets/csharp/language-reference/keywords/volatile/Program.cs#Volatile)]

<span data-ttu-id="2f0b7-125">將 `volatile` 修飾詞新增到 `_shouldStop` 的宣告之後，您將會一律取得相同的結果 (類似上述程式碼顯示的摘要)。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-125">With the `volatile` modifier added to the declaration of `_shouldStop` in place, you'll always get the same results (similar to the excerpt shown in the preceding code).</span></span> <span data-ttu-id="2f0b7-126">不過，如果 `_shouldStop` 成員上沒有修飾詞，則行為是無法預測的。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-126">However, without that modifier on the `_shouldStop` member, the behavior is unpredictable.</span></span> <span data-ttu-id="2f0b7-127">`DoWork` 方法可能會將成員存取最佳化，導致讀取過時的資料。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-127">The `DoWork` method may optimize the member access, resulting in reading stale data.</span></span> <span data-ttu-id="2f0b7-128">由於多執行緒程式設計的特性，過時讀取的數目是無法預測的。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-128">Because of the nature of multi-threaded programming, the number of stale reads is unpredictable.</span></span> <span data-ttu-id="2f0b7-129">程式不同次的執行會產生不同的結果。</span><span class="sxs-lookup"><span data-stu-id="2f0b7-129">Different runs of the program will produce somewhat different results.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="2f0b7-130">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="2f0b7-130">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="2f0b7-131">請參閱</span><span class="sxs-lookup"><span data-stu-id="2f0b7-131">See Also</span></span>

- [<span data-ttu-id="2f0b7-132">C# 語言規格：volatile 關鍵字</span><span class="sxs-lookup"><span data-stu-id="2f0b7-132">C# language specification: volatile keyword</span></span>](../../../../_csharplang/spec/classes.md#volatile-fields)
- [<span data-ttu-id="2f0b7-133">C# 參考</span><span class="sxs-lookup"><span data-stu-id="2f0b7-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2f0b7-134">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="2f0b7-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2f0b7-135">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="2f0b7-135">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2f0b7-136">修飾詞</span><span class="sxs-lookup"><span data-stu-id="2f0b7-136">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="2f0b7-137">lock 陳述式</span><span class="sxs-lookup"><span data-stu-id="2f0b7-137">lock statement</span></span>](lock-statement.md)
- <span data-ttu-id="2f0b7-138"><xref:System.Threading.Interlocked> 類別</span><span class="sxs-lookup"><span data-stu-id="2f0b7-138"><xref:System.Threading.Interlocked> class</span></span>
