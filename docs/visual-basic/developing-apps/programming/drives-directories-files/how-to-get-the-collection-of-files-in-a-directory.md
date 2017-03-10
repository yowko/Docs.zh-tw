---
title: "How to: Get the Collection of Files in a Directory in Visual Basic | Microsoft Docs"
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
  - "folders, working with"
  - "files, accessing"
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# How to: Get the Collection of Files in a Directory in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=fullName> 方法的多載會傳回唯讀的字串集合，代表了目錄內的檔案名稱：  
  
-   使用 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> 多載在指定目錄中進行簡單的檔案搜尋，而不搜尋子目錄。  
  
-   使用 [GetFiles\(String, SearchOption, String\<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%2CMicrosoft.VisualBasic.FileIO.SearchOption%2CSystem.String%5B%5D%29> 多載指定搜尋的其他選項。  您可以使用 `wildCards` 參數，指定搜尋模式。  若要在搜尋中包含子目錄，請將 `searchType` 參數設成 <xref:Microsoft.VisualBasic.FileIO.SearchOption?displayProperty=fullName>。  
  
 如果找不到符合指定模式的檔案，會傳回空的集合。  
  
### 列出目錄中的檔案  
  
-   使用其中一個 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=fullName> 方法多載，並在 `directory` 參數中提供要搜尋的目錄名稱和路徑。  下列範例會傳回目錄中的所有檔案，並將它們新增到  `ListBox1`。  
  
     [!code-vb[VbVbcnMyFileSystem#32](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-get-the-collectio_1.vb)]  
  
## 穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 \(開頭為 \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   路徑無效，因為它是 `Nothing` \(<xref:System.ArgumentNullException>\)。  
  
-   `directory` 不存在 \(<xref:System.IO.DirectoryNotFoundException>\)。  
  
-   `directory` 指向現有檔案 \(<xref:System.IO.IOException>\)。  
  
-   路徑超過系統定義的最大長度 \(<xref:System.IO.PathTooLongException>\)。  
  
-   路徑中的檔案或目錄名稱含有冒號 \(:\)，或者是無效的格式 \(<xref:System.NotSupportedException>\)。  
  
-   使用者缺乏必要的使用權限來檢視路徑 \(<xref:System.Security.SecurityException>\)。  
  
-   使用者缺乏必要的權限 \(<xref:System.UnauthorizedAccessException>\)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>   
 [How to: Find Files with a Specific Pattern](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)   
 [How to: Find Subdirectories with a Specific Pattern](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)