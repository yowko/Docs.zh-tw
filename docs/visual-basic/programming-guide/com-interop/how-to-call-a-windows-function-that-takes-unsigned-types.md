---
title: "如何︰ 呼叫 Windows 函式會採用不帶正負號的類型 (Visual Basic) |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- Windows functions, calling
- unsigned data types
- UShort data type, using
- functions [Visual Basic], calling Windows functions
- ULong data type, using
- UInteger data type, using
- data types [Visual Basic], using
- unsigned types
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types, using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
caps.latest.revision: 18
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fbff07f4923b0633a2bc9b4fd558d9d51f64370a
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a>如何：呼叫使用不帶正負號類型的 Windows 函式 (Visual Basic)
如果您使用的類別、 模組或具有不帶正負號的整數類型的成員的結構，您可以存取這些成員與[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]。  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a>若要呼叫 Windows 函式採用不帶正負號的型別  
  
1.  使用[宣告陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)告知[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式庫包含函式、 其名稱為該文件庫中，其呼叫的順序為何，以及如何將字串轉換呼叫它時。  
  
2.  在`Declare`陳述式中，使用`UInteger`， `ULong`， `UShort`，或`Byte`視需要針對每個參數具有不帶正負號的類型。  
  
3.  若要尋找的名稱和值的常數，它會使用呼叫 Windows 函式，請參閱文件。 多個 WinUser.h 檔案中定義。  
  
4.  宣告在程式碼中必要的常數。 許多 Windows 常數是 32 位元不帶正負號的值，以及您應該將這些宣告`As``UInteger`。  
  
5.  以一般方式呼叫函數。 下列範例會呼叫 Windows 函式`MessageBox`，後者會採用不帶正負號的整數引數。  
  
    ```  
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
  
     您可以測試函式`messageThroughWindows`為下列程式碼。  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  `UInteger`， `ULong`， `UShort`，和`SByte`資料類型不屬於[語言獨立性以及與語言無關的元件](https://msdn.microsoft.com/library/12a7a7h3)(CLS)，所以符合 CLS 標準的程式碼無法使用它們使用的元件。  
  
    > [!IMPORTANT]
    >  呼叫 unmanaged 程式碼，例如 Windows 應用程式開發介面 (API)，會公開您的程式碼的潛在安全性風險。  
  
    > [!IMPORTANT]
    >  呼叫 Windows API 需要 unmanaged 程式碼權限，這可能會影響它在部分信任情況下執行。 如需詳細資訊，請參閱<xref:System.Security.Permissions.SecurityPermission>和[程式碼存取權限](http://msdn.microsoft.com/en-us/e5ae402f-6dda-4732-bbe8-77296630f675)。</xref:System.Security.Permissions.SecurityPermission>  
  
## <a name="see-also"></a>另請參閱  
 [資料型別](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [整數資料類型](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [UInteger 資料類型](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)   
 [Declare 陳述式](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [逐步解說：呼叫 Windows API](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
