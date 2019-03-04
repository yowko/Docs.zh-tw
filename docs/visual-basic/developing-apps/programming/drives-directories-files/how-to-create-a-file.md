---
title: 作法：在 Visual Basic 中建立檔案
ms.date: 07/20/2015
helpviewer_keywords:
- text files [Visual Basic], creating
- files [Visual Basic], creating
ms.assetid: 0253bb6d-5519-4a50-b882-b93ef5cca0d9
ms.openlocfilehash: 397db70cc8f5977bd861e9e6d6df2f0c8f884db2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967006"
---
# <a name="how-to-create-a-file-in-visual-basic"></a>HOW TO：在 Visual Basic 中建立檔案
這個範例會在 <xref:System.IO.File> 類別中使用 <xref:System.IO.File.Create%2A> 方法，以在指定的路徑中建立空白文字檔。  
  
## <a name="example"></a>範例  
 [!code-vb[VbFileIOMisc#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIOMisc/VB/class2.vb#1)]  
  
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
- <xref:System.IO>
- <xref:System.IO.File.Create%2A>
- [從部分受信任程式碼使用程式庫](../../../../framework/misc/using-libraries-from-partially-trusted-code.md)
- [程式碼存取安全性的基本概念](../../../../framework/misc/code-access-security-basics.md)
