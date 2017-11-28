---
title: "如何：在 Visual Basic 中從固定寬度的文字檔讀取"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- fixed-width text file
- reading text files [Visual Basic], fixed-width
- files [Visual Basic], parsing
- text files [Visual Basic], tasks
- text files [Visual Basic], reading
ms.assetid: 99be5692-967a-4e85-993e-cd18139a5a69
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a5caa124af1bf4681a4c061f453ce5e09ec2dae7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-from-fixed-width-text-files-in-visual-basic"></a>如何：在 Visual Basic 中從固定寬度的文字檔讀取
`TextFieldParser` 物件可讓您輕鬆有效率地剖析結構化文字檔，例如記錄檔。  
  
 `TextFieldType` 屬性會定義所剖析的檔案是有分隔符號的檔案，還是具有固定寬度文字欄位的檔案。 在固定寬度的文字檔中，結尾欄位可以有可變寬度。 若要指定結尾欄位是否有可變寬度，請將其寬度定義為小於或等於零。  
  
### <a name="to-parse-a-fixed-width-text-file"></a>剖析固定寬度的文字檔  
  
1.  建立新的 `TextFieldParser`。 下列程式碼會建立名為 `Reader` 的 `TextFieldParser`，並開啟檔案 `test.log`。  
  
     [!code-vb[VbFileIORead#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_1.vb)]  
  
2.  將 `TextFieldType` 屬性定義為 `FixedWidth`，並定義寬度和格式。 下列程式碼會定義文字的資料行：第一個資料行為 5 個字元寬、第二個資料行為 10 個字元寬、第三個資料行為 11 個字元寬，而第四個資料行的寬度是可變動的。  
  
     [!code-vb[VbFileIORead#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_2.vb)]  
  
3.  在檔案的欄位之間執行迴圈。 如果有任何一行損毀，即會報告錯誤並繼續剖析。  
  
     [!code-vb[VbFileIORead#11](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_3.vb)]  
  
4.  使用 `End While` 和 `End Using` 關閉 `While` 和 `Using` 區塊。  
  
     [!code-vb[VbFileIORead#12](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_4.vb)]  
  
## <a name="example"></a>範例  
 此範例會從檔案 `test.log` 讀取。  
  
 [!code-vb[VbFileIORead#13](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-fixed-width-text-files_5.vb)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   無法使用指定格式剖析資料列 (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>)。 例外狀況訊息指出造成例外狀況的文字行，而 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> 屬性被指派至包含於該文字行中的文字。  
  
-   指定的檔案不存在 (<xref:System.IO.FileNotFoundException>)。  
  
-   發生使用者權限不足而無法存取檔案的部分信任狀況 (<xref:System.Security.SecurityException>)  
  
-   路徑太長 (<xref:System.IO.PathTooLongException>)。  
  
-   使用者沒有足夠權限以存取檔案 (<xref:System.UnauthorizedAccessException>)。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>  
 [如何：從逗號分隔文字檔讀取](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [如何：以多種格式從文字檔讀取](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [使用 TextFieldParser 物件剖析文字檔](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)  
 [逐步解說：在 Visual Basic 中管理檔案和目錄](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 [疑難排解：讀取和寫入文字檔](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 
