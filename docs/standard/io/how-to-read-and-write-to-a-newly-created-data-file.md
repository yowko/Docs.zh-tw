---
title: "如何：讀取和寫入新建立的資料檔案"
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
- cpp
helpviewer_keywords:
- streams, reading and writing data
- BinaryReader class, examples
- I/O [.NET Framework], reading data
- I/O [.NET Framework], writing data
- BinaryWriter class, examples
ms.assetid: e209d949-31e8-44ea-8e38-87f9093f3093
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: b547f2c85495a497e5fc384f9a2ea44de7bf861c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a>如何：讀取和寫入新建立的資料檔案
<xref:System.IO.BinaryWriter>和<xref:System.IO.BinaryReader?displayProperty=nameWithType>類別用於寫入和讀取資料而不是字元字串。 下列範例示範如何寫入資料，並從呼叫新的空白檔案資料流讀取資料`Test.data`。 建立在目前目錄中，相關聯的資料檔案後<xref:System.IO.BinaryWriter>和<xref:System.IO.BinaryReader>建立物件，而<xref:System.IO.BinaryWriter>物件用來寫入整數 0 到 10，以`Test.data`，，讓檔案指標的結尾檔案。 之後回到原始設定檔案指標<xref:System.IO.BinaryReader>物件讀取出指定的內容。  
  
## <a name="example"></a>範例  
 [!code-cpp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CPP/source6.cpp#7)]
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="robust-programming"></a>穩固程式設計  
 如果`Test.data`已存在於目前的目錄，<xref:System.IO.IOException>擲回例外狀況。 當您初始化檔案資料流時使用檔案模式選項 <xref:System.IO.FileMode.Create?displayProperty=nameWithType>，就會一律建立新檔案，而不會擲回例外狀況。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryWriter>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
 <xref:System.IO.SeekOrigin>  
 [操作說明：列舉目錄和檔案](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [如何：開啟並附加至記錄檔](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [如何：從檔案讀取文字](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [如何：將文字寫入檔案](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [如何：從字串中讀取字元](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [如何：將字元寫入至字串](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [檔案和資料流 I-O](../../../docs/standard/io/index.md)
