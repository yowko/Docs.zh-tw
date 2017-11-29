---
title: "如何：在 Visual Basic 中以 StreamWriter 將文字寫入檔案"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 874bb9cb88bbf25cb6208a0a33858855a7b26a49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a>如何：在 Visual Basic 中以 StreamWriter 將文字寫入檔案
此範例使用 `My.Computer.FileSystem.OpenTextFileWriter` 方法開啟 <xref:System.IO.StreamWriter> 物件，然後使用該物件搭配 <xref:System.IO.StreamWriter> 類別的 <xref:System.IO.TextWriter.WriteLine%2A> 方法，將字串寫入文字檔。  
  
## <a name="example"></a>範例  
 [!code-vb[VbFileIOWrite#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-with-a-streamwriter_1.vb)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   該檔案存在且為唯讀 (<xref:System.IO.IOException>)。  
  
-   磁碟已滿 (<xref:System.IO.IOException>)。  
  
-   路徑名稱太長 (<xref:System.IO.PathTooLongException>)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 如果檔案不存在，此範例就會建立新的檔案。 如果應用程式需要建立檔案，該應用程式就需要資料夾的 `Create` 權限。 如果檔案已經存在，則應用程式只需要 `Write` 權限，這是較小的權限。 若有可能，更為安全的做法是在部署期間建立檔案，並且只授與單一檔案的 `Read` 權限，而不授與資料夾的 `Create` 權限。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO.StreamWriter>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>  
 [如何：從文字檔讀取](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)  
 [寫入檔案](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)
