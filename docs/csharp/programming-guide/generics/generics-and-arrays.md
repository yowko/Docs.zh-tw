---
title: 泛型和陣列 - C# 程式設計指南
description: '瞭解 c # 程式設計中的泛型和陣列。 請參閱程式碼範例，並檢視其他可用的資源。'
ms.date: 07/20/2015
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
ms.openlocfilehash: 808e9ddafea9806a74ccd105c8850e7b77b563be
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91151450"
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="b7d19-104">泛型和陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="b7d19-104">Generics and Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="b7d19-105">在 C# 2.0 及更新版本中，下限為零的一維陣列會自動實作 <xref:System.Collections.Generic.IList%601>。</span><span class="sxs-lookup"><span data-stu-id="b7d19-105">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="b7d19-106">這能讓您建立泛型方法，使用相同的程式碼逐一查看陣列和其他集合類型。</span><span class="sxs-lookup"><span data-stu-id="b7d19-106">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="b7d19-107">這項技術主要用於讀取集合的資料。</span><span class="sxs-lookup"><span data-stu-id="b7d19-107">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="b7d19-108"><xref:System.Collections.Generic.IList%601> 介面不能用來新增或移除陣列中的元素。</span><span class="sxs-lookup"><span data-stu-id="b7d19-108">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="b7d19-109">如果您嘗試呼叫 <xref:System.Collections.Generic.IList%601> 方法，例如此內容陣列上的 <xref:System.Collections.Generic.IList%601.RemoveAt%2A>，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="b7d19-109">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="b7d19-110">下列程式碼範例示範使用 <xref:System.Collections.Generic.IList%601> 輸入參數的單一泛型方法，如何逐一查看清單和陣列，本例中為整數陣列。</span><span class="sxs-lookup"><span data-stu-id="b7d19-110">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#35)]  
  
## <a name="see-also"></a><span data-ttu-id="b7d19-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7d19-111">See also</span></span>

- <xref:System.Collections.Generic>
- [<span data-ttu-id="b7d19-112">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="b7d19-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="b7d19-113">泛型</span><span class="sxs-lookup"><span data-stu-id="b7d19-113">Generics</span></span>](./index.md)
- [<span data-ttu-id="b7d19-114">陣列</span><span class="sxs-lookup"><span data-stu-id="b7d19-114">Arrays</span></span>](../arrays/index.md)
- [<span data-ttu-id="b7d19-115">泛型</span><span class="sxs-lookup"><span data-stu-id="b7d19-115">Generics</span></span>](../../../standard/generics/index.md)
