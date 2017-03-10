---
title: "How to: Write to Binary Files in Visual Basic | Microsoft Docs"
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
  - "files, binary access"
  - "WriteAllBytes method"
  - "binary files, writing in Visual Basic"
ms.assetid: 59fae125-de5b-4c96-883c-209f4a55112c
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Write to Binary Files in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A> 方法會將資料寫入二進位檔案。  如果 `append` 參數為 `True`，則會將資料附加至檔案，否則會覆寫檔案中的資料。  
  
 如果指定的路徑 \(不含檔案名稱\) 無效，將會擲回 <xref:System.IO.DirectoryNotFoundException> 例外狀況。  如果路徑有效但檔案不存在，將會建立檔案。  
  
### 若要寫入二進位檔案  
  
-   使用 `WriteAllBytes` 方法，提供檔案路徑和名稱以及要寫入的位元組數。  這個範例會將資料陣列 `CustomerData` 附加至名為 `CollectedData.dat` 的檔案。  
  
     [!code-vb[VbVbcnMyFileSystem#27](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-write-to-binary-f_1.vb)]  
  
## 穩固程式設計  
 下列情況可能會導致例外狀況：  
  
-   因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元，或者它包含無效的字元   \(<xref:System.ArgumentException>\).  
  
-   路徑無效，因為它是 `Nothing` \(<xref:System.ArgumentNullException>\)。  
  
-   `File` 指向不存在的路徑 \(<xref:System.IO.FileNotFoundException> 或 <xref:System.IO.DirectoryNotFoundException>\)。  
  
-   檔案正由另一個程序使用中，或發生 I\/O 錯誤 \(<xref:System.IO.IOException>\)。  
  
-   路徑超過系統定義的最大長度 \(<xref:System.IO.PathTooLongException>\)。  
  
-   路徑中的檔案或目錄名稱含有冒號 \(:\)，或者是無效的格式 \(<xref:System.NotSupportedException>\)。  
  
-   使用者缺乏必要的使用權限來檢視路徑 \(<xref:System.Security.SecurityException>\)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>   
 [How to: Write Text to Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-write-text-to-files.md)