---
title: HOW TO：將字元寫入字串中
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb35c61b34fa571f35da6691ebe7fa2516eb2df1
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674746"
---
# <a name="how-to-write-characters-to-a-string"></a>HOW TO：將字元寫入字串中
下列程式碼範例會以同步或非同步的方式，將字元從字元陣列寫入字串。  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a>範例：在主控台應用程式中以同步方式寫入字元  
 下列範例會使用 <xref:System.IO.StringWriter>，以同步方式將五個字元寫入 <xref:System.Text.StringBuilder> 物件。 
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a>範例：在 WPF 應用程式中以非同步方式寫入字元 
 下一個範例是 WPF 應用程式背後的程式碼。 在載入視窗時，此範例會以非同步方式，從 <xref:System.Windows.Controls.TextBox> 控制項讀取所有字元，然後將其儲存在陣列中。 接著會以非同步方式將每個字母或空格字元寫入 <xref:System.Windows.Controls.TextBlock> 控制項的個別行。  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [檔案和資料流 I/O](../../../docs/standard/io/index.md)  
- [非同步檔案 I/O](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [如何：列舉目錄和檔案](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [如何：讀取和寫入新建立的資料檔案](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [如何：開啟並附加至記錄檔](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [如何：讀取檔案中的文字](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [如何：將文字寫入檔案](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [如何：讀取字串中的字元](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
