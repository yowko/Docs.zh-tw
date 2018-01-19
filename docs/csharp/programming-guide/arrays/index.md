---
title: "陣列 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
caps.latest.revision: "33"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8d395bcb179650fe29ab0918e7f91f3c8b6197b5
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2018
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="5dbc1-102">陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="5dbc1-102">Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="5dbc1-103">您可以在陣列資料結構中儲存相同類型的多個變數。</span><span class="sxs-lookup"><span data-stu-id="5dbc1-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="5dbc1-104">您可以指定陣列元素的類型來宣告陣列。</span><span class="sxs-lookup"><span data-stu-id="5dbc1-104">You declare an array by specifying the type of its elements.</span></span>  
  
 `type[] arrayName;`  
  
 <span data-ttu-id="5dbc1-105">下列範例會建立一維陣列、多維陣列和不規則陣列︰</span><span class="sxs-lookup"><span data-stu-id="5dbc1-105">The following examples create single-dimensional, multidimensional, and jagged arrays:</span></span>  
  
 [!code-csharp[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]  
  
## <a name="array-overview"></a><span data-ttu-id="5dbc1-106">陣列概觀</span><span class="sxs-lookup"><span data-stu-id="5dbc1-106">Array Overview</span></span>  
 <span data-ttu-id="5dbc1-107">陣列具有下列屬性︰</span><span class="sxs-lookup"><span data-stu-id="5dbc1-107">An array has the following properties:</span></span>  
  
-   <span data-ttu-id="5dbc1-108">陣列可以是[一維](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)、[多維](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)或[不規則](../../../csharp/programming-guide/arrays/jagged-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="5dbc1-108">An array can be [Single-Dimensional](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [Multidimensional](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) or [Jagged](../../../csharp/programming-guide/arrays/jagged-arrays.md).</span></span>  
  
-   <span data-ttu-id="5dbc1-109">當陣列執行個體建立時，也會建立維度的數目和每個維度的長度。</span><span class="sxs-lookup"><span data-stu-id="5dbc1-109">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="5dbc1-110">在執行個體的存留期期間，這些值無法變更。</span><span class="sxs-lookup"><span data-stu-id="5dbc1-110">These values can't be changed during the lifetime of the instance.</span></span>  
  
-   <span data-ttu-id="5dbc1-111">數值陣列元素的預設值設定為零，且參考元素會設定為 null。</span><span class="sxs-lookup"><span data-stu-id="5dbc1-111">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>  
  
-   <span data-ttu-id="5dbc1-112">不規則陣列為陣列的陣列，因此其元素為參考類型，且會初始化為 `null`。</span><span class="sxs-lookup"><span data-stu-id="5dbc1-112">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
-   <span data-ttu-id="5dbc1-113">陣列為以零為基底索引：具有 `n` 個元素的陣列，會從 `0` 到 `n-1` 編製索引。</span><span class="sxs-lookup"><span data-stu-id="5dbc1-113">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>  
  
-   <span data-ttu-id="5dbc1-114">陣列元素可以是任何類型，包含陣列類型。</span><span class="sxs-lookup"><span data-stu-id="5dbc1-114">Array elements can be of any type, including an array type.</span></span>  
  
-   <span data-ttu-id="5dbc1-115">陣列類型是衍生自抽象基底類型 <xref:System.Array> 的[參考類型](../../../csharp/language-reference/keywords/reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5dbc1-115">Array types are [reference types](../../../csharp/language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="5dbc1-116">由於這個類型會實作 <xref:System.Collections.IEnumerable> 和 <xref:System.Collections.Generic.IEnumerable%601>，您可以在所有以 C# 撰寫的陣列上使用 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 反覆項目。</span><span class="sxs-lookup"><span data-stu-id="5dbc1-116">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../../csharp/language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5dbc1-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="5dbc1-117">Related Sections</span></span>  
  
-   [<span data-ttu-id="5dbc1-118">陣列作為物件</span><span class="sxs-lookup"><span data-stu-id="5dbc1-118">Arrays as Objects</span></span>](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [<span data-ttu-id="5dbc1-119">搭配陣列使用 foreach</span><span class="sxs-lookup"><span data-stu-id="5dbc1-119">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [<span data-ttu-id="5dbc1-120">傳遞陣列作為引數</span><span class="sxs-lookup"><span data-stu-id="5dbc1-120">Passing Arrays as Arguments</span></span>](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
-   [<span data-ttu-id="5dbc1-121">使用 ref 和 out 傳遞陣列</span><span class="sxs-lookup"><span data-stu-id="5dbc1-121">Passing Arrays Using ref and out</span></span>](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)   
  
## <a name="c-language-specification"></a><span data-ttu-id="5dbc1-122">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="5dbc1-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5dbc1-123">請參閱</span><span class="sxs-lookup"><span data-stu-id="5dbc1-123">See Also</span></span>  
 [<span data-ttu-id="5dbc1-124">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5dbc1-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5dbc1-125">集合</span><span class="sxs-lookup"><span data-stu-id="5dbc1-125">Collections</span></span>](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b)  
 [<span data-ttu-id="5dbc1-126">Array 集合類型 (英文)</span><span class="sxs-lookup"><span data-stu-id="5dbc1-126">Array Collection Type</span></span>](http://msdn.microsoft.com/library/8a9964de-8941-47b1-a3cf-a01bc88db9e8)
