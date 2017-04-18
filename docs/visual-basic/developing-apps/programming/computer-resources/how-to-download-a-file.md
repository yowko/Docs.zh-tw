---
title: "如何：在 Visual Basic 中下載檔案 | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- downloading Internet resources, files
- downloading files
- remote computers, downloading from
- files, downloading
- files, transferring
ms.assetid: ac479f81-c0e2-4b99-af73-217f446b73da
caps.latest.revision: 22
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: bd37b52d12876dad6ec4b2a1bb34f4987f933c08
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-download-a-file-in-visual-basic"></a>如何：在 Visual Basic 中下載檔案
<xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A> 方法可用來下載遠端檔案，然後將它儲存至特定位置。 如果 `ShowUI` 參數設定為 `True`，則會顯示對話方塊以顯示下載進度，並允許使用者取消作業。 根據預設，不會覆寫具有相同名稱的現有檔案；如果您想要覆寫現有檔案，請將 `overwrite` 參數設定為 `True`。  
  
 以下條件可能會造成例外狀況：  
  
-   磁碟機名稱無效 (<xref:System.ArgumentException>)。  
  
-   尚未提供必要的驗證 (<xref:System.UnauthorizedAccessException> 或 <xref:System.Security.SecurityException>)。  
  
-   伺服器在指定的 `connectionTimeout` 內沒有回應 (<xref:System.TimeoutException>)。  
  
-   網站拒絕此要求 (<xref:System.Net.WebException>)。  
  
[!INCLUDE[note_settings_general](../../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
> [!IMPORTANT]
>  請勿根據檔案名稱來判斷檔案內容。 例如，檔案 Form1.vb 可能不是 Visual Basic 來源檔案。 在應用程式中使用這些資料之前，請先驗證所有輸入值。 檔案內容可能與預期不同，並從檔案讀取資料的方法會失敗。  
  
### <a name="to-download-a-file"></a>下載檔案  
  
-   使用 `DownloadFile` 方法下載檔案，並以字串或 URI 形式指定目標檔案的位置，以及指定要儲存檔案的位置。 此範例會從 `http://www.cohowinery.com/downloads` 下載 `WineList.txt` 檔案，然後將它儲存至 `C:\Documents and Settings\All Users\Documents`：  
  
     [!code-vb[VbResourceTasks#9](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_1.vb)]  
  
### <a name="to-download-a-file-specifying-a-time-out-interval"></a>下載檔案並指定逾時間隔  
  
-   使用 `DownloadFile` 方法下載檔案，並以字串或 URI 形式指定目標檔案的位置、指定要儲存檔案的位置，以及指定以毫秒為單位的逾時間隔 (預設值為 1000)。 此範例會從 `http://www.cohowinery.com/downloads` 下載 `WineList.txt` 檔案，然後將它儲存至 `C:\Documents and Settings\All Users\Documents`，並指定 500 毫秒的逾時間隔：  
  
     [!code-vb[VbResourceTasks#10](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_2.vb)]  
  
### <a name="to-download-a-file-supplying-a-user-name-and-password"></a>下載檔案並提供使用者名稱和密碼  
  
-   使用 `DownLoadFile` 方法下載檔案，並以字串或 URI 形式指定目標檔案的位置，以及指定要儲存檔案、使用者名稱和密碼的位置。 此範例會從 `http://www.cohowinery.com/downloads` 下載 `WineList.txt` 檔案，然後將它儲存至具有使用者名稱 `anonymous` 和空白密碼的 `C:\Documents and Settings\All Users\Documents`。  
  
     [!code-vb[VbResourceTasks#11](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-download-a-file_3.vb)]  
  
    > [!IMPORTANT]
    >  `DownLoadFile` 方法所使用的 FTP 通訊協定會以純文字傳送資訊 (包括密碼)，不應用於傳輸機密資訊。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.Devices.Network>   
 <xref:Microsoft.VisualBasic.Devices.Network.DownloadFile%2A>   
 [如何：上傳檔案](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-upload-a-file.md)   
 [如何：剖析檔案路徑](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)

