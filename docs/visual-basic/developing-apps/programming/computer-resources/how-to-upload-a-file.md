---
title: "How to: Upload a File in Visual Basic | Microsoft Docs"
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
  - "networks, uploading files"
  - "files, uploading"
  - "uploading files"
  - "UploadFile method"
  - "My.Computer.Network.UploadFile method"
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# How to: Upload a File in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> 方法可以用於上傳檔案，並存放到遠端位置。  如果 `ShowUI` 參數設定為 `True`，則會顯示對話方塊以顯示下載進度，並允許使用者取消作業。  
  
### 若要上傳檔案  
  
-   請使用 `UploadFile` 方法上傳檔案，將原始程式檔 \(Source File\) 的位置和目標目錄的位置指定為字串或統一資源識別元 \(URI\)。此範例會將檔案 `Order.txt` 上傳到 `http://www.cohowinery.com/uploads.aspx`。  
  
     [!code-vb[VbResourceTasks#6](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_1.vb)]  
  
### 若要上傳檔案並顯示作業進度  
  
-   請使用 `UploadFile` 方法上傳檔案，將原始程式檔的位置和目標目錄的位置指定為字串或 URI。  此範例中將檔案 `Order.txt` 上傳到 `http://www.cohowinery.com/uploads.aspx` 時不需要提供使用者名稱或密碼，而且會顯示上傳進度並具有 500 毫秒的逾時間隔。  
  
     [!code-vb[VbResourceTasks#7](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_2.vb)]  
  
### 若要提供使用者名稱和密碼以上傳檔案  
  
-   請使用 `UploadFile` 方法上傳檔案，將原始程式檔的位置和目標目錄的位置指定為字串或 URI，並指定使用者名稱和密碼。  此範例會提供使用者名稱 `anonymous` 和空白的密碼，以便將檔案 `Order.txt` 上傳到 `http://www.cohowinery.com/uploads.aspx`。  
  
     [!code-vb[VbResourceTasks#8](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-upload-a-file_3.vb)]  
  
## 穩固程式設計  
 下列情形可能會擲回例外狀況：  
  
-   本機檔案的路徑無效 \(<xref:System.ArgumentException>\)。  
  
-   驗證 \(Authentication\) 失敗 \(<xref:System.Security.SecurityException>\)。  
  
-   連接已逾時 \(<xref:System.TimeoutException>\)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Devices.Network?displayProperty=fullName>   
 <xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A>   
 [How to: Download a File](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)   
 [如何：剖析檔案路徑](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)