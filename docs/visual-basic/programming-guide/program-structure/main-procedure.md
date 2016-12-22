---
title: "Main Procedure in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Main"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Main procedure"
  - "Main method [Visual Basic]"
  - "main function"
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Main Procedure in Visual Basic
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

每個 Visual Basic 應用程式都必須包含一個稱為 `Main` 的程序。  此程序做為起點，並負責應用程式的整體控制。  當 .NET Framework 已載入應用程式並準備好要將控制項傳遞給該應用程式時，會呼叫 `Main` 程序。  除非您要建立的是 Windows Form 應用程式，否則您必須為單獨執行的應用程式撰寫 `Main` 程序。  
  
 `Main` 包含第一個執行的程式碼。  在 `Main` 中，您可以判斷當程式啟動時最先載入的表單、查明應用程式的複本是否已經在系統上執行、為應用程式建立一組變數，或是開啟應用程式需要的資料庫。  
  
## Main 程序的需求  
 獨立執行的檔案 \(副檔名通常是 .exe\) 必須包含 `Main` 程序。  程式庫 \(例如副檔名為 .dll\) 不會獨立執行，因此不需要 `Main` 程序。  您可以建立之各種類型專案的需求如下：  
  
-   主控台應用程式會獨立執行，而且您必須至少提供一個 `Main` 程序。  .  
  
-   Windows Form 應用程式會獨立執行。  不過，Visual Basic 編譯器會在這種應用程式中自動產生 `Main` 程序，因此不需要您撰寫。  
  
-   類別庫 \(Class Library\) 不需要 `Main` 程序。  它們包括 Windows 控制項程式庫和 Web 控制項程式庫。  Web 應用程式會部署為類別庫。  
  
## 宣告 Main 程序  
 宣告 `Main` 程序有四種方式。  它不一定能使用引數，也不一定能傳回值。  
  
> [!NOTE]
>  如果您在類別中宣告 `Main`，就必須使用 `Shared` 關鍵字。  在模組中，`Main` 不需要是 `Shared`。  
  
-   最簡單的方法是宣告不使用引數或不傳回值的 `Sub` 程序。  
  
    ```  
    Module mainModule  
        Sub Main()  
            MsgBox("The Main procedure is starting the application.")  
            ' Insert call to appropriate starting place in your code.  
            MsgBox("The application is terminating.")  
        End Sub  
    End Module  
    ```  
  
-   `Main` 也可傳回 `Integer` 值，作業系統利用此值做為您程式的結束代碼 \(Exit Code\)。  其他程式可利用檢查 Windows ERRORLEVEL 值，來測試這個代碼。  若要傳回結束代碼，您必須將 `Main` 宣告為 `Function` 程序而不是 `Sub` 程序。  
  
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
  
-   `Main` 也可採用 `String` 陣列做為引數。  陣列中的每個字串都包含一個用來叫用 \(Invoke\) 程式的命令列引數。  您可以根據其值採取不同的動作。  
  
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
  
-   您可以宣告 `Main` 檢查命令列引數但不傳回結束代碼，如下所示。  
  
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
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>   
 <xref:System.Array.Length%2A>   
 <xref:Microsoft.VisualBasic.Information.UBound%2A>   
 [Structure of a Visual Basic Program](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)   
 [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/zh-tw/9d030b60-e148-4366-a462-69532f02294c)   
 [\/main](../../../visual-basic/reference/command-line-compiler/main.md)   
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)   
 [Sub Statement](../../../visual-basic/language-reference/statements/sub-statement.md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)   
 [Integer Data Type](../../../visual-basic/language-reference/data-types/integer-data-type.md)   
 [String Data Type](../../../visual-basic/language-reference/data-types/string-data-type.md)