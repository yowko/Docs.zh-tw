---
title: 'How to: Read from text files with multiple formats'
ms.date: 07/20/2015
helpviewer_keywords:
- TextFieldParser object, reading from a file
- TextFieldType enumeration
- My.Computer.FileSystem.WriteAllText method, parsing structured text files
- WriteAllText method [Visual Basic], parsing structured text files
- PeekChars method [Visual Basic], determining format of text
- reading text files [Visual Basic], multiple formats
- I/O [Visual Basic], reading text files
- text files [Visual Basic], reading
ms.assetid: 8d185eb2-79ca-42cd-95a7-d3ff44a5a0f8
ms.openlocfilehash: b36c781d5f8333749d346bb8f19540f0d1bd1692
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74334577"
---
# <a name="how-to-read-from-fext-files-with-multiple-formats-in-visual-basic"></a>How to: Read from fext files with multiple formats in Visual Basic

<xref:Microsoft.VisualBasic.FileIO.TextFieldParser> 物件可讓您輕鬆有效率地剖析結構化文字檔，例如記錄檔。 您可以使用 `PeekChars` 方法來處理具有多種格式的檔案，以在剖析整個檔案時判斷每行格式。
  
### <a name="to-parse-a-text-file-with-multiple-formats"></a>剖析具有多種格式的文字檔

1. Add a text file named *testfile.txt* to your project. Add the following content to the text file:

    ```text
    Err  1001 Cannot access resource.
    Err  2014 Resource not found.
    Acc  10/03/2009User1      Administrator.
    Err  0323 Warning: Invalid access attempt.
    Acc  10/03/2009User2      Standard user.
    Acc  10/04/2009User2      Standard user.
    ```

2. 定義預期的格式，以及回報錯誤時所使用的格式。 每個陣列中的最後一個項目為 -1，因此將最後一個欄位假設為可變寬度。 陣列中的最後一個項目小於或等於 0 時會發生這種情況。

     [!code-vb[VbFileIORead#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#4)]

3. 建立新的 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser> 物件，並定義寬度和格式。

     [!code-vb[VbFileIORead#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#5)]

4. 反覆執行資料列，並在讀取之前測試格式。

     [!code-vb[VbFileIORead#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#6)]

5. 將錯誤寫入主控台。

     [!code-vb[VbFileIORead#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#7)]

## <a name="example"></a>範例

The following is the complete example that reads from the file `testfile.txt`:

 [!code-vb[VbFileIORead#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbFileIORead/VB/Class1.vb#8)]

## <a name="robust-programming"></a>穩固程式設計

以下條件可能會造成例外狀況：  
  
- 無法使用指定格式剖析資料列 (<xref:Microsoft.VisualBasic.FileIO.MalformedLineException>)。 例外狀況訊息指出造成例外狀況的文字行，而 <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.ErrorLine%2A> 屬性被指派至包含於該文字行中的文字。
- 指定的檔案不存在 (<xref:System.IO.FileNotFoundException>)。
- 發生使用者權限不足而無法存取檔案的部分信任狀況 (<xref:System.Security.SecurityException>)
- 路徑太長 (<xref:System.IO.PathTooLongException>)。
- 使用者沒有足夠權限以存取檔案 (<xref:System.UnauthorizedAccessException>)。

## <a name="see-also"></a>請參閱

- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.PeekChars%2A>
- <xref:Microsoft.VisualBasic.FileIO.MalformedLineException>
- <xref:Microsoft.VisualBasic.FileIO.FileSystem.WriteAllText%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.EndOfData%2A>
- <xref:Microsoft.VisualBasic.FileIO.TextFieldParser.TextFieldType%2A>
- [如何：從逗號分隔文字檔讀取](how-to-read-from-comma-delimited-text-files.md)
- [如何：從固定寬度的文字檔讀取](how-to-read-from-fixed-width-text-files.md)
- [使用 TextFieldParser 物件剖析文字檔](parsing-text-files-with-the-textfieldparser-object.md)
