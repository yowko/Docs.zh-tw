---
title: 如何：在 Visual Basic 中尋找具有特定模式的檔案
ms.date: 07/20/2015
helpviewer_keywords:
- files [Visual Basic], finding
- pattern matching
- patterns, matching
ms.assetid: 25e3b71d-b844-4293-9e4e-f06c5836b5cc
ms.openlocfilehash: c1e627893ca1ff03b405f0fb45072214ea76a194
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-files-with-a-specific-pattern-in-visual-basic"></a>如何：在 Visual Basic 中尋找具有特定模式的檔案
<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A> 方法會傳回代表檔案路徑名稱的唯讀字串集合。 您可以使用 `wildCards` 參數指定特定模式。 如果您想要在搜尋中包含子目錄，請將 `searchType` 參數設定為 `SearchOption.SearchAllSubDirectories`。  
  
 如果找不到符合指定模式的檔案，會傳回空的集合。  
  
> [!NOTE]
>  如需使用 `System.IO` 命名空間的 `DirectoryInfo` 類別來傳回檔案清單的資訊，請參閱 <xref:System.IO.DirectoryInfo.GetFiles%2A>。  
  
### <a name="to-find-files-with-a-specified-pattern"></a>尋找具有所指定模式的檔案  
  
-   使用 `GetFiles` 方法，並提供您想要搜尋之目錄的名稱和路徑，並指定模式。 下列範例會傳回目錄中副檔名為 `.dll` 的所有檔案，並將它們新增到 `ListBox1`。  
  
     [!code-vb[VbFileIOMisc#4](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-find-files-with-a-specific-pattern_1.vb)]  
  
## <a name="net-framework-security"></a>.NET Framework 安全性  
 以下條件可能會造成例外狀況：  
  
-   因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 (開頭為 \\\\.\\) (<xref:System.ArgumentException>)。  
  
-   路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。  
  
-   `directory` 不存在 (<xref:System.IO.DirectoryNotFoundException>)。  
  
-   `directory` 指向現有檔案 (<xref:System.IO.IOException>)。  
  
-   路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。  
  
-   路徑中的檔案或資料夾名稱包含冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。  
  
-   使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。  
  
-   使用者缺乏必要的權限 (<xref:System.UnauthorizedAccessException>)。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.GetFiles%2A>  
 [如何：尋找具有特定模式的子目錄](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)  
 [疑難排解：讀取和寫入文字檔](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 [如何：取得目錄的檔案集合](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
