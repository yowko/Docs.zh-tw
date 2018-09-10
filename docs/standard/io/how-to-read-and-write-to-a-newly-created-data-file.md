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
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/09/2018
ms.locfileid: "44187672"
---
# <a name="how-to-read-and-write-to-a-newly-created-data-file"></a><span data-ttu-id="588ad-102">如何：讀取和寫入新建立的資料檔案</span><span class="sxs-lookup"><span data-stu-id="588ad-102">How to: Read and Write to a Newly Created Data File</span></span>
<span data-ttu-id="588ad-103"><xref:System.IO.BinaryWriter> 和 <xref:System.IO.BinaryReader?displayProperty=nameWithType> 類別用於寫入和讀取資料，而不是字元字串。</span><span class="sxs-lookup"><span data-stu-id="588ad-103">The <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader?displayProperty=nameWithType> classes are used for writing and reading data rather than character strings.</span></span> <span data-ttu-id="588ad-104">下列範例示範如何在稱為 `Test.data` 的新空白檔案資料流中寫入資料和讀取資料。</span><span class="sxs-lookup"><span data-stu-id="588ad-104">The following example demonstrates how to write data to, and read data from, a new, empty file stream called `Test.data`.</span></span> <span data-ttu-id="588ad-105">在目前的目錄中建立資料檔案之後，系統會建立相關聯的 <xref:System.IO.BinaryWriter> 和 <xref:System.IO.BinaryReader> 物件，而且會使用 <xref:System.IO.BinaryWriter> 物件，將 0 到 10 的整數寫入 `Test.data`，讓檔案指標留在檔案的結尾。</span><span class="sxs-lookup"><span data-stu-id="588ad-105">After creating the data file in the current directory, the associated <xref:System.IO.BinaryWriter> and <xref:System.IO.BinaryReader> objects are created, and the <xref:System.IO.BinaryWriter> object is used to write the integers 0 through 10 to `Test.data`, which leaves the file pointer at the end of the file.</span></span> <span data-ttu-id="588ad-106">將檔案指標設定為原點之後，<xref:System.IO.BinaryReader> 物件會讀出指定的內容。</span><span class="sxs-lookup"><span data-stu-id="588ad-106">After setting the file pointer back to the origin, the <xref:System.IO.BinaryReader> object reads out the specified content.</span></span>  
  
## <a name="example"></a><span data-ttu-id="588ad-107">範例</span><span class="sxs-lookup"><span data-stu-id="588ad-107">Example</span></span>  
 [!code-cpp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CPP/source6.cpp#7)]
 [!code-csharp[System.IO.BinaryReaderWriter#7](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/CS/source6.cs#7)]
 [!code-vb[System.IO.BinaryReaderWriter#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.IO.BinaryReaderWriter/VB/source6.vb#7)]  
  
## <a name="robust-programming"></a><span data-ttu-id="588ad-108">穩固程式設計</span><span class="sxs-lookup"><span data-stu-id="588ad-108">Robust Programming</span></span>  
 <span data-ttu-id="588ad-109">如果 `Test.data` 已存在於目前的目錄中，則會擲回 <xref:System.IO.IOException> 例外狀況。</span><span class="sxs-lookup"><span data-stu-id="588ad-109">If `Test.data` already exists in the current directory, an <xref:System.IO.IOException> exception is thrown.</span></span> <span data-ttu-id="588ad-110">當您初始化檔案資料流時使用檔案模式選項 <xref:System.IO.FileMode.Create?displayProperty=nameWithType>，就會一律建立新檔案，而不會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="588ad-110">Use the file mode option <xref:System.IO.FileMode.Create?displayProperty=nameWithType> when you initialize the file stream to always create a new file without throwing an  exception.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="588ad-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="588ad-111">See also</span></span>

- <xref:System.IO.BinaryReader>  
- <xref:System.IO.BinaryWriter>  
- <xref:System.IO.FileStream>  
- <xref:System.IO.FileStream.Seek%2A?displayProperty=nameWithType>  
- <xref:System.IO.SeekOrigin>  
- [<span data-ttu-id="588ad-112">操作說明：列舉目錄和檔案</span><span class="sxs-lookup"><span data-stu-id="588ad-112">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="588ad-113">如何：開啟並附加至記錄檔</span><span class="sxs-lookup"><span data-stu-id="588ad-113">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="588ad-114">如何：從檔案讀取文字</span><span class="sxs-lookup"><span data-stu-id="588ad-114">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="588ad-115">如何：將文字寫入檔案</span><span class="sxs-lookup"><span data-stu-id="588ad-115">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="588ad-116">如何：從字串中讀取字元</span><span class="sxs-lookup"><span data-stu-id="588ad-116">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="588ad-117">如何：將字元寫入至字串</span><span class="sxs-lookup"><span data-stu-id="588ad-117">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="588ad-118">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="588ad-118">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
