---
title: 將陣列當做物件 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 8500cf508b77a0fa7e348ce0fe6b1f16fd2bab25
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56977162"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="3f1fa-102">將陣列當做物件 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="3f1fa-102">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="3f1fa-103">在 C# 中，陣列其實是物件，不只是 C 和 C++ 中連續記憶體的可定址區域。</span><span class="sxs-lookup"><span data-stu-id="3f1fa-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="3f1fa-104"><xref:System.Array> 是所有陣列類型的抽象基底類型。</span><span class="sxs-lookup"><span data-stu-id="3f1fa-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="3f1fa-105">您可以使用 <xref:System.Array> 擁有的屬性和其他類別成員。</span><span class="sxs-lookup"><span data-stu-id="3f1fa-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="3f1fa-106">此種範例會使用 <xref:System.Array.Length%2A> 屬性取得陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="3f1fa-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="3f1fa-107">下列程式碼會將 `numbers` 陣列的長度 (也就是 `5`) 指派到名為 `lengthOfNumbers` 的變數：</span><span class="sxs-lookup"><span data-stu-id="3f1fa-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 [!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]  
  
 <span data-ttu-id="3f1fa-108"><xref:System.Array> 類別會提供許多其他有用的方法和屬性以排序、搜尋和複製陣列。</span><span class="sxs-lookup"><span data-stu-id="3f1fa-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f1fa-109">範例</span><span class="sxs-lookup"><span data-stu-id="3f1fa-109">Example</span></span>

 <span data-ttu-id="3f1fa-110">這個範例會使用 <xref:System.Array.Rank%2A> 屬性來顯示陣列的維度數目。</span><span class="sxs-lookup"><span data-stu-id="3f1fa-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]  
  
## <a name="see-also"></a><span data-ttu-id="3f1fa-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3f1fa-111">See also</span></span>

- [<span data-ttu-id="3f1fa-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3f1fa-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="3f1fa-113">陣列</span><span class="sxs-lookup"><span data-stu-id="3f1fa-113">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)
- [<span data-ttu-id="3f1fa-114">一維陣列</span><span class="sxs-lookup"><span data-stu-id="3f1fa-114">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)
- [<span data-ttu-id="3f1fa-115">多維陣列</span><span class="sxs-lookup"><span data-stu-id="3f1fa-115">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)
- [<span data-ttu-id="3f1fa-116">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="3f1fa-116">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
