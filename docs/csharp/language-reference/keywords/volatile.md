---
title: "volatile (C# 參考)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- volatile_CSharpKeyword
- volatile
dev_langs:
- CSharp
helpviewer_keywords:
- volatile keyword [C#]
ms.assetid: 78089bc7-7b38-4cfd-9e49-87ac036af009
caps.latest.revision: 29
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
ms.openlocfilehash: c8f9fba15991197be885a973435089098a57db87
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="volatile-c-reference"></a><span data-ttu-id="8d77e-102">volatile (C# 參考)</span><span class="sxs-lookup"><span data-stu-id="8d77e-102">volatile (C# Reference)</span></span>
<span data-ttu-id="8d77e-103">`volatile` 關鍵字指出某個欄位可能是由同時執行的多個執行緒所修改。</span><span class="sxs-lookup"><span data-stu-id="8d77e-103">The `volatile` keyword indicates that a field might be modified by multiple threads that are executing at the same time.</span></span> <span data-ttu-id="8d77e-104">宣告 `volatile` 的欄位並不適用編譯器最佳化，因為編譯器最佳化是假設由單一執行緒進行存取。</span><span class="sxs-lookup"><span data-stu-id="8d77e-104">Fields that are declared `volatile` are not subject to compiler optimizations that assume access by a single thread.</span></span> <span data-ttu-id="8d77e-105">這樣可確保欄位中永遠出現最新的值。</span><span class="sxs-lookup"><span data-stu-id="8d77e-105">This ensures that the most up-to-date value is present in the field at all times.</span></span>  
  
 <span data-ttu-id="8d77e-106">針對多個執行緒存取的欄位，通常會使用 `volatile` 修飾詞，而不必使用 [lock](../../../csharp/language-reference/keywords/lock-statement.md) 陳述式來序列化存取。</span><span class="sxs-lookup"><span data-stu-id="8d77e-106">The `volatile` modifier is usually used for a field that is accessed by multiple threads without using the [lock](../../../csharp/language-reference/keywords/lock-statement.md) statement to serialize access.</span></span>  
  
 <span data-ttu-id="8d77e-107">`volatile` 關鍵字可以套用至下列類型的欄位：</span><span class="sxs-lookup"><span data-stu-id="8d77e-107">The `volatile` keyword can be applied to fields of these types:</span></span>  
  
-   <span data-ttu-id="8d77e-108">參考型別。</span><span class="sxs-lookup"><span data-stu-id="8d77e-108">Reference types.</span></span>  
  
-   <span data-ttu-id="8d77e-109">指標類型 (在不安全的內容中)。</span><span class="sxs-lookup"><span data-stu-id="8d77e-109">Pointer types (in an unsafe context).</span></span> <span data-ttu-id="8d77e-110">請注意，雖然指標本身可為 volatile，但它所指向的物件不得為 volatile。</span><span class="sxs-lookup"><span data-stu-id="8d77e-110">Note that although the pointer itself can be volatile, the object that it points to cannot.</span></span> <span data-ttu-id="8d77e-111">換句話說，您無法將指標宣告為 volatile。</span><span class="sxs-lookup"><span data-stu-id="8d77e-111">In other words, you cannot declare a "pointer to volatile."</span></span>  
  
-   <span data-ttu-id="8d77e-112">byte、byte、short、ushort、int、uint、char、float 和 bool 等類型。</span><span class="sxs-lookup"><span data-stu-id="8d77e-112">Types such as sbyte, byte, short, ushort, int, uint, char, float, and bool.</span></span>  
  
-   <span data-ttu-id="8d77e-113">具有 byte、sbyte、short、ushort、int 或 uint 基底類型之一的列舉類型。</span><span class="sxs-lookup"><span data-stu-id="8d77e-113">An enum type with one of the following base types: byte, sbyte, short, ushort, int, or uint.</span></span>  
  
-   <span data-ttu-id="8d77e-114">已知為參考型別的泛型型別參數。</span><span class="sxs-lookup"><span data-stu-id="8d77e-114">Generic type parameters known to be reference types.</span></span>  
  
-   <span data-ttu-id="8d77e-115"><xref:System.IntPtr> 和 <xref:System.UIntPtr>。</span><span class="sxs-lookup"><span data-stu-id="8d77e-115"><xref:System.IntPtr> and <xref:System.UIntPtr>.</span></span>  
  
 <span data-ttu-id="8d77e-116">volatile 關鍵字只能套用至類別或結構的欄位。</span><span class="sxs-lookup"><span data-stu-id="8d77e-116">The volatile keyword can only be applied to fields of a class or struct.</span></span> <span data-ttu-id="8d77e-117">區域變數不可以宣告為 `volatile`。</span><span class="sxs-lookup"><span data-stu-id="8d77e-117">Local variables cannot be declared `volatile`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d77e-118">範例</span><span class="sxs-lookup"><span data-stu-id="8d77e-118">Example</span></span>  
 <span data-ttu-id="8d77e-119">下列範例示範如何將公用欄位變數宣告為 `volatile`。</span><span class="sxs-lookup"><span data-stu-id="8d77e-119">The following example shows how to declare a public field variable as `volatile`.</span></span>  
  
 <span data-ttu-id="8d77e-120">[!code-cs[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="8d77e-120">[!code-cs[csrefKeywordsModifiers#24](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_1.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d77e-121">範例</span><span class="sxs-lookup"><span data-stu-id="8d77e-121">Example</span></span>  
 <span data-ttu-id="8d77e-122">下列範例示範如何建立和使用輔助或背景工作執行緒，以運用主執行緒的輔助或背景工作執行緒來執行平行處理。</span><span class="sxs-lookup"><span data-stu-id="8d77e-122">The following example demonstrates how an auxiliary or worker thread can be created and used to perform processing in parallel with that of the primary thread.</span></span> <span data-ttu-id="8d77e-123">如需多執行緒的背景資訊，請參閱 [Managed 執行緒處理](../../../standard/threading/index.md)和[執行緒](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)。</span><span class="sxs-lookup"><span data-stu-id="8d77e-123">For background information about multithreading, see [Threading](../../../standard/threading/index.md) and [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).</span></span>  
  
 <span data-ttu-id="8d77e-124">[!code-cs[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="8d77e-124">[!code-cs[csProgGuideThreading#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/volatile_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="8d77e-125">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="8d77e-125">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8d77e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d77e-126">See Also</span></span>  
 <span data-ttu-id="8d77e-127">[C# 參考](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="8d77e-127">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="8d77e-128">[C# 程式設計手冊](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="8d77e-128">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="8d77e-129">[C# 關鍵字](../../../csharp/language-reference/keywords/index.md) </span><span class="sxs-lookup"><span data-stu-id="8d77e-129">[C# Keywords](../../../csharp/language-reference/keywords/index.md) </span></span>  
 [<span data-ttu-id="8d77e-130">修飾詞</span><span class="sxs-lookup"><span data-stu-id="8d77e-130">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)

