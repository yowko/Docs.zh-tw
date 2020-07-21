---
title: 多維陣列 - C# 程式設計手冊
description: 'C # 中的陣列可以有一個以上的維度。 這個範例宣告會建立四個數據列和兩個數據行的二維陣列。'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], multidimensional
- multidimensional arrays [C#]
ms.assetid: 020ce02e-7dff-4273-8e53-bf0b33747232
ms.openlocfilehash: a2f204c0866672b317569fbc620aa8af60829ffd
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86475004"
---
# <a name="multidimensional-arrays-c-programming-guide"></a><span data-ttu-id="353e5-104">多維陣列 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="353e5-104">Multidimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="353e5-105">陣列可以有多個維度。</span><span class="sxs-lookup"><span data-stu-id="353e5-105">Arrays can have more than one dimension.</span></span> <span data-ttu-id="353e5-106">例如，下列宣告會建立具有四個資料列和兩個資料行的二維陣列。</span><span class="sxs-lookup"><span data-stu-id="353e5-106">For example, the following declaration creates a two-dimensional array of four rows and two columns.</span></span>  
  
 [!code-csharp[csProgGuideArrays#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#11)]  
  
 <span data-ttu-id="353e5-107">下列宣告會建立三維 (4、2 和 3) 陣列。</span><span class="sxs-lookup"><span data-stu-id="353e5-107">The following declaration creates an array of three dimensions, 4, 2, and 3.</span></span>  
  
 [!code-csharp[csProgGuideArrays#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#12)]  
  
## <a name="array-initialization"></a><span data-ttu-id="353e5-108">陣列初始化</span><span class="sxs-lookup"><span data-stu-id="353e5-108">Array Initialization</span></span>

 <span data-ttu-id="353e5-109">您可以在宣告後初始化陣列，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="353e5-109">You can initialize the array upon declaration, as is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#13)]  
  
 <span data-ttu-id="353e5-110">您也可以在不指定順位的情況下初始化陣列。</span><span class="sxs-lookup"><span data-stu-id="353e5-110">You can also initialize the array without specifying the rank.</span></span>  
  
 [!code-csharp[csProgGuideArrays#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#14)]  
  
 <span data-ttu-id="353e5-111">如果選擇在不進行初始化的情況下宣告變數，則必須使用 `new` 運算子將陣列指派給變數。</span><span class="sxs-lookup"><span data-stu-id="353e5-111">If you choose to declare an array variable without initialization, you must use the `new` operator to assign an array to the variable.</span></span> <span data-ttu-id="353e5-112">下列範例會顯示 `new` 的用法。</span><span class="sxs-lookup"><span data-stu-id="353e5-112">The use of `new` is shown in the following example.</span></span>  
  
 [!code-csharp[csProgGuideArrays#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#15)]  
  
 <span data-ttu-id="353e5-113">下列範例會將值指派給特定的陣列元素。</span><span class="sxs-lookup"><span data-stu-id="353e5-113">The following example assigns a value to a particular array element.</span></span>  
  
 [!code-csharp[csProgGuideArrays#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#16)]  
  
 <span data-ttu-id="353e5-114">同樣地，下列範例會取得特定陣列元素的值，並將它指派給 `elementValue` 變數。</span><span class="sxs-lookup"><span data-stu-id="353e5-114">Similarly, the following example gets the value of a particular array element and assigns it to variable `elementValue`.</span></span>  
  
 [!code-csharp[csProgGuideArrays#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#42)]  
  
 <span data-ttu-id="353e5-115">下列程式碼範例會將陣列元素初始化為預設值 (除了不規則陣列外)。</span><span class="sxs-lookup"><span data-stu-id="353e5-115">The following code example initializes the array elements to default values (except for jagged arrays).</span></span>  
  
 [!code-csharp[csProgGuideArrays#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#17)]  
  
## <a name="see-also"></a><span data-ttu-id="353e5-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="353e5-116">See also</span></span>

- [<span data-ttu-id="353e5-117">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="353e5-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="353e5-118">陣列</span><span class="sxs-lookup"><span data-stu-id="353e5-118">Arrays</span></span>](./index.md)
- [<span data-ttu-id="353e5-119">一維陣列</span><span class="sxs-lookup"><span data-stu-id="353e5-119">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="353e5-120">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="353e5-120">Jagged Arrays</span></span>](./jagged-arrays.md)
