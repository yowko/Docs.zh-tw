---
title: 一維陣列 - C# 程式設計手冊
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: 8f093d22da789c6df750475e47a3b4e4685c5651
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744205"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="5c913-102">一維陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="5c913-102">Single-Dimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="5c913-103">您可以宣告五個整數的一維陣列，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="5c913-103">You can declare a single-dimensional array of five integers as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#4)]  
  
 <span data-ttu-id="5c913-104">這個陣列包含從 `array[0]` 到 `array[4]` 的項目。</span><span class="sxs-lookup"><span data-stu-id="5c913-104">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="5c913-105">[new](../../language-reference/operators/new-operator.md) 運算子是用來建立陣列，並將陣列元素初始化為其預設值。</span><span class="sxs-lookup"><span data-stu-id="5c913-105">The [new](../../language-reference/operators/new-operator.md) operator is used to create the array and initialize the array elements to their default values.</span></span> <span data-ttu-id="5c913-106">在此範例中，所有陣列元素都會初始化為零。</span><span class="sxs-lookup"><span data-stu-id="5c913-106">In this example, all the array elements are initialized to zero.</span></span>  
  
 <span data-ttu-id="5c913-107">儲存字串項目的陣列可以使用相同的方式進行宣告。</span><span class="sxs-lookup"><span data-stu-id="5c913-107">An array that stores string elements can be declared in the same way.</span></span> <span data-ttu-id="5c913-108">例如，</span><span class="sxs-lookup"><span data-stu-id="5c913-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#5)]  
  
## <a name="array-initialization"></a><span data-ttu-id="5c913-109">陣列初始化</span><span class="sxs-lookup"><span data-stu-id="5c913-109">Array Initialization</span></span>

 <span data-ttu-id="5c913-110">您可以在宣告時將陣列初始化，在此情況下，因為長度規範已由初始化清單中的項目數所提供，所以不需要長度規範。</span><span class="sxs-lookup"><span data-stu-id="5c913-110">It is possible to initialize an array upon declaration, in which case, the length specifier is not needed because it is already supplied by the number of elements in the initialization list.</span></span> <span data-ttu-id="5c913-111">例如，</span><span class="sxs-lookup"><span data-stu-id="5c913-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#6)]  
  
 <span data-ttu-id="5c913-112">字串陣列可以使用相同的方式進行初始化。</span><span class="sxs-lookup"><span data-stu-id="5c913-112">A string array can be initialized in the same way.</span></span> <span data-ttu-id="5c913-113">以下是字串陣列宣告，其中都會以日名稱初始化每個陣列元素：</span><span class="sxs-lookup"><span data-stu-id="5c913-113">The following is a declaration of a string array where each array element is initialized by a name of a day:</span></span>  
 
 ```csharp
 string[] weekDays = new string[] { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };
 ```
  
 <span data-ttu-id="5c913-114">當您在宣告時初始化陣列時，可以使用下列快速鍵：</span><span class="sxs-lookup"><span data-stu-id="5c913-114">When you initialize an array upon declaration, you can use the following shortcuts:</span></span>  
  
 [!code-csharp[csProgGuideArrays#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#8)]  
  
 <span data-ttu-id="5c913-115">您可以在不進行初始化的情況下宣告陣列變數，但必須在將陣列指派給變數時使用 `new` 運算子。</span><span class="sxs-lookup"><span data-stu-id="5c913-115">It is possible to declare an array variable without initialization, but you must use the `new` operator when you assign an array to this variable.</span></span> <span data-ttu-id="5c913-116">例如，</span><span class="sxs-lookup"><span data-stu-id="5c913-116">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#9)]  
  
 <span data-ttu-id="5c913-117">C# 3.0 引進隱含型別陣列。</span><span class="sxs-lookup"><span data-stu-id="5c913-117">C# 3.0 introduces implicitly typed arrays.</span></span> <span data-ttu-id="5c913-118">如需詳細資訊，請參閱[隱含型別陣列](./implicitly-typed-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="5c913-118">For more information, see [Implicitly Typed Arrays](./implicitly-typed-arrays.md).</span></span>  
  
## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="5c913-119">實值型別和參考型別陣列</span><span class="sxs-lookup"><span data-stu-id="5c913-119">Value Type and Reference Type Arrays</span></span>

 <span data-ttu-id="5c913-120">請考慮下列陣列宣告：</span><span class="sxs-lookup"><span data-stu-id="5c913-120">Consider the following array declaration:</span></span>  
  
 [!code-csharp[csProgGuideArrays#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#10)]  
  
 <span data-ttu-id="5c913-121">此陳述式的結果取決於 `SomeType` 是實值型別還是參考型別。</span><span class="sxs-lookup"><span data-stu-id="5c913-121">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="5c913-122">如果它是實值型別，陳述式會建立 10 個項目的陣列，且每個都具有 `SomeType` 類型。</span><span class="sxs-lookup"><span data-stu-id="5c913-122">If it is a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="5c913-123">如果 `SomeType` 是參考型別，陳述式會建立 10 個項目的陣列，且每個都會初始化為 Null 參考。</span><span class="sxs-lookup"><span data-stu-id="5c913-123">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span>  
  
<span data-ttu-id="5c913-124">如需實數值型別和參考型別的詳細資訊，請參閱實[數值型別](../../language-reference/builtin-types/value-types.md)和[參考型別](../../language-reference/keywords/reference-types.md)。</span><span class="sxs-lookup"><span data-stu-id="5c913-124">For more information about value types and reference types, see [Value types](../../language-reference/builtin-types/value-types.md) and [Reference types](../../language-reference/keywords/reference-types.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="5c913-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c913-125">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="5c913-126">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="5c913-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="5c913-127">陣列</span><span class="sxs-lookup"><span data-stu-id="5c913-127">Arrays</span></span>](./index.md)
- [<span data-ttu-id="5c913-128">多維陣列</span><span class="sxs-lookup"><span data-stu-id="5c913-128">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="5c913-129">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="5c913-129">Jagged Arrays</span></span>](./jagged-arrays.md)
