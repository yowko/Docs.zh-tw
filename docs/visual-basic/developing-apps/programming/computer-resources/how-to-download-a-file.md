---
title: "How to: Download a File in Visual Basic | Microsoft Docs"
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
  - "downloading Internet resources, files"
  - "downloading files"
  - "remote computers, downloading from"
  - "files, downloading"
  - "files, transferring"
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# How to: Download a File in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

<xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> 方法可以用於下載遠端檔案，並存放到特定位置。  如果 `ShowUI` 參數設定為 `True`，則會顯示對話方塊以顯示下載進度，並允許使用者取消作業。  根據預設，不會覆寫具有相同名稱的現有檔案。若要覆寫現有檔案，請將 `overwrite` 參數設定為 `True`。  
  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   磁碟名稱無效 \(<xref:System.ArgumentException>\)。  
  
-   尚未提供必要的驗證 \(<xref:System.UnauthorizedAccessException> 或 <xref:System.Security.SecurityException>\)。  
  
-   伺服器沒有在指定的 `connectionTimeout` 內回應 \(<xref:System.TimeoutException>\)。  
  
-   網站拒絕此要求 \(<xref:System.Net.WebException>\)。  
  
 [!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
> [!IMPORTANT]
>  請勿根據檔案名稱來判斷檔案內容。  例如，檔案 Form1.vb 可能不是 Visual Basic 原始程式檔。  在應用程式中使用這些資料之前，請先驗證所有輸入值。  檔案內容可能與預期不同，而且從檔案讀取資料的方法可能會失敗。  
  
### 下載檔案  
  
-   請使用 `DownloadFile` 方法下載檔案，將目標檔案的位置指定為字串或 URI，並指定要存放檔案的位置。  這個範例會從 `http://www.cohowinery.com/downloads` 下載檔案 `WineList.txt`，並將該檔案儲存到 `C:\Documents and Settings\All Users\Documents`：  
  
     [!code-vb[VbResourceTasks#9](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_1.vb)]  
  
### 指定逾時間隔以下載檔案  
  
-   請使用 `DownloadFile` 方法下載檔案，將目標檔案的位置指定為字串或 URI、指定要存放檔案的位置，並以毫秒為單位指定逾時間隔 \(預設值為 1000\)。  這個範例會從 `http://www.cohowinery.com/downloads` 下載檔案 `WineList.txt`，並將該檔案儲存到 `C:\Documents and Settings\All Users\Documents`，而指定的逾時間隔為 500 毫秒：  
  
     [!code-vb[VbResourceTasks#10](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_2.vb)]  
  
### 提供使用者名稱和密碼以下載檔案  
  
-   請使用 `DownLoadFile` 方法下載檔案，將目標檔案的位置指定為字串或 URI，並指定要存放檔案的位置、使用者名稱和密碼。  這個範例會以使用者名稱 `anonymous` 和空白密碼，從 `http://www.cohowinery.com/downloads` 下載檔案 `WineList.txt`，並將該檔案儲存到 `C:\Documents and Settings\All Users\Documents`。  
  
     [!code-vb[VbResourceTasks#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_3.vb)]  
  
    > [!IMPORTANT]
    >  `DownLoadFile` 方法所使用的 FTP 通訊協定會以純文字格式傳送資訊 \(包括密碼\)，因此不應該用於傳輸機密資訊。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.Devices.Network>   
 <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>   
 [How to: Upload a File](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)   
 [如何：剖析檔案路徑](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)