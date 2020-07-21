---
title: 將陣列當做物件 - C# 程式設計手冊
description: 'C # 中的陣列是抽象基底類型陣列的物件。 您可以使用陣列的屬性和其他類別成員，例如 Length 屬性。'
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [C#], as objects
ms.assetid: f76d4403-bd0a-42a0-9bc8-694c55b2c926
ms.openlocfilehash: 984def3ef74b07d7099fae6cae6d6f8ce7e03e12
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474718"
---
# <a name="arrays-as-objects-c-programming-guide"></a><span data-ttu-id="3fc64-104">將陣列當做物件 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="3fc64-104">Arrays as Objects (C# Programming Guide)</span></span>

<span data-ttu-id="3fc64-105">在 C# 中，陣列其實是物件，不只是 C 和 C++ 中連續記憶體的可定址區域。</span><span class="sxs-lookup"><span data-stu-id="3fc64-105">In C#, arrays are actually objects, and not just addressable regions of contiguous memory as in C and C++.</span></span> <span data-ttu-id="3fc64-106"><xref:System.Array> 是所有陣列類型的抽象基底類型。</span><span class="sxs-lookup"><span data-stu-id="3fc64-106"><xref:System.Array> is the abstract base type of all array types.</span></span> <span data-ttu-id="3fc64-107">您可以使用具有的屬性和其他類別成員 <xref:System.Array> 。</span><span class="sxs-lookup"><span data-stu-id="3fc64-107">You can use the properties and other class members that <xref:System.Array> has.</span></span> <span data-ttu-id="3fc64-108">其中一個範例是使用 <xref:System.Array.Length%2A> 屬性來取得陣列的長度。</span><span class="sxs-lookup"><span data-stu-id="3fc64-108">An example of this is using the <xref:System.Array.Length%2A> property to get the length of an array.</span></span> <span data-ttu-id="3fc64-109">下列程式碼會將 `numbers` 陣列的長度 (也就是 `5`) 指派到名為 `lengthOfNumbers` 的變數：</span><span class="sxs-lookup"><span data-stu-id="3fc64-109">The following code assigns the length of the `numbers` array, which is `5`, to a variable called `lengthOfNumbers`:</span></span>

[!code-csharp[csProgGuideArrays#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#3)]

<span data-ttu-id="3fc64-110"><xref:System.Array> 類別會提供許多其他有用的方法和屬性以排序、搜尋和複製陣列。</span><span class="sxs-lookup"><span data-stu-id="3fc64-110">The <xref:System.Array> class provides many other useful methods and properties for sorting, searching, and copying arrays.</span></span>

## <a name="example"></a><span data-ttu-id="3fc64-111">範例</span><span class="sxs-lookup"><span data-stu-id="3fc64-111">Example</span></span>

<span data-ttu-id="3fc64-112">這個範例會使用 <xref:System.Array.Rank%2A> 屬性來顯示陣列的維度數目。</span><span class="sxs-lookup"><span data-stu-id="3fc64-112">This example uses the <xref:System.Array.Rank%2A> property to display the number of dimensions of an array.</span></span>

[!code-csharp[csProgGuideArrays#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideArrays/CS/Arrays.cs#2)]

## <a name="see-also"></a><span data-ttu-id="3fc64-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3fc64-113">See also</span></span>

- [<span data-ttu-id="3fc64-114">C # 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="3fc64-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3fc64-115">陣列</span><span class="sxs-lookup"><span data-stu-id="3fc64-115">Arrays</span></span>](./index.md)
- [<span data-ttu-id="3fc64-116">一維陣列</span><span class="sxs-lookup"><span data-stu-id="3fc64-116">Single-Dimensional Arrays</span></span>](./single-dimensional-arrays.md)
- [<span data-ttu-id="3fc64-117">多維陣列</span><span class="sxs-lookup"><span data-stu-id="3fc64-117">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="3fc64-118">不規則陣列</span><span class="sxs-lookup"><span data-stu-id="3fc64-118">Jagged Arrays</span></span>](./jagged-arrays.md)
