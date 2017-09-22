---
title: "如何：在 Visual Basic 中以多種格式從文字檔讀取"
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
- TextFieldParser object, reading from a file
- TextFieldType enumeration
- My.Computer.FileSystem.WriteAllText method, parsing structured text files
- WriteAllText method, parsing structured text files
- PeekChars method, determining format of text
- reading text files, multiple formats
- I/O [Visual Basic], reading text files
- text files, reading
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: be085e5a0f7a57890893ba310db3c66480b300da
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# How to: Read From Text Files with Multiple Formats in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.FileIO.TextFieldParser> 物件提供簡便且有效的方式來剖析結構化的文字檔，例如記錄檔。  您可以使用 `PeekChars` 方法處理具有多種格式的檔案，以便在剖析整個檔案時判斷每一行的格式。  
  
### 若要剖析具有多種格式的文字檔  
  
1.  將名為 testfile.txt 的文字檔加入至專案。  將下列內容加入至文字檔中。  
  
    ```  
    Err  1001 Cannot access resource.  
    Err  2014 Resource not found.  
    Acc  10/03/2009User1      Administrator.  
    Err  0323 Warning: Invalid access attempt.  
    Acc  10/03/2009User2      Standard user.  
    Acc  10/04/2009User2      Standard user.  
    ```  
  
2.  定義預期的格式，以及報告錯誤時要使用的格式。  每個陣列中的最後一個項目為 \-1，因此最後一個欄位被假設具有可變寬度的性質。  陣列中的最後一個項目小於或等於 0 時，就會發生此情形。  
  
     [!code-vb[VbFileIORead#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_1.vb)]  
  
3.  建立新的 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> 物件，定義寬度和格式。  
  
     [!code-vb[VbFileIORead#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_2.vb)]  
  
4.  對資料列進行迴圈 \(Loop\)，在讀取之前先測試格式。  
  
     [!code-vb[VbFileIORead#6](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_3.vb)]  
  
5.  將錯誤寫入至主控台 \(Console\)。  
  
     [!code-vb[VbFileIORead#7](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_4.vb)]  
  
## 範例  
 以下是示範讀取 `testfile.txt` 檔案的完整範例。  
  
 [!code-vb[VbFileIORead#8](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files-with-multiple-formats_5.vb)]  
  
## 穩固程式設計  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   不可以使用指定的格式剖析資料列 \(<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>\)。  例外狀況訊息會指出造成例外狀況的文字行，而 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> 屬性會指派給此行內含的文字。  
  
-   指定的檔案不存在 \(<xref:System.IO.FileNotFoundException>\)。  
  
-   發生使用者權限不足而無法存取檔案的部分信任狀況   \(<xref:System.Security.SecurityException>\).  
  
-   路徑太長 \(<xref:System.IO.PathTooLongException>\)。  
  
-   使用者沒有足夠的使用權限可以存取檔案 \(<xref:System.UnauthorizedAccessException>\)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>   
 <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>   
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>   
 [如何：從逗號分隔文字檔讀取](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)   
 [如何：從固定寬度的文字檔讀取](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)   
 [使用 TextFieldParser 物件剖析文字檔](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)

