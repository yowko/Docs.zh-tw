---
title: HOW TO：宣告結構 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: a52daddaa8701ccca9bd9b5b4a48535a6ffa19ed
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906707"
---
# <a name="how-to-declare-a-structure-visual-basic"></a>HOW TO：宣告結構 (Visual Basic)
開始使用在 structure 宣告[Structure 陳述式](../../../../visual-basic/language-reference/statements/structure-statement.md)，然後您使用`End Structure`陳述式。 這兩個陳述式之間必須宣告至少一個*項目*。 項目可以是任何資料類型，但至少一個必須為非共用的變數或非共用、 非自訂的事件。  
  
 您無法初始化任何在結構宣告中的結構項目。 當您宣告結構類型的變數時，您將值指派至項目透過變數來存取它們。  
  
 如需結構和類別之間的差異的討論，請參閱 <<c0> [ 結構和類別](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)。  
  
 基於示範目的，假設您想要用來追蹤員工的名稱、 電話分機號碼和薪資。 一種結構可讓您在單一變數中。  
  
### <a name="to-declare-a-structure"></a>若要宣告結構  
  
1. 建立的開始和結束陳述式中的結構。  
  
     您可以指定的結構，使用的存取層級[公開金鑰](../../../../visual-basic/language-reference/modifiers/public.md)，[受保護](../../../../visual-basic/language-reference/modifiers/protected.md)， [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)，或[私人](../../../../visual-basic/language-reference/modifiers/private.md)關鍵字，或者您可以讓它預設為`Public`。  
  
    ```  
    Private Structure employee  
    End Structure  
    ```  
  
2. 加入結構主體中的項目。  
  
     結構必須有至少一個項目。 您必須宣告每個項目，並為其指定存取層級。 如果您使用[Dim 陳述式](../../../../visual-basic/language-reference/statements/dim-statement.md)而不需要任何關鍵字，可存取性，預設值為`Public`。  
  
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
  
     `salary`在上述範例中的欄位是`Private`，這表示它是外部結構，甚至是從包含的類別無法存取。 不過，`giveRaise`程序是`Public`，因此它可以從外部呼叫結構。 同樣地，您可以提高`salaryReviewTime`結構之外的事件。  
  
     變數，除了`Sub`程序和事件，您也可以定義常數，`Function`程序和在結構中的屬性。 您可以指定最多一個屬性為*屬性預設*，前提是需要至少一個引數。 您可以處理的事件[Shared](../../../../visual-basic/language-reference/modifiers/shared.md) `Sub`程序。 如需詳細資訊，請參閱[如何：宣告，並在 Visual Basic 中呼叫預設屬性](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)。  
  
## <a name="see-also"></a>另請參閱

- [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [基礎資料類型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [複合資料類型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [Value Types and Reference Types](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [結構](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [結構變數](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [結構和其他程式設計項目](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [結構和類別](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [使用者定義的資料類型](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
