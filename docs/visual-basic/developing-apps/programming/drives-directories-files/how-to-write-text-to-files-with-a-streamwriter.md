---
title: "How to: Write Text to Files with a StreamWriter in Visual Basic | Microsoft Docs"
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
  - "files, writing to"
  - "text, writing to files"
  - "writing to files, StreamWriter"
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# How to: Write Text to Files with a StreamWriter in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

這個範例會利用 `My.Computer.FileSystem.OpenTextFileWriter` 方法開啟 <xref:System.IO.StreamWriter>，並且用它搭配 <xref:System.IO.StreamWriter> 類別的 <xref:System.IO.TextWriter.WriteLine%2A> 方法，將字串寫入文字檔。  
  
## 範例  
 [!code-vb[VbFileIOWrite#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-with-a-streamwriter_1.vb)]  
  
## 穩固程式設計  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   檔案存在並且是唯讀的 \(<xref:System.IO.IOException>\)。  
  
-   磁碟已滿 \(<xref:System.IO.IOException>\)。  
  
-   路徑名稱太長 \(<xref:System.IO.PathTooLongException>\)。  
  
## .NET Framework 安全性  
 如果檔案不存在，這個範例就會建立新檔案。  如果應用程式需要建立檔案，該應用程式就需要資料夾的 `Create` 權限。  如果檔案已經存在，則應用程式只需要 `Write` 權限，這是較小的權限。  若有可能，更為安全的做法是在部署期間建立檔案，並且只授與單一檔案的 `Read` 權限，而不授與資料夾的 `Create` 權限。  
  
## 請參閱  
 <xref:System.IO.StreamWriter>   
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>   
 [How to: Read from Text Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)   
 [Writing to Files](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)