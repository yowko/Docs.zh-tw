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
# <a name="how-to-create-a-file-in-visual-basic"></a>如何：在 Visual Basic 中建立檔案
這個範例會在 <xref:System.IO.File> 類別中使用 <xref:System.IO.File.Create%2A> 方法，以在指定的路徑中建立空白文字檔。  
  
## <a name="example"></a>範例  
 [!code-vb[VbFileIOMisc#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-create-a-file_1.vb)]  
  
## <a name="compiling-the-code"></a>編譯程式碼  
 使用 `file` 變數，以寫入檔案。  
  
## <a name="robust-programming"></a>穩固程式設計  
 如果檔案已存在，則會予以取代。  
  
 以下條件可能會造成例外狀況：  
  
-   路徑名稱的格式不正確。 例如，它包含不合法的字元，或只有空白字元 (<xref:System.ArgumentException>)。  
  
-   路徑為唯讀 (<xref:System.IO.IOException>)。  
  
-   路徑名稱是 `Nothing` (<xref:System.ArgumentNullException>)。  
  
-   路徑名稱太長 (<xref:System.IO.PathTooLongException>)。  
  
-   路徑無效 (<xref:System.IO.DirectoryNotFoundException>)。  
  
-   此路徑只是一個冒號 ":" (<xref:System.NotSupportedException>)。  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 在部分信任環境中，可能會擲回 <xref:System.Security.SecurityException>。  
  
 <xref:System.IO.File.Create%2A> 方法呼叫需要 <xref:System.Security.Permissions.FileIOPermission>。  
  
 如果使用者無權建立檔案，則會擲回 <xref:System.UnauthorizedAccessException>。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO>   
 <xref:System.IO.File.Create%2A>   
 [從部分受信任程式碼使用程式庫](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)   
 [程式碼存取安全性的基本概念](https://msdn.microsoft.com/library/33tceax8)

