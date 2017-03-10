---
title: "How to: Find Files with a Specific Pattern in Visual Basic | Microsoft Docs"
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
  - "files, finding"
  - "pattern matching"
  - "patterns, matching"
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# How to: Find Files with a Specific Pattern in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> 方法會傳回代表檔案的路徑名稱之字串的唯讀集合。  您可以使用 `wildCards` 參數，指定特定的模式。  如果要在搜尋中包含子目錄，請將 `searchType` 參數設定為 `SearchOption.SearchAllSubDirectories`。  
  
 如果找不到符合指定之模式的檔案，則會傳回空集合。  
  
> [!NOTE]
>  如需傳回使用 `System.IO` 命名空間的 `DirectoryInfo` 類別的檔案清單的詳細資訊，請參閱 <xref:System.IO.DirectoryInfo.GetFiles%2A>。  
  
### 若要搜尋具有指定模式的檔案  
  
-   使用 `GetFiles` 方法，提供要搜尋之目錄的名稱與路徑，並指定模式。  下列範例會傳回目錄中副檔名為 `.dll` 的所有檔案，並將它們加入至 `ListBox1`。  
  
     [!code-vb[VbFileIOMisc#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-find-files-with-a_1.vb)]  
  
## .NET Framework 安全性  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 \(開頭為 \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   路徑無效，因為它是 `Nothing` \(<xref:System.ArgumentNullException>\)。  
  
-   `directory` 不存在 \(<xref:System.IO.DirectoryNotFoundException>\)。  
  
-   `directory` 會指向現有的檔案 \(<xref:System.IO.IOException>\)。  
  
-   路徑超過系統定義的最大長度 \(<xref:System.IO.PathTooLongException>\)。  
  
-   路徑中的檔案或資料夾名稱含有冒號 \(:\)，或者是無效的格式 \(<xref:System.NotSupportedException>\)。  
  
-   使用者缺乏必要的使用權限來檢視路徑 \(<xref:System.Security.SecurityException>\)。  
  
-   使用者缺乏必要的使用權限 \(<xref:System.UnauthorizedAccessException>\)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>   
 [How to: Find Subdirectories with a Specific Pattern](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)   
 [Troubleshooting: Reading from and Writing to Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)   
 [How to: Get the Collection of Files in a Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)