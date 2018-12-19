---
title: 將陣列當做物件 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 0bbbf7ecc5eff650f7a2edc73546833afd2be094
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53242330"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="f4543-102">將陣列當做物件 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="f4543-102">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="f4543-103">在 C# 中，陣列其實是物件，不只是 C 和 C++ 中連續記憶體的可定址區域。</span><span class="sxs-lookup"><span data-stu-id="f4543-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="f4543-104"><xref:System.Array> 是所有陣列類型的抽象基底類型。</span><span class="sxs-lookup"><span data-stu-id="f4543-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="f4543-105">您可以使用 <xref:System.Array> 擁有的屬性和其他類別成員。</span><span class="sxs-lookup"><span data-stu-id="f4543-105">You can use the properties, and other class members, that <xref:System.Array> has.</span></span> <span data-ttu-id="f4543-106">此種範例會使用 <xref:System.Array.Length%2A> 屬性取得陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="f4543-106">An example of this would be using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="f4543-107">下列程式碼會將 `numbers` 陣列的長度 (也就是 `5`) 指派到名為 `lengthOfNumbers` 的變數：</span><span class="sxs-lookup"><span data-stu-id="f4543-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>  
  
 [!code-csharp[csProgGuideArrays#3](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_1.cs)]  
  
 <span data-ttu-id="f4543-108"><xref:System.Array> 類別會提供許多其他有用的方法和屬性以排序、搜尋和複製陣列。</span><span class="sxs-lookup"><span data-stu-id="f4543-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4543-109">範例</span><span class="sxs-lookup"><span data-stu-id="f4543-109">Example</span></span>

 <span data-ttu-id="f4543-110">這個範例會使用 <xref:System.Array.Rank%2A> 屬性來顯示陣列的維度數目。</span><span class="sxs-lookup"><span data-stu-id="f4543-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>  
  
 [!code-csharp[csProgGuideArrays#2](../../../csharp/programming-guide/arrays/codesnippet/CSharp/arrays-as-objects_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="f4543-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="f4543-111">See Also</span></span>

- [<span data-ttu-id="f4543-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="f4543-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="f4543-113">陣列</span><span class="sxs-lookup"><span data-stu-id="f4543-113">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="f4543-114">一維陣列</span><span class="sxs-lookup"><span data-stu-id="f4543-114">Single-Dimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/single-dimensional-arrays.md)  
- [<span data-ttu-id="f4543-115">多維陣列</span><span class="sxs-lookup"><span data-stu-id="f4543-115">Multidimensional Arrays</span></span>](../../../csharp/programming-guide/arrays/multidimensional-arrays.md)  
- [<span data-ttu-id="f4543-116">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="f4543-116">Jagged Arrays</span></span>](../../../csharp/programming-guide/arrays/jagged-arrays.md)
