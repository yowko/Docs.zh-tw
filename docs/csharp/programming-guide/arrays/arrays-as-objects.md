---
title: 將陣列當做物件 - C# 程式設計手冊
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 9905168662496c46d20f191c04f21d8630d02fa2
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2019
ms.locfileid: "72772115"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="c8b57-102">將陣列當做物件 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="c8b57-102">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="c8b57-103">在 C# 中，陣列其實是物件，不只是 C 和 C++ 中連續記憶體的可定址區域。</span><span class="sxs-lookup"><span data-stu-id="c8b57-103">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="c8b57-104"><xref:System.Array> 是所有陣列類型的抽象基底類型。</span><span class="sxs-lookup"><span data-stu-id="c8b57-104"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="c8b57-105">您可以使用 <xref:System.Array> 具有的屬性和其他類別成員。</span><span class="sxs-lookup"><span data-stu-id="c8b57-105">You can use the properties and other class members that <xref:System.Array> has.</span></span> <span data-ttu-id="c8b57-106">其中一個範例是使用 <xref:System.Array.Length%2A> 屬性來取得陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="c8b57-106">An example of this is using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="c8b57-107">下列程式碼會將 `numbers` 陣列的長度 (也就是 `5`) 指派到名為 `lengthOfNumbers` 的變數：</span><span class="sxs-lookup"><span data-stu-id="c8b57-107">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<span data-ttu-id="c8b57-108"><xref:System.Array> 類別會提供許多其他有用的方法和屬性以排序、搜尋和複製陣列。</span><span class="sxs-lookup"><span data-stu-id="c8b57-108">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>

## <a name="example"></a><span data-ttu-id="c8b57-109">範例</span><span class="sxs-lookup"><span data-stu-id="c8b57-109">Example</span></span>

<span data-ttu-id="c8b57-110">這個範例會使用 <xref:System.Array.Rank%2A> 屬性來顯示陣列的維度數目。</span><span class="sxs-lookup"><span data-stu-id="c8b57-110">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a><span data-ttu-id="c8b57-111">請參閱</span><span class="sxs-lookup"><span data-stu-id="c8b57-111">See also</span></span>

- [<span data-ttu-id="c8b57-112">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="c8b57-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c8b57-113">陣列</span><span class="sxs-lookup"><span data-stu-id="c8b57-113">Arrays</span></span>](./index.md)
- [<span data-ttu-id="c8b57-114">一維陣列</span><span class="sxs-lookup"><span data-stu-id="c8b57-114">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="c8b57-115">多維陣列</span><span class="sxs-lookup"><span data-stu-id="c8b57-115">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="c8b57-116">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="c8b57-116">Jagged Arrays</span></span>](./jagged-arrays.md)
