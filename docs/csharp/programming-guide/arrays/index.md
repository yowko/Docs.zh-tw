---
title: 陣列 - C# 程式設計手冊
description: '在 c # 中，將相同類型的多個變數儲存在陣列資料結構中。 藉由指定類型或指定物件來儲存任何類型，以宣告陣列。'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#]
- C# language, arrays
ms.assetid: bb79bdde-e570-4c30-adb0-1dd5759ae041
ms.openlocfilehash: e302ff2e4c2488c4899c4eb99a666d2d322119ce
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474731"
---
# <a name="arrays-c-programming-guide"></a><span data-ttu-id="f191a-104">陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="f191a-104">Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="f191a-105">您可以在陣列資料結構中儲存相同類型的多個變數。</span><span class="sxs-lookup"><span data-stu-id="f191a-105">You can store multiple variables of the same type in an array data structure.</span></span> <span data-ttu-id="f191a-106">您可以指定陣列元素的類型來宣告陣列。</span><span class="sxs-lookup"><span data-stu-id="f191a-106">You declare an array by specifying the type of its elements.</span></span> <span data-ttu-id="f191a-107">如果您想要讓陣列儲存任何類型的專案，您可以將指定 `object` 為其類型。</span><span class="sxs-lookup"><span data-stu-id="f191a-107">If you want the array to store elements of any type, you can specify `object` as its type.</span></span> <span data-ttu-id="f191a-108">在 C# 的統一型別系統中，所有類型 (預先定義和使用者定義的、參考型別和實值型別) 都會直接或間接繼承自 <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="f191a-108">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span>

```csharp
type[] arrayName;
```

## <a name="example"></a><span data-ttu-id="f191a-109">範例</span><span class="sxs-lookup"><span data-stu-id="f191a-109">Example</span></span>

<span data-ttu-id="f191a-110">下列範例會建立一維陣列、多維陣列和不規則陣列︰</span><span class="sxs-lookup"><span data-stu-id="f191a-110">The following example creates single-dimensional, multidimensional, and jagged arrays:</span></span>

[!code-csharp[csProgGuideArrays#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#1)]

## <a name="array-overview"></a><span data-ttu-id="f191a-111">陣列總覽</span><span class="sxs-lookup"><span data-stu-id="f191a-111">Array overview</span></span>

<span data-ttu-id="f191a-112">陣列具有下列屬性︰</span><span class="sxs-lookup"><span data-stu-id="f191a-112">An array has the following properties:</span></span>

- <span data-ttu-id="f191a-113">陣列可以是[一維](single-dimensional-arrays.md)、[多維](multidimensional-arrays.md)或[不規則](jagged-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="f191a-113">An array can be [Single-Dimensional](single-dimensional-arrays.md), [Multidimensional](multidimensional-arrays.md) or [Jagged](jagged-arrays.md).</span></span>
- <span data-ttu-id="f191a-114">當陣列執行個體建立時，也會建立維度的數目和每個維度的長度。</span><span class="sxs-lookup"><span data-stu-id="f191a-114">The number of dimensions and the length of each dimension are established when the array instance is created.</span></span> <span data-ttu-id="f191a-115">在執行個體的存留期期間，這些值無法變更。</span><span class="sxs-lookup"><span data-stu-id="f191a-115">These values can't be changed during the lifetime of the instance.</span></span>
- <span data-ttu-id="f191a-116">數值陣列元素的預設值設定為零，且參考元素會設定為 null。</span><span class="sxs-lookup"><span data-stu-id="f191a-116">The default values of numeric array elements are set to zero, and reference elements are set to null.</span></span>
- <span data-ttu-id="f191a-117">不規則陣列為陣列的陣列，因此其元素為參考類型，且會初始化為 `null`。</span><span class="sxs-lookup"><span data-stu-id="f191a-117">A jagged array is an array of arrays, and therefore its elements are reference types and are initialized to `null`.</span></span>
- <span data-ttu-id="f191a-118">陣列為以零為基底索引：具有 `n` 個元素的陣列，會從 `0` 到 `n-1` 編製索引。</span><span class="sxs-lookup"><span data-stu-id="f191a-118">Arrays are zero indexed: an array with `n` elements is indexed from `0` to `n-1`.</span></span>
- <span data-ttu-id="f191a-119">陣列元素可以是任何類型，包含陣列類型。</span><span class="sxs-lookup"><span data-stu-id="f191a-119">Array elements can be of any type, including an array type.</span></span>
- <span data-ttu-id="f191a-120">陣列類型是衍生自抽象基底類型 <xref:System.Array> 的[參考類型](../../language-reference/keywords/reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="f191a-120">Array types are [reference types](../../language-reference/keywords/reference-types.md) derived from the abstract base type <xref:System.Array>.</span></span> <span data-ttu-id="f191a-121">由於這個類型會實作 <xref:System.Collections.IEnumerable> 和 <xref:System.Collections.Generic.IEnumerable%601>，您可以在所有以 C# 撰寫的陣列上使用 [foreach](../../language-reference/keywords/foreach-in.md) 反覆項目。</span><span class="sxs-lookup"><span data-stu-id="f191a-121">Since this type implements <xref:System.Collections.IEnumerable> and <xref:System.Collections.Generic.IEnumerable%601>, you can use [foreach](../../language-reference/keywords/foreach-in.md) iteration on all arrays in C#.</span></span>

## <a name="related-sections"></a><span data-ttu-id="f191a-122">相關章節</span><span class="sxs-lookup"><span data-stu-id="f191a-122">Related sections</span></span>

- [<span data-ttu-id="f191a-123">陣列作為物件</span><span class="sxs-lookup"><span data-stu-id="f191a-123">Arrays as Objects</span></span>](arrays-as-objects.md)
- [<span data-ttu-id="f191a-124">搭配陣列使用 foreach</span><span class="sxs-lookup"><span data-stu-id="f191a-124">Using foreach with Arrays</span></span>](using-foreach-with-arrays.md)
- [<span data-ttu-id="f191a-125">傳遞陣列作為引數</span><span class="sxs-lookup"><span data-stu-id="f191a-125">Passing Arrays as Arguments</span></span>](passing-arrays-as-arguments.md)

## <a name="c-language-specification"></a><span data-ttu-id="f191a-126">C# 語言規格</span><span class="sxs-lookup"><span data-stu-id="f191a-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f191a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f191a-127">See also</span></span>

- [<span data-ttu-id="f191a-128">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f191a-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f191a-129">集合</span><span class="sxs-lookup"><span data-stu-id="f191a-129">Collections</span></span>](../concepts/collections.md)
