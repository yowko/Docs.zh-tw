---
title: "How to: Read Text from Files with a StreamReader (Visual Basic) | Microsoft Docs"
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
  - "reading files, text"
  - "text, reading from files"
  - "reading text from files"
  - "files, reading"
ms.assetid: 384033c6-18f9-4d59-9610-36371226558f
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# How to: Read Text from Files with a StreamReader (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

`My.Computer.FileSystem` 物件會提供方法，以開啟 <xref:System.IO.TextReader> 和 <xref:System.IO.TextWriter>。  這些方法 \(`OpenTextFileWriter` 和 `OpenTextFileReader`\) 是進階方法，除非您選取 \[**全部**\] 索引標籤，否則不會出現在 IntelliSense 中。  
  
### 若要以文字讀取器讀取檔案中的行  
  
-   使用 `OpenTextFileReader` 方法，開啟 <xref:System.IO.TextReader> \(其中已指定檔案\)。  此範例會開啟名為 `testfile.txt` 的檔案、讀取該檔案中的行，然後在訊息方塊中顯示該行。  
  
     [!code-vb[VbFileIORead#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-read-text-from-fi_1.vb)]  
  
## 穩固程式設計  
 讀取的檔案必須是文字檔。  
  
 請勿根據檔案名稱來判斷檔案內容。  例如，檔案 Form1.vb 可能不是 Visual Basic 原始程式檔。  
  
 在應用程式中使用這些資料之前，請先驗證所有輸入值。  檔案內容可能與預期不同，而且從檔案讀取資料的方法可能會失敗。  
  
## .NET Framework 安全性  
 若要從檔案讀取，組件 \(Assembly\) 需要 <xref:System.Security.Permissions.FileIOPermission> 類別 \(Class\) 所授與的權限層級。  如果是在部分信任的內容中執行，則程式碼可能會因權限不足而擲回例外狀況。  如需詳細資訊，請參閱[Code Access Security Basics](../Topic/Code%20Access%20Security%20Basics.md)。  使用者也需要存取檔案。  如需詳細資訊，請參閱 [ACL Technology Overview](http://msdn.microsoft.com/zh-tw/06fbf66d-6f02-4378-b863-b2f12e349045)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:System.Windows.Forms.OpenFileDialog>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileReader%2A>   
 [SaveFileDialog 元件](../Topic/SaveFileDialog%20Component%20\(Windows%20Forms\).md)   
 [Reading from Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)