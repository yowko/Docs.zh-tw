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
ms.openlocfilehash: d6708ee13963aaae43a73b159032f64f0fffac10
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91072206"
---
# <a name="main-procedure-in-visual-basic"></a>Visual Basic 中的 Main 程序

每個 Visual Basic 的應用程式都必須包含一個稱為的程式 `Main` 。 此程式可作為應用程式的起點和整體控制。 `Main`當程式載入您的應用程式，並準備好將控制權傳遞給它時，.NET Framework 會呼叫您的程式。 除非您要建立 Windows Forms 應用程式，否則您必須 `Main` 針對自己執行的應用程式撰寫程式。

 `Main` 包含先執行的程式碼。 在中 `Main` ，您可以決定要在程式啟動時先載入的表單、找出應用程式的複本是否已在系統上執行、為您的應用程式建立一組變數，或是開啟應用程式所需的資料庫。

## <a name="requirements-for-the-main-procedure"></a>主要程式的需求

 在自己的 (上執行的檔案通常使用副檔名) 必須包含程式 `Main` 。 程式庫 (例如副檔名為 .dll) 不會自行執行，也不需要程式 `Main` 。 您可以建立的不同專案類型的需求如下：

- 主控台應用程式會自行執行，而且您必須至少提供一個程式 `Main` 。

- Windows Forms 的應用程式會自行執行。 不過，Visual Basic 編譯器會 `Main` 在這類應用程式中自動產生程式，而您不需要撰寫一個程式。

- 類別庫不需要程式 `Main` 。 這些包括 Windows 控制項程式庫和 Web 控制項程式庫。 Web 應用程式會部署為類別庫。

## <a name="declaring-the-main-procedure"></a>宣告 Main 程式

 有四種方式可以宣告程式 `Main` 。 它可以採用引數，也可以傳回值。

> [!NOTE]
> 如果您 `Main` 在類別中宣告，則必須使用 `Shared` 關鍵字。 在模組中， `Main` 不需要是 `Shared` 。

- 最簡單的方式是宣告不 `Sub` 採用引數或傳回值的程式。

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- `Main` 也可以傳回 `Integer` 值，讓作業系統用來作為程式的結束代碼。 其他程式則可以藉由檢查 Windows ERRORLEVEL 值來測試此程式碼。 若要傳回結束代碼，您必須將宣告為程式， `Main` `Function` 而不是程式 `Sub` 。

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

- `Main` 也可以採用 `String` 陣列作為引數。 陣列中的每個字串都包含用來叫用程式的其中一個命令列引數。 您可以根據其值採取不同的動作。

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

- 您可以宣告 `Main` 以檢查命令列引數，但不會傳回結束代碼，如下所示。

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
- [整數資料類型](../../language-reference/data-types/integer-data-type.md)
- [String 資料類型](../../language-reference/data-types/string-data-type.md)
