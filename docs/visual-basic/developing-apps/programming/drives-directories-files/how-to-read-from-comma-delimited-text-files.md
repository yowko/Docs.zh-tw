---
title: "如何：在 Visual Basic 中從逗號分隔文字檔讀取"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- reading text files [Visual Basic], comma-delimited
- text files [Visual Basic], reading
ms.assetid: a8413fe4-0dba-49c8-8692-44fb67a9ec4f
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bd88762179d9760bcce37b4c500a2bb118e09173
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-comma-delimited-text-files-in-visual-basic"></a>如何：在 Visual Basic 中從逗號分隔文字檔讀取
`TextFieldParser` 物件可讓您輕鬆有效率地剖析結構化文字檔，例如記錄檔。 `TextFieldType` 屬性會定義檔案是有分隔符號的檔案，還是具有固定寬度文字欄位的檔案。  
  
### <a name="to-parse-a-comma-delimited-text-file"></a>剖析逗號分隔文字檔  
  
1.  建立新的 `TextFieldParser`。 下列程式碼會建立名為 `MyReader` 的 `TextFieldParser`，並開啟檔案 `test.txt`。  
  
     [!code-vb[VbFileIORead#15](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_1.vb)]  
  
2.  定義 `TextField` 類型和分隔符號。 下列程式碼會將 `TextFieldType` 屬性定義為 `Delimited`，並將分隔符號定義為 ","。  
  
     [!code-vb[VbFileIORead#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_2.vb)]  
  
3.  在檔案的欄位之間執行迴圈。 如果有任何一行損毀，即會報告錯誤並繼續剖析。 下列程式碼會在檔案之間執行迴圈，依序顯示每個欄位，並報告所有格式不正確的欄位。  
  
     [!code-vb[VbFileIORead#17](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_3.vb)]  
  
4.  使用 `End While` 和 `End Using` 關閉 `While` 和 `Using` 區塊。  
  
     [!code-vb[VbFileIORead#18](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_4.vb)]  
  
## <a name="example"></a>範例  
 此範例會從檔案 `test.txt` 讀取。  
  
 [!code-vb[VbFileIORead#19](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-comma-delimited-text-files_5.vb)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   無法使用指定格式剖析資料列 (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>)。 例外狀況訊息指出造成例外狀況的文字行，而 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> 屬性被指派至包含於該文字行中的文字。  
  
-   指定的檔案不存在 (<xref:System.IO.FileNotFoundException>)。  
  
-   發生使用者權限不足而無法存取檔案的部分信任狀況 (<xref:System.Security.SecurityException>)  
  
-   路徑太長 (<xref:System.IO.PathTooLongException>)。  
  
-   使用者沒有足夠權限以存取檔案 (<xref:System.UnauthorizedAccessException>)。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>  
 [如何：從固定寬度的文字檔讀取](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [如何：以多種格式從文字檔讀取](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [使用 TextFieldParser 物件剖析文字檔](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 [逐步解說：在 Visual Basic 中管理檔案和目錄](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 [疑難排解：讀取和寫入文字檔](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)
