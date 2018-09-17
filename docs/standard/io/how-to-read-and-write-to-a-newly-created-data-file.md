---
title: 如何：讀取和寫入新建立的資料檔案
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, reading and writing data
- BinaryReader class, examples
- I/O [.NET Framework], reading data
- I/O [.NET Framework], writing data
- BinaryWriter class, examples
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 65c56a11531f705b7e047e435ec575969d39a616
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/16/2018
ms.locfileid: "45592902"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>如何：讀取和寫入新建立的資料檔案
<xref:System.IO.BinaryWriter> 和 <xref:System.IO.BinaryReader?displayProperty=nameWithType> 類別用於寫入和讀取資料，而不是字元字串。 下列範例示範如何在稱為 `Test.data` 的新空白檔案資料流中寫入資料和讀取資料。 在目前的目錄中建立資料檔案之後，系統會建立相關聯的 <xref:System.IO.BinaryWriter> 和 <xref:System.IO.BinaryReader> 物件，而且會使用 <xref:System.IO.BinaryWriter> 物件，將 0 到 10 的整數寫入 `Test.data`，讓檔案指標留在檔案的結尾。 將檔案指標設定為原點之後，<xref:System.IO.BinaryReader> 物件會讀出指定的內容。  
  
## <a name="example"></a>範例  
 [!code-cpp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CPP/source6.cpp#7)]
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 如果 `Test.data` 已存在於目前的目錄中，則會擲回 <xref:System.IO.IOException> 例外狀況。 當您初始化檔案資料流時使用檔案模式選項 <xref:System.IO.FileMode.Create?displayProperty=nameWithType>，就會一律建立新檔案，而不會擲回例外狀況。  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [操作說明：列舉目錄和檔案](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [如何：開啟並附加至記錄檔](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [如何：從檔案讀取文字](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [如何：將文字寫入檔案](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [如何：從字串中讀取字元](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [如何：將字元寫入至字串](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [檔案和資料流 I/O](../../../docs/standard/io/index.md)
