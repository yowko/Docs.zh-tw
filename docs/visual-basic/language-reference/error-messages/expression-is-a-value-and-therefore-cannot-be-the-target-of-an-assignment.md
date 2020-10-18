---
title: 運算式是一個數值，不可以是指派的目標
ms.date: 07/20/2015
f1_keywords:
- bc30068
- vbc30068
helpviewer_keywords:
- BC30068
ms.assetid: d65141e1-f31e-4ac5-a3b8-0b2e02a71ebf
ms.openlocfilehash: cd23e6c2beb2f93578a350bc41a780c9ab785f26
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160889"
---
# <a name="bc30068-expression-is-a-value-and-therefore-cannot-be-the-target-of-an-assignment"></a>BC30068： Expression 是一個值，因此不能是指派的目標

語句嘗試將值指派給運算式。 您只能在執行時間將值指派給可寫入的變數、屬性或陣列元素。 下列範例說明如何發生此錯誤。

```vb
Dim yesterday As Integer
ReadOnly maximum As Integer = 45
yesterday + 1 = DatePart(DateInterval.Day, Now)
' The preceding line is an ERROR because of an expression on the left.
maximum = 50
' The preceding line is an ERROR because maximum is declared ReadOnly.
```

類似的範例可能適用于屬性和陣列元素。

**間接存取。** 透過實值型別的間接存取也會產生這個錯誤。 請考慮下列程式碼範例，其會嘗試 <xref:System.Drawing.Point> 透過間接存取來設定的值 <xref:System.Windows.Forms.Control.Location%2A> 。

```vb
' Assume this code runs inside Form1.
Dim exitButton As New System.Windows.Forms.Button()
exitButton.Text = "Exit this form"
exitButton.Location.X = 140
' The preceding line is an ERROR because of no storage for Location.
```

上述範例的最後一個語句會失敗，因為它只會為屬性所傳回的結構建立暫存配置 <xref:System.Drawing.Point> <xref:System.Windows.Forms.Control.Location%2A> 。 結構是實值型別，而且在語句執行之後，不會保留暫存結構。 藉由宣告和使用的變數來解決此問題 <xref:System.Windows.Forms.Control.Location%2A> ，這會為結構建立更永久的配置 <xref:System.Drawing.Point> 。 下列範例顯示可取代上述範例中最後一個語句的程式碼。

```vb
Dim exitLocation as New System.Drawing.Point(140, exitButton.Location.Y)
exitButton.Location = exitLocation
```

**錯誤識別碼：** BC30068

## <a name="to-correct-this-error"></a>更正這個錯誤

- 如果語句將值指派給運算式，請以單一可寫入的變數、屬性或陣列元素來取代運算式。

- 如果語句透過實值型別進行間接存取 (通常是結構) ，請建立變數來保存實值型別。

- 將適當的結構 (或其他實值型別) 指派給變數。

- 您可以使用變數來存取屬性，將值指派給它。

## <a name="see-also"></a>另請參閱

- [運算子和運算式](../../programming-guide/language-features/operators-and-expressions/index.md)
- [陳述式](../../programming-guide/language-features/statements.md)
- [程序的疑難排解](../../programming-guide/language-features/procedures/troubleshooting-procedures.md)
