---
title: 如何：決定與列舉值關聯的字串
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values [Visual Basic], enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
ms.openlocfilehash: 525da9206472afefa9f85b49ceee0775cbd168c3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414462"
---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a>如何：決定與列舉值關聯的字串 (Visual Basic)
<xref:System.Enum.GetValues%2A>和 <xref:System.Enum.GetNames%2A> 方法可讓您判斷與列舉成員相關聯的字串和值。  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a>若要判斷與列舉相關聯的字串  
  
- 使用 <xref:System.Enum.GetNames%2A> 方法來抓取與列舉成員相關聯的字串。 這個範例會宣告列舉， `flavorEnum` 然後使用 <xref:System.Enum.GetNames%2A> 方法來顯示與每個成員相關聯的字串。  
  
     [!code-vb[VbEnumsTask#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Enum.GetValues%2A>
- <xref:System.Enum.GetNames%2A>
- <xref:System.Enum>
- [如何：宣告列舉類型](how-to-declare-enumerations.md)
- [如何：參考列舉類型成員](how-to-refer-to-an-enumeration-member.md)
- [列舉和名稱限定性條件](enumerations-and-name-qualification.md)
- [如何：在 Visual Basic 中逐一查看列舉類型](how-to-iterate-through-an-enumeration.md)
- [何時使用列舉類型](when-to-use-an-enumeration.md)
- [End 陳述式](../../../language-reference/statements/enum-statement.md)
