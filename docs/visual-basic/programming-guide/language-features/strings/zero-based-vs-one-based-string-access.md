---
title: "以零為起始的 vs。在 Visual Basic 中的以一為字串存取 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: d8d1000f134fa8f99509d12727b9fbd84cb0e831
ms.contentlocale: zh-tw
ms.lasthandoff: 04/12/2017

---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="5bf19-102">以零為起始的 vs。在 Visual Basic 中以一為字串存取</span><span class="sxs-lookup"><span data-stu-id="5bf19-102">Zero-based vs. One-based String Access in Visual Basic</span></span>
<span data-ttu-id="5bf19-103">這個主題會比較如何[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]和[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]提供存取權的字串中的字元。</span><span class="sxs-lookup"><span data-stu-id="5bf19-103">This topic compares how [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] and the [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] provide access to the characters in a string.</span></span> <span data-ttu-id="5bf19-104">[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]一律會提供以零為起始的字元在字串中，存取而[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]提供以零為起始及一為基礎的存取，根據的函式。</span><span class="sxs-lookup"><span data-stu-id="5bf19-104">The [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] always provides zero-based access to the characters in a string, whereas [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="5bf19-105">以一為</span><span class="sxs-lookup"><span data-stu-id="5bf19-105">One-Based</span></span>  
 <span data-ttu-id="5bf19-106">如需範例的其中一個基礎[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]函式，請考慮`Mid`函式。</span><span class="sxs-lookup"><span data-stu-id="5bf19-106">For an example of a one-based [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] function, consider the `Mid` function.</span></span> <span data-ttu-id="5bf19-107">它會指出子字串開始，從位置 1 開始的字元位置的引數。</span><span class="sxs-lookup"><span data-stu-id="5bf19-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="5bf19-108">[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.String.Substring%2A?displayProperty=fullName>方法接受之字元的索引開始，將子字串在的字串中開始位置 0。</xref:System.String.Substring%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="5bf19-108">The [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.String.Substring%2A?displayProperty=fullName> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="5bf19-109">因此，如果您有字串"ABCDE"，個別字元的編號搭配 1,2,3,4,5`Mid`函式，但搭配 0,1,2,3,4<xref:System.String.Substring%2A?displayProperty=fullName>方法。</xref:System.String.Substring%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="5bf19-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=fullName> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="5bf19-110">以零為起始</span><span class="sxs-lookup"><span data-stu-id="5bf19-110">Zero-Based</span></span>  
 <span data-ttu-id="5bf19-111">如需範例，以零為起始的[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]函式，請考慮`Split`函式。</span><span class="sxs-lookup"><span data-stu-id="5bf19-111">For an example of a zero-based [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] function, consider the `Split` function.</span></span> <span data-ttu-id="5bf19-112">分隔字串，並傳回陣列，包含子字串。</span><span class="sxs-lookup"><span data-stu-id="5bf19-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="5bf19-113">[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.String.Split%2A?displayProperty=fullName>方法也會將字串分割，並傳回陣列，包含子字串。</xref:System.String.Split%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="5bf19-113">The [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] <xref:System.String.Split%2A?displayProperty=fullName> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="5bf19-114">因為`Split`函式和<xref:System.String.Split%2A>方法會傳回[!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)]的陣列，它們必須是以零為起始。</xref:System.String.Split%2A></span><span class="sxs-lookup"><span data-stu-id="5bf19-114">Because the `Split` function and <xref:System.String.Split%2A> method return [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bf19-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5bf19-115">See Also</span></span>  
 <span data-ttu-id="5bf19-116"><xref:Microsoft.VisualBasic.Strings.Mid%2A></xref:Microsoft.VisualBasic.Strings.Mid%2A></span><span class="sxs-lookup"><span data-stu-id="5bf19-116"><xref:Microsoft.VisualBasic.Strings.Mid%2A></span></span>   
 <span data-ttu-id="5bf19-117"><xref:Microsoft.VisualBasic.Strings.Split%2A></xref:Microsoft.VisualBasic.Strings.Split%2A></span><span class="sxs-lookup"><span data-stu-id="5bf19-117"><xref:Microsoft.VisualBasic.Strings.Split%2A></span></span>   
 <span data-ttu-id="5bf19-118"><xref:System.String.Substring%2A></xref:System.String.Substring%2A></span><span class="sxs-lookup"><span data-stu-id="5bf19-118"><xref:System.String.Substring%2A></span></span>   
 <span data-ttu-id="5bf19-119"><xref:System.String.Split%2A></xref:System.String.Split%2A></span><span class="sxs-lookup"><span data-stu-id="5bf19-119"><xref:System.String.Split%2A></span></span>   
<span data-ttu-id="5bf19-120"> [在 Visual Basic 中的字串簡介](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)</span><span class="sxs-lookup"><span data-stu-id="5bf19-120"> [Introduction to Strings in Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)</span></span>
