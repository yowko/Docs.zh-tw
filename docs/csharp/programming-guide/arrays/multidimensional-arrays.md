---
title: 多維陣列 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: 12cc7ff4f0a688145f2dee130e66dbe9a05ec7e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33313845"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="815e5-102">多維陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="815e5-102">Multidimensional Arrays (C# Programming Guide)</span></span>
<span data-ttu-id="815e5-103">陣列可以有多個維度。</span><span class="sxs-lookup"><span data-stu-id="815e5-103">Arrays can have more than one dimension.</span></span> <span data-ttu-id="815e5-104">例如，下列宣告會建立具有四個資料列和兩個資料行的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="815e5-104">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_1.cs)]  
  
 <span data-ttu-id="815e5-105">下列宣告會建立三維 (4、2 和 3) 陣列。</span><span class="sxs-lookup"><span data-stu-id="815e5-105">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_2.cs)]  
  
## <a name="array-initialization"></a><span data-ttu-id="815e5-106">陣列初始化</span><span class="sxs-lookup"><span data-stu-id="815e5-106">Array Initialization</span></span>  
 <span data-ttu-id="815e5-107">您可以在宣告後初始化陣列，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="815e5-107">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_3.cs)]  
  
 <span data-ttu-id="815e5-108">也可以初始化陣列，而不指定順位。</span><span class="sxs-lookup"><span data-stu-id="815e5-108">You also can initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_4.cs)]  
  
 <span data-ttu-id="815e5-109">如果選擇在不進行初始化的情況下宣告變數，則必須使用 `new` 運算子將陣列指派給變數。</span><span class="sxs-lookup"><span data-stu-id="815e5-109">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="815e5-110">下列範例會顯示 `new` 的用法。</span><span class="sxs-lookup"><span data-stu-id="815e5-110">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_5.cs)]  
  
 <span data-ttu-id="815e5-111">下列範例會將值指派給特定的陣列元素。</span><span class="sxs-lookup"><span data-stu-id="815e5-111">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_6.cs)]  
  
 <span data-ttu-id="815e5-112">同樣地，下列範例會取得特定陣列元素的值，並將它指派給 `elementValue` 變數。</span><span class="sxs-lookup"><span data-stu-id="815e5-112">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_7.cs)]  
  
 <span data-ttu-id="815e5-113">下列程式碼範例會將陣列元素初始化為預設值 (除了不規則陣列外)。</span><span class="sxs-lookup"><span data-stu-id="815e5-113">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](../../../csharp/programming-guide/arrays/codesnippet/CSharp/multidimensional-arrays_8.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="815e5-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="815e5-114">See Also</span></span>  
 [<span data-ttu-id="815e5-115">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="815e5-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="815e5-116">陣列</span><span class="sxs-lookup"><span data-stu-id="815e5-116">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="815e5-117">一維陣列</span><span class="sxs-lookup"><span data-stu-id="815e5-117">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="815e5-118">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="815e5-118">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
