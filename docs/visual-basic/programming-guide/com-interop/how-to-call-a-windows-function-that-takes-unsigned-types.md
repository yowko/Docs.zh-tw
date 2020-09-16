---
title: 作法：呼叫不帶正負號的類型的 Windows 函式
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
ms.openlocfilehash: 5b78c808de4a16060d37844ad0f17e89fa6f6d84
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90548074"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a>如何：呼叫使用不帶正負號類型的 Windows 函式 (Visual Basic)

如果您使用的類別、模組或結構具有不帶正負號整數類型的成員，您可以使用 Visual Basic 來存取這些成員。

## <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a>呼叫採用不帶正負號類型的 Windows 函數

1. 使用 [Declare 語句](../../language-reference/statements/declare-statement.md) 來告訴 Visual Basic 哪個程式庫持有函式、該程式庫中的名稱、其呼叫順序為何，以及如何在呼叫時轉換字串。

2. 在 `Declare` 語句中， `UInteger` `ULong` `UShort` `Byte` 針對每個具有不帶正負號類型的參數使用、、或。

3. 請參閱您要呼叫的 Windows 函式的檔，以尋找其所使用之常數的名稱和值。 其中許多都是在 WinUser 檔案中定義。

4. 在您的程式碼中宣告必要的常數。 許多 Windows 常數都是32位不帶正負號的值，您應該將其宣告 `As UInteger` 。

5. 以正常方式呼叫函數。 下列範例會呼叫 Windows 函 `MessageBox` 式，該函式接受不帶正負號的整數引數。

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

     您可以使用下列程式碼來測試函數 `messageThroughWindows` 。

    ```vb
    Public Sub consumeWindowsMessage()
        Dim w As New windowsMessage
        w.messageThroughWindows()
    End Sub
    ```

    > [!CAUTION]
    > `UInteger`、 `ULong` 、 `UShort` 和 `SByte` 資料類型不是[語言獨立性和語言獨立元件](../../../standard/language-independence-and-language-independent-components.md) (cls) 的一部分，因此符合 cls 標準的程式碼無法使用使用這些元件的元件。

    > [!IMPORTANT]
    > 呼叫非受控程式碼（例如 Windows 應用程式開發介面 (API) ）會將程式碼公開給潛在的安全性風險。

    > [!IMPORTANT]
    > 呼叫 Windows API 需要未受管理的程式碼許可權，在部分信任的情況下可能會影響它的執行。 如需詳細資訊，請參閱 <xref:System.Security.Permissions.SecurityPermission> 和程式 [代碼存取權限](/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100))。

## <a name="see-also"></a>另請參閱

- [Data types (資料類型)](../../language-reference/data-types/index.md)
- [整數資料類型](../../language-reference/data-types/integer-data-type.md)
- [UInteger 資料類型](../../language-reference/data-types/uinteger-data-type.md)
- [Declare Statement](../../language-reference/statements/declare-statement.md)
- [逐步解說：呼叫 Windows API](walkthrough-calling-windows-apis.md)
