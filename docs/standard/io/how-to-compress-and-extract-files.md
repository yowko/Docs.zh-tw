---
title: 操作說明：壓縮與解壓縮檔案
ms.date: 06/06/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 669936d15cfe1ea125ed36ffdfcfd093b6aacbe1
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/28/2018
ms.locfileid: "47424424"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="c451b-102">操作說明：壓縮與解壓縮檔案</span><span class="sxs-lookup"><span data-stu-id="c451b-102">How to: Compress and extract files</span></span>

<span data-ttu-id="c451b-103"><xref:System.IO.Compression> 命名空間包含壓縮及解壓縮檔案和資料流的下列類型。</span><span class="sxs-lookup"><span data-stu-id="c451b-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="c451b-104">您也可以使用這些類型讀取和修改壓縮檔案的內容：</span><span class="sxs-lookup"><span data-stu-id="c451b-104">You can also use these types to read and modify the contents of a compressed file:</span></span>

- <xref:System.IO.Compression.ZipFile>

- <xref:System.IO.Compression.ZipArchive>

- <xref:System.IO.Compression.ZipArchiveEntry>

- <xref:System.IO.Compression.DeflateStream>

- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="c451b-105">下列範例示範您可以在使用壓縮檔案時執行的部分函式。</span><span class="sxs-lookup"><span data-stu-id="c451b-105">The following examples show some of the functions you can perform when working with compressed files.</span></span>

## <a name="example-1---create-and-extract-a-zip-file"></a><span data-ttu-id="c451b-106">範例 1：建立和解壓縮 .zip 檔案</span><span class="sxs-lookup"><span data-stu-id="c451b-106">Example 1 - Create and extract a .zip file</span></span>

<span data-ttu-id="c451b-107">以下範例示範如何使用 <xref:System.IO.Compression.ZipFile> 類別，建立和解壓縮副檔名為 .zip 的檔案。</span><span class="sxs-lookup"><span data-stu-id="c451b-107">The following example shows how to create and extract a compressed file that has a .zip file name extension by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="c451b-108">它會資料夾的內容壓縮至新的 .zip 檔案，然後將該內容解壓縮至新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="c451b-108">It compresses the contents of a folder into a new .zip file and then extracts that content to a new folder.</span></span> <span data-ttu-id="c451b-109">若要使用 <xref:System.IO.Compression.ZipFile> 類別，您必須參考專案中的 `System.IO.Compression.FileSystem` 組件。</span><span class="sxs-lookup"><span data-stu-id="c451b-109">To use the <xref:System.IO.Compression.ZipFile> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2---extract-specific-file-extensions"></a><span data-ttu-id="c451b-110">範例 2：解壓縮特定的檔案副檔名</span><span class="sxs-lookup"><span data-stu-id="c451b-110">Example 2 - Extract specific file extensions</span></span>

<span data-ttu-id="c451b-111">下一個範例示範如何逐一查看現有 .zip 檔案的內容，並將副檔名為 .txt 的檔案解壓縮。</span><span class="sxs-lookup"><span data-stu-id="c451b-111">The next example shows how to iterate through the contents of an existing .zip file and extract files that have a .txt extension.</span></span> <span data-ttu-id="c451b-112">它會使用 <xref:System.IO.Compression.ZipArchive> 類別存取現有的 .zip 檔案，並使用 <xref:System.IO.Compression.ZipArchiveEntry> 類別檢查壓縮檔案中的個別項目。</span><span class="sxs-lookup"><span data-stu-id="c451b-112">It uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries in the compressed file.</span></span> <span data-ttu-id="c451b-113">它會為 <xref:System.IO.Compression.ZipArchiveEntry> 物件使用擴充方法 (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>)。</span><span class="sxs-lookup"><span data-stu-id="c451b-113">It uses an extension method (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) for the <xref:System.IO.Compression.ZipArchiveEntry> object.</span></span> <span data-ttu-id="c451b-114">擴充方法可在 <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> 類別中使用。</span><span class="sxs-lookup"><span data-stu-id="c451b-114">The extension method is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="c451b-115">若要使用 <xref:System.IO.Compression.ZipFileExtensions> 類別，您必須參考專案中的 `System.IO.Compression.FileSystem` 組件。</span><span class="sxs-lookup"><span data-stu-id="c451b-115">To use the <xref:System.IO.Compression.ZipFileExtensions> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c451b-116">當您在解壓縮檔案時，必須尋找惡意的檔案路徑，以免它逸出您要解壓縮的目的目錄。</span><span class="sxs-lookup"><span data-stu-id="c451b-116">When unzipping files, you must look for malicious file paths which can escape out of the directory where you want to unzip into.</span></span> <span data-ttu-id="c451b-117">這是所謂的路徑周遊攻擊。</span><span class="sxs-lookup"><span data-stu-id="c451b-117">This is known as a path traversal attack.</span></span>

<span data-ttu-id="c451b-118">以下範例示範如何檢查惡意的檔案路徑，並提供安全的方式來解壓縮：</span><span class="sxs-lookup"><span data-stu-id="c451b-118">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip:</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3---add-a-new-file-to-an-existing-zip-file"></a><span data-ttu-id="c451b-119">範例 3：將新檔案加入至現有的 .zip 檔案</span><span class="sxs-lookup"><span data-stu-id="c451b-119">Example 3 - Add a new file to an existing .zip file</span></span>

<span data-ttu-id="c451b-120">以下範例使用 <xref:System.IO.Compression.ZipArchive> 類別存取現有的 .zip 檔案，並將新檔案加入至壓縮檔案。</span><span class="sxs-lookup"><span data-stu-id="c451b-120">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and adds a new file to the compressed file.</span></span> <span data-ttu-id="c451b-121">當您將新檔案加入至現有的 .zip 檔案時，會壓縮該檔案。</span><span class="sxs-lookup"><span data-stu-id="c451b-121">The new file gets compressed when you add it to the existing .zip file.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4---compress-and-decompress-a-directory-of-gz-files"></a><span data-ttu-id="c451b-122">範例 4：壓縮和解壓縮 .gz 檔案目錄</span><span class="sxs-lookup"><span data-stu-id="c451b-122">Example 4 - Compress and decompress a directory of .gz files</span></span>

<span data-ttu-id="c451b-123">您也可以使用 <xref:System.IO.Compression.GZipStream> 和 <xref:System.IO.Compression.DeflateStream> 類別壓縮和解壓縮資料。</span><span class="sxs-lookup"><span data-stu-id="c451b-123">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="c451b-124">它們會使用相同的壓縮演算法。</span><span class="sxs-lookup"><span data-stu-id="c451b-124">They use the same compression algorithm.</span></span> <span data-ttu-id="c451b-125">除了 <xref:System.IO.Compression.GZipStream> 所提供的方法之外，寫入至副檔名為 .gz 之檔案的壓縮 <xref:System.IO.Compression.GZipStream> 物件還可以使用許多常用工具解壓縮。</span><span class="sxs-lookup"><span data-stu-id="c451b-125">Compressed <xref:System.IO.Compression.GZipStream> objects that are written to a file that has an extension of .gz can be decompressed by using many common tools in addition to the methods provided by <xref:System.IO.Compression.GZipStream>.</span></span> <span data-ttu-id="c451b-126">以下範例示範如何使用 <xref:System.IO.Compression.GZipStream> 類別壓縮和解壓縮檔案目錄：</span><span class="sxs-lookup"><span data-stu-id="c451b-126">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="c451b-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c451b-127">See also</span></span>

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [<span data-ttu-id="c451b-128">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="c451b-128">File and Stream I/O</span></span>](../../../docs/standard/io/index.md)
