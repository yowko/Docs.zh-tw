---
title: 如何：宣告結構
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: 41d2d03064dea703909218de56feb863526c220b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350002"
---
# <a name="how-to-declare-a-structure-visual-basic"></a>如何：宣告結構 (Visual Basic)
您可以使用[Structure 語句](../../../../visual-basic/language-reference/statements/structure-statement.md)開始結構宣告，然後使用 `End Structure` 語句來結束它。 在這兩個語句之間，您必須宣告至少一個*元素*。 元素可以是任何資料類型，但至少必須有一個非共用變數或非共用的 noncustom 事件。  
  
 您無法初始化結構宣告中的任何結構元素。 當您將變數宣告為結構類型時，您可以透過變數來存取它們，藉以指派值給專案。  
  
 如需結構和類別之間差異的討論，請參閱[結構和類別](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)。  
  
 基於示範目的，請考慮您想要追蹤員工姓名、電話分機和薪資的情況。 結構可讓您在單一變數中執行此動作。  
  
### <a name="to-declare-a-structure"></a>若要宣告結構  
  
1. 建立結構的開始和結束語句。  
  
     您可以使用[Public](../../../../visual-basic/language-reference/modifiers/public.md)、 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)、 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)或[Private](../../../../visual-basic/language-reference/modifiers/private.md)關鍵字來指定結構的存取層級，也可以讓它預設為 `Public`。  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. 將元素加入至結構的主體。  
  
     結構必須至少有一個元素。 您必須宣告每個元素，並指定它的存取層級。 如果您使用[Dim 語句](../../../../visual-basic/language-reference/statements/dim-statement.md)，但沒有任何關鍵字，協助工具預設為 `Public`。  
  
    ```vb  
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
  
     上述範例中的 `salary` 欄位是 `Private`，這表示它無法從結構外部存取，即使是從包含類別也一樣。 不過，`giveRaise` 程式是 `Public`的，因此可以從結構外部呼叫。 同樣地，您也可以從結構外部引發 `salaryReviewTime` 事件。  
  
     除了變數、`Sub` 程式和事件以外，您也可以在結構中定義常數、`Function` 程式和屬性。 您最多可以指定一個屬性做為*預設屬性*，前提是它至少接受一個引數。 您可以使用[共用](../../../../visual-basic/language-reference/modifiers/shared.md)的`Sub` 程式來處理事件。 如需詳細資訊，請參閱[如何：在 Visual Basic 中宣告及呼叫預設屬性](../../../../visual-basic/programming-guide/language-features/procedures/how-to-declare-and-call-a-default-property.md)。  
  
## <a name="see-also"></a>請參閱

- [資料類型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [基礎資料類型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [複合資料類型](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)
- [值類型和參考類型](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [結構](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [資料類型的疑難排解](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [結構變數](../../../../visual-basic/programming-guide/language-features/data-types/structure-variables.md)
- [結構和其他程式設計項目](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-other-programming-elements.md)
- [結構和類別](../../../../visual-basic/programming-guide/language-features/data-types/structures-and-classes.md)
- [使用者定義的資料類型](../../../../visual-basic/language-reference/data-types/user-defined-data-type.md)
