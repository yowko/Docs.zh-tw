---
title: 陣列 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 1b1a3d2e61507a497349deeb857e4333356f66a5
ms.sourcegitcommit: 5dcfeb59179e81071f54840d4902cbe00b184294
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2019
ms.locfileid: "54857797"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="47786-102">陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="47786-102">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="47786-103">您可以在陣列資料結構中儲存相同類型的多個變數。</span><span class="sxs-lookup"><span data-stu-id="47786-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="47786-104">您可以指定陣列元素的類型來宣告陣列。</span><span class="sxs-lookup"><span data-stu-id="47786-104">You declare an array by specifying the type of its elements.</span></span>  
  
 `type[] arrayName;`  
  
 <span data-ttu-id="47786-105">下列範例會建立一維陣列、多維陣列和不規則陣列︰</span><span class="sxs-lookup"><span data-stu-id="47786-105">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>  
  
 [!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]  
  
## <a name="array-overview"></a><span data-ttu-id="47786-106">陣列概觀</span><span class="sxs-lookup"><span data-stu-id="47786-106">Array Overview</span></span>

 <span data-ttu-id="47786-107">陣列具有下列屬性︰</span><span class="sxs-lookup"><span data-stu-id="47786-107">An array has the following properties:</span></span>  
  
-   <span data-ttu-id="47786-108">陣列可以是[一維](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)、[多維](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)或[不規則](../../../csharp/programming-guide/arrays/jagged-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="47786-108">An array can be [Single-Dimensional](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md), [Multidimensional](../../../csharp/programming-guide/arrays/multidimensional-arrays.md) or [Jagged](../../../csharp/programming-guide/arrays/jagged-arrays.md).</span></span>  
  
-   <span data-ttu-id="47786-109">當陣列執行個體建立時，也會建立維度的數目和每個維度的長度。</span><span class="sxs-lookup"><span data-stu-id="47786-109">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="47786-110">在執行個體的存留期期間，這些值無法變更。</span><span class="sxs-lookup"><span data-stu-id="47786-110">These values can't be changed during the lifetime of the instance.</span></span>  
  
-   <span data-ttu-id="47786-111">數值陣列元素的預設值設定為零，且參考元素會設定為 null。</span><span class="sxs-lookup"><span data-stu-id="47786-111">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>  
  
-   <span data-ttu-id="47786-112">不規則陣列為陣列的陣列，因此其元素為參考類型，且會初始化為 `null`。</span><span class="sxs-lookup"><span data-stu-id="47786-112">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>  
  
-   <span data-ttu-id="47786-113">陣列為以零為基底索引：具有 `n` 個元素的陣列，會從 `0` 到 `n-1` 編製索引。</span><span class="sxs-lookup"><span data-stu-id="47786-113">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>  
  
-   <span data-ttu-id="47786-114">陣列元素可以是任何類型，包含陣列類型。</span><span class="sxs-lookup"><span data-stu-id="47786-114">Array elements can be of any type, including an array type.</span></span>  
  
-   <span data-ttu-id="47786-115">陣列類型是衍生自抽象基底類型 <xref:System.Array> 的[參考類型](../../../csharp/language-reference/keywords/reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="47786-115">Array types are [reference types](../../../csharp/language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="47786-116">由於這個類型會實作 <xref:System.Collections.IEnumerable> 和 <xref:System.Collections.Generic.IEnumerable%601>，您可以在所有以 C# 撰寫的陣列上使用 [foreach](../../../csharp/language-reference/keywords/foreach-in.md) 反覆項目。</span><span class="sxs-lookup"><span data-stu-id="47786-116">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../../csharp/language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="47786-117">相關章節</span><span class="sxs-lookup"><span data-stu-id="47786-117">Related Sections</span></span>  
  
-   [<span data-ttu-id="47786-118">陣列作為物件</span><span class="sxs-lookup"><span data-stu-id="47786-118">Arrays as Objects</span></span>](../../../csharp/programming-guide/arrays/arrays-as-objects.md)  
  
-   [<span data-ttu-id="47786-119">搭配陣列使用 foreach</span><span class="sxs-lookup"><span data-stu-id="47786-119">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
  
-   [<span data-ttu-id="47786-120">傳遞陣列作為引數</span><span class="sxs-lookup"><span data-stu-id="47786-120">Passing Arrays as Arguments</span></span>](../../../csharp/programming-guide/arrays/passing-arrays-as-arguments.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="47786-121">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="47786-121">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="47786-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47786-122">See also</span></span>

- [<span data-ttu-id="47786-123">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="47786-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="47786-124">集合</span><span class="sxs-lookup"><span data-stu-id="47786-124">Collections</span></span>](../../../csharp/programming-guide/concepts/collections.md)
