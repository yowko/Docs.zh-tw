---
title: 如何：開啟並附加至記錄檔
ms.date: 03/30/2017
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
ms.openlocfilehash: 35a7d481cf82818054a852f7c2e142f615022fcb
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2018
ms.locfileid: "46695802"
---
# <a name="how-to-open-and-append-to-a-log-file"></a><span data-ttu-id="0c3b6-102">如何：開啟並附加至記錄檔</span><span class="sxs-lookup"><span data-stu-id="0c3b6-102">How to: Open and Append to a Log File</span></span>
<span data-ttu-id="0c3b6-103"><xref:System.IO.StreamWriter> 和 <xref:System.IO.StreamReader> 會在資料流中寫入字元和讀取字元。</span><span class="sxs-lookup"><span data-stu-id="0c3b6-103"><xref:System.IO.StreamWriter> and <xref:System.IO.StreamReader> write characters to and read characters from streams.</span></span> <span data-ttu-id="0c3b6-104">下列程式碼範例會開啟用於輸入的 `log.txt` 檔案，如果該檔案還未存在，則會建立該檔案，並將資訊附加至檔案的結尾。</span><span class="sxs-lookup"><span data-stu-id="0c3b6-104">The following code example opens the `log.txt` file for input, or creates the file if it does not already exist, and appends information to the end of the file.</span></span> <span data-ttu-id="0c3b6-105">接著，檔案的內容會寫入標準輸出以供顯示。</span><span class="sxs-lookup"><span data-stu-id="0c3b6-105">The contents of the file are then written to standard output for display.</span></span> <span data-ttu-id="0c3b6-106">此範例的替代方法是，將資訊儲存成單一字串或字串陣列，而且 <xref:System.IO.File.WriteAllText%2A> 或 <xref:System.IO.File.WriteAllLines%2A> 方法可以用來達成相同的功能。</span><span class="sxs-lookup"><span data-stu-id="0c3b6-106">As an alternative to this example, the information could be stored as a single string or string array, and the <xref:System.IO.File.WriteAllText%2A> or <xref:System.IO.File.WriteAllLines%2A> method could be used to achieve the same functionality.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c3b6-107">Visual Basic 使用者可以選擇使用 <xref:Microsoft.VisualBasic.Logging.Log> 類別或 <xref:Microsoft.VisualBasic.FileIO.FileSystem> 類別所提供的方法和屬性來建立或寫入記錄檔。</span><span class="sxs-lookup"><span data-stu-id="0c3b6-107">Visual Basic users may choose to use the methods and properties provided by the <xref:Microsoft.VisualBasic.Logging.Log> class or <xref:Microsoft.VisualBasic.FileIO.FileSystem> class for creating or writing to log files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c3b6-108">範例</span><span class="sxs-lookup"><span data-stu-id="0c3b6-108">Example</span></span>  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0c3b6-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c3b6-109">See also</span></span>

- <xref:System.IO.StreamWriter>  
- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="0c3b6-110">操作說明：列舉目錄和檔案</span><span class="sxs-lookup"><span data-stu-id="0c3b6-110">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="0c3b6-111">如何：讀取和寫入新建立的資料檔案</span><span class="sxs-lookup"><span data-stu-id="0c3b6-111">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="0c3b6-112">如何：從檔案讀取文字</span><span class="sxs-lookup"><span data-stu-id="0c3b6-112">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="0c3b6-113">如何：將文字寫入檔案</span><span class="sxs-lookup"><span data-stu-id="0c3b6-113">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="0c3b6-114">如何：從字串中讀取字元</span><span class="sxs-lookup"><span data-stu-id="0c3b6-114">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="0c3b6-115">如何：將字元寫入至字串</span><span class="sxs-lookup"><span data-stu-id="0c3b6-115">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="0c3b6-116">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="0c3b6-116">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
