---
title: HOW TO：決定與列舉值 (Visual Basic) 相關聯的字串
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 92d2e9918429c9cf408f288f832e4615b95ad423
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690185"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>HOW TO：決定與列舉值 (Visual Basic) 相關聯的字串
<xref:System.Enum.GetValues%2A>和<xref:System.Enum.GetNames%2A>方法可讓您決定的字串和列舉成員相關聯的值。  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>若要決定與列舉型別相關聯的字串  
  
-   使用<xref:System.Enum.GetNames%2A>方法來擷取與列舉成員相關聯的字串。 這個範例會宣告列舉`flavorEnum`，然後使用<xref:System.Enum.GetNames%2A>方法，以顯示每個成員相關聯的字串。  
  
     [!code-vb[VbEnumsTask#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-determine-the-string-associated-with-an-enumeration-value_1.vb)]  
  
## <a name="see-also"></a>另請參閱
- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [如何：宣告列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [如何：參考列舉成員](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [列舉和名稱限定性條件](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [如何：逐一查看 Visual Basic 中列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [何時使用列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Enum 陳述式](../../../../visual-basic/language-reference/statements/enum-statement.md)
