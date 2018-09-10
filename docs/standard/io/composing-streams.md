---
title: 撰寫資料流
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5e52b827f337892c33ec61b9affa1cc646a759c5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44182460"
---
# <a name="composing-streams"></a>撰寫資料流
備份存放區是一種儲存媒體，例如磁碟或記憶體。 每個不同的備份存放區都會實作自己的資料流，作為 <xref:System.IO.Stream> 類別的實作。 每個資料流類型都會在其指定的備份存放區中讀取和寫入位元組。 連線到備份存放區的資料流稱為基底資料流。 基底資料流的建構函式具有將資料流連線至備份存放區所需的參數。 例如，<xref:System.IO.FileStream> 的建構函式會指定路徑參數，此參數可指定處理程序共用檔案的方式等等。  
  
 <xref:System.IO> 類別的設計可提供簡化的資料流撰寫。 基底資料流可以附加至一個或多個可提供您想要之功能的傳遞資料流。 讀取器或寫入器可以附加至鏈結的結尾，如此可以輕易地讀取或寫入慣用的類型。  
  
 下列程式碼範例會在現有 `MyFile.txt` 的周圍建立 **FileStream** 以緩衝處理 `MyFile.txt`  (請注意，預設會緩衝處理 **Filestream**)。接著，系統會建立一個 <xref:System.IO.StreamReader> 來讀取 **FileStream** 中的字元，之後再傳遞至 **StreamReader** 作為其建構函式引數。 <xref:System.IO.StreamReader.ReadLine%2A> 會讀取到 <xref:System.IO.StreamReader.Peek%2A> 找不到其他字元為止。  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 下列程式碼範例會在現有 `MyFile.txt` 的周圍建立 **FileStream** 以緩衝處理 `MyFile.txt`  (請注意，預設會緩衝處理 **Filestream**)。接著，系統會建立一個 **BinaryReader** 來讀取 **FileStream** 中的位元組，之後再傳遞至 **BinaryReader** 作為其建構函式引數。 <xref:System.IO.BinaryReader.ReadByte%2A> 會讀取到 <xref:System.IO.BinaryReader.PeekChar%2A> 找不到其他位元組為止。  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IO.StreamReader>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
