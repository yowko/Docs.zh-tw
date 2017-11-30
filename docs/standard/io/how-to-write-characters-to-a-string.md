---
title: "如何：將字元寫入至字串"
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
- data streams, writing characters to string
- writing characters to strings
- streams, writing characters to strings
- I/O [.NET Framework], writing characters to strings
ms.assetid: 1222cbeb-0760-44bf-9888-914a2a37174b
caps.latest.revision: "17"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 336a7fec5e64cc0c45566631c73928e0c1d40a5a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="8a86a-102">如何：將字元寫入至字串</span><span class="sxs-lookup"><span data-stu-id="8a86a-102">How to: Write Characters to a String</span></span>
<span data-ttu-id="8a86a-103">下列程式碼範例將字元寫入同步和非同步方式從字元陣列轉換為字串。</span><span class="sxs-lookup"><span data-stu-id="8a86a-103">The following code examples write characters synchronously and asynchronously from a character array into a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8a86a-104">範例</span><span class="sxs-lookup"><span data-stu-id="8a86a-104">Example</span></span>  
 <span data-ttu-id="8a86a-105">下列範例將 5 個字元以同步方式從陣列寫入字串。</span><span class="sxs-lookup"><span data-stu-id="8a86a-105">The following example writes 5 characters synchronously from an array to a string.</span></span>  
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example"></a><span data-ttu-id="8a86a-106">範例</span><span class="sxs-lookup"><span data-stu-id="8a86a-106">Example</span></span>  
 <span data-ttu-id="8a86a-107">下一個範例會讀取所有字元以非同步方式從<xref:System.Windows.Controls.TextBox>控制項，然後將它們儲存在陣列中。</span><span class="sxs-lookup"><span data-stu-id="8a86a-107">The next example reads all the characters asynchronously from a <xref:System.Windows.Controls.TextBox> control, and stores them in an array.</span></span> <span data-ttu-id="8a86a-108">然後，它以非同步方式寫入每個字母或空格字元後面接著分行的個別行上<xref:System.Windows.Controls.TextBlock>控制項。</span><span class="sxs-lookup"><span data-stu-id="8a86a-108">It then asynchronously writes each letter or white space character on a separate line followed by a line break to a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="8a86a-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a86a-109">See Also</span></span>  
 <xref:System.IO.StringWriter>  
 <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
 <xref:System.Text.StringBuilder>  
 [<span data-ttu-id="8a86a-110">檔案和資料流 I-O</span><span class="sxs-lookup"><span data-stu-id="8a86a-110">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)  
 [<span data-ttu-id="8a86a-111">非同步檔案 I/O</span><span class="sxs-lookup"><span data-stu-id="8a86a-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [<span data-ttu-id="8a86a-112">操作說明：列舉目錄和檔案</span><span class="sxs-lookup"><span data-stu-id="8a86a-112">How to: Enumerate Directories and Files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
 [<span data-ttu-id="8a86a-113">操作說明：讀取和寫入新建立的資料檔案</span><span class="sxs-lookup"><span data-stu-id="8a86a-113">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="8a86a-114">如何：開啟並附加至記錄檔</span><span class="sxs-lookup"><span data-stu-id="8a86a-114">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="8a86a-115">如何：從檔案讀取文字</span><span class="sxs-lookup"><span data-stu-id="8a86a-115">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="8a86a-116">如何：將文字寫入檔案</span><span class="sxs-lookup"><span data-stu-id="8a86a-116">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="8a86a-117">如何：從字串中讀取字元</span><span class="sxs-lookup"><span data-stu-id="8a86a-117">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
