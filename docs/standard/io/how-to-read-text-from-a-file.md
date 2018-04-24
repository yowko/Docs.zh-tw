---
title: 如何：從檔案讀取文字
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
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
caps.latest.revision: 23
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e1058879d4af8aac12baf24d10a0c22894351e6f
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-read-text-from-a-file"></a><span data-ttu-id="dfd02-102">如何：從檔案讀取文字</span><span class="sxs-lookup"><span data-stu-id="dfd02-102">How to: Read Text from a File</span></span>
<span data-ttu-id="dfd02-103">下列範例將示範如何以同步和非同步方式，從使用適用於桌面應用程式的 .NET 之文字檔讀取文字。</span><span class="sxs-lookup"><span data-stu-id="dfd02-103">The following examples show how to read text synchronously and asynchronously from a text file using .NET for desktop apps.</span></span> <span data-ttu-id="dfd02-104">在這兩個範例中，當您建立 <xref:System.IO.StreamReader> 類別的執行個體時，會提供檔案的相對路徑或絕對路徑。</span><span class="sxs-lookup"><span data-stu-id="dfd02-104">In both examples, when you create the instance of the <xref:System.IO.StreamReader> class, you provide the relative or absolute path to the file.</span></span> <span data-ttu-id="dfd02-105">下列範例會假設名為 TestFile.txt 的檔案與應用程式位於相同資料夾中。</span><span class="sxs-lookup"><span data-stu-id="dfd02-105">The following examples assume that the file named TestFile.txt is in the same folder as the application.</span></span>  
  
 <span data-ttu-id="dfd02-106">由於 Windows 執行階段提供不同的資料流類型來讀取和寫入檔案，因此這些程式碼不適用於 Windows 市集應用程式的開發工作。</span><span class="sxs-lookup"><span data-stu-id="dfd02-106">These code examples do not apply developing for Windows Store Apps because the Windows Runtime provides different streams types reading and writing to files.</span></span> <span data-ttu-id="dfd02-107">如需示範如何在 Windows 市集應用程式的內容中從檔案讀取文字的範例，請參閱[快速入門：讀取和寫入檔案](http://msdn.microsoft.com/library/windows/apps/hh758325.aspx)。</span><span class="sxs-lookup"><span data-stu-id="dfd02-107">For an example that shows how to read text from a file within the context of a Windows Store app, see [Quickstart: Reading and writing files](http://msdn.microsoft.com/library/windows/apps/hh758325.aspx).</span></span> <span data-ttu-id="dfd02-108">如需如何在 .NET Framework 資料流和 Windows 執行階段資料流之間轉換的範例，請參閱[操作說明：在 .NET Framework 資料流與 Windows 執行階段資料流之間轉換](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)。</span><span class="sxs-lookup"><span data-stu-id="dfd02-108">For examples that show how to convert between .NET Framework streams and Windows runtime streams see [How to: Convert Between .NET Framework Streams and Windows Runtime Streams](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="dfd02-109">範例</span><span class="sxs-lookup"><span data-stu-id="dfd02-109">Example</span></span>  
 <span data-ttu-id="dfd02-110">第一個範例將示範在主控台應用程式內的同步讀取作業。</span><span class="sxs-lookup"><span data-stu-id="dfd02-110">The first example shows a synchronous read operation within a console application.</span></span> <span data-ttu-id="dfd02-111">在這個範例中，會使用資料流讀取器開啟文字檔案，內容會複製到字串，而字串會輸出到主控台。</span><span class="sxs-lookup"><span data-stu-id="dfd02-111">In this example, the text file is opened using a stream reader, the contents are copied to a string and string is output to the console.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source3.cs#3)]
 [!code-vb[Conceptual.BasicIO.TextFiles#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source3.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="dfd02-112">範例</span><span class="sxs-lookup"><span data-stu-id="dfd02-112">Example</span></span>  
 <span data-ttu-id="dfd02-113">第二個範例將示範 Windows Presentation Foundation (WPF) 應用程式內的非同步讀取作業。</span><span class="sxs-lookup"><span data-stu-id="dfd02-113">The second example shows an asynchronous read operation within a Windows Presentation Foundation (WPF) application.</span></span>  
  
 [!code-csharp[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/source6.cs#6)]
 [!code-vb[Conceptual.BasicIO.TextFiles#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/source6.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="dfd02-114">請參閱</span><span class="sxs-lookup"><span data-stu-id="dfd02-114">See Also</span></span>  
 <xref:System.IO.StreamReader>  
 <xref:System.IO.File.OpenText%2A?displayProperty=nameWithType>  
 <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="dfd02-115">非同步檔案 I/O</span><span class="sxs-lookup"><span data-stu-id="dfd02-115">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
 [<span data-ttu-id="dfd02-116">NIB：操作說明：建立目錄清單</span><span class="sxs-lookup"><span data-stu-id="dfd02-116">NIB: How to: Create a Directory Listing</span></span>](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)  
 [<span data-ttu-id="dfd02-117">快速入門：讀取和寫入檔案</span><span class="sxs-lookup"><span data-stu-id="dfd02-117">Quickstart: Reading and writing files</span></span>](http://msdn.microsoft.com/library/windows/apps/hh758325.aspx)  
 [<span data-ttu-id="dfd02-118">操作說明：在 .NET Framework 資料流與 Windows 執行階段資料流之間轉換</span><span class="sxs-lookup"><span data-stu-id="dfd02-118">How to: Convert Between .NET Framework Streams and Windows Runtime Streams</span></span>](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)  
 [<span data-ttu-id="dfd02-119">如何：讀取和寫入新建立的資料檔案</span><span class="sxs-lookup"><span data-stu-id="dfd02-119">How to: Read and Write to a Newly Created Data File</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)  
 [<span data-ttu-id="dfd02-120">操作說明：開啟並附加至記錄檔</span><span class="sxs-lookup"><span data-stu-id="dfd02-120">How to: Open and Append to a Log File</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)  
 [<span data-ttu-id="dfd02-121">如何：將文字寫入檔案</span><span class="sxs-lookup"><span data-stu-id="dfd02-121">How to: Write Text to a File</span></span>](../../../docs/standard/io/how-to-write-text-to-a-file.md)  
 [<span data-ttu-id="dfd02-122">如何：從字串中讀取字元</span><span class="sxs-lookup"><span data-stu-id="dfd02-122">How to: Read Characters from a String</span></span>](../../../docs/standard/io/how-to-read-characters-from-a-string.md)  
 [<span data-ttu-id="dfd02-123">如何：將字元寫入至字串</span><span class="sxs-lookup"><span data-stu-id="dfd02-123">How to: Write Characters to a String</span></span>](../../../docs/standard/io/how-to-write-characters-to-a-string.md)  
 [<span data-ttu-id="dfd02-124">檔案和資料流 I-O</span><span class="sxs-lookup"><span data-stu-id="dfd02-124">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
