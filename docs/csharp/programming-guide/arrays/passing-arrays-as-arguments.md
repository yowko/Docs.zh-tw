---
title: 傳遞陣列當做引數 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/05/2018
helpviewer_keywords:
- arrays [C#], passing as arguments
ms.assetid: f3a0971e-c87c-4a1f-8262-bc0a3b712772
ms.openlocfilehash: 6e11020491c36349f035abb333aa3396c246dd68
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245609"
---
# <a name="passing-arrays-as-arguments-c-programming-guide"></a><span data-ttu-id="d994b-102">傳遞陣列當做引數 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="d994b-102">Passing arrays as arguments (C# Programming Guide)</span></span>

<span data-ttu-id="d994b-103">陣列可以作為引數傳遞至方法參數。</span><span class="sxs-lookup"><span data-stu-id="d994b-103">Arrays can be passed as arguments to method parameters.</span></span> <span data-ttu-id="d994b-104">因為陣列是參考型別，所以方法可以變更項目的值。</span><span class="sxs-lookup"><span data-stu-id="d994b-104">Because arrays are reference types, the method can change the value of the elements.</span></span>

## <a name="passing-single-dimensional-arrays-as-arguments"></a><span data-ttu-id="d994b-105">傳遞一維陣列作為引數</span><span class="sxs-lookup"><span data-stu-id="d994b-105">Passing single-dimensional arrays as arguments</span></span>

<span data-ttu-id="d994b-106">您可以將初始化的一維陣列傳遞至方法。</span><span class="sxs-lookup"><span data-stu-id="d994b-106">You can pass an initialized single-dimensional array to a method.</span></span> <span data-ttu-id="d994b-107">例如，下列陳述式會將陣列傳送至列印方法。</span><span class="sxs-lookup"><span data-stu-id="d994b-107">For example, the following statement sends an array to a print method.</span></span>

[!code-csharp[csProgGuideArrays#34](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#34)]

<span data-ttu-id="d994b-108">下列程式碼顯示列印方法的部分實作。</span><span class="sxs-lookup"><span data-stu-id="d994b-108">The following code shows a partial implementation of the print method.</span></span>

[!code-csharp[csProgGuideArrays#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#33)]

<span data-ttu-id="d994b-109">您可以在一個步驟中初始化並傳遞新的陣列，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="d994b-109">You can initialize and pass a new array in one step, as is shown in the following example.</span></span>

[!code-csharp[CsProgGuideArrays#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#35)]

### <a name="example"></a><span data-ttu-id="d994b-110">範例</span><span class="sxs-lookup"><span data-stu-id="d994b-110">Example</span></span>

<span data-ttu-id="d994b-111">在下列範例中，字串的陣列會初始化，並作為引數傳遞至字串的 `DisplayArray` 方法。</span><span class="sxs-lookup"><span data-stu-id="d994b-111">In the following example, an array of strings is initialized and passed as an argument to a `DisplayArray` method for strings.</span></span> <span data-ttu-id="d994b-112">此方法會顯示陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="d994b-112">The method displays the elements of the array.</span></span> <span data-ttu-id="d994b-113">接下來，`ChangeArray` 方法會反轉陣列項目，然後 `ChangeArrayElements` 方法會修改陣列的前三個項目。</span><span class="sxs-lookup"><span data-stu-id="d994b-113">Next, the `ChangeArray` method reverses the array elements, and then the `ChangeArrayElements` method modifies the first three elements of the array.</span></span> <span data-ttu-id="d994b-114">每個方法傳回之後，`DisplayArray` 方法會顯示以傳值方式傳遞陣列不會防止變更陣列元素。</span><span class="sxs-lookup"><span data-stu-id="d994b-114">After each method returns, the `DisplayArray` method shows that passing an array by value doesn't prevent changes to the array elements.</span></span>

[!code-csharp[csProgGuideArrays#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/ArrayExample.cs)]

## <a name="passing-multidimensional-arrays-as-arguments"></a><span data-ttu-id="d994b-115">傳遞多維陣列作為引數</span><span class="sxs-lookup"><span data-stu-id="d994b-115">Passing multidimensional arrays as arguments</span></span>

<span data-ttu-id="d994b-116">將初始化的多維陣列傳遞至方法所使用的方式，與傳遞一維陣列的方式相同。</span><span class="sxs-lookup"><span data-stu-id="d994b-116">You pass an initialized multidimensional array to a method in the same way that you pass a one-dimensional array.</span></span>

[!code-csharp[csProgGuideArrays#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#41)]

<span data-ttu-id="d994b-117">下列程式碼顯示可接受二維陣列作為其引數之列印方法的部分宣告。</span><span class="sxs-lookup"><span data-stu-id="d994b-117">The following code shows a partial declaration of a print method that accepts a two-dimensional array as its argument.</span></span>

[!code-csharp[csProgGuideArrays#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#36)]

<span data-ttu-id="d994b-118">您可以在一個步驟中初始化並傳遞新的陣列，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="d994b-118">You can initialize and pass a new array in one step, as is shown in the following example:</span></span>

[!code-csharp[csProgGuideArrays#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#32)]

### <a name="example"></a><span data-ttu-id="d994b-119">範例</span><span class="sxs-lookup"><span data-stu-id="d994b-119">Example</span></span>

<span data-ttu-id="d994b-120">在下列範例中，整數的二維陣列會初始化並傳遞至 `Print2DArray` 方法。</span><span class="sxs-lookup"><span data-stu-id="d994b-120">In the following example, a two-dimensional array of integers is initialized and passed to the `Print2DArray` method.</span></span> <span data-ttu-id="d994b-121">此方法會顯示陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="d994b-121">The method displays the elements of the array.</span></span>

[!code-csharp[csProgGuideArrays#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#31)]

## <a name="see-also"></a><span data-ttu-id="d994b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d994b-122">See also</span></span>

- [<span data-ttu-id="d994b-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="d994b-123">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="d994b-124">陣列</span><span class="sxs-lookup"><span data-stu-id="d994b-124">Arrays</span></span>](index.md)  
- [<span data-ttu-id="d994b-125">一維陣列</span><span class="sxs-lookup"><span data-stu-id="d994b-125">Single-Dimensional Arrays</span></span>](single-dimensional-arrays.md)  
- [<span data-ttu-id="d994b-126">多維陣列</span><span class="sxs-lookup"><span data-stu-id="d994b-126">Multidimensional Arrays</span></span>](multidimensional-arrays.md)  
- [<span data-ttu-id="d994b-127">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="d994b-127">Jagged Arrays</span></span>](jagged-arrays.md)  