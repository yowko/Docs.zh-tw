---
title: "如何：串連多個字串 (C# 程式設計手冊)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
caps.latest.revision: "21"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ca240523e2483289e11433fd58d9630a31721b33
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-concatenate-multiple-strings-c-programming-guide"></a><span data-ttu-id="bbe4f-102">如何：串連多個字串 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="bbe4f-102">How to: Concatenate Multiple Strings (C# Programming Guide)</span></span>
<span data-ttu-id="bbe4f-103">「串連」是將一個字串附加至另一個字串結尾的程序。</span><span class="sxs-lookup"><span data-stu-id="bbe4f-103">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="bbe4f-104">當您使用 `+` 運算子串連字串常值或字串常數時，編譯器會建立單一字串。</span><span class="sxs-lookup"><span data-stu-id="bbe4f-104">When you concatenate string literals or string constants by using the `+` operator, the compiler creates a single string.</span></span> <span data-ttu-id="bbe4f-105">不會發生執行階段串連。</span><span class="sxs-lookup"><span data-stu-id="bbe4f-105">No run time concatenation occurs.</span></span> <span data-ttu-id="bbe4f-106">不過，字串變數只會在執行階段串連。</span><span class="sxs-lookup"><span data-stu-id="bbe4f-106">However, string variables can be concatenated only at run time.</span></span> <span data-ttu-id="bbe4f-107">這種情況下，您應該了解各種方法的效能含意。</span><span class="sxs-lookup"><span data-stu-id="bbe4f-107">In this case, you should understand the performance implications of the various approaches.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbe4f-108">範例</span><span class="sxs-lookup"><span data-stu-id="bbe4f-108">Example</span></span>  
 <span data-ttu-id="bbe4f-109">下例示範如何將長字串常值分割成較小的字串，以改善原始程式碼的可讀性。</span><span class="sxs-lookup"><span data-stu-id="bbe4f-109">The following example shows how to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="bbe4f-110">這些組件在編譯時期會串連成單一字串。</span><span class="sxs-lookup"><span data-stu-id="bbe4f-110">These parts will be concatenated into a single string at compile time.</span></span> <span data-ttu-id="bbe4f-111">不論涉及多少字串，都沒有執行階段效能成本。</span><span class="sxs-lookup"><span data-stu-id="bbe4f-111">There is no run time performance cost regardless of the number of strings involved.</span></span>  
  
 [!code-csharp[csProgGuideStrings#30](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="bbe4f-112">範例</span><span class="sxs-lookup"><span data-stu-id="bbe4f-112">Example</span></span>  
 <span data-ttu-id="bbe4f-113">若要串連字串變數，您可以使用 `+` 或 `+=` 運算子，或使用 <xref:System.String.Concat%2A?displayProperty=nameWithType>、<xref:System.String.Format%2A?displayProperty=nameWithType> 或 <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="bbe4f-113">To concatenate string variables, you can use the `+` or `+=` operators, or the <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Format%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="bbe4f-114">`+` 運算子簡單易用，且容易建立直覺化程式碼。</span><span class="sxs-lookup"><span data-stu-id="bbe4f-114">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="bbe4f-115">即使一個陳述式使用數個 + 運算子，字串內容也只會複製一次。</span><span class="sxs-lookup"><span data-stu-id="bbe4f-115">Even if you use several + operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="bbe4f-116">但若是多次重複這項作業，例如在迴圈中，可能會造成效率問題。</span><span class="sxs-lookup"><span data-stu-id="bbe4f-116">But if you repeat this operation multiple times, for example in a loop, it might cause efficiency problems.</span></span> <span data-ttu-id="bbe4f-117">例如，請注意下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="bbe4f-117">For example, note the following code:</span></span>  
  
 [!code-csharp[csProgGuideStrings#23](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_2.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="bbe4f-118">在字串串連作業中，C# 編譯器會將 null 字串視同空字串，但不會轉換原始的 null 字串值。</span><span class="sxs-lookup"><span data-stu-id="bbe4f-118">In string concatenation operations, the C# compiler treats a null string the same as an empty string, but it does not convert the value of the original null string.</span></span>  
  
 <span data-ttu-id="bbe4f-119">如果不串連大量的字串 (例如，在迴圈中)，這段程式碼的效能成本可能就不那麼明顯。</span><span class="sxs-lookup"><span data-stu-id="bbe4f-119">If you are not concatenating large numbers of strings (for example, in a loop), the performance cost of this code is probably not significant.</span></span> <span data-ttu-id="bbe4f-120"><xref:System.String.Concat%2A?displayProperty=nameWithType> 和 <xref:System.String.Format%2A?displayProperty=nameWithType> 方法也同樣如此。</span><span class="sxs-lookup"><span data-stu-id="bbe4f-120">The same is true for the <xref:System.String.Concat%2A?displayProperty=nameWithType> and <xref:System.String.Format%2A?displayProperty=nameWithType> methods.</span></span>  
  
 <span data-ttu-id="bbe4f-121">不過，當效能很重要時，您應該一律使用 <xref:System.Text.StringBuilder> 類別來串連字串。</span><span class="sxs-lookup"><span data-stu-id="bbe4f-121">However, when performance is important, you should always use the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span> <span data-ttu-id="bbe4f-122">下列程式碼會使用 <xref:System.Text.StringBuilder> 類別的 <xref:System.Text.StringBuilder.Append%2A> 方法來串連字串，沒有 `+` 運算子的鏈結效果。</span><span class="sxs-lookup"><span data-stu-id="bbe4f-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings without the chaining effect of the `+` operator.</span></span>  
  
 [!code-csharp[csProgGuideStrings#22](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-concatenate-multiple-strings_3.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="bbe4f-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbe4f-123">See Also</span></span>  
 <xref:System.String>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="bbe4f-124">C# 程式設計指南</span><span class="sxs-lookup"><span data-stu-id="bbe4f-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bbe4f-125">字串</span><span class="sxs-lookup"><span data-stu-id="bbe4f-125">Strings</span></span>](../../../csharp/programming-guide/strings/index.md)
