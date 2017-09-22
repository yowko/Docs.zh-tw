---
title: "如何：在 Visual Basic 中於不同資料夾內建立檔案複本"
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: ef6fcfaa38343d0fb137571b82f4d2719f3d61ef
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# How to: Create a Copy of a File in a Different Directory in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

`My.Computer.FileSystem.CopyFile` 方法允許您複製檔案。  它的參數會提供覆寫現有檔案、重新命名檔案、顯示作業進度等功能，並且允許使用者取消作業。  
  
### 若要將文字檔複製到其他資料夾  
  
-   使用 `CopyFile` 方法複製檔案，並且指定來源檔案和目標目錄。  `overwrite` 參數允許您指定是否覆寫現有的檔案。  下列程式碼範例會使用 `CopyFile`。  
  
     [!code-vb[VbFileIOMisc#24](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-a-different-directory_1.vb)]  
  
## 穩固程式設計  
 下列條件可能造成擲回例外狀況：  
  
-   因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 \(開頭為 \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   系統無法擷取絕對路徑 \(<xref:System.ArgumentException>\)。  
  
-   路徑無效，因為它是 `Nothing` \(<xref:System.ArgumentNullException>\)。  
  
-   原始程式檔無效或不存在 \(<xref:System.IO.FileNotFoundException>\)。  
  
-   組合路徑會指向現有的目錄 \(<xref:System.IO.IOException>\)。  
  
-   目的檔存在且 `overwrite` 設定為 `False` \(<xref:System.IO.IOException>\)。  
  
-   使用者沒有足夠的使用權限可以存取檔案 \(<xref:System.IO.IOException>\)。  
  
-   目標資料夾中具有相同名稱的檔案正在使用中 \(<xref:System.IO.IOException>\)。  
  
-   路徑中的檔案或資料夾名稱含有冒號 \(:\)，或者是無效的格式 \(<xref:System.NotSupportedException>\)。  
  
-   `ShowUI` 設為 `True`、`onUserCancel` 設為 `ThrowException`，而且使用者已取消作業 \(<xref:System.OperationCanceledException>\)。  
  
-   `ShowUI` 設為 `True`、`onUserCancel` 設為 `ThrowException`，而且發生未指定的 I\/O 錯誤 \(<xref:System.OperationCanceledException>\)。  
  
-   路徑超過系統定義的最大長度 \(<xref:System.IO.PathTooLongException>\)。  
  
-   使用者未具備必要的使用權限 \(<xref:System.UnauthorizedAccessException>\)。  
  
-   使用者缺乏必要的使用權限來檢視路徑 \(<xref:System.Security.SecurityException>\)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyFile%2A>   
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>   
 [如何：將具有特定模式的檔案複製到目錄](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-files-with-a-specific-pattern-to-a-directory.md)   
 [如何：在相同目錄內建立檔案複本](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-the-same-directory.md)   
 [如何：將目錄複製到另一個目錄](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)   
 [如何：重新命名檔案](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)

