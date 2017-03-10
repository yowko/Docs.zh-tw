---
title: "How to: Find Subdirectories with a Specific Pattern in Visual Basic | Microsoft Docs"
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
  - "pattern matching"
  - "folders, finding"
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Find Subdirectories with a Specific Pattern in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> 方法會傳回唯讀的字串集合，代表目錄中子目錄的路徑名稱。  您可以使用 `wildCards` 參數，指定特定的模式。  如果要在搜尋中納入子目錄的內容，請將 `searchType` 參數設定為 `SearchOption.SearchAllSubDirectories`。  
  
 如果找不到與指定模式相符的目錄，則會傳回空的集合。  
  
### 若要尋找具有特定模式的子目錄  
  
-   使用 `GetDirectories` 方法，以提供要搜尋之目錄的名稱和路徑。  下列範例會傳回在目錄結構中，名稱中含有 "Logs" 這個字的所有目錄，並將這些目錄加入至 `ListBox1` 中。  
  
     [!code-vb[VbVbcnFileAccess#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-find-subdirectori_1.vb)]  
  
## 穩固程式設計  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 \(開頭為 \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   路徑無效，因為它是 `Nothing` \(<xref:System.ArgumentNullException>\)。  
  
-   一或多個指定的萬用字元 \(Wildcard Character\) 為 `Nothing`、空字串，或只包含空格 \(<xref:System.ArgumentNullException>\)。  
  
-   `directory` 不存在 \(<xref:System.IO.DirectoryNotFoundException>\)。  
  
-   `directory` 會指向現有的檔案 \(<xref:System.IO.IOException>\)。  
  
-   路徑超過系統定義的最大長度 \(<xref:System.IO.PathTooLongException>\)。  
  
-   路徑中的檔案或資料夾名稱含有冒號 \(:\)，或者是無效的格式 \(<xref:System.NotSupportedException>\)。  
  
-   使用者缺乏必要的使用權限來檢視路徑 \(<xref:System.Security.SecurityException>\)。  
  
-   使用者缺乏必要的使用權限 \(<xref:System.UnauthorizedAccessException>\)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>   
 [How to: Find Files with a Specific Pattern](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)