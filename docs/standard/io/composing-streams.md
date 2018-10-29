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
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2018
ms.locfileid: "48841173"
---
# <a name="composing-streams"></a><span data-ttu-id="c854e-102">撰寫資料流</span><span class="sxs-lookup"><span data-stu-id="c854e-102">Composing Streams</span></span>
<span data-ttu-id="c854e-103">備份存放區是一種儲存媒體，例如磁碟或記憶體。</span><span class="sxs-lookup"><span data-stu-id="c854e-103">A backing store is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="c854e-104">每個不同的備份存放區都會實作自己的資料流，作為 <xref:System.IO.Stream> 類別的實作。</span><span class="sxs-lookup"><span data-stu-id="c854e-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="c854e-105">每個資料流類型都會在其指定的備份存放區中讀取和寫入位元組。</span><span class="sxs-lookup"><span data-stu-id="c854e-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="c854e-106">連線到備份存放區的資料流稱為基底資料流。</span><span class="sxs-lookup"><span data-stu-id="c854e-106">Streams that connect to backing stores are called base streams.</span></span> <span data-ttu-id="c854e-107">基底資料流的建構函式具有將資料流連線至備份存放區所需的參數。</span><span class="sxs-lookup"><span data-stu-id="c854e-107">Base streams have constructors that have the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="c854e-108">例如，<xref:System.IO.FileStream> 的建構函式會指定路徑參數，此參數可指定處理程序共用檔案的方式等等。</span><span class="sxs-lookup"><span data-stu-id="c854e-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes, and so on.</span></span>  
  
 <span data-ttu-id="c854e-109"><xref:System.IO> 類別的設計可提供簡化的資料流撰寫。</span><span class="sxs-lookup"><span data-stu-id="c854e-109">The design of the <xref:System.IO> classes provides simplified stream composing.</span></span> <span data-ttu-id="c854e-110">基底資料流可以附加至一個或多個可提供您想要之功能的傳遞資料流。</span><span class="sxs-lookup"><span data-stu-id="c854e-110">Base streams can be attached to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="c854e-111">讀取器或寫入器可以附加至鏈結的結尾，如此可以輕易地讀取或寫入慣用的類型。</span><span class="sxs-lookup"><span data-stu-id="c854e-111">A reader or writer can be attached to the end of the chain so that the preferred types can be read or written easily.</span></span>  
  
 <span data-ttu-id="c854e-112">下列程式碼範例會在現有 `MyFile.txt` 的周圍建立 **FileStream** 以緩衝處理 `MyFile.txt` </span><span class="sxs-lookup"><span data-stu-id="c854e-112">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="c854e-113">(請注意，預設會緩衝處理 **Filestream**)。接著，系統會建立一個 <xref:System.IO.StreamReader> 來讀取 **FileStream** 中的字元，之後再傳遞至 **StreamReader** 作為其建構函式引數。</span><span class="sxs-lookup"><span data-stu-id="c854e-113">(Note that **FileStreams** are buffered by default.) Next, a <xref:System.IO.StreamReader> is created to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="c854e-114"><xref:System.IO.StreamReader.ReadLine%2A> 會讀取到 <xref:System.IO.StreamReader.Peek%2A> 找不到其他字元為止。</span><span class="sxs-lookup"><span data-stu-id="c854e-114"><xref:System.IO.StreamReader.ReadLine%2A> reads until <xref:System.IO.StreamReader.Peek%2A> finds no more characters.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 <span data-ttu-id="c854e-115">下列程式碼範例會在現有 `MyFile.txt` 的周圍建立 **FileStream** 以緩衝處理 `MyFile.txt` </span><span class="sxs-lookup"><span data-stu-id="c854e-115">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="c854e-116">(請注意，預設會緩衝處理 **Filestream**)。接著，系統會建立一個 **BinaryReader** 來讀取 **FileStream** 中的位元組，之後再傳遞至 **BinaryReader** 作為其建構函式引數。</span><span class="sxs-lookup"><span data-stu-id="c854e-116">(Note that **FileStreams** are buffered by default.) Next, a **BinaryReader** is created to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="c854e-117"><xref:System.IO.BinaryReader.ReadByte%2A> 會讀取到 <xref:System.IO.BinaryReader.PeekChar%2A> 找不到其他位元組為止。</span><span class="sxs-lookup"><span data-stu-id="c854e-117"><xref:System.IO.BinaryReader.ReadByte%2A> reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="c854e-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c854e-118">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
