---
title: HOW TO：呼叫採用不帶正負號類型的 Windows 函式（Visual Basic）
ms.date: 07/20/2015
helpviewer_keywords:
- Windows functions [Visual Basic], calling
- unsigned data types [Visual Basic]
- UShort data type [Visual Basic], using
- functions [Visual Basic], calling Windows functions
- ULong data type [Visual Basic], using
- UInteger data type [Visual Basic], using
- data types [Visual Basic], using
- unsigned types [Visual Basic]
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types [Visual Basic], using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
ms.openlocfilehash: 97075fb6149ed8c0ce06318d0e5bb6f01b841f30
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053319"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a>HOW TO：呼叫採用不帶正負號類型的 Windows 函式（Visual Basic）

如果您使用的類別、模組或結構具有不帶正負號整數類型的成員，您可以使用 Visual Basic 來存取這些成員。

## <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a>呼叫採用不帶正負號類型的 Windows 函式

1. 使用[Declare 語句](../../../visual-basic/language-reference/statements/declare-statement.md)來告訴 Visual Basic 哪一個程式庫包含函式、它在該程式庫中的名稱、其呼叫順序為何，以及如何在呼叫它時轉換字串。

2. `Byte` `UShort` `ULong` `UInteger`在語句中，針對具有不帶正負號類型的每個參數，使用、、或。 `Declare`

3. 請參閱您所呼叫之 Windows 函式的檔，以尋找其所使用之常數的名稱和值。 其中有許多都是在 WinUser 檔案中定義。

4. 在您的程式碼中宣告必要的常數。 許多 Windows 常數都是32位不帶正負號的值，您`As UInteger`應該將它們宣告為。

5. 以正常方式呼叫函式。 下列範例會呼叫 Windows `MessageBox`函式，它會採用不帶正負號的整數引數。

    ```vb
    Public Class windowsMessage
        Private Declare Auto Function mb Lib "user32.dll" Alias "MessageBox" (
            ByVal hWnd As Integer,
            ByVal lpText As String,
            ByVal lpCaption As String,
            ByVal uType As UInteger) As Integer
        Private Const MB_OK As UInteger = 0
        Private Const MB_ICONEXCLAMATION As UInteger = &H30
        Private Const IDOK As UInteger = 1
        Private Const IDCLOSE As UInteger = 8
        Private Const c As UInteger = MB_OK Or MB_ICONEXCLAMATION
        Public Function messageThroughWindows() As String
            Dim r As Integer = mb(0, "Click OK if you see this!",
                "Windows API call", c)
            Dim s As String = "Windows API MessageBox returned " &
                 CStr(r)& vbCrLf & "(IDOK = " & CStr(IDOK) &
                 ", IDCLOSE = " & CStr(IDCLOSE) & ")"
            Return s
        End Function
    End Class
    ```

     您可以使用下列程式`messageThroughWindows`代碼來測試函數。

    ```vb
    Public Sub consumeWindowsMessage()
        Dim w As New windowsMessage
        w.messageThroughWindows()
    End Sub
    ```

    > [!CAUTION]
    > `UInteger`、 、和`UShort`資料類型不是[語言獨立性和與語言無關的元件](../../../standard/language-independence-and-language-independent-components.md)（CLS）的一部分，因此符合 CLS 標準的程式碼無法取用使用它們的元件。 `SByte` `ULong`

    > [!IMPORTANT]
    > 呼叫非受控碼（例如 Windows 應用程式開發介面（API））會讓您的程式碼暴露于潛在的安全性風險下。

    > [!IMPORTANT]
    > 呼叫 Windows API 需要未受管理的程式碼許可權，這可能會影響在部分信任情況下的執行。 如需詳細資訊， <xref:System.Security.Permissions.SecurityPermission>請參閱和程式[代碼存取權限](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100))。

## <a name="see-also"></a>另請參閱

- [資料類型](../../../visual-basic/language-reference/data-types/index.md)
- [Integer 資料類型](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [UInteger 資料類型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)
- [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)
- [逐步解說：呼叫 Windows API](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
