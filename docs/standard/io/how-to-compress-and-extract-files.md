---
title: 操作說明：壓縮與解壓縮檔案
description: 壓縮 & 使用系統壓縮檔案壓縮。 請參閱使用 ZipFile、ZipArchive、ZipArchiveEntry、DeflateStream、& GZipStream 的範例。
ms.date: 01/14/2019
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
ms.openlocfilehash: ea078099aba3161818844d14af221eb582e7f11b
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188285"
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="bc59e-104">操作說明：壓縮與解壓縮檔案</span><span class="sxs-lookup"><span data-stu-id="bc59e-104">How to: Compress and extract files</span></span>

<span data-ttu-id="bc59e-105"><xref:System.IO.Compression> 命名空間包含壓縮及解壓縮檔案和資料流的下列類型。</span><span class="sxs-lookup"><span data-stu-id="bc59e-105">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="bc59e-106">您也可以使用這些類型讀取和修改壓縮檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="bc59e-106">You can also use these types to read and modify the contents of a compressed file.</span></span>

- <xref:System.IO.Compression.ZipFile>
- <xref:System.IO.Compression.ZipArchive>
- <xref:System.IO.Compression.ZipArchiveEntry>
- <xref:System.IO.Compression.DeflateStream>
- <xref:System.IO.Compression.GZipStream>

<span data-ttu-id="bc59e-107">下列範例示範您可以搭配壓縮檔案執行的部分作業。</span><span class="sxs-lookup"><span data-stu-id="bc59e-107">The following examples show some of the operations you can perform with compressed files.</span></span> <span data-ttu-id="bc59e-108">這些範例需要將下列 NuGet 套件新增至您的專案：</span><span class="sxs-lookup"><span data-stu-id="bc59e-108">These examples require the following NuGet packages to be added to your project:</span></span>

- [<span data-ttu-id="bc59e-109">System.IO.Compression</span><span class="sxs-lookup"><span data-stu-id="bc59e-109">System.IO.Compression</span></span>](https://www.nuget.org/packages/System.IO.Compression)
- [<span data-ttu-id="bc59e-110">System.IO.Compression.ZipFile</span><span class="sxs-lookup"><span data-stu-id="bc59e-110">System.IO.Compression.ZipFile</span></span>](https://www.nuget.org/packages/System.IO.Compression.ZipFile)

<span data-ttu-id="bc59e-111">如果您是使用 .NET Framework，請將這兩個程式庫的參考新增至您的專案：</span><span class="sxs-lookup"><span data-stu-id="bc59e-111">If you're using .NET Framework, add references to these two libraries to your project:</span></span>

- `System.IO.Compression`
- `System.IO.Compression.FileSystem`

## <a name="example-1-create-and-extract-a-zip-file"></a><span data-ttu-id="bc59e-112">範例1：建立和解壓縮 .zip 檔案</span><span class="sxs-lookup"><span data-stu-id="bc59e-112">Example 1: Create and extract a .zip file</span></span>

<span data-ttu-id="bc59e-113">下列範例示範如何使用 <xref:System.IO.Compression.ZipFile> 類別，建立和解壓縮 *.zip* 檔案。</span><span class="sxs-lookup"><span data-stu-id="bc59e-113">The following example shows how to create and extract a compressed *.zip* file by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="bc59e-114">此範例會將資料夾的內容壓縮至新的 *.zip* 檔案，然後將該 zip 解壓縮至新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="bc59e-114">The example compresses the contents of a folder into a new *.zip* file, and then extracts the zip to a new folder.</span></span>

<span data-ttu-id="bc59e-115">若要執行樣本，請在程式資料夾中建立 *啟動* 資料夾，並在其中填入要壓縮的檔案。</span><span class="sxs-lookup"><span data-stu-id="bc59e-115">To run the sample, create a *start* folder in your program folder and populate it with files to zip.</span></span>

[!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]

## <a name="example-2-extract-specific-file-extensions"></a><span data-ttu-id="bc59e-116">範例2：解壓縮特定的副檔名</span><span class="sxs-lookup"><span data-stu-id="bc59e-116">Example 2: Extract specific file extensions</span></span>

<span data-ttu-id="bc59e-117">下一個範例會逐一查看現有 *.zip* 檔案的內容，並將副檔名為 *.txt* 的檔案解壓縮。</span><span class="sxs-lookup"><span data-stu-id="bc59e-117">The next example iterates through the contents of an existing *.zip* file and extracts files that have a *.txt* extension.</span></span> <span data-ttu-id="bc59e-118">它會使用 <xref:System.IO.Compression.ZipArchive> 類別來存取 zip，以及使用 <xref:System.IO.Compression.ZipArchiveEntry> 類別來檢查個別項目。</span><span class="sxs-lookup"><span data-stu-id="bc59e-118">It uses the <xref:System.IO.Compression.ZipArchive> class to access the zip, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries.</span></span> <span data-ttu-id="bc59e-119"><xref:System.IO.Compression.ZipArchiveEntry> 物件的擴充方法 <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> 可在 <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> 類別中使用。</span><span class="sxs-lookup"><span data-stu-id="bc59e-119">The extension method <xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A> for the <xref:System.IO.Compression.ZipArchiveEntry> object is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span>

<span data-ttu-id="bc59e-120">若要執行樣本，請將名為 *result.zip* 的 *.zip* 檔案置於您的程式資料夾中。</span><span class="sxs-lookup"><span data-stu-id="bc59e-120">To run the sample, place a *.zip* file called *result.zip* in your program folder.</span></span> <span data-ttu-id="bc59e-121">出現提示時，提供要擷取至的資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="bc59e-121">When prompted, provide a folder name to extract to.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bc59e-122">當您在解壓縮檔案時，必須尋找惡意的檔案路徑，以免它逸出您解壓縮的目的目錄。</span><span class="sxs-lookup"><span data-stu-id="bc59e-122">When unzipping files, you must look for malicious file paths, which can escape out of the directory you unzip into.</span></span> <span data-ttu-id="bc59e-123">這是所謂的路徑周遊攻擊。</span><span class="sxs-lookup"><span data-stu-id="bc59e-123">This is known as a path traversal attack.</span></span> <span data-ttu-id="bc59e-124">以下範例示範如何檢查惡意的檔案路徑，並提供安全的方式來解壓縮。</span><span class="sxs-lookup"><span data-stu-id="bc59e-124">The following example demonstrates how to check for malicious file paths and provides a safe way to unzip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]

## <a name="example-3-add-a-file-to-an-existing-zip"></a><span data-ttu-id="bc59e-125">範例3：將檔案新增至現有的 zip</span><span class="sxs-lookup"><span data-stu-id="bc59e-125">Example 3: Add a file to an existing zip</span></span>

<span data-ttu-id="bc59e-126">下列範例使用 <xref:System.IO.Compression.ZipArchive> 類別存取現有的 *.zip* 檔案，並將檔案新增至其中。</span><span class="sxs-lookup"><span data-stu-id="bc59e-126">The following example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing *.zip* file, and adds a file to it.</span></span> <span data-ttu-id="bc59e-127">將新檔案新增至現有的 .zip 時，即會壓縮該檔案。</span><span class="sxs-lookup"><span data-stu-id="bc59e-127">The new file gets compressed when you add it to the existing zip.</span></span>

[!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
[!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]

## <a name="example-4-compress-and-decompress-gz-files"></a><span data-ttu-id="bc59e-128">範例4：壓縮和解壓縮 gz 檔案</span><span class="sxs-lookup"><span data-stu-id="bc59e-128">Example 4: Compress and decompress .gz files</span></span>

<span data-ttu-id="bc59e-129">您也可以使用 <xref:System.IO.Compression.GZipStream> 和 <xref:System.IO.Compression.DeflateStream> 類別壓縮和解壓縮資料。</span><span class="sxs-lookup"><span data-stu-id="bc59e-129">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="bc59e-130">它們會使用相同的壓縮演算法。</span><span class="sxs-lookup"><span data-stu-id="bc59e-130">They use the same compression algorithm.</span></span> <span data-ttu-id="bc59e-131">您可以使用許多常用工具，將寫入至 *.gz* 檔案的 <xref:System.IO.Compression.GZipStream> 物件解壓縮。</span><span class="sxs-lookup"><span data-stu-id="bc59e-131">You can decompress <xref:System.IO.Compression.GZipStream> objects that are written to a *.gz* file by using many common tools.</span></span> <span data-ttu-id="bc59e-132">以下範例示範如何使用 <xref:System.IO.Compression.GZipStream> 類別壓縮和解壓縮檔案目錄：</span><span class="sxs-lookup"><span data-stu-id="bc59e-132">The following example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class:</span></span>

[!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
[!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]

## <a name="see-also"></a><span data-ttu-id="bc59e-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bc59e-133">See also</span></span>

- <xref:System.IO.Compression.ZipArchive>  
- <xref:System.IO.Compression.ZipFile>  
- <xref:System.IO.Compression.ZipArchiveEntry>  
- <xref:System.IO.Compression.DeflateStream>  
- <xref:System.IO.Compression.GZipStream>  
- [<span data-ttu-id="bc59e-134">檔案和資料流 I/O</span><span class="sxs-lookup"><span data-stu-id="bc59e-134">File and stream I/O</span></span>](index.md)
