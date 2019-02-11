---
title: HOW TO：讀取檔案中的文字
ms.date: 01/03/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, reading text from files
- reading text files
- reading data, text files
- data streams, reading text from files
- I/O [.NET Framework], reading text from files
ms.assetid: ed180baa-dfc6-4c69-a725-46e87edafb27
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aa6787e018b540dbf19b6da3473b699096cc4ae3
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/03/2019
ms.locfileid: "55674395"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="19c75-102">HOW TO：讀取檔案中的文字</span><span class="sxs-lookup"><span data-stu-id="19c75-102">How to: Read text from a file</span></span>
<span data-ttu-id="19c75-103">下列範例將示範如何以同步和非同步方式，從使用適用於桌面應用程式的 .NET 之文字檔讀取文字。</span><span class="sxs-lookup"><span data-stu-id="19c75-103">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="19c75-104">在這兩個範例中，當您建立 <xref:System.IO.StreamReader> 類別的執行個體時，會提供檔案的相對路徑或絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="19c75-104">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span> 
  
> [!NOTE]
> <span data-ttu-id="19c75-105">由於 Windows 執行階段提供不同的資料流類型來讀取和寫入檔案，因此這些程式碼不適用於 Universal Windows (UWP) 應用程式的開發工作。</span><span class="sxs-lookup"><span data-stu-id="19c75-105">These code examples do not apply to developing for Universal Windows (UWP) apps, because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="19c75-106">如需示範如何在 UWP 應用程式中從檔案讀取文字的範例，請參閱[快速入門：讀取和寫入檔案](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10))。</span><span class="sxs-lookup"><span data-stu-id="19c75-106">For an example that shows how to read text from a file in a UWP app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="19c75-107">如需示範如何在 .NET Framework 資料流和 Windows 執行階段資料流之間進行轉換的範例，請參閱[如何：在 .NET Framework 資料流與 Windows 執行階段資料流之間轉換](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)。</span><span class="sxs-lookup"><span data-stu-id="19c75-107">For examples that show how to convert between .NET Framework streams and Windows Runtime streams, see [How to: Convert between .NET Framework streams and Windows Runtime streams](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example-synchronous-read-in-a-console-app"></a><span data-ttu-id="19c75-108">範例：主控台應用程式中的同步讀取</span><span class="sxs-lookup"><span data-stu-id="19c75-108">Example: Synchronous read in a console app</span></span>  
<span data-ttu-id="19c75-109">下列範例將示範在主控台應用程式內的同步讀取作業。</span><span class="sxs-lookup"><span data-stu-id="19c75-109">The following example shows a synchronous read operation within a console app.</span></span> <span data-ttu-id="19c75-110">此範例會使用資料流讀取器開啟文字檔、將內容複製到字串，並將字串輸出至主控台。</span><span class="sxs-lookup"><span data-stu-id="19c75-110">This example opens the text file using a stream reader, copies the contents to a string, and outputs the string to the console.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="19c75-111">範例假設名為 *TestFile.txt* 的檔案已與應用程式存在於相同的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="19c75-111">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a><span data-ttu-id="19c75-112">範例：WPF 應用程式中的非同步讀取</span><span class="sxs-lookup"><span data-stu-id="19c75-112">Example: Asynchronous read in a WPF app</span></span> 
 <span data-ttu-id="19c75-113">下列範例將示範 Windows Presentation Foundation (WPF) 應用程式內的非同步讀取作業。</span><span class="sxs-lookup"><span data-stu-id="19c75-113">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) app.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="19c75-114">範例假設名為 *TestFile.txt* 的檔案已與應用程式存在於相同的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="19c75-114">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="19c75-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19c75-115">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="19c75-116">非同步檔案 I/O</span><span class="sxs-lookup"><span data-stu-id="19c75-116">Asynchronous file I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
- [<span data-ttu-id="19c75-117">如何：建立目錄清單</span><span class="sxs-lookup"><span data-stu-id="19c75-117">How to: Create a directory listing</span></span>](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)  
- [<span data-ttu-id="19c75-118">快速入門：讀取和寫入檔案</span><span class="sxs-lookup"><span data-stu-id="19c75-118">Quickstart: Reading and writing files</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [<span data-ttu-id="19c75-119">如何：在 .NET Framework 資料流與 Windows 執行階段資料流之間轉換</span><span class="sxs-lookup"><span data-stu-id="19c75-119">How to: Convert between .NET Framework streams and Windows Runtime streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [<span data-ttu-id="19c75-120">如何：讀取和寫入新建立的資料檔案</span><span class="sxs-lookup"><span data-stu-id="19c75-120">How to: Read and write to a newly created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="19c75-121">如何：開啟並附加至記錄檔</span><span class="sxs-lookup"><span data-stu-id="19c75-121">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="19c75-122">如何：將文字寫入檔案</span><span class="sxs-lookup"><span data-stu-id="19c75-122">How to: Write text to a file</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="19c75-123">如何：讀取字串中的字元</span><span class="sxs-lookup"><span data-stu-id="19c75-123">How to: Read characters from a string</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="19c75-124">如何：將字元寫入字串</span><span class="sxs-lookup"><span data-stu-id="19c75-124">How to: Write characters to a string</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="19c75-125">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="19c75-125">File and stream I/O</span></span>](../../../docs/standard/io/index.md)
