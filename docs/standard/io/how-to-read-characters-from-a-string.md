---
title: HOW TO：讀取字串中的字元
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reading characters from strings
- data streams, reading characters from string
- I/O [.NET Framework], reading characters from strings
- reading data, strings
- streams, reading characters from string
ms.assetid: 27ea5e52-6db8-42d8-980a-50bcfc7fd270
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 01d5fb2e4f785a4a510715b58e95d310a6ffa4e2
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675344"
---
# <a name="how-to-read-characters-from-a-string"></a>HOW TO：讀取字串中的字元
下列程式碼範例會示範如何以同步或非同步的方式，從字串讀取字元。  
  
## <a name="example-read-characters-synchronously"></a>範例：以同步方式讀取字元 
 此範例會以同步方式，從字串讀取 13 個字元、將其儲存在陣列中，然後顯示它們。 接著讀取字串中剩餘的字元、從陣列的第六個元素開始儲存這些字元，然後顯示陣列的內容。  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a>範例：以非同步方式讀取字元  
 下一個範例是 WPF 應用程式背後的程式碼。 在載入視窗時，此範例會以非同步方式，從 <xref:System.Windows.Controls.TextBox> 控制項讀取所有字元，然後將其儲存在陣列中。 接著會以非同步方式將每個字母或空格字元寫入 <xref:System.Windows.Controls.TextBlock> 控制項的個別行。  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [非同步檔案 I/O](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [如何：建立目錄清單](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)  
- [如何：讀取和寫入新建立的資料檔案](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [如何：開啟並附加至記錄檔](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [如何：讀取檔案中的文字](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [如何：將文字寫入檔案](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [如何：將字元寫入字串](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [檔案和資料流 I/O](../../../docs/standard/io/index.md)
