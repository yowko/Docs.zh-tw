---
title: "如何：在 Visual Basic 中將具有特定模式的檔案複製到目錄"
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
- My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]
- files, copying
- CopyFile method, copying files in Visual Basic
- I/O [Visual Basic], copying files
ms.assetid: f205d2ad-bbe5-4d55-8a40-acda21aa82dd
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 812fd59769da386f8d0b81eb80a4cd93c9764534
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-copy-files-with-a-specific-pattern-to-a-directory-in-visual-basic"></a>如何：在 Visual Basic 中將具有特定模式的檔案複製到目錄
<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> 方法會傳回代表檔案路徑名稱的唯讀字串集合。 您可以使用 `wildCards` 參數指定特定模式。  
  
 如果找不到相符的檔案，則會傳回空集合。  
  
 您可以使用 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A> 方法，將檔案複製至目錄。  
  
### <a name="to-copy-files-with-a-specific-pattern-to-a-directory"></a>將具有特定模式的檔案複製至目錄  
  
1.  使用 `GetFiles` 方法來傳回檔案清單。 這個範例會傳回所指定目錄中的所有 .rtf 檔案。  
  
     [!code-vb[VbFileIOMisc#36](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_1.vb)]  
  
2.  使用 `CopyFile` 方法來複製檔案。 這個範例會將檔案複製至名稱為 `testdirectory`的目錄中。  
  
     [!code-vb[VbVbcnMyFileSystem#88](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_2.vb)]  
  
3.  使用 `For` 陳述式來關閉 `Next` 陳述式。  
  
     [!code-vb[VbVbcnMyFileSystem#89](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_3.vb)]  
  
## <a name="example"></a>範例  
 下列範例 (以完整形式呈現上述程式碼片段) 會將所指定目錄中的所有 .rtf 檔案複製至名稱為 `testdirectory`的目錄中。  
  
 [!code-vb[VbFileIOMisc#37](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-files-with-a-specific-pattern-to-a-directory_4.vb)]  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 以下條件可能會造成例外狀況：  
  
-   因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 (開頭為 \\\\.\\) (<xref:System.ArgumentException>)。  
  
-   路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。  
  
-   目錄不存在 (<xref:System.IO.DirectoryNotFoundException>)。  
  
-   目錄指向現有檔案 (<xref:System.IO.IOException>)。  
  
-   路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。  
  
-   路徑中的檔案或目錄名稱含有冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。  
  
-   使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。 使用者缺乏必要的權限 (<xref:System.UnauthorizedAccessException>)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>   
 <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>   
 [如何：尋找具有特定模式的子目錄](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)   
 [疑難排解：讀取和寫入文字檔](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)   
 [如何：取得目錄的檔案集合](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)

