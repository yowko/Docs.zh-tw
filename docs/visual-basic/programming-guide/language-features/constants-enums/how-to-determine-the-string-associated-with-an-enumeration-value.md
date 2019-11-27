---
title: 如何：決定與列舉值關聯的字串
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: c396a4e2ebe973f5be65c3fab5f22cdedb29be1a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351138"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>如何：決定與列舉值關聯的字串 (Visual Basic)
<xref:System.Enum.GetValues%2A> 和 <xref:System.Enum.GetNames%2A> 方法可讓您判斷與列舉成員相關聯的字串和值。  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>若要判斷與列舉相關聯的字串  
  
- 使用 <xref:System.Enum.GetNames%2A> 方法來抓取與列舉成員相關聯的字串。 這個範例會宣告列舉，`flavorEnum`，然後使用 <xref:System.Enum.GetNames%2A> 方法來顯示與每個成員相關聯的字串。  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a>請參閱

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [如何：宣告列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)
- [如何：參考列舉成員](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [列舉和名稱限定性條件](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [如何：在 Visual Basic 中逐一查看列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)
- [何時使用列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [Enum 陳述式](../../../../visual-basic/language-reference/statements/enum-statement.md)
