---
title: "How to: Dispose of a System Resource (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Using statement, disposing of system resources"
  - "Visual Basic code, control flow"
  - "system resources, disposing of"
  - "resources [Visual Basic], disposing of system"
  - "system resources"
  - "Using statement, Using...End Using"
  - "Using block"
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
caps.latest.revision: 15
caps.handback.revision: 15
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Dispose of a System Resource (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

您可以使用 `Using` 區塊，保證當程式碼結束這個區塊時，系統會處置 \(Dispose\) 資源。  如果您所使用的系統資源會消耗大量記憶體，或是其他元件也要使用此系統資源，則這個方法非常有用。  
  
### 在程式碼結束使用資料庫連接時，處置資料庫連接  
  
1.  確定您已在原始程式檔 \(Source File\) 的開頭，為資料庫連接加入適當的 [Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) \(在此範例中為 <xref:System.Data.SqlClient>\)。  
  
2.  使用 `Using` 和 `End Using` 陳述式來建立 `Using` 區塊。  在區塊內，放入處理資料庫連接的程式碼。  
  
3.  在 `Using` 陳述式中，宣告連接並建立連接的執行個體 \(Instance\)。  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     不論您是如何結束這個區塊 \(包括因未處理的例外狀況 \(Exception\) 而造成區塊結束\)，系統都會處置 \(Dispose\) 資源。  
  
     請注意，因為 `sqc` 的範圍 \(Scope\) 僅限於 `Using` 區塊，所以無法從這個區塊之外的地方進行存取。  
  
     您可以對像是檔案控制代碼 \(File Handle\) 或 COM 包裝函式這類的系統資源，使用這套相同的技術。  您可以使用 `Using` 區塊，確保在結束 `Using` 區塊後，其他元件能夠繼續使用資源。  
  
## 請參閱  
 <xref:System.Data.SqlClient.SqlConnection>   
 [Control Flow](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)   
 [Decision Structures](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)   
 [Loop Structures](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)   
 [Other Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)   
 [Nested Control Structures](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)   
 [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md)