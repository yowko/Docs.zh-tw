---
title: "使用 ref 和 out 傳遞陣列 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: arrays [C#], passing using ref and out
ms.assetid: 6a2b261e-a1cc-49a6-b4f0-6cacae385a1e
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f2d4e613491b26e82523d230398af3ec34b4d0c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arrays-using-ref-and-out-c-programming-guide"></a><span data-ttu-id="e3628-102">使用 ref 和 out 傳遞陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="e3628-102">Passing Arrays Using ref and out (C# Programming Guide)</span></span>
<span data-ttu-id="e3628-103">如同所有的 [out](../../../csharp/language-reference/keywords/out.md) 參數，陣列類型的 `out` 參數必須先指派才能使用，也就是說，被呼叫端必須先指派這個參數。</span><span class="sxs-lookup"><span data-stu-id="e3628-103">Like all [out](../../../csharp/language-reference/keywords/out.md) parameters, an `out` parameter of an array type must be assigned before it is used; that is, it must be assigned by the callee.</span></span> <span data-ttu-id="e3628-104">例如: </span><span class="sxs-lookup"><span data-stu-id="e3628-104">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#39](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_1.cs)]  
  
 <span data-ttu-id="e3628-105">如同所有的 [ref](../../../csharp/language-reference/keywords/ref.md) 參數，陣列類型的 `ref` 參數也必須由呼叫端明確指派。</span><span class="sxs-lookup"><span data-stu-id="e3628-105">Like all [ref](../../../csharp/language-reference/keywords/ref.md) parameters, a `ref` parameter of an array type must be definitely assigned by the caller.</span></span> <span data-ttu-id="e3628-106">因此，被呼叫端就不需要明確指派該參數。</span><span class="sxs-lookup"><span data-stu-id="e3628-106">Therefore, there is no need to be definitely assigned by the callee.</span></span> <span data-ttu-id="e3628-107">呼叫的結果可能會修改陣列類型的 `ref` 參數。</span><span class="sxs-lookup"><span data-stu-id="e3628-107">A `ref` parameter of an array type may be altered as a result of the call.</span></span> <span data-ttu-id="e3628-108">例如，陣列可以擁有指派的 [null](../../../csharp/language-reference/keywords/null.md) 值，或是初始化為不同的陣列。</span><span class="sxs-lookup"><span data-stu-id="e3628-108">For example, the array can be assigned the [null](../../../csharp/language-reference/keywords/null.md) value or can be initialized to a different array.</span></span> <span data-ttu-id="e3628-109">例如: </span><span class="sxs-lookup"><span data-stu-id="e3628-109">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#40](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_2.cs)]  
  
 <span data-ttu-id="e3628-110">下列兩個範例將示範在陣列傳遞至方法時使用 `out` 和 `ref` 之間的差異。</span><span class="sxs-lookup"><span data-stu-id="e3628-110">The following two examples demonstrate the difference between `out` and `ref` when used in passing arrays to methods.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3628-111">範例</span><span class="sxs-lookup"><span data-stu-id="e3628-111">Example</span></span>  
 <span data-ttu-id="e3628-112">在這個範例中，`theArray` 陣列是在呼叫端 (`Main` 方法) 宣告，並且在 `FillArray` 方法中進行初始化。</span><span class="sxs-lookup"><span data-stu-id="e3628-112">In this example, the array `theArray` is declared in the caller (the `Main` method), and initialized in the `FillArray` method.</span></span> <span data-ttu-id="e3628-113">接著陣列元素會傳回呼叫端並顯示。</span><span class="sxs-lookup"><span data-stu-id="e3628-113">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 [!code-csharp[csProgGuideArrays#37](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="e3628-114">範例</span><span class="sxs-lookup"><span data-stu-id="e3628-114">Example</span></span>  
 <span data-ttu-id="e3628-115">在這個範例中，`theArray` 陣列是在呼叫端 (`Main` 方法) 進行初始化，並且會使用 `FillArray` 參數將該陣列傳遞至 `ref` 方法。</span><span class="sxs-lookup"><span data-stu-id="e3628-115">In this example, the array `theArray` is initialized in the caller (the `Main` method), and passed to the `FillArray` method by using the `ref` parameter.</span></span> <span data-ttu-id="e3628-116">有些陣列元素會在 `FillArray` 方法中更新。</span><span class="sxs-lookup"><span data-stu-id="e3628-116">Some of the array elements are updated in the `FillArray` method.</span></span> <span data-ttu-id="e3628-117">接著陣列元素會傳回呼叫端並顯示。</span><span class="sxs-lookup"><span data-stu-id="e3628-117">Then, the array elements are returned to the caller and displayed.</span></span>  
  
 [!code-csharp[csProgGuideArrays#38](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-using-ref-and-out_4.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e3628-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3628-118">See Also</span></span>  
 [<span data-ttu-id="e3628-119">ref</span><span class="sxs-lookup"><span data-stu-id="e3628-119">ref</span></span>](../../../csharp/language-reference/keywords/ref.md)  
 [<span data-ttu-id="e3628-120">out 參數修飾詞</span><span class="sxs-lookup"><span data-stu-id="e3628-120">out parameter modifier</span></span>](../../../csharp/language-reference/keywords/out-parameter-modifier.md)  
 [<span data-ttu-id="e3628-121">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e3628-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e3628-122">陣列</span><span class="sxs-lookup"><span data-stu-id="e3628-122">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="e3628-123">一維陣列</span><span class="sxs-lookup"><span data-stu-id="e3628-123">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="e3628-124">多維陣列</span><span class="sxs-lookup"><span data-stu-id="e3628-124">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="e3628-125">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="e3628-125">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
