---
title: 主要程序
ms.date: 07/20/2015
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
ms.openlocfilehash: cf6003206566dfe8f70a7f75cd4d7ec7565794a5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403170"
---
# <a name="main-procedure-in-visual-basic"></a>Visual Basic 中的 Main 程序
每個 Visual Basic 應用程式都必須包含名為的程式 `Main` 。 此程式可做為您應用程式的起點和整體控制。 .NET Framework `Main` 會在載入您的應用程式並準備好將控制權傳遞給它時，呼叫您的程式。 除非您要建立 Windows Forms 應用程式，否則必須 `Main` 針對自己執行的應用程式撰寫程式。

 `Main`包含第一個執行的程式碼。 在中 `Main` ，您可以決定要在程式啟動時先載入哪一個表單、找出應用程式的複本是否已經在系統上執行、為您的應用程式建立一組變數，或是開啟應用程式所需的資料庫。

## <a name="requirements-for-the-main-procedure"></a>主要程式的需求
 本身本身執行的檔案（通常副檔名為 .exe）必須包含一個程式 `Main` 。 程式庫（例如，副檔名為 .dll）本身不會執行，也不需要程式 `Main` 。 您可以建立的不同專案類型的需求如下：

- 主控台應用程式會自行執行，而且您必須至少提供一個程式 `Main` 。

- Windows Forms 應用程式會自行執行。 不過，Visual Basic 編譯器會自動 `Main` 在這類應用程式中產生程式，而您不需要撰寫一個。

- 類別庫不需要程式 `Main` 。 其中包括 Windows 控制項程式庫和 Web 控制項程式庫。 Web 應用程式會部署為類別庫。

## <a name="declaring-the-main-procedure"></a>宣告 Main 程式
 有四種方式可以宣告程式 `Main` 。 它可以接受引數，也可以傳回值。

> [!NOTE]
> 如果您 `Main` 在類別中宣告，則必須使用 `Shared` 關鍵字。 在模組中， `Main` 不需要是 `Shared` 。

- 最簡單的方式是宣告不 `Sub` 接受引數或傳回值的程式。

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- `Main`也可以傳回 `Integer` 值，以供作業系統用來做為程式的結束代碼。 其他程式則可以藉由檢查 Windows ERRORLEVEL 值來測試此程式碼。 若要傳回結束代碼，您必須將宣告為程式， `Main` `Function` 而不是程式 `Sub` 。

    ```vb
    Module mainModule
        Function Main() As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' Insert call to appropriate starting place in your code.
            ' On return, assign appropriate value to returnValue.
            ' 0 usually means successful completion.
            MsgBox("The application is terminating with error level " &
                 CStr(returnValue) & ".")
            Return returnValue
        End Function
    End Module
    ```

- `Main`也可以採用 `String` 陣列做為引數。 陣列中的每個字串都包含用來叫用程式的其中一個命令列引數。 您可以根據它們的值來採取不同的動作。

    ```vb
    Module mainModule
        Function Main(ByVal cmdArgs() As String) As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
            End If
            ' Insert call to appropriate starting place in your code.
            ' On return, assign appropriate value to returnValue.
            ' 0 usually means successful completion.
            MsgBox("The application is terminating with error level " &
                 CStr(returnValue) & ".")
            Return returnValue
        End Function
    End Module
    ```

- 您可以宣告 `Main` 來檢查命令列引數，但不會傳回結束代碼，如下所示。

    ```vb
    Module mainModule
        Sub Main(ByVal cmdArgs() As String)
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
            End If
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [Visual Basic 程式的結構](structure-of-a-visual-basic-program.md)
- [-main](../../reference/command-line-compiler/main.md)
- [共用][](../../language-reference/modifiers/shared.md)
- [Sub 陳述式](../../language-reference/statements/sub-statement.md)
- [Function 陳述式](../../language-reference/statements/function-statement.md)
- [Integer 資料類型](../../language-reference/data-types/integer-data-type.md)
- [String 資料類型](../../language-reference/data-types/string-data-type.md)
