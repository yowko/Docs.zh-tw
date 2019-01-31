---
title: HOW TO：在 Visual Basic 中重新命名檔案
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], renaming files
- files [Visual Basic], renaming
ms.assetid: 0ea7e0c8-2cb2-4bf5-a00d-7b6e3c08a3bc
ms.openlocfilehash: 3b1e85cc9e0b0768f7065ff690f6dc969ee040b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676363"
---
# <a name="how-to-rename-a-file-in-visual-basic"></a>HOW TO：在 Visual Basic 中重新命名檔案
您可以使用 `My.Computer.FileSystem` 物件的 `RenameFile` 方法，藉由提供目前的位置、檔案名稱和新的檔案名稱，來重新命名檔案。 這個方法無法用來移動檔案，請使用 `MoveFile` 方法來移動並重新命名檔案。  
  
### <a name="to-rename-a-file"></a>重新命名檔案  
  
-   使用 `My.Computer.FileSystem.RenameFile` 方法來重新命名檔案。 此範例會將名為 `Test.txt` 的檔案重新命名為 `SecondTest.txt`。  
  
     [!code-vb[VbVbcnMyFileSystem#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-rename-a-file_1.vb)]  
  
 這個程式碼範例也可用為 IntelliSense 程式碼片段。 在程式碼片段選擇器中，該程式碼片段會位於 [檔案系統 - 處理磁碟、資料夾和檔案] 中。 如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 (開頭為 \\\\.\\) (<xref:System.ArgumentException>)。  
  
-   `newName` 包含路徑資訊 (<xref:System.ArgumentException>)。  
  
-   路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。  
  
-   `newName` 為 `Nothing` 或空字串 (<xref:System.ArgumentNullException>)。  
  
-   來源檔案無效或不存在 (<xref:System.IO.FileNotFoundException>)。  
  
-   已有 `newName` 中所指定之名稱的檔案或目錄 (<xref:System.IO.IOException>)。  
  
-   路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。  
  
-   路徑中的檔案或目錄名稱含有冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。  
  
-   使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。  
  
-   使用者沒有必要的權限 (<xref:System.UnauthorizedAccessException>)。  
  
## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.RenameFile%2A>
- [如何：移動檔案](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-move-a-file.md)
- [建立、刪除和移動檔案和目錄](../../../../visual-basic/developing-apps/programming/drives-directories-files/creating-deleting-and-moving-files-and-directories.md)
- [如何：在相同目錄內建立檔案複本](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)
- [如何：於不同目錄內建立檔案複本](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)
