---
title: 作法：讀取字串中的字元
ms.date: 01/21/2019
ms.technology: dotnet-standard
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e890e4172e645e9919ea88ec5835aaed7432c0c6
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/26/2019
ms.locfileid: "56835196"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="37fc6-102">HOW TO：讀取字串中的字元</span><span class="sxs-lookup"><span data-stu-id="37fc6-102">How to: Read characters from a string</span></span>
<span data-ttu-id="37fc6-103">下列程式碼範例會示範如何以同步或非同步的方式，從字串讀取字元。</span><span class="sxs-lookup"><span data-stu-id="37fc6-103">The following code examples show how to read characters synchronously or asynchronously from a string.</span></span>  
  
## <a name="example-read-characters-synchronously"></a><span data-ttu-id="37fc6-104">範例：以同步方式讀取字元</span><span class="sxs-lookup"><span data-stu-id="37fc6-104">Example: Read characters synchronously</span></span> 
 <span data-ttu-id="37fc6-105">此範例會以同步方式，從字串讀取 13 個字元、將其儲存在陣列中，然後顯示它們。</span><span class="sxs-lookup"><span data-stu-id="37fc6-105">This example reads 13 characters synchronously from a string, stores them in an array, and displays them.</span></span> <span data-ttu-id="37fc6-106">接著讀取字串中剩餘的字元、從陣列的第六個元素開始儲存這些字元，然後顯示陣列的內容。</span><span class="sxs-lookup"><span data-stu-id="37fc6-106">The example then reads the rest of the characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a><span data-ttu-id="37fc6-107">範例：以非同步方式讀取字元</span><span class="sxs-lookup"><span data-stu-id="37fc6-107">Example: Read characters asynchronously</span></span>  
 <span data-ttu-id="37fc6-108">下一個範例是 WPF 應用程式背後的程式碼。</span><span class="sxs-lookup"><span data-stu-id="37fc6-108">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="37fc6-109">在載入視窗時，此範例會以非同步方式，從 <xref:System.Windows.Controls.TextBox> 控制項讀取所有字元，然後將其儲存在陣列中。</span><span class="sxs-lookup"><span data-stu-id="37fc6-109">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="37fc6-110">接著會以非同步方式將每個字母或空格字元寫入 <xref:System.Windows.Controls.TextBlock> 控制項的個別行。</span><span class="sxs-lookup"><span data-stu-id="37fc6-110">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="37fc6-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37fc6-111">See also</span></span>

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="37fc6-112">非同步檔案 I/O</span><span class="sxs-lookup"><span data-stu-id="37fc6-112">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- <span data-ttu-id="37fc6-113">[如何：建立目錄清單](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="37fc6-113">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="37fc6-114">如何：讀取和寫入新建立的資料檔案</span><span class="sxs-lookup"><span data-stu-id="37fc6-114">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="37fc6-115">如何：開啟並附加至記錄檔</span><span class="sxs-lookup"><span data-stu-id="37fc6-115">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="37fc6-116">如何：讀取檔案中的文字</span><span class="sxs-lookup"><span data-stu-id="37fc6-116">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="37fc6-117">如何：將文字寫入檔案</span><span class="sxs-lookup"><span data-stu-id="37fc6-117">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="37fc6-118">如何：將字元寫入字串</span><span class="sxs-lookup"><span data-stu-id="37fc6-118">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="37fc6-119">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="37fc6-119">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
