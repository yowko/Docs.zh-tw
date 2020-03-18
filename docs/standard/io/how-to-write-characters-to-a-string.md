---
title: 如何：將字元寫入字串
ms.date: 01/21/2019
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
ms.openlocfilehash: ecbfa2de2c21ff79df269f74eeddfa0738e7e25c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160272"
---
# <a name="how-to-write-characters-to-a-string"></a><span data-ttu-id="82643-102">如何：將字元寫入字串</span><span class="sxs-lookup"><span data-stu-id="82643-102">How to: Write characters to a string</span></span>
<span data-ttu-id="82643-103">下列程式碼範例會以同步或非同步的方式，將字元從字元陣列寫入字串。</span><span class="sxs-lookup"><span data-stu-id="82643-103">The following code examples write characters synchronously or asynchronously from a character array into a string.</span></span>  
  
## <a name="example-write-characters-synchronously-in-a-console-app"></a><span data-ttu-id="82643-104">示例：在主控台應用中同步寫入字元</span><span class="sxs-lookup"><span data-stu-id="82643-104">Example: Write characters synchronously in a console app</span></span>  
 <span data-ttu-id="82643-105">下列範例會使用 <xref:System.IO.StringWriter>，以同步方式將五個字元寫入 <xref:System.Text.StringBuilder> 物件。</span><span class="sxs-lookup"><span data-stu-id="82643-105">The following example uses a <xref:System.IO.StringWriter> to write five characters synchronously to a <xref:System.Text.StringBuilder> object.</span></span>
  
 [!code-csharp[Conceptual.StringBuilder#9](../../../samples/snippets/csharp/VS_Snippets_CLR/Conceptual.StringBuilder/cs/example2.cs#9)]
 [!code-vb[Conceptual.StringBuilder#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Conceptual.StringBuilder/vb/example2.vb#9)]  
  
## <a name="example-write-characters-asynchronously-in-a-wpf-app"></a><span data-ttu-id="82643-106">示例：在 WPF 應用中非同步寫入字元</span><span class="sxs-lookup"><span data-stu-id="82643-106">Example: Write characters asynchronously in a WPF app</span></span>
 <span data-ttu-id="82643-107">下一個範例是 WPF 應用程式背後的程式碼。</span><span class="sxs-lookup"><span data-stu-id="82643-107">The next example is the code behind a WPF app.</span></span> <span data-ttu-id="82643-108">在載入視窗時，此範例會以非同步方式，從 <xref:System.Windows.Controls.TextBox> 控制項讀取所有字元，然後將其儲存在陣列中。</span><span class="sxs-lookup"><span data-stu-id="82643-108">On window load, the example asynchronously reads all characters from a <xref:System.Windows.Controls.TextBox> control and stores them in an array.</span></span> <span data-ttu-id="82643-109">接著會以非同步方式將每個字母或空格字元寫入 <xref:System.Windows.Controls.TextBlock> 控制項的個別行。</span><span class="sxs-lookup"><span data-stu-id="82643-109">It then asynchronously writes each letter or white-space character to a separate line of a <xref:System.Windows.Controls.TextBlock> control.</span></span>  
  
 [!code-csharp[StreamReaderWriter](../../../samples/snippets/csharp/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.cs)]
 [!code-vb[StreamReaderWriter](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StringReaderWriter/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="82643-110">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82643-110">See also</span></span>

- <xref:System.IO.StringWriter>  
- <xref:System.IO.StringWriter.Write%2A?displayProperty=nameWithType>  
- <xref:System.Text.StringBuilder>  
- [<span data-ttu-id="82643-111">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="82643-111">File and stream I/O</span></span>](../../../docs/standard/io/index.md)  
- [<span data-ttu-id="82643-112">非同步檔 I/O</span><span class="sxs-lookup"><span data-stu-id="82643-112">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [<span data-ttu-id="82643-113">如何：枚舉目錄和檔</span><span class="sxs-lookup"><span data-stu-id="82643-113">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)  
- [<span data-ttu-id="82643-114">如何：讀取和寫入新創建的資料檔案</span><span class="sxs-lookup"><span data-stu-id="82643-114">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="82643-115">如何：打開並追加到日誌檔</span><span class="sxs-lookup"><span data-stu-id="82643-115">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="82643-116">如何：從檔讀取文本</span><span class="sxs-lookup"><span data-stu-id="82643-116">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)  
- [<span data-ttu-id="82643-117">如何：將文本寫入檔</span><span class="sxs-lookup"><span data-stu-id="82643-117">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="82643-118">如何：從字串中讀取字元</span><span class="sxs-lookup"><span data-stu-id="82643-118">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)
