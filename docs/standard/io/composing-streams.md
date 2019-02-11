---
title: 撰寫資料流
ms.date: 01/21/2019
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
ms.openlocfilehash: 452071e9726a95b4b3d9bb9cefe720d39bbc3e0c
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674343"
---
# <a name="compose-streams"></a>撰寫資料流
*備份存放區*是一種儲存媒體，例如磁碟或記憶體。 每個不同的備份存放區都會實作自己的資料流，作為 <xref:System.IO.Stream> 類別的實作。 

每個資料流類型都會在其指定的備份存放區中讀取和寫入位元組。 連線到備份存放區的資料流稱為*基底資料流*。 基底資料流具有建構函式，其中包含將資料流連線至備份存放區所需的參數。 例如，<xref:System.IO.FileStream> 的建構函式會指定路徑參數，此參數可指定處理程序共用檔案的方式。  

<xref:System.IO> 類別的設計可提供簡化的資料流撰寫。 您可以將基底資料流附加至一個或多個可提供您想要功能的傳遞資料流。 您可以將讀取器或寫入器附加至鏈結的結尾，以便可以輕易地讀取或寫入慣用的類型。  

下列程式碼範例會在現有 **MyFile.txt** 的周圍建立 *FileStream* 以緩衝處理 *MyFile.txt*。 請注意，預設會緩衝處理 **Filestream**。

>[!IMPORTANT]
>範例假設名為 *MyFile.txt* 的檔案已與應用程式存在於相同的資料夾中。  

## <a name="example-use-streamreader"></a>範例：使用 StreamReader
下列範例會建立一個 <xref:System.IO.StreamReader> 來讀取 **FileStream** 中的字元，之後再傳遞至 **StreamReader** 作為其建構函式引數。 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> 接著會一直讀取，直到 <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> 找不到其他字元。  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a>範例：使用 BinaryReader
下列範例會建立一個 <xref:System.IO.BinaryReader> 來讀取 **FileStream** 中的位元組，之後再傳遞至 **BinaryReader** 作為其建構函式引數。 <xref:System.IO.BinaryReader.ReadByte%2A> 接著會一直讀取，直到 <xref:System.IO.BinaryReader.PeekChar%2A> 找不到其他位元組。  
  
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
