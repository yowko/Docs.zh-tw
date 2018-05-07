---
title: 如何：在 Visual Basic 中逐一查看列舉類型
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 06609d38c805e5f073a2f3a299ecc3aa7cf7be01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>如何：在 Visual Basic 中逐一查看列舉類型
列舉提供使用相關常數組和建立常數值與名稱之關聯的便利方法。 要逐一查看列舉類型，您可以將它移至陣列使用<xref:System.Enum.GetValues%2A>方法。 您也可以逐一列舉型別使用`For...Each`陳述式中，使用<xref:System.Enum.GetNames%2A>或<xref:System.Enum.GetValues%2A>方法，可擷取的字串或數值的值。  
  
### <a name="to-iterate-through-an-enumeration"></a>若要逐一查看列舉類型  
  
-   宣告陣列，並使用轉換成列舉<xref:System.Enum.GetValues%2A>方法，然後再將陣列傳遞為您將任何其他變數。 下列範例會顯示每個成員的列舉型別<xref:Microsoft.VisualBasic.FirstDayOfWeek>逐一查看的列舉型別。  
  
     [!code-vb[VbEnumsTask#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-iterate-through-an-enumeration_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [列舉的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)  
 [如何： 宣告列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [何時使用列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [如何：決定與列舉值相關聯的字串](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [如何：參考列舉成員](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [列舉和名稱限定性條件](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
