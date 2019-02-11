---
title: HOW TO：開啟並附加至記錄檔
ms.date: 01/21/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 921b13e057929d7d6b283b26014a4c1f195f39c9
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674837"
---
# <a name="how-to-open-and-append-to-a-log-file"></a><span data-ttu-id="0b110-102">HOW TO：開啟並附加至記錄檔</span><span class="sxs-lookup"><span data-stu-id="0b110-102">How to: Open and append to a log file</span></span>
<span data-ttu-id="0b110-103"><xref:System.IO.StreamWriter> 和 <xref:System.IO.StreamReader> 會在資料流中寫入字元和讀取字元。</span><span class="sxs-lookup"><span data-stu-id="0b110-103"><xref:System.IO.StreamWriter> and <xref:System.IO.StreamReader> write characters to and read characters from streams.</span></span> <span data-ttu-id="0b110-104">下列程式碼範例會開啟用於輸入的 *log.txt* 檔案，或者，如果該檔案不存在，則會建立它，並將記錄資訊附加至檔案的結尾。</span><span class="sxs-lookup"><span data-stu-id="0b110-104">The following code example opens the *log.txt* file for input, or creates it if it doesn't exist, and appends log information to the end of the file.</span></span> <span data-ttu-id="0b110-105">此範例接著會將檔案的內容寫入標準輸出以供顯示。</span><span class="sxs-lookup"><span data-stu-id="0b110-105">The example then writes the contents of the file to standard output for display.</span></span> 

<span data-ttu-id="0b110-106">此範例的替代方法是，您可以將資訊儲存成單一字串或字串陣列，並使用 <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> 或 <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> 方法來達成相同的功能。</span><span class="sxs-lookup"><span data-stu-id="0b110-106">As an alternative to this example, you could store the information as a single string or string array, and use the <xref:System.IO.File.WriteAllText%2A?displayProperty=nameWithType> or <xref:System.IO.File.WriteAllLines%2A?displayProperty=nameWithType> method to achieve the same functionality.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0b110-107">Visual Basic 使用者可以選擇使用 <xref:Microsoft.VisualBasic.Logging.Log> 類別或 <xref:Microsoft.VisualBasic.FileIO.FileSystem> 類別所提供的方法和屬性來建立或寫入記錄檔。</span><span class="sxs-lookup"><span data-stu-id="0b110-107">Visual Basic users may choose to use the methods and properties provided by the <xref:Microsoft.VisualBasic.Logging.Log> class or <xref:Microsoft.VisualBasic.FileIO.FileSystem> class for creating or writing to log files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b110-108">範例</span><span class="sxs-lookup"><span data-stu-id="0b110-108">Example</span></span>  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0b110-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b110-109">See also</span></span>

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="0b110-110">如何：列舉目錄和檔案</span><span class="sxs-lookup"><span data-stu-id="0b110-110">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="0b110-111">如何：讀取和寫入新建立的資料檔案</span><span class="sxs-lookup"><span data-stu-id="0b110-111">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="0b110-112">如何：讀取檔案中的文字</span><span class="sxs-lookup"><span data-stu-id="0b110-112">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="0b110-113">如何：將文字寫入檔案</span><span class="sxs-lookup"><span data-stu-id="0b110-113">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="0b110-114">如何：讀取字串中的字元</span><span class="sxs-lookup"><span data-stu-id="0b110-114">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="0b110-115">如何：將字元寫入字串</span><span class="sxs-lookup"><span data-stu-id="0b110-115">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="0b110-116">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="0b110-116">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
