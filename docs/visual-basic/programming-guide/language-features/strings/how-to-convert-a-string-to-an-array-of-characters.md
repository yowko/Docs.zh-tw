---
title: 如何：將字串轉換為字元陣列
ms.date: 07/20/2015
helpviewer_keywords:
- character arrays [Visual Basic], converting strings
- arrays [Visual Basic], converting strings to
- examples [Visual Basic], string conversion
- strings [Visual Basic], converting to arrays
- string conversion [Visual Basic], arrays
ms.assetid: 1b54b686-ab29-413b-adce-6bd5422376eb
ms.openlocfilehash: d2f7128f97e576d37216d3aa9736921f13f77004
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352451"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a><span data-ttu-id="d6336-102">如何：在 Visual Basic 中將字串轉換為字元陣列</span><span class="sxs-lookup"><span data-stu-id="d6336-102">How to: Convert a String to an Array of Characters in Visual Basic</span></span>
<span data-ttu-id="d6336-103">有時候，您的字串中有字元的相關資料，以及字串內這些字元的位置，例如當您剖析字串時，會很有用。</span><span class="sxs-lookup"><span data-stu-id="d6336-103">Sometimes it is useful to have data about the characters in your string and the positions of those characters within your string, such as when you are parsing a string.</span></span> <span data-ttu-id="d6336-104">這個範例示範如何藉由呼叫字串的 <xref:System.String.ToCharArray%2A> 方法，來取得字串中的字元陣列。</span><span class="sxs-lookup"><span data-stu-id="d6336-104">This example shows how you can get an array of the characters in a string by calling the string's <xref:System.String.ToCharArray%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6336-105">範例</span><span class="sxs-lookup"><span data-stu-id="d6336-105">Example</span></span>  
 <span data-ttu-id="d6336-106">這個範例示範如何將字串分割成 `Char` 陣列，以及如何將字串分割成 Unicode 文字字元的 `String` 陣列。</span><span class="sxs-lookup"><span data-stu-id="d6336-106">This example demonstrates how to split a string into a `Char` array, and how to split a string into a `String` array of its Unicode text characters.</span></span> <span data-ttu-id="d6336-107">這項區別的原因是 Unicode 文字字元可以由兩個或多個 `Char` 字元組成（例如代理程式配對或結合字元序列）。</span><span class="sxs-lookup"><span data-stu-id="d6336-107">The reason for this distinction is that Unicode text characters can be composed of two or more `Char` characters (such as a surrogate pair or a combining character sequence).</span></span> <span data-ttu-id="d6336-108">如需詳細資訊，請參閱 <xref:System.Globalization.TextElementEnumerator> 和[Unicode 標準](https://www.unicode.org/standard/standard.html)。</span><span class="sxs-lookup"><span data-stu-id="d6336-108">For more information, see <xref:System.Globalization.TextElementEnumerator> and [The Unicode Standard](https://www.unicode.org/standard/standard.html).</span></span>  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a><span data-ttu-id="d6336-109">範例</span><span class="sxs-lookup"><span data-stu-id="d6336-109">Example</span></span>  
 <span data-ttu-id="d6336-110">比較難以將字串分割成 Unicode 文字字元，但如果您需要字串的視覺標記法的相關資訊，這就是必要的。</span><span class="sxs-lookup"><span data-stu-id="d6336-110">It is more difficult to split a string into its Unicode text characters, but this is necessary if you need information about the visual representation of a string.</span></span> <span data-ttu-id="d6336-111">這個範例會使用 <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> 方法來取得組成字串之 Unicode 文字字元的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="d6336-111">This example uses the <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> method to get information about the Unicode text characters that make up a string.</span></span>  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a><span data-ttu-id="d6336-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="d6336-112">See also</span></span>

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [<span data-ttu-id="d6336-113">如何：存取字串中的字元</span><span class="sxs-lookup"><span data-stu-id="d6336-113">How to: Access Characters in Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)
- [<span data-ttu-id="d6336-114">在 Visual Basic 中的字串和其他資料類型之間進行轉換</span><span class="sxs-lookup"><span data-stu-id="d6336-114">Converting Between Strings and Other Data Types in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [<span data-ttu-id="d6336-115">字串</span><span class="sxs-lookup"><span data-stu-id="d6336-115">Strings</span></span>](../../../../visual-basic/programming-guide/language-features/strings/index.md)
