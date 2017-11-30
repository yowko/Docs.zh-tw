---
title: "如何：壓縮與解壓縮檔案"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- I/O [.NET Framework], compression
- compression
- compress files
ms.assetid: e9876165-3c60-4c84-a272-513e47acf579
caps.latest.revision: "19"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 22a95ce18b602d4e329499c5d36557213e08a8b5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-compress-and-extract-files"></a><span data-ttu-id="9f97c-102">如何：壓縮與解壓縮檔案</span><span class="sxs-lookup"><span data-stu-id="9f97c-102">How to: Compress and Extract Files</span></span>
<span data-ttu-id="9f97c-103"><xref:System.IO.Compression>命名空間包含下列型別來壓縮和解壓縮檔案和資料流。</span><span class="sxs-lookup"><span data-stu-id="9f97c-103">The <xref:System.IO.Compression> namespace contains the following types for compressing and decompressing files and streams.</span></span> <span data-ttu-id="9f97c-104">您也可以使用這些類型，以讀取和修改壓縮檔案的內容：</span><span class="sxs-lookup"><span data-stu-id="9f97c-104">You can also use these types to read and modify the contents of a compressed file:</span></span>  
  
-   <xref:System.IO.Compression.ZipFile>  
  
-   <xref:System.IO.Compression.ZipArchive>  
  
-   <xref:System.IO.Compression.ZipArchiveEntry>  
  
-   <xref:System.IO.Compression.DeflateStream>  
  
-   <xref:System.IO.Compression.GZipStream>  
  
 <span data-ttu-id="9f97c-105">下列範例顯示一些使用壓縮的檔案時，您可以執行的函式。</span><span class="sxs-lookup"><span data-stu-id="9f97c-105">The following examples show some of the functions you can perform when working with compressed files.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f97c-106">範例</span><span class="sxs-lookup"><span data-stu-id="9f97c-106">Example</span></span>  
 <span data-ttu-id="9f97c-107">這個範例示範如何建立和解壓縮檔案使用具有.zip 副檔名<xref:System.IO.Compression.ZipFile>類別。</span><span class="sxs-lookup"><span data-stu-id="9f97c-107">This example shows how to create and extract a compressed file that has a .zip file name extension by using the <xref:System.IO.Compression.ZipFile> class.</span></span> <span data-ttu-id="9f97c-108">它壓縮資料夾的內容至新的.zip 檔案，然後會擷取該內容發佈至新的資料夾。</span><span class="sxs-lookup"><span data-stu-id="9f97c-108">It compresses the contents of a folder into a new .zip file and then extracts that content to a new folder.</span></span> <span data-ttu-id="9f97c-109">若要使用<xref:System.IO.Compression.ZipFile>類別，您必須參考`System.IO.Compression.FileSystem`專案中的組件。</span><span class="sxs-lookup"><span data-stu-id="9f97c-109">To use the <xref:System.IO.Compression.ZipFile> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipFile#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.zipfile/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipFile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.zipfile/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="9f97c-110">範例</span><span class="sxs-lookup"><span data-stu-id="9f97c-110">Example</span></span>  
 <span data-ttu-id="9f97c-111">下一個範例示範如何逐一查看現有的.zip 檔案的內容，將副檔名為.txt 的檔案解壓縮。</span><span class="sxs-lookup"><span data-stu-id="9f97c-111">The next example shows how to iterate through the contents of an existing .zip file and extract files that have a .txt extension.</span></span> <span data-ttu-id="9f97c-112">它會使用<xref:System.IO.Compression.ZipArchive>類別來存取現有的.zip 檔案，而<xref:System.IO.Compression.ZipArchiveEntry>類別來檢查壓縮檔案中的個別項目。</span><span class="sxs-lookup"><span data-stu-id="9f97c-112">It uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and the <xref:System.IO.Compression.ZipArchiveEntry> class to inspect the individual entries in the compressed file.</span></span> <span data-ttu-id="9f97c-113">它會使用擴充方法 (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) 的<xref:System.IO.Compression.ZipArchiveEntry>物件。</span><span class="sxs-lookup"><span data-stu-id="9f97c-113">It uses an extension method (<xref:System.IO.Compression.ZipFileExtensions.ExtractToFile%2A>) for the <xref:System.IO.Compression.ZipArchiveEntry> object.</span></span> <span data-ttu-id="9f97c-114">擴充方法位於<xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType>類別。</span><span class="sxs-lookup"><span data-stu-id="9f97c-114">The extension method is available in the <xref:System.IO.Compression.ZipFileExtensions?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="9f97c-115">若要使用<xref:System.IO.Compression.ZipFileExtensions>類別，您必須參考`System.IO.Compression.FileSystem`專案中的組件。</span><span class="sxs-lookup"><span data-stu-id="9f97c-115">To use the <xref:System.IO.Compression.ZipFileExtensions> class, you must reference the `System.IO.Compression.FileSystem` assembly in your project.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipArchive#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchive/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchive/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="9f97c-116">範例</span><span class="sxs-lookup"><span data-stu-id="9f97c-116">Example</span></span>  
 <span data-ttu-id="9f97c-117">下一個範例會使用<xref:System.IO.Compression.ZipArchive>類別來存取現有的.zip 檔案，並將新檔案加入至壓縮的檔案。</span><span class="sxs-lookup"><span data-stu-id="9f97c-117">The next example uses the <xref:System.IO.Compression.ZipArchive> class to access an existing .zip file, and adds a new file to the compressed file.</span></span> <span data-ttu-id="9f97c-118">當您將它加入至現有的.zip 檔案，取得壓縮的新檔案。</span><span class="sxs-lookup"><span data-stu-id="9f97c-118">The new file gets compressed when you add it to the existing .zip file.</span></span>  
  
 [!code-csharp[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/cs/program1.cs#1)]
 [!code-vb[System.IO.Compression.ZipArchiveMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.compression.ziparchivemode/vb/program1.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="9f97c-119">範例</span><span class="sxs-lookup"><span data-stu-id="9f97c-119">Example</span></span>  
 <span data-ttu-id="9f97c-120">您也可以使用<xref:System.IO.Compression.GZipStream>和<xref:System.IO.Compression.DeflateStream>來壓縮和解壓縮資料的類別。</span><span class="sxs-lookup"><span data-stu-id="9f97c-120">You can also use the <xref:System.IO.Compression.GZipStream> and <xref:System.IO.Compression.DeflateStream> classes to compress and decompress data.</span></span> <span data-ttu-id="9f97c-121">它們使用相同的壓縮演算法。</span><span class="sxs-lookup"><span data-stu-id="9f97c-121">They use the same compression algorithm.</span></span> <span data-ttu-id="9f97c-122">壓縮<xref:System.IO.Compression.GZipStream>物件寫入至副檔名為.gz 檔案可以使用許多常用的工具，除了所提供的方法解壓縮<xref:System.IO.Compression.GZipStream>。</span><span class="sxs-lookup"><span data-stu-id="9f97c-122">Compressed <xref:System.IO.Compression.GZipStream> objects that are written to a file that has an extension of .gz can be decompressed by using many common tools in addition to the methods provided by <xref:System.IO.Compression.GZipStream>.</span></span> <span data-ttu-id="9f97c-123">這個範例示範如何壓縮和解壓縮檔案目錄使用<xref:System.IO.Compression.GZipStream>類別。</span><span class="sxs-lookup"><span data-stu-id="9f97c-123">This example shows how to compress and decompress a directory of files by using the <xref:System.IO.Compression.GZipStream> class.</span></span>  
  
 [!code-csharp[IO.Compression.GZip1#1](../../../samples/snippets/csharp/VS_Snippets_CLR/IO.Compression.GZip1/CS/gziptest.cs#1)]
 [!code-vb[IO.Compression.GZip1#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/IO.Compression.GZip1/VB/gziptest.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="9f97c-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9f97c-124">See Also</span></span>  
 <xref:System.IO.Compression.ZipArchive>  
 <xref:System.IO.Compression.ZipFile>  
 <xref:System.IO.Compression.ZipArchiveEntry>  
 <xref:System.IO.Compression.DeflateStream>  
 <xref:System.IO.Compression.GZipStream>  
 [<span data-ttu-id="9f97c-125">檔案和資料流 I-O</span><span class="sxs-lookup"><span data-stu-id="9f97c-125">File and Stream I-O</span></span>](../../../docs/standard/io/index.md)
