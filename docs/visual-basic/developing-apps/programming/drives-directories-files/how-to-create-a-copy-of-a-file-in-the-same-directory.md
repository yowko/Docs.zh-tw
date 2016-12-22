---
title: "How to: Create a Copy of a File in the Same Directory in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "File.Copy"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "My.Computer.FileSystem.CopyFile method, copying files [Visual Basic]"
  - "files, copying"
  - "CopyFile method, copying files in Visual Basic"
  - "I/O [Visual Basic], copying files"
ms.assetid: b2fdda86-e666-42c2-9706-9527e9fa68ff
caps.latest.revision: 21
caps.handback.revision: 21
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Create a Copy of a File in the Same Directory in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

使用 `My.Computer.FileSystem.CopyFile` 方法複製檔案。  此參數可讓您覆寫現有的檔案、重新命名檔案、顯示作業進度，並允許使用者取消作業。  
  
### 若要在相同的資料夾中建立檔案的複本  
  
-   請使用 `CopyFile` 方法，提供目標檔案和位置。  下列範例會建立名為 `test2.txt` 之 `test.txt` 的複本。  
  
     [!code-vb[VbVbcnMyFileSystem#51](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_1.vb)]  
  
### 若要在相同的資料夾中建立檔案的複本，以覆寫現有的檔案  
  
-   請使用 `CopyFile` 方法，提供目標檔案和位置，並將 `overwrite` 設定為 `True`。  下列範例會建立名為 `test2.txt` 之 `test.txt` 的複本，並以該名稱覆寫所有的現有檔案。  
  
     [!code-vb[VbVbcnMyFileSystem#52](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-copy-of-a-file-in-the-same-directory_2.vb)]  
  
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
 [如何：將具有特定模式的檔案複製到目錄](../Topic/How%20to:%20Copy%20Files%20with%20a%20Specific%20Pattern%20to%20a%20Directory%20in%20Visual%20Basic.md)   
 [How to: Create a Copy of a File in a Different Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-create-a-copy-of-a-file-in-a-different-directory.md)   
 [How to: Copy a Directory to Another Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-copy-a-directory-to-another-directory.md)   
 [How to: Rename a File](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-rename-a-file.md)