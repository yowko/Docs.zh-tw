---
title: HOW TO：將字元寫入字串
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 125c8ba03c4d1006535dd1e10cbd162b32fede4f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54740979"
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="1bdab-102">HOW TO：將字元寫入字串</span><span class="sxs-lookup"><span data-stu-id="1bdab-102">How to: Write Characters to a String</span></span>
<span data-ttu-id="1bdab-103">下列程式碼範例會以同步和非同步的方式，將字元從字元陣列寫入字串。</span><span class="sxs-lookup"><span data-stu-id="1bdab-103">The following code examples write characters synchronously and asynchronously from a character array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bdab-104">範例</span><span class="sxs-lookup"><span data-stu-id="1bdab-104">Example</span></span>  
 <span data-ttu-id="1bdab-105">下列範例會以同步方式，將 5 個字元從陣列寫入字串。</span><span class="sxs-lookup"><span data-stu-id="1bdab-105">The following example writes 5 characters synchronously from an array to a string.</span></span>  
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="1bdab-106">範例</span><span class="sxs-lookup"><span data-stu-id="1bdab-106">Example</span></span>  
 <span data-ttu-id="1bdab-107">下一個範例會以非同步方式，從 <xref:System.Windows.Controls.TextBox> 控制項讀取所有字元，然後將其儲存在陣列中。</span><span class="sxs-lookup"><span data-stu-id="1bdab-107">The next example reads all the characters asynchronously from a <xref:System.Windows.Controls.TextBox> control, and stores them in an array.</span></span> <span data-ttu-id="1bdab-108">接著，它會以非同步方式，在個別的行上，將每個字母或空格字元後面接著分行符號寫入 <xref:System.Windows.Controls.TextBlock> 控制項。</span><span class="sxs-lookup"><span data-stu-id="1bdab-108">It then asynchronously writes each letter or white space character on a separate line followed by a line break to a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="1bdab-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1bdab-109">See also</span></span>

- <xref:System.IO.StringWriter>
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>
- <xref:System.Text.StringBuilder>
- [<span data-ttu-id="1bdab-110">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="1bdab-110">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
- [<span data-ttu-id="1bdab-111">Asynchronous File I/O</span><span class="sxs-lookup"><span data-stu-id="1bdab-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)
- [<span data-ttu-id="1bdab-112">如何：列舉目錄和檔案</span><span class="sxs-lookup"><span data-stu-id="1bdab-112">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="1bdab-113">如何：讀取和寫入新建立的資料檔案</span><span class="sxs-lookup"><span data-stu-id="1bdab-113">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="1bdab-114">如何：開啟並附加至記錄檔</span><span class="sxs-lookup"><span data-stu-id="1bdab-114">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="1bdab-115">如何：讀取檔案中的文字</span><span class="sxs-lookup"><span data-stu-id="1bdab-115">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [<span data-ttu-id="1bdab-116">如何：將文字寫入檔案</span><span class="sxs-lookup"><span data-stu-id="1bdab-116">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)
- [<span data-ttu-id="1bdab-117">如何：讀取字串中的字元</span><span class="sxs-lookup"><span data-stu-id="1bdab-117">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
