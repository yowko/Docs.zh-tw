---
title: 將陣列當做物件 - C# 程式設計手冊
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: d8b929eccf9be259874d03dd93f49a49798bb349
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715096"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="fe50b-102">將陣列當做物件 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="fe50b-102">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="fe50b-103">在 C# 中，陣列其實是物件，不只是 C 和 C++ 中連續記憶體的可定址區域。</span><span class="sxs-lookup"><span data-stu-id="fe50b-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="fe50b-104"><xref:System.Array> 是所有陣列類型的抽象基底類型。</span><span class="sxs-lookup"><span data-stu-id="fe50b-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="fe50b-105">您可以使用<xref:System.Array>具有的屬性和其他類成員。</span><span class="sxs-lookup"><span data-stu-id="fe50b-105">You can use the properties and other class members that <xref:System.Array> has.</span></span> <span data-ttu-id="fe50b-106">例如，使用 屬性<xref:System.Array.Length%2A>獲取陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="fe50b-106">An example of this is using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="fe50b-107">下列程式碼會將 `numbers` 陣列的長度 (也就是 `5`) 指派到名為 `lengthOfNumbers` 的變數：</span><span class="sxs-lookup"><span data-stu-id="fe50b-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<span data-ttu-id="fe50b-108"><xref:System.Array> 類別會提供許多其他有用的方法和屬性以排序、搜尋和複製陣列。</span><span class="sxs-lookup"><span data-stu-id="fe50b-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>

## <a name="example"></a><span data-ttu-id="fe50b-109">範例</span><span class="sxs-lookup"><span data-stu-id="fe50b-109">Example</span></span>

<span data-ttu-id="fe50b-110">這個範例會使用 <xref:System.Array.Rank%2A> 屬性來顯示陣列的維度數目。</span><span class="sxs-lookup"><span data-stu-id="fe50b-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a><span data-ttu-id="fe50b-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fe50b-111">See also</span></span>

- [<span data-ttu-id="fe50b-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="fe50b-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="fe50b-113">陣 列</span><span class="sxs-lookup"><span data-stu-id="fe50b-113">Arrays</span></span>](./index.md)
- [<span data-ttu-id="fe50b-114">一維陣列</span><span class="sxs-lookup"><span data-stu-id="fe50b-114">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="fe50b-115">多維陣列</span><span class="sxs-lookup"><span data-stu-id="fe50b-115">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="fe50b-116">鋸齒狀陣列</span><span class="sxs-lookup"><span data-stu-id="fe50b-116">Jagged Arrays</span></span>](./jagged-arrays.md)
