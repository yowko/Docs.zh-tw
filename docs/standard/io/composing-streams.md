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
ms.openlocfilehash: 689cc9537cd7a5fe6a677d42e5790bbcf1b3aefa
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708144"
---
# <a name="compose-streams"></a><span data-ttu-id="84b56-102">撰寫資料流</span><span class="sxs-lookup"><span data-stu-id="84b56-102">Compose streams</span></span>
<span data-ttu-id="84b56-103">*備份存放區*是一種儲存媒體，例如磁碟或記憶體。</span><span class="sxs-lookup"><span data-stu-id="84b56-103">A *backing store* is a storage medium, such as a disk or memory.</span></span> <span data-ttu-id="84b56-104">每個不同的備份存放區都會實作自己的資料流，作為 <xref:System.IO.Stream> 類別的實作。</span><span class="sxs-lookup"><span data-stu-id="84b56-104">Each different backing store implements its own stream as an implementation of the <xref:System.IO.Stream> class.</span></span> 

<span data-ttu-id="84b56-105">每個資料流類型都會在其指定的備份存放區中讀取和寫入位元組。</span><span class="sxs-lookup"><span data-stu-id="84b56-105">Each stream type reads and writes bytes from and to its given backing store.</span></span> <span data-ttu-id="84b56-106">連線到備份存放區的資料流稱為*基底資料流*。</span><span class="sxs-lookup"><span data-stu-id="84b56-106">Streams that connect to backing stores are called *base streams*.</span></span> <span data-ttu-id="84b56-107">基底資料流具有建構函式，其中包含將資料流連線至備份存放區所需的參數。</span><span class="sxs-lookup"><span data-stu-id="84b56-107">Base streams have constructors with the parameters necessary to connect the stream to the backing store.</span></span> <span data-ttu-id="84b56-108">例如，<xref:System.IO.FileStream> 的建構函式會指定路徑參數，此參數可指定處理程序共用檔案的方式。</span><span class="sxs-lookup"><span data-stu-id="84b56-108">For example, <xref:System.IO.FileStream> has constructors that specify a path parameter, which specifies how the file will be shared by processes.</span></span>  

<span data-ttu-id="84b56-109"><xref:System.IO> 類別的設計可提供簡化的資料流撰寫。</span><span class="sxs-lookup"><span data-stu-id="84b56-109">The design of the <xref:System.IO> classes provides simplified stream composition.</span></span> <span data-ttu-id="84b56-110">您可以將基底資料流附加至一個或多個可提供您想要功能的傳遞資料流。</span><span class="sxs-lookup"><span data-stu-id="84b56-110">You can attach base streams to one or more pass-through streams that provide the functionality you want.</span></span> <span data-ttu-id="84b56-111">您可以將讀取器或寫入器附加至鏈結的結尾，以便可以輕易地讀取或寫入慣用的類型。</span><span class="sxs-lookup"><span data-stu-id="84b56-111">You can attach a reader or writer to the end of the chain, so the preferred types can be read or written easily.</span></span>  

<span data-ttu-id="84b56-112">下列程式碼範例會在現有 **MyFile.txt** 的周圍建立 *FileStream* 以緩衝處理 *MyFile.txt*。</span><span class="sxs-lookup"><span data-stu-id="84b56-112">The following code examples create a **FileStream** around the existing *MyFile.txt* in order to buffer *MyFile.txt*.</span></span> <span data-ttu-id="84b56-113">請注意，預設會緩衝處理 **Filestream**。</span><span class="sxs-lookup"><span data-stu-id="84b56-113">Note that **FileStreams** are buffered by default.</span></span>

>[!IMPORTANT]
><span data-ttu-id="84b56-114">範例假設名為 *MyFile.txt* 的檔案已與應用程式存在於相同的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="84b56-114">The examples assume that a file named *MyFile.txt* already exists in the same folder as the app.</span></span>  

## <a name="example-use-streamreader"></a><span data-ttu-id="84b56-115">範例：使用 StreamReader</span><span class="sxs-lookup"><span data-stu-id="84b56-115">Example: Use StreamReader</span></span>
<span data-ttu-id="84b56-116">下列範例會建立一個 <xref:System.IO.StreamReader> 來讀取 **FileStream** 中的字元，之後再傳遞至 **StreamReader** 作為其建構函式引數。</span><span class="sxs-lookup"><span data-stu-id="84b56-116">The following example creates a <xref:System.IO.StreamReader> to read characters from the **FileStream**, which is passed to the **StreamReader** as its constructor argument.</span></span> <span data-ttu-id="84b56-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> 接著會一直讀取，直到 <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> 找不到其他字元。</span><span class="sxs-lookup"><span data-stu-id="84b56-117"><xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType> then reads until <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType> finds no more characters.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#20](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source2.cs#20)]
 [!code-vb[System.IO.StreamReader#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source2.vb#20)]  
  
## <a name="example-use-binaryreader"></a><span data-ttu-id="84b56-118">範例：使用 BinaryReader</span><span class="sxs-lookup"><span data-stu-id="84b56-118">Example: Use BinaryReader</span></span>
<span data-ttu-id="84b56-119">下列範例會建立一個 <xref:System.IO.BinaryReader> 來讀取 **FileStream** 中的位元組，之後再傳遞至 **BinaryReader** 作為其建構函式引數。</span><span class="sxs-lookup"><span data-stu-id="84b56-119">The following example creates a <xref:System.IO.BinaryReader> to read bytes from the **FileStream**, which is passed to the **BinaryReader** as its constructor argument.</span></span> <span data-ttu-id="84b56-120"><xref:System.IO.BinaryReader.ReadByte%2A> 接著會一直讀取，直到 <xref:System.IO.BinaryReader.PeekChar%2A> 找不到其他位元組。</span><span class="sxs-lookup"><span data-stu-id="84b56-120"><xref:System.IO.BinaryReader.ReadByte%2A> then reads until <xref:System.IO.BinaryReader.PeekChar%2A> finds no more bytes.</span></span>  
  
 [!code-csharp[System.IO.StreamReader#21](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.StreamReader/CS/source3.cs#21)]
 [!code-vb[System.IO.StreamReader#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.StreamReader/VB/source3.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="84b56-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="84b56-121">See also</span></span>

- <xref:System.IO.StreamReader>
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>
- <xref:System.IO.StreamReader.Peek%2A?displayProperty=nameWithType>
- <xref:System.IO.FileStream>
- <xref:System.IO.BinaryReader>
- <xref:System.IO.BinaryReader.ReadByte%2A?displayProperty=nameWithType>
- <xref:System.IO.BinaryReader.PeekChar%2A?displayProperty=nameWithType>
