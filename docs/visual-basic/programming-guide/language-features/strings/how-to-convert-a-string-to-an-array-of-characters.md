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
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845186"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>如何：在 Visual Basic 中將字串轉換為字元陣列
有時候最好擁有您的字串與您的字串，例如當您在剖析字串內的這些字元的位置中的字元資料。 此範例示範如何呼叫字串的字串中取得的字元陣列<xref:System.String.ToCharArray%2A>方法。  
  
## <a name="example"></a>範例  
 此範例示範如何分割成字串`Char`陣列，以及如何分割成字串`String`Unicode 文字字元的陣列。 這項區別的原因是 Unicode 文字字元所組成兩個或多個`Char`字元 (例如，surrogate 字組或組合字元順序)。 如需詳細資訊，請參閱 <<c0> <xref:System.Globalization.TextElementEnumerator> 並[Unicode 標準](https://www.unicode.org/standard/standard.html)。  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a>範例  
 它很難將字串分割成其 Unicode 文字字元，但這是需要字串的視覺表示方式的相關資訊。 這個範例會使用<xref:System.Globalization.StringInfo.SubstringByTextElements%2A>方法，以取得字串所組成的 Unicode 文字字元的相關資訊。  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [如何：存取字串中的字元](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [在 Visual Basic 中的字串和其他資料類型之間進行轉換](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [字串](../../../../visual-basic/programming-guide/language-features/strings/index.md)
