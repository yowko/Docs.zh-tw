---
title: 以零為基底的與以一為基底的字串存取
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], indexing
ms.assetid: 0ed39f35-d68e-421d-ae14-460a5c0373b8
ms.openlocfilehash: 91d3fb9d7bfdf3d5af27fc6499583640946a802f
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072284"
---
# <a name="zero-based-vs-one-based-string-access-in-visual-basic"></a><span data-ttu-id="5fedf-102">Visual Basic 中以零起始與以一起始的字串存取之比較</span><span class="sxs-lookup"><span data-stu-id="5fedf-102">Zero-based vs. One-based String Access in Visual Basic</span></span>

<span data-ttu-id="5fedf-103">本主題將比較 Visual Basic 和 .NET Framework 如何提供字串中字元的存取權。</span><span class="sxs-lookup"><span data-stu-id="5fedf-103">This topic compares how Visual Basic and the .NET Framework provide access to the characters in a string.</span></span> <span data-ttu-id="5fedf-104">.NET Framework 一律以零為基底的方式存取字串中的字元，而 Visual Basic 提供以零為基礎和以一為基礎的存取，視函式而定。</span><span class="sxs-lookup"><span data-stu-id="5fedf-104">The .NET Framework always provides zero-based access to the characters in a string, whereas Visual Basic provides zero-based and one-based access, depending on the function.</span></span>  
  
## <a name="one-based"></a><span data-ttu-id="5fedf-105">以一為基礎</span><span class="sxs-lookup"><span data-stu-id="5fedf-105">One-Based</span></span>  

 <span data-ttu-id="5fedf-106">如需以一個為基礎 Visual Basic 函式的範例，請考慮函式 `Mid` 。</span><span class="sxs-lookup"><span data-stu-id="5fedf-106">For an example of a one-based Visual Basic function, consider the `Mid` function.</span></span> <span data-ttu-id="5fedf-107">它會採用引數，指出子字串開始的字元位置，從位置1開始。</span><span class="sxs-lookup"><span data-stu-id="5fedf-107">It takes an argument that indicates the character position at which the substring will start, starting with position 1.</span></span> <span data-ttu-id="5fedf-108">.NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> 方法會使用字串中要開始子字串的字元索引，從位置0開始。</span><span class="sxs-lookup"><span data-stu-id="5fedf-108">The .NET Framework <xref:System.String.Substring%2A?displayProperty=nameWithType> method takes an index of the character in the string at which the substring is to start, starting with position 0.</span></span> <span data-ttu-id="5fedf-109">因此，如果您的字串為 "ABCDE"，則個別字元的編號為1、2、3、4、5，以與函式搭配使用 `Mid` ，但是0，1，2，3，4則用於 <xref:System.String.Substring%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="5fedf-109">Thus, if you have a string "ABCDE", the individual characters are numbered 1,2,3,4,5 for use with the `Mid` function, but 0,1,2,3,4 for use with the <xref:System.String.Substring%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="zero-based"></a><span data-ttu-id="5fedf-110">以零為基底</span><span class="sxs-lookup"><span data-stu-id="5fedf-110">Zero-Based</span></span>  

 <span data-ttu-id="5fedf-111">如需以零為基底的 Visual Basic 函式的範例，請考慮使用 `Split` 函數。</span><span class="sxs-lookup"><span data-stu-id="5fedf-111">For an example of a zero-based Visual Basic function, consider the `Split` function.</span></span> <span data-ttu-id="5fedf-112">它會分割字串，並傳回包含子字串的陣列。</span><span class="sxs-lookup"><span data-stu-id="5fedf-112">It splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="5fedf-113">.NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> 方法也會分割字串，並傳回包含子字串的陣列。</span><span class="sxs-lookup"><span data-stu-id="5fedf-113">The .NET Framework <xref:System.String.Split%2A?displayProperty=nameWithType> method also splits a string and returns an array containing the substrings.</span></span> <span data-ttu-id="5fedf-114">因為函式 `Split` 和 <xref:System.String.Split%2A> 方法會傳回 .NET Framework 陣列，所以它們必須以零為基底。</span><span class="sxs-lookup"><span data-stu-id="5fedf-114">Because the `Split` function and <xref:System.String.Split%2A> method return .NET Framework arrays, they must be zero-based.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fedf-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5fedf-115">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Mid%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:System.String.Substring%2A>
- <xref:System.String.Split%2A>
- [<span data-ttu-id="5fedf-116">Visual Basic 中的字串簡介</span><span class="sxs-lookup"><span data-stu-id="5fedf-116">Introduction to Strings in Visual Basic</span></span>](introduction-to-strings.md)
