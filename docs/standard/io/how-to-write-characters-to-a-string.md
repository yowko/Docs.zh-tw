---
title: "如何：將字元寫入至字串"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 336a7fec5e64cc0c45566631c73928e0c1d40a5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-characters-to-a-string"></a>如何：將字元寫入至字串
下列程式碼範例將字元寫入同步和非同步方式從字元陣列轉換為字串。  
  
## <a name="example"></a>範例  
 下列範例將 5 個字元以同步方式從陣列寫入字串。  
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example"></a>範例  
 下一個範例會讀取所有字元以非同步方式從<xref:System.Windows.Controls.TextBox>控制項，然後將它們儲存在陣列中。 然後，它以非同步方式寫入每個字母或空格字元後面接著分行的個別行上<xref:System.Windows.Controls.TextBlock>控制項。  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO.StringWriter>  
 <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
 <xref:System.Text.StringBuilder>  
 [檔案和資料流 I-O](../../../docs/standard/io/index.md)  
 [非同步檔案 I/O](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [操作說明：列舉目錄和檔案](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [操作說明：讀取和寫入新建立的資料檔案](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [如何：開啟並附加至記錄檔](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [如何：從檔案讀取文字](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [如何：將文字寫入檔案](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [如何：從字串中讀取字元](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
