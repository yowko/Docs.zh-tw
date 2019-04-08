---
title: 作法：在 Visual Basic 中取得目錄的檔案集合
ms.date: 07/20/2015
helpviewer_keywords:
- folders, working with
- files [Visual Basic], accessing
ms.assetid: 6c8ba7e8-dd37-4853-92bf-762b67c98160
ms.openlocfilehash: 788e3d572be1b4e76574af8679ebcff4b61197a5
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58818835"
---
# <a name="how-to-get-the-collection-of-files-in-a-directory-in-visual-basic"></a>作法：在 Visual Basic 中取得目錄的檔案集合
<xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> 方法的多載會傳回唯讀的字串集合，代表了目錄內的檔案名稱：  
  
-   使用 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%28System.String%29> 多載在指定目錄中進行簡單的檔案搜尋，而不搜尋子目錄。  
  
-   使用 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles(System.String,Microsoft.VisualBasic.FileIO.SearchOption,System.String[])> 多載指定搜尋的其他選項。 您可以使用 `wildCards` 參數，指定搜尋模式。 若要在搜尋中包含子目錄，請將 `searchType` 參數設成 <xref:Microsoft.VisualBasic.FileIO.SearchOption.SearchAllSubDirectories?displayProperty=nameWithType>。  
  
 如果找不到符合指定模式的檔案，會傳回空的集合。  
  
### <a name="to-list-files-in-a-directory"></a>列出目錄中的檔案  
  
-   使用其中一個 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A?displayProperty=nameWithType> 方法多載，並在 `directory` 參數中提供要搜尋的目錄名稱和路徑。 下列範例會傳回目錄中的所有檔案，並將它們新增到 `ListBox1`。  
  
     [!code-vb[VbVbcnMyFileSystem#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#32)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 (開頭為 \\\\.\\) (<xref:System.ArgumentException>)。  
  
-   路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。  
  
-   `directory` 不存在 (<xref:System.IO.DirectoryNotFoundException>)。  
  
-   `directory` 指向現有檔案 (<xref:System.IO.IOException>)。  
  
-   路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。  
  
-   路徑中的檔案或目錄名稱含有冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。  
  
-   使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。  
  
-   使用者缺乏必要的權限 (<xref:System.UnauthorizedAccessException>)。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFiles%2A>
- [如何：尋找具有特定模式的檔案](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-files-with-a-specific-pattern.md)
- [如何：尋找具有特定模式的子目錄](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
