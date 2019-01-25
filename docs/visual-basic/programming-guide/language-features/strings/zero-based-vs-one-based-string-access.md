---
title: 以零為起始的 vs。在 Visual Basic 中的其中一個基礎字串存取
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: d4b2f73f8955b103e70e240e714e2b31d6198438
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54535526"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="e4a43-102">以零為起始的 vs。在 Visual Basic 中的其中一個基礎字串存取</span><span class="sxs-lookup"><span data-stu-id="e4a43-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="e4a43-103">本主題會比較如何 Visual Basic 和[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]提供字串中字元的權限。</span><span class="sxs-lookup"><span data-stu-id="e4a43-103">This topic compares how Visual Basic and the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] provide access to the characters in a string.</span></span> <span data-ttu-id="e4a43-104">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]一律提供之以零起始的存取權的字元在字串中，而 Visual Basic 提供的以零為起始與以一為基的存取，視函數而定。</span><span class="sxs-lookup"><span data-stu-id="e4a43-104">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="e4a43-105">以一為</span><span class="sxs-lookup"><span data-stu-id="e4a43-105">One-Based</span></span>  
 <span data-ttu-id="e4a43-106">如需以一為基的 Visual Basic 函式的範例，請考慮`Mid`函式。</span><span class="sxs-lookup"><span data-stu-id="e4a43-106">For an example of a one-based Visual Basic function, consider the `Mid` function.</span></span> <span data-ttu-id="e4a43-107">它會指出子字串將會開始，從位置 1 開始的字元位置的引數。</span><span class="sxs-lookup"><span data-stu-id="e4a43-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="e4a43-108">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType>方法採用索引之字元的子字串開始，已在字串中從開始位置 0。</span><span class="sxs-lookup"><span data-stu-id="e4a43-108">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="e4a43-109">因此，如果您有一個字串"ABCDE"時，個別字元的編號搭配 id:1,2,3,4,5`Mid`函式，但搭配 0,1,2,3,4<xref:System.String.Substring%2A?displayProperty=nameWithType>方法。</span><span class="sxs-lookup"><span data-stu-id="e4a43-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="e4a43-110">以零為起始</span><span class="sxs-lookup"><span data-stu-id="e4a43-110">Zero-Based</span></span>  
 <span data-ttu-id="e4a43-111">如需以零為起始的 Visual Basic 函式的範例，請考慮`Split`函式。</span><span class="sxs-lookup"><span data-stu-id="e4a43-111">For an example of a zero-based Visual Basic function, consider the `Split` function.</span></span> <span data-ttu-id="e4a43-112">它會將字串分割，並傳回陣列，包含子字串。</span><span class="sxs-lookup"><span data-stu-id="e4a43-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="e4a43-113">[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType>方法也會將字串分割，並傳回陣列，包含子字串。</span><span class="sxs-lookup"><span data-stu-id="e4a43-113">The [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="e4a43-114">因為`Split`函式與<xref:System.String.Split%2A>方法會傳回[!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]它們必須是以零為起始的陣列、 物。</span><span class="sxs-lookup"><span data-stu-id="e4a43-114">Because the `Split` function and <xref:System.String.Split%2A> method return [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4a43-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4a43-115">See also</span></span>
- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [<span data-ttu-id="e4a43-116">Visual Basic 中的字串簡介</span><span class="sxs-lookup"><span data-stu-id="e4a43-116">Introduction to Strings in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
