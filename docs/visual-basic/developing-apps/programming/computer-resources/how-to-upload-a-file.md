---
title: "如何：在 Visual Basic 中上載檔案"
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
- networks, uploading files
- files, uploading
- uploading files
- UploadFile method
- My.Computer.Network.UploadFile method
ms.assetid: a8b37924-c523-4fd3-b5ca-cb0074df29cd
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 29baf1f420cece6e0b05f9638b30a326178a013d
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-upload-a-file-in-visual-basic"></a>如何：在 Visual Basic 中上載檔案
<xref:Microsoft.VisualBasic.Devices.Network.UploadFile%2A> 方法可以用於上傳檔案，並將其存放到遠端位置。 如果 `ShowUI` 參數設定為 `True`，則會顯示對話方塊以顯示上傳進度，並允許使用者取消作業。  
  
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
 [如何：下載檔案](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-download-a-file.md)   
 [如何：剖析檔案路徑](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)

