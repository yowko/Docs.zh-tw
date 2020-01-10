---
title: 陣列 - C# 程式設計手冊
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: bbabc84c144e5b3415c19f346b890782e251662c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715060"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="19118-102">陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="19118-102">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="19118-103">您可以在陣列資料結構中儲存相同類型的多個變數。</span><span class="sxs-lookup"><span data-stu-id="19118-103">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="19118-104">您可以指定陣列元素的類型來宣告陣列。</span><span class="sxs-lookup"><span data-stu-id="19118-104">You declare an array by specifying the type of its elements.</span></span> <span data-ttu-id="19118-105">如果您想要讓陣列儲存任何類型的元素，您可以指定 `object` 做為其類型。</span><span class="sxs-lookup"><span data-stu-id="19118-105">If you want the array to store elements of any type, you can specify `object` as its type.</span></span> <span data-ttu-id="19118-106">在 C# 的統一型別系統中，所有類型 (預先定義和使用者定義的、參考型別和實值型別) 都會直接或間接繼承自 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="19118-106">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span>

```csharp
type[] arrayName;
```

## <a name="example"></a><span data-ttu-id="19118-107">範例</span><span class="sxs-lookup"><span data-stu-id="19118-107">Example</span></span>

<span data-ttu-id="19118-108">下列範例會建立一維陣列、多維陣列和不規則陣列︰</span><span class="sxs-lookup"><span data-stu-id="19118-108">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a><span data-ttu-id="19118-109">陣列總覽</span><span class="sxs-lookup"><span data-stu-id="19118-109">Array overview</span></span>

<span data-ttu-id="19118-110">陣列具有下列屬性︰</span><span class="sxs-lookup"><span data-stu-id="19118-110">An array has the following properties:</span></span>

- <span data-ttu-id="19118-111">陣列可以是[一維](single-dimensional-arrays.md)、[多維](multidimensional-arrays.md)或[不規則](jagged-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="19118-111">An array can be [Single-Dimensional](single-dimensional-arrays.md), [Multidimensional](multidimensional-arrays.md) or [Jagged](jagged-arrays.md).</span></span>
- <span data-ttu-id="19118-112">當陣列執行個體建立時，也會建立維度的數目和每個維度的長度。</span><span class="sxs-lookup"><span data-stu-id="19118-112">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="19118-113">在執行個體的存留期期間，這些值無法變更。</span><span class="sxs-lookup"><span data-stu-id="19118-113">These values can't be changed during the lifetime of the instance.</span></span>
- <span data-ttu-id="19118-114">數值陣列元素的預設值設定為零，且參考元素會設定為 null。</span><span class="sxs-lookup"><span data-stu-id="19118-114">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>
- <span data-ttu-id="19118-115">不規則陣列為陣列的陣列，因此其元素為參考類型，且會初始化為 `null`。</span><span class="sxs-lookup"><span data-stu-id="19118-115">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>
- <span data-ttu-id="19118-116">陣列為以零為基底索引：具有 `n` 個元素的陣列，會從 `0` 到 `n-1` 編製索引。</span><span class="sxs-lookup"><span data-stu-id="19118-116">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>
- <span data-ttu-id="19118-117">陣列元素可以是任何類型，包含陣列類型。</span><span class="sxs-lookup"><span data-stu-id="19118-117">Array elements can be of any type, including an array type.</span></span>
- <span data-ttu-id="19118-118">陣列類型是衍生自抽象基底類型 <xref:System.Array> 的[參考類型](../../language-reference/keywords/reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="19118-118">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="19118-119">由於這個類型會實作 <xref:System.Collections.IEnumerable> 和 <xref:System.Collections.Generic.IEnumerable%601>，您可以在所有以 C# 撰寫的陣列上使用 [foreach](../../language-reference/keywords/foreach-in.md) 反覆項目。</span><span class="sxs-lookup"><span data-stu-id="19118-119">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>

## <a name="related-sections"></a><span data-ttu-id="19118-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="19118-120">Related sections</span></span>

- [<span data-ttu-id="19118-121">陣列作為物件</span><span class="sxs-lookup"><span data-stu-id="19118-121">Arrays as Objects</span></span>](arrays-as-objects.md)
- [<span data-ttu-id="19118-122">搭配陣列使用 foreach</span><span class="sxs-lookup"><span data-stu-id="19118-122">Using foreach with Arrays</span></span>](using-foreach-with-arrays.md)
- [<span data-ttu-id="19118-123">傳遞陣列作為引數</span><span class="sxs-lookup"><span data-stu-id="19118-123">Passing Arrays as Arguments</span></span>](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a><span data-ttu-id="19118-124">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="19118-124">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="19118-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="19118-125">See also</span></span>

- [<span data-ttu-id="19118-126">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="19118-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="19118-127">集合</span><span class="sxs-lookup"><span data-stu-id="19118-127">Collections</span></span>](../concepts/collections.md)
