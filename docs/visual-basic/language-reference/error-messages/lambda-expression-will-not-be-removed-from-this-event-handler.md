---
title: Lambda 運算式將不會從這個事件處理常式中移除
ms.date: 07/20/2015
f1_keywords:
- bc42326
- vbc42326
helpviewer_keywords:
- BC42326
ms.assetid: 63214dc6-0112-4245-8ebf-7c9e8f5a5782
ms.openlocfilehash: 07ace3f1b9c5e512227dc1f718ef768b631c8303
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397372"
---
# <a name="lambda-expression-will-not-be-removed-from-this-event-handler"></a>Lambda 運算式將不會從這個事件處理常式中移除

Lambda 運算式將不會從這個事件處理常式中移除。 將 lambda 運算式指派給變數，並使用變數來加入和移除事件。

當 lambda 運算式與事件處理常式搭配使用時，您可能不會看到預期的行為。 編譯器會針對每個 lambda 運算式定義產生新的方法，即使兩者相同也是一樣。 因此，下列程式碼會顯示 `False` 。

```vb
Module Module1

    Sub Main()
        Dim fun1 As ChangeInteger = Function(p As Integer) p + 1
        Dim fun2 As ChangeInteger = Function(p As Integer) p + 1
        Console.WriteLine(fun1 = fun2)
    End Sub

    Delegate Function ChangeInteger(ByVal x As Integer) As Integer

End Module
```

當 lambda 運算式與事件處理常式搭配使用時，這可能會導致非預期的結果。 在下列範例中， `AddHandler` 語句不會移除加入的 lambda 運算式 `RemoveHandler` 。

```vb
Module Module1

    Event ProcessInteger(ByVal x As Integer)

    Sub Main()

        ' The following line adds one listener to the event.
        AddHandler ProcessInteger, Function(m As Integer) m

        ' The following statement searches the current listeners
        ' for a match to remove. However, this lambda is not the same
        ' as the previous one, so nothing is removed.
        RemoveHandler ProcessInteger, Function(m As Integer) m

    End Sub
End Module
```

根據預設，這個訊息是一個警告。 如需如何隱藏警告或將警告視為錯誤的詳細資訊，請參閱 [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)。

**錯誤識別碼：** BC42326

## <a name="to-correct-this-error"></a>更正這個錯誤

若要避免警告並移除 lambda 運算式，請將 lambda 運算式指派給變數，並在和語句中使用變數 `AddHandler` `RemoveHandler` ，如下列範例所示。

```vb
Module Module1

    Event ProcessInteger(ByVal x As Integer)

    Dim PrintHandler As ProcessIntegerEventHandler

    Sub Main()

        ' Assign the lambda expression to a variable.
        PrintHandler = Function(m As Integer) m

        ' Use the variable to add the listener.
        AddHandler ProcessInteger, PrintHandler

        ' Use the variable again when you want to remove the listener.
        RemoveHandler ProcessInteger, PrintHandler

    End Sub
End Module
```

## <a name="see-also"></a>另請參閱

- [Lambda 運算式](../../programming-guide/language-features/procedures/lambda-expressions.md)
- [寬鬆委派轉換](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [事件](../../programming-guide/language-features/events/index.md)
