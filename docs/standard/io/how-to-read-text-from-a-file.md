---
title: 如何：從檔案讀取文字
description: 在本文中，請參閱如何在 .NET 中使用桌面應用程式的 StreamReader 類別，以同步或非同步方式從文字檔讀取文字的範例。
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
ms.openlocfilehash: cbdeab3e907b34b6658eef7228fa6567ae198b08
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/05/2020
ms.locfileid: "84447052"
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="812ec-103">如何：從檔案讀取文字</span><span class="sxs-lookup"><span data-stu-id="812ec-103">How to: Read text from a file</span></span>
<span data-ttu-id="812ec-104">下列範例將示範如何以同步和非同步方式，從使用適用於桌面應用程式的 .NET 之文字檔讀取文字。</span><span class="sxs-lookup"><span data-stu-id="812ec-104">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="812ec-105">在這兩個範例中，當您建立 <xref:System.IO.StreamReader> 類別的執行個體時，會提供檔案的相對路徑或絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="812ec-105">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span>
  
> [!NOTE]
> <span data-ttu-id="812ec-106">由於 Windows 執行階段提供不同的資料流類型來讀取和寫入檔案，因此這些程式碼不適用於 Universal Windows (UWP) 應用程式的開發工作。</span><span class="sxs-lookup"><span data-stu-id="812ec-106">These code examples do not apply to developing for Universal Windows (UWP) apps, because the Windows Runtime provides different stream types for reading and writing to files.</span></span> <span data-ttu-id="812ec-107">如需說明如何從 UWP 應用程式中的檔案讀取文字的範例，請參閱[快速入門：讀取和寫入](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10))檔案。</span><span class="sxs-lookup"><span data-stu-id="812ec-107">For an example that shows how to read text from a file in a UWP app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span></span> <span data-ttu-id="812ec-108">如需示範如何在 .NET Framework 資料流程和 Windows 執行階段資料流程之間進行轉換的範例，請參閱[如何：在 .NET Framework 資料流程和 Windows 執行階段資料流程之間進行轉換](how-to-convert-between-dotnet-streams-and-winrt-streams.md)。</span><span class="sxs-lookup"><span data-stu-id="812ec-108">For examples that show how to convert between .NET Framework streams and Windows Runtime streams, see [How to: Convert between .NET Framework streams and Windows Runtime streams](how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example-synchronous-read-in-a-console-app"></a><span data-ttu-id="812ec-109">範例：主控台應用程式中的同步讀取</span><span class="sxs-lookup"><span data-stu-id="812ec-109">Example: Synchronous read in a console app</span></span>  
<span data-ttu-id="812ec-110">下列範例將示範在主控台應用程式內的同步讀取作業。</span><span class="sxs-lookup"><span data-stu-id="812ec-110">The following example shows a synchronous read operation within a console app.</span></span> <span data-ttu-id="812ec-111">此範例會使用資料流讀取器開啟文字檔、將內容複製到字串，並將字串輸出至主控台。</span><span class="sxs-lookup"><span data-stu-id="812ec-111">This example opens the text file using a stream reader, copies the contents to a string, and outputs the string to the console.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="812ec-112">範例假設名為 *TestFile.txt* 的檔案已與應用程式存在於相同的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="812ec-112">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example-asynchronous-read-in-a-wpf-app"></a><span data-ttu-id="812ec-113">範例： WPF 應用程式中的非同步讀取</span><span class="sxs-lookup"><span data-stu-id="812ec-113">Example: Asynchronous read in a WPF app</span></span>
 <span data-ttu-id="812ec-114">下列範例將示範 Windows Presentation Foundation (WPF) 應用程式內的非同步讀取作業。</span><span class="sxs-lookup"><span data-stu-id="812ec-114">The following example shows an asynchronous read operation in a Windows Presentation Foundation (WPF) app.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="812ec-115">範例假設名為 *TestFile.txt* 的檔案已與應用程式存在於相同的資料夾中。</span><span class="sxs-lookup"><span data-stu-id="812ec-115">The example assumes that a file named *TestFile.txt* already exists in the same folder as the app.</span></span>  

 [!code-csharp[TextFiles](../../../samples/snippets/csharp/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.cs)]
 [!code-vb[TextFiles](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextFiles/MainWindow.xaml.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="812ec-116">請參閱</span><span class="sxs-lookup"><span data-stu-id="812ec-116">See also</span></span>

- <xref:System.IO.StreamReader>  
- <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
- <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
- [<span data-ttu-id="812ec-117">非同步檔案 I/O</span><span class="sxs-lookup"><span data-stu-id="812ec-117">Asynchronous file I/O</span></span>](asynchronous-file-i-o.md)  
- <span data-ttu-id="812ec-118">[How to：建立目錄清單](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="812ec-118">[How to: Create a directory listing](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/5cf8zcfh(v=vs.100))</span></span>  
- [<span data-ttu-id="812ec-119">快速入門：讀取和寫入檔案</span><span class="sxs-lookup"><span data-stu-id="812ec-119">Quickstart: Reading and writing files</span></span>](https://docs.microsoft.com/previous-versions/windows/apps/hh758325%28v=win.10%29)  
- [<span data-ttu-id="812ec-120">如何：在 .NET Framework 資料流程和 Windows 執行階段資料流程之間轉換</span><span class="sxs-lookup"><span data-stu-id="812ec-120">How to: Convert between .NET Framework streams and Windows Runtime streams</span></span>](how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
- [<span data-ttu-id="812ec-121">如何：讀取和寫入新建立的資料檔案</span><span class="sxs-lookup"><span data-stu-id="812ec-121">How to: Read and write to a newly created data file</span></span>](how-to-read-and-write-to-a-newly-created-data-file.md)  
- [<span data-ttu-id="812ec-122">如何：開啟並附加至記錄檔</span><span class="sxs-lookup"><span data-stu-id="812ec-122">How to: Open and append to a log file</span></span>](how-to-open-and-append-to-a-log-file.md)  
- [<span data-ttu-id="812ec-123">如何：將文字寫入檔案</span><span class="sxs-lookup"><span data-stu-id="812ec-123">How to: Write text to a file</span></span>](how-to-write-text-to-a-file.md)  
- [<span data-ttu-id="812ec-124">如何：從字串讀取字元</span><span class="sxs-lookup"><span data-stu-id="812ec-124">How to: Read characters from a string</span></span>](how-to-read-characters-from-a-string.md)  
- [<span data-ttu-id="812ec-125">如何：將字元寫入字串</span><span class="sxs-lookup"><span data-stu-id="812ec-125">How to: Write characters to a string</span></span>](how-to-write-characters-to-a-string.md)  
- [<span data-ttu-id="812ec-126">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="812ec-126">File and stream I/O</span></span>](index.md)
