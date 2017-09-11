---
title: "陣列 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
caps.latest.revision: 33
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
ms.openlocfilehash: 1035caae15b64d1311305cfe4c1f1a74c80ed19a
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="8ec8c-102">陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="8ec8c-102">Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="8ec8c-103">您可以在陣列資料結構中儲存相同類型的多個變數。</span><span class="sxs-lookup"><span data-stu-id="8ec8c-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="8ec8c-104">您可以指定陣列元素的類型來宣告陣列。</span><span class="sxs-lookup"><span data-stu-id="8ec8c-104">You declare an array by specifying the type of its elements.</span></span>  
  
 `type[] arrayName;`  
  
 <span data-ttu-id="8ec8c-105">下列範例會建立一維陣列、多維陣列和不規則陣列︰</span><span class="sxs-lookup"><span data-stu-id="8ec8c-105">The following examples create single-dimensional, multidimensional, and jagged arrays:</span></span>  
  
 <span data-ttu-id="8ec8c-106">[!code-cs[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="8ec8c-106">[!code-cs[csProgGuideArrays#1](../../../csharp/programming-guide/arrays/codesnippet/CSharp/index_1.cs)]</span></span>  
  
## <a name="array-overview"></a><span data-ttu-id="8ec8c-107">陣列概觀</span><span class="sxs-lookup"><span data-stu-id="8ec8c-107">Array Overview</span></span>  
 <span data-ttu-id="8ec8c-108">陣列具有下列屬性︰</span><span class="sxs-lookup"><span data-stu-id="8ec8c-108">An array has the following properties:</span></span>  
  
-   <span data-ttu-id="8ec8c-109">陣列可以是[一維](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)、[多維](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)或[不規則](../../../csharp/programming-guide/arrays/jagged-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="8ec8c-109">An array can be [Single-Dimensional](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [Multidimensional](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) or [Jagged](../../../csharp/programming-guide/arrays/jagged-arrays.md).</span></span>  
  
-   <span data-ttu-id="8ec8c-110">當陣列執行個體建立時，也會建立維度的數目和每個維度的長度。</span><span class="sxs-lookup"><span data-stu-id="8ec8c-110">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="8ec8c-111">在執行個體的存留期期間，這些值無法變更。</span><span class="sxs-lookup"><span data-stu-id="8ec8c-111">These values can't be changed during the lifetime of the instance.</span></span>  
  
-   <span data-ttu-id="8ec8c-112">數值陣列元素的預設值設定為零，且參考元素會設定為 null。</span><span class="sxs-lookup"><span data-stu-id="8ec8c-112">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>  
  
-   <span data-ttu-id="8ec8c-113">不規則陣列為陣列的陣列，因此其元素為參考類型，且會初始化為 `null`。</span><span class="sxs-lookup"><span data-stu-id="8ec8c-113">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
-   <span data-ttu-id="8ec8c-114">陣列為以零為基底索引：具有 `n` 個元素的陣列，會從 `0` 到 `n-1` 編製索引。</span><span class="sxs-lookup"><span data-stu-id="8ec8c-114">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>  
  
-   <span data-ttu-id="8ec8c-115">陣列元素可以是任何類型，包含陣列類型。</span><span class="sxs-lookup"><span data-stu-id="8ec8c-115">Array elements can be of any type, including an array type.</span></span>  
  
-   <span data-ttu-id="8ec8c-116">陣列類型是衍生自抽象基底類型 <xref:System.Array> 的[參考類型](../../../csharp/language-reference/keywords/reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="8ec8c-116">Array types are [reference types](../../../csharp/language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="8ec8c-117">由於這個類型會實作 <xref:System.Collections.IEnumerable> 和 <xref:System.Collections.Generic.IEnumerable%601>，您可以在所有以 C# 撰寫的陣列上使用 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 反覆項目。</span><span class="sxs-lookup"><span data-stu-id="8ec8c-117">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../../csharp/language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8ec8c-118">相關章節</span><span class="sxs-lookup"><span data-stu-id="8ec8c-118">Related Sections</span></span>  
  
-   [<span data-ttu-id="8ec8c-119">陣列作為物件</span><span class="sxs-lookup"><span data-stu-id="8ec8c-119">Arrays as Objects</span></span>](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [<span data-ttu-id="8ec8c-120">搭配陣列使用 foreach</span><span class="sxs-lookup"><span data-stu-id="8ec8c-120">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [<span data-ttu-id="8ec8c-121">傳遞陣列作為引數</span><span class="sxs-lookup"><span data-stu-id="8ec8c-121">Passing Arrays as Arguments</span></span>](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
-   [<span data-ttu-id="8ec8c-122">使用 ref 和 out 傳遞陣列</span><span class="sxs-lookup"><span data-stu-id="8ec8c-122">Passing Arrays Using ref and out</span></span>](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md)   
  
## <a name="c-language-specification"></a><span data-ttu-id="8ec8c-123">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="8ec8c-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8ec8c-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ec8c-124">See Also</span></span>  
 <span data-ttu-id="8ec8c-125">[C# 程式設計指南](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="8ec8c-125">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="8ec8c-126">[集合](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) </span><span class="sxs-lookup"><span data-stu-id="8ec8c-126">[Collections](http://msdn.microsoft.com/library/e76533a9-5033-4a0b-b003-9c2be60d185b) </span></span>  
 [<span data-ttu-id="8ec8c-127">Array 集合類型 (英文)</span><span class="sxs-lookup"><span data-stu-id="8ec8c-127">Array Collection Type</span></span>](http://msdn.microsoft.com/en-us/8a9964de-8941-47b1-a3cf-a01bc88db9e8)

