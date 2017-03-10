---
title: "How to: Append to Text Files in Visual Basic | Microsoft Docs"
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
  - "I/O [Visual Basic], appending to files"
  - "I/O [Visual Basic], My.Computer.FileSystem.WriteAllText method"
  - "I/O [Visual Basic], WriteAllText method"
ms.assetid: bbbd7fb5-f169-41a9-b53f-520ea9613913
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# How to: Append to Text Files in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

藉由指定將 `append` 參數設定為 `True`，<xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A> 方法可用於附加至文字檔。  
  
### 若要附加至文字檔  
  
-   請使用 `WriteAllText` 方法，指定目標檔案和要附加的字串，並將 `append` 參數設定為 `True`。  
  
     這個範例會將字串 `"This is a test string."` 寫入名為 `Testfile.txt` 的檔案。  
  
     [!code-vb[VbFileIOWrite#6](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/visualbasic/how-to-append-to-text-fi_1.vb)]  
  
## 穩固程式設計  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 \(開頭為 \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   路徑無效，因為它是 `Nothing` \(<xref:System.ArgumentNullException>\)。  
  
-   `File` 指向不存在的路徑 \(<xref:System.IO.FileNotFoundException> 或 <xref:System.IO.DirectoryNotFoundException>\)。  
  
-   檔案正由另一個程序使用中，或發生 I\/O 錯誤 \(<xref:System.IO.IOException>\)。  
  
-   路徑超過系統定義的最大長度 \(<xref:System.IO.PathTooLongException>\)。  
  
-   路徑中的檔案或目錄名稱含有冒號 \(:\)，或者是無效的格式 \(<xref:System.NotSupportedException>\)。  
  
-   使用者缺乏必要的使用權限來檢視路徑 \(<xref:System.Security.SecurityException>\)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 [Writing to Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)