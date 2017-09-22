---
title: "如何：在 Visual Basic 中建立檔案"
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
- text files, creating
- files, creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
caps.latest.revision: 15
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
ms.openlocfilehash: d06d274b31afad0a437405d1679e0be7548f2e14
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# How to: Create a File in Visual Basic
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

這個範例會使用 <xref:System.IO.File> 類別 \(Class\) 中的 <xref:System.IO.File.Create%2A> 方法，在指定的路徑建立空的文字檔。  
  
## 範例  
 [!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]  
  
## 編譯程式碼  
 請使用 `file` 變數寫入至檔案。  
  
## 穩固程式設計  
 如果檔案已存在，則會取代該檔案。  
  
 下列情形可能會造成例外狀況 \(Exception\)：  
  
-   路徑名稱錯誤。  例如，它包含不合法的字元或只是泛空白字元 \(<xref:System.ArgumentException>\)。  
  
-   路徑是唯讀的 \(<xref:System.IO.IOException>\)。  
  
-   路徑名稱是 `Nothing` \(<xref:System.ArgumentNullException>\)。  
  
-   路徑名稱太長 \(<xref:System.IO.PathTooLongException>\)。  
  
-   路徑無效 \(<xref:System.IO.DirectoryNotFoundException>\)。  
  
-   路徑只是冒號 ":" \(<xref:System.NotSupportedException>\)。  
  
## .NET Framework 安全性  
 在部分信任的環境下可能會擲回 <xref:System.Security.SecurityException>。  
  
 呼叫 <xref:System.IO.File.Create%2A> 方法時需要 <xref:System.Security.Permissions.FileIOPermission>。  
  
 如果使用者沒有建立檔案的權限，則會擲回 <xref:System.UnauthorizedAccessException>。  
  
## 請參閱  
 <xref:System.IO>   
 <xref:System.IO.File.Create%2A>   
 [從部分受信任程式碼使用程式庫](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)   
 [程式碼存取安全性的基本概念](https://msdn.microsoft.com/library/33tceax8)

