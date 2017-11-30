---
title: "如何：開啟並附加至記錄檔"
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
helpviewer_keywords:
- log files, opening
- streams, opening and appending to log file
- log files, appending to
- I/O [.NET Framework], log files
ms.assetid: 74423362-1721-49cb-aa0a-e04005f72a06
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 60c31339231405a1cbbb98dae37d36ad3c3709c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-open-and-append-to-a-log-file"></a><span data-ttu-id="309c6-102">如何：開啟並附加至記錄檔</span><span class="sxs-lookup"><span data-stu-id="309c6-102">How to: Open and Append to a Log File</span></span>
<span data-ttu-id="309c6-103"><xref:System.IO.StreamWriter>和<xref:System.IO.StreamReader>寫入字元和從資料流讀取字元。</span><span class="sxs-lookup"><span data-stu-id="309c6-103"><xref:System.IO.StreamWriter> and <xref:System.IO.StreamReader> write characters to and read characters from streams.</span></span> <span data-ttu-id="309c6-104">下列程式碼範例會開啟`log.txt`檔案輸入，或如果它不存在，並將資訊附加至檔案結尾建立檔案。</span><span class="sxs-lookup"><span data-stu-id="309c6-104">The following code example opens the `log.txt` file for input, or creates the file if it does not already exist, and appends information to the end of the file.</span></span> <span data-ttu-id="309c6-105">檔案的內容再寫入標準輸出顯示。</span><span class="sxs-lookup"><span data-stu-id="309c6-105">The contents of the file are then written to standard output for display.</span></span> <span data-ttu-id="309c6-106">此範例的替代方法，為的資訊無法儲存成單一字串或字串陣列，而<xref:System.IO.File.WriteAllText%2A>或<xref:System.IO.File.WriteAllLines%2A>方法無法用來達成相同的功能。</span><span class="sxs-lookup"><span data-stu-id="309c6-106">As an alternative to this example, the information could be stored as a single string or string array, and the <xref:System.IO.File.WriteAllText%2A> or <xref:System.IO.File.WriteAllLines%2A> method could be used to achieve the same functionality.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="309c6-107">Visual Basic 使用者可以選擇使用的方法和屬性所提供<xref:Microsoft.VisualBasic.Logging.Log>類別或<xref:Microsoft.VisualBasic.FileIO.FileSystem>類別來建立或寫入至記錄檔。</span><span class="sxs-lookup"><span data-stu-id="309c6-107">Visual Basic users may choose to use the methods and properties provided by the <xref:Microsoft.VisualBasic.Logging.Log> class or <xref:Microsoft.VisualBasic.FileIO.FileSystem> class for creating or writing to log files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="309c6-108">範例</span><span class="sxs-lookup"><span data-stu-id="309c6-108">Example</span></span>  
 [!code-csharp[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source2.cs#2)]
 [!code-vb[Conceptual.BasicIO.TextFiles#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="309c6-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="309c6-109">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.AppendText%2A?displayProperty=nameWithType>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="309c6-110">操作說明：列舉目錄和檔案</span><span class="sxs-lookup"><span data-stu-id="309c6-110">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="309c6-111">如何：讀取和寫入新建立的資料檔案</span><span class="sxs-lookup"><span data-stu-id="309c6-111">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="309c6-112">如何：從檔案讀取文字</span><span class="sxs-lookup"><span data-stu-id="309c6-112">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="309c6-113">如何：將文字寫入檔案</span><span class="sxs-lookup"><span data-stu-id="309c6-113">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="309c6-114">如何：從字串中讀取字元</span><span class="sxs-lookup"><span data-stu-id="309c6-114">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [<span data-ttu-id="309c6-115">如何：將字元寫入至字串</span><span class="sxs-lookup"><span data-stu-id="309c6-115">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [<span data-ttu-id="309c6-116">檔案和資料流 I-O</span><span class="sxs-lookup"><span data-stu-id="309c6-116">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
