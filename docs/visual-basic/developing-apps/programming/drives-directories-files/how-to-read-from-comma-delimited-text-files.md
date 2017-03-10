---
title: "How to: Read From Comma-Delimited Text Files in Visual Basic | Microsoft Docs"
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
  - "files, parsing"
  - "text files, tasks"
  - "reading text files, comma-delimited"
  - "text files, reading"
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# How to: Read From Comma-Delimited Text Files in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

`TextFieldParser` 物件提供簡便且有效的方式來剖析結構化的文字檔，例如記錄檔。  `TextFieldType` 屬性 \(Property\) 會定義檔案是否為分隔的檔案，或是具有固定寬度文字欄位的檔案。  
  
### 若要剖析以逗號分隔的文字檔  
  
1.  建立新的 `TextFieldParser`。  下列程式碼會建立名為 `MyReader` 的 `TextFieldParser`，並開啟檔案 `test.txt`。  
  
     [!code-vb[VbFileIORead#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-read-from-comma-d_1.vb)]  
  
2.  定義 `TextField` 型別和分隔符號 \(Delimiter\)。  下列程式碼會將 `TextFieldType` 屬性定義為 `Delimited`，並將分隔符號定義為 ","。  
  
     [!code-vb[VbFileIORead#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-read-from-comma-d_2.vb)]  
  
3.  在檔案的欄位之間執行迴圈 \(Loop\)。  如果有任何一行損毀，即會報告錯誤並繼續剖析。  下列程式碼會在檔案之間執行迴圈，依序顯示每個欄位，並報告所有格式不正確的欄位。  
  
     [!code-vb[VbFileIORead#17](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-read-from-comma-d_3.vb)]  
  
4.  使用 `End While` 和 `End Using`，以關閉 `While` 和 `Using` 區塊。  
  
     [!code-vb[VbFileIORead#18](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-read-from-comma-d_4.vb)]  
  
## 範例  
 這個範例會讀取檔案 `test.txt`。  
  
 [!code-vb[VbFileIORead#19](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-read-from-comma-d_5.vb)]  
  
## 穩固程式設計  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   不可以使用指定的格式剖析資料列 \(<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>\)。  例外狀況訊息會指出造成例外狀況的文字行，而 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> 屬性會指派給此行內含的文字。  
  
-   指定的檔案不存在 \(<xref:System.IO.FileNotFoundException>\)。  
  
-   發生使用者權限不足而無法存取檔案的部分信任狀況   \(<xref:System.Security.SecurityException>\).  
  
-   路徑太長 \(<xref:System.IO.PathTooLongException>\)。  
  
-   使用者沒有足夠的使用權限可以存取檔案 \(<xref:System.UnauthorizedAccessException>\)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=fullName>   
 [How to: Read From Fixed\-width Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)   
 [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)   
 [Parsing Text Files with the TextFieldParser Object](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)   
 [Walkthrough: Manipulating Files and Directories in Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)   
 [Troubleshooting: Reading from and Writing to Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)   
 [疑難排解例外狀況：Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException](../Topic/Troubleshooting%20Exceptions:%20Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException.md)