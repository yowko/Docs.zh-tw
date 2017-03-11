---
title: "How to: Read From Fixed-width Text Files in Visual Basic | Microsoft Docs"
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
  - "fixed-width text file"
  - "reading text files, fixed-width"
  - "files, parsing"
  - "text files, tasks"
  - "text files, reading"
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 24
---
# How to: Read From Fixed-width Text Files in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

`TextFieldParser` 物件提供簡便且有效的方式來剖析結構化的文字檔，例如記錄檔。  
  
 `TextFieldType` 屬性會定義剖析的檔是分隔檔還是文字欄位寬度固定的檔案。  在固定寬度文字檔中，結尾欄位可以有可變寬度。  若要指定結尾欄位是否有可變寬度，請將其寬度定義為小於或等於零。  
  
### 若要剖析固定寬度的文字檔  
  
1.  建立新的 `TextFieldParser`。  下列程式碼會建立名為 `Reader` 的 `TextFieldParser`，並開啟檔案 `test.log`。  
  
     [!code-vb[VbFileIORead#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-read-from-fixed-w_1.vb)]  
  
2.  將 `TextFieldType` 屬性定義為 `FixedWidth`，並定義寬度和格式。  下列程式碼會定義文字的資料行：第一個資料行為 5 個字元寬、第二個為 10 個字元寬、第三個為 11 個字元寬，而第四個資料行的寬度是可變動的。  
  
     [!code-vb[VbFileIORead#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-read-from-fixed-w_2.vb)]  
  
3.  在檔案的欄位之間執行迴圈 \(Loop\)。  若有任何一行毀損，則報告錯誤並繼續剖析。  
  
     [!code-vb[VbFileIORead#11](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-read-from-fixed-w_3.vb)]  
  
4.  使用 `End While` 和 `End Using`，以關閉 `While` 和 `Using` 區塊。  
  
     [!code-vb[VbFileIORead#12](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-read-from-fixed-w_4.vb)]  
  
## 範例  
 這個範例會讀取檔案 `test.log`。  
  
 [!code-vb[VbFileIORead#13](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-read-from-fixed-w_5.vb)]  
  
## 穩固程式設計  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   不可以使用指定的格式剖析資料列 \(<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>\)。  例外狀況訊息會指出造成例外狀況的文字行，而 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> 屬性會指派給此行內含的文字。  
  
-   指定的檔案不存在 \(<xref:System.IO.FileNotFoundException>\)。  
  
-   發生使用者權限不足而無法存取檔案的部分信任狀況   \(<xref:System.Security.SecurityException>\).  
  
-   路徑太長 \(<xref:System.IO.PathTooLongException>\)。  
  
-   使用者沒有足夠的使用權限可以存取檔案 \(<xref:System.UnauthorizedAccessException>\)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=fullName>   
 [How to: Read From Comma\-Delimited Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)   
 [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)   
 [Parsing Text Files with the TextFieldParser Object](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)   
 [Walkthrough: Manipulating Files and Directories in Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)   
 [Troubleshooting: Reading from and Writing to Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)   
 [疑難排解例外狀況：Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException](../Topic/Troubleshooting%20Exceptions:%20Microsoft.VisualBasic.FileIO.TextFieldParser.MalformedLineException.md)