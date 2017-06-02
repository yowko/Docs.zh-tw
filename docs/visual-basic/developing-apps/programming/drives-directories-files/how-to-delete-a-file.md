---
title: "如何：在 Visual Basic 中刪除檔案 | Microsoft Docs"
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
- Delete method
- files, deleting
- files, manipulating
- File object
ms.assetid: 4b721769-3e45-4be7-b7fe-b08dc4141b44
caps.latest.revision: 24
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: f6cf3192d6983b6222815c5c77a3dfd0b3845650
ms.contentlocale: zh-tw
ms.lasthandoff: 05/22/2017

---
# <a name="how-to-delete-a-file-in-visual-basic"></a>如何：在 Visual Basic 中刪除檔案
`My.Computer.FileSystem` 物件的 `DeleteFile` 方法可讓您刪除檔案。 提供的選項包括︰是否要將已刪除的檔案傳送至 [資源回收筒]、是否要求使用者確認應該刪除檔案，以及使用者取消該作業時該怎麼辦。  
  
### <a name="to-delete-a-text-file"></a>刪除文字檔  
  
-   使用 `DeleteFile` 方法來刪除檔案。 下列程式碼示範如何刪除名為 `test.txt` 的檔案。  
  
     [!code-vb[VbVbcnMyFileSystem#22](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_1.vb)]  
  
### <a name="to-delete-a-text-file-and-ask-the-user-to-confirm-that-the-file-should-be-deleted"></a>刪除文字檔並要求使用者確認應該刪除檔案  
  
-   使用 `DeleteFile` 方法來刪除檔案，並將 `showUI` 設定為 `AllDialogs`。 下列程式碼示範如何刪除名為 `test.txt` 的檔案，並讓使用者確認應該刪除檔案。  
  
     [!code-vb[VbFileIOMisc#9](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_2.vb)]  
  
### <a name="to-delete-a-text-file-and-send-it-to-the-recycle-bin"></a>刪除文字檔並將它傳送至資源回收筒  
  
-   使用 `DeleteFile` 方法來刪除檔案，並指定 `recycle` 參數的 `SendToRecycleBin`。 下列程式碼示範如何刪除名為 `test.txt` 的檔案，並將它傳送至 [資源回收筒]。  
  
     [!code-vb[VbFileIOMisc#10](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-delete-a-file_3.vb)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 (開頭為 \\\\.\\) (<xref:System.ArgumentException>)。  
  
-   路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。  
  
-   路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。  
  
-   路徑中的檔案或資料夾名稱包含冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。  
  
-   檔案正在使用中 (<xref:System.IO.IOException>)。  
  
-   使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。  
  
-   檔案不存在 (<xref:System.IO.FileNotFoundException>)。  
  
-   使用者無權刪除檔案，或檔案為唯讀 (<xref:System.UnauthorizedAccessException>)。  
  
-   發生使用者權限不足的部分信任狀況 (<xref:System.Security.SecurityException>)。  
  
-   使用者已取消作業，而且 `onUserCancel` 設定為 `ThrowException` (<xref:System.OperationCanceledException>)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.FileIO.UICancelOption>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 <xref:Microsoft.VisualBasic.FileIO.UIOption>   
 <xref:Microsoft.VisualBasic.FileIO.RecycleOption>   
 [如何：取得目錄的檔案集合](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
