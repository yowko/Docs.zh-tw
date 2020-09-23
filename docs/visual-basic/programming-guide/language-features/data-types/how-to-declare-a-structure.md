---
title: 作法：宣告結構
ms.date: 07/20/2015
helpviewer_keywords:
- declarations [Visual Basic], structures
- structure statements [Visual Basic]
- statements [Visual Basic], structure
- structures [Visual Basic], declaring
ms.assetid: d5e98381-eb81-47d4-af83-48cc534a2572
ms.openlocfilehash: bffdc5974eff6b71e0abc4780a61aa300769eed6
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058543"
---
# <a name="how-to-declare-a-structure-visual-basic"></a>如何：宣告結構 (Visual Basic)

您可以使用 [Structure 語句](../../../language-reference/statements/structure-statement.md)來開始結構宣告，然後使用語句來結束它 `End Structure` 。 在這兩個語句之間，您必須宣告至少一個 *元素*。 元素可以是任何資料類型，但至少一個必須是非共用變數或非共用的 noncustom 事件。  
  
 您無法初始化結構宣告中的任何結構元素。 當您將變數宣告為結構類型時，您可以透過變數存取它們，藉以指派值給專案。  
  
 如需結構和類別之間差異的討論，請參閱 [結構和類別](structures-and-classes.md)。  
  
 基於示範目的，請考慮您要追蹤員工姓名、電話分機和薪資的情況。 結構可讓您在單一變數中進行這項作業。  
  
### <a name="to-declare-a-structure"></a>宣告結構  
  
1. 建立結構的開頭和結尾語句。  
  
     您可以使用 [Public](../../../language-reference/modifiers/public.md)、 [Protected](../../../language-reference/modifiers/protected.md)、 [Friend](../../../language-reference/modifiers/friend.md)或 [Private](../../../language-reference/modifiers/private.md) 關鍵字來指定結構的存取層級，也可以讓它預設為 `Public` 。  
  
    ```vb  
    Private Structure employee  
    End Structure  
    ```  
  
2. 將元素加入至結構的主體。  
  
     結構至少必須有一個元素。 您必須宣告每個元素，並為其指定存取層級。 如果您在沒有任何關鍵字的情況下使用 [Dim 語句](../../../language-reference/statements/dim-statement.md) ，存取範圍預設為 `Public` 。  
  
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
  
     `salary`上述範例中的欄位是 `Private` ，這表示它無法在結構外部存取，即使是從包含類別也一樣。 不過， `giveRaise` 程式是 `Public` ，因此可以從結構外部呼叫。 同樣地，您可以 `salaryReviewTime` 從結構外部引發事件。  
  
     除了變數、 `Sub` 程式和事件之外，您也可以 `Function` 在結構中定義常數、程式和屬性。 您可以指定最多一個屬性作為 *預設屬性*，前提是它至少需要一個引數。 您可以使用[共用](../../../language-reference/modifiers/shared.md)程式來處理事件 `Sub` 。 如需詳細資訊，請參閱 [如何：在 Visual Basic 中宣告及呼叫預設屬性](../procedures/how-to-declare-and-call-a-default-property.md)。  
  
## <a name="see-also"></a>另請參閱

- [Data types (資料類型)](index.md)
- [基礎資料類型](elementary-data-types.md)
- [複合資料類型](composite-data-types.md)
- [Value Types and Reference Types](value-types-and-reference-types.md)
- [結構](structures.md)
- [疑難排解資料類型的問題](troubleshooting-data-types.md)
- [結構變數](structure-variables.md)
- [結構與其他程式設計項目](structures-and-other-programming-elements.md)
- [結構與類別](structures-and-classes.md)
- [使用者定義資料類型](../../../language-reference/data-types/user-defined-data-type.md)
