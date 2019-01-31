---
title: HOW TO：將字元寫入字串
ms.date: 03/30/2017
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
ms.openlocfilehash: 125c8ba03c4d1006535dd1e10cbd162b32fede4f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740979"
---
# <a name="how-to-write-characters-to-a-string"></a>HOW TO：將字元寫入字串
下列程式碼範例會以同步和非同步的方式，將字元從字元陣列寫入字串。  
  
## <a name="example"></a>範例  
 下列範例會以同步方式，將 5 個字元從陣列寫入字串。  
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example"></a>範例  
 下一個範例會以非同步方式，從 <xref:System.Windows.Controls.TextBox> 控制項讀取所有字元，然後將其儲存在陣列中。 接著，它會以非同步方式，在個別的行上，將每個字母或空格字元後面接著分行符號寫入 <xref:System.Windows.Controls.TextBlock> 控制項。  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO.StringWriter>
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>
- <xref:System.Text.StringBuilder>
- [檔案和資料流 I/O](../../../docs/standard/io/index.md)
- [Asynchronous File I/O](../../../docs/standard/io/asynchronous-file-i-o.md)
- [如何：列舉目錄和檔案](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [如何：讀取和寫入新建立的資料檔案](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [如何：開啟並附加至記錄檔](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [如何：讀取檔案中的文字](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [如何：將文字寫入檔案](../../../docs/standard/io/how-to-write-text-to-a-file.md)
- [如何：讀取字串中的字元](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
