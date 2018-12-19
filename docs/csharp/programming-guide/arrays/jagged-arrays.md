---
title: 不規則陣列 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: f517a9a6d6e10f04df70729fb9e641c1f955f28a
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237853"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="87f26-102">不規則陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="87f26-102">Jagged Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="87f26-103">不規則陣列是一種陣列，其元素也是陣列。</span><span class="sxs-lookup"><span data-stu-id="87f26-103">A jagged array is an array whose elements are arrays.</span></span> <span data-ttu-id="87f26-104">不規則陣列的項目可以有不同的維度和大小。</span><span class="sxs-lookup"><span data-stu-id="87f26-104">The elements of a jagged array can be of different dimensions and sizes.</span></span> <span data-ttu-id="87f26-105">不規則陣列有時稱為「陣列的陣列」。</span><span class="sxs-lookup"><span data-stu-id="87f26-105">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="87f26-106">下列範例示範如何宣告、初始化和存取不規則陣列。</span><span class="sxs-lookup"><span data-stu-id="87f26-106">The following examples show how to declare, initialize, and access jagged arrays.</span></span>  
  
 <span data-ttu-id="87f26-107">下列是具有三個項目的一維陣列宣告，且每個都是整數的一維陣列：</span><span class="sxs-lookup"><span data-stu-id="87f26-107">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>  
  
 [!code-csharp[csProgGuideArrays#19](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_1.cs)]  
  
 <span data-ttu-id="87f26-108">必須先初始化 `jaggedArray` 的項目，才能予以使用。</span><span class="sxs-lookup"><span data-stu-id="87f26-108">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="87f26-109">您可以初始化項目，如下所示：</span><span class="sxs-lookup"><span data-stu-id="87f26-109">You can initialize the elements like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#20](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_2.cs)]  
  
 <span data-ttu-id="87f26-110">每個項目都是整數的一維陣列。</span><span class="sxs-lookup"><span data-stu-id="87f26-110">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="87f26-111">第一個項目是 5 個整數的陣列、第二個是 4 個整數的陣列，而第三個是 2 個整數的陣列。</span><span class="sxs-lookup"><span data-stu-id="87f26-111">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>  
  
 <span data-ttu-id="87f26-112">也可以使用初始設定式將值填入陣列元素，在此情況下，您不需要陣列大小。</span><span class="sxs-lookup"><span data-stu-id="87f26-112">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="87f26-113">例如：</span><span class="sxs-lookup"><span data-stu-id="87f26-113">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#21](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_3.cs)]  
  
 <span data-ttu-id="87f26-114">您也可以在宣告時初始化陣列，如下所示：</span><span class="sxs-lookup"><span data-stu-id="87f26-114">You can also initialize the array upon declaration like this:</span></span>  
  
 [!code-csharp[csProgGuideArrays#22](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_4.cs)]  
  
 <span data-ttu-id="87f26-115">您可以使用下列簡短格式。</span><span class="sxs-lookup"><span data-stu-id="87f26-115">You can use the following shorthand form.</span></span> <span data-ttu-id="87f26-116">請注意，您不能從項目初始化省略 `new` 運算子，因為沒有項目的預設初始化：</span><span class="sxs-lookup"><span data-stu-id="87f26-116">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>  
  
 [!code-csharp[csProgGuideArrays#23](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_5.cs)]  
  
 <span data-ttu-id="87f26-117">不規則陣列為陣列的陣列，因此其元素為參考類型，且會初始化為 `null`。</span><span class="sxs-lookup"><span data-stu-id="87f26-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
 <span data-ttu-id="87f26-118">您可以存取個別陣列元素，例如下列範例：</span><span class="sxs-lookup"><span data-stu-id="87f26-118">You can access individual array elements like these examples:</span></span>  
  
 [!code-csharp[csProgGuideArrays#24](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_6.cs)]  
  
 <span data-ttu-id="87f26-119">可以混合使用不規則陣列與多維陣列。</span><span class="sxs-lookup"><span data-stu-id="87f26-119">It is possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="87f26-120">以下是一維不規則陣列的宣告和初始化，而此陣列包含三個不同大小的二維陣列元素。</span><span class="sxs-lookup"><span data-stu-id="87f26-120">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="87f26-121">如需二維陣列的詳細資訊，請參閱[多維陣列](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="87f26-121">For more information about two-dimensional arrays, see [Multidimensional Arrays](../../../csharp/programming-guide/arrays/multidimensional-arrays.md).</span></span>  
  
 [!code-csharp[csProgGuideArrays#25](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_7.cs)]  
  
 <span data-ttu-id="87f26-122">如此範例所示，您可以存取個別項目，其中會顯示第一個陣列的項目 `[1,0]` 值 (值 `5`)：</span><span class="sxs-lookup"><span data-stu-id="87f26-122">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>  
  
 [!code-csharp[csProgGuideArrays#26](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_8.cs)]  
  
 <span data-ttu-id="87f26-123">`Length` 方法會傳回不規則陣列中所含的陣列數目。</span><span class="sxs-lookup"><span data-stu-id="87f26-123">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="87f26-124">例如，假設您已經宣告先前的陣列，如下行所示：</span><span class="sxs-lookup"><span data-stu-id="87f26-124">For example, assuming you have declared the previous array, this line:</span></span>  
  
 [!code-csharp[csProgGuideArrays#27](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_9.cs)]  
  
 <span data-ttu-id="87f26-125">會傳回值 3。</span><span class="sxs-lookup"><span data-stu-id="87f26-125">returns a value of 3.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87f26-126">範例</span><span class="sxs-lookup"><span data-stu-id="87f26-126">Example</span></span>

 <span data-ttu-id="87f26-127">此範例會建置其項目本身為陣列的陣列。</span><span class="sxs-lookup"><span data-stu-id="87f26-127">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="87f26-128">每個陣列元素都會有不同的大小。</span><span class="sxs-lookup"><span data-stu-id="87f26-128">Each one of the array elements has a different size.</span></span>  
  
 [!code-csharp[csProgGuideArrays#18](../../../csharp/programming-guide/arrays/codesnippet/CSharp/jagged-arrays_10.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="87f26-129">請參閱</span><span class="sxs-lookup"><span data-stu-id="87f26-129">See Also</span></span>

- <xref:System.Array>  
- [<span data-ttu-id="87f26-130">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="87f26-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="87f26-131">陣列</span><span class="sxs-lookup"><span data-stu-id="87f26-131">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="87f26-132">一維陣列</span><span class="sxs-lookup"><span data-stu-id="87f26-132">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
- [<span data-ttu-id="87f26-133">多維陣列</span><span class="sxs-lookup"><span data-stu-id="87f26-133">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
