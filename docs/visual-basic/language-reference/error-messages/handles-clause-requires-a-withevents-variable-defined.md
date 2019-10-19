---
title: Handles 子句需要 WithEvents 變數，該變數定義於包含類型或它的一種基底類型中
ms.date: 07/20/2015
f1_keywords:
- vbc30506
- bc30506
helpviewer_keywords:
- BC30506
ms.assetid: 5b66f6a8-f050-4e03-a57f-a64e85f80cb5
ms.openlocfilehash: 191415408f607d0ff768e50c41fa9b3c4405a688
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582818"
---
# <a name="handles-clause-requires-a-withevents-variable-defined-in-the-containing-type-or-one-of-its-base-types"></a>Handles 子句需要 WithEvents 變數，該變數定義於包含類型或它的一種基底類型中

您未在 `Handles` 子句中提供 `WithEvents` 變數。 程式宣告結尾的 `Handles` 關鍵字會使它處理使用 `WithEvents` 關鍵字宣告之物件變數所引發的事件。

**錯誤識別碼：** BC30506

## <a name="to-correct-this-error"></a>更正這個錯誤

提供必要的 `WithEvents` 變數。

## <a name="example"></a>範例

在下列範例中，Visual Basic 會產生編譯器錯誤 `BC30506`，因為[WithEvents](../modifiers/withevents.md)關鍵字不會用於 <xref:System.Timers.Timer?displayProperty=nameWithType> 實例的定義中。

```vb
Imports System.Timers

Module Module1
    Private _timer1 As New Timer() With {.Interval = 1000, .Enabled = True}

    Sub Main()
        Console.WriteLine("Press any key to start the timer...")
        Console.ReadKey()
        _timer1.Start()
        Console.ReadKey()
    End Sub

    Private Sub Timer1_Tick(sender As Object, args As EventArgs) Handles _timer1.Elapsed
        Console.WriteLine("Press any key to terminate...")
    End Sub
End Module
```

下列範例會成功編譯，因為 `_timer1` 變數是以 `WithEvents` 關鍵字定義的：

```vb
Imports System.Timers

Module Module1
    Private WithEvents _timer1 As New Timer() With {.Interval = 1000}

    Sub Main()
        Console.WriteLine("Press any key to start the timer...")
        Console.ReadKey()
        _timer1.Start()
        Console.ReadKey()
    End Sub

    Private Sub Timer1_Tick(sender As Object, args As EventArgs) Handles _timer1.Elapsed
        Console.WriteLine("Press any key to terminate...")
    End Sub

End Module
```

## <a name="see-also"></a>請參閱

- [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
