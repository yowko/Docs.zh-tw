---
title: volatile (C# 參考)
ms.date: 07/20/2015
f1_keywords:
- volatile_CSharpKeyword
- volatile
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
ms.openlocfilehash: 64bd5ce7d7dfe3265c3c645467493ab7d8792172
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37936874"
---
# <a name="volatile-c-reference"></a><span data-ttu-id="ba5c0-102">volatile (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="ba5c0-102">volatile (C# Reference)</span></span>
<span data-ttu-id="ba5c0-103">`volatile` 關鍵字指出某個欄位可能是由同時執行的多個執行緒所修改。</span><span class="sxs-lookup"><span data-stu-id="ba5c0-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="ba5c0-104">宣告 `volatile` 的欄位並不適用編譯器最佳化，因為編譯器最佳化是假設由單一執行緒進行存取。</span><span class="sxs-lookup"><span data-stu-id="ba5c0-104">Fields that are declared `volatile` are not subject to compiler optimizations that assume access by a single thread.</span></span> <span data-ttu-id="ba5c0-105">這些限制可確保所有的執行緒將會觀察任何其他執行緒執行的 volatile 寫入會按照其執行的順序進行。</span><span class="sxs-lookup"><span data-stu-id="ba5c0-105">These restrictions ensure that all threads will observe volatile writes performed by any other thread in the order in which they were performed.</span></span> <span data-ttu-id="ba5c0-106">不保證 volatile 寫入的單一總排序如所有執行緒的執行中所示。</span><span class="sxs-lookup"><span data-stu-id="ba5c0-106">There is no guarantee of a single total ordering of volatile writes as seen from all threads of execution.</span></span>  
  
 <span data-ttu-id="ba5c0-107">針對多個執行緒存取的欄位，通常會使用 `volatile` 修飾詞，而不必使用 [lock](../../../csharp/language-reference/keywords/lock-statement.md) 陳述式來序列化存取。</span><span class="sxs-lookup"><span data-stu-id="ba5c0-107">The `volatile` modifier is usually used for a field that is accessed by multiple threads without using the [lock](../../../csharp/language-reference/keywords/lock-statement.md) statement to serialize access.</span></span>  
  
 <span data-ttu-id="ba5c0-108">`volatile` 關鍵字可以套用至下列類型的欄位：</span><span class="sxs-lookup"><span data-stu-id="ba5c0-108">The `volatile` keyword can be applied to fields of these types:</span></span>  
  
-   <span data-ttu-id="ba5c0-109">參考型別。</span><span class="sxs-lookup"><span data-stu-id="ba5c0-109">Reference types.</span></span>  
  
-   <span data-ttu-id="ba5c0-110">指標類型 (在不安全的內容中)。</span><span class="sxs-lookup"><span data-stu-id="ba5c0-110">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="ba5c0-111">請注意，雖然指標本身可為 volatile，但它所指向的物件不得為 volatile。</span><span class="sxs-lookup"><span data-stu-id="ba5c0-111">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="ba5c0-112">換句話說，您無法將指標宣告為 volatile。</span><span class="sxs-lookup"><span data-stu-id="ba5c0-112">In other words, you cannot declare a "pointer to volatile."</span></span>  
  
-   <span data-ttu-id="ba5c0-113">byte、byte、short、ushort、int、uint、char、float 和 bool 等類型。</span><span class="sxs-lookup"><span data-stu-id="ba5c0-113">Types such as sbyte, byte, short, ushort, int, uint, char, float, and bool.</span></span>  
  
-   <span data-ttu-id="ba5c0-114">具有 byte、sbyte、short、ushort、int 或 uint 基底類型之一的列舉類型。</span><span class="sxs-lookup"><span data-stu-id="ba5c0-114">An enum type with one of the following base types: byte, sbyte, short, ushort, int, or uint.</span></span>  
  
-   <span data-ttu-id="ba5c0-115">已知為參考型別的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="ba5c0-115">Generic type parameters known to be reference types.</span></span>  
  
-   <span data-ttu-id="ba5c0-116"><xref:System.IntPtr> 和 <xref:System.UIntPtr>。</span><span class="sxs-lookup"><span data-stu-id="ba5c0-116"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>  
  
 <span data-ttu-id="ba5c0-117">volatile 關鍵字只能套用至類別或結構的欄位。</span><span class="sxs-lookup"><span data-stu-id="ba5c0-117">The volatile keyword can only be applied to fields of a class or struct.</span></span> <span data-ttu-id="ba5c0-118">區域變數不可以宣告為 `volatile`。</span><span class="sxs-lookup"><span data-stu-id="ba5c0-118">Local variables cannot be declared `volatile`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ba5c0-119">範例</span><span class="sxs-lookup"><span data-stu-id="ba5c0-119">Example</span></span>  
 <span data-ttu-id="ba5c0-120">下列範例示範如何將公用欄位變數宣告為 `volatile`。</span><span class="sxs-lookup"><span data-stu-id="ba5c0-120">The following example shows how to declare a public field variable as `volatile`.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="ba5c0-121">範例</span><span class="sxs-lookup"><span data-stu-id="ba5c0-121">Example</span></span>  
 <span data-ttu-id="ba5c0-122">下列範例示範如何建立和使用輔助或背景工作執行緒，以運用主執行緒的輔助或背景工作執行緒來執行平行處理。</span><span class="sxs-lookup"><span data-stu-id="ba5c0-122">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="ba5c0-123">如需多執行緒的背景資訊，請參閱 [Managed 執行緒處理](../../../standard/threading/index.md)和[執行緒處理 (C#)](../../programming-guide/concepts/threading/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ba5c0-123">For background information about multithreading, see [Managed Threading](../../../standard/threading/index.md) and [Threading (C#)](../../programming-guide/concepts/threading/index.md).</span></span>  
  
 [!code-csharp[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="ba5c0-124">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="ba5c0-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ba5c0-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="ba5c0-125">See Also</span></span>  
 [<span data-ttu-id="ba5c0-126">C# 參考</span><span class="sxs-lookup"><span data-stu-id="ba5c0-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ba5c0-127">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="ba5c0-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ba5c0-128">C# 關鍵字</span><span class="sxs-lookup"><span data-stu-id="ba5c0-128">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="ba5c0-129">修飾詞</span><span class="sxs-lookup"><span data-stu-id="ba5c0-129">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
