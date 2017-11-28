---
title: "泛型和陣列 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], arrays
- arrays [C#], generics
ms.assetid: 7d956536-3851-41b5-94ad-3e7c0a5fe485
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 94b144075fac44ff749474a5bfa8e81aaadc0a0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="generics-and-arrays-c-programming-guide"></a><span data-ttu-id="bd735-102">泛型和陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="bd735-102">Generics and Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="bd735-103">在 C# 2.0 及更新版本中，下限為零的一維陣列會自動實作 <xref:System.Collections.Generic.IList%601>。</span><span class="sxs-lookup"><span data-stu-id="bd735-103">In C# 2.0 and later, single-dimensional arrays that have a lower bound of zero automatically implement <xref:System.Collections.Generic.IList%601>.</span></span> <span data-ttu-id="bd735-104">這能讓您建立泛型方法，使用相同的程式碼逐一查看陣列和其他集合類型。</span><span class="sxs-lookup"><span data-stu-id="bd735-104">This enables you to create generic methods that can use the same code to iterate through arrays and other collection types.</span></span> <span data-ttu-id="bd735-105">這項技術主要用於讀取集合的資料。</span><span class="sxs-lookup"><span data-stu-id="bd735-105">This technique is primarily useful for reading data in collections.</span></span> <span data-ttu-id="bd735-106"><xref:System.Collections.Generic.IList%601> 介面不能用來新增或移除陣列中的元素。</span><span class="sxs-lookup"><span data-stu-id="bd735-106">The <xref:System.Collections.Generic.IList%601> interface cannot be used to add or remove elements from an array.</span></span> <span data-ttu-id="bd735-107">如果您嘗試呼叫 <xref:System.Collections.Generic.IList%601> 方法，例如此內容陣列上的 <xref:System.Collections.Generic.IList%601.RemoveAt%2A>，會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="bd735-107">An exception will be thrown if you try to call an <xref:System.Collections.Generic.IList%601> method such as <xref:System.Collections.Generic.IList%601.RemoveAt%2A> on an array in this context.</span></span>  
  
 <span data-ttu-id="bd735-108">下列程式碼範例示範使用 <xref:System.Collections.Generic.IList%601> 輸入參數的單一泛型方法，如何逐一查看清單和陣列，本例中為整數陣列。</span><span class="sxs-lookup"><span data-stu-id="bd735-108">The following code example demonstrates how a single generic method that takes an <xref:System.Collections.Generic.IList%601> input parameter can iterate through both a list and an array, in this case an array of integers.</span></span>  
  
 [!code-csharp[csProgGuideGenerics#35](../../../csharp/programming-guide/generics/codesnippet/CSharp/generics-and-arrays_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="bd735-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd735-109">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="bd735-110">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="bd735-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bd735-111">泛型</span><span class="sxs-lookup"><span data-stu-id="bd735-111">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)  
 [<span data-ttu-id="bd735-112">陣列</span><span class="sxs-lookup"><span data-stu-id="bd735-112">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="bd735-113">泛型</span><span class="sxs-lookup"><span data-stu-id="bd735-113">Generics</span></span>](~/docs/standard/generics/index.md)
