---
title: HOW TO：在 Visual Basic 中尋找具有特定模式的子目錄
ms.date: 07/20/2015
helpviewer_keywords:
- pattern matching
- folders, finding
ms.assetid: c9265fd1-7483-4150-8b7f-ff642caa939d
ms.openlocfilehash: 32b0f5c1052d45e9c068d291f8e6efaf6dfbf906
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677689"
---
# <a name="how-to-find-subdirectories-with-a-specific-pattern-in-visual-basic"></a>HOW TO：在 Visual Basic 中尋找具有特定模式的子目錄
<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A> 方法會傳回代表目錄中子目錄之路徑名稱的唯讀字串集合。 您可以使用 `wildCards` 參數指定特定模式。 如果您想要在搜尋中包括子目錄的內容，請將 `searchType` 參數設定為 `SearchOption.SearchAllSubDirectories`。  
  
 如果找不到符合指定模式的目錄，則會傳回空集合。  
  
### <a name="to-find-subdirectories-with-a-specific-pattern"></a>尋找具有特定模式的子目錄  
  
-   使用 `GetDirectories` 方法，並提供您想要搜尋之目錄的名稱和路徑。 下列範例會傳回目錄結構中名稱包含 "Logs" 單字的所有目錄，並將它們新增至 `ListBox1`。  
  
     [!code-vb[VbVbcnFileAccess#1](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-find-subdirectories-with-a-specific-pattern_1.vb)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 (開頭為 \\\\.\\) (<xref:System.ArgumentException>)。  
  
-   路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。  
  
-   一或多個指定的萬用字元是 `Nothing`、空字串，或只包含空格 (<xref:System.ArgumentNullException>)。  
  
-   `directory` 不存在 (<xref:System.IO.DirectoryNotFoundException>)。  
  
-   `directory` 指向現有檔案 (<xref:System.IO.IOException>)。  
  
-   路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。  
  
-   路徑中的檔案或資料夾名稱包含冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。  
  
-   使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。  
  
-   使用者缺乏必要的權限 (<xref:System.UnauthorizedAccessException>)。  
  
## <a name="see-also"></a>另請參閱
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetDirectories%2A>
- [如何：尋找具有特定模式的檔案](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
