---
title: "How to: Read From Text Files in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "extended characters, reading"
  - "reading text files"
  - "reading data, text files"
  - "examples [Visual Basic], reading text files"
  - "text files, reading"
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
caps.latest.revision: 27
caps.handback.revision: 27
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Read From Text Files in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

`My.Computer.FileSystem` 物件的 <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> 方法允許您從文字檔讀取。  如果檔案的內容是使用 ASCII 或 UTF\-8 之類的編碼方式，則可以指定檔案編碼方式。  
  
 如果您是從含擴充字元的檔案讀取，您將需要指定檔案的編碼方式。  
  
> [!NOTE]
>  若要一次讀取檔案中的一行文字，請使用 `My.Computer.FileSystem` 物件的 <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> 方法。  `OpenTextFileReader` 方法會傳回 <xref:System.IO.StreamReader> 物件。  您可以使用 `StreamReader` 物件的 <xref:System.IO.StreamReader.ReadLine%2A> 方法，以一次讀取檔案中的一行。  您可以使用 `StreamReader` 物件的 <xref:System.IO.StreamReader.EndOfStream%2A> 方法測試檔案的結尾。  
  
### 若要從文字檔讀取  
  
-   使用 `My.Computer.FileSystem` 物件的 `ReadAllText` 方法並提供路徑，將文字檔的內容讀取到字串中。  下列範例會將 test.txt 的內容讀取到字串中，然後顯示於訊息方塊中。  
  
     [!code-vb[VbFileIORead#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_1.vb)]  
  
### 若要從已編碼的文字檔讀取  
  
-   使用 `My.Computer.FileSystem` 物件的 `ReadAllText` 方法，並且提供路徑和檔案編碼類型，將文字檔的內容讀取到字串中。  下列範例會將 UTF32 檔案 test.txt 的內容讀取到字串中，然後顯示於訊息方塊中。  
  
     [!code-vb[VbFileIORead#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_2.vb)]  
  
## 穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 \(<xref:System.ArgumentException>\)。  
  
-   路徑無效，因為它是 `Nothing` \(<xref:System.ArgumentNullException>\)。  
  
-   檔案不存在 \(<xref:System.IO.FileNotFoundException>\)。  
  
-   檔案正由另一個程序使用中，或發生 I\/O 錯誤 \(<xref:System.IO.IOException>\)。  
  
-   路徑超過系統定義的最大長度 \(<xref:System.IO.PathTooLongException>\)。  
  
-   路徑中的檔案或目錄名稱含有冒號 \(:\)，或者是無效的格式 \(<xref:System.NotSupportedException>\)。  
  
-   沒有足夠的記憶體可將字串寫入緩衝區 \(<xref:System.OutOfMemoryException>\)。  
  
-   使用者缺乏必要的使用權限來檢視路徑 \(<xref:System.Security.SecurityException>\)。  
  
 請勿根據檔案名稱來判斷檔案內容。  例如，檔案 Form1.vb 可能不是 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 原始程式檔 \(Source File\)。  
  
 在應用程式中使用這些資料之前，請先驗證所有輸入值。  檔案內容可能與預期不同，並從檔案讀取資料的方法會失敗。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>   
 [Reading from Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [How to: Read From Comma\-Delimited Text Files](../Topic/How%20to:%20Read%20From%20Comma-Delimited%20Text%20Files%20in%20Visual%20Basic.md)   
 [How to: Read From Fixed\-width Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)   
 [How to: Read From Text Files with Multiple Formats](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)   
 [Troubleshooting: Reading from and Writing to Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)   
 [Walkthrough: Manipulating Files and Directories in Visual Basic](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)   
 [File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)