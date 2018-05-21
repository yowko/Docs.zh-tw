---
title: 傳遞陣列當做引數 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: d863cdc33a8a1a844aabbea9ba5876614e6e8dba
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="02c07-102">傳遞陣列當做引數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="02c07-102">Passing Arrays as Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="02c07-103">陣列可以作為引數傳遞至方法參數。</span><span class="sxs-lookup"><span data-stu-id="02c07-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="02c07-104">因為陣列是參考型別，所以方法可以變更項目的值。</span><span class="sxs-lookup"><span data-stu-id="02c07-104">Because arrays are reference types, the method can change the value of the elements.</span></span>  
  
## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="02c07-105">傳遞一維陣列作為引數</span><span class="sxs-lookup"><span data-stu-id="02c07-105">Passing Single-Dimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="02c07-106">您可以將初始化的一維陣列傳遞至方法。</span><span class="sxs-lookup"><span data-stu-id="02c07-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="02c07-107">例如，下列陳述式會將陣列傳送至列印方法。</span><span class="sxs-lookup"><span data-stu-id="02c07-107">For example, the following statement sends an array to a print method.</span></span>  
  
 [!code-csharp[csProgGuideArrays#34](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_1.cs)]  
  
 <span data-ttu-id="02c07-108">下列程式碼顯示列印方法的部分實作。</span><span class="sxs-lookup"><span data-stu-id="02c07-108">The following code shows a partial implementation of the print method.</span></span>  
  
 [!code-csharp[csProgGuideArrays#33](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_2.cs)]  
  
 <span data-ttu-id="02c07-109">您可以在一個步驟中初始化並傳遞新的陣列，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="02c07-109">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 [!code-csharp[CsProgGuideArrays#35](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_3.cs)]  
  
## <a name="example"></a><span data-ttu-id="02c07-110">範例</span><span class="sxs-lookup"><span data-stu-id="02c07-110">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="02c07-111">描述</span><span class="sxs-lookup"><span data-stu-id="02c07-111">Description</span></span>  
 <span data-ttu-id="02c07-112">在下列範例中，字串的陣列會初始化，並作為引數傳遞至字串的 `PrintArray` 方法。</span><span class="sxs-lookup"><span data-stu-id="02c07-112">In the following example, an array of strings is initialized and passed as an argument to a `PrintArray` method for strings.</span></span> <span data-ttu-id="02c07-113">此方法會顯示陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="02c07-113">The method displays the elements of the array.</span></span> <span data-ttu-id="02c07-114">接著，會呼叫 `ChangeArray` 和`ChangeArrayElement` 方法，以顯示透過值傳送陣列引數不會阻止變更陣列元素。</span><span class="sxs-lookup"><span data-stu-id="02c07-114">Next, methods `ChangeArray` and `ChangeArrayElement` are called to demonstrate that sending an array argument by value does not prevent changes to the array elements.</span></span>  
  
### <a name="code"></a><span data-ttu-id="02c07-115">程式碼</span><span class="sxs-lookup"><span data-stu-id="02c07-115">Code</span></span>  
 [!code-csharp[csProgGuideArrays#30](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_4.cs)]  
  
## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="02c07-116">傳遞多維陣列作為引數</span><span class="sxs-lookup"><span data-stu-id="02c07-116">Passing Multidimensional Arrays As Arguments</span></span>  
 <span data-ttu-id="02c07-117">將初始化的多維陣列傳遞至方法所使用的方式，與傳遞一維陣列的方式相同。</span><span class="sxs-lookup"><span data-stu-id="02c07-117">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#41](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_5.cs)]  
  
 <span data-ttu-id="02c07-118">下列程式碼顯示可接受二維陣列作為其引數之列印方法的部分宣告。</span><span class="sxs-lookup"><span data-stu-id="02c07-118">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>  
  
 [!code-csharp[csProgGuideArrays#36](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_6.cs)]  
  
 <span data-ttu-id="02c07-119">您可以在一個步驟中初始化並傳遞新的陣列，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="02c07-119">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#32](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_7.cs)]  
  
## <a name="example"></a><span data-ttu-id="02c07-120">範例</span><span class="sxs-lookup"><span data-stu-id="02c07-120">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="02c07-121">描述</span><span class="sxs-lookup"><span data-stu-id="02c07-121">Description</span></span>  
 <span data-ttu-id="02c07-122">在下列範例中，整數的二維陣列會初始化並傳遞至 `Print2DArray` 方法。</span><span class="sxs-lookup"><span data-stu-id="02c07-122">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="02c07-123">此方法會顯示陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="02c07-123">The method displays the elements of the array.</span></span>  
  
### <a name="code"></a><span data-ttu-id="02c07-124">程式碼</span><span class="sxs-lookup"><span data-stu-id="02c07-124">Code</span></span>  
 [!code-csharp[csProgGuideArrays#31](../../../csharp/programming-guide/arrays/codesnippet/CSharp/passing-arrays-as-arguments_8.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="02c07-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="02c07-125">See Also</span></span>  
 [<span data-ttu-id="02c07-126">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="02c07-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="02c07-127">陣列</span><span class="sxs-lookup"><span data-stu-id="02c07-127">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="02c07-128">一維陣列</span><span class="sxs-lookup"><span data-stu-id="02c07-128">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="02c07-129">多維陣列</span><span class="sxs-lookup"><span data-stu-id="02c07-129">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="02c07-130">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="02c07-130">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
