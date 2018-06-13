---
title: 一維陣列 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: 2f5dcb032c5dea764cdd212bbcd02e1640089d96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313949"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="1ea27-102">一維陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="1ea27-102">Single-Dimensional Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="1ea27-103">您可以宣告五個整數的一維陣列，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="1ea27-103">You can declare a single-dimensional array of five integers as shown in the following example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#4](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_1.cs)]  
  
 <span data-ttu-id="1ea27-104">這個陣列包含從 `array[0]` 到 `array[4]` 的項目。</span><span class="sxs-lookup"><span data-stu-id="1ea27-104">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="1ea27-105">[new](../../../csharp/language-reference/keywords/new.md) 運算子是用來建立陣列，並將陣列元素初始化為其預設值。</span><span class="sxs-lookup"><span data-stu-id="1ea27-105">The [new](../../../csharp/language-reference/keywords/new.md) operator is used to create the array and initialize the array elements to their default values.</span></span> <span data-ttu-id="1ea27-106">在此範例中，所有陣列元素都會初始化為零。</span><span class="sxs-lookup"><span data-stu-id="1ea27-106">In this example, all the array elements are initialized to zero.</span></span>  
  
 <span data-ttu-id="1ea27-107">儲存字串項目的陣列可以使用相同的方式進行宣告。</span><span class="sxs-lookup"><span data-stu-id="1ea27-107">An array that stores string elements can be declared in the same way.</span></span> <span data-ttu-id="1ea27-108">例如: </span><span class="sxs-lookup"><span data-stu-id="1ea27-108">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#5](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a><span data-ttu-id="1ea27-109">陣列初始化</span><span class="sxs-lookup"><span data-stu-id="1ea27-109">Array Initialization</span></span>  
 <span data-ttu-id="1ea27-110">可以在宣告時初始化陣列，在此情況下，不需要陣序規範，因為它已由初始化清單中的項目數所提供。</span><span class="sxs-lookup"><span data-stu-id="1ea27-110">It is possible to initialize an array upon declaration, in which case, the rank specifier is not needed because it is already supplied by the number of elements in the initialization list.</span></span> <span data-ttu-id="1ea27-111">例如: </span><span class="sxs-lookup"><span data-stu-id="1ea27-111">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#6](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_3.cs)]  
  
 <span data-ttu-id="1ea27-112">字串陣列可以使用相同的方式進行初始化。</span><span class="sxs-lookup"><span data-stu-id="1ea27-112">A string array can be initialized in the same way.</span></span> <span data-ttu-id="1ea27-113">以下是字串陣列宣告，其中都會以日名稱初始化每個陣列元素：</span><span class="sxs-lookup"><span data-stu-id="1ea27-113">The following is a declaration of a string array where each array element is initialized by a name of a day:</span></span>  
  
 [!code-csharp[csProgGuideArrays#7](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_4.cs)]  
  
 <span data-ttu-id="1ea27-114">當您在宣告時初始化陣列時，可以使用下列快速鍵：</span><span class="sxs-lookup"><span data-stu-id="1ea27-114">When you initialize an array upon declaration, you can use the following shortcuts:</span></span>  
  
 [!code-csharp[csProgGuideArrays#8](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_5.cs)]  
  
 <span data-ttu-id="1ea27-115">您可以在不進行初始化的情況下宣告陣列變數，但必須在將陣列指派給變數時使用 `new` 運算子。</span><span class="sxs-lookup"><span data-stu-id="1ea27-115">It is possible to declare an array variable without initialization, but you must use the `new` operator when you assign an array to this variable.</span></span> <span data-ttu-id="1ea27-116">例如: </span><span class="sxs-lookup"><span data-stu-id="1ea27-116">For example:</span></span>  
  
 [!code-csharp[csProgGuideArrays#9](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_6.cs)]  
  
 <span data-ttu-id="1ea27-117">C# 3.0 引進隱含型別陣列。</span><span class="sxs-lookup"><span data-stu-id="1ea27-117">C# 3.0 introduces implicitly typed arrays.</span></span> <span data-ttu-id="1ea27-118">如需詳細資訊，請參閱[隱含型別陣列](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md)。</span><span class="sxs-lookup"><span data-stu-id="1ea27-118">For more information, see [Implicitly Typed Arrays](../../../csharp/programming-guide/arrays/implicitly-typed-arrays.md).</span></span>  
  
## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="1ea27-119">實值型別和參考型別陣列</span><span class="sxs-lookup"><span data-stu-id="1ea27-119">Value Type and Reference Type Arrays</span></span>  
 <span data-ttu-id="1ea27-120">請考慮下列陣列宣告：</span><span class="sxs-lookup"><span data-stu-id="1ea27-120">Consider the following array declaration:</span></span>  
  
 [!code-csharp[csProgGuideArrays#10](../../../csharp/programming-guide/arrays/codesnippet/CSharp/single-dimensional-arrays_7.cs)]  
  
 <span data-ttu-id="1ea27-121">此陳述式的結果取決於 `SomeType` 是實值型別還是參考型別。</span><span class="sxs-lookup"><span data-stu-id="1ea27-121">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="1ea27-122">如果它是實值型別，陳述式會建立 10 個項目的陣列，且每個都具有 `SomeType` 類型。</span><span class="sxs-lookup"><span data-stu-id="1ea27-122">If it is a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="1ea27-123">如果 `SomeType` 是參考型別，陳述式會建立 10 個項目的陣列，且每個都會初始化為 Null 參考。</span><span class="sxs-lookup"><span data-stu-id="1ea27-123">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span>  
  
 <span data-ttu-id="1ea27-124">如需實值型別和參考型別的詳細資訊，請參閱[類型](../../../csharp/language-reference/keywords/types.md)。</span><span class="sxs-lookup"><span data-stu-id="1ea27-124">For more information about value types and reference types, see [Types](../../../csharp/language-reference/keywords/types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ea27-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="1ea27-125">See Also</span></span>  
 <xref:System.Array>  
 [<span data-ttu-id="1ea27-126">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="1ea27-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1ea27-127">陣列</span><span class="sxs-lookup"><span data-stu-id="1ea27-127">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="1ea27-128">多維陣列</span><span class="sxs-lookup"><span data-stu-id="1ea27-128">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="1ea27-129">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="1ea27-129">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
