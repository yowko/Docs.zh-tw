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
ms.openlocfilehash: c109143601e304b1ec15a60c71d65fe6bd15aae8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648615"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>如何：在 Visual Basic 中將字串轉換為字元陣列
有時候很有用的字元，在您的字串與您在字串內，例如當您在剖析字串的字元位置的資料。 此範例示範如何取得陣列的字元字串中藉由呼叫的字串<xref:System.String.ToCharArray%2A>方法。  
  
## <a name="example"></a>範例  
 這個範例示範如何分割字串成`Char`陣列，以及如何分割字串成`String`Unicode 文字字元的陣列。 此差異的原因是 Unicode 文字字元所組成兩個或多個`Char`字元 (例如 surrogate 字組或結合字元序列)。 如需詳細資訊，請參閱<xref:System.Globalization.TextElementEnumerator>和 「 Unicode 標準 「 http://www.unicode.org。  
  
 [!code-vb[VbVbalrStrings#75](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_1.vb)]  
  
## <a name="example"></a>範例  
 更難以將字串分隔為 Unicode 文字字元，但這是需要字串的視覺表示方式的相關資訊。 這個範例會使用<xref:System.Globalization.StringInfo.SubstringByTextElements%2A>方法來取得 Unicode 文字字元字串所組成的相關資訊。  
  
 [!code-vb[VbVbalrStrings#76](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/how-to-convert-a-string-to-an-array-of-characters_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.String.Chars%2A>  
 <xref:System.Globalization.StringInfo?displayProperty=nameWithType>  
 [如何：存取字串中的字元](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)  
 [在 Visual Basic 中的字串和其他資料類型之間進行轉換](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)  
 [字串](../../../../visual-basic/programming-guide/language-features/strings/index.md)
