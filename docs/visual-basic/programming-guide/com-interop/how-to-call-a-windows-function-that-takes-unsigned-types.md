---
title: "How to: Call a Windows Function that Takes Unsigned Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Windows functions, calling"
  - "unsigned data types"
  - "UShort data type, using"
  - "functions [Visual Basic], calling Windows functions"
  - "ULong data type, using"
  - "UInteger data type, using"
  - "data types [Visual Basic], using"
  - "unsigned types"
  - "data types [Visual Basic], unsigned"
  - "data types [Visual Basic], numeric"
  - "unsigned types, using"
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

如果您所使用的類別、模組或結構具有屬於不帶正負號整數 \(Unsigned Integer\) 型別的成員，則可以使用 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 存取這些成員。  
  
### 呼叫使用不帶正負號型別的 Windows 函式  
  
1.  使用 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)告知 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 是哪個程式庫保留了這個函式、這個函式在該程式庫中的名稱、這個函式的呼叫順序 \(Calling Sequence\)，以及呼叫這個函式時轉換字串的方式。  
  
2.  在 `Declare` 陳述式中，視需要針對每個不帶正負號型別的參數，使用 `UInteger`、`ULong`、`UShort` 或 `Byte`。  
  
3.  請參閱所要呼叫 Windows 函式的文件，了解這個函式可以使用的常數名稱和值。  其中許多常數都已定義在 WinUser.h 檔案中。  
  
4.  在程式碼中宣告必要的常數。  許多 Windows 常數都是 32 位元不帶正負號的值，您應該將這些常數宣告為 `As` `UInteger`。  
  
5.  以正常方式呼叫函式。  下列範例會呼叫 Windows 函式 `MessageBox`，此函式使用不帶正負號的整數 \(Unsigned Integer\) 引數。  
  
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
  
     您可以使用下列程式碼測試函式 `messageThroughWindows`。  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  由於 `UInteger`、`ULong`、`UShort` 和 `SByte` 資料型別不是 [語言獨立性以及與語言無關的元件](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) 標準的一部分，所以符合 CLS 標準的程式碼將無法利用使用這些資料型別的元件。  
  
    > [!IMPORTANT]
    >  呼叫 Windows 應用程式開發介面 \(Application Programming Interface，API\) 等這類的 Unmanaged 程式碼，可能會對您的程式碼造成安全性風險。  
  
    > [!IMPORTANT]
    >  呼叫 Windows API 需要 Unmanaged 程式碼的使用權限，該權限在部分信任的情況中，可能會影響 Windows API 的執行。  如需詳細資訊，請參閱 <xref:System.Security.Permissions.SecurityPermission> 和[Code Access Permissions](http://msdn.microsoft.com/zh-tw/e5ae402f-6dda-4732-bbe8-77296630f675)。  
  
## 請參閱  
 [Data Types](../../../visual-basic/language-reference/data-types/data-type-summary.md)   
 [Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [UInteger Data Type](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)   
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)