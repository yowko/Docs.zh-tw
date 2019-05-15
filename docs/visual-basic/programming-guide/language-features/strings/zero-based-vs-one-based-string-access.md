---
title: 以零為起始與在 Visual Basic 中的其中一個基礎字串存取
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: cc8f286de41d7e44225e889e73ff3c7b1fdbd881
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591743"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="c2344-102">以零為起始與在 Visual Basic 中的其中一個基礎字串存取</span><span class="sxs-lookup"><span data-stu-id="c2344-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="c2344-103">本主題會比較 Visual Basic 和.NET Framework 提供字串中字元的權限。</span><span class="sxs-lookup"><span data-stu-id="c2344-103">This topic compares how Visual Basic and the .NET Framework provide access to the characters in a string.</span></span> <span data-ttu-id="c2344-104">.NET Framework 一律會提供以零為起始的存取權的字元在字串中，而 Visual Basic 提供的以零為起始與以一為基的存取，視函數而定。</span><span class="sxs-lookup"><span data-stu-id="c2344-104">The .NET Framework always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="c2344-105">以一為</span><span class="sxs-lookup"><span data-stu-id="c2344-105">One-Based</span></span>  
 <span data-ttu-id="c2344-106">如需以一為基的 Visual Basic 函式的範例，請考慮`Mid`函式。</span><span class="sxs-lookup"><span data-stu-id="c2344-106">For an example of a one-based Visual Basic function, consider the `Mid` function.</span></span> <span data-ttu-id="c2344-107">它會指出子字串將會開始，從位置 1 開始的字元位置的引數。</span><span class="sxs-lookup"><span data-stu-id="c2344-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="c2344-108">.NET Framework<xref:System.String.Substring%2A?displayProperty=nameWithType>方法採用索引之字元的子字串開始，已在字串中從開始位置 0。</span><span class="sxs-lookup"><span data-stu-id="c2344-108">The .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="c2344-109">因此，如果您有一個字串"ABCDE"時，個別字元的編號搭配 id:1,2,3,4,5`Mid`函式，但搭配 0,1,2,3,4<xref:System.String.Substring%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="c2344-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="c2344-110">以零為起始</span><span class="sxs-lookup"><span data-stu-id="c2344-110">Zero-Based</span></span>  
 <span data-ttu-id="c2344-111">如需以零為起始的 Visual Basic 函式的範例，請考慮`Split`函式。</span><span class="sxs-lookup"><span data-stu-id="c2344-111">For an example of a zero-based Visual Basic function, consider the `Split` function.</span></span> <span data-ttu-id="c2344-112">它會將字串分割，並傳回陣列，包含子字串。</span><span class="sxs-lookup"><span data-stu-id="c2344-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="c2344-113">.NET Framework<xref:System.String.Split%2A?displayProperty=nameWithType>方法也會將字串分割，並傳回陣列，包含子字串。</span><span class="sxs-lookup"><span data-stu-id="c2344-113">The .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="c2344-114">因為`Split`函式和<xref:System.String.Split%2A>方法傳回.NET Framework 的陣列，它們必須是以零為起始。</span><span class="sxs-lookup"><span data-stu-id="c2344-114">Because the `Split` function and <xref:System.String.Split%2A> method return .NET Framework arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2344-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2344-115">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [<span data-ttu-id="c2344-116">Visual Basic 中的字串簡介</span><span class="sxs-lookup"><span data-stu-id="c2344-116">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
