---
title: 如何：宣告結構 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: 6128addd60609bfc88a1409648fb320bc7089974
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-a-structure-visual-basic"></a>如何：宣告結構 (Visual Basic)
開始使用在 structure 宣告[Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)，和您結束該處理序與`End``Structure`陳述式。 這兩個陳述式之間必須宣告至少一個*元素*。 項目可以是任何資料類型，但至少一個必須非共用的變數或共用的非自訂的事件。  
  
 您無法初始化任何結構中的項目結構宣告。 當您宣告為結構類型的變數時，您將值指派至項目透過變數存取它們。  
  
 如需結構和類別之間的差異的討論，請參閱[結構和類別](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)。  
  
 針對示範用途，請考慮您想要用來追蹤員工的名稱、 電話分機號碼和薪資的情況。 結構，可讓您在單一的變數中這麼做。  
  
### <a name="to-declare-a-structure"></a>宣告結構  
  
1.  建立的開始和結束結構的陳述式。  
  
     您可以指定的存取層級結構使用[公用](../../../../visual-basic/language-reference/modifiers/public.md)，[保護](../../../../visual-basic/language-reference/modifiers/protected.md)， [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)，或[私人](../../../../visual-basic/language-reference/modifiers/private.md)關鍵字，或您可以讓它預設為`Public`。  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2.  將項目加入至結構主體。  
  
     結構必須至少一個元素。 您必須宣告每個項目，並為其指定的存取層級。 如果您使用[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)存取範圍預設為不含任何關鍵字， `Public`。  
  
    ```  
    Private Structure employee  
        Public givenName As String  
        Public familyName As String  
        Public phoneExtension As Long  
        Private salary As Decimal  
        Public Sub giveRaise(raise As Double)  
            salary *= raise  
        End Sub  
        Public Event salaryReviewTime()  
    End Structure  
    ```  
  
     `salary`在上述範例中的欄位是`Private`，這表示它是外部結構，甚至是從包含的類別無法存取。 不過，`giveRaise`程序是`Public`，因此可以從中呼叫在結構之外。 同樣地，您可以提高`salaryReviewTime`在結構之外的事件。  
  
     除了變數之外，`Sub`程序和事件，您也可以定義常數，`Function`程序和結構中的屬性。 您可以指定最多一個屬性做為*預設屬性*，前提是它需要至少一個引數。 您可以處理的事件，該[共用](../../../../visual-basic/language-reference/modifiers/shared.md)`Sub`程序。 如需詳細資訊，請參閱[如何： 宣告及呼叫預設屬性在 Visual Basic 中](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)。  
  
## <a name="see-also"></a>另請參閱  
 [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [基礎資料類型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [複合資料類型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)  
 [結構](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [結構變數](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)  
 [結構和其他程式設計項目](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)  
 [結構和類別](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)  
 [使用者定義的資料類型](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
