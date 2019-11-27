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
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>如何：在 Visual Basic 中將字串轉換為字元陣列
有時候，您的字串中有字元的相關資料，以及字串內這些字元的位置，例如當您剖析字串時，會很有用。 這個範例示範如何藉由呼叫字串的 <xref:System.String.ToCharArray%2A> 方法，來取得字串中的字元陣列。  
  
## <a name="example"></a>範例  
 這個範例示範如何將字串分割成 `Char` 陣列，以及如何將字串分割成 Unicode 文字字元的 `String` 陣列。 這項區別的原因是 Unicode 文字字元可以由兩個或多個 `Char` 字元組成（例如代理程式配對或結合字元序列）。 如需詳細資訊，請參閱 <xref:System.Globalization.TextElementEnumerator> 和[Unicode 標準](https://www.unicode.org/standard/standard.html)。  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a>範例  
 比較難以將字串分割成 Unicode 文字字元，但如果您需要字串的視覺標記法的相關資訊，這就是必要的。 這個範例會使用 <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> 方法來取得組成字串之 Unicode 文字字元的相關資訊。  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [如何：存取字串中的字元](../../../../visual-basic/programming-guide/language-features/strings/how-to-access-characters-in-strings.md)
- [在 Visual Basic 中的字串和其他資料類型之間進行轉換](../../../../visual-basic/programming-guide/language-features/strings/converting-between-strings-and-other-data-types.md)
- [字串](../../../../visual-basic/programming-guide/language-features/strings/index.md)
