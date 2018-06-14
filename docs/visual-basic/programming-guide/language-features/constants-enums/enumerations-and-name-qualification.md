---
title: 列舉和名稱限定 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], enumerations
- Imports statement [Visual Basic], namespace declarations
- declaring namespaces [Visual Basic], enumerations
- name collisions
- ambiguous names [Visual Basic], enumerations
- enumerations [Visual Basic], name qualification
- names [Visual Basic], avoiding conflicts
- namespaces [Visual Basic], declaring
- naming conflicts, enumerations
- naming conflicts, qualifying names
- declaring enumerations
- references [Visual Basic], enumeration members
- naming conventions [Visual Basic], naming conflicts
- declarations [Visual Basic], namespaces
ms.assetid: 08ba2738-df52-4140-bc55-f57c871c9b73
ms.openlocfilehash: eb1f5653d968e81168833cd57813219e8f049b70
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648576"
---
# <a name="enumerations-and-name-qualification-visual-basic"></a>列舉和名稱限定 (Visual Basic)
一般來說，當參考的列舉成員，您必須限定成員名稱與列舉型別名稱。 例如，若要參考`Sunday`隸屬您`Days`列舉型別，您可以使用下列語法：  
  
 [!code-vb[VbEnumsTask#18](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_1.vb)]  
  
## <a name="using-the-imports-statement"></a>使用匯入陳述式  
 您可以避免使用完整限定的名稱，再加入`Imports`陳述式，以您的程式碼，如下列範例所示的命名空間宣告區段：  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 `Imports`陳述式匯入命名空間名稱，從參考的專案和組件以及在相同的專案出現陳述式的模組。 加入這個陳述式後，您可以參考列舉成員，無限制，如下列範例所示：  
  
 [!code-vb[VbEnumsTask#24](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_3.vb)]  
  
 藉由組織相關的常數列舉型別中的設定，您可以使用相同的常數名稱在不同內容中。 例如，您可以使用相同的名稱中的週間日常數`Days`和`WorkDays`列舉型別。 如果您使用`Imports`陳述式對列舉型別，您必須小心避免模稜兩可的參考。 參考下列範例：  
  
 [!code-vb[VbEnumsTask#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_2.vb)]  
  
 [!code-vb[VbEnumsTask#25](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_4.vb)]  
  
 假設`Monday`兩者的成員`Days`列舉型別和`Workdays`列舉型別，此程式碼會產生編譯器錯誤。 若要參考個別常數時，請避免模稜兩可的參考，限定的列舉常數的名稱。 下列程式碼是指`Saturday`中的常數`Days`和`WorkDays`列舉型別。  
  
 [!code-vb[VbEnumsTask#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/enumerations-and-name-qualification_5.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [常數和列舉](../../../../visual-basic/language-reference/constants-and-enumerations.md)  
 [如何： 宣告列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [如何：參考列舉成員](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [如何： 逐一查看 Visual Basic 中列舉類型](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [如何：決定與列舉值相關聯的字串](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [何時使用列舉](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [常數和常值資料類型](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [Enum 陳述式](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
 [資料類型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)
