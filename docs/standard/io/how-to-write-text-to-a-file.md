---
title: HOW TO：將文字寫入檔案中
ms.date: 01/04/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- writing text to files
- I/O [.NET Framework], writing text to files
- streams, writing text to files
- data streams, writing text to files
ms.assetid: 060cbe06-2adf-4337-9e7b-961a5c840208
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 93d87dc98284fad6b8159f681f7d99ce460d60d6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54524191"
---
# <a name="how-to-write-text-to-a-file"></a><span data-ttu-id="e5e19-102">HOW TO：將文字寫入檔案中</span><span class="sxs-lookup"><span data-stu-id="e5e19-102">How to: Write text to a file</span></span>
<span data-ttu-id="e5e19-103">本主題說明針對 .NET 應用程式將文字寫入檔案的不同方式。</span><span class="sxs-lookup"><span data-stu-id="e5e19-103">This topic shows different ways to write text to a file for a .NET app.</span></span> 

<span data-ttu-id="e5e19-104">通常會使用下列類別和方法，將文字寫入至檔案：</span><span class="sxs-lookup"><span data-stu-id="e5e19-104">The following classes and methods are typically used to write text to a file:</span></span>  
  
-   <span data-ttu-id="e5e19-105"><xref:System.IO.StreamWriter> 包含同步 (<xref:System.IO.StreamWriter.Write%2A> 和 <xref:System.IO.TextWriter.WriteLine%2A>) 或非同步 (<xref:System.IO.StreamWriter.WriteAsync%2A> 和 <xref:System.IO.StreamWriter.WriteLineAsync%2A>) 寫入檔案的方法。</span><span class="sxs-lookup"><span data-stu-id="e5e19-105"><xref:System.IO.StreamWriter> contains methods to write to a file synchronously (<xref:System.IO.StreamWriter.Write%2A> and <xref:System.IO.TextWriter.WriteLine%2A>) or asynchronously (<xref:System.IO.StreamWriter.WriteAsync%2A> and <xref:System.IO.StreamWriter.WriteLineAsync%2A>).</span></span>  
  
-   <span data-ttu-id="e5e19-106"><xref:System.IO.File> 所提供的靜態方法可將文字寫入檔案 (例如 <xref:System.IO.File.WriteAllLines%2A> 和 <xref:System.IO.File.WriteAllText%2A>)，或將文字附加至檔案 (例如 <xref:System.IO.File.AppendAllLines%2A>、<xref:System.IO.File.AppendAllText%2A> 或 <xref:System.IO.File.AppendText%2A>)。</span><span class="sxs-lookup"><span data-stu-id="e5e19-106"><xref:System.IO.File> provides static methods to write text to a file, such as <xref:System.IO.File.WriteAllLines%2A> and <xref:System.IO.File.WriteAllText%2A>, or to append text to a file, such as <xref:System.IO.File.AppendAllLines%2A>, <xref:System.IO.File.AppendAllText%2A>, and <xref:System.IO.File.AppendText%2A>.</span></span>  
  
- <span data-ttu-id="e5e19-107"><xref:System.IO.Path> 適用於含有檔案或目錄路徑資訊的字串。</span><span class="sxs-lookup"><span data-stu-id="e5e19-107"><xref:System.IO.Path> is for strings that have file or directory path information.</span></span> <span data-ttu-id="e5e19-108">它包含 <xref:System.IO.Path.Combine%2A> 方法 (在 .NET Core 2.1 和更新本中則包含 <xref:System.IO.Path.Join%2A> 和 <xref:System.IO.Path.TryJoin%2A> 方法)，可允許使用字串的串連來建置檔案或目錄路徑。</span><span class="sxs-lookup"><span data-stu-id="e5e19-108">It contains the <xref:System.IO.Path.Combine%2A> method and, in .NET Core 2.1 and later, the <xref:System.IO.Path.Join%2A> and <xref:System.IO.Path.TryJoin%2A> methods, which allow concatenation of strings to build a file or directory path.</span></span>

> [!NOTE]
> <span data-ttu-id="e5e19-109">下列範例只顯示所需的最少數量程式碼。</span><span class="sxs-lookup"><span data-stu-id="e5e19-109">The following examples show only the minimum amount of code needed.</span></span> <span data-ttu-id="e5e19-110">真實世界應用程式通常會提供更強大的錯誤檢查和例外狀況處理。</span><span class="sxs-lookup"><span data-stu-id="e5e19-110">A real-world app usually provides more robust error checking and exception handling.</span></span>  
  
## <a name="example-synchronously-write-text-with-streamwriter"></a><span data-ttu-id="e5e19-111">範例：使用 StreamWriter 同步寫入文字</span><span class="sxs-lookup"><span data-stu-id="e5e19-111">Example: Synchronously write text with StreamWriter</span></span>

<span data-ttu-id="e5e19-112">下列範例示範如何使用 <xref:System.IO.StreamWriter> 類別，以同步方式一次一行將文字寫入新檔案。</span><span class="sxs-lookup"><span data-stu-id="e5e19-112">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously write text to a new file one line at a time.</span></span> <span data-ttu-id="e5e19-113">由於 <xref:System.IO.StreamWriter> 物件是在 `using` 陳述式中宣告及具現化，因此會叫用 <xref:System.IO.StreamWriter.Dispose%2A> 方法，其會自動排清並關閉資料流。</span><span class="sxs-lookup"><span data-stu-id="e5e19-113">Because the <xref:System.IO.StreamWriter> object is declared and instantiated in a `using` statement, the <xref:System.IO.StreamWriter.Dispose%2A> method is invoked, which automatically flushes and closes the stream.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/write.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/write.vb)]  

## <a name="example-synchronously-append-text-with-streamwriter"></a><span data-ttu-id="e5e19-114">範例：使用 StreamWriter 同步附加文字</span><span class="sxs-lookup"><span data-stu-id="e5e19-114">Example: Synchronously append text with StreamWriter</span></span>

<span data-ttu-id="e5e19-115">下列範例示範如何使用 <xref:System.IO.StreamWriter> 類別，以同步方式將文字附加至第一個範例中建立的文字檔。</span><span class="sxs-lookup"><span data-stu-id="e5e19-115">The following example shows how to use the <xref:System.IO.StreamWriter> class to synchronously append text to the text file created in the first example.</span></span>   

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/append.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/append.vb)]  

## <a name="example-asynchronously-write-text-with-streamwriter"></a><span data-ttu-id="e5e19-116">範例：使用 StreamWriter 同步寫入文字</span><span class="sxs-lookup"><span data-stu-id="e5e19-116">Example: Asynchronously write text with StreamWriter</span></span>

<span data-ttu-id="e5e19-117">下列範例示範如何使用 <xref:System.IO.StreamWriter> 類別，以非同步方式將文字寫入至新檔案。</span><span class="sxs-lookup"><span data-stu-id="e5e19-117">The following example shows how to asynchronously write text to a new file using the <xref:System.IO.StreamWriter> class.</span></span> <span data-ttu-id="e5e19-118">若要叫用 <xref:System.IO.StreamWriter.WriteAsync%2A> 方法，必須在 `async` 方法中呼叫此方法。</span><span class="sxs-lookup"><span data-stu-id="e5e19-118">To invoke the <xref:System.IO.StreamWriter.WriteAsync%2A> method, the method call must be within an `async` method.</span></span> <span data-ttu-id="e5e19-119">C# 範例需要 C# 7.1 或更新版本，它會在程式進入點新增對 `async` 修飾詞的支援。</span><span class="sxs-lookup"><span data-stu-id="e5e19-119">The C# example requires C# 7.1 or later, which adds support for the `async` modifier on the program entry point.</span></span> 

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/async.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/async.vb)]  

## <a name="example-write-and-append-text-with-the-file-class"></a><span data-ttu-id="e5e19-120">範例：使用 File 類別寫入和附加文字</span><span class="sxs-lookup"><span data-stu-id="e5e19-120">Example: Write and append text with the File class</span></span>

<span data-ttu-id="e5e19-121">下列範例示範如何使用 <xref:System.IO.File> 類別，將文字寫入至新檔案，並將新的文字行附加至相同的檔案。</span><span class="sxs-lookup"><span data-stu-id="e5e19-121">The following example shows how to write text to a new file and append new lines of text to the same file using the <xref:System.IO.File> class.</span></span> <span data-ttu-id="e5e19-122"><xref:System.IO.File.WriteAllText%2A> 和 <xref:System.IO.File.AppendAllLines%2A> 方法會自動開啟和關閉檔案。</span><span class="sxs-lookup"><span data-stu-id="e5e19-122">The <xref:System.IO.File.WriteAllText%2A> and <xref:System.IO.File.AppendAllLines%2A> methods open and close the file automatically.</span></span> <span data-ttu-id="e5e19-123">如果提供給 <xref:System.IO.File.WriteAllText%2A> 方法的路徑已經存在，則會覆寫該檔案。</span><span class="sxs-lookup"><span data-stu-id="e5e19-123">If the path you provide to the <xref:System.IO.File.WriteAllText%2A> method already exists, the file is overwritten.</span></span>  

[!code-csharp[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.basicio.textfiles/cs/file.cs)] 
[!code-vb[Conceptual.BasicIO.TextFiles#WriteLine](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.basicio.textfiles/vb/file.vb)]  

## <a name="see-also"></a><span data-ttu-id="e5e19-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5e19-124">See also</span></span>

- <xref:System.IO.StreamWriter>
- <xref:System.IO.Path>
- <xref:System.IO.File.CreateText%2A?displayProperty=nameWithType>
- [<span data-ttu-id="e5e19-125">如何：列舉目錄和檔案</span><span class="sxs-lookup"><span data-stu-id="e5e19-125">How to: Enumerate directories and files</span></span>](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)
- [<span data-ttu-id="e5e19-126">如何：讀取和寫入新建立的資料檔案</span><span class="sxs-lookup"><span data-stu-id="e5e19-126">How to: Read and write to a newly-created data file</span></span>](../../../docs/standard/io/how-to-read-and-write-to-a-newly-created-data-file.md)
- [<span data-ttu-id="e5e19-127">如何：開啟並附加至記錄檔</span><span class="sxs-lookup"><span data-stu-id="e5e19-127">How to: Open and append to a log file</span></span>](../../../docs/standard/io/how-to-open-and-append-to-a-log-file.md)
- [<span data-ttu-id="e5e19-128">如何：讀取檔案中的文字</span><span class="sxs-lookup"><span data-stu-id="e5e19-128">How to: Read text from a file</span></span>](../../../docs/standard/io/how-to-read-text-from-a-file.md)
- [<span data-ttu-id="e5e19-129">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="e5e19-129">File and stream I/O</span></span>](../../../docs/standard/io/index.md)