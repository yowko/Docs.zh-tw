---
title: 變數 '<variablename>' 在封閉區塊中隱藏了變數
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: 408acaafd5e266266b5191313611b94b72a5c270
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92161344"
---
# <a name="bc30616-variable-variablename-hides-a-variable-in-an-enclosing-block"></a>BC30616：變數 ' \<variablename> ' 會隱藏封閉區塊中的變數

包含在區塊中的變數與另一個區域變數具有相同的名稱。

 **錯誤識別碼：** BC30616

## <a name="to-correct-this-error"></a>更正這個錯誤

- 重新命名封閉區塊中的變數，使其與任何其他本機變數不同。 例如：

    ```vb
    Dim a, b, x As Integer
    If a = b Then
       Dim y As Integer = 20 ' Uniquely named block variable.
    End If
    ```

- 此錯誤的常見原因是在 `Catch e As Exception` 事件處理常式內使用。 如果是這種情況，請為 `Catch` 區塊變數命名， `ex` 而不是 `e` 。

- 此錯誤的另一個常見來源，是嘗試存取在個別區塊的區塊中宣告的區域變數 `Try` `Catch` 。 若要修正這個錯誤，請在結構之外宣告變數 `Try...Catch...Finally` 。

## <a name="see-also"></a>另請參閱

- [Try...Catch...Finally 陳述式](../statements/try-catch-finally-statement.md)
- [變數宣告](../../programming-guide/language-features/variables/variable-declaration.md)
