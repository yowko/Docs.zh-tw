---
title: 陣列 - C# 程式設計手冊
description: '在 c # 的陣列資料結構中儲存相同類型的多個變數。 藉由指定類型或指定物件來儲存任何類型來宣告陣列。'
ms.date: 01/22/2021
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: 203d8b86da4e74d8c5397132a0ba68618eedf348
ms.sourcegitcommit: 4d5e25a46aa7cd0d29b4b9227b92987354d444c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/26/2021
ms.locfileid: "98794773"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="e93f2-104">陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="e93f2-104">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="e93f2-105">您可以在陣列資料結構中儲存相同類型的多個變數。</span><span class="sxs-lookup"><span data-stu-id="e93f2-105">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="e93f2-106">您可以指定陣列元素的類型來宣告陣列。</span><span class="sxs-lookup"><span data-stu-id="e93f2-106">You declare an array by specifying the type of its elements.</span></span> <span data-ttu-id="e93f2-107">如果您希望陣列儲存任何類型的元素，您可以指定 `object` 做為其類型。</span><span class="sxs-lookup"><span data-stu-id="e93f2-107">If you want the array to store elements of any type, you can specify `object` as its type.</span></span> <span data-ttu-id="e93f2-108">在 C# 的統一型別系統中，所有類型 (預先定義和使用者定義的、參考型別和實值型別) 都會直接或間接繼承自 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="e93f2-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span>

```csharp
type[] arrayName;
```

## <a name="example"></a><span data-ttu-id="e93f2-109">範例</span><span class="sxs-lookup"><span data-stu-id="e93f2-109">Example</span></span>

<span data-ttu-id="e93f2-110">下列範例會建立一維陣列、多維陣列和不規則陣列︰</span><span class="sxs-lookup"><span data-stu-id="e93f2-110">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a><span data-ttu-id="e93f2-111">陣列總覽</span><span class="sxs-lookup"><span data-stu-id="e93f2-111">Array overview</span></span>

<span data-ttu-id="e93f2-112">陣列具有下列屬性︰</span><span class="sxs-lookup"><span data-stu-id="e93f2-112">An array has the following properties:</span></span>

- <span data-ttu-id="e93f2-113">陣列可以是[單一維度](single-dimensional-arrays.md) [、多維度或](multidimensional-arrays.md)[不規則](jagged-arrays.md)的。</span><span class="sxs-lookup"><span data-stu-id="e93f2-113">An array can be [single-dimensional](single-dimensional-arrays.md), [multidimensional](multidimensional-arrays.md) or [jagged](jagged-arrays.md).</span></span>
- <span data-ttu-id="e93f2-114">當陣列執行個體建立時，也會建立維度的數目和每個維度的長度。</span><span class="sxs-lookup"><span data-stu-id="e93f2-114">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="e93f2-115">在執行個體的存留期期間，這些值無法變更。</span><span class="sxs-lookup"><span data-stu-id="e93f2-115">These values can't be changed during the lifetime of the instance.</span></span>
- <span data-ttu-id="e93f2-116">數值陣列元素的預設值設定為零，且參考元素會設定為 null。</span><span class="sxs-lookup"><span data-stu-id="e93f2-116">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>
- <span data-ttu-id="e93f2-117">不規則陣列為陣列的陣列，因此其元素為參考類型，且會初始化為 `null`。</span><span class="sxs-lookup"><span data-stu-id="e93f2-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>
- <span data-ttu-id="e93f2-118">陣列為以零為基底索引：具有 `n` 個元素的陣列，會從 `0` 到 `n-1` 編製索引。</span><span class="sxs-lookup"><span data-stu-id="e93f2-118">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>
- <span data-ttu-id="e93f2-119">陣列元素可以是任何類型，包含陣列類型。</span><span class="sxs-lookup"><span data-stu-id="e93f2-119">Array elements can be of any type, including an array type.</span></span>
- <span data-ttu-id="e93f2-120">陣列類型是衍生自抽象基底類型 <xref:System.Array> 的[參考類型](../../language-reference/keywords/reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="e93f2-120">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="e93f2-121">由於這個類型會實作 <xref:System.Collections.IEnumerable> 和 <xref:System.Collections.Generic.IEnumerable%601>，您可以在所有以 C# 撰寫的陣列上使用 [foreach](../../language-reference/keywords/foreach-in.md) 反覆項目。</span><span class="sxs-lookup"><span data-stu-id="e93f2-121">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>

### <a name="arrays-as-objects"></a><span data-ttu-id="e93f2-122">陣列作為物件</span><span class="sxs-lookup"><span data-stu-id="e93f2-122">Arrays as Objects</span></span>

<span data-ttu-id="e93f2-123">在 C# 中，陣列其實是物件，不只是 C 和 C++ 中連續記憶體的可定址區域。</span><span class="sxs-lookup"><span data-stu-id="e93f2-123">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="e93f2-124"><xref:System.Array> 是所有陣列類型的抽象基底類型。</span><span class="sxs-lookup"><span data-stu-id="e93f2-124"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="e93f2-125">您可以使用具有的屬性和其他類別成員 <xref:System.Array> 。</span><span class="sxs-lookup"><span data-stu-id="e93f2-125">You can use the properties and other class members that <xref:System.Array> has.</span></span> <span data-ttu-id="e93f2-126">其中一個範例是使用 <xref:System.Array.Length%2A> 屬性來取得陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="e93f2-126">An example of this is using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="e93f2-127">下列程式碼會將 `numbers` 陣列的長度 (也就是 `5`) 指派到名為 `lengthOfNumbers` 的變數：</span><span class="sxs-lookup"><span data-stu-id="e93f2-127">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<span data-ttu-id="e93f2-128"><xref:System.Array> 類別會提供許多其他有用的方法和屬性以排序、搜尋和複製陣列。</span><span class="sxs-lookup"><span data-stu-id="e93f2-128">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span> <span data-ttu-id="e93f2-129">下列範例會使用 <xref:System.Array.Rank%2A> 屬性來顯示陣列的維度數目。</span><span class="sxs-lookup"><span data-stu-id="e93f2-129">The following example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a><span data-ttu-id="e93f2-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e93f2-130">See also</span></span>

- [<span data-ttu-id="e93f2-131">如何使用一維陣列</span><span class="sxs-lookup"><span data-stu-id="e93f2-131">How to use single-dimensional arrays</span></span>](single-dimensional-arrays.md)
- [<span data-ttu-id="e93f2-132">如何使用多維度陣列</span><span class="sxs-lookup"><span data-stu-id="e93f2-132">How to use multi-dimensional arrays</span></span>](multidimensional-arrays.md)
- [<span data-ttu-id="e93f2-133">如何使用不規則陣列</span><span class="sxs-lookup"><span data-stu-id="e93f2-133">How to use jagged arrays</span></span>](jagged-arrays.md)
- [<span data-ttu-id="e93f2-134">搭配陣列使用 foreach</span><span class="sxs-lookup"><span data-stu-id="e93f2-134">Using foreach with arrays</span></span>](using-foreach-with-arrays.md)
- [<span data-ttu-id="e93f2-135">傳遞陣列作為引數</span><span class="sxs-lookup"><span data-stu-id="e93f2-135">Passing arrays as arguments</span></span>](passing-arrays-as-arguments.md)
- [<span data-ttu-id="e93f2-136">隱含類型陣列</span><span class="sxs-lookup"><span data-stu-id="e93f2-136">Implicitly typed arrays</span></span>](implicitly-typed-arrays.md)
- [<span data-ttu-id="e93f2-137">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="e93f2-137">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="e93f2-138">集合</span><span class="sxs-lookup"><span data-stu-id="e93f2-138">Collections</span></span>](../concepts/collections.md)

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]
