---
title: HOW TO：決定與列舉值 (Visual Basic) 相關聯的字串
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 25c55c14507c67b9bdd8606cb85afd55f9a748fa
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610537"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>HOW TO：決定與列舉值 (Visual Basic) 相關聯的字串
<xref:System.Enum.GetValues%2A>和<xref:System.Enum.GetNames%2A>方法可讓您決定的字串和列舉成員相關聯的值。  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>若要決定與列舉型別相關聯的字串  
  
- 使用<xref:System.Enum.GetNames%2A>方法來擷取與列舉成員相關聯的字串。 這個範例會宣告列舉`flavorEnum`，然後使用<xref:System.Enum.GetNames%2A>方法，以顯示每個成員相關聯的字串。  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
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
