---
title: "撰寫資料流"
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
- streams, base streams
- I/O [.NET Framework], composing streams
- Stream class, composing streams
- base streams
- streams, backing stores
ms.assetid: da761658-a535-4f26-a452-b30df47f73d5
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 75800210a52620c5b08a01c5f8fa888bf40843fe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="composing-streams"></a>撰寫資料流
備份存放區是儲存媒體，例如磁碟或記憶體。 每個不同的備份存放區實作自己的資料流，做為實作的<xref:System.IO.Stream>類別。 每個資料流類型讀取和寫入位元組至其指定的支援儲存區。 連接到備份存放區的資料流，會呼叫基底資料流。 基底資料流則具有建構函式具有備份存放區連接的資料流所需的參數。 例如，<xref:System.IO.FileStream>建構函式所指定的路徑參數，指定檔案共用的處理程序等等的方式。  
  
 設計<xref:System.IO>類別提供簡化的資料流組成。 基底資料流可附加至一或多個傳遞資料流，提供您想要的功能。 讀取器或寫入器可以附加至鏈結的結尾，讓慣用的類型可以被輕易讀取或寫入。  
  
 下列程式碼範例會建立**FileStream**周圍現有`MyFile.txt`緩衝區順序`MyFile.txt`。 (請注意， **Filestream**預設緩衝處理。)下一步<xref:System.IO.StreamReader>是用來讀取的字元**FileStream**，傳遞給**StreamReader**做為建構函式引數。 <xref:System.IO.StreamReader.ReadLine%2A>讀取直到<xref:System.IO.StreamReader.Peek%2A>尋找沒有更多字元。  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 下列程式碼範例會建立**FileStream**周圍現有`MyFile.txt`緩衝區順序`MyFile.txt`。 (請注意， **Filestream**預設緩衝處理。)下一步 **BinaryReader**是用來讀取位元組從**FileStream**，傳遞給**BinaryReader**做為建構函式引數。 <xref:System.IO.BinaryReader.ReadByte%2A>讀取直到<xref:System.IO.BinaryReader.PeekChar%2A>尋找沒有更多的位元組。  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
 <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
