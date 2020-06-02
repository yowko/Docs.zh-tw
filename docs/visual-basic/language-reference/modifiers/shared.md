---
title: Shared
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
ms.openlocfilehash: bc63de4bda1e8e605e25fbe293686c187dd4d005
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290989"
---
# <a name="shared-visual-basic"></a>Shared (Visual Basic)

指定一或多個宣告的程式設計專案與大型的類別或結構相關聯，而不是與類別或結構的特定實例產生關聯。

## <a name="when-to-use-shared"></a>使用 Shared 的時機

共用類別或結構的成員，可將它提供給每個實例，而不是*非共用*，其中每個實例都會保留自己的複本。 例如，如果變數的值適用于整個應用程式，這就很有用。 如果您將該變數宣告為 `Shared` ，則所有實例都會存取相同的儲存位置，而如果一個實例變更變數的值，則所有實例都會存取更新的值。

共用不會改變成員的存取層級。 例如，類別成員可以是共用和私用（只能從類別記憶體取），或非共用和公用。 如需詳細資訊，請參閱[Visual Basic 中的存取層級](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)。

## <a name="rules"></a>規則

- **宣告內容。** 您只能在模組層級使用 `Shared`。 這表示元素的宣告內容 `Shared` 必須是類別或結構，而且不能是原始程式檔、命名空間或程式。

- **結合的修飾詞。** 您不能 `Shared` 在相同的宣告[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)中，將[覆寫](../../../visual-basic/language-reference/modifiers/overrides.md)、可覆寫、 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)、 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)或[Static](../../../visual-basic/language-reference/modifiers/static.md)指定在一起。

- **正在.** 您可以存取共用專案，方法是以其類別或結構名稱加以限定，而不是使用其類別或結構之特定實例的變數名稱。 您甚至不需要建立類別或結構的實例來存取其共用成員。

     下列範例會呼叫結構所公開的共用 <xref:System.Double.IsNaN%2A> 程式 <xref:System.Double> 。

     ```vb
     If Double.IsNaN(result) Then Console.WriteLine("Result is mathematically undefined.")
     ```

- **隱含共用。** 您不能 `Shared` 在[Const 語句](../../../visual-basic/language-reference/statements/const-statement.md)中使用修飾詞，但會隱含地共用常數。 同樣地，您無法將模組或介面的成員宣告為 `Shared` ，但它們會隱含共用。

## <a name="behavior"></a>行為

- **容量.** 共用變數或事件只會儲存一次，無論您建立類別或結構的實例有多少或數個。 同樣地，共用程式或屬性只會保留一組本機變數。

- **透過執行個體變數存取。** 藉由使用包含其類別或結構之特定實例的變數名稱來限定共用專案，可以存取該元素。 雖然這通常會如預期般運作，但編譯器會產生警告訊息，並透過類別或結構名稱而不是變數來進行存取。

- **透過實例運算式來存取。** 如果您透過傳回其類別或結構實例的運算式來存取共用專案，編譯器會透過類別或結構名稱進行存取，而不會評估運算式。 如果您想要運算式來執行其他動作以及傳回實例，這會產生非預期的結果。 下列範例將說明這點。
  
    ```vb
    Sub Main()
        ' The following line is the preferred way to access Total.
        ShareTotal.Total = 10

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of through
        ' the variable instanceVar. This works as expected and adds
        ' 100 to Total.
        Dim instanceVar As New ShareTotal
        instanceVar.Total += 100

        ' The following line generates a compiler warning message and
        ' accesses total through class ShareTotal instead of calling
        ' ReturnClass(). This adds 1000 to total but does not work as
        ' expected, because the WriteLine in ReturnClass() does not run.
        Console.WriteLine("Value of total is " & CStr(ShareTotal.Total))
        ReturnClass().Total += 1000
    End Sub

    Public Function ReturnClass() As ShareTotal
        Console.WriteLine("Function ReturnClass() called")
        Return New ShareTotal
    End Function

    Public Class ShareTotal
        Public Shared Property Total As Integer
    End Class
    ```

     在上述範例中，編譯器會產生一則警告訊息，這兩次程式碼都會 `Total` 透過實例存取共用屬性。 在每個案例中，它會直接透過類別進行存取 `ShareTotal` ，而不會使用任何實例。 對於程式的預期呼叫 `ReturnClass` ，這表示它甚至不會產生對的呼叫 `ReturnClass` ，因此不會執行顯示 "Function ReturnClass （）" 的其他動作。

`Shared` 修飾詞可用於以下內容：

- [Dim 陳述式](../statements/dim-statement.md)
- [Event 陳述式](../statements/event-statement.md)
- [Function 陳述式](../statements/function-statement.md)
- [Operator Statement](../operator-statement.md)
- [Property Statement](../property-statement.md)
- [Sub 陳述式](../sub-statement.md)
  
## <a name="see-also"></a>另請參閱

- [Shadows](shadows.md)
- [靜止](static.md)
- [Visual Basic 中的存留期](../../programming-guide/language-features/declared-elements/lifetime.md)
- [程序](../../programming-guide/language-features/procedures/index.md)
- [結構](../../programming-guide/language-features/data-types/structures.md)
- [物件和類別](../../programming-guide/language-features/objects-and-classes/index.md)
