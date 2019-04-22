---
title: Visual Basic 中的 Main 程序
ms.date: 07/20/2015
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
ms.openlocfilehash: 641edd2d0e0dde5f509c8fa77ccf65358fa76a31
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "58833663"
---
# <a name="main-procedure-in-visual-basic"></a>Visual Basic 中的 Main 程序
每個 Visual Basic 應用程式必須包含呼叫的程序`Main`。 起始點和應用程式的整體控制，就會作為此程序。 .NET Framework 會呼叫您`Main`時它已載入您的應用程式，並已準備好將控制權傳給它的程序。 除非您要建立的 Windows Forms 應用程式，您必須撰寫`Main`上執行自己的應用程式的程序。  
  
 `Main` 包含會先執行程式碼。 在  `Main`，您可以判斷哪一個表單是在程式啟動時，第一次載入、 找出您的應用程式的複本是否已執行系統上，為您的應用程式中，建立一組變數或開啟應用程式所需的資料庫。  
  
## <a name="requirements-for-the-main-procedure"></a>在主要程序的需求  
 （通常具有副檔名.exe) 單獨執行的檔案必須包含`Main`程序。 無法在執行它自己的程式庫 （例如.dll 副檔名)，而且不需要`Main`程序。 您可以建立不同類型的專案的需求如下所示：  
  
-   主控台應用程式上執行其本身，而您則必須提供至少一個`Main`程序。 。  
  
-   Windows Forms 應用程式上執行自己。 不過，Visual Basic 編譯器會自動產生`Main`程序，在這類應用程式，而且您不需要撰寫一個。  
  
-   類別庫不需要`Main`程序。 其中包括 Windows 控制項程式庫和 Web 控制項程式庫。 Web 應用程式會部署為類別庫。  
  
## <a name="declaring-the-main-procedure"></a>宣告的 Main 程序  
 有四種方式來宣告`Main`程序。 它可以接受引數，和與否，它可以傳回值。  
  
> [!NOTE]
>  如果您宣告`Main`在類別中，您必須使用`Shared`關鍵字。 在模組中，`Main`不需要是`Shared`。  
  
-   最簡單的方式是將宣告`Sub`不接受引數或傳回值的程序。  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   `Main` 也可以傳回`Integer`作業系統做為您的程式結束代碼的值。 其他程式可以測試此程式碼檢查 Windows ERRORLEVEL 值。 若要傳回的結束代碼，您必須宣告`Main`作為`Function`程序，而不是`Sub`程序。  
  
    ```  
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
  
-   `Main` 也可以採用`String`做為引數的陣列。 陣列中的每個字串會包含用來叫用程式的命令列引數之一。 您可以採取不同的動作，取決於其值。  
  
    ```  
    Module mainModule  
        Function Main(ByVal cmdArgs() As String) As Integer  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
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
  
-   您可以宣告`Main`檢查命令列引數，但不會傳回結束程式碼，如下所示。  
  
    ```  
    Module mainModule  
        Sub Main(ByVal cmdArgs() As String)  
            MsgBox("The Main procedure is starting the application.")  
            Dim returnValue As Integer = 0  
            ' See if there are any arguments.  
            If cmdArgs.Length > 0 Then  
                For argNum As Integer = 0 To UBound(cmdArgs, 1)  
                    ' Insert code to examine cmdArgs(argNum) and take  
                    ' appropriate action based on its value.  
                Next argNum  
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
- [Visual Basic 程式的結構](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [/main](../../../visual-basic/reference/command-line-compiler/main.md)
- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Sub 陳述式](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Function 陳述式](../../../visual-basic/language-reference/statements/function-statement.md)
- [Integer 資料類型](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [String 資料類型](../../../visual-basic/language-reference/data-types/string-data-type.md)
