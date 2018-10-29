---
title: 如何：在 Visual Basic 中將字串轉換為字元陣列
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: cc12b70cddcb93a72b4421a8ddd93542ef84f55b
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/29/2018
ms.locfileid: "50202758"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="8b675-102">如何：在 Visual Basic 中將字串轉換為字元陣列</span><span class="sxs-lookup"><span data-stu-id="8b675-102">How to: Convert a String to an Array of Characters in Visual Basic</span></span>
<span data-ttu-id="8b675-103">有時候最好擁有您的字串與您的字串，例如當您在剖析字串內的這些字元的位置中的字元資料。</span><span class="sxs-lookup"><span data-stu-id="8b675-103">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="8b675-104">此範例示範如何呼叫字串的字串中取得的字元陣列<xref:System.String.ToCharArray%2A>方法。</span><span class="sxs-lookup"><span data-stu-id="8b675-104">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8b675-105">範例</span><span class="sxs-lookup"><span data-stu-id="8b675-105">Example</span></span>  
 <span data-ttu-id="8b675-106">此範例示範如何分割成字串`Char`陣列，以及如何分割成字串`String`Unicode 文字字元的陣列。</span><span class="sxs-lookup"><span data-stu-id="8b675-106">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="8b675-107">這項區別的原因是 Unicode 文字字元所組成兩個或多個`Char`字元 (例如，surrogate 字組或組合字元順序)。</span><span class="sxs-lookup"><span data-stu-id="8b675-107">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="8b675-108">如需詳細資訊，請參閱 <<c0> <xref:System.Globalization.TextElementEnumerator> 並[Unicode 標準](https://www.unicode.org/standard/standard.html)。</span><span class="sxs-lookup"><span data-stu-id="8b675-108">For more information, see <xref:System.Globalization.TextElementEnumerator> and [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="8b675-109">範例</span><span class="sxs-lookup"><span data-stu-id="8b675-109">Example</span></span>  
 <span data-ttu-id="8b675-110">它很難將字串分割成其 Unicode 文字字元，但這是需要字串的視覺表示方式的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8b675-110">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="8b675-111">這個範例會使用<xref:System.Globalization.StringInfo.SubstringByTextElements%2A>方法，以取得字串所組成的 Unicode 文字字元的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="8b675-111">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="8b675-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8b675-112">See Also</span></span>  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [<span data-ttu-id="8b675-113">如何：存取字串中的字元</span><span class="sxs-lookup"><span data-stu-id="8b675-113">How to: Access Characters in Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [<span data-ttu-id="8b675-114">在 Visual Basic 中的字串和其他資料類型之間進行轉換</span><span class="sxs-lookup"><span data-stu-id="8b675-114">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [<span data-ttu-id="8b675-115">字串</span><span class="sxs-lookup"><span data-stu-id="8b675-115">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
