---
title: "How to: Read From Binary Files in Visual Basic | Microsoft Docs"
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
  - "binary files, reading from"
  - "I/O [Visual Basic], reading from binary files"
  - "ReadAllBytes method, reading from binary files"
  - "My.Computer.FileSystem object, reading from binary files"
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# How to: Read From Binary Files in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

`My.Computer.FileSystem` 物件會提供 `ReadAllBytes` 方法以讀取二進位檔案 \(Binary File\)。  
  
### 若要讀取二進位檔案  
  
-   使用 `ReadAllBytes` 方法，會傳回檔案內容做為位元組陣列。  這個範例會讀取檔案 `C:/Documents and Settings/selfportrait.jpg`。  
  
     [!code-vb[VbVbcnMyFileSystem#78](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-binary-files_1.vb)]  
  
-   若是大型二進位檔案，您可以先使用 <xref:System.IO.FileStream> 物件的 <xref:System.IO.FileStream.Read%2A> 方法，只讀取檔案一段指定的時間。  接著限定每次讀取作業時，將檔案的多少部分載入記憶體。  下列程式碼範例會複製檔案，並允許呼叫端指定每次讀取作業要將檔案的多少部分載入記憶體。  
  
     [!code-vb[VbVbcnMyFileSystem#91](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-binary-files_2.vb)]  
  
## 穩固程式設計  
 下列條件可能造成擲回例外狀況：  
  
-   因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 \(<xref:System.ArgumentException>\)。  
  
-   路徑無效，因為它是 `Nothing` \(<xref:System.ArgumentNullException>\)。  
  
-   檔案不存在 \(<xref:System.IO.FileNotFoundException>\)。  
  
-   檔案正由另一個程序使用中，或發生 I\/O 錯誤 \(<xref:System.IO.IOException>\)。  
  
-   路徑超過系統定義的最大長度 \(<xref:System.IO.PathTooLongException>\)。  
  
-   路徑中的檔案或目錄名稱含有冒號 \(:\)，或者是無效的格式 \(<xref:System.NotSupportedException>\)。  
  
-   沒有足夠的記憶體可將字串寫入緩衝區 \(<xref:System.OutOfMemoryException>\)。  
  
-   使用者缺乏必要的使用權限來檢視路徑 \(<xref:System.Security.SecurityException>\)。  
  
 請勿根據檔案名稱來判斷檔案內容。  例如，檔案 Form1.vb 可能不是 Visual Basic 原始程式檔。  
  
 在應用程式中使用這些資料之前，請先驗證所有輸入值。  檔案內容可能與預期不同，而且從檔案讀取資料的方法可能會失敗。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>   
 [Reading from Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)   
 [Storing Data to and Reading from the Clipboard](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)