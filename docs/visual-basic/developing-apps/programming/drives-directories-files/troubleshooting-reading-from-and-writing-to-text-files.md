---
title: "Troubleshooting: Reading from and Writing to Text Files (Visual Basic) | Microsoft Docs"
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
  - "troubleshooting file I/O"
  - "writing text to files, troubleshooting"
  - "troubleshooting Visual Basic, text files"
  - "I/O [Visual Basic], troubleshooting text files"
  - "writing to files, troubleshooting"
  - "reading text files, troubleshooting"
ms.assetid: a8e9b44d-facb-4718-8c0f-466537171182
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Troubleshooting: Reading from and Writing to Text Files (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

這個主題會討論使用文字檔時遇到的常見問題，並針對每個問題建議處理方法。  
  
## 常見問題  
 使用文字檔時遇到最常見的問題，包括安全性例外狀況、檔案編碼方式或路徑無效。  
  
### 安全性例外狀況  
 發生安全性的錯誤時，就會擲回 <xref:System.Security.SecurityException>。  這通常是因為使用者缺少必要的使用權限所導致，可藉由加入使用權限或在隔離儲存區 \(Isolated Storage\) 中使用檔案解決。  如需詳細資訊，請參閱[疑難排解例外狀況：System.Security.SecurityException](../Topic/Troubleshooting%20Exceptions:%20System.Security.SecurityException.md)。  
  
### 檔案編碼方式  
 檔案編碼方式 \(也稱為字元編碼方式\) 會指定在處理文字時字元的表示方式。  編碼方式不正確可能會導致文字檔中產生未預期的字元。  對於大部分的檔案而言，雖然通常會偏好 Unicode，但是仍然以是否能處理語言字元而偏好某一種編碼方式。  如需詳細資訊，請參閱[File Encodings](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)和 <xref:System.Text.Encoding>。  
  
### 不正確的路徑  
 剖析檔案路徑時 \(特別是相對路徑\)，很容易就提供錯誤資料。  確定您所提供的路徑正確，即可更正許多問題。  如需詳細資訊，請參閱 [如何：剖析檔案路徑](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)。  
  
## 請參閱  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>   
 [Reading from Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)   
 [Writing to Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)   
 [Parsing Text Files with the TextFieldParser Object](../../../../visual-basic/developing-apps/programming/drives-directories-files/parsing-text-files-with-the-textfieldparser-object.md)