---
title: 檔案和資料流 I/O
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- IO namespace
- files, I/O
- System.IO namespace
- I/O [.NET Framework]
- streams, I/O
- data streams, I/O
ms.assetid: 4f4a33a9-66b7-4cd7-a285-4ad3e4276cd2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a0ffef95c8f9a187d5dac6902462d9747023384d
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/08/2018
ms.locfileid: "44214884"
---
# <a name="file-and-stream-io"></a><span data-ttu-id="6bd69-102">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="6bd69-102">File and Stream I/O</span></span>
<span data-ttu-id="6bd69-103">檔案和資料流 I/O (輸入/輸出) 是指對儲存媒體來回傳輸資料。</span><span class="sxs-lookup"><span data-stu-id="6bd69-103">File and stream I/O (input/output) refers to the transfer of data either to or from a storage medium.</span></span> <span data-ttu-id="6bd69-104">在 .NET Framework 中，`System.IO` 命名空間包含能夠以同步和非同步方式在資料流和檔案上進行讀取和寫入的類型。</span><span class="sxs-lookup"><span data-stu-id="6bd69-104">In the .NET Framework, the `System.IO` namespaces contain types that enable reading and writing, both synchronously and asynchronously, on data streams and files.</span></span> <span data-ttu-id="6bd69-105">這些命名空間還包含對檔案進行壓縮和解壓縮的類型，以及透過管道和序列埠進行通訊的類型。</span><span class="sxs-lookup"><span data-stu-id="6bd69-105">These namespaces also contain types that perform compression and decompression on files, and types that enable communication through pipes and serial ports.</span></span>  
  
 <span data-ttu-id="6bd69-106">檔案是具有永續性存放裝置的已排序具名位元組集合。</span><span class="sxs-lookup"><span data-stu-id="6bd69-106">A file is an ordered and named collection of bytes that has persistent storage.</span></span> <span data-ttu-id="6bd69-107">當您使用檔案時，也會處理目錄路徑、磁碟存放裝置，以及檔案和目錄名稱。</span><span class="sxs-lookup"><span data-stu-id="6bd69-107">When you work with files, you work with directory paths, disk storage, and file and directory names.</span></span> <span data-ttu-id="6bd69-108">相反地，資料流是可以用來讀取和寫入備份存放區的位元組序列，這類備份存放區可以是數種儲存媒體的其中一種 (例如磁碟或記憶體)。</span><span class="sxs-lookup"><span data-stu-id="6bd69-108">In contrast, a stream is a sequence of bytes that you can use to read from and write to a backing store, which can be one of several storage mediums (for example, disks or memory).</span></span> <span data-ttu-id="6bd69-109">就像除了磁碟以外，還有多種備份存放區一樣，資料流的種類除了檔案資料流之外，還有其他數種，例如網路、記憶體和管道資料流。</span><span class="sxs-lookup"><span data-stu-id="6bd69-109">Just as there are several backing stores other than disks, there are several kinds of streams other than file streams, such as network, memory, and pipe streams.</span></span>  
  
## <a name="files-and-directories"></a><span data-ttu-id="6bd69-110">檔案和目錄</span><span class="sxs-lookup"><span data-stu-id="6bd69-110">Files and Directories</span></span>  
 <span data-ttu-id="6bd69-111">您可以使用 <xref:System.IO?displayProperty=nameWithType> 命名空間中的類型與檔案和目錄互動。</span><span class="sxs-lookup"><span data-stu-id="6bd69-111">You can use the types in the <xref:System.IO?displayProperty=nameWithType> namespace to interact with files and directories.</span></span> <span data-ttu-id="6bd69-112">例如，您可以取得及設定檔案和目錄的屬性，並且根據搜尋條件擷取檔案和目錄集合。</span><span class="sxs-lookup"><span data-stu-id="6bd69-112">For example, you can get and set properties for files and directories, and retrieve collections of files and directories based on search criteria.</span></span>  

<span data-ttu-id="6bd69-113">如需 Windows 系統的路徑命名慣例及檔案路徑表達方式，包括 .NET Core 1.1 及更新版本和 .NET Framework 4.6.2 及更新版本中支援的 DOS 裝置語法，請參閱 [Windows 系統上的檔案路徑格式](file-path-formats.md)。</span><span class="sxs-lookup"><span data-stu-id="6bd69-113">For path naming conventions and the ways to express a file path for Windows systems, including with the DOS device syntax supported in .NET Core 1.1 and later and the .NET Framework 4.6.2 and later, see [File path formats on Windows systems](file-path-formats.md).</span></span> 
  
 <span data-ttu-id="6bd69-114">以下是常用的檔案和目錄類別：</span><span class="sxs-lookup"><span data-stu-id="6bd69-114">Here are some commonly used file and directory classes:</span></span>  
  
-   <span data-ttu-id="6bd69-115"><xref:System.IO.File> - 提供建立、複製、刪除、移動和開啟檔案的靜態方法，並協助建立 <xref:System.IO.FileStream> 物件。</span><span class="sxs-lookup"><span data-stu-id="6bd69-115"><xref:System.IO.File> - provides static methods for creating, copying, deleting, moving, and opening files, and helps create a <xref:System.IO.FileStream> object.</span></span>  
  
-   <span data-ttu-id="6bd69-116"><xref:System.IO.FileInfo> - 提供建立、複製、刪除、移動和開啟檔案的執行個體方法，並協助建立 <xref:System.IO.FileStream> 物件。</span><span class="sxs-lookup"><span data-stu-id="6bd69-116"><xref:System.IO.FileInfo> - provides instance methods for creating, copying, deleting, moving, and opening files, and helps create a <xref:System.IO.FileStream> object.</span></span>  
  
-   <span data-ttu-id="6bd69-117"><xref:System.IO.Directory> - 提供建立、移動和列舉目錄和子目錄的靜態方法。</span><span class="sxs-lookup"><span data-stu-id="6bd69-117"><xref:System.IO.Directory> - provides static methods for creating, moving, and enumerating through directories and subdirectories.</span></span>  
  
-   <span data-ttu-id="6bd69-118"><xref:System.IO.DirectoryInfo> - 提供建立、移動和列舉目錄和子目錄的執行個體方法。</span><span class="sxs-lookup"><span data-stu-id="6bd69-118"><xref:System.IO.DirectoryInfo> - provides instance methods for creating, moving, and enumerating through directories and subdirectories.</span></span>  
  
-   <span data-ttu-id="6bd69-119"><xref:System.IO.Path> - 提供以跨平台方式處理目錄字串的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="6bd69-119"><xref:System.IO.Path> - provides methods and properties for processing directory strings in a cross-platform manner.</span></span>  
  
 <span data-ttu-id="6bd69-120">除了使用這些類別之外，Visual Basic 使用者還可以使用 <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=nameWithType> 類別針對檔案 I/O 提供的方法。</span><span class="sxs-lookup"><span data-stu-id="6bd69-120">In addition to using these classes, Visual Basic users can use the methods and properties provided by the <xref:Microsoft.VisualBasic.FileIO.FileSystem?displayProperty=nameWithType> class for file I/O.</span></span>  
  
 <span data-ttu-id="6bd69-121">請參閱[如何：複製目錄](../../../docs/standard/io/how-to-copy-directories.md)、[如何：建立目錄清單](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69)，以及[如何：列舉目錄和檔案](../../../docs/standard/io/how-to-enumerate-directories-and-files.md)。</span><span class="sxs-lookup"><span data-stu-id="6bd69-121">See [How to: Copy Directories](../../../docs/standard/io/how-to-copy-directories.md), [How to: Create a Directory Listing](https://msdn.microsoft.com/library/4d2772b1-b991-4532-a8a6-6ef733277e69), and [How to: Enumerate Directories and Files](../../../docs/standard/io/how-to-enumerate-directories-and-files.md).</span></span>  
  
## <a name="streams"></a><span data-ttu-id="6bd69-122">資料流</span><span class="sxs-lookup"><span data-stu-id="6bd69-122">Streams</span></span>  
 <span data-ttu-id="6bd69-123">抽象基底類別 <xref:System.IO.Stream> 支援讀取和寫入位元組。</span><span class="sxs-lookup"><span data-stu-id="6bd69-123">The abstract base class <xref:System.IO.Stream> supports reading and writing bytes.</span></span> <span data-ttu-id="6bd69-124">代表繼承自 <xref:System.IO.Stream> 類別之資料流的所有類別。</span><span class="sxs-lookup"><span data-stu-id="6bd69-124">All classes that represent streams inherit from the <xref:System.IO.Stream> class.</span></span> <span data-ttu-id="6bd69-125"><xref:System.IO.Stream> 類別和它的衍生類別提供了資料來源和儲存機制的一般觀點，並且將程式設計人員與作業系統和基礎裝置的特有詳細資料加以隔離。</span><span class="sxs-lookup"><span data-stu-id="6bd69-125">The <xref:System.IO.Stream> class and its derived classes provide a common view of data sources and repositories, and isolate the programmer from the specific details of the operating system and underlying devices.</span></span>  
  
 <span data-ttu-id="6bd69-126">資料流包含三項基本作業：</span><span class="sxs-lookup"><span data-stu-id="6bd69-126">Streams involve three fundamental operations:</span></span>  
  
-   <span data-ttu-id="6bd69-127">讀取 - 從資料流將資料傳送至資料結構，例如位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="6bd69-127">Reading - transferring data from a stream into a data structure, such as an array of bytes.</span></span>  
  
-   <span data-ttu-id="6bd69-128">寫入 - 從資料來源將資料傳送至資料流。</span><span class="sxs-lookup"><span data-stu-id="6bd69-128">Writing - transferring data to a stream from a data source.</span></span>  
  
-   <span data-ttu-id="6bd69-129">搜尋 - 查詢和修改資料流內的目前位置。</span><span class="sxs-lookup"><span data-stu-id="6bd69-129">Seeking - querying and modifying the current position within a stream.</span></span>  
  
 <span data-ttu-id="6bd69-130">依據基礎資料來源或儲存機制而定，資料流可能只支援其中部分功能。</span><span class="sxs-lookup"><span data-stu-id="6bd69-130">Depending on the underlying data source or repository, a stream might support only some of these capabilities.</span></span> <span data-ttu-id="6bd69-131">例如，<xref:System.IO.Pipes.PipeStream> 類別不支援搜尋。</span><span class="sxs-lookup"><span data-stu-id="6bd69-131">For example, the <xref:System.IO.Pipes.PipeStream> class does not support seeking.</span></span> <span data-ttu-id="6bd69-132">資料流的 <xref:System.IO.Stream.CanRead%2A>、<xref:System.IO.Stream.CanWrite%2A> 和 <xref:System.IO.Stream.CanSeek%2A> 屬性會指定資料流支援的作業。</span><span class="sxs-lookup"><span data-stu-id="6bd69-132">The <xref:System.IO.Stream.CanRead%2A>, <xref:System.IO.Stream.CanWrite%2A>, and <xref:System.IO.Stream.CanSeek%2A> properties of a stream specify the operations that the stream supports.</span></span>  
  
 <span data-ttu-id="6bd69-133">以下是部分常用的資料流類別：</span><span class="sxs-lookup"><span data-stu-id="6bd69-133">Here are some commonly used stream classes:</span></span>  
  
-   <span data-ttu-id="6bd69-134"><xref:System.IO.FileStream> – 用於讀取和寫入檔案。</span><span class="sxs-lookup"><span data-stu-id="6bd69-134"><xref:System.IO.FileStream> – for reading and writing to a file.</span></span>  
  
-   <span data-ttu-id="6bd69-135"><xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> – 用於讀取和寫入位於隔離儲存區中的檔案。</span><span class="sxs-lookup"><span data-stu-id="6bd69-135"><xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> – for reading and writing to a file in isolated storage.</span></span>  
  
-   <span data-ttu-id="6bd69-136"><xref:System.IO.MemoryStream> – 用於讀取和寫入做為備份存放區的記憶體。</span><span class="sxs-lookup"><span data-stu-id="6bd69-136"><xref:System.IO.MemoryStream> – for reading and writing to memory as the backing store.</span></span>  
  
-   <span data-ttu-id="6bd69-137"><xref:System.IO.BufferedStream> – 用於改善讀取和寫入作業的效能。</span><span class="sxs-lookup"><span data-stu-id="6bd69-137"><xref:System.IO.BufferedStream> – for improving performance of read and write operations.</span></span>  
  
-   <span data-ttu-id="6bd69-138"><xref:System.Net.Sockets.NetworkStream> – 用於透過網路通訊端讀取和寫入。</span><span class="sxs-lookup"><span data-stu-id="6bd69-138"><xref:System.Net.Sockets.NetworkStream> – for reading and writing over network sockets.</span></span>  
  
-   <span data-ttu-id="6bd69-139"><xref:System.IO.Pipes.PipeStream> – 用於透過匿名和具名管道讀取和寫入。</span><span class="sxs-lookup"><span data-stu-id="6bd69-139"><xref:System.IO.Pipes.PipeStream> – for reading and writing over anonymous and named pipes.</span></span>  
  
-   <span data-ttu-id="6bd69-140"><xref:System.Security.Cryptography.CryptoStream> – 用於將資料流連結至密碼編譯的轉換作業。</span><span class="sxs-lookup"><span data-stu-id="6bd69-140"><xref:System.Security.Cryptography.CryptoStream> – for linking data streams to cryptographic transformations.</span></span>  
  
 <span data-ttu-id="6bd69-141">以非同步方式處理資料流的範例，請參閱[非同步檔案 I/O](../../../docs/standard/io/asynchronous-file-i-o.md)。</span><span class="sxs-lookup"><span data-stu-id="6bd69-141">For an example of working with streams asynchronously, see [Asynchronous File I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="readers-and-writers"></a><span data-ttu-id="6bd69-142">讀取器和寫入器</span><span class="sxs-lookup"><span data-stu-id="6bd69-142">Readers and Writers</span></span>  
 <span data-ttu-id="6bd69-143"><xref:System.IO?displayProperty=nameWithType> 命名空間提供從資料流讀取編碼字元以及將編碼字元寫入資料流的類型。</span><span class="sxs-lookup"><span data-stu-id="6bd69-143">The <xref:System.IO?displayProperty=nameWithType> namespace also provides types for reading encoded characters from streams and writing them to streams.</span></span> <span data-ttu-id="6bd69-144">通常資料流是針對位元組輸入和輸出所設計。</span><span class="sxs-lookup"><span data-stu-id="6bd69-144">Typically, streams are designed for byte input and output.</span></span> <span data-ttu-id="6bd69-145">讀取器和寫入器類型會處理編碼字元與位元組之間的轉換，讓資料流能夠完成作業。</span><span class="sxs-lookup"><span data-stu-id="6bd69-145">The reader and writer types handle the conversion of the encoded characters to and from bytes so the stream can complete the operation.</span></span> <span data-ttu-id="6bd69-146">每個讀取器和寫入器類別都會與資料流相關聯，可透過類別的 `BaseStream` 屬性擷取。</span><span class="sxs-lookup"><span data-stu-id="6bd69-146">Each reader and writer class is associated with a stream, which can be retrieved through the class's `BaseStream` property.</span></span>  
  
 <span data-ttu-id="6bd69-147">以下是常用的讀取器和寫入器類別：</span><span class="sxs-lookup"><span data-stu-id="6bd69-147">Here are some commonly used reader and writer classes:</span></span>  
  
-   <span data-ttu-id="6bd69-148"><xref:System.IO.BinaryReader> 和 <xref:System.IO.BinaryWriter> – 用於將基本資料類型當做二進位值讀取和寫入。</span><span class="sxs-lookup"><span data-stu-id="6bd69-148"><xref:System.IO.BinaryReader> and <xref:System.IO.BinaryWriter> – for reading and writing primitive data types as binary values.</span></span>  
  
-   <span data-ttu-id="6bd69-149"><xref:System.IO.StreamReader> 和 <xref:System.IO.StreamWriter> – 使用編碼值在字元與位元組之間進行轉換的方式讀取和寫入字元。</span><span class="sxs-lookup"><span data-stu-id="6bd69-149"><xref:System.IO.StreamReader> and <xref:System.IO.StreamWriter> – for reading and writing characters by using an encoding value to convert the characters to and from bytes.</span></span>  
  
-   <span data-ttu-id="6bd69-150"><xref:System.IO.StringReader> 和 <xref:System.IO.StringWriter> – 從字串讀取字元以及將字元寫入字串。</span><span class="sxs-lookup"><span data-stu-id="6bd69-150"><xref:System.IO.StringReader> and <xref:System.IO.StringWriter> – for reading and writing characters to and from strings.</span></span>  
  
-   <span data-ttu-id="6bd69-151"><xref:System.IO.TextReader> 和 <xref:System.IO.TextWriter> – 做為其他讀取和寫入二進位資料以外的字元與字串之讀取器和寫入器的抽象基底類別。</span><span class="sxs-lookup"><span data-stu-id="6bd69-151"><xref:System.IO.TextReader> and <xref:System.IO.TextWriter> – serve as the abstract base classes for other readers and writers that read and write characters and strings, but not binary data.</span></span>  
  
 <span data-ttu-id="6bd69-152">請參閱[如何：從檔案讀取文字](../../../docs/standard/io/how-to-read-text-from-a-file.md)、[如何：將文字寫入檔案](../../../docs/standard/io/how-to-write-text-to-a-file.md)、[如何：從字串讀取字元](../../../docs/standard/io/how-to-read-characters-from-a-string.md)，以及[如何：將字元寫入字串](../../../docs/standard/io/how-to-write-characters-to-a-string.md)。</span><span class="sxs-lookup"><span data-stu-id="6bd69-152">See [How to: Read Text from a File](../../../docs/standard/io/how-to-read-text-from-a-file.md), [How to: Write Text to a File](../../../docs/standard/io/how-to-write-text-to-a-file.md), [How to: Read Characters from a String](../../../docs/standard/io/how-to-read-characters-from-a-string.md), and [How to: Write Characters to a String](../../../docs/standard/io/how-to-write-characters-to-a-string.md).</span></span>  
  
## <a name="asynchronous-io-operations"></a><span data-ttu-id="6bd69-153">非同步 I/O 作業</span><span class="sxs-lookup"><span data-stu-id="6bd69-153">Asynchronous I/O Operations</span></span>  
 <span data-ttu-id="6bd69-154">讀取或寫入大量資料可能會耗用大量資源。</span><span class="sxs-lookup"><span data-stu-id="6bd69-154">Reading or writing a large amount of data can be resource-intensive.</span></span> <span data-ttu-id="6bd69-155">如果您的應用程式需要保持對使用者的回應能力，您應該以非同步方式執行這些工作。</span><span class="sxs-lookup"><span data-stu-id="6bd69-155">You should perform these tasks asynchronously if your application needs to remain responsive to the user.</span></span> <span data-ttu-id="6bd69-156">進行同步 I/O 作業時，UI 執行緒會遭到封鎖，直至耗用資源的作業完成為止。</span><span class="sxs-lookup"><span data-stu-id="6bd69-156">With synchronous I/O operations, the UI thread is blocked until the resource-intensive operation has completed.</span></span>  <span data-ttu-id="6bd69-157">開發 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式時請使用非同步 I/O 作業，避免造成應用程式停止運作的印象。</span><span class="sxs-lookup"><span data-stu-id="6bd69-157">Use asynchronous I/O operations when developing [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps to prevent creating the impression that your app has stopped working.</span></span>  
  
 <span data-ttu-id="6bd69-158">非同步成員的名稱中包含 `Async`，例如 <xref:System.IO.Stream.CopyToAsync%2A>、<xref:System.IO.Stream.FlushAsync%2A>、<xref:System.IO.Stream.ReadAsync%2A> 和 <xref:System.IO.Stream.WriteAsync%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="6bd69-158">The asynchronous members contain `Async` in their names, such as the <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>,  <xref:System.IO.Stream.ReadAsync%2A>, and <xref:System.IO.Stream.WriteAsync%2A> methods.</span></span> <span data-ttu-id="6bd69-159">這些方法可搭配 `async` 和 `await` 關鍵字使用。</span><span class="sxs-lookup"><span data-stu-id="6bd69-159">You use these methods with the `async` and `await` keywords.</span></span>  
  
 <span data-ttu-id="6bd69-160">如需詳細資訊，請參閱[非同步檔案 I/O](../../../docs/standard/io/asynchronous-file-i-o.md)。</span><span class="sxs-lookup"><span data-stu-id="6bd69-160">For more information, see [Asynchronous File I/O](../../../docs/standard/io/asynchronous-file-i-o.md).</span></span>  
  
## <a name="compression"></a><span data-ttu-id="6bd69-161">壓縮</span><span class="sxs-lookup"><span data-stu-id="6bd69-161">Compression</span></span>  
 <span data-ttu-id="6bd69-162">壓縮是指縮減檔案大小以便儲存的程序。</span><span class="sxs-lookup"><span data-stu-id="6bd69-162">Compression refers to the process of reducing the size of a file for storage.</span></span> <span data-ttu-id="6bd69-163">解壓縮則是指擷取壓縮檔的內容使其成為可使用格式的程序。</span><span class="sxs-lookup"><span data-stu-id="6bd69-163">Decompression is the process of extracting the contents of a compressed file so they are in a usable format.</span></span> <span data-ttu-id="6bd69-164"><xref:System.IO.Compression?displayProperty=nameWithType> 命名空間包含壓縮及解壓縮檔案和資料流的類型。</span><span class="sxs-lookup"><span data-stu-id="6bd69-164">The <xref:System.IO.Compression?displayProperty=nameWithType> namespace contains types for compressing and decompressing files and streams.</span></span>  
  
 <span data-ttu-id="6bd69-165">以下是壓縮和解壓縮檔案和資料流時經常使用的類別：</span><span class="sxs-lookup"><span data-stu-id="6bd69-165">The following classes are frequently used when compressing and decompressing files and streams:</span></span>  
  
-   <span data-ttu-id="6bd69-166"><xref:System.IO.Compression.ZipArchive> – 用於建立和擷取 zip 封存中的項目。</span><span class="sxs-lookup"><span data-stu-id="6bd69-166"><xref:System.IO.Compression.ZipArchive> – for creating and retrieving entries in the zip archive.</span></span>  
  
-   <span data-ttu-id="6bd69-167"><xref:System.IO.Compression.ZipArchiveEntry> – 用於表示壓縮檔。</span><span class="sxs-lookup"><span data-stu-id="6bd69-167"><xref:System.IO.Compression.ZipArchiveEntry> – for representing a compressed file.</span></span>  
  
-   <span data-ttu-id="6bd69-168"><xref:System.IO.Compression.ZipFile> – 用於建立、擷取和開啟壓縮的封裝。</span><span class="sxs-lookup"><span data-stu-id="6bd69-168"><xref:System.IO.Compression.ZipFile> – for creating,  extracting, and opening a compressed package.</span></span>  
  
-   <span data-ttu-id="6bd69-169"><xref:System.IO.Compression.ZipFileExtensions> – 用於建立和擷取壓縮封裝中的項目。</span><span class="sxs-lookup"><span data-stu-id="6bd69-169"><xref:System.IO.Compression.ZipFileExtensions> – for creating and extracting entries in a compressed package.</span></span>  
  
-   <span data-ttu-id="6bd69-170"><xref:System.IO.Compression.DeflateStream> – 使用 Deflate 演算法壓縮及解壓縮資料流。</span><span class="sxs-lookup"><span data-stu-id="6bd69-170"><xref:System.IO.Compression.DeflateStream> – for compressing and decompressing streams using the Deflate algorithm.</span></span>  
  
-   <span data-ttu-id="6bd69-171"><xref:System.IO.Compression.GZipStream> – 以 gzip 資料格式壓縮和解壓縮資料流。</span><span class="sxs-lookup"><span data-stu-id="6bd69-171"><xref:System.IO.Compression.GZipStream> – for compressing and decompressing streams in gzip data format.</span></span>  
  
 <span data-ttu-id="6bd69-172">請參閱[如何：壓縮與解壓縮檔案](../../../docs/standard/io/how-to-compress-and-extract-files.md)。</span><span class="sxs-lookup"><span data-stu-id="6bd69-172">See [How to: Compress and Extract Files](../../../docs/standard/io/how-to-compress-and-extract-files.md).</span></span>  
  
## <a name="isolated-storage"></a><span data-ttu-id="6bd69-173">隔離儲存區</span><span class="sxs-lookup"><span data-stu-id="6bd69-173">Isolated Storage</span></span>  
 <span data-ttu-id="6bd69-174">隔離儲存區 (Isolated Storage) 為資料儲存機制，藉著定義標準化方式，將程式碼與儲存的資料產生關聯，以提供隔離和安全。</span><span class="sxs-lookup"><span data-stu-id="6bd69-174">Isolated storage is a data storage mechanism that provides isolation and safety by defining standardized ways of associating code with saved data.</span></span> <span data-ttu-id="6bd69-175">儲存區提供依使用者、組件和 (選擇性) 網域隔離的虛擬檔案系統。</span><span class="sxs-lookup"><span data-stu-id="6bd69-175">The storage provides a virtual file system that is isolated by user, assembly, and (optionally) domain.</span></span> <span data-ttu-id="6bd69-176">隔離儲存區在應用程式未具備存取使用者檔案的權限時特別實用。</span><span class="sxs-lookup"><span data-stu-id="6bd69-176">Isolated storage is particularly useful when your application does not have permission to access user files.</span></span> <span data-ttu-id="6bd69-177">您可以藉由電腦的安全性原則所控制的方式儲存應用程式的設定或檔案。</span><span class="sxs-lookup"><span data-stu-id="6bd69-177">You can save settings or files for your application in a manner that is controlled by the computer's security policy.</span></span>  
  
 <span data-ttu-id="6bd69-178">隔離儲存區不適用於 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式，請改用 [Windows.Storage](/uwp/api/Windows.Storage) 命名空間中的應用程式資料類別。</span><span class="sxs-lookup"><span data-stu-id="6bd69-178">Isolated storage is not available for [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps; instead, use application data classes in the [Windows.Storage](/uwp/api/Windows.Storage) namespace.</span></span> <span data-ttu-id="6bd69-179">如需詳細資訊，請參閱 Windows 開發人員中心的[應用程式資料](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10))。</span><span class="sxs-lookup"><span data-stu-id="6bd69-179">For more information, see [Application data](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) in the Windows Dev Center.</span></span>  
  
 <span data-ttu-id="6bd69-180">以下是實作隔離儲存區時經常使用的類別：</span><span class="sxs-lookup"><span data-stu-id="6bd69-180">The following classes are frequently used when implementing isolated storage:</span></span>  
  
-   <span data-ttu-id="6bd69-181"><xref:System.IO.IsolatedStorage.IsolatedStorage> – 提供隔離儲存區實作所使用的基底類別。</span><span class="sxs-lookup"><span data-stu-id="6bd69-181"><xref:System.IO.IsolatedStorage.IsolatedStorage> – provides the base class for isolated storage implementations.</span></span>  
  
-   <span data-ttu-id="6bd69-182"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> – 提供包含檔案和目錄的隔離存放區域。</span><span class="sxs-lookup"><span data-stu-id="6bd69-182"><xref:System.IO.IsolatedStorage.IsolatedStorageFile> – provides an isolated storage area that contains files and directories.</span></span>  
  
-   <span data-ttu-id="6bd69-183"><xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> - 公開隔離儲存區內的檔案。</span><span class="sxs-lookup"><span data-stu-id="6bd69-183"><xref:System.IO.IsolatedStorage.IsolatedStorageFileStream> - exposes a file within isolated storage.</span></span>  
  
 <span data-ttu-id="6bd69-184">請參閱[隔離儲存區](../../../docs/standard/io/isolated-storage.md)。</span><span class="sxs-lookup"><span data-stu-id="6bd69-184">See [Isolated Storage](../../../docs/standard/io/isolated-storage.md).</span></span>  
  
## <a name="io-operations-in-windows-store-apps"></a><span data-ttu-id="6bd69-185">Windows 市集應用程式中的 I/O 作業</span><span class="sxs-lookup"><span data-stu-id="6bd69-185">I/O Operations in Windows Store apps</span></span>  
 <span data-ttu-id="6bd69-186">[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] 包含許多用於讀取和寫入資料流的類型，不過這個集合並未包含所有 .NET Framework I/O 類型。</span><span class="sxs-lookup"><span data-stu-id="6bd69-186">The [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)] contains many of the types for reading from and writing to streams; however, this set does not include all the .NET Framework I/O types.</span></span>  
  
 <span data-ttu-id="6bd69-187">以下是在 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]應用程式中使用 I/O 作業時要注意的一些重要差異：</span><span class="sxs-lookup"><span data-stu-id="6bd69-187">Some important differences to note when using I/O operations in [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps:</span></span>  
  
-   <span data-ttu-id="6bd69-188"><xref:System.IO.File> 中未包含與檔案作業特別相關的類型，例如 <xref:System.IO.FileInfo>、<xref:System.IO.Directory>、<xref:System.IO.DirectoryInfo> 和 [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6bd69-188">Types specifically related to file operations, such as <xref:System.IO.File>, <xref:System.IO.FileInfo>, <xref:System.IO.Directory> and <xref:System.IO.DirectoryInfo>, are not included in the [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)].</span></span> <span data-ttu-id="6bd69-189">因此，請改用 [!INCLUDE[wrt](../../../includes/wrt-md.md)] 的 [Windows.Storage](https://msdn.microsoft.com/library/windows/apps/windows.storage.aspx) 命名空間中的類型，例如 [StorageFile](https://msdn.microsoft.com/library/windows/apps/windows.storage.storagefile.aspx) 和 [StorageFolder](https://msdn.microsoft.com/library/windows/apps/windows.storage.storagefolder.aspx)。</span><span class="sxs-lookup"><span data-stu-id="6bd69-189">Instead, use the types in the [Windows.Storage](https://msdn.microsoft.com/library/windows/apps/windows.storage.aspx) namespace of the [!INCLUDE[wrt](../../../includes/wrt-md.md)], such as [StorageFile](https://msdn.microsoft.com/library/windows/apps/windows.storage.storagefile.aspx) and [StorageFolder](https://msdn.microsoft.com/library/windows/apps/windows.storage.storagefolder.aspx).</span></span>  
  
-   <span data-ttu-id="6bd69-190">無法使用隔離儲存區，請改用[應用程式資料](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10))。</span><span class="sxs-lookup"><span data-stu-id="6bd69-190">Isolated storage is not available; instead, use [application data](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)).</span></span>  
  
-   <span data-ttu-id="6bd69-191">使用非同步方法，例如 <xref:System.IO.Stream.ReadAsync%2A> 和 <xref:System.IO.Stream.WriteAsync%2A>，防止封鎖 UI 執行緒。</span><span class="sxs-lookup"><span data-stu-id="6bd69-191">Use asynchronous methods, such as <xref:System.IO.Stream.ReadAsync%2A> and <xref:System.IO.Stream.WriteAsync%2A>, to prevent blocking the UI thread.</span></span>  
  
-   <span data-ttu-id="6bd69-192">無法使用路徑壓縮類型 <xref:System.IO.Compression.ZipFile> 和 <xref:System.IO.Compression.ZipFileExtensions>。</span><span class="sxs-lookup"><span data-stu-id="6bd69-192">The path-based compression types <xref:System.IO.Compression.ZipFile> and <xref:System.IO.Compression.ZipFileExtensions> are not available.</span></span> <span data-ttu-id="6bd69-193">因此，請改用 [Windows.Storage.Compression](https://msdn.microsoft.com/library/windows/apps/windows.storage.compression.aspx) 命名空間中的類型。</span><span class="sxs-lookup"><span data-stu-id="6bd69-193">Instead, use the types in the [Windows.Storage.Compression](https://msdn.microsoft.com/library/windows/apps/windows.storage.compression.aspx) namespace.</span></span>  
  
 <span data-ttu-id="6bd69-194">如有需要，您可以在 .NET Framework 資料流和 Windows 執行階段資料流之間進行轉換。</span><span class="sxs-lookup"><span data-stu-id="6bd69-194">You can convert between .NET Framework streams and Windows Runtime streams, if necessary.</span></span> <span data-ttu-id="6bd69-195">如需詳細資訊，請參閱[如何：在 .NET Framework 資料流與 Windows 執行階段資料流之間轉換](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md)或 [System.IO.WindowsRuntimeStreamExtensions (英文)](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx)。</span><span class="sxs-lookup"><span data-stu-id="6bd69-195">For more information, see [How to: Convert Between .NET Framework Streams and Windows Runtime Streams](../../../docs/standard/io/how-to-convert-between-dotnet-streams-and-winrt-streams.md) or [System.IO.WindowsRuntimeStreamExtensions](https://msdn.microsoft.com/library/system.io.windowsruntimestreamextensions.aspx).</span></span> <!--zz TODO: <xref:System.IO.WindowsRuntimeStreamExtensions>--> 
  
 <span data-ttu-id="6bd69-196">如需有關 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式中 I/O 作業的詳細資訊，請參閱[快速入門：讀取和寫入檔案](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10))。</span><span class="sxs-lookup"><span data-stu-id="6bd69-196">For more information about I/O operations in a [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] app, see [Quickstart: Reading and writing files](https://docs.microsoft.com/previous-versions/windows/apps/hh758325(v=win.10)).</span></span>  
  
## <a name="io-and-security"></a><span data-ttu-id="6bd69-197">I/O 和安全性</span><span class="sxs-lookup"><span data-stu-id="6bd69-197">I/O and Security</span></span>  
 <span data-ttu-id="6bd69-198">當您使用 <xref:System.IO?displayProperty=nameWithType> 命名空間中的類別時，必須遵循作業系統安全性需求，例如存取控制清單 (ACL)，以控制對檔案和目錄的存取。</span><span class="sxs-lookup"><span data-stu-id="6bd69-198">When you use the classes in the <xref:System.IO?displayProperty=nameWithType> namespace, you must follow operating system security requirements such as access control lists (ACLs) to control access to files and directories.</span></span> <span data-ttu-id="6bd69-199">任何 <xref:System.Security.Permissions.FileIOPermission> 需求上都會附加這個需求。</span><span class="sxs-lookup"><span data-stu-id="6bd69-199">This requirement is in addition to any <xref:System.Security.Permissions.FileIOPermission> requirements.</span></span> <span data-ttu-id="6bd69-200">您可以用程式設計的方式管理 ACL。</span><span class="sxs-lookup"><span data-stu-id="6bd69-200">You can manage ACLs programmatically.</span></span> <span data-ttu-id="6bd69-201">如需詳細資訊，請參閱[如何：新增或移除存取控制清單項目](../../../docs/standard/io/how-to-add-or-remove-access-control-list-entries.md)。</span><span class="sxs-lookup"><span data-stu-id="6bd69-201">For more information, see [How to: Add or Remove Access Control List Entries](../../../docs/standard/io/how-to-add-or-remove-access-control-list-entries.md).</span></span>  
  
 <span data-ttu-id="6bd69-202">預設安全性原則可避免網際網路或內部網路應用程式存取使用者電腦上的檔案。</span><span class="sxs-lookup"><span data-stu-id="6bd69-202">Default security policies prevent Internet or intranet applications from accessing files on the user’s computer.</span></span> <span data-ttu-id="6bd69-203">因此，撰寫將透過網際網路或內部網路下載的程式碼時，請不要使用需要實體檔案路徑的 I/O 類別。</span><span class="sxs-lookup"><span data-stu-id="6bd69-203">Therefore, do not use the I/O classes that require a path to a physical file when writing code that will be downloaded over the Internet or intranet.</span></span> <span data-ttu-id="6bd69-204">對於傳統 .NET Framework 應用程式請改用[隔離儲存區](../../../docs/standard/io/isolated-storage.md)，對於 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] 應用程式則改用[應用程式資料](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10))。</span><span class="sxs-lookup"><span data-stu-id="6bd69-204">Instead, use [isolated storage](../../../docs/standard/io/isolated-storage.md) for traditional .NET Framework applications, or use [application data](https://docs.microsoft.com/previous-versions/windows/apps/hh464917(v=win.10)) for [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] apps.</span></span>  
  
 <span data-ttu-id="6bd69-205">只會對已建構的資料流進行安全性檢查。</span><span class="sxs-lookup"><span data-stu-id="6bd69-205">A security check is performed only when the stream is constructed.</span></span> <span data-ttu-id="6bd69-206">因此，請不要開啟資料流，然後將它傳遞至較不受信任的程式碼或應用程式定義域。</span><span class="sxs-lookup"><span data-stu-id="6bd69-206">Therefore, do not open a stream and then pass it to less-trusted code or application domains.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="6bd69-207">相關主題</span><span class="sxs-lookup"><span data-stu-id="6bd69-207">Related Topics</span></span>  
  
-   [<span data-ttu-id="6bd69-208">一般 I/O 工作</span><span class="sxs-lookup"><span data-stu-id="6bd69-208">Common I/O Tasks</span></span>](../../../docs/standard/io/common-i-o-tasks.md)  
  
 <span data-ttu-id="6bd69-209">提供與檔案、目錄和資料流相關聯的 I/O 工作清單，並且連結至每一項工作的相關內容和範例。</span><span class="sxs-lookup"><span data-stu-id="6bd69-209">Provides a list of I/O tasks associated with files, directories, and streams, and links to relevant content and examples for each task.</span></span>  
  
-   [<span data-ttu-id="6bd69-210">非同步檔案 I/O</span><span class="sxs-lookup"><span data-stu-id="6bd69-210">Asynchronous File I/O</span></span>](../../../docs/standard/io/asynchronous-file-i-o.md)  
  
 <span data-ttu-id="6bd69-211">描述非同步 I/O 的效能利益和基本作業。</span><span class="sxs-lookup"><span data-stu-id="6bd69-211">Describes the performance advantages and basic operation of asynchronous I/O.</span></span>  
  
-   [<span data-ttu-id="6bd69-212">隔離儲存區</span><span class="sxs-lookup"><span data-stu-id="6bd69-212">Isolated Storage</span></span>](../../../docs/standard/io/isolated-storage.md)  
  
 <span data-ttu-id="6bd69-213">描述資料儲存機制，此機制藉著定義標準化方式將程式碼與儲存的資料產生關聯，以提供隔離和安全。</span><span class="sxs-lookup"><span data-stu-id="6bd69-213">Describes a data storage mechanism that provides isolation and safety by defining standardized ways of associating code with saved data.</span></span>  
  
-   [<span data-ttu-id="6bd69-214">管道</span><span class="sxs-lookup"><span data-stu-id="6bd69-214">Pipes</span></span>](../../../docs/standard/io/pipe-operations.md)  
  
 <span data-ttu-id="6bd69-215">描述 .NET Framework 中的非同步與具名管道作業。</span><span class="sxs-lookup"><span data-stu-id="6bd69-215">Describes anonymous and named pipe operations in the .NET Framework.</span></span>  
  
-   [<span data-ttu-id="6bd69-216">記憶體對應檔案</span><span class="sxs-lookup"><span data-stu-id="6bd69-216">Memory-Mapped Files</span></span>](../../../docs/standard/io/memory-mapped-files.md)  
  
 <span data-ttu-id="6bd69-217">描述記憶體對應檔案，這些檔案包含磁碟檔案在虛擬記憶體中的內容。</span><span class="sxs-lookup"><span data-stu-id="6bd69-217">Describes memory-mapped files, which contain the contents of files on disk in virtual memory.</span></span> <span data-ttu-id="6bd69-218">您可以使用記憶體對應檔案來編輯超大的檔案，以及建立供處理序間通訊使用的共用記憶體。</span><span class="sxs-lookup"><span data-stu-id="6bd69-218">You can use memory-mapped files to edit very large files and to create shared memory for interprocess communication.</span></span>
