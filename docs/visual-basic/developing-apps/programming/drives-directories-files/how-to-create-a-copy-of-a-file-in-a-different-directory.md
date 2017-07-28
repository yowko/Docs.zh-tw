---
title: "如何：在 Visual Basic 中於不同目錄內建立檔案複本 | Microsoft Docs"
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
ms.assetid: 88e2145c-d414-45a5-ad03-6f5d58ecca26
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: a51633fa65321325e1ae08c1e03cf2392f771cc9
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-create-a-copy-of-a-file-in-a-different-directory-in-visual-basic"></a>如何：在 Visual Basic 中於不同資料夾內建立檔案複本
`My.Computer.FileSystem.CopyFile` 方法可讓您複製檔案。 它的參數可以覆寫現有檔案、重新命名檔案、顯示作業進度，並讓使用者取消作業。  
  
### <a name="to-copy-a-text-file-to-another-folder"></a>將文字檔複製到另一個資料夾  
  
-   使用 `CopyFile` 方法來複製檔案，並指定來源檔案和目標目錄。 `overwrite` 參數可讓您指定是否要覆寫現有檔案。 下列程式碼範例示範如何使用 `CopyFile`。  
  
     [!code-vb[VbFileIOMisc#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-a-different-directory_1.vb)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 下列條件可能會造成擲回例外狀況：  
  
-   因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 (開頭為 \\\\.\\) (<xref:System.ArgumentException>)。  
  
-   系統無法擷取絕對路徑 (<xref:System.ArgumentException>)。  
  
-   路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。  
  
-   來源檔案無效或不存在 (<xref:System.IO.FileNotFoundException>)。  
  
-   合併的路徑指向現有目錄 (<xref:System.IO.IOException>)。  
  
-   目的地檔案存在且 `overwrite` 設定為 `False` (<xref:System.IO.IOException>)。  
  
-   使用者沒有足夠權限以存取檔案 (<xref:System.IO.IOException>)。  
  
-   正在使用目標資枓夾中同名的檔案 (<xref:System.IO.IOException>)。  
  
-   路徑中的檔案或資料夾名稱包含冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。  
  
-   `ShowUI` 設定為 `True`、`onUserCancel` 設定為 `ThrowException`，而且使用者已取消作業 (<xref:System.OperationCanceledException>)。  
  
-   `ShowUI` 設定為 `True`、`onUserCancel` 設定為 `ThrowException`，而且發生未指定的 I/O 錯誤 (<xref:System.OperationCanceledException>)。  
  
-   路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。  
  
-   使用者沒有必要的權限 (<xref:System.UnauthorizedAccessException>)。  
  
-   使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>   
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>   
 [如何：將具有特定模式的檔案複製到目錄](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)   
 [如何：在相同目錄內建立檔案複本](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)   
 [如何：將目錄複製到另一個目錄](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)   
 [如何：重新命名檔案](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)
