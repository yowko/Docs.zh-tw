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
ms.openlocfilehash: b15dd08d69f372317b9140001e8072eeb66d44ab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604545"
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)
指定一或多個宣告的程式設計項目相關聯的類別或結構，而不在類別或結構的特定執行個體。  
  
## <a name="remarks"></a>備註  
  
## <a name="when-to-use-shared"></a>何時使用共用  
 共用的類別或結構成員會使其可使用每個執行個體，而非*非共用*、 其中的每個執行個體保留其自己的複本。 這非常有用，例如，如果變數的值套用至整個應用程式。 如果您宣告該變數`Shared`、 所有執行個體存取相同的儲存位置，和一個執行個體變更變數的值，如果所有執行個體存取更新的值。  
  
 共用並不會改變成員的存取層級。 比方說，您可以共用的類別成員和私用 （只能從存取類別內），或非共用及公用。 如需詳細資訊，請參閱[存取 Visual Basic 中的層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。  
  
## <a name="rules"></a>規則  
  
-   **宣告內容。** 您只能在模組層級使用 `Shared`。 這表示宣告內容`Shared`項目必須是類別或結構，並不能是原始程式檔、 命名空間或程序。  
  
-   **結合的修飾詞。** 您無法指定`Shared`搭配[會覆寫](../../../visual-basic/language-reference/modifiers/overrides.md)， [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)， [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)， [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)，或[靜態](../../../visual-basic/language-reference/modifiers/static.md)相同宣告中。  
  
-   **存取。** 您可以限定其名稱與其類別或結構的名稱，而非其類別或結構的特定執行個體的變數名稱存取共用項目。 您甚至不必建立類別或結構，以存取其共用的成員的執行個體。  
  
     下列範例會呼叫共用的程序<xref:System.Double.IsNaN%2A>所公開<xref:System.Double>結構。  
  
     `If Double.IsNaN(result) Then MsgBox("Result is mathematically undefined.")`  
  
-   **隱含的共用。** 您無法使用`Shared`修飾詞[Const 陳述式](../../../visual-basic/language-reference/statements/const-statement.md)，但是常數會隱含地共用。 同樣地，您無法宣告指向成員的模組或介面`Shared`，但是隱含共用它們。  
  
## <a name="behavior"></a>行為  
  
-   **儲存體。** 共用的變數或事件會儲存在記憶體中一次，不論多少個執行個體建立其類別或結構。 同樣地，共用的程序或屬性會保存只有一個本機變數的集合。  
  
-   **透過執行個體變數存取。** 您可存取共用項目來限定變數，內含其類別或結構的特定執行個體的名稱取代。 雖然這通常在如預期般運作，編譯器會產生警告訊息，而且會透過類別或結構名稱，而不是變數的存取權。  
  
-   **透過執行個體運算式存取。** 如果您是透過傳回其類別或結構的執行個體的運算式存取共用項目，編譯器會透過類別或結構名稱，而不是評估運算式的存取權。 如果您想要執行其他動作，以及傳回執行個體的運算式，這會產生非預期的結果。 下列範例將說明這點。  
  
    ```  
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
  
     在上述範例中，編譯器會產生一則警告訊息的程式碼會存取共用的變數這兩個時間`total`透過執行個體。 在每個案例會透過類別的直接存取`shareTotal`而且也不會使用任何執行個體。 在預期的呼叫程序的情況下`returnClass`，這表示它甚至不會產生呼叫`returnClass`，因此不會執行其他動作的顯示"呼叫的函式 returnClass()"。  
  
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
