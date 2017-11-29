---
title: "疑難排解：讀取和寫入文字檔 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- troubleshooting file I/O
- writing text to files [Visual Basic], troubleshooting
- troubleshooting Visual Basic, text files
- I/O [Visual Basic], troubleshooting text files
- writing to files [Visual Basic], troubleshooting
- reading text files [Visual Basic], troubleshooting
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e836f79cd05dbaa180cc7bf5413ce57004e3500b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="troubleshooting-reading-from-and-writing-to-text-files-visual-basic"></a>疑難排解：讀取和寫入文字檔 (Visual Basic)
本主題討論處理文字檔時所遇到的常見問題，並建議每個問題的處理方法。  
  
## <a name="common-problems"></a>常見問題  
 處理文字檔時所遇到的最常見問題包括安全性例外狀況、檔案編碼方式或無效路徑。  
  
### <a name="security-exceptions"></a>安全性例外狀況  
 發生安全性錯誤時，將會擲回 <xref:System.Security.SecurityException>。 這通常是使用者缺乏必要權限所造成，而解決方法可能是新增權限，或處理隔離儲存空間中的檔案。  
  
### <a name="file-encodings"></a>檔案編碼方式  
 檔案編碼方式，也稱為字元編碼方式，指定在處理文字時如何代表字元。 文字檔中的未預期字元可能是編碼方式不正確所造成。 針對大部分的檔案，就可以或無法處理的語言字元部分而言，可能會偏好使用某種編碼，但是通常偏好使用 Unicode。 如需詳細資訊，請參閱[檔案編碼方式](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)和 <xref:System.Text.Encoding>。  
  
### <a name="incorrect-paths"></a>路徑不正確  
 剖析檔案路徑時，特別是相對路徑，很容易就會提供錯誤資料。 確認您所提供的路徑正確，即可更正許多問題。 如需詳細資訊，請參閱[如何：剖析檔案路徑](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 [從檔案讀取](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [寫入檔案](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)  
 [使用 TextFieldParser 物件剖析文字檔](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)
