---
title: Shared (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Shared
helpviewer_keywords:
- Shared keyword [Visual Basic]
- members [Visual Basic], shared
- shared members
- nonshared
- shared [elements VB]
- elements [Visual Basic], shared
ms.assetid: 2bf7cf2c-b0dd-485e-8749-b5d674dab4cd
ms.openlocfilehash: b76d999bfe3f7ae5205cb9486e040c1d6191b78c
ms.sourcegitcommit: dc02d7d95f1e3efcc7166eaf431b0ec0dc9d8dca
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/02/2018
ms.locfileid: "37143527"
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)
指定一或多個宣告的程式設計項目與類別或結構的大規模，而非與該類別或結構的特定執行個體相關聯。  
  
## <a name="remarks"></a>備註  
  
## <a name="when-to-use-shared"></a>何時使用共用  
 共用的類別或結構成員會將其提供給每個執行個體，而非*非共用*、 其中的每個執行個體保留它自己的複本。 例如，如果變數的值會套用到整個應用程式，這十分有用。 如果您宣告該變數`Shared`、 然後所有執行個體存取相同的儲存體位置，以及如果一個執行個體變更變數的值，所有執行個體存取更新的值。  
  
 共用時，不會更改成員的存取層級。 例如，可共用的類別成員和私用 （只能從存取類別內），或非共用和公用。 如需詳細資訊，請參閱 <<c0> [ 存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="rules"></a>規則  
  
-   **宣告內容。** 您只能在模組層級使用 `Shared`。 這表示的宣告內容`Shared`項目必須是類別或結構，並不能是原始程式檔、 命名空間或程序。  
  
-   **結合的修飾詞。** 您無法指定`Shared`連同[覆寫](../../../visual-basic/language-reference/modifiers/overrides.md)， [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)， [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)， [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)，或[靜態](../../../visual-basic/language-reference/modifiers/static.md)相同宣告中。  
  
-   **存取。** 您可以限定其名稱與其類別或結構的名稱，而非與特定的執行個體，其類別或結構的變數名稱，以存取共用的項目。 您甚至不必建立的類別或結構，以存取其共用的成員執行個體。  
  
     下列範例會呼叫共用的程序<xref:System.Double.IsNaN%2A>由<xref:System.Double>結構。  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   **隱含的共用。** 您無法使用`Shared`修飾詞[Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)，但是常數會以隱含方式共用。 同樣地，您無法在此宣告的模組或介面成員，才能被`Shared`，但它們會以隱含方式共用。  
  
## <a name="behavior"></a>行為  
  
-   **儲存體。** 共用的變數或事件會儲存在記憶體中一次，不論多少個執行個體建立其類別或結構。 同樣地，共用的程序或屬性會保留只有一組本機變數。  
  
-   **透過執行個體變數存取。** 可以限定其名稱的變數，包含其類別或結構的特定執行個體的名稱來存取共用的項目。 雖然這通常在如預期般運作，編譯器會產生一則警告訊息，並可透過類別或結構名稱，而不是變數的存取權。  
  
-   **透過執行個體運算式的存取。** 如果您透過該運算式會傳回其類別或結構的執行個體存取共用的項目，編譯器就會進行與存取的類別或結構的名稱，而不是評估運算式。 如果您想要執行其他動作，以及傳回執行個體的運算式，這會產生非預期的結果。 下列範例將說明這點。  
  
    ```vb
    Sub main()  
        shareTotal.total = 10  
        ' The preceding line is the preferred way to access total.  
        Dim instanceVar As New shareTotal  
        instanceVar.total += 100  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of through  
        ' the variable instanceVar. This works as expected and adds  
        ' 100 to total.  
        returnClass().total += 1000  
        ' The preceding line generates a compiler warning message and  
        ' accesses total through class shareTotal instead of calling  
        ' returnClass(). This adds 1000 to total but does not work as  
        ' expected, because the MsgBox in returnClass() does not run.  
        MsgBox("Value of total is " & CStr(shareTotal.total))  
    End Sub  
    Public Function returnClass() As shareTotal  
        MsgBox("Function returnClass() called")  
        Return New shareTotal  
    End Function  
    Public Class shareTotal  
        Public Shared total As Integer  
    End Class  
    ```  
  
     在上述範例中，編譯器會產生一則警告訊息的程式碼會存取共用的變數這兩個時間`total`透過執行個體。 它可讓每個案例中透過類別直接存取`shareTotal`，而且使用的任何執行個體。 在程序想要呼叫的情況下`returnClass`，這表示它甚至不會產生呼叫`returnClass`，因此不會執行其他動作，顯示 「 呼叫函式 returnClass()"。  
  
 `Shared` 修飾詞可用於以下內容：  
  
 [Dim 陳述式](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [Event 陳述式](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Operator 陳述式](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Property 陳述式](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>另請參閱  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Static](../../../visual-basic/language-reference/modifiers/static.md)  
 [在 Visual Basic 中的存留期](../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [程序](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
 [結構](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [物件和類別](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
