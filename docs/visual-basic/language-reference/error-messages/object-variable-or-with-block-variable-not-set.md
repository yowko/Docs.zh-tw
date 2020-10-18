---
title: 未設定物件變數或 With 區塊變數
ms.date: 07/20/2015
f1_keywords:
- vbrID91
ms.assetid: 2f03e611-f0ed-465c-99a2-a816e034faa3
ms.openlocfilehash: 5eff7622ce2a35cf2846c5141cede98ea033d708
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159881"
---
# <a name="object-variable-or-with-block-variable-not-set"></a>未設定物件變數或 With 區塊變數

參考了不正確物件變數。 發生這個錯誤的原因有下列幾種︰

- 宣告的變數未指定類型。 如果宣告的變數未指定類型，則會預設為類型 `Object` 。

    例如，使用宣告的變數 `Dim x` 的類型會是類型 `Object;` `Dim x As String` `String` 。

    > [!TIP]
    > `Option Strict`語句不允許隱含型別產生型別 `Object` 。 如果您省略型別，就會發生編譯階段錯誤。 請參閱 [Option Strict 語句](../statements/option-strict-statement.md)。

- 您正在嘗試參考已設定為的物件 `Nothing` 。

- 您嘗試存取的陣列變數元素未正確宣告。

    例如，如果您嘗試參考陣列的元素，則宣告為的陣列 `products() As String` 將會觸發錯誤 `products(3) = "Widget"` 。 陣列沒有元素，並被視為物件。

- 您正在嘗試先存取區塊內的程式碼 `With...End With` ，再初始化區塊。   `With...End With`區塊必須藉由執行 `With` 語句進入點來初始化。

> [!NOTE]
> 在舊版的 Visual Basic 或 VBA 中，此錯誤也會藉由指派值給變數來觸發，而不使用 `Set` 關鍵字 (， `x = "name"` 而不是 `Set x = "name"`) 。 `Set`Visual Basic .net 中的關鍵字已不再有效。

## <a name="to-correct-this-error"></a>更正這個錯誤

1. 將 `Option Strict` `On` 下列程式碼新增至檔案的開頭，以將設定為：

    ```vb
    Option Strict On
    ```

    當您執行專案時，如果未指定類型，則會在 **錯誤清單** 中顯示編譯器錯誤。

2. 如果您不想要啟用 `Option Strict` ，請在您的程式碼中搜尋未指定類型的任何變數 (`Dim x` 而不是 `Dim x As String`) ，然後將所需的類型加入至宣告。

3. 請確定您未參考已設定為的物件變數 `Nothing` 。  搜尋您的程式碼中的關鍵字 `Nothing` ，並修改您的程式碼，使物件在 `Nothing` 您參考它之前都不會設定為。

4. 在您存取陣列變數之前，請先確定其已建立維度。 當您第一次建立陣列 (`Dim x(5) As String` 而不是) 時，您可以指派維度 `Dim x() As String` ，或在 `ReDim` 第一次存取陣列之前使用關鍵字來設定陣列的維度。

5. 請確定您的 `With` 區塊是藉由執行 `With` 語句進入點來初始化。

## <a name="see-also"></a>另請參閱

- [物件變數宣告](../../programming-guide/language-features/variables/object-variable-declaration.md)
- [ReDim 陳述式](../statements/redim-statement.md)
- [With...End With 陳述式](../statements/with-end-with-statement.md)
