---
title: 如何：在 Visual Basic 中從文字檔讀取
ms.date: 07/20/2015
helpviewer_keywords:
- extended characters [Visual Basic], reading
- reading text files [Visual Basic]
- reading data, text files
- examples [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 735fe9d7-0f7a-4185-ba02-f35e580ec4b8
ms.openlocfilehash: eba2e9c23914950d1a93325dc1a00aeba4a0a01c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591582"
---
# <a name="how-to-read-from-text-files-in-visual-basic"></a>如何：在 Visual Basic 中從文字檔讀取
<xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.ReadAllText%2A> 物件的 `My.Computer.FileSystem` 方法允許您從文字檔讀取。 如果檔案的內容是使用 ASCII 或 UTF-8 之類的編碼方式，則可以指定檔案編碼方式。  
  
 如果您是從含擴充字元的檔案讀取，您將需要指定檔案的編碼方式。  
  
> [!NOTE]
>  若要一次讀取檔案中的一行文字，請使用 <xref:Microsoft.VisualBasic.MyServices.FileSystemProxy.OpenTextFileReader%2A> 物件的 `My.Computer.FileSystem` 方法。 `OpenTextFileReader` 方法會傳回 <xref:System.IO.StreamReader> 物件。 您可以使用 <xref:System.IO.StreamReader.ReadLine%2A> 物件的 `StreamReader` 方法，以一次讀取檔案中的一行。 您可以使用 <xref:System.IO.StreamReader.EndOfStream%2A> 物件的 `StreamReader` 方法測試檔案的結尾。  
  
### <a name="to-read-from-a-text-file"></a>若要從文字檔讀取  
  
-   使用 `ReadAllText` 物件的 `My.Computer.FileSystem` 方法並提供路徑，將文字檔的內容讀取到字串中。 下列範例會將 test.txt 的內容讀取到字串中，然後顯示於訊息方塊中。  
  
     [!code-vb[VbFileIORead#2](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_1.vb)]  
  
### <a name="to-read-from-a-text-file-that-is-encoded"></a>若要從已編碼的文字檔讀取  
  
-   使用 `ReadAllText` 物件的 `My.Computer.FileSystem` 方法，並且提供路徑和檔案編碼類型，將文字檔的內容讀取到字串中。 下列範例會將 UTF32 檔案 test.txt 的內容讀取到字串中，然後顯示於訊息方塊中。  
  
     [!code-vb[VbFileIORead#3](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-read-from-text-files_2.vb)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 以下條件可能會造成例外狀況：  
  
-   因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 (<xref:System.ArgumentException>)。  
  
-   路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。  
  
-   檔案不存在 (<xref:System.IO.FileNotFoundException>)。  
  
-   檔案正由另一個程序使用中，或發生 I/O 錯誤 (<xref:System.IO.IOException>)。  
  
-   路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。  
  
-   路徑中的檔案或目錄名稱含有冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。  
  
-   沒有足夠的記憶體可將字串寫入緩衝區 (<xref:System.OutOfMemoryException>)。  
  
-   使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。  
  
 請勿根據檔案名稱來判斷檔案內容。 例如，檔案 Form1.vb 可能不是 Visual Basic 來源檔案。  
  
 在應用程式中使用這些資料之前，請先驗證所有輸入值。 檔案內容可能與預期不同，並從檔案讀取資料的方法會失敗。  
  
## <a name="see-also"></a>請參閱  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllText%2A>  
 [從檔案讀取](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)  
 [如何：從逗號分隔文字檔讀取](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-comma-delimited-text-files.md)  
 [如何：從固定寬度的文字檔讀取](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-fixed-width-text-files.md)  
 [如何：以多種格式從文字檔讀取](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)  
 [疑難排解：讀取和寫入文字檔](../../../../visual-basic/developing-apps/programming/drives-directories-files/troubleshooting-reading-from-and-writing-to-text-files.md)  
 [逐步解說：在 Visual Basic 中管理檔案和目錄](../../../../visual-basic/developing-apps/programming/drives-directories-files/walkthrough-manipulating-files-and-directories.md)  
 [檔案編碼方式](../../../../visual-basic/developing-apps/programming/drives-directories-files/file-encodings.md)
