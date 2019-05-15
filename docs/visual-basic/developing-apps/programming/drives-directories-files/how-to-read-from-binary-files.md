---
title: 作法：在 Visual Basic 中從二進位檔案讀取
ms.date: 07/20/2015
helpviewer_keywords:
- binary files [Visual Basic], reading from
- I/O [Visual Basic], reading from binary files
- ReadAllBytes method [Visual Basic], reading from binary files
- My.Computer.FileSystem object, reading from binary files
ms.assetid: d2b1269e-24b6-42e0-9414-ae708db282d8
ms.openlocfilehash: 72e9361193a5b099841d989e842ff36662cf690d
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64623725"
---
# <a name="how-to-read-from-binary-files-in-visual-basic"></a>作法：在 Visual Basic 中從二進位檔案讀取
`My.Computer.FileSystem` 物件提供用來讀取二進位檔案的 `ReadAllBytes` 方法。  
  
### <a name="to-read-from-a-binary-file"></a>讀取二進位檔案  
  
- 使用 `ReadAllBytes` 方法，以將檔案內容傳回為位元組陣列。 此範例會從檔案 `C:/Documents and Settings/selfportrait.jpg` 讀取。  
  
     [!code-vb[VbVbcnMyFileSystem#78](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#78)]  
  
- 對於大型二進位檔案，您可以使用 <xref:System.IO.FileStream> 物件的 <xref:System.IO.FileStream.Read%2A> 方法，同時只讀取指定數量的檔案。 您接著可以限制每次讀取作業時將檔案的多少內容載入至記憶體。 下列程式碼範例會複製檔案，並可讓呼叫端指定在每次讀取作業時將檔案的多少內容讀入記憶體。  
  
     [!code-vb[VbVbcnMyFileSystem#91](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnMyFileSystem/VB/Class1.vb#91)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 下列條件可能會造成擲回例外狀況：  
  
- 因下列其中一項原因而導致路徑無效：它是長度為零的字串、它只包含空白字元、它包含無效的字元，或者它是裝置路徑 (<xref:System.ArgumentException>)。  
  
- 路徑無效，因為它是 `Nothing` (<xref:System.ArgumentNullException>)。  
  
- 檔案不存在 (<xref:System.IO.FileNotFoundException>)。  
  
- 檔案正由另一個處理序使用中，或發生 I/O 錯誤 (<xref:System.IO.IOException>)。  
  
- 路徑超過系統定義的最大長度 (<xref:System.IO.PathTooLongException>)。  
  
- 路徑中的檔案或目錄名稱含有冒號 (:)，或者是無效的格式 (<xref:System.NotSupportedException>)。  
  
- 沒有足夠的記憶體可將字串寫入緩衝區 (<xref:System.OutOfMemoryException>)。  
  
- 使用者缺乏必要的使用權限來檢視路徑 (<xref:System.Security.SecurityException>)。  
  
 請勿根據檔案名稱來判斷檔案內容。 例如，檔案 Form1.vb 可能不是 Visual Basic 來源檔案。  
  
 在應用程式中使用這些資料之前，請先驗證所有輸入值。 檔案內容可能與預期不同，並從檔案讀取資料的方法會失敗。  
  
## <a name="see-also"></a>另請參閱

- <xref:Microsoft.VisualBasic.FileIO.FileSystem.ReadAllBytes%2A>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllBytes%2A>
- [從檔案讀取](../../../../visual-basic/developing-apps/programming/drives-directories-files/reading-from-files.md)
- [如何：以多種格式從文字檔讀取](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files-with-multiple-formats.md)
- [在剪貼簿儲存和讀取資料](../../../../visual-basic/developing-apps/programming/computer-resources/storing-data-to-and-reading-from-the-clipboard.md)
