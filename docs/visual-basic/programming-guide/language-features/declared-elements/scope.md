---
title: Visual Basic 中的範圍
ms.date: 07/20/2015
helpviewer_keywords:
- module scope [Visual Basic]
- scope [Visual Basic], levels
- module level
- procedures [Visual Basic], scope
- declared elements [Visual Basic], scope
- namespaces [Visual Basic], scope
- scope [Visual Basic], declared elements
- scope [Visual Basic], about scope
- levels of scope [Visual Basic]
- block scope [Visual Basic]
- scope [Visual Basic], Visual Basic
- procedure scope [Visual Basic]
ms.assetid: 208106fe-79c9-4eec-93c6-55f08548895f
ms.openlocfilehash: 7f7e32d6ac838e250c260987d3d5c375f8697c45
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512855"
---
# <a name="scope-in-visual-basic"></a>Visual Basic 中的範圍

已宣告專案的*範圍*是一組可以參考它的程式碼, 但不限定其名稱, 或透過[Imports 語句 (.net 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)提供它。 元素的範圍可以是下列其中一個層級:

|層級|描述|
|-----------|-----------------|
|區塊範圍|只能在其宣告所在的程式碼區塊中使用|
|程式範圍|可供宣告之程式內的所有程式碼使用|
|模組範圍|適用于其宣告所在之模組、類別或結構內的所有程式碼|
|命名空間範圍|可供宣告之命名空間中的所有程式碼使用|

從最窄 (區塊) 到最廣泛 (命名空間) 的這些範圍進度層級, 其中最*窄的範圍*表示可以參考該專案但未限定的程式碼之一集。 如需詳細資訊, 請參閱此頁面上的「範圍層級」。

## <a name="specifying-scope-and-defining-variables"></a>指定範圍和定義變數

當您宣告元素時, 您可以指定專案的範圍。 範圍可以視下列因素而定:

- 您在其中宣告元素的區域 (區塊、程式、模組、類別或結構)

- 包含元素宣告的命名空間

- 您為元素宣告的存取層級

當您定義具有相同名稱但範圍不同的變數時, 請小心使用, 因為這樣做可能會導致非預期的結果。 如需詳細資訊，請參閱 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)。

## <a name="levels-of-scope"></a>範圍層級

程式設計項目可在您宣告它的整個區域中使用。 相同區域中的所有程式碼都可以參考該元素, 而不會限定其名稱。

### <a name="block-scope"></a>封鎖範圍

區塊是包含在起始和結束宣告語句中的一組語句, 如下所示:

- `Do` 和 `Loop`

- `For`[`Each`] 和`Next`

- `If` 和 `End If`

- `Select` 和 `End Select`

- `SyncLock` 和 `End SyncLock`

- `Try` 和 `End Try`

- `While` 和 `End While`

- `With` 和 `End With`

如果您在區塊內宣告變數, 就只能在該區塊內使用它。 在下列範例中, `cube`整數變數的範圍是和`End If`之間`If`的區塊`cube` , 而且當執行超出區塊時, 您就不能再參考。

```vb
If n < 1291 Then
    Dim cube As Integer
    cube = n ^ 3
End If
```

> [!NOTE]
> 即使變數的範圍限制為區塊, 它的存留期仍然是整個程式的存留時間。 如果您在程式期間多次輸入區塊, 每個區塊變數都會保留其先前的值。 為了避免這種情況發生非預期的結果, 在區塊開頭初始化區塊變數是明智的做法。

### <a name="procedure-scope"></a>程式範圍

在程式中宣告的元素無法在該程式之外使用。 只有包含宣告的程式可以使用它。 此層級的變數也稱為「*區域變數」 (local variables*)。 您可以使用[Dim 語句](../../../../visual-basic/language-reference/statements/dim-statement.md)來宣告它們, 其中包含或不使用[Static](../../../../visual-basic/language-reference/modifiers/static.md)關鍵字。

程式與區塊領域密切相關。 如果您在程式中宣告變數, 但在該程式內的任何區塊外, 您可以將變數視為具有區塊範圍, 其中區塊是整個程式。

> [!NOTE]
> 所有的本機專案 (即使是`Static`變數) 都是其出現所在程式的私用。 您不能在程式內使用[Public](../../../../visual-basic/language-reference/modifiers/public.md)關鍵字來宣告任何專案。

### <a name="module-scope"></a>模組範圍

為了方便起見, 單一詞彙*模組層級*同樣適用于模組、類別和結構。 您可以在此層級宣告專案, 方法是將宣告語句放在任何程式或區塊的外部, 但是在模組、類別或結構中。

當您在模組層級進行宣告時, 您選擇的存取層級會決定範圍。 包含模組、類別或結構的命名空間也會影響範圍。

您宣告[私](../../../../visual-basic/language-reference/modifiers/private.md)用存取層級的專案可用於該模組中的每個程式, 但不適用於不同模組中的任何程式碼。 如果`Dim`您未使用任何存取層`Private`級關鍵字, 則模組層級的語句會預設為。 不過, 您可以`Private` `Dim`在語句中使用關鍵字, 讓範圍和存取層級更明顯。

在下列範例中, 模組中定義的所有程式都可以參考字串變數`strMsg`。 呼叫第二個程式時, 會在對話方塊中顯示字串變數`strMsg`的內容。

```vb
' Put the following declaration at module level (not in any procedure).
Private strMsg As String
' Put the following Sub procedure in the same module.
Sub initializePrivateVariable()
    strMsg = "This variable cannot be used outside this module."
End Sub
' Put the following Sub procedure in the same module.
Sub usePrivateVariable()
    MsgBox(strMsg)
End Sub
```

### <a name="namespace-scope"></a>命名空間範圍

如果您使用[Friend](../../../../visual-basic/language-reference/modifiers/friend.md)或[Public](../../../../visual-basic/language-reference/modifiers/public.md)關鍵字在模組層級宣告專案, 它會變成可供在宣告專案之命名空間中的所有程式使用。 在上述範例中的下列變更中, 字串變數`strMsg`可以在其宣告的命名空間中的任何位置參考程式碼。

```vb
' Include this declaration at module level (not inside any procedure).
Public strMsg As String
```

命名空間範圍包含嵌套的命名空間。 您也可以從命名空間內的任何命名空間中, 取得可從命名空間中取得的專案。

如果您的專案未包含任何[命名空間語句](../../../../visual-basic/language-reference/statements/namespace-statement.md), 則專案中的所有內容都會位於相同的命名空間中。 在此情況下, 可以將命名空間範圍視為專案範圍。 `Public`模組、類別或結構中的元素也可供參考其專案的任何專案使用。

## <a name="choice-of-scope"></a>選擇範圍

當您宣告變數時, 在選擇其範圍時, 您應該記住下列幾點。

### <a name="advantages-of-local-variables"></a>本機變數的優點

針對任何類型的暫時計算而言, 本機變數都是不錯的選擇, 原因如下:

- **避免名稱衝突。** 本機變數名稱不容易發生衝突。 例如, 您可以建立數個不同的程式, 其中包含`intTemp`名為的變數。 只要每個`intTemp`都宣告為區域變數, 每個程式就只會辨識自己的`intTemp`版本。 任何一個程式都可以在其本機`intTemp`中改變值, 而不會影響`intTemp`其他程式中的變數。

- **記憶體耗用量。** 本機變數只有在其程式正在執行時才會耗用記憶體。 當程式返回呼叫的程式碼時, 就會釋放其記憶體。 相反地,[共用](../../../../visual-basic/language-reference/modifiers/shared.md)和[靜態](../../../../visual-basic/language-reference/modifiers/static.md)變數會耗用記憶體資源, 直到您的應用程式停止執行為止, 因此只有在必要時才使用它們。 *執行個體變數*會耗用記憶體, 而其實例會繼續存在, 讓它們比區域變數更有效率, 但可能比`Shared`或`Static`變數更有效率。

### <a name="minimizing-scope"></a>最小化範圍

一般來說, 在宣告任何變數或常數時, 最好的程式設計作法是讓範圍盡可能縮小 (區塊範圍是最窄的)。 這有助於節省記憶體, 並將程式碼錯誤地參考錯誤變數的機率降到最低。 同樣地, 您應該將變數宣告為[靜態](../../../../visual-basic/language-reference/modifiers/static.md), 只有在必要時, 才必須在程序呼叫之間保留其值。

## <a name="see-also"></a>另請參閱

- [宣告項目特性](../../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-characteristics.md)
- [如何：控制變數的範圍](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-control-the-scope-of-a-variable.md)
- [Visual Basic 中的存留期](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Visual Basic 中的存取層級](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [對已宣告項目的參考](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [變數宣告](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
