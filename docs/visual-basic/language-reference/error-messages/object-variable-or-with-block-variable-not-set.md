---
title: 未設定物件變數或 With 區塊變數
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 07c215d373e4ac1cbadf82a48b8cb3d90efdbdb4
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040549"
---
# <a name="object-variable-or-with-block-variable-not-set"></a>未設定物件變數或 With 區塊變數
參考的物件變數無效。   發生這個錯誤的原因有下列幾種︰

- 已宣告變數, 但未指定類型。 如果在未指定類型的情況下宣告變數, 則會預設`Object`為類型。

    例如, 以`Dim x`宣告`Object;`的變數會是類型, 以宣告的變數`Dim x As String`會是類型`String`。

    > [!TIP]
    > 語句不允許產生`Object`類型的隱含類型。 `Option Strict` 如果您省略型別, 就會發生編譯時期錯誤。 請參閱[Option Strict 語句](../../../visual-basic/language-reference/statements/option-strict-statement.md)。

- 您嘗試參考已設定為`Nothing`的物件。

- 您嘗試存取未正確宣告之陣列變數的元素。

    例如, 如果您嘗試參考陣列`products() As String` `products(3) = "Widget"`的元素, 則宣告為的陣列將會觸發錯誤。 陣列沒有任何元素, 而且會被視為物件。

- 您正嘗試在區塊初始化之前, `With...End With`先存取區塊內的程式碼。   區塊必須藉由`With`執行語句進入點來初始化。 `With...End With`

> [!NOTE]
> 在舊版的 Visual Basic 或 VBA 中, 也會藉由指派值給變數而不使用`Set`關鍵字 (`x = "name"`而不是`Set x = "name"`) 來觸發此錯誤。 `Set`關鍵字在 Visual Basic .net 中已不再有效。

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 將`Option Strict`下列`On`程式碼新增至檔案的開頭, 將設為:

    ```vb
    Option Strict On
    ```

    當您執行專案時, 如果未指定任何類型的變數, 則會在**錯誤清單**中顯示編譯器錯誤。

2. 如果您不想要啟用`Option Strict`, 請在您的程式碼中搜尋未使用類型 (`Dim x`而非`Dim x As String`) 指定的任何變數, 並將所需的類型加入至宣告。

3. 請確定您未參考已設定為`Nothing`的物件變數。  在您的程式碼中`Nothing`搜尋關鍵字, 然後修改您的程式碼, 讓物件`Nothing`不會設定為, 直到您參考它為止。

4. 在存取之前, 請確定所有陣列變數都已建立維度。 您可以在第一次建立陣列時指派維度 (`Dim x(5) As String` `Dim x() As String`而不是`ReDim` ), 或使用關鍵字來設定陣列的維度, 然後再進行第一次存取。

5. 請確定您`With`的區塊是藉由`With`執行語句進入點來初始化。

## <a name="see-also"></a>另請參閱

- [物件變數宣告](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [ReDim 陳述式](../../../visual-basic/language-reference/statements/redim-statement.md)
- [With...End With 陳述式](../../../visual-basic/language-reference/statements/with-end-with-statement.md)
