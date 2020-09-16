---
title: 如何：從字串讀取字元
description: 瞭解如何從 .NET 中的字串讀取字元。 查看以同步和非同步方式讀取的字元範例。
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
ms.openlocfilehash: fa03d13036e9e245b8ca3f8c3218ae80a2762a12
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90553944"
---
# <a name="how-to-read-characters-from-a-string"></a><span data-ttu-id="b584d-104">如何：從字串讀取字元</span><span class="sxs-lookup"><span data-stu-id="b584d-104">How to: Read characters from a string</span></span>
<span data-ttu-id="b584d-105">下列程式碼範例會示範如何以同步或非同步的方式，從字串讀取字元。</span><span class="sxs-lookup"><span data-stu-id="b584d-105">The following code examples show how to read characters synchronously or asynchronously from a string.</span></span>  
  
## <a name="example-read-characters-synchronously"></a><span data-ttu-id="b584d-106">範例：同步讀取字元</span><span class="sxs-lookup"><span data-stu-id="b584d-106">Example: Read characters synchronously</span></span>
 <span data-ttu-id="b584d-107">此範例會以同步方式，從字串讀取 13 個字元、將其儲存在陣列中，然後顯示它們。</span><span class="sxs-lookup"><span data-stu-id="b584d-107">This example reads 13 characters synchronously from a string, stores them in an array, and displays them.</span></span> <span data-ttu-id="b584d-108">接著讀取字串中剩餘的字元、從陣列的第六個元素開始儲存這些字元，然後顯示陣列的內容。</span><span class="sxs-lookup"><span data-stu-id="b584d-108">The example then reads the rest of the characters in the string, stores them in the array starting at the sixth element, and displays the contents of the array.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.stringreader/cs/source.cs#1)]
 [!code-vb[Conceptual.StringReader#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.stringreader/vb/source.vb#1)]  
  
## <a name="example-read-characters-asynchronously"></a><span data-ttu-id="b584d-109">範例：以非同步方式讀取字元</span><span class="sxs-lookup"><span data-stu-id="b584d-109">Example: Read characters asynchronously</span></span>  
 <span data-ttu-id="b584d-110">下一個範例是 WPF 應用程式背後的程式碼。</span><span class="sxs-lookup"><span data-stu-id="b584d-110">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="b584d-111">在載入視窗時，此範例會以非同步方式，從 <xref:System.Windows.Controls.TextBox> 控制項讀取所有字元，然後將其儲存在陣列中。</span><span class="sxs-lookup"><span data-stu-id="b584d-111">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="b584d-112">接著會以非同步方式將每個字母或空格字元寫入 <xref:System.Windows.Controls.TextBlock> 控制項的個別行。</span><span class="sxs-lookup"><span data-stu-id="b584d-112">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[Conceptual.StringReader#2](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[Conceptual.StringReader#2](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b584d-113">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b584d-113">See also</span></span>

- <xref:System.IO.StringReader>  
- <xref:System.IO.StringReader.Read%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="b584d-114">非同步檔案 I/O</span><span class="sxs-lookup"><span data-stu-id="b584d-114">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- <span data-ttu-id="b584d-115">[如何：建立目錄清單](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="b584d-115">[How to: Create a directory listing](/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="b584d-116">如何：讀取和寫入新建立的資料檔案</span><span class="sxs-lookup"><span data-stu-id="b584d-116">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="b584d-117">如何：開啟並附加至記錄檔</span><span class="sxs-lookup"><span data-stu-id="b584d-117">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="b584d-118">如何：從檔案讀取文字</span><span class="sxs-lookup"><span data-stu-id="b584d-118">How to: Read text from a file</span></span>](how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="b584d-119">如何：將文字寫入檔案</span><span class="sxs-lookup"><span data-stu-id="b584d-119">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="b584d-120">如何：將字元寫入字串</span><span class="sxs-lookup"><span data-stu-id="b584d-120">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="b584d-121">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="b584d-121">File and stream I/O</span></span>](index.md)
