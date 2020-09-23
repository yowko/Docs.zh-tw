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
ms.openlocfilehash: e1f634fcdb23f16e794449f8fe7b53c451c8c5b8
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91059167"
---
# <a name="how-to-convert-a-string-to-an-array-of-characters-in-visual-basic"></a>如何：在 Visual Basic 中將字串轉換為字元陣列

有時候，在您的字串中包含字元的資料以及字串內這些字元的位置，例如當您剖析字串時，會很有用。 這個範例會示範如何呼叫字串的方法，以取得字串中的字元陣列 <xref:System.String.ToCharArray%2A> 。  
  
## <a name="example"></a>範例  

 這個範例示範如何將字串分割成 `Char` 陣列，以及如何將字串分割成 `String` 其 Unicode 文字字元的陣列。 這項差異的原因是 Unicode 文字字元可以由兩個或多個 `Char` 字元組成 (例如代理組或合併字元順序) 。 如需詳細資訊，請參閱 <xref:System.Globalization.TextElementEnumerator> 和 [Unicode 標準](https://www.unicode.org/standard/standard.html)。  
  
 [!code-vb[VbVbalrStrings#75](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#75)]  
  
## <a name="example"></a>範例  

 將字串分割成 Unicode 文字字元是比較困難的，但如果您需要字串的視覺標記法的相關資訊，這就是必要的。 這個範例會使用 <xref:System.Globalization.StringInfo.SubstringByTextElements%2A> 方法來取得組成字串的 Unicode 文字字元的相關資訊。  
  
 [!code-vb[VbVbalrStrings#76](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class4.vb#76)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.String.Chars%2A>
- <xref:System.Globalization.StringInfo?displayProperty=nameWithType>
- [如何：存取字串中的字元](how-to-access-characters-in-strings.md)
- [在 Visual Basic 中的字串和其他資料類型之間進行轉換](converting-between-strings-and-other-data-types.md)
- [字串](index.md)
