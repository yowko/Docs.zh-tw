---
title: HOW TO：逐一查看 Visual Basic 中列舉
ms.date: 07/20/2015
helpviewer_keywords:
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
ms.openlocfilehash: 63597145e96b04affc5f0e80e05a56b3fdf27278
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61907032"
---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a>HOW TO：逐一查看 Visual Basic 中列舉
列舉提供使用相關常數組和建立常數值與名稱之關聯的便利方法。 若要逐一查看列舉型別，您可以將它移到陣列使用<xref:System.Enum.GetValues%2A>方法。 您也可以逐一列舉使用`For...Each`陳述式中，使用<xref:System.Enum.GetNames%2A>或<xref:System.Enum.GetValues%2A>方法來擷取字串或數值的值。  
  
### <a name="to-iterate-through-an-enumeration"></a>若要逐一查看列舉類型  
  
- 宣告陣列，並將列舉型別轉換成與其<xref:System.Enum.GetValues%2A>方法，然後再將陣列傳遞為您將任何其他變數。 下列範例會顯示每個成員的列舉型別<xref:Microsoft.VisualBasic.FirstDayOfWeek>逐一查看列舉型別。  
  
     [!code-vb[VbEnumsTask#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#7)]  
  
## <a name="see-also"></a>另請參閱

- [列舉的概觀](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md)
- [如何：宣告列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [何時使用列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [如何：決定與列舉值關聯的字串](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)
- [如何：參考列舉成員](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [列舉和名稱限定性條件](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [陣列](../../../../visual-basic/programming-guide/language-features/arrays/index.md)
