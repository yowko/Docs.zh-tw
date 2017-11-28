---
title: "如何：在 Visual Basic 中剖析檔案路徑"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- file names [Visual Basic], parsing [Visual Basic]
- parsing, file paths [Visual Basic]
ms.assetid: c1bd99c9-8160-456a-b5ab-60a49139b923
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 913fe45cf6fc7afdc6e0f31e028bc18808cecf89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-parse-file-paths-in-visual-basic"></a>如何：在 Visual Basic 中剖析檔案路徑
<xref:Microsoft.VisualBasic.FileIO.FileSystem> 物件提供剖析檔案路徑時的數種有用方法。  
  
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A> 方法會採用兩個路徑，並傳回格式正確的合併路徑。  
  
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetParentPath%2A> 方法會傳回所提供路徑之上層的絕對路徑。  
  
-   <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A> 方法會傳回 <xref:System.IO.FileInfo> 物件，這個物件可以進行查詢來判斷檔案的屬性 (例如其名稱和路徑)。  
  
 請不要根據副檔名來判斷檔案內容。 例如，檔案 Form1.vb 可能不是 Visual Basic 來源檔案。  
  
### <a name="to-determine-a-files-name-and-path"></a>判斷檔案的名稱和路徑  
  
-   使用 <xref:System.IO.FileInfo.DirectoryName%2A> 物件的 <xref:System.IO.FileInfo.Name%2A> 和 <xref:System.IO.FileInfo> 屬性來判斷檔案的名稱和路徑。 這個範例會判斷名稱和路徑，並予以顯示。  
  
     [!code-vb[VbVbcnMyFileSystem#54](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_1.vb)]  
  
### <a name="to-combine-a-files-name-and-directory-to-create-the-full-path"></a>合併檔案的名稱和目錄以建立完整路徑  
  
-   使用 `CombinePath` 方法，並提供目錄和名稱。 這個範例會採用前一個範例中所建立的字串 `folderPath` 和 `fileName` 、合併它們，並顯示結果。  
  
     [!code-vb[VbVbcnMyFileSystem#55](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-parse-file-paths_2.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CombinePath%2A>  
 <xref:System.IO.FileInfo>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.GetFileInfo%2A>  
 [如何：取得目錄的檔案集合](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
