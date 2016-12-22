---
title: "How to: Delete a File in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "Delete method"
  - "files, deleting"
  - "files, manipulating"
  - "File object"
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Delete a File in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

`My.Computer.FileSystem` 物件的 `DeleteFile` 方法可以讓您刪除檔案。  而它所提供的選項包括：是否要將刪除的檔案傳送至 \[**資源回收筒**\]、是否要詢問使用者以確認要刪除該檔案，以及當使用者取消作業時該如何做。  
  
### 若要刪除文字檔  
  
-   使用 `DeleteFile` 方法刪除檔案。  下列程式碼會示範如何刪除名為 `test.txt` 的檔案。  
  
     [!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_1.vb)]  
  
### 若要刪除文字檔並詢問使用者確認是否要刪除檔案  
  
-   使用 `DeleteFile` 方法刪除檔案，並將 `showUI` 設為 `AllDialogs`。  下列程式碼會示範如何刪除名為 `test.txt` 的檔案，並讓使用者確認是否刪除檔案。  
  
     [!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_2.vb)]  
  
### 若要刪除文字檔並將它傳送到資源回收筒  
  
-   使用 `DeleteFile` 方法刪除檔案，並指定 `SendToRecycleBin` 為 `recycle` 參數。  下列程式碼會示範如何刪除名為 `test.txt` 的檔案，並將它傳送到 \[**資源回收筒**\]。  
  
     [!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_3.vb)]  
  
## 穩固程式設計  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 \(開頭為 \\\\.  \\\) \(<xref:System.ArgumentException>\).  
  
-   路徑無效，因為它是 `Nothing` \(<xref:System.ArgumentNullException>\)。  
  
-   路徑超過系統定義的最大長度 \(<xref:System.IO.PathTooLongException>\)。  
  
-   路徑中的檔案或資料夾名稱含有冒號 \(:\)，或者是無效的格式 \(<xref:System.NotSupportedException>\)。  
  
-   檔案正在使用中 \(<xref:System.IO.IOException>\)。  
  
-   使用者缺乏必要的使用權限來檢視路徑 \(<xref:System.Security.SecurityException>\)。  
  
-   檔案不存在 \(<xref:System.IO.FileNotFoundException>\)。  
  
-   使用者沒有刪除檔案的使用權限，或者檔案是唯讀的 \(<xref:System.UnauthorizedAccessException>\)。  
  
-   發生使用者權限不足的部分信任狀況 \(<xref:System.Security.SecurityException>\)。  
  
-   使用者取消作業並且 `onUserCancel` 設為 `ThrowException` \(<xref:System.OperationCanceledException>\)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.UIOption>   
 <xref:Microsoft.VisualBasic.FileIO.RecycleOption>   
 [How to: Get the Collection of Files in a Directory](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)