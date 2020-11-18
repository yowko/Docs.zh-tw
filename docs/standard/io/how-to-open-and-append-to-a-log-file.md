---
title: 如何：開啟並附加至記錄檔
description: 使用 .NET 中的 StreamWriter 和 StreamReader 類別來開啟並附加至記錄檔，這會將字元寫入和讀取資料流程中的字元。
ms.date: 01/21/2019
dev_langs:
- csharp
- vb
helpviewer_keywords:
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
ms.openlocfilehash: f92dd34b15ca79f229b365c7c2db4ace411d9353
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830749"
---
# <a name="how-to-open-and-append-to-a-log-file"></a>如何：開啟並附加至記錄檔

<xref:System.IO.StreamWriter> 和 <xref:System.IO.StreamReader> 會在資料流中寫入字元和讀取字元。 下列程式碼範例會開啟用於輸入的 *log.txt* 檔案，或者，如果該檔案不存在，則會建立它，並將記錄資訊附加至檔案的結尾。 此範例接著會將檔案的內容寫入標準輸出以供顯示。

此範例的替代方法是，您可以將資訊儲存成單一字串或字串陣列，並使用 <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> 或 <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> 方法來達成相同的功能。  
  
> [!NOTE]
> Visual Basic 使用者可以選擇使用 <xref:Microsoft.VisualBasic.Logging.Log> 類別或 <xref:Microsoft.VisualBasic.FileIO.FileSystem> 類別所提供的方法和屬性來建立或寫入記錄檔。  
  
## <a name="example"></a>範例  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [如何：列舉目錄和檔案](how-to-enumerate-directories-and-files.md)  
- [如何：讀取和寫入新建立的資料檔案](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [如何：從檔案讀取文字](how-to-read-text-from-a-file.md)  
- [如何：將文字寫入檔案](how-to-write-text-to-a-file.md)  
- [如何：從字串讀取字元](how-to-read-characters-from-a-string.md)  
- [如何：將字元寫入字串](how-to-write-characters-to-a-string.md)  
- [檔案和資料流程 i/o](index.md)
