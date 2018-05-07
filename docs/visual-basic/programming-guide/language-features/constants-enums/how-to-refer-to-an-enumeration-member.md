---
title: 如何：參考列舉成員 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: f995a0ef69c503360a5d709551a7f0ccfd67ce40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a>如何：參考列舉成員 (Visual Basic)
列舉型別提供便利的方式來處理組相關的常數和常數值與名稱。 例如，您可以宣告列舉來當作一組與當週的日次建立關聯的整數常數，接著在程式碼中使用日次的名稱而不是它們的整數值。  
  
 您可以避免使用具有完整格式的名稱`Imports`陳述式。 如需詳細資訊，請參閱[列舉型別和名稱限定](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)。  
  
### <a name="to-refer-to-an-enumeration-member"></a>若要為列舉成員，請參閱  
  
-   限定成員名稱與列舉型別。 例如，下列範例會將指派`Saturday`隸屬`FirstDayOfWeek`列舉型別變數`DayValue`。  
  
     [!code-vb[VbEnumsTask#19](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-refer-to-an-enumeration-member_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [如何： 宣告列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [列舉和名稱限定性條件](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [如何： 逐一查看 Visual Basic 中列舉類型](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [如何：決定與列舉值相關聯的字串](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [何時使用列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
