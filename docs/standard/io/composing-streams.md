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
# <a name="composing-streams"></a><span data-ttu-id="856e7-102">撰寫資料流</span><span class="sxs-lookup"><span data-stu-id="856e7-102">Composing Streams</span></span>
<span data-ttu-id="856e7-103">備份存放區是儲存媒體，例如磁碟或記憶體。</span><span class="sxs-lookup"><span data-stu-id="856e7-103">A backing store is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="856e7-104">每個不同的備份存放區實作自己的資料流，做為實作的<xref:System.IO.Stream>類別。</span><span class="sxs-lookup"><span data-stu-id="856e7-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="856e7-105">每個資料流類型讀取和寫入位元組至其指定的支援儲存區。</span><span class="sxs-lookup"><span data-stu-id="856e7-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="856e7-106">連接到備份存放區的資料流，會呼叫基底資料流。</span><span class="sxs-lookup"><span data-stu-id="856e7-106">Streams that connect to backing stores are called base streams.</span></span> <span data-ttu-id="856e7-107">基底資料流則具有建構函式具有備份存放區連接的資料流所需的參數。</span><span class="sxs-lookup"><span data-stu-id="856e7-107">Base streams have constructors that have the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="856e7-108">例如，<xref:System.IO.FileStream>建構函式所指定的路徑參數，指定檔案共用的處理程序等等的方式。</span><span class="sxs-lookup"><span data-stu-id="856e7-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes, and so on.</span></span>  
  
 <span data-ttu-id="856e7-109">設計<xref:System.IO>類別提供簡化的資料流組成。</span><span class="sxs-lookup"><span data-stu-id="856e7-109">The design of the <xref:System.IO> classes provides simplified stream composing.</span></span> <span data-ttu-id="856e7-110">基底資料流可附加至一或多個傳遞資料流，提供您想要的功能。</span><span class="sxs-lookup"><span data-stu-id="856e7-110">Base streams can be attached to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="856e7-111">讀取器或寫入器可以附加至鏈結的結尾，讓慣用的類型可以被輕易讀取或寫入。</span><span class="sxs-lookup"><span data-stu-id="856e7-111">A reader or writer can be attached to the end of the chain so that the preferred types can be read or written easily.</span></span>  
  
 <span data-ttu-id="856e7-112">下列程式碼範例會建立**FileStream**周圍現有`MyFile.txt`緩衝區順序`MyFile.txt`。</span><span class="sxs-lookup"><span data-stu-id="856e7-112">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="856e7-113">(請注意， **Filestream**預設緩衝處理。)下一步<xref:System.IO.StreamReader>是用來讀取的字元**FileStream**，傳遞給**StreamReader**做為建構函式引數。</span><span class="sxs-lookup"><span data-stu-id="856e7-113">(Note that **FileStreams** are buffered by default.) Next, a <xref:System.IO.StreamReader> is created to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="856e7-114"><xref:System.IO.StreamReader.ReadLine%2A>讀取直到<xref:System.IO.StreamReader.Peek%2A>尋找沒有更多字元。</span><span class="sxs-lookup"><span data-stu-id="856e7-114"><xref:System.IO.StreamReader.ReadLine%2A> reads until <xref:System.IO.StreamReader.Peek%2A> finds no more characters.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#20](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source2.cpp#20)]
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
 <span data-ttu-id="856e7-115">下列程式碼範例會建立**FileStream**周圍現有`MyFile.txt`緩衝區順序`MyFile.txt`。</span><span class="sxs-lookup"><span data-stu-id="856e7-115">The following code example creates a **FileStream** around the existing `MyFile.txt` in order to buffer `MyFile.txt`.</span></span> <span data-ttu-id="856e7-116">(請注意， **Filestream**預設緩衝處理。)下一步 **BinaryReader**是用來讀取位元組從**FileStream**，傳遞給**BinaryReader**做為建構函式引數。</span><span class="sxs-lookup"><span data-stu-id="856e7-116">(Note that **FileStreams** are buffered by default.) Next, a **BinaryReader** is created to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="856e7-117"><xref:System.IO.BinaryReader.ReadByte%2A>讀取直到<xref:System.IO.BinaryReader.PeekChar%2A>尋找沒有更多的位元組。</span><span class="sxs-lookup"><span data-stu-id="856e7-117"><xref:System.IO.BinaryReader.ReadByte%2A> reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-cpp[System.IO.StreamReader#21](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.StreamReader/CPP/source3.cpp#21)]
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="856e7-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="856e7-118">See Also</span></span>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>  
 <xref:System.IO.FileStream>  
 <xref:System.IO.BinaryReader>  
 <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>  
 <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
