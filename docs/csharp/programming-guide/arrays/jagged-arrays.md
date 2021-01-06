---
title: 不規則陣列 - C# 程式設計手冊
description: 'C # 中的不規則陣列是陣列，其元素是不同大小的陣列。 瞭解如何宣告、初始化及存取不規則陣列。'
ms.date: 12/18/2020
helpviewer_keywords:
- jagged arrays [C#]
- arrays [C#], jagged
ms.assetid: 537c65a6-0e0a-4a00-a2b8-086f38519c70
ms.openlocfilehash: 6d4fb939fb6594c7644a80eb688ea852ddf8a5c5
ms.sourcegitcommit: c3093e9d106d8ca87cc86eef1f2ae4ecfb392118
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2020
ms.locfileid: "97737277"
---
# <a name="jagged-arrays-c-programming-guide"></a><span data-ttu-id="5bd1f-104">不規則陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="5bd1f-104">Jagged Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="5bd1f-105">不規則陣列是其元素為數組的陣列，可能會有不同的大小。</span><span class="sxs-lookup"><span data-stu-id="5bd1f-105">A jagged array is an array whose elements are arrays, possibly of different sizes.</span></span> <span data-ttu-id="5bd1f-106">不規則陣列有時稱為「陣列的陣列」。</span><span class="sxs-lookup"><span data-stu-id="5bd1f-106">A jagged array is sometimes called an "array of arrays."</span></span> <span data-ttu-id="5bd1f-107">下列範例示範如何宣告、初始化和存取不規則陣列。</span><span class="sxs-lookup"><span data-stu-id="5bd1f-107">The following examples show how to declare, initialize, and access jagged arrays.</span></span>

 <span data-ttu-id="5bd1f-108">下列是具有三個項目的一維陣列宣告，且每個都是整數的一維陣列：</span><span class="sxs-lookup"><span data-stu-id="5bd1f-108">The following is a declaration of a single-dimensional array that has three elements, each of which is a single-dimensional array of integers:</span></span>

 [!code-csharp[csProgGuideArrays#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#19)]

 <span data-ttu-id="5bd1f-109">必須先初始化 `jaggedArray` 的項目，才能予以使用。</span><span class="sxs-lookup"><span data-stu-id="5bd1f-109">Before you can use `jaggedArray`, its elements must be initialized.</span></span> <span data-ttu-id="5bd1f-110">您可以初始化項目，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5bd1f-110">You can initialize the elements like this:</span></span>

 [!code-csharp[csProgGuideArrays#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#20)]

 <span data-ttu-id="5bd1f-111">每個項目都是整數的一維陣列。</span><span class="sxs-lookup"><span data-stu-id="5bd1f-111">Each of the elements is a single-dimensional array of integers.</span></span> <span data-ttu-id="5bd1f-112">第一個項目是 5 個整數的陣列、第二個是 4 個整數的陣列，而第三個是 2 個整數的陣列。</span><span class="sxs-lookup"><span data-stu-id="5bd1f-112">The first element is an array of 5 integers, the second is an array of 4 integers, and the third is an array of 2 integers.</span></span>

 <span data-ttu-id="5bd1f-113">也可以使用初始設定式將值填入陣列元素，在此情況下，您不需要陣列大小。</span><span class="sxs-lookup"><span data-stu-id="5bd1f-113">It is also possible to use initializers to fill the array elements with values, in which case you do not need the array size.</span></span> <span data-ttu-id="5bd1f-114">例如：</span><span class="sxs-lookup"><span data-stu-id="5bd1f-114">For example:</span></span>

 [!code-csharp[csProgGuideArrays#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#21)]

 <span data-ttu-id="5bd1f-115">您也可以在宣告時初始化陣列，如下所示：</span><span class="sxs-lookup"><span data-stu-id="5bd1f-115">You can also initialize the array upon declaration like this:</span></span>

 [!code-csharp[csProgGuideArrays#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#22)]

 <span data-ttu-id="5bd1f-116">您可以使用下列簡短格式。</span><span class="sxs-lookup"><span data-stu-id="5bd1f-116">You can use the following shorthand form.</span></span> <span data-ttu-id="5bd1f-117">請注意，您不能從項目初始化省略 `new` 運算子，因為沒有項目的預設初始化：</span><span class="sxs-lookup"><span data-stu-id="5bd1f-117">Notice that you cannot omit the `new` operator from the elements initialization because there is no default initialization for the elements:</span></span>

 [!code-csharp[csProgGuideArrays#23](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#23)]

 <span data-ttu-id="5bd1f-118">不規則陣列為陣列的陣列，因此其元素為參考類型，且會初始化為 `null`。</span><span class="sxs-lookup"><span data-stu-id="5bd1f-118">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>

 <span data-ttu-id="5bd1f-119">您可以存取個別陣列元素，例如下列範例：</span><span class="sxs-lookup"><span data-stu-id="5bd1f-119">You can access individual array elements like these examples:</span></span>

 [!code-csharp[csProgGuideArrays#24](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#24)]

 <span data-ttu-id="5bd1f-120">您可以混合不規則和多維陣列。</span><span class="sxs-lookup"><span data-stu-id="5bd1f-120">It's possible to mix jagged and multidimensional arrays.</span></span> <span data-ttu-id="5bd1f-121">以下是一維不規則陣列的宣告和初始化，而此陣列包含三個不同大小的二維陣列元素。</span><span class="sxs-lookup"><span data-stu-id="5bd1f-121">The following is a declaration and initialization of a single-dimensional jagged array that contains three two-dimensional array elements of different sizes.</span></span> <span data-ttu-id="5bd1f-122">如需詳細資訊，請參閱 [多維陣列](./multidimensional-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="5bd1f-122">For more information, see [Multidimensional Arrays](./multidimensional-arrays.md).</span></span>

 [!code-csharp[csProgGuideArrays#25](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#25)]

 <span data-ttu-id="5bd1f-123">如此範例所示，您可以存取個別項目，其中會顯示第一個陣列的項目 `[1,0]` 值 (值 `5`)：</span><span class="sxs-lookup"><span data-stu-id="5bd1f-123">You can access individual elements as shown in this example, which displays the value of the element `[1,0]` of the first array (value `5`):</span></span>

 [!code-csharp[csProgGuideArrays#26](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#26)]

 <span data-ttu-id="5bd1f-124">`Length` 方法會傳回不規則陣列中所含的陣列數目。</span><span class="sxs-lookup"><span data-stu-id="5bd1f-124">The method `Length` returns the number of arrays contained in the jagged array.</span></span> <span data-ttu-id="5bd1f-125">例如，假設您已經宣告先前的陣列，如下行所示：</span><span class="sxs-lookup"><span data-stu-id="5bd1f-125">For example, assuming you have declared the previous array, this line:</span></span>

 [!code-csharp[csProgGuideArrays#27](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#27)]

 <span data-ttu-id="5bd1f-126">會傳回值 3。</span><span class="sxs-lookup"><span data-stu-id="5bd1f-126">returns a value of 3.</span></span>

## <a name="example"></a><span data-ttu-id="5bd1f-127">範例</span><span class="sxs-lookup"><span data-stu-id="5bd1f-127">Example</span></span>

 <span data-ttu-id="5bd1f-128">此範例會建置其項目本身為陣列的陣列。</span><span class="sxs-lookup"><span data-stu-id="5bd1f-128">This example builds an array whose elements are themselves arrays.</span></span> <span data-ttu-id="5bd1f-129">每個陣列元素都會有不同的大小。</span><span class="sxs-lookup"><span data-stu-id="5bd1f-129">Each one of the array elements has a different size.</span></span>

 [!code-csharp[csProgGuideArrays#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#18)]

## <a name="see-also"></a><span data-ttu-id="5bd1f-130">請參閱</span><span class="sxs-lookup"><span data-stu-id="5bd1f-130">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="5bd1f-131">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5bd1f-131">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5bd1f-132">陣列</span><span class="sxs-lookup"><span data-stu-id="5bd1f-132">Arrays</span></span>](./index.md)
- [<span data-ttu-id="5bd1f-133">一維陣列</span><span class="sxs-lookup"><span data-stu-id="5bd1f-133">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="5bd1f-134">多維陣列</span><span class="sxs-lookup"><span data-stu-id="5bd1f-134">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
