---
title: 運算式是一個數值，不可以是指派的目標
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: d5aae4d30abbf9ed2af260412352a5e0452e0dcc
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513041"
---
# <a name="expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a>運算式是一個數值，不可以是指派的目標

語句會嘗試將值指派給運算式。 您只能在執行時間, 將值指派給可寫入的變數、屬性或陣列元素。 下列範例說明此錯誤的發生方式。

```vb
Dim yesterday As Integer
ReadOnly maximum As Integer = 45
yesterday + 1 = DatePart(DateInterval.Day, Now)
' The preceding line is an ERROR because of an expression on the left.
maximum = 50
' The preceding line is an ERROR because maximum is declared ReadOnly.
```

類似的範例可能適用于屬性和陣列元素。

**間接存取。** 透過實值型別的間接存取也會產生此錯誤。 請考慮下列<xref:System.Drawing.Point>程式碼範例, 它會嘗試透過<xref:System.Windows.Forms.Control.Location%2A>間接存取來設定的值。

```vb
' Assume this code runs inside Form1.
Dim exitButton As New System.Windows.Forms.Button()
exitButton.Text = "Exit this form"
exitButton.Location.X = 140
' The preceding line is an ERROR because of no storage for Location.
```

前述範例的最後一個語句會失敗, 因為它只會針對<xref:System.Drawing.Point> <xref:System.Windows.Forms.Control.Location%2A>屬性所傳回的結構建立暫存配置。 結構是實值型別, 而且在執行語句之後, 不會保留暫存結構。 此問題的解決方式是宣告和使用的變數<xref:System.Windows.Forms.Control.Location%2A>, 這會為<xref:System.Drawing.Point>結構建立更永久的配置。 下列範例顯示的程式碼可以取代先前範例中的最後一個語句。

```vb
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)
exitButton.Location = exitLocation
```

**錯誤識別碼:** BC30068

## <a name="to-correct-this-error"></a>更正這個錯誤

- 如果語句將值指派給運算式, 請將運算式取代為單一可寫入的變數、屬性或陣列元素。

- 如果語句透過實值型別 (通常是結構) 進行間接存取, 請建立變數來保存實值型別。

- 將適當的結構 (或其他實數值型別) 指派給變數。

- 使用變數來存取屬性, 以將值指派給它。

## <a name="see-also"></a>另請參閱

- [運算子和運算式](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [陳述式](../../../visual-basic/programming-guide/language-features/statements.md)
- [程序的疑難排解](../../../visual-basic/programming-guide/language-features/procedures/troubleshooting-procedures.md)
