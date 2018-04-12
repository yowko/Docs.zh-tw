---
title: 傳遞陣列當做引數 (C# 程式設計手冊)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f152173b747a171052ab99f261ed91ced9465fdc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="cb551-102">傳遞陣列當做引數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="cb551-102">Passing Arrays as Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="cb551-103">陣列可以作為引數傳遞至方法參數。</span><span class="sxs-lookup"><span data-stu-id="cb551-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="cb551-104">因為陣列是參考型別，所以方法可以變更項目的值。</span><span class="sxs-lookup"><span data-stu-id="cb551-104">Because arrays are reference types, the method can change the value of the elements.</span></span>  
  
## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="cb551-105">傳遞一維陣列作為引數</span><span class="sxs-lookup"><span data-stu-id="cb551-105">Passing Single-Dimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="cb551-106">您可以將初始化的一維陣列傳遞至方法。</span><span class="sxs-lookup"><span data-stu-id="cb551-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="cb551-107">例如，下列陳述式會將陣列傳送至列印方法。</span><span class="sxs-lookup"><span data-stu-id="cb551-107">For example, the following statement sends an array to a print method.</span></span>  
  
 [!code-csharp[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]  
  
 <span data-ttu-id="cb551-108">下列程式碼顯示列印方法的部分實作。</span><span class="sxs-lookup"><span data-stu-id="cb551-108">The following code shows a partial implementation of the print method.</span></span>  
  
 [!code-csharp[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]  
  
 <span data-ttu-id="cb551-109">您可以在一個步驟中初始化並傳遞新的陣列，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="cb551-109">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 [!code-csharp[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="cb551-110">範例</span><span class="sxs-lookup"><span data-stu-id="cb551-110">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="cb551-111">描述</span><span class="sxs-lookup"><span data-stu-id="cb551-111">Description</span></span>  
 <span data-ttu-id="cb551-112">在下列範例中，字串的陣列會初始化，並作為引數傳遞至字串的 `PrintArray` 方法。</span><span class="sxs-lookup"><span data-stu-id="cb551-112">In the following example, an array of strings is initialized and passed as an argument to a `PrintArray` method for strings.</span></span> <span data-ttu-id="cb551-113">此方法會顯示陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="cb551-113">The method displays the elements of the array.</span></span> <span data-ttu-id="cb551-114">接著，會呼叫 `ChangeArray` 和`ChangeArrayElement` 方法，以顯示透過值傳送陣列引數不會阻止變更陣列元素。</span><span class="sxs-lookup"><span data-stu-id="cb551-114">Next, methods `ChangeArray` and `ChangeArrayElement` are called to demonstrate that sending an array argument by value does not prevent changes to the array elements.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cb551-115">程式碼</span><span class="sxs-lookup"><span data-stu-id="cb551-115">Code</span></span>  
 [!code-csharp[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]  
  
## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="cb551-116">傳遞多維陣列作為引數</span><span class="sxs-lookup"><span data-stu-id="cb551-116">Passing Multidimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="cb551-117">將初始化的多維陣列傳遞至方法所使用的方式，與傳遞一維陣列的方式相同。</span><span class="sxs-lookup"><span data-stu-id="cb551-117">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]  
  
 <span data-ttu-id="cb551-118">下列程式碼顯示可接受二維陣列作為其引數之列印方法的部分宣告。</span><span class="sxs-lookup"><span data-stu-id="cb551-118">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>  
  
 [!code-csharp[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]  
  
 <span data-ttu-id="cb551-119">您可以在一個步驟中初始化並傳遞新的陣列，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="cb551-119">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]  
  
## <a name="example"></a><span data-ttu-id="cb551-120">範例</span><span class="sxs-lookup"><span data-stu-id="cb551-120">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="cb551-121">描述</span><span class="sxs-lookup"><span data-stu-id="cb551-121">Description</span></span>  
 <span data-ttu-id="cb551-122">在下列範例中，整數的二維陣列會初始化並傳遞至 `Print2DArray` 方法。</span><span class="sxs-lookup"><span data-stu-id="cb551-122">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="cb551-123">此方法會顯示陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="cb551-123">The method displays the elements of the array.</span></span>  
  
### <a name="code"></a><span data-ttu-id="cb551-124">程式碼</span><span class="sxs-lookup"><span data-stu-id="cb551-124">Code</span></span>  
 [!code-csharp[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="cb551-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb551-125">See Also</span></span>  
 [<span data-ttu-id="cb551-126">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="cb551-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cb551-127">陣列</span><span class="sxs-lookup"><span data-stu-id="cb551-127">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="cb551-128">一維陣列</span><span class="sxs-lookup"><span data-stu-id="cb551-128">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="cb551-129">多維陣列</span><span class="sxs-lookup"><span data-stu-id="cb551-129">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="cb551-130">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="cb551-130">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
