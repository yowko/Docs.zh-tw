---
title: 如何：讀取和寫入新建立的資料檔案
description: 瞭解如何使用 BinaryReader 和 BinaryWriter 類別，在 .NET 中讀取和寫入新建立的資料檔案。
ms.date: 01/21/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- streams, reading and writing data
- BinaryReader class, examples
- I/O [.NET], reading data
- I/O [.NET], writing data
- BinaryWriter class, examples
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
ms.openlocfilehash: 8ec14ef560ddd69e8c9217298271b7ec715fcb9c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734578"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>如何：讀取和寫入新建立的資料檔案

<xref:System.IO.BinaryWriter?displayProperty=nameWithType> 和 <xref:System.IO.BinaryReader?displayProperty=nameWithType> 類別用於寫入和讀取資料，而不是字元字串。 下列範例顯示如何建立空的檔案資料流、將資料寫入其中，以及從中讀取資料。

此範例會在目前的目錄中建立一個稱為 *Test.data* 的資料檔案、建立相關聯的 <xref:System.IO.BinaryWriter> 和 <xref:System.IO.BinaryReader> 物件，而且會使用 <xref:System.IO.BinaryWriter> 物件，將 0 到 10 的整數寫入 *Test.data*，讓檔案指標留在檔案的結尾。 <xref:System.IO.BinaryReader> 物件接著會將檔案指標設定為原點， 並讀出指定的內容。  
  
> [!NOTE]
> 如果 *Test.data* 已存在於目前的目錄中，則會擲回 <xref:System.IO.IOException> 例外狀況。 使用檔案模式選項 <xref:System.IO.FileMode.Create?displayProperty=nameWithType>，而不是 <xref:System.IO.FileMode.CreateNew?displayProperty=nameWithType>，來一律建立新檔案，而不會擲回例外狀況。  
  
## <a name="example"></a>範例  

 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [如何：列舉目錄和檔案](how-to-enumerate-directories-and-files.md)  
- [如何：開啟並附加至記錄檔](how-to-open-and-append-to-a-log-file.md)  
- [如何：從檔案讀取文字](how-to-read-text-from-a-file.md)  
- [如何：將文字寫入檔案](how-to-write-text-to-a-file.md)  
- [如何：從字串讀取字元](how-to-read-characters-from-a-string.md)  
- [如何：將字元寫入字串](how-to-write-characters-to-a-string.md)  
- [檔案和資料流 I/O](index.md)
