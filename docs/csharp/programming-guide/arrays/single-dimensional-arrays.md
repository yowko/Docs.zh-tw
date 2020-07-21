---
title: 一維陣列 - C# 程式設計手冊
description: '使用 new 運算子，在 c # 中建立一維陣列，以指定陣列專案類型和元素數目。'
ms.date: 06/03/2020
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: ada01262d57cbfebc8bfa1a5fee0639a10db5a4b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474588"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="fceb5-103">一維陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="fceb5-103">Single-Dimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="fceb5-104">您可以使用[new](../../language-reference/operators/new-operator.md)運算子來建立一維陣列，以指定陣列專案類型和元素數目。</span><span class="sxs-lookup"><span data-stu-id="fceb5-104">You create a single-dimensional array using the [new](../../language-reference/operators/new-operator.md) operator specifying the array element type and the number of elements.</span></span> <span data-ttu-id="fceb5-105">下列範例會宣告五個整數的陣列：</span><span class="sxs-lookup"><span data-stu-id="fceb5-105">The following example declares an array of five integers:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntDeclaration":::

<span data-ttu-id="fceb5-106">這個陣列包含從 `array[0]` 到 `array[4]` 的項目。</span><span class="sxs-lookup"><span data-stu-id="fceb5-106">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="fceb5-107">陣列的元素會初始化為整數的元素類型的預設值 `0` 。</span><span class="sxs-lookup"><span data-stu-id="fceb5-107">The elements of the array are initialized to the default value of the element type, `0` for integers.</span></span>

<span data-ttu-id="fceb5-108">陣列可以儲存您指定的任何元素類型，例如下列宣告字串陣列的範例：</span><span class="sxs-lookup"><span data-stu-id="fceb5-108">Arrays can store any element type you specify, such as the following example that declares an array of strings:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringDeclaration":::

## <a name="array-initialization"></a><span data-ttu-id="fceb5-109">陣列初始化</span><span class="sxs-lookup"><span data-stu-id="fceb5-109">Array Initialization</span></span>

<span data-ttu-id="fceb5-110">當您宣告陣列時，您可以初始化陣列的元素。</span><span class="sxs-lookup"><span data-stu-id="fceb5-110">You can initialize the elements of an array when you declare the array.</span></span> <span data-ttu-id="fceb5-111">長度規範不是必要的，因為它是由初始化清單中的元素數目所推斷。</span><span class="sxs-lookup"><span data-stu-id="fceb5-111">The length specifier isn't needed because it's inferred by the number of elements in the initialization list.</span></span> <span data-ttu-id="fceb5-112">例如：</span><span class="sxs-lookup"><span data-stu-id="fceb5-112">For example:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntInitialization":::

<span data-ttu-id="fceb5-113">下列程式碼顯示字串陣列的宣告，其中每個陣列專案都是以一天的名稱初始化：</span><span class="sxs-lookup"><span data-stu-id="fceb5-113">The following code shows a declaration of a string array where each array element is initialized by a name of a day:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringInitialization":::
  
<span data-ttu-id="fceb5-114">當您在宣告 `new` 時初始化陣列時，可以避免運算式和陣列類型，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="fceb5-114">You can avoid the `new` expression and the array type when you initialize an array upon declaration, as shown in the following code.</span></span> <span data-ttu-id="fceb5-115">這稱為[隱含類型陣列](implicitly-typed-arrays.md)：</span><span class="sxs-lookup"><span data-stu-id="fceb5-115">This is called an [implicitly typed array](implicitly-typed-arrays.md):</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="ShorthandInitialization":::

<span data-ttu-id="fceb5-116">您可以宣告陣列變數而不建立它，但 `new` 當您將新陣列指派給這個變數時，必須使用運算子。</span><span class="sxs-lookup"><span data-stu-id="fceb5-116">You can declare an array variable without creating it, but you must use the `new` operator when you assign a new array to this variable.</span></span> <span data-ttu-id="fceb5-117">例如：</span><span class="sxs-lookup"><span data-stu-id="fceb5-117">For example:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="DeclareAllocate":::

## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="fceb5-118">實值型別和參考型別陣列</span><span class="sxs-lookup"><span data-stu-id="fceb5-118">Value Type and Reference Type Arrays</span></span>

<span data-ttu-id="fceb5-119">請考慮下列陣列宣告：</span><span class="sxs-lookup"><span data-stu-id="fceb5-119">Consider the following array declaration:</span></span>  

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="FinalInstantiation":::

<span data-ttu-id="fceb5-120">此陳述式的結果取決於 `SomeType` 是實值型別還是參考型別。</span><span class="sxs-lookup"><span data-stu-id="fceb5-120">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="fceb5-121">如果它是實值型別，則語句會建立10個專案的陣列，其中每個專案都有型別 `SomeType` 。</span><span class="sxs-lookup"><span data-stu-id="fceb5-121">If it's a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="fceb5-122">如果 `SomeType` 是參考型別，陳述式會建立 10 個項目的陣列，且每個都會初始化為 Null 參考。</span><span class="sxs-lookup"><span data-stu-id="fceb5-122">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span> <span data-ttu-id="fceb5-123">在這兩個實例中，專案都會初始化為元素類型的預設值。</span><span class="sxs-lookup"><span data-stu-id="fceb5-123">In both instances, the elements are initialized to the default value for the element type.</span></span> <span data-ttu-id="fceb5-124">如需實數值型別和參考型別的詳細資訊，請參閱實[數值型別](../../language-reference/builtin-types/value-types.md)和[參考型別](../../language-reference/keywords/reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="fceb5-124">For more information about value types and reference types, see [Value types](../../language-reference/builtin-types/value-types.md) and [Reference types](../../language-reference/keywords/reference-types.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="fceb5-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fceb5-125">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="fceb5-126">陣列</span><span class="sxs-lookup"><span data-stu-id="fceb5-126">Arrays</span></span>](./index.md)
- [<span data-ttu-id="fceb5-127">多維陣列</span><span class="sxs-lookup"><span data-stu-id="fceb5-127">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="fceb5-128">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="fceb5-128">Jagged Arrays</span></span>](./jagged-arrays.md)
