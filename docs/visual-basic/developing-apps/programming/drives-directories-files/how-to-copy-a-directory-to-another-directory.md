---
title: 作法：在 Visual Basic 中將目錄複製到另一個目錄
ms.date: 07/20/2015
helpviewer_keywords:
- I/O [Visual Basic], copying directories
- I/O [Visual Basic], copying folders
- folders [Visual Basic], copying
- directories [Visual Basic], copying
ms.assetid: 2a370bd7-10ba-4219-afc4-4519d031eb6c
ms.openlocfilehash: d8f32da0f4b701d745cd5f70feb7cc461a09842f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039461"
---
# <a name="how-to-copy-a-directory-to-another-directory-in-visual-basic"></a>HOW TO：在 Visual Basic 中將目錄複製到另一個目錄

使用 <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A> 方法可將目錄複製到另一個目錄。 這個方法會複製目錄內容以及目錄本身。 如果目標目錄不存在，則會予以建立。 如果目標位置存在同名的目錄且 `overwrite` 設為 `False`，即合併兩個目錄的內容。 您可以在作業期間指定目錄的新名稱。

複製目錄內的檔案時，可能會因為特定的檔案而擲回例外狀況，例如合併期間存在檔案，而 `overwrite` 設為 `False`。 當這類例外狀況被擲回時，它們會合併成單一例外狀況，其 `Data` 屬性保留項目中的檔案或目錄路徑是索引鍵，而特定的例外狀況訊息則包含在對應值中。

## <a name="to-copy-a-directory-to-another-directory"></a>將目錄複製到另一個目錄

- 使用 `CopyDirectory` 方法指定來源和目的地目錄名稱。 下例會將名為 `TestDirectory1` 的目錄複製到 `TestDirectory2`，覆寫現有的檔案。

    [!code-vb[VbVbcnMyFileSystem#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#16)]

    這個程式碼範例也可用為 IntelliSense 程式碼片段。 在程式碼片段選擇器中，它位於 [檔案系統 - 處理磁碟、資料夾和檔案] 中。 如需詳細資訊，請參閱[程式碼片段](/visualstudio/ide/code-snippets)。

## <a name="robust-programming"></a>穩固程式設計

以下條件可能會造成例外狀況：

- 為目錄指定的新名稱包含冒號 (:) 或斜線 (\ 或 /) (<xref:System.ArgumentException>)。

- 因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 (開頭為 \\\\.\\) (<xref:System.ArgumentException>)。

- 路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。

- `destinationDirectoryName` 為 `Nothing` 或空字串 (<xref:System.ArgumentNullException>)

- 來源目錄不存在 (<xref:System.IO.DirectoryNotFoundException>)。

- 來源目錄不是根目錄 (<xref:System.IO.IOException>)。

- 合併路徑指向現有的檔案 (<xref:System.IO.IOException>)。

- 來源路徑和目標路徑相同 (<xref:System.IO.IOException>)。

- `ShowUI` 設定為 `UIOption.AllDialogs` 且使用者取消作業，或無法複製目錄中的一或多個檔案 (<xref:System.OperationCanceledException>)。

- 作業是循環的 (<xref:System.InvalidOperationException>)。

- 路徑包含冒號 (:) (<xref:System.NotSupportedException>)。

- 路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。

- 路徑中的檔案或資料夾名稱包含冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。

- 使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。

- 目的地檔案存在，但無法存取 (<xref:System.UnauthorizedAccessException>)。

## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.CopyDirectory%2A>
- [如何：尋找具有特定模式的子目錄](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-find-subdirectories-with-a-specific-pattern.md)
- [如何：取得目錄的檔案集合](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-get-the-collection-of-files-in-a-directory.md)
