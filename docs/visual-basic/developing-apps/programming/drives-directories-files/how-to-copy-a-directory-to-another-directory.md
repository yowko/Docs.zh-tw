---
title: "How to: Copy a Directory to Another Directory in Visual Basic | Microsoft Docs"
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
  - "I/O [Visual Basic], copying directories"
  - "I/O [Visual Basic], copying folders"
  - "folders [Visual Basic], copying"
  - "directories [Visual Basic], copying"
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# How to: Copy a Directory to Another Directory in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

使用 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>，將目錄複製到另一個目錄。  此方法會複製目錄的內容及目錄本身。  如果目標目錄不存在，將會建立它。  如果目標位置中已存在具有相同名稱的目錄，並且將 `overwrite` 設為 `False`，則會合併這兩個目錄的內容。  您可以在作業期間為目錄指定新的名稱。  
  
 複製目錄中的檔案時，雖然將 `overwrite` 設定為 `False`，仍然會在合併期間擲回特定檔案 \(例如，已存在的檔案\) 所造成的例外狀況。  擲回這類例外狀況時，會將它們合併至單一的例外狀況，它的 `Data` 屬性會保留檔案或目錄路徑在其中為索引鍵的項目，而且特定的例外狀況訊息會包含在對應值中。  
  
### 若要將目錄複製到另一個目錄  
  
-   使用 `CopyDirectory` 方法，指定來源與目的目錄的名稱。  下列範例會將名為 `TestDirectory1` 的目錄複製到 `TestDirectory2`，並覆寫現有檔案。  
  
     [!code-vb[VbVbcnMyFileSystem#16](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-copy-a-directory-to-another-directory_1.vb)]  
  
     這個程式碼範例也可做為 IntelliSense 程式碼片段。  在程式碼片段選擇器中，它是位於 \[**檔案系統 \- 處理磁碟、資料夾和檔案**\] 中。  如需詳細資訊，請參閱 [程式碼片段](/visual-studio/ide/code-snippets)。  
  
## 穩固程式設計  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   針對目錄所指定的新名稱含有冒號 \(:\) 或斜線 \(\\ 或 \/\) \(<xref:System.ArgumentException>\)。  
  
-   因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 \(開頭為 \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   路徑無效，因為它是 `Nothing` \(<xref:System.ArgumentNullException>\)。  
  
-   `destinationDirectoryName` 為 `Nothing` 或空字串 \(<xref:System.ArgumentNullException>\)  
  
-   來源目錄不存在 \(<xref:System.IO.DirectoryNotFoundException>\)。  
  
-   來源目錄是根目錄 \(<xref:System.IO.IOException>\)。  
  
-   組合路徑會指向現有的檔案 \(<xref:System.IO.IOException>\)。  
  
-   來源路徑和目標路徑相同 \(<xref:System.IO.IOException>\)。  
  
-   `ShowUI` 設定為 `UIOption.AllDialogs` 且使用者會取消作業，或是無法複製目錄中的一或多個檔案 \(<xref:System.OperationCanceledException>\)。  
  
-   作業是循環的 \(<xref:System.InvalidOperationException>\)。  
  
-   路徑包含冒號 \(:\) \(<xref:System.NotSupportedException>\)。  
  
-   路徑超過系統定義的最大長度 \(<xref:System.IO.PathTooLongException>\)。  
  
-   路徑中的檔案或資料夾名稱含有冒號 \(:\)，或者是無效的格式 \(<xref:System.NotSupportedException>\)。  
  
-   使用者缺乏必要的使用權限來檢視路徑 \(<xref:System.Security.SecurityException>\)。  
  
-   目的檔案存在，但無法存取它 \(<xref:System.UnauthorizedAccessException>\)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>   
 [How to: Find Subdirectories with a Specific Pattern](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)   
 [How to: Get the Collection of Files in a Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)