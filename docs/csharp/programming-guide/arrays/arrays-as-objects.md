---
title: 將陣列當做物件 (C# 程式設計手冊)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e29685af509009f42f38ba2dbf8524075e880ff9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="98818-102">將陣列當做物件 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="98818-102">Arrays as Objects (C# Programming Guide)</span></span>
<span data-ttu-id="98818-103">在 C# 中，陣列其實是物件，不只是 C 和 C++ 中連續記憶體的可定址區域。</span><span class="sxs-lookup"><span data-stu-id="98818-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="98818-104"><xref:System.Array> 是所有陣列類型的抽象基底類型。</span><span class="sxs-lookup"><span data-stu-id="98818-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="98818-105">您可以使用 <xref:System.Array> 擁有的屬性和其他類別成員。</span><span class="sxs-lookup"><span data-stu-id="98818-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="98818-106">此種範例會使用 <xref:System.Array.Length%2A> 屬性取得陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="98818-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="98818-107">下列程式碼會將 `numbers` 陣列的長度 (也就是 `5`) 指派到名為 `lengthOfNumbers` 的變數：</span><span class="sxs-lookup"><span data-stu-id="98818-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <span data-ttu-id="98818-108"><xref:System.Array> 類別會提供許多其他有用的方法和屬性以排序、搜尋和複製陣列。</span><span class="sxs-lookup"><span data-stu-id="98818-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="98818-109">範例</span><span class="sxs-lookup"><span data-stu-id="98818-109">Example</span></span>  
 <span data-ttu-id="98818-110">這個範例會使用 <xref:System.Array.Rank%2A> 屬性來顯示陣列的維度數目。</span><span class="sxs-lookup"><span data-stu-id="98818-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="98818-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98818-111">See Also</span></span>  
 [<span data-ttu-id="98818-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="98818-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="98818-113">陣列</span><span class="sxs-lookup"><span data-stu-id="98818-113">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="98818-114">一維陣列</span><span class="sxs-lookup"><span data-stu-id="98818-114">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
 [<span data-ttu-id="98818-115">多維陣列</span><span class="sxs-lookup"><span data-stu-id="98818-115">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
 [<span data-ttu-id="98818-116">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="98818-116">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
