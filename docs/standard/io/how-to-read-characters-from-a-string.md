---
title: "如何：從字串中讀取字元"
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
- reading characters from strings
- data streams, reading characters from string
- I/O [.NET Framework], reading characters from strings
- reading data, strings
- streams, reading characters from string
ms.assetid: 27ea5e52-6db8-42d8-980a-50bcfc7fd270
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9116ec63bfc1d12daf7627186a52bd29d5918485
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="ea237-102">如何：從字串中讀取字元</span><span class="sxs-lookup"><span data-stu-id="ea237-102">How to: Read Characters from a String</span></span>
<span data-ttu-id="ea237-103">下列程式碼範例示範如何從字串讀取字元同步和非同步方式。</span><span class="sxs-lookup"><span data-stu-id="ea237-103">The following code examples show how to read characters synchronously and asynchronously from a string.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea237-104">範例</span><span class="sxs-lookup"><span data-stu-id="ea237-104">Example</span></span>  
 <span data-ttu-id="ea237-105">這個範例會讀取 13 個字元的字串，以同步方式將它們儲存在陣列中，並顯示這些字元。</span><span class="sxs-lookup"><span data-stu-id="ea237-105">This example reads 13 characters synchronously from a string, stores them in an array, and displays those characters.</span></span> <span data-ttu-id="ea237-106">然後讀取字串中剩餘的字元，將它們儲存在陣列的第六個項目，開始，並顯示為陣列的內容。</span><span class="sxs-lookup"><span data-stu-id="ea237-106">It then reads the remaining characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-cpp[Conceptual.StringReader#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.stringreader/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="ea237-107">範例</span><span class="sxs-lookup"><span data-stu-id="ea237-107">Example</span></span>  
 <span data-ttu-id="ea237-108">下一個範例會讀取所有字元以非同步方式從<xref:System.Windows.Controls.TextBox>控制項，然後將它們儲存在陣列中。</span><span class="sxs-lookup"><span data-stu-id="ea237-108">The next example reads all the characters asynchronously from a <xref:System.Windows.Controls.TextBox> control, and stores them in an array.</span></span> <span data-ttu-id="ea237-109">然後，它以非同步方式寫入每個字母或空格字元後面接著分行的個別行上<xref:System.Windows.Controls.TextBlock>控制項。</span><span class="sxs-lookup"><span data-stu-id="ea237-109">It then asynchronously writes each letter or white space character on a separate line followed by a line break to a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source2.cs#2)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source2.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="ea237-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea237-110">See Also</span></span>  
 <xref:System.IO.StringReader>  
 <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="ea237-111">非同步檔案 I/O</span><span class="sxs-lookup"><span data-stu-id="ea237-111">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [<span data-ttu-id="ea237-112">NIB： 如何： 建立目錄清單</span><span class="sxs-lookup"><span data-stu-id="ea237-112">NIB: How to: Create a Directory Listing</span></span>](http://msdn.microsoft.com/en-us/4d2772b1-b991-4532-a8a6-6ef733277e69)  
 [<span data-ttu-id="ea237-113">如何：讀取和寫入新建立的資料檔案</span><span class="sxs-lookup"><span data-stu-id="ea237-113">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="ea237-114">如何：開啟並附加至記錄檔</span><span class="sxs-lookup"><span data-stu-id="ea237-114">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="ea237-115">如何：從檔案讀取文字</span><span class="sxs-lookup"><span data-stu-id="ea237-115">How to: Read Text from a File</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
 [<span data-ttu-id="ea237-116">如何：將文字寫入檔案</span><span class="sxs-lookup"><span data-stu-id="ea237-116">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="ea237-117">如何：將字元寫入至字串</span><span class="sxs-lookup"><span data-stu-id="ea237-117">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [<span data-ttu-id="ea237-118">檔案和資料流 I-O</span><span class="sxs-lookup"><span data-stu-id="ea237-118">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
